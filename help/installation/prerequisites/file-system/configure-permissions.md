---
title: ファイルの所有権と権限の設定
description: 次の手順に従って、Adobe Commerceのオンプレミスインストール用のファイルシステム権限を設定します。
exl-id: 2410ee4f-978c-4b71-b3f6-0c042f9f4dc4
source-git-commit: 84a20012a81278cc95587ec14281b05330261687
workflow-type: tm+mt
source-wordcount: '981'
ht-degree: 0%

---

# ファイルの所有権と権限の設定

ここでは、Adobe Commerceをインストールする前に、web サーバーグループに読み取り/書き込み権限を設定する方法について説明します。 これは、コマンドラインがファイルをファイルシステムに書き込めるようにするために必要です。

使用する手順は、[&#x200B; 共有ホスティング &#x200B;](#set-permissions-for-one-user-on-shared-hosting) を使用して 1 人のユーザーが存在するか、[&#x200B; プライベートサーバー &#x200B;](#set-ownership-and-permissions-for-two-users) を使用して 2 人のユーザーが存在するかによって異なります。

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

   必要に応じてすべてのコマンドを 1 行に入力するには、アプリケーションが `/var/www/html/magento2` にインストールされている場合は、次のように入力します。

   ```bash
   cd /var/www/html/magento2 && find var generated vendor pub/static pub/media app/etc -type f -exec chmod u+w {} + && find var generated vendor pub/static pub/media app/etc -type d -exec chmod u+w {} + && chmod u+x bin/magento
   ```

1. まだ行っていない場合は、次のいずれかの方法でアプリケーションを取得します。

   * [Composer メタパッケージ](../../composer.md)
   * [&#x200B; リポジトリのクローンを作成する（コントリビューションを行う開発者のみ） &#x200B;](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository)

1. ファイルシステムの所有権と権限を設定したら、[&#x200B; アプリケーションをインストールします &#x200B;](../../advanced.md)。

>[!NOTE]
>
>アプリケーションのインストール後に権限をさらに制限するには、[umask を構成 &#x200B;](../../next-steps/set-umask.md) します。

## 2 人のユーザーの所有権と権限の設定

この節では、独自のサーバーまたはプライベートホスティング設定の所有権と権限を設定する方法について説明します。 このタイプの設定では、通常、web サーバーユーザーとしてログインしたり、web サーバーユーザーに切り替えたりすることは *できません*。 通常は、1 人のユーザーとしてログインし、別のユーザーとして web サーバーを実行します。

2 ユーザー・システムの所有権および権限を設定するには、次の手順に従います。

次のタスクを、表示されている順序で実行します。

* [共有グループについて](#about-the-shared-group)
* [ファイルシステムの所有者を作成し、強力なパスワードをユーザーに付与します。](#create-the-file-system-owner-and-give-the-user-a-strong-password)
* [Web サーバーユーザーのグループの検索](#find-the-web-server-user-group)
* [ファイルシステムの所有者を web サーバーグループに追加します。](#put-the-file-system-owner-in-the-web-server-group)
* [ソフトウェアの入手](#get-the-software)
* [共有グループの所有権と権限の設定](#set-ownership-and-permissions-for-the-shared-group)

### 共有グループについて

Web サーバがファイル・システムにファイルとディレクトリを書き込み、ファイル・システムの所有者が *所有権* を維持できるようにするには、両方のユーザーが同じグループに属している必要があります。 これは、両方のユーザーがファイル（管理者またはその他の web ベースのユーティリティを使用して作成されたファイルを含む）に対してアクセスを共有するために必要です。

この節では、ファイルシステムの所有者を作成し、そのユーザーを web サーバーのグループに追加する方法について説明します。 必要に応じて、既存のユーザーアカウントを使用できます。セキュリティ上の理由から、ユーザーには強力なパスワードを使用することをお勧めします。

>[!NOTE]
>
>既存のユーザーアカウントを使用する予定がある場合は、[Web サーバーユーザーグループを見つける &#x200B;](#find-the-web-server-user-group) にスキップします。

### ファイルシステムの所有者を作成し、強力なパスワードをユーザーに付与します。

このセクションでは、ファイルシステムの所有者を作成する方法について説明します。 （ファイルシステムの所有者は、*コマンドラインユーザー* の別の用語です。）

CentOS または Ubuntu でユーザーを作成するには、`root` 権限を持つユーザーとして次のコマンドを入力します。

```bash
adduser <username>
```

ユーザーにパスワードを付与するには、`root` 権限を持つユーザーとして、次のコマンドを入力します。

```bash
passwd <username>
```

画面の指示に従って、ユーザーのパスワードを作成します。

>[!WARNING]
>
>アプリケーションサーバーに対する `root` 権限がない場合は、別のローカルユーザーアカウントを使用できます。 ユーザーに強力なパスワードがあることを確認し、[Web サーバーグループにファイルシステムの所有者を配置する &#x200B;](#step-3-put-the-file-system-owner-in-the-web-servers-group) を続行します。

例えば、`magento_user` という名前のユーザーを作成し、パスワードを指定するには、次のように入力します。

```bash
sudo adduser magento_user
```

```bash
sudo passwd magento_user
```

>[!WARNING]
>
>このユーザーを作成する目的は、セキュリティを強化することなので、必ず [strong password](https://en.wikipedia.org/wiki/Password_strength) を作成してください。

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

通常、ユーザー名とグループ名は両方とも `apache` です。

* Ubuntu:`ps aux | grep apache` で Apache ユーザーを探し、`groups <apache user>` でグループを探します。

通常、ユーザー名とグループ名は両方とも `www-data` です。

### ファイルシステムの所有者を web サーバーグループに追加します。

ファイルシステムの所有者を web サーバーのプライマリグループに配置するには（CentOS と Ubuntu の一般的な Apache グループ名を想定）、`root` 権限を持つユーザーとして次のコマンドを入力します。

* CentOS: `usermod -a -G apache <username>`
* Ubuntu: `usermod -a -G www-data <username>`

>[!NOTE]
>
>`-a -G` のオプションは、`apache` または `www-data` を *セカンダリ* グループとしてユーザーアカウントに追加し、ユーザーの *プライマリ* グループを保持するので重要です。 セカンダリ グループをユーザーアカウントに追加すると、共有グループのメンバーが特定のファイルにのみアクセスできるように [&#x200B; ファイルの所有権とアクセス許可を制限 &#x200B;](#set-ownership-and-permissions-for-two-users) できます。

例えば、ユーザー `magento_user` を CentOS の `apache` プライマリグループに追加するには、次のようにします。

```bash
sudo usermod -a -G apache magento_user
```

ユーザーが web サーバーグループのメンバーであることを確認するには、次のコマンドを入力します。

```bash
groups magento_user
```

次の例は、ユーザーのプライマリ（`magento`）グループとセカンダリ（`apache`）グループを示しています。

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
* [&#x200B; リポジトリのクローンを作成する（コントリビューションを行う開発者のみ） &#x200B;](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository)

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

すべてのコマンドを 1 行で入力するには、アプリケーションが `/var/www/html/magento2` にインストールされており、Web サーバーグループ名が `apache` の場合は、次のように入力します。

```bash
cd /var/www/html/magento2 && find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} + && find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} + && chown -R :apache . && chmod u+x bin/magento
```

ファイルシステムの権限が不適切に設定され、ファイルシステムの所有者が変更できない場合は、`root` の権限を持つユーザーとしてコマンドを入力できます。

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
