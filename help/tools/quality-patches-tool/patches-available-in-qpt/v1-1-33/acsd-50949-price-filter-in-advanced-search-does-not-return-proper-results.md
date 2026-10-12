---
title: ACSD-50949：高度な検索の価格フィルターは、SKU フィルターと共に使用すると、適切な結果を返しません
description: ACSD-50949 パッチを適用して、高度な検索で価格フィルターを使用すると、SKU フィルターと共に使用したときに適切な結果が返されないAdobe Commerceの問題を修正します。
feature: Orders, Search
role: Admin
exl-id: 89e54940-e763-4554-8641-a162516bcabd
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
subfeature_v2:
  - id: a1d22079-48b9-5e69-9ee6-eb236068ef34
    internal-label: Search
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 3%
---
# ACSD-50949：高度な検索の価格フィルターで、SKU フィルターで使用すると適切な結果が返されない

ACSD-50949 パッチでは、高度な検索で価格フィルターを使用しても、SKU フィルターと共に使用すると適切な結果が返されない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.33がインストールされている場合に利用できます。 パッチ IDはACSD-50949です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

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
   | MJ3 | 商品3 | $21 | 10 |
   | MJ4 | 商品4 | $32 | 10 |
   | MJ5 | 製品5 | $33 | 10 |
   | MJ6 | 商品6 | $34 | 10 |
   | MJ7 | 商品7 | $44 | 10 |

1. ストアフロントで&#x200B;**[!UICONTROL Advanced Search]**&#x200B;を開き、SKUで「MJ」を検索します。
1. 「**[!UICONTROL Modify your search]**」リンクをクリックします。
1. *1*&#x200B;から&#x200B;*21*&#x200B;までの条件に価格範囲を追加し、**[!UICONTROL Search]** ボタンをクリックします。

<u>期待される結果</u>:

定義された範囲内の価格を持つ製品のみが返されます。

<u>実際の結果</u>:

価格が&#x200B;*$21*&#x200B;より高い商品が返されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) パッチを検索する」を参照してください。
