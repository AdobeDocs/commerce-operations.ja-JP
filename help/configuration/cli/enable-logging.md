---
title: ログを有効にする
description: Adobe Commerceでさまざまな種類のログインを有効および無効にする方法について説明します。 ロギングの設定と管理テクニックについて説明します。
feature: Configuration, Logs
exl-id: 78b0416a-5bad-42a9-a918-603600e98928
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 0%

---

# ログを有効にする

{{file-system-owner}}

## デバッグログ

デフォルトでは、Commerceはデフォルトモードまたは開発モードの場合はデバッグログ（`<install_directory>/var/log/debug.log`）に書き込まれますが、実稼動モードの場合は書き込まれません。 `bin/magento setup:config:set --enable-debug-logging` コマンドを使用して、既定値を変更します。

>[!INFO]
>
>Commerce 2.3.1以降、`bin/magento config:set dev/debug/debug_logging` コマンドを使用して現在のモードのデバッグログを有効または無効にすることはできなくなります。

### デバッグログを有効にするには

1. 現在のモードのデバッグ ログを有効にするには、`setup:config:set` コマンドを使用します。

   ```shell
   bin/magento setup:config:set --enable-debug-logging=true
   ```

1. キャッシュをフラッシュします。

   ```shell
   bin/magento cache:flush
   ```

### デバッグログを無効にするには

1. 現在のモードのデバッグ ログを無効にするには、`setup:config:set` コマンドを使用します。

   ```shell
   bin/magento setup:config:set --enable-debug-logging=false
   ```

1. キャッシュをフラッシュします。

   ```shell
   bin/magento cache:flush
   ```

## データベースのログ

デフォルトでは、Commerceはデータベースアクティビティログを`<install-dir>/var/debug/db.log` ファイルに書き込みます。

### クエリログの保存場所

データベースログが有効になっている場合、Commerceはクエリログを次の場所に保存します。

- **クエリログファイル**: `<install-directory>/var/debug/db.log`
- **ログディレクトリ**: `<install-directory>/var/debug/`

クエリログには次のものが含まれます。
- アプリケーションによって実行されるSQL クエリ
- クエリ実行時間
- クエリパラメーターとバインディング
- データベース接続情報

>[!NOTE]
>
>クエリログファイルは、トラフィックの多い環境では急速に大きくなる可能性があります。 ディスク容量を監視し、ログローテーションまたはクエリログファイルの定期的なクリーンアップの実装を検討してください。

### データベースのロギングを有効にするには

1. データベースのログ記録を有効または無効にするには、`dev:query-log` コマンドを使用します。

   ```shell
   bin/magento dev:query-log:enable
   ```

   ```shell
   bin/magento dev:query-log:disable
   ```

1. キャッシュをフラッシュします。

   ```shell
   bin/magento cache:flush
   ```

### クエリログを表示するには

標準のファイル表示コマンドを使用して、クエリログを表示できます。

```shell
# View the entire query log
cat var/debug/db.log

# View the last 100 lines of the query log
tail -n 100 var/debug/db.log

# Monitor the query log in real-time
tail -f var/debug/db.log

# Search for specific queries
grep "SELECT" var/debug/db.log
```

## Cron ログ

バージョン 2.3.1のリリースで、Commerceは個別の`cron` ログを作成するようになりました。 \
Commerceは最近、cronのログ記録をより詳細にし、より多くの情報を提供しましたが、`system.log`を大幅に延長しました。
`cron`情報を専用ログに移動すると、両方のログが読みやすくなります。

デフォルトでは、Commerceは`cron`情報を`<install-directory>/var/log/cron.log` ファイルに書き込みます。

## Syslog ログ

デフォルトでは、Commerceは&#x200B;_syslog_ ログをオペレーティングシステム `syslog` ファイルに書き込みます。
Commerce 2.3.1以降では、`magento` コマンドを使用してsyslogを有効または無効にする必要があります。
管理者の設定が削除されました。

### syslog ログを有効にするには

`syslog`へのログインは既定で無効になっています。

1. `setup:config:set` コマンドを使用して、`dev/syslog/syslog_logging` データベースの値を`true`に変更します。

   ```shell
   bin/magento setup:config:set --enable-syslog-logging=true
   ```

1. キャッシュをフラッシュします。

   ```shell
   bin/magento cache:flush
   ```

### syslog ログを無効にするには

1. `setup:config:set` コマンドを使用して、`dev/syslog/syslog_logging` データベースの値を`false`に変更します。

   ```shell
   bin/magento setup:config:set --enable-syslog-logging=false
   ```

1. キャッシュをフラッシュします。

   ```shell
   bin/magento cache:flush
   ```
