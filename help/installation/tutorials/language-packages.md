---
title: 言語パッケージのアンインストール
description: Adobe Commerce言語パッケージをアンインストールするには、次の手順に従います。
exl-id: 9901aa0b-af1a-4ae9-968f-ac8421060f57
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 0%
---
# 言語パッケージのアンインストール

この節では、1つ以上の言語パッケージをアンインストールする方法について説明します。オプションとして、言語パッケージのコードをファイルシステムから含めることができます。 まずバックアップを作成して、後でデータを復元できます。

このコマンドは、`composer.json`で指定された&#x200B;*のみ*&#x200B;の言語パッケージ、つまりComposer パッケージとして提供される言語パッケージをアンインストールします。 言語パッケージがComposer パッケージでない場合は、言語パッケージコードをファイルシステムから削除して、手動でアンインストールする必要があります。

バックアップはいつでも[`magento setup:rollback`](uninstall-modules.md#roll-back-the-file-system-database-or-media-files) コマンドを使用して復元できます。

コマンドの使用状況：

```shell
bin/magento i18n:uninstall [-b|--backup-code] {language package name} ... {language package name}
```

言語パッケージのアンインストールコマンドは、次のタスクを実行します。

1. 依存関係を確認します。依存関係がある場合、コマンドは終了します。

   これを回避するには、すべての依存言語パッケージを同時にアンインストールするか、最初に依存言語パッケージをアンインストールします。

1. `--backup code`が指定されている場合は、ファイルシステム（`var`および`pub/static` ディレクトリを除く）を`var/backups/<timestamp>_filesystem.tgz`にバックアップします
1. `composer remove`を使用して、コードベースから言語パッケージ ファイルを削除します。
1. キャッシュをクリーニングします。

例えば、別の言語パッケージが依存する言語パッケージをアンインストールしようとすると、次のメッセージが表示されます。

```text
Cannot uninstall vendorname/language-en_us because the following package(s) depend on it:
      vendorname/language-en_gb
```

もう1つの方法は、コードベースをバックアップした後に両方の言語パッケージをアンインストールすることです。

```shell
bin/magento i18n:uninstall vendorname/language-en_us vendorname/language-en_gb --backup-code
```

次のようなメッセージが表示されます。

```text
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
