---
title: cron ジョブの設定と実行
description: cron ジョブの管理方法を説明します。
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '766'
ht-degree: 0%

---


# cron ジョブの設定

{{file-system-owner}}

一部のコマース機能には、少なくとも 1 つの cron ジョブが必要です。このジョブは、将来アクティビティをスケジュールします。 これらのアクティビティの一部を次に示します。

- カタログ価格ルール
- ニュースレター
- Googleサイトマップの生成
- 顧客アラート/通知（製品価格の変更、製品の在庫再追加）
- インデックス再作成
- 非公開販売 (Adobe Commerceのみ )
- 通貨レートの自動更新
- すべてのコマース電子メール（注文確認およびトランザクションを含む）

>[!WARNING]
>
>今後は実行できません `dev/tools/cron.sh` スクリプトが削除されたので、

>[!INFO]
>
>コマースは、インデックス作成を含む多くの重要なシステム機能に対して、適切な cron ジョブ設定に依存します。 正しく設定されていない場合、Commerce は期待どおりに機能しません。

UNIX システムは、 _crontab_:cron デーモンに対する命令を含むファイルで、デーモンに対して「この日にこのコマンドを実行する」ように指示します。 各ユーザには独自の crontab があり、任意の crontab 内のコマンドは、その crontab を所有するユーザとして実行されます。

Web ブラウザーで cron を実行するには、 [ブラウザーで実行する cron.php を保護します。](../security/secure-cron-php.md).

## Commerce crontab を作成または削除します

この節では、コマースの crontab（Commerce cron ジョブの設定）を作成または削除する方法について説明します。

この _crontab_ は、cron ジョブの実行に使用される設定です。

Commerce アプリケーションは、異なる設定で実行できる cron タスクを使用します。 PHP のコマンドライン設定は、インデクサの再インデックス、電子メールの生成、サイトマップの生成などを行う一般的な cron ジョブを制御します。

>[!WARNING]
>
>- インストールとアップグレードの際の問題を回避するため、PHP のコマンドライン設定と PHP Web サーバーのプラグイン設定の両方に同じ PHP 設定を適用することを強くお勧めします。 詳しくは、 [必要な PHP 設定](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/php-settings.html).
>- マルチノードシステムでは、crontab は 1 つのノードでのみ実行できます。 これは、パフォーマンスや拡張性に関する理由から複数の Web ノードを設定した場合にのみ当てはまります。


### Commerce crontab を作成します。

バージョン 2.2 以降、Commerce は crontab を作成します。 コマースの crontab を、コマースファイルシステムの所有者用に設定された crontab に追加します。 つまり、他の拡張機能やアプリケーション用に crontabs を既に設定している場合は、Commerce crontab を追加します。

Commerce crontab は内部にあります `#~ MAGENTO START` および `#~ MAGENTO END` crontab でのコメント。

Commerce crontab を作成するには：

1. にログインするか、に切り替えます。 [ファイルシステム所有者](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).
1. Commerce のインストールディレクトリに移動します。
1. 次のコマンドを入力します。

   ```bash
   bin/magento cron:install [--force]
   ```

用途 `--force` 既存の crontab を書き換える。

>[!INFO]
>
>- `magento cron:install` 内の既存の crontab を書き換えない `#~ MAGENTO START` および `#~ MAGENTO END` crontab でのコメント。
>- `magento cron:install --force` は、Commerce コメント以外の cron ジョブには影響しません。


crontab を表示するには、次のコマンドをファイルシステムの所有者として入力します。

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
>この `update/cron.php` ファイルが Commerce 2.4.0 で削除されました。このファイルがインストールに存在する場合は、安全に削除できます。
>
>への参照 `update/cron.php` および `bin/magento setup:cron:run` また、crontab から削除する必要があります。

### Commerce crontab を削除します。

Commerce アプリケーションをアンインストールする前に、Commerce の crontab を削除する必要があります。

Commerce crontab を削除するには：

1. としてログインするか、に切り替えます。 [ファイルシステム所有者](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).
1. Commerce のインストールディレクトリに移動します。
1. 次のコマンドを入力します。

   ```bash
   bin/magento cron:remove
   ```

>[!INFO]
>
>このコマンドは、 `#~ MAGENTO START` および `#~ MAGENTO END` crontab でのコメント。

## コマンドラインから cron を実行します。

コマンドオプション：

```bash
bin/magento cron:run [--group="<cron group name>"]
```

場所 `--group` 実行する cron グループを指定します（すべてのグループに対して cron を実行する場合は、このオプションを省略します）。

cron ジョブのインデックス作成を実行するには、次のように入力します。

```bash
bin/magento cron:run --group index
```

デフォルトの cron ジョブを実行するには、次のように入力します。

```bash
bin/magento cron:run --group default
```

カスタム Cron ジョブとグループを設定するには、 [カスタム cron ジョブと cron グループの設定](../cron/custom-cron.md).

>[!INFO]
>
>cron を 2 回実行する必要があります。実行するタスクを初めて検出し、2 回目は、タスク自体を実行する場合です。 2 回目の cron 実行は、 `scheduled_at` 各タスクの時間

## ログ

すべて `cron` ジョブ情報は次の場所から移動されました： `system.log` 別の場所に `cron.log`.
デフォルトでは、cron 情報は次の場所にあります。 `<install_directory>/var/log/cron.log`.
cron ジョブのすべての例外は、次の方法でログに記録されます。 `\Magento\Cron\Observer\ProcessCronQueueObserver::execute`.

ログインに加えて `cron.log`:

- 次の条件で失敗したジョブ `ERROR` および `MISSED` ステータスは `<install_directory>/var/log/support_report.log`.

- と `ERROR` ステータスは常に次のように記録されます `CRITICAL` in `<install_directory>/var/log/exception.log`.

- とのジョブ `MISSED` のステータスは次のように記録されます。 `INFO` 内 `<install_directory>/var/log/debug.log` ディレクトリ（開発者モードのみ）。

>[!INFO]
>
>すべての cron データも `cron_schedule` Commerce データベースのテーブル。 この表は、次のような cron ジョブの履歴を示しています。
>
>- ジョブ ID とコード
>- ステータス
>- 作成日
>- 予定日
>- 実行日
>- 終了日
>
>テーブル内のレコードを確認するには、コマンドラインで Commerce データベースにログインし、と入力します。 `SELECT * from cron_schedule;`.
