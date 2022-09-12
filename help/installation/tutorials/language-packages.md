---
title: 言語パッケージのアンインストール
description: 次の手順に従って、Adobe CommerceまたはMagento Open Source言語パッケージをアンインストールします。
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 0%

---


# 言語パッケージのアンインストール

このセクションでは、1 つ以上の言語パッケージをアンインストールする方法について説明します。また、オプションで、言語パッケージのコードをファイルシステムから含めます。 最初にバックアップを作成して、後でデータを復元できます。

このコマンドは、アンインストールします *のみ* 言語パッケージ `composer.json`;言い換えれば、 [コンポーザー](https://glossary.magento.com/composer) パッケージ。 次に、 [言語パッケージ](https://glossary.magento.com/language-package) は Composer パッケージではありません。言語パッケージコードをファイルシステムから削除して、手動でアンインストールする必要があります。

バックアップは、 [`magento setup:rollback`](uninstall-modules.md#roll-back-the-file-system-database-or-media-files) コマンドを使用します。

コマンドの使用：

```bash
bin/magento i18n:uninstall [-b|--backup-code] {language package name} ... {language package name}
```

言語パッケージのアンインストールコマンドは、次のタスクを実行します。

1. 依存関係をチェックします。その場合、コマンドは終了します。

   この問題を回避するには、依存言語パッケージをすべて同時にアンインストールするか、依存言語パッケージを最初にアンインストールします。

1. If `--backup code` を指定した場合は、ファイル・システムをバックアップします ( `var` および `pub/static` ディレクトリ ) `var/backups/<timestamp>_filesystem.tgz`
1. を使用して、コードベースから言語パッケージファイルを削除します。 `composer remove`.
1. 次をクリーンアップ： [キャッシュ](https://glossary.magento.com/cache).

例えば、別の言語パッケージが依存する言語パッケージをアンインストールしようとすると、次のメッセージが表示されます。

```terminal
Cannot uninstall vendorname/language-en_us because the following package(s) depend on it:
      vendorname/language-en_gb
```

その代わりに、コードベースのバックアップ後に両方の言語パッケージをアンインストールします。

```bash
bin/magento i18n:uninstall vendorname/language-en_us vendorname/language-en_gb --backup-code
```

次のようなメッセージが表示されます。

```terminal
Code backup is starting...
Code backup filename: 1435261098_filesystem_code.tgz (The archive can be uncompressed with 7-Zip on Windows systems)
Code backup path: /var/www/html/magento2/var/backups/1435261098_filesystem_code.tgz
[SUCCESS]: Code backup completed successfully.
Loading composer repositories with package information
Updating dependencies (including require-dev)
  - Removing vendorname/language-en_us (dev-master)
Removing Magento/LanguageEn_us
  - Removing vendorname/language-en_br (dev-master)
  - Removing vendorname/language-en_br (dev-master)
Writing lock file
Generating autoload files
```
