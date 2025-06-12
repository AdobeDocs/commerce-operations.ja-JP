---
title: ACSD-52202：デフォルト以外の在庫が順番に 0 数量に設定されると、デフォルトの在庫販売可能数量がエラーで 0 に変更される
description: 注文でデフォルト以外の在庫が数量 0 に設定されている場合に、デフォルトの在庫販売可能数量が誤って 0 に変わるAdobe Commerceの問題を修正するために、ACSD-52202 パッチを適用します。
feature: Inventory, Products
role: Admin
exl-id: 2ba5cc3b-9774-49f6-948f-371ab3c0c9df
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 0%

---

# ACSD-52202：注文でデフォルト以外の在庫が数量 0 に設定されると、デフォルトの在庫販売可能数量がエラーで 0 に変更される

ACSD-52202 パッチは、注文でデフォルト以外の在庫が 0 数量に設定されている場合に、デフォルトの在庫販売可能数量（数量）がエラーで 0 に変更される問題を修正します。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.35 がインストールされている場合に使用できます。 パッチ ID は ACSD-52202 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p1

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3 ～ 2.4.6-p1

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

注文でデフォルト以外の在庫が 0 数量に設定されている場合、デフォルトの在庫販売可能数量がエラーで 0 に変更される。

<u> 再現手順 </u>:

1. [!DNL Admin] にログインします。
1. **website2** を作成します。
1. カスタム **source2** を作成します。
1. カスタム **stock2** を作成します。
1. **source2** と **stock2** を **website1** に割り当て、デフォルトのソースと stock をデフォルトの web サイトに割り当てます。
1. シンプルな製品を作成し、デフォルトソースに **qty** = *10*、ソースに **qty** = *1* を割り当てます **source2**。
1. **website2** の場合は、**qty** = *1* の注文を行います。
1. 請求書と出荷を作成します。
1. 簡易製品 **販売可能数量** を確認します。

<u> 期待される結果 </u>:

**source2** の **salable quantity *=*10**。

<u> 実際の結果 </u>:

両方のソースの **販売可能数量** = *0*。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md)[!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)」を参照してください。
