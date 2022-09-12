---
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 1%

---
# 通信がセキュリティで保護されていることを確認します

この節では、HTTP 基本認証が機能していることを確認する 2 つの方法について説明します。

* の使用 `curl` コマンドを使用して、クラスタの状態を取得するには、ユーザ名とパスワードを入力する必要があることを確認します
* 管理での HTTP 基本認証の設定

## の使用 `curl` クラスタの状態を確認するコマンド

次のコマンドを入力します。

```bash
curl -i http://<hostname, ip, or localhost>:<proxy port>/_cluster/health
```

例えば、検索エンジンサーバーでコマンドを入力し、プロキシがポート 8080 を使用する場合：

```bash
curl -i http://localhost:8080/_cluster/health
```

次のメッセージが表示され、認証に失敗したことを示します。

```terminal
HTTP/1.1 401 Unauthorized
Date: Tue, 23 Feb 2016 20:35:29 GMT
Content-Type: text/html
Content-Length: 194
Connection: keep-alive
WWW-Authenticate: Basic realm="Restricted"
<html>
<head><title>401 Authorization Required</title></head>
<body bgcolor="white">
  <center><h1>401 Authorization Required</h1></center>
</body>
</html>
```

次のコマンドを試してみてください。

```bash
curl -i -u <username>:<password> http://<hostname, ip, or localhost>:<proxy port>/_cluster/health
```

例：

```bash
curl -i -u magento_elasticsearch:mypassword http://localhost:8080/_cluster/health
```

この時点で、コマンドは次のようなメッセージで成功します。

```terminal
HTTP/1.1 200 OK
Date: Tue, 23 Feb 2016 20:38:03 GMT
Content-Type: application/json; charset=UTF-8
Content-Length: 389
Connection: keep-alive
{"cluster_name":"elasticsearch","status":"yellow","timed_out":false,"number_of_nodes":1,"number_of_data_nodes":1,"active_primary_shards":5,"active_shards":5,"relocating_shards":0,"initializing_shards":0,"unassigned_shards":5,"delayed_unassigned_shards":0,"number_of_pending_tasks":0,"number_of_in_flight_fetch":0,"task_max_waiting_in_queue_millis":0,"active_shards_percent_as_number":50.0}
```

## 管理での HTTP 基本認証の設定

同じタスクを実行します ( [検索エンジンの設定](../configuration/search/configure-search-engine.md) *例外* クリック **[!UICONTROL Yes]** から **[!UICONTROL Enable Elasticsearch HTTP Auth]** の一覧を開き、指定したフィールドにユーザー名とパスワードを入力します。

クリック **[!UICONTROL Test Connection]** 正常に動作するようにし、 **[!UICONTROL Save Config]**.

続行する前に、Magentoキャッシュをフラッシュし、インデックスを再作成する必要があります。
