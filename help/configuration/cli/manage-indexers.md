---
title: インデクサーの管理
description: コマースインデクサーの表示および管理方法の例を参照してください。
source-git-commit: a7ead687c681914d90e9ed2680c8f7494eba74d4
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# インデクサーの管理

{{file-system-owner}}

すべてのインデクサーのリストを表示するには、次の手順に従います。

```bash
bin/magento indexer:info
```

リストは次のように表示されます。

```terminal
design_config_grid                       Design Config Grid
customer_grid                            Customer Grid
catalog_category_product                 Category Products
catalog_product_category                 Product Categories
catalogrule_rule                         Catalog Rule Product
catalog_product_attribute                Product EAV
inventory                                Inventory
catalogrule_product                      Catalog Product Rule
cataloginventory_stock                   Stock
targetrule_product_rule                  Product/Target Rule
targetrule_rule_product                  Target Rule/Product
catalog_product_price                    Product Price
catalogsearch_fulltext                   Catalog Search
salesrule_rule                           Sales Rule
```

## インデクサーの状態の表示

すべてのインデクサーまたは特定のインデクサーのステータスを表示するには、このコマンドを使用します。 例えば、インデクサーのインデックスを再作成する必要があるかどうかを調べます。

コマンドオプション：

```bash
bin/magento indexer:status [indexer]
```

ここで、 `[indexer]` は、スペースで区切られたインデクサーのリストです。 省略 `[indexer]` をクリックして、すべてのインデクサーのステータスを表示します。

サンプル結果：

```terminal
+----------------------+------------------+-----------+---------------------+---------------------+
| Title                | Status           | Update On | Schedule Status     | Schedule Updated    |
+----------------------+------------------+-----------+---------------------+---------------------+
| Catalog Product Rule | Reindex required | Save      |                     |                     |
| Catalog Rule Product | Reindex required | Save      |                     |                     |
| Catalog Search       | Ready            | Save      |                     |                     |
| Category Products    | Reindex required | Schedule  | idle (0 in backlog) | 2021-06-28 09:45:53 |
| Customer Grid        | Ready            | Schedule  | idle (0 in backlog) | 2021-06-28 09:45:52 |
| Design Config Grid   | Ready            | Schedule  | idle (0 in backlog) | 2018-06-28 09:45:52 |
| Inventory            | Ready            | Save      |                     |                     |
| Product Categories   | Reindex required | Schedule  | idle (0 in backlog) | 2021-06-28 09:45:53 |
| Product EAV          | Reindex required | Save      |                     |                     |
| Product Price        | Reindex required | Save      |                     |                     |
| Stock                | Reindex required | Save      |                     |                     |
+----------------------+------------------+-----------+---------------------+---------------------+
```

## 再インデックス

このコマンドを使用して、すべてのまたは選択したインデクサーのインデックスを 1 回だけ再作成します。

>[!INFO]
>
>このコマンドは、1 回だけインデックスを再作成します。 インデクサーを最新の状態に保つには、 [cron ジョブ](../cli/configure-cron-jobs.md).

コマンドオプション：

```bash
bin/magento indexer:reindex [indexer]
```

ここで、 `[indexer]` は、スペースで区切られたインデクサーのリストです。 省略 `[indexer]` すべてのインデクサを再インデックス化します。

サンプル結果：

```terminal
Design Config Grid index has been rebuilt successfully in <time>
Customer Grid index has been rebuilt successfully in <time>
Category Products index has been rebuilt successfully in <time>
Product Categories index has been rebuilt successfully in <time>
Catalog Rule Product index has been rebuilt successfully in <time>
Product EAV index has been rebuilt successfully in <time>
Inventory index has been rebuilt successfully in <time>
Catalog Product Rule index has been rebuilt successfully in <time>
Stock index has been rebuilt successfully in <time>
Product Price index has been rebuilt successfully in <time>
Catalog Search index has been rebuilt successfully in <time>
```

>[!INFO]
>
>すべてのインデクサーのインデックスを再作成すると、製品、顧客、カテゴリ、プロモーションルールが多数あるストアに対して長い時間を要する可能性があります。

### 並列モードでのインデックス再作成

インデクサーは、並列モードでのインデックス再作成をサポートするために、スコープ指定およびマルチスレッド化されます。 インデクサーのディメンションで並列化し、複数のスレッドで実行するので、処理時間が短縮されます。

この文脈では、 `dimension` はインデックス再作成の範囲です。例えば、 `website` または特定の `customer_group`.

インデックスの並列化は、スコープ化されたインデクサーにのみ影響します。つまり、Commerce は、すべてのデータを 1 つのテーブルに保持する代わりに、インデクサーをスコープとして使用して、データを複数のテーブルに分割します。

次のインデックスを並列モードで実行できます。

- `Catalog Search Fulltext` は、ストアビューで並行できます。
- `Category Product` は、ストアビューで並行できます。
- `Catalog Price` は、Web サイトや顧客グループに比べて優れています。
- `Catalog Permissions` は、顧客グループに比べて優れています。

>[!INFO]
>
>「カタログ検索のフルテキスト」と「カテゴリ製品」の並列化は、デフォルトで有効になっています。

並列化を使用するには、製品価格インデクサで使用可能な次元モードの 1 つを設定します。

- `none` （デフォルト）
- `website`
- `customer_group`
- `website_and_customer_group`

例えば、Web サイトごとのモードを設定するには、次のようにします。

```bash
bin/magento indexer:set-dimensions-mode catalog_product_price website
```

カタログ権限に並列化を使用するには、カタログ権限インデクサーで使用可能な次元モードの 1 つを設定します。

- `none` （デフォルト）
- `customer_group`

または、現在のモードを確認するには、次の手順を実行します。

```bash
bin/magento indexer:show-dimensions-mode
```

並列モードで再インデックスを行うには、環境変数を使用して reindex コマンドを実行します。 `MAGE_INDEXER_THREADS_COUNT`または、 `env.php` ファイル。 この変数は、再インデックス処理のスレッド数を設定します。

たとえば、次のコマンドは `Catalog Search Fulltext` 3 つのスレッドにわたるインデクサー：

```bash
MAGE_INDEXER_THREADS_COUNT=3 php -f bin/magento indexer:reindex catalogsearch_fulltext
```

## インデクサーをリセット

すべてのインデクサーまたは特定のインデクサーの状態を無効にするには、このコマンドを使用します。

コマンドオプション：

```bash
bin/magento indexer:reset [indexer]
```

ここで、 ```[indexer]``` は、スペースで区切られたインデクサーのリストです。 省略 `[indexer]` をクリックして、すべてのインデクサーを無効にします。

サンプル結果：

```terminal
Design Config Grid indexer has been invalidated.
Customer Grid indexer has been invalidated.
Category Products indexer has been invalidated.
Product Categories indexer has been invalidated.
Catalog Rule Product indexer has been invalidated.
Product EAV indexer has been invalidated.
Inventory indexer has been invalidated.
Catalog Product Rule indexer has been invalidated.
Stock indexer has been invalidated.
Product Price indexer has been invalidated.
Catalog Search indexer has been invalidated.
```

## インデクサーの設定

このコマンドを使用して、次のインデクサーオプションを設定します。

- **保存時に更新 (`realtime`)**:インデックス付きのデータは、管理で変更が加えられると更新されます。 （例えば、カテゴリ製品インデックスは、製品が管理者のカテゴリに追加された後に再インデックスされます）。 これがデフォルトです。
- **スケジュールに従って更新 (`schedule`)**:データは、cron ジョブで設定されたスケジュールに従ってインデックス付けされます。

[インデックス作成の詳細を説明します](https://developer.adobe.com/commerce/php/development/components/indexing/).

### 現在の設定を表示

現在のインデクサー構成を表示するには、次の手順に従います。

```bash
bin/magento indexer:show-mode [indexer]
```

ここで、 `[indexer]` は、スペースで区切られたインデクサーのリストです。 省略 `[indexer]` すべてのインデクサのモードを表示します。 例えば、すべてのインデクサーのモードを表示するには、次のようにします。

サンプル結果：

```terminal
Design Config Grid:                                Update on Save
Customer Grid:                                     Update on Save
Category Products:                                 Update on Save
Product Categories:                                Update on Save
Catalog Rule Product:                              Update on Save
Product EAV:                                       Update on Save
Inventory:                                         Update on Save
Catalog Product Rule:                              Update on Save
Stock:                                             Update on Save
Product Price:                                     Update on Save
Catalog Search:                                    Update on Save
```

### インデクサーの設定

>[!INFO]
>
>インデクサーモードを切り替える前に、Web サイトを [維持](../../installation/tutorials/maintenance-mode.md) モードと [cron ジョブを無効にする](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html#disable-cron-jobs). これにより、データベースのロックに影響を受けなくなります。

インデクサー設定を指定するには：

```bash
bin/magento indexer:set-mode {realtime|schedule} [indexer]
```

ここで、

- `realtime` — 保存時に更新する選択したインデクサを設定します。
- `schedule`- Cron スケジュールに従って、指定したインデクサを保存するように設定します。
- `indexer` — インデクサのスペース区切りリストです。 省略 `indexer` すべてのインデクサーを同じ方法で設定する場合。

例えば、カテゴリの製品と製品カテゴリのインデクサーのみを変更してスケジュールに従って更新するには、次のように入力します。

```bash
bin/magento indexer:set-mode schedule catalog_category_product catalog_product_category
```

サンプル結果：

```terminal
Index mode for Indexer Category Products was changed from 'Update on Save' to 'Update by Schedule'
Index mode for Indexer Product Categories was changed from 'Update on Save' to 'Update by Schedule'
```

インデクサーモードが `schedule` インデクサーモードが `realtime`. インデクサーがに設定されている間にトリガーがデータベースに存在しない場合 `schedule`、インデクサーをに変更します。 `realtime` その後、元に戻します。 `schedule`. これにより、トリガーがリセットされます。
