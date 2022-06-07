---
title: '"[!DNL Upgrade Compatibility Tool] 要件"'
description: 'システムが、 [!DNL Upgrade Compatibility Tool] ( Adobe Commerceプロジェクトのコマンドラインインターフェイス ) を使用します。 '
source-git-commit: 7ec999f9122eb0707ac6c37b7b49f9c423945318
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 0%

---


# Adobe Commerceアクセスキー

{{commerce-only}}

必ず [Adobe Commerceアクセスキー](https://devdocs.magento.com/marketplace/sellers/profile-information.html#access-keys) をダウンロードして使用するには、以下を実行します。 [!DNL Upgrade Compatibility Tool]. Adobe Commerceアクセスキーを `auth.json` 次の場所にあるファイル `~/.composer` デフォルトでは。

>[!NOTE]
>
>以下を確認します。 **COMPOSER_HOME** 環境変数を使用して、どこに `auth.json` ファイルが見つかりました。

この **公開鍵** は、 _ユーザー名_ 一方で **秘密鍵** が _パスワード_:

## Adobe Commerceアクセスキーの例

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
> を正しく設定していない場合、 **Adobe Commerceアクセスキー**&#x200B;を使用している場合、 [!DNL Upgrade Compatibility Tool] そして `composer create-project` コマンドが失敗します。

実行 `composer install` をターミナルに追加して、依存関係をインストールします。

## 必要システム構成

を使用するための最小要件 [!DNL Upgrade Compatibility Tool] コマンドラインインターフェイスでは、次の操作を行います。

| **要件** | **制約** |
|----------------|-----------------|
| PHP バージョン | >= 7.3 |
| コンポーザー | 不明な要件はありません。 |
| Node.js | Node.js のバージョン `^12.22.0`, `^14.17.0`または `>=16.0.0` ( [Node.js のインストール](https://nodejs.dev/learn/how-to-install-nodejs)) |
| メモリ制限 | 2GB 以上の RAM。 |

Adobe Commerceは Linux オペレーティングシステムでのみサポートされています。 次を実行できます。 [!DNL Upgrade Compatibility Tool] （Linux OS の場合） を実行する必要はありません。 [!DNL Upgrade Compatibility Tool] Adobe Commerceインスタンスの場所

～に必要だ [!DNL Upgrade Compatibility Tool] Adobe Commerceインスタンスのソースコードにアクセスできるようにする。 例えば、あるサーバーにインストールし、別のサーバー上のAdobe Commerceインストール場所を示すことができます。

を実行している場合、 [!DNL Upgrade Compatibility Tool] 大きなモジュールやファイルを含むAdobe Commerceインスタンスに対しては、大量の RAM（少なくとも 2GB）が必要になる場合があります。
