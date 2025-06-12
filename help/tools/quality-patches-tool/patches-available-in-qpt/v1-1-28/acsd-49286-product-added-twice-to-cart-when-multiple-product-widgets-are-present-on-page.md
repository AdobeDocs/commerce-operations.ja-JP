---
title: ACSD-49286：複数の製品ウィジェットが存在する場合に、買い物かごに製品が 2 回追加される
description: ページ上に複数の商品ウィジェットが存在する場合に、商品が買い物かごに 2 回追加されるAdobe Commerceの問題を修正するために、ACSD-49286 パッチを適用します。
feature: Admin Workspace, Orders, Products, Shopping Cart
role: Admin
exl-id: 03fdaafe-5566-4b75-a0eb-e0cba3dad3e7
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# ACSD-49286：複数の製品ウィジェットが存在する場合に、買い物かごに製品が 2 回追加される

ACSD-49286 パッチは、ページに複数の製品ウィジェットが存在する場合に、製品が買い物かごに 2 回追加される問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.28 がインストールされている場合に使用できます。 パッチ ID は ACSD-49286 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p1

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3 ～ 2.4.6

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

ページに複数の製品ウィジェットが存在する場合、製品は買い物かごに 2 回追加されます。

<u> 再現手順 </u>:

1. 管理者にログインし、**[!UICONTROL Admin]**/**[!UICONTROL Content]**/**[!UICONTROL Page]**/**[!UICONTROL Home Page]** に移動します
1. 「コンテンツ」セクションで、「[!DNL Page Builder] を使用して **[!UICONTROL Edit]** をクリックします。
1. **[!UICONTROL Content]** に 2 つの行要素を追加します。
1. 製品を両方の行要素に追加します。
1. 最初の行で、製品の外観を [!UICONTROL Product Grid] に設定し、表示するカテゴリを選択します。
1. 2 行目で、製品の外観を [!UICONTROL Product Carousel] に設定し、表示するその他のカテゴリを選択します。
1. ストアフロントの **[!UICONTROL Home Page]** に移動して、製品グリッドから 1 つの製品を追加します。
1. [!UICONTROL Product Carousel] から別の製品を追加します。

<u> 期待される結果 </u>:

[!UICONTROL Product Grid] から買い物かごに製品を追加した後で、製品数量を倍増しないでください。

<u> 実際の結果 </u>:

[!UICONTROL Product Grid] から買い物かごに製品を追加すると、製品数が倍増します。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md)[!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。 

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)」を参照してください。
