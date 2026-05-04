---
title: 'ACSD-62965: GraphQLの注文プレースメント応答でLocalizedException メッセージが欠落しているのを修正しました'
description: ACSD-62965 パッチを適用して、注文処理中に「LocalizedException」メッセージがGraphQL応答に含まれていなかったAdobe Commerceの問題を修正します。
feature: Orders, GraphQL
role: Admin, Developer
exl-id: cf9d1409-6fe3-4019-9207-df5f12a41505
type: Troubleshooting
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---

# ACSD-62965: GraphQLの注文プレースメント応答で`LocalizedException` メッセージが見つからない問題を修正

ACSD-62965 パッチは、注文処理中に`LocalizedException` メッセージがGraphQL応答に含まれなかった問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57で利用できます。 パッチ IDはACSD-62965です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

Adobe Commerce（すべてのデプロイメント方法） 2.4.7

**Adobe Commerceのバージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方法） 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

注文プレースメントのGraphQL応答に`LocalizedException` メッセージが含まれていないため、デバッグのエラーの詳細が不十分です。

<u>複製する手順</u>:

1. クリーンな&#x200B;**[!DNL Adobe Commerce]** インスタンスをインストールします。
1. 商品をカートに追加し、注文手続きに進みます。
1. `LocalizedException`を`app/code/Magento/QuoteGraphQl/Model/Resolver/PlaceOrder.php`の`Magento\Framework\Exception\LocalizedException`に追加します。
1. 次の行の後に例外を挿入します。

   ```shell
   $cart = $this->getCartForCheckout->execute($maskedCartId, $userId, $storeId);
   ```

   例外を追加します。

   ```text
   throw new LocalizedException(new Phrase("Test LocalizedException"));
   ```

1. 次の手順で、注文のGraphQL リクエストを実行します。

   ```graphql
   mutation {
   placeOrder(input: {cart_id: "cart_id"}) {
       order {
       order_number
       }
   }
   }
   ```

1. 応答を観察する：
   1. 応答に`LocalizedException` メッセージが含まれていません。
   1. 誤った応答の例：

      ```json
      {
      "data": {
          "placeOrder": {
          "order": null
          }
      }
      }
      ```

<u>期待される結果</u>:

`LocalizedException`が発生した場合、エラー処理を改善するために、例外メッセージを注文配置GraphQL応答に含める必要があります。

<u>実際の結果</u>:

`LocalizedException`が発生した場合、例外メッセージは注文プレースメント GraphQLのレスポンスに含まれません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
