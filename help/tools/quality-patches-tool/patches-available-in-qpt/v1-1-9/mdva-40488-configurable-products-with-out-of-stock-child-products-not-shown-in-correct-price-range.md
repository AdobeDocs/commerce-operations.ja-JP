---
title: MDVA-40488：在庫切れの子商品が正しい価格帯で表示されない、設定可能な商品
description: MDVA-40488 パッチは、在庫切れの子商品を含む設定可能な商品が正しい価格帯で表示されない問題を解決します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.9がインストールされている場合に利用できます。 パッチ IDはMDVA-40488です。 この問題は、Adobe Commerce 2.4.4で修正される予定です。
feature: Configuration, Orders, Products
role: Admin
exl-id: 9a843d1b-88df-4bd7-a358-3aa34c436bdf
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '679'
ht-degree: 0%

---

# MDVA-40488：在庫切れの子商品が正しい価格帯で表示されない、設定可能な商品

MDVA-40488 パッチは、在庫切れの子商品を含む設定可能な商品が正しい価格帯で表示されない問題を解決します。 このパッチは、[品質パッチツール （QPT） ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.9がインストールされている場合に使用できます。 パッチ IDはMDVA-40488です。 この問題は、Adobe Commerce 2.4.4で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

在庫切れの子商品を含む設定可能な商品は、正しい価格帯で表示されません。

<u>前提条件</u>:

Commerce Admin > **stores** > **configuration** > **catalog** > **Inventory** > **stock options**&#x200B;に移動し、**在庫切れ商品の表示**&#x200B;設定を&#x200B;*Yes*&#x200B;に設定します。

<u>複製する手順</u>:

1. 2つの関連製品を含む設定可能な製品を作成します。 例えば、シンプルな製品の赤と茶色。
1. 単純な製品の在庫を赤に設定し、「在庫ステータス」を「*在庫*」に設定し、「製品を有効にする」ステータスを「*No*」に設定します。
1. シンプルな製品ブラウンの在庫を設定し、「製品を有効にする」ステータスを&#x200B;*はい*&#x200B;に設定します。
1. 設定可能な製品の在庫ステータスが&#x200B;*在庫*&#x200B;であることを確認します。
1. シンプルな商品の「Brown」の在庫を0に変更し、「Stock Status」を&#x200B;*在庫切れ*&#x200B;に設定します。
1. この時点で、設定可能な製品の在庫状況は引き続き&#x200B;*在庫状況*&#x200B;です。
1. 再インデックスを実行します。
1. `catalog_product_index_price` DB テーブルの設定可能な製品の`min_price`と`max_price`を確認してください。2つの値は0に設定されています。
1. しかし、設定可能な製品の在庫状況を&#x200B;*在庫切れ*&#x200B;に設定し、インデックスを再作成すると、設定可能な製品のゼロ以外の`min_price`値と`max_price`値が表示されます。

<u>期待される結果</u>:

すべての子商品が&#x200B;*在庫切れ*&#x200B;であり、設定可能な商品自体も&#x200B;*在庫切れ*&#x200B;である場合、価格はすべての子商品を使用して計算されます。

<u>実際の結果</u>:

`catalog_product_index_price` DB テーブルの設定可能な製品の`min_price`と`max_price`の値は、設定可能な在庫ステータスが&#x200B;*在庫*&#x200B;の場合は0に設定されますが、*在庫切れ*&#x200B;の場合は0以外の値になります。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [品質パッチツール ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
