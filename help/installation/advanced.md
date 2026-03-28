---
title: 高度なオンプレミス インストール
description: Adobe Commerce オンプレミス展開の高度なインストールのシナリオについて説明します。 複雑な設定とカスタム設定オプションをご確認ください。
exl-id: e16e750a-e068-4a63-8ad9-62043e2a8231
source-git-commit: 7054a5286f01e26e324401f4d8505e4e0faed93e
workflow-type: tm+mt
source-wordcount: '2484'
ht-degree: 0%

---

# 高度なオンプレミス インストール

>[!TIP]
>
>お忘れですか？ 助ける手が必要ですか？ [&#x200B; クイックスタートインストール &#x200B;](composer.md)または[&#x200B; コントリビューターインストール &#x200B;](https://developer.adobe.com/commerce/contributor/guides/install/) ガイドをお試しください。

>[!NOTE]
>
>SELinuxを有効にする場合は、[SELinuxとiptables](prerequisites/security.md)を参照してください。

## コマンドラインインターフェイス（CLI）

Adobe Commerceには、インストール タスクと設定タスク用の1つのコマンド ライン インターフェイスがあります：`<magento_root>/bin/magento`。 インターフェイスは、次のような複数のタスクを実行します。

* インストール（およびデータベーススキーマの作成や更新、デプロイメント設定の作成など）に関連するタスク。
* キャッシュのクリア。
* インデックス再作成を含むインデックスの管理。
* 翻訳辞書と翻訳パッケージの作成。
* プラグインのファクトリやインターセプタなどの存在しないクラスを生成し、オブジェクトマネージャーの依存関係インジェクション設定を生成します。
* 静的ビューファイルのデプロイ。
* より少ないCSSの作成。

その他の利点：

* 単一のコマンド （`<magento_root>/bin/magento list`）には、使用可能なすべてのインストールおよび設定コマンドが一覧表示されます。
* Symfonyに基づいた一貫したユーザーインターフェイス。
* CLIは拡張可能なので、サードパーティの開発者はCLIに「プラグイン」できます。 これは、ユーザーの学習曲線を排除するという追加の利点があります。
* 無効なモジュールのコマンドは表示されません。

このトピックでは、CLIを使用したAdobe Commerce ソフトウェアのインストールについて説明します。 設定について詳しくは、[設定ガイド &#x200B;](../configuration/overview.md)を参照してください。

インストーラーは必要に応じて複数回実行できるので、次のことが可能です。

* 異なる値を指定

  例えば、セキュアソケットレイヤー（SSL）用にweb サーバーを設定した後、インストーラーを実行してSSL オプションを設定できます。

* 以前のインストールでの間違いを修正
* 別のデータベースインスタンスへのAdobe Commerceのインストール

## インストールの開始前

開始する前に、次の手順を実行します。

* お使いのシステムが[&#x200B; システム要件](system-requirements.md)で説明されている要件を満たしていることを確認します。

* すべての[前提条件](prerequisites/overview.md) タスクを完了します。

* 最初のインストール手順を完了します。 [&#x200B; インストールまたはアップグレードのパス &#x200B;](overview.md)を参照してください。

* アプリケーションサーバーにログインした後、[&#x200B; ファイルシステム所有者](prerequisites/file-system/overview.md)に切り替えます。

* [&#x200B; インストールのクイックスタート &#x200B;](composer.md)の概要を確認します。

>[!NOTE]
>
>Adobe Commerceを`bin` サブディレクトリからインストールする必要があります。

インストーラーを複数回実行して、次のようなインストールタスクを完了できます。

* 段階的なインストール – 例えば、Web サーバーをSSL （Secure Sockets Layer）用に設定した後、インストーラーを再度実行してSSL オプションを設定できます。

* 以前のインストールで発生したエラーを修正します。

* 別のデータベースインスタンスにAdobe Commerceをインストールします。

>[!NOTE]
>
>デフォルトでは、同じデータベースインスタンスにソフトウェアをインストールしても、インストーラーはデータベースを上書きしません。 オプションの`cleanup-database` パラメーターを使用して、この動作を変更できます。

[更新、再インストール、アンインストール &#x200B;](tutorials/uninstall.md)も参照してください。

### 安全なインストール

{{$include /help/_includes/secure-install.md}}

## インストーラーヘルプコマンド

次のコマンドを実行して、必須の引数の値を検索できます。

| インストーラー引数 | コマンド |
| ------------------ | ------------------------------- |
| 言語 | `bin/magento info:language:list` |
| 通貨 | `bin/magento info:currency:list` |
| タイムゾーン | `bin/magento info:timezone:list` |

>[!NOTE]
>
>これらのコマンドを実行するとエラーが表示される場合は、[&#x200B; インストール依存関係の更新](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies)で説明したように、インストール依存関係を更新したことを確認してください。

## コマンドラインからインストール

install コマンドでは、次の形式が使用されます。

```bash
bin/magento setup:install --<option>=<value> ... --<option>=<value>
```

次の表に、インストールオプションの名前と値を示します。 インストールコマンドの例については、[&#x200B; サンプル localhost インストール &#x200B;](#sample-localhost-installations)を参照してください。

>[!NOTE]
>
>スペースまたは特殊文字を含むオプションは、1つまたは2つの引用符で囲む必要があります。

**管理者の資格情報：**

次のオプションは、管理者ユーザーのユーザー情報と資格情報を指定します。

インストール中またはインストール後に管理者ユーザーを作成できます。 インストール中にユーザーを作成する場合は、すべての管理者資格情報変数が必要です。 [&#x200B; サンプル localhost インストール &#x200B;](#sample-localhost-installations)を参照してください。

次の表に、使用可能なインストールパラメーターの多くはありますが、一部ではありません。 完全なリストについては、[&#x200B; コマンドラインツールのリファレンス &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/cli-reference/commerce-on-premises)を参照してください。

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
| `--base-url` | 次のいずれかの形式で管理者およびストアフロントにアクセスするために使用するベース URL:<br><br>`http[s]://<host or ip>/<your install dir>/`。<br><br>**注意：** スキーム （http://またはhttps://）と末尾のスラッシュは両方とも必須です。<br><br>`<your install dir>`は、Adobe Commerce ソフトウェアをインストールするdocroot相対パスです。 Web サーバーと仮想ホストの設定方法によっては、パスがmagento2であるか、空白である可能性があります。<br><br>Adobe CommerceまたはMagenAdobe Commerceにアクセスするには、`http://127.0.0.1/<your install dir>/`または`http://127.0.0.1/<your install dir>/`のいずれかを使用してください。<br><br>- `{{base_url}}`は、仮想ホスト設定またはDockerなどの仮想化環境によって定義されたベース URLを表します。 例えば、ホスト名`magento.example.com`で仮想ホストを設定する場合、`--base-url={{base_url}}`でソフトウェアをインストールし、`http://magento.example.com/admin`のようなURLで管理者にアクセスできます。 | はい |
| `--backend-frontname` | 管理者にアクセスするためのURI （Uniform Resource Identifier）。 このパラメーターを省略すると、次のパターン <code>admin_jkhgdfqを持つランダム URIをアプリケーションで生成できます</code>。<br><br> セキュリティ上の理由から、ランダム URIをお勧めします。 ランダム URIは、ハッカーや悪意のあるソフトウェアが悪用するのが困難です。<br><br>URIはインストールの最後に表示されます。 後で`bin/magento info:adminuri` コマンドを使用して、いつでも表示できます。<br><br>値を入力する場合は、「管理者」、「バックエンド」などの一般的な単語を使用しないことをお勧めします。 管理者URIには、英数字とアンダースコア文字（`_`）のみを含めることができます。 | いいえ |
| `--db-host` | 次のいずれかを使用します。<br><br>- データベース サーバーの完全修飾ホスト名またはIP アドレス。データベース サーバーがweb サーバーと同じホスト上にある場合、<br><br>- `localhost` （デフォルト）または`127.0.0.1`。localhostは、MySQL クライアントライブラリがUNIX ソケットを使用してデータベースに接続することを意味します。 `127.0.0.1`によって、クライアント ライブラリでTCP プロトコルが使用されます。 ソケットについて詳しくは、[PHP PDO_MYSQL ドキュメント &#x200B;](https://www.php.net/manual/en/ref.pdo-mysql.php)を参照してください。<br><br>**注：** データベース サーバーのポートは、オプションで`www.example.com:9000`のようにホスト名に指定できます | はい |
| `--db-name` | データベーステーブルをインストールするデータベースインスタンスの名前。<br><br> デフォルトは`magento2`です。 | はい |
| `--db-user` | データベースインスタンス所有者のユーザー名。<br><br> デフォルトは`root`です。 | はい |
| `--db-password` | データベースインスタンス所有者のパスワード。 | はい |
| `--db-prefix` | 既にAdobe Commerce テーブルが含まれているデータベースインスタンスにデータベーステーブルをインストールする場合にのみ使用します。<br><br>その場合、プレフィックスを使用して、このインストールのテーブルを識別します。 一部のお客様は、同じデータベース内のすべてのテーブルを含む複数のAdobe CommerceまたはMagenAdobe Commerce Serverを持っています。<br><br> プレフィックスは、最大5文字まで指定できます。 文字で始まる必要があり、文字、数字、アンダースコア文字のみを含めることができます。<br><br>このオプションを使用すると、お客様は複数のAdobe Commerce インストールでデータベース サーバーを共有できます | |
| `--db-ssl-key` | クライアントキーへのパス。 | いいえ |
| `--db-ssl-cert` | クライアント証明書へのパス。 | いいえ |
| `--db-ssl-ca` | サーバー証明書へのパス。 | いいえ |
| `--language` | 管理者とストアフロントで使用する言語コード。 （まだ行っていない場合は、bin ディレクトリから`bin/magento info:language:list`を入力して、言語コードのリストを表示できます）。 | いいえ |
| `--currency` | ストアフロントで使用するデフォルト通貨。 （まだ行っていない場合は、bin ディレクトリから`bin/magento info:currency:list`を入力して、通貨のリストを表示できます）。 | いいえ |
| `--timezone` | 管理者とストアフロントで使用するデフォルトのタイムゾーン。 （まだ実行していない場合は、`bin/magento info:timezone:list` ディレクトリから`bin/`を入力して、タイムゾーンのリストを表示できます）。 | いいえ |
| `--use-rewrites` | `1`とは、ストアフロントおよび管理画面で生成されたリンクにweb サーバーの書き換えを使用することを意味します。<br><br>`0`は、web サーバーの書き換えの使用を無効にします。 これがデフォルトです。 | いいえ |
| `--use-secure` | `1`では、ストアフロント URLでSSL （Secure Sockets Layer）を使用できます。 このオプションを選択する前に、web サーバーがSSLをサポートしていることを確認してください。<br><br>`0`はSSLの使用を無効にします。 この場合、その他のすべてのセキュア URL オプションも0と見なされます。 これがデフォルトです。 | いいえ |
| `--base-url-secure` | 管理者およびストアフロントへのアクセスに使用するセキュアなベース URL: `http[s]://<host or ip>/<your install dir>/` | いいえ |
| `--use-secure-admin` | `1`とは、SSLを使用して管理者にアクセスすることを意味します。 このオプションを選択する前に、web サーバーがSSLをサポートしていることを確認してください。<br><br>`0`は、管理者と一緒にSSLを使用しないことを意味します。 これがデフォルトです。 | いいえ |
| `--admin-use-security-key` | 1を指定すると、アプリケーションはランダムに生成されたキー値を使用して、管理者およびフォームのページにアクセスできます。 これらのキー値は、クロスサイトスクリプトフォージェリー攻撃を防ぐのに役立ちます。 これがデフォルトです。<br><br>`0`は、キーの使用を無効にします。 | いいえ |
| `--session-save` | 次のいずれかを使用して、セッションデータをデータベースに保存します。<br><br> ～ `db` クラスター化されたデータベースがある場合は、データベースストレージを選択します。そうでない場合、ファイルベースのストレージよりもメリットが大きくない可能性があります。セッションデータをファイルシステムに保存するための<br><br> ～ `files`。 ファイルベースのセッションストレージは、ファイルシステムのアクセス速度が遅い、クラスター化されたデータベースがある、またはセッションデータをRedisに保存したい場合を除いて適切です。セッションデータをRedisに保存する<br><br> ～ `redis`。 デフォルトまたはページキャッシュにRedisを使用している場合は、Redisが既にインストールされている必要があります。 Redisのサポートの設定について詳しくは、セッションストレージにRedisを使用するを参照してください。 | いいえ |
| `--key` | データベースがある場合は、データベース内の機密データを暗号化するためのキーを指定します。 アカウントをお持ちでない場合は、アプリケーションによってアカウントが生成されます。 | はい |
| `--cleanup-database` | Adobe Commerceをインストールする前にデータベーステーブルをドロップするには、値を指定せずにこのパラメーターを指定します。 それ以外の場合は、データベースはそのまま残ります。 | いいえ |
| `--db-init-statements` | 高度なMySQL設定パラメーター。 データベース初期化ステートメントを使用して、MySQL データベースに接続するときに実行します。 値を設定する前に、このリファレンスと同様のリファレンスを参照してください。<br><br> デフォルトは`SET NAMES utf8;`です。 | いいえ |
| `--sales-order-increment-prefix` | 受注の接頭辞として使用する文字列値を指定します。 通常、これは決済代行会社の一意の注文番号を保証するために使用されます。 | いいえ |

**検索エンジン設定オプション：**

| 名前 | 値 | 必要ですか？ |
|--- |--- |--- |
| `--search-engine` | 検索エンジンとして使用するElasticsearchまたはOpenSearchのバージョン。 デフォルトは`elasticsearch7`です。 Elasticsearch 5は非推奨（廃止予定）であり、お勧めしません。 | いいえ |
| `--elasticsearch-host` | Elasticsearchが実行されているホスト名またはIP アドレス。 デフォルトは`localhost`です。 | いいえ |
| `--elasticsearch-port` | 受信HTTP リクエスト用のElasticsearch ポート。 デフォルトは`9200`です。 | いいえ |
| `--elasticsearch-index-prefix` | Elasticsearch検索インデックスを識別するプレフィックス。 デフォルトは`magento2`です。 | いいえ |
| `--elasticsearch-timeout` | システムがタイムアウトするまでの秒数。 デフォルトは`15`です。 | いいえ |
| `--elasticsearch-enable-auth` | Elasticsearch サーバーでの認証を有効にします。 デフォルトは`false`です。 | いいえ |
| `--elasticsearch-username` | Elasticsearch サーバーに対する認証のユーザーID。 | いいえ、認証が有効になっていない限り |
| `--elasticsearch-password` | Elasticsearchserverに対する認証のパスワード。 | いいえ、認証が有効になっていない限り |
| `--opensearch-host` | OpenSearchが実行されているホスト名またはIP アドレス。 デフォルトは`localhost`です。 | いいえ |
| `--opensearch-port` | 受信HTTP リクエストのOpenSearch ポート。 デフォルトは`9200`です。 | いいえ |
| `--opensearch-index-prefix` | OpenSearch検索インデックスを識別するプレフィックス。 デフォルトは`magento2`です。 | いいえ |
| `--opensearch-timeout` | システムがタイムアウトするまでの秒数。 デフォルトは`15`です。 | いいえ |
| `--opensearch-enable-auth` | OpenSearch サーバーでの認証を有効にします。 デフォルトは`false`です。 | いいえ |
| `--opensearch-username` | OpenSearch サーバーに対して認証するユーザーID。 | いいえ、認証が有効になっていない限り |
| `--opensearch-password` | OpenSearch サーバーに対する認証のパスワード。 | いいえ、認証が有効になっていない限り |

**[!DNL RabbitMQ]設定オプション：**

| 名前 | 値 | 必要ですか？ |
|--- |--- |--- |
| `--amqp-host` | `--amqp`のインストールを既に設定していない限り、[!DNL RabbitMQ] オプションを使用しないでください。 [!DNL RabbitMQ]のインストールと設定について詳しくは、[!DNL RabbitMQ] インストールを参照してください。<br><br>[!DNL RabbitMQ]がインストールされているホスト名。 | いいえ |
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
>Adobe Commerceのインストール後にモジュールを有効または無効にするには、[&#x200B; モジュールの有効と無効](tutorials/manage-modules.md)を参照してください。

**機密データ：**

{{$include /help/_includes/sensitive-data.md}}

### localhostのインストール例

次の例は、様々なオプションを使用してAdobe Commerceをローカルにインストールするコマンドを示しています。

#### 例1：管理者ユーザーアカウントを使用した基本的なインストール

次の例では、次のオプションを使用してAdobe Commerceをインストールします。

* アプリケーションは、`magento2`のweb サーバーのdocrootに関連する`localhost` ディレクトリにインストールされ、管理者へのパスは`admin`です。したがって、次のようになります。

  ストアフロント URLは`http://127.0.0.1`です

* データベース・サーバは、Web サーバと同じホスト上にあります。

  データベース名は`magento`で、ユーザー名とパスワードはどちらも`magento`です

* サーバーの書き換えの使用

* 管理者には次のプロパティがあります。

   * 氏名は`Magento User`です
   * ユーザー名は`admin`、パスワードは`admin123`です
   * メールアドレスは`user@example.com`です

* 既定の言語は`en_US` （米国英語）です
* デフォルト通貨は米ドルです
* デフォルトのタイムゾーンは米国中部（アメリカ/シカゴ）です
* OpenSearch 1.2は`os-host.example.com`にインストールされ、ポート 9200に接続しています

```bash
magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--admin-firstname=Magento --admin-lastname=User --admin-email=user@example.com \
--admin-user=admin --admin-password=admin123 --language=en_US \
--currency=USD --timezone=America/Chicago --use-rewrites=1 \
--search-engine=opensearch --opensearch-host=os-host.example.com \
--opensearch-port=9200
```

インストールが成功したことを示す次のようなメッセージが表示されます。

```
Post installation file permissions check...
For security, remove write permissions from these directories: '/var/www/html/magento2/app/etc'
[Progress: 274 / 274]
[SUCCESS]: Magento installation complete.
[SUCCESS]: Admin Panel URI: /admin_puu71q
```

#### 例2 – 管理者ユーザーアカウントを持たない基本インストール

次の例に示すように、管理者ユーザーを作成せずにAdobe Commerceをインストールできます。

```bash
magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--language=en_US --currency=USD --timezone=America/Chicago --use-rewrites=1 \
--search-engine=opensearch --opensearch-host=os-host.example.com \
--opensearch-port=9200
```

インストールが成功した場合、次のようなメッセージが表示されます。

```
Post installation file permissions check...
For security, remove write permissions from these directories: '/var/www/html/magento2/app/etc'
[Progress: 274 / 274]
[SUCCESS]: Magento installation complete.
[SUCCESS]: Admin Panel URI: /admin_puu71q
```

インストール後、`admin:user:create` コマンドを使用して管理者ユーザーを作成できます。
[管理者を作成または編集](tutorials/admin.md#create-or-edit-an-administrator)

#### 例3：追加のオプションを使用したインストール

次の例では、次のオプションを使用してAdobe Commerceをインストールします。

* アプリケーションは、`magento2`のweb サーバーのdocrootに関連する`localhost` ディレクトリにインストールされ、管理者へのパスは`admin`です。したがって、次のようになります。

  ストアフロント URLは`http://127.0.0.1`です

* データベース・サーバは、Web サーバと同じホスト上にあります。

  データベース名は`magento`で、ユーザー名とパスワードはどちらも`magento`です

* 管理者には次のプロパティがあります。

   * 氏名は`Magento User`です
   * ユーザー名は`admin`、パスワードは`admin123`です
   * メールアドレスは`user@example.com`です

* 既定の言語は`en_US` （米国英語）です
* デフォルト通貨は米ドルです
* デフォルトのタイムゾーンは米国中部（アメリカ/シカゴ）です
* インストーラーは、テーブルとスキーマをインストールする前に、まずデータベースをクリーンアップします
* 販売注文増分プレフィックス `ORD$`を使用できます（特殊文字[`$`]が含まれているため、値は二重引用符で囲む必要があります）
* セッションデータはデータベースに保存されます
* サーバーの書き換えの使用
* OpenSearchは`os-host.example.com`にインストールされ、ポート 9200に接続しています

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
>コマンドは、1行で入力するか、前の例のように、各行の末尾に`\`文字を付けて入力する必要があります。

インストールが成功した場合、次のようなメッセージが表示されます。

```
Post installation file permissions check...
For security, remove write permissions from these directories: '/var/www/html/magento2/app/etc'
[Progress: 274 / 274]
[SUCCESS]: Magento installation complete.
[SUCCESS]: Admin Panel URI: /admin_puu71q
```

#### 例4 - ActiveMQ Artemisを使用したインストール

次に、メッセージブローカーとしてActiveMQ Artemisを使用してAdobe Commerceをインストールする例を示します。

```bash
bin/magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--admin-firstname=Magento --admin-lastname=User --admin-email=user@example.com \
--admin-user=admin --admin-password=admin123 --language=en_US \
--currency=USD --timezone=America/Chicago --use-rewrites=1 \
--search-engine=opensearch --opensearch-host=os-host.example.com \
--opensearch-port=9200 --stomp-host=localhost --stomp-port=61613 \
--stomp-user=artemis --stomp-password=artemis
```

>[!NOTE]
>
>ActiveMQ Artemisのインストールには、Adobe Commerce 2.4.5以降が必要です。

<!-- Last updated from includes: 2024-04-16 09:42:31 -->
