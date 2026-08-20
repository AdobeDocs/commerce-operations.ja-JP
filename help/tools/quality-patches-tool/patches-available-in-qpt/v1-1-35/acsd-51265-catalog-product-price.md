---
title: ACSD-51265：バンドル製品のインデックス再作成を最適化する
description: システム内にバンドルされた商品が多すぎる場合、「catalog_product_price」のインデックス再作成パフォーマンスが低くなるAdobe Commerceの問題を修正するには、ACSD-51265 パッチを適用します。
feature: Products, Price Indexer
role: Admin
exl-id: 1a173ca7-f99e-42d8-87d7-81a6b33f2d4d
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 0%

---

# ACSD-51265：バンドル製品のインデックス再作成を最適化する

ACSD-51265 パッチは、システムにバンドルされた製品が多すぎる場合に`catalog_product_price`のインデックス再作成パフォーマンスが低くなる問題を修正します。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.35がインストールされている場合に利用できます。 パッチ IDはACSD-51265です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2 - 2.4.6-p1

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

システム内にバンドルされた製品が多すぎる場合、カタログ製品価格のインデックス再作成のパフォーマンスが低くなります。

<u>複製する手順</u>:

1. 動的な価格オプションを使用して、少なくとも&#x200B;*10,000*&#x200B;個のバンドルされた商品を含むカタログを生成します。
1. 製品価格のインデックス再作成を実行します。

<u>期待される結果</u>

製品価格のインデックス再作成にかかる時間は15分未満です。

<u>実際の結果</u>

製品価格のインデックス再作成には1時間以上かかります。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
