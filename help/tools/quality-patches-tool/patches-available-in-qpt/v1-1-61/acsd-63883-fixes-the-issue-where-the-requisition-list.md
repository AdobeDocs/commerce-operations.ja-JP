---
title: 'ACSD-63883: [!UICONTROL Requisition List]の [!DNL GraphQL] 応答の「items_count」が正しくありません'
description: ACSD-63883 パッチを適用して、[!UICONTROL Requisition List]が [!DNL GraphQL] 応答で誤った'items_count'を返す問題を修正します。
feature: B2B, GraphQL
role: Admin, Developer
exl-id: 8946d7fb-558a-4867-a843-a61715416f25
type: Troubleshooting
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 0%

---

# ACSD-63883: [!UICONTROL Requisition List]の[!DNL GraphQL]応答の`items_count`を修正しています

ACSD-63883 パッチは、**[!UICONTROL Requisition List]**&#x200B;が[!DNL GraphQL]応答で誤った`items_count`を返す問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61がインストールされている場合に利用できます。 パッチ IDはACSD-63883です。 この問題は、Adobe Commerce B2B 1.5.3で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p3

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

**[!UICONTROL Requisition List]**&#x200B;は、[!DNL GraphQL]応答で正しくない`items_count`を返します。


<u>複製する手順</u>:

1. B2B **[!UICONTROL Requisition List]**&#x200B;機能を有効にします。
1. いくつかの商品を制作する。
1. 顧客アカウントの作成。
1. **[!UICONTROL Create new Requisition List]**&#x200B;をクリックします。
1. `addProductsToRequisitionList` [!DNL GraphQL]の突然変異リクエストを製品と共に送信して、[!UICONTROL Requisition List]に追加します。

   ```graphql
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

1. `addProductsToRequisitionList` [!DNL GraphQL]の突然変異リクエストを他の3つの製品と一緒に送信して、[!UICONTROL Requisition List]に追加します。
1. 応答の`items_count`を確認してください。

**期待される結果**:

* `items_count`: 4を応答で返す必要があります。

**実際の結果**:

* `items_count`: 2が応答で返されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)」（Commerce クラウドインフラストラクチャガイド）。


## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
