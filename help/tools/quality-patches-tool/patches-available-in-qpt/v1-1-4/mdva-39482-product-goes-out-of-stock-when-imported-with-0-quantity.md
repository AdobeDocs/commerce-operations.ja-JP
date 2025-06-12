---
title: 'MDVA-39482: バックオーダーが有効な''0''数量でインポートした場合、商品の在庫切れになります'
description: MDVA-39482 は、MSI とバックオーダーが有効で、在庫切れのしきい値がマイナス値に設定されている場合に、数量が「0」でインポートされた場合に製品の在庫切れになる問題を修正します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.4 がインストールされている場合に利用できます。 パッチ ID は MDVA-39482。 この問題はAdobe Commerce 2.4.4 で修正される予定であることに注意してください。
feature: Data Import/Export, Orders, Products
role: Admin
exl-id: 9d705ebf-2372-4e59-b447-cdb5b0db32f4
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '476'
ht-degree: 0%

---

# MDVA-39482: バックオーダーが有効な&#39;0&#39;数量でインポートした場合、商品の在庫切れになります

MDVA-39482 は、MSI とバックオーダーが有効で、在庫切れのしきい値がマイナス値に設定されている場合に、数量が「0」でインポートされた場合に製品の在庫切れになる問題を修正します。 このパッチは、[Quality Patches Tool （QPT） ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)1.1.4 がインストールされている場合に使用できます。 パッチ ID は MDVA-39482。 この問題はAdobe Commerce 2.4.4 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

Adobe Commerce（すべてのデプロイメント方法） 2.4.1-p1

**Adobe Commerce バージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方法） 2.3.6 ～ 2.3.7-p2、2.4.1 ～ 2.4.3-p1

>[!NOTE]
>
>パッチは、新しい Quality Patches Tool リリースを使用する他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

MSI とバックオーダーが有効で、在庫切れのしきい値がマイナス値に設定されている場合、数量が「0」でインポートされた製品は在庫切れになります。

<u> 前提条件 </u>:

1. MSI とサンプルデータをインストールする必要があります。
1. **ストア**/**設定**/**カタログ**/**在庫** に移動します。
   * バックオーダーを「Allow Qty Below 0」に設定します。
   * 在庫切れのしきい値を「–10」に設定します

<u> 再現手順 </u>:

1. SKU が **在庫中** で、数量が **24-MB01** あることを確認します。
1. 在庫ソースの CSV を読み込みます。 エンティティタイプで「在庫ソース」を選択していることを確認します。

   ```code panel
   sku,qty,out_of_stock_qty
   24-MB01,0,-10
   ```

1. 在庫ソースが読み込まれた後、製品の在庫ステータスを確認します。

<u> 期待される結果 </u>:

24-MB01 は、ストアフロントの **在庫** です。

<u> 実際の結果 </u>:

ストアフロントの 24 MB01 は **在庫切れ** です。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md)[!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

品質向上パッチツールの詳細については、次を参照してください。

* [ 品質向上パッチツールがリリースされました：品質向上パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) がサポートナレッジベースに追加されました。
* [Quality Patches Tool を使用して、Adobe Commerceの問題に対するパッチが使用可能かどうかを確認します ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!DNL Quality Patches Tool] ガイド）。

QPT で使用可能なその他のパッチについては、[QPT で使用可能なパッチ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) の節を参照してください。
