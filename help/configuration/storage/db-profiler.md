---
title: データベースプロファイラーの設定
description: データベース・プロファイラの出力の構成方法の例を参照してください。
feature: Configuration, Storage
badge: label="執筆：Atish Goswami" type="Informative" url="https://github.com/atishgoswami" tooltip="アティッシュ ゴスワミ"
exl-id: 87780db5-6e50-4ebb-9591-0cf22ab39af5
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 0%

---

# データベースプロファイラーの設定

Commerce データベースプロファイラーは、ページに実装されているすべてのクエリを表示します。これには、各クエリの時間や、適用されたパラメーターが含まれます。

## 手順 1：デプロイメント設定を変更する

変更 `<magento_root>/app/etc/env.php` 次の参照をに追加します [データベース プロファイラークラス](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/DB/Profiler.php):

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

## 手順 2：出力の設定

Commerce アプリケーションのブートストラップファイルに出力を設定します。次に例を示します `<magento_root>/pub/index.php` または、web サーバーの仮想ホスト設定に配置することもできます。

次の例では、結果が 3 列のテーブルに表示されます。

- 合計時間（ページ上のすべてのクエリの実行時間の合計を表示します）
- SQL （すべての SQL 問合せを表示します。行ヘッダーには問合せの件数が表示されます）
- クエリパラメーター（各 SQL クエリのパラメーターを表示します）

出力を設定するには、の後に次を追加します `$bootstrap->run($app);` bootstrap ファイルの行：

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

## 手順 3：結果の表示

結果を表示するには、ストアフロントまたは管理者の任意のページに移動します。 次に例を示します。

![データベース プロファイラーの結果のサンプル](../../assets/configuration/db-profiler-results.png)
