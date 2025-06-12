---
title: ACSD-51120:CMS ブロックを含むCMS ページのGraphQL GET リクエストキャッシュがクリアされない
description: ACSD-51120 パッチを適用して、CMS ブロックを含んだCMS ページのGraphQL GET リクエストキャッシュがクリアされないAdobe Commerceの問題を修正してください。
exl-id: e1b84db0-2441-4729-aeeb-8486a623aebf
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# ACSD-51120:CMS ブロックを含むCMS ページのGraphQL GET リクエストキャッシュがクリアされない

ACSD-51120 パッチでは、ステージングアップデートによって更新されたGET ブロックを含んだCMS ページのGraphQL CMS リクエストキャッシュがクリアされない問題が修正されています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.33 がインストールされている場合に使用できます。 パッチ ID は ACSD-51120 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2-p2

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.7 ～ 2.4.2-p2

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

ステージングアップデートにより更新されたCMS ブロックを含むCMS ページのGraphQL GET リクエストキャッシュがクリアされない。

<u> 再現手順 </u>:

1. CMS ブロックを作成します。
1. [!DNL Page Builder] を使用して、CMS ブロックをCMS ページに含めます。
1. GET リクエストを使用して、指定されたCMS クエリを使用してGraphQL ページを取得します。

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

1. GraphQLの応答が [!DNL Varnish] にキャッシュされていることを確認します。
1. ブロックに対してスケジュールされた更新を作成します。
1. スケジュールされた更新が適用されるのを待ってから、cron ジョブを実行してスケジュールされた更新を適用します。
1. GET リクエストを使用して、指定されたCMS クエリを使用してGraphQL ページを再度取得します。

<u> 期待される結果 </u>:

応答には、更新されたコンテンツが表示されます。

<u> 実際の結果 </u>:

応答には古いコンテンツが引き続き表示されます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md)[!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。


## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)」を参照してください。
