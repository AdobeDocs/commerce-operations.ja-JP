---
title: 検索エンジンの設定
description: Adobe CommerceとMagento Open Sourceのオンプレミスデプロイメント用に検索エンジンを設定します。
feature: Configuration, Search
exl-id: 61fbe0c2-bdd5-4f57-a518-23e180401804
source-git-commit: 789b7d9dc400b1f669de0067a59e2036c2977a19
workflow-type: tm+mt
source-wordcount: '652'
ht-degree: 0%

---

# 検索エンジンの設定

このセクションでは、Adobe CommerceとMagento Open SourceのオンプレミスデプロイメントでElasticsearchまたは OpenSearch をテストする場合に選択する必要がある最小の設定について説明します。

>[!TIP]
>
>バージョン 2.4.4 および 2.4.3-p2 では、 **Elasticsearch** は OpenSearch にも適用されます。
>バージョン 2.4.6 でElasticsearch8.x のサポートが導入された際に、Elasticsearchと OpenSearch 設定を区別するための新しいラベルが作成されました。

検索エンジンの設定について詳しくは、 [ユーザーガイド](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-configuration.html).

## 管理者から検索エンジンを設定する

>[!TIP]
>
>新しい検索エンジンバージョンへのアップグレード手順については、 [アップグレードの前提条件](../../upgrade/prepare/prerequisites.md).

システムで OpenSearch またはElasticsearchを使用するように設定するには：

1. 管理者として管理者にログインします。
1. クリック **[!UICONTROL Stores]** > [!UICONTROL Settings] > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]**.
1. 次の **[!UICONTROL Search Engine]** リストで、検索エンジンの対応するバージョンを選択します。

   Commerce との接続を設定およびテストするために必要なオプションを次の表に示します。 検索エンジンのサーバ設定を変更しない限り、デフォルトは機能します。 次の手順に進みます。

   | オプション | 説明 |
   |--- |--- |
   | **[!UICONTROL Server Hostname]** | Elasticsearchまたは OpenSearch を実行するマシンの完全修飾ホスト名または IP アドレスを入力します。<br>Adobe Commerce on cloud infrastructure:この値は、統合システムから取得します。 |
   | **[!UICONTROL Server Port]** | Web サーバーのプロキシポートを入力します。 デフォルトは 9200 です。<br>Adobe Commerce on cloud infrastructure:この値は、統合システムから取得します。 |
   | **[!UICONTROL Index Prefix]** | 検索エンジンのインデックスのプレフィックスを入力します。 複数のコマースインストール（ステージング環境と実稼動環境）に 1 つのインスタンスを使用する場合は、インストールごとに一意のプレフィックスを指定する必要があります。 それ以外の場合は、デフォルトのプレフィックス magento2 を使用できます。 |
   | **[!UICONTROL Enable HTTP Auth]** | クリック **[!UICONTROL Yes]** 検索エンジンサーバーの認証を有効にした場合にのみ有効です。 その場合は、提供されたフィールドにユーザー名とパスワードを入力します。 |
   | **[!UICONTROL Server Timeout]** | Elasticsearchまたは OpenSearch サーバーへの接続を確立しようとしたときに待機する時間（秒）を入力します。 |

1. クリック **[!UICONTROL Test Connection]**.

   レスポンスのサンプル：

   ![成功](../../assets/configuration/elastic_test-success.png)

   続行：

   - [検索エンジン用に Apache を設定](../../installation/prerequisites/search-engine/configure-apache.md)
   - [検索エンジン用に nginx を設定する](../../installation/prerequisites/search-engine/configure-nginx.md)

   または、

   ![失敗](../../assets/configuration/elastic_test-fail.png)

その場合は、次の操作を試します。

- 検索エンジンサーバーが実行中であることを確認します。
- サーバーが Commerce とは異なるホスト上にある場合は、Commerce サーバーにログインし、検索エンジンホストに ping を送信します。 ネットワーク接続の問題を解決し、接続を再度テストします。
- スタックトレースと例外をElasticsearchまたは OpenSearch を開始したコマンドウィンドウを調べます。 続行する前に、それらを解決する必要があります。 特に、を使用して検索エンジンを起動したことを確認してください。 `root` 権限。
- 必ず [UNIX ファイアウォールと SELinux](../../installation/prerequisites/search-engine/overview.md#firewall-and-selinux) は両方とも無効になっているか、検索エンジンとコマースが相互に通信できるようにルールを設定しています。
- の値を検証します。 **[!UICONTROL Server Hostname]** フィールドに入力します。 サーバーが使用可能であることを確認します。 代わりに、サーバーの IP アドレスを試すことができます。
- 以下を使用： `netstat -an | grep <listen-port>` コマンドを使用して、 **[!UICONTROL Server Port]** フィールドが別のプロセスで使用されていません。

   例えば、検索エンジンがデフォルトのポートで実行されているかどうかを確認するには、次のコマンドを使用します。

   ```bash
   netstat -an | grep 9200
   ```

   ポート 9200 で実行されている場合は、次のように表示されます。

   ```terminal
   `tcp        0      0 :::9200            :::-         LISTEN`
   ```

## カタログ検索のインデックスを再作成し、ページキャッシュ全体を更新

検索エンジンの設定を変更した後、カタログ検索インデックスを再インデックスし、管理者またはコマンドラインを使用してページキャッシュ全体を更新する必要があります。

管理者を使用してキャッシュを更新するには：

1. 管理者で、 **[!UICONTROL System]** > **[!UICONTROL Cache Management]**.
1. の横にあるチェックボックスを選択します。 **[!UICONTROL Page Cache]**.
1. 次の **[!UICONTROL Actions]** 右上のリストで、「 **更新**.

   ![キャッシュ管理](../../assets/configuration/refresh-cache.png)

コマンドラインを使用してキャッシュをクリーンアップするには： [`bin/magento cache:clean`](../cli/manage-cache.md#clean-and-flush-cache-types)

コマンドラインを使用してインデックスを再作成するには：

1. コマースサーバーに、 [ファイルシステム所有者](../../installation/prerequisites/file-system/overview.md).
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
