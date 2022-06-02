---
title: '"[!DNL Upgrade Compatibility Tool] 要件"'
description: 'システムが、 [!DNL Upgrade Compatibility Tool] Adobe Commerceプロジェクト用 '
source-git-commit: e539824b336978debd6e6adc538cd8bad367eff1
workflow-type: tm+mt
source-wordcount: '276'
ht-degree: 0%

---


# 必要システム構成

{{commerce-only}}

を使用するための最小要件 [!DNL Upgrade Compatibility Tool] 次の場合：

| **要件** | **制約** |
|----------------|-----------------|
| PHP バージョン | >= 7.3 |
| コンポーザー | 不明な要件 |
| Node.js | [Node.js](https://nodejs.org/) (`^12.22.0`, `^14.17.0`または `>=16.0.0`) |
| メモリ制限 | 2GB 以上の RAM |

次を実行できます。 [!DNL Upgrade Compatibility Tool] （Windows はサポートされていません）。 を実行する必要はありません。 [!DNL Upgrade Compatibility Tool] Adobe Commerceインスタンスの場所

～に必要だ [!DNL Upgrade Compatibility Tool] Adobe Commerceインスタンスのソースコードにアクセスできるようにする。 例えば、あるサーバーにインストールし、別のサーバー上のAdobe Commerceインストール場所を示すことができます。

を実行している場合、 [!DNL Upgrade Compatibility Tool] 大きなモジュールやファイルを含むAdobe Commerceインスタンスに対しては、大量の RAM（少なくとも 2GB）が必要になる場合があります。

## Adobe Commerceアクセスキー

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

## コンポーザー

をダウンロードします。 [!DNL Upgrade Compatibility Tool] リポジトリと実行 `composer install` をターミナルに追加して、依存関係をインストールします。

>[!NOTE]
>
> を正しく設定していない場合、 **Adobe Commerceアクセスキー**&#x200B;を使用している場合、 [!DNL Upgrade Compatibility Tool]. の実行 `composer create-project` コマンドが失敗します。

## Node.js

Node.js をインストールするには、Node.js [ドキュメント](https://nodejs.dev/learn/how-to-install-nodejs).

## サードパーティの拡張機能

Adobeでは、拡張機能のベンダーに問い合わせて、拡張機能が最新バージョンのAdobe Commerceと完全に互換性があるかどうかを確認することをお勧めします。
