---
title: ACSD-48661：会社のクレジット制限のコンマ区切り記号の検証の問題
description: ACSD-48661 パッチを適用すると、Adobe Commerceの問題を修正できます。この問題では、会社のクレジット制限が 999 を超える場合、コンマ区切り記号を使用すると、検証エラーが原因で会社を保存することができません。
feature: Admin Workspace, B2B, Companies, Orders
role: Admin
exl-id: 7115226e-5942-4a8f-9dec-b1b6f665eef8
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# ACSD-48661：会社のクレジット制限のコンマ区切り記号の検証の問題

ACSD-48661 パッチでは、会社のクレジット制限が 999 を超える場合、コンマ区切り記号によって、検証エラーによる会社の保存が妨げられる問題が修正されています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.26 がインストールされている場合に使用できます。 パッチ ID は ACSD-48661 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p1

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.7 - 2.4.5-p1

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

会社のクレジット制限が 999 を超える場合、コンマ区切り記号を使用すると、検証エラーが原因で会社が保存されるのを防ぐことができます。

<u> 再現手順 </u>:

1. **[!UICONTROL Store]**/**[!UICONTROL Configuration]**/**[!UICONTROL General]**/**[!UICONTROL B2B Features]** で会社情報機能を有効にします。
1. 会社を作成し、「**[!UICONTROL Company Credit]**」タブで 999 を超えるクレジット制限を追加します。
1. 会社を保存します。
1. 会社を編集して、もう一度保存してみてください。

<u> 期待される結果 </u>:

クレジット制限を修正せずに会社を保存できます。 金額および価格の入力フィールドでは、コンマはサポートされていません。

<u> 実際の結果 </u>:

*[!UICONTROL Credit Limit]* フィールドの検証エラーのため、会社を保存できません。 Adobe Commerceでは、「[!UICONTROL Credit Limit]」フィールドがコンマを使用しない場合でも、与信限度額に対してコンマ区切り記号が自動的に追加されます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md)[!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)」を参照してください。
