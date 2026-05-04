---
title: ' [!DNL Data Migration Tool]をインストール'
description: Magento 1とMagento 2間でデータを転送する [!DNL Data Migration Tool] をインストールする方法について説明します。
exl-id: 5f57067b-3ce8-4b51-b9ae-f60ae089c4ba
topic: Commerce, Migration
feature: Configuration, Install
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# [!DNL Data Migration Tool]をインストール

>[!INFO]
>
>Magentoと[!DNL Data Migration Tool]のバージョンは一致する必要があります。


Magento 2と[!DNL Data Migration Tool]の両方で&#x200B;*同じリリースバージョン*&#x200B;を使用していることを確認してください。 例えば、Magento バージョン 2.2.0の場合、[!DNL Data Migration Tool] バージョン 2.2.0も使用する必要があります。

## バージョンを確認

お使いのMagentoのバージョンを確認するには、次のいずれかの方法を使用します。

- [Composer](#composer-metapackage)
- [GitHub リポジトリ](#github-repository)

### Composer メタパッケージ

Composer メタパッケージを使用してMagento ソフトウェアをダウンロードした場合は、次のコマンドを入力します。

```shell
php <magento_root>/bin/magento --version
```

### GitHub リポジトリ

Magento 2 GitHub リポジトリをクローンした場合は、次のコマンドを入力します。

```shell
cd <your Magento 2 clone directory>
```

```shell
git branch
```

現在`develop` ブランチにいる場合は、続行する前に[&#x200B; リリースブランチ &#x200B;](https://developer.adobe.com/commerce/contributor/guides/install/change-version)に変更する必要があります。

Adobe Commerce ソフトウェアをまだインストールしていない場合は、[今すぐインストールしてください](../../installation/prerequisites/commerce.md)。
GitHub リポジトリをクローンする場合は、[&#x200B; （Contributor）の説明に従ってリリースタグをチェックアウトし、GitHub リポジトリをクローンしてください](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository)。

## [!DNL Data Migration Tool]のリリース済みバージョンを検索

[!DNL Data Migration Tool] GitHub リポジトリの[&#x200B; リリース &#x200B;](https://github.com/magento/data-migration-tool/releases) ページに移動して、使用可能なリリース済みバージョンを確認します。

## [!DNL Data Migration Tool]をインストール

[!DNL Data Migration Tool]は次の場所からインストールできます。

- [`repo.magento.com`](#install-from-repomagentocom)
- [GitHub](#install-from-github)

インストールする前に、次のことを確認してください。

- [前提条件](prerequisites.md) セクションに記載されているすべてのタスクを完了しました
- [Magento 2 ソフトウェアのバージョン &#x200B;](install.md#check-your-version)を確認しました

### `repo.magento.com`からインストール

[!DNL Data Migration Tool]をインストールするには、Magento ルート インストール ディレクトリの`composer.json`を更新して、[!DNL Data Migration Tool] パッケージの場所を指定する必要があります。

1. [&#x200B; ファイルシステム所有者](../../installation/prerequisites/file-system/overview.md)としてアプリケーションサーバーにログインするか、切り替えます。
1. アプリケーションのルートディレクトリに移動します。
1. 次のコマンドを入力します。

   ```shell
   composer config repositories.magento composer https://repo.magento.com
   ```

   ```shell
   composer require magento/data-migration-tool:<version>
   ```

   ここで、`<version>`はMagento 2 コードベースのバージョンと一致する必要があります。

   例えば、バージョン 2.2.0の場合、次のように入力します。

   ```shell
   composer config repositories.magento composer https://repo.magento.com
   ```

   ```shell
   composer require magento/data-migration-tool:2.2.0
   ```

1. プロンプトが表示されたら、[認証キー](../../installation/prerequisites/authentication-keys.md)を入力します。 公開鍵はユーザー名、秘密鍵はパスワードです。

### GitHubからインストール

GitHub リポジトリをクローンした場合は、次の手順に従って[!DNL Data Migration Tool]をインストールします。

1. [&#x200B; ファイルシステム所有者](../../installation/prerequisites/file-system/overview.md)としてアプリケーションサーバーにログインするか、切り替えます。
1. アプリケーションのルートディレクトリに移動します。
1. 次のコマンドを入力します。

   ```shell
   composer config repositories.data-migration-tool git https://github.com/magento/data-migration-tool
   ```

   ```shell
   composer require magento/data-migration-tool:<version>
   ```

   ここで、`<version>`はMagento 2 コードベースのバージョンと一致する必要があります。

   例えば、バージョン 2.2.0の場合、次のように入力します。

   ```shell
   composer config repositories.data-migration-tool git https://github.com/magento/data-migration-tool
   ```

   ```shell
   composer require magento/data-migration-tool:2.2.0
   ```

### インストール済み[!DNL Data Migration Tool]のバージョンを確認してください

1. [!DNL Data Migration Tool] ディレクトリ `<vendor>/magento/data-migration-tool`に変更します。

1. [`composer.json`](https://github.com/magento/data-migration-tool/blob/2.4/composer.json)をテキストエディターで開きます。

1. このファイルの`version` エントリは[!DNL Data Migration Tool]のバージョンです。
