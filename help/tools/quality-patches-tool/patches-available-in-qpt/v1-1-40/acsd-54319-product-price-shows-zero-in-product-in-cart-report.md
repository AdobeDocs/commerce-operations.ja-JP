---
title: ACSD-54319:*[!UICONTROL Products in Carts]* レポートで製品価格がゼロと表示される
description: '*[!UICONTROL Products in Carts]* レポートで製品価格がゼロと表示されるAdobe Commerceの問題を修正するには、ACSD-54319 パッチを適用してください'
feature: Reporting, Products
role: Admin, Developer
exl-id: 10052d32-99f8-4b45-9fe9-a4c45bcaaa44
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---

# ACSD-54319：製品価格がレポートにゼロ *[!UICONTROL Products in Carts]* 表示される

ACSD-54319 パッチは、レポートで製品価格がゼロと表示される問題 *[!UICONTROL Products in Carts]* 修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.40 がインストールされている場合に使用できます。 パッチ ID は ACSD-54319 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p3

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2 ～ 2.4.5-p5

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

レポートには製品価格がゼロ *[!UICONTROL Products in Carts]* 表示されます。

<u> 再現手順 </u>:

1. **[!UICONTROL Catalog Price Scope]**/**[!UICONTROL Website]**/**[!UICONTROL Stores]**/**[!UICONTROL Configuration]**/**[!UICONTROL Catalog]**/**[!UICONTROL Catalog]** から **[!UICONTROL Price]** を **[!UICONTROL Catalog Price Scope]** に設定します。
1. **[!UICONTROL Stores]** > **[!UICONTROL All Stores]** で 2 つ目の web サイトを作成します。
1. **[!UICONTROL Catalog]**/**[!UICONTROL Products]** から製品を作成します。
1. この製品を 2 番目の web サイトにのみ割り当てます。
1. 2 番目の web サイトから買い物かごに製品を追加します。
1. **[!UICONTROL Admin]**/**[!UICONTROL Reports]**/**[!UICONTROL Marketing]**/**[!UICONTROL Products In Carts]** グリッドに移動します。
1. グリッドの *[!UICONTROL Price]* 列を確認 *[!UICONTROL Products In Carts]* ます。

<u> 期待される結果 </u>:

レポートグリッドで製品価格がゼロ *[!UICONTROL Products in Carts]* はない。

<u> 実際の結果 </u>:

レポートグリッドで製品価格 *[!UICONTROL Products in Carts]* ゼロです。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md)[!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[[!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html): Search for patches[!DNL Quality Patches Tool]」を参照してください。
