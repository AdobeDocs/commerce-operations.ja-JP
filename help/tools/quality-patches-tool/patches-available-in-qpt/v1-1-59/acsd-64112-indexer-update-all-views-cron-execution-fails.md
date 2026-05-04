---
title: 'ACSD-64112: ''MAGE_INDEXER_THREADS_COUNT''が設定されていると、''indexer_update_all_views'' cronの実行が失敗する'
description: ACSD-64112 パッチを適用して、「MAGE_INDEXER_THREADS_COUNT」が設定されているときに「indexer_update_all_views」 cronの実行が失敗するAdobe Commerceの問題を修正します。
feature: Catalog Management, B2B
role: Admin, Developer
exl-id: c95f179d-5291-481f-b655-08a9db608513
type: Troubleshooting
source-git-commit: 319f3232d1ba5f5ed7cdd10ce85b9d7ffbeec89a
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# ACSD-64112: `MAGE_INDEXER_THREADS_COUNT`が設定されているときに`indexer_update_all_views` cronの実行が失敗する

>[!NOTE]
>
>このパッチは、2.4.7より前のAdobe Commerce バージョンの[ACP2E-3705](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-61/acp2e-3705-fixes-an-issue-where-the-indexer.md)に置き換えられました。

ACSD-64112 パッチは、`MAGE_INDEXER_THREADS_COUNT`が設定されているときに`indexer_update_all_views` cronの実行が失敗する問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.59がインストールされている場合に利用できます。 パッチ IDはACSD-64112です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p10

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5 - 2.4.6-p10

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

`MAGE_INDEXER_THREADS_COUNT`が2より大きい値に設定されていると、`indexer_update_all_views` cronの実行が失敗します。特に、B2Bが有効になっている[!UICONTROL Customer Segments] インデクサーに影響します。

<u>複製する手順</u>:

1. B2B クリーンインスタンスのインストール。
1. **[!UICONTROL B2B Company]**&#x200B;と&#x200B;**[!UICONTROL Shared Catalog]**&#x200B;を有効にします。
1. カテゴリを作成します。
1. いくつかの商品を作成し、カテゴリに割り当てます。
1. 完全なインデックス再作成を実行します。
1. 次のインデクサーを&#x200B;**[!UICONTROL Update on Schedule]**&#x200B;に設定します。

   ```shell
   bin/magento indexer:set-mode schedule catalogpermissions_category catalogpermissions_product
   ```

1. バックエンドに移動し、新しく作成したカテゴリを読み込みます。
1. **[!UICONTROL Category Permissions]**&#x200B;をクリックし、既存の顧客グループの&#x200B;**[!UICONTROL New Permission]**&#x200B;を作成します。
1. `catalogpermissions_category` インデクサーにバックログがあることを確認します。 これを確認するには、次のコマンドを実行します。

   ```shell
   bin/magento indexer:status
   ```

1. `env.php`で次のインデクサースレッド数を設定します。

   ```php
   'MAGE_INDEXER_THREADS_COUNT' => 8
   ```

1. cron ジョブを実行します。

   ```shell
   bin/magento cron:run
   ```

<u>期待される結果</u>:

cron ジョブは問題なく実行されます。

<u>実際の結果</u>:

`indexer_update_all_views` cron ジョブで次のエラーが発生しました：

```text
report.CRITICAL: PDOException: There is no active transaction in /home/vendor/magento/zend-db/library/Zend/Db/Adapter/Pdo/Abstract.php:326
```

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)」（Commerce クラウドインフラストラクチャガイド）。

## パッチのインストール後に必要な追加手順

（このセクションはオプションです。問題を修正するためにパッチを適用した後に必要な手順がいくつかある場合があります）。 

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
* Commerce Configuration Guideの[&#x200B; パラレルモードでのインデックス再作成](https://experienceleague.adobe.com/ja/docs/commerce-operations/configuration-guide/cli/manage-indexers#reindexing-in-parallel-mode)。
