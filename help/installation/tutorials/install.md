---
title: Adobe Commerceのインストール
description: 所有しているインフラストラクチャにAdobe Commerceをインストールするには、次の手順に従います。
exl-id: 25f3c56e-0654-4f8b-a69d-f4152f68aca3
source-git-commit: 84a20012a81278cc95587ec14281b05330261687
workflow-type: tm+mt
source-wordcount: '2261'
ht-degree: 0%

---

# Adobe Commerceのインストール

開始する前に、次の手順を実行します。

* お使いのシステムが [&#x200B; システム要件 &#x200B;](../system-requirements.md) で説明されている要件を満たしていることを確認します。

* すべての [&#x200B; 前提条件 &#x200B;](../prerequisites/overview.md) タスクを完了します。

* 最初のインストール手順を完了します。 [&#x200B; インストールまたはアップグレードのパス &#x200B;](../overview.md) を参照してください。

* アプリケーションサーバーにログインしたら、[&#x200B; ファイルシステムの所有者に切り替えます &#x200B;](../prerequisites/file-system/overview.md)。

* [&#x200B; コマンドラインインストールの基本を学ぶ &#x200B;](../composer.md) の概要を確認します。

>[!NOTE]
>
>`bin` サブディレクトリからアプリケーションをインストールする必要があります。

インストーラーを複数回実行し、様々なオプションを指定して、次のようなインストールタスクを完了することができます。

* 段階的にインストールする – 例えば、Web サーバーを Secure Sockets Layer （SSL）用に設定した後、インストーラーを再度実行して、SSL オプションを設定できます。

* 以前のインストールでの間違いを修正します。

* 別のデータベースインスタンスにアプリケーションをインストールします。

>[!NOTE]
>
>デフォルトでは、同じデータベースインスタンスにCommerce ソフトウェアをインストールしても、インストーラーによってデータベースが上書きされることはありません。 この動作を変更するには、オプションの `cleanup-database` パラメーターを使用できます。

[&#x200B; 更新、再インストール、アンインストール &#x200B;](uninstall.md) も参照してください。

## 安全なインストール

{{$include /help/_includes/secure-install.md}}

## インストーラーヘルプコマンド

次のコマンドを実行すると、必要な引数の値を検索できます。

| インストーラー引数 | コマンド |
| ------------------ | ------------------------------- |
| 言語 | `magento info:language:list` |
| 通貨 | `magento info:currency:list` |
| タイムゾーン | `magento info:timezone:list` |

>[!NOTE]
>
>これらのコマンドを実行したときにエラーが表示される場合は、[&#x200B; インストールの依存関係の更新 &#x200B;](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies) の説明に従って、インストールの依存関係を更新したことを確認してください。

## コマンドラインからのインストール

インストールコマンドでは、次の形式を使用します。

```bash
magento setup:install --<option>=<value> ... --<option>=<value>
```

次の表に、インストールコマンドなどのインストールオプションの名前と値を示します。 [&#x200B; サンプルローカルホストのインストール &#x200B;](#sample-localhost-installations) を参照してください。

>[!NOTE]
>
>スペースや特殊文字を含むオプションは、一重引用符または二重引用符で囲む必要があります。

**管理者資格情報：**

次のオプションでは、管理者ユーザーのユーザー情報と資格情報を指定します。

Adobe Commerce バージョン 2.2.8 以降では、インストール中またはインストール後に管理者ユーザーを作成できます。 インストール時にユーザーを作成する場合は、すべての管理者資格情報の変数が必要です。 [&#x200B; サンプルローカルホストのインストール &#x200B;](#sample-localhost-installations) を参照してください。

| 名前 | 値 | 必須？ |
|--- |--- |--- |
| `--admin-firstname` | 管理者ユーザーの名。 | はい |
| `--admin-lastname` | 管理者ユーザーの姓。 | はい |
| `--admin-email` | 管理者ユーザーのメールアドレス。 | はい |
| `--admin-user` | 管理者ユーザー名。 | はい |
| `--admin-password` | 管理者ユーザーのパスワード。 パスワードは 7 文字以上で、アルファベットと数字が少なくとも 1 つずつ含まれている必要があります。 より長く、より複雑なパスワードをお勧めします。 パスワード文字列全体を一重引用符で囲みます。 例：`--admin-password='A0b9%t3g'` | はい |

**サイトとデータベースの構成オプション：**

| 名前 | 値 | 必須？ |
|--- |--- |--- |
| `--base-url` | 次のいずれかの形式で管理者およびストアフロントにアクセスするために使用するベース URL:<br><br>`http[s]://<host or ip>/<your install dir>/`。<br><br>**注意：** スキーム（http://またはhttps://）と末尾のスラッシュは両方とも必須です。<br><br>`<your install dir>` は、アプリケーションをインストールするドキュメントルート相対パスです。 Web サーバーと仮想ホストの設定方法に応じて、パスは magento2 になるか、空になります。<br><br>localhost 上のアプリケーションにアクセスするには、`http://127.0.0.1/<your install dir>/` または `http://127.0.0.1/<your install dir>/` を使用します。<br><br> – 仮想ホスト設定または Docker などの仮想化環境によって定義されたベース URL を表す `{{base_url}}`。 例えば、ホスト名がcommerce.example.comの仮想ホストを設定した場合、`--base-url={{base_url}}` を使用してアプリケーションをインストールし、`http://commerce.example.com/admin` のような URL を使用して管理者にアクセスできます。 | はい |
| `--backend-frontname` | 管理者にアクセスするための URI （Uniform Resource Identifier）。 このパラメーターを省略すると、アプリケーションは次のパターンのランダムな URI を生成できます。<code>admin_jkhgdfq</code>。<br><br> セキュリティ上の理由から、ランダムな URI を使用することをお勧めします。 ランダム URI は、ハッカーや悪意のあるソフトウェアが悪用しにくくなります。<br><br>URI はインストールの最後に表示されます。 `magento info:adminuri` コマンドを使用すれば、後でいつでも表示することができます。<br><br> 値を入力する場合は、admin、backend などの一般的な単語を使用しないことをお勧めします。 管理 URI には、英数字とアンダースコア文字（`_`）のみを含めることができます。 | 不可 |
| `--db-host` | 次のいずれかを使用します。<br><br>- データベースサーバーの完全修飾ホスト名または IP アドレス。<br><br>- `localhost` （デフォルト）またはデータベースサーバーが web サーバーと同じホスト上にある場合は `127.0.0.1`。localhost は、MySQL クライアントライブラリが UNIX ソケットを使用してデータベースに接続することを意味します。 `127.0.0.1` は、クライアントライブラリで TCP プロトコルを使用します。 ソケットの詳細については、[PHP PDO_MYSQL のドキュメント &#x200B;](https://www.php.net/manual/en/ref.pdo-mysql.php) を参照してください。<br><br>**注意：** オプションで、www.example.comのようなホスト名でデータベースサーバーポートを指定できます :9000 | はい |
| `--db-name` | データベーステーブルをインストールするデータベースインスタンスの名前。<br><br> デフォルトは `magento2` です。 | はい |
| `--db-user` | データベース・インスタンス所有者のユーザー名。<br><br> デフォルトは `root` です。 | はい |
| `--db-password` | データベースインスタンス所有者のパスワード。 | はい |
| `--db-prefix` | 既にAdobe Commerce テーブルが含まれているデータベースインスタンスにデータベーステーブルをインストールしている場合にのみ、を使用します。<br><br> その場合、プレフィックスを使用して、このインストールのテーブルを識別します。 一部のお客様は、1 台のサーバーで複数のAdobe Commerce インスタンスが実行されており、すべてのテーブルが同じデータベース内にある場合があります。<br><br> プレフィックスの長さは最大 5 文字です。 文字で始まる必要があり、文字、数字、アンダースコア文字のみを含めることができます。<br><br> このオプションを使用すると、複数のインストールでデータベース・サーバを共有できます。 | 不可 |
| `--db-ssl-key` | クライアントキーへのパス。 | 不可 |
| `--db-ssl-cert` | クライアント証明書へのパス。 | 不可 |
| `--db-ssl-ca` | サーバー証明書へのパス。 | 不可 |
| `--language` | 管理およびストアフロントで使用する言語コード。 （まだ実行していない場合は、bin ディレクトリから `magento info:language:list` を入力して、言語コードのリストを表示できます）。 | 不可 |
| `--currency` | ストアフロントで使用するデフォルト通貨。 （まだ行っていない場合は、bin ディレクトリから `magento info:currency:list` と入力して通貨のリストを表示できます）。 | 不可 |
| `--timezone` | 管理およびストアフロントで使用するデフォルトのタイムゾーン。 （まだタイムゾーンリストを表示していない場合は、bin ディレクトリから `magento info:timezone:list` を入力すると、タイムゾーンリストを表示できます）。 | 不可 |
| `--use-rewrites` | つま `1`、ストアフロントおよび管理者で生成されたリンクに対して、web サーバーの書き換えを使用します。<br><br>`0` は、web サーバーの書き換えの使用を無効にします。 これがデフォルトです。 | 不可 |
| `--use-secure` | `1` を使用すると、ストアフロント URL で Secure Sockets Layer （SSL）を使用できます。 このオプションを選択する前に、web サーバーで SSL がサポートされていることを確認してください。<br><br>`0` は SSL の使用を無効にします。 この場合、他のすべてのセキュア URL オプションも 0 と見なされます。 これがデフォルトです。 | 不可 |
| `--base-url-secure` | 管理者およびストアフロントにアクセスするために使用するセキュアなベース URL を次の形式で指定します：`http[s]://<host or ip>/<your install dir>/` | 不可 |
| `--use-secure-admin` | `1` まり、SSL を使用して管理者にアクセスします。 このオプションを選択する前に、web サーバーで SSL がサポートされていることを確認してください。<br><br>`0` れは、管理者で SSL を使用しないことを意味します。 これがデフォルトです。 | 不可 |
| `--admin-use-security-key` | 1 を指定すると、アプリケーションはランダムに生成されたキー値を使用して、管理およびフォームのページにアクセスします。 これらのキー値は、クロスサイトスクリプトフォージェリー攻撃を防ぐのに役立ちます。 これがデフォルトです。<br><br>`0` はキーの使用を無効にします。 | 不可 |
| `--session-save` | 次のいずれかを使用します。<br><br>- `db` を使用して、セッションデータをデータベースに保存します。 クラスター化されたデータベースがある場合は、データベースストレージを選択します。そうしないと、ファイルベースのストレージに比べて大きなメリットがない可能性があります。<br><br>- セッションデータをファイルシステムに保存する `files` ール。 ファイルベースのセッションストレージは、ファイルシステムアクセスが遅い場合、クラスター化されたデータベースがある場合、または Redis にセッションデータを保存する場合を除いて、適切です。<br><br>- セッションデータを Redis に保存する `redis` ール。 デフォルトまたはページキャッシュに Redis を使用している場合は、Redis がインストールされている必要があります。 Redis のサポートの設定に関する詳細は、セッションストレージに Redis を使用するを参照してください。 | 不可 |
| `--key` | キーがある場合は、データベース内の機密データを暗号化するキーを指定します。 ユーザーが定義されていない場合は、自動的に定義されます。 | はい |
| `--cleanup-database` | アプリケーションをインストールする前にデータベーステーブルをドロップするには、このパラメーターに値を指定しません。 それ以外の場合、データベースはそのまま残ります。 | 不可 |
| `--db-init-statements` | MySQL の詳細設定パラメーター。 データベース初期化文を使用して、MySQL データベースへの接続時に実行します。 値を設定する前に、これに類似したリファレンスを参照してください。<br><br> デフォルトは `SET NAMES utf8;` です。 | 不可 |
| `--sales-order-increment-prefix` | 販売注文のプレフィックスとして使用する文字列値を指定します。 通常、これは支払い処理者向けの一意の注文番号を保証するために使用されます。 | 不可 |

>[!TIP]
>
>インストール中にリモート記憶域サービスを有効にするには、[&#x200B; 構成ガイド &#x200B;](../../configuration/remote-storage/remote-storage.md) の _リモート記憶域の構成_ を参照してください。

**検索エンジン設定オプション：**

| 名前 | 値 | 必須？ |
|--- |--- |--- |
| `--search-engine` | 検索エンジンのバージョン。 使用可能な値は、`elasticsearch7`、`elasticsearch6`、`elasticsearch5` です。 デフォルトは `elasticsearch7` です。 OpenSearch を検索エンジンとしてインストールした場合は、値 `elasticsearch7` を指定します。 Elasticsearch 5 は非推奨（廃止予定）となったので、お勧めしません。 | 不可 |
| `--elasticsearch-host` | 検索エンジンが実行されているホスト名または IP アドレス。 デフォルトは `localhost` です。 | 不可 |
| `--elasticsearch-port` | 受信 HTTP リクエストのポート。 デフォルトは `9200` です。 | 不可 |
| `--elasticsearch-index-prefix` | 検索インデックスを識別するプレフィックス。 デフォルトは `magento2` です。 | 不可 |
| `--elasticsearch-timeout` | システムがタイムアウトするまでの秒数。 デフォルトは `15` です。 | 不可 |
| `--elasticsearch-enable-auth` | 検索エンジン サーバーでの認証を有効にします。 デフォルトは `false` です。 | 不可 |
| `--elasticsearch-username` | 認証するユーザー ID | いいえ（認証が有効になっていない場合） |
| `--elasticsearch-password` | 認証するパスワード | いいえ（認証が有効になっていない場合） |

**[!DNL RabbitMQ]設定オプション：**

| 名前 | 値 | 必須？ |
|--- |--- |--- |
| `--amqp-host` | `--amqp` のインストールを既にセットアップしていない限り、[!DNL RabbitMQ] のオプションは使用しないでください。 [!DNL RabbitMQ] のインストールと設定について詳しくは、[!DNL RabbitMQ] のインストールを参照してください。<br><br>[!DNL RabbitMQ] がインストールされているホスト名。 | 不可 |
| `--amqp-port` | [!DNL RabbitMQ] への接続に使用するポート。 デフォルトは 5672 です。 | 不可 |
| `--amqp-user` | [!DNL RabbitMQ] に接続するためのユーザー名。 デフォルトのユーザー `guest` は使用しないでください。 | 不可 |
| `--amqp-password` | [!DNL RabbitMQ] に接続するためのパスワード デフォルトのパスワード `guest` は使用しないでください。 | 不可 |
| `--amqp-virtualhost` | [!DNL RabbitMQ] に接続するための仮想ホスト。 デフォルトは `/` です。 | 不可 |
| `--amqp-ssl` | [!DNL RabbitMQ] に接続するかどうかを示します。 デフォルトは `false` です。 [!DNL RabbitMQ] の SSL の設定については、[!DNL RabbitMQ] を参照してください。 | 不可 |
| `--consumers-wait-for-messages` | 消費者はキューからのメッセージを待つ必要がありますか？ 1 – はい、0 – いいえ | 不可 |

**ActiveMQ Artemis 設定オプション：**

>[!NOTE]
>
>ActiveMQ Artemis は、Adobe Commerce 2.4.6 以降のバージョンで導入されました。

| 名前 | 値 | 必須？ |
|--- |--- |--- |
| `--stomp-host` | ActiveMQ Artemis のインストールをセットアップ済みでない限り、`--stomp` のオプションは使用しないでください。 ActiveMQ Artemis のインストールと構成の詳細については、「ActiveMQ Artemis のインストール」を参照してください。<br><br>ActiveMQ Artemis がインストールされているホスト名。 | 不可 |
| `--stomp-port` | ActiveMQ Artemis への接続に使用するポートです。 デフォルトは 61613 です。 | 不可 |
| `--stomp-user` | ActiveMQ Artemis に接続するためのユーザー名。 デフォルトのユーザー `artemis` は使用しないでください。 | 不可 |
| `--stomp-password` | ActiveMQ Artemis に接続するためのパスワードです。 デフォルトのパスワード `artemis` は使用しないでください。 | 不可 |
| `--stomp-ssl` | SSL を使用して ActiveMQ Artemis に接続するかどうかを示します。 デフォルトは `false` です。 ActiveMQ Artemis の SSL の設定については、ActiveMQ Artemis を参照してください。 | 不可 |
| `--consumers-wait-for-messages` | 消費者はキューからのメッセージを待つ必要がありますか？ 1 – はい、0 – いいえ | 不可 |

**リモートストレージオプション：**

| 名前 | 説明 | 必須？ |
|--- |--- |--- |
| `remote-storage-driver` | アダプター名 <br> 使用可能な値：<br>**file**: リモートストレージを無効にし、ローカルファイルシステムを使用します <br>**aws-s3**: [Amazon Simple Storage Service （Amazon S3）を使用 &#x200B;](https://aws.amazon.com/s3/) | 不可 |
| `remote-storage-bucket` | オブジェクトストレージまたはコンテナ名 | 不可 |
| `remote-storage-prefix` | オプションのプレフィックス（オブジェクトストレージ内の場所） | 不可 |
| `remote-storage-region` | 地域名 | 不可 |
| `remote-storage-key` | オプションのアクセスキー | 不可 |
| `remote-storage-secret` | オプションの秘密鍵 | 不可 |

**ロック設定オプション：**

| 名前 | 値 | 必須？ |
|--- |--- |--- |
| `--lock-provider` | プロバイダ名をロックします。<br><br> 使用可能なロック プロバイダー：`db`、`zookeeper`、`file`。<br><br> デフォルトのロックプロバイダー：`db` | 不可 |
| `--lock-db-prefix` | ロックプロバイダーの使用時にロックの競合を回避するため `db` 特定の db プレフィックス。<br><br> デフォルト値：`NULL` | 不可 |
| `--lock-zookeeper-host` | ロックプロバイダーを使用する際に Zookeeper クラスターに接続するホスト `zookeeper` ポート。<br><br> 例：`127.0.0.1:2181` | はい（`--lock-provider=zookeeper` を設定した場合） |
| `--lock-zookeeper-path` | Zookeeper がロックを保存するパス。<br><br> デフォルトパスは `/magento/locks` です。 | 不可 |
| `--lock-file-path` | ファイルのロックが保存されるパス。 | はい（`--lock-provider=file` を設定した場合） |

**コンシューマー設定オプション：**

{{$include /help/_includes/cli-consumers.md}}

>[!NOTE]
>
>アプリケーションのインストール後にモジュールを有効または無効にする方法については、[&#x200B; モジュールの有効/無効 &#x200B;](manage-modules.md) を参照してください。

**機密データ：**

{{$include /help/_includes/sensitive-data.md}}

### ローカルホストのインストールのサンプル

次の例は、Adobe Commerceを様々なオプションを使用してローカルにインストールするコマンドを示しています。

#### 例 1 – 管理者ユーザーアカウントを使用した基本インストール

次の例では、次のオプションを使用してアプリケーションをインストールします。

* アプリケーションは、`magento2` 上の Web サーバーの docroot に対する相対パスである `localhost` ディレクトリにインストールされ、Admin へのパスは `admin` になります。したがって、次のようになります。

  ストアフロント URL は `http://127.0.0.1` です

* データベース・サーバは、Web サーバと同じホスト上にあります。

  データベース名は `magento`、ユーザー名とパスワードは両方とも `magento` です

* サーバーの書き換えを使用

* 管理者には次のプロパティがあります。

   * 氏名は `Commerce User`
   * ユーザー名は `admin`、パスワードは `admin123`
   * 電子メール アドレスは `user@example.com` です

* デフォルト言語は `en_US` （英語（米国））
* デフォルトの通貨は米国ドルです
* デフォルトのタイムゾーンは米国中部（アメリカ/シカゴ）です
* Elasticsearch 7 は `es-host.example.com` にインストールされ、ポート 9200 に接続します。

```bash
magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--admin-firstname=Commerce --admin-lastname=User --admin-email=user@example.com \
--admin-user=admin --admin-password=admin123 --language=en_US \
--currency=USD --timezone=America/Chicago --use-rewrites=1 \
--search-engine=elasticsearch7 --elasticsearch-host=es-host.example.com \
--elasticsearch-port=9200
```

次のようなメッセージが表示され、インストールが成功したことが示されます。

```
Post installation file permissions check...
For security, remove write permissions from these directories: '/var/www/html/magento2/app/etc'
[Progress: 274 / 274]
[SUCCESS]: Magento installation complete.
[SUCCESS]: Admin Panel URI: /admin_puu71q
```

#### 例 2 – 管理者ユーザーアカウントを使用しない基本インストール

次の例に示すように、管理者ユーザーを作成せずにアプリケーションをインストールできます。

```bash
magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--language=en_US --currency=USD --timezone=America/Chicago --use-rewrites=1 \
--search-engine=elasticsearch7 --elasticsearch-host=es-host.example.com \
--elasticsearch-port=9200
```

インストールが成功すると、次のようなメッセージが表示されます。

```
Post installation file permissions check...
For security, remove write permissions from these directories: '/var/www/html/magento2/app/etc'
[Progress: 274 / 274]
[SUCCESS]: Magento installation complete.
[SUCCESS]: Admin Panel URI: /admin_puu71q
```

インストール後、`admin:user:create` のコマンドを使用して管理者ユーザーを作成できます。
[&#x200B; 管理者の作成または編集 &#x200B;](admin.md#create-or-edit-an-administrator)

#### 例 3 – 追加オプションを使用したインストール

次の例では、次のオプションを使用してアプリケーションをインストールします。

* Magapplication は、`magento2` 上の web サーバーの docroot に対する相対パスである `localhost` ディレクトリにインストールされ、Admin へのパスは `admin` です。したがって、次のようになります。

  ストアフロント URL は `http://127.0.0.1` です

* データベース・サーバは、Web サーバと同じホスト上にあります。

  データベース名は `magento`、ユーザー名とパスワードは両方とも `magento` です

* 管理者には次のプロパティがあります。

   * 氏名は `Commerce User`
   * ユーザー名は `admin`、パスワードは `admin123`
   * 電子メール アドレスは `user@example.com` です

* デフォルト言語は `en_US` （英語（米国））
* デフォルトの通貨は米国ドルです
* デフォルトのタイムゾーンは米国中部（アメリカ/シカゴ）です
* インストーラーは、まずデータベースをクリーンアップしてから、テーブルとスキーマをインストールします
* `ORD$` の受注増分プリフィックスを使用します（特殊文字 [`$`] が含まれているため、値は二重引用符で囲む必要があります）
* セッションデータはデータベースに保存されます
* サーバーの書き換えを使用
* Elasticsearch 7 は `es-host.example.com` にインストールされ、ポート 9200 に接続します。

```bash
magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--admin-firstname=Commerce --admin-lastname=User --admin-email=user@example.com \
--admin-user=admin --admin-password=admin123 --language=en_US \
--currency=USD --timezone=America/Chicago --cleanup-database \
--sales-order-increment-prefix="ORD$" --session-save=db --use-rewrites=1 \
--search-engine=elasticsearch7 --elasticsearch-host=es-host.example.com \
--elasticsearch-port=9200
```

>[!NOTE]
>
>コマンドは、1 行で入力するか、前の例のように、各行の末尾に `\` 文字を付けて入力する必要があります。

インストールが成功すると、次のようなメッセージが表示されます。

```
Post installation file permissions check...
For security, remove write permissions from these directories: '/var/www/html/magento2/app/etc'
[Progress: 274 / 274]
[SUCCESS]: Magento installation complete.
[SUCCESS]: Admin Panel URI: /admin_puu71q
```

#### 例 4:ActiveMQ Artemis を使用したインストール

次の例は、ActiveMQ Artemis をメッセージブローカーとして使用してAdobe Commerceをインストールする方法を示しています。

```bash
magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--admin-firstname=Commerce --admin-lastname=User --admin-email=user@example.com \
--admin-user=admin --admin-password=admin123 --language=en_US \
--currency=USD --timezone=America/Chicago --use-rewrites=1 \
--search-engine=elasticsearch7 --elasticsearch-host=es-host.example.com \
--elasticsearch-port=9200 --stomp-host=localhost --stomp-port=61613 \
--stomp-user=artemis --stomp-password=artemis
```

>[!NOTE]
>
>ActiveMQ Artemis のインストールには、Adobe Commerce 2.4.6 以降が必要です。

>[!TIP]
>
>1 つのユーザーアカウントでアプリケーションサーバーにアクセスする場合は、[umask の設定 &#x200B;](../next-steps/set-umask.md) を参照してください。 このタイプの設定は、共有ホスティングで一般的です。

<!-- Last updated from includes: 2024-04-16 09:42:31 -->
