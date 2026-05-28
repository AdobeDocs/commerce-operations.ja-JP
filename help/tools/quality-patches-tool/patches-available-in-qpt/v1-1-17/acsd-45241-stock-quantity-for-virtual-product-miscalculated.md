---
title: 'ACSD-45241: バーチャル製品の在庫量が計算に失敗しました'
description: ACSD-45241 パッチは、クレジットメモを作成した後にバーチャル製品の在庫量が誤って計算される問題を修正します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.17がインストールされている場合に利用できます。 パッチ IDはACSD-45241です。 この問題はAdobe Commerce 2.4.4で修正されています。
feature: Orders, Products
role: Admin
exl-id: 447a84f0-aab4-4bb1-9f06-c056c006cd69
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '580'
ht-degree: 0%

---

# ACSD-45241: バーチャル製品の在庫量が計算に失敗しました

ACSD-45241 パッチは、クレジットメモを作成した後にバーチャル製品の在庫量が誤って計算される問題を修正します。 このパッチは、[品質パッチツール（QPT） ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.17がインストールされている場合に使用できます。 パッチ IDはACSD-45241です。 この問題はAdobe Commerce 2.4.4で修正されています。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.5 - 2.4.4

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

クレジットメモを作成した後、バーチャル商品の在庫量が誤って計算される。

<u>複製する手順</u>:

1. Commerce Adminで、バーチャル商品を子商品として使用して設定可能な商品を作成します。
1. ステップ 1で作成した両方の商品の在庫があることを確認します。
1. ステップ 1で作成したバーチャル商品の数量を100としてマークし、販売可能数量も100として保持します。
1. 商品をショッピングカートに追加します。
1. 最初のステップで作成したバーチャル商品で注文します。
1. 注文ステータスを「保留中」のままにします。 支払いを処理する必要はありません。
1. `order_created` レコードが`inventory_reservation`に作成されました。 バーチャル製品数量は、99として販売可能な数量で100を示します。
1. 注文を開き、**請求書** > **請求書を送信**&#x200B;に移動します。
1. `invoice_created` レコードが`inventory_reservation`に作成されました。 バーチャル商品数量は99、販売可能数量も99となっています。
1. 「**Stockに戻る**」を選択せずにクレジットメモを作成します。

<u>期待される結果</u>:

`inventory_reservation`に新しいレコードは作成されず、バーチャル製品の在庫量は変更されません。

<u>実際の結果</u>:

`creditmemo_created` レコードが`inventory_reservation`に作成され、バーチャル製品の在庫量が98に調整され、販売可能な数量が99になります。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [品質パッチツール ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) パッチを検索する」を参照してください。
