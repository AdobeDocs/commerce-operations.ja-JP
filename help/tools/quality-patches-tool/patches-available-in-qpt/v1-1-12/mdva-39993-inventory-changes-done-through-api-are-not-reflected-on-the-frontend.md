---
title: 「MDVA-39993:API を使用して行われたインベントリの変更がストアフロントに反映されない」
description: MDVA-39993 パッチは、API を介して行われたインベントリの変更がストアフロントに反映されない問題を解決します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/ja/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches） 1.1.12 がインストールされている場合に利用できます。 パッチ ID は MDVA-39993。 この問題はAdobe Commerce 2.4.5 で修正される予定であることに注意してください。
feature: REST, Inventory, Orders, Storefront
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '508'
ht-degree: 0%

---

# MDVA-39993: API を使用して行われたインベントリの変更がストアフロントに反映されない

MDVA-39993 パッチは、API を介して行われたインベントリの変更がストアフロントに反映されない問題を解決します。 このパッチは、[Quality Patches Tool （QPT） ](https://experienceleague.adobe.com/ja/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)1.1.12 がインストールされている場合に使用できます。 パッチ ID は MDVA-39993。 この問題はAdobe Commerce 2.4.5 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2-p1

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.5 ～ 2.3.7-p2 および 2.4.0 ～ 2.4.3-p1

>[!NOTE]
>
>パッチは、新しい Quality Patches Tool リリースを使用する他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/ja/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

API を通じて行われた在庫の変更は、ストアフロントの製品ページには反映されません。

<u> 前提条件 </u>:

インストール済みのインベントリモジュール。

<u> 再現手順 </u>:

1. キューが cron で実行するように設定され、cron がインストールされ実行中であることを確認します。
1. 2 つの色（黒と赤）、2 つのサイズ（M と L）を持つ設定可能な製品（COC001）を作成します。
1. 在庫切れ（COC001-Red-M）を 1 つ作成します。
1. 設定可能な製品ページをストアフロントに読み込んで、各色をクリックしてみてください。 **赤** をクリックすると、在庫切れのため **M** サイズが消えます。
1. 次の API エンドポイントとペイロードを使用して、COC001-Red-M を在庫にします。

   ```json
   POST http://{domain}/rest/V1/inventory/source-items
   
   {
     "sourceItems": [
       {
         "sku": "COC001-Red-M",
         "source_code": "default",
         "quantity": 1000,
         "status": 1
       }
     ]
   }
   ```

1. バックエンドからこの単純な製品をチェックし、それが In Stock に更新されていることを確認します。
1. フロントエンドから設定可能な製品を読み込み、各色をクリックします。 **赤** をクリックすると、サイズ **M** に注目してください。

<u> 期待される結果 </u>:

API を使用して在庫に更新したので、COC001-Red-M オプションは廃止されません。

<u> 実際の結果 </u>:

COC001-Red-M オプションは、在庫があるにもかかわらず、まだ取り消されています。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Sourceオンプレミス：[[!DNL Quality Patches Tool] > Usage](/help/tools/quality-patches-tool/usage.md) in the [!DNL Quality Patches Tool] guide.
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

品質向上パッチツールの詳細については、次を参照してください。

* [ 品質向上パッチツールがリリースされました：品質向上パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) がサポートナレッジベースに追加されました。
* [Quality Patches Tool を使用して、Adobe Commerceの問題に対するパッチが使用可能かどうかを確認します ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!DNL Quality Patches Tool] ガイド）。

QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)」を参照してください。
