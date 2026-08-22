---
title: 'ACSD-56193: [!DNL Fastly]  キャッシュがコンテンツのステージング更新でクリアされない'
description: ACSD-56193 パッチを適用して、コンテンツのステージング更新で [!DNL Fastly]  キャッシュがクリアされないAdobe Commerceの問題を修正します。
feature: Cache, GraphQL, Staging
role: Admin, Developer
exl-id: a702ce22-cc85-4f58-8766-637a1b93d405
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---

# ACSD-56193: コンテンツのステージング更新で[!DNL Fastly] キャッシュがクリアされない

ACSD-56193 パッチは、コンテンツのステージング更新のために[!DNL Fastly] キャッシュがクリアされない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.44がインストールされている場合に利用できます。 パッチ IDはACSD-56193です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2-p2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2 - 2.4.4

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

コンテンツのステージング更新のために[!DNL Fastly/Varnish] キャッシュがクリアされません

<u>複製する手順</u>:

1. [!DNL Varnish] キャッシュをインストールして設定します。
1. スケジュールされた更新を含む静的ブロックを作成します。
1. 静的ブロックを埋め込むカテゴリを作成します。
1. 次のGraphQL クエリを使用して、カテゴリのコンテンツを取得します。

   ```GraphQL
      query GetCategories($id: String!) {
         categoryList(filters: { category_uid: { eq: $id } }) 
       {
           meta_title
           meta_keywords
           meta_description
           description
           path
           cms_block {
             content
             identifier
             title
             __typename
           }
           __typename
       }
     }
     {"id":"Mwo="}
   ```

1. このクエリを複数回実行し、応答が[!DNL Varnish]にキャッシュされていることを確認します。
1. cronを実行して、スケジュールされた変更を適用します。
1. 上記のGraphQL クエリを再度実行します。
1. 同じ静的ブロックに新しいスケジュールを作成します。
1. 5 ～ 9の番号の手順を繰り返します。

<u>期待される結果</u>:

更新されたコンテンツは、スケジュールされた更新の実行後に返されます。

<u>実際の結果</u>:

スケジュールされた更新の実行後、古いコンテンツが返されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) パッチを検索する」を参照してください。
