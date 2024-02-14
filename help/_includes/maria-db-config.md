---
source-git-commit: d7926b9150137813b1161581bb1d7884a6fe11e9
workflow-type: tm+mt
source-wordcount: '138'
ht-degree: 1%

---
# MariaDB 構成設定

MariaDB 10.4 および 10.6 でのインデックス再作成は、以前の MariaDB または MySQL バージョンと比べて時間がかかります。 インデックスの再作成を高速化するには、次の MariaDB 設定パラメーターを設定することをお勧めします。

* [`optimizer_switch='rowid_filter=off'`](https://mariadb.com/kb/en/optimizer-switch/)
* [`optimizer_use_condition_selectivity = 1`](https://mariadb.com/products/skysql/docs/reference/es/system-variables/optimizer_use_condition_selectivity/)

MariaDB 10.6 にアップグレードした後、インデックス化に関連しないパフォーマンスの低下が発生する場合は、 [`--query-cache-type`](https://mariadb.com/kb/en/server-system-variables/#query_cache_type) 設定。 例： `--query-cache-type=ON`.

クラウドインフラストラクチャプロジェクト上のAdobe Commerceをアップグレードする前に、MariaDB ([MariaDB アップグレードのベストプラクティスを参照してください。](../implementation-playbook/best-practices/maintenance/mariadb-upgrade.md)) をクリックします。

例：

* Adobe Commerce 2.4.6（MariaDB バージョン 10.5.1 以降を使用）
* Adobe Commerce 2.3.5（MariaDB バージョン 10.3 以前）

次の推奨事項に加えて、次のパラメーターの設定については、データベース管理者に問い合わせる必要があります。

>[!NOTE]
>
>これらの設定は、オンプレミスでの展開でのみ使用できます。 Adobe Commerce on cloud infrastructure のお客様は、これらの設定にアクセスできません。

* [`--query-cache-limit`](https://mariadb.com/kb/en/server-system-variables/#query_cache_limit)
* [`--query-cache-size`](https://mariadb.com/kb/en/server-system-variables/#query_cache_size)
* [`--join-buffer-size`](https://mariadb.com/kb/en/server-system-variables/#join_buffer_size)
* [`--innodb-buffer-pool-size`](https://mariadb.com/kb/en/innodb-buffer-pool/#innodb_buffer_pool_size)
