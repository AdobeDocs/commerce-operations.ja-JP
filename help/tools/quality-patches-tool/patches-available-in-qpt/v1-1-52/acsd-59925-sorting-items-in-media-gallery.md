---
title: 「ACSD-59925:GraphQLでの位置による [!UICONTROL Media Gallery] 内の項目の並べ替え」
description: ACSD-59925 パッチを適用すると、[!UICONTROL Media Gallery] 内の項目が位置で並べ替えられず、誤った表示順につながるAdobe Commerceの問題を修正できます。
feature: Media, GraphQL
role: Admin, Developer
source-git-commit: 97e3ab77e7c8f5f1efd9b616b5e1d198a1b41ab0
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---

# ACSD-59925:GraphQL内の位置で [!UICONTROL Media Gallery] 内の項目を並べ替える

ACSD-59925 パッチでは、[!UICONTROL Media Gallery] ージ内の項目が位置で並べ替えられず、誤った表示順序につながる問題が修正されています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.52 がインストールされている場合に使用できます。 パッチ ID は ACSD-59925 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p3

**Adobe Commerce バージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p2

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

[!UICONTROL Media Gallery] 内の項目が位置で並べ替えられないので、間違った表示順序になります。

<u> 再現手順 </u>:

1. 商品を作成/編集します。
1. 複数の画像を追加して保存します。
1. 同じ製品を編集しますが、今回は最後の画像を最初の位置にドラッグします。
1. 商品を保存します。
1. 再インデックス。
1. GraphQL クライアントに移動します。
1. GraphQL クエリを実行します。

   ```GraphQL
   {
     products(filter: { sku: { eq: "24-MB01" } }) {
        items {
          name
          sku
          url_key
          stock_status
          media_gallery {
             __typename
             ... on ProductVideo {
               video_content {
                 video_url
                 video_title
                 __typename
               }
               __typename
             }
             ... on ProductImage {
               url
               __typename
             }
               position
               disabled
            }
         }
         total_count
         page_info {
         page_size
        }
      }
    }
   ```

<u> 期待される結果 </u>:

`media_gallery` 内の項目は位置順に並べ替えられます。

<u> 実際の結果 </u>:

`media_gallery` 内の項目は、位置で並べ替えられていません。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Sourceオンプレミス：[[!DNL Quality Patches Tool] > Usage](/help/tools/quality-patches-tool/usage.md) in the [!DNL Quality Patches Tool] guide.
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)」を参照してください。