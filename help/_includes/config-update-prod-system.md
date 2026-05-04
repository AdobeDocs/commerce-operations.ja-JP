---
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '85'
ht-degree: 0%

---
# 実稼動システムの更新

**実稼動システムを更新するには**:

1. 本番システムにファイルシステム所有者としてログインします。
1. アプリケーションルートに変更し、メンテナンスモードを有効にします。

   ```shell
   cd <Magento root dir>
   ```

   ```shell
   bin/magento maintenance:enable
   ```

   IP アドレスのホワイトリストを設定する機能など、その他のオプションについては、[`magento maintenance:enable`](../installation/tutorials/maintenance-mode.md)を参照してください。

1. `cron_run`を`app/etc/env.php`の`false`に次のように設定して、実行中のキューワーカーを停止します。

   ```php?start_inline=1
   'cron_consumers_runner' => [
           'cron_run' => false
       ]
   ```

1. 設定を更新します。

   ```shell
   bin/magento app:config:import
   ```

1. 最後に、アクティブなコンシューマープロセスを`kill`個まで追加します。

   ```shell
   kill <PID>
   ```

   ここで、`PID`は破棄されるプロセス IDです。例：

   ```shell
   kill 1234
   ```

1. ソース管理からコードを取得します。

   ```shell
   git pull mconfig m2.2_deploy
   ```

1. 設定を更新します。

   ```shell
   bin/magento app:config:import
   ```

1. キャッシュをクリーニングします。

   ```shell
   bin/magento cache:clean
   ```

1. メンテナンスモードを終了します。

   ```shell
   bin/magento maintenance:disable
   ```
