---
title: 単一マシンの導入
description: コマンドラインを使用して、実稼動サーバー上に Commerce に更新をデプロイする方法を説明します。
feature: Configuration, Deploy
exl-id: ca73309c-7584-4506-99de-dd933651eeb6
source-git-commit: dcc283b901917e3681863370516771763ae87462
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 0%

---

# シングルマシンの導入

このトピックでは、コマンドラインを使用して実稼動サーバーにコマースの更新を展開する手順を説明します。 このプロセスは、一部のテーマとロケールがインストールされた 1 台のマシン上で実行されるストアを担当する技術ユーザーに適用されます。

## 前提

- Commerce をインストールしているのは [コンポーザー](../../installation/composer.md).
- サーバーに直接更新を適用しています。

>[!WARNING]
>
>このガイドは、 `git clone` Commerce をインストールします。
>貢献する開発者は、 [このガイド][install] をクリックして、コマースのインストールを更新します。

## デプロイメントの手順

1. 実稼動サーバーに、 [ファイルシステム所有者](../../installation/prerequisites/file-system/overview.md).

1. Commerce ベースディレクトリにディレクトリを変更します。

   ```bash
   cd <Commerce base directory>
   ```

1. 次のコマンドを使用して、メンテナンスモードを有効にします。

   ```bash
   bin/magento maintenance:enable
   ```

1. 次のコマンドパターンを使用して、コマースまたはコンポーネントに更新を適用します。

   ```bash
   composer require-commerce <package> <version> --no-update
   ```

   **パッケージ**:更新するパッケージの名前。

   例：

   - `magento/product-community-edition`
   - `magento/product-enterprise-edition`

   **version**:更新するパッケージの対象バージョン。

1. コンポーザーでコンポーネントを更新：

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

1. キャッシュをクリーンアップします。

   ```bash
   bin/magento cache:clean
   ```

1. メンテナンスモードを終了：

   ```bash
   bin/magento maintenance:disable
   ```

<!-- link definitions -->

[install]: https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies/
