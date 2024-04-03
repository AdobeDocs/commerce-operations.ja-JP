---
title: インストールガイド
description: このガイドを使用して、をインストールします。 [!DNL Site-Wide Analysis Tool] （Web サイト用）
exl-id: ba36dc74-806d-49c5-b4d1-ba53ed4076fb
feature: Configuration, Install
source-git-commit: f72316b3baee52ef6b000afa281a2e146f560ead
workflow-type: tm+mt
source-wordcount: '1136'
ht-degree: 0%

---

# インストールガイド

>[!IMPORTANT]
>
>2024 年 4 月 23 日、 [!DNL Site-Wide Analysis Tool] は、すべてのAdobe Commerceオンプレミスユーザーに対して廃止されます。

The [!DNL Site-Wide Analysis Tool] では、クラウドインフラストラクチャのインストール時にAdobe Commerceのセキュリティと操作性を確保するための24/7のリアルタイムパフォーマンス監視、レポートおよび推奨事項を提供しています。 また、利用可能なパッチとインストール済みのパッチ、サードパーティの拡張機能、Adobe Commerceのインストールに関する詳細情報も提供されます。

>[!INFO]
>
>学ぶ [有効にする方法](../site-wide-analysis-tool/access.md) の [!DNL Site-Wide Analysis Tool] レポートを生成します。

Adobe Commerceをオンプレミスでインストールしている場合は、このツールを使用するために、インフラストラクチャにエージェントをインストールします。 クラウドインフラストラクチャプロジェクト上のAdobe Commerceにエージェントをインストールする必要はありません。

## エージェント

The [!DNL Site-Wide Analysis Tool] エージェントを使用すると、 [!DNL Site-Wide Analysis Tool] Adobe Commerceのオンプレミスインストールの場合。

The [!DNL Site-Wide Analysis Tool] エージェントは、アプリケーションとビジネスデータを収集し、分析し、インストールの状態に関する追加のインサイトを提供して、顧客体験を向上させます。 アプリケーションを監視し、パフォーマンス、セキュリティ、可用性、アプリケーションの問題を特定します。

エージェントのインストールには、次の手順が必要です。

1. システム要件を確認します。

1. での API キーの設定 [!UICONTROL Commerce Services Connector] 拡張子。

1. エージェントをインストールします。

1. エージェントを実行します。

>[!INFO]
>
>エージェントは、複数ノードのAdobe Commerceインストールをサポートします。 各ノードにエージェントをインストールして設定します。

## 必要システム構成

オンプレミスのインフラストラクチャは、エージェントをインストールする前に、次の要件を満たす必要があります。

- オペレーティングシステム

   - [!DNL Linux x86-64] 次のような配分： [!DNL Red Hat® Enterprise Linux (RHEL)], [!DNL CentOS], [!DNL Ubuntu], [!DNL Debian]、類似

  >[!IMPORTANT]
  >
  >Adobe Commerceはではサポートされていません [!DNL Microsoft Windows] または [!DNL macOS].

- Adobe Commerce 2.4.5-p1 以降（Service Connector の依存関係による）

- [!DNL Commerce Services Connector extension]

- PHP CLI

- Bash/shell ユーティリティ

   - `php`

   - `wget`

   - `awk`

   - `nice`

   - `grep`

   - `openssl`

## [!DNL Commerce Services Connector]

エージェントには [[!DNL Commerce Services Connector]](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html) お使いのシステムにインストールする拡張機能および [設定済み](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html) と API キーを組み合わせました。 拡張機能がインストールされていることを確認するには、次のコマンドを実行します。

```bash
bin/magento module:status Magento_ServicesId
```

拡張機能をインストールし、別のサービスの既存の API キーを使用して設定した場合は、 **API キーを再生成する必要があります** エージェントのAdobe Commerce Admin で更新します。

1. Web サイトをに配置する [メンテナンスモード](../../installation/tutorials/maintenance-mode.md).

1. ログイン [account.magento.com](https://account.magento.com/customer/account/login?_ga=2.164207871.117144580.1649172612-1623400270.1640858671).

   >[!NOTE]
   >
   > アカウントへのアクセスに問題がある場合は、 [Adobe Commerceサポートまたはクラウドアカウントにログインできません](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/unable-to-log-in-to-support-or-cloud-project.html) 」を参照してください。

1. クリック **[!UICONTROL API Portal]**.

1. クリック **[!UICONTROL Delete]** をクリックします。

1. [設定](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html) 新しい API キー。

>[!IMPORTANT]
>
> API ポータルで新しいキーを生成する場合は、 [!DNL Admin configuration]. 新しいキーを生成し、 [!DNL Admin]を使用した場合、SaaS 拡張機能は機能しなくなり、貴重なデータが失われます。

拡張機能がインストールされていない場合は、次の手順に従ってインストールします。

1. 拡張機能を `composer.json` ファイルを作成し、インストールします。

   ```bash
   composer require magento/services-id
   ```

1. 拡張機能を有効にします。

   ```bash
   bin/magento module:enable Magento_ServicesId
   ```

1. データベーススキーマを更新します。

   ```bash
   bin/magento setup:upgrade
   ```

1. キャッシュをクリアします。

   ```bash
   bin/magento cache:clean
   ```

1. [API キーの設定](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html) 拡張機能をシステムに接続する場合。

## エージェントのインストール

以下を作成しました： [シェルスクリプト](https://github.com/magento-swat/install-agent-helpers/blob/main/install.sh) インストールを簡単にする。 シェルスクリプトを使用することをお勧めしますが、次の手順に従うことができます。 [手動設置](#manual) メソッドを使用します（必要な場合）。

>[!INFO]
>
>エージェントのインストール後は、新しいリリースが利用可能になると、自己更新が行われます。

### スクリプト

1. シェルスクリプトをダウンロードして実行します。

   ```bash
   bash -c "$(wget -qO - https://raw.githubusercontent.com/magento-swat/install-agent-helpers/main/install.sh)"
   ```

   >[!TIP]
   >
   >ルートのAdobe Commerceプロジェクトディレクトリの外にエージェントをインストールすることをお勧めします。

1. インストールを確認します。

   ```bash
   ./scheduler -v
   ```

   ```bash
   Version: 1.0.1
   Success exit.
   ```

1. エージェントをダウンロードしてインストールした後、 [実行するように設定します](#run-the-agent) 次のいずれかの方法を使用します。

   - [サービス](#service) （ルートアクセス権を持っている場合に推奨）

   - [Cron](#cron)

### 手動 {#manual}

以下を使用しない場合は、 [シェルスクリプト](https://github.com/magento-swat/install-agent-helpers/blob/main/install.sh) エージェントをインストールするには、次の手順に従って手動でインストールする必要があります。

1. エージェントをダウンロードするディレクトリを作成します。

   >[!TIP]
   >
   >ルートのAdobe Commerceプロジェクトディレクトリの外にエージェントをインストールすることをお勧めします。

1. バイナリファイルをダウンロードし、解凍します。

   >[!INFO]
   >
   >次の手順で [!DNL Site-Wide Analysis Tool]の場合、まずAdobe Commerce Admin からダッシュボードにアクセスする際に表示される利用条件を読み、それに同意する必要があります。

   の **AMD64** アーキテクチャ：

   1. ランチャーアーカイブをダウンロードします。

      ```bash
      curl -O https://updater.supportinsights.adobe.com/launcher/launcher.linux-amd64.tar.gz
      ```

   1. ランチャーアーカイブを解凍します。

      ```bash
      tar -xf launcher.linux-amd64.tar.gz
      ```

   の **ARM64** アーキテクチャ：

   1. ランチャーアーカイブをダウンロードします。

      ```bash
      curl -O https://updater.supportinsights.adobe.com/launcher/launcher.linux-arm64.tar.gz
      ```

   1. ランチャーアーカイブを解凍します。

      ```bash
      tar -xf launcher.linux-arm64.tar.gz
      ```

1. *（オプション）* チェックサムファイルの署名を検証します。

   ```bash
   echo -n "LS0tLS1CRUdJTiBQVUJMSUMgS0VZLS0tLS0KTUlJQ0lqQU5CZ2txaGtpRzl3MEJBUUVGQUFPQ0FnOEFNSUlDQ2dLQ0FnRUE0M2FBTk1WRXR3eEZBdTd4TE91dQpacG5FTk9pV3Y2aXpLS29HendGRitMTzZXNEpOR3lRS1Jha0MxTXRsU283VnFPWnhUbHZSSFhQZWt6TG5vSHVHCmdmNEZKa3RPUEE2S3d6cjF4WFZ3RVg4MEFYU1JNYTFadzdyOThhenh0ZHdURVh3bU9GUXdDcjYramFOM3ErbUoKbkRlUWYzMThsclk0NVJxWHV1R294QzBhbWVoakRnTGxJUSs1d1kxR1NtRGRiaDFJOWZqMENVNkNzaFpsOXFtdgorelhjWGh4dlhmTUU4MUZsVUN1elRydHJFb1Bsc3dtVHN3ODNVY1lGNTFUak8zWWVlRno3RFRhRUhMUVVhUlBKClJtVzdxWE9kTGdRdGxIV0t3V2ppMFlrM0d0Ylc3NVBMQ2pGdEQzNytkVDFpTEtzYjFyR0VUYm42V3I0Nno4Z24KY1Q4cVFhS3pYRThoWjJPSDhSWjN1aFVpRHhZQUszdmdsYXJSdUFacmVYMVE2ZHdwYW9ZcERKa29XOXNjNXlkWApBTkJsYnBjVXhiYkpaWThLS0lRSURnTFdOckw3SVNxK2FnYlRXektFZEl0Ni9EZm1YUnJlUmlMbDlQMldvOFRyCnFxaHNHRlZoRHZlMFN6MjYyOU55amgwelloSmRUWXRpdldxbGl6VTdWbXBob1NrVnNqTGtwQXBiUUNtVm9vNkgKakJmdU1sY1JPeWI4TXJCMXZTNDJRU1MrNktkMytwR3JyVnh0akNWaWwyekhSSTRMRGwrVzUwR1B6LzFkeEw2TgprZktZWjVhNUdCZm00aUNlaWVNa3lBT2lKTkxNa1cvcTdwM200ejdUQjJnbWtldm1aU3Z5MnVMNGJLYlRoYXRlCm9sdlpFd253WWRxaktkcVkrOVM1UlNVQ0F3RUFBUT09Ci0tLS0tRU5EIFBVQkxJQyBLRVktLS0tLQ==" | base64 -d > release.pub
   ```

   ```bash
   openssl dgst -sha256 -verify release.pub -signature launcher.sha256 launcher.checksum
   ```

1. *（オプション）* チェックサムを検証します。

   ```bash
   shasum -a 512 -c launcher.checksum
   ```

1. を作成します。 `config.yaml` ファイルに次の内容を含めます。

   ```yaml
   project:
     appname: "Acme Inc" # Company or site name that you provided when installing the agent
   application:
     phppath: php # Path to your PHP CLI interpreter (usually /usr/bin/php)
     magentopath: /var/www/html/example.com # Root directory where your Adobe Commerce application is installed (usually /var/www/html)
     checkregistrypath: /path/to/swat-agent/tmp # Temporary directory for the agent (usually /usr/local/swat-agent/tmp)
     issandbox: false # Enabling sandbox mode to use the agent on staging environment (true or false)
     database:
       user: your-adobe-commerce-db-username # Database user for your Adobe Commerce installation
       password: your-password # Database password for the specified user for your Adobe Commerce installation
       host: 127.0.0.1 # Database host for your Adobe Commerce installation
       dbname: your-adobe-commerce-db-name # Database name for your Adobe Commerce installation
       port: 3306 # Database port for your Adobe Commerce installation (usually 3306)
       tableprefix: # Table Prefix for your Adobe Commerce installation (default value: empty)
    enableautoupgrade: true # Enables automatic upgrade (restart required after an upgrade; agent does not check for upgrades if the option is disabled; true or false)
    runchecksonstart: true # Collect data on the first run (Usually 1)
    loglevel: error # Determines what events are logged based on severity (usually error)
   ```

1. インストールを確認します。

   ```bash
   scheduler -v
   ```

   ```bash
   Version: 1.0.1
   Success exit.
   ```

1. エージェントをダウンロードしてインストールした後、次の操作を行う必要があります。 [実行するように設定します](#run-the-agent) 次のいずれかの方法を使用します。

   - [サービス](#service) （ルートアクセス権を持っている場合に推奨）

   - [Cron](#cron)

## エージェントの実行 {#run-the-agent}

エージェントをサービスとして実行するように設定することをお勧めします。 インフラストラクチャへのアクセスが制限されていて、ルート権限がない場合は、 [cron](#cron) 代わりに、

### サービス {#service}

1. systemd ユニットファイルの作成 `(/etc/systemd/system/scheduler.service)` を次の設定に置き換えます ( `<filesystemowner>` エージェントとAdobe Commerceソフトウェアがインストールされているディレクトリを所有する UNIX®ユーザー ) エージェントをルートユーザーとしてダウンロードした場合は、ディレクトリとネストされたファイルの所有者を変更します。

   ```config
   [Unit]
   Wants=network.target
   After=network.target
   
   [Service]
   Type=simple
   User=<filesystemowner>
   ExecStart=/path/to/agent/scheduler
   Restart=always
   RestartSec=3
   
   [Install]
   WantedBy=multi-user.target
   ```

1. サービスを起動します。

   ```bash
   systemctl daemon-reload
   ```

   ```bash
   systemctl start scheduler
   ```

   ```bash
   systemctl enable scheduler
   ```

1. サービスが起動し、実行中であることを検証します。

   ```bash
   journalctl -u scheduler | grep "Application is going to update" | tail -1 && echo "Agent is successfully installed"
   ```

### Cron {#cron}

root 権限がない場合や、root としてサービスを設定する権限がない場合は、cron を代わりに使用できます。

Cron スケジュールを更新します。

```bash
( crontab -l ; echo "* * * * * flock -n /tmp/swat-agent.lockfile -c '/path/to/agent/scheduler' >> /path/to/agent/errors.log 2>&1" ) | sort - | uniq - | crontab -
```

## アンインストール

次のコマンドを実行して、システムからサービスをアンインストールし、生成されたすべてのファイルを削除します。

1. スケジューラーを停止します。

   ```bash
   systemctl stop scheduler
   ```

1. スケジューラーを無効にします。

   ```bash
   systemctl disable scheduler
   ```

1. スケジューラーサービスの `systemd` 単位ファイル。

   ```bash
   rm /etc/systemd/system/scheduler.service
   ```

1. をリロードします。 `systemd` マネージャー設定。

   ```bash
   systemctl daemon-reload
   ```

1. いずれかをリセット `systemd` の単位を失敗状態から取得します。

   ```bash
   systemctl reset-failed
   ```

1. スケジューラーサービスディレクトリを削除します。

   ```bash
   rm -rf <CHECK_REGISTRY_PATH> #see SWAT_AGENT_APPLICATION_CHECK_REGISTRY_PATH in /etc/systemd/system/scheduler.service
   ```

1. スケジューラーバイナリファイルを削除します。

   ```bash
   rm /usr/local/bin/scheduler
   ```

代わりに cron を使用して実行するようにエージェントを設定した場合は、次の手順に従います。

1. crontab リストからエージェントを削除します。

   ```bash
   crontab -e
   ```

1. 実行中のジョブを停止します。

   ```bash
   ps aux | grep scheduler
   ```

1. エージェントをインストールしたディレクトリを削除します。

   ```bash
   rm -rf swat-agent
   ```

## トラブルシューティング

### アクセスキーが正しく解析されません

アクセスキーが正しく解析されない場合、次のエラーが表示される場合があります。

```terminal
ERRO[2022-10-10 00:01:41] Error while refreshing token: error while getting jwt from magento: invalid character 'M' looking for beginning of value
FATA[2022-12-10 20:38:44] bad http status from https://updater.supportinsights.adobe.com/linux-amd64.json: 403 Forbidden
```

このエラーを解決するには、次の手順を試してください。

1. 以下を実行します。 [スクリプトインストール](#scripted)、出力を保存し、エラーの出力を確認します。
1. 生成された `config.yaml` ファイルを開き、コマースインスタンスと PHP へのパスが正しいことを確認します。
1. スケジューラーを実行しているユーザーが [ファイルシステム所有者](../../installation/prerequisites/file-system/overview.md) UNIX グループまたははファイルシステムの所有者と同じユーザーです。
1. 次を確認します。 [Commerce Services コネクタ](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html) キーが正しくインストールされていることを確認し、拡張機能をシステムに接続するためにキーを更新してみてください。
1. [アンインストール](#uninstall) キーを更新し、を使用して再インストールした後のエージェント [インストールスクリプト](#scripted).
1. スケジューラーを実行し、同じエラーが引き続き表示されるかどうかを確認します。
1. それでも同じエラーが発生する場合は、 `config.yaml` をクリックして、サポートチケットをデバッグし開きます。

### *SIGFAULT* エラー

次のような場合に、 *SIGFAULT* バイナリを実行中にエラーが発生した場合は、Adobe Commerceおよびエージェントファイルのファイル所有者として、これを実行しない可能性があります。
解決するには、エージェントディレクトリ内の、Adobe Commerceファイルが持つファイル所有者と同じユーザーを持つすべてのファイルと、そのユーザーの下でバイナリを実行する必要があるかどうかを確認してください。
以下を使用すると、 `chown` コマンドを使用して、ファイルの所有者を変更し、適切なユーザーに切り替えます。
デーモン化メカニズム（Cron または System.d）が適切なユーザーでプロセスを実行していることを確認します。

>[!INFO]
>
>詳しくは、 [アクセス方法 [!DNL Site-Wide Analysis Tool] レポートを生成します。](../site-wide-analysis-tool/access.md).
