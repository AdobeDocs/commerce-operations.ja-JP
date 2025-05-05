---
title: 「ACSD-45424：一部払い戻し後に作成された予約報酬が正しくありません」
description: ACSD-45424 パッチは、部分的な払い戻しの後に誤った予約報酬が作成される問題を修正します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/ja/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches） 1.1.17 がインストールされている場合に利用できます。 パッチ ID は ACSD-45424 です。 この問題はAdobe Commerce 2.4.6 で修正される予定であることに注意してください。
feature: Orders
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '571'
ht-degree: 0%

---

# ACSD-45424：一部払い戻し後に作成された予約報酬が正しくありません

ACSD-45424 パッチは、部分的な払い戻しの後に誤った予約報酬が作成される問題を修正します。 このパッチは、[Quality Patches Tool （QPT） ](https://experienceleague.adobe.com/ja/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)1.1.17 がインストールされている場合に使用できます。 パッチ ID は ACSD-45424 です。 この問題はAdobe Commerce 2.4.6 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.1

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.4 ～ 2.4.4

>[!NOTE]
>
>パッチは、新しい Quality Patches Tool リリースを使用する他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/ja/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

一部払い戻し後に、誤った予約報酬が作成されます。

<u> 再現手順 </u>:

1. 店舗内配送配送方法を有効にします。
1. 3 つの在庫ソースを作成し、それぞれに集荷場所がアクティブであることを確認します（source1、source2、source3）。
1. 新しい在庫を作成し、3 つのソースを新しい在庫に割り当てます。
   * この在庫は、メインの web サイトに割り当てる必要があります。
1. 単純な製品 P3 を作成し、すべてのソースを割り当てます。
1. 単純製品のソースに次の数量を追加し、バックオーダーを有効化します。
   * デフォルトソース - 100
   * ソース 1 - 0
   * ソース 2 - 10
   * ソース 3 - 0
1. フロントエンドからカートにシンプルな製品を追加し、配送フォームに進みます。
1. 出荷場所として「source1」を選択します。
1. 注文を完了し、データベースで次のクエリを実行します。

   ```sql
   SELECT * FROM inventory_reservation WHERE sku = 'P3';
   ```

   注文したレコードは `inventory_reservation` のテーブルに表示されます。 数量は 10 で、これは正しい値です。
1. この注文をバックエンドから請求します。
1. これで、1 つの製品のみのクレジットメモを作成します。 「*在庫に戻る*」チェックボックスを選択しないでください。
1. 手順 8 で同じクエリを実行します。

<u> 期待される結果 </u>:

クレジット・メモの作成時に *Return to Stock* を選択しなかった場合、クレジット・メモに対応するレコードは `inventory_reservation` の表には含まれません。

<u> 実際の結果 </u>:

クレジットメモの作成時に *Return to Stock* を選択しなくても、イベントタイプを使用してテーブルにレコード `inventory_reservation` 追加 `creditmemo_created` れます。 また、`inventory_reservation` 表に追加されたクレジット・メモ・レコードの数量は 10 ですが、クレジット・メモを作成した数量は 1 つのみです。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Sourceオンプレミス：[[!DNL Quality Patches Tool] > Usage](/help/tools/quality-patches-tool/usage.md) in the [!DNL Quality Patches Tool] guide.
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

品質向上パッチツールの詳細については、次を参照してください。

* [ 品質向上パッチツールがリリースされました：品質向上パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) がサポートナレッジベースに追加されました。
* [Quality Patches Tool を使用して、Adobe Commerceの問題に対するパッチが使用可能かどうかを確認します ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!DNL Quality Patches Tool] ガイド）。

QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)」を参照してください。
