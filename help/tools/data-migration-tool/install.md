---
title: をインストールします。 [!DNL Data Migration Tool]
description: をインストールする方法を説明します。 [!DNL Data Migration Tool] Magento1 とMagento2 の間でデータを転送する。
exl-id: 5f57067b-3ce8-4b51-b9ae-f60ae089c4ba
topic: Commerce, Migration
feature: Configuration, Install
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# をインストールします。 [!DNL Data Migration Tool]

>[!INFO]
>
>Magentoと [!DNL Data Migration Tool] は、に一致する必要があります。


次を使用していることを確認します。 *同じリリース版* Magento2 と [!DNL Data Migration Tool]. 例えば、Magentoバージョン 2.2.0 の場合、 [!DNL Data Migration Tool] バージョン 2.2.0.

## バージョンを確認

次のメソッドのいずれかを使用して、バージョンのMagentoを検証します。

- [コンポーザー](#composer-metapackage)
- [GitHub リポジトリ](#github-repository)

### Composer メタパッケージ

Composer のメタパッケージを使用してMagentoソフトウェアをダウンロードした場合は、次のコマンドを入力します。

```bash
php <magento_root>/bin/magento --version
```

### GitHub リポジトリ

Magento2 GitHub リポジトリを複製した場合は、次のコマンドを入力します。

```bash
cd <your Magento 2 clone directory>
```

```bash
git branch
```

現在、 `develop` ブランチの場合は、 [解放枝](https://developer.adobe.com/commerce/contributor/guides/install/change-version/) 続行する前に

Adobe CommerceまたはMagento Open Sourceソフトウェアをまだインストールしていない場合は、 [今すぐインストール](../../installation/prerequisites/commerce.md).
GitHub リポジトリのクローンを作成する場合は、リリースタグを確認してください。詳しくは、 [(Contributor)GitHub リポジトリのクローン](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/).

## のリリースバージョンの検索 [!DNL Data Migration Tool]

次に移動： [リリース](https://github.com/magento/data-migration-tool/releases) ページ [!DNL Data Migration Tool] GitHub リポジトリを使用して、リリースされた利用可能なバージョンを見つけます。

## をインストールします。 [!DNL Data Migration Tool]

以下をインストールしてください： [!DNL Data Migration Tool] 送信元：

- [&#39;repo.magento.com&#39;](#install-from-repomagentocom)
- [GitHub](#install-from-github)

インストールする前に、以下を確認してください。

- 「 [前提条件](prerequisites.md) セクション
- [バージョンを検証済み](install.md#check-your-version) Magento2 ソフトウェアの

### インストール元 `repo.magento.com`

をインストールするには、以下を実行します。 [!DNL Data Migration Tool]を更新する必要があります。 `composer.json` をMagentoのルートインストールディレクトリに追加し、 [!DNL Data Migration Tool] パッケージ。

1. アプリケーションサーバーに、 [ファイルシステム所有者](../../installation/prerequisites/file-system/overview.md).
1. アプリケーションのルートディレクトリに移動します。
1. 次のコマンドを入力します。

   ```bash
   composer config repositories.magento composer https://repo.magento.com
   ```

   ```bash
   composer require magento/data-migration-tool:<version>
   ```

   ここで、 `<version>` は、Magento2 のコードベースのバージョンと一致する必要があります。

   例えば、バージョン 2.2.0 の場合は、次のように入力します。

   ```bash
   composer config repositories.magento composer https://repo.magento.com
   ```

   ```bash
   composer require magento/data-migration-tool:2.2.0
   ```

1. プロンプトが表示されたら、 [認証キー](../../installation/prerequisites/authentication-keys.md). 公開鍵はユーザー名、秘密鍵はパスワードです。

### GitHub からのインストール

GitHub リポジトリのクローンを作成した場合は、次の手順に従って、 [!DNL Data Migration Tool].

1. アプリケーションサーバーに、 [ファイルシステム所有者](../../installation/prerequisites/file-system/overview.md).
1. アプリケーションのルートディレクトリに移動します。
1. 次のコマンドを入力します。

   ```bash
   composer config repositories.data-migration-tool git https://github.com/magento/data-migration-tool
   ```

   ```bash
   composer require magento/data-migration-tool:<version>
   ```

   場所 `<version>` は、Magento2 のコードベースのバージョンと一致する必要があります。

   例えば、バージョン 2.2.0 の場合は、次のように入力します。

   ```bash
   composer config repositories.data-migration-tool git https://github.com/magento/data-migration-tool
   ```

   ```bash
   composer require magento/data-migration-tool:2.2.0
   ```

### インストールされているのバージョンを確認する [!DNL Data Migration Tool]

1. を [!DNL Data Migration Tool] ディレクトリ： `<vendor>/magento/data-migration-tool`.

1. 開く [`composer.json`](https://github.com/magento/data-migration-tool/blob/2.4/composer.json) をクリックします。

1. The `version` そのファイルのエントリは、 [!DNL Data Migration Tool].
