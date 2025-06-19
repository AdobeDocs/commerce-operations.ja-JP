---
title: 'ACSD-48634: [!DNL JS] errors when [!DNL Google Analytics Content Experiments] enabled'
description: が有効な場合に  [!DNL JS]  更新ページでエラーを修正するために  [!DNL staging] ACSD-48634 パッチ  [!DNL Google Analytics Content Experiments]  適用します。
feature: Catalog Management, Categories, Console, Page Content
role: Admin
exl-id: 99368346-157f-4283-bb8c-192a62501717
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# ACSD-48634：有効にすると [!DNL JS] エラー [!DNL Google Analytics Content Experiments] 発生する

ACSD-48634 パッチは、[!DNL Google Analytics Content Experiments] が有効 [!DNL JS] なっている場合に [!DNL staging] 更新ページで発生するエラーを修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.27 がインストールされている場合に使用できます。 パッチ ID は ACSD-48634 です。 この問題はAdobe Commerce 2.4.7 で修正されました。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.7 ～ 2.4.6

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

[!DNL Google Analytics Content Experiments] が有効になっている場合、[!DNL staging] 更新ページで [!DNL JS] のエラーが発生します。

<u> 再現手順 </u>:

1. **[!UICONTROL Admin]**/**[!UICONTROL Stores]**/**[!UICONTROL All Stores]** で、追加の web サイト、ストア、**[!UICONTROL Store View]** を作成します。 **[!UICONTROL Store View]** が *[!UICONTROL Enabled]* であることを確認します。
1. **[!UICONTROL Stores]**/**[!UICONTROL Settings]**/**[!UICONTROL Configuration]**/**[!UICONTROL Sales]**/**[!UICONTROL Google API]** に移動して、**[!DNL Configure Google Analytics]** を設定します。
   * **[!DNL Main]** および追加の web サイトの [!DNL scope] 細：
      * **[!UICONTROL Enabled]**: *[!UICONTROL Yes]*
      * **[!UICONTROL Account type]**: *[!UICONTROL Google Tag Manager]*
      * **[!UICONTROL Anonymize IP]**: *[!UICONTROL Yes]*
      * **[!UICONTROL Enable Content Experiments]**: *[!UICONTROL Yes]*
      * **[!UICONTROL Container Id]**: *[!UICONTROL (GTM container ID)]*
      * 他のフィールドには *[!UICONTROL Use Default]* を **[!DNL Uncheck]** しますが、変更しないでください。
   * **[!DNL Default Config]** [!DNL scope] の場合：
      * **[!UICONTROL Enabled]**: *[!UICONTROL Yes]*
      * **[!UICONTROL Account type]**: *[!UICONTROL Universal Analytics]*
      * **[!UICONTROL Account Number]**: *[!UICONTROL (Universal Analytics account number)]*
      * **[!UICONTROL Anonymize IP]**: *[!UICONTROL Yes]*
      * **[!UICONTROL Enable Content Experiments]**: *[!UICONTROL Yes]*
1. **[!UICONTROL Enable]** を *[!UICONTROL Yes]* から *[!UICONTROL No]* に変更して、**[!DNL Default Config]** [!DNL scope] の **[!DNL Configure Google Analytics]** を無効にします。 他の設定は変更しないでください。
1. **[!UICONTROL Catalog]**/**[!UICONTROL Categories]** に移動します。
1. 任意の **[!UICONTROL category]** を作成して編集し、スケジュールされた更新を追加します。
   * 任意の名前、開始日が将来、終了日が将来、および **[!UICONTROL category]** の変更（[!UICONTROL For Example]: *[!UICONTROL disable category]*）。
1. 更新を保存し、[!DNL browser developer console] にエラーがないか確認します。

<u> 期待される結果 </u>:

[!DNL JS] のエラーはなく、[!DNL staging] の更新に対する変更は正常に保存されました。

<u> 実際の結果 </u>:

エラーがコンソールに表示される [!DNL JS]、フォームの形式が正しくなく、保存後に [!DNL spinner] が無効になることはありません。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)」を参照してください。
