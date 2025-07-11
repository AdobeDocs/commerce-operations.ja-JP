---
title: ACSD-64118：同じ製品に対する同時の製品保存リクエストにより、データの不整合とエントリの重複が発生する
description: ACSD-64118 パッチを適用すると、同じ商品を保存および更新する同時リクエストによってデータの不整合や商品の重複が発生するAdobe Commerceの問題が修正されます。
feature: REST
role: Admin, Developer
type: Troubleshooting
source-git-commit: 4235511ccbef028e1564d7626daadaa5beae0fd4
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---


# ACSD-64118：同じ製品に対する同時の製品保存リクエストにより、データの不整合とエントリの重複が発生する

ACSD-64118 パッチでは、同じ製品を保存および更新する同時リクエストによってデータの不整合や製品の重複が発生する問題が修正されています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.65 がインストールされている場合に使用できます。 パッチ ID は ACSD-64118 です。 この問題はAdobe Commerce 2.4.9 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p7

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.6-p10

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

同じ製品を保存および更新する同時リクエストによって、データの不整合や製品の重複が発生します。

<u> 再現手順 </u>:

1. `env.php` でコンシューマー向けにマルチプロセスを設定します。

   ```
   'multiple_processes' =>
       array (
           'async.operations.all' => 4,
       ),
   ```

1. メイン Web サイトにストアと新しいストアのレビューを追加します。
1. 次のペイロードを持つデフォルトの storereview エンドポイント `/rest/default/async/bulk/V1/products` に一括 API リクエストを送信して、製品を作成します。

   ```
   [
     {
       "product": {
         "sku": "Test_Prod",
         "name": "Test Product",
         "attribute_set_id": 4
       }
     }
   ]
   ```

1. 同じペイロードを使用して、新しい storereview エンドポイント `/rest/store/async/bulk/V1/products` に一括 API リクエストを送信し、製品を更新します。
1. キャッシュをフラッシュします。
1. cron ジョブを実行します。
1. 前の手順で取得した製品のエントリを `catalog_product_entity` の表で確認します。

<u> 期待される結果 </u>:

* 製品 SKU の 1 つのエントリが `catalog_product_entity` の表に存在する必要があります。
* 最初の REST API リクエストでは、1 つのデータベースエントリを作成し、後続のすべてのリクエストではそのデータベースエントリを更新する必要があります。

<u> 実際の結果 </u>:

同じ SKU の複数のエントリが `catalog_product_entity` テーブルに存在します。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
