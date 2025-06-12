---
title: ACSD-50814：管理者ユーザーがクレジットメモを作成できない
description: 管理者ユーザーがクレジットメモを作成できないAdobe Commerceの問題を修正するには、ACSD-50814 パッチを適用します。
feature: Admin Workspace, Orders, Returns
role: Admin
exl-id: 87ee7166-7492-4948-9a85-a183ecf54fa7
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# ACSD-50814：管理者ユーザーがクレジットメモを作成できない

ACSD-50814 パッチは、管理者ユーザーがクレジットメモを作成できない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.30 がインストールされている場合に使用できます。 パッチ ID は ACSD-50814 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

管理者ユーザーはクレジットメモを作成できません。

<u> 再現手順 </u>:

1. Adobe Commerce Admin で、**[!UICONTROL Stores]** / **[!UICONTROL Configuration]** / **[!UICONTROL Sales]** / **[!UICONTROL Shipping methods]** / **[!UICONTROL Free shipping]** に移動し、**[!UICONTROL Enable free shipping]** を *[!UICONTROL Yes]* に設定します。
1. 再び **[!UICONTROL Stores]**/**[!UICONTROL Configuration]**/**[!UICONTROL Sales]**/**[!UICONTROL Tax]** に移動し、計算設定を展開して、次の項目を設定します。
   * [!UICONTROL Shipping prices] = [!UICONTROL Including tax]
   * [!UICONTROL Enable cross border trade] = [!UICONTROL No]
1. 価格表示設定を展開し、[!UICONTROL Display shipping prices] = [!UICONTROL Including tax] を設定します。
1. [!UICONTROL Orders]、[!UICONTROL Invoices]、[!UICONTROL Credit memo] の表示設定を展開し、[!UICONTROL Display shipping amount] = [!UICONTROL Including tax] を設定します。
1. キャッシュをクリアします。
1. 店頭で注文します。
1. 管理画面で注文の請求書を作成します。
1. クレジットメモを作成します。

<u> 期待される結果 </u>:

クレジット メモが作成されます。

<u> 実際の結果 </u>:

次のエラーが発生します。

*エラーにより、ページを表示できません*

```
report.CRITICAL: DivisionByZeroError: Division by zero in vendor/magento/module-sales/Model/Order/Creditmemo/Total/Tax.php:139*
```

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md)[!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)」を参照してください。
