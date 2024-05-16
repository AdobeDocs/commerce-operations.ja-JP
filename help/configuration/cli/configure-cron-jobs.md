---
title: Cron ジョブの設定と実行
description: Cron ジョブの管理方法を説明します。
exl-id: 8ba2b2f9-5200-4e96-9799-1b00d7d23ce1
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
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
>実行できなくなりました `dev/tools/cron.sh` スクリプトが削除されたためです。

>[!INFO]
>
>Commerceは、インデックス作成を含む多くの重要なシステム機能に対して、適切な cron ジョブ設定に依存します。 適切に設定されていない場合、Commerceが期待どおりに機能しません。

UNIX システムは、特定のユーザーが実行するタスクを、 _crontab_&#x200B;これは cron デーモンに対し、「この時点でこのコマンドを実行する」という指示を実際にデーモンに伝える指示を含むファイルです。 各ユーザは独自の crontab を持ち、特定の crontab 内のコマンドは、その crontab を所有するユーザとして実行されます。

Web ブラウザーで cron を実行するには、以下を参照してください [ブラウザーで実行する cron.php を保護する](../security/secure-cron-php.md).

## Commerce crontab を作成または削除する

この節では、Commerce crontab （Commerce cron ジョブの設定）を作成または削除する方法について説明します。

この _crontab_ は、cron ジョブを実行するために使用される設定です。

Commerce アプリケーションは、異なる設定で実行できる cron タスクを使用します。 PHP のコマンドライン設定は、インデクサーのインデックス再作成、メールの生成、サイトマップの生成などを行う一般的な cron ジョブを制御します。

>[!WARNING]
>
>- インストールおよびアップグレード時の問題を回避するために、PHP コマンドライン設定と PHP web サーバープラグインの設定の両方に同じ PHP 設定を適用することを強くお勧めします。 詳しくは、を参照してください [必要な PHP 設定](../../installation/prerequisites/php-settings.md).
>- マルチノードシステムでは、crontab は 1 つのノードでのみ実行できます。 これは、パフォーマンスやスケーラビリティに関連する理由で複数の web ノードを設定した場合にのみ適用されます。

### Commerce crontab の作成

バージョン 2.2 以降、Commerceによって crontab が作成されます。 Commerce ファイルシステムの所有者用に設定された crontab にCommerce crontab を追加します。 つまり、他の拡張機能やアプリケーション用に crontab を既に設定している場合は、Commerce crontab を追加します。

Commerce crontab が内部にある `#~ MAGENTO START` および `#~ MAGENTO END` crontab のコメント。

Commerce crontab を作成するには：

1. としてログインするか、に切り替える [ファイルシステム所有者](../../installation/prerequisites/file-system/overview.md).
1. Commerce インストールディレクトリに移動します。
1. 次のコマンドを入力します。

   ```bash
   bin/magento cron:install [--force]
   ```

使用方法 `--force` 既存の crontab を書き換えます。

>[!INFO]
>
>- `magento cron:install` 内の既存の crontab を書き換えない `#~ MAGENTO START` および `#~ MAGENTO END` crontab のコメント。
>- `magento cron:install --force` は、Commerce コメント以外の cron ジョブには影響しません。

crontab を表示するには、ファイルシステムの所有者として次のコマンドを入力します。

```bash
crontab -l
```

次に例を示します。

```terminal
#~ MAGENTO START c5f9e5ed71cceaabc4d4fd9b3e827a2b
* * * * * /usr/bin/php /var/www/html/magento2/bin/magento cron:run 2>&1 | grep -v "Ran jobs by schedule" >> /var/www/html/magento2/var/log/magento.cron.log
#~ MAGENTO END c5f9e5ed71cceaabc4d4fd9b3e827a2b
```

>[!INFO]
>
>この `update/cron.php` ファイルはCommerce 2.4.0 で削除されました。このファイルがインストール上に存在する場合は、安全に削除できます。
>
>への参照 `update/cron.php` および `bin/magento setup:cron:run` は crontab からも削除されます

### Commerce crontab を削除します。

Commerce アプリケーションをアンインストールする前にのみ、Commerce crontab を削除してください。

Commerce crontab を削除するには：

1. としてログインするか、に切り替える [ファイルシステム所有者](../../installation/prerequisites/file-system/overview.md).
1. Commerce インストールディレクトリに移動します。
1. 次のコマンドを入力します。

   ```bash
   bin/magento cron:remove
   ```

>[!INFO]
>
>このコマンドは、以外の cron ジョブには影響しません。 `#~ MAGENTO START` および `#~ MAGENTO END` crontab のコメント。

## コマンドラインから cron を実行します

コマンドオプション：

```bash
bin/magento cron:run [--group="<cron group name>"]
```

ここで、 `--group` 実行する cron グループを指定します（すべてのグループに対して cron を実行する場合はこのオプションを省略します）。

インデックス作成 cron ジョブを実行するには、次のように入力します。

```bash
bin/magento cron:run --group index
```

デフォルトの cron ジョブを実行するには、以下を入力します。

```bash
bin/magento cron:run --group default
```

カスタム cron ジョブとグループを設定するには、以下を参照してください。 [カスタム cron ジョブと cron グループの設定](../cron/custom-cron.md).

>[!INFO]
>
>cron を 2 回実行する必要があります。1 回目は実行するタスクを検出し、2 回目はタスク自体を実行します。 2 回目の cron 実行は、以降に行う必要があります `scheduled_at` タスクごとの時間。

## ログ

すべて `cron` ジョブ情報はから移動しました `system.log` 別の場所に `cron.log`.
デフォルトでは、cron 情報はにあります。 `<install_directory>/var/log/cron.log`.
Cron ジョブからのすべての例外は、次のユーザーが記録します。 `\Magento\Cron\Observer\ProcessCronQueueObserver::execute`.

ログインしている他に `cron.log`:

- で失敗したジョブ `ERROR` および `MISSED` ステータスは「」に記録されます。 `<install_directory>/var/log/support_report.log`.

- を使用したジョブ `ERROR` ステータスは常に次のように記録されます `CRITICAL` 。対象： `<install_directory>/var/log/exception.log`.

- を使用したジョブ `MISSED` ステータスのログ形式 `INFO` が含まれる `<install_directory>/var/log/debug.log` ディレクトリ （開発者モードのみ）。

>[!INFO]
>
>すべての cron データも `cron_schedule` Commerce データベース内のテーブル。 この表には、次のような cron ジョブの履歴が表示されます。
>
>- ジョブ ID とコード
>- ステータス
>- 作成日
>- スケジュール日
>- 実行日
>- 完了日
>
>テーブルのレコードを表示するには、コマンドラインでCommerce データベースにログインして次のコマンドを入力します `SELECT * from cron_schedule;`.
