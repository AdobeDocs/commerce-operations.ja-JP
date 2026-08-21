---
title: 'ACSD-52160: カート価格ルールに対する製品の検証結果'
description: ACSD-52160 パッチを適用して、カート価格ルールに対する製品の検証結果がルール条件*[!UICONTROL If an item is FOUND/NOT FOUND in the cart with All/Any of these conditions true]*に基づいて正しく評価されないAdobe Commerceの問題を修正します。
exl-id: 8f8799c9-850a-4c8f-bde4-68df64e46c85
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# ACSD-52160：買い物かごの価格ルールに対する製品の検証結果が正しく評価されない

ACSD-52160 パッチは、買い物かごの価格ルールに対する製品検証結果が、ルール条件&#x200B;*[!UICONTROL If an item is FOUND/NOT FOUND in the cart with All/Any of these conditions true]*&#x200B;に基づいて適切に評価されない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.34がインストールされている場合に利用できます。 パッチ IDはACSD-52160です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.6-p1

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

カート価格ルールに対する製品の検証結果が、ルール条件&#x200B;*[!UICONTROL If an item is FOUND/NOT FOUND in the cart with All/Any of these conditions true]*&#x200B;に基づいて正しく評価されません。

<u>複製する手順</u>:

1. 2つの商品を作成し、2つの異なるカテゴリーに割り当て。
1. 次のような条件で&#x200B;**[!UICONTROL Cart Price Rule]**&#x200B;を作成します。

   * *[!UICONTROL FOUND]* パラメーターの&#x200B;**SKU 1**
   * *[!UICONTROL NOT FOUND]* パラメーターの&#x200B;**SKU 2**

1. 両方の商品をカートに入れる。
1. クーポンコードを適用します。

<u>期待される結果</u>

カートには制限されたカテゴリの商品が含まれているため、クーポンコードは適用されません。

<u>実際の結果</u>

クーポンコードが適用されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
