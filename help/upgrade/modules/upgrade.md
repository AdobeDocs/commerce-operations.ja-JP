---
title: アップグレードモジュールおよび拡張機能
description: コマンドラインインターフェイスと Composer を使用して、Adobe Commerce モジュールと拡張機能をアップグレードします。
exl-id: 017d75df-fd21-4fb4-abc9-80a35fc47d0f
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 0%

---

# モジュールおよび拡張機能のアップグレード

モジュールまたは拡張機能を更新またはアップグレードするには：

1. Marketplace または別の拡張機能開発者から、更新されたファイルをダウンロードします。 モジュール名とバージョンをメモします。

1. 内容をAdobe Commerce ルートインストールディレクトリに書き出します。

1. モジュール用の Composer パッケージが存在する場合は、次のいずれかを実行します。

   モジュール名ごとのアップデート：

   ```bash
   composer update vendor/module-name
   ```

   バージョンごとのアップデート：

   ```bash
   composer require vendor/module-name ^x.x.x
   ```

1. 次のコマンドを実行して、キャッシュをアップグレード、デプロイおよびクリーンアップします。

   ```bash
   bin/magento setup:upgrade --keep-generated
   ```

   ```bash
   bin/magento setup:static-content:deploy
   ```

   ```bash
   bin/magento cache:clean
   ```

## ベンダーバンドルの拡張機能（VBE）

Adobeは 2.4.4 ですべての [VBE](https://experienceleague.adobe.com/ja/docs/commerce-operations/upgrade-guide/modules/upgrade) を削除しました。ベンダーは、Adobe Commerce Marketplace でこれらの拡張機能を引き続きサポートします。

Adobe Commerce 2.4.4 以降で、これらの拡張機能を引き続き使用する場合は、`composer.json` ファイル内の対応するパッケージの依存関係を更新する必要があります _アップグレードする前に_ 2.4.4 に。使用するパッケージの名前とバージョンについては、ベンダーにお問い合わせください。

詳しくは、以下のAdobe Commerce Marketplace のリストを参照してください。

- [Amazon支払 ](https://marketplace.magento.com/amzn-amazon-pay-magento-2-module.html)
- [Dotdigital](https://marketplace.magento.com/dotdigital-dotdigital-magento2-os-package.html)
- [ クルナ ](https://marketplace.magento.com/klarna-m2-klarna.html)
- [ 頂点 ](https://marketplace.magento.com/vertexinc-vertex-tax-module.html)
- [ ヨッポ ](https://marketplace.magento.com/yotpo-module-yotpo.html)
