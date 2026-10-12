---
title: ACSD-53098：共有カタログ内の製品がフロントエンドに反映されない
description: ACSD-53098 パッチを適用して、共有カタログに割り当てられた商品が、部分的なインデックスを実行してもフロントエンドに反映されないAdobe Commerceの問題を修正します。
feature: B2B, Catalog Management, Categories, Products
role: Admin, Developer
exl-id: 25230086-13b5-4b16-b50f-931e9e3d7102
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
  - id: e91a50b1-0b31-436e-9033-00e4776e94cb
    internal-label: Categories
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
source-wordcount: '442'
ht-degree: 0%
---
# ACSD-53098：共有カタログ内の製品がフロントエンドに反映されない

ACSD-53098 パッチは、部分的なインデックスを実行すると、共有カタログに割り当てられた製品がフロントエンドで反映されない問題を修正します。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.38がインストールされている場合に利用できます。 パッチ IDはACSD-53098です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3 - 2.4.3-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

APIを介して共有カタログに割り当てられた製品は、部分的なインデクサーがcron ジョブを実行し、コンシューマーcronが実行された後、フロントエンドに表示されません。

<u>複製する手順</u>:

1. [!DNL RabbitMQ]をキューサービスとして設定します。
1. インデクサーを&#x200B;**[!UICONTROL Update on Schedule]** モードに切り替えます。
1. 共有カタログを作成して、会社に割り当てます。
1. シンプルな商品を作成し、カテゴリーに割り当てる： 部分再インデックスを実行します。

   `bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1`

1. 次のAPI リクエストを使用して、作成した製品を共有カタログに割り当てます。

   ```text
   pub/rest/all/V1/sharedCatalog/<id>/assignProducts
   {
       "products":[{
           "sku": "24-MB06"
           }
       ]
   }
   ```

1. 次のcronを実行してキューをクリアし、部分再インデックスを実行します。

   `bin/magento cron:run --group=consumers`

   `bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1`

1. 会社のユーザーとしてフロントエンドにログインします。
1. フロントエンドのカテゴリーページを確認します。

<u>期待される結果</u>:

新しく割り当てられた製品がフロントエンドに表示されます。

<u>実際の結果</u>:

新しく割り当てられた製品がフロントエンドに表示されない。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
