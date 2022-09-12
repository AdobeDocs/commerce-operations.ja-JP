---
title: ファイル・システム、メディア、データベースのバックアップとロールバック
description: 次の手順に従って、Adobe CommerceまたはMagento Open Sourceアプリケーションをバックアップおよび復元します。
source-git-commit: 8f05fb6fc212c2b3fda80457bbf27ecf16fb1194
workflow-type: tm+mt
source-wordcount: '516'
ht-degree: 0%

---


# ファイル・システム、メディア、データベースのバックアップとロールバック

このコマンドを使用すると、次のバックアップを実行できます。

* ファイルシステム ( `var` および `pub/static` ディレクトリ )
* この `pub/media` directory
* データベース

バックアップは、 `var/backups` ディレクトリに保存され、いつでも [`magento setup:rollback`](uninstall-modules.md#roll-back-the-file-system-database-or-media-files) コマンドを使用します。

バックアップ後、次の操作を実行できます。 [rollback](#rollback) 後で。

>[!TIP]
>
>Adobe Commerce on cloud infrastructure プロジェクトについては、 [スナップショットとバックアップ管理](https://devdocs.magento.com/cloud/project/project-webint-snap.html) 内 _クラウドガイド_.

## バックアップの有効化

バックアップ機能は、デフォルトで無効になっています。 有効にするには、次の CLI コマンドを入力します。

```bash
bin/magento config:set system/backup/functionality_enabled 1
```

>[!WARNING]
>
>**廃止のお知らせ：**
>バックアップ機能は、2.1.16、2.2.7 および 2.3.0 で廃止されました。追加のバックアップテクノロジーとバイナリバックアップツール（Percona XtraBackup など）を調査することをお勧めします。

## 開くファイルの制限を設定する

前回のバックアップへのロールバックは、警告なく失敗し、不完全なデータが [`magento setup:rollback`](uninstall-modules.md#roll-back-the-file-system-database-or-media-files) コマンドを使用します。

長いクエリ文字列を指定すると、再帰呼び出しが多すぎるため、ユーザーが割り当てたメモリ領域が不足する場合があります。

## 開いているファイルを設定する方法 `ulimit`

「開く」ファイルを設定することをお勧めします [`ulimit`](https://ss64.com/bash/ulimit.html) ( ファイルシステムユーザーの値が `65536` その他。

これは、コマンドラインで実行するか、シェルスクリプトを編集してユーザーに対して永続的な設定にすることができます。

続行する前に、まだおこなっていない場合は、 [ファイルシステム所有者](../prerequisites/file-system/overview.md).

コマンド：

```bash
ulimit -s 65536
```

必要に応じて、この値を大きい値に変更できます。

>[!NOTE]
>
>開いているファイルの構文 `ulimit` 使用する UNIX シェルに依存します。 上記の設定は、Bash シェルで CentOS および Ubuntu で動作します。 ただし、macOSの場合、正しい設定は次のようになります。 `ulimit -S 65532`. 詳細は、のマニュアルページまたはオペレーティングシステムのリファレンスを参照してください。

ユーザーの Bash シェルで値をオプションで設定するには、次の手順に従います。

1. まだおこなっていない場合は、 [ファイルシステム所有者](../prerequisites/file-system/overview.md).
1. 開く `/home/<username>/.bashrc` をクリックします。
1. 次の行を追加します。

   ```bash
   ulimit -s 65536
   ```

1. 変更をに保存します。 `.bashrc` をクリックし、テキストエディタを終了します。

>[!WARNING]
>
>の値は設定しないことをお勧めします。 [`pcre.recursion_limit`](https://www.php.net/manual/en/pcre.configuration.php) 内 `php.ini` ファイルを作成する必要があります。

## バックアップ中

コマンドの使用：

```bash
bin/magento setup:backup [--code] [--media] [--db]
```

このコマンドは、次のタスクを実行します。

1. ストアをメンテナンスモードにします。
1. 次のいずれかのコマンドオプションを実行します。

   | オプション | 意味 | バックアップファイルの名前と場所 |
   |--- |--- |--- |
   | `--code` | ファイル・システムをバックアップします（var および pub/static ディレクトリを除く）。 | `var/backups/<timestamp>/_filesystem.tgz` |
   | `--media` | pub/media ディレクトリをバックアップします。 | `var/backups/<timestamp>/_filesystem_media.tgz` |
   | `--db` | データベースをバックアップします。 | `var/backups/<timestamp>/_db.sql` |

1. メンテナンスモードからストアを削除します。

たとえば、ファイル・システムとデータベースをバックアップするには、次のようにします。

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

## ロールバック

このセクションでは、以前に作成したバックアップにロールバックする方法について説明します。 復元するバックアップファイルのファイル名を把握しておく必要があります。

バックアップの名前を検索するには、次のように入力します。

```bash
bin/magento info:backups:list
```

バックアップファイル名の最初の文字列は、タイムスタンプです。

以前のバックアップにロールバックするには、次のように入力します。

```bash
bin/magento setup:rollback [-c|--code-file="<name>"] [-m|--media-file="<name>"] [-d|--db-file="<name>"]
```

例えば、次の名前のメディアバックアップを復元するには、次のように指定します。 `1440611839_filesystem_media.tgz`を入力して、

```bash
bin/magento setup:rollback -m 1440611839_filesystem_media.tgz
```

次のようなメッセージが表示されます。

```terminal
[SUCCESS]: Media rollback completed successfully.
Please set file permission of bin/magento to executable
Disabling maintenance mode
```
