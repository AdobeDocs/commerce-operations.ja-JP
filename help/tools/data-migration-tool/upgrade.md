---
title: をアップグレードする  [!DNL Data Migration Tool]
description: Magento 1 とMagento 2 の間でデータを転送する  [!DNL Data Migration Tool]  うにアップグレードする方法について説明します。
exl-id: c0d56d1d-b15b-437f-be72-74282dbe85c1
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 0%

---

# [!DNL Data Migration Tool] のアップグレード

現在インストールされているMagento 2 と [!DNL Data Migration Tool] のバージョンを正確に一致させるには、ツールをアップグレードする必要があります。

## 前提条件

[!DNL Data Migration Tool] をアップグレードする前に、次の操作を行う必要があります。

* 最新バージョンを入手するには、Magentoソフトウェアをアップグレードしてください

* `vendor/magento/data-migration-tool` ディレクトリのバックアップ

* [!DNL Data Migration Tool] のバージョンがMagentoアプリケーションのバージョンと一致していることを確認します

### Magentoソフトウェアのアップグレード

まだ行っていない場合は、[Magentoソフトウェアをアップグレード ](../../upgrade/overview.md) します。

### `vendor/magento/data-migration-tool` ディレクトリのバックアップ

[!DNL Data Migration Tool] をアップグレードする前に、少なくとも `vendor/magento/data-migration-tool` ディレクトリをバックアップしてください。 アップグレード中に、削除して更新されたコードに置き換えることができます。

次のコマンドを使用して、Magentoコードベース全体とデータベース全体をバックアップすることもできます。

```bash
php <magento_root>/bin/magento setup:backup --code --db
```

>[!WARNING]
>
>`vendor/magento/data-migration-tool` ディレクトリには、カスタムコードが含まれています。 バックアップしないと、アップグレード中にカスタマイズが失われる可能性があります。


### バージョンが一致することの確認

[!DNL Data Migration Tool] とMagentoソフトウェアのバージョンは完全に一致する必要があります。 例えば、Magento 2.1.2 には [!DNL Data Migration Tool] のバージョン 2.1.2 が必要です。

[ インストール  [!DNL Data Migration Tool]](install.md) のトピックを参照して、次の方法を理解してください。

* [ 確認 ](install.md#check-your-version)Magento 2 のバージョン

* [!DNL Data Migration Tool] のリリース済みバージョンを [ 検索 ](install.md#find-released-versions-of-data-migration-tool) します

* [ チェック ](install.md#check-version-of-installed-data-migration-tool)[!DNL Data Migration Tool] バージョン

## [!DNL Data Migration Tool] のアップグレード

1. アプリケーションサーバーにとしてログインするか、（ファイルシステムの所有者 [ に切り替え ](../../installation/prerequisites/file-system/overview.md) す。
1. アプリケーションのルートディレクトリに移動します。
1. 次のコマンドを入力します。

   ```bash
   composer require magento/data-migration-tool:<version>
   ```

   `<version>` は、Magento 2 コードベースのバージョンと一致する必要があります。

   例えば、バージョン 2.1.2 の場合は、次のように入力します。

   ```bash
   composer require magento/data-migration-tool:2.1.2
   ```

1. コマンドが完了するまで待ちます。
