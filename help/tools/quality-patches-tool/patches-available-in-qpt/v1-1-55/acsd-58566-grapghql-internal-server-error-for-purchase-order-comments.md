---
title: ACSD-58566：発注コメントのGraphQL内部サーバーエラー
description: ACSD-58566 パッチを適用して、「addPurchaseOrderComment」のミューテーションで「created_at」フィールドをクエリする際にGraphQLが内部サーバーエラーを返すAdobe Commerceの問題を修正します。
feature: B2B, Purchase Orders, GraphQL
role: Admin, Developer
exl-id: 6d051f57-7a2f-44a5-a1c9-834917ed986c
type: Troubleshooting
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---

# ACSD-58566：発注コメントのGraphQL内部サーバーエラー

ACSD-58566 パッチは、`addPurchaseOrderComment`変異内の`created_at` フィールドをクエリすると、想定される日時ではなくnull値が返される問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55がインストールされている場合に利用できます。 パッチ IDはACSD-58566です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p4

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

GraphQLは、`addPurchaseOrderComment`の変異で`created_at` フィールドをクエリする際に、内部サーバーエラーを返します。

<u>前提条件</u>:

B2B モジュールがインストールされ、会社と発注書が有効になります。

<u>複製する手順</u>:

1. 企業ユーザーの顧客トークンを生成します。
1. 次の一連のGraphQL リクエストを実行します。
   1. `customerCart`を使用して&#x200B;*カート*&#x200B;を作成します。
   1. `addProductsToCart`を使用して&#x200B;*買い物かご*&#x200B;に商品を追加します。
   1. `placePurchaseOrder`を使用して注文します。
   1. `addPurchaseOrderComment`を使用して注文書にコメントを追加します。

   ```graphql
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

<u>期待される結果</u>:

`created_at` フィールドは、発注コメントの日時を返します。

<u>実際の結果</u>:

`created_at`日ではなくnullを表示します。

```json
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

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

[[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
