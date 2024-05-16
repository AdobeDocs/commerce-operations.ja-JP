---
title: サポートユーティリティを実行します
description: 組み込みサポートユーティリティを使用してCommerce プロジェクトのトラブルシューティングを行います。
exl-id: 021b795f-e00d-43b5-9cbb-5b57a4795be7
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 0%

---

# サポートユーティリティを実行します

{{ee-only}}

{{file-system-owner}}

Adobe Commerce サポートユーティリティ（別名） [データ コレクタ](https://docs.magento.com/user-guide/system/support-data-collector.html)- ユーザーが、サポートチームが使用できる、システムに関するトラブルシューティング情報を収集できるようにします。

Adobe Commerceでは、次のバックアップを使用します _ダンプ_&#x200B;コードへのアクセスが必要な問題を分析します。 一般的なシナリオを次に示します。

1. Commerce ストアに問題があり、Adobe Commerce サポートにお問い合わせください。
1. サポートは、問題を再現するためにコードまたはデータベースを確認する必要があると判断します。
1. コードをにバックアップします `.tar.gz` ファイル。

   このバックアップは、プロセスを高速化し、ファイルのサイズを大幅に小さくするために、メディアファイルを除外します（_E）。

1. データベースをにバックアップしました `.tar.gz` ファイル。

   デフォルトでは、バックアップの実行時に機密データがハッシュ化されます。

1. バックアップをファイル共有サービスにアップロードします。
1. サポートは、開発環境や実稼動環境に影響を与えることなく、問題を分析します。

ユーティリティが完了するまでに数分かかる場合があります。

## コードバックアップの作成

このコマンドは、コードをバックアップして次の形式で圧縮します `tar.gz` 形式。

{{tip-backup-command}}

コマンドオプション：

```bash
bin/magento support:backup:code [--name=<file name>] [-o|--output=<path>] [-l|--logs]
```

ここで、

- **`--name`** ダンプファイル名を指定します（オプション）。 このパラメーターを省略した場合、ダンプファイルには時刻と日付のスタンプが付けられます。
- **`-o|--output=<path>`** は、バックアップを保存するファイルシステムの絶対パスです（必須）。
- **`-l|--logs`** ログファイルを含める（オプション）。

例えば、という名前のコードバックアップを作成できます。 `/var/www/html/magento2/var/log/mycodebackup.tar.gz`:

```bash
bin/magento support:backup:code --name mycodebackup -o /var/www/html/magento2/var/log
```

コマンドが完了したら、Adobe Commerce サポートへのコードバックアップを提供します。

## データベースバックアップの作成

このコマンドは、Commerce データベースをバックアップして圧縮します。 `tar.gz` 形式。

{{tip-backup-command}}

コマンドオプション：

```bash
bin/magento support:backup:db [--name=<name>] [-o|--output=<path>] [-l|--logs] [-i|--ignore-sanitize]
```

ここで、

- **`--name`** ダンプファイル名を指定します（オプション）。 このパラメーターを省略した場合、ダンプファイルには時刻と日付のスタンプが付けられます。
- **`-o|--output=<path>` は、バックアップを保存するファイルシステムの絶対パスです（必須）。
- **`-l|--logs`** ログファイルを含める（オプション）。
- **`-i|--ignore-sanitize`** は、データが保持されることを意味します。バックアップの作成時に、データベースに保存されている機密データをハッシュ化するフラグを省略します（オプション）。

機密データには、次のデータベーステーブルからの顧客情報が含まれます。

```terminal
'customer_entity',
'customer_entity_varchar',
'customer_address_entity',
'customer_address_entity_varchar',
'customer_grid_flat',
'quote',
'quote_address',
'sales_order',
'sales_order_address',
'sales_order_grid'
```

コマンドが完了したら、Adobe Commerce サポートにデータベースバックアップを提供します。

## トラブルシューティング：表示ユーティリティとパス

データ コレクタおよびコマンド ラインに必要なユーティリティへのパスを表示するコマンドを提供します。 これらのコマンドは、例えば、次のようなエラーが管理者またはコマンドラインに表示される場合に使用できます。

```terminal
Utility lsof not found
```

次のコマンドを表示された順序で実行して、サポート ユーティリティおよびデータ コレクタで使用されるアプリケーションへのパスを表示します。

1. Commerce インストールディレクトリに移動します。

   例：`cd /var/www/magento2`

   >[!INFO]
   >
   >コマンドは正しく実行されます _のみ_ インストールディレクトリから。

1. `bin/magento support:utility:paths` を作成 `<magento_root>/var/support/Paths.php`：ユーティリティで使用されるすべてのアプリケーションへのパスが一覧表示されます。
1. `bin/magento support:utility:check` ファイル・システムのパスが表示されます。

次に例を示します。

```terminal
   gzip => /bin/gzip
   lsof => /usr/sbin/lsof
   mysqldump => /usr/bin/mysqldump
   nice => /bin/nice
   php => /usr/bin/php
   tar => /bin/tar
   sed => /bin/sed
   bash => /bin/bash
   mysql => /usr/bin/mysql
```

ツールの実行に関する問題を解決するには、これらのアプリケーションがインストールされ、web サーバーユーザーにあることを確認します。 `$PATH` 環境変数。
