---
title: ACSD-61805：バックオーダーステータスの更新後、REST APIを使用してストアフロントの在庫の問題を修正しました
description: REST API経由でバックオーダーステータスを更新した後、ストアフロントで商品が在庫切れのままになるAdobe Commerceの問題を修正するには、ACSD-61805 パッチを適用します
feature: REST, Catalog Management, Inventory
role: Admin, Developer
exl-id: ff85e747-6394-43db-a02a-87b1e5e59f00
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: 8dc0e58b-adf0-51bb-8db5-bb36e3e656fb
    internal-label: Inventory
  - id: c4f010fa-1478-4300-a88d-706fbc036a7a
    internal-label: APIs and SDKs
subfeature_v2:
  - id: e0ca0e7a-9738-48d1-b98b-615468ab4aaf
    internal-label: REST API
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 0%
---
# ACSD-61805：バックオーダーステータスの更新後、REST APIを使用してストアフロントの在庫の問題を修正しました

ACSD-61805 パッチは、REST APIを介してバックオーダーステータスを更新した後、ストアフロントで製品が在庫切れのままになる問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56がインストールされている場合に利用できます。 パッチ IDはACSD-61805です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

REST APIでバックオーダーのステータスを更新した後、ストアフロントで商品の在庫が切れたままになります。

<u>複製する手順</u>:

1. サンプルデータを使用してクリーンインスタンスをインストールします。
1. 新しい在庫ソースを作成します。
1. 新しい在庫在庫を作成し、それに新しいソースを割り当てます。
1. 新しいソースを製品24-MB01に割り当てます。
1. 両方の製品ソースの&#x200B;**[!UICONTROL Source Item Status]**&#x200B;を`In Stock`に設定します。
1. 両方の製品数量の数量（**[!UICONTROL QTY]**）を&#x200B;*0*&#x200B;に設定します。
1. 製品を保存します。
1. このエンドポイント URLから管理トークンを取得します：`/rest/default/V1/integration/admin/token`

   ```json
   {
     "username":"admin", 
     "password":"password" 
   }
   ```

1. エンドポイント `/rest/default/V1/products`を使用して製品を更新します

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

1. cron ジョブを2回実行します（スケジュールを作成するには1回、スケジュールを実行するには1回）。

   ```shell
   bin/magento cron:run
   ```

1. フロントエンドに移動して製品を確認します。

<u>期待される結果</u>:

商品は&#x200B;*在庫*&#x200B;である必要があります。

<u>実際の結果</u>:

製品は&#x200B;*在庫切れ*&#x200B;です。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
