---
title: ACSD-50260:GraphQL商品の検索結果が制限される
description: GraphQL製品の検索結果が 10,000 件のみに制限されるAdobe Commerceの問題を修正するために、ACSD-50260 パッチを適用してください。
feature: Admin Workspace, Categories, GraphQL, Products, Search
role: Admin
exl-id: a9099fab-226d-439b-b2d0-f354d6b5638f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 0%

---

# ACSD-50260:GraphQL商品の検索結果が制限される

ACSD-50260 パッチは、GraphQL製品の検索結果が 10,000 件のみに制限される問題を修正しました。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.29 がインストールされている場合に使用できます。 パッチ ID は ACSD-50260 です。 この問題はAdobe Commerce 2.4.6 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p1

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5 ～ 2.4.5-p2

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

GraphQL製品の検索結果は、10,000 件までに制限されます。

<u> 再現手順 </u>:

1. 1 つのカテゴリに *[!UICONTROL 15,000 products]* を生成します。
1. 次に添付されたGraphQL リクエストを使用して、そのカテゴリをクエリします。

```GraphQL
{
  products(
    filter: { category_id: { eq: "{CATEGORY_ID}" } }
    pageSize: 5
    currentPage: 1
  ) {
    total_count
    page_info {
      current_page
      page_size
      total_pages
    }

    aggregations {
      attribute_code
      count
      label
      options {
        label
        value
      }
    }

    items {
      uid
      sku
      is_for_clearance
      categories {
        name
        breadcrumbs {
          category_name
          category_uid
        }
        display_mode
        description
      }
    }
  }
}
```

<u> 期待される結果 </u>:

`total_count = 15k`

検索結果ですべての製品を取得する可能性。

<u> 実際の結果 </u>:

`total_count = 10k`

検索結果で、この 10,000 個のバッチに従って製品が取得される可能性はありません。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[[!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html): Search for patches[!DNL Quality Patches Tool]」を参照してください。
