---
title: ' [!DNL Data Migration Tool] のインストール'
description: Magento 1 とMagento 2 間でデータを転送する  [!DNL Data Migration Tool]  をインストールする方法を説明します。
exl-id: 5f57067b-3ce8-4b51-b9ae-f60ae089c4ba
topic: Commerce, Migration
feature: Configuration, Install
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# [!DNL Data Migration Tool] のインストール

>[!INFO]
>
>Magentoと [!DNL Data Migration Tool] のバージョンが一致している必要があります。


Magento 2 と [!DNL Data Migration Tool] の両方で *同じリリース版* を使用していることを確認してください。 例えば、Magentoバージョン 2.2.0 の場合、[!DNL Data Migration Tool] バージョン 2.2.0 も使用する必要があります。

## バージョンを確認

Magentoのバージョンを確認するには、次のいずれかの方法を使用します。

- [コンポーザー](#composer-metapackage)
- [GitHub リポジトリ](#github-repository)

### Composer メタパッケージ

Composer メタパッケージを使用してMagento ソフトウェアをダウンロードした場合は、次のコマンドを入力します。

```bash
php <magento_root>/bin/magento --version
```

### GitHub リポジトリ

Magento 2 GitHub リポジトリのクローンを作成した場合は、次のコマンドを入力します。

```bash
cd <your Magento 2 clone directory>
```

```bash
git branch
```

現在 `develop` ブランチにいる場合は、続行する前に [ リリース済みのブランチ ](https://developer.adobe.com/commerce/contributor/guides/install/change-version/) に変更する必要があります。

Adobe Commerce ソフトウェアをまだインストールしていない場合は、[ 今すぐインストール ](../../installation/prerequisites/commerce.md) してください。
GitHub リポジトリをクローンする場合は、[ （Contributor） GitHub リポジトリのクローン ](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/) で説明されているように、リリースタグをチェックアウトしてください。

## [!DNL Data Migration Tool] のリリース済みバージョンの検索

[!DNL Data Migration Tool] GitHub リポジトリの [ リリース ](https://github.com/magento/data-migration-tool/releases) ページに移動して、使用可能なリリース済みバージョンを見つけます。

## [!DNL Data Migration Tool] のインストール

[!DNL Data Migration Tool] は次の場所からインストールできます。

- [『 repo.magento.com 』](#install-from-repomagentocom)
- [GitHub](#install-from-github)

インストールする前に、次のことを確認します。

- [ 前提条件 ](prerequisites.md) セクションに記載されているすべてのタスクを完了しました
- Magento2 ソフトウェアの [ バージョンの確認 ](install.md#check-your-version)

### `repo.magento.com` からのインストール

[!DNL Data Migration Tool] をインストールするには、Magentoルートインストールディレクトリの `composer.json` を更新して、[!DNL Data Migration Tool] パッケージの場所を指定する必要があります。

1. [ ファイルシステムの所有者 ](../../installation/prerequisites/file-system/overview.md) としてアプリケーションサーバーにログインするか、に切り替えます。
1. アプリケーションのルートディレクトリに移動します。
1. 次のコマンドを入力します。

   ```bash
   composer config repositories.magento composer https://repo.magento.com
   ```

   ```bash
   composer require magento/data-migration-tool:<version>
   ```

   `<version>` は、Magento 2 コードベースのバージョンと一致する必要があります。

   例えば、バージョン 2.2.0 の場合は、次のように入力します。

   ```bash
   composer config repositories.magento composer https://repo.magento.com
   ```

   ```bash
   composer require magento/data-migration-tool:2.2.0
   ```

1. プロンプトが表示されたら、[ 認証キー ](../../installation/prerequisites/authentication-keys.md) を入力します。 公開鍵はユーザー名で、秘密鍵はパスワードです。

### GitHub からのインストール

GitHub リポジトリのクローンを作成した場合は、次の手順に従って [!DNL Data Migration Tool] をインストールします。

1. [ ファイルシステムの所有者 ](../../installation/prerequisites/file-system/overview.md) としてアプリケーションサーバーにログインするか、に切り替えます。
1. アプリケーションのルートディレクトリに移動します。
1. 次のコマンドを入力します。

   ```bash
   composer config repositories.data-migration-tool git https://github.com/magento/data-migration-tool
   ```

   ```bash
   composer require magento/data-migration-tool:<version>
   ```

   `<version>` は、Magento 2 コードベースのバージョンと一致する必要があります。

   例えば、バージョン 2.2.0 の場合は、次のように入力します。

   ```bash
   composer config repositories.data-migration-tool git https://github.com/magento/data-migration-tool
   ```

   ```bash
   composer require magento/data-migration-tool:2.2.0
   ```

### インストールされている [!DNL Data Migration Tool] のバージョンを確認

1. [!DNL Data Migration Tool] ディレクトリに移動します：`<vendor>/magento/data-migration-tool`。

1. [`composer.json`](https://github.com/magento/data-migration-tool/blob/2.4/composer.json) をテキストエディターで開きます。

1. そのファイルの `version` のエントリは、[!DNL Data Migration Tool] のバージョンです。
