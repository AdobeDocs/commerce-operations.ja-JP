---
title: Adobe Commerceのインストール
description: 所有しているインフラストラクチャにAdobe Commerceをインストールするには、次の手順に従います。
exl-id: 25f3c56e-0654-4f8b-a69d-f4152f68aca3
source-git-commit: 319f3232d1ba5f5ed7cdd10ce85b9d7ffbeec89a
workflow-type: tm+mt
source-wordcount: '2281'
ht-degree: 0%

---

# Adobe Commerceのインストール

開始する前に、次の手順を実行します。

* お使いのシステムが、[&#x200B; システム要件](../system-requirements.md)で説明されている要件を満たしていることを確認します。

* すべての[前提条件](../prerequisites/overview.md) タスクを完了します。

* 最初のインストール手順を完了します。 [&#x200B; インストールまたはアップグレードのパス &#x200B;](../overview.md)を参照してください。

* アプリケーションサーバーにログインした後、[&#x200B; ファイルシステム所有者](../prerequisites/file-system/overview.md)に切り替えます。

* 「[&#x200B; コマンドラインインストールを開始する](../composer.md)」の概要を確認します。

>[!NOTE]
>
>アプリケーションを`bin` サブディレクトリからインストールする必要があります。

インストーラーを複数回実行して、次のようなインストールタスクを完了できます。

* 段階的なインストール – 例えば、Web サーバーをSecure Sockets Layer （SSL）用に設定した後、インストーラーを再度実行してSSL オプションを設定できます。

* 以前のインストールで発生したエラーを修正します。

* アプリケーションを別のデータベースインスタンスにインストールします。

>[!NOTE]
>
>デフォルトでは、同じデータベースインスタンスにCommerce ソフトウェアをインストールしても、インストーラーはデータベースを上書きしません。 オプションの`cleanup-database` パラメーターを使用して、この動作を変更できます。

[更新、再インストール、アンインストール &#x200B;](uninstall.md)も参照してください。

## 安全なインストール

{{$include /help/_includes/secure-install.md}}

## インストーラーヘルプコマンド

次のコマンドを実行して、必須の引数の値を検索できます。

| インストーラー引数 | コマンド |
| ------------------ | ------------------------------- |
| 言語 | `magento info:language:list` |
| 通貨 | `magento info:currency:list` |
| タイムゾーン | `magento info:timezone:list` |

>[!NOTE]
>
>これらのコマンドを実行するとエラーが表示される場合は、[&#x200B; インストール依存関係の更新](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies)で説明したように、インストール依存関係を更新したことを確認してください。

## コマンドラインからインストール

install コマンドでは、次の形式が使用されます。

```shell
magento setup:install --<option>=<value> ... --<option>=<value>
```

次の表に、インストールオプションの名前と値（インストールコマンドなど）を示します。 [&#x200B; サンプル localhost インストール &#x200B;](#sample-localhost-installations)を参照してください。

>[!NOTE]
>
>スペースまたは特殊文字を含むオプションは、1つまたは2つの引用符で囲む必要があります。

**管理者の資格情報：**

次のオプションは、管理者ユーザーのユーザー情報と資格情報を指定します。

Adobe Commerce バージョン 2.2.8以降では、インストール中またはインストール後に管理者ユーザーを作成できます。 インストール中にユーザーを作成する場合は、すべての管理者資格情報変数が必要です。 [&#x200B; サンプル localhost インストール &#x200B;](#sample-localhost-installations)を参照してください。

| 名前 | 値 | 必要ですか？ |
|--- |--- |--- |
| `--admin-firstname` | 管理者ユーザーの名前。 | はい |
| `--admin-lastname` | 管理者ユーザーの姓。 | はい |
| `--admin-email` | 管理者ユーザーのメールアドレス。 | はい |
| `--admin-user` | 管理者ユーザー名。 | はい |
| `--admin-password` | 管理者ユーザーパスワード。 パスワードは、少なくとも7文字の長さである必要があり、少なくとも1つのアルファベットと少なくとも1つの数字を含める必要があります。 より長く複雑なパスワードを使用することをお勧めします。 パスワード文字列全体を一重引用符で囲みます。 例：`--admin-password='A0b9%t3g'` | はい |

**サイトとデータベースの設定オプション：**

| 名前 | 値 | 必要ですか？ |
|--- |--- |--- |
| `--base-url` | 次のいずれかの形式で管理者およびストアフロントにアクセスするために使用するベース URL:<br><br>`http[s]://<host or ip>/<your install dir>/`。<br><br>**注意：** スキーム（http://またはhttps://）と末尾のスラッシュはどちらも必要です。<br><br>`<your install dir>` は、アプリケーションをインストールするdocroot相対パスです。 Web サーバーと仮想ホストの設定方法によっては、パスがmagento2であるか、空白である可能性があります。<br><br>localhost上のアプリケーションにアクセスするには、`http://127.0.0.1/<your install dir>/`または`http://127.0.0.1/<your install dir>/`のいずれかを使用できます。<br><br>- `{{base_url}}`は、仮想ホスト設定またはDockerなどの仮想化環境で定義されたベース URLを表します。 例えば、ホスト名commerce.example.comで仮想ホストを設定した場合、`--base-url={{base_url}}`でアプリケーションをインストールし、`http://commerce.example.com/admin`のようなURLで管理者にアクセスできます。 | はい |
| `--backend-frontname` | 管理者にアクセスするためのURI （Uniform Resource Identifier）。 このパラメーターを省略すると、次のパターン <code>admin_jkhgdfqを持つランダム URIをアプリケーションで生成できます</code>.<br><br> セキュリティ上の理由から、ランダムなURIを使用することをお勧めします。 ランダム URIは、ハッカーや悪意のあるソフトウェアが悪用するのが困難です。<br><br>URIはインストールの最後に表示されます。 後で`magento info:adminuri` コマンドを使用して、いつでも表示できます。<br><br>値を入力する場合は、「管理者」、「バックエンド」などの一般的な単語を使用しないことをお勧めします。 管理者URIには、英数字とアンダースコア文字（`_`）のみを含めることができます。 | いいえ |
| `--db-host` | 次のいずれかを使用します。<br><br>- データベースサーバーの完全修飾ホスト名またはIP アドレス。<br><br>- `localhost` （デフォルト）または`127.0.0.1` （データベースサーバーがweb サーバーと同じホスト上にある場合）。localhostは、MySQL クライアントライブラリがUNIX ソケットを使用してデータベースに接続することを意味します。 `127.0.0.1`によって、クライアント ライブラリでTCP プロトコルが使用されます。 ソケットについて詳しくは、[PHP PDO_MYSQLのドキュメント &#x200B;](https://www.php.net/manual/en/ref.pdo-mysql.php)を参照してください。<br><br>**注：** www.example.com:9000のように、ホスト名にデータベースサーバーポートをオプションで指定できます | はい |
| `--db-name` | データベーステーブルをインストールするデータベースインスタンスの名前。<br><br> デフォルトは`magento2`です。 | はい |
| `--db-user` | データベースインスタンス所有者のユーザー名。<br><br> デフォルトは`root`です。 | はい |
| `--db-password` | データベースインスタンス所有者のパスワード。 | はい |
| `--db-prefix` | 既にAdobe Commerce テーブルが含まれているデータベースインスタンスにデータベーステーブルをインストールする場合にのみ使用します。<br><br>その場合、プレフィックスを使用して、このインストールのテーブルを識別します。 一部のお客様は、同じデータベース内のすべてのテーブルを含むサーバー上で複数のAdobe Commerce インスタンスを実行しています。<br><br> プレフィックスは、最大5文字まで指定できます。 文字で始まる必要があり、文字、数字、アンダースコア文字のみを含めることができます。<br><br>このオプションを使用すると、ユーザーはデータベース サーバーを複数のインストールと共有できます。 | いいえ |
| `--db-ssl-key` | クライアントキーへのパス。 | いいえ |
| `--db-ssl-cert` | クライアント証明書へのパス。 | いいえ |
| `--db-ssl-ca` | サーバー証明書へのパス。 | いいえ |
| `--language` | 管理者とストアフロントで使用する言語コード。 （まだ行っていない場合は、bin ディレクトリから`magento info:language:list`を入力して、言語コードのリストを表示できます）。 | いいえ |
| `--currency` | ストアフロントで使用するデフォルト通貨。 （まだ行っていない場合は、bin ディレクトリから`magento info:currency:list`を入力して、通貨のリストを表示できます）。 | いいえ |
| `--timezone` | 管理者とストアフロントで使用するデフォルトのタイムゾーン。 （まだ実行していない場合は、bin ディレクトリから`magento info:timezone:list`を入力して、タイムゾーンのリストを表示できます）。 | いいえ |
| `--use-rewrites` | `1`とは、ストアフロントおよび管理者で生成されたリンクにweb サーバーの書き換えを使用することを意味します。<br><br>`0` web サーバーの書き換えの使用を無効にします。 これがデフォルトです。 | いいえ |
| `--use-secure` | `1`では、ストアフロント URLでSSL （Secure Sockets Layer）を使用できます。 このオプションを選択する前に、Web サーバーがSSLをサポートしていることを確認してください。<br><br>`0` sslの使用を無効にします。 この場合、その他のすべてのセキュア URL オプションも0と見なされます。 これがデフォルトです。 | いいえ |
| `--base-url-secure` | 管理者およびストアフロントへのアクセスに使用するセキュアなベース URL: `http[s]://<host or ip>/<your install dir>/` | いいえ |
| `--use-secure-admin` | `1`とは、SSLを使用して管理者にアクセスすることを意味します。 このオプションを選択する前に、Web サーバーがSSLをサポートしていることを確認してください。<br><br>`0` つまり、管理者と一緒にSSLを使用しません。 これがデフォルトです。 | いいえ |
| `--admin-use-security-key` | 1を指定すると、アプリケーションはランダムに生成されたキー値を使用して、管理者およびフォームのページにアクセスできます。 これらのキー値は、クロスサイトスクリプトフォージェリー攻撃を防ぐのに役立ちます。 これは既定値です。<br><br>`0` キーの使用を無効にします。 | いいえ |
| `--session-save` | 次のいずれかを使用して、セッションデータをデータベースに保存します。<br><br> ～ `db` クラスター化されたデータベースがある場合は、データベース ストレージを選択します。そうでない場合は、ファイルベースのストレージよりもメリットが少ない可能性があります。<br><br>- `files` セッションデータをファイルシステムに保存します。 ファイルベースのセッションストレージは、ファイルシステムのアクセス速度が遅い、クラスター化されたデータベースがある、またはセッションデータをRedisに保存する場合を除いて適切です。<br><br>- `redis` セッションデータをRedisに保存します。 デフォルトまたはページキャッシュにRedisを使用している場合は、Redisが既にインストールされている必要があります。 Redisのサポートの設定について詳しくは、セッションストレージにRedisを使用するを参照してください。 | いいえ |
| `--key` | データベースがある場合は、データベース内の機密データを暗号化するためのキーを指定します。 アカウントをお持ちでない場合は、アプリケーションによってアカウントが生成されます。 | はい |
| `--cleanup-database` | アプリケーションをインストールする前にデータベーステーブルをドロップするには、値を指定せずにこのパラメーターを指定します。 それ以外の場合は、データベースはそのまま残ります。 | いいえ |
| `--db-init-statements` | 高度なMySQL設定パラメーター。 データベース初期化ステートメントを使用して、MySQL データベースに接続するときに実行します。 値を設定する前に、このリファレンスと同様のリファレンスを参照してください。<br><br> デフォルトは`SET NAMES utf8;`です。 | いいえ |
| `--sales-order-increment-prefix` | 受注の接頭辞として使用する文字列値を指定します。 通常、これは決済代行会社の一意の注文番号を保証するために使用されます。 | いいえ |

>[!TIP]
>
>インストール中にリモートストレージサービスを有効にするには、_設定ガイド_&#x200B;の[&#x200B; リモートストレージの設定](../../configuration/remote-storage/remote-storage.md)を参照してください。

**検索エンジン設定オプション：**

| 名前 | 値 | 必要ですか？ |
|--- |--- |--- |
| `--search-engine` | 検索エンジンのバージョン。 指定できる値は`elasticsearch7`、`elasticsearch6`、`elasticsearch5`です。 デフォルトは`elasticsearch7`です。 検索エンジンとしてOpenSearchをインストールしている場合は、値`elasticsearch7`を指定します。 Elasticsearch 5は非推奨（廃止予定）であり、お勧めしません。 | いいえ |
| `--elasticsearch-host` | 検索エンジンが実行されているホスト名またはIP アドレス。 デフォルトは`localhost`です。 | いいえ |
| `--elasticsearch-port` | 受信HTTP リクエストのポート。 デフォルトは`9200`です。 | いいえ |
| `--elasticsearch-index-prefix` | 検索インデックスを識別するプレフィックス。 デフォルトは`magento2`です。 | いいえ |
| `--elasticsearch-timeout` | システムがタイムアウトするまでの秒数。 デフォルトは`15`です。 | いいえ |
| `--elasticsearch-enable-auth` | 検索エンジンサーバーでの認証を有効にします。 デフォルトは`false`です。 | いいえ |
| `--elasticsearch-username` | 認証するユーザーID | いいえ、認証が有効になっていない限り |
| `--elasticsearch-password` | 認証するためのパスワード | いいえ、認証が有効になっていない限り |

**[!DNL RabbitMQ]設定オプション：**

| 名前 | 値 | 必要ですか？ |
|--- |--- |--- |
| `--amqp-host` | [!DNL RabbitMQ]のインストールを既に設定していない限り、`--amqp` オプションを使用しないでください。 [!DNL RabbitMQ]のインストールと設定について詳しくは、[!DNL RabbitMQ]のインストールを参照してください。<br><br>[!DNL RabbitMQ]がインストールされているホスト名。 | いいえ |
| `--amqp-port` | [!DNL RabbitMQ]への接続に使用するポート。 デフォルトは5672です。 | いいえ |
| `--amqp-user` | [!DNL RabbitMQ]に接続するためのユーザー名。 既定のユーザー`guest`は使用しないでください。 | いいえ |
| `--amqp-password` | [!DNL RabbitMQ]に接続するためのパスワード。 既定のパスワード `guest`は使用しないでください。 | いいえ |
| `--amqp-virtualhost` | [!DNL RabbitMQ]に接続するための仮想ホスト。 デフォルトは`/`です。 | いいえ |
| `--amqp-ssl` | [!DNL RabbitMQ]に接続するかどうかを示します。 デフォルトは`false`です。 [!DNL RabbitMQ]のSSLの設定について詳しくは、[!DNL RabbitMQ]を参照してください。 | いいえ |
| `--consumers-wait-for-messages` | 消費者はキューからのメッセージを待つべきですか？ 1 – はい、0 – いいえ | いいえ |

**ActiveMQ Artemis設定オプション：**

>[!NOTE]
>
>ActiveMQ Artemisは、Adobe Commerce 2.4.5以降で導入されました。

| 名前 | 値 | 必要ですか？ |
|--- |--- |--- |
| `--stomp-host` | ActiveMQ Artemisのインストールを既に設定していない限り、`--stomp` オプションを使用しないでください。 ActiveMQ Artemisのインストールと設定について詳しくは、ActiveMQ Artemisのインストールを参照してください。<br><br>ActiveMQ Artemisがインストールされているホスト名。 | いいえ |
| `--stomp-port` | ActiveMQ Artemisへの接続に使用するポート。 デフォルトは61613です。 | いいえ |
| `--stomp-user` | ActiveMQ Artemisに接続するためのユーザー名。 既定のユーザー`artemis`は使用しないでください。 | いいえ |
| `--stomp-password` | ActiveMQ Artemisに接続するためのパスワード。 既定のパスワード `artemis`は使用しないでください。 | いいえ |
| `--stomp-ssl` | SSLを使用してActiveMQ Artemisに接続するかどうかを示します。 デフォルトは`false`です。 ActiveMQ ArtemisのSSL設定について詳しくは、ActiveMQ Artemisを参照してください。 | いいえ |
| `--consumers-wait-for-messages` | 消費者はキューからのメッセージを待つべきですか？ 1 – はい、0 – いいえ | いいえ |

**リモート ストレージ オプション：**

| 名前 | 説明 | 必要ですか？ |
|--- |--- |--- |
| `remote-storage-driver` | アダプタ名<br>可能な値：<br>**ファイル**：リモートストレージを無効にし、ローカルファイルシステムを使用します&#x200B;<br>**aws-s3**: [Amazon Simple Storage Service （Amazon S3）を使用します](https://aws.amazon.com/s3/) | いいえ |
| `remote-storage-bucket` | オブジェクトストレージまたはコンテナ名 | いいえ |
| `remote-storage-prefix` | オプションの接頭辞（オブジェクトストレージ内の場所） | いいえ |
| `remote-storage-region` | 地域名 | いいえ |
| `remote-storage-key` | オプションのアクセスキー | いいえ |
| `remote-storage-secret` | オプションの秘密鍵 | いいえ |

**設定オプションのロック：**

| 名前 | 値 | 必要ですか？ |
|--- |--- |--- |
| `--lock-provider` | プロバイダー名をロックします。<br><br>使用可能なロック プロバイダー：`db`、`zookeeper`、`file`。<br><br>既定のロック プロバイダー：`db` | いいえ |
| `--lock-db-prefix` | `db` ロックプロバイダーの使用時にロックの競合を回避するための特定のdb プレフィックス。<br><br> デフォルト値：`NULL` | いいえ |
| `--lock-zookeeper-host` | `zookeeper` ロックプロバイダーを使用する場合に、Zookeeper クラスターに接続するためのホストとポート。<br><br>例：`127.0.0.1:2181` | はい、`--lock-provider=zookeeper`を設定した場合 |
| `--lock-zookeeper-path` | Zookeeperがロックを保存するパス。<br><br> デフォルトパスは`/magento/locks`です | いいえ |
| `--lock-file-path` | ファイルロックが保存されるパス。 | はい、`--lock-provider=file`を設定した場合 |

**コンシューマー設定オプション：**

{{$include /help/_includes/cli-consumers.md}}

>[!NOTE]
>
>アプリケーションのインストール後にモジュールを有効または無効にするには、[&#x200B; モジュールの有効と無効](manage-modules.md)を参照してください。

**機密データ：**

{{$include /help/_includes/sensitive-data.md}}

### localhostのインストール例

次の例は、様々なオプションを使用してAdobe Commerceをローカルにインストールするコマンドを示しています。

#### 例1：管理者ユーザーアカウントを使用した基本的なインストール

次の例では、次のオプションを使用してアプリケーションをインストールします。

* アプリケーションは、`localhost`のweb サーバーのdocrootに関連する`magento2` ディレクトリにインストールされ、管理者へのパスは`admin`です。したがって、次のようになります。

  ストアフロント URLは`http://127.0.0.1`です

* データベース・サーバは、Web サーバと同じホスト上にあります。

  データベース名は`magento`で、ユーザー名とパスワードはどちらも`magento`です

* サーバーの書き換えの使用

* 管理者には次のプロパティがあります。

   * 氏名は`Commerce User`です
   * ユーザー名は`admin`、パスワードは`admin123`です
   * メールアドレスは`user@example.com`です

* 既定の言語は`en_US` （米国英語）です
* デフォルト通貨は米ドルです
* デフォルトのタイムゾーンは米国中部（アメリカ/シカゴ）です
* Elasticsearch 7は`es-host.example.com`にインストールされ、ポート 9200に接続しています

```shell
magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--admin-firstname=Commerce --admin-lastname=User --admin-email=user@example.com \
--admin-user=admin --admin-password=admin123 --language=en_US \
--currency=USD --timezone=America/Chicago --use-rewrites=1 \
--search-engine=elasticsearch7 --elasticsearch-host=es-host.example.com \
--elasticsearch-port=9200
```

インストールが成功したことを示す次のようなメッセージが表示されます。

```text
Post installation file permissions check...
For security, remove write permissions from these directories: '/var/www/html/magento2/app/etc'
[Progress: 274 / 274]
[SUCCESS]: Magento installation complete.
[SUCCESS]: Admin Panel URI: /admin_puu71q
```

#### 例2：管理者ユーザーアカウントを持たない基本インストール

次の例に示すように、管理者ユーザーを作成せずにアプリケーションをインストールできます。

```shell
magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--language=en_US --currency=USD --timezone=America/Chicago --use-rewrites=1 \
--search-engine=elasticsearch7 --elasticsearch-host=es-host.example.com \
--elasticsearch-port=9200
```

インストールが成功した場合、次のようなメッセージが表示されます。

```text
Post installation file permissions check...
For security, remove write permissions from these directories: '/var/www/html/magento2/app/etc'
[Progress: 274 / 274]
[SUCCESS]: Magento installation complete.
[SUCCESS]: Admin Panel URI: /admin_puu71q
```

インストール後、`admin:user:create` コマンドを使用して管理者ユーザーを作成できます。
[管理者を作成または編集](admin.md#create-or-edit-an-administrator)

#### 例3：追加のオプションを使用したインストール

次の例では、次のオプションを使用してアプリケーションをインストールします。

* Magapplicationは、`localhost`のweb サーバーのdocrootに関連する`magento2` ディレクトリにインストールされ、管理者へのパスは`admin`です。したがって、次のようになります。

  ストアフロント URLは`http://127.0.0.1`です

* データベース・サーバは、Web サーバと同じホスト上にあります。

  データベース名は`magento`で、ユーザー名とパスワードはどちらも`magento`です

* 管理者には次のプロパティがあります。

   * 氏名は`Commerce User`です
   * ユーザー名は`admin`、パスワードは`admin123`です
   * メールアドレスは`user@example.com`です

* 既定の言語は`en_US` （米国英語）です
* デフォルト通貨は米ドルです
* デフォルトのタイムゾーンは米国中部（アメリカ/シカゴ）です
* インストーラーは、テーブルとスキーマをインストールする前に、まずデータベースをクリーンアップします
* `ORD$`件の販売注文増分プレフィックスを使用します（特殊文字[`$`]が含まれているため、値は二重引用符で囲む必要があります）
* セッションデータはデータベースに保存されます
* サーバーの書き換えの使用
* Elasticsearch 7は`es-host.example.com`にインストールされ、ポート 9200に接続しています

```shell
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
>コマンドは、1行で入力するか、前の例のように、各行の末尾に`\`文字を付けて入力する必要があります。

インストールが成功した場合、次のようなメッセージが表示されます。

```text
Post installation file permissions check...
For security, remove write permissions from these directories: '/var/www/html/magento2/app/etc'
[Progress: 274 / 274]
[SUCCESS]: Magento installation complete.
[SUCCESS]: Admin Panel URI: /admin_puu71q
```

#### 例4 - ActiveMQ Artemisを使用したインストール

次に、メッセージブローカーとしてActiveMQ Artemisを使用してAdobe Commerceをインストールする例を示します。

```shell
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
>ActiveMQ Artemisのインストールには、Adobe Commerce 2.4.5以降が必要です。

>[!TIP]
>
>アプリケーションサーバーにアクセスするためのユーザーアカウントが1つある場合は、[umaskの設定](../next-steps/set-umask.md)を参照してください。 このタイプの設定は、共有ホスティングで一般的です。

<!-- Last updated from includes: 2024-04-16 09:42:31 -->
