---
title: データベース・プロファイラの構成
description: データベース・プロファイラの出力を構成する方法の例を参照してください。
badge: label="Contributed by Atish Goswami" type="Informative" url="https://github.com/atishgoswami" tooltip="Atish Goswami"
source-git-commit: bcb995ea417423b0cbc59c035ba5fdedbce3310e
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 0%

---


# データベース・プロファイラの構成

コマースデータベースプロファイラは、各クエリの時間や適用されたパラメータを含め、ページに実装されたすべてのクエリを表示します。

## 手順 1:デプロイメント設定を変更する

変更 `<magento_root>/app/etc/env.php` 次の参照を [データベース・プロファイラ・クラス](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/DB/Profiler.php):

```php?start_inline=1
        'profiler' => [
            'class' => '\Magento\Framework\DB\Profiler',
            'enabled' => true,
        ],
```

次に例を示します。

```php?start_inline=1
 'db' =>
  array (
    'table_prefix' => '',
    'connection' =>
    array (
      'default' =>
      array (
        'host' => 'localhost',
        'dbname' => 'magento',
        'username' => 'magento',
        'password' => 'magento',
        'model' => 'mysql4',
        'engine' => 'innodb',
        'initStatements' => 'SET NAMES utf8;',
        'active' => '1',
        'profiler' => [
            'class' => '\Magento\Framework\DB\Profiler',
            'enabled' => true,
        ],
      ),
    ),
  ),
```

## 手順 2:出力の設定

コマースアプリケーションのブートストラップファイルで出力を設定する。これは、 `<magento_root>/pub/index.php` または、Web サーバーの仮想ホスト設定に配置できます。

次の例では、3 列のテーブルの結果を表示します。

- 合計時間（ページに対するすべてのクエリを実行する合計時間を表示します）
- SQL ( すべての SQL クエリを表示します。行ヘッダーには、クエリの数が表示されます )
- クエリーパラメーター（各 SQL クエリーのパラメーターを表示）

出力を設定するには、 `$bootstrap->run($app);` ブートストラップファイルの行：

```php?start_inline=1
/** @var \Magento\Framework\App\ResourceConnection $res */
$res = \Magento\Framework\App\ObjectManager::getInstance()->get('Magento\Framework\App\ResourceConnection');
/** @var Magento\Framework\DB\Profiler $profiler */
$profiler = $res->getConnection('read')->getProfiler();
echo "<table cellpadding='0' cellspacing='0' border='1'>";
echo "<tr>";
echo "<th>Time <br/>[Total Time: ".$profiler->getTotalElapsedSecs()." secs]</th>";
echo "<th>SQL [Total: ".$profiler->getTotalNumQueries()." queries]</th>";
echo "<th>Query Params</th>";
echo "</tr>";
foreach ($profiler->getQueryProfiles() as $query) {
    /** @var Zend_Db_Profiler_Query $query*/
    echo '<tr>';
    echo '<td>', number_format(1000 * $query->getElapsedSecs(), 2), 'ms', '</td>';
    echo '<td>', $query->getQuery(), '</td>';
    echo '<td>', json_encode($query->getQueryParams()), '</td>';
    echo '</tr>';
}
echo "</table>";
```

## 手順 3:結果を表示

ストアフロントまたは管理者の任意のページに移動して、結果を表示します。 次に例を示します。

![データベース・プロファイラの結果のサンプル](../../assets/configuration/db-profiler-results.png)
