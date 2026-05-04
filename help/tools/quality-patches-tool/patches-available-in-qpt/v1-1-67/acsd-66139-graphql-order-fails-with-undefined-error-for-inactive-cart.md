---
title: ACSD-66139：非アクティブな買い物かごのUNDEFINED エラーでGraphQL注文が失敗する
description: ACSD-66139 パッチを適用して、Adobe Commerceの問題を修正します。この問題では、存在しないカートまたは非アクティブなカートの注文を行うと、エラーメッセージが翻訳されたときにGraphQLは特定のエラーコードではなく、未定義のエラーコードを返します。
feature: GraphQL
role: Admin, Developer
type: Troubleshooting
exl-id: 5a1a94ca-f274-4098-8b44-d3f1a0ea65a1
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# ACSD-66139：非アクティブな買い物かごの「未定義」エラーでGraphQL注文が失敗する

ACSD-66139 パッチでは、存在しないカートまたは非アクティブなカートの注文を行う際に、エラーメッセージが翻訳されたときに、GraphQLが特定のエラーコードの代わりに&#x200B;*UNDEFINED* エラーコードを返す問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67がインストールされている場合に利用できます。 パッチ IDはACSD-66139です。 この問題は、Adobe Commerce 2.4.9で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p5

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7 - 2.4.7-p6

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

GraphQLは、存在しないカートまたは非アクティブなカートの注文を行う際に、エラーメッセージが翻訳された場合、特定のエラーコードではなく&#x200B;*UNDEFINED* エラーコードを返します。

<u>複製する手順</u>:

1. `app/i18n/Magento/de_DE/de_DE.csv`を追加し、次のエラー文字列翻訳を含めます：

```shell
"Could not find a cart with ID ""%masked_cart_id""","Oh noo, we have an UNDEFINED issue, see!",module,Magento_QuoteGraphQl
```

1. 管理パネルで、**[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL All Stores]** > **[!UICONTROL Create Store View]**&#x200B;に移動して、ストアビューを作成します。
1. **[!UICONTROL Code]**&#x200B;を&#x200B;*テスト*&#x200B;に設定します。
1. 新しく作成したストアビューに`german`言語を割り当てます。
1. `setup:upgrade`と`setup:static-content:deploy -f`を実行します。
1. ヘッダー`Store:test`を含む次のGraphQL クエリを実行します。

```graphql
mutation {
    placeOrder(input: { cart_id: "test" }) {
        orderV2 {
            id
            number
        }
    }
}
```

<u>期待される結果</u>:

正しいエラー応答：

```graphql
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

<u>実際の結果</u>:

返された`error_code`は&#x200B;*UNDEFINED*&#x200B;です：

```graphql
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

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
