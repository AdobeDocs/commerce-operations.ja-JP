---
title: ACSD-63883:[!UICONTROL Requisition List] に対する応答で間違った「items_count」  [!DNL GraphQL]  修正
description: ACSD-63883 パッチを適用して、[!UICONTROL Requisition List] が応答で誤った「items_count」を返す問題を修正し  [!DNL GraphQL]  ください。
feature: B2B, GraphQL
role: Admin, Developer
source-git-commit: 5d8b78588b11534828a9b925cbab0cc945860367
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---

# ACSD-63883:[!UICONTROL Requisition List] に対する応答で誤った `items_count` ータ [!DNL GraphQL] 修正

ACSD-63883 パッチは、**[!UICONTROL Requisition List]**&#x200B;が [!DNL GraphQL] 応答で誤った`items_count`を返す問題を修正します。このパッチは、 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61 がインストールされている場合に使用できます。 パッチ ID は ACSD-63883 です。 この問題は、Adobe Systems Commerce B2B 1.5.3 で修正される予定です。

## 影響を受ける製品とバージョン

**パッチは Adobe Systems コマースバージョン用に作成されます。**

* Adobe Systems コマース(すべてのデプロイメント方法)2.4.7-p3

**Adobe Systems Commerce バージョンとの互換性:**

* Adobe Systems コマース (すべてのデプロイメントメソッド) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

**[!UICONTROL Requisition List]** は、[!DNL GraphQL]応答で正しくない`items_count`を返します。


<u>再現する手順</u>:

1. B2B **[!UICONTROL Requisition List]** 機能を有効化します。
1. いくつかの製品作成。
1. 顧客アカウント作成。
1. [ **[!UICONTROL Create new Requisition List]**] をクリックします。
1. `addProductsToRequisitionList` [!DNL GraphQL]突然変異リクエストを製品に送信して、[!UICONTROL Requisition List]に追加します。

   ```
   mutation addProductsToRequisitionList(
   $requisitionListUid: ID!
   $requisitionListItems: [RequisitionListItemsInput!]!
   ) {
   addProductsToRequisitionList(
   requisitionListUid: $requisitionListUid
   requisitionListItems: $requisitionListItems
   ) {
   requisition_list
   { uid name description items_count }
   }
   }
   ```

1. `addProductsToRequisitionList` [!DNL GraphQL]変異リクエストを他の3つの製品と送信して、それらを[!UICONTROL Requisition List]に追加します。
1. 応答の `items_count` を確認します。

**期待される結果**:

* 応答で `items_count`:4 が返されます。

**実際の結果**:

* `items_count`: 応答では 2 が返されます。

## パッチ適用

個人パッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe Systems コマースまたはオンプレミスMagento Open Source: [!DNL Quality Patches Tool]ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャー での Commerce Adobe Systems: クラウド インフラストラクチャ ガイド での Commerce の [アップグレードとパッチ > 適用 パッチ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja) 。


## 関連読書

[!DNL Quality Patches Tool]について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
