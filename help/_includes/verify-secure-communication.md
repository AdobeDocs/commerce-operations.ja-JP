---
source-git-commit: 4c18f00e0b92e49924676274c4ed462a175a7e4b
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 1%

---
# 通信がセキュリティで保護されていることを確認

この項では、HTTP 基本認証が機能していることを確認する 2 つの方法について説明します。

* の使用 `curl` 確認するコマンド クラスタ状態を取得するには、ユーザー名とパスワードを入力する必要があります
* 管理者での HTTP 基本認証の設定

## を使用 `curl` クラスターの状態を確認するコマンド

次のコマンドを入力します。

```bash
curl -i http://<hostname, ip, or localhost>:<proxy port>/_cluster/health
```

例えば、検索エンジンサーバーにコマンドを入力し、プロキシがポート 8080 を使用している場合は、次のようになります。

```bash
curl -i http://localhost:8080/_cluster/health
```

次のメッセージが表示され、認証が失敗したことを示します。

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

次のコマンドを試してください。

```bash
curl -i -u <username>:<password> http://<hostname, ip, or localhost>:<proxy port>/_cluster/health
```

例：

```bash
curl -i -u magento_elasticsearch:mypassword http://localhost:8080/_cluster/health
```

今回は、コマンドが成功し、次のようなメッセージが表示されます。

```terminal
HTTP/1.1 200 OK
Date: Tue, 23 Feb 2016 20:38:03 GMT
Content-Type: application/json; charset=UTF-8
Content-Length: 389
Connection: keep-alive
{"cluster_name":"elasticsearch","status":"yellow","timed_out":false,"number_of_nodes":1,"number_of_data_nodes":1,"active_primary_shards":5,"active_shards":5,"relocating_shards":0,"initializing_shards":0,"unassigned_shards":5,"delayed_unassigned_shards":0,"number_of_pending_tasks":0,"number_of_in_flight_fetch":0,"task_max_waiting_in_queue_millis":0,"active_shards_percent_as_number":50.0}
```

## 管理画面で HTTP 基本認証を設定

の説明と同じタスクを実行します [検索エンジン設定](../configuration/search/configure-search-engine.md) *例外* click **[!UICONTROL Yes]** から **[!UICONTROL Enable HTTP Auth]** 表示されたフィールドにユーザー名とパスワードを入力します。

クリック **[!UICONTROL Test Connection]** 動作することを確認し、 **[!UICONTROL Save Config]**.

続行する前に、キャッシュをフラッシュして再インデックス化する必要があります。
