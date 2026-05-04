---
title: モジュールのアンインストール
description: コード、スキーマ、データをオプションで削除してAdobe Commerce モジュールをアンインストールする方法と、アンインストールする代わりにモジュールを無効にするタイミングについて説明します。
exl-id: 66879ef5-47c7-4b61-8c7e-78b60441980a
source-git-commit: 319f3232d1ba5f5ed7cdd10ce85b9d7ffbeec89a
workflow-type: tm+mt
source-wordcount: '754'
ht-degree: 0%

---

# モジュールのアンインストール

この節では、1つ以上のモジュールをアンインストールする方法について説明します。 アンインストール時に、オプションでモジュールのコード、データベーススキーマ、データベースデータを削除できます。 最初にバックアップを作成して、後でデータを復元できます。

モジュールは、確実に使用できない場合にのみアンインストールする必要があります。 モジュールをアンインストールする代わりに、[ モジュールの有効化または無効化](manage-modules.md)で説明したようにモジュールを無効化できます。

>[!NOTE]
>
>このコマンドは、`composer.json` ファイルで宣言された依存関係のみをチェックします。 `composer.json` ファイルで定義されている&#x200B;_not_&#x200B;のモジュールをアンインストールすると、このコマンドは依存関係を確認せずにモジュールをアンインストールします。 ただし、このコマンドは&#x200B;_not_&#x200B;を実行しますが、モジュールのコードをファイルシステムから削除します。 モジュールのコード （例：`rm -rf <path to module>`）を削除するには、ファイル システム ツールを使用する必要があります。 代わりに、[ コンポーザー以外のモジュールを](manage-modules.md)無効にできます。

コマンドの使用状況：

```shell
bin/magento module:uninstall [--backup-code] [--backup-media] [--backup-db] [-r|--remove-data] [-c|--clear-static-content] \
  {ModuleName} ... {ModuleName}
```

ここで、`{ModuleName}`は`<VendorName>_<ModuleName>`形式のモジュール名を指定します。 例えば、顧客モジュール名は`Magento_Customer`です。 モジュール名のリストを取得するには、`magento module:status`と入力します

モジュールのアンインストールコマンドは、次のタスクを実行します。

1. 指定したモジュールがコードベースに存在し、Composerによってインストールされたパッケージであることを確認します。

   このコマンドは、Composer パッケージとして定義されたモジュールで&#x200B;_のみ_&#x200B;に機能します。

1. 他のモジュールとの依存関係を確認し、満たされていない依存関係がある場合はコマンドを終了します。

   これを回避するには、すべてのモジュールを同時にアンインストールするか、最初に依存モジュールをアンインストールします。

1. 続行するには、確認を依頼します。
1. ストアをメンテナンスモードにします。
1. 次のコマンドオプションを処理します。

   | オプション | 意味 | バックアップファイルの名前と場所 |
   | ---------------- | -------------------------------------------------------------------------------- | -------------------------------------------- |
   | `--backup-code` | ファイルシステムをバックアップします（`var`および`pub/static` ディレクトリを除く）。 | `var/backups/<timestamp>_filesystem.tgz` |
   | `--backup-media` | pub/media ディレクトリをバックアップします。 | `var/backups/<timestamp>_filesystem_media.tgz` |
   | `--backup-db` | データベースをバックアップします。 | `var/backups/<timestamp>_db.gz` |

1. `--remove-data`が指定されている場合は、モジュールの`Uninstall` クラスで定義されているデータベース スキーマとデータを削除します。

   指定された各モジュールをアンインストールするには、その`Uninstall` クラスで`uninstall` メソッドを呼び出します。 このクラスは[Magento\Framework\Setup\UninstallInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Setup/UninstallInterface.php)から継承する必要があります。

1. 指定されたモジュールを`setup_module` データベース テーブルから削除します。
1. 指定されたモジュールを[ デプロイメント設定](../../configuration/reference/deployment-files.md)のモジュールリストから削除します。
1. `composer remove`を使用してコードベースからコードを削除します。

   >[!NOTE]
   >
   >モジュール _always_&#x200B;をアンインストールすると、`composer remove`が実行されます。 `--remove-data` オプションは、モジュールの`Uninstall` クラスによって定義されたデータベース データとスキーマを削除します。

1. キャッシュをクリーニングします。
1. 生成されたクラスを更新します。
1. `--clear-static-content`が指定されている場合、[生成された静的ビューファイル ](../../configuration/cli/static-view-file-deployment.md)をクリーンアップします。
1. メンテナンスモードからストアを取り除きます。

例えば、別のモジュールが依存しているモジュールをアンインストールしようとすると、次のメッセージが表示されます。

```shell
magento module:uninstall Magento_SampleMinimal
    Cannot uninstall module 'Magento_SampleMinimal' because the following module(s) depend on it:
        Magento_SampleModifyContent
```

1つの代替策として、モジュールファイルシステム、`pub/media`個のファイル、およびデータベーステーブルをバックアップした後に両方のモジュールをアンインストールしますが、モジュールのデータベーススキーマまたはデータを&#x200B;_not_&#x200B;削除します。

```shell
bin/magento module:uninstall Magento_SampleMinimal Magento_SampleModifyContent --backup-code --backup-media --backup-db
```

次のようなメッセージが表示されます。

```text
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
>別のモジュールに依存するモジュールをアンインストールしようとすると、エラーが表示されます。 この場合、1つのモジュールをアンインストールすることはできません。両方をアンインストールする必要があります。

## ファイルシステム、データベース、またはメディアファイルをロールバックする

コードベースをバックアップした状態に戻すには、次のコマンドを使用します。

```shell
bin/magento setup:rollback [-c|--code-file="<filename>"] [-m|--media-file="<filename>"] [-d|--db-file="<filename>"]
```

ここで、`<filename>`は`<app_root>/var/backups` ディレクトリ内のバックアップ ファイルの名前です。 バックアップ ファイルのリストを表示するには、`magento info:backups:list`と入力します

>[!WARNING]
>
>このコマンドは、指定したファイルまたはデータベースを削除してから復元します。 例えば、`--media-file` オプションは、指定されたロールバックファイルから復元する前に、`pub/media` ディレクトリの下のメディアアセットを削除します。 このコマンドを使用する前に、保持するファイルシステムまたはデータベースを変更していないことを確認してください。

>[!NOTE]
>
>使用可能なバックアップ ファイルのリストを表示するには、`magento info:backups:list`と入力します

このコマンドは、次のタスクを実行します。

1. ストアをメンテナンスモードにします。
1. バックアップファイル名を確認します。
1. コードロールバックファイルを指定した場合：

   a. ロールバック先の場所が書き込み可能であることを確認します（`pub/static`および`var` フォルダーは無視されることに注意）。

   b. アプリケーションインストールディレクトリの下にあるすべてのファイルとディレクトリを削除します。

   c. アーカイブ ファイルを保存先の場所に抽出します。

1. データベース・ロールバック・ファイルを指定した場合：

   a. データベース全体をドロップします。

   b. データベースのバックアップを使用してデータベースを復元します。

1. メディアロールバックファイルを指定した場合：

   a. ロールバック先の場所が書き込み可能であることを確認します。

   b. `pub/media`以下のすべてのファイルとディレクトリを削除します

   c. アーカイブ ファイルを保存先の場所に抽出します。

1. メンテナンスモードからストアを取り除きます。

例えば、コード（ファイルシステム）のバックアップを復元するには、次のコマンドを次の順序で入力します。

* バックアップのリストを表示します。

  ```shell
  magento info:backups:list
  ```

* `1433876616_filesystem.tgz`という名前のファイル バックアップを復元：

  ```shell
  magento setup:rollback --code-file="1433876616_filesystem.tgz"
  ```

  次のようなメッセージが表示されます。

  ```text
  Enabling maintenance mode
  Code rollback is starting ...
  Code rollback filename: 1433876616_filesystem.tgz
  Code rollback file path: /var/www/html/magento2/var/backups/1433876616_filesystem.tgz
  [SUCCESS]: Code rollback has completed successfully.
  Disabling maintenance mode
  ```

>[!NOTE]
>
>ディレクトリを変更せずに`magento` コマンドを再度実行するには、`cd pwd`を入力する必要がある場合があります。
