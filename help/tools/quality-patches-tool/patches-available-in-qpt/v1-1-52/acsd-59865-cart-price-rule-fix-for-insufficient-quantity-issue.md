---
title: ACSD-59865：製品数量が不十分なため、[!UICONTROL Cart Price Rule] が以前のルールのキャンセルに失敗します
description: ACSD-59865 パッチを適用すると、Adobe Commerceの問題を修正できます。この問題では、固定金額割引、*製品価格割引の割合、*Buy X get Y*の*割引数量ステップ*の値によって、以前のルールのアクション [!UICONTROL Cart Price Rules] キャンセルされなくなります。
feature: Price Rules
role: Admin, Developer
exl-id: 5838a740-018d-44c2-8135-54426ea08627
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 0%

---

# ACSD-59865：製品数量が不十分なため、[!UICONTROL Cart Price Rule] が以前のルールのキャンセルに失敗します

ACSD-59865 パッチは、*[!UICONTROL Fixed amount discount]、* *[!UICONTROL Percent of product price discount]、* および *[!UICONTROL Buy X get Y]* [!UICONTROL Cart Price Rules] の *[!UICONTROL Discount quantity step]* 値によって以前のルールのアクションがキャンセルされなくなる問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.52 がインストールされている場合に使用できます。 パッチ ID は ACSD-59865 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p1

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

カート内の製品数量が不十分なため、[!UICONTROL Cart Price Rule] は以前に適用されたルールをキャンセルできません。

<u> 再現手順 </u>:

1. 管理者としてログインします。
1. **[!UICONTROL Marketing]**/**[!UICONTROL Cart Price Rules]** に移動し、「**[!UICONTROL Add New rule]**」をクリックします。
   * Set **[!UICONTROL Rule Name]** = *テスト - 1*
   * すべての *Web サイト* および *顧客グループ* を選択します
   * Set **[!UICONTROL Priority]** = *0*
   * **[!UICONTROL Actions]** のセクションに移動します。
      * Set **[!UICONTROL Apply]** = *製品価格割引のパーセント*
      * Set **[!UICONTROL Discount amount]** = *10*
      * Set **[!UICONTROL Maximum Qty Discount is Applied To]** = *100*
      * Set **[!UICONTROL Discount Qty Step (Buy X)]** = *0*
      * **[!UICONTROL Discard subsequent rules]** を *いいえ* に設定
1. キャッシュをクリアします。
1. ストアフロントに移動し、買い物かごに商品を 1 つ追加して、*チェックアウト/買い物かご* に進みます。
1. *10%* の割引が買い物かごに適用されることを確認します。
1. **[!UICONTROL Cart Price Rules]** に戻り、新しいルールを作成します。
   * Set **[!UICONTROL Rule Name]** = *テスト - 2*
   * すべての **[!UICONTROL Websites]** と **[!UICONTROL Customer Groups]** を選択
   * Set **[!UICONTROL Priority]** = *2*
   * **[!UICONTROL Actions]** のセクションに移動します。
      * Set **[!UICONTROL Apply]** = *製品価格割引のパーセント*
      * Set **[!UICONTROL Discount amount]** = *20*
      * Set **[!UICONTROL Maximum Qty Discount is Applied To]** = *100*
      * Set **[!UICONTROL Discount Qty Step (Buy X)]** = *3*
1. キャッシュをクリアします。
1. 再びストアフロントに戻ります。
1. 買い物かごを更新して、ルールを更新します。 *10%* 割引が適用されなくなったことを確認します。
1. 数量が 2 番目のルールに必要な *ステップ* 値を満たすまで、買い物かごに品目を追加します。

<u> 期待される結果 </u>:

2 番目のルールの条件が満たされると、最初の [!UICONTROL Cart Price Rule] が適用されます。

<u> 実際の結果 </u>:

価格ルールは、管理ダッシュボードで設定されたとおりに適用されます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md)[!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。

QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)」を参照してください。
