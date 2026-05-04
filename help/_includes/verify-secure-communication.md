---
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 1%

---
# 通信が安全であることを確認する

この節では、HTTP Basic認証が機能していることを確認する2つの方法について説明します。

* `curl` コマンドを使用して検証するには、ユーザー名とパスワードを入力してクラスターステータスを取得する必要があります
* AdminでのHTTP Basic認証の設定

## `curl` コマンドを使用してクラスターの状態を確認する

次のコマンドを入力します。

```shell
curl -i http://<hostname, ip, or localhost>:<proxy port>/_cluster/health
```

例えば、検索エンジンサーバーでコマンドを入力し、プロキシでポート 8080を使用している場合は、次のようになります。

```shell
curl -i http://localhost:8080/_cluster/health
```

認証に失敗したことを示す次のメッセージが表示されます。

```text
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

次のコマンドを実行します。

```shell
curl -i -u <username>:<password> http://<hostname, ip, or localhost>:<proxy port>/_cluster/health
```

例：

```shell
curl -i -u magento_elasticsearch:mypassword http://localhost:8080/_cluster/health
```

この場合、コマンドは次のようなメッセージで成功します。

```text
HTTP/1.1 200 OK
Date: Tue, 23 Feb 2016 20:38:03 GMT
Content-Type: application/json; charset=UTF-8
Content-Length: 389
Connection: keep-alive
{"cluster_name":"elasticsearch","status":"yellow","timed_out":false,"number_of_nodes":1,"number_of_data_nodes":1,"active_primary_shards":5,"active_shards":5,"relocating_shards":0,"initializing_shards":0,"unassigned_shards":5,"delayed_unassigned_shards":0,"number_of_pending_tasks":0,"number_of_in_flight_fetch":0,"task_max_waiting_in_queue_millis":0,"active_shards_percent_as_number":50.0}
```

## AdminでのHTTP Basic認証の設定

[検索エンジン設定](../configuration/search/configure-search-engine.md) *で説明したタスクと同じタスクを実行します（*&#x200B;を除く）。**[!UICONTROL Enable HTTP Auth]** リストから&#x200B;**[!UICONTROL Yes]**&#x200B;をクリックし、指定されたフィールドにユーザー名とパスワードを入力します。

**[!UICONTROL Test Connection]**&#x200B;をクリックして動作することを確認し、**[!UICONTROL Save Config]**&#x200B;をクリックします。

続行する前に、キャッシュをフラッシュし、インデックスを再作成する必要があります。
