---
title: 単一マシンの導入
description: コマンドラインを使用して、実稼動サーバーにCommerceのアップデートをデプロイする方法について説明します。
feature: Configuration, Deploy
exl-id: ca73309c-7584-4506-99de-dd933651eeb6
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 1%

---

# シングルマシン導入

このトピックでは、コマンドラインを使用して実稼動サーバー上のCommerceにアップデートをデプロイする手順について説明します。 このプロセスは、いくつかのテーマとロケールがインストールされた単一のマシンで実行されているストアを担当するテクニカルユーザーに適用されます。

## 前提条件

- [Composer](../../installation/composer.md)を使用してCommerceをインストールしました。
- 更新をサーバーに直接適用しています。

>[!WARNING]
>
>このガイドは、`git clone`を使用してCommerceをインストールした場合には適用されません。
>共同制作者は、[このガイド &#x200B;](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies)を使用して、Commerce インストールを更新する必要があります。

## デプロイメントステップ

1. 実稼動サーバーに[&#x200B; ファイルシステム所有者](../../installation/prerequisites/file-system/overview.md)としてログインするか、切り替えます。

1. ディレクトリをCommerce ベースディレクトリに変更します。

   ```shell
   cd <Commerce base directory>
   ```

1. 次のコマンドを使用してメンテナンスモードを有効にします。

   ```shell
   bin/magento maintenance:enable
   ```

1. 次のコマンドパターンを使用して、Commerceまたはそのコンポーネントにアップデートを適用します。

   ```shell
   composer require-commerce <package> <version> --no-update
   ```

   **パッケージ**：更新するパッケージの名前。

   例：

   - `magento/product-community-edition`
   - `magento/product-enterprise-edition`

   **version**：更新するパッケージのターゲットバージョン。

1. Composerでコンポーネントを更新：

   ```shell
   composer update
   ```

1. データベーススキーマとデータを更新します。

   ```shell
   bin/magento setup:upgrade
   ```

1. コードをコンパイルします。

   ```shell
   bin/magento setup:di:compile
   ```

1. 静的コンテンツをデプロイ：

   ```shell
   bin/magento setup:static-content:deploy
   ```

1. キャッシュをクリーニングします。

   ```shell
   bin/magento cache:clean
   ```

1. メンテナンスモードを終了：

   ```shell
   bin/magento maintenance:disable
   ```

