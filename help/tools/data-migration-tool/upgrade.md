---
title: ' [!DNL Data Migration Tool]をアップグレード'
description: Magento 1とMagento 2間でデータを転送するために [!DNL Data Migration Tool] をアップグレードする方法について説明します。
exl-id: c0d56d1d-b15b-437f-be72-74282dbe85c1
topic: Commerce, Migration
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 0%

---

# [!DNL Data Migration Tool]をアップグレード

現在のMagento 2 インストールと[!DNL Data Migration Tool]のバージョンが正確に一致することを確認するには、ツールをアップグレードする必要がある場合があります。

## 前提条件

[!DNL Data Migration Tool]をアップグレードする前に、次の操作を行う必要があります。

* Magento ソフトウェアをアップグレードして最新バージョンを入手する

* `vendor/magento/data-migration-tool` ディレクトリのバックアップ

* [!DNL Data Migration Tool] バージョンがMagento アプリケーションのバージョンと一致していることを確認してください

### Magento ソフトウェアのアップグレード

まだアップグレードしていない場合は、[Magento ソフトウェアをアップグレードしてください](../../upgrade/overview.md)。

### `vendor/magento/data-migration-tool` ディレクトリのバックアップ

[!DNL Data Migration Tool]をアップグレードする前に、少なくとも`vendor/magento/data-migration-tool` ディレクトリをバックアップしてください。 アップグレード中に、更新されたコードで削除および置き換えられる可能性があります。

次のコマンドを使用して、Magento コードベースとデータベース全体をバックアップすることもできます。

```shell
php <magento_root>/bin/magento setup:backup --code --db
```

>[!WARNING]
>
>`vendor/magento/data-migration-tool` ディレクトリにカスタムコードが含まれています。 バックアップに失敗すると、アップグレード中にカスタマイズが失われる可能性があります。


### バージョンが一致することを確認します

[!DNL Data Migration Tool]とMagento ソフトウェアのバージョンは正確に一致する必要があります。 例えば、Magento 2.1.2では、[!DNL Data Migration Tool]のバージョン 2.1.2が必要です。

[Install [!DNL Data Migration Tool]](install.md) トピックを参照して、以下の方法を確認してください。

* Magento 2のバージョンを[確認](install.md#check-your-version)してください

* [Find](install.md#find-released-versions-of-data-migration-tool)がリリースした[!DNL Data Migration Tool]のバージョン

* [!DNL Data Migration Tool] バージョンを[ チェック ](install.md#check-version-of-installed-data-migration-tool)

## [!DNL Data Migration Tool]をアップグレード

1. アプリケーションサーバーに[ ファイルシステム所有者](../../installation/prerequisites/file-system/overview.md)としてログインするか、切り替えます。
1. アプリケーションのルートディレクトリに移動します。
1. 次のコマンドを入力します。

   ```shell
   composer require magento/data-migration-tool:<version>
   ```

   ここで、`<version>`はMagento 2 コードベースのバージョンと一致する必要があります。

   例えば、バージョン 2.1.2の場合、次のように入力します。

   ```shell
   composer require magento/data-migration-tool:2.1.2
   ```

1. コマンドが完了するまでお待ちください。
