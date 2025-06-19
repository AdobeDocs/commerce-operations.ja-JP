---
title: ACSD-63883:[!UICONTROL Requisition List] に対する応答で間違った「items_count」  [!DNL GraphQL]  修正
description: ACSD-63883 パッチを適用して、[!UICONTROL Requisition List] が応答で誤った「items_count」を返す問題を修正し  [!DNL GraphQL]  ください。
feature: B2B, GraphQL
role: Admin, Developer
exl-id: 8946d7fb-558a-4867-a843-a61715416f25
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---

# ACSD-63883:[!UICONTROL Requisition List] に対する応答で誤った `items_count` ータ [!DNL GraphQL] 修正

ACSD-63883 パッチは、**[!UICONTROL Requisition List]** が [!DNL GraphQL] 応答で誤った `items_count` を返す問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61 がインストールされている場合に使用できます。 パッチ ID は ACSD-63883 です。 この問題はAdobe Commerce B2B 1.5.3 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p3

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

[!DNL GraphQL] 応答で **[!UICONTROL Requisition List]** が誤った `items_count` を返します。


<u> 再現手順 </u>:

1. B2B **[!UICONTROL Requisition List]** 機能を有効にします。
1. いくつかの製品を作成します。
1. 顧客アカウントを作成します。
1. 「**[!UICONTROL Create new Requisition List]**」をクリックします。
1. `addProductsToRequisitionList` [!DNL GraphQL] ミューテーションリクエストを製品と共に送信して、[!UICONTROL Requisition List] に追加します。

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

1. `addProductsToRequisitionList` [!DNL GraphQL] ミューテーションリクエストを他の 3 つの製品と共に送信して、[!UICONTROL Requisition List] に追加します。
1. 応答の `items_count` を確認します。

**期待される結果**:

* 応答で `items_count`:4 が返されます。

**実際の結果**:

* `items_count`:2 が応答で返されます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。


## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
