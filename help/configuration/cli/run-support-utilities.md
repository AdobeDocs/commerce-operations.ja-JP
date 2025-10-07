---
title: サポートユーティリティを実行します
description: サポートユーティリティを実行してAdobe Commerce プロジェクトのトラブルシューティングを行う方法について説明します。 組み込みの診断ツールとサポートツールを確認します。
exl-id: 021b795f-e00d-43b5-9cbb-5b57a4795be7
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '470'
ht-degree: 0%

---

# サポートユーティリティを実行します

{{ee-only}}

{{file-system-owner}}

Adobe Commerce サポートユーティリティ（[&#x200B; データコレクター &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/support#data-collector) とも呼ばれます）を使用すると、アドビのサポートチームが使用できる、お使いのシステムに関するトラブルシューティング情報を収集できます。

Adobe Commerceは、これらのバックアップを使用し（「_ダンプ_ とも呼ばれます）、コードへのアクセスが必要な問題を分析します。 一般的なシナリオを次に示します。

1. Commerce ストアに問題があり、Adobe Commerce サポートにお問い合わせください。
1. サポートは、問題を再現するためにコードまたはデータベースを確認する必要があると判断します。
1. コードを `.tar.gz` ファイルにバックアップします。

   このバックアップは、プロセスを高速化し、ファイルのサイズを大幅に小さくするために、メディアファイルを除外します（_E）。

1. データベースを `.tar.gz` ファイルにバックアップします。

   デフォルトでは、バックアップの実行時に機密データがハッシュ化されます。

1. バックアップをファイル共有サービスにアップロードします。
1. サポートは、開発環境や実稼動環境に影響を与えることなく、問題を分析します。

ユーティリティが完了するまでに数分かかる場合があります。

## コードバックアップの作成

このコマンドは、コードをバックアップし、`tar.gz` 形式で圧縮します。

{{tip-backup-command}}

コマンドオプション：

```bash
bin/magento support:backup:code [--name=<file name>] [-o|--output=<path>] [-l|--logs]
```

ここで、

- **`--name`** ダンプファイル名を指定します（オプション）。 このパラメーターを省略した場合、ダンプファイルには時刻と日付のスタンプが付けられます。
- **`-o|--output=<path>`** は、バックアップを保存するファイルシステムの絶対パスです（必須）。
- **`-l|--logs`** にはログファイルが含まれます（オプション）。

例えば、`/var/www/html/magento2/var/log/mycodebackup.tar.gz` という名前のコードバックアップを作成するには、次のように指定します。

```bash
bin/magento support:backup:code --name mycodebackup -o /var/www/html/magento2/var/log
```

コマンドが完了したら、Adobe Commerce サポートへのコードバックアップを提供します。

## データベースバックアップの作成

このコマンドは、Commerce データベースをバックアップし、`tar.gz` フォーマットで圧縮します。

{{tip-backup-command}}

コマンドオプション：

```bash
bin/magento support:backup:db [--name=<name>] [-o|--output=<path>] [-l|--logs] [-i|--ignore-sanitize]
```

ここで、

- **`--name`** ダンプファイル名を指定します（オプション）。 このパラメーターを省略した場合、ダンプファイルには時刻と日付のスタンプが付けられます。
- **`-o|--output=<path>` は、バックアップを保存するファイルシステムの絶対パスです（必須）。
- **`-l|--logs`** にはログファイルが含まれます（オプション）。
- **`-i|--ignore-sanitize`** れは、データが保持されることを意味します。バックアップの作成時に、データベースに保存されている機密データをハッシュ化するフラグを省略します（オプション）。

機密データには、次のデータベーステーブルからの顧客情報が含まれます。

```
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

```
Utility lsof not found
```

次のコマンドを表示された順序で実行して、サポート ユーティリティおよびデータ コレクタで使用されるアプリケーションへのパスを表示します。

1. Commerce インストールディレクトリに移動します。

   例：`cd /var/www/magento2`

   >[!INFO]
   >
   >コマンドは、インストールディレクトリから正しく _のみ_ 実行されます。

1. `bin/magento support:utility:paths` は、ユーティリティが使用するすべてのアプリケーションへのパスをリストする `<magento_root>/var/support/Paths.php` を作成します。
1. ファイルシステムのパスが `bin/magento support:utility:check` に表示されます。

次に例を示します。

```
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

ツールの実行に関する問題を解決するには、これらのアプリケーションがインストールされ、web サーバーユーザーの `$PATH` 環境変数に設定されていることを確認します。
