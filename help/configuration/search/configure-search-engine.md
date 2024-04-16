---
title: 検索エンジン設定
description: Adobe Commerceのオンプレミスデプロイメント用の検索エンジンを設定します。
feature: Configuration, Search
exl-id: 61fbe0c2-bdd5-4f57-a518-23e180401804
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '643'
ht-degree: 0%

---

# 検索エンジン設定

この節では、Adobe CommerceのオンプレミスデプロイメントでElasticsearchまたは OpenSearch をテストするために必要な最小設定について説明します。

>[!TIP]
>
>バージョン 2.4.4 および 2.4.3-p2 では、すべてのフィールドにラベルが付いています **Elasticsearch** opensearch にも適用されます。
>Elasticsearch 2.4.6 でバージョン 8.x のサポートが導入された際には、Elasticsearch設定と OpenSearch 設定を区別する新しいラベルが作成されました。

検索エンジンの設定について詳しくは、 [ユーザーガイド](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-configuration.html).

## 管理者からの検索エンジンの設定

>[!TIP]
>
>新しい検索エンジン バージョンにアップグレードする方法については、を参照してください。 [アップグレードの前提条件](../../upgrade/prepare/prerequisites.md).

Elasticsearchまたは OpenSearch を使用するようにシステムを設定するには：

1. 管理者として管理者にログインします。
1. クリック **[!UICONTROL Stores]** > [!UICONTROL Settings] > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]**.
1. から **[!UICONTROL Search Engine]** リストで、検索エンジンの対応するバージョンを選択します。

   次の表に、Commerceとの接続を設定およびテストするために必要なオプションを示します。 検索エンジンのサーバー設定を変更しない限り、デフォルトは機能します。 次の手順にスキップします。

   | オプション | 説明 |
   |--- |--- |
   | **[!UICONTROL Server Hostname]** | Elasticsearchまたは OpenSearch を実行しているマシンの完全修飾ホスト名または IP アドレスを入力します。<br>クラウドインフラストラクチャー上のAdobe Commerce：この価値を統合システムから取得します。 |
   | **[!UICONTROL Server Port]** | Web サーバーのプロキシポートを入力します。 デフォルトは 9200 です<br>クラウドインフラストラクチャー上のAdobe Commerce：この価値を統合システムから取得します。 |
   | **[!UICONTROL Index Prefix]** | 検索エンジンのインデックスプレフィックスを入力します。 複数のCommerce インストールに 1 つのインスタンスを使用する場合（ステージング環境と実稼動環境）、インストールごとに一意のプレフィックスを指定する必要があります。 それ以外の場合は、デフォルトのプレフィックス magento2 を使用できます。 |
   | **[!UICONTROL Enable HTTP Auth]** | クリック **[!UICONTROL Yes]** 検索エンジン サーバーの認証を有効にした場合のみ。 その場合は、指定されたフィールドにユーザー名とパスワードを入力します。 |
   | **[!UICONTROL Server Timeout]** | Elasticsearchまたは OpenSearch サーバーへの接続を確立しようとするときに待機する時間（秒）を入力します。 |

1. クリック **[!UICONTROL Test Connection]**.

   応答の例：

   ![成功](../../assets/configuration/elastic_test-success.png)

   続行：

   - [検索エンジン用に Apache を設定する](../../installation/prerequisites/search-engine/configure-apache.md)
   - [検索エンジンの nginx の設定](../../installation/prerequisites/search-engine/configure-nginx.md)

   以下が表示されます。

   ![失敗](../../assets/configuration/elastic_test-fail.png)

その場合は、次の操作を試してください。

- 検索エンジン サーバーが実行中であることを確認してください。
- サーバーがCommerceとは別のホスト上にある場合は、Commerce サーバーにログインし、検索エンジンホストに対して ping を実行します。 ネットワーク接続の問題を解決し、接続を再度テストします。
- Elasticsearchまたは OpenSearch を開始したコマンド ウィンドウで、スタック トレースと例外を調べます。 続行する前にそれらを解決する必要があります。 特に、次の条件を満たすユーザーとして検索エンジンを起動したことを確認します。 `root` 権限。
- 次のことを確認します [UNIX ファイアウォールと SELinux](../../installation/prerequisites/search-engine/overview.md#firewall-and-selinux) を無効にするか、ルールを設定して検索エンジンとCommerceが相互に通信できるようにします。
- の値を確認します。 **[!UICONTROL Server Hostname]** フィールド。 サーバーが使用可能であることを確認します。 代わりに、サーバーの IP アドレスを試してみてください。
- の使用 `netstat -an | grep <listen-port>` で指定されたポートを検証するコマンド **[!UICONTROL Server Port]** フィールドは別のプロセスで使用されていません。

  例えば、検索エンジンがデフォルトのポートで実行されているかどうかを確認するには、次のコマンドを使用します。

  ```bash
  netstat -an | grep 9200
  ```

  ポート 9200 で実行されている場合は、次のように表示されます。

  ```terminal
  `tcp        0      0 :::9200            :::-         LISTEN`
  ```

## カタログ検索のインデックスを再作成して、ページ全体のキャッシュを更新します。

検索エンジンの設定を変更した後、管理者またはコマンドラインを使用して、カタログ検索インデックスを再インデックスし、ページのフルキャッシュを更新する必要があります。

管理者を使用してキャッシュを更新するには：

1. 管理者で、 **[!UICONTROL System]** > **[!UICONTROL Cache Management]**.
1. の横にあるチェックボックスをオンにします。 **[!UICONTROL Page Cache]**.
1. から **[!UICONTROL Actions]** 右上のリストで、 **更新**.

   ![キャッシュ管理](../../assets/configuration/refresh-cache.png)

コマンドラインを使用してキャッシュをクリーンアップするには： [`bin/magento cache:clean`](../cli/manage-cache.md#clean-and-flush-cache-types)

コマンドラインを使用してインデックスを再作成するには：

1. Commerce サーバーにとしてログインするか、に切り替えます [ファイルシステム所有者](../../installation/prerequisites/file-system/overview.md).
1. 次のいずれかのコマンドを入力します。

   次のコマンドを入力して、カタログ検索インデックスのみを再インデックス化します。

   ```bash
   bin/magento indexer:reindex catalogsearch_fulltext
   ```

   次のコマンドを入力して、すべてのインデクサーを再インデックス化します。

   ```bash
   bin/magento indexer:reindex
   ```

1. 再インデックスが完了するまで待ちます。

   >[!INFO]
   >
   >キャッシュとは異なり、インデクサーは cron ジョブによって更新されます。 確認する [cron は有効です](../cli/configure-cron-jobs.md) 検索エンジンの使用を開始する前に。
