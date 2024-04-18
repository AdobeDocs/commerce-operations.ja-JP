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

このコマンドを使用する前に、次の操作を行う必要があります [アプリケーションのインストール](../advanced.md).

## データベーススキーマとデータのアップグレード

データベーススキーマまたはデータを変更するアクションを実行する場合は、ここで説明するコマンドを実行して更新する必要があります。 理由の一部を次に示します。

* コマンドラインを使用してアプリケーションをアップグレードしました
* コマンドラインを使用してコンポーネントをインストールまたは更新した。
* コマンドラインを使用してコンポーネントを有効または無効にしました

>[!NOTE]
>
>A *component* モジュール、テーマ、言語パックのいずれかを指定できます。コンポーネントがCommerce Marketplaceから取得されるかどうかは関係ありません。

1. アップグレードを開始します。

   ```bash
   bin/magento setup:upgrade [--keep-generated]
   ```

   ここで、 `--keep-generated` は、更新されないオプションの引数です [静的ビューファイル](../../configuration/cli/static-view-file-deployment.md). このオプションの引数は次の目的で使用されます *のみ* 限られた環境の中で、経験豊富なシステムインテグレーターによる検証。 使用する必要があります *のみ* 。対象： [実稼動モード](../../configuration/bootstrap/application-modes.md#production-mode). これは、 *ではない* 使用される [開発者モード](../../configuration/bootstrap/application-modes.md#developer-mode).

1. キャッシュのクリーンアップ：

   ```bash
   bin/magento cache:clean
   ```
