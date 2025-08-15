---
title: ACSD-45049：顧客の'必須'属性設定が、管理者の Web サイト範囲に応じて機能しません
description: ACSD-45049 パッチを適用すると、Adobe Commerceの問題を修正できます。この問題では、管理者の Web サイトの範囲に応じて顧客の「[!UICONTROL Is required]」属性が適切に上書きされません。
feature: Attributes, Customers
role: Admin, Developer
exl-id: 368af877-a3ec-431f-8f41-5d51354be571
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# ACSD-45049：顧客 *[!UICONTROL Is required]* 属性の設定が、管理者の web サイト範囲に応じて機能しない

ACSD-45049 パッチを適用すると、Admin の Web サイトの範囲に応じて顧客 *[!UICONTROL Is required]* 属性の設定が正しく機能しない問題が修正されます。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/usage.md) 1.1.50 がインストールされている場合に使用できます。 パッチ ID は ACSD-45049 です。 この問題はAdobe Commerce 2.4.6 で修正されました。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3-p1

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 ～ 2.4.4-p7 および 2.4.5 ～ 2.4.5-p9

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

顧客 *[!UICONTROL Is required]* 属性の設定が、管理の web サイト範囲に応じて正しく機能しない。

<u> 再現手順 </u>:

1. 2 つの web サイトを作成します。
1. **[!UICONTROL Admin]**/**[!UICONTROL Stores]**/**[!UICONTROL Customer attribute]** を開きます。
1. 新しい属性を作成し、**[!UICONTROL Is value required]** = *いいえ* に設定します。
1. デフォルトの Web サイトに切り替えて、**[!UICONTROL Is value required]** = *はい* に変更します。 もう一方の web サイトはデフォルト値になっています。
1. デフォルト以外の web サイト用に管理者から新しい顧客を作成します。

<u> 期待される結果 </u>:

デフォルト以外の web サイトの場合、この属性は必須ではありません。

<u> 実際の結果 </u>:

* 属性は、管理者で顧客を作成する際に、デフォルト以外の web サイトに対して必要です。
* ストアフロントで顧客を登録する場合、デフォルト以外の web サイトには属性は必要ありません。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md)[!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[[!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html): Search for patches[!DNL Quality Patches Tool]」を参照してください。
