---
title: 「MDVA-37748:GraphQL クエリを実行すると、共有カタログに割り当てられていない商品が返される」
description: MDVA-37748 パッチは、GraphQLのクエリーが共有カタログに割り当てられていない商品を返す問題を修正します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches） 1.1.5 がインストールされている場合に利用できます。 パッチ ID は MDVA-37748。 この問題はAdobe Commerce 2.4.4 で修正される予定であることに注意してください。
feature: B2B, GraphQL, Catalog Management, Categories, Products
role: Admin
source-git-commit: 1fb76b8d648cbbe2a9f602d2b1a0149f1f4f0e46
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 0%

---

# MDVA-37748:GraphQL クエリは、共有カタログに割り当てられていない商品を返します

MDVA-37748 パッチは、GraphQLのクエリーが共有カタログに割り当てられていない商品を返す問題を修正します。 このパッチは、[Quality Patches Tool （QPT） ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)1.1.5 がインストールされている場合に使用できます。 パッチ ID は MDVA-37748。 この問題はAdobe Commerce 2.4.4 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

Adobe Commerce（すべてのデプロイメント方法） 2.4.2

**Adobe Commerce バージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方法） 2.4.2 ～ 2.4.2-p2

>[!NOTE]
>
>パッチは、新しい Quality Patches Tool リリースを使用する他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

GraphQL クエリは、共有カタログに割り当てられていない製品を返します。

<u> 前提条件 </u>:

B2B モジュールがインストールされている。

<u> 再現手順 </u>:

1. 2 つの製品を作成してカテゴリに割り当てます。
   * 製品 1 - パブリック
   * 製品 2

1. 「Product 1 - Public」を「Default （General）」共有カタログに割り当てます。
1. 追加のカスタム共有カタログを作成して、「製品 2」に割り当てます。
1. 新しい会社を作成して、手順 3 で作成した追加の共有カタログに割り当てます。
1. Cron 実行/再インデックス作成後、フロントエンドで、ログインしていない場合に「製品 1 - パブリック」が表示されることを検証します。
1. 手順 4 で作成した会社の管理者としてログインし、「Product 2」のみが表示されることを確認します。
1. 次のGraphQL クエリを使用して、認証トークンをリクエストします。

   <pre>
    <code class="language-graphql">
    mutation &lbrace;
      generateCustomerToken(
        email: "company.admin@exapmle.test"
        password: "password"
      ) &lbrace;
        token
      &rbrace;
    &rbrace;
    </code>
    </pre>

1. ヘッダー **Authorization Bearer value-of-the-token** を追加し、次のGraphQL クエリを実行します。

   <pre>
    <code class="language-graphql">
    &lbrace;
      products(
          filter: {},
          pageSize: 100,
          currentPage: 1
          sort: {}
        ) &lbrace;
          total_count
          page_info &lbrace;
            page_size
            current_page
          &rbrace;
          aggregations &lbrace;
            attribute_code
            count
            label
            options &lbrace;
              label
              value
              count
            &rbrace;
          &rbrace;
          items &lbrace;
            name
            sku
            created_at
            updated_at
            stock_status
            description {html}
            short_description {html}
            url_key
            url_path
            price_tiers&lbrace;
              final_price&lbrace;
                  value
                  currency
                &rbrace;
              discount&lbrace;
                  amount_off
                  percent_off
                &rbrace;
              quantity
            &rbrace;
            price_range &lbrace;
             maximum_price &lbrace;
              regular_price &lbrace;
                value
              &rbrace;
              final_price &lbrace;
                value
              &rbrace;
            &rbrace;
            minimum_price &lbrace;
              regular_price &lbrace;
                value
              &rbrace;
              final_price &lbrace;
               value
              &rbrace;
            &rbrace;
          &rbrace;
          image &lbrace;
           url
          &rbrace;
          thumbnail &lbrace;
           url
          &rbrace;
          small_image &lbrace;
           url
          &rbrace;
          media_gallery &lbrace;
           url
          &rbrace;
          ... on ConfigurableProduct &lbrace;
            configurable_options &lbrace;
             id

             label
             position
             use_default
             attribute_code
             values &lbrace;
               value_index
               label
               swatch_data &lbrace;
                 value
               &rbrace;
            &rbrace;
            product_id
          &rbrace;
          variants &lbrace;
            product &lbrace;
              id
              name
              sku
              &#x200B;#margin
              &#x200B;#margin_percentage
              image &lbrace;
                url
              &rbrace;
              small_image &lbrace;
                url
              &rbrace;
              thumbnail &lbrace;
                url
              &rbrace;
              media_gallery&lbrace;
                url
              &rbrace;
              attribute_set_id
              ... on PhysicalProductInterface &lbrace;
                weight
              &rbrace;
              price_range &lbrace;
                minimum_price &lbrace;
                  regular_price &lbrace;
                    value
                    currency
                  &rbrace;
                &rbrace;
              &rbrace;
            &rbrace;
            attributes &lbrace;
              label
              code
              value_index
            &rbrace;
          &rbrace;
        &rbrace;
      &rbrace;

    &rbrace;
&rbrace;
</code>
</pre>

<u> 期待される結果 </u>:

GraphQLから返されるカウントと商品は、ログインしたユーザーに関連付けられた共有カタログに割り当てられた商品のみを考慮します。

<u> 実際の結果 </u>:

「Product 2」のみが返されますが、`total_count` には 2 つが表示されます。

<pre>
<code class="language-graphql">
&lbrace;
  "data": &lbrace;
    "products": &lbrace;
      "total_count": 2,
      "page_info": &lbrace;
        "page_size": 100,
        "current_page": 1
      &rbrace;,
      "aggregations": &lbrack;
        &lbrace;
          "attribute_code": "price",
          "count": 2,
          "label": "Price",
          "options": &lbrack;
            &lbrace;
              "label": "0-100",
              "value": "0_100",
              "count": 1
            &rbrace;,
            &lbrace;
              "label": "100-200",
              "value": "100_200",
              "count": 1
            &rbrace;
          &rbrack;
        &rbrace;,
        &lbrace;
          "attribute_code": "category_id",
          "count": 1,
          "label": "Category",
          "options": &lbrack;
            &lbrace;
              "label": "Cat 1",
              "value": "3",
              "count": 2
            &rbrace;
          &rbrack;
        &rbrace;
      &rbrack;,
      "items": &lbrack;
        &lbrace;
          "name": "Product 2",
          "sku": "Product 2",
          "created_at": "2021-05-12 10:51:44",
          "updated_at": "2021-05-12 11:03:24",
          "stock_status": "IN_STOCK",
          "description": &lbrace;
            "html": ""
          &rbrace;,
          "short_description": &lbrace;
            "html": ""
          &rbrace;,
          "url_key": "product-2",
          "url_path": null,
          "price_tiers": &lbrack;
            &lbrace;
              "final_price": &lbrace;
                "value": 90,
                "currency": "USD"
              &rbrace;,
              "discount": &lbrace;
                "amount_off": 10,
                "percent_off": 10
              &rbrace;,
              "quantity": 1
            &rbrace;
          &rbrack;,
          "price_range": &lbrace;
            "maximum_price": &lbrace;
              "regular_price": &lbrace;
                "value": 100
              &rbrace;,
              "final_price": &lbrace;
                "value": 90
              &rbrace;
            &rbrace;,
            "minimum_price": &lbrace;
              "regular_price": &lbrace;
                "value": 100
              &rbrace;,
              "final_price": &lbrace;
                "value": 90
              &rbrace;
            &rbrace;
          &rbrace;,
          "image": &lbrace;
            "url": "../pub/static/version1620816308/frontend/Magento/luma/en_US/Magento_Catalog/images/product/placeholder/image.jpg"
          &rbrace;,
          "thumbnail": &lbrace;
            "url": "../pub/static/version1620816308/frontend/Magento/luma/en_US/Magento_Catalog/images/product/placeholder/thumbnail.jpg"
          &rbrace;,
          "small_image": &lbrace;
            "url": "../pub/static/version1620816308/frontend/Magento/luma/en_US/Magento_Catalog/images/product/placeholder/small_image.jpg"
          &rbrace;,
          "media_gallery": []
        &rbrace;
      &rbrack;
    &rbrace;
  &rbrace;
&rbrace;
</code>
</pre>

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Sourceオンプレミス：[[!DNL Quality Patches Tool] > Usage](/help/tools/quality-patches-tool/usage.md) in the [!DNL Quality Patches Tool] guide.
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

品質向上パッチツールの詳細については、次を参照してください。

* [ 品質向上パッチツールがリリースされました：品質向上パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) がサポートナレッジベースに追加されました。
* [Quality Patches Tool を使用して、Adobe Commerceの問題に対するパッチが使用可能かどうかを確認します ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!DNL Quality Patches Tool] ガイド）。

QPT で使用可能なその他のパッチについては、[QPT で使用可能なパッチ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) の節を参照してください。
