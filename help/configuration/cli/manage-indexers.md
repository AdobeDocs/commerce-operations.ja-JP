---
title: インデクサーの管理
description: Commerce インデクサーの表示および管理方法の例を参照してください。
exl-id: d2cd1399-231e-4c42-aa0c-c2ed5d7557a0
source-git-commit: ceefb9371dd0a85046cc5bfc0ddc72144d649608
workflow-type: tm+mt
source-wordcount: '964'
ht-degree: 0%

---

# インデクサーの管理

{{file-system-owner}}

すべてのインデクサーのリストを表示するには：

```bash
bin/magento indexer:info
```

リストは次のように表示されます。

```text
cataloginventory_stock                   Stock
design_config_grid                       Design Config Grid
customer_grid                            Customer Grid
catalog_category_product                 Category Products
catalog_product_category                 Product Categories
catalogrule_rule                         Catalog Rule Product
catalog_product_attribute                Product EAV
inventory                                Inventory
catalog_product_price                    Product Price
catalogrule_product                      Catalog Product Rule
targetrule_product_rule                  Product/Target Rule
targetrule_rule_product                  Target Rule/Product
catalogsearch_fulltext                   Catalog Search
salesrule_rule                           Sales Rule
sales_order_data_exporter                Sales Order Feed
sales_order_status_data_exporter         Sales Order Statuses Feed
store_data_exporter                      Stores Feed
```

>[!NOTE]
>
> Live Search、カタログサービス、Product Recommendations を使用するAdobe Commerce マーチャントには、[SaaS ベースの価格インデックス作成 ](https://experienceleague.adobe.com/ja/docs/commerce/price-indexer/price-indexing) を使用するオプションがあります。

## インデクサーのステータスの表示

このコマンドを使用して、すべてのインデクサーまたは特定のインデクサーのステータスを表示します。 例えば、インデクサーのインデックスを再作成する必要があるかどうかを確認します。

コマンドオプション：

```bash
bin/magento indexer:status [indexer]
```

ここで、`[indexer]` はインデクサーのスペース区切りのリストです。 すべてのインデクサーの状態を表示するには、`[indexer]` を省略します。

結果の例：

```text
+----------------------------------+---------------------------+--------+-----------+---------------------+---------------------+
| ID                               | Title                     | Status | Update On | Schedule Status     | Schedule Updated    |
+----------------------------------+---------------------------+--------+-----------+---------------------+---------------------+
| catalogrule_product              | Catalog Product Rule      | Ready  | Schedule  | idle (0 in backlog) | 2025-07-11 08:00:52 |
| catalogrule_rule                 | Catalog Rule Product      | Ready  | Schedule  | idle (0 in backlog) | 2025-07-11 08:00:52 |
| catalogsearch_fulltext           | Catalog Search            | Ready  | Schedule  | idle (0 in backlog) | 2025-07-11 08:01:02 |
| catalog_category_product         | Category Products         | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:11:33 |
| customer_grid                    | Customer Grid             | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:11:31 |
| design_config_grid               | Design Config Grid        | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:11:31 |
| inventory                        | Inventory                 | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:11:36 |
| catalog_product_category         | Product Categories        | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:11:33 |
| catalog_product_attribute        | Product EAV               | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:11:36 |
| catalog_product_price            | Product Price             | Ready  | Schedule  | idle (0 in backlog) | 2025-07-11 08:00:54 |
| targetrule_product_rule          | Product/Target Rule       | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:11:39 |
| sales_order_data_exporter        | Sales Order Feed          | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:12:10 |
| sales_order_status_data_exporter | Sales Order Statuses Feed | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:12:10 |
| salesrule_rule                   | Sales Rule                | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:12:10 |
| cataloginventory_stock           | Stock                     | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:11:31 |
| store_data_exporter              | Stores Feed               | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:12:11 |
| targetrule_rule_product          | Target Rule/Product       | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:11:39 |
+----------------------------------+---------------------------+--------+-----------+---------------------+---------------------+
```

## 再インデックス

すべてのインデクサーまたは選択したインデクサーの再インデックスを 1 回だけ実行するには、このコマンドを使用します。

>[!INFO]
>
>このコマンドは 1 回だけ再インデックスを実行します。 インデクサーを最新の状態に保つには、[cron ジョブ ](../cli/configure-cron-jobs.md) を設定する必要があります。

コマンドオプション：

```bash
bin/magento indexer:reindex [indexer]
```

ここで、`[indexer]` はインデクサーのスペース区切りのリストです。 すべてのインデクサーを再インデックス化する場合は、`[indexer]` を省略します。

結果の例：

```text
Stock index has been rebuilt successfully in <time>
Design Config Grid index has been rebuilt successfully in <time>
Customer Grid index has been rebuilt successfully in <time>
Category Products index has been rebuilt successfully in <time>
Product Categories index has been rebuilt successfully in <time>
Catalog Rule Product index has been rebuilt successfully in <time>
Product EAV index has been rebuilt successfully in <time>
Inventory index has been rebuilt successfully in <time>
Product Price index has been rebuilt successfully in <time>
Catalog Product Rule index has been rebuilt successfully in <time>
Product/Target Rule index has been rebuilt successfully in <time>
Target Rule/Product index has been rebuilt successfully in <time>
Catalog Search index has been rebuilt successfully in <time>
Sales Rule index has been rebuilt successfully in <time>
Sales Order Feed index has been rebuilt successfully in <time>
Sales Order Statuses Feed index has been rebuilt successfully in <time>
Stores Feed index has been rebuilt successfully in <time>
```

>[!INFO]
>
>すべてのインデクサーのインデックス再作成は、製品、顧客、カテゴリおよびプロモーションルールが多数あるストアでは、時間がかかる場合があります。

### 並列モードでのインデックス再作成

{{php-process-control}}

インデクサーは、並列モードでのインデックス再作成をサポートするために、スコープ指定されマルチスレッド化されます。 インデクサーのディメンションで並列化され、複数のスレッドにわたって実行されるので、処理時間が短縮されます。

このコンテキストでは、インデックス再作成の範囲は `dimension` のとおりです（例：`website` または特定の `customer_group` のみ）。

インデックスの並列化は、スコープ指定されたインデクサーにのみ影響します。つまり、Commerceでは、すべてのデータを 1 つのテーブルに保持するのではなく、インデクサーをスコープとして使用して、データを複数のテーブルに分割します。

次のインデックスを並列モードで実行できます。

- `Catalog Search Fulltext` は、ストアのビューで並べることができます。
- `Category Product` は、ストアのビューで並べることができます。
- `Catalog Price` れは、web サイトと顧客グループで並行できます。
- `Catalog Permissions` は、顧客グループごとに並行して実行できます。

>[!INFO]
>
>カタログ検索全文とカテゴリ製品の並列化は、デフォルトで有効になっています。

並列化を使用するには、製品価格インデクサーで使用可能なディメンションモードの 1 つを設定します。

- `none` （デフォルト）
- `website`
- `customer_group`
- `website_and_customer_group`

例えば、web サイトごとにモードを設定するには、次のようにします。

```bash
bin/magento indexer:set-dimensions-mode catalog_product_price website
```

カタログ権限の並列化を使用するには、カタログ権限インデクサーで使用可能ないずれかのディメンションモードを設定します。

- `none` （デフォルト）
- `customer_group`

または、現在のモードを確認します。

```bash
bin/magento indexer:show-dimensions-mode
```

並列モードでインデックスを再作成するには、環境変数 `MAGE_INDEXER_THREADS_COUNT` を使用して reindex コマンドを実行するか、`env.php` ファイルに環境変数を追加します。 この変数は、再インデックス処理のスレッド数を設定します。

例えば、次のコマンドは、3 つのスレッドに対して `Catalog Search Fulltext` インデクサーを実行します。

```bash
MAGE_INDEXER_THREADS_COUNT=3 php -f bin/magento indexer:reindex catalogsearch_fulltext
```

## インデクサーをリセット

すべてのインデクサーまたは特定のインデクサーのステータスを無効にするには、このコマンドを使用します。

コマンドオプション：

```bash
bin/magento indexer:reset [indexer]
```

ここで、```[indexer]``` はインデクサーのスペース区切りのリストです。 `[indexer]` を省略すると、すべてのインデクサーが無効になります。

結果の例：

```text
Stock indexer has been invalidated.
Design Config Grid indexer has been invalidated.
Customer Grid indexer has been invalidated.
Category Products indexer has been invalidated.
Product Categories indexer has been invalidated.
Catalog Rule Product indexer has been invalidated.
Product EAV indexer has been invalidated.
Inventory indexer has been invalidated.
Product Price indexer has been invalidated.
Catalog Product Rule indexer has been invalidated.
Product/Target Rule indexer has been invalidated.
Target Rule/Product indexer has been invalidated.
Catalog Search indexer has been invalidated.
Sales Rule indexer has been invalidated.
Sales Order Feed indexer has been invalidated.
Sales Order Statuses Feed indexer has been invalidated.
Stores Feed indexer has been invalidated.
```

## インデクサーの設定

このコマンドを使用して、次のインデクサーオプションを設定します。

- **保存時に更新（`realtime`）**：インデックス付きデータは、管理者で変更が加えられると更新されます。 （例えば、カテゴリ製品インデックスは、製品が管理者のカテゴリに追加された後に再インデックスされます。）
- **スケジュールで更新（`schedule`）**:cron ジョブで設定したスケジュールに従ってデータのインデックスが作成されます。

[ インデックス作成の詳細情報 ](https://developer.adobe.com/commerce/php/development/components/indexing/)。

### 現在の設定を表示

現在のインデクサー設定を表示するには：

```bash
bin/magento indexer:show-mode [indexer]
```

ここで、`[indexer]` はインデクサーのスペース区切りのリストです。 `[indexer]` を省略すると、すべてのインデクサーのモードが表示されます。 例えば、すべてのインデクサーのモードを表示するには、次のようにします。

結果の例：

```text
Stock:                                             Update by Schedule
Design Config Grid:                                Update by Schedule
Customer Grid:                                     Update by Schedule
Category Products:                                 Update by Schedule
Product Categories:                                Update by Schedule
Catalog Rule Product:                              Update by Schedule
Product EAV:                                       Update by Schedule
Inventory:                                         Update by Schedule
Product Price:                                     Update by Schedule
Catalog Product Rule:                              Update by Schedule
Product/Target Rule:                               Update by Schedule
Target Rule/Product:                               Update by Schedule
Catalog Search:                                    Update by Schedule
Sales Rule:                                        Update by Schedule
Sales Order Feed:                                  Update by Schedule
Sales Order Statuses Feed:                         Update by Schedule
Stores Feed:                                       Update by Schedule
```

### インデクサーモードの設定

>[!IMPORTANT]
>
>[!DNL Customer Grid] のインデクサーの動作は 2.4.8 で変更されました。
>
>- **2.4.8 より前**:[!DNL Customer Grid] インデクサーのインデックスは、[!UICONTROL Update on Save] オプションを使用してのみ再作成でき、[!UICONTROL Update by Schedule] オプションはサポートしていません。
>
>   次のコマンドを使用して、保存時にこのインデクサーを更新するように設定します。
>
>   ```bash
>   bin/magento indexer:set-mode realtime customer_grid
>   ```
>
>- **2.4.8 以降**:[!DNL Customer Grid] インデクサーは、[!UICONTROL Update on Save] モードと [!UICONTROL Update by Schedule] モードの両方をサポートしており、デフォルトは [!UICONTROL Update by Schedule] です。
>
>[ 実装プレイブック ](https://experienceleague.adobe.com/ja/docs/commerce-operations/implementation-playbook/best-practices/maintenance/indexer-configuration) の _インデクサー設定のベストプラクティス_ を参照してください。

>[!INFO]
>
>インデクサーモードを切り替える前に、web サイトを [ メンテナンス ](../../installation/tutorials/maintenance-mode.md) モードと [cron ジョブを無効 ](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/configure/app/properties/crons-property) に設定します。 これにより、データベースのロックが発生しないようにします。

インデクサー設定を指定するには：

```bash
bin/magento indexer:set-mode {realtime|schedule} [indexer]
```

ここで、

- `realtime` – 保存時に更新する選択したインデクサーを設定します。
- `schedule` - cron スケジュールに従って、指定されたインデクサーを保存するように設定します。
- `indexer` - インデクサーのスペース区切りのリストです。 すべてのインデクサーを同じ方法で設定する場合は、`indexer` を省略します。

たとえば、スケジュールに従って更新するカテゴリ製品と製品カテゴリのインデクサーのみを変更するには、次のように入力します。

```bash
bin/magento indexer:set-mode schedule catalog_category_product catalog_product_category
```

結果の例：

```
Index mode for Indexer Category Products was changed from 'Update on Save' to 'Update by Schedule'
Index mode for Indexer Product Categories was changed from 'Update on Save' to 'Update by Schedule'
```

インデクサー関連のデータベーストリガーは、インデクサーモードが `schedule` に設定されている場合は追加され、インデクサーモードが `realtime` に設定されている場合は削除されます。 インデクサーが `schedule` に設定されているときに、トリガーがデータベースにない場合は、インデクサーを `realtime` に変更してから、`schedule` に戻します。 これにより、トリガーがリセットされます。

### インデクサーのステータスを設定

`bin/magento indexer:set-status` コマンドは、Adobe Commerce 2.4.7 で導入されました。これにより、管理者は 1 つ以上のインデクサーの動作ステータスを変更し、データのインポート、更新、メンテナンスなどの広範な操作中にシステムのパフォーマンスを最適化できます。

コマンド構文：

```bash
bin/magento indexer:set-status {invalid|suspended|valid} [indexer]
```

ここで、

- `invalid` - インデクサーを期限切れとマークし、中断されない限り、次回 cron 実行時にインデックス再作成を促します。
- `suspended` - インデクサーの cron トリガーによる自動更新を一時的に停止します。 このステータスはリアルタイムモードとスケジュールモードの両方に適用され、集中的な操作中に自動更新を一時停止できます。
- `valid` - インデクサー・データが最新であることを示し、インデックスの再作成は不要です。
- `indexer` - インデクサーのスペース区切りのリストです。 すべてのインデクサーを同じ方法で設定する場合は、`indexer` を省略します。

例えば、特定のインデクサーを休止するには、次のように入力します。

```bash
bin/magento indexer:set-status suspended catalog_category_product catalog_product_category
```

結果の例：

```
Index status for Indexer 'Category Products' was changed from 'valid' to 'suspended'.
Index status for Indexer 'Product Categories' was changed from 'valid' to 'suspended'.
```

#### 中断されたインデクサーのステータスの管理

インデクサーが `suspended` ステータスに設定されると、主に自動インデックス再作成と実体化ビュー（Materialized View）の更新に影響します。 概要を次に示します。

**インデックス再作成がスキップされました**：システムは、`suspended` インデクサーと、同じ `shared_index` を共有するインデクサーの自動インデックス再作成をスキップします。 このアプローチでは、中断されたプロセスに関連するデータのインデックス再作成を回避することで、システムリソースを節約できます。

**マテリアライズド・ビュー更新のスキップ**：再インデックス化と同様に、`suspended` インデックスまたはその共有インデックスに関連するマテリアライズド・ビューに対する更新も一時停止されます。 この一時停止により、休止期間中のシステムの負荷がさらに軽減されます。

>[!INFO]
>
>`indexer:reindex` コマンドは、`suspended` としてマークされたインデクサーを含むすべてのインデクサーのインデックスを再作成するので、自動インデクサーが一時停止した場合の手動での更新に役立ちます。

>[!IMPORTANT]
>
>インデクサーのステータスを `valid` または `suspended` から `invalid` に変更する場合は注意が必要です。 インデックスのないデータが蓄積されている場合は、パフォーマンスが低下する可能性があります。
>
>システムのパフォーマンスとデータの整合性を維持するために、ステータスを `valid` に手動で更新する前に、すべてのデータのインデックスが正確に作成されていることを確認することが重要です。
