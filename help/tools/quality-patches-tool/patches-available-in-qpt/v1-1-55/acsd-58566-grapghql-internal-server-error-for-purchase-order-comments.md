---
title: ACSD-58566：発注書コメントのGraphQL内部サーバーエラー
description: ACSD-58566 パッチを適用すると、「addPurchaseOrderComment」ミューテーションの「created_at」フィールドに対するクエリを実行する際に、GraphQLが内部サーバーエラーを返すAdobe Commerceの問題が修正されます。
feature: B2B, Purchase Orders, GraphQL
role: Admin, Developer
source-git-commit: 3b8cc44ea8d71982b8a2eb76d9d7ec2a5c3180b0
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---

# ACSD-58566：発注書コメントのGraphQL内部サーバーエラー

ACSD-58566 パッチでは、`addPurchaseOrderComment` ミューテーションの `created_at` フィールドをクエリすると、期待される日時ではなく null 値が返される問題を修正しました。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55 がインストールされている場合に使用できます。 パッチ ID は ACSD-58566 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p4

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

`addPurchaseOrderComment` ミューテーションの `created_at` フィールドに対してクエリを実行すると、GraphQLが内部サーバーエラーを返します。

<u> 前提条件 </u>:

B2B モジュールがインストールされ、会社および発注書が有効になっています。

<u> 再現手順 </u>:

1. 会社ユーザーの顧客トークンを生成します。
1. 次のGraphQL リクエストのシーケンスを実行します。
   1. `customerCart` を使用して *買い物かご* を作成します。
   1. `addProductsToCart` を使用して、商品を *買い物かご* に追加します。
   1. `placePurchaseOrder` を使用して注文します。
   1. `addPurchaseOrderComment` を使用して、発注書にコメントを追加します。

   ```
   mutation {
       addPurchaseOrderComment(
           input: { purchase_order_uid: "MQ==", comment: "Looks good to me" }
   ) {
           comment {
               uid
               created_at
               author {
                   firstname
                   lastname
                   email
               }
               text
           }
       }
   }
   ```

<u> 期待される結果 </u>:

`created_at` フィールドは、発注書コメントの日時を返します。

<u> 実際の結果 </u>:

`created_at` 日ではなく null を表示します。

```
{
  "errors": [
    {
      "message": "Internal server error",
      "locations": [
        {
          "line": 10,
          "column": 1
        }
      ],
      "path": [
        "addPurchaseOrderComment",
        "comment",
        "created_at"
      ]
    }
  ],
  "data": {
    "addPurchaseOrderComment": null
  }
}
```

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Sourceオンプレミス：[[!DNL Quality Patches Tool] > Usage](/help/tools/quality-patches-tool/usage.md) in the [!DNL Quality Patches Tool] guide.
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

[[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
