---
title: オンプレミスでのクイックスタートのインストール
description: Composer を使用して独自のインフラストラクチャにAdobe Commerceをインストールする方法を説明します。 クイックスタート手順と設定要件について説明します。
exl-id: a93476e8-2b30-461a-91df-e73eb1a14d3c
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '964'
ht-degree: 0%

---

# オンプレミスでのクイックスタートのインストール

このページの手順では、セルフホストインフラストラクチャにAdobe Commerceをインストールする方法について説明します。 既存のインストールのアップグレードに関するガイダンスについては、[_アップグレードガイド_](../upgrade/overview.md) を参照してください。

Adobeでは [Composer](https://getcomposer.org/) を使用して、Adobe Commerce コンポーネントとその依存関係を管理します。 Composer を使用してAdobe Commerce メタパッケージを取得すると、次の利点があります。

- サードパーティ製ライブラリをソースコードとバンドルせずに再利用
- 堅牢な依存関係管理を備えたコンポーネントベースのアーキテクチャを使用することで、拡張機能の競合と互換性の問題を軽減します。
- [PHP-Framework Interoperability Group （FIG） &#x200B;](https://www.php-fig.org/) 規格に準拠
- Magento Open Sourceを他のコンポーネントと再パッケージ化
- 実稼動環境でのAdobe Commerce ソフトウェアの使用

>[!NOTE]
>
>Magento Open Sourceに投稿する開発者は、[git ベースの &#x200B;](https://developer.adobe.com/commerce/contributor/guides/install/) インストール方式を使用する必要があります。

## 前提条件

続行する前に、次の操作を行う必要があります。

- すべての [&#x200B; 前提条件タスク &#x200B;](system-requirements.md) を完了します。
- [Composer のインストール &#x200B;](https://getcomposer.org/download/)。
- [&#x200B; 認証キー &#x200B;](prerequisites/authentication-keys.md) をAdobe Commerce Composer リポジトリに取得します。

## ファイルシステム所有者としてログインします。

所有権、権限、ファイルシステムの所有者については、[&#x200B; 所有権と権限の概要 &#x200B;](prerequisites/file-system/overview.md) トピックを参照してください。

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

1. 任意のディレクトリから CLI コマンドを実行するには、`<app_root>/bin` をシステム `PATH` に追加します。

   シェルは構文が異なるため、[unix.stackexchange.com](https://unix.stackexchange.com/questions/117467/how-to-permanently-set-environmental-variables) などのリファレンスを参照してください。

   CentOS 用の bash シェルの例：

   ```bash
   export PATH=$PATH:/var/www/html/magento2/bin
   ```

   オプションで、次の方法でコマンドを実行できます。

   - `cd <app_root>/bin` として `./magento <command name>` び出して実行
   - `app_root>/bin/magento <command name>`
   - `<app_root>` は、web サーバーの docroot のサブディレクトリです。

## メタパッケージを入手する

Adobe Commerce メタパッケージを入手するには：

1. [&#x200B; ファイルシステムの所有者 &#x200B;](prerequisites/file-system/overview.md) としてアプリケーションサーバーにログインするか、に切り替えます。
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

   プロンプトが表示されたら、認証キーを入力します。 公開鍵と秘密鍵は、[Commerce Marketplace - アクセスキー &#x200B;](https://commercemarketplace.adobe.com/customer/account/login/) から作成および設定されます。 `[!UICONTROL username]` の場合は、公開鍵の値をコピーして貼り付けます。 `[!UICONTROL password]` の場合は、秘密鍵の値をコピー&amp;ペーストします。

   >[!NOTE]
   >
   > Commerce認証キーで設定された Composer `[auth.json](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/authentication-keys)` ファイルまたは環境変数を使用する場合、認証キーを入力するように求められません。

   `Could not find package...` や `...no matching package found` などのエラーが発生した場合は、コマンドに入力ミスがないことを確認してください。 それでもエラーが発生する場合は、Adobe Commerceのダウンロードが許可されていない可能性があります。 [Adobe Commerce サポート &#x200B;](https://support.magento.com/hc/en-us) にお問い合わせください。

   その他のエラーのヘルプについては、[&#x200B; トラブルシューティング &#x200B;](https://support.magento.com/hc/en-us/articles/360033818091) を参照してください。

### 例 – マイナーリリース

マイナーリリースには、新機能、品質修正、セキュリティ修正が含まれています。 Composer を使用してマイナーリリースを指定します。 例えば、Adobe Commerce 2.4.6 メタパッケージを指定するには、次のように指定します。

```bash
composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition=2.4.6 <install-directory-name>
```

### 例 – 品質パッチ

品質向上パッチには、主に機能 _および_ セキュリティ修正が含まれています。 ただし、下位互換性のある新しい機能が含まれることもあります。 Composer を使用して品質パッチをダウンロードします。 例えば、Adobe Commerce 2.4.6 メタパッケージを指定するには、次のように指定します。

```bash
composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition=2.4.6 <install-directory-name>
```

### 例 – セキュリティパッチ

セキュリティパッチには、セキュリティ修正のみが含まれています。 これらは、アップグレードプロセスをより速く、より簡単にするように設計されています。

セキュリティパッチでは、Composer の命名規則 `2.4.6-px` を使用します。 Composer を使用してパッチを指定します。 例えば、Adobe Commerce 2.4.6-p1 メタパッケージをダウンロードするには、次の手順に従います。

```bash
composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition=2.4.6-p1 <install-directory-name>
```

## ファイルのアクセス許可の設定

Adobe Commerceをインストールする前に、web サーバーグループの読み取り/書き込み権限を設定する必要があります。 これは、コマンドラインがファイルをファイルシステムに書き込めるようにするために必要です。

```bash
cd /var/www/html/<magento install directory>
find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} +
find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} +
chown -R :www-data . # Ubuntu
chmod u+x bin/magento
```

## アプリケーションのインストール

Adobe Commerceをインストールするには、コマンドラインを使用する必要があります。

この例では、インストールディレクトリの名前が `magento2ee` で、`db-host` が同じマシン（`localhost`）上にあり、`db-name`、`db-user`、`db-password` がすべて `magento` であることを前提としています。

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
>`--backend-frontname` オプションを使用して、管理 URI をカスタマイズできます。 ただし、Adobeでは、このオプションを省略し、インストールコマンドがランダムな URI を自動生成できるようにすることをお勧めします。 ランダム URI は、ハッカーや悪意のあるソフトウェアが悪用しにくくなります。 インストールが完了すると、コンソールに URI が表示されます。

>[!TIP]
>
>CLI インストール オプションの詳細については、「[&#x200B; コマンド ラインからアプリケーションをインストールする &#x200B;](advanced.md)」を参照してください。

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
| `magento admin:user:create` | 管理者ユーザーを作成します。 | 次のユーザーを作成できます。<br><br> デプロイメント設定 <br><br> 少なくとも `Magento_User` モジュールと `Magento_Authorization` モジュールを有効にする <br><br> データベース（`bin/magento setup:upgrade` を使用する方法が最も簡単です） |
| `magento list` | 使用可能なすべてのコマンドを一覧表示します。 | なし |
| `magento help` | 指定したコマンドのヘルプを表示します。 | なし |

### 一般的な引数

次の引数は、すべてのコマンドに共通です。 次のコマンドは、アプリケーションのインストール前またはインストール後に実行できます。

| ロングバージョン | ショートバージョン | 意味 |
|--- |--- |--- |
| `--help` | `-h` | 任意のコマンドのヘルプを表示します。 例えば、`./magento help setup:install` や `./magento help setup:config:set` です。 |
| `--quiet` | `-q` | クワイエットモード。出力なし。 |
| `--no-interaction` | `-n` | インタラクティブな質問はありません。 |
| `--verbose=1,2,3` | `-v, -vv, -vvv` | 詳細レベル。 例えば、`--verbose=3` または `-vvv` は、デバッグの詳細を表示します。これは最も詳細な出力です。 デフォルトは `--verbose=1` または `-v` です。 |
| `--version` | `-V` | このアプリケーションのバージョンを表示 |
| `--ansi` | 該当なし | ANSI 出力を強制 |
| `--no-ansi` | 該当なし | ANSI 出力を無効にする |

>[!NOTE]
>
>おめでとうございます。 クイックインストールが完了しました。 より高度なヘルプが必要な場合は、 [&#x200B; 高度なインストール &#x200B;](advanced.md) ガイドを確認してください。
