---
title: ファイルの所有権と権限の設定
description: 次の手順に従って、Adobe Commerceのオンプレミスインストール用のファイルシステム権限を設定します。
exl-id: 2410ee4f-978c-4b71-b3f6-0c042f9f4dc4
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '981'
ht-degree: 0%

---

# ファイルの所有権と権限の設定

ここでは、Adobe Commerceをインストールする前に、web サーバーグループに読み取り/書き込み権限を設定する方法について説明します。 これは、コマンドラインがファイルをファイルシステムに書き込めるようにするために必要です。

使用する手順は、を使用するかによって異なります [共有ホスティング](#set-permissions-for-one-user-on-shared-hosting) ユーザーが 1 人いる、または [プライベートサーバー](#set-ownership-and-permissions-for-two-users) とに 2 人のユーザーがいます。

## 共有ホスティングでの 1 人のユーザーに対する権限の設定

この項では、Web サーバーも実行するユーザーと同じユーザーとしてアプリケーション・サーバーにログインする場合に、インストール前の権限を設定する方法について説明します。 このタイプの設定は、共有ホスティング環境で一般的です。

アプリケーションをインストールする前に権限を設定するには、次の手順に従います。

1. アプリケーションサーバーにログインします。
1. 共有ホスティング プロバイダが提供するファイル マネージャ アプリケーションを使用して、書き込みアクセス許可が次のディレクトリに設定されていることを確認します。

   * `vendor` （Composer または圧縮アーカイブのインストール）
   * `app/etc`
   * `pub/static`
   * `var`
   * `generated`
   * その他の静的リソース

1. コマンドラインでアクセスできる場合は、次のコマンドを表示されている順序で入力します。

   ```bash
   cd <app_root>
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type f -exec chmod u+w {} +
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type d -exec chmod u+w {} +
   ```

   ```bash
   chmod u+x bin/magento
   ```

   オプションですべてのコマンドを 1 行で入力するには、アプリケーションが次の場所にインストールされていると仮定して、次のように入力します `/var/www/html/magento2`:

   ```bash
   cd /var/www/html/magento2 && find var generated vendor pub/static pub/media app/etc -type f -exec chmod u+w {} + && find var generated vendor pub/static pub/media app/etc -type d -exec chmod u+w {} + && chmod u+x bin/magento
   ```

1. まだ行っていない場合は、次のいずれかの方法でアプリケーションを取得します。

   * [Composer メタパッケージ](../../composer.md)
   * [リポジトリのクローンを作成します（コントリビューションをしている開発者のみ）。](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)

1. ファイルシステムの所有権と権限を設定したら、 [アプリケーションのインストール](../../advanced.md)

>[!NOTE]
>
>アプリケーションのインストール後に権限をさらに制限するには、次の操作を行います [umask の設定](../../next-steps/set-umask.md).

## 2 人のユーザーの所有権と権限の設定

この節では、独自のサーバーまたはプライベートホスティング設定の所有権と権限を設定する方法について説明します。 このタイプの設定では、通常、 *できません* web サーバーユーザーとしてログインするか、に切り替えます。 通常は、1 人のユーザーとしてログインし、別のユーザーとして web サーバーを実行します。

2 ユーザー・システムの所有権および権限を設定するには、次の手順に従います。

次のタスクを、表示されている順序で実行します。

* [共有グループについて](#about-the-shared-group)
* [ファイルシステムの所有者を作成し、強力なパスワードをユーザーに付与します。](#create-the-file-system-owner-and-give-the-user-a-strong-password)
* [Web サーバーユーザーのグループの検索](#find-the-web-server-user-group)
* [ファイルシステムの所有者を web サーバーグループに追加します。](#put-the-file-system-owner-in-the-web-server-group)
* [ソフトウェアの入手](#get-the-software)
* [共有グループの所有権と権限の設定](#set-ownership-and-permissions-for-the-shared-group)

### 共有グループについて

Web サーバーがファイル・システムにファイルとディレクトリを書き込めるようにし、さらにメンテナンスできるようにする場合 *所有権* ファイルシステムの所有者は、両方のユーザーが同じグループに属している必要があります。 これは、両方のユーザーがファイル（管理者またはその他の web ベースのユーティリティを使用して作成されたファイルを含む）に対してアクセスを共有するために必要です。

この節では、ファイルシステムの所有者を作成し、そのユーザーを web サーバーのグループに追加する方法について説明します。 必要に応じて、既存のユーザーアカウントを使用できます。セキュリティ上の理由から、ユーザーには強力なパスワードを使用することをお勧めします。

>[!NOTE]
>
>次にスキップ [Web サーバーユーザーグループの検索](#find-the-web-server-user-group) 既存のユーザーアカウントを使用する予定がある場合。

### ファイルシステムの所有者を作成し、強力なパスワードをユーザーに付与します。

このセクションでは、ファイルシステムの所有者を作成する方法について説明します。 （ファイル・システムの所有者は、 *コマンドラインユーザー*.）

CentOS または Ubuntu でユーザーを作成するには、ユーザーとして次のコマンドを入力します。 `root` 権限：

```bash
adduser <username>
```

ユーザーにパスワードを付与するには、ユーザーとして次のコマンドを入力します。 `root` 権限：

```bash
passwd <username>
```

画面の指示に従って、ユーザーのパスワードを作成します。

>[!WARNING]
>
>持っていない場合 `root` アプリケーションサーバー上の権限。別のローカルユーザーアカウントを使用できます。 ユーザーに強力なパスワードが設定されていることを確認して、に進みます [ファイルシステムの所有者を web サーバーグループに追加します。](#step-3-put-the-file-system-owner-in-the-web-servers-group).

例えば、という名前のユーザーを作成するには、次のように指定します `magento_user` ユーザーにパスワードを入力し、次のように入力します。

```bash
sudo adduser magento_user
```

```bash
sudo passwd magento_user
```

>[!WARNING]
>
>このユーザーを作成する目的は、セキュリティを強化することなので、必ず以下を作成してください。 [強力なパスワード](https://en.wikipedia.org/wiki/Password_strength).

### Web サーバーユーザーグループの検索

Web サーバーユーザーのグループを見つけるには：

* CentOS:

  ```bash
  grep -E -i '^user|^group' /etc/httpd/conf/httpd.conf
  ```

  または

  ```bash
  grep -Ei '^user|^group' /etc/httpd/conf/httpd.conf
  ```

通常、ユーザー名とグループ名は両方とも指定します `apache`.

* Ubuntu: `ps aux | grep apache` Apache ユーザーを探すには、次の手順を実行します。 `groups <apache user>` グループを検索します。

通常、ユーザー名とグループ名は両方とも指定します `www-data`.

### ファイルシステムの所有者を web サーバーグループに追加します。

ファイルシステムの所有者を web サーバーのプライマリグループに配置するには（CentOS と Ubuntu の一般的な Apache グループ名を想定）、次のコマンドをユーザーとして入力します。 `root` 権限：

* CentOS: `usermod -a -G apache <username>`
* Ubuntu: `usermod -a -G www-data <username>`

>[!NOTE]
>
>この `-a -G` オプションは、次の点を追加するため重要です `apache` または `www-data` as a *2 次* ユーザーアカウントにグループ化します。これにより、ユーザーの *プライマリ* グループ。 ユーザーアカウントへのセカンダリグループの追加は役に立ちます [ファイルの所有権と権限の制限](#set-ownership-and-permissions-for-two-users) 共有グループのメンバーが特定のファイルにのみアクセスできるようにします。

例えば、ユーザーを追加するには、次のコマンドを実行します `magento_user` に `apache` centOS のプライマリグループ：

```bash
sudo usermod -a -G apache magento_user
```

ユーザーが web サーバーグループのメンバーであることを確認するには、次のコマンドを入力します。

```bash
groups magento_user
```

次のサンプル結果は、ユーザーのプライマリ （`magento`）とセカンダリ （`apache`） グループ。

```bash
magento_user : magento_user apache
```

>[!NOTE]
>
>通常、ユーザー名とプライマリグループ名は同じです。

タスクを完了するには、web サーバーを再起動します。

* Ubuntu: `service apache2 restart`
* CentOS: `service httpd restart`

### ソフトウェアの入手

まだ行っていない場合は、次のいずれかの方法でソフトウェアを入手します。

* [Composer メタパッケージ](../../composer.md)
* [リポジトリのクローンを作成します（コントリビューションをしている開発者のみ）。](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)

### 共有グループの所有権と権限の設定

アプリケーションをインストールする前に所有権と権限を設定するには、次の手順に従います。

1. ファイルシステムの所有者としてアプリケーションサーバーにログインするか、所有者に切り替えます。
1. 次のコマンドを表示されている順序で入力します。

   ```bash
   cd <app_root>
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} +
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} +
   ```

   ```bash
   chown -R :<web server group> .
   ```

   ```bash
   chmod u+x bin/magento
   ```

オプションですべてのコマンドを 1 行で入力するには、アプリケーションが次の場所にインストールされていると仮定して、次のように入力します `/var/www/html/magento2` web サーバーグループ名はです。 `apache`:

```bash
cd /var/www/html/magento2 && find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} + && find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} + && chown -R :apache . && chmod u+x bin/magento
```

ファイルシステムの権限が不適切に設定され、ファイルシステムの所有者が変更できない場合は、 `root` 権限：

```bash
cd /var/www/html/magento2 && sudo find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} + && sudo find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} + && sudo chown -R :apache . && sudo chmod u+x bin/magento
```

## ファイルシステムの所有者に切り替える

このトピックの他のタスクを実行した後、次のいずれかのコマンドを入力してそのユーザーに切り替えます。

* Ubuntu: `su <username>`
* CentOS: `su - <username>`

以下に例を挙げます。

```bash
su magento_user
```
