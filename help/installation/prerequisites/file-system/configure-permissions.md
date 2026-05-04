---
title: ファイルの所有権と権限の設定
description: Adobe Commerceのオンプレミスインストールのファイルシステム権限を設定するには、次の手順に従います。
exl-id: 2410ee4f-978c-4b71-b3f6-0c042f9f4dc4
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '1005'
ht-degree: 0%

---

# ファイルの所有権と権限の設定

このトピックでは、Adobe Commerceをインストールする前に、web サーバーグループに対する読み取り/書き込み権限を設定する方法について説明します。 これは、コマンドラインがファイルシステムにファイルを書き込めるようにするために必要です。

使用する手順は、[共有ホスティング ](#set-permissions-for-one-user-on-shared-hosting)を使用し、1人のユーザーを持っているか、[ プライベートサーバー](#set-ownership-and-permissions-for-two-users)を使用し、2人のユーザーを持っているかによって異なります。

## 共有ホスティングで1人のユーザーの権限を設定する

この節では、アプリケーションサーバーにweb サーバーも実行するのと同じユーザーとしてログインする場合のプリインストール権限の設定方法について説明します。 このタイプの設定は、共有ホスティング環境では一般的です。

アプリケーションをインストールする前に権限を設定するには：

1. アプリケーションサーバーにログインします。
1. 共有ホスティングプロバイダーが提供するファイルマネージャーアプリケーションを使用して、書き込み権限が次のディレクトリに設定されていることを確認します。

   * `vendor` （Composerまたは圧縮アーカイブのインストール）
   * `app/etc`
   * `pub/static`
   * `var`
   * `generated`
   * その他の静的リソース

1. コマンドラインアクセスがある場合は、次のコマンドを次の順序で入力します。

   ```shell
   cd <app_root>
   ```

   ```shell
   find var generated vendor pub/static pub/media app/etc -type f -exec chmod u+w {} +
   ```

   ```shell
   find var generated vendor pub/static pub/media app/etc -type d -exec chmod u+w {} +
   ```

   ```shell
   chmod u+x bin/magento
   ```

   オプションで1行にすべてのコマンドを入力するには、アプリケーションが`/var/www/html/magento2`にインストールされていると仮定して、次のように入力します。

   ```shell
   cd /var/www/html/magento2 && find var generated vendor pub/static pub/media app/etc -type f -exec chmod u+w {} + && find var generated vendor pub/static pub/media app/etc -type d -exec chmod u+w {} + && chmod u+x bin/magento
   ```

1. まだ実行していない場合は、次のいずれかの方法でアプリケーションを取得します。

   * [Composer メタパッケージ](../../composer.md)
   * [リポジトリのクローンを作成する（開発者向け）](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository)

1. ファイルシステムの所有権と権限を設定したら、[ アプリケーションをインストール ](../../advanced.md)

>[!NOTE]
>
>アプリケーションのインストール後に権限をさらに制限するには、[umask](../../next-steps/set-umask.md)を設定できます。

## 2人のユーザーの所有権と権限を設定する

この節では、独自のサーバーまたはプライベートホスティング設定の所有権と権限を設定する方法について説明します。 この種類の設定では、通常、*はWeb サーバーユーザーとしてログインしたり、Web サーバーユーザーに切り替えたりすることはできません*。 通常、1人のユーザーとしてログインし、別のユーザーとしてweb サーバーを実行します。

2 ユーザーシステムの所有権と権限を設定するには：

次のタスクを次の順序で実行します。

* [共有グループについて](#about-the-shared-group)
* [ファイルシステムの所有者を作成し、ユーザーに強力なパスワードを付与します](#create-the-file-system-owner-and-give-the-user-a-strong-password)
* [Web サーバーユーザーのグループを検索する](#find-the-web-server-user-group)
* [Web サーバーグループにファイルシステムの所有者を配置する](#put-the-file-system-owner-in-the-web-server-group)
* [ソフトウェアを入手](#get-the-software)
* [共有グループの所有権と権限の設定](#set-ownership-and-permissions-for-the-shared-group)

### 共有グループについて

Web サーバーがファイルシステムにファイルやディレクトリを書き込み、ファイルシステム所有者が&#x200B;*所有権*&#x200B;を維持できるようにするには、両方のユーザーが同じグループに属している必要があります。 これは、両方のユーザーがファイル（管理者またはその他のweb ベースのユーティリティを使用して作成されたファイルを含む）へのアクセスを共有できるようにするために必要です。

この節では、ファイルシステム所有者を作成し、そのユーザーをweb サーバーのグループに入れる方法について説明します。 必要に応じて、既存のユーザーアカウントを使用できます。セキュリティ上の理由から、ユーザーには強力なパスワードを使用することをお勧めします。

>[!NOTE]
>
>既存のユーザーアカウントを使用する予定がある場合は、[Web サーバーユーザーグループ ](#find-the-web-server-user-group)にスキップします。

### ファイルシステムの所有者を作成し、ユーザーに強力なパスワードを付与します

この節では、ファイルシステム所有者の作成方法について説明します。 （ファイルシステム所有者は、*コマンドラインユーザー*&#x200B;の別の用語です）。

CentOSまたはUbuntuでユーザーを作成するには、`root`権限を持つユーザーとして次のコマンドを入力します。

```shell
adduser <username>
```

ユーザーにパスワードを付与するには、`root`権限を持つユーザーとして次のコマンドを入力します。

```shell
passwd <username>
```

画面の指示に従って、ユーザーのパスワードを作成します。

>[!WARNING]
>
>アプリケーションサーバーに`root`権限がない場合は、別のローカルユーザーアカウントを使用できます。 ユーザーが強力なパスワードを持っていることを確認し、[Web サーバーグループにファイルシステム所有者を配置](#step-3-put-the-file-system-owner-in-the-web-servers-group)します。

例えば、`magento_user`という名前のユーザーを作成し、そのユーザーにパスワードを付与するには、次のように入力します。

```shell
sudo adduser magento_user
```

```shell
sudo passwd magento_user
```

>[!WARNING]
>
>このユーザーを作成する目的は、セキュリティを強化することなので、[強力なパスワード ](https://en.wikipedia.org/wiki/Password_strength)を作成してください。

### Web サーバーのユーザーグループを見つける

Web サーバーユーザーのグループを見つけるには：

* CentOS:

  ```shell
  grep -E -i '^user|^group' /etc/httpd/conf/httpd.conf
  ```

  または

  ```shell
  grep -Ei '^user|^group' /etc/httpd/conf/httpd.conf
  ```

通常、ユーザー名とグループ名はどちらも`apache`です。

* Ubuntu: `ps aux | grep apache`を使用してApache ユーザーを検索し、次に`groups <apache user>`を使用してグループを検索します。

通常、ユーザー名とグループ名はどちらも`www-data`です。

### Web サーバーグループにファイルシステムの所有者を配置する

Web サーバーのプライマリグループにファイルシステム所有者を配置するには（CentOSおよびUbuntuの一般的なApache グループ名を想定）、`root`権限を持つユーザーとして次のコマンドを入力します。

* CentOS: `usermod -a -G apache <username>`
* Ubuntu: `usermod -a -G www-data <username>`

>[!NOTE]
>
>`-a -G` オプションは、`apache`または`www-data`を&#x200B;*セカンダリ* グループとしてユーザーアカウントに追加し、ユーザーの&#x200B;*プライマリ* グループを保持するため、重要です。 ユーザーアカウントにセカンダリグループを追加すると、[ ファイルの所有権と権限を制限](#set-ownership-and-permissions-for-two-users)して、共有グループのメンバーが特定のファイルのみにアクセスできるようにします。

例えば、ユーザー`magento_user`をCentOSの`apache` プライマリグループに追加するには、次の手順を実行します。

```shell
sudo usermod -a -G apache magento_user
```

ユーザーがweb サーバーグループのメンバーであることを確認するには、次のコマンドを入力します。

```shell
groups magento_user
```

次のサンプル結果は、ユーザーのプライマリ （`magento`）およびセカンダリ （`apache`） グループを示しています。

```shell
magento_user : magento_user apache
```

>[!NOTE]
>
>通常、ユーザー名とプライマリグループ名は同じです。

タスクを完了するには、web サーバーを再起動します。

* Ubuntu: `service apache2 restart`
* CentOS: `service httpd restart`

### ソフトウェアを入手

まだ実行していない場合は、次のいずれかの方法でソフトウェアを入手します。

* [Composer メタパッケージ](../../composer.md)
* [リポジトリのクローンを作成する（開発者向け）](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository)

### 共有グループの所有権と権限の設定

アプリケーションをインストールする前に、所有権と権限を設定するには：

1. ファイルシステム所有者としてアプリケーションサーバーにログインするか、ファイル所有者に切り替えます。
1. 次のコマンドを次の順序で入力します。

   ```shell
   cd <app_root>
   ```

   ```shell
   find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} +
   ```

   ```shell
   find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} +
   ```

   ```shell
   chown -R :<web server group> .
   ```

   ```shell
   chmod u+x bin/magento
   ```

オプションで1行にすべてのコマンドを入力するには、アプリケーションが`/var/www/html/magento2`にインストールされ、web サーバーグループ名が`apache`であると仮定して、次のように入力します。

```shell
cd /var/www/html/magento2 && find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} + && find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} + && chown -R :apache . && chmod u+x bin/magento
```

イベント ファイル システムの権限が正しく設定されておらず、ファイル システムの所有者が変更できない場合は、次のコマンドを`root`権限を持つユーザーとして入力できます。

```shell
cd /var/www/html/magento2 && sudo find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} + && sudo find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} + && sudo chown -R :apache . && sudo chmod u+x bin/magento
```

## ファイルシステムの所有者に切り替える

このトピックの他のタスクを実行した後、次のいずれかのコマンドを入力して、そのユーザーに切り替えます。

* Ubuntu: `su <username>`
* CentOS: `su - <username>`

以下に例を挙げます。

```shell
su magento_user
```
