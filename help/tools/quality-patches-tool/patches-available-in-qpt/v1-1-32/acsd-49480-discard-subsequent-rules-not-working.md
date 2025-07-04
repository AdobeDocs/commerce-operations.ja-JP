---
title: ACSD-49480：機能しない後続のルールを破棄する
description: ACSD-49480 パッチを適用して、[!UICONTROL Cart Price Rule - Discard Subsequent Rules] が意図したとおりに動作しないAdobe Commerceの問題を修正してください。
feature: Price Rules
role: Admin
exl-id: 1919043b-99a8-46a2-94df-9285c05bec7b
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%

---

# ACSD-49480:[!UICONTROL Cart Price Rule - Discard Subsequent Rules] が意図したとおりに動作しない

ACSD-49480 パッチは、[!UICONTROL Cart Price Rule - Discard Subsequent Rules] が意図したとおりに動作しない問題を修正します。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.32 がインストールされている場合に使用できます。 パッチ ID は ACSD-49480 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.5

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

[!UICONTROL Cart Price Rule - Discard Subsequent Rules] は意図したとおりに動作していません。

<u> 再現手順 </u>:

1. 「**[!UICONTROL Actions]**」タブの *製品 ID 1* に 10 ドルの割引を与えるクーポンコード（名前は *TEST*）で、[!UICONTROL Discard Subsequent Rules] を *[!UICONTROL Yes]* に、[!UICONTROL Priority] を *1* に設定した **[!UICONTROL Cart Price Rule]** ールを作成します。
1. **[!UICONTROL Actions]** タブの *製品 ID 2* が *2* に設定されている場合に$5 割引となるクーポンコードのない別の **[!UICONTROL Cart Price Rule]** ール [!UICONTROL Priority] 作成します。 ここでは、これが *製品 ID 2* のグローバルセールであると仮定します。
1. フロントエンドサイトに移動し、*製品 ID 1* と *製品 ID 2* を買い物かごに追加します。
1. *TEST* クーポンコードを適用します。

<u> 期待される結果 </u>

* *商品 ID 1* に *割引 1* が適用されます。
* *割引 2* が *製品 ID 2* に適用されます。

<u> 実績 </u>

* *商品 ID 1* に適用されるのは *割引 1* のみです。
* *割引 2* は *製品 ID 2* には適用されません。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)」を参照してください。
