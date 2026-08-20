---
title: ACP2E-3841：サブセレクト条件を使用し、送料無料が有効になっている場合、複数配送の商品のカート価格ルールが正しく適用されない
description: ACP2E-3841 パッチを適用して、サブセレクト条件を使用し、送料無料が有効になっている場合に、複数配送の商品のカート価格ルールが正しく適用されないAdobe Commerceの問題を修正します。
feature: Shopping Cart, Price Rules
role: Admin, Developer
exl-id: 73979b71-9b15-4a4b-a1c9-37d3213c177f
type: Troubleshooting
source-git-commit: 4266dbeca837bc62e5a76b2ef22b065a3452e088
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 2%

---

# ACP2E-3841：サブセレクト条件を使用し、送料無料が有効になっている場合、複数配送の商品のカート価格ルールが正しく適用されない

ACP2E-3841 パッチでは、サブセレクト条件が使用され、送料無料が有効になっている場合に、複数配送の商品のカート価格ルールが正しく適用されない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64がインストールされている場合に利用できます。 パッチ IDはACP2E-3841です。 この問題は、Adobe Commerce 2.4.9で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p9

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5 - 2.4.7-p5

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

サブセレクト条件を使用し、送料無料が有効になっている場合、複数配送の商品のカート価格ルールが正しく適用されません。

<u>前提条件</u>:

**設定：**
1. **[!UICONTROL Free Shipping]** = *有効*
1. **[!UICONTROL Minimum Order Amount]** = *99999999*

**必要なカテゴリ：**
1. カテゴリテスト 1
1. カテゴリテスト 2

**必要な製品：**
1. 製品テスト 1:
   1. カテゴリ：カテゴリテスト 1
   1. 価格：45 ドル
1. 製品テスト 2:
   1. カテゴリー：カテゴリテスト 2
   1. 価格：56.25 ドル 
      **（テストが正しく動作するようにするには、価格がここに示す価格と同じである必要があります。）**

**買い物かごの価格ルール：**

管理者としてログインし、**[!UICONTROL Marketing]** > **[!UICONTROL Promotions]** > **[!UICONTROL Cart Price Rules]** > **[!UICONTROL Add new rule]**&#x200B;に移動します。 次の値を使用します。

**[!UICONTROL Rule Information]:**
1. **[!UICONTROL Rule Name]**：送料無料のテスト
1. **[!UICONTROL Active]**: *はい*
1. **[!UICONTROL Websites]**: *メイン Web サイト*
1. **[!UICONTROL Customer Groups]**: *ログインしていません、一般、卸売、Retailer*
1. **[!UICONTROL Coupon]**: *クーポンなし*
1. **[!UICONTROL Uses per Customer]**: *0*
1. **[!UICONTROL Priority]**: *1*

**[!UICONTROL Conditions]:**

**[!UICONTROL If ALL of these conditions are TRUE:]**


**[!UICONTROL If total amount (incl. tax) equals or greater than 100 for a subselection of items in cart matching ALL of these conditions:]**


**[!UICONTROL Category is]** *5,12,13*

アクション：

**[!UICONTROL Percent of product price discount]** = *10*

<u>複製する手順</u>:

1. ストアフロントにログインします。
2. 製品テスト 1を追加します。
3. Product Test 2を2個追加します。
4. カートにアクセス。
5. **[!UICONTROL Check Out with Multiple Addresses]**&#x200B;を選択します。

<u>期待される結果</u>:

エラーがありません。

<u>実際の結果</u>:

*500 エラー*

*メッセージ：非推奨の機能：浮動小数112.5からintへの暗黙的な変換は、214行目の/app/code/Magento/SalesRule/Model/Rule/Condition/Product/Subselect.phpで精度を失います*

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
