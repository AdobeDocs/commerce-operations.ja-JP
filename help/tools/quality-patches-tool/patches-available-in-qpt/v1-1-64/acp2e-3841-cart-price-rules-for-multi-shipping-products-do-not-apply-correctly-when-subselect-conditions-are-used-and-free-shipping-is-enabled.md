---
title: ACP2E-3841：副選択条件を使用し、送料無料が有効になっている場合、複数出荷製品の買い物かご価格ルールが正しく適用されない
description: ACP2E-3841 パッチを適用すると、副選択条件が使用され、送料無料が有効になっている場合に、複数配送商品の買い物かご価格ルールが正しく適用されないAdobe Commerceの問題を修正できます。
feature: Shopping Cart, Price Rules
role: Admin, Developer
source-git-commit: 1abb32109d5ca4a90cdd1d210d1fae6a728699fd
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---


# ACP2E-3841：副選択条件を使用し、送料無料が有効になっている場合、複数出荷製品の買い物かご価格ルールが正しく適用されない

ACP2E-3841 パッチは、副選択条件が使用され、送料無料が有効になっている場合に、複数配送製品の買い物かご価格ルールが正しく適用されない問題を修正しました。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64 がインストールされている場合に使用できます。 パッチ ID は ACP2E-3841 です。 この問題はAdobe Commerce 2.4.9 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p9

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5 ～ 2.4.7-p5

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

複数出荷製品の買い物かご価格ルールは、副選択条件が使用され、送料無料が有効になっている場合、正しく適用されません。

<u> 前提条件 </u>:

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
   1. カテゴリ：カテゴリテスト 2
   1. 価格：56.25 ドル 

      **（テストが正しく動作することを確認するために、価格はこちらと同じにする必要があります。）**

**買い物かご価格ルール：**

管理者としてログインし、**[!UICONTROL Marketing]**/**[!UICONTROL Promotions]**/**[!UICONTROL Cart Price Rules]**/**[!UICONTROL Add new rule]** に移動します。 次の値を使用します。

**[!UICONTROL Rule Information]:**
1. **[!UICONTROL Rule Name]**：送料無料のテスト
1. **[!UICONTROL Active]**: *はい*
1. **[!UICONTROL Websites]**: *メイン Web サイト*
1. **[!UICONTROL Customer Groups]**: *ログインしていない、一般、卸売、Retailer*
1. **[!UICONTROL Coupon]**: *クーポンなし*
1. **[!UICONTROL Uses per Customer]**: *0*
1. **[!UICONTROL Priority]**: *1*

**[!UICONTROL Conditions]:**

**[!UICONTROL If ALL of these conditions are TRUE:]**


**[!UICONTROL If total amount (incl. tax) equals or greater than 100 for a subselection of items in cart matching ALL of these conditions:]**


**[!UICONTROL Category is]** *5,12,13*

アクション：

**[!UICONTROL Percent of product price discount]** = *10*

<u> 再現手順 </u>:

1. ストアフロントにログインします。
2. 製品テスト 1 を追加します。
3. 2 つの製品テストを追加します。
4. 買い物かごにアクセスします。
5. 「**[!UICONTROL Check Out with Multiple Addresses]**」を選択します。

<u> 期待される結果 </u>:

エラーはありません。

<u> 実際の結果 </u>:

*500 エラー*

*メッセージ：非推奨（廃止予定）の機能：float 112.5 から int への暗黙的な変換により、214 行目の/app/code/Magento/SalesRule/Model/Rule/Condition/Product/Subselect.phpで精度が失われます*

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
