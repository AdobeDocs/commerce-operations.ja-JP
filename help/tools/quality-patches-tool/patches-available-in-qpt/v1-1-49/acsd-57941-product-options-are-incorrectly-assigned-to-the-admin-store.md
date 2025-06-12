---
title: ACSD-57941：製品オプションが誤って管理ストアに割り当てられている
description: ACSD-57941 パッチを適用すると、商品オプションが各ストアではなく管理ストアに誤って割り当てられるAdobe Commerceの問題を修正できます。
feature: Products
role: Admin, Developer
exl-id: a78c1797-c366-4931-b036-966d3dcf59bb
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 0%

---

# ACSD-57941：製品オプションが誤って管理ストアに割り当てられている

ACSD-57941 パッチでは、製品オプションが各ストアではなく管理ストアに誤って割り当てられる問題が修正されています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.49 がインストールされている場合に使用できます。 パッチ ID は ACSD-57941 です。 この問題はAdobe Commerce 2.4.7 で修正されました。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p3

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3 ～ 2.4.6-p7

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

製品オプションが、それぞれのストアではなく管理ストアに誤って割り当てられます。

<u> 再現手順 </u>:

1. シンプルな製品を作成します。
1. いくつかのカスタムオプションを使用して同じ製品を読み込みます。
1. **[!UICONTROL Catalog]**/**[!UICONTROL Products]** に移動し、作成した製品を開きます。 「**[!UICONTROL Customizable options]**」をクリックし、読み込んだオプションが表示されていることを確認します。
1. 同じファイルをさらに数回読み込みます。

<u> 期待される結果 </u>:

カスタムオプションが更新されます。

<u> 実際の結果 </u>:

製品のカスタムオプションが複製されます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md)[!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)」を参照してください。
