---
title: ACSD-66041：国 ID がないため、アイルランド （IE）の郵便番号で集荷場所を検索できません
description: ACSD-66041 パッチを適用して、アイルランド（IE）の郵便番号が CountryID がないために集荷場所で検索できなかったAdobe Commerceの問題を修正してください。
feature: Shipping/Delivery, Shopping Cart
role: Admin, Developer
type: Troubleshooting
exl-id: 4c33da14-38b2-4a3c-a680-849b62dfb896
source-git-commit: fcbc85eaa6aceb5c02929d5b9dbee24f184c03b4
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 0%

---

# ACSD-66041: アイルランド（IE）の郵便番号が、`CountryID` ードの欠落により集荷場所で検索できない

ACSD-66041 パッチは、`CountryID` ールが見つからないためにアイルランド（IE）のポストコードがピックアップ場所で検索できない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.66 がインストールされている場合に使用できます。 パッチ ID は ACSD-66041 です。 この問題はAdobe Commerce 2.4.9 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p5

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.8

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

アイルランド（IE）の郵便番号は、`CountryID` が欠落しているため、集荷場所で検索できません。

<u> 再現手順 </u>:

1. 次のGraphQL クエリを実行します。

   ```graphql
   query getStoresTestError($term: String!, $radius: Int!) {
       pickupLocations(
           sort: { distance: ASC }
           area: { radius: $radius, search_term: $term }
       ) {
           items {
                   pickup_location_code
                   name
                   description
   		    latitude
   		    longitude
   		    country_id
   		    region
   		    city
   		    street
   		    postcode
   		    phone
           }
       }
   }
   ```

1. 次の変数を使用します。

   ```
   {
       "radius": 81,
       "term": "dublin:IE"
   }
   ```

<u> 期待される結果 </u>:

アイルランドの郵便番号は、集荷場所を検索するために使用できます。

<u> 実際の結果 </u>:

* *内部サーバーエラー* が返されます。
* `var/log/exception.log` には、次のエラーが含まれます。

  ```
  report.ERROR: Provided countryId does not exist.  {"exception":"[object] (GraphQL\\Error\\Error(code: 0): Provided countryId does not exist.
  ```

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
