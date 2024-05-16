---
title: カスタム cron ジョブと cron グループの設定（チュートリアル）
description: このステップバイステップのチュートリアルを使用して、カスタム cron ジョブを作成します。
exl-id: d8efcafc-3ae1-4c2d-a8ad-4a806fb48932
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '809'
ht-degree: 0%

---

# カスタム cron ジョブの設定

このステップバイステップのチュートリアルでは、サンプルモジュールでカスタム cron ジョブとオプションで cron グループを作成する方法を説明します。 既に持っているモジュールを使用するか、以下のサンプルモジュールを使用できます。 [`magento2-samples` リポジトリ][samples].

cron ジョブを実行すると、に行が追加されます。 `cron_schedule` cron ジョブの名前を含むテーブル。 `custom_cron`.

また、オプションで cron グループを作成する方法も示します。このグループを使用して、Commerce アプリケーションのデフォルト以外の設定でカスタム cron ジョブを実行できます。

このチュートリアルでは、以下を想定しています。

- Commerce アプリケーションのインストール先 `/var/www/html/magento2`
- Commerce データベースのユーザー名とパスワードの両方を指定します `magento`
- すべてのアクションを次のように実行します [ファイルシステム所有者](../../installation/prerequisites/file-system/overview.md)

## 手順 1：サンプルモジュールの取得

カスタム cron ジョブを設定するには、サンプルモジュールが必要です。 以下をお勧めします。 `magento-module-minimal` モジュール。

既にサンプルモジュールがある場合は、それを使用できます。この手順と次の手順をスキップし、手順 3:cron を実行するクラスの作成に進みます。

**サンプルモジュールを取得する方法**:

1. Commerce サーバーにとしてログインするか、に切り替えます [ファイルシステム所有者](../../installation/prerequisites/file-system/overview.md).
1. をCommerce アプリケーションのルートにないディレクトリ（ホームディレクトリなど）に移動します。
1. のクローン [`magento2-samples` リポジトリ][samples].

   ```bash
   git clone git@github.com:magento/magento2-samples.git
   ```

   コマンドがエラーで失敗した場合 `Permission denied (publickey).`は、次の操作が必要です [ssh 公開鍵をGitHub.comに追加します][git-ssh].

1. サンプルコードのコピー先となるディレクトリを作成します。

   ```bash
   mkdir -p /var/www/html/magento2/app/code/Magento/SampleMinimal
   ```

1. 次のサンプルモジュールコードをコピーします。

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

1. Commerce データベースとスキーマを更新します。

   ```bash
   bin/magento setup:upgrade
   ```

1. キャッシュのクリーンアップ：

   ```bash
   bin/magento cache:clean
   ```

## 手順 2：サンプルモジュールを確認する

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
>出力に `Module does not exist`, レビュー [手順 1](#step-1-get-a-sample-module) 慎重に。 コードが正しいディレクトリにあることを確認します。 スペルと大文字と小文字の区別は重要です。何か異なる場合、モジュールは読み込まれません。 また、実行することを忘れないでください `magento setup:upgrade`.

## 手順 3:cron を実行するクラスの作成

この手順では、cron ジョブを作成するための単純なクラスを示します。 クラスは、に行を書き込むだけです。 `cron_schedule` 正常に設定されていることを確認するテーブル。

クラスを作成するには：

1. クラスのディレクトリを作成し、そのディレクトリに変更します。

   ```bash
   mkdir /var/www/html/magento2/app/code/Magento/SampleMinimal/Cron && cd /var/www/html/magento2/app/code/Magento/SampleMinimal/Cron
   ```

1. という名前のファイルを作成しました。 `Test.php` このディレクトリには、次の内容が含まれています。

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

## 手順 4：作成 `crontab.xml`

この `crontab.xml` ファイルは、カスタム cron コードを実行するスケジュールを設定します。

作成 `crontab.xml` 次に示すとおり `/var/www/html/magento2/app/code/Magento/SampleMinimal/etc` ディレクトリ：

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

前項 `crontab.xml` を実行します `Magento/SampleMinimal/Cron/Test.php` 1 分に 1 回のクラス。この結果、行がに追加されます。 `cron_schedule` テーブル。

管理者が cron スケジュールを設定できるようにするには、システム設定フィールドの設定パスを使用します。

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

ここで、 `system/config/path` は、で定義されたシステム設定パスです。 `etc/adminhtml/system.xml` （モジュールの）。

## 手順 5：コンパイルとキャッシュのクリーンアップ

次のコマンドを使用してコードをコンパイルします。

```bash
bin/magento setup:di:compile
```

次のコマンドを使用してキャッシュをクリーンアップします。

```bash
bin/magento cache:clean
```

## 手順 6:cron ジョブの検証

この手順では、で SQL クエリを使用してカスタム cron ジョブを正常に検証する方法を示します `cron_schedule` データベーステーブル。

cron を検証するには：

1. Commerce cron ジョブを実行します。

   ```bash
   bin/magento cron:run
   ```

1. を入力 `magento cron:run` 2、3 回命令してください。

   コマンドを初めて入力すると、ジョブがキューに入れられ、その後、cron ジョブが実行されます。 コマンドを入力する必要があります _少なくとも_ 2 回。

1. SQL クエリを実行 `SELECT * from cron_schedule WHERE job_code like '%custom%'` 次のように設定します。

   1. Enter `mysql -u magento -p`
   1. 時刻 `mysql>` プロンプト，enter `use magento;`
   1. Enter `SELECT * from cron_schedule WHERE job_code like '%custom%';`

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

1. （オプション）メッセージがCommerce システムログに書き込まれていることを確認します。

   ```bash
   cat /var/www/html/magento2/var/log/system.log
   ```

   次のようなエントリが 1 つ以上表示されます。

   ```terminal
   [2016-11-02 22:17:03] main.INFO: Cron Works [] []
   ```

   これらのメッセージは、 `execute` メソッド： `Test.php`:

   ```php
   public function execute() {
        $this->logger->info('Cron Works');
   ```

SQL コマンドとシステム ログにエントリが含まれていない場合は、 `magento cron:run` もう数回命令して待ってください。 データベースの更新には、ある程度の時間がかかる場合があります。

## 手順 7 （オプション）：カスタム cron グループの設定

この手順では、カスタム cron グループをオプションで設定する方法を示します。 カスタム cron ジョブを他の cron ジョブとは異なるスケジュール（通常は 1 分に 1 回）で実行する場合や、複数のカスタム cron ジョブを異なる設定で実行する場合は、カスタム cron グループを設定する必要があります。

カスタム cron グループを設定するには：

1. 開く `crontab.xml` テキストエディター。
1. 変更 `<group id="default">` 対象： `<group id="custom_crongroup">`
1. テキストエディターを終了します。
1. 作成 `/var/www/html/magento2/app/code/Magento/SampleMinimal/etc/cron_groups.xml` 次の内容を含みます。

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

オプションの意味については、を参照してください。 [Cron リファレンスのカスタマイズ](custom-cron-reference.md).

## 手順 8：カスタム cron グループの検証

この _optional_ 管理者を使用してカスタム cron グループを検証する手順を示します。

カスタム cron グループを検証するには：

1. カスタムグループに対してCommerce cron ジョブを実行します。

   ```bash
   php /var/www/html/magento2/bin/magento cron:run --group="custom_crongroup"
   ```

   コマンドを少なくとも 2 回実行します。

1. キャッシュのクリーンアップ：

   ```bash
   php /var/www/html/magento2/bin/magento cache:clean
   ```

1. 管理者として管理者にログインします。
1. クリック **ストア** > **設定** > **設定** > **詳細** > **システム**.
1. 右側のパネルで、を展開します **Cron**.

   cron グループは次のように表示されます。

   ![カスタム cron グループ](../../assets/configuration/cron-group.png)

<!-- link definitions -->

[git-ssh]: https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account
[samples]: https://github.com/magento/magento2-samples
