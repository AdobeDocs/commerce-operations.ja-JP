---
title: インデクサーの管理
description: コマンドラインツールを使用して、Adobe Commerce インデクサーを表示および管理する方法について説明します。 インデクサーコマンド、ステータスチェック、およびインデックス再作成のテクニックを確認します。
exl-id: d2cd1399-231e-4c42-aa0c-c2ed5d7557a0
source-git-commit: 2c221ccf793a0b469fc6984b443699c30a6064ce
workflow-type: tm+mt
source-wordcount: '1025'
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
> ライブサーチ、カタログサービス、商品レコメンデーションを使用しているAdobe Commerceのマーチャントには、[SaaS ベースの価格インデックス &#x200B;](https://experienceleague.adobe.com/en/docs/commerce/price-indexer/price-indexing)を使用するオプションがあります。

## インデクサーステータスの表示

すべてのインデクサーまたは特定のインデクサーのステータスを表示するには、このコマンドを使用します。 例えば、インデクサーのインデックスを再作成する必要があるかどうかを確認します。

コマンドオプション：

```bash
bin/magento indexer:status [indexer]
```

ここで、`[indexer]`はスペース区切りのインデクサーのリストです。 すべてのインデクサーのステータスを表示するには、`[indexer]`を省略します。

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

このコマンドを使用すると、すべてのインデクサーまたは選択したインデクサーを1回だけ再インデックスできます。

>[!INFO]
>
>このコマンドは、1回だけインデックスを再作成します。 インデックスを最新の状態に保つには、[cron ジョブ &#x200B;](../cli/configure-cron-jobs.md)を設定する必要があります。

コマンドオプション：

```bash
bin/magento indexer:reindex [indexer]
```

ここで、`[indexer]`はスペース区切りのインデクサーのリストです。 すべてのインデクサーのインデックスを再作成するには、`[indexer]`を省略します。

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
>すべてのインデックスを再作成すると、多数の商品、顧客、カテゴリ、およびプロモーションルールを持つストアに時間がかかる場合があります。

### パラレルモードでのインデックス再作成

{{php-process-control}}

インデクサーはスコープ付きでマルチスレッド化され、パラレルモードでのインデックス再作成をサポートします。 インデクサーのディメンションによって並列化され、複数のスレッドにわたって実行され、処理時間が短縮されます。

このコンテキストでは、`dimension`はインデックス再作成の範囲です。例えば、`website`や特定の`customer_group`などです。

インデックスの並列化は、スコープ付きインデクサーにのみ影響します。つまり、Commerceは、すべてのデータを1つのテーブルに保持するのではなく、インデクサーをスコープとして使用してデータを複数のテーブルに分割します。

パラレルモードでは、次のインデックスを実行できます。

- `Catalog Search Fulltext`は、ストアビューで並行させることができます。
- `Category Product`は、ストアビューで並行させることができます。
- `Catalog Price`は、web サイトと顧客グループで並行させることができます。
- `Catalog Permissions`は、顧客グループで並行させることができます。

>[!INFO]
>
>カタログ検索フルテキストとカテゴリ製品の並列化は、デフォルトで有効になっています。

並列化を使用するには、製品価格インデクサーで使用可能な次元モードの1つを設定します。

- `none` （既定値）
- `website`
- `customer_group`
- `website_and_customer_group`

例えば、web サイトごとにモードを設定するには、次の手順を実行します。

```bash
bin/magento indexer:set-dimensions-mode catalog_product_price website
```

カタログ権限に並列化を使用するには、カタログ権限インデクサーで使用可能なディメンション モードのいずれかを設定します。

- `none` （既定値）
- `customer_group`

または、現在のモードを確認するには：

```bash
bin/magento indexer:show-dimensions-mode
```

並列モードで再インデックスを作成するには、環境変数`MAGE_INDEXER_THREADS_COUNT`を使用して再インデックス コマンドを実行するか、環境変数を`env.php` ファイルに追加します。 この変数は、再インデックス処理のスレッド数を設定します。

例えば、次のコマンドは、3つのスレッドにわたって`Catalog Search Fulltext` インデクサーを実行します。

```bash
MAGE_INDEXER_THREADS_COUNT=3 php -f bin/magento indexer:reindex catalogsearch_fulltext
```

## インデクサーをリセット

すべてのインデクサーまたは特定のインデクサーのステータスを無効にするには、このコマンドを使用します。

コマンドオプション：

```bash
bin/magento indexer:reset [indexer]
```

ここで、`[indexer]`はスペース区切りのインデクサーのリストです。 すべてのインデクサーを無効にするには、`[indexer]`を省略します。

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

- **保存時の更新（`realtime`）**：管理者で変更が行われると、インデックス付きデータが更新されます。 （例えば、カテゴリ製品インデックスは、管理者のカテゴリに製品が追加された後に再インデックスされます）。
- **スケジュール別に更新（`schedule`）**: データは、cron ジョブで設定されたスケジュールに従ってインデックスが作成されます。

[&#x200B; インデックス作成について詳しく見る](https://developer.adobe.com/commerce/php/development/components/indexing/)。

### 現在の設定を表示

現在のインデクサー設定を表示するには：

```bash
bin/magento indexer:show-mode [indexer]
```

ここで、`[indexer]`はスペース区切りのインデクサーのリストです。 すべてのインデクサーのモードを表示するには、`[indexer]`を省略します。 例えば、すべてのインデクサーのモードを表示するには：

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
>2.4.8で[!DNL Customer Grid] インデクサーの動作が変更されました。
>
>- **2.4.8**&#x200B;以前：[!DNL Customer Grid] インデクサーは[!UICONTROL Update on Save] オプションを使用してのみインデックスを再作成でき、[!UICONTROL Update by Schedule] オプションはサポートしていません。
>
>   次のコマンドを使用して、保存時にこのインデクサーを更新するように設定します。
>
>   ```bash
>   bin/magento indexer:set-mode realtime customer_grid
>   ```
>
>- **2.4.8以降**: [!DNL Customer Grid] インデクサーは[!UICONTROL Update on Save]と[!UICONTROL Update by Schedule] モードの両方をサポートし、デフォルトは[!UICONTROL Update by Schedule]です。
>
>_実装プレイブック_&#x200B;の「[&#x200B; インデクサー設定のベストプラクティス &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/maintenance/indexer-configuration)」を参照してください。

>[!INFO]
>
>インデクサーモードを切り替える前に、web サイトを[&#x200B; メンテナンス &#x200B;](../../installation/tutorials/maintenance-mode.md) モードに設定し、[cron ジョブを無効にします](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/app/properties/crons-property)。 これにより、データベースのロックが発生しないようにします。

インデクサー設定を指定するには：

```bash
bin/magento indexer:set-mode {realtime|schedule} [indexer]
```

どこで：

- `realtime` – 選択したインデックスを保存時に更新するように設定します。
- `schedule` - cron スケジュールに従って保存する指定されたインデクサーを設定します。
- `indexer` - スペース区切りのインデクサーのリストです。 すべてのインデクサーを同じように設定するには、`indexer`を省略します。

例えば、カテゴリ製品と製品カテゴリのインデクサーのみをスケジュールに従って更新するように変更するには、次のように入力します。

```bash
bin/magento indexer:set-mode schedule catalog_category_product catalog_product_category
```

結果の例：

```text
Index mode for Indexer Category Products was changed from 'Update on Save' to 'Update by Schedule'
Index mode for Indexer Product Categories was changed from 'Update on Save' to 'Update by Schedule'
```

インデクサーモードが`schedule`に設定されている場合はインデクサー関連のデータベーストリガーが追加され、インデクサーモードが`realtime`に設定されている場合は削除されます。 インデックスが`schedule`に設定されている間にトリガーがデータベースに見つからない場合は、インデックスを`realtime`に変更してから、`schedule`に戻します。 これにより、トリガーがリセットされます。

### インデクサーステータスの設定

`bin/magento indexer:set-status` コマンドはAdobe Commerce 2.4.7で導入されました。 管理者は、1つ以上のインデクサーの操作ステータスを変更し、データのインポート、更新、メンテナンスなどの広範な操作中にシステムパフォーマンスを最適化できます。

コマンドの構文：

```bash
bin/magento indexer:set-status {invalid|suspended|valid} [indexer]
```

どこで：

- `invalid` - インデクサーを古いインデクサーとしてマークし、次のcron実行でインデックス再作成を求めるメッセージを表示します（停止しない限り）。
- `suspended` - インデクサーの自動クロントリガー更新を一時的に停止します。 このステータスは、リアルタイムモードとスケジュールモードの両方に適用され、集中的な操作中に自動更新が一時停止されるようにします。
- `valid` - インデックス データが最新であることを示します。インデックスを再作成する必要はありません。
- `indexer` - スペース区切りのインデクサーのリストです。 すべてのインデクサーを同じように設定するには、`indexer`を省略します。

例えば、特定のインデックスを一時停止するには、次のように入力します。

```bash
bin/magento indexer:set-status suspended catalog_category_product catalog_product_category
```

結果の例：

```text
Index status for Indexer 'Category Products' was changed from 'valid' to 'suspended'.
Index status for Indexer 'Product Categories' was changed from 'valid' to 'suspended'.
```

#### 休止インデクサーステータスの管理

インデクサーが`suspended` ステータスに設定されている場合、主にインデックス再作成とマテリアライズド ビューの自動更新に影響します。 概要を説明します。

**インデックス再作成がスキップされました**: システムは、`suspended`個のインデクサーと同じ`shared_index`を共有する任意のインデクサーの自動インデックス再作成をスキップします。 このアプローチは、中断されたプロセスに関連するデータのインデックス再作成を回避することで、システムリソースを節約します。

**マテリアライズド ビューの更新がスキップされました**：インデックス再作成と同様に、システムは、`suspended`個のインデクサーまたはその共有インデックスに関連するマテリアライズド ビューの更新も一時停止します。 この一時停止により、サスペンション期間中のシステム負荷がさらに軽減されます。

>[!INFO]
>
>`indexer:reindex` コマンドは、`suspended`としてマークされたインデックスを含むすべてのインデックスを再作成するので、自動更新が一時停止されたときに手動で更新する場合に便利です。

>[!IMPORTANT]
>
>インデクサーのステータスを`suspended`または`invalid`から`valid`に変更するには、注意が必要です。 このアクションは、インデックス付けされていないデータが蓄積されている場合に、パフォーマンスが低下する可能性があります。
>
>システムのパフォーマンスとデータの整合性を維持するために、ステータスを`valid`に手動で更新する前に、すべてのデータが正確にインデックス作成されていることを確認することが重要です。
