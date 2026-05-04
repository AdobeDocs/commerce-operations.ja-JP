---
title: ACSD-64118：同じ製品に対する同時製品の保存リクエストが原因で、データの不整合とエントリの重複が発生する
description: ACSD-64118 パッチを適用して、同じ商品を保存および更新する同時リクエストがデータの不整合または商品の重複につながるAdobe Commerceの問題を修正します。
feature: REST
role: Admin, Developer
type: Troubleshooting
exl-id: e014645e-72b2-4b3d-8b44-3daca502c950
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 0%

---

# ACSD-64118：同じ製品に対する同時製品の保存リクエストが原因で、データの不整合とエントリの重複が発生する

ACSD-64118 パッチでは、同じ製品を保存して更新する同時要求によって、データの不整合や製品の重複が生じる問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.65がインストールされている場合に利用できます。 パッチ IDはACSD-64118です。 この問題は、Adobe Commerce 2.4.9で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p7

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.6-p10

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

同じ製品を保存して更新する要求を同時に行うと、データの不整合や製品の重複が発生します。

<u>複製する手順</u>:

1. `env.php`でコンシューマーのマルチプロセスを設定します。

   ```text
   'multiple_processes' =>
       array (
           'async.operations.all' => 4,
       ),
   ```

1. メイン web サイトに新しいストアと新しいストアビューを追加します。
1. 製品を作成するには、次のペイロードを使用して、デフォルトのストアビューエンドポイント `/rest/default/async/bulk/V1/products`に一括API リクエストを送信します。

   ```text
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

1. 同じペイロードを使用して、製品を更新するために新しいストアビューエンドポイント `/rest/store/async/bulk/V1/products`に一括API リクエストを送信します。
1. キャッシュをフラッシュします。
1. cron ジョブを実行します。
1. 前の手順の製品のエントリについては、`catalog_product_entity` テーブルを確認してください。

<u>期待される結果</u>:

* 製品SKUの1つのエントリが`catalog_product_entity` テーブルに存在する必要があります。
* 最初のREST API リクエストでは、1つのデータベースエントリを作成し、その後のすべてのリクエストはそのデータベースエントリを更新する必要があります。

<u>実際の結果</u>:

同じSKUに対する複数のエントリが`catalog_product_entity` テーブルに存在します。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
