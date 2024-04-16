---
title: Adobe Commerceのインストール
description: 所有しているインフラストラクチャにAdobe CommerceまたはMagento Open Sourceをインストールするには、次の手順に従います。
exl-id: 25f3c56e-0654-4f8b-a69d-f4152f68aca3
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '2102'
ht-degree: 0%

---

# Adobe Commerceのインストール

開始する前に、次の手順を実行します。

* お使いのシステムがに記載されている要件を満たしていることを確認します。 [必要システム構成](../system-requirements.md).

* すべて完了 [前提条件](../prerequisites/overview.md) 件のタスク。

* 最初のインストール手順を完了します。 参照： [インストールまたはアップグレードのパス](../overview.md).

* アプリケーションサーバーにログインした後、 [ファイルシステムの所有者に切り替える](../prerequisites/file-system/overview.md).

* をレビュー [コマンドラインインストールの基本を学ぶ](../composer.md) の概要。

>[!NOTE]
>
>からアプリケーションをインストールする必要があります `bin` サブディレクトリ。

インストーラーを複数回実行し、様々なオプションを指定して、次のようなインストールタスクを完了することができます。

* 段階的にインストールする – 例えば、Web サーバーを Secure Sockets Layer （SSL）用に設定した後、インストーラーを再度実行して、SSL オプションを設定できます。

* 以前のインストールでの間違いを修正します。

* 別のデータベースインスタンスにアプリケーションをインストールします。

>[!NOTE]
>
>デフォルトでは、同じデータベースインスタンスにCommerce ソフトウェアをインストールしても、インストーラーによってデータベースが上書きされることはありません。 オプションのを使用できます `cleanup-database` この動作を変更するパラメーター。

関連トピック [更新、再インストール、アンインストール](uninstall.md).

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
>これらのコマンドを実行したときにエラーが表示される場合は、で説明されているように、インストールの依存関係を更新したことを確認してください [インストールの依存関係の更新](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies/).

## コマンドラインからのインストール

インストールコマンドでは、次の形式を使用します。

```bash
magento setup:install --<option>=<value> ... --<option>=<value>
```

次の表に、インストールコマンドなどのインストールオプションの名前と値を示します。 参照： [ローカルホストのインストールのサンプル](#sample-localhost-installations).

>[!NOTE]
>
>スペースや特殊文字を含むオプションは、一重引用符または二重引用符で囲む必要があります。

**管理者の資格情報：**

次のオプションでは、管理者ユーザーのユーザー情報と資格情報を指定します。

Adobe Commerce バージョン 2.2.8 以降では、インストール中またはインストール後に管理者ユーザーを作成できます。 インストール時にユーザーを作成する場合は、すべての管理者資格情報の変数が必要です。 参照： [ローカルホストのインストールのサンプル](#sample-localhost-installations).

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
| `--base-url` | 管理者およびストアフロントにアクセスするために使用するベース URL を次の形式のいずれかで指定します。<br><br>`http[s]://<host or ip>/<your install dir>/`.<br><br>**注意：** スキーム（http://またはhttps://）と末尾のスラッシュは両方とも必須です。<br><br>`<your install dir>` は、アプリケーションをインストールするドキュメントルートの相対パスです。 Web サーバーと仮想ホストの設定方法に応じて、パスは magento2 になるか、空になります。<br><br>localhost 上のアプリケーションにアクセスするには、次のいずれかを使用します `http://127.0.0.1/<your install dir>/` または `http://127.0.0.1/<your install dir>/`.<br><br>- `{{base_url}}` これは、仮想ホスト設定または Docker などの仮想化環境で定義されたベース URL を表します。 例えば、ホスト名がcommerce.example.comの仮想ホストを設定した場合、次を使用してアプリケーションをインストールできます `--base-url={{base_url}}` 次のような URL で管理者にアクセスします。 `http://commerce.example.com/admin`. | はい |
| `--backend-frontname` | 管理者にアクセスするための URI （Uniform Resource Identifier）。 このパラメーターを省略すると、次のパターンのランダムな URI をアプリケーションで生成できます <code>admin_jkhgdfq</code>。<br><br>セキュリティ上の理由から、ランダムな URI を使用することをお勧めします。 ランダム URI は、ハッカーや悪意のあるソフトウェアが悪用しにくくなります。<br><br>インストールの最後に URI が表示されます。 後で次のコマンドを使用して表示することができます。 `magento info:adminuri` コマンド。<br><br>値を入力する場合は、admin、backend などの一般的な単語を使用しないことをお勧めします。 管理 URI には、英数字とアンダースコア文字（`_`）のみ。 | 不可 |
| `--db-host` | 次のいずれかを使用します。<br><br>- データベースサーバーの完全修飾ホスト名または IP アドレス。<br><br>- `localhost` （デフォルト）または `127.0.0.1` データベースサーバーが web サーバーと同じホスト上にある場合。localhost は、MySQL クライアントライブラリが UNIX ソケットを使用してデータベースに接続することを意味します。 `127.0.0.1` クライアントライブラリで TCP プロトコルを使用します。 ソケットの詳細については、 [PHP PDO_MYSQL ドキュメント](https://www.php.net/manual/en/ref.pdo-mysql.php).<br><br>**注意：** オプションで、www.example.com:9000のようなホスト名でデータベースサーバーポートを指定できます。 | はい |
| `--db-name` | データベーステーブルをインストールするデータベースインスタンスの名前。<br><br>デフォルトは `magento2`. | はい |
| `--db-user` | データベース・インスタンス所有者のユーザー名。<br><br>デフォルトは `root`. | はい |
| `--db-password` | データベースインスタンス所有者のパスワード。 | はい |
| `--db-prefix` | Adobe CommerceまたはMagento Open Sourceテーブルが既に含まれているデータベースインスタンスにデータベーステーブルをインストールしている場合にのみ、を使用します。<br><br>その場合は、プレフィックスを使用して、このインストールのテーブルを識別します。 一部のお客様は、1 台のサーバーで複数のAdobe Commerce インスタンスが実行されており、すべてのテーブルが同じデータベース内にある場合があります。<br><br>プレフィックスの長さは最大 5 文字です。 文字で始まる必要があり、文字、数字、アンダースコア文字のみを含めることができます。<br><br>このオプションを使用すると、複数のインストールでデータベース・サーバを共有できます。 | 不可 |
| `--db-ssl-key` | クライアントキーへのパス。 | 不可 |
| `--db-ssl-cert` | クライアント証明書へのパス。 | 不可 |
| `--db-ssl-ca` | サーバー証明書へのパス。 | 不可 |
| `--language` | 管理およびストアフロントで使用する言語コード。 （言語コードのリストをまだ表示していない場合は、次のように入力して表示できます。 `magento info:language:list` bin ディレクトリから）。 | 不可 |
| `--currency` | ストアフロントで使用するデフォルト通貨。 （まだ行っていない場合は、次のように入力して通貨のリストを表示できます `magento info:currency:list` bin ディレクトリから）。 | 不可 |
| `--timezone` | 管理およびストアフロントで使用するデフォルトのタイムゾーン。 （タイムゾーンのリストをまだ表示していない場合は、次のように入力して表示できます。 `magento info:timezone:list` bin ディレクトリから）。 | 不可 |
| `--use-rewrites` | `1` つまり、ストアフロントおよび管理者で生成されたリンクに対して、web サーバーの書き換えを使用します。<br><br>`0` web サーバーの書き換えの使用を無効にします。 これがデフォルトです。 | 不可 |
| `--use-secure` | `1` ストアフロント URL での Secure Sockets Layer （SSL）の使用を有効にします。 このオプションを選択する前に、web サーバーで SSL がサポートされていることを確認してください。<br><br>`0` は SSL の使用を無効にします。 この場合、他のすべてのセキュア URL オプションも 0 と見なされます。 これがデフォルトです。 | 不可 |
| `--base-url-secure` | 管理者およびストアフロントにアクセスするために使用するセキュアなベース URL を次の形式で指定します。 `http[s]://<host or ip>/<your install dir>/` | 不可 |
| `--use-secure-admin` | `1` は、SSL を使用して管理者にアクセスすることを意味します。 このオプションを選択する前に、web サーバーで SSL がサポートされていることを確認してください。<br><br>`0` は、管理者で SSL を使用しないことを意味します。 これがデフォルトです。 | 不可 |
| `--admin-use-security-key` | 1 を指定すると、アプリケーションはランダムに生成されたキー値を使用して、管理およびフォームのページにアクセスします。 これらのキー値は、クロスサイトスクリプトフォージェリー攻撃を防ぐのに役立ちます。 これがデフォルトです。<br><br>`0` キーの使用を無効にします。 | 不可 |
| `--session-save` | 次のいずれかを使用します。<br><br>- `db` セッションデータをデータベースに保存します。 クラスター化されたデータベースがある場合は、データベースストレージを選択します。そうしないと、ファイルベースのストレージに比べて大きなメリットがない可能性があります。<br><br>- `files` セッションデータをファイルシステムに格納する。 ファイルベースのセッションストレージは、ファイルシステムアクセスが遅い場合、クラスター化されたデータベースがある場合、または Redis にセッションデータを保存する場合を除いて、適切です。<br><br>- `redis` セッションデータを Redis に保存します。 デフォルトまたはページキャッシュに Redis を使用している場合は、Redis がインストールされている必要があります。 Redis のサポートの設定に関する詳細は、セッションストレージに Redis を使用するを参照してください。 | 不可 |
| `--key` | キーがある場合は、データベース内の機密データを暗号化するキーを指定します。 ユーザーが定義されていない場合は、自動的に定義されます。 | はい |
| `--cleanup-database` | アプリケーションをインストールする前にデータベーステーブルをドロップするには、このパラメーターに値を指定しません。 それ以外の場合、データベースはそのまま残ります。 | 不可 |
| `--db-init-statements` | MySQL の詳細設定パラメーター。 データベース初期化文を使用して、MySQL データベースへの接続時に実行します。 値を設定する前に、これに類似したリファレンスを参照してください。<br><br>デフォルトは `SET NAMES utf8;`. | 不可 |
| `--sales-order-increment-prefix` | 販売注文のプレフィックスとして使用する文字列値を指定します。 通常、これは支払い処理者向けの一意の注文番号を保証するために使用されます。 | 不可 |

>[!TIP]
>
>インストール中にリモート記憶域サービスを有効にするには、を参照してください。 [リモートストレージの設定](../../configuration/remote-storage/remote-storage.md) が含まれる _設定ガイド_.

**検索エンジン設定オプション：**

| 名前 | 値 | 必須？ |
|--- |--- |--- |
| `--search-engine` | 検索エンジンのバージョン。 使用可能な値は次のとおりです `elasticsearch7`, `elasticsearch6`、および `elasticsearch5`. デフォルトはです `elasticsearch7`. OpenSearch を検索エンジンとしてインストールしている場合は、値を指定します `elasticsearch7`. Elasticsearch 5 は非推奨（廃止予定）となったので、お勧めしません。 | 不可 |
| `--elasticsearch-host` | 検索エンジンが実行されているホスト名または IP アドレス。 デフォルトはです `localhost`. | 不可 |
| `--elasticsearch-port` | 受信 HTTP リクエストのポート。 デフォルトはです `9200`. | 不可 |
| `--elasticsearch-index-prefix` | 検索インデックスを識別するプレフィックス。 デフォルトはです `magento2`. | 不可 |
| `--elasticsearch-timeout` | システムがタイムアウトするまでの秒数。 デフォルトはです `15`. | 不可 |
| `--elasticsearch-enable-auth` | 検索エンジン サーバーでの認証を有効にします。 デフォルトはです `false`. | 不可 |
| `--elasticsearch-username` | 認証するユーザー ID | いいえ（認証が有効になっていない場合） |
| `--elasticsearch-password` | 認証するパスワード | いいえ（認証が有効になっていない場合） |

**[!DNL RabbitMQ]設定オプション：**

| 名前 | 値 | 必須？ |
|--- |--- |--- |
| `--amqp-host` | を使用しないでください。 `--amqp` のインストールを既に設定していない場合のオプション [!DNL RabbitMQ]. 参照： [!DNL RabbitMQ] インストールと設定の詳細については、インストールを参照してください [!DNL RabbitMQ].<br><br>ホスト名 [!DNL RabbitMQ] がインストールされました。 | 不可 |
| `--amqp-port` | への接続に使用するポート [!DNL RabbitMQ]. デフォルトは 5672 です。 | 不可 |
| `--amqp-user` | に接続するためのユーザー名 [!DNL RabbitMQ]. デフォルトユーザーを使用しない `guest`. | 不可 |
| `--amqp-password` | に接続するためのパスワード [!DNL RabbitMQ]. デフォルトのパスワードを使用しない `guest`. | 不可 |
| `--amqp-virtualhost` | 接続先の仮想ホスト [!DNL RabbitMQ]. デフォルトはです `/`. | 不可 |
| `--amqp-ssl` | 接続先を示します [!DNL RabbitMQ]. デフォルトはです `false`. 参照： [!DNL RabbitMQ] の SSL の設定について [!DNL RabbitMQ]. | 不可 |
| `--consumers-wait-for-messages` | 消費者はキューからのメッセージを待つ必要がありますか？ 1 – はい、0 – いいえ | 不可 |

**リモートストレージオプション：**

| 名前 | 説明 | 必須？ |
|--- |--- |--- |
| `remote-storage-driver` | アダプター名<br>使用可能な値：<br>**ファイル**：リモートストレージを無効にし、ローカルファイルシステムを使用します。<br>**aws-s3**：を使用します [Amazon Simple Storage Service （Amazon S3）](https://aws.amazon.com/s3/) | 不可 |
| `remote-storage-bucket` | オブジェクトストレージまたはコンテナ名 | 不可 |
| `remote-storage-prefix` | オプションのプレフィックス（オブジェクトストレージ内の場所） | 不可 |
| `remote-storage-region` | 地域名 | 不可 |
| `remote-storage-key` | オプションのアクセスキー | 不可 |
| `remote-storage-secret` | オプションの秘密鍵 | 不可 |

**ロック設定オプション：**

| 名前 | 値 | 必須？ |
|--- |--- |--- |
| `--lock-provider` | プロバイダ名をロックします。<br><br>使用可能なロック プロバイダー： `db`, `zookeeper`, `file`.<br><br>デフォルトのロックプロバイダーは次のとおりです。 `db` | 不可 |
| `--lock-db-prefix` | を使用する際にロックの競合を回避するための特定の db プレフィックス `db` プロバイダをロックします。<br><br>デフォルト値は次のとおりです。 `NULL` | 不可 |
| `--lock-zookeeper-host` | 使用時に Zookeeper クラスターに接続するホストおよびポート `zookeeper` プロバイダをロックします。<br><br>例： `127.0.0.1:2181` | はい（設定する場合） `--lock-provider=zookeeper` |
| `--lock-zookeeper-path` | Zookeeper がロックを保存するパス。<br><br>デフォルトのパスはです。 `/magento/locks` | 不可 |
| `--lock-file-path` | ファイルのロックが保存されるパス。 | はい（設定する場合） `--lock-provider=file` |

**コンシューマー設定オプション：**

{{$include /help/_includes/cli-consumers.md}}

>[!NOTE]
>
>アプリケーションのインストール後にモジュールを有効または無効にするには、を参照してください。 [モジュールの有効化と無効化](manage-modules.md).

**機密データ：**

{{$include /help/_includes/sensitive-data.md}}

### ローカルホストのインストールのサンプル

次の例は、Adobe Commerceを様々なオプションを使用してローカルにインストールするコマンドを示しています。

#### 例 1 – 管理者ユーザーアカウントを使用した基本インストール

次の例では、次のオプションを使用してアプリケーションをインストールします。

* アプリケーションは `magento2` の web サーバーのドキュメントルートに相対したディレクトリ `localhost` また、管理者へのパスはです `admin`したがって、

  ストアフロント URL はです `http://127.0.0.1`

* データベース・サーバは、Web サーバと同じホスト上にあります。

  データベース名は `magento`、およびユーザー名とパスワードは両方とも `magento`

* サーバーの書き換えを使用

* 管理者には次のプロパティがあります。

   * 氏名は `Commerce User`
   * ユーザー名： `admin` パスワードはです `admin123`
   * 電子メール アドレス： `user@example.com`

* デフォルト言語はです。 `en_US` （米国英語）
* デフォルトの通貨は米国ドルです
* デフォルトのタイムゾーンは米国中部（アメリカ/シカゴ）です
* Elasticsearch 7 はにインストールされています `es-host.example.com` ポート 9200 で接続します。

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

```terminal
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

```terminal
Post installation file permissions check...
For security, remove write permissions from these directories: '/var/www/html/magento2/app/etc'
[Progress: 274 / 274]
[SUCCESS]: Magento installation complete.
[SUCCESS]: Admin Panel URI: /admin_puu71q
```

インストール後、を使用して管理者ユーザーを作成できます。 `admin:user:create` コマンド：
[管理者の作成または編集](admin.md#create-or-edit-an-administrator)

#### 例 3 – 追加オプションを使用したインストール

次の例では、次のオプションを使用してアプリケーションをインストールします。

* Magapplication は `magento2` の web サーバーのドキュメントルートに相対したディレクトリ `localhost` また、管理者へのパスはです `admin`したがって、

  ストアフロント URL はです `http://127.0.0.1`

* データベース・サーバは、Web サーバと同じホスト上にあります。

  データベース名は `magento`、およびユーザー名とパスワードは両方とも `magento`

* 管理者には次のプロパティがあります。

   * 氏名は `Commerce User`
   * ユーザー名： `admin` パスワードはです `admin123`
   * 電子メール アドレス： `user@example.com`

* デフォルト言語はです。 `en_US` （米国英語）
* デフォルトの通貨は米国ドルです
* デフォルトのタイムゾーンは米国中部（アメリカ/シカゴ）です
* インストーラーは、まずデータベースをクリーンアップしてから、テーブルとスキーマをインストールします
* を使用します `ORD$` 販売注文の増分プレフィックス （特殊文字が含まれているため） [`$`]（値は二重引用符で囲む必要があります）
* セッションデータはデータベースに保存されます
* サーバーの書き換えを使用
* Elasticsearch 7 はにインストールされています `es-host.example.com` ポート 9200 で接続します。

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
>コマンドは、1 行で入力するか、前述の例のように、 `\` 各行の末尾の文字。

インストールが成功すると、次のようなメッセージが表示されます。

```terminal
Post installation file permissions check...
For security, remove write permissions from these directories: '/var/www/html/magento2/app/etc'
[Progress: 274 / 274]
[SUCCESS]: Magento installation complete.
[SUCCESS]: Admin Panel URI: /admin_puu71q
```

>[!TIP]
>
>1 つのユーザーアカウントでアプリケーションサーバーにアクセスする場合は、を参照してください [umask を設定](../next-steps/set-umask.md). このタイプの設定は、共有ホスティングで一般的です。
