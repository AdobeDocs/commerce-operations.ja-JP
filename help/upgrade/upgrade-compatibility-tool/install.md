---
title: をダウンロードします。 [!DNL Upgrade Compatibility Tool]
description: 次の手順に従って、 [!DNL Upgrade Compatibility Tool] Adobe Commerceプロジェクト用
source-git-commit: 5ff08d231269ea0bcb69f8c80aa546b171a5e4a0
workflow-type: tm+mt
source-wordcount: '233'
ht-degree: 0%

---


# のインストール [!DNL Upgrade Compatibility Tool]

{{commerce-only}}

この [!DNL Upgrade Compatibility Tool] は、Adobe Commerceカスタマイズ済みのインスタンスを、そのインスタンスにインストールされているすべてのモジュールを分析することで、特定のバージョンと照合するコマンドラインツールです。 最新バージョンのAdobe Commerceにアップグレードする前に対処する必要があるエラーと警告のリストを返します。

## 前提条件

をインストールするには、以下を実行します。 [!DNL Upgrade Compatibility Tool]を使用する場合は、必要な前提条件をインストールする必要があります。

詳しくは、 [前提条件](../upgrade-compatibility-tool/prerequisites.md) を参照してください。

## をダウンロードします。 [!DNL Upgrade Compatibility Tool]

次の手順で [!DNL Upgrade Compatibility Tool]、次のコマンドを実行します。

```bash
composer create-project magento/upgrade-compatibility-tool uct --repository https://repo.magento.com
```

### Adobe Commerceアクセスキー

必ず [Adobe Commerceアクセスキー](https://devdocs.magento.com/marketplace/sellers/profile-information.html#access-keys) をダウンロードして使用するには、以下を実行します。 [!DNL Upgrade Compatibility Tool]. Adobe Commerceアクセスキーを `auth.json` 次の場所にあるファイル `~/.composer` デフォルトでは。

>[!WARNING]
>
>以下を確認します。 **COMPOSER_HOME** 環境変数を使用して、どこに `auth.json` ファイルが見つかりました。

この **公開鍵** は、 _ユーザー名_ 一方で **秘密鍵** が _パスワード_:

### Adobe Commerceアクセスキーの例

```json
    "http-basic": {
        "repo.magento.com": {
            "username": "YOUR_MAGENTO_PUBLIC_KEY",
            "password": "YOUR_MAGENTO_PRIVATE_KEY"
        }
    },
```

### コンポーザー

をダウンロードします。 [!DNL Upgrade Compatibility Tool] リポジトリと実行 `composer install` をターミナルに追加して、依存関係をインストールします。

>[!WARNING]
>
>この **Adobe Commerceアクセスキー** が正しく設定されていない場合、 [!DNL Upgrade Compatibility Tool] 実行時に `composer create-project` コマンドを実行すると失敗します。

### Node.js

Node.js をインストールするには、Node.js [ドキュメント](https://nodejs.dev/learn/how-to-install-nodejs).

## サードパーティの拡張機能

Adobeでは、拡張機能のベンダーに問い合わせて、最新のリリースバージョンとの互換性が拡張機能に完全にあるかどうかを確認することをお勧めします。

詳しくは、 [ツールを実行](../upgrade-compatibility-tool/run.md) : [!DNL Upgrade Compatibility Tool].
