---
title: ログを有効にする
description: ログの種類を有効または無効にする方法を説明します。
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---


# ログを有効にする

{{file-system-owner}}

## デバッグのログ

デフォルトでは、Commerce はデバッグログ (`<install_directory>/var/log/debug.log`) は、デフォルトまたは開発モードの場合に呼び出されますが、実稼働モードの場合は呼び出されません。 以下を使用： `bin/magento setup:config:set --enable-debug-logging` コマンドを使用してデフォルト値を変更します。

>[!INFO]
>
>Commerce 2.3.1 以降では、 `bin/magento config:set dev/debug/debug_logging` コマンドを使用して、現在のモードのデバッグログを有効または無効にします。

### デバッグログを有効にするには

1. 以下を使用： `setup:config:set` コマンドを使用して、現在のモードのデバッグログを有効にします。

   ```bash
   bin/magento setup:config:set --enable-debug-logging=true
   ```

1. キャッシュをフラッシュします。

   ```bash
   bin/magento cache:flush
   ```

### デバッグログを無効にするには

1. 以下を使用： `setup:config:set` コマンドを使用して、現在のモードのデバッグログを無効にします。

   ```bash
   bin/magento setup:config:set --enable-debug-logging=false
   ```

1. キャッシュをフラッシュします。

   ```bash
   bin/magento cache:flush
   ```

## データベースログ

Commerce はデフォルトで、データベースアクティビティログを `<install-dir>/var/debug/db.log` ファイル。

### データベースログを有効にするには

1. 以下を使用： `dev:query-log` コマンドを使用して、データベースログを有効または無効にします。

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

## Cron ログ

バージョン 2.3.1 のリリースで、Commerce は別の `cron` ログ。 \
Commerce で最近、cron ログがより詳細になりました。より多くの情報が提供されましたが、長くなりました。 `system.log` かなり。
移動 `cron` 専用ログに情報を追加すると、両方のログを読みやすくなります。

デフォルトでは、Commerce は次のように書き込みます。 `cron` 情報 `<install-directory>/var/log/cron.log` ファイル。

## Syslog ログ

デフォルトでは、Commerce は次のように書き込みます。 _syslog_ オペレーティングシステムにログを記録する `syslog` ファイル。
Commerce 2.3.1 以降では、 `magento` コマンドを使用して、syslog を有効または無効にします。
管理者の設定は削除されました。

### syslog ログを有効にするには

へのログ `syslog` は、デフォルトでは無効です。

1. 以下を使用： `setup:config:set` コマンドを使用して `dev/syslog/syslog_logging` データベース値 `true`.

   ```bash
   bin/magento setup:config:set --enable-syslog-logging=true
   ```

1. キャッシュをフラッシュします。

   ```bash
   bin/magento cache:flush
   ```

### syslog ログを無効にするには

1. 以下を使用： `setup:config:set` コマンドを使用して `dev/syslog/syslog_logging` データベース値 `false`.

   ```bash
   bin/magento setup:config:set --enable-syslog-logging=false
   ```

1. キャッシュをフラッシュします。

   ```bash
   bin/magento cache:flush
   ```
