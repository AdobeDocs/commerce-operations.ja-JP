---
title: モジュールと拡張機能のアップグレード
description: コマンドラインインターフェイスとComposerを使用して、Adobe Commerce モジュールと拡張機能をアップグレードします。
exl-id: 017d75df-fd21-4fb4-abc9-80a35fc47d0f
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 0%
---
# モジュールと拡張機能のアップグレード

モジュールまたは拡張機能を更新またはアップグレードするには：

1. Marketplaceまたは別の拡張機能の開発者から更新されたファイルをダウンロードします。 モジュール名とバージョンをメモします。

1. 内容をAdobe Commerceのルートインストールディレクトリに書き出します。

1. モジュールにComposer パッケージが存在する場合は、次のいずれかを実行します。

   モジュール名ごとに更新：

   ```shell
   composer update vendor/module-name
   ```

   バージョンごとに更新：

   ```shell
   composer require vendor/module-name ^x.x.x
   ```

1. 次のコマンドを実行して、キャッシュをアップグレード、デプロイ、クリーニングします。

   ```shell
   bin/magento setup:upgrade --keep-generated
   ```

   ```shell
   bin/magento setup:static-content:deploy
   ```

   ```shell
   bin/magento cache:clean
   ```

## ベンダーバンドル拡張機能（VBE）

Adobeは、2.4.4ですべての[VBE](/help/upgrade/modules/upgrade.md)を削除しました。 Adobe Commerce Marketplaceでこれらの拡張機能を引き続きサポートします。

Adobe Commerce 2.4.4以降でこれらの拡張機能を引き続き使用する場合は、2.4.4にアップグレードする前に、`composer.json` ファイル _内の対応するパッケージ依存関係を更新する必要があります。_&#x200B;使用するパッケージ名とバージョンについては、ベンダーにお問い合わせください。

詳しくは、次のAdobe Commerce Marketplace リストを参照してください。

- [Amazon Pay](https://commercemarketplace.adobe.com//amzn-amazon-pay-magento-2-module.html)
- [Dotdigital](https://commercemarketplace.adobe.com//dotdigital-dotdigital-magento2-os-package.html)
- [クラルナ](https://commercemarketplace.adobe.com//klarna-m2-klarna.html)
- [頂点](https://commercemarketplace.adobe.com//vertexinc-vertex-tax-module.html)
- [ヨットポ](https://commercemarketplace.adobe.com//yotpo-module-yotpo.html)
