---
title: ACSD-65777:「MediaGallery」GraphQL リクエストで商品画像タイプの「types」フィールドが見つからない
description: ACSD-65777 パッチを適用して、「MediaGallery」GraphQL リクエストの商品画像タイプに「types」フィールドが見つからないAdobe Commerceの問題を修正します。
feature: GraphQL, Media
role: Admin, Developer
type: Troubleshooting
exl-id: 20866963-54a3-4859-9c2d-716945e37156
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---

# ACSD-65777: `MediaGallery` GraphQL リクエストに商品イメージタイプの&#x200B;**[!UICONTROL types]** フィールドがありません

ACSD-65777 パッチは、`MediaGallery` GraphQL リクエストで製品の画像タイプに&#x200B;**[!UICONTROL types]** フィールドが見つからない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.66がインストールされている場合に利用できます。 パッチ IDはACSD-65777です。 この問題は、Adobe Commerce 2.4.9で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.8

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.8

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

`MediaGallery` GraphQL リクエストを介してメディアデータを取得する際に、商品の画像タイプに&#x200B;**[!UICONTROL types]** フィールドが見つかりません。

<u>複製する手順</u>:

1. 商品を作成する。
1. 商品に画像をアップロードします。
1. 次のGraphQLを使用してメディアデータを取得します。

   ```text
   query{
     products(search:"",filter:{sku:{eq:"p1"}})\{
       items{
         media_gallery{
           disabled
           label
           position
           url
         }
         media_gallery_entries\{
           types
         }
       }
     }
   }
   ```

<u>期待される結果</u>:

`media_gallery` GraphQL インターフェイスには、**[!UICONTROL types]** フィールドを含める必要があります。

<u>実際の結果</u>:

`media_gallery`にメディア **[!UICONTROL types]** フィールドが含まれていません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
