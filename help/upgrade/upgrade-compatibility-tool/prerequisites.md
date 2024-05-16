---
title: '[!DNL Upgrade Compatibility Tool] 要件'
description: お使いのシステムがを実行するために必要な要件を満たしていることを確認します。 [!DNL Upgrade Compatibility Tool] Adobe Commerce プロジェクトのコマンドラインインターフェイス。
exl-id: b8af2e07-3d28-4937-bb88-b0a1c88a2938
source-git-commit: 40d850add2ef8c51e9192758135768306b163780
workflow-type: tm+mt
source-wordcount: '273'
ht-degree: 0%

---

# Adobe Commerce アクセスキー

{{commerce-only}}

以下が必要です [Adobe Commerce アクセスキー](https://developer.adobe.com/commerce/marketplace/guides/sellers/profile-information/#access-keys) をダウンロードして使用するには [!DNL Upgrade Compatibility Tool]. Adobe Commerce アクセスキーをに追加 `auth.json` ファイル（にあります） `~/.composer` デフォルトでは。

>[!NOTE]
>
>を確認 **COMPOSER_ホーム** 環境変数を使用して、の場所を確認します `auth.json` ファイルの場所はです。

この **公開鍵** 次に対応 _ユーザー名_ それに対して **秘密鍵** が _password_:

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
> を正しく設定していない場合 **Adobe Commerce アクセスキー**&#x200B;をダウンロードすることはできません。 [!DNL Upgrade Compatibility Tool] および `composer create-project` コマンドが失敗します。

実行 `composer install` をターミナルに入力して、依存関係をインストールします。

## 必要システム構成

を使用するための最小要件 [!DNL Upgrade Compatibility Tool] コマンドラインインターフェイスには、次のものがあります。

| **要件** | **制約** |
|----------------|-----------------|
| PHP バージョン | >= 7.3 |
| コンポーザー | 既知の要件はありません。 |
| Node.js | Node.js のバージョン `^12.22.0`, `^14.17.0`、または `>=16.0.0` （を参照） [Node.js のインストール](https://nodejs.org/en/learn/getting-started/how-to-install-nodejs)） |
| メモリの制限 | 2 GB 以上の RAM。 |

[!DNL Upgrade Compatibility Tool] が必要 [PCNTL](https://www.php.net/manual/en/book.pcntl.php) とその他の実行用 PHP 拡張モジュール。 を使用して、必要な PHP 拡張モジュールをチェックします。 `composer check-platform-reqs` コマンド：

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

Adobe Commerceは、Linux オペレーティングシステムでのみサポートされています。 を実行できます [!DNL Upgrade Compatibility Tool] Linux OS の場合。 を実行する必要はありません [!DNL Upgrade Compatibility Tool] Adobe Commerce インスタンスの場所。

以下が必要です [!DNL Upgrade Compatibility Tool] Adobe Commerce インスタンスのソースコードにアクセスできること。 例えば、あるサーバーにインストールして、別のサーバー上のAdobe Commerce インストールで指定することができます。

を実行している場合 [!DNL Upgrade Compatibility Tool] 大きなモジュールとファイルを持つAdobe Commerce インスタンスの場合、ツールに大量の RAM （少なくとも 2 GB）が必要になることがあります。

を実行 [!DNL Upgrade Compatibility Tool] から [[!DNL Site-Wide Analysis Tool]](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/use-upgrade-compatibility-tool/integrate-analysis-tool.html) （用） [クラウドインフラストラクチャー上のAdobe Commerce](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html){target=_blank} プロジェクト。
