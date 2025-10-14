---
title: ACSD-54965：グリッド [!UICONTROL Visual Merchandising] 正しい素材が表示されない
description: ACSD-54965 パッチを適用すると、商品がカスタム在庫に割り当てられたときに [!UICONTROL Visual Merchandising] グリッドに正しい在庫が表示されないAdobe Commerceの問題を修正できます。
feature: Merchandising, Categories
role: Admin, Developer
exl-id: bd8a3547-1d84-4a17-b006-b35d92256211
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# ACSD-54965：グリッド [!UICONTROL Visual Merchandising] 正しい素材が表示されない

ACSD-54965 パッチは、製品がカスタム在庫に割り当てられたときに、[!UICONTROL Visual Merchandising] グリッドに正しい在庫が表示されない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.45 がインストールされている場合に使用できます。 パッチ ID は ACSD-54965 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p2

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5 ～ 2.4.5-p5

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

製品がカスタム在庫に割り当てられると、[!UICONTROL Visual Merchandising] グリッドに正しい在庫が表示されません。

<u> 再現手順 </u>:

1. 新規ソースを作成します。
1. 新しい在庫を作成します。
1. 2 つの製品を作成します。
   * カスタム在庫のみを持つ 1 つの製品。
   * デフォルトの在庫のみを持つ製品。
1. これらの製品をカテゴリに追加します。
1. [!UICONTROL visual Merchandising] グリッド（*[!UICONTROL Products in Category]*）に移動します。

<u> 実際の結果 </u>:

*[!UICONTROL All Store Views]* の範囲では、カスタム在庫を持つ製品には数量が表示されません。 *[!UICONTROL Default Store View]* の範囲が選択され、カスタム在庫に製品の数量が表示される場合にのみ使用します。

<u> 期待される結果 </u>:

範囲が *[!UICONTROL All Store Views]* の場合、グリッドにはすべての在庫情報が表示されます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 &#x200B;](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [&#x200B; アップグレードとパッチ &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [&#x200B; を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[[!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja): Search for patches[!DNL Quality Patches Tool]」を参照してください。
