---
title: オンプレミスでの迅速なインストールを開始
description: 所有しているインフラストラクチャにAdobe CommerceまたはMagento Open Sourceをインストールするには、次の手順に従います。
exl-id: a93476e8-2b30-461a-91df-e73eb1a14d3c
source-git-commit: 3c6527e5936438d6f1f52b32082cc7dde5f87f22
workflow-type: tm+mt
source-wordcount: '993'
ht-degree: 0%

---

# オンプレミスでの迅速なインストールを開始

このページの手順では、にAdobe CommerceとMagento Open Sourceをインストールする方法を説明します。 [自己ホスト型の](../implementation-playbook/infrastructure/self-hosting/overview.md) インフラストラクチャ 既存のインストールのアップグレードに関するガイダンスについては、 [_アップグレードガイド_](../upgrade/overview.md).

Adobe使用 [コンポーザー](https://getcomposer.org/) :Adobe CommerceとMagento Open Sourceのコンポーネントとその依存関係を管理します。 Composer を使用してAdobe CommerceとMagento Open Sourceのメタパッケージを取得すると、次の利点があります。

- サードパーティライブラリをソースコードと一緒にバンドルせずに再利用する
- 堅牢な依存関係管理を備えたコンポーネントベースのアーキテクチャを使用することで、拡張機能の競合と互換性の問題を減らす
- 準拠先 [PHP-Framework Interoperability Group (FIG)](https://www.php-fig.org/) 標準規格
- Magento Open Sourceを他のコンポーネントと再パッケージ化
- 実稼働環境でのAdobe CommerceまたはMagento Open Sourceソフトウェアの使用

>[!NOTE]
>
>Magento Open Sourceに貢献する開発者は、 [git ベース](https://developer.adobe.com/commerce/contributor/guides/install/) インストール方法。

## 前提条件

続行する前に、次の操作を行う必要があります。

- すべてを完了 [前提条件のタスク](system-requirements.md).
- [Composer のインストール](https://getcomposer.org/download/).
- 取得 [認証キー](prerequisites/authentication-keys.md) をAdobe CommerceおよびMagento Open SourceComposer リポジトリに追加します。

## ファイルシステムの所有者としてログイン

の所有権、権限、およびファイルシステムの所有者について説明します。 [所有権と権限のトピックの概要](prerequisites/file-system/overview.md).

ファイル・システムの所有者に切り替えるには、次の手順に従います。

1. ファイル・システムへの書き込み権限を持つユーザーとしてアプリケーション・サーバにログインするか、切り替えます。

   bash シェルを使用する場合は、次の構文を使用して、ファイルシステムの所有者に切り替え、同時にコマンドを入力できます。

   ```bash
   su <file system owner> -s /bin/bash -c <command>
   ```

   ファイルシステムの所有者がログインを許可していない場合は、次の操作を実行できます。

   ```bash
   sudo -u <file system owner>  <command>
   ```

1. 任意のディレクトリから CLI コマンドを実行するには、 `<app_root>/bin` システムに `PATH`.

   シェルの構文は異なるので、次のような参照を参照してください。 [unix.stackexchange.com](https://unix.stackexchange.com/questions/117467/how-to-permanently-set-environmental-variables).

   CentOS 用の bash シェルの例：

   ```bash
   export PATH=$PATH:/var/www/html/magento2/bin
   ```

   必要に応じて、次の方法でコマンドを実行できます。

   - `cd <app_root>/bin` を実行します。 `./magento <command name>`
   - `app_root>/bin/magento <command name>`
   - `<app_root>` は、Web サーバーの docroot のサブディレクトリです。

## メタパッケージの取得

Adobe CommerceまたはMagento Open Sourceのメタパッケージを取得するには：

1. アプリケーションサーバーに、 [ファイルシステム所有者](prerequisites/file-system/overview.md).
1. Web サーバーの docroot ディレクトリ、または仮想ホストの docroot として設定したディレクトリに変更します。
1. Adobe CommerceまたはMagento Open Sourceメタパッケージを使用して Composer プロジェクトを作成します。

   **Magento Open Source**

   ```bash
   composer create-project --repository-url=https://repo.magento.com/ magento/project-community-edition <install-directory-name>
   ```

   **Adobe Commerce**

   ```bash
   composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition <install-directory-name>
   ```

   プロンプトが表示されたら、認証キーを入力します。 公開鍵と秘密鍵は、 [Commerce Marketplace](https://commercemarketplace.adobe.com/customer/account/login/).

   >[!NOTE]
   >
   > コンポーザーを使用する場合 `auth.json` ファイルまたは環境変数を使用する場合、認証キーの入力を求めるプロンプトは表示されません。

   次のようなエラーが発生した場合： `Could not find package...` または `...no matching package found`を使用する場合は、コマンドに入力ミスがないことを確認します。 それでもエラーが発生する場合は、Adobe Commerceのダウンロードが許可されていない可能性があります。 連絡先 [Adobe Commerceサポート](https://support.magento.com/hc/en-us) を参照してください。

   詳しくは、 [トラブルシューティング](https://support.magento.com/hc/en-us/articles/360033818091) を参照してください。

### 例 — マイナーリリース

マイナーリリースには、新機能、品質修正およびセキュリティ修正が含まれています。 Composer を使用してマイナーリリースを指定します。 例えば、Adobe Commerce 2.4.6 のメタパッケージを指定するには、次のようにします。

```bash
composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition=2.4.6 <install-directory-name>
```

### 例 — 品質パッチ

品質パッチには主に機能が含まれる _および_ セキュリティの修正。 ただし、後方互換性のある新しい機能を含めることもできます。 Composer を使用して、品質パッチをダウンロードします。 例えば、Adobe Commerce 2.4.6 のメタパッケージを指定するには、次のようにします。

```bash
composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition=2.4.6 <install-directory-name>
```

### 例 — セキュリティパッチ

セキュリティパッチにはセキュリティ修正のみが含まれています。 これらは、アップグレードプロセスをより迅速かつ容易にするように設計されています。

セキュリティパッチでは、Composer の命名規則を使用します。 `2.4.6-px`. Composer を使用してパッチを指定します。 例えば、Adobe Commerce 2.4.6-p1 メタパッケージをダウンロードするには、次のようにします。

```bash
composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition=2.4.6-p1 <install-directory-name>
```

## ファイルの権限の設定

Adobe CommerceまたはMagento Open Sourceをインストールする前に、Web サーバーグループの読み取り/書き込み権限を設定する必要があります。 これは、コマンドラインがファイルをファイルシステムに書き込めるようにするために必要です。

```terminal
cd /var/www/html/<magento install directory>
find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} +
find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} +
chown -R :www-data . # Ubuntu
chmod u+x bin/magento
```

## アプリケーションのインストール

コマンドラインを使用して、Adobe CommerceまたはMagento Open Sourceをインストールする必要があります。

この例では、インストールディレクトリの名前がとなっていることを前提としています。 `magento2ee`、 `db-host` は同じマシン (`localhost`)、および `db-name`, `db-user`、および `db-password` すべて `magento`:

```bash
bin/magento setup:install \
--base-url=http://localhost/magento2ee \
--db-host=localhost \
--db-name=magento \
--db-user=magento \
--db-password=magento \
--admin-firstname=admin \
--admin-lastname=admin \
--admin-email=admin@admin.com \
--admin-user=admin \
--admin-password=admin123 \
--language=en_US \
--currency=USD \
--timezone=America/Chicago \
--use-rewrites=1 \
--search-engine=opensearch \
--opensearch-host=os-host.example.com \
--opensearch-port=9200 \
--opensearch-index-prefix=magento2 \
--opensearch-timeout=15
```

>[!TIP]
>
>管理 URI は、 `--backend-frontname` オプション。 ただし、Adobeでは、このオプションを省略し、インストールコマンドでランダムな URI を自動的に生成することをお勧めします。 ランダムな URI は、ハッカーや悪意のあるソフトウェアが悪用するのを難しくします。 インストールが完了すると、URI がコンソールに表示されます。

>[!TIP]
>
>CLI インストールオプションの詳細については、を参照してください。 [コマンドラインからアプリケーションをインストールする](advanced.md).

## コマンドの概要

コマンドの完全なリストを表示するには、次のように入力します。

```bash
bin/magento list
```

特定のコマンドのヘルプを表示するには、次のように入力します。

```bash
bin/magento help <command>
```

例：

```bash
bin/magento help setup:install
```

```bash
bin/magento help cache:enable
```

次の表に、使用可能なコマンドの概要を示します。 コマンドは概要形式でのみ表示されます。 コマンドの詳細については、[ コマンド ] 列のリンクをクリックします。

| コマンド | 説明 | 前提条件 |
|--- |--- |--- |
| `magento setup:install` | アプリケーションをインストールします | なし |
| `magento setup:uninstall` | アプリケーションを削除します。 | インストールされたアプリケーション |
| `magento setup:upgrade` | アプリケーションを更新します。 | デプロイメント設定 |
| `magento maintenance:{enable/disable}` | メンテナンスモードを有効または無効にします（メンテナンスモードでは、管理者またはストアフロントにアクセスできるのは除外 IP アドレスのみです）。 | インストールされたアプリケーション |
| `magento setup:config:set` | デプロイメント設定を作成または更新します。 | なし |
| `magento module:{enable/disable}` | モジュールを有効または無効にします。 | なし |
| `magento setup:store-config:set` | ベース URL、言語、タイムゾーンなど、ストアフロント関連のオプションを設定します。 | デプロイメント設定 |
| `magento setup:db-schema:upgrade` | データベーススキーマを更新します。 | デプロイメント設定 |
| `magento setup:db-data:upgrade` | データベースデータを更新します。 | デプロイメント設定 |
| `magento setup:db:status` | データベースがコードで最新かどうかを確認します。 | デプロイメント設定 |
| `magento admin:user:create` | 管理者ユーザーを作成します。 | 次のユーザーを作成できます。<br><br>デプロイメント設定<br><br>少なくとも `Magento_User` および `Magento_Authorization` モジュール<br><br>データベース ( 最も簡単な方法は `bin/magento setup:upgrade`) |
| `magento list` | 使用可能なすべてのコマンドを一覧表示します。 | なし |
| `magento help` | 指定したコマンドに関するヘルプを提供します。 | なし |

### 共通の引数

次の引数は、すべてのコマンドに共通です。 次のコマンドは、アプリケーションのインストール前またはインストール後に実行できます。

| 長いバージョン | 短いバージョン | 意味 |
|--- |--- |--- |
| `--help` | `-h` | 任意のコマンドに関するヘルプを取得します。 例： `./magento help setup:install` または `./magento help setup:config:set`. |
| `--quiet` | `-q` | クワイエットモード。出力なし。 |
| `--no-interaction` | `-n` | インタラクティブな質問はありません。 |
| `--verbose=1,2,3` | `-v, -vv, -vvv` | 詳細レベル。 例： `--verbose=3` または `-vvv` は、最も詳細な出力である debug verbosity を表示します。 デフォルトはです。 `--verbose=1` または `-v`. |
| `--version` | `-V` | このアプリケーションバージョンを表示 |
| `--ansi` | 該当なし | ANSI 出力を強制 |
| `--no-ansi` | 該当なし | ANSI 出力を無効にする |

>[!NOTE]
>
>おめでとうございます。クイックインストールを完了しました。 より高度なヘルプが必要な場合は、 以下を確認します。 [高度なインストール](advanced.md) ガイド。
