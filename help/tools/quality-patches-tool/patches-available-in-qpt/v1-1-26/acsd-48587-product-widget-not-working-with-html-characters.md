---
title: ACSD-48587:HTML文字を含むSKUで製品ウィジェットが機能しない
description: Acsd-48587 パッチを適用して、HTMLの特殊文字がproducts widgetの一致ルールに含まれていて、一致する商品が表示されないAdobe Commerceの問題を修正します。
feature: Admin Workspace, CMS, Orders, Products
role: Admin
exl-id: c3e31835-03be-46b4-a080-09edf55b5b4e
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# ACSD-48587:HTML文字を含むSKUで製品ウィジェットが機能しない

ACSD-48587 パッチでは、製品ウィジェットの一致ルール内のHTML特殊文字が一致する製品を表示できない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.26がインストールされている場合に利用できます。 パッチ IDはACSD-48587です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.7 - 2.4.6

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

製品ウィジェットは、*&quot;&amp;&quot;* シンボルを含むSKUで機能しません。

<u>複製する手順</u>:

1. SKUに&#x200B;*&quot;&amp;&quot;*&#x200B;を含む製品（例：s000&amp;01）を作成します。
1. *ページビルダー*&#x200B;でCMS ページの内容を編集します。
1. 製品ウィジェットを追加します。
1. ウィジェットを編集し、**[!UICONTROL Select Products by]** = **[!UICONTROL SKU]**&#x200B;を設定します。
1. 製品SKU フィールドに&#x200B;*&quot;&amp;&quot;*&#x200B;を含むSKUを入力します。
1. コンテンツとCMS ページを保存します。
1. *ページビルダーのプレビュー*&#x200B;と製品ストアフロントについては、*CMS Page*&#x200B;のコンテンツを確認してください。

<u>期待される結果</u>:

SKUに&#x200B;*&quot;&amp;&quot;*&#x200B;が含まれる商品は、ページビルダーのプレビューとストアフロントに表示されます。

<u>実際の結果</u>:

SKUに&#x200B;*&quot;&amp;&quot;*&#x200B;が含まれる製品は、ページビルダープレビューに表示されません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
