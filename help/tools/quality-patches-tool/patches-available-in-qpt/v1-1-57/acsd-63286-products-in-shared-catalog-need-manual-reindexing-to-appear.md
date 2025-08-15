---
title: ACSD-63286：共有カタログに割り当てられた製品を表示するには、手動でのインデックス再作成が必要です
description: ACSD-63286 パッチを適用すると、API を介して共有カタログに割り当てられた商品が、手動の再インデックスが実行されるまでストアフロントに表示されないAdobe Commerceの問題を修正できます。
feature: Products, REST
role: Admin, Developer
exl-id: 0435c06e-337e-4320-acc6-fa79a3b34008
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---

# ACSD-63286：共有カタログに割り当てられた製品を表示するには、手動でのインデックス再作成が必要です

ACSD-63286 パッチでは、API を介して共有カタログに割り当てられた製品が、手動の再インデックスが実行されるまでストアフロントに表示されない問題を修正しました。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57 がインストールされている場合に使用できます。 パッチ ID は ACSD-63286 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p6

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6 - 2.4.6-p8

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

API 経由で製品が共有カタログに割り当てられた場合、部分インデクサーおよびコンシューマークローンジョブの実行後は、製品はフロントエンドに表示されません。 ただし、手動で完全にインデックスを再作成した後は表示されます。

<u> 再現手順 </u>:

1. [!DNL RabbitMQ] をキューサービスとして設定します。
1. 共有カタログを作成して会社に割り当てます。
1. シンプルな製品を作成してカテゴリに割り当てます。
1. 部分再インデックスを実行します。

   ```
   bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1
   ```

1. 次の API リクエストを使用して、作成した製品を共有カタログの `pub/rest/all/V1/sharedCatalog/<id>/assignProducts` に割り当てます。

   ```
   {
       "products":[{
           "sku": "24-MB06"
           }
       ]
   }
   ```

1. 次の cron を実行してキューをクリアし、部分再インデックスを実行します。

   ```
   bin/magento cron:run --group=consumers
   ```

   ```
   bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1
   ```

1. 会社のユーザーとしてフロントエンドにログインします。
1. フロントエンドカテゴリページを確認します。 新しく割り当てられた製品は表示されません。
1. 手動のインデックス再作成を実行します。

   ```
   bin/magento index:reindex
   ```

<u> 期待される結果 </u>:

この製品は、手動でインデックスを再作成しなくてもフロントエンドに表示されます。

<u> 実際の結果 </u>:

製品は、手動でインデックスを再作成した後にのみ、フロントエンドに表示されます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。


## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
