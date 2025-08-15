---
title: 検索エンジン設定
description: Adobe Commerceのオンプレミスデプロイメント用の検索エンジンを設定します。
feature: Configuration, Search
exl-id: 61fbe0c2-bdd5-4f57-a518-23e180401804
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '643'
ht-degree: 0%

---

# 検索エンジン設定

この節では、Adobe CommerceのオンプレミスデプロイメントでElasticsearchまたは OpenSearch をテストするために選択する必要がある最小設定について説明します。

>[!TIP]
>
>バージョン 2.4.4 および 2.4.3-p2 では、**Elasticsearch** というラベルの付いたすべてのフィールドも OpenSearch に適用されます。
>&#x200B;>バージョン 2.4.6 でElasticsearch 8.x がサポートされたとき、Elasticsearch設定と OpenSearch 設定を区別する新しいラベルが作成されました。

検索エンジンの設定について詳しくは、[ ユーザーガイド ](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-configuration.html) を参照してください。

## 管理者からの検索エンジンの設定

>[!TIP]
>
>新しい検索エンジン バージョンにアップグレードする手順については、[ アップグレードの前提条件 ](../../upgrade/prepare/prerequisites.md) を参照してください。

Elasticsearchまたは OpenSearch を使用するようにシステムを設定するには：

1. 管理者として管理者にログインします。
1. **[!UICONTROL Stores]**/[!UICONTROL Settings]/**[!UICONTROL Configuration]**/**[!UICONTROL Catalog]**/**[!UICONTROL Catalog]**/**[!UICONTROL Catalog Search]** をクリックします。
1. **[!UICONTROL Search Engine]** リストから、検索エンジンの対応するバージョンを選択します。

   次の表に、Commerceとの接続を設定およびテストするために必要なオプションを示します。 検索エンジンのサーバー設定を変更しない限り、デフォルトは機能します。 次の手順にスキップします。

   | オプション | 説明 |
   |--- |--- |
   | **[!UICONTROL Server Hostname]** | Elasticsearchまたは OpenSearch を実行しているマシンの完全修飾ホスト名または IP アドレスを入力します。<br> クラウドインフラストラクチャー上のAdobe Commerce：統合システムからこの価値を取得します。 |
   | **[!UICONTROL Server Port]** | Web サーバーのプロキシポートを入力します。 デフォルトは 9200<br> クラウドインフラストラクチャー上のAdobe Commerceです。この値は、統合システムから取得してください。 |
   | **[!UICONTROL Index Prefix]** | 検索エンジンのインデックスプレフィックスを入力します。 複数のCommerce インストールに 1 つのインスタンスを使用する場合（ステージング環境と実稼動環境）、インストールごとに一意のプレフィックスを指定する必要があります。 それ以外の場合は、デフォルトのプレフィックス magento2 を使用できます。 |
   | **[!UICONTROL Enable HTTP Auth]** | 検索エンジン サーバーの認証を有効にした場合のみ、[**[!UICONTROL Yes]**] をクリックします。 その場合は、指定されたフィールドにユーザー名とパスワードを入力します。 |
   | **[!UICONTROL Server Timeout]** | Elasticsearchまたは OpenSearch サーバーへの接続を確立しようとするときに待機する時間（秒単位）を入力します。 |

1. 「**[!UICONTROL Test Connection]**」をクリックします。

   応答の例：

   ![ 成功 ](../../assets/configuration/elastic_test-success.png)

   続行：

   - [検索エンジン用に Apache を設定する](../../installation/prerequisites/search-engine/configure-apache.md)
   - [検索エンジンの nginx の設定](../../installation/prerequisites/search-engine/configure-nginx.md)

   以下が表示されます。

   ![ 失敗 ](../../assets/configuration/elastic_test-fail.png)

その場合は、次の操作を試してください。

- 検索エンジン サーバーが実行中であることを確認してください。
- サーバーがCommerceとは別のホスト上にある場合は、Commerce サーバーにログインし、検索エンジンホストに対して ping を実行します。 ネットワーク接続の問題を解決し、接続を再度テストします。
- Elasticsearchまたは OpenSearch を起動したコマンドウィンドウで、スタックトレースと例外を調べます。 続行する前にそれらを解決する必要があります。 特に、`root` 権限を持つユーザーとして検索エンジンを起動したことを確認してください。
- [UNIX ファイアウォールと SELinux](../../installation/prerequisites/search-engine/overview.md#firewall-and-selinux) の両方が無効になっていることを確認するか、検索エンジンとCommerceが相互に通信できるようにルールを設定します。
- **[!UICONTROL Server Hostname]** フィールドの値を確認します。 サーバーが使用可能であることを確認します。 代わりに、サーバーの IP アドレスを試してみてください。
- `netstat -an | grep <listen-port>` コマンドを使用して、**[!UICONTROL Server Port]** フィールドで指定されたポートが別のプロセスで使用されていないことを確認します。

  例えば、検索エンジンがデフォルトのポートで実行されているかどうかを確認するには、次のコマンドを使用します。

  ```bash
  netstat -an | grep 9200
  ```

  ポート 9200 で実行されている場合は、次のように表示されます。

  ```
  `tcp        0      0 :::9200            :::-         LISTEN`
  ```

## カタログ検索のインデックスを再作成して、ページ全体のキャッシュを更新します。

検索エンジンの設定を変更した後、管理者またはコマンドラインを使用して、カタログ検索インデックスを再インデックスし、ページのフルキャッシュを更新する必要があります。

管理者を使用してキャッシュを更新するには：

1. 管理者で、**[!UICONTROL System]**/**[!UICONTROL Cache Management]** をクリックします。
1. 「**[!UICONTROL Page Cache]**」の横にあるチェックボックスをオンにします。
1. 右上の **[!UICONTROL Actions]** リストで、「**更新**」をクリックします。

   ![ キャッシュ管理 ](../../assets/configuration/refresh-cache.png)

コマンドラインを使用してキャッシュをクリーンアップするには：[`bin/magento cache:clean`](../cli/manage-cache.md#clean-and-flush-cache-types)

コマンドラインを使用してインデックスを再作成するには：

1. [ ファイルシステムのオーナー ](../../installation/prerequisites/file-system/overview.md) としてCommerce サーバーにログインするか、に切り替えます。
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
   >キャッシュとは異なり、インデクサーは cron ジョブによって更新されます。 検索エンジンの使用を開始する前に、[cron が有効になっていること ](../cli/configure-cron-jobs.md) を確認します。
