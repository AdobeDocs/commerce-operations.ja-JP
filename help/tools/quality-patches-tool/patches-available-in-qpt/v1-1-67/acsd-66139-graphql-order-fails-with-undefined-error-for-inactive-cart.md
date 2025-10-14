---
title: ACSD-66139：非アクティブな買い物かごに対してGraphQLの注文が失敗し、UNDEFINED エラーが発生する
description: ACSD-66139 パッチを適用すると、存在しない、または非アクティブな買い物かごに注文すると、エラーメッセージの翻訳時にGraphQLが特定のエラーコードではなく UNDEFINED エラーコードを返すAdobe Commerceの問題が修正されます。
feature: GraphQL
role: Admin, Developer
type: Troubleshooting
exl-id: 5a1a94ca-f274-4098-8b44-d3f1a0ea65a1
source-git-commit: 8681dd706e614f86bbee36c182b47491ec707196
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---

# ACSD-66139：非アクティブな買い物かごに対して「UNDEFINED」エラーが発生してGraphQLの注文が失敗する

ACSD-66139 パッチは、存在しない、または非アクティブな買い物かごに注文すると、GraphQLがエラーメッセージの翻訳時に、特定のエラーコードではなく *UNDEFINED* エラーコードを返す問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67 がインストールされている場合に使用できます。 パッチ ID は ACSD-66139 です。 この問題はAdobe Commerce 2.4.9 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p5

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7 - 2.4.7-p6

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがお使いのAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを latestvers に更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

存在しない買い物かごや非アクティブな買い物かごに注文すると、エラーメッセージが翻訳されると、GraphQLは、特定のエラーコードではなく *UNDEFINED* エラーコードを返します。

<u> 再現手順 </u>:

1. `app/i18n/Magento/de_DE/de_DE.csv` を追加し、次のエラー文字列翻訳を含めます。

```
"Could not find a cart with ID ""%masked_cart_id""","Oh noo, we have an UNDEFINED issue, see!",module,Magento_QuoteGraphQl
```

1. 管理パネルで、**[!UICONTROL Stores]** / **[!UICONTROL Settings]** / **[!UICONTROL All Stores]** / **[!UICONTROL Create Store View]** に移動して、ストア表示を作成します。
1. **[!UICONTROL Code]** を *test* に設定します。
1. 新しく作成 `german` たストア表示に言語を割り当てます。
1. `setup:upgrade` および `setup:static-content:deploy -f` を実行します。
1. ヘッダー `Store:test` を指定して次のGraphQL クエリを実行します。

```
mutation {
    placeOrder(input: { cart_id: "test" }) {
        orderV2 {
            id
            number
        }
    }
}
```

<u> 期待される結果 </u>:

正しいエラー応答：

```
{
    "errors": [
        {
            "message": "Oh noo, we have an UNDEFINED issue, see!",
            "locations": [
                {
                    "line": 2,
                    "column": 2
                }
            ],
            "path": [
                "placeOrder"
            ],
            "extensions": {
                "category": "graphql-input",
                "error_code": "CART_NOT_FOUND"
            }
        }
    ],
    "data": {
        "placeOrder": null
    }
}
```

<u> 実際の結果 </u>:

返される `error_code` は *UNDEFINED* です。

```
{
    "errors": [
        {
            "message": "Oh noo, we have an UNDEFINED issue, see!",
            "locations": [
                {
                    "line": 2,
                    "column": 2
                }
            ],
            "path": [
                "placeOrder"
            ],
            "extensions": {
                "category": "graphql-input",
                "error_code": "UNDEFINED"
            }
        }
    ],
    "data": {
        "placeOrder": null
    }
}
```

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 &#x200B;](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [&#x200B; アップグレードとパッチ &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
