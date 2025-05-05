---
title: インデクサーの管理
description: Commerce インデクサー表示および管理方法の例を参照してください。
exl-id: d2cd1399-231e-4c42-aa0c-c2ed5d7557a0
source-git-commit: 16feb8ec7ecc88a6ef03a769d45b1a3a2fe88d97
workflow-type: tm+mt
source-wordcount: '947'
ht-degree: 0%

---

# インデクサーの管理

{{file-system-owner}}

すべてのインデクサーのリスト表示には:

```bash
bin/magento indexer:info
```

リストは次のように表示されます。

```
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

>[!NOTE]
> ライブSearch、カタログサービス、または製品Recommendationsを使用しているAdobe Systemsコマースマーチャントには、 [SaaSベースの価格インデックス](https://experienceleague.adobe.com/docs/commerce/price-indexer/index.html)を使用するオプションがあります。

## インデクサーのステータスの表示

このコマンドを使用して、すべてのインデクサーまたは特定のインデクサーのステータスを表示します。 例えば、インデクサーのインデックスを再作成する必要があるかどうかを確認します。

コマンドオプション：

```bash
bin/magento indexer:status [indexer]
```

ここで、`[indexer]` はインデクサーのスペース区切りのリストです。 すべてのインデクサーの状態を表示するには、`[indexer]` を省略します。

結果の例：

```
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

```
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

## リセット インデクサー

このコマンドは、すべてのインデクサーまたは特定のインデクサーの状態を無効にするために使用します。

コマンドオプション:

```bash
bin/magento indexer:reset [indexer]
```

ここで、 ```[indexer]``` はスペースで区切られたインデクサーのリストです。 `[indexer]`を省略すると、すべてのインデクサーが無効になります。

サンプル結果:

```
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

## インデクサーの構成

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

```
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

### インデクサーモードの設定

>[!IMPORTANT]
>
>[!DNL Customer Grid]には、`schedule`ではなく `realtime` を使用するように設定してください。[!DNL Customer Grid]は、[!UICONTROL Update on Save]オプションを使用した場合のみインデックスを再作成できます。このインデックスは `Update by Schedule` オプションをサポートしていません。 次のコマンドラインを使用して、保存時にこのインデクサーが更新されるように設定します。 `php bin/magento indexer:set-mode realtime customer_grid`
>
>_実装実践ブック_&#x200B;の[インデクサー構成のベスト プラクティス](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/indexer-configuration.html?lang=ja)を参照してください。

>[!INFO]
>
>インデクサーモードを切り替える前に、Web サイトを [メンテナンス](../../installation/tutorials/maintenance-mode.md) モードに設定し、cron ジョブを [無効にする](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html?lang=ja#disable-cron-jobs)。 これにより、データベースがロックされるのを防ぐことができます。

インデクサー構成を指定するには:

```bash
bin/magento indexer:set-mode {realtime|schedule} [indexer]
```

どこ：

- `realtime`- 選択したインデクサーが保存時に更新されるように設定します。
- `schedule`- 指定したインデクサーが cron スケジュールに従って保存されるように設定します。
- `indexer`- インデクサーのスペース区切りのリストです。 すべてのインデクサーを同じ方法で構成するには、 `indexer` を省略します。

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

**インデックス再作成がスキップされました**：同じインデックスを共有する `suspended` インデクサーとインデクサーに対しては、自動 `shared_index` ンデックス再作成がバイパスされます。 これにより、中断されたプロセスに関連するデータのインデックスを再作成しなくても、システムリソースを確実に節約できます。

**マテリアライズド・ビュー更新のスキップ**：再インデックス化と同様に、`suspended` インデックスまたはその共有インデックスに関連するマテリアライズド・ビューの更新も一時停止されます。 このアクションにより、休止期間中のシステム負荷がさらに軽減されます。

>[!INFO]
>
>`indexer:reindex` コマンドは、`suspended` としてマークされたインデクサーを含むすべてのインデクサーのインデックスを再作成するので、自動インデクサーが一時停止した場合の手動での更新に役立ちます。

>[!IMPORTANT]
>
>インデクサーのステータスを `suspended` または `invalid` から `valid` に変更する場合は注意が必要です。 インデックスのないデータが蓄積されている場合は、パフォーマンスが低下する可能性があります。
>
>システムのパフォーマンスとデータの整合性を維持するために、ステータスを `valid` に手動で更新する前に、すべてのデータのインデックスが正確に作成されていることを確認することが重要です。
