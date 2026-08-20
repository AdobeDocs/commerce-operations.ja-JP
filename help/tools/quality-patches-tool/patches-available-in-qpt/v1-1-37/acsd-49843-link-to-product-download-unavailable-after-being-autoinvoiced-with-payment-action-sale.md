---
title: 'ACSD 49843: [!UICONTROL Payment Action] = [!UICONTROL Intent Sale]で自動請求された後、製品ダウンロードリンクを利用できません'
description: '[!UICONTROL Payment Action]が[!UICONTROL Intent Sale]に設定されている場合、注文した商品がオンライン支払い方法で自動請求された後、商品のダウンロードリンクが利用できないAdobe Commerceの問題を修正するには、ACSD-49843 パッチを適用します。'
feature: Catalog Management, Configuration, Invoices, Orders, Storefront
role: Admin, Developer
exl-id: e990b550-fb32-48d2-9c39-2176d7ab34c9
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '510'
ht-degree: 0%

---

# ACSD-49843: [!UICONTROL Payment Action] = [!UICONTROL Intent Sale]で自動請求された後、製品ダウンロードリンクを利用できません

ACSD-49843 パッチは、[!UICONTROL Payment Action]が[!UICONTROL Intent Sale]に設定されている場合に、注文済み商品がオンライン支払い方法で自動請求された後、製品ダウンロードリンクが利用できない問題を修正します。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.37がインストールされている場合に利用できます。 パッチ IDはACSD-49843です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方式） 2.3.7 - 2.3.7-p4、2.4.1 - 2.4.6-p2

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

[!UICONTROL Payment Action]が[!UICONTROL Intent Sale]に設定されている場合、注文済み商品がオンライン支払い方法で自動請求された後、製品ダウンロードリンクを利用できません。

<u>複製する手順</u>:

1. Adobe Commerce管理者にログインし、**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Configure Braintree]**&#x200B;に移動します。

   * [!UICONTROL Payment Action] ドロップダウンで、**[!UICONTROL Intent Sale]**&#x200B;を選択し、*[!UICONTROL Enable Card Payments]*&#x200B;を&#x200B;*はい*&#x200B;に設定します。

1. **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Downloadable Product Option]** > **[!UICONTROL Order Item status for Download]**&#x200B;に移動し、「*&quot;請求済み&quot;*」に設定されていることを確認します。
1. ストアフロントで、顧客としてログインします。

   * ダウンロード可能な商品とシンプルな商品をカートに追加します。
   * カード オプションを使用して注文するには、[!DNL Braintree Pay]を使用します。

1. **[!UICONTROL My Orders]**&#x200B;に移動し、注文の請求書が自動的に作成され、両方のアイテムのステータスが&#x200B;*「請求済み」*&#x200B;であることを確認します。
1. **[!UICONTROL My Downloadable Products]**&#x200B;に移動し、ダウンロードリンクがまだ利用できないことを確認します。
1. 管理画面で、その注文に移動し、その注文の配送を作成します。
1. ストアフロントで、**[!UICONTROL My Downloadable Products]**&#x200B;に移動し、ダウンロードリンクが利用可能になったことを確認します。

<u>期待される結果</u>:

ダウンロード可能な製品ステータスが&#x200B;*「請求済み」*&#x200B;の場合、ダウンロードリンクを利用できます。

<u>実際の結果</u>:

ダウンロード可能な製品ステータスに「*&quot;請求済み&quot;*」と表示されている場合でも、ダウンロードリンクを利用できません。 これは、物理的な製品の出荷が作成された後にのみ使用できます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) パッチを検索する」を参照してください。
