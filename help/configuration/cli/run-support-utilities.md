---
title: サポートユーティリティの実行
description: サポートユーティリティを実行して、Adobe Commerce プロジェクトのトラブルシューティングを行う方法について説明します。 組み込みの診断ツールとサポートツールをご紹介します。
exl-id: 021b795f-e00d-43b5-9cbb-5b57a4795be7
source-git-commit: 319f3232d1ba5f5ed7cdd10ce85b9d7ffbeec89a
workflow-type: tm+mt
source-wordcount: '484'
ht-degree: 0%

---

# サポートユーティリティの実行

{{ee-only}}

{{file-system-owner}}

Adobe Commerce サポートユーティリティ（[Data Collector](https://experienceleague.adobe.com/ja/docs/commerce-admin/systems/tools/support#data-collector)とも呼ばれます）を使用すると、お客様のシステムに関するトラブルシューティング情報を収集できます。この情報は、サポートチームで使用できます。

Adobe Commerceでは、コードへのアクセスが必要な問題を分析するために、これらのバックアップ（_ダンプ_&#x200B;とも呼ばれます）を使用します。 一般的なシナリオは次のとおりです。

1. Commerce ストアに問題が発生しており、Adobe Commerce サポートにお問い合わせください。
1. サポートは、問題を再現するためにコードまたはデータベースを確認する必要があると判断します。
1. コードを`.tar.gz` ファイルにバックアップします。

   このバックアップは、メディアファイルを除外して、プロセスを高速化し、ファイルを大幅に小さくします。

1. データベースを`.tar.gz` ファイルにバックアップします。

   デフォルトでは、機密データはバックアップ時にハッシュ化されます。

1. バックアップをファイル共有サービスにアップロードします。
1. サポートは、開発や実稼動環境に影響を与えることなく、問題を分析します。

ユーティリティは完了するのに数分かかることがあります。

## コードバックアップの作成

このコマンドは、コードをバックアップし、`tar.gz`形式で圧縮します。

{{tip-backup-command}}

コマンドオプション：

```shell
bin/magento support:backup:code [--name=<file name>] [-o|--output=<path>] [-l|--logs]
```

どこで：

- **`--name`**&#x200B;は、ダンプファイル名を指定します（オプション）。 このパラメーターを省略すると、ダンプファイルは時刻と日付がスタンプされます。
- **`-o|--output=<path>`**&#x200B;は、バックアップを保存するための絶対ファイル システム パスです（必須）。
- **`-l|--logs`**&#x200B;にはログファイルが含まれています（オプション）。

例えば、`/var/www/html/magento2/var/log/mycodebackup.tar.gz`という名前のコードバックアップを作成するには：

```shell
bin/magento support:backup:code --name mycodebackup -o /var/www/html/magento2/var/log
```

コマンドが完了したら、コードのバックアップをAdobe Commerce サポートに提供します。

## データベースのバックアップの作成

このコマンドは、Commerce データベースをバックアップし、`tar.gz`形式で圧縮します。

{{tip-backup-command}}

コマンドオプション：

```shell
bin/magento support:backup:db [--name=<name>] [-o|--output=<path>] [-l|--logs] [-i|--ignore-sanitize]
```

どこで：

- **`--name`**&#x200B;は、ダンプファイル名を指定します（オプション）。 このパラメーターを省略すると、ダンプファイルは時刻と日付がスタンプされます。
- **`-o|--output=<path>`は、バックアップを保存するための絶対ファイルシステムパスです（必須）。
- **`-l|--logs`**&#x200B;にはログファイルが含まれています（オプション）。
- **`-i|--ignore-sanitize`**&#x200B;は、データが保持されることを意味します。バックアップの作成時に、データベースに保存されている機密データをハッシュするフラグを省略します（オプション）。

機密データには、次のデータベーステーブルからの顧客情報が含まれます。

```text
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

コマンドが完了したら、データベースのバックアップをAdobe Commerce サポートに提供します。

## トラブルシューティング：表示ユーティリティとパス

データコレクターとコマンドラインで必要なユーティリティへのパスを表示するコマンドを提供します。 例えば、次のようなエラーが管理者またはコマンドラインに表示される場合は、これらのコマンドを使用できます。

```text
Utility lsof not found
```

次のコマンドを順に実行して、サポートユーティリティとデータコレクターで使用されるアプリケーションへのパスを表示します。

1. Commerceのインストールディレクトリに移動します。

   例：`cd /var/www/magento2`

   >[!INFO]
   >
   >インストールディレクトリから&#x200B;_only_ コマンドが正しく実行されます。

1. `bin/magento support:utility:paths`は`<magento_root>/var/support/Paths.php`を作成し、ユーティリティで使用されるすべてのアプリケーションへのパスを一覧表示します。
1. `bin/magento support:utility:check`はファイルシステムのパスを表示します。

サンプルは次のとおりです。

```text
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

ツールの実行に関する問題を解決するには、これらのアプリケーションがインストールされ、web サーバーユーザーの`$PATH`環境変数にあることを確認してください。
