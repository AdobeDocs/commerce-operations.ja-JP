---
title: ACSD-47292：在庫切れのバンドル商品がGraphQLのレスポンスで利用できない
description: 「在庫切れ商品を表示」が「はい」に設定されている場合でも、GraphQLの対応で在庫切れのバンドル商品が利用できないAdobe Commerceの問題を修正するには、ACSD-47292 パッチを適用します。
feature: Admin Workspace, Categories, GraphQL, Orders, Products
role: Admin
exl-id: 3b8114a3-cc45-4d65-af74-cb3e905d7f75
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 0%

---

# ACSD-47292：在庫切れのバンドル商品がGraphQLのレスポンスで利用できない

ACSD-47292 パッチでは、[!UICONTROL Display Out-of-Stock Products]が&#x200B;*[!UICONTROL Yes]*&#x200B;に設定されていても、GraphQLの対応で在庫切れのバンドル商品が利用できない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.25がインストールされている場合に利用できます。 パッチ IDはACSD-47292です。 この問題は、Adobe Commerce 2.4.6で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.5-p1

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

[!UICONTROL Display Out-of-Stock Products]が&#x200B;*[!UICONTROL Yes]*&#x200B;に設定されている場合でも、GraphQLの回答で在庫切れのバンドル商品は利用できません。

<u>複製する手順</u>:

1. Adobe Commerce Admin > **[!UICONTROL System]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]**&#x200B;に移動し、[!UICONTROL Display Out-of-Stock Products]を&#x200B;*[!UICONTROL Yes]*&#x200B;に設定します。
1. s1とs2の2つのシンプルな商品を作成します。
1. s1を在庫切れにして個別に表示しないようにし、s2を個別に表示しないようにして、カテゴリに割り当てます。
1. 少なくとも1つのオプション製品を含むバンドル製品を作成し、s1とs2をこのオプションに割り当てます（入力タイプ「RadioButton」）。
1. バンドルされた製品を保存し、カテゴリに割り当てます。
1. ストアフロントに移動し、このバンドル製品を開きます。 在庫切れオプション s1はグレー表示になりますが、表示されます。
1. GraphQL リクエストを送信します。

```GraphQL
{
  categoryList(filters: { ids: { in: ["3"] } }) {
    id
    name
    products(pageSize: 8, sort: { position: ASC }) {
      total_count
      items {
        id
        sku
        name
        ... on BundleProduct {
          url_key
          items {
            title
            sku
            options {
              quantity
              position
              is_default
              product {
                id
                name
                sku
              }
            }
          }
        }
      }
    }
  }
}
```

<u>期待される結果</u>:

s1 バンドルオプションは、[!UICONTROL Display Out-of-Stock Products]が&#x200B;*[!UICONTROL Yes]*&#x200B;に設定されているため、GraphQLの応答に一覧表示され、ストアフロントに表示されます。

<u>実際の結果</u>:

s1 バンドルオプションは、GraphQLのレスポンスには表示されません。

```GraphQL
"items": [
                                {
                                    "title": "oo1",
                                    "sku": "bundle2",
                                    "options": [
                                        {
                                            "quantity": 1,
                                            "position": 2,
                                            "is_default": false,
                                            "product": {
                                                "id": 2,
                                                "name": "s2",
                                                "sku": "s2"
                                            }
                                        }
                                    ]
                                }
                            ]
```

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
