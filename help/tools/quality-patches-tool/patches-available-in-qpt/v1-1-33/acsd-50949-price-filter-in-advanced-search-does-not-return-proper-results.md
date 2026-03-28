---
title: ACSD-50949：高度な検索の価格フィルターは、SKU フィルターと共に使用すると、適切な結果を返しません
description: ACSD-50949 パッチを適用して、高度な検索で価格フィルターを使用すると、SKU フィルターと共に使用したときに適切な結果が返されないAdobe Commerceの問題を修正します。
feature: Orders, Search
role: Admin
exl-id: 89e54940-e763-4554-8641-a162516bcabd
type: Troubleshooting
source-git-commit: 7054a5286f01e26e324401f4d8505e4e0faed93e
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 1%

---

# ACSD-50949：高度な検索の価格フィルターで、SKU フィルターで使用すると適切な結果が返されない

ACSD-50949 パッチでは、高度な検索で価格フィルターを使用しても、SKU フィルターと共に使用すると適切な結果が返されない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.33がインストールされている場合に利用できます。 パッチ IDはACSD-50949です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2 - 2.4.6-p1

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## イシュー

高度な検索の価格フィルターは、SKU フィルターと共に使用すると、適切な結果を返しません。

<u>複製する手順</u>:

1. 複数の製品を作成します。例：

   | SKU | 名前 | 価格 | 量 |
   |-----|-----------|-------|----------|
   | MJ1 | 商品1 | $10 | 10 |
   | MJ2 | 商品2 | $15 | 10 |
   | MJ3 | 商品3 | 21 ドル | 10 |
   | MJ4 | 商品4 | $32 | 10 |
   | MJ5 | 製品5 | $33 | 10 |
   | MJ6 | 商品6 | $34 | 10 |
   | MJ7 | 商品7 | 44 ドル | 10 |

1. ストアフロントで&#x200B;**[!UICONTROL Advanced Search]**&#x200B;を開き、SKUで「MJ」を検索します。
1. 「**[!UICONTROL Modify your search]**」リンクをクリックします。
1. *1*&#x200B;から&#x200B;*21*&#x200B;までの条件に価格範囲を追加し、**[!UICONTROL Search]** ボタンをクリックします。

<u>期待される結果</u>:

定義された範囲内の価格を持つ製品のみが返されます。

<u>実際の結果</u>:

価格が&#x200B;*$21*&#x200B;より高い商品が返されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool]  ガイドの](/help/tools/quality-patches-tool/usage.md)>使用状況[!DNL Quality Patches Tool]。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [&#x200B; [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) ガイドの[!UICONTROL Quality Patches Tool]を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) ガイドの「[!DNL Quality Patches Tool] パッチを検索する」を参照してください。
