---
title: カスタム cron ジョブと cron グループの設定（チュートリアル）
description: この詳しい手順のチュートリアルを使用して、カスタム cron ジョブを作成します。
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '808'
ht-degree: 0%

---


# カスタム Cron ジョブの設定

このステップバイステップのチュートリアルでは、サンプルモジュールでカスタム cron ジョブと（オプションで）cron グループを作成する方法を説明します。 お持ちのモジュールを使用するか、または当社のサンプルモジュールを使用できます [`magento2-samples` リポジトリ][samples].

cron ジョブを実行すると、行が `cron_schedule` cron ジョブの名前を持つテーブル `custom_cron`.

また、Commerce アプリケーションのデフォルト以外の設定でカスタム cron ジョブを実行するために使用できる cron グループの作成方法も示します。

このチュートリアルでは、次の点を前提としています。

- Commerce アプリケーションがにインストールされている `/var/www/html/magento2`
- Commerce データベースのユーザー名とパスワードは両方とも `magento`
- すべてのアクションは、 [ファイルシステム所有者](../../installation/prerequisites/file-system/overview.md)

## 手順 1:サンプルモジュールの取得

カスタム cron ジョブを設定するには、サンプルモジュールが必要です。 以下を推奨します。 `magento-module-minimal` モジュール。

既にサンプルモジュールがある場合は、それを使用できます。この手順と次の手順をスキップし、手順 3 に進みます。cron を実行するクラスを作成します。

**サンプルモジュールを取得するには**:

1. コマースサーバーに、 [ファイルシステム所有者](../../installation/prerequisites/file-system/overview.md).
1. コマースアプリケーションのルートにないディレクトリ（ホームディレクトリなど）に変更します。
1. のクローン [`magento2-samples` リポジトリ][samples].

   ```bash
   git clone git@github.com:magento/magento2-samples.git
   ```

   コマンドがエラーで失敗した場合 `Permission denied (publickey).`を [SSH 公開鍵を GitHub.com に追加する][git-ssh].

1. サンプルコードのコピー先ディレクトリを作成します。

   ```bash
   mkdir -p /var/www/html/magento2/app/code/Magento/SampleMinimal
   ```

1. サンプルモジュールコードをコピーします。

   ```bash
   cp -r ~/magento2-samples/sample-module-minimal/* /var/www/html/magento2/app/code/Magento/SampleMinimal
   ```

1. 正しくコピーされたファイルを確認します。

   ```bash
   ls -al /var/www/html/magento2/app/code/Magento/SampleMinimal
   ```

   次の結果が表示されます。

   ```terminal
   drwxrwsr-x.   4 magento_user apache  4096 Oct 30 13:19 .
   drwxrwsr-x. 121 magento_user apache  4096 Oct 30 13:19 ..
   -rw-rw-r--.   1 magento_user apache   372 Oct 30 13:19 composer.json
   drwxrwsr-x.   2 magento_user apache  4096 Oct 30 13:19 etc
   -rw-rw-r--.   1 magento_user apache 10376 Oct 30 13:19 LICENSE_AFL.txt
   -rw-rw-r--.   1 magento_user apache 10364 Oct 30 13:19 LICENSE.txt
   -rw-rw-r--.   1 magento_user apache  1157 Oct 30 13:19 README.md
   -rw-rw-r--.   1 magento_user apache   270 Oct 30 13:19 registration.php
   drwxrwsr-x.   3 magento_user apache  4096 Oct 30 13:19 Test
   ```

1. コマースデータベースとスキーマを更新します。

   ```bash
   bin/magento setup:upgrade
   ```

1. キャッシュをクリーンアップします。

   ```bash
   bin/magento cache:clean
   ```

## 手順 2:サンプルモジュールの検証

続行する前に、サンプルモジュールが登録され、有効になっていることを確認します。

1. 次のコマンドを実行します。

   ```bash
   bin/magento module:status Magento_SampleMinimal
   ```

1. モジュールが有効になっていることを確認します。

   ```terminal
   Module is enabled
   ```

>[!TIP]
>
>出力が `Module does not exist`，レビュー [手順 1](#step-1-get-a-sample-module) 慎重に。 コードが正しいディレクトリにあることを確認します。 つづりと大文字と小文字は重要です。何かが異なる場合、モジュールは読み込まれません。 また、を実行することを忘れないでください。 `magento setup:upgrade`.

## 手順 3:cron を実行するクラスを作成します

この手順では、cron ジョブを作成するための単純なクラスを示します。 クラスは、 `cron_schedule` が正常に設定されたことを確認する表。

クラスを作成するには：

1. クラスのディレクトリを作成し、そのディレクトリに変更します。

   ```bash
   mkdir /var/www/html/magento2/app/code/Magento/SampleMinimal/Cron && cd /var/www/html/magento2/app/code/Magento/SampleMinimal/Cron
   ```

1. という名前のファイルを作成しました `Test.php` を次の内容で指定します。

   ```php
   <?php
   namespace Magento\SampleMinimal\Cron;
   
   use Psr\Log\LoggerInterface;
   
   class Test {
       protected $logger;
   
       public function __construct(LoggerInterface $logger) {
           $this->logger = $logger;
       }
   
      /**
       * Write to system.log
       *
       * @return void
       */
       public function execute() {
           $this->logger->info('Cron Works');
       }
   }
   ```

## 手順 4:作成 `crontab.xml`

この `crontab.xml` ファイルは、カスタム cron コードを実行するスケジュールを設定します。

作成 `crontab.xml` 次のように `/var/www/html/magento2/app/code/Magento/SampleMinimal/etc` ディレクトリ：

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Cron:etc/crontab.xsd">
    <group id="default">
        <job name="custom_cronjob" instance="Magento\SampleMinimal\Cron\Test" method="execute">
            <schedule>* * * * *</schedule>
        </job>
    </group>
</config>
```

前の `crontab.xml` を実行 `Magento/SampleMinimal/Cron/Test.php` 1 分に 1 回クラスを定義し、その結果、行が `cron_schedule` 表。

Cron スケジュールを管理者から設定できるようにするには、システム設定フィールドの設定パスを使用します。

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Cron:etc/crontab.xsd">
    <group id="default">
        <job name="custom_cronjob" instance="Magento\SampleMinimal\Cron\Test" method="execute">
            <config_path>system/config/path</config_path>
        </job>
    </group>
</config>
```

ここで、 `system/config/path` は、 `etc/adminhtml/system.xml` モジュールの。

## 手順 5:クリーンをコンパイルしてキャッシュ

次のコマンドでコードをコンパイルします。

```bash
bin/magento setup:di:compile
```

次のコマンドを使用してキャッシュをクリーンアップします。

```bash
bin/magento cache:clean
```

## 手順 6:cron ジョブの検証

この手順では、 `cron_schedule` データベーステーブル。

cron を検証するには：

1. コマース cron ジョブを実行します。

   ```bash
   bin/magento cron:run
   ```

1. 次を入力します。 `magento cron:run` コマンドは 2 回か 3 回。

   コマンドを初めて入力すると、ジョブがキューに入ります。その後、cron ジョブが実行されます。 コマンドを入力する必要があります _少なくとも_ 2 回。

1. SQL クエリを実行 `SELECT * from cron_schedule WHERE job_code like '%custom%'` 次のように指定します。

   1. 入力 `mysql -u magento -p`
   1. 次の場合： `mysql>` プロンプト、入力 `use magento;`
   1. 入力 `SELECT * from cron_schedule WHERE job_code like '%custom%';`

      結果は次のようになります。

      ```terminal
      +-------------+----------------+---------+----------+---------------------+---------------------+---------------------+---------------------+
      | schedule_id | job_code       | status  | messages | created_at        | scheduled_at        | executed_at         | finished_at     |
      +-------------+----------------+---------+----------+---------------------+---------------------+---------------------+---------------------+
      |        3670 | custom_cronjob | success | NULL     | 2016-11-02 09:38:03 | 2016-11-02 09:38:00 | 2016-11-02 09:39:03 | 2016-11-02 09:39:03 |
      |        3715 | custom_cronjob | success | NULL     | 2016-11-02 09:53:03 | 2016-11-02 09:53:00 | 2016-11-02 09:54:04 | 2016-11-02 09:54:04 |
      |        3758 | custom_cronjob | success | NULL     | 2016-11-02 10:09:03 | 2016-11-02 10:09:00 | 2016-11-02 10:10:03 | 2016-11-02 10:10:03 |
      |        3797 | custom_cronjob | success | NULL     | 2016-11-02 10:24:03 | 2016-11-02 10:24:00 | 2016-11-02 10:25:03 | 2016-11-02 10:25:03 |
      +-------------+----------------+---------+----------+---------------------+---------------------+---------------------+---------------------+
      ```

1. （オプション）Commerce のシステムログにメッセージが書き込まれていることを確認します。

   ```bash
   cat /var/www/html/magento2/var/log/system.log
   ```

   次のような 1 つ以上のエントリが表示されます。

   ```terminal
   [2016-11-02 22:17:03] main.INFO: Cron Works [] []
   ```

   これらのメッセージは、 `execute` メソッド `Test.php`:

   ```php
   public function execute() {
        $this->logger->info('Cron Works');
   ```

SQL コマンドとシステム・ログにエントリが含まれていない場合は、 `magento cron:run` コマンドを数回実行し、待ちます。 データベースの更新には時間がかかる場合があります。

## 手順 7（オプション）:カスタム Cron グループの設定

この手順では、カスタム cron グループをオプションで設定する方法を示します。 他の cron ジョブ（通常は 1 分に 1 回）とは異なるスケジュールでカスタム cron ジョブを実行する場合、または異なる設定で複数のカスタム cron ジョブを実行する場合は、カスタム cron グループを設定する必要があります。

カスタム cron グループを設定するには：

1. 開く `crontab.xml` をクリックします。
1. 変更 `<group id="default">` から `<group id="custom_crongroup">`
1. テキストエディタを終了します。
1. 作成 `/var/www/html/magento2/app/code/Magento/SampleMinimal/etc/cron_groups.xml` を次の内容で指定します。

   ```xml
   <?xml version="1.0"?>
   <config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Cron:etc/cron_groups.xsd">
       <group id="custom_crongroup">
           <schedule_generate_every>1</schedule_generate_every>
           <schedule_ahead_for>4</schedule_ahead_for>
           <schedule_lifetime>2</schedule_lifetime>
           <history_cleanup_every>10</history_cleanup_every>
           <history_success_lifetime>60</history_success_lifetime>
           <history_failure_lifetime>600</history_failure_lifetime>
           <use_separate_process>1</use_separate_process>
       </group>
   </config>
   ```

オプションの意味については、 [Cron リファレンスのカスタマイズ](custom-cron-reference.md).

## 手順 8:カスタム Cron グループを検証します。

この _オプション_ 手順には、管理者を使用してカスタム cron グループを検証する方法が示されています。

カスタム Cron グループを検証するには：

1. カスタムグループに対して Commerce cron ジョブを実行します。

   ```bash
   php /var/www/html/magento2/bin/magento cron:run --group="custom_crongroup"
   ```

   コマンドを少なくとも 2 回実行します。

1. キャッシュをクリーンアップします。

   ```bash
   php /var/www/html/magento2/bin/magento cache:clean
   ```

1. 管理者として管理者にログインします。
1. クリック **ストア** > **設定** > **設定** > **詳細** > **システム**.
1. 右側のウィンドウで、を展開します。 **Cron**.

   cron グループは次のように表示されます。

   ![カスタム Cron グループ](../../assets/configuration/cron-group.png)

<!-- link definitions -->

[git-ssh]: https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account
[samples]: https://github.com/magento/magento2-samples
