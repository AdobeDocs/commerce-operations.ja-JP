---
title: 単一マシンの導入
description: コマンドラインを使用して実稼動サーバーにCommerceのアップデートをデプロイする方法を説明します。
feature: Configuration, Deploy
exl-id: ca73309c-7584-4506-99de-dd933651eeb6
source-git-commit: 84a20012a81278cc95587ec14281b05330261687
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 1%

---

# 単一マシンの導入

このトピックでは、コマンドラインを使用して実稼動サーバーにCommerceのアップデートをデプロイする手順を説明します。 このプロセスは、一部のテーマとロケールがインストールされた 1 台のマシン上でストアを実行する技術ユーザーに適用されます。

## 前提

- [Composer](../../installation/composer.md) を使用してCommerceをインストールしている。
- 更新をサーバーに直接適用しています。

>[!WARNING]
>
>このガイドは、`git clone` を使用してCommerceをインストールした場合には適用されません。
>投稿する開発者は、[ このガイド ][install] を使用してCommerceのインストールを更新する必要があります。

## デプロイメント手順

1. [&#x200B; ファイルシステムの所有者 &#x200B;](../../installation/prerequisites/file-system/overview.md) として実稼動サーバーにログインするか、に切り替えます。

1. ディレクトリをCommerceのベースディレクトリに変更します。

   ```bash
   cd <Commerce base directory>
   ```

1. 次のコマンドを使用して、メンテナンスモードを有効にします。

   ```bash
   bin/magento maintenance:enable
   ```

1. 次のコマンドパターンを使用して、Commerceまたはそのコンポーネントに更新を適用します。

   ```bash
   composer require-commerce <package> <version> --no-update
   ```

   **package**：更新するパッケージの名前。

   例：

   - `magento/product-community-edition`
   - `magento/product-enterprise-edition`

   **version**：更新するパッケージのターゲットバージョン。

1. Composer によるコンポーネントの更新：

   ```bash
   composer update
   ```

1. データベーススキーマとデータを更新します。

   ```bash
   bin/magento setup:upgrade
   ```

1. コードをコンパイルします。

   ```bash
   bin/magento setup:di:compile
   ```

1. 静的コンテンツのデプロイ：

   ```bash
   bin/magento setup:static-content:deploy
   ```

1. キャッシュのクリーンアップ：

   ```bash
   bin/magento cache:clean
   ```

1. メンテナンスモードを終了します。

   ```bash
   bin/magento maintenance:disable
   ```

<!-- link definitions -->

[install]: https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies
