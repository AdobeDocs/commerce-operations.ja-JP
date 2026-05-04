---
title: オンプレミスのクイックスタートインストール
description: Composerを使用して、独自のインフラストラクチャにAdobe Commerceをインストールする方法について説明します。 クイックスタートの手順と必要な設定について説明します。
exl-id: a93476e8-2b30-461a-91df-e73eb1a14d3c
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '1003'
ht-degree: 0%

---

# オンプレミスのクイックスタートインストール

このページの手順では、Adobe Commerceをセルフホスト型インフラストラクチャにインストールする方法について説明します。 既存のインストールのアップグレードに関するガイダンスについては、[_アップグレードガイド_](../upgrade/overview.md)&#x200B;を参照してください。

Adobeでは、[Composer](https://getcomposer.org/)を使用して、Adobe Commerce コンポーネントとその依存関係を管理します。 Composerを使用してAdobe Commerce メタパッケージを取得すると、次の利点が得られます。

- サードパーティライブラリをソースコードにバンドルすることなく再利用
- 堅牢な依存関係管理を備えたコンポーネントベースのアーキテクチャを使用することで、拡張機能の競合や互換性の問題を軽減できます
- [PHP フレームワーク相互運用性グループ （FIG） ](https://www.php-fig.org/)標準に準拠
- Magento Open Sourceと他のコンポーネントの再パッケージ
- 本番環境でのAdobe Commerce ソフトウェアの使用

>[!NOTE]
>
>Magento Open Sourceに参加する開発者は、[git ベースの](https://developer.adobe.com/commerce/contributor/guides/install/)のインストール方法を使用する必要があります。

## 前提条件

続行する前に、次の操作を行う必要があります。

- すべての[前提条件タスク ](system-requirements.md)を完了します。
- [Composer](https://getcomposer.org/download/)をインストールします。
- Adobe Commerce Composer リポジトリに[認証キー](prerequisites/authentication-keys.md)を取得します。

## ファイルシステム所有者としてログイン

所有権、権限、およびファイルシステムの所有者について詳しくは、[所有権と権限の概要トピック ](prerequisites/file-system/overview.md)を参照してください。

ファイルシステムの所有者に切り替えるには：

1. ファイルシステムへの書き込み権限を持つユーザーとしてアプリケーションサーバーにログインするか、切り替えます。

   bash シェルを使用する場合は、次の構文を使用してファイルシステム所有者に切り替え、同時にコマンドを入力できます。

   ```shell
   su <file system owner> -s /bin/bash -c <command>
   ```

   ファイルシステムの所有者がログインを許可しない場合は、次の操作を実行できます。

   ```shell
   sudo -u <file system owner>  <command>
   ```

1. 任意のディレクトリからCLI コマンドを実行するには、システム `PATH`に`<app_root>/bin`を追加します。

   シェルの構文は異なるので、[unix.stackexchange.com](https://unix.stackexchange.com/questions/117467/how-to-permanently-set-environmental-variables)などの参照を参照してください。

   CentOSのbash シェルの例：

   ```shell
   export PATH=$PATH:/var/www/html/magento2/bin
   ```

   オプションで、次の方法でコマンドを実行できます。

   - `cd <app_root>/bin`として実行`./magento <command name>`
   - `app_root>/bin/magento <command name>`
   - `<app_root>`はweb サーバーのdocrootのサブディレクトリです

## メタパッケージを入手

Adobe Commerce メタパッケージを取得するには：

1. [ ファイルシステム所有者](prerequisites/file-system/overview.md)としてアプリケーションサーバーにログインするか、切り替えます。
1. Web サーバーのdocroot ディレクトリまたは仮想ホストのdocrootとして設定したディレクトリに変更します。
1. Commerce メタパッケージを使用してComposer プロジェクトを作成します。

   **Magento Open Source**

   ```shell
   composer create-project --repository-url=https://repo.magento.com/ magento/project-community-edition <install-directory-name>
   ```

   **Adobe Commerce**

   ```shell
   composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition <install-directory-name>
   ```

   プロンプトが表示されたら、認証キーを入力します。 公開鍵と秘密鍵は、[Commerce Marketplace - アクセスキー](https://commercemarketplace.adobe.com/customer/account/login/)から作成および設定されます。 `[!UICONTROL username]`の場合は、公開鍵の値をコピーして貼り付けます。 `[!UICONTROL password]`の場合は、秘密鍵の値をコピーして貼り付けます。

   >[!NOTE]
   >
   > Commerce認証キーで構成されたComposer `[auth.json](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/authentication-keys)` ファイルまたは環境変数を使用する場合、認証キーを入力するメッセージは表示されません。

   `Could not find package...`や`...no matching package found`などのエラーが発生した場合は、コマンドにタイプミスがないことを確認してください。 それでもエラーが発生する場合は、Adobe Commerceのダウンロードが許可されない場合があります。 ヘルプについては、[Adobe Commerce サポート ](https://support.magento.com/hc/en-us)にお問い合わせください。

   その他のエラーについては、[ トラブルシューティング ](https://support.magento.com/hc/en-us/articles/360033818091)を参照してください。

### 例 – マイナーリリース

マイナーリリースには、新機能、品質修正、セキュリティ修正が含まれています。 マイナーリリースを指定するには、Composerを使用します。 例えば、Adobe Commerce 2.4.6 メタパッケージを指定するには、次の手順を実行します。

```shell
composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition=2.4.6 <install-directory-name>
```

### 例 – 品質パッチ

品質パッチには、主に機能的な&#x200B;_および_&#x200B;のセキュリティ修正が含まれています。 しかし、新しい後方互換性のある機能を含むこともあります。 Composerを使用して、高品質のパッチをダウンロードします。 例えば、Adobe Commerce 2.4.6 メタパッケージを指定するには、次の手順を実行します。

```shell
composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition=2.4.6 <install-directory-name>
```

### 例 – セキュリティパッチ

セキュリティパッチにはセキュリティ修正のみが含まれています。 アップグレードプロセスをより迅速かつ容易に行えるように設計されています。

セキュリティパッチでは、Composerの命名規則`2.4.6-px`が使用されます。 Composerを使用してパッチを指定します。 例えば、Adobe Commerce 2.4.6-p1 メタパッケージをダウンロードするには、次の手順を実行します。

```shell
composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition=2.4.6-p1 <install-directory-name>
```

## ファイル権限の設定

Adobe Commerceをインストールする前に、web サーバーグループの読み取り/書き込み権限を設定する必要があります。 これは、コマンドラインがファイルシステムにファイルを書き込めるようにするために必要です。

```shell
cd /var/www/html/<magento install directory>
find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} +
find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} +
chown -R :www-data . # Ubuntu
chmod u+x bin/magento
```

## アプリケーションのインストール

Adobe Commerceをインストールするには、コマンドラインを使用する必要があります。

この例では、インストールディレクトリの名前が`magento2ee`で、`db-host`が同じコンピューター（`localhost`）にあり、`db-name`、`db-user`、`db-password`がすべて`magento`であると仮定します。

```shell
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
>管理者URIは、`--backend-frontname` オプションでカスタマイズできます。 ただし、Adobeでは、このオプションを省略し、インストールコマンドでランダムなURIを自動生成できるようにすることをお勧めします。 ランダム URIは、ハッカーや悪意のあるソフトウェアが悪用するのが困難です。 インストールが完了すると、URIがコンソールに表示されます。

>[!TIP]
>
>CLI インストールオプションの詳細については、[ コマンドラインからのアプリケーションのインストール ](advanced.md)を参照してください。

## コマンドの概要

コマンドの完全なリストを表示するには、次のように入力します。

```shell
bin/magento list
```

特定のコマンドのヘルプを表示するには、次のように入力します。

```shell
bin/magento help <command>
```

例：

```shell
bin/magento help setup:install
```

```shell
bin/magento help cache:enable
```

次の表に、使用可能なコマンドの概要を示します。 コマンドはサマリーフォームでのみ表示されます。 コマンドの詳細については、「コマンド」列のリンクをクリックしてください。

| コマンド | 説明 | 前提条件 |
|--- |--- |--- |
| `magento setup:install` | アプリケーションをインストールします | なし |
| `magento setup:uninstall` | アプリケーションを削除します。 | インストール済みアプリケーション |
| `magento setup:upgrade` | アプリケーションを更新します。 | デプロイメント設定 |
| `magento maintenance:{enable/disable}` | メンテナンスモードを有効または無効にします（メンテナンスモードでは、除外IP アドレスのみが管理者またはストアフロントにアクセスできます）。 | インストール済みアプリケーション |
| `magento setup:config:set` | デプロイメント設定を作成または更新します。 | なし |
| `magento module:{enable/disable}` | モジュールを有効または無効にします。 | なし |
| `magento setup:store-config:set` | ベース URL、言語、タイムゾーンなど、ストアフロント関連のオプションを設定します。 | デプロイメント設定 |
| `magento setup:db-schema:upgrade` | データベーススキーマを更新します。 | デプロイメント設定 |
| `magento setup:db-data:upgrade` | データベースデータを更新します。 | デプロイメント設定 |
| `magento setup:db:status` | データベースがコードで最新かどうかを確認します。 | デプロイメント設定 |
| `magento admin:user:create` | 管理者ユーザーを作成します。 | 次のユーザーを作成できます。<br><br> デプロイメント設定<br><br>少なくとも`Magento_User`および`Magento_Authorization` モジュール <br><br> データベースを有効にする（最も簡単な方法は`bin/magento setup:upgrade`を使用することです） |
| `magento list` | 使用可能なすべてのコマンドを一覧表示します。 | なし |
| `magento help` | 指定したコマンドのヘルプを表示します。 | なし |

### 共通引数

次の引数は、すべてのコマンドに共通です。 これらのコマンドは、アプリケーションのインストール前またはインストール後に実行できます。

| 長文 | 短いバージョン | 意味 |
|--- |--- |--- |
| `--help` | `-h` | 任意のコマンドのヘルプを表示します。 例：`./magento help setup:install`または`./magento help setup:config:set` |
| `--quiet` | `-q` | 静かなモード。出力なし。 |
| `--no-interaction` | `-n` | インタラクティブな質問なし。 |
| `--verbose=1,2,3` | `-v, -vv, -vvv` | 詳細レベル： 例えば、`--verbose=3`または`-vvv`は、最も冗長な出力であるデバッグの冗長性を表示します。 デフォルトは`--verbose=1`または`-v`です。 |
| `--version` | `-V` | このアプリケーションのバージョンを表示 |
| `--ansi` | なし | ANSI出力を強制 |
| `--no-ansi` | なし | ANSI出力を無効にする |

>[!NOTE]
>
>おめでとうございます。 クイックインストールが完了しました。 より高度なサポートが必要ですか？ [詳細インストール ](advanced.md) ガイドをご覧ください。
