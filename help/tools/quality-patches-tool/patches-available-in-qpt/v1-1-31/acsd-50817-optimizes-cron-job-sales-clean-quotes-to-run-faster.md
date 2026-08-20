---
title: 'ACSD-50817: cron ジョブ sales_clean_quotesを最適化して高速に実行します'
description: ACSD-50817 パッチを適用して、cron ジョブ「sales_clean_quotes」を最適化し、quote テーブルの「store_id」列と「updated_at」列に複合インデックスを追加して高速に実行します。
feature: Quotes
role: Admin
exl-id: b6cd412f-2f37-438b-9abc-d45de6ed54d6
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# ACSD-50817: cron ジョブ `sales_clean_quotes`を高速に実行するように最適化します

ACSD-50817 パッチは、引用テーブルの`store_id`列と`updated_at`列に複合インデックスを追加することで、cron ジョブ `sales_clean_quotes`をより高速に実行するように最適化します。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.31がインストールされている場合に利用できます。 パッチ IDはACSD-50817です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.7 - 2.4.6

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

cron ジョブ `sales_clean_quotes`が遅すぎます。 このパッチでは、引用テーブルの`store_id`列と`updated_at`列に複合インデックスを追加することで、より高速に実行するように最適化されました。

<u>複製する手順</u>:

1. `updated_at`が30日以内に設定されている場合、50～80 Mの見積もりを生成します。
1. 見積テーブルでcron ジョブ `sales_clean_quotes`または次のクエリを実行します。

   ```cron
   SELECT COUNT(*) FROM `quote` AS `main_table` WHERE (`store_id` = '1') AND (`updated_at` <= '2023-02-25') AND (`is_persistent` = '0')
   
   SELECT * FROM `quote` AS `main_table` WHERE (`store_id` = '1') AND (`updated_at` <= '2023-02-25') AND (`is_persistent` = '0') LIMIT 50
   ```

<u>期待される結果</u>

Cron ジョブ `sales_clean_quotes`は、引用テーブルの`store_id`列と`updated_at`列に複合インデックスを追加することで、より高速に実行するように最適化されています。

<u>実際の結果</u>

クエリが遅すぎます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
