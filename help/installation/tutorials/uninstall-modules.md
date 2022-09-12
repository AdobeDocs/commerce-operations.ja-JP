---
title: モジュールのアンインストール
description: 次の手順に従って、Adobe CommerceまたはMagento Open Sourceモジュールをアンインストールします。
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '753'
ht-degree: 0%

---


# モジュールのアンインストール

このセクションでは、1 つ以上のモジュールをアンインストールする方法について説明します。 アンインストール時に、オプションでモジュールのコード、データベーススキーマ、データベースデータを削除できます。 最初にバックアップを作成して、後でデータを回復できるようにすることができます。

モジュールをアンインストールする必要があるのは、使用しないと確信できる場合のみです。 モジュールをアンインストールする代わりに、モジュールを無効にできます。 [モジュールの有効化または無効化](manage-modules.md).

>[!NOTE]
>
>このコマンドは、 `composer.json` ファイル。 をアンインストールした場合、 [モジュール](https://glossary.magento.com/module) は _not_ で定義 `composer.json` このコマンドは、依存関係をチェックせずにモジュールをアンインストールします。 このコマンドは実行します _not_&#x200B;ただし、ファイルシステムからモジュールのコードを削除します。 モジュールのコードを削除するには、ファイルシステムツールを使用する必要があります ( 例： `rm -rf <path to module>`) をクリックします。 別の方法として、次の操作を実行できます。 [無効](manage-modules.md) 非コンポーザーモジュール。

コマンドの使用：

```bash
bin/magento module:uninstall [--backup-code] [--backup-media] [--backup-db] [-r|--remove-data] [-c|--clear-static-content] \
  {ModuleName} ... {ModuleName}
```

ここで、 `{ModuleName}` モジュール名を `<VendorName>_<ModuleName>` 形式 例えば、顧客モジュール名は `Magento_Customer`. モジュール名のリストを取得するには、 `magento module:status`

module uninstall コマンドは、次のタスクを実行します。

1. 指定したモジュールがコードベースに存在し、パッケージが次のようにインストールされていることを確認します。 [コンポーザー](https://glossary.magento.com/composer).

   このコマンドは機能します _のみ_ と、コンポーザーパッケージとして定義されたモジュール。

1. 他のモジュールとの依存関係をチェックし、未満の依存関係がある場合はコマンドを終了します。

   この問題を回避するには、すべてのモジュールを同時にアンインストールするか、最初に依存するモジュールをアンインストールします。

1. 続行するには、確認を要求します。
1. ストアをメンテナンスモードにします。
1. 次のコマンドオプションを処理します。

   | オプション | 意味 | バックアップファイルの名前と場所 |
   | ---------------- | -------------------------------------------------------------------------------- | -------------------------------------------- |
   | `--backup-code` | ファイル・システムのバックアップ ( `var` および `pub/static` ディレクトリ )。 | `var/backups/<timestamp>_filesystem.tgz` |
   | `--backup-media` | pub/media ディレクトリをバックアップします。 | `var/backups/<timestamp>_filesystem_media.tgz` |
   | `--backup-db` | データベースをバックアップします。 | `var/backups/<timestamp>_db.gz` |

1. If `--remove-data` が指定されている場合、モジュールの `Uninstall` クラス。

   指定したモジュールごとに、 `uninstall` 法 `Uninstall` クラス。 このクラスは、 [Magento\Framework\Setup\UninstallInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Setup/UninstallInterface.php).

1. 指定したモジュールを `setup_module` データベーステーブル。
1. 指定したモジュールを [デプロイメント設定](../../configuration/reference/deployment-files.md).
1. を使用してコードベースからコードを削除します。 `composer remove`.

   >[!NOTE]
   >
   >モジュールのアンインストール _常に_ 実行 `composer remove`. この `--remove-data` オプションは、モジュールの `Uninstall` クラス。

1. 次をクリーンアップ： [キャッシュ](https://glossary.magento.com/cache).
1. 生成されたクラスを更新します。
1. If `--clear-static-content` が指定され、クリーン [生成された静的ビューファイル](../../configuration/cli/static-view-file-deployment.md).
1. メンテナンスモードからストアを削除します。

例えば、別のモジュールが依存するモジュールをアンインストールしようとすると、次のメッセージが表示されます。

```terminal
magento module:uninstall Magento_SampleMinimal
    Cannot uninstall module 'Magento_SampleMinimal' because the following module(s) depend on it:
        Magento_SampleModifyContent
```

その代わりに、モジュールファイルシステムのバックアップ後に両方のモジュールをアンインストールする方法があります。 `pub/media` ファイルとデータベース・テーブル ( _not_ モジュールの削除 [データベーススキーマ](https://glossary.magento.com/database-schema) またはデータ：

```bash
bin/magento module:uninstall Magento_SampleMinimal Magento_SampleModifyContent --backup-code --backup-media --backup-db
```

次のようなメッセージが表示されます。

```terminal
You are about to remove code and/or database tables. Are you sure?[y/N]y
Enabling maintenance mode
Code backup is starting...
Code backup filename: 1435261098_filesystem_code.tgz (The archive can be uncompressed with 7-Zip on Windows systems)
Code backup path: /var/www/html/magento2/var/backups/1435261098_filesystem_code.tgz
[SUCCESS]: Code backup completed successfully.
Media backup is starting...
Media backup filename: 1435261098_filesystem_media.tgz (The archive can be uncompressed with 7-Zip on Windows systems)
Media backup path: /var/www/html/magento2/var/backups/1435261098_filesystem_media.tgz
[SUCCESS]: Media backup completed successfully.
DB backup is starting...
DB backup filename: 1435261098_db.gz (The archive can be uncompressed with 7-Zip on Windows systems)
DB backup path: /var/www/html/magento2/var/backups/1435261098_db.gz
[SUCCESS]: DB backup completed successfully.
You are about to remove a module(s) that might have database data. Remove the database data manually after uninstalling, if desired.
Removing Magento_SampleMinimal, Magento_SampleModifyContent from module registry in database
Removing Magento_SampleMinimal, Magento_SampleModifyContent from module list in deployment configuration
Removing code from Magento codebase:
Loading composer repositories with package information
Updating dependencies (including require-dev)
  - Removing magento/sample-module-modifycontent (1.0.0)
Removing Magento/SampleModifycontent
  - Removing magento/sample-module-minimal (1.0.0)
Removing Magento/SampleMinimal
Writing lock file
Generating autoload files
Cache cleared successfully.
Generated classes cleared successfully.
Alert: Generated static view files were not cleared. You can clear them using the --clear-static-content option. Failure to clear static view files might cause display issues in the Admin and storefront.
Disabling maintenance mode
```

>[!NOTE]
>
>別のモジュールに依存するモジュールをアンインストールしようとすると、エラーが表示されます。 その場合、1 つのモジュールをアンインストールすることはできません。両方をアンインストールする必要があります。

## ファイル・システム、データベース、メディア・ファイルのロールバック

コードベースをバックアップした状態に復元するには、次のコマンドを使用します。

```bash
bin/magento setup:rollback [-c|--code-file="<filename>"] [-m|--media-file="<filename>"] [-d|--db-file="<filename>"]
```

ここで、 `<filename>` は、 `<app_root>/var/backups` ディレクトリ。 バックアップファイルの一覧を表示するには、次のように入力します。 `magento info:backups:list`

>[!WARNING]
>
>このコマンドは、指定したファイルまたはデータベースを復元する前に削除します。 例えば、 `--media-file` オプションは、 `pub/media` 指定したロールバックファイルからリストアする前のディレクトリ。 このコマンドを使用する前に、保持するファイルシステムまたはデータベースを変更していないことを確認してください。

>[!NOTE]
>
>使用可能なバックアップファイルの一覧を表示するには、次のように入力します。 `magento info:backups:list`

このコマンドは、次のタスクを実行します。

1. ストアをメンテナンスモードにします。
1. バックアップファイル名を検証します。
1. コードのロールバックファイルを指定する場合：

   a.ロールバック先の場所が書き込み可能であることを確認します ( `pub/static` および `var` フォルダーは無視されます )。

   b.アプリケーションのインストールディレクトリの下にあるすべてのファイルとディレクトリを削除します。

   c.アーカイブファイルを宛先の場所に抽出します。

1. データベース・ロールバック・ファイルを指定する場合：

   a.データベース全体を破棄します。

   b.データベースのバックアップを使用してデータベースをリストアします。

1. メディアのロールバック・ファイルを指定する場合：

   a.ロールバック先の場所が書き込み可能であることを確認します。

   b.以下のすべてのファイルとディレクトリを削除します。 `pub/media`

   c.アーカイブファイルを宛先の場所に抽出します。

1. メンテナンスモードからストアを削除します。

たとえば、コード（ファイルシステム）のバックアップを復元するには、次のコマンドを次の順序で入力します。

* バックアップの一覧を表示する：

   ```bash
   magento info:backups:list
   ```

* 次の名前のファイルバックアップを復元します。 `1433876616_filesystem.tgz`:

   ```bash
   magento setup:rollback --code-file="1433876616_filesystem.tgz"
   ```

   次のようなメッセージが表示されます。

   ```terminal
   Enabling maintenance mode
   Code rollback is starting ...
   Code rollback filename: 1433876616_filesystem.tgz
   Code rollback file path: /var/www/html/magento2/var/backups/1433876616_filesystem.tgz
   [SUCCESS]: Code rollback has completed successfully.
   Disabling maintenance mode
   ```

>[!NOTE]
>
>次の手順で `magento` コマンドを再度実行し、ディレクトリを変更せずに、 `cd pwd`.
