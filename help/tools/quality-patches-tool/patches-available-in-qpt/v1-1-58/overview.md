---
title: 概要： [!DNL Quality Patches Tool]  （QPT） v1.1.58
description: このサブセクションでは、 [!DNL Quality Patches Tool]  （QPT） v1.1.58で使用可能なパッチによって修正された問題について詳しく説明します。
feature: Tools and External Services
role: Admin, Developer
exl-id: 61bf8b82-f897-41f6-8524-5aa74c6440f1
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%

---

# 概要：[!DNL Quality Patches Tool] （QPT） v1.1.58

このサブセクションでは、[!DNL Quality Patches Tool] （QPT） v1.1.58で利用可能なパッチによって修正された問題について詳しく説明します。

QPT v1.1.58には次のパッチが含まれています。

1. **ACSD-48570**: **ストアコードをURLに追加**&#x200B;が&#x200B;*有効*&#x200B;で、以前はログインページまたは404 ページが表示されていた場合に、[!UICONTROL Admin] パスワードリセット リンクをクリックしてパスワードリセット ページにアクセスできなかった問題を修正します。
1. **ACSD-62118**: [!DNL B2B]件の注文が発注メソッドを使用して行われたときに`sales_order_tax_item` テーブルが完全に更新されない問題を修正します。
1. **ACSD-63067**：すべての製品数量が誤って強調表示され、1つの数量のみが正しくない場合に、グループ化された製品内のすべての製品にメッセージ *[!DNL Please specify the quantity of product(s).]*&#x200B;が表示される問題を修正します。
1. **ACSD-63090**：製品がカートに追加された後、削除されたときにショッピングカートのアイテムが削除される問題を修正します。
1. **ACSD-63182**: **[!DNL MSI]** *が有効*&#x200B;になっている重複したバンドル製品を保存する際にエラーが発生する問題を修正します。
1. **ACSD-63283**：ギフトレジストリからアイテムを注文すると例外が発生し、ギフトレジストリの更新にレジストリに属しないアイテムが含まれる問題を修正します。
1. **ACSD-63299**：設定可能な製品の特別価格がストアフロントに表示されない問題を修正します。
1. **ACSD-63325**：空の[!DNL GraphQL] リクエストを送信する際に`Syntax Error: Unexpected <EOF>` エラーが発生する問題を修正します。
1. **ACSD-63329**: [!DNL REST API]を介して製品を作成する際に、**[!UICONTROL Date]**&#x200B;または&#x200B;**[!UICONTROL Date and Time]**&#x200B;入力タイプの属性のデフォルト値が設定されない問題を修正しました。
1. **ACSD-63572**: インデクサープロセスが終了した場合に`CatalogRule` インデクサーの一時テーブルがクリーンアップされない問題を修正します。
1. **ACSD-63578**: [!UICONTROL Admin]で&#x200B;**[!UICONTROL Add to Order by SKU]**&#x200B;の&#x200B;**[!UICONTROL Delete]** ボタンをクリックしても[!DNL SKU]が削除されない問題を修正しました。

左側のメニューを使用して、特定のパッチページに移動します。
