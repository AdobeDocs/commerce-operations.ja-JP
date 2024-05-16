---
title: データベースレプリケーション
description: データベースレプリケーションを設定するメリットを確認します。
recommendations: noCatalog
exl-id: 0e41dca0-5a23-4d12-96fe-241c511ae366
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 0%

---

# データベースレプリケーション

{{ee-only}}

{{deprecate-split-db}}

データベースレプリケーションを設定すると、次の利点があります。

- データのバックアップを提供
- マスターデータベースに影響を与えずにデータ分析を有効にします
- 拡張性

MySQL データベースは非同期でレプリケートするので、スレーブがマスターから更新を受け取るために永続的に接続される必要はありません。

## データベースレプリケーションの設定

データベースレプリケーションの詳細については、このガイドの範囲外です。 設定するには、次のようなリソースを参照します。

- [MySQL ドキュメント](https://dev.mysql.com/doc/refman/5.6/en/replication.html)
- [MySQL でマスタースレーブレプリケーションを設定する方法（digitalocean）](https://www.digitalocean.com/community/tutorials/how-to-set-up-replication-in-mysql)

Commerceは、スレーブデータベース用の MySQL 設定のサンプルを提供します。 を使用した簡単な設定ができます `ResourceConnections` クラス `README.md`.

より高度な次の説明は、情報提供のみを目的としています。

```php
   return array (
      //...
      'db' =>
         array (
            'connection' =>
               array (
                  'indexer' =>
                     array (
                        'host' => 'default-master-host',
                        'dbname' => 'magento',
                        'username' => 'magento',
                        'password' => 'magento',
                        'active' => '1',
                        'persistent' => NULL,
                     ),
                  'default' =>
                     array (
                        'host' => 'default-master-host',
                        'dbname' => 'magento',
                        'username' => 'magento',
                        'password' => 'magento',
                        'active' => '1',
                     ),
                  'checkout' =>
                     array (
                        'host' => 'checkout-master-host',
                        'dbname' => 'checkout',
                        'username' => 'magento',
                        'password' => 'magento',
                        'model' => 'mysql4',
                        'engine' => 'innodb',
                        'initStatements' => 'SET NAMES utf8;',
                        'active' => '1',
                     ),
                  'sales' =>
                     array (
                        'host' => 'sales-master-host',
                        'dbname' => 'sales',
                        'username' => 'magento',
                        'password' => 'magento',
                        'model' => 'mysql4',
                        'engine' => 'innodb',
                        'initStatements' => 'SET NAMES utf8;',
                        'active' => '1',
                     ),
               ),
            'slave_connection' =>
               array (
                  'default' =>
                     array (
                        'host' => 'default-slave-host',
                        'dbname' => 'magento',
                        'username' => 'read_only',
                        'password' => 'password',
                        'active' => '1',
                     ),
                  'checkout' =>
                     array (
                        'host' => 'checkout-slave-host',
                        'dbname' => 'checkout',
                        'username' => 'read_only',
                        'password' => 'password',
                        'model' => 'mysql4',
                        'engine' => 'innodb',
                        'initStatements' => 'SET NAMES utf8;',
                        'active' => '1',
                     ),
                  'sales' =>
                     array (
                        'host' => 'sales-slave-host',
                        'dbname' => 'sales',
                        'username' => 'read_only',
                        'password' => 'password',
                        'model' => 'mysql4',
                        'engine' => 'innodb',
                        'initStatements' => 'SET NAMES utf8;',
                        'active' => '1',
                     ),
                  ),
               'table_prefix' => '',
   ),
   //.......
```

## パフォーマンスの向上

マスタースレーブレプリケーションのパフォーマンスを向上させるために、スレーブインスタンス上の一部のテーブルをフィルタリングできます。 名前パターンを使用してすべての一時テーブルをフィルタリングすることをお勧めします。 `search\_tmp\_%` これは、カタログ検索に使用されます。

これを行うには、に次の行を追加します `my.cnf` スレーブインスタンス上のファイル：

```conf
replicate-wild-ignore-table=%.search\_tmp\_%
```
