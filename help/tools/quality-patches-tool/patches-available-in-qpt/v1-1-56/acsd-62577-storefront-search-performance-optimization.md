---
title: 'ACSD-62577: ストアフロント検索パフォーマンスの最適化'
description: ACSD-62577 パッチを適用して、大きな「search_query」テーブルによってクエリの実行が遅くなったためにストアフロントの検索パフォーマンスが低下するAdobe Commerceの問題を修正します。
feature: Search
role: Admin, Developer
exl-id: 211c1e3c-0739-4ff6-a25c-b27d335920d1
type: Troubleshooting
source-git-commit: 319f3232d1ba5f5ed7cdd10ce85b9d7ffbeec89a
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# ACSD-62577: ストアフロント検索パフォーマンスの最適化

ACSD-62577 パッチは、クエリインデックスとテーブルインデックスの両方を最適化することで、ストアフロント検索クエリのパフォーマンスが遅くなる問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56で利用できます。 パッチ IDはACSD-62577です。 この問題は、Adobe Commerce 2.4.8で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

Adobe Commerce（すべてのデプロイメント方法） 2.4.6、2.4.7-p2

**Adobe Commerceのバージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

大きな`search_query` テーブルでは、ストアフロントの検索が大幅に遅くなり、非効率的なクエリと最適化されたテーブルインデックスの欠如により、フロントエンドの応答時間が増加します。

<u>複製する手順</u>:

1. パフォーマンス ツールキット `small.xml`を使用してAdobe Commerce Developを設定します。
1. SQL コマンドラインにアクセスし、次のコマンドを使用して`search_query` テーブルを削除します。

   ```text
   SET FOREIGN_KEY_CHECKS = 0;  
   DROP TABLE search_query;  
   SET FOREIGN_KEY_CHECKS = 1;  
   ```

1. `search_query` テーブルに多数のレコード（例：400万件のレコード）を入力します。
1. トリガーのインデックス再作成とキャッシュのフラッシュ。

   ```shell
   bin/magento indexer:reindex  
   bin/magento c:c  
   bin/magento c:f  
   ```

1. データベースのデバッグログを有効にします。

   ```shell
   bin/magento dev:query-log:enable  
   ```

1. ストアフロントの検索バーでキーワードを検索します（例：
   `http://your_magento_instance/default/catalogsearch/result/?q=test.`
1. 次のSQLのクエリ実行時間については、`db.log`を確認してください。

   ```sql
   SELECT COUNT(*) FROM (  
   SELECT DISTINCT `main_table`.`query_text`  
   FROM `search_query` AS `main_table`  
   WHERE (main_table.store_id IN (1))  
   AND (main_table.num_results > 0)  
   ORDER BY `main_table`.`popularity` DESC  
   LIMIT 100  ) AS `result` WHERE (result.query_text = 'test')  
   ```

<u>期待される結果</u>:

クエリ実行時間が最適化され、大きな`search_query` テーブルを処理する際の応答時間の大幅な増加が少なくなります。

<u>実際の結果</u>:

大きな`search_query` テーブルの処理が非効率的なため、クエリの実行時間が大幅に増加します。

```text
TIME: 10.8520 seconds  
```

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
