---
title: 'ACSD-47232: [!UICONTROL Same as Billing Address]がオンになっている場合にクーポンが適用されない'
description: '[!UICONTROL Same as Billing Address]がオンになっている場合にクーポンが適用されないAdobe Commerceの問題を修正するには、ACSD-47232 パッチを適用します。'
feature: Orders, Shipping/Delivery
role: Admin
exl-id: d8050f6e-00a9-4aa3-bb8b-1631e0e7a714
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# ACSD-47232: [!UICONTROL Same as Billing Address]がオンになっている場合にクーポンが適用されない

ACSD-47232 パッチは、**[!UICONTROL Same as Billing Address]**&#x200B;がチェックされたときにクーポンが適用されない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.23がインストールされている場合に利用できます。 パッチ IDはACSD-47232です。 この問題は、Adobe Commerce 2.4.6で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

**[!UICONTROL Same as Billing Address]**&#x200B;がオンになっている場合、クーポンは適用されません。

<u>複製する手順</u>:

1. Adobe Commerceをインストールします。
1. 重み= *8*&#x200B;のシンプルな商品を作成します。
1. デフォルトの請求先住所と配送先住所を使用して新しい顧客を作成します。
1. クーポン付きのカート価格ルールを作成。
   * **[!UICONTROL Conditions]** セクションで、*合計の重みが5*&#x200B;以上を追加します
1. [!UICONTROL Commerce]管理者で新しい注文を作成してみてください。
   * 今すぐ作成した顧客を使用する
   * 製品の追加
   * クーポンを適用してみてください

<u>期待される結果</u>:

クーポンが適用されます。

<u>実際の結果</u>:

次のようなエラーが発生します。*123 クーポンコードが無効です。 コードを確認して、もう一度やり直してください。*

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) パッチを検索する」を参照してください。
