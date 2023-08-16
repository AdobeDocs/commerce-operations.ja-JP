---
title: ファイルの所有権と権限の設定
description: 次の手順に従って、Adobe CommerceとMagento Open Sourceのオンプレミスインストールに対するファイルシステムの権限を設定します。
exl-id: 2410ee4f-978c-4b71-b3f6-0c042f9f4dc4
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1005'
ht-degree: 0%

---

# ファイルの所有権と権限の設定

このトピックでは、Adobe CommerceまたはMagento Open Sourceをインストールする前に、Web サーバーグループに読み取り/書き込み権限を設定する方法について説明します。 これは、コマンドラインがファイルをファイルシステムに書き込むために必要です。

使用する手順は、 [共有ホスティング](#set-permissions-for-one-user-on-shared-hosting) を持っているか、 [プライベートサーバー](#set-ownership-and-permissions-for-two-users) とには 2 人のユーザーがいます。

## 共有ホスティングで 1 人のユーザーに対する権限を設定する

この項では、Web サーバーも実行しているのと同じユーザーとしてアプリケーションサーバーにログインした場合に、プリインストール権限を設定する方法について説明します。 このタイプの設定は、共有ホスティング環境で一般的です。

アプリケーションをインストールする前に権限を設定するには、次の手順に従います。

1. アプリケーションサーバーにログインします。
1. 共有ホスティングプロバイダーが提供するファイルマネージャーアプリケーションを使用して、次のディレクトリに書き込み権限が設定されていることを確認します。

   * `vendor` （Composer または圧縮アーカイブのインストール）
   * `app/etc`
   * `pub/static`
   * `var`
   * `generated`
   * その他の静的リソース

1. コマンドラインアクセス権がある場合は、次のコマンドを次の順に入力します。

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

   1 行にすべてのコマンドを任意で入力するには、次のように入力します（アプリケーションがにインストールされていると仮定）。 `/var/www/html/magento2`:

   ```bash
   cd /var/www/html/magento2 && find var generated vendor pub/static pub/media app/etc -type f -exec chmod u+w {} + && find var generated vendor pub/static pub/media app/etc -type d -exec chmod u+w {} + && chmod u+x bin/magento
   ```

1. まだおこなっていない場合は、次のいずれかの方法でアプリケーションを取得します。

   * [Composer メタパッケージ](../../composer.md)
   * [リポジトリのクローン（貢献する開発者のみ）](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)

1. ファイル・システムの所有権と権限を設定した後、 [アプリケーションのインストール](../../advanced.md)

>[!NOTE]
>
>アプリケーションをインストールした後に権限をさらに制限するには、次の手順を実行します。 [umask の設定](../../next-steps/set-umask.md).

## 2 人のユーザーの所有権と権限を設定

このセクションでは、独自のサーバーまたはプライベートホスティング設定の所有権と権限を設定する方法について説明します。 このタイプの設定では、通常、 *できません* web サーバーユーザーとしてログインするか、に切り替えます。 通常、1 人のユーザーとしてログインし、別のユーザーとして Web サーバーを実行します。

2 人のユーザーを持つシステムの所有権と権限を設定するには、次の手順に従います。

次の順序でタスクを実行します。

* [共有グループについて](#about-the-shared-group)
* [ファイルシステムの所有者を作成し、ユーザーに堅牢なパスワードを与えます。](#create-the-file-system-owner-and-give-the-user-a-strong-password)
* [Web サーバーユーザーのグループを検索します。](#find-the-web-server-user-group)
* [Web サーバグループにファイルシステムの所有者を配置する](#put-the-file-system-owner-in-the-web-server-group)
* [ソフトウェアの入手](#get-the-software)
* [共有グループの所有権と権限を設定する](#set-ownership-and-permissions-for-the-shared-group)

### 共有グループについて

Web サーバーがファイル・システム内のファイルとディレクトリを書き込むと同時に、 *所有権* ファイル・システムの所有者は、両方のユーザーが同じグループに属している必要があります。 これは、両方のユーザーがファイル（管理者または他の Web ベースのユーティリティを使用して作成されたファイルを含む）へのアクセス権を共有できるようにするために必要です。

このセクションでは、ファイル・システムの所有者を作成し、そのユーザーを Web サーバのグループに配置する方法について説明します。 必要に応じて既存のユーザーアカウントを使用できます。セキュリティ上の理由から、ユーザーには強力なパスワードを使用することをお勧めします。

>[!NOTE]
>
>スキップして [Web サーバーのユーザーグループを検索します。](#find-the-web-server-user-group) 既存のユーザーアカウントを使用する場合。

### ファイルシステムの所有者を作成し、ユーザーに堅牢なパスワードを与えます。

このセクションでは、ファイルシステムの所有者を作成する方法について説明します。 ( ファイルシステムの所有者は、 *コマンドラインユーザ*.)

CentOS または Ubuntu でユーザーを作成するには、次のコマンドををを使用してユーザーとして入力します。 `root` 権限：

```bash
adduser <username>
```

ユーザーにパスワードを与えるには、次のコマンドを `root` 権限：

```bash
passwd <username>
```

画面の指示に従って、ユーザーのパスワードを作成します。

>[!WARNING]
>
>次の条件を満たしていない場合： `root` アプリケーションサーバー上での権限を持っている場合は、別のローカルユーザーアカウントを使用できます。 ユーザーに堅牢なパスワードが設定されていることを確認し、次の手順に進みます。 [Web サーバグループにファイルシステムの所有者を配置する](#step-3-put-the-file-system-owner-in-the-web-servers-group).

例えば、次の名前のユーザーを作成するには、次のようにします。 `magento_user` ユーザーにパスワードを入力するには、次のように入力します。

```bash
sudo adduser magento_user
```

```bash
sudo passwd magento_user
```

>[!WARNING]
>
>このユーザーを作成する際は、セキュリティを強化する必要があるので、必ず [堅牢なパスワード](https://en.wikipedia.org/wiki/Password_strength).

### Web サーバーのユーザーグループを検索します。

Web サーバーユーザーのグループを検索するには、次の手順に従います。

* CentOS:

  ```bash
  grep -E -i '^user|^group' /etc/httpd/conf/httpd.conf
  ```

  または

  ```bash
  grep -Ei '^user|^group' /etc/httpd/conf/httpd.conf
  ```

通常、ユーザー名とグループ名の両方が `apache`.

* Ubuntu: `ps aux | grep apache` Apache ユーザーを検索し、 `groups <apache user>` をクリックしてグループを検索します。

通常、ユーザー名とグループ名は両方ともです `www-data`.

### Web サーバグループにファイルシステムの所有者を配置する

Web サーバーのプライマリグループにファイルシステム所有者を配置するには（CentOS と Ubuntu の一般的な Apache グループ名を想定）、次のコマンドをユーザーとして入力します。 `root` 権限：

* CentOS: `usermod -a -G apache <username>`
* Ubuntu: `usermod -a -G www-data <username>`

>[!NOTE]
>
>The `-a -G` オプションは、 `apache` または `www-data` as a *セカンダリ* グループをユーザーアカウントに割り当て、ユーザーの *プライマリ* グループ化します。 セカンダリグループをユーザーアカウントに追加すると、 [ファイルの所有権と権限を制限](#set-ownership-and-permissions-for-two-users) 共有グループのメンバーが特定のファイルにのみアクセスできるようにする。

例えば、次のユーザーを追加します。 `magento_user` から `apache` CentOS のプライマリグループ：

```bash
sudo usermod -a -G apache magento_user
```

ユーザーが Web サーバーグループのメンバーであることを確認するには、次のコマンドを入力します。

```bash
groups magento_user
```

以下のサンプル結果は、ユーザーのプライマリ (`magento`) およびセカンダリ (`apache`) グループに関連付けられています。

```bash
magento_user : magento_user apache
```

>[!NOTE]
>
>通常、ユーザー名とプライマリグループ名は同じです。

タスクを完了するには、Web サーバーを再起動します。

* Ubuntu: `service apache2 restart`
* CentOS: `service httpd restart`

### ソフトウェアの入手

まだおこなっていない場合は、次のいずれかの方法でソフトウェアを入手します。

* [Composer メタパッケージ](../../composer.md)
* [リポジトリのクローン（貢献する開発者のみ）](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)

### 共有グループの所有権と権限を設定する

アプリケーションをインストールする前に所有権と権限を設定するには、次の手順に従います。

1. アプリケーションサーバーに、ファイルシステムの所有者としてログインするか、ファイルシステムの所有者に切り替えます。
1. 次のコマンドを、次の順序で入力します。

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

1 行にすべてのコマンドを任意で入力するには、次のように入力します（アプリケーションがにインストールされていると仮定）。 `/var/www/html/magento2` Web サーバーのグループ名は、 `apache`:

```bash
cd /var/www/html/magento2 && find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} + && find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} + && chown -R :apache . && chmod u+x bin/magento
```

イベントファイルシステムの権限が適切に設定されておらず、ファイルシステムの所有者が変更できない場合は、を使用してコマンドをユーザーとして入力できます。 `root` 権限：

```bash
cd /var/www/html/magento2 && sudo find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} + && sudo find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} + && sudo chown -R :apache . && sudo chmod u+x bin/magento
```

## ファイルシステムの所有者に切り替え

このトピックの他のタスクを実行した後、次のいずれかのコマンドを入力して、そのユーザーに切り替えます。

* Ubuntu: `su <username>`
* CentOS: `su - <username>`

以下に例を挙げます。

```bash
su magento_user
```
