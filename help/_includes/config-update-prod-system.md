---
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '85'
ht-degree: 0%

---
# 本番システムを更新

**本番システムを更新するには**:

1. 本番システムに、ファイルシステムの所有者としてログインします。
1. アプリケーションルートに変更し、メンテナンスモードを有効にします。

   ```bash
   cd <Magento root dir>
   ```

   ```bash
   bin/magento maintenance:enable
   ```

   IP アドレスのホワイトリスト設定機能など、その他のオプションについては、 [`magento maintenance:enable`](../installation/tutorials/maintenance-mode.md).

1. 次の設定を行って、実行中のキューワーカーを停止します。 `cron_run` から `false` in `app/etc/env.php` 次のように指定します。

   ```php?start_inline=1
   'cron_consumers_runner' => [
           'cron_run' => false
       ]
   ```

1. 設定を更新します。

   ```bash
   bin/magento app:config:import
   ```

1. 最後に `kill` アクティブなコンシューマープロセス

   ```bash
   kill <PID>
   ```

   ここで、 `PID` 強制終了するプロセス ID です。例：

   ```bash
   kill 1234
   ```

1. ソース管理からコードを抽出します。

   ```bash
   git pull mconfig m2.2_deploy
   ```

1. 設定を更新します。

   ```bash
   bin/magento app:config:import
   ```

1. キャッシュをクリーンアップします。

   ```bash
   bin/magento cache:clean
   ```

1. メンテナンスモードを終了します。

   ```bash
   bin/magento maintenance:disable
   ```
