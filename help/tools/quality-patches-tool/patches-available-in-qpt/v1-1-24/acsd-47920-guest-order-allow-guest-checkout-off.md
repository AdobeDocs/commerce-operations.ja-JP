---
title: 'ACSD-47920: [!UICONTROL Allow Guest Checkout]がオフの場合でも、ゲストユーザーがREST APIを介して注文を行うことができます'
description: ACSD-47920 パッチを適用して、[!UICONTROL Allow Guest Checkout]がオフになっている場合でも、REST APIを介してゲストユーザーとして注文を行うことができるAdobe Commerceの問題を修正します。
feature: REST, Checkout, Orders
role: Admin
exl-id: 27c74803-a3f3-46bc-9eb8-8e2c72c30cd9
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# ACSD-47920: **[!UICONTROL Allow Guest Checkout]**&#x200B;がオフの場合でも、ゲストユーザーがREST APIを介して注文を行うことができます

ACSD-47920 パッチは、**[!UICONTROL Allow Guest Checkout]**&#x200B;がオフになっている場合でも、REST APIを介してゲストユーザーとして注文を配置できる問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.24がインストールされている場合に利用できます。 パッチ IDはACSD-47920です。 この問題は、Adobe Commerce 2.4.6で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

**[!UICONTROL Allow Guest Checkout]**&#x200B;がオフになっている場合でも、Rest APIを介してゲストユーザーとして注文を行うことができます。

<u>複製する手順</u>:

1. Adobe Commerce Admin > **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Sales]** > **[!UICONTROL Checkout]** > **[!UICONTROL Checkout Options]** >に移動し、**[!UICONTROL Allow Guest Checkout]**&#x200B;を&#x200B;_No_&#x200B;に設定します。
1. REST APIを使用して商品をカートに追加し、注文します。

<u>期待される結果</u>:

ゲストチェックアウト APIは、**[!UICONTROL Allow Guest Checkout]**&#x200B;が&#x200B;_No_&#x200B;に設定されている場合、*[!UICONTROL Sorry, guest checkout is not available]* エラーを返します。

<u>実際の結果</u>:

ゲストチェックアウト APIを使用すると、**[!UICONTROL Allow Guest Checkout]**&#x200B;が&#x200B;_No_&#x200B;に設定されている場合でも、注文を行うことができます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) パッチを検索する」を参照してください。
