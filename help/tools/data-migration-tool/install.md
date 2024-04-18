---
title: のインストール [!DNL Data Migration Tool]
description: のインストール方法を説明します [!DNL Data Migration Tool] Magento1 とMagento2 との間でデータを転送する。
exl-id: 5f57067b-3ce8-4b51-b9ae-f60ae089c4ba
topic: Commerce, Migration
feature: Configuration, Install
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# のインストール [!DNL Data Migration Tool]

>[!INFO]
>
>Magentoおよびのバージョン [!DNL Data Migration Tool] は一致する必要があります。


を使用していることを確認します *同じリリース版* （Magento 2 と両方） [!DNL Data Migration Tool]. 例えば、Magentoバージョン 2.2.0 の場合、も使用する必要があります。 [!DNL Data Migration Tool] バージョン 2.2.0。

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

現在のメンバーの場合 `develop` 分岐。に変更する必要があります。 [リリースされたブランチ](https://developer.adobe.com/commerce/contributor/guides/install/change-version/) 先に進む前に。

Adobe Commerce ソフトウェアをまだインストールしていない場合は、 [今すぐインストール](../../installation/prerequisites/commerce.md).
GitHub リポジトリをクローンする場合は、の説明に従って、必ずリリースタグをチェックアウトしてください。 [（投稿者） GitHub リポジトリのクローン](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/).

## のリリース済みバージョンの検索 [!DNL Data Migration Tool]

に移動します [リリース](https://github.com/magento/data-migration-tool/releases) のページ [!DNL Data Migration Tool] 利用可能なリリースバージョンを検索するための GitHub リポジトリ。

## のインストール [!DNL Data Migration Tool]

をインストールできます [!DNL Data Migration Tool] コピー元：

- [『 repo.magento.com 』](#install-from-repomagentocom)
- [GitHub](#install-from-github)

インストールする前に、次のことを確認します。

- に記載されているすべてのタスクを完了しました [前提条件](prerequisites.md) セクション
- [バージョンを確認。](install.md#check-your-version) （Magento2 ソフトウェア）

### インストール元 `repo.magento.com`

をインストールするには [!DNL Data Migration Tool]を更新する必要があります `composer.json` Magentoのルートインストールディレクトリでを指定します。 [!DNL Data Migration Tool] パッケージ。

1. アプリケーションサーバーにとしてログインするか、 [ファイルシステム所有者](../../installation/prerequisites/file-system/overview.md).
1. アプリケーションのルートディレクトリに移動します。
1. 次のコマンドを入力します。

   ```bash
   composer config repositories.magento composer https://repo.magento.com
   ```

   ```bash
   composer require magento/data-migration-tool:<version>
   ```

   ここで、 `<version>` Magento 2 コードベースのバージョンと一致する必要があります。

   例えば、バージョン 2.2.0 の場合は、次のように入力します。

   ```bash
   composer config repositories.magento composer https://repo.magento.com
   ```

   ```bash
   composer require magento/data-migration-tool:2.2.0
   ```

1. プロンプトが表示されたら、 [認証キー](../../installation/prerequisites/authentication-keys.md). 公開鍵はユーザー名で、秘密鍵はパスワードです。

### GitHub からのインストール

GitHub リポジトリのクローンを作成した場合は、次の手順に従ってインストールします [!DNL Data Migration Tool].

1. アプリケーションサーバーにとしてログインするか、 [ファイルシステム所有者](../../installation/prerequisites/file-system/overview.md).
1. アプリケーションのルートディレクトリに移動します。
1. 次のコマンドを入力します。

   ```bash
   composer config repositories.data-migration-tool git https://github.com/magento/data-migration-tool
   ```

   ```bash
   composer require magento/data-migration-tool:<version>
   ```

   ここで、 `<version>` Magento 2 コードベースのバージョンと一致する必要があります。

   例えば、バージョン 2.2.0 の場合は、次のように入力します。

   ```bash
   composer config repositories.data-migration-tool git https://github.com/magento/data-migration-tool
   ```

   ```bash
   composer require magento/data-migration-tool:2.2.0
   ```

### インストールされているのバージョンを確認 [!DNL Data Migration Tool]

1. をに変更します。 [!DNL Data Migration Tool] ディレクトリ： `<vendor>/magento/data-migration-tool`.

1. 開く [`composer.json`](https://github.com/magento/data-migration-tool/blob/2.4/composer.json) テキストエディター。

1. この `version` そのファイルのエントリは、のバージョンです。 [!DNL Data Migration Tool].
