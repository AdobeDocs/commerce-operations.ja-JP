---
title: 'ACSD-64813: REST API経由で[!DNL B2B]共有カタログのカテゴリの割り当て解除が遅い'
description: REST API経由で[!DNL B2B]共有カタログのカテゴリの割り当て解除が遅くなるAdobe Commerceの問題を修正するには、ACSD-64813 パッチを適用します。
feature: B2B, REST, Categories
role: Admin, Developer
type: Troubleshooting
exl-id: e6fd89c2-d3c0-462f-b328-7a80b456d96d
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
  - id: c4f010fa-1478-4300-a88d-706fbc036a7a
    internal-label: APIs and SDKs
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
  - id: e0ca0e7a-9738-48d1-b98b-615468ab4aaf
    internal-label: REST API
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
source-wordcount: '398'
ht-degree: 0%
---
# ACSD-64813: REST API経由で[!DNL B2B]共有カタログのカテゴリの割り当て解除が遅い

ACSD-64813 パッチは、REST APIを介して[!DNL B2B]共有カタログ内のカテゴリの割り当て解除が遅い問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.65がインストールされている場合に利用できます。 パッチ IDはACSD-64813です。 この問題は、Adobe Commerce 2.4.9で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p3

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.8

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

REST APIを介して[!DNL B2B]共有カタログ内のカテゴリの割り当てを解除すると、動作が遅くなります。

<u>複製する手順</u>:

1. **[!UICONTROL B2B]**、**[!UICONTROL Company]**、**[!UICONTROL Shared Catalog]**&#x200B;を有効にします。
1. 30,000点を超えるアクティブな在庫商品を創出。
1. [&#x200B; カスタム共有カタログ &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/shared-catalogs/catalog-shared#actions-controls)を作成し、すべての製品をそれに割り当てます。
1. デフォルトのルートカテゴリの下に新しいカテゴリを作成し、それにいくつかの製品を割り当てます。
1. 管理トークンを使用して、新しいカテゴリ IDでREST API エンドポイント `rest/all/V1/sharedCatalog/<shared_catalog_id>/assignCategories`を呼び出します。

   ```json
   {
     "categories": [
       { "id": <new category id> }
     ]
   }
   ```

1. 応答が&#x200B;*true*&#x200B;であることを確認してください。
1. `bin/magento cron:run`を2回実行するか、インデックス再作成を実行します。
1. 管理トークンを使用して、新しいカテゴリ IDでREST API エンドポイント `rest/all/V1/sharedCatalog/<shared_catalog_id>/unassignCategories`を呼び出します。

   ```json
   {
     "categories": [
       { "id": <new category id> }
     ]
   }
   ```

<u>期待される結果</u>:

操作は合理的な時間（数分以内）で完了する必要があります。

<u>実際の結果</u>:

実行には約30分かかるか、タイムアウトエラーが発生します。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
