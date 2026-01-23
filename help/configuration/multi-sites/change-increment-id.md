---
title: 増分 ID を変更
description: Commerce データベースエンティティの増分 ID を変更します。
exl-id: 039fc34c-d9cf-42f4-af5d-16a26a3e8171
source-git-commit: 6896d31a202957d7354c3dd5eb6459eda426e8d7
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# 増分 ID を変更

この記事では、`ALTER TABLE` SQL 文を使用して、特定のCommerce ストアでCommerce Database （DB）エンティティ（注文、請求書、クレジットメモなど）の増分 ID を変更する方法について説明します。

## 影響を受けるバージョン

- Adobe Commerce（オンプレミス）: 2.x.x
- クラウドインフラストラクチャー上のAdobe Commerce:2.x.x
- MySQL: [&#x200B; サポートされている任意のバージョン &#x200B;](../../installation/prerequisites/database/mysql.md)

## 増分 ID を変更する必要があるのはいつですか？

次のような場合は、新しい DB エンティティの増分 ID を変更する必要があります。

- ライブサイトでのハードバックアップの復元後
- 一部の注文記録は失われましたが、その ID は、現在のマーチャントアカウントの支払いゲートウェイ（PayPal など）で既に使用されています。 このような場合、支払いゲートウェイは、同じ ID を持つ新しい注文の処理を停止し、「請求書 ID が重複」というエラーを返します

>[!INFO]
>
>また、PayPal の支払い受け取り環境設定で請求書 ID ごとに複数の支払いを許可することで、PayPal の支払いゲートウェイの問題を修正することもできます。 [&#x200B; ナレッジベース &#x200B;](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/paypal-gateway-rejected-request-duplicate-invoice-issue.html) の「PayPal ゲートウェイの拒否リクエスト – 請求書の重複問題 _」を参照してください_。

## 前提条件の手順

1. 新しい増分 ID を変更する必要があるストアとエンティティを見つけます。
1. MySQL DB に接続します。
クラウドインフラストラクチャー上のAdobe Commerceの場合、最初に SSH を使用して環境に接続する必要があります。
1. 次のクエリを使用して、エンティティシーケンステーブルの現在の `auto_increment` 値を確認します。

   ```sql
   SHOW TABLE STATUS FROM `{database_name}` WHERE `name` LIKE 'sequence_{entity_type}_{store_id}';
   ```

ID=1 のストアで注文の自動インクリメントをチェックしている場合、テーブル名は「sequence_order_1」になります。

`auto_increment` 列の値が「1234」の場合、`ID=1` を持つ店舗での次の注文には ID 「#100001234」が割り当てられます。

## 増分 ID を変更するエンティティを更新

次のクエリを使用してエンティティを更新します。

```sql
ALTER TABLE sequence_{entity_type}_{store_id} AUTO_INCREMENT = {new_increment_value};
```

>[!INFO]
>
>重要：新しい増分値は、現在の値より大きい値にする必要があります。

次のクエリを実行した後：

```sql
ALTER TABLE sequence_order_1 AUTO_INCREMENT = 2000;
```

`ID=1` を使用して次に店舗で行われた注文には、ID 「#100002000」が割り当てられます。

## クラウド実稼動環境におけるその他の推奨手順

クラウドインフラストラクチャー上のAdobe Commerceの実稼動環境で `ALTER TABLE` クエリを実行する前に、次の手順を実行することを強くお勧めします。

- ステージング環境で増分 ID を変更する手順全体をテストします
- [DB バックアップの作成 &#x200B;](https://support.magento.com/hc/en-us/articles/360003254334)：障害発生時に実稼動 DB を復元します

