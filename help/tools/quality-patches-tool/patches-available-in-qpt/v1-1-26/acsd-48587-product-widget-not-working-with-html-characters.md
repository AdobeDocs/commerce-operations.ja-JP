---
title: 「ACSD-48587:HTMLキャラクターを含む SKU で product ウィジェットが機能しない」
description: ACSD-48587 パッチを適用すると、products ウィジェットのマッチングルール内のHTMLの特殊文字によって、一致する商品が表示されないAdobe Commerceの問題を修正できます。
feature: Admin Workspace, CMS, Orders, Products
role: Admin
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# ACSD-48587:HTMLキャラクターを含む SKU で product ウィジェットが機能しない

ACSD-48587 パッチでは、products ウィジェットのマッチングルール内のHTMLの特殊文字によって、一致する商品が表示されない問題が修正されています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.26 がインストールされている場合に使用できます。 パッチ ID は ACSD-48587 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.7 ～ 2.4.6

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

製品ウィジェットが、*&quot;&amp;&quot;* 記号を含む SKU で機能しません。

<u> 再現手順 </u>:

1. SKU に *&quot;&amp;&quot;* を含む製品を作成します（例：s000&amp;01）。
1. *ページビルダー* でCMSページのコンテンツを編集する。
1. 製品ウィジェットを追加します。
1. ウィジェットを編集し、**[!UICONTROL Select Products by]** = **[!UICONTROL SKU]** を設定します。
1. 製品 SKU フィールドに *&quot;&amp;&quot;* を含む SKU を入力します。
1. コンテンツとCMSページを保存します。
1. *ページビルダーのプレビュー* および製品ストアフロントについては、*CMS ページ* のコンテンツを確認してください。

<u> 期待される結果 </u>:

SKU に *&quot;&amp;&quot;* が含まれている製品は、ページビルダーのプレビューとストアフロントに表示されます。

<u> 実際の結果 </u>:

SKU に *&quot;&amp;&quot;* が含まれている製品は、ページビルダーのプレビューには表示されません。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Sourceオンプレミス：[[!DNL Quality Patches Tool] > Usage](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in the [!DNL Quality Patches Tool] guide.
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)」を参照してください。
