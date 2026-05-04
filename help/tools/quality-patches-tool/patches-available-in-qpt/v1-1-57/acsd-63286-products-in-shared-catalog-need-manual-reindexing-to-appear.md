---
title: ACSD-63286：共有カタログに割り当てられた製品を表示するには、手作業によるインデックス再作成が必要です
description: APIを介して共有カタログに割り当てられた商品がストアフロントに表示されないAdobe Commerceの問題を修正するには、ACSD-63286 パッチを適用して、手動でインデックス再作成を実行します。
feature: Products, REST
role: Admin, Developer
exl-id: 0435c06e-337e-4320-acc6-fa79a3b34008
type: Troubleshooting
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---

# ACSD-63286：共有カタログに割り当てられた製品を表示するには、手作業によるインデックス再作成が必要です

ACSD-63286 パッチでは、APIを介して共有カタログに割り当てられた製品が、手動でインデックス再作成が実行されるまでストアフロントに表示されない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57がインストールされている場合に利用できます。 パッチ IDはACSD-63286です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p6

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6 - 2.4.6-p8

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

APIを介して共有カタログに製品が割り当てられている場合、部分的なインデクサーとコンシューマーのcron ジョブの実行後にフロントエンドに製品が表示されません。 ただし、手動で完全にインデックスを再作成した後に表示されます。

<u>複製する手順</u>:

1. [!DNL RabbitMQ]をキューサービスとして設定します。
1. 共有カタログを作成し、それを会社に割り当てます。
1. シンプルな商品を作成し、カテゴリーに割り当てる：
1. 部分的なインデックス再作成を実行します。

   ```shell
   bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1
   ```

1. 次のAPI リクエストを使用して、作成した製品を共有カタログ `pub/rest/all/V1/sharedCatalog/<id>/assignProducts`に割り当てます。

   ```json
   {
       "products":[{
           "sku": "24-MB06"
           }
       ]
   }
   ```

1. 次のcronを実行して、キューをクリアし、部分的なインデックス再作成を実行します。

   ```shell
   bin/magento cron:run --group=consumers
   ```

   ```shell
   bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1
   ```

1. 企業ユーザーとしてフロントエンドにログインします。
1. フロントエンドのカテゴリーページを確認します。 新しく割り当てられた製品は表示されません。
1. 手動でインデックスを再作成します。

   ```shell
   bin/magento index:reindex
   ```

<u>期待される結果</u>:

この製品は、手作業によるインデックス再作成を行うことなくフロントエンドに表示されます。

<u>実際の結果</u>:

製品は、手動でインデックスを再作成した後にのみフロントエンドに表示されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。


## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
