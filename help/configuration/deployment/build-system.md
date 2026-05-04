---
title: ビルドシステム設定
description: ソース管理、生成アセット、静的コンテンツ要件を使用して、Adobe Commerce デプロイメント用のビルドシステムを設定する方法について説明します。
feature: Configuration, Build, Deploy
exl-id: f6daf5c6-6d12-46b0-b775-76791bacea53
source-git-commit: 41b8d77793f1c24f08ff7e6a2d35826a62477534
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# システム設定の構築

次の要件を満たすビルドシステムを1つ用意できます。

- すべてのCommerce コードは、開発および実稼動システムと同じリポジトリ内のソース管理の下にあります
- ソース管理に&#x200B;_インクルード_&#x200B;が含まれていることを確認してください。

   - `app/etc/config.php`
   - `generated` ディレクトリ （およびサブディレクトリ）
   - `pub/media` ディレクトリ
   - `pub/media/wysiwyg` ディレクトリ （およびサブディレクトリ）
   - `pub/static` ディレクトリ （およびサブディレクトリ）

- 互換性のあるPHP バージョンがインストールされている必要があります
- Composerがインストールされている必要があります
- このファイル システムには、[開発、ビルド、および実稼動システムの前提条件](../deployment/technical-details.md)で説明されているように、ファイル システムの所有権と権限が設定されています。
- ビルドシステムはCommerceをインストールする必要はありませんが、コードを利用できる必要があります。

>[!WARNING]
>
>データベース接続は、既に`config.php`に含まれている場合は必要ありません。[設定の書き出し](../cli/export-configuration.md)を参照してください。 それ以外の場合は、データベース接続が必要です。

>[!INFO]
>
>ビルドマシンは、独自のホスト上に存在するか、インストールされているCommerce システムと同じホスト上に存在する可能性があります。

## ビルドマシンの設定

次の節では、ビルドマシンの設定方法について説明します。

### Composerのインストール

まず、Composerが既にインストールされているかどうかを確認します。

コマンドプロンプトで、次のいずれかのコマンドを入力します。

- `composer --help`
- `composer list --help`

コマンドヘルプが表示された場合は、Composerが既にインストールされています。

エラーが表示された場合は、次の手順に従ってComposerをインストールします。

Composerをインストールするには：

1. Commerce サーバー上の空のディレクトリに移動するか、空のディレクトリを作成します。

1. 次のコマンドを入力します。

   ```shell
   curl -sS https://getcomposer.org/installer | php
   ```

   ```shell
   mv composer.phar /usr/local/bin/composer
   ```

その他のインストールオプションについては、[Composer インストールドキュメント ](https://getcomposer.org/download/)を参照してください。

### PHPのインストール

[CentOS](https://wiki.centos.org/HowTos/php7)または[Ubuntu](https://help.ubuntu.com/lts/serverguide/php.html)にPHPをインストールします。

### ビルドシステムの設定

ビルドシステムを設定するには：

1. ビルドシステムにファイルシステム所有者としてログインするか、ファイルシステム所有者に切り替えます。
1. ソースコントロールからCommerce コードを取得します。

   Gitを使用する場合は、次のコマンドを使用します。

   ```shell
   git clone [-b <branch name>] <repository URL>
   ```

1. Commerceのルートディレクトリに移動し、次のように入力します。

   ```shell
   composer install
   ```

1. 依存関係が更新されるのを待ちます。
1. 所有権の設定：

   ```shell
   chown -R <Commerce file system owner name>:<web server username> .
   ```

   以下に例を挙げます。

   ```shell
   chown -R commerce-username:apache .
   ```

1. Gitを使用している場合は、テキストエディターで`.gitignore`を開きます。
1. 次の各行を`#`文字で開始して、コメントアウトします。

   ```conf
   # app/etc/config.php
   # pub/media/*
   # generated/*
   # pub/media/*.*
   # pub/media/wysiwyg/*
   # pub/static/*
   ```

1. 変更を`.gitignore`に保存して、テキストエディターを終了します。
1. Gitを使用する場合は、次のコマンドを使用して変更をコミットします。

   ```shell
   git add .gitignore && git commit -m "Modify .gitignore for build and production"
   ```

   詳しくは、[`.gitignore` reference](../reference/config-reference-gitignore.md)を参照してください。

1. ビルドシステムでは、[ デフォルトモード ](../bootstrap/application-modes.md#default-mode)または[開発者モード ](../bootstrap/application-modes.md#developer-mode)を使用する必要があります。

   ```shell
   bin/magento deploy:mode:set <mode>
   ```

   `<mode>`が必要です。 `default`または`developer`を指定できます。

