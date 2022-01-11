---
title: モジュールと拡張機能のアップグレード
description: コマンドラインインターフェイスと Composer を使用して、Adobe CommerceおよびMagento Open Sourceモジュールと拡張機能をアップグレードします。
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '96'
ht-degree: 0%

---


# モジュールと拡張機能のアップグレード

モジュールまたは拡張機能を更新またはアップグレードするには：

1. Marketplace または他の拡張機能の開発者から、更新したファイルをダウンロードします。 モジュールの名前とバージョンをメモしておきます。

1. コンテンツをAdobe CommerceまたはMagento Open Sourceのルートインストールディレクトリに書き出します。

1. モジュール用の Composer パッケージが存在する場合は、次のいずれかを実行します。

   モジュール名ごとに更新：

   ```bash
   composer update vendor/module-name
   ```

   バージョンごとに更新：

   ```bash
   composer require vendor/module-name ^x.x.x
   ```

1. 次のコマンドを実行して、キャッシュをアップグレード、デプロイ、クリーンアップします。

   ```bash
   bin/magento setup:upgrade --keep-generated
   ```

   ```bash
   bin/magento setup:static-content:deploy
   ```

   ```bash
   bin/magento cache:clean
   ```
