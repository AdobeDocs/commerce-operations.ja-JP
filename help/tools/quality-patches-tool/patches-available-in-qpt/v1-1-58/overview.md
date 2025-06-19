---
title: 概要： [!DNL Quality Patches Tool]  （QPT） v1.1.58
description: ここでは、 [!DNL Quality Patches Tool]  （QPT） v1.1.58 で使用可能なパッチによって修正された問題について詳しく説明します。
feature: Tools and External Services
role: Admin, Developer
exl-id: 61bf8b82-f897-41f6-8524-5aa74c6440f1
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 0%

---

# 概要：[!DNL Quality Patches Tool] （QPT） v1.1.58

このサブセクションでは、[!DNL Quality Patches Tool] （QPT） v1.1.58 で使用可能なパッチによって修正された問題について詳しく説明します。

QPT v1.1.58 には、次のパッチが含まれています。

1. **ACSD-48570**:**URL にストアコードを追加** が *有効* になっている場合に、パスワードリセットリンクの [!UICONTROL Admin] をクリックしてもパスワードリセットのページにアクセスできず、以前はログインページまたは 404 ページが表示されていた問題を修正しました。
1. **ACSD-62118**：発注方法を使用して注文を行ったときに、`sales_order_tax_item` テーブルが完全 [!DNL B2B] 更新されない問題を修正しました。
1. **ACSD-63067**：すべての製品数量が誤ってハイライト表示され、1 つの数量のみが間違っている場合に、グループ化された製品のすべての製品に関して *[!DNL Please specify the quantity of product(s).]* というメッセージが表示される問題を修正しました。
1. **ACSD-63090**：商品がカートに追加された後に削除されると、買い物かごの商品が削除される問題を修正しました。
1. **ACSD-63182**：重複したバンドル製品を *有効* で保存するとエラーが発生す **[!DNL MSI]** 問題を修正。
1. **ACSD-63283**：ギフトレジストリからの項目の並べ替えによって例外が発生する場合や、ギフトレジストリの更新にレジストリに属さない項目が含まれている問題を修正しました。
1. **ACSD-63299**：設定可能な製品の特別価格がストアフロントに表示されない問題を修正しました。
1. **ACSD-63325**：空の [!DNL GraphQL] リクエストを送信すると `Syntax Error: Unexpected <EOF>` エラーが発生する問題を修正しました。
1. **ACSD-63329**:[!DNL REST API] を使用して製品を作成する際に、入力タイプが **[!UICONTROL Date]** または **[!UICONTROL Date and Time]** の属性のデフォルト値が設定されない問題を修正しました。
1. **ACSD-63572**：インデクサープロセスが終了しても、`CatalogRule` インデクサーの一時テーブルがクリーンアップされない問題を修正しました。
1. **ACSD-63578**:[!UICONTROL Admin] ールバーの **[!UICONTROL Add to Order by SKU]** にある「**[!UICONTROL Delete]**」ボタンをクリックしても [!DNL SKU] が削除されない問題を修正しました。

左側のメニューを使用して、特定のパッチページに移動します。
