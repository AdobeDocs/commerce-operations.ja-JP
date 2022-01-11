---
title: アップグレード互換性ツールのインストール
description: 次の手順に従って、Adobe Commerceプロジェクトのアップグレード互換性ツールをインストールします。
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# アップグレード互換性ツールのインストール

アップグレード互換性ツールは、Adobe Commerceカスタマイズ済みのインスタンスを特定のバージョンと照合するために、その中にインストールされているすべてのモジュールを分析するコマンドラインツールです。 最新バージョンのAdobe Commerceにアップグレードする前に対処する必要があるエラーと警告のリストを返します。

## ワークフロー

次の図は、アップグレード互換性ツールを実行する際に期待されるワークフローを示しています。

![アップグレード互換性ツールの図](../../assets/upgrade-guide/mvp-diagram-v3.png)

## アップグレード互換性ツールは誰のためのものですか？

次の使用例では、Adobe Commerceパートナーがクライアントのインスタンスをアップグレードする際の一般的なプロセスを示します。

1. パートナーのソフトウェアエンジニアが、アップグレード互換性ツールパッケージを [Adobe Commerceリポジトリ](https://repo.magento.com/) 最新のAdobe Commerceリリースのベータ段階で実行されます。 詳しくは、 [アップグレード互換性ツールのダウンロード](../upgrade-compatibility-tool/install.md#download-the-upgrade-compatibility-tool) トピックを参照してください。
1. ソフトウェアエンジニアは、現在インストールされているAdobe Commerceの特定のバージョンのバニラインスタンスを生成します。 詳しくは、 [コントリビューターガイド](https://devdocs.magento.com/contributor-guide/contributing.html#vanilla-pr) を参照してください。 `instance` コマンドを使用してバニラインストールを生成します。
1. ソフトウェアエンジニアは、インベントリモジュールとカタログモジュールに、カスタマイズされた複数の領域が壊れていることを確認し、X の複雑なスコアを獲得します。 [開発者](../upgrade-compatibility-tool/developer.md) ガイドを参照してください。
1. この情報を使用して、ソフトウェアエンジニアはアップグレードの複雑さを理解し、この情報をパートナーのアカウントマネージャに返すことができます。
1. アカウントマネージャーは、Adobe Commerceのアップグレードのタイムラインとコストを作成し、マネージャーの承認を得ることができます。
1. 管理者の承認を得て、ソフトウェアエンジニアは、必要なコード変更を行い、破損したモジュールを修正します。
1. ソフトウェアエンジニアは、Adobe Commerceのプレリリースでもう一度アップグレード互換性ツールを実行し、新しい問題がなく、ベータ段階で見つかった問題をコードが変更されたことで修正しました。
1. すべてのテストがチェックアウトされ、ソフトウェアエンジニアがこのコードをステージング環境にプッシュします。回帰テストでは、すべてのテストが緑であることが確認され、Adobe Commerceのプレリリース日と同じ日に最新のAdobe Commerceバージョンを実稼動環境にリリースできます。

   ![互換性ツールのオーディエンスをアップグレード](../../assets/upgrade-guide/audience-uct-v3.png)

>[!NOTE]
>
>バニラインスタンスは、特定のリリースバージョン用に、指定したバージョンタグまたはブランチをクリーンインストールしたものです。

## 前提条件

詳しくは、 [前提条件](../upgrade-compatibility-tool/prerequisites.md) を参照してください。

>[!NOTE]
>
>アップグレード互換性ツールは、任意のオペレーティングシステムで実行できます。 Adobe Commerceインスタンスが配置されているアップグレード互換性ツールを実行する必要はありません。 アップグレード互換性ツールでAdobe Commerceインスタンスのソースコードにアクセスできる必要があります。 例えば、あるサーバーにこのツールをインストールし、別のサーバー上のAdobe Commerceインストールにこのツールをポイントすることができます。

大きなモジュールやファイルを含むAdobe Commerceインスタンスに対してアップグレード互換性ツールを実行している場合、ツールには大量の RAM（少なくとも 2GB の RAM）が必要になる場合があります。

### 推奨されるアクション

Adobe Commerceのベストプラクティスでは、同じ名前の 2 つのモジュールを使用しないことをお勧めします。 この場合、アップグレード互換性ツールにはセグメント化エラーが表示されます。

このエラーを回避するには、 `bin` コマンドと追加オプション `-m`:

```bash
bin/uct upgrade:check /<dir>/<instance-name> --coming-version=2.4.1 -m /vendor/<vendor-name>/<module-name>
```

>[!NOTE]
>
>この `<dir>` 値は、Adobe Commerceインスタンスが配置されるディレクトリです。

この `-m` 「 」オプションを使用すると、アップグレード互換性ツールで各特定のモジュールを個別に分析でき、Adobe Commerceインスタンスで同じ名前の 2 つのモジュールが発生するのを防ぐことができます。

また、このコマンドオプションを使用すると、アップグレード互換性ツールで、次の複数のモジュールを含むフォルダを分析できます。

```bash
bin/uct upgrade:check /<dir>/<instance-name> --coming-version=2.4.1 -m /vendor/<vendor-name>/
```

この推奨事項は、アップグレード互換性ツールの実行時に発生する可能性のあるメモリの問題にも役立ちます。

## アップグレード互換性ツールのダウンロード

アップグレード互換性ツールをダウンロードするには、次のコマンドを実行します。

```bash
composer create-project magento/upgrade-compatibility-tool uct --repository https://repo.magento.com
```

## インストール

アップグレード互換性ツールをインストールするには、必要な前提条件をインストールする必要があります。

* Adobe Commerceアクセスキー
* コンポーザー
* Node.js

### Adobe Commerceアクセスキー

必ず [Adobe Commerceアクセスキー](https://devdocs.magento.com/marketplace/sellers/profile-information.html#access-keys) をクリックして、アップグレード互換性ツールをダウンロードして使用します。 Adobe Commerceアクセスキーを `auth.json` 次の場所にあるファイル `~/.composer` デフォルトでは。

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

アップグレード互換性ツールリポジトリを複製してを実行します。 `composer install` をターミナルに追加して、依存関係をインストールします。

>[!WARNING]
>
>この **Adobe Commerceアクセスキー** が正しく構成されていない場合、アップグレード互換性ツールはインストールされず、 `composer install` コマンドを使用します。

### Node.js

Node.js をインストールするには、Node.js [ドキュメント](https://nodejs.dev/learn/how-to-install-nodejs).

## サードパーティの拡張機能

Adobeでは、拡張機能のベンダーに問い合わせて、Adobe Commerce 2.4.x との互換性が完全にあるかどうかを確認することをお勧めします。

詳しくは、 [ツールを実行](../upgrade-compatibility-tool/run.md) を参照してください。
