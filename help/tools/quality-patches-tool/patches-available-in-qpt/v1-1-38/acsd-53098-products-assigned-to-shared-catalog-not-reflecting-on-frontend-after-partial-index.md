---
title: ACSD-53098：共有カタログ内の製品がフロントエンドに反映されない
description: ACSD-53098 パッチを適用すると、共有カタログに割り当てられた商品が部分的なインデックスを実行したときにフロントエンドに反映されないAdobe Commerceの問題を修正できます。
feature: B2B, Catalog Management, Categories, Products
role: Admin, Developer
exl-id: 25230086-13b5-4b16-b50f-931e9e3d7102
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 0%

---

# ACSD-53098：共有カタログ内の製品がフロントエンドに反映されない

ACSD-53098 パッチは、共有カタログに割り当てられた製品が部分的なインデックスを実行したときにフロントエンドに反映されない問題を修正します。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.38 がインストールされている場合に使用できます。 パッチ ID は ACSD-53098 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3 - 2.4.3-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

API を介して共有カタログに割り当てられた製品は、部分インデクサーが cron ジョブを実行し、その後に消費者 cron が実行された後は、フロントエンドに表示されません。

<u> 再現手順 </u>:

1. [!DNL RabbitMQ] をキューサービスとして設定します。
1. インデクサーを **[!UICONTROL Update on Schedule]** モードに切り替えます。
1. 共有カタログを作成して会社に割り当てます。
1. シンプルな製品を作成してカテゴリに割り当てます。 部分再インデックスを実行します。

   `bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1`

1. 次の API リクエストを使用して、作成した製品を共有カタログに割り当てます。

   ```
   pub/rest/all/V1/sharedCatalog/<id>/assignProducts
   {
       "products":[{
           "sku": "24-MB06"
           }
       ]
   }
   ```

1. 次の cron を実行してキューをクリアし、部分再インデックスを実行します。

   `bin/magento cron:run --group=consumers`

   `bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1`

1. 会社のユーザーとしてフロントエンドにログインします。
1. フロントエンドカテゴリページを確認します。

<u> 期待される結果 </u>:

新しく割り当てられた製品がフロントエンドに表示されます。

<u> 実際の結果 </u>:

新しく割り当てられた製品は、フロントエンドには表示されません。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md)[!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)」を参照してください。
