---
title: ACSD-49286：複数の製品ウィジェットが存在する場合、製品がカートに2回追加される
description: ACSD-49286 パッチを適用して、ページに複数の商品ウィジェットが存在する場合に商品がカートに2回追加されるAdobe Commerceの問題を修正します。
feature: Admin Workspace, Orders, Products, Shopping Cart
role: Admin
exl-id: 03fdaafe-5566-4b75-a0eb-e0cba3dad3e7
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '435'
ht-degree: 0%

---

# ACSD-49286：複数の製品ウィジェットが存在する場合、製品がカートに2回追加される

ACSD-49286 パッチは、複数の製品ウィジェットがページに存在する場合に、製品がカートに2回追加される問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.28がインストールされている場合に利用できます。 パッチ IDはACSD-49286です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3 - 2.4.6

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

ページに複数の製品ウィジェットがある場合、製品がカートに2回追加されます。

<u>複製する手順</u>:

1. 管理者にログインして、**[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Page]** > **[!UICONTROL Home Page]**&#x200B;に移動します
1. コンテンツセクションで、[!DNL Page Builder]を使用して&#x200B;**[!UICONTROL Edit]**&#x200B;をクリックします。
1. **[!UICONTROL Content]**&#x200B;に2つの行要素を追加します。
1. 両方の行エレメントに製品を追加します。
1. 最初の行で、製品の外観を[!UICONTROL Product Grid]に設定し、表示するカテゴリを選択します。
1. 2行目で、製品の外観を[!UICONTROL Product Carousel]に設定し、表示する他のカテゴリを選択します。
1. ストアフロント **[!UICONTROL Home Page]**&#x200B;に移動し、Product Gridから1つの製品を追加します。
1. [!UICONTROL Product Carousel]から別の製品を追加します。

<u>期待される結果</u>:

[!UICONTROL Product Grid]から商品をカートに追加した後、商品の数量が倍増しないようにします。

<u>実際の結果</u>:

[!UICONTROL Product Grid]から商品をカートに追加すると、商品の数量が2倍になります。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。 

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
