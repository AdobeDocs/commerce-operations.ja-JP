---
title: RabbitMQ から ActiveMQ への移行
description: Adobe Commerceのオンプレミスインストールに使用する Message Queue Broker の置き換えについて説明します。
feature: Services, Configuration
source-git-commit: 8f57a4fa7744f4647ab96d0fcfae08b8eb4927c6
workflow-type: tm+mt
source-wordcount: '648'
ht-degree: 0%

---

# ActiveMQ への移行

ActiveMQ （Apache ActiveMQ Artemis）は、Adobe Commerceでメッセージキューを処理するために RabbitMQ の代わりとなる高性能のマルチプロトコルメッセージブローカーです。

2.4.8-p3、2.4.7-p8 および 2.4.6-p13 以降、Adobe Commerceはメッセージキューブローカーとして ActiveMQ をサポートします。 これにより、オンプレミスインストールがインフラストラクチャ要件と専門知識に基づいて RabbitMQ と ActiveMQ のどちらかを選択する柔軟性が向上します。

## 始める前に

移行を開始する前に、以下を確認します。

1. `app/etc/env.php` で現在の RabbitMQ 設定を確認します。
1. データベースとコードベースの完全なバックアップを取ります。
1. インストール環境が ActiveMQ のシステム要件を満たしていることを確認します。
1. メンテナンスウィンドウを計画して移行を完了します。

## 移行パス

ActiveMQ への移行は簡単なプロセスですが、保留中のすべてのメッセージがブローカーを切り替える前に処理されるようにすることが不可欠です。

これらの移行手順では、メッセージキューブローカーを使用するアプリケーションがAdobe Commerceのみであることを前提としています。

### 手順 1：サイトをメンテナンスモードにする

1. サイトを [ メンテナンスモード ](../../installation/tutorials/maintenance-mode.md) にします。

   ```bash
   bin/magento maintenance:enable
   ```

1. メンテナンスモードが有効になっていることを確認します。

   ```bash
   bin/magento maintenance:status
   ```

### 手順 2:RabbitMQ メッセージ数の確認

先に進む前に、RabbitMQ のすべてのメッセージが処理されていることを確認します。 次のいずれかの方法を使用します。

#### 方法 A:RabbitMQ 管理ダッシュボードの使用

1. RabbitMQ 管理 UI （`http://<host>:15672`）にアクセスします。
1. 既定の資格情報：`guest/guest`
1. 「**キュー**」タブに移動します
1. すべてのキューに **0 メッセージが表示されることを確認する**

   ![RabbitMQ 管理ダッシュボード ](../../assets/upgrade-guide/rabbitmq_mgmt_dashboard.png)

#### 方法 B: rabbitmqctl コマンドラインの使用

1. すべてのキューとそのメッセージ数を確認します。

   ```bash
   rabbitmqctl list_queues name messages consumers
   ```

   <img src="../../assets/upgrade-guide/rabbitmqctl.png" alt="RabbitMQ CLI 出力" width="500" />

1. 詳細なキュー情報を確認します。

   ```bash
   rabbitmqctl list_queues name messages messages_ready messages_unacknowledged consumers
   ```

   <img src="../../assets/upgrade-guide/rabbitmqctl_detailed.png" alt="RabbitMQ CLI の詳細出力" width="500" />

### 手順 3：保留中のメッセージの処理

いずれかのキューでメッセージが保留中の場合は、処理してから続行します。

1. 使用可能なコンシューマーのリストを取得します。

   ```bash
   bin/magento queue:consumers:list
   ```

1. コンシューマーをグループとして、または個々のメッセージキューごとに処理します。

   - **コンシューマーをグループとして処理**

     ```bash
     bin/magento cron:run --group=consumers
     ```

     >[!NOTE]
     >
     >Cron が既にシステムで実行されている場合は、手動で実行する必要はあり `bin/magento cron:run --group=consumers` せん。 代わりに、手順 2 のコマンドを使用してメッセージ数を確認し、メッセージが処理されていることを確認します。

   - **特定のメッセージキューの処理**

     ```bash
     bin/magento queue:consumers:start <consumer_name> --max-messages=<number>
     ```

     例えば、非同期操作を処理するには、次のようにします。

     ```bash
     bin/magento queue:consumers:start async.operations.all --max-messages=1000
     ```

     >[!NOTE]
     >
     >`--max-messages` パラメーターは、コンシューマーが停止するまでに処理するメッセージの数を制限します。 キューサイズに基づいて、この値を調整します。

   - **メッセージ処理の監視**

     すべてのキューが空になるまで、メッセージ数を継続的に確認します。

     ```bash
     # Check every few seconds until 0 messages remain
     watch -n 5 "rabbitmqctl list_queues name messages | grep -v '^Listing' | grep -v '0$'"
     ```

### 手順 4：すべてのメッセージが処理されることを確認する

次の手順に進む前に、**すべてのキューに表示されるメッセージが 0 件になる** ことを確認します。 手順 2 の検証コマンドを再度実行します。

>[!WARNING]
>
>未処理のメッセージがある場合は、次の手順に進まないでください。 メッセージがまだ保留中の間にブローカーを切り替えると、データが失われる可能性があります。

### 手順 5：コンシューマーと cron ジョブを停止する

1. 実行中のすべてのメッセージキューコンシューマーを停止します。

   ```bash
   # If using supervisor
   supervisorctl stop all
   
   # Or manually kill consumer processes
   pkill -f "queue:consumers:start"
   ```

1. cron ジョブを無効にする：

   ```bash
   bin/magento cron:remove
   ```

1. Cron ジョブが削除されたことを確認します。

   ```bash
   crontab -l
   ```

### 手順 6：現在の設定のバックアップ

現在の設定のバックアップを作成します。

```bash
cp app/etc/env.php app/etc/env.php.backup.rabbitmq
```

### 手順 7:RabbitMQ をオプションでアンインストールする

RabbitMQ が不要になった場合は、アンインストールできます。

### 手順 8:Adobe Commerceへの ActiveMQ のインストールと設定

STOMP プロトコルの構成や接続の検証など、ActiveMQ のインストールおよび構成タスクを完了するには、[ インストールおよび構成ガイド ](../../installation/prerequisites/activemq.md) を参照してください。

### 手順 9:cron ジョブの再インストール

1. テストが正常に完了したら、cron ジョブを再インストールします。

   ```bash
   bin/magento cron:install
   ```

1. cron ジョブがスケジュールされていることを確認します。

   ```bash
   crontab -l
   ```

### 手順 10：メンテナンスモードを無効にする

1. すべてが正常に動作していることを確認したら、メンテナンスモードを無効にします。

   ```bash
   bin/magento maintenance:disable
   ```

1. メンテナンスモードが無効になっていることを確認します。

   ```bash
   bin/magento maintenance:status
   ```

### 手順 11：システムの監視

移行後 24～48 時間システムを監視し、すべてのキュー操作が正しく機能していることを確認します。

- ActiveMQ Web コンソールでメッセージのスループットを定期的に確認します
- キュー関連エラーのアプリケーションログの監視
- 非同期操作（設定の保存、書き出しなど）が機能していることを確認します
- コンシューマーが実行中であることを cron ログで確認

```bash
# Monitor system logs for queue activity
tail -f var/log/system.log | grep -i queue

# Monitor cron logs
tail -f var/log/cron.log

# Check running consumer processes
ps aux | grep "queue:consumers:start"
```

## Rollback

移行中または移行後に問題が発生した場合は、RabbitMQ にロールバックできます。

1. メンテナンスモードを有効にする：

   ```bash
   bin/magento maintenance:enable
   ```

1. すべてのコンシューマーを停止し、cron を無効にします。

   ```bash
   pkill -f "queue:consumers:start"
   bin/magento cron:remove
   ```

1. 以前の設定を復元します。

   ```bash
   cp app/etc/env.php.backup.rabbitmq app/etc/env.php
   ```

1. RabbitMQ を起動します（停止している場合）。

   ```bash
   sudo systemctl start rabbitmq-server
   ```

1. キャッシュのクリア：

   ```bash
   bin/magento cache:flush
   ```

1. Cron を再インストールします。

   ```bash
   bin/magento cron:install
   ```

1. メンテナンスモードを無効にする：

   ```bash
   bin/magento maintenance:disable
   ```

移行が完了したら、設定値をさらに変更する必要はありません。

