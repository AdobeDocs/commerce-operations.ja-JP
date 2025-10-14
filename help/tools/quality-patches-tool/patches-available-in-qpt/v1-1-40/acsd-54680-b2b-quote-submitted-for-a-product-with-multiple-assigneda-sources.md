---
title: ACSD-54680：複数のソースが割り当てられている製品の B2B 見積もりを処理できない
description: 複数のソースが割り当てられている商品の B2B Quote が処理できないAdobe Commerceの問題を修正するには、ACSD-54680 パッチを適用します。
feature: B2B
role: Admin, Developer
exl-id: c5307785-a4c6-4d0c-9009-0d0caee97b3d
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# ACSD-54680：複数のソースが割り当てられている製品の B2B 見積もりは処理できません。

ACSD-54680 パッチは、複数のソースが割り当てられている製品の B2B Quote が処理できない問題を修正します。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.40 がインストールされている場合に使用できます。 パッチ ID は ACSD-54680 です。 この問題はAdobe Commerce 2.4.6 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.0 ～ 2.4.5-p5

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

複数のソースが割り当てられている製品の B2B 見積もりは処理できません。

<u> 再現手順 </u>:

1. **[!UICONTROL Admin]**/**[!UICONTROL Store]**/**[!UICONTROL Sources]** に移動して、2 つの新しいソース（**Source 1** と **Source 2** を作成します。
1. **[!UICONTROL Admin]**/**[!UICONTROL Store]**/**[!UICONTROL Stocks]** に移動して、新しい在庫を作成します。**在庫 A** をメイン web サイトに割り当て、**Source 1** と **Source 2** を割り当てます。
1. シンプルな商品を作成し、**Source 1&rbrace; と** 2&rbrace;Source 2 **を割り当て、各ソースに対して数量=** 2 *を設定します。*（その結果、製品の販売可能数量は *4* になります。）
1. 会社アカウントを作成します。
1. **[!UICONTROL Storefront]** に移動し、会社アカウントにログインします。
1. シンプルな製品を数量= *4* で買い物かごに追加します。
1. *[!UICONTROL Shopping cart]* を開いて「」ボタン **[!UICONTROL Request a quote]** クリックします。
1. コメントと引用符名を追加し、「」ボタン **[!UICONTROL Send a Request]** クリックします。
1. **[!UICONTROL Admin]**/**[!UICONTROL Sales]**/**[!UICONTROL Quotes]** に移動します。
1. 最近送信した見積もりを開きます。

<u> 期待される結果 </u>:

引用された品目には、注文された製品が含まれています。

<u> 実際の結果 </u>:

引用した項目のページ セクションが空で、引用を処理できません。
`var/log/system.log` contains

```
report.CRITICAL: TypeError: number_format() expects parameter 1 to be float, null given in .../vendor/magento/module-negotiable-quote/Model/QuoteUpdatesInfo.php:232
```

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 &#x200B;](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [&#x200B; アップグレードとパッチ &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [&#x200B; を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[[!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja): Search for patches[!DNL Quality Patches Tool]」を参照してください。
