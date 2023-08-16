---
title: 高度なオンプレミスインストール
description: Adobe Commerceの高度なインストールシナリオ、または所有しているインフラストラクチャのMagento Open Sourceについて説明します。
exl-id: e16e750a-e068-4a63-8ad9-62043e2a8231
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '2406'
ht-degree: 0%

---

# 高度なオンプレミスインストール

>[!TIP]
>
>迷った？ 手を貸す？ 所要時間： [クイックスタートインストール](composer.md) または [寄稿者のインストール](https://developer.adobe.com/commerce/contributor/guides/install/) ガイド。

>[!NOTE]
>
>SELinux を有効にする場合は、 [SELinux と iptables](prerequisites/security.md).

## CLI（コマンド・ライン・インタフェース）

Adobe CommerceとMagento Open Sourceは、インストールおよび設定タスク用の 1 つのコマンドラインインターフェイスを備えています。 `<magento_root>/bin/magento`. インターフェイスは、次のような複数のタスクを実行します。

* インストール（およびデータベーススキーマの作成や更新、デプロイメント設定の作成など、関連するタスク）。
* キャッシュをクリアします。
* インデックスの管理（インデックスの再作成を含む）。
* 翻訳辞書と翻訳パッケージを作成します。
* プラグインのファクトリやインターセプタなどの存在しないクラスを生成し、オブジェクトマネージャの依存インジェクション設定を生成します。
* 静的ビューファイルのデプロイ。
* CSS を「少ない」から作成する。

その他の利点：

* 1 つのコマンド (`<magento_root>/bin/magento list`) に、使用可能なすべてのインストールおよび設定コマンドを示します。
* Symfony に基づく一貫したユーザ・インタフェース。
* CLI は拡張可能なため、サード・パーティの開発者は CLI に「プラグイン」できます。 これにより、ユーザーの学習曲線をなくすこともできます。
* 無効なモジュールのコマンドは表示されません。

このトピックでは、CLI を使用したAdobe CommerceまたはMagento Open Sourceソフトウェアのインストールについて説明します。 設定について詳しくは、 [設定ガイド](../configuration/overview.md).

必要に応じて、インストーラーを複数回実行して、次の操作を実行できます。

* 異なる値を指定

  例えば、Secure Sockets Layer(SSL) 用に Web サーバーを設定した後、インストーラーを実行して SSL オプションを設定できます。

* 以前のインストールでの誤りを修正する
* 別のデータベースインスタンスにAdobe CommerceまたはMagento Open Sourceをインストールする

## インストールを開始する前に

開始する前に、次の手順を実行します。

* お使いのシステムが、 [システム要件](system-requirements.md).

* すべてを完了 [前提条件](prerequisites/overview.md) タスク。

* 最初のインストール手順を完了します。 詳しくは、 [インストールまたはアップグレードのパス](overview.md).

* アプリケーションサーバーにログインした後、 [ファイルシステムの所有者に切り替え](prerequisites/file-system/overview.md).

* 以下を確認します。 [インストールクイックスタート](composer.md) の概要。

>[!NOTE]
>
>Adobe CommerceまたはMagento Open Sourceは、 `bin` サブディレクトリ。

次のようなインストールタスクを完了するには、異なるオプションを指定してインストーラーを複数回実行します。

* 段階的にインストールする：例えば、Secure Sockets Layer(SSL) 用に Web サーバーを設定した後に、インストーラを再実行して SSL オプションを設定できます。

* 以前のインストールでの誤りを修正します。

* 別のデータベースインスタンスにAdobe CommerceまたはMagento Open Sourceをインストールします。

>[!NOTE]
>
>デフォルトでは、同じデータベースインスタンスにソフトウェアをインストールしても、インストーラーはデータベースを上書きしません。 オプションの `cleanup-database` パラメーターを使用してこの動作を変更できます。

関連トピック [更新、再インストール、アンインストール](tutorials/uninstall.md).

### 安全なインストール

{{$include /help/_includes/secure-install.md}}

## インストーラのヘルプコマンド

次のコマンドを実行して、必要な引数の値を検索できます。

| インストーラーの引数 | コマンド |
| ------------------ | ------------------------------- |
| 言語 | bin/magento 情報:language:リスト |
| 通貨 | bin/magento 情報:currency:リスト |
| タイムゾーン | bin/magento 情報:timezone:リスト |

>[!NOTE]
>
>これらのコマンドを実行するとエラーが表示される場合は、「 [インストールの依存関係を更新](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies/).

## コマンドラインからインストールする

install コマンドは、次の形式を使用します。

```bash
bin/magento setup:install --<option>=<value> ... --<option>=<value>
```

次の表に、インストールオプションの名前と値を示します。 インストールコマンドの例については、 [ローカルホストでのインストール例](#sample-localhost-installations).

>[!NOTE]
>
>スペースや特殊文字を含むオプションは、一重引用符または二重引用符で囲む必要があります。

**管理者資格情報：**

次のオプションで、管理者ユーザーのユーザー情報と資格情報を指定します。

管理者ユーザーは、インストール中またはインストール後に作成できます。 インストール中にユーザーを作成する場合は、管理者資格情報の変数がすべて必要です。 詳しくは、 [ローカルホストでのインストール例](#sample-localhost-installations).

次の表に、多くのインストールパラメータを示しますが、すべてのインストールパラメータを示すわけではありません。 完全なリストについては、 [コマンドラインツールリファレンス](https://devdocs.magento.com/guides/v2.4/reference/cli/magento.html).

| 名前 | 値 | 必須？ |
|--- |--- |--- |
| `--admin-firstname` | 管理者ユーザーの名。 | はい |
| `--admin-lastname` | 管理者ユーザーの姓。 | はい |
| `--admin-email` | 管理者ユーザーの電子メールアドレス。 | はい |
| `--admin-user` | 管理者ユーザー名。 | はい |
| `--admin-password` | 管理者ユーザーのパスワード。 パスワードは 7 文字以上で、英字および数字を少なくとも 1 文字含める必要があります。 より長く、より複雑なパスワードを使用することをお勧めします。 パスワード文字列全体を一重引用符で囲みます。 例：`--admin-password='A0b9%t3g'` | はい |

**サイトおよびデータベースの構成オプション：**

| 名前 | 値 | 必須？ |
|--- |--- |--- |
| `--base-url` | 次のいずれかの形式で管理者およびストアフロントにアクセスするために使用するベース URL。<br><br>`http[s]://<host or ip>/<your install dir>/`.<br><br>**注意：** スキーム (http://またはhttps://) と末尾のスラッシュは両方とも必要です。<br><br>`<your install dir>` は、Adobe CommerceまたはMagento Open Sourceソフトウェアをインストールする docroot 相対パスです。 Web サーバーと仮想ホストの設定方法に応じて、パスは magento2 になる場合と空になる場合があります。<br><br>localhost 上のAdobe CommerceまたはMagento Open Sourceにアクセスするには、次のいずれかを使用します。 `http://127.0.0.1/<your install dir>/` または `http://127.0.0.1/<your install dir>/`.<br><br>- `{{base_url}}` これは、仮想ホスト設定または Docker のような仮想化環境で定義されるベース URL を表します。 例えば、ホスト名を持つ仮想ホストを設定する場合、 `magento.example.com`を使用すると、 `--base-url={{base_url}}` また、のような URL を使用して管理者にアクセスします。 `http://magento.example.com/admin`. | はい |
| `--backend-frontname` | Uniform Resource Identifier(URI) を使用して管理者にアクセスできます。 このパラメーターを省略すると、次のパターンのランダムな URI をアプリケーションで生成できます <code>admin_jkhgdfq</code>。<br><br>セキュリティ上の理由から、ランダムな URI を使用することをお勧めします。 ランダムな URI は、ハッカーや悪意のあるソフトウェアが悪用するのを難しくします。<br><br>インストールの最後に URI が表示されます。 後で表示する場合は、 `bin/magento info:adminuri` コマンドを使用します。<br><br>値を入力する場合は、admin や backend などの一般的な単語を使用しないことをお勧めします。 管理 URI には、英数字とアンダースコア文字 (`_`) のみを読み込みます。 | いいえ |
| `--db-host` | 次のいずれかを使用します。<br><br> — データベース・サーバの完全修飾ホスト名または IP アドレス。<br><br>- `localhost` （デフォルト）または `127.0.0.1` データベースサーバーが web server.localhost と同じホスト上にある場合、MySQL クライアントライブラリは UNIX ソケットを使用してデータベースに接続します。 `127.0.0.1` を指定すると、クライアントライブラリは TCP プロトコルを使用します。 ソケットの詳細については、 [PHP PDO_MYSQL ドキュメント](https://www.php.net/manual/en/ref.pdo-mysql.php).<br><br>**注意：** オプションで、ホスト名にwww.example.com:9000などのデータベースサーバーポートを指定できます。 | はい |
| `--db-name` | データベーステーブルをインストールするデータベースインスタンスの名前。<br><br>デフォルトはです。 `magento2`. | はい |
| `--db-user` | データベースインスタンスの所有者のユーザー名。<br><br>デフォルトはです。 `root`. | はい |
| `--db-password` | データベースインスタンスの所有者のパスワード。 | はい |
| `--db-prefix` | 既にデータベーステーブルまたはデータベーステーブルが含まれるデータベースインスタンスにMagento Open Sourceテーブルをインストールする場合にのみ使用してください。<br><br>この場合は、プレフィックスを使用して、このインストール用のテーブルを識別します。 1 台のサーバー上で複数のAdobe CommerceまたはMagento Open Sourceインスタンスを実行し、同じデータベース内のすべてのテーブルを含むお客様もいます。<br><br>プレフィックスの長さは最大 5 文字です。 文字で始まる必要があり、文字、数字、アンダースコア文字のみを含めることができます。<br><br>このオプションを使用すると、お客様は、複数のAdobe CommerceまたはMagento Open Sourceのインストールでデータベースサーバーを共有できます。 | いいえ |
| `--db-ssl-key` | クライアントキーへのパス。 | いいえ |
| `--db-ssl-cert` | クライアント証明書のパス。 | いいえ |
| `--db-ssl-ca` | サーバー証明書のパス。 | いいえ |
| `--language` | 管理およびストアフロントで使用する言語コード。 ( まだ行っていない場合は、 `bin/magento info:language:list` bin ディレクトリから )。 | いいえ |
| `--currency` | ストアフロントで使用するデフォルトの通貨。 ( まだ通貨リストを表示していない場合は、「 `bin/magento info:currency:list` bin ディレクトリから )。 | いいえ |
| `--timezone` | Admin およびストアフロントで使用するデフォルトのタイムゾーン。 ( まだタイムゾーンを表示していない場合は、 `bin/magento info:timezone:list` から `bin/` ディレクトリ ) | いいえ |
| `--use-rewrites` | `1` とは、生成されたリンクに対して、ストアフロントと管理で web サーバーの書き換えを使用することを意味します。<br><br>`0` web サーバーの書き換えを使用できなくします。 これがデフォルトです。 | いいえ |
| `--use-secure` | `1` ストアフロント URL での Secure Sockets Layer(SSL) の使用を有効にします。 このオプションを選択する前に、Web サーバーが SSL をサポートしていることを確認してください。<br><br>`0` は SSL の使用を無効にします。 この場合、他のセキュア URL オプションもすべて 0 と見なされます。 これがデフォルトです。 | いいえ |
| `--base-url-secure` | 管理者およびストアフロントへのアクセスに使用するセキュアベース URL は、次の形式です。 `http[s]://<host or ip>/<your install dir>/` | いいえ |
| `--use-secure-admin` | `1` は、SSL を使用して管理者にアクセスすることを意味します。 このオプションを選択する前に、Web サーバーが SSL をサポートしていることを確認してください。<br><br>`0` は、管理者と共に SSL を使用していないことを意味します。 これがデフォルトです。 | いいえ |
| `--admin-use-security-key` | 1 を指定すると、アプリケーションは、ランダムに生成されたキー値を使用して、管理者およびフォームのページにアクセスします。 これらのキー値は、クロスサイトスクリプトフォージェリ攻撃を防ぐのに役立ちます。 これがデフォルトです。<br><br>`0` キーの使用を無効にします。 | いいえ |
| `--session-save` | 次のいずれかを使用します。<br><br>- `db` を使用して、データベースにセッションデータを格納します。 クラスタ化されたデータベースがある場合は、データベースストレージを選択します。選択しない場合は、ファイルベースのストレージよりも多くのメリットが得られない可能性があります。<br><br>- `files` を使用して、セッションデータをファイルシステムに保存します。 ファイルシステムのアクセスが遅い場合や、クラスタ化されたデータベースが存在する場合、またはセッションデータを Redis に格納する場合を除き、ファイルベースのセッションストレージが適切です。<br><br>- `redis` セッションデータを Redis に保存する。 Redis をデフォルトまたはページキャッシュに使用している場合は、Redis が既にインストールされている必要があります。 Redis のサポートを設定する方法について詳しくは、「セッションストレージの Redis を使用する」を参照してください。 | いいえ |
| `--key` | データベース内の機密データを暗号化するキーがある場合は、そのキーを指定します。 1 つもない場合は、アプリケーションによって生成されます。 | はい |
| `--cleanup-database` | Adobe Commerceまたはデータベースをインストールする前にデータベーステーブルをドロップするには、このMagento Open Sourceーを値なしで指定します。 それ以外の場合、データベースはそのまま残ります。 | いいえ |
| `--db-init-statements` | MySQL 設定の詳細パラメーター。 MySQL データベースへの接続時に、データベース初期化文を使用して実行します。 値を設定する前に、このような参照を参照してください。<br><br>デフォルトはです。 `SET NAMES utf8;`. | いいえ |
| `--sales-order-increment-prefix` | 販売注文のプレフィックスとして使用する文字列値を指定します。 通常、これは、支払プロセッサの一意の注文番号を保証するために使用されます。 | いいえ |

**検索エンジンの設定オプション：**

| 名前 | 値 | 必須？ |
|--- |--- |--- |
| `--search-engine` | 検索エンジンとして使用するElasticsearchまたは OpenSearch のバージョン。 デフォルトはです。 `elasticsearch7`. Elasticsearch5 は非推奨（廃止予定）となったので、お勧めしません。 | いいえ |
| `--elasticsearch-host` | Elasticsearchが実行されているホスト名または IP アドレス。 デフォルトはです。 `localhost`. | いいえ |
| `--elasticsearch-port` | 受信 HTTP リクエストのElasticsearchポート。 デフォルトはです。 `9200`. | いいえ |
| `--elasticsearch-index-prefix` | Elasticsearch検索インデックスを識別するプレフィックス。 デフォルトはです。 `magento2`. | いいえ |
| `--elasticsearch-timeout` | システムがタイムアウトするまでの秒数。 デフォルトはです。 `15`. | いいえ |
| `--elasticsearch-enable-auth` | 認証サーバーでのElasticsearchを有効にします。 デフォルトはです。 `false`. | いいえ |
| `--elasticsearch-username` | サーバーに対して認証するElasticsearchID。 | いいえ（認証が有効になっていない場合） |
| `--elasticsearch-password` | Elasticsearchserver に対して認証するパスワード。 | いいえ（認証が有効になっていない場合） |
| `--opensearch-host` | OpenSearch が実行されているホスト名または IP アドレス。 デフォルトはです。 `localhost`. | いいえ |
| `--opensearch-port` | 受信 HTTP リクエストの OpenSearch ポート。 デフォルトはです。 `9200`. | いいえ |
| `--opensearch-index-prefix` | OpenSearch 検索インデックスを識別するプレフィックス。 デフォルトはです。 `magento2`. | いいえ |
| `--opensearch-timeout` | システムがタイムアウトするまでの秒数。 デフォルトはです。 `15`. | いいえ |
| `--opensearch-enable-auth` | OpenSearch サーバーでの認証を有効にします。 デフォルトはです。 `false`. | いいえ |
| `--opensearch-username` | OpenSearch サーバーに対して認証するユーザー ID。 | いいえ（認証が有効になっていない場合） |
| `--opensearch-password` | OpenSearch サーバーに対する認証用のパスワード。 | いいえ（認証が有効になっていない場合） |

**[!DNL RabbitMQ]設定オプション：**

| 名前 | 値 | 必須？ |
|--- |--- |--- |
| `--amqp-host` | 次を使用しない `--amqp` のインストールを設定していない限り、オプション [!DNL RabbitMQ]. 詳しくは、 [!DNL RabbitMQ] インストールと設定の詳細については、を参照してください。 [!DNL RabbitMQ].<br><br>ホスト名： [!DNL RabbitMQ] がインストールされている。 | いいえ |
| `--amqp-port` | 接続に使用するポート [!DNL RabbitMQ]. デフォルト値は 5672 です。 | いいえ |
| `--amqp-user` | 接続先のユーザー名 [!DNL RabbitMQ]. デフォルトのユーザーを使用しない `guest`. | いいえ |
| `--amqp-password` | 接続用のパスワード [!DNL RabbitMQ]. デフォルトのパスワードを使用しない `guest`. | いいえ |
| `--amqp-virtualhost` | 接続する仮想ホスト [!DNL RabbitMQ]. デフォルトはです。 `/`. | いいえ |
| `--amqp-ssl` | 接続するかどうかを示します [!DNL RabbitMQ]. デフォルトはです。 `false`. 詳しくは、 [!DNL RabbitMQ] の SSL 設定について詳しくは、 [!DNL RabbitMQ]. | いいえ |
| `--consumers-wait-for-messages` | コンシューマーはキューからのメッセージを待つ必要がありますか？ 1 — はい、0 — いいえ | いいえ |

**ロック設定オプション：**

| 名前 | 値 | 必須？ |
|--- |--- |--- |
| `--lock-provider` | プロバイダー名をロックします。<br><br>使用可能なロックプロバイダ： `db`, `zookeeper`, `file`.<br><br>デフォルトのロックプロバイダーは次のとおりです。 `db` | いいえ |
| `--lock-db-prefix` | 使用時にロックの競合を避けるための特定の db プレフィックス `db` プロバイダをロックします。<br><br>デフォルト値は次のとおりです。 `NULL` | いいえ |
| `--lock-zookeeper-host` | 使用時に Zookeeper クラスターに接続するホストとポート `zookeeper` プロバイダをロックします。<br><br>例： `127.0.0.1:2181` | はい、 `--lock-provider=zookeeper` |
| `--lock-zookeeper-path` | Zookeeper がロックを保存するパス。<br><br>デフォルトのパスは次のとおりです。 `/magento/locks` | いいえ |
| `--lock-file-path` | ファイルのロックが保存されるパス。 | はい、 `--lock-provider=file` |

**コンシューマー設定オプション：**

{{$include /help/_includes/cli-consumers.md}}

>[!NOTE]
>
>Adobe CommerceまたはMagento Open Sourceのインストール後にモジュールを有効または無効にするには、 [モジュールの有効化と無効化](tutorials/manage-modules.md).

**機密データ：**

{{$include /help/_includes/sensitive-data.md}}

### ローカルホストでのインストール例

次の例は、様々なオプションを使用してAdobe Commerceをローカルにインストールするコマンドを示しています。

#### 例 1 — 管理者ユーザーアカウントを使用した基本インストール

次の例では、Adobe CommerceまたはMagento Open Sourceを次のオプションと共にインストールします。

* アプリケーションが `magento2` 次の場所にある web サーバーのドキュメントルートを基準とした相対ディレクトリ `localhost` また、管理者へのパスは `admin`の場合は次のようになります。

  ストアフロント URL は `http://127.0.0.1`

* データベース・サーバは、Web サーバと同じホスト上に存在します。

  データベース名はです。 `magento`ユーザー名とパスワードは両方とも `magento`

* サーバー書き換えを使用

* 管理者には次のプロパティがあります。

   * 姓と名は `Magento User`
   * ユーザー名： `admin` パスワードは `admin123`
   * 電子メールアドレス： `user@example.com`

* デフォルトの言語は `en_US` （米国英語）
* デフォルトの通貨は米ドルです
* デフォルトのタイムゾーンは米国中部（アメリカ/シカゴ）です。
* OpenSearch 1.2 がにインストールされている `os-host.example.com` とは、ポート 9200 で接続します。

```bash
magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--admin-firstname=Magento --admin-lastname=User --admin-email=user@example.com \
--admin-user=admin --admin-password=admin123 --language=en_US \
--currency=USD --timezone=America/Chicago --use-rewrites=1 \
--search-engine=opensearch --opensearch-host=os-host.example.com \
--opensearch-port=9200
```

インストールが成功したことを示す次の表示に示すメッセージです。

```terminal
Post installation file permissions check...
For security, remove write permissions from these directories: '/var/www/html/magento2/app/etc'
[Progress: 274 / 274]
[SUCCESS]: Magento installation complete.
[SUCCESS]: Admin Panel URI: /admin_puu71q
```

#### 例 2 — 管理者ユーザーアカウントを使用しない基本インストール

次の例に示すように、管理者ユーザーを作成せずに、Adobe CommerceまたはMagento Open Sourceをインストールできます。

```bash
magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--language=en_US --currency=USD --timezone=America/Chicago --use-rewrites=1 \
--search-engine=opensearch --opensearch-host=os-host.example.com \
--opensearch-port=9200
```

インストールが成功した場合は、次のようなメッセージが表示されます。

```terminal
Post installation file permissions check...
For security, remove write permissions from these directories: '/var/www/html/magento2/app/etc'
[Progress: 274 / 274]
[SUCCESS]: Magento installation complete.
[SUCCESS]: Admin Panel URI: /admin_puu71q
```

インストール後、 `admin:user:create` コマンド：
[管理者の作成または編集](tutorials/admin.md#create-or-edit-an-administrator)

#### 例 3 — 追加のオプションを使用してインストールする

次の例では、Adobe CommerceまたはMagento Open Sourceを次のオプションと共にインストールします。

* アプリケーションが `magento2` 次の場所にある web サーバーのドキュメントルートを基準とした相対ディレクトリ `localhost` また、管理者へのパスは `admin`の場合は次のようになります。

  ストアフロント URL は `http://127.0.0.1`

* データベース・サーバは、Web サーバと同じホスト上に存在します。

  データベース名はです。 `magento`ユーザー名とパスワードは両方とも `magento`

* 管理者には次のプロパティがあります。

   * 姓と名は `Magento User`
   * ユーザー名： `admin` パスワードは `admin123`
   * 電子メールアドレス： `user@example.com`

* デフォルトの言語は `en_US` （米国英語）
* デフォルトの通貨は米ドルです
* デフォルトのタイムゾーンは米国中部（アメリカ/シカゴ）です。
* インストーラーは、テーブルとスキーマをインストールする前に、まずデータベースをクリーンアップします
* 販売注文増分プレフィックスを使用できます `ORD$` ( 特殊文字が含まれるので [`$`]の場合、値を二重引用符で囲む必要があります )
* セッションデータはデータベースに保存されます
* サーバー書き換えを使用
* OpenSearch がにインストールされている `os-host.example.com` とは、ポート 9200 で接続します。

```bash
magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--admin-firstname=Magento --admin-lastname=User --admin-email=user@example.com \
--admin-user=admin --admin-password=admin123 --language=en_US \
--currency=USD --timezone=America/Chicago --cleanup-database \
--sales-order-increment-prefix="ORD$" --session-save=db --use-rewrites=1 \
--search-engine=opensearch --opensearch-host=os-host.example.com \
--opensearch-port=9200
```

>[!NOTE]
>
>コマンドは、1 行で入力するか、前の例のように、 `\` 文字を各行の末尾に配置します。

インストールが成功した場合は、次のようなメッセージが表示されます。

```terminal
Post installation file permissions check...
For security, remove write permissions from these directories: '/var/www/html/magento2/app/etc'
[Progress: 274 / 274]
[SUCCESS]: Magento installation complete.
[SUCCESS]: Admin Panel URI: /admin_puu71q
```
