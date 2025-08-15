---
title: ACSD-65777:「MediaGallery」GraphQL リクエストに商品の画像タイプの「types」フィールドがありません
description: ACSD-65777 パッチを適用すると、「MediaGallery」GraphQL リクエストで商品の画像タイプの「types」フィールドが見つからなかったAdobe Commerceの問題を修正できます。
feature: GraphQL, Media
role: Admin, Developer
type: Troubleshooting
exl-id: 20866963-54a3-4859-9c2d-716945e37156
source-git-commit: 5bcafd22647f9a87596c4f2d852bda76a5d6427b
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 0%

---

# ACSD-65777:**[!UICONTROL types]** GraphQL リクエストに商品 `MediaGallery` 像タイプの画像フィールドがありません

ACSD-65777 パッチでは、**[!UICONTROL types]** GraphQL リクエストの product image types の `MediaGallery` フィールドが見つからなかった問題を修正しています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.66 がインストールされている場合に使用できます。 パッチ ID は ACSD-65777 です。 この問題はAdobe Commerce 2.4.9 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.8

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.8

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

**[!UICONTROL types]** GraphQL リクエストを介してメディアデータを取得する場合、商品画像タイプの `MediaGallery` フィールドがありません。

<u> 再現手順 </u>:

1. 商品を作成します。
1. 製品に画像をアップロードします。
1. 次のGraphQLを使用してメディアデータを取得します。

   ```
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

<u> 期待される結果 </u>:

`media_gallery` GraphQL インターフェイスには、**[!UICONTROL types]** フィールドを含める必要があります。

<u> 実際の結果 </u>:

`media_gallery` には、メディア **[!UICONTROL types]** フィールドが含まれていません。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
