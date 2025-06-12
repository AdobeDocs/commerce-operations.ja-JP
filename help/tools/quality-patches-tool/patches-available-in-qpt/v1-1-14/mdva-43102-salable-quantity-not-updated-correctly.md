---
title: MDVA-43102：販売可能数量が正しく更新されていません
description: MDVA-43102 パッチは、REST API を介して払い戻しが行われた際に、販売可能数量が正しく更新されない問題を修正します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.14 がインストールされている場合に利用できます。 パッチ ID は MDVA-43102。 この問題はAdobe Commerce 2.4.5 で修正される予定であることに注意してください。
feature: Variables
role: Admin
exl-id: 6a10f586-bbde-4252-9b8e-9b2b712f0fb3
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 0%

---

# MDVA-43102：販売可能数量が正しく更新されていません

MDVA-43102 パッチは、REST API を介して払い戻しが行われた際に、販売可能数量が正しく更新されない問題を修正します。 このパッチは、[Quality Patches Tool （QPT） ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)1.1.14 がインストールされている場合に使用できます。 パッチ ID は MDVA-43102。 この問題はAdobe Commerce 2.4.5 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.1 ～ 2.4.4

>[!NOTE]
>
>パッチは、新しい Quality Patches Tool リリースを使用する他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

REST API を使用して返金を行った場合、販売可能数量が正しく更新されない。

<u> 再現手順 </u>:

1. 買い物かごに商品を追加します。
1. 「在庫数量」と「販売可能数量」をチェックします。
1. オーダーを作成します。
1. 必要に応じて請求書を作成します。
1. 次のペイロードを使用して、請求書の払い戻しに REST リクエストを送信します。

   * オフライン方法/注文/`<order_id>` 注/返金
   * オンライン方法/請求書/`<invoice_id>` 金/払戻

   ```rest
   {
     "items": [
     {
       "order_item_id": <order_item_id>,
       "qty": 1
     }
     ],
     "notify": true,
     "arguments": {
       "shipping_amount": 5,
       "extension_attributes": {
         "return_to_stock_items": [
         <order_item_id>
         ]
       }
     }
   }
   ```

1. アイテムを出荷しないでください。
1. 以前の在庫数量と販売可能数量を比較します。 両方とも同じ量で更新する必要があります。

<u> 期待される結果 </u>:

注文を出荷する前に払い戻しが発行され、製品が在庫に戻されると、販売可能な数量が正しく更新されます。

<u> 実際の結果 </u>:

注文を発送する前に払い戻しが発行され、商品が在庫に戻された場合、販売可能数量は更新されません。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md)[!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

品質向上パッチツールの詳細については、次を参照してください。

* [ 品質向上パッチツールがリリースされました：品質向上パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) がサポートナレッジベースに追加されました。
* [Quality Patches Tool を使用して、Adobe Commerceの問題に対するパッチが使用可能かどうかを確認します ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!DNL Quality Patches Tool] ガイド）。

QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)」を参照してください。
