---
title: 'ACSD-51120: CMS ブロックを含むCMS ページでGraphQL GET リクエストキャッシュがクリアされない'
description: CMS ブロックを含むCMS ページでGraphQL GET リクエストキャッシュがクリアされないAdobe Commerceの問題を修正するには、ACSD-51120 パッチを適用します。
exl-id: e1b84db0-2441-4729-aeeb-8486a623aebf
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# ACSD-51120: CMS ブロックを含むCMS ページでGraphQL GET リクエストキャッシュがクリアされない

ACSD-51120 パッチは、ステージング更新によって更新されるGraphQL ブロックを含むCMS ページで、CMS GET リクエストキャッシュがクリアされない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.33がインストールされている場合に利用できます。 パッチ IDはACSD-51120です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2-p2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.7 - 2.4.2-p2

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

ステージング更新によって更新されるCMS ブロックを含むCMS ページでは、GraphQL GET リクエストキャッシュがクリアされません。

<u>複製する手順</u>:

1. CMS ブロックを作成します。
1. [!DNL Page Builder]を使用して、CMS ブロックをCMS ページに含めます。
1. GET リクエストを使用して、特定のGraphQL クエリを使用してCMS ページを取得します。

   ```GraphQL
   {
   cmsPage( identifier: "<CMS PAGE IDENTIFIER>") {
       content
       content_heading
       identifier
       meta_description
       meta_keywords
       meta_title
       page_layout
       title
       url_key
   }
   }
   ```

1. GraphQLの応答が[!DNL Varnish]にキャッシュされていることを確認してください。
1. ブロックのスケジュールされた更新を作成します。
1. スケジュールされた更新が適用されるのを待ち、cron ジョブを実行してスケジュールされた更新を適用します。
1. GET リクエストを使用して、指定されたGraphQL クエリを使用して、CMS ページを再度フェッチします。

<u>期待される結果</u>:

応答は、更新されたコンテンツを示します。

<u>実際の結果</u>:

応答は古いコンテンツを表示します。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。


## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
