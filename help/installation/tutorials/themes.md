---
title: テーマのアンインストール
description: コマンドラインからAdobe Commerce テーマをアンインストールする方法（Composer パッケージ、コードの削除、バックアップなど）について説明します。
feature: Install, Themes
exl-id: 73150e8c-2d83-4479-b96b-75f41fd9c842
source-git-commit: 319f3232d1ba5f5ed7cdd10ce85b9d7ffbeec89a
workflow-type: tm+mt
source-wordcount: '476'
ht-degree: 0%

---

# テーマのアンインストール

このコマンドを使用する前に、テーマへの相対パスを知っておく必要があります。 テーマは`<magento_root>/app/design/<area name>`のサブディレクトリにあります。 領域で始まるテーマへのパスを指定する必要があります。これは、`frontend` （ストアフロントテーマの場合）または`adminhtml` （管理者テーマの場合）です。

例えば、Adobe Commerceで提供されるLuma テーマへのパスは`frontend/Magento/luma`です。

テーマについて詳しくは、[ テーマ構造](https://developer.adobe.com/commerce/frontend-core/guide/themes/structure)を参照してください。

## テーマのアンインストールの概要

この節では、1つ以上のテーマをアンインストールする方法について説明します。オプションで、ファイルシステムからテーマのコードを含めることができます。 まずバックアップを作成して、後でデータを復元できます。

このコマンドは、`composer.json`で指定された&#x200B;*のみ*&#x200B;個のテーマをアンインストールします。つまり、Composer パッケージとして提供されるテーマです。 テーマがComposer パッケージでない場合は、次の方法で手動でアンインストールする必要があります。

* テーマへの参照を削除するために、`theme.xml`の`parent` ノード情報を更新しています。
* ファイルシステムからのテーマコードの削除。

  [ テーマの継承に関する詳細情報](https://developer.adobe.com/commerce/frontend-core/guide/themes/inheritance)。

## テーマのアンインストール

コマンドの使用状況：

```shell
bin/magento theme:uninstall [--backup-code] [-c|--clear-static-content] {theme path} ... {theme path}
```

どこで

* `{theme path}`は、エリア名で始まるテーマへの相対パスです。 例えば、Adobe Commerceで指定された空白テーマへのパスは`frontend/Magento/blank`です。
* `--backup-code`は、次の段落で説明されているように、コードベースをバックアップします。
* `--clear-static-content`は、静的ビューファイルを適切に表示するために必要な[静的ビューファイル ](../../configuration/cli/static-view-file-deployment.md)を生成しました。

このコマンドは、次のタスクを実行します。

1. 指定したテーマパスが存在することを確認します。存在しない場合は、コマンドを終了します。
1. テーマがComposer パッケージであることを確認します。そうでない場合は、コマンドは終了します。
1. 依存関係を確認し、満たされていない依存関係がある場合はコマンドを終了します。

   これを回避するには、すべてのテーマを同時にアンインストールするか、最初にテーマに応じてをアンインストールします。

1. テーマが使用されていないことを確認します。使用されている場合、コマンドは終了します。
1. テーマが仮想テーマのベースでないことを確認します。仮想テーマのベースである場合、コマンドは終了します。
1. ストアをメンテナンスモードにします。
1. `--backup-code`が指定されている場合は、`pub/static`、`pub/media`、`var` ディレクトリを除くコードベースをバックアップします。

   バックアップ ファイル名は`var/backups/<timestamp>_filesystem.tgz`です

   バックアップはいつでも[`magento setup:rollback`](uninstall-modules.md#roll-back-the-file-system-database-or-media-files) コマンドを使用して復元できます。

1. `theme` データベース テーブルからテーマを削除します。
1. `composer remove`を使用してコードベースからテーマを削除します。
1. キャッシュをクリーニングします。
1. 生成されたクラスをクリア
1. `--clear-static-content`が指定されている場合、[生成された静的ビューファイル ](../../configuration/cli/static-view-file-deployment.md)をクリーンアップします。

例えば、別のテーマが依存しているテーマをアンインストールしようとすると、次のメッセージが表示されます。

```text
Cannot uninstall frontend/ExampleCorp/SampleModuleTheme because the following package(s) depend on it:
        ExampleCorp/sample-module-theme-depend
```

もう1つの方法は、コードベースのバックアップに従って、両方のテーマを同時にアンインストールすることです。

```shell
bin/magento theme:uninstall frontend/ExampleCorp/SampleModuleTheme frontend/ExampleCorp/SampleModuleThemeDepend --backup-code
```

次のようなメッセージが表示されます。

```text
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
>管理者テーマをアンインストールするには、コンポーネントの依存関係インジェクション設定`<component root directory>/etc/di.xml`からも削除する必要があります。
