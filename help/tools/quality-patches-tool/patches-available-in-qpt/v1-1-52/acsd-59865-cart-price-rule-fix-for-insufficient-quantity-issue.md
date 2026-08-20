---
title: 'ACSD-59865: [!UICONTROL Cart Price Rule]は、製品数量が不足しているため、以前のルールをキャンセルできません'
description: ACSD-59865 パッチを適用して、Adobe Commerceの問題を修正します。この問題では、*値引き*の*割引量*値、*値引き**および*買いXはYを取得* [!UICONTROL Cart Price Rules]で以前のルールのアクションがキャンセルされなくなりました。
feature: Price Rules
role: Admin, Developer
exl-id: 5838a740-018d-44c2-8135-54426ea08627
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '508'
ht-degree: 0%

---

# ACSD-59865: [!UICONTROL Cart Price Rule]は、製品数量が不足しているため、以前のルールをキャンセルできません

ACSD-59865 パッチは、*[!UICONTROL Fixed amount discount]、*、*[!UICONTROL Percent of product price discount]、*、*[!UICONTROL Buy X get Y]* [!UICONTROL Cart Price Rules]の&#x200B;*[!UICONTROL Discount quantity step]*&#x200B;値が以前のルールのアクションをキャンセルしなくなった問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.52がインストールされている場合に利用できます。 パッチ IDはACSD-59865です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

カート内の製品数量が不十分なため、以前に適用したルールを[!UICONTROL Cart Price Rule]でキャンセルできません。

<u>複製する手順</u>:

1. 管理者としてログインします。
1. **[!UICONTROL Marketing]** > **[!UICONTROL Cart Price Rules]**&#x200B;に移動し、**[!UICONTROL Add New rule]**&#x200B;をクリックします。
   * Set **[!UICONTROL Rule Name]** = *Test - 1*
   * すべての&#x200B;*Web サイト*&#x200B;と&#x200B;*顧客グループ*&#x200B;を選択
   * Set **[!UICONTROL Priority]** = *0*
   * **[!UICONTROL Actions]** セクションに移動します。
     * セット **[!UICONTROL Apply]** = *製品価格割引のパーセント*
     * Set **[!UICONTROL Discount amount]** = *10*
     * Set **[!UICONTROL Maximum Qty Discount is Applied To]** = *100*
     * Set **[!UICONTROL Discount Qty Step (Buy X)]** = *0*
     * **[!UICONTROL Discard subsequent rules]**&#x200B;を&#x200B;*No*&#x200B;に設定
1. キャッシュをクリアします。
1. ストアフロントに移動し、1つの商品をカートに追加して、*チェックアウト/カート*&#x200B;に進みます。
1. *10%*&#x200B;割引がカートに適用されていることを確認します。
1. **[!UICONTROL Cart Price Rules]**&#x200B;に戻り、新しいルールを作成します。
   * Set **[!UICONTROL Rule Name]** = *Test - 2*
   * **[!UICONTROL Websites]**&#x200B;と&#x200B;**[!UICONTROL Customer Groups]**&#x200B;をすべて選択
   * Set **[!UICONTROL Priority]** = *2*
   * 「**[!UICONTROL Actions]**」セクションに移動します。
     * セット **[!UICONTROL Apply]** = *製品価格割引のパーセント*
     * Set **[!UICONTROL Discount amount]** = *20*
     * Set **[!UICONTROL Maximum Qty Discount is Applied To]** = *100*
     * Set **[!UICONTROL Discount Qty Step (Buy X)]** = *3*
1. キャッシュをクリアします。
1. もう一度ストアフロントに戻ります。
1. カートを更新してルールを更新します。 *10%*&#x200B;割引が適用されなくなったことを確認します。
1. 数量が2番目のルールに必要な&#x200B;*ステップ*&#x200B;の値を満たすまで、商品をカートに追加します。

<u>期待される結果</u>:

最初の[!UICONTROL Cart Price Rule]は、2番目のルールの条件が満たされたときに適用されます。

<u>実際の結果</u>:

価格ルールは、管理者ダッシュボードの設定に従って適用されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
