---
title: 増分 ID を変更
description: Commerce データベースエンティティの増分 ID を変更します。
exl-id: 039fc34c-d9cf-42f4-af5d-16a26a3e8171
source-git-commit: 2a45fe77d5a6fac089ae2c55d0ad047064dd07b0
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 0%

---

# 増分 ID を変更

この記事では、特定のコマースストアで、DB (Commerce Database) エンティティの増分 ID（注文、請求書、クレジットメモなど）を `ALTER TABLE` SQL 文。

## 影響を受けるバージョン

- Adobe Commerce（オンプレミス）:2.x.x
- Adobe Commerce on cloud infrastructure: 2.x.x
- MySQL: [サポート対象のバージョン](../../installation/prerequisites/database/mysql.md)

## 増分 ID を変更する必要がある状況

次の場合は、新しい DB エンティティの増分 ID を変更する必要が生じる場合があります。

- ライブサイトでのハードバックアップのリストア後
- 一部の注文レコードは失われましたが、その ID は現在の Merchant アカウントの支払いゲートウェイ（PayPal など）で既に使用されています。 その場合、支払ゲートウェイは同じ ID を持つ新しい注文の処理を停止し、「請求書 ID の重複」エラーを返します。

>[!INFO]
>
>また、PayPal の Payment Receiving Preferences で、請求書 ID ごとに複数の支払いを許可することで、PayPal の支払いゲートウェイの問題を修正することもできます。 詳しくは、 [PayPal ゲートウェイがリクエストを拒否しました — 請求書の重複の問題](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/paypal-gateway-rejected-request-duplicate-invoice-issue.html) （内） _ナレッジベース_.

## 前提条件の手順

1. 新しい増分 ID を変更する必要がある店舗とエンティティを検索します。
1. MySQL DB に接続します。
クラウドインフラストラクチャ上のAdobe Commerceの場合、最初は SSH を使用して環境に接続する必要があります。
1. 現在の `auto_increment` 次のクエリーを使用して、エンティティシーケンステーブルの値を指定します。

   ```sql
   SHOW TABLE STATUS FROM `{database_name}` WHERE `name` LIKE 'sequence_{entity_type}_{store_id}';
   ```

ID=1 のストアでオーダーの自動増分をチェックしている場合、テーブル名は「sequence_order_1」になります。

次の値が `auto_increment` 列は「1234」で、次の注文は `ID=1` ID「#100001234」が付与されます。

## 増分 ID を変更するためにエンティティを更新

次のクエリを使用してエンティティを更新します。

```sql
ALTER TABLE sequence_{entity_type}_{store_id} AUTO_INCREMENT = {new_increment_value};
```

>[!INFO]
>
>重要：新しい増分値は、現在の増分値より大きい値である必要があります。

次のクエリを実行した後：

```sql
ALTER TABLE sequence_order_1 AUTO_INCREMENT = 2000;
```

次の注文は `ID=1` ID「#100002000」が付与されます。

## クラウド実稼動環境でのその他の推奨手順

を実行する前に、 `ALTER TABLE` クラウドインフラストラクチャ上のAdobe Commerceの実稼動環境に対するクエリを実行する場合は、次の手順を実行することを強くお勧めします。

- ステージング環境で増分 ID を変更する手順全体をテストします。
- [DB バックアップの作成] 失敗した場合に実稼動 DB を復元するには

<!-- Link Definitions -->

[PayPal gateway rejected request - duplicate invoice issue]: https://support.magento.com/hc/en-us/articles/115002457473
[DB バックアップの作成]: https://support.magento.com/hc/en-us/articles/360003254334
[サポート対象のバージョン]
