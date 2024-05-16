---
title: をアップグレード [!DNL Data Migration Tool]
description: をアップグレードする方法を説明します [!DNL Data Migration Tool] Magento1 とMagento2 との間でデータを転送する。
exl-id: c0d56d1d-b15b-437f-be72-74282dbe85c1
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 0%

---

# をアップグレード [!DNL Data Migration Tool]

現在のMagento2 のインストール環境のバージョンおよび [!DNL Data Migration Tool] 完全に一致する場合は、ツールをアップグレードする必要があります。

## 前提条件

アップグレードの前に [!DNL Data Migration Tool]は、以下を行う必要があります。

* 最新バージョンを入手するには、Magentoソフトウェアをアップグレードしてください

* をバックアップ `vendor/magento/data-migration-tool` directory

* 次のことを確認します [!DNL Data Migration Tool] version はMagentoアプリケーションのバージョンと一致します

### Magentoソフトウェアのアップグレード

まだ行っていない場合は、 [Magentoソフトウェアのアップグレード](../../upgrade/overview.md).

### をバックアップ `vendor/magento/data-migration-tool` directory

アップグレードの前に [!DNL Data Migration Tool]、少なくとも `vendor/magento/data-migration-tool` ディレクトリ。 アップグレード中に、削除して更新されたコードに置き換えることができます。

次のコマンドを使用して、Magentoコードベース全体とデータベース全体をバックアップすることもできます。

```bash
php <magento_root>/bin/magento setup:backup --code --db
```

>[!WARNING]
>
>この `vendor/magento/data-migration-tool` ディレクトリには、カスタムコードが含まれています。 バックアップしないと、アップグレード中にカスタマイズが失われる可能性があります。


### バージョンが一致することの確認

のバージョン [!DNL Data Migration Tool] とMagentoソフトウェアは完全に一致する必要があります。 例えば、Magento 2.1.2 にはバージョン 2.1.2 の [!DNL Data Migration Tool].

を参照してください。 [インストール [!DNL Data Migration Tool]](install.md) 次の方法を理解しておくトピックです。

* [チェック](install.md#check-your-version) お使いのMagento 2 バージョン

* [検索](install.md#find-released-versions-of-data-migration-tool) のリリース版 [!DNL Data Migration Tool]

* [チェック](install.md#check-version-of-installed-data-migration-tool) この [!DNL Data Migration Tool] version

## をアップグレード [!DNL Data Migration Tool]

1. アプリケーションサーバーにとしてログインするか、に切り替えます。 [ファイルシステム所有者](../../installation/prerequisites/file-system/overview.md).
1. アプリケーションのルートディレクトリに移動します。
1. 次のコマンドを入力します。

   ```bash
   composer require magento/data-migration-tool:<version>
   ```

   ここで、 `<version>` Magento 2 コードベースのバージョンと一致する必要があります。

   例えば、バージョン 2.1.2 の場合は、次のように入力します。

   ```bash
   composer require magento/data-migration-tool:2.1.2
   ```

1. コマンドが完了するまで待ちます。
