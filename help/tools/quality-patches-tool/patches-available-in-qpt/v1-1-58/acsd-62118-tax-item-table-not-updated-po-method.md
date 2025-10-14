---
title: 'ACSD-62118: [!UICONTROL Purchase Order] メソッドを使用して発注された B2B 注文の''sales_order_tax_item'' テーブルが完全に更新されていません'
description: ACSD-62118 パッチを適用すると、[!UICONTROL Purchase Order] メソッドを使用して B2B 注文を行ったときに「sales_order_tax_item」テーブルが完全に更新されないAdobe Commerceの問題が修正されます。
feature: Purchase Orders, B2B
role: Admin, Developer
exl-id: 8ace73ad-f5a5-47ab-aca7-62c818775d2f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---

# ACSD-62118: `sales_order_tax_item` メソッド [!UICONTROL Purchase Order] 使用して注文された B2B 注文のテーブルが完全に更新されていません

ACSD-62118 パッチは、`sales_order_tax_item` メソッドを使用して B2B 注文を行ったときに *[!UICONTROL Purchase Order]* テーブルが完全に更新されない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58 がインストールされている場合に使用できます。 パッチ ID は ACSD-62118 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p3

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

*[!UICONTROL Purchase Order]* メソッドを使用して B2B 注文を送信した場合、`sales_order_tax_item` テーブルは完全には更新されません。 このイシューは、税計算と注文処理に影響します。 特に、API を使用して注文をクエリする場合、`applied_taxes` 配列は空で、`tax_item_amount` と `tax_item_percent` の両方が NULL です。

<u> 再現手順 </u>:

1. **[!UICONTROL Product]** と **[!UICONTROL Shipping]** の両方に対して税務処理基準を追加します。
1. 会社設定で **[!UICONTROL Purchase Order]** メソッドを有効にします。
1. 会社管理者ユーザーとしてログインします。
1. オフラインでの支払い方法を使用して **[!UICONTROL Purchase Order]** を配置します。
1. [!UICONTROL Purchase Order] が自動承認され、注文に変換されたら、`sales_order_tax_item` テーブルおよび REST API で税金データを確認します。

<u> 期待される結果 </u>:

* `sales_order_tax_item` テーブルには、`tax_item` データを含める必要があります。
* `applied_taxes` 配列には、他の支払い方法（小切手/マネーオーダーなど）と同様に、発注書に対する API 応答で正しい税金情報が表示されます。

<u> 実際の結果 </u>:

* `sales_order_tax_item` テーブルに `tax_item` データが含まれていません。
* `applied_taxes` の API 応答で、`item_applied_taxes` 配列と *[!UICONTROL Purchase Order]* 配列が空です。
* *[!UICONTROL Purchase Order]* 支払い方法を使用する場合、税金データは表示されません。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 &#x200B;](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [&#x200B; アップグレードとパッチ &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
