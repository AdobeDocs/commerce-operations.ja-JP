---
title: データベーススキーマとデータのアップグレード
description: Adobe Commerce データベーススキーマをアップグレードするには、次の手順に従います。
exl-id: bef04561-6c6b-4636-a8ab-a1ade44f5a8f
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 0%

---

# データベーススキーマとデータのアップグレード

このコマンドを使用する前に、アプリケーションを[&#x200B; インストールする必要があります](../advanced.md)。

## データベーススキーマとデータのアップグレード

データベース・スキーマまたはデータを変更するアクションを実行する場合は、この節で説明するコマンドを実行して、データベース・スキーマまたはデータを更新する必要があります。 理由の一部は次のとおりです。

* コマンドラインを使用してアプリケーションをアップグレードしました
* コマンドラインを使用してコンポーネントをインストールまたは更新しました
* コマンドラインを使用してコンポーネントを有効または無効にしました

>[!NOTE]
>
>*コンポーネント*&#x200B;は、モジュール、テーマ、または言語パックにすることができます。コンポーネントがCommerce Marketplaceから来るかどうかは関係ありません。

1. アップグレードを開始します。

   ```shell
   bin/magento setup:upgrade [--keep-generated]
   ```

   ここで、`--keep-generated`は、[静的ビューファイル &#x200B;](../../configuration/cli/static-view-file-deployment.md)を更新しないオプションの引数です。 このオプションの引数は、経験豊富なシステムインテグレーターによる限られた状況で&#x200B;*only*&#x200B;を使用するためのものです。 [実稼動モード &#x200B;](../../configuration/bootstrap/application-modes.md#production-mode)では&#x200B;*のみ*&#x200B;を使用する必要があります。 *not*&#x200B;は[開発者モード &#x200B;](../../configuration/bootstrap/application-modes.md#developer-mode)で使用する必要があります。

1. キャッシュをクリーニングします。

   ```shell
   bin/magento cache:clean
   ```
