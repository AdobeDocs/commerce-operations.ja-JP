---
title: 'ACSD-49973: [!DNL GraphQL]を介したバンドル製品の取得時のパフォーマンスが向上しました'
description: ACSD-49973 パッチを適用して、 [!DNL GraphQL]経由でバンドルされた製品を取得する際にパフォーマンスが低下するAdobe Commerceの問題を修正します。
feature: GraphQL, Products
role: Admin
exl-id: d4817522-65dd-4ac8-8759-8518818684ed
type: Troubleshooting
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 0%

---

# ACSD-49973: [!DNL GraphQL]を介したバンドル製品の取得時のパフォーマンスが向上しました

ACSD-49973 パッチは、[!DNL GraphQL]を介してバンドルされた製品を取得する際のパフォーマンスを向上させます。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.30がインストールされている場合に利用できます。 パッチ IDはACSD-49973です。 この問題は、Adobe Commerce 2.4.7で修正されています。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4-p2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.4-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

[!DNL GraphQL]を介してバンドル製品を取得すると、パフォーマンスの低下が発生します。

<u>前提条件</u>:

[Performance toolkit](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/generate-data.html)を使用して2000 バンドル製品を作成します。

<u>複製する手順</u>:

1. [!DNL DB] クエリロガーを有効にします。

   ```shell
   bin/magento dev:query-log:enable
   ```

1. 次の[!DNL GraphQL] クエリを実行します。

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

1. `catalog_product_bundle_selection` テーブルへのリクエストについては、`var/log/db.log`を確認してください。

<u>期待される結果</u>:

`catalog_product_bundle_selection` テーブルへのリクエストは、`var/log/db.log`に存在してはなりません。

<u>実際の結果</u>:

同時にトリガーされる`catalog_product_bundle_selection` テーブルへのリクエストが2000件あり、パフォーマンスが低下します。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > Commerce クラウドインフラストラクチャ上のパッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」ガイド

## 関連トピックス

* [[!DNL Quality Patches Tool]  リリース：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを確認します
* [Commerce実装プレイブックのデータベーステーブルを修正するためのベストプラクティス &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications)

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
