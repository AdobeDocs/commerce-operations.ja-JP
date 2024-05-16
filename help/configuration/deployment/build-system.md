---
title: システム設定の作成
description: Commerceをビルドシステムにデプロイする方法を説明します。
feature: Configuration, Build, Deploy
exl-id: f6daf5c6-6d12-46b0-b775-76791bacea53
source-git-commit: dcc283b901917e3681863370516771763ae87462
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# システム設定の作成

次の要件を満たすビルドシステムを 1 つ用意できます。

- すべてのCommerce コードは、開発システムおよび実稼働システムと同じリポジトリでソース管理下にあります
- 次のすべてを確認します _included_ ソース管理で、次の操作を行います。

   - `app/etc/config.php`
   - `generated` ディレクトリ（およびサブディレクトリ）
   - `pub/media` directory
   - `pub/media/wysiwyg` ディレクトリ（およびサブディレクトリ）
   - `pub/static` ディレクトリ（およびサブディレクトリ）

- 互換性のある PHP バージョンがインストールされている必要があります
- Composer がインストールされている必要があります。
- ファイル・システムの所有権と権限が設定されています（を参照）。 [開発、ビルド、実稼動システムの前提条件](../deployment/technical-details.md).
- ビルドシステムではCommerceをインストールする必要はありませんが、コードを使用できる必要があります。

>[!WARNING]
>
>データベース接続は、に既に含まれている場合は必要ありません `config.php`；を参照してください [設定のエクスポート](../cli/export-configuration.md). それ以外の場合は、データベース接続が必要です。

>[!INFO]
>
>ビルドマシンは、独自のホスト上か、インストールされているCommerce システムと同じホスト上に存在できます。

## ビルドマシンの設定

次の節では、ビルドマシンの設定方法について説明します。

### Composer のインストール

まず、Composer がすでにインストールされているかどうかをチェックします。

コマンドプロンプトで、次のいずれかのコマンドを入力します。

- `composer --help`
- `composer list --help`

コマンド ヘルプが表示された場合、Composer はすでにインストールされています。

エラーが表示された場合は、以下の手順で Composer をインストールします。

Composer をインストールするには：

1. をCommerce サーバー上の空のディレクトリに移動または作成します。

1. 次のコマンドを入力します。

   ```bash
   curl -sS https://getcomposer.org/installer | php
   ```

   ```bash
   mv composer.phar /usr/local/bin/composer
   ```

その他のインストール オプションについては、を参照してください [Composer インストール ドキュメント][composer].

### PHP のインストール

に PHP をインストールする [CentOS] または [Ubuntu].

### ビルドシステムの設定

ビルドシステムを設定するには：

1. ファイルシステムの所有者としてビルドシステムにログインするか、所有者に切り替えます。
1. ソース管理からCommerce コードを取得します。

   Git を使用する場合は、次のコマンドを使用します。

   ```bash
   git clone [-b <branch name>] <repository URL>
   ```

1. Commerceのルートディレクトリに移動して、次のように入力します。

   ```bash
   composer install
   ```

1. 依存関係が更新されるのを待ちます。
1. 所有権の設定：

   ```bash
   chown -R <Commerce file system owner name>:<web server username> .
   ```

   以下に例を挙げます。

   ```bash
   chown -R commerce-username:apache .
   ```

1. Git を使用している場合は、を開きます。 `.gitignore` テキストエディター。
1. 次の各行を `#` コメントアウトする文字：

   ```conf
   # app/etc/config.php
   # pub/media/*
   # generated/*
   # pub/media/*.*
   # pub/media/wysiwyg/*
   # pub/static/*
   ```

1. 変更をに保存します。 `.gitignore` をクリックして、テキストエディターを終了します。
1. Git を使用する場合は、次のコマンドを使用して変更をコミットします。

   ```bash
   git add .gitignore && git commit -m "Modify .gitignore for build and production"
   ```

   を参照してください。 [`.gitignore` 参照](../reference/config-reference-gitignore.md) を参照してください。

1. ビルドシステムでは、を使用する必要があります [デフォルトモード](../bootstrap/application-modes.md#default-mode) または [開発者モード](../bootstrap/application-modes.md#developer-mode):

   ```bash
   bin/magento deploy:mode:set <mode>
   ```

   `<mode>` は必須です。 次のいずれかを指定できます `default` または `developer`.

<!-- Link Definitions -->

[CentOS]: https://wiki.centos.org/HowTos/php7
[composer]: https://getcomposer.org/download/
[Ubuntu]: https://help.ubuntu.com/lts/serverguide/php.html
