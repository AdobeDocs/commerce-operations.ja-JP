---
title: モジュールのアンインストール
description: Adobe Commerce モジュールをアンインストールするには、次の手順に従います。
exl-id: 66879ef5-47c7-4b61-8c7e-78b60441980a
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '727'
ht-degree: 0%

---

# モジュールのアンインストール

この節では、1 つ以上のモジュールをアンインストールする方法について説明します。 アンインストール時に、モジュールのコード、データベーススキーマ、データベースデータをオプションで削除できます。 最初にバックアップを作成して、後でデータを回復できるようにします。

モジュールを使用しないことが確実な場合にのみ、モジュールをアンインストールしてください。 モジュールをアンインストールする代わりに、[&#x200B; モジュールの有効化または無効化 &#x200B;](manage-modules.md) で説明されているように無効にすることができます。

>[!NOTE]
>
>このコマンドは、`composer.json` ファイルで宣言されている依存関係のみを確認します。 _ファイルで定義されて_ ない `composer.json` モジュールをアンインストールする場合、このコマンドは依存関係を確認せずにモジュールをアンインストールします。 ただし、このコマンドはモジュールのコードをファイルシステムから削除 _しません_。 モジュールのコード（例：`rm -rf <path to module>`）を削除するには、ファイルシステムツールを使用する必要があります。 別の方法として、Composer 以外のモジュールを [&#x200B; 無効 &#x200B;](manage-modules.md) することもできます。

コマンドの使用法：

```bash
bin/magento module:uninstall [--backup-code] [--backup-media] [--backup-db] [-r|--remove-data] [-c|--clear-static-content] \
  {ModuleName} ... {ModuleName}
```

ここで、`{ModuleName}` は `<VendorName>_<ModuleName>` 形式のモジュール名を指定します。 例えば、顧客モジュール名は `Magento_Customer` です。 モジュール名のリストを取得するには、`magento module:status` と入力します

モジュールのアンインストール コマンドは、次のタスクを実行します。

1. 指定したモジュールがコード ベースに存在し、Composer によってインストールされたパッケージであることを確認します。

   このコマンドは、Composer パッケージとして定義されたモジュールで _のみ_ 機能します。

1. 他のモジュールとの依存関係をチェックし、満たされていない依存関係がある場合はコマンドを終了します。

   この問題を回避するには、すべてのモジュールを同時にアンインストールするか、最初に依存モジュールをアンインストールします。

1. 続行の確認を要求します。
1. ストアをメンテナンスモードにします。
1. 次のコマンド オプションを処理します。

   | オプション | 意味 | バックアップ ファイルの名前と場所 |
   | ---------------- | -------------------------------------------------------------------------------- | -------------------------------------------- |
   | `--backup-code` | ファイルシステムをバックアップします（`var` ディレクトリと `pub/static` ディレクトリを除く）。 | `var/backups/<timestamp>_filesystem.tgz` |
   | `--backup-media` | pub/media ディレクトリをバックアップします。 | `var/backups/<timestamp>_filesystem_media.tgz` |
   | `--backup-db` | データベースをバックアップします。 | `var/backups/<timestamp>_db.gz` |

1. `--remove-data` が指定されている場合は、モジュールの `Uninstall` クラスで定義されているデータベーススキーマとデータを削除します。

   指定したモジュールをアンインストールするたびに、は `uninstall` クラスの `Uninstall` メソッドを呼び出します。 このクラスは [Magento\Framework\Setup\UninstallInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Setup/UninstallInterface.php) から継承する必要があります。

1. 指定されたモジュールを `setup_module` データベース テーブルから削除します。
1. 指定されたモジュールを [&#x200B; 展開の構成 &#x200B;](../../configuration/reference/deployment-files.md) のモジュール一覧から削除します。
1. `composer remove` を使用してコードベースからコードを削除します。

   >[!NOTE]
   >
   >モジュールを _常に_ アンインストールすると、`composer remove` 実行されます。 `--remove-data` オプションは、モジュールの `Uninstall` クラスによって定義されたデータベースデータおよびスキーマを削除します。

1. キャッシュをクリアします。
1. 生成されたクラスを更新します。
1. `--clear-static-content` が指定されている場合、は [&#x200B; 生成された静的ビューファイル &#x200B;](../../configuration/cli/static-view-file-deployment.md) をクリーンアップします。
1. ストアをメンテナンスモードから削除します。

例えば、別のモジュールが依存しているモジュールをアンインストールしようとすると、次のメッセージが表示されます。

```
magento module:uninstall Magento_SampleMinimal
    Cannot uninstall module 'Magento_SampleMinimal' because the following module(s) depend on it:
        Magento_SampleModifyContent
```

モジュール ファイル システム、`pub/media` ファイル、およびデータベース テーブルをバックアップした後で、モジュールのデータベース スキーマまたはデータを削除して _以_ の方法で両方のモジュールをアンインストールすることもできます。

```bash
bin/magento module:uninstall Magento_SampleMinimal Magento_SampleModifyContent --backup-code --backup-media --backup-db
```

次のようなメッセージが表示されます。

```
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

ここで、`<filename>` は `<app_root>/var/backups` ディレクトリ内のバックアップファイルの名前です。 バックアップ ファイルの一覧を表示するには、`magento info:backups:list` と入力します

>[!WARNING]
>
>このコマンドは、指定されたファイルまたはデータベースを復元する前に削除します。 例えば、`--media-file` オプションを指定すると、`pub/media` ディレクトリの下のメディアアセットが削除されてから、指定したロールバックファイルから復元されます。 このコマンドを使用する前に、保存するファイル・システムまたはデータベースを変更していないことを確認してください。

>[!NOTE]
>
>使用可能なバックアップ ファイルの一覧を表示するには、`magento info:backups:list` と入力します

このコマンドは、次のタスクを実行します。

1. ストアをメンテナンスモードにします。
1. バックアップ ファイル名を確認します。
1. コードのロールバックファイルを指定した場合：

   a. ロールバック先の場所が書き込み可能であることを確認します（`pub/static` フォルダーと `var` フォルダーは無視されます）。

   b. アプリケーションのインストールディレクトリの下にあるすべてのファイルとディレクトリを削除します。

   c. アーカイブ・ファイルをデスティネーションの場所に抽出します。

1. データベース・ロールバック・ファイルを指定する場合：

   a. データベース全体を削除します。

   b. データベース バックアップを使用してデータベースをリストアします。

1. メディア ロールバック ファイルを指定した場合：

   a. ロールバック先の場所が書き込み可能であることを確認します。

   b. `pub/media` のすべてのファイルとディレクトリを削除します

   c. アーカイブ・ファイルをデスティネーションの場所に抽出します。

1. ストアをメンテナンスモードから削除します。

例えば、コード（ファイルシステム）のバックアップを復元するには、次のコマンドを表示された順序で入力します。

* バックアップの一覧を表示する：

  ```bash
  magento info:backups:list
  ```

* `1433876616_filesystem.tgz` という名前のファイル バックアップを復元します。

  ```bash
  magento setup:rollback --code-file="1433876616_filesystem.tgz"
  ```

  次のようなメッセージが表示されます。

  ```
  Enabling maintenance mode
  Code rollback is starting ...
  Code rollback filename: 1433876616_filesystem.tgz
  Code rollback file path: /var/www/html/magento2/var/backups/1433876616_filesystem.tgz
  [SUCCESS]: Code rollback has completed successfully.
  Disabling maintenance mode
  ```

>[!NOTE]
>
>ディレクトリを変更せずに `magento` コマンドを再度実行するには、`cd pwd` を入力する必要があります。
