---
title: ACSD-61805:REST API を使用してバックオーダーのステータスを更新した後、ストアフロントの在庫の問題を修正しました
description: REST API を使用してバックオーダーのステータスを更新した後、商品がストアフロントで在庫切れのままになるAdobe Commerceの問題を修正するために、ACSD-61805 パッチを適用します
feature: REST, Catalog Management, Inventory
role: Admin, Developer
source-git-commit: abad1a2f2a1bdc2c1a4b6f821e6b02190a5ebe83
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---


# ACSD-61805:REST API を使用してバックオーダーのステータスを更新した後、ストアフロントの在庫の問題を修正しました

ACSD-61805 パッチは、REST API を使用してバックオーダーのステータスを更新した後、製品がストアフロントに残り、在庫切れになる問題を修正しました。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56 がインストールされている場合に使用できます。 パッチ ID は ACSD-61805 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

REST API を使用してバックオーダーのステータスを更新した後、製品はストアフロントで在庫切れのままになります。

<u> 再現手順 </u>:

1. サンプルデータを含んだクリーンなインスタンスをインストールします。
1. 新規在庫ソースを作成します。
1. 新しい在庫在庫を作成し、それに新しいソースを割り当てます。
1. 新しいソースを製品 24-MB01 に割り当てます。
1. 両方の製品ソースで **[!UICONTROL Source Item Status]** を `In Stock` に設定します。
1. 両方の製品数量の数量（**[!UICONTROL QTY]**）を *0* に設定します。
1. 商品を保存します。
1. 次のエンドポイント URL から管理トークンを取得します：`/rest/default/V1/integration/admin/token`

   ```json
   {
     "username":"admin", 
     "password":"password" 
   }
   ```

1. エンドポイント `/rest/default/V1/products` を使用して製品を更新します。

   ```json
   {
     "product":{
       "sku": "24-MB01",
       "extension_attributes": {
           "stock_item": {
               "stock_id": "1",
               "is_in_stock": "0",
               "use_config_backorders": "false",
               "backorders": "0"
           }
       }
     }
   }
   ```

1. cron ジョブを 2 回実行します（1 回はスケジュールを作成し、1 回はスケジュールを実行）。

   ```bash
   bin/magento cron:run
   ```

1. フロントエンドに移動し、製品を確認します。

<u> 期待される結果 </u>:

商品は *在庫* である必要があります。

<u> 実際の結果 </u>:

製品が *在庫切れ* です。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Sourceオンプレミス：[[!DNL Quality Patches Tool] > Usage](/help/tools/quality-patches-tool/usage.md) in the [!DNL Quality Patches Tool] guide.
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
