---
source-git-commit: 631735eceb3609edd743c682291f373f6b01b399
workflow-type: tm+mt
source-wordcount: '143'
ht-degree: 0%

---
# MariaDB 構成設定

MariaDB 10.4 および 10.6 でのインデックス再作成は、以前の MariaDB または MySQL バージョンと比べて時間がかかります。 インデックスの再作成を高速化するには、次の MariaDB 設定パラメーターを設定することをお勧めします。

* [`optimizer_switch='rowid_filter=off'`](https://mariadb.com/kb/en/optimizer-switch/)
* [`optimizer_use_condition_selectivity = 1`](https://mariadb.com/products/skysql/docs/reference/es/system-variables/optimizer_use_condition_selectivity/)

MariaDB 10.6 にアップグレードした後、インデックス化に関連しないパフォーマンスの低下が発生する場合は、 [`--query-cache-type`](https://mariadb.com/kb/en/server-system-variables/#query_cache_type) 設定。 例： `--query-cache-type=ON`.

次の推奨事項に加えて、次のパラメーターの設定については、データベース管理者に問い合わせる必要があります。

>[!NOTE]
>
>これらの設定は、オンプレミスでの展開でのみ使用できます。 Adobe Commerce on cloud infrastructure のお客様は、これらの設定にアクセスできません。

* [`--query-cache-limit`](https://mariadb.com/kb/en/server-system-variables/#query_cache_limit)
* [`--query-cache-size`](https://mariadb.com/kb/en/server-system-variables/#query_cache_size)
* [`--join-buffer-size`](https://mariadb.com/kb/en/server-system-variables/#join_buffer_size)
* [`--innodb-buffer-pool-size`](https://mariadb.com/kb/en/innodb-buffer-pool/#innodb_buffer_pool_size)
