---
title: ACSD-62577：ストアフロント検索のパフォーマンスの最適化
description: ACSD-62577 パッチを適用すると、大きな「search_query」テーブルが原因でクエリの実行が遅くなるため、ストアフロントの検索パフォーマンスが低下するAdobe Commerceの問題が修正されます。
feature: Search
role: Admin, Developer
source-git-commit: dbb185fb44b491b9e8d12290d75538d98c911eac
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# ACSD-62577：ストアフロント検索のパフォーマンスの最適化

ACSD-62577 パッチは、クエリインデックスとテーブルインデックスの両方を最適化することで、ストアフロント検索クエリのパフォーマンスが遅い問題を修正しました。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56 で使用できます。パッチ ID は ACSD-62577 です。 この問題はAdobe Commerce 2.4.8 で修正される予定だったことに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

Adobe Commerce（すべてのデプロイメント方法） 2.4.6、2.4.7-p2

**Adobe Commerce バージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

大きな `search_query` テーブルを使用すると、ストアフロントの検索が大幅に遅くなり、クエリの効率が悪く、最適化されたテーブルインデックスがないため、フロントエンドの応答時間が長くなります。

<u> 再現手順 </u>:

1. Performance Toolkit `small.xml` を使用して、Adobe Commerce Develop を設定します。
1. SQL コマンドラインにアクセスし、次のコマンドを使用して `search_query` テーブルを削除します。

   ```
   SET FOREIGN_KEY_CHECKS = 0;  
   DROP TABLE search_query;  
   SET FOREIGN_KEY_CHECKS = 1;  
   ```

1. 多数のレコード（例：400 万件のレコード）を `search_query` テーブルに入力します。
1. キャッシュのインデックス再作成とフラッシュのトリガー。

   ```
   bin/magento indexer:reindex  
   bin/magento c:c  
   bin/magento c:f  
   ```

1. データベースのデバッグログを有効にする：

   ```
   bin/magento dev:query-log:enable  
   ```

1. ストアフロント検索バーで用語を検索します（例：）。
   `http://your_magento_instance/default/catalogsearch/result/?q=test.`
1. 次の SQL のクエリ実行時間の `db.log` を確認します。

   ```
   SELECT COUNT(*) FROM (  
   SELECT DISTINCT `main_table`.`query_text`  
   FROM `search_query` AS `main_table`  
   WHERE (main_table.store_id IN (1))  
   AND (main_table.num_results > 0)  
   ORDER BY `main_table`.`popularity` DESC  
   LIMIT 100  ) AS `result` WHERE (result.query_text = 'test')  
   ```

<u> 期待される結果 </u>:

クエリの実行時間が最適化されるので、大きな `search_query` テーブルを処理する際の応答時間の増加は目立ちません。

<u> 実際の結果 </u>:

大きな `search_query` テーブルに対する処理が非効率的なので、クエリの実行時間が大幅に長くなります。

```
TIME: 10.8520 seconds  
```

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Sourceオンプレミス：[[!DNL Quality Patches Tool] > Usage](/help/tools/quality-patches-tool/usage.md) in the [!DNL Quality Patches Tool] guide.
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
