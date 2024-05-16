---
title: ログを有効にする
description: タイプのログを有効または無効にする方法について説明します。
feature: Configuration, Logs
exl-id: 78b0416a-5bad-42a9-a918-603600e98928
source-git-commit: 403a5937561d82b02fd126c95af3f70b0ded0747
workflow-type: tm+mt
source-wordcount: '258'
ht-degree: 0%

---

# ログを有効にする

{{file-system-owner}}

## デバッグログ

デフォルトでは、Commerceはデバッグログ（`<install_directory>/var/log/debug.log`）に設定する必要があります（デフォルトまたは開発モードの場合）。ただし、実稼動モードの場合は設定できません。 の使用 `bin/magento setup:config:set --enable-debug-logging` デフォルト値を変更するコマンド。

>[!INFO]
>
>Commerce 2.3.1 以降では、 `bin/magento config:set dev/debug/debug_logging` 現在のモードのデバッグログを有効または無効にするコマンド。

### デバッグ ログを有効にするには

1. の使用 `setup:config:set` 現在のモードのデバッグログを有効にするコマンド。

   ```bash
   bin/magento setup:config:set --enable-debug-logging=true
   ```

1. キャッシュをフラッシュします。

   ```bash
   bin/magento cache:flush
   ```

### デバッグ ログを無効にするには

1. の使用 `setup:config:set` 現在のモードのデバッグログを無効にするコマンド。

   ```bash
   bin/magento setup:config:set --enable-debug-logging=false
   ```

1. キャッシュをフラッシュします。

   ```bash
   bin/magento cache:flush
   ```

## データベースログ

デフォルトでは、Commerceはデータベースのアクティビティログをに書き込みます `<install-dir>/var/debug/db.log` ファイル。

### データベース ログを有効にするには

1. の使用 `dev:query-log` コマンドを使用して、データベース・ログを有効または無効にします。

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

バージョン 2.3.1 のリリースでは、Commerceは個別にを作成するようになりました `cron` ログ。 \
Commerceは最近、cron のログの詳細度を高めました。これにより提供される情報が増えましたが、ログの時間が長くなりました。 `system.log` かなり。
移動中 `cron` 専用ログに情報を書き込むと、両方のログが読みやすくなります。

デフォルトでは、Commerceは次のように記述します `cron` の情報 `<install-directory>/var/log/cron.log` ファイル。

## Syslog ログ

デフォルトでは、Commerceは次のように記述します _syslog_ オペレーティングシステムにログを記録 `syslog` ファイル。
Commerce 2.3.1 では、を使用する必要があります `magento` syslog を有効または無効にするコマンド。
管理者の設定が削除されました。

### syslog ログを有効にするには

へのログ `syslog` はデフォルトで無効になっています。

1. の使用 `setup:config:set` 変更するコマンド `dev/syslog/syslog_logging` データベースの値 `true`.

   ```bash
   bin/magento setup:config:set --enable-syslog-logging=true
   ```

1. キャッシュをフラッシュします。

   ```bash
   bin/magento cache:flush
   ```

### syslog ログを無効にするには

1. の使用 `setup:config:set` 変更するコマンド `dev/syslog/syslog_logging` データベースの値 `false`.

   ```bash
   bin/magento setup:config:set --enable-syslog-logging=false
   ```

1. キャッシュをフラッシュします。

   ```bash
   bin/magento cache:flush
   ```
