---
title: ACSD-49480：後続のルールを破棄する
description: ACSD-49480 パッチを適用して、[!UICONTROL Cart Price Rule - Discard Subsequent Rules]が意図したとおりに動作しないAdobe Commerceの問題を修正します。
feature: Price Rules
role: Admin
exl-id: 1919043b-99a8-46a2-94df-9285c05bec7b
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# ACSD-49480: [!UICONTROL Cart Price Rule - Discard Subsequent Rules]は意図したとおりに動作していません

ACSD-49480 パッチは、[!UICONTROL Cart Price Rule - Discard Subsequent Rules]が意図したとおりに動作しない問題を修正します。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.32がインストールされている場合に利用できます。 パッチ IDはACSD-49480です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.5

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

[!UICONTROL Cart Price Rule - Discard Subsequent Rules]は意図したとおりに動作していません。

<u>複製する手順</u>:

1. [!UICONTROL Discard Subsequent Rules]が&#x200B;*[!UICONTROL Yes]*&#x200B;に、[!UICONTROL Priority]が&#x200B;*1*&#x200B;に設定された&#x200B;**[!UICONTROL Actions]** タブの&#x200B;*製品ID 1*&#x200B;に$10の割引を与えるクーポンコード （*TEST*&#x200B;という名前）を持つ&#x200B;**[!UICONTROL Cart Price Rule]**&#x200B;を作成します。
1. [!UICONTROL Priority]が&#x200B;*2*&#x200B;に設定された&#x200B;**[!UICONTROL Actions]** タブの&#x200B;*製品ID 2*&#x200B;に$5の割引を与えるクーポンコードを使用せずに、別の&#x200B;**[!UICONTROL Cart Price Rule]**&#x200B;を作成します。 ここでは、これは&#x200B;*製品ID 2*&#x200B;のグローバル販売であると仮定します。
1. フロントエンドサイトに移動し、*製品ID 1*&#x200B;と&#x200B;*製品ID 2*&#x200B;をカートに追加します。
1. *TEST* クーポンコードを適用します。

<u>期待される結果</u>

* *割引1*&#x200B;は&#x200B;*製品ID 1*&#x200B;に適用されます。
* *割引2*&#x200B;は&#x200B;*製品ID 2*&#x200B;に適用されます。

<u>実際の結果</u>

* *割引1*&#x200B;のみが&#x200B;*製品ID 1*&#x200B;に適用されます。
* *割引2*&#x200B;は&#x200B;*製品ID 2*&#x200B;に適用されません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) パッチを検索する」を参照してください。
