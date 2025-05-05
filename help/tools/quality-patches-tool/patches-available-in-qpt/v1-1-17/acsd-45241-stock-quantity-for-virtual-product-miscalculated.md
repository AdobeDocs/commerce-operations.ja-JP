---
title: 「ACSD-45241：仮想製品の在庫数の計算ミス」
description: ACSD-45241 パッチは、クレジットメモを作成した後に仮想製品の在庫数が誤って計算される問題を修正します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/ja/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches） 1.1.17 がインストールされている場合に利用できます。 パッチ ID は ACSD-45241 です。 この問題はAdobe Commerce 2.4.4 で修正されました。
feature: Orders, Products
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '500'
ht-degree: 0%

---

# ACSD-45241：仮想製品の在庫数の計算ミス

ACSD-45241 パッチは、クレジットメモを作成した後に仮想製品の在庫数が誤って計算される問題を修正します。 このパッチは、[Quality Patches Tool （QPT） ](https://experienceleague.adobe.com/ja/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)1.1.17 がインストールされている場合に使用できます。 パッチ ID は ACSD-45241 です。 この問題はAdobe Commerce 2.4.4 で修正されました。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.5 ～ 2.4.4

>[!NOTE]
>
>パッチは、新しい Quality Patches Tool リリースを使用する他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/ja/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

仮想商品の在庫数が、クレジットメモの作成後に誤って計算されます。

<u> 再現手順 </u>:

1. Commerce Admin で、バーチャル製品を子製品として使用して設定可能な製品を作成します。
1. 手順 1 で作成した両方の製品が在庫にあることを確認します。
1. 手順 1 で作成したバーチャル製品の数量を 100 としてマークし、販売可能数量を 100 のままにします。
1. 商品を買い物かごに追加します。
1. 手順 1 で作成した仮想製品で注文します。
1. 注文ステータスは「保留中」のままにします。 支払いを処理する必要はありません。
1. `inventory_reservation` `order_created` 作成されたレコード。 仮想製品数量は 100 で、販売可能数量は 99 です。
1. 注文を開き、**請求書**/**請求書を送信** に移動します。
1. `inventory_reservation` `invoice_created` 作成されたレコード。 仮想製品数量は 99 になり、販売可能数量も 99 になります。
1. 「在庫に戻る **を選択せずにクレジットメモを作成** ます。

<u> 期待される結果 </u>:

`inventory_reservation` に新しいレコードは作成されず、バーチャル製品の在庫数は変更されません。

<u> 実際の結果 </u>:

`inventory_reservation` で `creditmemo_created` レコードが作成され、仮想製品の在庫数は 98 に調整され、販売可能数は 99 になります。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Sourceオンプレミス：[[!DNL Quality Patches Tool] > Usage](/help/tools/quality-patches-tool/usage.md) in the [!DNL Quality Patches Tool] guide.
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

品質向上パッチツールの詳細については、次を参照してください。

* [ 品質向上パッチツールがリリースされました：品質向上パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) がサポートナレッジベースに追加されました。
* [Quality Patches Tool を使用して、Adobe Commerceの問題に対するパッチが使用可能かどうかを確認します ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!DNL Quality Patches Tool] ガイド）。

QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)」を参照してください。
