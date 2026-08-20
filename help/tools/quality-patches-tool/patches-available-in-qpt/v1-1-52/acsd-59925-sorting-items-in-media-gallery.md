---
title: 'ACSD-59925: [!UICONTROL Media Gallery]のアイテムをGraphQLの位置で並べ替える'
description: ACSD-59925 パッチを適用して、[!UICONTROL Media Gallery]内の項目が位置で並べ替えられないAdobe Commerceの問題を修正し、誤った表示順序が発生します。
feature: Media, GraphQL
role: Admin, Developer
exl-id: a4dd840f-44d2-40dc-b0e1-13d55b688204
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# ACSD-59925: [!UICONTROL Media Gallery]内の項目をGraphQLの位置で並べ替える

ACSD-59925 パッチでは、[!UICONTROL Media Gallery]内の項目が位置で並べ替えられない問題が修正され、誤った表示順序が発生します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.52がインストールされている場合に利用できます。 パッチ IDはACSD-59925です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p3

**Adobe Commerceのバージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p2

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

[!UICONTROL Media Gallery]内の項目は位置で並べ替えられないため、表示順序が正しくありません。

<u>複製する手順</u>:

1. 商品の作成/編集。
1. 2つ以上の画像を追加して保存します。
1. 同じ商品を編集しますが、今回は最後の画像を最初の位置にドラッグします。
1. 製品を保存します。
1. 再インデックス：
1. GraphQL クライアントに移動します。
1. GraphQL クエリの実行：

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

<u>期待される結果</u>:

`media_gallery`内の項目は、位置で並べ替えられます。

<u>実際の結果</u>:

`media_gallery`の項目は、位置で並べ替えられません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
