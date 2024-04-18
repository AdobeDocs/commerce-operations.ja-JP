---
title: テーマのアンインストール
description: Adobe Commerce テーマをアンインストールするには、次の手順に従います。
feature: Install, Themes
exl-id: 73150e8c-2d83-4479-b96b-75f41fd9c842
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# テーマのアンインストール

このコマンドを使用する前に、テーマへの相対パスを知っておく必要があります。 テーマは、次のサブディレクトリにあります。 `<magento_root>/app/design/<area name>`. テーマのパスは領域で始めて指定する必要があります。領域は次のいずれかになります `frontend` （ストアフロントテーマの場合）または `adminhtml` （管理テーマ用）。

例えば、Adobe Commerceで提供される Luma テーマへのパスは次のとおりです `frontend/Magento/luma`.

テーマについて詳しくは、次を参照してください [テーマの構造](https://developer.adobe.com/commerce/frontend-core/guide/themes/structure/).

## テーマのアンインストールの概要

この節では、1 つ以上のテーマをアンインストールする方法について説明します。テーマのコードはファイルシステムから必要に応じてアンインストールできます。 最初にバックアップを作成して、後でデータを復元できるようにします。

このコマンドはアンインストールします *のみ* で指定されているテーマ `composer.json`つまり、Composer パッケージとして提供されるテーマです。 テーマが Composer パッケージでない場合は、次の方法で手動でアンインストールする必要があります。

* を更新中 `parent` のノード情報 `theme.xml` をクリックして、テーマへの参照を削除します。
* ファイルシステムからテーマコードを削除しています。

  [テーマの継承に関する詳細情報](https://developer.adobe.com/commerce/frontend-core/guide/themes/inheritance/).

## テーマのアンインストール

コマンドの使用法：

```bash
bin/magento theme:uninstall [--backup-code] [-c|--clear-static-content] {theme path} ... {theme path}
```

ここで、

* `{theme path}` は、領域名で始まる、テーマの相対パスです。 例えば、Adobe Commerceに用意されている空白のテーマへのパスはです。 `frontend/Magento/blank`.
* `--backup-code` 以降の段落で説明するように、コードベースをバックアップします。
* `--clear-static-content` クリーンアップが生成されました [静的ビューファイル](../../configuration/cli/static-view-file-deployment.md)（静的ビューファイルを正しく表示するために必要）。

コマンドは、次のタスクを実行します。

1. 指定したテーマのパスが存在することを確認します。存在しない場合は、コマンドは終了します。
1. テーマが Composer パッケージであることを確認します。そうでない場合、コマンドは終了します。
1. 依存関係をチェックし、満たされていない依存関係がある場合はコマンドを終了します。

   これを回避するには、すべてのテーマを同時にアンインストールするか、テーマに応じてを最初にアンインストールします。

1. テーマが使用されていないことを確認します。使用されている場合は、コマンドが終了します。
1. テーマが仮想テーマのベースでないことを確認します。仮想テーマのベースである場合、コマンドは終了します。
1. ストアをメンテナンスモードにします。
1. 次の場合 `--backup-code` が指定されている場合は、を除くコードベースをバックアップします。 `pub/static`, `pub/media`、および `var` ディレクトリ。

   バックアップ ファイル名は `var/backups/<timestamp>_filesystem.tgz`

   を使用すると、いつでもバックアップを復元できます [`magento setup:rollback`](uninstall-modules.md#roll-back-the-file-system-database-or-media-files) コマンド。

1. からテーマを削除 `theme` データベーステーブル。
1. を使用してコードベースからテーマを削除する `composer remove`.
1. キャッシュをクリアします。
1. 生成されたクラスをクリーンアップ
1. 次の場合 `--clear-static-content` 指定した場合、クリアする [生成された静的ビューファイル](../../configuration/cli/static-view-file-deployment.md).

例えば、別のテーマが依存するテーマをアンインストールしようとすると、次のメッセージが表示されます。

```terminal
Cannot uninstall frontend/ExampleCorp/SampleModuleTheme because the following package(s) depend on it:
        ExampleCorp/sample-module-theme-depend
```

コードベースのバックアップを次のように行い、両方のテーマを同時にアンインストールすることもできます。

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
>また、管理テーマをアンインストールするには、コンポーネントの依存関係の挿入設定から削除する必要があります。 `<component root directory>/etc/di.xml`.
