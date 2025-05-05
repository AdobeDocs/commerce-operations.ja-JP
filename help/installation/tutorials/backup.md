---
title: ファイル・システム、メディア、データベースのバックアップとロールバック
description: Adobe Commerce アプリケーションをバックアップおよび復元するには、次の手順に従います。
exl-id: b9925198-37b4-4456-aa82-7c55d060c9eb
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '506'
ht-degree: 0%

---

# ファイル・システム、メディア、データベースのバックアップとロールバック

このコマンドを使用すると、次の項目をバックアップできます。

* ファイルシステム（`var` ディレクトリと `pub/static` ディレクトリを除く）
* `pub/media` ディレクトリ
* データベース

バックアップは `var/backups` ディレクトリに保存され、[`magento setup:rollback`](uninstall-modules.md#roll-back-the-file-system-database-or-media-files) コマンドを使用していつでも復元できます。

バックアップ後、後で [ ロールバック ](#rollback) できます。

>[!TIP]
>
>クラウドインフラストラクチャプロジェクトのAdobe Commerceについては、_クラウドガイド_ の [ スナップショットとバックアップの管理 ](https://experienceleague.adobe.com/ja/docs/commerce-cloud-service/user-guide/develop/storage/snapshots) を参照してください。

## バックアップを有効にする

バックアップ機能はデフォルトで無効になっています。 有効にするには、次の CLI コマンドを入力します。

```bash
bin/magento config:set system/backup/functionality_enabled 1
```

>[!WARNING]
>
>**非推奨（廃止予定）のお知らせ：**
>バックアップ機能は、2.1.16、2.2.7、2.3.0 で非推奨（廃止予定）となりました。追加のバックアップテクノロジーとバイナリバックアップツール（Percona XtraBackup など）を調査することをお勧めします。

## 開いているファイルの上限を設定

以前のバックアップへのロールバックはサイレントに失敗する場合があり、[`magento setup:rollback`](uninstall-modules.md#roll-back-the-file-system-database-or-media-files) コマンドを使用して不完全なデータがファイルシステムまたはデータベースに書き込まれる結果となります。

クエリ文字列が長いと、再帰呼び出しが多すぎることが原因で、ユーザーに割り当てられたメモリ領域がメモリ不足になることがあります。

## 開いているファイルの `ulimit` 定方法

ファイルシステムユーザーに対して開いているファイル [`ulimit`](https://ss64.com/bash/ulimit.html) を `65536` 以上の値に設定することをお勧めします。

これをコマンドラインで実行するか、シェルスクリプトを編集してユーザーに恒久的な設定を与えることができます。

続行する前に、まだ実行していない場合は、[ ファイルシステムの所有者 ](../prerequisites/file-system/overview.md) に切り替えます。

コマンド：

```bash
ulimit -s 65536
```

必要に応じて、これを大きい値に変更できます。

>[!NOTE]
>
>開いているファイル `ulimit` の構文は、使用する UNIX シェルによって異なります。 上記の設定は、Bash シェルを使用している CentOS および Ubuntu で動作する必要があります。 ただし、macOSの場合、正しい設定は `ulimit -S 65532` です。 詳細については、マニュアルページまたは OS のリファレンスを参照してください。

ユーザーの Bash シェルにオプションで値を設定するには：

1. まだ切り替えていない場合は、[ ファイルシステムの所有者 ](../prerequisites/file-system/overview.md) に切り替えます。
1. `/home/<username>/.bashrc` をテキストエディターで開きます。
1. 次の行を追加します。

   ```bash
   ulimit -s 65536
   ```

1. `.bashrc` への変更を保存し、テキストエディターを終了します。

>[!WARNING]
>
>`php.ini` ファイルで [`pcre.recursion_limit`](https://www.php.net/manual/en/pcre.configuration.php) の値を設定することは避けることをお勧めします。設定すると、エラー通知のない不完全なロールバックが生じる可能性があるからです。

## バックアップ中

コマンドの使用法：

```bash
bin/magento setup:backup [--code] [--media] [--db]
```

コマンドは、次のタスクを実行します。

1. ストアをメンテナンスモードにします。
1. 次のいずれかのコマンド オプションを実行します。

   | オプション | 意味 | バックアップ ファイルの名前と場所 |
   |--- |--- |--- |
   | `--code` | ファイルシステムをバックアップします（var ディレクトリと pub/static ディレクトリを除く）。 | `var/backups/<timestamp>/_filesystem.tgz` |
   | `--media` | pub/media ディレクトリをバックアップします。 | `var/backups/<timestamp>/_filesystem_media.tgz` |
   | `--db` | データベースをバックアップします。 | `var/backups/<timestamp>/_db.sql` |

1. ストアをメンテナンスモードから削除します。

例えば、ファイルシステムとデータベースをバックアップするには、次のように指定します。

```bash
bin/magento setup:backup --code --db
```

次のようなメッセージが表示されます。

```
Enabling maintenance mode
Code backup is starting...
Code backup filename: 1434133011_filesystem.tgz (The archive can be uncompressed with 7-Zip on Windows systems)
Code backup path: /var/www/html/magento2/var/backups/1434133011_filesystem.tgz
[SUCCESS]: Code backup completed successfully.
DB backup is starting...
DB backup filename: 1434133011_db.sql
DB backup path: /var/www/html/magento2/var/backups/1434133011_db.sql
[SUCCESS]: DB backup completed successfully.
Disabling maintenance mode
```

## Rollback

このセクションでは、以前に作成したバックアップにロールバックする方法について説明します。 復元するバックアップファイルのファイル名を知っている必要があります。

バックアップの名前を検索するには、次のように入力します。

```bash
bin/magento info:backups:list
```

バックアップ ファイル名の最初の文字列はタイムスタンプです。

以前のバックアップにロールバックするには、次のように入力します。

```bash
bin/magento setup:rollback [-c|--code-file="<name>"] [-m|--media-file="<name>"] [-d|--db-file="<name>"]
```

たとえば、`1440611839_filesystem_media.tgz` という名前のメディア バックアップを復元するには、次のように入力します

```bash
bin/magento setup:rollback -m 1440611839_filesystem_media.tgz
```

次のようなメッセージが表示されます。

```
[SUCCESS]: Media rollback completed successfully.
Please set file permission of bin/magento to executable
Disabling maintenance mode
```
