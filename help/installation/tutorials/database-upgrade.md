---
title: データベーススキーマとデータのアップグレード
description: 次の手順に従って、Adobe CommerceまたはMagento Open Sourceデータベーススキーマをアップグレードします。
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 0%

---


# データベーススキーマとデータのアップグレード

このコマンドを使用する前に、 [アプリケーションのインストール](../advanced.md).

## データベーススキーマとデータのアップグレード

データベースのスキーマまたはデータを変更するアクションを実行する場合は、この節で説明するコマンドを実行して更新する必要があります。 理由の一部を次に示します。

* コマンドラインを使用してアプリケーションをアップグレードしました
* コマンドラインを使用してコンポーネントをインストールまたは更新した
* コマンドラインを使用してコンポーネントを有効または無効にした

>[!NOTE]
>
>A *コンポーネント* は、モジュール、テーマ、または言語パックです。コンポーネントがCommerce Marketplaceから取得されたかどうかは関係ありません。

1. アップグレードを開始します。

   ```bash
   bin/magento setup:upgrade [--keep-generated]
   ```

   ここで、 `--keep-generated` は、更新されないオプションの引数です [静的表示ファイル](../../configuration/cli/static-view-file-deployment.md). このオプションの引数は使用します *のみ* 経験豊富なシステムインテグレーターによる限られた状況でのみ。 使用する必要があります *のみ* in [実稼動モード](../../configuration/bootstrap/application-modes.md#production-mode). それは *not* ～で使われる [開発者モード](../../configuration/bootstrap/application-modes.md#developer-mode).

1. キャッシュをクリーンアップします。

   ```bash
   bin/magento cache:clean
   ```
