---
title: テーマのアンインストール
description: 次の手順に従って、Adobe CommerceまたはMagento Open Sourceテーマをアンインストールします。
feature: Install, Themes
exl-id: 73150e8c-2d83-4479-b96b-75f41fd9c842
source-git-commit: ce405a6bb548b177427e4c02640ce13149c48aff
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%

---

# テーマのアンインストール

このコマンドを使用する前に、テーマの相対パスを把握しておく必要があります。 テーマは、のサブディレクトリに配置されます。 `<magento_root>/app/design/<area name>`. テーマのパスは、領域 ( `frontend` （ストアフロントテーマの場合）または `adminhtml` （管理テーマ用）。

例えば、Adobe CommerceとMagento Open Sourceで提供される Luma テーマへのパスが `frontend/Magento/luma`.

テーマについて詳しくは、 [テーマ構造](https://developer.adobe.com/commerce/frontend-core/guide/themes/structure/).

## テーマのアンインストールの概要

このセクションでは、1 つ以上のテーマをアンインストールする方法について説明します。その際に、必要に応じてファイルシステムからテーマのコードを含めます。 最初にバックアップを作成して、後でデータを復元できます。

このコマンドは、アンインストールします *のみ* 指定されたテーマ `composer.json`;つまり、コンポーザーパッケージとして提供されるテーマです。 テーマが Composer パッケージでない場合は、次の方法で手動でアンインストールする必要があります。

* の更新 `parent` ノード情報 `theme.xml` をクリックして、テーマへの参照を削除します。
* ファイルシステムからテーマコードを削除する。

  [テーマの継承の詳細](https://developer.adobe.com/commerce/frontend-core/guide/themes/inheritance/).

## テーマのアンインストール

コマンドの使用：

```bash
bin/magento theme:uninstall [--backup-code] [-c|--clear-static-content] {theme path} ... {theme path}
```

ここで、

* `{theme path}` は、テーマの相対パスで、領域名から始まります。 例えば、Adobe CommerceとMagento Open Sourceで提供される空のテーマへのパスが `frontend/Magento/blank`.
* `--backup-code` 後述の段落で説明するように、コードベースをバックアップします。
* `--clear-static-content` 生成されたクリーン [静的表示ファイル](../../configuration/cli/static-view-file-deployment.md)：静的ビューファイルが正しく表示されるために必要です。

このコマンドは、次のタスクを実行します。

1. 指定したテーマのパスが存在することを確認します。そうでない場合、コマンドは終了します。
1. テーマが Composer パッケージであることを確認する。そうでない場合、コマンドは終了します。
1. 依存関係をチェックし、未満の依存関係がある場合はコマンドを終了します。

   この問題を回避するには、すべてのテーマを同時にアンインストールするか、まずテーマに応じてをアンインストールします。

1. テーマが使用されていないことを確認します。使用中の場合、コマンドは終了します。
1. テーマが仮想テーマのベースでないことを確認します。仮想テーマのベースの場合、コマンドは終了します。
1. ストアをメンテナンスモードにします。
1. If `--backup-code` を指定し、コードベースをバックアップします ( `pub/static`, `pub/media`、および `var` ディレクトリ。

   バックアップファイル名は次のとおりです。 `var/backups/<timestamp>_filesystem.tgz`

   バックアップは、 [`magento setup:rollback`](uninstall-modules.md#roll-back-the-file-system-database-or-media-files) コマンドを使用します。

1. テーマを `theme` データベーステーブル。
1. 次を使用して、コードベースからテーマを削除する `composer remove`.
1. キャッシュをクリーンします。
1. 生成されたクラスをクリーン
1. If `--clear-static-content` が指定され、クリーン [生成された静的ビューファイル](../../configuration/cli/static-view-file-deployment.md).

例えば、別のテーマが依存するテーマをアンインストールしようとすると、次のメッセージが表示されます。

```terminal
Cannot uninstall frontend/ExampleCorp/SampleModuleTheme because the following package(s) depend on it:
        ExampleCorp/sample-module-theme-depend
```

その 1 つは、次のコードベースのバックアップと同時に、両方のテーマをアンインストールする方法です。

```bash
bin/magento theme:uninstall frontend/ExampleCorp/SampleModuleTheme frontend/ExampleCorp/SampleModuleThemeDepend --backup-code
```

次のようなメッセージが表示されます。

```terminal
Code backup is starting...
Code backup filename: 1435261098_filesystem_code.tgz (The archive can be uncompressed with 7-Zip on Windows systems)
Code backup path: /var/www/html/magento2/var/backups/1435261098_filesystem_code.tgz
[SUCCESS]: Code backup completed successfully.Removing frontend/ExampleCorp/SampleModuleTheme, frontend/ExampleCorp/SampleModuleThemeDepend from database
Loading composer repositories with package information
Updating dependencies (including require-dev)
Removing frontend/ExampleCorp/SampleModuleTheme, frontend/ExampleCorp/SampleModuleThemeDepend from Magento codebase
  - Removing ExampleCorp/sample-module-theme-depend (dev-master)
Removing ExampleCorp/SampleThemeDepend
  - Removing ExampleCorp/sample-module-theme (dev-master)
Removing ExampleCorp/SampleTheme
Writing lock file
Generating autoload files
Cache cleared successfully.
Alert: Generated static view files were not cleared. You can clear them using the --clear-static-content option.
Failure to clear static view files might cause display issues in the Admin and storefront.
Disabling maintenance mode
```

>[!NOTE]
>
>管理テーマをアンインストールするには、コンポーネントの依存関係挿入設定から削除する必要もあります。 `<component root directory>/etc/di.xml`.
