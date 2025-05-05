---
title: 「ACSD-54626:GraphQLから NUMBER_OF_SKU を持つ新しい発注書ルールを作成できない」
description: ACSD-54626 パッチを適用すると、お客様がGraphQLを介して「NUMBER_OF_SKUS」属性を含む新しい発注書ルール （「createPurchaseOrderApprovalRule」）を作成できないAdobe Commerceの問題を修正できます。
feature: Attributes, B2B, GraphQL, Purchase Orders
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---

# ACSD-54626:GraphQLで NUMBER_OF_SKU を使用して新しい発注書ルールを作成できない

ACSD-54626 パッチは、GraphQLを介して `NUMBER_OF_SKUS` 属性を持つ新しい発注書ルール（`createPurchaseOrderApprovalRule`）を作成できない問題を修正します。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.42 がインストールされている場合に使用できます。 パッチ ID は ACSD-54626 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p2

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

お客様は、GraphQLを使用して `NUMBER_OF_SKUS` 属性を持つ新しい発注書ルール （`createPurchaseOrderApprovalRule`）を作成することはできません。

<u> 前提条件 </u>:

Adobe Commerce B2B モジュールをインストールして有効にします。

<u> 再現手順 </u>:

1. B2B 会社と購入ルールを有効にします。
1. 購入ルールが有効な会社を作成します。
1. 次のGraphQL クエリを実行します。

   ```
   mutation CreatePurchaseRule {
       createPurchaseOrderApprovalRule(
           input: {
               name: "Test Rule"
               description: "description"
               applies_to: "MQ=="
               status: ENABLED
               approvers: "MQ=="
               condition: {
                   attribute: NUMBER_OF_SKUS
                   operator: MORE_THAN
                   quantity: 10
               }
           }
       ) {
           uid
           name
           __typename
       }
   }
   ```

<u> 期待される結果 </u>:

購入ルールが作成されます。

<u> 実際の結果 </u>:

次のエラーが発生します。

```
{
    "errors": [
        {
            "message": "Required data is missing from a rule condition.",
            "locations": [
                {
                    "line": 2,
                    "column": 3
                }
            ],
            "path": [
                "createPurchaseOrderApprovalRule"
            ],
            "extensions": {
                "category": "graphql-input"
            }
        }
    ],
    "data": {
        "createPurchaseOrderApprovalRule": null
    }
}
```

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Sourceオンプレミス：[[!DNL Quality Patches Tool] > Usage](/help/tools/quality-patches-tool/usage.md) in the [!DNL Quality Patches Tool] guide.
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)」を参照してください。
