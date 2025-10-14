---
title: ACSD-64813:REST API を使用した共有カタログ内のカテゴリ  [!DNL B2B]  割り当て解除が遅い
description: ACSD-64813 パッチを適用すると、Adobe Commerceの問題を修正できます。この問題では、REST API を使用して共有カタログのカテゴリの割り当て解除を行  [!DNL B2B]  と時間がかかります。
feature: B2B, REST, Categories
role: Admin, Developer
type: Troubleshooting
exl-id: e6fd89c2-d3c0-462f-b328-7a80b456d96d
source-git-commit: 239a9efcc2ae231b337f654e4e36e6119e6eff7e
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# ACSD-64813:REST API を使用した共有カタログ内のカテゴリ [!DNL B2B] 割り当て解除が遅い

ACSD-64813 パッチでは、[!DNL B2B] 共有カタログのカテゴリの割り当て解除が REST API を使用して遅くなる問題が修正されています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.65 がインストールされている場合に使用できます。 パッチ ID は ACSD-64813 です。 この問題はAdobe Commerce 2.4.9 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p3

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.8

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

REST API を使用して [!DNL B2B] 共有カタログのカテゴリの割り当てを解除する処理が遅い。

<u> 再現手順 </u>:

1. **[!UICONTROL B2B]**、**[!UICONTROL Company]**、**[!UICONTROL Shared Catalog]** を有効にします。
1. 30,000 個のアクティブな在庫製品を生成します。
1. [&#x200B; カスタム共有カタログ &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce-admin/b2b/shared-catalogs/catalog-shared#actions-controls) を作成し、すべての製品を割り当てます。
1. デフォルトのルートカテゴリの下に新しいカテゴリを作成し、いくつかの製品を割り当てます。
1. 管理トークンを使用して、新しいカテゴリ ID で REST API エンドポイント `rest/all/V1/sharedCatalog/<shared_catalog_id>/assignCategories` を呼び出します。

   ```
   {
     "categories": [
       { "id": <new category id> }
     ]
   }
   ```

1. 応答が *true* であることを確認します。
1. `bin/magento cron:run` を 2 回実行するか、再インデックスを実行します。
1. 管理トークンを使用して、新しいカテゴリ ID で REST API エンドポイント `rest/all/V1/sharedCatalog/<shared_catalog_id>/unassignCategories` を呼び出します。

   ```
   {
     "categories": [
       { "id": <new category id> }
     ]
   }
   ```

<u> 期待される結果 </u>:

操作は適切な時間で完了する必要があります（数分以内）。

<u> 実際の結果 </u>:

実行には約 30 分かかるか、タイムアウトエラーが発生します。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 &#x200B;](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [&#x200B; アップグレードとパッチ &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
