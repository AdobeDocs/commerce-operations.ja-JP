---
title: ACSD-52398：バンドルされた製品の数量を更新しようとすると、リクエストされた数量が利用できません
description: ACSD-52398 パッチを適用して、ストアフロントのカート内の同梱商品の数量を更新しようとすると、リクエストされた数量が利用できないAdobe Commerceの問題を修正します。
feature: Shopping Cart, Quotes, Products
role: Admin
exl-id: 75fa5f96-22e7-40a2-8b8a-f44452e5124d
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 0%

---

# ACSD-52398：バンドルされた製品の数量を更新しようとすると、リクエストされた数量が利用できません

ACSD-52398 パッチは、ストアフロントのカート内の同梱商品の数量を更新しようとすると、要求された数量が利用できない問題を修正します。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.35がインストールされている場合に利用できます。 パッチ IDはACSD-52398です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3-p3

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.0 - 2.4.6-p1

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

ストアフロントのカート内のバンドルされた商品の数量を更新しようとすると、リクエストされた数量は利用できません。

<u>複製する手順</u>:

1. 数量&#x200B;*1*&#x200B;と&#x200B;*10*&#x200B;の2つのシンプルな商品を作成します。
1. シンプルな商品を使ってバンドル商品を作成します。
1. 商品をカートに追加します。
1. 製品を編集し、*10*&#x200B;個のアイテムが使用可能なオプションの数量を&#x200B;*3*&#x200B;に更新してみてください。

<u>期待される結果</u>:

エラーはありません。 このオプションの在庫が&#x200B;*10*&#x200B;件あるので、数量は正常に更新されます。

<u>実際の結果</u>:

次のエラーがスローされます：*リクエストされた数量は利用できません*。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
