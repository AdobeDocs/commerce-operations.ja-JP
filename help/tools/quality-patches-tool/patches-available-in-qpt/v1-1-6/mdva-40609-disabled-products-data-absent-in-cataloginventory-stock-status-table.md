---
title: 'MDVA-40609: cataloginventory_stock_status テーブルに存在しない無効な製品データ'
description: MDVA-40609 パッチは、無効な製品データが「cataloginventory_stock_status」インデックステーブルに表示されず、誤った製品数量が表示される問題を解決します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.6がインストールされている場合に利用できます。 パッチ IDはMDVA-40609です。 この問題は、Adobe Commerce 2.4.3で修正されています。
feature: Catalog Management, Inventory, Orders, Products
role: Admin
exl-id: e207ee55-b6ce-4065-bae1-2be89dcf5092
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---

# MDVA-40609: cataloginventory_stock_status テーブルに存在しない無効な製品データ

MDVA-40609 パッチは、無効な製品データが`cataloginventory_stock_status` インデックステーブルに表示されず、誤った製品数量が表示される問題を解決します。 このパッチは、[品質パッチツール （QPT） &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.6がインストールされている場合に使用できます。 パッチ IDはMDVA-40609です。 この問題は、Adobe Commerce 2.4.3で修正されています。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2 - 2.4.2-p2

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

無効な製品データが`cataloginventory_stock_status` インデックステーブルに表示されないため、誤った製品数量が表示されます。

<u>前提条件</u>:

インベントリモジュールがインストールされている。

<u>複製する手順</u>:

1. ストアビューとストアビューを持つ2つのweb サイトを設定する。
1. 新しいソースと在庫を作成します。
1. シンプルな商品を追加する：
   * 「製品を有効にする」を&#x200B;*No*&#x200B;に設定します。
   * Source Item Status = InstockおよびQtyが0より大きい2つのソースを割り当てます。
1. 製品を保存します。
1. 「**製品販売可能数量**」タブを確認します。

<u>期待される結果</u>:

両方の株式が0より大きい値を入力しました。

<u>実際の結果</u>:

1つの在庫の価値はゼロです。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [品質パッチツール &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、「QPT[&#128279;](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-)で使用可能な パッチ」セクションを参照してください。
