---
title: 増分IDを変更
description: サイトを結合または復元する際にSQLを使用して、注文、請求書、クレジットメモおよびその他のCommerce データベースエンティティの増分IDを変更する方法について説明します。
exl-id: 039fc34c-d9cf-42f4-af5d-16a26a3e8171
source-git-commit: 41b8d77793f1c24f08ff7e6a2d35826a62477534
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# 増分IDを変更

この記事では、`ALTER TABLE` SQL ステートメントを使用して、特定のCommerce ストア上のCommerce データベース （DB） エンティティ （注文、請求書、クレジットメモなど）の増分IDを変更する方法について説明します。

## 影響のあるバージョン

- Adobe Commerce（オンプレミス）:2.x.x
- Adobe Commerce オンクラウドインフラストラクチャ：2.x.x
- MySQL: [ サポートされているすべてのバージョン ](../../installation/prerequisites/database/mysql.md)

## 増分IDを変更する必要があるタイミング

次のような場合、新しいDB エンティティの増分IDを変更する必要が生じる可能性があります。

- ライブサイトでのハードバックアップ復元後
- 一部の注文記録は失われましたが、そのIDは既に現在の加盟店アカウントの支払いゲートウェイ（PayPalなど）で使用されています。 このような場合、支払いゲートウェイは、同じIDを持つ新しい注文の処理を停止し、「請求書IDの重複」エラーを返します

>[!INFO]
>
>また、PayPalの支払い受取設定で請求書IDごとに複数の支払いを許可することで、PayPalの支払いゲートウェイの問題を修正することもできます。 _ナレッジベース_&#x200B;の「[PayPal ゲートウェイがリクエストを拒否しました – 重複した請求書の問題](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/paypal-gateway-rejected-request-duplicate-invoice-issue.html)」を参照してください。

## 前提条件のステップ

1. 新しい増分IDを変更する必要があるストアとエンティティを検索します。
1. MySQL DBに接続します。
Adobe Commerce on cloud infrastructureの場合、最初にSSHを使用して環境に接続する必要があります。
1. 次のクエリを使用して、エンティティ シーケンス テーブルの現在の`auto_increment`値を確認します。

   ```sql
   SHOW TABLE STATUS FROM `{database_name}` WHERE `name` LIKE 'sequence_{entity_type}_{store_id}';
   ```

ID=1のストアで注文の自動増分を確認する場合、テーブル名は「sequence_order_1」になります。

`auto_increment`列の値が&#39;1234&#39;の場合、`ID=1`を含む店舗に配置された次の注文のIDは&#39;#100001234&#39;になります。

## 増分IDを変更するためのエンティティの更新

次のクエリを使用してエンティティを更新します。

```sql
ALTER TABLE sequence_{entity_type}_{store_id} AUTO_INCREMENT = {new_increment_value};
```

>[!INFO]
>
>重要：新しい増分値は、現在の値よりも大きくなければなりません。

次のクエリを実行した後：

```sql
ALTER TABLE sequence_order_1 AUTO_INCREMENT = 2000;
```

`ID=1`の店舗で次に注文した場合は、IDが「#100002000」になります。

## クラウドの本番環境に関するその他の推奨ステップ

Adobe Commerce on cloud infrastructureの実稼働環境で`ALTER TABLE` クエリを実行する前に、次の手順を実行することを強くお勧めします。

- ステージング環境で増分IDを変更する手順全体をテストします
- [DB バックアップを作成](https://support.magento.com/hc/en-us/articles/360003254334)して、障害が発生した場合に実稼動DBを復元します

