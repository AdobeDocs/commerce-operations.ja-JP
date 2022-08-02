---
title: サポートユーティリティを実行する
description: 組み込みのサポートユーティリティを使用して Commerce プロジェクトをトラブルシューティングします。
source-git-commit: 2c12c6ea6e7b6ffeb07bbda17ded34e39de6656a
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 0%

---


# サポートユーティリティを実行する

{{ee-only}}

{{file-system-owner}}

Adobe Commerce Support ユーティリティ ( [データコレクター](https://docs.magento.com/user-guide/system/support-data-collector.html) — ユーザーは、アドビのサポートチームが使用できるシステムに関するトラブルシューティング情報を収集できます。

Adobe Commerceは、これらのバックアップを使用します。 _ダンプ_&#x200B;を使用して、コードへのアクセスを必要とする問題を分析します。 一般的なシナリオを次に示します。

1. コマースストアに問題が発生しています。Adobe Commerceサポートにお問い合わせください。
1. サポートでは、コードやデータベースを参照して問題を再現する必要があると判断します。
1. コードを `.tar.gz` ファイル。

   このバックアップでは、メディアファイルが除外され、プロセスの速度を上げ、ファイルのサイズを大幅に小さくできます。

1. データベースを `.tar.gz` ファイル。

   デフォルトでは、バックアップを作成する際に機密データがハッシュ化されます。

1. バックアップをファイル共有サービスにアップロードします。
1. サポートは、開発環境や実稼動環境に影響を与えることなく、問題を分析します。

ユーティリティの完了には数分かかる場合があります。

## コードバックアップの作成

このコマンドは、コードをバックアップし、で圧縮します。 `tar.gz` 形式

{{tip-backup-command}}

コマンドオプション：

```bash
bin/magento support:backup:code [--name=<file name>] [-o|--output=<path>] [-l|--logs]
```

ここで、

- **`--name`** ダンプファイル名を指定します（オプション）。 このパラメータを省略した場合、ダンプファイルは時刻と日付のスタンプが付きます。
- **`-o|--output=<path>`** は、バックアップを保存するファイルシステムの絶対パスです（必須）。
- **`-l|--logs`** には、ログファイルが含まれます（オプション）。

例えば、次の名前のコードバックアップを作成するには、次のようにします。 `/var/www/html/magento2/var/log/mycodebackup.tar.gz`:

```bash
bin/magento support:backup:code --name mycodebackup -o /var/www/html/magento2/var/log
```

コマンドが完了したら、Adobe Commerce Support にコードのバックアップを提供します。

## データベースバックアップの作成

このコマンドは、Commerce データベースをバックアップし、圧縮します。 `tar.gz` 形式

{{tip-backup-command}}

コマンドオプション：

```bash
bin/magento support:backup:db [--name=<name>] [-o|--output=<path>] [-l|--logs] [-i|--ignore-sanitize]
```

ここで、

- **`--name`** ダンプファイル名を指定します（オプション）。 このパラメータを省略した場合、ダンプファイルは時刻と日付のスタンプが付きます。
- **`-o|--output=<path>` は、バックアップを保存するファイルシステムの絶対パスです（必須）。
- **`-l|--logs`** には、ログファイルが含まれます（オプション）。
- **`-i|--ignore-sanitize`** は、データが保持されていることを意味します。バックアップを作成する際に、データベースに保存されている機密データをハッシュ化する場合は、このフラグを省略します（オプション）。

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

コマンドが完了したら、データベースのバックアップをAdobe Commerce Support に提供します。

## トラブルシューティング：ユーティリティとパスを表示

データコレクターとコマンドラインで必要なユーティリティへのパスを表示するコマンドを提供します。 例えば、以下のようなエラーが管理者やコマンドラインに表示される場合に、これらのコマンドを使用できます。

```terminal
Utility lsof not found
```

次のコマンドを、次の図の順に実行して、サポートユーティリティとデータコレクターで使用されるアプリケーションへのパスを表示します。

1. Commerce のインストールディレクトリに移動します。

   例：`cd /var/www/magento2`

   >[!INFO]
   >
   >コマンドは正しく実行されます _のみ_ をインストールディレクトリから削除します。

1. `bin/magento support:utility:paths` 作成 `<magento_root>/var/support/Paths.php`：ユーティリティで使用されるすべてのアプリケーションへのパスをリストします。
1. `bin/magento support:utility:check` ファイル・システムのパスを表示します。

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

ツールの実行に関する問題を解決するには、これらのアプリケーションがインストールされ、Web サーバーのユーザーの `$PATH` 環境変数。
