---
title: cron ジョブの設定と実行
description: Adobe Commerceでcron ジョブを設定および管理する方法について説明します。 スケジュール設定、トラブルシューティングなどの手法を紹介します。
exl-id: 8ba2b2f9-5200-4e96-9799-1b00d7d23ce1
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '764'
ht-degree: 0%

---

# cron ジョブの設定

{{file-system-owner}}

Commerceのいくつかの機能には、少なくとも1つのcron ジョブが必要で、将来のアクティビティをスケジュールします。 これらのアクティビティの一部を以下に示します。

- カタログ価格ルール
- ニュースレター
- Google サイトマップの生成
- 顧客アラート/通知（製品価格変更、再入荷）
- インデックス再作成
- プライベートセールス（Adobe Commerceのみ）
- 通貨レートの自動更新
- すべてのCommerce電子メール（注文確認と取引確認を含む）

>[!WARNING]
>
>スクリプトが削除されたため、`dev/tools/cron.sh`を実行できなくなりました。

>[!INFO]
>
>Commerceは、インデックス作成を含む多くの重要なシステム機能について、適切なcron ジョブ設定に依存します。 適切に設定しないと、Commerceが期待どおりに機能しません。

UNIX システムは、_crontab_&#x200B;を使用して特定のユーザーが実行するタスクをスケジュールします。これは、実際にデーモンに「この日付でこのコマンドを実行する」ように指示するcron デーモンへの指示を含むファイルです。 各ユーザーには独自のcrontabがあり、特定のcrontab内のコマンドは、それを所有するユーザーとして実行されます。

Web ブラウザーでcronを実行するには、[&#x200B; ブラウザーで実行するcron.phpのセキュリティ保護](../security/secure-cron-php.md)を参照してください。

## Commerce crontabの作成または削除

この節では、Commerce crontab （つまり、Commerce cron ジョブの設定）を作成または削除する方法について説明します。

_crontab_&#x200B;は、cron ジョブの実行に使用される設定です。

Commerce アプリケーションでは、様々な設定で実行できるcron タスクを使用します。 PHPのコマンドライン設定は、インデクサーのインデックス再作成、電子メールの生成、サイトマップの生成などを行う一般的なcron ジョブを制御します。

>[!WARNING]
>
>- インストールおよびアップグレード時の問題を回避するには、PHP コマンドライン設定とPHP web サーバープラグインの設定の両方に同じPHP設定を適用することを強くお勧めします。 詳しくは、[必要なPHP設定](../../installation/prerequisites/php-settings.md)を参照してください。
>- マルチノードシステムでは、crontabは1つのノードでのみ実行できます。 これは、パフォーマンスまたはスケーラビリティに関連する理由で複数のweb ノードを設定した場合にのみ適用されます。

### Commerce crontabの作成

バージョン 2.2以降、Commerceはcrontabを作成します。 Commerceのcrontabは、Commerce ファイルシステムのオーナー用に設定されたcrontabに追加します。 つまり、他の拡張機能やアプリケーション用にcrontabsを既に設定している場合は、Commerce crontabが追加されます。

Commerceのcrontabは、crontab内の`#~ MAGENTO START`件と`#~ MAGENTO END`件のコメント内にあります。

Commerce crontabを作成するには：

1. [&#x200B; ファイルシステム所有者](../../installation/prerequisites/file-system/overview.md)としてログインするか、切り替えます。
1. Commerceのインストールディレクトリに移動します。
1. 次のコマンドを入力します。

   ```shell
   bin/magento cron:install [--force]
   ```

`--force`を使用して、既存のcrontabを書き換えます。

>[!INFO]
>
>- `magento cron:install`は、crontab内の`#~ MAGENTO START`および`#~ MAGENTO END`件のコメント内の既存のcrontabを書き換えません。
>- `magento cron:install --force`は、Commerce コメント以外のcron ジョブには影響しません。

crontabを表示するには、ファイルシステム所有者として次のコマンドを入力します。

```shell
crontab -l
```

サンプルは次のとおりです。

```shell
#~ MAGENTO START c5f9e5ed71cceaabc4d4fd9b3e827a2b
* * * * * /usr/bin/php /var/www/html/magento2/bin/magento cron:run 2>&1 | grep -v "Ran jobs by schedule" >> /var/www/html/magento2/var/log/magento.cron.log
#~ MAGENTO END c5f9e5ed71cceaabc4d4fd9b3e827a2b
```

>[!INFO]
>
>`update/cron.php` ファイルはCommerce 2.4.0で削除されました。このファイルがインストールに存在する場合は、安全に削除できます。
>
>`update/cron.php`および`bin/magento setup:cron:run`への参照もcrontab&#39;から削除する必要があります

### Commerceのcrontabを削除

Commerce アプリケーションをアンインストールする前にのみ、Commerce crontabを削除する必要があります。

Commerceのcrontabを削除するには：

1. としてログインするか、[&#x200B; ファイルシステム所有者](../../installation/prerequisites/file-system/overview.md)に切り替えます。
1. Commerceのインストールディレクトリに移動します。
1. 次のコマンドを入力します。

   ```shell
   bin/magento cron:remove
   ```

>[!INFO]
>
>このコマンドは、crontabの`#~ MAGENTO START`および`#~ MAGENTO END` コメント以外のcron ジョブには影響しません。

## コマンドラインからcronを実行する

コマンドオプション：

```shell
bin/magento cron:run [--group="<cron group name>"]
```

ここで`--group`は、実行するcron グループを指定します（すべてのグループに対してcronを実行する場合は、このオプションを省略します）

インデックス作成cron ジョブを実行するには、次のように入力します。

```shell
bin/magento cron:run --group index
```

デフォルトのcron ジョブを実行するには、次のように入力します。

```shell
bin/magento cron:run --group default
```

カスタム cron ジョブとグループを設定するには、[&#x200B; カスタム cron ジョブとcron グループの設定](../cron/custom-cron.md)を参照してください。

>[!INFO]
>
>実行するタスクを最初に見つけ出すcronと、タスク自体を実行する2回目のcronを2回実行する必要があります。 2回目のcron実行は、各タスクに対して`scheduled_at`回以降に実行する必要があります。

## ログ

すべての`cron`件のジョブ情報が`system.log`から別の`cron.log`に移動しました。
デフォルトでは、cron情報は`<install_directory>/var/log/cron.log`にあります。
cron ジョブからのすべての例外は、`\Magento\Cron\Observer\ProcessCronQueueObserver::execute`によって記録されます。

`cron.log`にログインしているだけでなく、

- ステータスが`ERROR`および`MISSED`の失敗したジョブは、`<install_directory>/var/log/support_report.log`に記録されます。

- ステータスが`ERROR`のジョブは、常に`<install_directory>/var/log/exception.log`に`CRITICAL`として記録されます。

- ステータスが`MISSED`のジョブは、`<install_directory>/var/log/debug.log` ディレクトリに`INFO`として記録されます（開発者モードのみ）。

>[!INFO]
>
>すべてのcron データは、Commerce データベースの`cron_schedule` テーブルにも書き込まれます。 このテーブルには、次のようなcron ジョブの履歴が表示されます。
>
>- ジョブ IDとコード
>- ステータス
>- 作成日
>- 予定日
>- 実行日
>- 完了日
>
>テーブル内のレコードを表示するには、コマンドラインでCommerce データベースにログインし、`SELECT * from cron_schedule;`と入力します。
