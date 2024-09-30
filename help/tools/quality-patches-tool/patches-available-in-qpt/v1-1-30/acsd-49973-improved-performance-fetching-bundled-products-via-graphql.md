---
title: '「ACSD-49973: [!DNL GraphQL] を介したバンドル製品の取得でパフォーマンスが向上」'
description: ACSD-49973 パッチを適用すると、 [!DNL GraphQL] を介してバンドルされた製品を取得する際にパフォーマンスが低下するAdobe Commerceの問題を修正できます。
feature: GraphQL, Products
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 0%

---

# ACSD-49973:[!DNL GraphQL] を介したバンドル製品の取得パフォーマンスの向上

ACSD-49973 パッチにより、[!DNL GraphQL] を介したバンドル製品の取得パフォーマンスが向上します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.30 がインストールされている場合に使用できます。 パッチ ID は ACSD-49973 です。 この問題はAdobe Commerce 2.4.7 で修正されていることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4-p2

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.4-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

バンドルされた製品を [!DNL GraphQL] 経由で取得すると、パフォーマンスが低下します。

<u> 前提条件 </u>:

[Performance toolkit](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/generate-data.html) を使用して、2000 バンドル製品を作成します。

<u> 再現手順 </u>:

1. [!DNL DB] クエリロガーを有効にします。

   ```
   bin/magento dev:query-log:enable
   ```

1. 次の [!DNL GraphQL] クエリを実行します。

   ```GraphQL
   {
     products(
       search: "bundle"
       pageSize: 2000,
       sort: { relevance: DESC }
     ) {
       total_count
       items {
         name
         sku
       }
     }
   }
   ```

1. `catalog_product_bundle_selection` テーブルに対するリクエストの `var/log/db.log` を確認します。

<u> 期待される結果 </u>:

`catalog_product_bundle_selection` テーブルへのリクエストは、`var/log/db.log` に存在できません。

<u> 実際の結果 </u>:

同時にトリガーされるテーブルに対 `catalog_product_bundle_selection` るリクエストは 2000 件あり、パフォーマンスが低下します。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Sourceオンプレミス：[[!DNL Quality Patches Tool] > Usage](/help/tools/quality-patches-tool/usage.md) in the [!DNL Quality Patches Tool] guide.
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)」を参照してください。
