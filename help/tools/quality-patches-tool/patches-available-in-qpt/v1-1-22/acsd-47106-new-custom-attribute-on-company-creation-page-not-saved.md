---
title: ACSD-47106：会社作成ページの新しいカスタム属性が保存されない
description: ACSD-47106 パッチを適用すると、会社作成ページの新しいカスタム属性に値を保存できないAdobe Commerceの問題を修正できます。
feature: Attributes, B2B, Companies
role: Developer
exl-id: 5835760d-fca1-44ba-aa5e-8797258c7c75
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# ACSD-47106：会社作成ページの新しいカスタム属性が保存されない

ACSD-47106 パッチは、会社作成ページの新しいカスタム属性に値を保存できない問題を修正しました。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.22 がインストールされている場合に使用できます。 パッチ ID は ACSD-47106 です。 この問題はAdobe Commerce 2.4.6 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.5-p1

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

会社作成ページの新しいカスタム属性に値を保存することはできません。

<u> 前提条件 </u>:

* B2B モジュールがインストールされている。

<u> 再現手順 </u>:

1. Commerce管理者/ **[!UICONTROL Stores]** / **[!UICONTROL Attributes]** / **[!UICONTROL Customer]** / **[!UICONTROL Add New Attribute]** に移動します。
1. 新しい属性 _Test 01_ を作成します。
1. Commerce管理者/ **[!UICONTROL Customers]** / **[!UICONTROL Companies]** /に移動して、必要な詳細をすべて含んだ新しい会社を作成します。
1. カスタム属性に値を追加してみてください _Test 01_。
1. カスタム属性の値を更新してみてください _Test 01_。

<u> 期待される結果 </u>:

変更内容が保存されます。

<u> 実際の結果 </u>:

変更は保存されません。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)」を参照してください。
