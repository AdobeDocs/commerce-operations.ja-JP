---
title: モジュールのアンインストール
description: Adobe Commerce モジュールをアンインストールするには、次の手順に従います。
exl-id: 66879ef5-47c7-4b61-8c7e-78b60441980a
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '727'
ht-degree: 0%

---

# モジュールのアンインストール

この節では、1 つ以上のモジュールをアンインストールする方法について説明します。 アンインストール時に、モジュールのコード、データベーススキーマ、データベースデータをオプションで削除できます。 最初にバックアップを作成して、後でデータを回復できるようにします。

モジュールを使用しないことが確実な場合にのみ、モジュールをアンインストールしてください。 モジュールをアンインストールする代わりに、の説明に従って無効にすることができます。 [モジュールの有効化または無効化](manage-modules.md).

>[!NOTE]
>
>このコマンドは、 `composer.json` ファイル。 次のモジュールをアンインストールした場合： _ではない_ で定義 `composer.json` ファイル。このコマンドは、依存関係をチェックせずにモジュールをアンインストールします。 このコマンドは、 _ではない_&#x200B;ただし、ファイルシステムからモジュールのコードを削除します。 モジュールのコードを削除するには、ファイルシステムツールを使用する必要があります（例： `rm -rf <path to module>`）に設定します。 または、次のことができます。 [disable](manage-modules.md) 非 Composer モジュール

コマンドの使用法：

```bash
bin/magento module:uninstall [--backup-code] [--backup-media] [--backup-db] [-r|--remove-data] [-c|--clear-static-content] \
  {ModuleName} ... {ModuleName}
```

ここで、 `{ModuleName}` でモジュール名を指定 `<VendorName>_<ModuleName>` 形式。 例えば、顧客モジュール名はです `Magento_Customer`. モジュール名のリストを取得するには、と入力します `magento module:status`

モジュールのアンインストール コマンドは、次のタスクを実行します。

1. 指定したモジュールがコード ベースに存在し、Composer によってインストールされたパッケージであることを確認します。

   このコマンドは機能します _のみ_ （Composer パッケージとして定義されたモジュール）

1. 他のモジュールとの依存関係をチェックし、満たされていない依存関係がある場合はコマンドを終了します。

   この問題を回避するには、すべてのモジュールを同時にアンインストールするか、最初に依存モジュールをアンインストールします。

1. 続行の確認を要求します。
1. ストアをメンテナンスモードにします。
1. 次のコマンド オプションを処理します。

   | オプション | 意味 | バックアップ ファイルの名前と場所 |
   | ---------------- | -------------------------------------------------------------------------------- | -------------------------------------------- |
   | `--backup-code` | ファイル・システムをバックアップする（を除く） `var` および `pub/static` ディレクトリ）に含まれます。 | `var/backups/<timestamp>_filesystem.tgz` |
   | `--backup-media` | pub/media ディレクトリをバックアップします。 | `var/backups/<timestamp>_filesystem_media.tgz` |
   | `--backup-db` | データベースをバックアップします。 | `var/backups/<timestamp>_db.gz` |

1. 次の場合 `--remove-data` が指定されている場合、モジュールで定義されたデータベーススキーマおよびデータを削除します。 `Uninstall` クラス。

   指定したモジュールをアンインストールするたびに、はを呼び出します。 `uninstall` メソッド内 `Uninstall` クラス。 このクラスはから継承する必要があります [Magento\Framework\Setup\UninstallInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Setup/UninstallInterface.php).

1. 指定されたモジュールを `setup_module` データベーステーブル。
1. 指定されたモジュールをモジュール一覧から削除します [デプロイメント設定](../../configuration/reference/deployment-files.md).
1. を使用して、コードベースからコードを削除します。 `composer remove`.

   >[!NOTE]
   >
   >モジュールのアンインストール _常に_ 実行数 `composer remove`. この `--remove-data` オプションは、モジュールによって定義されたデータベースデータおよびスキーマを削除します。 `Uninstall` クラス。

1. キャッシュをクリアします。
1. 生成されたクラスを更新します。
1. 次の場合 `--clear-static-content` 指定した場合、クリアする [生成された静的ビューファイル](../../configuration/cli/static-view-file-deployment.md).
1. ストアをメンテナンスモードから削除します。

例えば、別のモジュールが依存しているモジュールをアンインストールしようとすると、次のメッセージが表示されます。

```terminal
magento module:uninstall Magento_SampleMinimal
    Cannot uninstall module 'Magento_SampleMinimal' because the following module(s) depend on it:
        Magento_SampleModifyContent
```

モジュールのファイルシステムをバックアップした後で両方のモジュールをアンインストールする方法もあります。 `pub/media` ファイル、およびデータベーステーブル _ではない_ モジュールのデータベーススキーマまたはデータを削除しています：

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
>別のモジュールに依存するモジュールをアンインストールしようとすると、エラーが表示されます。 この場合、1 つのモジュールをアンインストールすることはできません。両方をアンインストールする必要があります。

## ファイル・システム、データベース、メディア・ファイルのロール・バック

コードベースをバックアップした状態に復元するには、次のコマンドを使用します。

```bash
bin/magento setup:rollback [-c|--code-file="<filename>"] [-m|--media-file="<filename>"] [-d|--db-file="<filename>"]
```

ここで、 `<filename>` は、に含まれるバックアップファイルの名前です。 `<app_root>/var/backups` ディレクトリ。 バックアップ・ファイルのリストを表示するには、次のように入力します `magento info:backups:list`

>[!WARNING]
>
>このコマンドは、指定されたファイルまたはデータベースを復元する前に削除します。 例： `--media-file` の下にあるメディアアセットが削除されます。 `pub/media` 指定したロールバック・ファイルからリストアする前のディレクトリ。 このコマンドを使用する前に、保存するファイル・システムまたはデータベースを変更していないことを確認してください。

>[!NOTE]
>
>使用可能なバックアップ・ファイルのリストを表示するには、次のように入力します `magento info:backups:list`

このコマンドは、次のタスクを実行します。

1. ストアをメンテナンスモードにします。
1. バックアップ ファイル名を確認します。
1. コードのロールバックファイルを指定した場合：

   a. ロールバック先の場所が書き込み可能であることを確認します（注： `pub/static` および `var` フォルダーは無視されます）。

   b. アプリケーションのインストールディレクトリの下にあるすべてのファイルとディレクトリを削除します。

   c. アーカイブ・ファイルをデスティネーションの場所に抽出します。

1. データベース・ロールバック・ファイルを指定する場合：

   a. データベース全体を削除します。

   b. データベース バックアップを使用してデータベースをリストアします。

1. メディア ロールバック ファイルを指定した場合：

   a. ロールバック先の場所が書き込み可能であることを確認します。

   b.以下のすべてのファイルとディレクトリを削除します `pub/media`

   c. アーカイブ・ファイルをデスティネーションの場所に抽出します。

1. ストアをメンテナンスモードから削除します。

例えば、コード（ファイルシステム）のバックアップを復元するには、次のコマンドを表示された順序で入力します。

* バックアップの一覧を表示する：

  ```bash
  magento info:backups:list
  ```

* という名前のファイルバックアップを復元します。 `1433876616_filesystem.tgz`:

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
>を実行するには `magento` ディレクトリを変更せずに再度コマンドを実行する場合は、を入力する必要があります。 `cd pwd`.
