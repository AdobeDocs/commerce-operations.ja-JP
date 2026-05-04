---
title: ファイルシステム、メディア、データベースのバックアップとロールバック
description: Adobe Commerce アプリケーションをバックアップおよび復元するには、次の手順に従います。
exl-id: b9925198-37b4-4456-aa82-7c55d060c9eb
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '522'
ht-degree: 0%

---

# ファイルシステム、メディア、データベースのバックアップとロールバック

このコマンドを使用すると、次のバックアップを作成できます。

* ファイルシステム （`var`および`pub/static` ディレクトリを除く）
* `pub/media` ディレクトリ
* データベース

バックアップは`var/backups` ディレクトリに保存され、[`magento setup:rollback`](uninstall-modules.md#roll-back-the-file-system-database-or-media-files) コマンドを使用していつでも復元できます。

バックアップ後、後で[&#x200B; ロールバック &#x200B;](#rollback)できます。

>[!TIP]
>
>クラウドインフラストラクチャプロジェクト上のAdobe Commerceについては、_クラウドガイド_&#x200B;の[&#x200B; スナップショットとバックアップ管理](https://experienceleague.adobe.com/ja/docs/commerce-cloud-service/user-guide/develop/storage/snapshots)を参照してください。

## バックアップを有効にする

バックアップ機能はデフォルトで無効になっています。 有効にするには、次のCLI コマンドを入力します。

```shell
bin/magento config:set system/backup/functionality_enabled 1
```

>[!WARNING]
>
>**非推奨化のお知らせ：**
>バックアップ機能は、2.1.16、2.2.7、および2.3.0で廃止されました。 追加のバックアップテクノロジーとバイナリバックアップツール（Percona XtraBackupなど）を調査することをお勧めします。

## 開いているファイルの制限を設定する

以前のバックアップにロールバックすると、サイレントに失敗する可能性があり、不完全なデータが[`magento setup:rollback`](uninstall-modules.md#roll-back-the-file-system-database-or-media-files) コマンドを使用してファイルシステムまたはデータベースに書き込まれます。

クエリ文字列が長すぎると、再帰呼び出しが多すぎるため、ユーザーに割り当てられたメモリ領域がメモリ不足になることがあります。

## 開いているファイル `ulimit`の設定方法

ファイル システム ユーザーの開いているファイル [`ulimit`](https://ss64.com/bash/ulimit.html)を`65536`以上の値に設定することをお勧めします。

これはコマンドラインで行うことも、シェルスクリプトを編集してユーザーの永続的な設定にすることもできます。

続行する前に、まだ実行していない場合は、[&#x200B; ファイルシステム所有者](../prerequisites/file-system/overview.md)に切り替えてください。

コマンド：

```shell
ulimit -s 65536
```

必要に応じてこれを大きな値に変更できます。

>[!NOTE]
>
>開いているファイル `ulimit`の構文は、使用するUNIX シェルによって異なります。 上記の設定は、CentOSおよびUbuntuとBash シェルで動作する必要があります。 ただし、macOSの場合、正しい設定は`ulimit -S 65532`です。 詳細については、マニュアル ページまたはオペレーティング システム リファレンスを参照してください。

オプションで、ユーザーのBash シェルの値を設定するには、次の手順を実行します。

1. まだ実行していない場合は、[&#x200B; ファイルシステム所有者](../prerequisites/file-system/overview.md)に切り替えます。
1. `/home/<username>/.bashrc`をテキストエディターで開きます。
1. 次の行を追加します。

   ```shell
   ulimit -s 65536
   ```

1. 変更を`.bashrc`に保存して、テキストエディターを終了します。

>[!WARNING]
>
>`php.ini` ファイルの[`pcre.recursion_limit`](https://www.php.net/manual/en/pcre.configuration.php)に値を設定することを避けることをお勧めします。これにより、エラー通知なしで不完全なロールバックが発生する可能性があります。

## バックアップ

コマンドの使用状況：

```shell
bin/magento setup:backup [--code] [--media] [--db]
```

このコマンドは、次のタスクを実行します。

1. ストアをメンテナンスモードにします。
1. 次のいずれかのコマンドオプションを実行します。

   | オプション | 意味 | バックアップファイルの名前と場所 |
   |--- |--- |--- |
   | `--code` | ファイルシステムをバックアップします（varおよびpub/static ディレクトリを除く）。 | `var/backups/<timestamp>/_filesystem.tgz` |
   | `--media` | pub/media ディレクトリをバックアップします。 | `var/backups/<timestamp>/_filesystem_media.tgz` |
   | `--db` | データベースをバックアップします。 | `var/backups/<timestamp>/_db.sql` |

1. メンテナンスモードからストアを取り除きます。

例えば、ファイルシステムとデータベースをバックアップするには，

```shell
bin/magento setup:backup --code --db
```

次のようなメッセージが表示されます。

```shell
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

このセクションでは、以前に作成したバックアップにロールバックする方法について説明します。 復元するバックアップファイルのファイル名を知っている必要があります。

バックアップの名前を検索するには、次のように入力します。

```shell
bin/magento info:backups:list
```

バックアップファイル名の最初の文字列はタイムスタンプです。

以前のバックアップにロールバックするには、次のように入力します。

```shell
bin/magento setup:rollback [-c|--code-file="<name>"] [-m|--media-file="<name>"] [-d|--db-file="<name>"]
```

例えば、`1440611839_filesystem_media.tgz`という名前のメディア バックアップを復元するには、次のように入力します

```shell
bin/magento setup:rollback -m 1440611839_filesystem_media.tgz
```

次のようなメッセージが表示されます。

```shell
[SUCCESS]: Media rollback completed successfully.
Please set file permission of bin/magento to executable
Disabling maintenance mode
```
