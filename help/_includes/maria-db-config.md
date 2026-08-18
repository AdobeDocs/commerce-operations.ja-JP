---
source-git-commit: 84a20012a81278cc95587ec14281b05330261687
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 1%

---
# MariaDB設定

MariaDB 10.4および10.6でのインデックス再作成は、以前のMariaDBまたはMySQL バージョンと比較して時間がかかります。 インデックス再作成を高速化するには、次のMariaDB設定パラメーターを設定することをお勧めします。

* [`optimizer_switch='rowid_filter=off'`](https://mariadb.com/kb/en/optimizer-switch/)
* [`optimizer_use_condition_selectivity = 1`](https://mariadb.com/docs/server/server-management/variables-and-modes/server-system-variables#optimizer_use_condition_selectivity)

MariaDB 10.6へのアップグレード後にインデックス作成に関連しないパフォーマンス低下が発生した場合は、[`--query-cache-type`](https://mariadb.com/kb/en/server-system-variables/#query_cache_type)設定を有効にすることを検討してください。 例：`--query-cache-type=ON`。

クラウドインフラストラクチャプロジェクト上のAdobe Commerceをアップグレードする前に、MariaDBをアップグレードする必要がある場合もあります（[MariaDB アップグレードのベストプラクティス &#x200B;](../implementation-playbook/best-practices/maintenance/mariadb-upgrade.md)を参照）。

例：

* Adobe Commerce 2.4.6 （MariaDB バージョン 10.5.1以降）
* MariaDB バージョン 10.3以前のAdobe Commerce 2.3.5

これらの推奨事項に加えて、次のパラメーターの設定については、データベース管理者に相談する必要があります。

>[!NOTE]
>
>これらの設定は、オンプレミスでのデプロイメントでのみ使用できます。 Adobe Commerce on cloud infrastructureのお客様は、これらの設定にアクセスできません。

* [`--query-cache-limit`](https://mariadb.com/kb/en/server-system-variables/#query_cache_limit)
* [`--query-cache-size`](https://mariadb.com/kb/en/server-system-variables/#query_cache_size)
* [`--join-buffer-size`](https://mariadb.com/kb/en/server-system-variables/#join_buffer_size)
* [`--innodb-buffer-pool-size`](https://mariadb.com/kb/en/innodb-buffer-pool/#innodb_buffer_pool_size)
