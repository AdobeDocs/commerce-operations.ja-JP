---
title: '[!DNL Upgrade Compatibility Tool] 要件'
description: Adobe Commerce プロジェクトのコマンドラインインターフェ  [!DNL Upgrade Compatibility Tool]  スでを実行するために必要な要件を満たしていることを確認します。
exl-id: b8af2e07-3d28-4937-bb88-b0a1c88a2938
source-git-commit: 40d850add2ef8c51e9192758135768306b163780
workflow-type: tm+mt
source-wordcount: '273'
ht-degree: 0%

---

# Adobe Commerce アクセスキー

{{commerce-only}}

[!DNL Upgrade Compatibility Tool] をダウンロードして使用するには、[Adobe Commerce アクセスキー ](https://developer.adobe.com/commerce/marketplace/guides/sellers/profile-information/#access-keys) が必要です。 Adobe Commerce アクセスキーを `auth.json` ファイルに追加します。このファイルは、デフォルトで `~/.composer` にあります。

>[!NOTE]
>
>**COMPOSER_HOME** 環境変数をチェックして、`auth.json` ファイルの場所を確認します。

**公開鍵** は _ユーザー名_ に対応し、**秘密鍵** は _パスワード_ に対応します。

## Adobe Commerce アクセスキーの例

```json
    "http-basic": {
        "repo.magento.com": {
            "username": "YOUR_MAGENTO_PUBLIC_KEY",
            "password": "YOUR_MAGENTO_PRIVATE_KEY"
        }
    },
```

>[!NOTE]
>
> **Adobe Commerce アクセスキー** を正しく設定しない場合は、[!DNL Upgrade Compatibility Tool] をダウンロードできず、`composer create-project` コマンドが失敗します。

ターミナルで `composer install` を実行して、依存関係をインストールします。

## 必要システム構成

コマンドラインインターフェイスで [!DNL Upgrade Compatibility Tool] を使用するための最小要件を次に示します。

| **要件** | **制約** |
|----------------|-----------------|
| PHP バージョン | >= 7.3 |
| コンポーザー | 既知の要件はありません。 |
| Node.js | Node.js のバージョン `^12.22.0`、`^14.17.0`、`>=16.0.0` （[Node.js のインストール ](https://nodejs.org/en/learn/getting-started/how-to-install-nodejs) を参照） |
| メモリの制限 | 2 GB 以上の RAM。 |

[!DNL Upgrade Compatibility Tool] を実行するには、[PCNTL](https://www.php.net/manual/en/book.pcntl.php) やその他の PHP 拡張機能が必要です。 次のコマンドを使用して、必要な PHP 拡張機能 `composer check-platform-reqs` 確認します。

```bash
# Example output of `composer check-platform-reqs` command for UCT 2.2.6 and PHP 7.4:

$ composer check-platform-reqs
Checking platform requirements for packages in the vendor dir
ext-ctype     *         success provided by symfony/polyfill-ctype
ext-dom       20031129  success
ext-filter    7.4.30    success
ext-json      7.4.30    success
ext-libxml    7.4.30    success
ext-mbstring  *         success provided by symfony/polyfill-mbstring
ext-openssl   7.4.30    success
ext-pcntl     7.4.30    success
ext-pcre      7.4.30    success
ext-phar      7.4.30    success
ext-simplexml 7.4.30    success
ext-tokenizer 7.4.30    success
ext-xml       7.4.30    success
ext-xmlwriter 7.4.30    success
ext-zip       1.15.6    success
php           7.4.30    success
```

Adobe Commerceは、Linux オペレーティングシステムでのみサポートされています。 Linux OS で [!DNL Upgrade Compatibility Tool] を実行できます。 Adobe Commerce インスタンスがある [!DNL Upgrade Compatibility Tool] を実行する必要はありません。

[!DNL Upgrade Compatibility Tool] がAdobe Commerce インスタンスのソースコードにアクセスできる必要があります。 例えば、あるサーバーにインストールして、別のサーバー上のAdobe Commerce インストールで指定することができます。

大きなモジュールやファイルを含むAdobe Commerce インスタンスに対して [!DNL Upgrade Compatibility Tool] を実行する場合、ツールに大量の RAM （少なくとも 2 GB）が必要になることがあります。

クラウドインフラストラクチャー上の [Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html?lang=ja){target=_blank} プロジェクトの [[!DNL Site-Wide Analysis Tool]](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/use-upgrade-compatibility-tool/integrate-analysis-tool.html?lang=ja) から [!DNL Upgrade Compatibility Tool] を実行します。
