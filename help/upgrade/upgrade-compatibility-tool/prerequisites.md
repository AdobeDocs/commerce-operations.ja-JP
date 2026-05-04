---
title: '[!DNL Upgrade Compatibility Tool]要件'
description: Adobe Commerce プロジェクトのコマンドラインインターフェイスで [!DNL Upgrade Compatibility Tool] を実行するために必要な要件を満たしていることを確認します。
exl-id: b8af2e07-3d28-4937-bb88-b0a1c88a2938
source-git-commit: f9a135fc63574ccbecd3f564a87fc5c4ac03f009
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 0%

---

# Adobe Commerce アクセスキー

{{commerce-only}}

[!DNL Upgrade Compatibility Tool]をダウンロードして使用するには、[Adobe Commerce アクセス キー](https://developer.adobe.com/commerce/marketplace/guides/sellers/profile-information#access-keys)が必要です。 Adobe Commerce アクセスキーを`auth.json` ファイルに追加します。このファイルはデフォルトで`~/.composer`に配置されています。

>[!NOTE]
>
>**COMPOSER_HOME**&#x200B;環境変数を確認して、`auth.json` ファイルの場所を確認します。

**公開鍵**&#x200B;は&#x200B;_ユーザー名_&#x200B;に対応していますが、**秘密鍵**&#x200B;は&#x200B;_パスワード_&#x200B;です。

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
> **Adobe Commerce アクセスキー**&#x200B;を正しく設定しないと、[!DNL Upgrade Compatibility Tool]をダウンロードできず、`composer create-project` コマンドが失敗します。

ターミナルで`composer install`を実行して、依存関係をインストールします。

## 必要システム構成

コマンドライン インターフェイスで[!DNL Upgrade Compatibility Tool]を使用するための最小要件は次のとおりです。

| **要件** | **制約** |
|----------------|-----------------|
| PHP バージョン | >= 7.3 |
| Composer | 既知の要件はありません。 |
| Node.js | Node.js バージョン `^12.22.0`、`^14.17.0`または`>=16.0.0` （[Node.jsのインストール ](https://nodejs.org/en/download)を参照） |
| メモリの制限 | 2GB以上のRAM。 |

[!DNL Upgrade Compatibility Tool]では、実行に[PCNTL](https://www.php.net/manual/en/book.pcntl.php)およびその他のPHP拡張機能が必要です。 `composer check-platform-reqs` コマンドを使用して、必要なPHP拡張機能を確認します。

```shell
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

Adobe Commerceは、Linux オペレーティングシステムでのみサポートされています。 Linux OSで[!DNL Upgrade Compatibility Tool]を実行できます。 Adobe Commerce インスタンスがある[!DNL Upgrade Compatibility Tool]を実行する必要はありません。

[!DNL Upgrade Compatibility Tool]がAdobe Commerce インスタンスのソースコードにアクセスする必要があります。 例えば、あるサーバーにインストールし、別のサーバーのAdobe Commerce インストールに指定できます。

大きなモジュールとファイルを含むAdobe Commerce インスタンスに対して[!DNL Upgrade Compatibility Tool]を実行する場合、このツールには大量のRAM （少なくとも2 GB）が必要になる場合があります。

[Adobe Commerceの[[!DNL Site-Wide Analysis Tool]](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/use-upgrade-compatibility-tool/integrate-analysis-tool.html)から[!DNL Upgrade Compatibility Tool]をクラウドインフラストラクチャ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html){target=_blank} プロジェクトで実行します。
