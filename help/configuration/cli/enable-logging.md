---
title: ログを有効にする
description: Adobe Commerceで様々なタイプのログを有効または無効にする方法について説明します。 ログ設定と管理の手法について説明します。
feature: Configuration, Logs
exl-id: 78b0416a-5bad-42a9-a918-603600e98928
source-git-commit: aff705cefcd4de38d17cad41628bc8dbd6d630cb
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 0%

---

# ログを有効にする

{{file-system-owner}}

## デバッグログ

デフォルトでは、Commerceは、デフォルトまたは開発モードの場合はデバッグログ（`<install_directory>/var/log/debug.log`）に書き込みますが、実稼動モードの場合は書き込まれません。 `bin/magento setup:config:set --enable-debug-logging` コマンドを使用して、デフォルト値を変更します。

>[!INFO]
>
>Commerce 2.3.1 以降では、現在のモードのデバッグログを有効または無効にするために `bin/magento config:set dev/debug/debug_logging` コマンドを使用できなくなりました。

### デバッグ ログを有効にするには

1. `setup:config:set` コマンドを使用して、現在のモードのデバッグログを有効にします。

   ```bash
   bin/magento setup:config:set --enable-debug-logging=true
   ```

1. キャッシュをフラッシュします。

   ```bash
   bin/magento cache:flush
   ```

### デバッグ ログを無効にするには

1. `setup:config:set` コマンドを使用して、現在のモードのデバッグログを無効にします。

   ```bash
   bin/magento setup:config:set --enable-debug-logging=false
   ```

1. キャッシュをフラッシュします。

   ```bash
   bin/magento cache:flush
   ```

## データベースログ

デフォルトでは、Commerceはデータベースのアクティビティログを `<install-dir>/var/debug/db.log` ファイルに書き込みます。

### クエリ ログ ストレージの場所

データベースのログが有効な場合、Commerceはクエリログを次の場所に保存します。

- **クエリログファイル**:`<install-directory>/var/debug/db.log`
- **ログディレクトリ**: `<install-directory>/var/debug/`

クエリログには、次の内容が含まれます。
- アプリケーションで実行される SQL クエリ
- クエリの実行時間
- クエリパラメーターとバインディング
- データベース接続情報

>[!NOTE]
>
>高トラフィック環境では、クエリログファイルが急速に大きくなる可能性があります。 ディスク領域を監視し、ログのローテーションの実装またはクエリログファイルの定期的なクリーンアップを検討してください。

### データベース ログを有効にするには

1. `dev:query-log` コマンドを使用して、データベース・ログを有効または無効にします。

   ```bash
   bin/magento dev:query-log:enable
   ```

   ```bash
   bin/magento dev:query-log:disable
   ```

1. キャッシュをフラッシュします。

   ```bash
   bin/magento cache:flush
   ```

### クエリログを表示するには

標準のファイル表示コマンドを使用して、クエリログを表示できます。

```bash
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

バージョン 2.3.1 のリリースでは、Commerceは個別の `cron` ログを作成するようになりました。 \
Commerceは最近、cron のログの詳細度を高めました。これにより提供される情報は増えましたが、`system.log` が大幅に長くなりました。
情報 `cron` 専用ログに移動すると、両方のログが読みやすくなります。

デフォルトでは、Commerceは `cron` の情報を `<install-directory>/var/log/cron.log` ファイルに書き込みます。

## Syslog ログ

デフォルトでは、Commerceはオペレーティングシステムの _ファイルに_ syslog`syslog` ログを書き込みます。
Commerce 2.3.1 では、syslog を有効または無効にするには、`magento` コマンドを使用する必要があります。
管理者の設定が削除されました。

### syslog ログを有効にするには

`syslog` へのログは、デフォルトでは無効になっています。

1. `setup:config:set` コマンドを使用して、`dev/syslog/syslog_logging` データベースの値を `true` に変更します。

   ```bash
   bin/magento setup:config:set --enable-syslog-logging=true
   ```

1. キャッシュをフラッシュします。

   ```bash
   bin/magento cache:flush
   ```

### syslog ログを無効にするには

1. `setup:config:set` コマンドを使用して、`dev/syslog/syslog_logging` データベースの値を `false` に変更します。

   ```bash
   bin/magento setup:config:set --enable-syslog-logging=false
   ```

1. キャッシュをフラッシュします。

   ```bash
   bin/magento cache:flush
   ```
