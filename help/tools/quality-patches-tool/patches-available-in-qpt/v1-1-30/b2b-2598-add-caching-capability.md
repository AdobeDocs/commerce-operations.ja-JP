---
title: B2B-2598:storeConfig、通貨、国、国、利用可能なStores GraphQl クエリにキャッシュ機能を追加
description: B2B-2598 パッチを適用して、storeConfig、通貨、国、国、利用可能なStores GraphQl クエリにキャッシュ機能を追加します。
feature: B2B, GraphQL, Cache
role: Admin
type: Troubleshooting
autotag-review: '2026-05-22T20:21:20.687Z'
TQID: 'https://experienceleague.adobe.com/DQWkSrUHcUhOTn3fWdnRPVQUK6jRkPGCAnIKPRHkebQ'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: c32adafa-ed01-4b31-997e-2413013911b0
subfeature_v2:
  - id: e396cff5-f586-484c-89f0-7f1da3308f92
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
topic_v2:
  - id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
industry_v2:
  - id: aad1e361-483a-40cf-9a88-144325515074
source-git-commit: 891f738f4a3db4e361984d11585f3679068c8ced
workflow-type: tm+mt
source-wordcount: 458
ht-degree: 0%

---

# B2B-2598: `storeConfig`、`currency`、`country`、`countries`、および`availableStores`個のGraphQl クエリにキャッシュ機能を追加

B2B-2598 パッチでは、`storeConfig`、`currency`、`country`、`countries`、および`availableStores`個のGraphQl クエリにキャッシュ機能が追加されています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.30がインストールされている場合に利用できます。 パッチ IDはB2B-2598です。 この問題は、Adobe Commerce 2.4.7-beta1で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.6

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.6

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

`availableStores`、`countries`、`country`、`currency`、`storeConfig`および`customAttributeMetadata` GraphQL クエリはキャッシュできません。

<u>前提条件</u>:

* サーバーがAdobe Commerce バックエンドに[!DNL Varnish] プロキシを指定しています。
* 設定設定`system/full_page_cache/caching_application`は&#x200B;*2* （[!DNL Varnish]）に設定されているか、Adobe Commerce Admin > **[!UICONTROL Stores]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Caching Application]** >に移動して[!DNL Varnish]に設定します。

パッチが適用されたら、次の手順を実行して、キャッシュ機能が使用可能になったことを確認します。

1. 任意のフィールドを使用して、上記のGraphQL クエリのいずれかに`GET` リクエストを送信します。
1. 変更を加えずにリクエストを再送信します。はるかに速くなります。 リクエストはバックエンドに送信されませんが、キャッシュヒットとして[!DNL Varnish]によって完全に処理されます。
1. さらにプルーフが必要な場合は、[VCL](https://github.com/magento/magento2/blob/026e5b29a5edfd619bbdea62d636b3cab2ea03b4/app/code/Magento/PageCache/etc/varnish6.vcl#L227)に存在する`X-Magento-Debug` ヘッダーのアンセットをコメントし、[!DNL Varnish]を再起動して、上記の手順を再度実行します。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
