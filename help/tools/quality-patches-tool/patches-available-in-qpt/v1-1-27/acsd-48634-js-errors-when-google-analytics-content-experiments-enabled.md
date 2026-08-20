---
title: 'ACSD-48634: [!DNL Google Analytics Content Experiments] が有効になっている場合の [!DNL JS]  エラー'
description: ' [!DNL Google Analytics Content Experiments] が有効になっている場合に、 [!DNL staging] 更新ページの [!DNL JS]  エラーを修正するためにACSD-48634 パッチを適用します。'
feature: Catalog Management, Categories, Console, Page Content
role: Admin
exl-id: 99368346-157f-4283-bb8c-192a62501717
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 12%

---

# ACSD-48634: [!DNL Google Analytics Content Experiments]が有効になっている場合の[!DNL JS] エラー

[!DNL Google Analytics Content Experiments]が有効になっている場合、[!DNL staging]更新ページの[!DNL JS]個のエラーがACSD-48634 パッチによって修正されます。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.27がインストールされている場合に利用できます。 パッチ IDはACSD-48634です。 この問題は、Adobe Commerce 2.4.7で修正されています。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.7 - 2.4.6

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

[!DNL Google Analytics Content Experiments]が有効になっている場合、[!DNL staging]更新ページで[!DNL JS] エラーが発生します。

<u>複製する手順</u>:

1. **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL All Stores]**&#x200B;で、追加のweb サイト、ストア、および&#x200B;**[!UICONTROL Store View]**&#x200B;を作成します。 **[!UICONTROL Store View]**&#x200B;が&#x200B;*[!UICONTROL Enabled]*&#x200B;であることを確認してください。
1. **[!DNL Configure Google Analytics]**&#x200B;を設定するには、**[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Google API]**&#x200B;に移動します。
   * **[!DNL Main]**&#x200B;とその他のWeb サイト [!DNL scope]の場合：
     * **[!UICONTROL Enabled]**: *[!UICONTROL Yes]*
     * **[!UICONTROL Account type]**: *[!UICONTROL Google Tag Manager]*
     * **[!UICONTROL Anonymize IP]**: *[!UICONTROL Yes]*
     * **[!UICONTROL Enable Content Experiments]**: *[!UICONTROL Yes]*
     * **[!UICONTROL Container Id]**: *[!UICONTROL (GTM container ID)]*
     * 他のフィールドには&#x200B;**[!DNL Uncheck]** *[!UICONTROL Use Default]*&#x200B;がありますが、変更しないでください。
   * **[!DNL Default Config]** [!DNL scope]について：
     * **[!UICONTROL Enabled]**: *[!UICONTROL Yes]*
     * **[!UICONTROL Account type]**: *[!UICONTROL Universal Analytics]*
     * **[!UICONTROL Account Number]**: *[!UICONTROL (Universal Analytics account number)]*
     * **[!UICONTROL Anonymize IP]**: *[!UICONTROL Yes]*
     * **[!UICONTROL Enable Content Experiments]**: *[!UICONTROL Yes]*
1. **[!UICONTROL Enable]**&#x200B;を&#x200B;*[!UICONTROL Yes]*&#x200B;から&#x200B;*[!UICONTROL No]*&#x200B;に変更して、**[!DNL Default Config]** [!DNL scope]の&#x200B;**[!DNL Configure Google Analytics]**&#x200B;を無効にします。 他の何かを変えないようにしましょう！
1. **[!UICONTROL Catalog]** > **[!UICONTROL Categories]**&#x200B;に移動します。
1. 任意の&#x200B;**[!UICONTROL category]**&#x200B;を作成して編集し、スケジュールされた更新を追加します。
   * 任意の名前、開始日、開始日、終了日、および&#x200B;**[!UICONTROL category]** （[!UICONTROL For Example]: *[!UICONTROL disable category]*）の変更。
1. 更新プログラムを保存し、[!DNL browser developer console]にエラーがないか確認してください。

<u>期待される結果</u>:

[!DNL JS] エラーはなく、[!DNL staging]の更新に対する変更は正常に保存されます。

<u>実際の結果</u>:

[!DNL JS]個のエラーがコンソールに表示され、フォームの形式が正しくなく、保存後に[!DNL spinner]が無効になることはありません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
