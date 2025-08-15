---
title: Cron ジョブの設定と実行
description: Cron ジョブの管理方法を説明します。
exl-id: 8ba2b2f9-5200-4e96-9799-1b00d7d23ce1
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '748'
ht-degree: 0%

---

# Cron ジョブの設定

{{file-system-owner}}

いくつかのCommerce機能には少なくとも 1 つの cron ジョブが必要で、これにより将来のアクティビティがスケジュールされます。 これらのアクティビティの一部のリストを次に示します。

- カタログ価格ルール
- ニュースレター
- Google サイトマップの生成
- 顧客アラート/通知（製品価格の変更、製品の再入荷）
- 再インデックス
- 民間販売（Adobe Commerceのみ）
- 通貨レートの自動更新
- すべてのCommerce メール （注文確認およびトランザクションを含む）

>[!WARNING]
>
>スクリプトが削除されているので、`dev/tools/cron.sh` を実行できなくなりました。

>[!INFO]
>
>Commerceは、インデックス作成を含む多くの重要なシステム機能に対して、適切な cron ジョブ設定に依存します。 適切に設定されていない場合、Commerceが期待どおりに機能しません。

UNIX システムは、特定のユーザーが実行するタスクを _crontab_ を使用してスケジュールします。このファイルには、デーモンに「この日付に、このコマンドを現時点で実行する」ように指示する指示が含まれています。 各ユーザは独自の crontab を持ち、特定の crontab 内のコマンドは、その crontab を所有するユーザとして実行されます。

Web ブラウザーで cron を実行するには、[Secure cron.php to run in a browser](../security/secure-cron-php.md) を参照してください。

## Commerce crontab を作成または削除する

この節では、Commerce crontab （Commerce cron ジョブの設定）を作成または削除する方法について説明します。

_crontab_ は、cron ジョブを実行するために使用される設定です。

Commerce アプリケーションは、異なる設定で実行できる cron タスクを使用します。 PHP のコマンドライン設定は、インデクサーのインデックス再作成、メールの生成、サイトマップの生成などを行う一般的な cron ジョブを制御します。

>[!WARNING]
>
>- インストールおよびアップグレード時の問題を回避するために、PHP コマンドライン設定と PHP web サーバープラグインの設定の両方に同じ PHP 設定を適用することを強くお勧めします。 詳しくは、[PHP の設定が必要 ](../../installation/prerequisites/php-settings.md) を参照してください。
>- マルチノードシステムでは、crontab は 1 つのノードでのみ実行できます。 これは、パフォーマンスやスケーラビリティに関連する理由で複数の web ノードを設定した場合にのみ適用されます。

### Commerce crontab の作成

バージョン 2.2 以降、Commerceによって crontab が作成されます。 Commerce ファイルシステムの所有者用に設定された crontab にCommerce crontab を追加します。 つまり、他の拡張機能やアプリケーション用に crontab を既に設定している場合は、Commerce crontab を追加します。

Commerce crontab は `#~ MAGENTO START` 内にあり、crontab 内にはコメントが `#~ MAGENTO END` まれています。

Commerce crontab を作成するには：

1. [ ファイルシステムの所有者 ](../../installation/prerequisites/file-system/overview.md) としてログインするか、に切り替えます。
1. Commerce インストールディレクトリに移動します。
1. 次のコマンドを入力します。

   ```bash
   bin/magento cron:install [--force]
   ```

`--force` を使用して、既存の crontab を書き換えます。

>[!INFO]
>
>- `magento cron:install` は、`#~ MAGENTO START` 内の既存の crontab を書き換えず、crontab 内のコメントを `#~ MAGENTO END` き直しません。
>- `magento cron:install --force` は、Commerce コメント以外の cron ジョブには影響しません。

crontab を表示するには、ファイルシステムの所有者として次のコマンドを入力します。

```bash
crontab -l
```

次に例を示します。

```
#~ MAGENTO START c5f9e5ed71cceaabc4d4fd9b3e827a2b
* * * * * /usr/bin/php /var/www/html/magento2/bin/magento cron:run 2>&1 | grep -v "Ran jobs by schedule" >> /var/www/html/magento2/var/log/magento.cron.log
#~ MAGENTO END c5f9e5ed71cceaabc4d4fd9b3e827a2b
```

>[!INFO]
>
>`update/cron.php` ファイルはCommerce 2.4.0 で削除されました。このファイルがインストール上に存在する場合は、安全に削除できます。
>
>`update/cron.php` と `bin/magento setup:cron:run` への参照も crontab から削除してください

### Commerce crontab を削除します。

Commerce アプリケーションをアンインストールする前にのみ、Commerce crontab を削除してください。

Commerce crontab を削除するには：

1. としてログインするか、[ ファイルシステムの所有者 ](../../installation/prerequisites/file-system/overview.md) に切り替えます。
1. Commerce インストールディレクトリに移動します。
1. 次のコマンドを入力します。

   ```bash
   bin/magento cron:remove
   ```

>[!INFO]
>
>このコマンドは、`#~ MAGENTO START` 外の cron ジョブや crontab のコメント `#~ MAGENTO END` は影響しません。

## コマンドラインから cron を実行します

コマンドオプション：

```bash
bin/magento cron:run [--group="<cron group name>"]
```

ここで、`--group` は実行する cron グループを指定します（すべてのグループに対して cron を実行する場合は、このオプションを省略します）。

インデックス作成 cron ジョブを実行するには、次のように入力します。

```bash
bin/magento cron:run --group index
```

デフォルトの cron ジョブを実行するには、以下を入力します。

```bash
bin/magento cron:run --group default
```

カスタム cron ジョブとグループを設定するには、[ カスタム cron ジョブとグループの設定 ](../cron/custom-cron.md) を参照してください。

>[!INFO]
>
>cron を 2 回実行する必要があります。1 回目は実行するタスクを検出し、2 回目はタスク自体を実行します。 2 回目の cron 実行は、各タスクについて `scheduled_at` 回以降に実行する必要があります。

## ログ

すべて `cron` ジョブ情報は、`system.log` から別の `cron.log` に移動しました。
デフォルトでは、cron 情報は `<install_directory>/var/log/cron.log` にあります。
Cron ジョブからのすべての例外は `\Magento\Cron\Observer\ProcessCronQueueObserver::execute` によって記録されます。

`cron.log` にログインする以外に、

- `ERROR` および `MISSED` のステータスを持つ失敗したジョブが `<install_directory>/var/log/support_report.log` に記録されます。

- `ERROR` ステータスのジョブは、常に `CRITICAL` で `<install_directory>/var/log/exception.log` として記録されます。

- `MISSED` ステータスのジョブは、`INFO` ディレクトリに `<install_directory>/var/log/debug.log` として記録されます（開発者モードのみ）。

>[!INFO]
>
>また、すべての cron データはCommerce データベースの `cron_schedule` テーブルにも書き込まれます。 この表には、次のような cron ジョブの履歴が表示されます。
>
>- ジョブ ID とコード
>- ステータス
>- 作成日
>- スケジュール日
>- 実行日
>- 完了日
>
>テーブルのレコードを表示するには、コマンドラインでCommerce データベースにログインして、`SELECT * from cron_schedule;` と入力します。
