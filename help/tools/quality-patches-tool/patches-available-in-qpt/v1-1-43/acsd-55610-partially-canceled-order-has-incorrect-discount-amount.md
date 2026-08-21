---
title: ACSD-55610：一部キャンセルされた注文の割引額が正しくありません
description: ACSD-55610 パッチを適用して、部分的にキャンセルされた注文に誤った割引額が含まれているAdobe Commerceの問題を修正します。
feature: Invoices, Orders, Price Rules, Shopping Cart
role: Admin, Developer
exl-id: b7b94c9d-e027-4601-837b-d70b7ff8bd2c
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 0%

---

# ACSD-55610：一部キャンセルされた注文の割引額が正しくありません

ACSD-55610 パッチでは、部分的にキャンセルされた注文に誤った割引額が含まれている問題を修正します。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.43がインストールされている場合に利用できます。 パッチ IDはACSD-55610です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

部分的にキャンセルされた注文には、誤った割引金額が含まれています。

<u>複製する手順</u>:

1. ショッピングカートの価格ルールを作成。

   * *[!UICONTROL Rule Name]*: *ウィンターセール*
   * *[!UICONTROL Active]* = *はい*
   * *[!UICONTROL Websites]* = *メイン Web サイト*
   * あらゆる顧客グループに対応：
   * 特定のクーポンを選択します。
   * *[!UICONTROL Coupon Code]*: *冬10*
   * *[!UICONTROL Conditions]*: *[!UICONTROL If ALL of these conditions are TRUE]*: *小計（除く。 Tax）が75*&#x200B;より大きいまたは
   * *[!UICONTROL Percent of product price discount]*&#x200B;を適用します。
   * *[!UICONTROL Discount Amount]*: *10*
   * *[!UICONTROL Discard subsequent rules]*: *はい*

1. 価格が100に設定された3つの商品を作成します。
1. 3つの商品をカートに入れます。
1. クーポンを適用します。
1. 注文する。
1. 注文の1つのアイテムを請求書に記入し、それを発送します。
1. 他の2つの項目をキャンセルします。
1. `base_discount_canceled`列を確認してください。

<u>期待される結果</u>:

`base_discount_cancelled`の割引額が正しく反映されます。

<u>実際の結果</u>:

`base_discount_cancelled`が正しくありません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) パッチを検索する」を参照してください。
