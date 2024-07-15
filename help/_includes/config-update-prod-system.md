---
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '85'
ht-degree: 0%

---
# 実稼動システムを更新

**実稼動システムを更新するには**:

1. ファイルシステムの所有者として、実稼動システムにログインします。
1. アプリケーションルートに変更し、メンテナンスモードを有効にします。

   ```bash
   cd <Magento root dir>
   ```

   ```bash
   bin/magento maintenance:enable
   ```

   IP アドレスの許可リストを設定する機能など、その他のオプションについては、[`magento maintenance:enable`](../installation/tutorials/maintenance-mode.md) を参照してください。

1. `app/etc/env.php` で `cron_run` を `false` に設定して、実行中のキューワーカーをすべて停止します。

   ```php?start_inline=1
   'cron_consumers_runner' => [
           'cron_run' => false
       ]
   ```

1. 設定を更新します。

   ```bash
   bin/magento app:config:import
   ```

1. 最後に、アクティブなコンシューマープロセスを `kill` きます。

   ```bash
   kill <PID>
   ```

   `PID` は、強制終了されるプロセス ID です（例：）。

   ```bash
   kill 1234
   ```

1. ソース管理からコードを取り込みます。

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
