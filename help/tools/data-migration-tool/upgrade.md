---
title: のアップグレード [!DNL Data Migration Tool]
description: をアップグレードする方法を説明します。 [!DNL Data Migration Tool] Magento1 とMagento2 の間でデータを転送する。
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 0%

---


# のアップグレード [!DNL Data Migration Tool]

現在のMagento2 のインストールと [!DNL Data Migration Tool] 正確に一致する場合は、ツールをアップグレードする必要があります。

## 前提条件

をアップグレードする前に [!DNL Data Migration Tool]を使用する場合は、次の操作を行う必要があります。

* Magentoソフトウェアをアップグレードして最新バージョンを入手する

* バックアップ `vendor/magento/data-migration-tool` directory

* 必ず [!DNL Data Migration Tool] バージョンがMagentoのバージョン

### Magentoソフトウェアのアップグレード

まだおこなっていない場合は、 [Magento・ソフトウェアのアップグレード](../../upgrade/overview.md).

### バックアップ `vendor/magento/data-migration-tool` directory

をアップグレードする前に、 [!DNL Data Migration Tool]、少なくとも `vendor/magento/data-migration-tool` ディレクトリ。 アップグレード中に削除され、更新されたコードに置き換えられる可能性があります。

次のコマンドを使用して、Magento・コード・ベースとデータベース全体をバックアップすることもできます。

```bash
php <magento_root>/bin/magento setup:backup --code --db
```

>[!WARNING]
>
>この `vendor/magento/data-migration-tool` ディレクトリにはカスタムコードが含まれます。 バックアップに失敗した場合、アップグレード中にカスタマイズ内容が失われる可能性があります。


### バージョンが一致していることを確認します。

のバージョン。 [!DNL Data Migration Tool] そして、Magentoソフトウェアが正確に一致する必要があります。 例えば、Magento2.1.2 では、 [!DNL Data Migration Tool].

詳しくは、 [インストール [!DNL Data Migration Tool]](install.md) トピックを参照してください。

* [チェック](install.md#check-your-version) Magento2 のバージョン

* [検索](install.md#find-released-versions-of-data-migration-tool) リリースされたバージョンの [!DNL Data Migration Tool]

* [チェック](install.md#check-version-of-installed-data-migration-tool) の [!DNL Data Migration Tool] version

## のアップグレード [!DNL Data Migration Tool]

1. アプリケーションサーバーにとしてログインするか、に切り替えます。 [ファイルシステムの所有者](../../installation/prerequisites/file-system/overview.md).
1. アプリケーションのルートディレクトリに移動します。
1. 次のコマンドを入力します。

   ```bash
   composer require magento/data-migration-tool:<version>
   ```

   場所 `<version>` は、Magento2 のコードベースのバージョンと一致する必要があります。

   例えば、バージョン 2.1.2 の場合は、次のように入力します。

   ```bash
   composer require magento/data-migration-tool:2.1.2
   ```

1. コマンドが完了するまで待ちます。
