---
title: ACSD-64112:「MAGE_INDEXER_THREADS_COUNT」が設定されている場合、「indexer_update_all_views」 cron 実行が失敗します
description: ACSD-64112 パッチを適用すると、「MAGE_INDEXER_THREADS_COUNT」が設定されている場合に「indexer_update_all_views」 cron の実行が失敗するAdobe Commerceの問題を修正できます。
feature: Catalog Management, B2B
role: Admin, Developer
exl-id: c95f179d-5291-481f-b655-08a9db608513
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# ACSD-64112:`MAGE_INDEXER_THREADS_COUNT` が設定されている場合、`indexer_update_all_views` cron 実行が失敗する

>[!NOTE]
>
>このパッチは、2.4.7 より前のAdobe Commerce バージョンでは [ACP2E-3705](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-61/acp2e-3705-fixes-an-issue-where-the-indexer.md) に置き換えられました。

ACSD-64112 パッチは、`MAGE_INDEXER_THREADS_COUNT` が設定されている場合に `indexer_update_all_views` cron の実行が失敗する問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.59 がインストールされている場合に使用できます。 パッチ ID は ACSD-64112 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p10

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5 ～ 2.4.6-p10

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

`MAGE_INDEXER_THREADS_COUNT` が 2 より大きい値に設定されている場合、`indexer_update_all_views` cron の実行は失敗します。特に、B2B が有効になっている [!UICONTROL Customer Segments] インデクサーに影響します。

<u> 再現手順 </u>:

1. B2B でクリーンなインスタンスをインストールします。
1. **[!UICONTROL B2B Company]** と **[!UICONTROL Shared Catalog]** を有効にします。
1. カテゴリを作成します。
1. いくつかの製品を作成してカテゴリに割り当てます。
1. 完全な再インデックスを実行します。
1. 次のインデクサーを **[!UICONTROL Update on Schedule]** に設定します。

   ```
   bin/magento indexer:set-mode schedule catalogpermissions_category catalogpermissions_product
   ```

1. バックエンドに移動し、新しく作成したカテゴリを読み込みます。
1. 「**[!UICONTROL Category Permissions]**」をクリックし、既存の顧客グループの **[!UICONTROL New Permission]** を作成します。
1. `catalogpermissions_category` インデクサーにバックログがあることを確認します。 これを確認するには、次のコマンドを実行します。

   ```
   bin/magento indexer:status
   ```

1. `env.php` で次のインデクサースレッド数を設定します。

   ```php
   'MAGE_INDEXER_THREADS_COUNT' => 8
   ```

1. cron ジョブを実行します。

   ```
   bin/magento cron:run
   ```

<u> 期待される結果 </u>:

cron ジョブは問題なく実行する必要があります。

<u> 実際の結果 </u>:

`indexer_update_all_views` cron ジョブで次のエラーが発生します。

```
report.CRITICAL: PDOException: There is no active transaction in /home/vendor/magento/zend-db/library/Zend/Db/Adapter/Pdo/Abstract.php:326
```

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## パッチのインストール後に必要な追加手順

（この節はオプションです。問題を修正するためにパッチを適用した後に必要な手順が含まれる場合があります）。 

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
