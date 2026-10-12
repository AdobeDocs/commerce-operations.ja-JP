---
title: データベースレプリケーション
description: バックアップ、分析オフロード、非同期MySQL スレーブ設定など、Adobe Commerceのデータベースレプリケーションのメリットについて説明します。
recommendations: noCatalog
exl-id: 0e41dca0-5a23-4d12-96fe-241c511ae366
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 0%
---
# データベースレプリケーション

{{ee-only}}

{{deprecate-split-db}}

データベース・レプリケーションを設定すると、次のメリットが得られます。

- データバックアップを提供
- マスターデータベースに影響を与えることなく、データ分析を有効にします
- 拡張性

MySQL データベースは非同期でレプリケートされるため、スレーブはマスターから更新を受け取るために永続的に接続する必要はありません。

## データベースレプリケーションの設定

データベース・レプリケーションの詳細については、このガイドの範囲を超えています。 設定するには、次のようなリソースを参照してください。

- [MySQL ドキュメント](https://dev.mysql.com/doc/refman/5.6/en/replication.html)
- [MySQLでマスタースレーブレプリケーションを設定する方法（digitalocean）](https://www.digitalocean.com/community/tutorials/how-to-set-up-replication-in-mysql)

Commerceには、スレーブデータベースのMySQL設定のサンプルが用意されています。 `ResourceConnections` クラス `README.md`には、簡単な設定が用意されています。

次の機能は高度なもので、情報を提供する場合にのみ使用できます。

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

マスタースレーブレプリケーションのパフォーマンスを向上させるために、スレーブインスタンス上のテーブルをフィルタリングできます。 カタログ検索に使用される名前パターン `search\_tmp\_%`を持つすべての一時テーブルをフィルタリングすることをお勧めします。

これを行うには、スレーブインスタンスの`my.cnf` ファイルに次の行を追加します。

```conf
replicate-wild-ignore-table=%.search\_tmp\_%
```
