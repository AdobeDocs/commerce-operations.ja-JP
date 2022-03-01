---
title: のインストール [!DNL Upgrade Compatibility Tool]
description: 次の手順に従って、 [!DNL Upgrade Compatibility Tool] Adobe Commerceプロジェクト用
source-git-commit: 317a044e66fe796ff66b9d8cf7b308f741eb82c1
workflow-type: tm+mt
source-wordcount: '740'
ht-degree: 0%

---


# のインストール [!DNL Upgrade Compatibility Tool]

{{commerce-only}}

この [!DNL Upgrade Compatibility Tool] は、Adobe Commerceカスタマイズ済みのインスタンスを、そのインスタンスにインストールされているすべてのモジュールを分析することで、特定のバージョンと照合するコマンドラインツールです。 最新バージョンのAdobe Commerceにアップグレードする前に対処する必要があるエラーと警告のリストを返します。

## ワークフロー

次の図は、 [!DNL Upgrade Compatibility Tool]:

![[!DNL Upgrade Compatibility Tool] 図](../../assets/upgrade-guide/mvp-diagram-v3.png)

## 誰が [!DNL Upgrade Compatibility Tool] ?

次の使用例では、Adobe Commerceパートナーがクライアントのインスタンスをアップグレードする際の一般的なプロセスを示します。

1. パートナーのソフトウェアエンジニアが [!DNL Upgrade Compatibility Tool] パッケージ [Adobe Commerceリポジトリ](https://repo.magento.com/) 最新のAdobe Commerceリリースのベータ段階で実行されます。 詳しくは、 [をダウンロードします。 [!DNL Upgrade Compatibility Tool]](../upgrade-compatibility-tool/install.md#download-the-upgrade-compatibility-tool) トピックを参照してください。
1. ソフトウェアエンジニアは、現在インストールされているAdobe Commerceの特定のバージョンのバニラインスタンスを生成します。 詳しくは、 [コントリビューターガイド](https://devdocs.magento.com/contributor-guide/contributing.html#vanilla-pr) を参照してください。 `instance` コマンドを使用してバニラインストールを生成します。
1. ソフトウェアエンジニアは、インベントリモジュールとカタログモジュールに、カスタマイズされた複数の領域が壊れていることを確認し、X の複雑なスコアを獲得します。 [開発者](../upgrade-compatibility-tool/developer.md) ガイドを参照してください。
1. この情報を使用して、ソフトウェアエンジニアはアップグレードの複雑さを理解し、この情報をパートナーのアカウントマネージャに返すことができます。
1. アカウントマネージャーは、Adobe Commerceのアップグレードのタイムラインとコストを作成し、マネージャーの承認を得ることができます。
1. 管理者の承認を得て、ソフトウェアエンジニアは、必要なコード変更を行い、破損したモジュールを修正します。
1. ソフトウェアエンジニアが [!DNL Upgrade Compatibility Tool] Adobe Commerceのプレリリースで、新しい問題がなく、そのコードが変更されてベータ段階で見つかった問題が修正されたことを確認しました。
1. すべてのテストがチェックアウトされ、ソフトウェアエンジニアがこのコードをステージング環境にプッシュします。回帰テストでは、すべてのテストが緑であることが確認され、Adobe Commerceのプレリリース日と同じ日に最新のAdobe Commerceバージョンを実稼動環境にリリースできます。

   ![[!DNL Upgrade Compatibility Tool] audience](../../assets/upgrade-guide/audience-uct-v3.png)

>[!NOTE]
>
>バニラインスタンスは、特定のリリースバージョン用に、指定したバージョンタグまたはブランチをクリーンインストールしたものです。

## 前提条件

詳しくは、 [前提条件](../upgrade-compatibility-tool/prerequisites.md) を参照してください。

>[!NOTE]
>
>次を実行できます。 [!DNL Upgrade Compatibility Tool] （任意のオペレーティングシステム）。 を実行する必要はありません。 [!DNL Upgrade Compatibility Tool] Adobe Commerceインスタンスの場所 ～に必要だ [!DNL Upgrade Compatibility Tool] Adobe Commerceインスタンスのソースコードにアクセスできるようにする。 例えば、あるサーバーにこのツールをインストールし、別のサーバー上のAdobe Commerceインストールにこのツールをポイントすることができます。

を実行している場合、 [!DNL Upgrade Compatibility Tool] 大きなモジュールやファイルを持つAdobe Commerceインスタンスに対しては、このツールに大量の RAM（2GB 以上の RAM）が必要になる場合があります。

### 推奨されるアクション

Adobe Commerceのベストプラクティスでは、同じ名前の 2 つのモジュールを使用しないことをお勧めします。 この場合、 [!DNL Upgrade Compatibility Tool] セグメント化障害エラーを示します。

このエラーを回避するには、 `bin` コマンドと追加オプション `-m`:

```bash
bin/uct upgrade:check /<dir>/<instance-name> --coming-version=2.4.1 -m /vendor/<vendor-name>/<module-name>
```

>[!NOTE]
>
>この `<dir>` 値は、Adobe Commerceインスタンスが配置されるディレクトリです。

この `-m` オプションを使用すると、 [!DNL Upgrade Compatibility Tool] Adobe Commerceインスタンス内で同じ名前の 2 つのモジュールが発生するのを防ぐために、特定の各モジュールを個別に分析する。

このコマンドオプションを使用すると、 [!DNL Upgrade Compatibility Tool] 複数のモジュールを含むフォルダーを分析するには：

```bash
bin/uct upgrade:check /<dir>/<instance-name> --coming-version=2.4.1 -m /vendor/<vendor-name>/
```

この推奨事項は、 [!DNL Upgrade Compatibility Tool].

## をダウンロードします。 [!DNL Upgrade Compatibility Tool]

次の手順で [!DNL Upgrade Compatibility Tool]、次のコマンドを実行します。

```bash
composer create-project magento/upgrade-compatibility-tool uct --repository https://repo.magento.com
```

## インストール

をインストールするには、以下を実行します。 [!DNL Upgrade Compatibility Tool]を使用する場合は、必要な前提条件をインストールする必要があります。

* Adobe Commerceアクセスキー
* コンポーザー
* Node.js

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

のクローン [!DNL Upgrade Compatibility Tool] リポジトリと実行 `composer install` をターミナルに追加して、依存関係をインストールします。

>[!WARNING]
>
>この **Adobe Commerceアクセスキー** が正しく設定されていない場合は、 [!DNL Upgrade Compatibility Tool] はインストールされず、実行時にエラーが発生します `composer install` コマンドを使用します。

### Node.js

Node.js をインストールするには、Node.js [ドキュメント](https://nodejs.dev/learn/how-to-install-nodejs).

## サードパーティの拡張機能

Adobeでは、拡張機能のベンダーに問い合わせて、Adobe Commerce 2.4.x との互換性が完全にあるかどうかを確認することをお勧めします。

詳しくは、 [ツールを実行](../upgrade-compatibility-tool/run.md) : [!DNL Upgrade Compatibility Tool].
