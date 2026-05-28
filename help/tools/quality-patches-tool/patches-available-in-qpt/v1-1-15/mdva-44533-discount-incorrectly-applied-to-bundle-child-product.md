---
title: MDVA-44533：バンドルされた子商品に誤って適用される割引
description: MDVA-44533 パッチは、バンドルされた子製品に誤って割引が適用される問題を修正します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.15がインストールされている場合に利用できます。 パッチ IDはMDVA-44533です。 この問題は、Adobe Commerce 2.4.5で修正される予定です。
feature: Orders, Personalization, Products
role: Admin
exl-id: 150fe577-a61a-451e-838a-d60be7754bf4
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '547'
ht-degree: 0%

---

# MDVA-44533：バンドルされた子商品に誤って適用される割引

MDVA-44533 パッチは、バンドルされた子製品に誤って割引が適用される問題を修正します。 このパッチは、[品質パッチツール（QPT） ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.15がインストールされている場合に使用できます。 パッチ IDはMDVA-44533です。 この問題は、Adobe Commerce 2.4.5で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2-p2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.1 - 2.4.3-p2

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

バンドルされた子商品に誤って割引が適用される。

<u>複製する手順</u>:

1. 50 ドルの価格でシンプルな商品を作成します。
1. バンドル製品を作成し、バンドル製品の唯一のオプションとして単純な製品を割り当てます。
1. 以下を使用してカート価格ルールを作成します。

   * 条件：合計金額が130$を超える場合
   * アクション：10$の固定金額割引が適用されます

1. ストアフロントに移動し、数量= 1のバンドル商品をカートに追加します。
1. カートに移動し、バンドル製品の総費用が50$、割引が適用されないことを確認してください。
1. 数量を2に変更し、買い物かごを更新します。 バンドルされた製品の合計コストは100 ドルになります。

<u>期待される結果</u>:

小計が100\$で、ルール条件で130\$未満であるため、割引は適用されません。

<u>実際の結果</u>:

割引が適用されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [品質パッチツール ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
