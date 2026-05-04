---
title: ACSD-54680：複数の割り当てられたソースを持つ製品のB2B見積もりを処理できません
description: ACSD-54680 パッチを適用して、複数の割り当てられたソースを持つ商品のB2B見積もりを処理できないAdobe Commerceの問題を修正します。
feature: B2B
role: Admin, Developer
exl-id: c5307785-a4c6-4d0c-9009-0d0caee97b3d
type: Troubleshooting
source-git-commit: 319f3232d1ba5f5ed7cdd10ce85b9d7ffbeec89a
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 0%

---

# ACSD-54680：複数の割り当てられたソースを持つ製品のB2B見積もりを処理できません。

ACSD-54680 パッチでは、複数の割り当てられたソースを持つ製品のB2B見積もりを処理できない問題を修正します。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.40がインストールされている場合に利用できます。 パッチ IDはACSD-54680です。 この問題は、Adobe Commerce 2.4.6で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.0 - 2.4.5-p5

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

複数の割り当てられたソースを持つ製品のB2B見積もりは処理できません。

<u>複製する手順</u>:

1. **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Sources]**&#x200B;に移動し、**Source 1**&#x200B;と&#x200B;**Source 2**&#x200B;の2つの新しいソースを作成します。
1. **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Stocks]**&#x200B;に移動し、新しいStock: **Stock A**&#x200B;を作成し、メイン web サイトに割り当て、それに&#x200B;**Source 1**&#x200B;と&#x200B;**Source 2**&#x200B;を割り当てます。
1. シンプルな商品を作成し、**Source 1**&#x200B;と&#x200B;**Source 2**&#x200B;を割り当て、各ソースに数量= *2*&#x200B;を設定します。 （結果として、製品の販売可能数量は&#x200B;*4*&#x200B;である必要があります）。
1. 会社アカウントを作成します。
1. **[!UICONTROL Storefront]**&#x200B;に移動し、会社アカウントにログインします。
1. 数量= *4*&#x200B;の買い物かごにシンプルな商品を追加します。
1. *[!UICONTROL Shopping cart]*&#x200B;を開き、**[!UICONTROL Request a quote]** ボタンをクリックします。
1. コメントと引用符の名前を追加し、**[!UICONTROL Send a Request]** ボタンをクリックします。
1. **[!UICONTROL Admin]** > **[!UICONTROL Sales]** > **[!UICONTROL Quotes]**&#x200B;に移動します。
1. 最近送信した見積を開きます。

<u>期待される結果</u>:

引用された項目には、注文された製品が含まれています。

<u>実際の結果</u>:

「引用符で囲まれたページ」セクションが空で、引用符を処理できません。
`var/log/system.log`が含まれています

```text
report.CRITICAL: TypeError: number_format() expects parameter 1 to be float, null given in .../vendor/magento/module-negotiable-quote/Model/QuoteUpdatesInfo.php:232
```

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
