---
title: ACSD-49839：共有カタログの価格と構造がエラーをスロー
description: ACSD-49839 パッチを適用すると、商品の SKU に一重引用符または二重引用符が含まれている場合、共有カタログの価格と構造が管理者でエラーをスローするAdobe Commerceの問題を修正できます。
feature: Admin Workspace, Catalog Management, Categories
role: Admin
exl-id: b74e3926-16c8-4222-b642-ed1b7095dea4
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 0%

---

# ACSD-49839：共有カタログの価格と構造がエラーをスロー

製品の SKU に一重引用符または二重引用符が含まれている場合、共有カタログの価格と構造が管理者でエラーをスローする問題が、ACSD-49839 パッチで修正されました。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.29 がインストールされている場合に使用できます。 パッチ ID は ACSD-49839 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p1

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.7 ～ 2.4.6

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

製品の SKU に一重引用符または二重引用符が含まれている場合、共有カタログの価格と構造により、管理者でエラーがスローされる。

<u> 再現手順 </u>:

1. 特殊文字（二重引用符など）を使用して、一部の製品 SKU を設定します。
   *[Product&quot;12, Product&quot;14, Product&quot;15]*。
1. **[!UICONTROL Admin]**/**[!UICONTROL Catalog]**/**[!UICONTROL Shared Catalog]**/**[!UICONTROL Add Shared Catalog]** に移動します（例：*[共有カタログをテスト]*）。
1. すべての **[!UICONTROL Products and Categories]**/**[!UICONTROL Generate Catalog]**/**[!UICONTROL Save]** を割り当てます。
1. **[!UICONTROL Admin]**/**[!UICONTROL Catalog]**/**[!UICONTROL Shared Catalog]**/**[!UICONTROL Test Shared Catalog]**/**[!UICONTROL Action]**/**[!UICONTROL Set Pricing and Structure]** に移動します。
1. すべてのカテゴリと製品を選択するには、*[!UICONTROL Root Catalog]* をマークします。
1. ネットワークパネルでAJAX リクエストを確認します。

<u> 期待される結果 </u>:

製品の SKU に一重引用符または二重引用符が含まれている場合、共有カタログの価格と構造で、管理者にエラーが表示されない。

<u> 実際の結果 </u>:

製品の SKU に一重引用符または二重引用符が含まれている場合、共有カタログの価格と構造により、管理者にエラーが発生する。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)」を参照してください。
