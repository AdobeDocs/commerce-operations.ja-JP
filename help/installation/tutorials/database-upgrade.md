---
title: データベーススキーマとデータのアップグレード
description: Adobe Commerce データベーススキーマをアップグレードするには、次の手順に従います。
exl-id: bef04561-6c6b-4636-a8ab-a1ade44f5a8f
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 0%

---

# データベーススキーマとデータのアップグレード

このコマンドを使用する前に、[ アプリケーションをインストールする ](../advanced.md) 必要があります。

## データベーススキーマとデータのアップグレード

データベーススキーマまたはデータを変更するアクションを実行する場合は、ここで説明するコマンドを実行して更新する必要があります。 理由の一部を次に示します。

* コマンドラインを使用してアプリケーションをアップグレードしました
* コマンドラインを使用してコンポーネントをインストールまたは更新した。
* コマンドラインを使用してコンポーネントを有効または無効にしました

>[!NOTE]
>
>*コンポーネント* は、モジュール、テーマ、言語パックのいずれかにすることができます。コンポーネントがCommerce Marketplaceから取得されたかどうかは関係ありません。

1. アップグレードを開始します。

   ```bash
   bin/magento setup:upgrade [--keep-generated]
   ```

   ここで、`--keep-generated` は、更新されないオプションの引数です [ 静的ビューファイル ](../../configuration/cli/static-view-file-deployment.md)。 このオプション引数は、経験豊富なシステムインテグレーターが限られた状況で使用する *のみ* です。 *実稼動モード* で [ 使用する必要があ ](../../configuration/bootstrap/application-modes.md#production-mode) ます。 *開発者モード* では使用しないでください [&#128279;](../../configuration/bootstrap/application-modes.md#developer-mode)。

1. キャッシュのクリーンアップ：

   ```bash
   bin/magento cache:clean
   ```
