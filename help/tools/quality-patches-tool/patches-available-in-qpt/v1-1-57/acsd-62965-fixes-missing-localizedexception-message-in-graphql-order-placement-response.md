---
title: ACSD-62965:GraphQL注文プレースメント応答に LocalizedException メッセージが見つからない問題を修正しました
description: ACSD-62965 パッチを適用して、注文時にGraphQL応答に「LocalizedException」メッセージが含まれなかったAdobe Commerceの問題を修正してください。
feature: Orders, GraphQL
role: Admin, Developer
exl-id: cf9d1409-6fe3-4019-9207-df5f12a41505
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 0%

---

# ACSD-62965:GraphQLの注文配置応答に `LocalizedException` メッセージがない問題を修正しました

ACSD-62965 パッチでは、`LocalizedException` メッセージが注文時のGraphQL応答に含まれない問題が修正されています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57 で使用できます。パッチ ID は ACSD-62965 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

Adobe Commerce（すべてのデプロイメント方法） 2.4.7

**Adobe Commerce バージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方法） 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

注文配置に対するGraphQL応答に `LocalizedException` メッセージが含まれていないので、デバッグのエラーの詳細が不十分になります。

<u> 再現手順 </u>:

1. クリーンな **[!DNL Adobe Commerce]** インスタンスをインストールします。
1. 買い物かごに製品を追加し、注文配置ステップに進みます。
1. `app/code/Magento/QuoteGraphQl/Model/Resolver/PlaceOrder.php` で `Magento\Framework\Exception\LocalizedException` に `LocalizedException` を追加します。
1. 次の行の後に例外を挿入します。

   ```
   $cart = $this->getCartForCheckout->execute($maskedCartId, $userId, $storeId);
   ```

   例外を追加します。

   ```
   throw new LocalizedException(new Phrase("Test LocalizedException"));
   ```

1. Place order GraphQL リクエストを実行します。

   ```
   mutation {
   placeOrder(input: {cart_id: "cart_id"}) {
       order {
       order_number
       }
   }
   }
   ```

1. 応答を確認します。
   1. 応答には `LocalizedException` メッセージは含まれません。
   1. 間違った応答の例：

      ```
      {
      "data": {
          "placeOrder": {
          "order": null
          }
      }
      }
      ```

<u> 期待される結果 </u>:

`LocalizedException` ラーが発生した場合、エラー処理を改善するために、注文プレースメントのGraphQL応答に例外メッセージを含める必要があります。

<u> 実際の結果 </u>:

`LocalizedException` ラーが発生した場合、この例外メッセージは注文の発注に関するGraphQLの応答には含まれません。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
