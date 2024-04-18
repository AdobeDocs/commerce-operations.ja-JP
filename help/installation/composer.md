---
title: オンプレミスでのクイックスタートのインストール
description: 所有しているインフラストラクチャにAdobe Commerceをインストールするには、次の手順に従います。
exl-id: a93476e8-2b30-461a-91df-e73eb1a14d3c
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '933'
ht-degree: 0%

---

# オンプレミスでのクイックスタートのインストール

ここでは、にAdobe Commerceをインストールする手順を説明します [自己ホスト](../implementation-playbook/infrastructure/self-hosting/overview.md) インフラストラクチャ 既存のインストールのアップグレードに関するガイダンスについては、 [_アップグレードガイド_](../upgrade/overview.md).

Adobeの用途 [コンポーザー](https://getcomposer.org/) Adobe Commerce コンポーネントとその依存関係を管理します。 Composer を使用してAdobe Commerce メタパッケージを取得すると、次の利点があります。

- サードパーティ製ライブラリをソースコードとバンドルせずに再利用
- 堅牢な依存関係管理を備えたコンポーネントベースのアーキテクチャを使用することで、拡張機能の競合と互換性の問題を軽減します。
- 付着 [PHP-Framework Interoperability Group （FIG）](https://www.php-fig.org/) 標準規格
- Magento Open Sourceを他のコンポーネントと再パッケージ化
- 実稼動環境でのAdobe Commerce ソフトウェアの使用

>[!NOTE]
>
>Magento Open Sourceに貢献する開発者は、 [git ベース](https://developer.adobe.com/commerce/contributor/guides/install/) インストール方法。

## 前提条件

続行する前に、次の操作を行う必要があります。

- すべて完了 [前提条件のタスク](system-requirements.md).
- [Composer のインストール](https://getcomposer.org/download/).
- 取得 [認証キー](prerequisites/authentication-keys.md) をAdobe Commerce Composer リポジトリに追加します。

## ファイルシステム所有者としてログインします。

での所有権、権限およびファイルシステム所有者について説明します [所有権と権限のトピックの概要](prerequisites/file-system/overview.md).

ファイルシステムの所有者に切り替えるには、次の手順に従います。

1. ファイルシステムへの書き込み権限を持つユーザーとしてアプリケーションサーバーにログインするか、そのユーザーに切り替えます。

   bash シェルを使用する場合は、次の構文を使用してファイルシステムの所有者に切り替え、同時にコマンドを入力できます。

   ```bash
   su <file system owner> -s /bin/bash -c <command>
   ```

   ファイルシステムの所有者がログインを許可しない場合は、次の操作を実行できます。

   ```bash
   sudo -u <file system owner>  <command>
   ```

1. 任意のディレクトリから CLI コマンドを実行するには、次のコマンドを追加します。 `<app_root>/bin` お使いのシステム `PATH`.

   シェルは構文が異なるので、のようなリファレンスを参照してください。 [unix.stackexchange.com](https://unix.stackexchange.com/questions/117467/how-to-permanently-set-environmental-variables).

   CentOS 用の bash シェルの例：

   ```bash
   export PATH=$PATH:/var/www/html/magento2/bin
   ```

   オプションで、次の方法でコマンドを実行できます。

   - `cd <app_root>/bin` そしてそれらを `./magento <command name>`
   - `app_root>/bin/magento <command name>`
   - `<app_root>` は、web サーバーの docroot のサブディレクトリです。

## メタパッケージを入手する

Adobe Commerce メタパッケージを入手するには：

1. アプリケーションサーバーにとしてログインするか、 [ファイルシステム所有者](prerequisites/file-system/overview.md).
1. Web サーバーの docroot ディレクトリまたは仮想ホストの docroot として設定したディレクトリに移動します。
1. Commerce メタパッケージを使用して Composer プロジェクトを作成します。

   **Magento Open Source**

   ```bash
   composer create-project --repository-url=https://repo.magento.com/ magento/project-community-edition <install-directory-name>
   ```

   **Adobe Commerce**

   ```bash
   composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition <install-directory-name>
   ```

   プロンプトが表示されたら、認証キーを入力します。 公開鍵と秘密鍵は、で作成および設定します。 [Commerce Marketplace](https://commercemarketplace.adobe.com/customer/account/login/).

   >[!NOTE]
   >
   > Composer を使用する場合 `auth.json` ファイルまたは環境変数の場合、認証キーを入力するように求められることはありません。

   エラー（例：）が発生した場合 `Could not find package...` または `...no matching package found`コマンドに入力ミスがないことを確認します。 それでもエラーが発生する場合は、Adobe Commerceのダウンロードが許可されていない可能性があります。 連絡先 [Adobe Commerce サポート](https://support.magento.com/hc/en-us) ヘルプを参照してください。

   参照： [トラブルシューティング](https://support.magento.com/hc/en-us/articles/360033818091) その他のエラーに関するヘルプ。

### 例 – マイナーリリース

マイナーリリースには、新機能、品質修正、セキュリティ修正が含まれています。 Composer を使用してマイナーリリースを指定します。 例えば、Adobe Commerce 2.4.6 メタパッケージを指定するには、次のように指定します。

```bash
composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition=2.4.6 <install-directory-name>
```

### 例 – 品質パッチ

品質向上パッチには、主に機能性パッチが含まれています _および_ セキュリティの修正。 ただし、下位互換性のある新しい機能が含まれることもあります。 Composer を使用して品質パッチをダウンロードします。 例えば、Adobe Commerce 2.4.6 メタパッケージを指定するには、次のように指定します。

```bash
composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition=2.4.6 <install-directory-name>
```

### 例 – セキュリティパッチ

セキュリティパッチには、セキュリティ修正のみが含まれています。 これらは、アップグレードプロセスをより速く、より簡単にするように設計されています。

セキュリティパッチでは、Composer 命名規則を使用します `2.4.6-px`. Composer を使用してパッチを指定します。 例えば、Adobe Commerce 2.4.6-p1 メタパッケージをダウンロードするには、次の手順に従います。

```bash
composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition=2.4.6-p1 <install-directory-name>
```

## ファイルのアクセス許可の設定

Adobe Commerceをインストールする前に、web サーバーグループの読み取り/書き込み権限を設定する必要があります。 これは、コマンドラインがファイルをファイルシステムに書き込めるようにするために必要です。

```terminal
cd /var/www/html/<magento install directory>
find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} +
find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} +
chown -R :www-data . # Ubuntu
chmod u+x bin/magento
```

## アプリケーションのインストール

Adobe Commerceをインストールするには、コマンドラインを使用する必要があります。

この例では、インストールディレクトリの名前がであることを前提としています `magento2ee`, `db-host` が同じマシン上にある（`localhost`）に設定し、 `db-name`, `db-user`、および `db-password` が全て `magento`:

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
>の管理 URI は次のようにカスタマイズできます。 `--backend-frontname` オプション。 ただし、Adobeでは、このオプションを省略し、インストールコマンドがランダムな URI を自動生成できるようにすることをお勧めします。 ランダム URI は、ハッカーや悪意のあるソフトウェアが悪用しにくくなります。 インストールが完了すると、コンソールに URI が表示されます。

>[!TIP]
>
>CLI インストール・オプションの詳細については、を参照してください。 [コマンドラインからのアプリケーションのインストール](advanced.md).

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

次の表に、使用可能なコマンドを示します。 コマンドは、要約の形式でのみ表示されます。 コマンドの詳細については、[ コマンド ] 列のリンクをクリックしてください。

| コマンド | 説明 | 前提条件 |
|--- |--- |--- |
| `magento setup:install` | アプリケーションをインストールします | なし |
| `magento setup:uninstall` | アプリケーションを削除します。 | インストールされているアプリケーション |
| `magento setup:upgrade` | アプリケーションを更新します。 | デプロイメント設定 |
| `magento maintenance:{enable/disable}` | メンテナンスモードを有効または無効にします（メンテナンスモードでは、除外 IP アドレスのみが管理者またはストアフロントにアクセスできます）。 | インストールされているアプリケーション |
| `magento setup:config:set` | デプロイメント設定を作成または更新します。 | なし |
| `magento module:{enable/disable}` | モジュールを有効または無効にします。 | なし |
| `magento setup:store-config:set` | ストアフロントに関連するオプション（ベース URL、言語、タイムゾーンなど）を設定します。 | デプロイメント設定 |
| `magento setup:db-schema:upgrade` | データベーススキーマを更新します。 | デプロイメント設定 |
| `magento setup:db-data:upgrade` | データベース データを更新します。 | デプロイメント設定 |
| `magento setup:db:status` | データベースがコードの最新かどうかを確認します。 | デプロイメント設定 |
| `magento admin:user:create` | 管理者ユーザーを作成します。 | 次のユーザーを作成できます。<br><br>デプロイメント設定<br><br>少なくとも「」を有効にします `Magento_User` および `Magento_Authorization` モジュール<br><br>データベース（最も簡単な方法は使用することです） `bin/magento setup:upgrade`） |
| `magento list` | 使用可能なすべてのコマンドを一覧表示します。 | なし |
| `magento help` | 指定したコマンドのヘルプを表示します。 | なし |

### 一般的な引数

次の引数は、すべてのコマンドに共通です。 次のコマンドは、アプリケーションのインストール前またはインストール後に実行できます。

| ロングバージョン | ショートバージョン | 意味 |
|--- |--- |--- |
| `--help` | `-h` | 任意のコマンドのヘルプを表示します。 例： `./magento help setup:install` または `./magento help setup:config:set`. |
| `--quiet` | `-q` | クワイエットモード。出力なし。 |
| `--no-interaction` | `-n` | インタラクティブな質問はありません。 |
| `--verbose=1,2,3` | `-v, -vv, -vvv` | 詳細レベル。 例： `--verbose=3` または `-vvv` デバッグの詳細を表示します。デバッグの詳細は、最も詳細な出力です。 デフォルトは `--verbose=1` または `-v`. |
| `--version` | `-V` | このアプリケーションのバージョンを表示 |
| `--ansi` | 該当なし | ANSI 出力を強制 |
| `--no-ansi` | 該当なし | ANSI 出力を無効にする |

>[!NOTE]
>
>おめでとうございます。クイックインストールが完了しました。 より高度なヘルプが必要な場合は、 を確認してください。 [高度なインストール](advanced.md) ガイド。
