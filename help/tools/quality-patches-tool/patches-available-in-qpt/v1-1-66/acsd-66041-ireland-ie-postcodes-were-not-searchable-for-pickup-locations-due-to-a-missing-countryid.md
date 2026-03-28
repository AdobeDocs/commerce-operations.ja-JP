---
title: 'ACSD-66041: アイルランド （IE） ポストコードが、CountryIDがないため、受け取り場所で検索できない'
description: 国IDが欠落しているため、アイルランド（IE）のポストコードが受け取り場所を検索できないAdobe Commerceの問題を修正するには、ACSD-66041 パッチを適用します。
feature: Shipping/Delivery, Shopping Cart
role: Admin, Developer
type: Troubleshooting
exl-id: 4c33da14-38b2-4a3c-a680-849b62dfb896
source-git-commit: 7054a5286f01e26e324401f4d8505e4e0faed93e
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 0%

---

# ACSD-66041: `CountryID`が見つからないため、アイルランド （IE） ポストコードで受け取り場所を検索できません

ACSD-66041 パッチは、欠落している`CountryID`が原因でアイルランド （IE） ポストコードがピックアップ場所で検索できない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.66がインストールされている場合に利用できます。 パッチ IDはACSD-66041です。 この問題は、Adobe Commerce 2.4.9で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p5

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.8

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

アイルランド （IE） ポストコードは、`CountryID`が見つからないため、受け取り場所を検索できません。

<u>複製する手順</u>:

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

<u>期待される結果</u>:

アイルランドの郵便番号は、受け取り場所を検索するために利用できます。

<u>実際の結果</u>:

* *内部サーバーエラー*&#x200B;が返されます。
* `var/log/exception.log`に次のエラーが含まれています：

  ```
  report.ERROR: Provided countryId does not exist.  {"exception":"[object] (GraphQL\\Error\\Error(code: 0): Provided countryId does not exist.
  ```

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool]  ガイドの](/help/tools/quality-patches-tool/usage.md)>使用状況[!DNL Quality Patches Tool]。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
