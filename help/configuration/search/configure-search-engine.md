---
title: 検索エンジンの設定
description: 検索エンジンをAdobe CommerceとMagento Open Sourceで設定
source-git-commit: 80abb0180fcd8ecc275428c23b68feb5883cbc28
workflow-type: tm+mt
source-wordcount: '666'
ht-degree: 0%

---


# 検索エンジンの設定

このセクションでは、Adobe CommerceとMagento Open SourceでElasticsearchまたは OpenSearch をテストするために選択する必要がある最小の設定について説明します。 バージョン 2.4.4 および 2.4.3-p2 以降では、ラベルの付いたすべてのフィールド **Elasticsearch** は OpenSearch にも適用されます。

検索エンジンの設定について詳しくは、 [ユーザーガイド](https://docs.magento.com/user-guide/catalog/search-elasticsearch.html).

## 管理者から検索エンジンを設定する

システムで OpenSearch またはElasticsearchを使用するように設定するには：

1. 管理者として管理者にログインします。
1. クリック **ストア** /設定/ **設定** > **カタログ** > **カタログ** > **カタログ検索**.
1. 次の **検索エンジン** リストから、検索エンジンの対応するバージョンを選択します。OpenSearch を使用している場合は、「Elasticsearch7」を選択する必要があります。

   次の表に、Commerce との接続を設定およびテストするために必要な設定オプションを示します。
検索エンジンのサーバ設定を変更しない限り、デフォルトは機能します。 次の手順に進みます。

   | オプション | 説明 |
   |--- |--- |
   | **Elasticsearchサーバーのホスト名** | Elasticsearchまたは OpenSearch を実行するマシンの完全修飾ホスト名または IP アドレスを入力します。<br>Adobe Commerce on cloud infrastructure:この値は、統合システムから取得します。 |
   | **Elasticsearchサーバーポート** | Web サーバーのプロキシポートを入力します。 デフォルトは 9200 です。<br>Adobe Commerce on cloud infrastructure:この値は、統合システムから取得します。 |
   | **Elasticsearchインデックスのプレフィックス** | 検索エンジンのインデックスのプレフィックスを入力します。 複数のコマースインストール（ステージング環境と実稼動環境）に 1 つのインスタンスを使用する場合は、インストールごとに一意のプレフィックスを指定する必要があります。 それ以外の場合は、デフォルトのプレフィックス magento2 を使用できます。 |
   | **ElasticsearchHTTP 認証を有効にする** | クリック **はい** 検索エンジンサーバーの認証を有効にした場合にのみ有効です。 その場合は、提供されたフィールドにユーザー名とパスワードを入力します。 |

1. クリック **接続をテスト**.

   レスポンスのサンプル：

   ![成功](../../assets/configuration/elastic_test-success.png)

   続行：

   - [検索エンジン用に Apache を設定](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/es-config-apache.html)
   - [検索エンジン用に nginx を設定する](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/es-config-nginx.html)

   または、

   ![失敗](../../assets/configuration/elastic_test-fail.png)

その場合は、次の操作を試します。

- 検索エンジンサーバーが実行中であることを確認します。
- サーバーが Commerce とは異なるホスト上にある場合は、Commerce サーバーにログインし、検索エンジンホストに ping を送信します。 ネットワーク接続の問題を解決し、接続を再度テストします。
- スタックトレースと例外をElasticsearchまたは OpenSearch を開始したコマンドウィンドウを調べます。 続行する前に、それらを解決する必要があります。 特に、を使用して検索エンジンを起動したことを確認してください。 `root` 権限。
- 必ず [UNIX ファイアウォールと SELinux](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/elasticsearch.html#firewall-selinux) は両方とも無効になっているか、検索エンジンとコマースが相互に通信できるようにルールを設定しています。
- の値を検証します。 **Elasticsearchサーバーのホスト名** フィールドに入力します。 サーバーが使用可能であることを確認します。 代わりに、サーバーの IP アドレスを試すことができます。
- 以下を使用： `netstat -an | grep <listen-port>` コマンドを使用して、 **Elasticsearchサーバーポート** フィールドが別のプロセスで使用されていません。

   例えば、検索エンジンがデフォルトのポートで実行されているかどうかを確認するには、次のコマンドを使用します。

   ```bash
   netstat -an | grep 9200
   ```

   ポート 9200 で実行されている場合は、次のように表示されます。

   ```terminal
   `tcp        0      0 :::9200            :::-         LISTEN`
   ```

## カタログ検索のインデックス再作成とページキャッシュ全体の更新

検索エンジンの設定を変更した後、カタログ検索インデックスを再インデックスし、管理者またはコマンドラインを使用してページキャッシュ全体を更新する必要があります。

管理者を使用してキャッシュを更新するには：

1. 管理者で、 **システム** > **キャッシュ管理**.
1. の横にあるチェックボックスを選択します。 **ページキャッシュ**.
1. 次の **アクション** 右上のリストで、「 **更新**.

   ![キャッシュ管理](../../assets/configuration/refresh-cache.png)

コマンドラインを使用してキャッシュをクリーンアップするには： [`bin/magento cache:clean`](../cli/manage-cache.md#clean-and-flush-cache-types)

コマンドラインを使用してインデックスを再作成するには：

1. コマースサーバーに、 [ファイルシステム所有者](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).
1. 次のいずれかのコマンドを入力します。

   次のコマンドを入力して、カタログ検索インデックスのインデックスを再作成します。

   ```bash
   bin/magento indexer:reindex catalogsearch_fulltext
   ```

   次のコマンドを入力して、すべてのインデクサーを再インデックスします。

   ```bash
   bin/magento indexer:reindex
   ```

1. インデックスの再作成が完了するまで待ちます。

   >[!INFO]
   >
   >キャッシュとは異なり、インデクサーは cron ジョブで更新されます。 確認 [cron が有効になっています](../cli/configure-cron-jobs.md) 検索エンジンを使用する前に

