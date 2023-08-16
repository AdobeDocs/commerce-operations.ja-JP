---
title: ビルドシステム設定
description: コマースをビルドシステムにデプロイする方法を説明します。
feature: Configuration, Build, Deploy
exl-id: f6daf5c6-6d12-46b0-b775-76791bacea53
source-git-commit: dcc283b901917e3681863370516771763ae87462
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# システム設定の作成

以下の要件を満たすビルドシステムを 1 つ用意することができます。

- すべてのコマースコードは、開発および実稼動システムと同じリポジトリ内のソース管理下にあります
- 次のすべてを確認します。 _含む_ ソース管理：

   - `app/etc/config.php`
   - `generated` ディレクトリ（およびサブディレクトリ）
   - `pub/media` directory
   - `pub/media/wysiwyg` ディレクトリ（およびサブディレクトリ）
   - `pub/static` ディレクトリ（およびサブディレクトリ）

- 互換性のある PHP バージョンがインストールされている必要があります
- Composer をインストールしておく必要がある
- ファイル・システムの所有権と権限が設定されています。 [開発、ビルド、実稼動システムの前提条件](../deployment/technical-details.md).
- ビルドシステムに Commerce をインストールする必要はありませんが、コードを使用するにはコードが必要です。

>[!WARNING]
>
>データベース接続は、既に `config.php`を参照してください。 [設定の書き出し](../cli/export-configuration.md). それ以外の場合は、データベース接続が必要です。

>[!INFO]
>
>ビルドマシンは、それぞれのホスト上に配置することも、インストールされている Commerce システムと同じホスト上に配置することもできます。

## ビルドマシンを設定する

次のセクションでは、ビルドマシンの構成方法を説明します。

### Composer のインストール

まず、Composer が既にインストールされているかどうかを確認します。

コマンドプロンプトで、次のいずれかのコマンドを入力します。

- `composer --help`
- `composer list --help`

コマンドヘルプが表示された場合、Composer は既にインストールされています。

エラーが表示される場合は、次の手順に従って Composer をインストールします。

Composer をインストールするには：

1. コマースサーバー上に空のディレクトリを変更するか、作成します。

1. 次のコマンドを入力します。

   ```bash
   curl -sS https://getcomposer.org/installer | php
   ```

   ```bash
   mv composer.phar /usr/local/bin/composer
   ```

その他のインストールオプションについては、 [Composer のインストールドキュメント][composer].

### PHP のインストール

に PHP をインストールします。 [CentOS] または [Ubuntu].

### ビルドシステムを設定する

ビルドシステムを設定するには、次の手順に従います。

1. ビルドシステムに、ファイルシステムの所有者としてログインするか、ファイルシステムの所有者に切り替えます。
1. ソース管理からコマースコードを取得します。

   Git を使用する場合は、次のコマンドを使用します。

   ```bash
   git clone [-b <branch name>] <repository URL>
   ```

1. コマースのルートディレクトリに移動し、次のように入力します。

   ```bash
   composer install
   ```

1. 依存関係が更新されるのを待ちます。
1. 所有権を設定：

   ```bash
   chown -R <Commerce file system owner name>:<web server username> .
   ```

   以下に例を挙げます。

   ```bash
   chown -R commerce-username:apache .
   ```

1. Git を使用している場合は、 `.gitignore` をクリックします。
1. 次の各行を `#` コメントアウトする文字：

   ```conf
   # app/etc/config.php
   # pub/media/*
   # generated/*
   # pub/media/*.*
   # pub/media/wysiwyg/*
   # pub/static/*
   ```

1. 変更をに保存します。 `.gitignore` をクリックし、テキストエディタを終了します。
1. Git を使用する場合は、次のコマンドを使用して変更をコミットします。

   ```bash
   git add .gitignore && git commit -m "Modify .gitignore for build and production"
   ```

   詳しくは、 [`.gitignore` 参照](../reference/config-reference-gitignore.md) を参照してください。

1. ビルドシステムでは、 [デフォルトモード](../bootstrap/application-modes.md#default-mode) または [開発者モード](../bootstrap/application-modes.md#developer-mode):

   ```bash
   bin/magento deploy:mode:set <mode>
   ```

   `<mode>` が必要です。 次のいずれかを指定できます。 `default` または `developer`.

<!-- Link Definitions -->

[CentOS]: https://wiki.centos.org/HowTos/php7
[composer]: https://getcomposer.org/download/
[Ubuntu]: https://help.ubuntu.com/lts/serverguide/php.html
