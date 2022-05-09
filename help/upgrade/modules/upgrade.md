---
title: モジュールと拡張機能のアップグレード
description: コマンドラインインターフェイスと Composer を使用して、Adobe CommerceおよびMagento Open Sourceモジュールと拡張機能をアップグレードします。
source-git-commit: 28ce8cca3bb1780ee1466cc2c1b2143e923fe768
workflow-type: tm+mt
source-wordcount: '195'
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

## ベンダーバンドル拡張機能 (VBE)

Adobeがすべて削除されました [VBEs](https://devdocs.magento.com/extensions/vendor/) 2.4.4.ベンダーは、Adobe Commerce Marketplace で引き続きこれらの拡張機能をサポートします。

Adobe CommerceおよびMagento Open Source2.4.4 以降でこれらの拡張機能を引き続き使用する場合は、 `composer.json` ファイル _前_ 2.4.4 にアップグレードします。使用するパッケージ名とバージョンについては、ベンダーにお問い合わせください。

詳しくは、次のAdobe Commerce Marketplace リストを参照してください。

- [Amazon Pay](https://marketplace.magento.com/amzn-amazon-pay-magento-2-module.html)
- [Dotdigital](https://marketplace.magento.com/dotdigital-dotdigital-magento2-os-package.html)
- [クラルナ](https://marketplace.magento.com/klarna-m2-klarna.html)
- [頂点](https://marketplace.magento.com/vertexinc-vertex-tax-module.html)
- [ヨトポ](https://marketplace.magento.com/yotpo-module-yotpo.html)

