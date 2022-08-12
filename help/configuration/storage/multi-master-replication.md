---
title: データベースレプリケーション
description: データベースレプリケーションを設定するメリットを参照してください。
source-git-commit: 52f92ef79586d618fd4ac51c00eaa1446a2dc98f
workflow-type: tm+mt
source-wordcount: '178'
ht-degree: 0%

---


# データベースレプリケーション

{{ee-only}}

{{deprecate-split-db}}

データベース・レプリケーションを設定すると、次のメリットが得られます。

- データのバックアップを提供
- マスター・データベースに影響を与えずにデータ分析を可能にします。
- 拡張性

MySQL データベースは非同期でレプリケートされます。つまり、マスターから更新を受け取るためにスレーブを恒久的に接続する必要はありません。

## データベースレプリケーションの設定

データベースレプリケーションに関する詳細な説明は、このガイドの範囲外です。 設定するには、次のようなリソースを参照してください。

- [MySQL ドキュメント](https://dev.mysql.com/doc/refman/5.6/en/replication.html)
- [MySQL(digitalocean) でマスタースレーブレプリケーションを設定する方法](https://www.digitalocean.com/community/tutorials/how-to-set-up-replication-in-mysql)

Commerce には、スレーブデータベース用の MySQL 設定例が用意されています。 簡単な設定が、 `ResourceConnections` クラス `README.md`.

次の機能は、より高度なもので、ユーザー情報に対してのみ提供されています。

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

マスタースレーブレプリケーションのパフォーマンスを向上させるには、スレーブインスタンス上の一部のテーブルをフィルタリングします。 名前のパターンを持つすべての一時テーブルをフィルタリングすることをお勧めします `search\_tmp\_%` に使用される [カタログ](https://glossary.magento.com/catalog) 検索。

これをおこなうには、 `my.cnf` スレーブインスタンス上のファイル：

```conf
replicate-wild-ignore-table=%.search\_tmp\_%
```