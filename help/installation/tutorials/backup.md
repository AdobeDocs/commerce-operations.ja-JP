---
title: ファイル・システム、メディア、データベースのバックアップとロールバック
description: Adobe Commerce アプリケーションをバックアップおよび復元するには、次の手順に従います。
exl-id: b9925198-37b4-4456-aa82-7c55d060c9eb
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '506'
ht-degree: 0%

---

# ファイル・システム、メディア、データベースのバックアップとロールバック

このコマンドを使用すると、次の項目をバックアップできます。

* ファイルシステム（を除く） `var` および `pub/static` ディレクトリ）
* この `pub/media` directory
* データベース

バックアップは `var/backups` ディレクトリであり、 [`magento setup:rollback`](uninstall-modules.md#roll-back-the-file-system-database-or-media-files) コマンド。

バックアップ後、次の操作を実行できます [rollback](#rollback) 後で。

>[!TIP]
>
>クラウドインフラストラクチャプロジェクトのAdobe Commerceについては、次を参照してください [スナップショットとバックアップ管理](https://devdocs.magento.com/cloud/project/project-webint-snap.html) が含まれる _クラウドガイド_.

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

以前のバックアップへのロールバックはサイレント・エラーで失敗する場合があり、不完全なデータがファイル・システムまたはデータベースに書き込まれる際に [`magento setup:rollback`](uninstall-modules.md#roll-back-the-file-system-database-or-media-files) コマンド。

クエリ文字列が長いと、再帰呼び出しが多すぎることが原因で、ユーザーに割り当てられたメモリ領域がメモリ不足になることがあります。

## 開いているファイルの設定方法 `ulimit`

開いているファイルを設定することをお勧めします [`ulimit`](https://ss64.com/bash/ulimit.html) （ファイルシステムユーザーの値を `65536` 以上。

これをコマンドラインで実行するか、シェルスクリプトを編集してユーザーに恒久的な設定を与えることができます。

続行する前に、まだ切り替えていない場合は、に切り替えます。 [ファイルシステム所有者](../prerequisites/file-system/overview.md).

コマンド：

```bash
ulimit -s 65536
```

必要に応じて、これを大きい値に変更できます。

>[!NOTE]
>
>開いているファイルの構文 `ulimit` 使用する UNIX シェルによって異なります。 上記の設定は、Bash シェルを使用している CentOS および Ubuntu で動作する必要があります。 ただし、macOSの場合、正しい設定は次のとおりです `ulimit -S 65532`. 詳細については、マニュアルページまたは OS のリファレンスを参照してください。

ユーザーの Bash シェルにオプションで値を設定するには：

1. まだ切り替えていない場合は、 [ファイルシステム所有者](../prerequisites/file-system/overview.md).
1. 開く `/home/<username>/.bashrc` テキストエディター。
1. 次の行を追加します。

   ```bash
   ulimit -s 65536
   ```

1. 変更をに保存します。 `.bashrc` をクリックして、テキストエディターを終了します。

>[!WARNING]
>
>の値は設定しないことをお勧めします [`pcre.recursion_limit`](https://www.php.net/manual/en/pcre.configuration.php) が含まれる `php.ini` 失敗の通知がない場合、ロールバックが不完全になる可能性があるためです。

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

```terminal
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

例えば、という名前のメディアバックアップを復元するには `1440611839_filesystem_media.tgz`、と入力します

```bash
bin/magento setup:rollback -m 1440611839_filesystem_media.tgz
```

次のようなメッセージが表示されます。

```terminal
[SUCCESS]: Media rollback completed successfully.
Please set file permission of bin/magento to executable
Disabling maintenance mode
```
