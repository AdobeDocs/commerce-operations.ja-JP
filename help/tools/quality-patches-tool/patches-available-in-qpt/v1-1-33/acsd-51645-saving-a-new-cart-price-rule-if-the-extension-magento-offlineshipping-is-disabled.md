---
title: ACSD-51645：拡張機能Magento_OfflineShipping が無効な場合の、新しい「買い物かご」価格ルールの保存
description: Magento_OfflineShipping 拡張機能が無効になっている場合、新しい「買い物かご価格」ルールを保存するとエラーが発生するAdobe Commerceの問題を修正するために ACSD-51645 パッチを適用してください。
exl-id: ce747ae4-6d2f-41c0-ba75-7da72be359c7
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 0%

---

# ACSD-51645：拡張機能Magento_OfflineShipping が無効な場合の、新しい「買い物かご」価格ルールの保存

ACSD-51645 パッチでは、拡張機能のMagento_OfflineShipping が無効になっている場合に、新しい買い物かご価格ルールを保存するとエラーが発生する問題が修正されています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.33 がインストールされている場合に使用できます。 パッチ ID は ACSD-51645 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6 - 2.4.6-p1

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

拡張機能 `Magento_OfflineShipping` が無効になっている場合、新しい買い物かご価格ルールを保存するとエラーが発生します。

<u> 再現手順 </u>:

1. `Magento_OfflineShipping` モジュールを無効にします。
1. **Admin** にログインします。
1. **[!UICONTROL Marketing]**/**[!UICONTROL Cart Price Rules]** に移動します。
1. 新しい **[!UICONTROL Cart Price Rule]** を作成します。
1. 必須フィールドに入力します。
1. **[!UICONTROL Cart Price Rule]** を保存します。

<u> 期待される結果 </u>:

買い物かご価格ルールが正常に保存されました。

<u> 実際の結果 </u>:

次のエラーが発生します。
`report.ERROR: Warning: Undefined array key "simple_free_shipping" in app/code/Magento/SalesRule/Controller/Adminhtml/Promo/Quote/Save.php on line 67 [] []`

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md)[!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>)」を参照してください。
