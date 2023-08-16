---
title: データベーススキーマとデータのアップグレード
description: 次の手順に従って、Adobe CommerceまたはMagento Open Sourceデータベーススキーマをアップグレードします。
exl-id: bef04561-6c6b-4636-a8ab-a1ade44f5a8f
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
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
>A *コンポーネント* は、モジュール、テーマ、または言語パックのいずれでもかまいません。コンポーネントがCommerce Marketplaceから提供されたかどうかは関係ありません。

1. アップグレードを開始します。

   ```bash
   bin/magento setup:upgrade [--keep-generated]
   ```

   ここで、 `--keep-generated` は、更新されないオプションの引数です [静的表示ファイル](../../configuration/cli/static-view-file-deployment.md). このオプションの引数は使用します。 *のみ* 経験豊富なシステムインテグレーターによる限られた状況でのみ可能です。 使用する必要があります *のみ* in [実稼動モード](../../configuration/bootstrap/application-modes.md#production-mode). 次のようにします。 *not* ～で使われる [開発者モード](../../configuration/bootstrap/application-modes.md#developer-mode).

1. キャッシュをクリーンアップします。

   ```bash
   bin/magento cache:clean
   ```
