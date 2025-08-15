---
title: 言語パッケージのアンインストール
description: Adobe Commerce言語パッケージをアンインストールするには、次の手順に従います。
exl-id: 9901aa0b-af1a-4ae9-968f-ac8421060f57
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 0%

---

# 言語パッケージのアンインストール

ここでは、1 つ以上の言語パッケージ（オプションでファイルシステムから言語パッケージのコードも含む）をアンインストールする方法について説明します。 最初にバックアップを作成して、後でデータを復元できるようにします。

このコマンドは、*で指定された* のみ `composer.json` 言語パッケージ、つまり Composer パッケージとして提供されている言語パッケージをアンインストールします。 言語パッケージが Composer パッケージでない場合は、ファイルシステムから言語パッケージコードを削除して、手動でアンインストールする必要があります。

[`magento setup:rollback`](uninstall-modules.md#roll-back-the-file-system-database-or-media-files) コマンドを使用すれば、いつでもバックアップを復元できます。

コマンドの使用法：

```bash
bin/magento i18n:uninstall [-b|--backup-code] {language package name} ... {language package name}
```

言語パッケージのアンインストール コマンドは、次のタスクを実行します。

1. 依存関係を確認します。依存関係があれば、コマンドは終了します。

   これを回避するには、すべての依存言語パッケージを同時にアンインストールするか、最初に依存言語パッケージをアンインストールします。

1. `--backup code` が指定されている場合は、ファイルシステム（`var` ディレクトリと `pub/static` ディレクトリを除く）を `var/backups/<timestamp>_filesystem.tgz` にバックアップします
1. `composer remove` を使用して、コードベースから言語パッケージファイルを削除します。
1. キャッシュをクリアします。

例えば、別の言語パッケージが依存する言語パッケージをアンインストールしようとすると、次のメッセージが表示されます。

```
Cannot uninstall vendorname/language-en_us because the following package(s) depend on it:
      vendorname/language-en_gb
```

コードベースをバックアップした後で両方の言語パッケージをアンインストールする方法もあります。

```bash
bin/magento i18n:uninstall vendorname/language-en_us vendorname/language-en_gb --backup-code
```

次のようなメッセージが表示されます。

```
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
