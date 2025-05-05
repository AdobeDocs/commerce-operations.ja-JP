---
title: インストールガイド
description: 'このガイドを使用して、Web サイトをインストール [!DNL Site-Wide Analysis Tool] '
exl-id: ba36dc74-806d-49c5-b4d1-ba53ed4076fb
feature: Configuration, Install
source-git-commit: 16feb8ec7ecc88a6ef03a769d45b1a3a2fe88d97
workflow-type: tm+mt
source-wordcount: '1136'
ht-degree: 0%

---

# インストールガイド

>[!IMPORTANT]
>
>2024 年 4 月 23 日より、 [!DNL Site-Wide Analysis Tool] はすべての Adobe Systems Commerce オンプレミスのお客様に対して廃止されます。

この [!DNL Site-Wide Analysis Tool] は、クラウドインフラストラクチャーインストールでのAdobe Systemsコマースのセキュリティと操作性を確保するための24時間年中無休のリアルタイムパフォーマンス監視、レポート、および推奨事項を提供します。 また、使用可能なパッチとインストールされているパッチ、サードパーティ拡張機能、および Adobe Systems Commerce のインストールに関する詳細情報も提供します。

>[!INFO]
>
>[!DNL Site-Wide Analysis Tool]を有効にしてレポートを生成する[方法について](../site-wide-analysis-tool/access.md)説明します。

Adobe Systems Commerce のオンプレミスインストールがある場合は、ツールを使用するためにインフラストラクチャにエージェントをインストールします。 クラウドインフラストラクチャープロジェクトの Adobe Systems Commerce にエージェントをインストールする必要はありません。

## エージェント

[!DNL Site-Wide Analysis Tool] エージェントを使用すると、Adobe Systems Commerce のオンプレミスインストールに[!DNL Site-Wide Analysis Tool]を使用できます。

[!DNL Site-Wide Analysis Tool] Agent は、アプリケーションデータとビジネス データを収集して分析し、インストールの正常性に関する追加の分析情報を提供して、エクスペリエンスを向上させることができます。アプリケーションを監視し、パフォーマンス、セキュリティ、可用性、アプリケーションの問題を特定するのに役立ちます。

エージェントをインストールするには、次の手順を実行する必要があります。

1. システム要件を確認します。

1. [!UICONTROL Commerce Services Connector] 拡張機能で API キーを設定します。

1. エージェントをインストールします。

1. エージェントを実行します。

>[!INFO]
>
>エージェントは、マルチノード Adobe Systems Commerce のインストールをサポートします。 各ノードにエージェントをインストールして設定します。

## 必要システム構成

エージェントをインストールする前に、オンプレミスインフラストラクチャが次の要件を満たしている必要があります。

- オペレーティングシステム

   - [!DNL Red Hat® Enterprise Linux (RHEL)]、[!DNL CentOS]、[!DNL Ubuntu]、[!DNL Debian] などの [!DNL Linux x86-64] ディストリビューション

  >[!IMPORTANT]
  >
  >Adobe Commerceは [!DNL Microsoft Windows] または [!DNL macOS] ではサポートされていません。

- Adobe Commerce 2.4.5-p1 以降（サービスコネクタの依存関係による）

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

エージェントを使用するには、[[!DNL Commerce Services Connector]](https://experienceleague.adobe.com/docs/commerce/user-guides/integration-services/saas.html?lang=ja) 拡張機能がシステムにインストールされ、API キーを使用して [ 設定 ](https://experienceleague.adobe.com/docs/commerce/user-guides/integration-services/saas.html?lang=ja) されている必要があります。 拡張機能がインストールされていることを確認するには、次のコマンドを実行します。

```bash
bin/magento module:status Magento_ServicesId
```

拡張機能をインストールし、別のサービス用の既存の API キーを使用して設定した場合は、**API キーを再生成し** エージェントのAdobe Commerce管理者で更新する必要があります。

1. Web サイトを [メンテナンスモード](../../installation/tutorials/maintenance-mode.md)にします。

1. [account.magento.com](https://account.magento.com/customer/account/login?_ga=2.164207871.117144580.1649172612-1623400270.1640858671)にログインします。

   >[!NOTE]
   >
   > アカウントにアクセスできない場合は、トラブルシューティングのヘルプについて [Adobe Systems Commerce サポートまたはクラウドアカウントにログインできない](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/unable-to-log-in-to-support-or-cloud-project.html?lang=ja) を参照してください。

1. [ **[!UICONTROL API Portal]**] をクリックします。

1. 既存の API キーの横にある **[!UICONTROL Delete]** をクリックします。

1. [設定](https://experienceleague.adobe.com/docs/commerce/user-guides/integration-services/saas.html?lang=ja) 新しい API キー。

>[!IMPORTANT]
>
> API ポータルで新しいキーを生成した場合は、すぐに [!DNL Admin configuration]で API キーを更新してください。 新しいキーを生成し、 [!DNL Admin]内のキーを更新しないと、SaaS拡張機能は機能しなくなり、貴重なデータが失われます。

拡張機能がインストールされていない場合は、次の手順を使用してインストールします。

1. 拡張機能を `composer.json` ファイルに追加してインストールします。

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

1. [API キーを設定 ](https://experienceleague.adobe.com/docs/commerce/user-guides/integration-services/saas.html?lang=ja) して、拡張機能をシステムに接続します。

## エージェントのインストール

インストールを簡単にする [ シェルスクリプト ](https://github.com/magento-swat/install-agent-helpers/blob/main/install.sh) を作成しました。 シェルスクリプトを使用することをお勧めしますが、必要に応じて [ 手動インストール ](#manual) 方法に従うことができます。

>[!INFO]
>
>エージェントのインストール後、新しいリリースが使用可能になると自動的にアップデートされます。

### スクリプト

1. シェルスクリプト無償体験版で試してみるして実行します。

   ```bash
   bash -c "$(wget -qO - https://raw.githubusercontent.com/magento-swat/install-agent-helpers/main/install.sh)"
   ```

   >[!TIP]
   >
   >ルート Adobe Systems Commerce プロジェクト ディレクトリの外部にエージェントをインストールすることをお勧めします。

1. インストールを確認します。

   ```bash
   ./scheduler -v
   ```

   ```bash
   Version: 1.0.1
   Success exit.
   ```

1. エージェントをダウンロードしてインストールしたら、次のいずれかの方法を使用して [エージェントを実行するように構成](#run-the-agent) します。

   - [サービス](#service) (ルートアクセス権がある場合は推奨)

   - [Cron](#cron)

### 手動 {#manual}

エージェントのインストールに [シェルスクリプト](https://github.com/magento-swat/install-agent-helpers/blob/main/install.sh) を使用したくない場合は、次の手順に従って手動でインストールする必要があります。

1. エージェントダウンロードするディレクトリ作成。

   >[!TIP]
   >
   >ルート Adobe Systems Commerce プロジェクト ディレクトリの外部にエージェントをインストールすることをお勧めします。

1. バイナリファイルをダウンロードして解凍します。

   >[!INFO]
   >
   >[!DNL Site-Wide Analysis Tool] を使用するには、まずAdobe Commerce管理者からダッシュボードにアクセスする際に表示される利用条件を読み、同意する必要があります。

   **AMD64** アーキテクチャの場合:

   1. ランチャーアーカイブ無償体験版で試してみるします。

      ```bash
      curl -O https://updater.supportinsights.adobe.com/launcher/launcher.linux-amd64.tar.gz
      ```

   1. ランチャーアーカイブを展開します。

      ```bash
      tar -xf launcher.linux-amd64.tar.gz
      ```

   **ARM64** アーキテクチャの場合:

   1. ランチャーアーカイブ無償体験版で試してみるします。

      ```bash
      curl -O https://updater.supportinsights.adobe.com/launcher/launcher.linux-arm64.tar.gz
      ```

   1. ランチャーアーカイブを展開します。

      ```bash
      tar -xf launcher.linux-arm64.tar.gz
      ```

1. *(オプション)* チェックサムファイルの署名を検証します。

   ```bash
   echo -n "LS0tLS1CRUdJTiBQVUJMSUMgS0VZLS0tLS0KTUlJQ0lqQU5CZ2txaGtpRzl3MEJBUUVGQUFPQ0FnOEFNSUlDQ2dLQ0FnRUE0M2FBTk1WRXR3eEZBdTd4TE91dQpacG5FTk9pV3Y2aXpLS29HendGRitMTzZXNEpOR3lRS1Jha0MxTXRsU283VnFPWnhUbHZSSFhQZWt6TG5vSHVHCmdmNEZKa3RPUEE2S3d6cjF4WFZ3RVg4MEFYU1JNYTFadzdyOThhenh0ZHdURVh3bU9GUXdDcjYramFOM3ErbUoKbkRlUWYzMThsclk0NVJxWHV1R294QzBhbWVoakRnTGxJUSs1d1kxR1NtRGRiaDFJOWZqMENVNkNzaFpsOXFtdgorelhjWGh4dlhmTUU4MUZsVUN1elRydHJFb1Bsc3dtVHN3ODNVY1lGNTFUak8zWWVlRno3RFRhRUhMUVVhUlBKClJtVzdxWE9kTGdRdGxIV0t3V2ppMFlrM0d0Ylc3NVBMQ2pGdEQzNytkVDFpTEtzYjFyR0VUYm42V3I0Nno4Z24KY1Q4cVFhS3pYRThoWjJPSDhSWjN1aFVpRHhZQUszdmdsYXJSdUFacmVYMVE2ZHdwYW9ZcERKa29XOXNjNXlkWApBTkJsYnBjVXhiYkpaWThLS0lRSURnTFdOckw3SVNxK2FnYlRXektFZEl0Ni9EZm1YUnJlUmlMbDlQMldvOFRyCnFxaHNHRlZoRHZlMFN6MjYyOU55amgwelloSmRUWXRpdldxbGl6VTdWbXBob1NrVnNqTGtwQXBiUUNtVm9vNkgKakJmdU1sY1JPeWI4TXJCMXZTNDJRU1MrNktkMytwR3JyVnh0akNWaWwyekhSSTRMRGwrVzUwR1B6LzFkeEw2TgprZktZWjVhNUdCZm00aUNlaWVNa3lBT2lKTkxNa1cvcTdwM200ejdUQjJnbWtldm1aU3Z5MnVMNGJLYlRoYXRlCm9sdlpFd253WWRxaktkcVkrOVM1UlNVQ0F3RUFBUT09Ci0tLS0tRU5EIFBVQkxJQyBLRVktLS0tLQ==" | base64 -d > release.pub
   ```

   ```bash
   openssl dgst -sha256 -verify release.pub -signature launcher.sha256 launcher.checksum
   ```

1. *(オプション)* チェックサムを確認します。

   ```bash
   shasum -a 512 -c launcher.checksum
   ```

1. 次の内容の `config.yaml` ファイルを作成します。

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

1. エージェントをダウンロードしてインストールしたら、次のいずれかの方法を使用して [実行するように構成](#run-the-agent) する必要があります。

   - [サービス](#service) (ルートアクセス権がある場合は推奨)

   - [Cron](#cron)

## エージェントを実行する {#run-the-agent}

エージェントをサービスとして実行するように設定することをお勧めします。 インフラストラクチャへのアクセスが制限されていて、ルート権限がない場合は、代わりに [cron](#cron) を使用する必要があります。

### サービス {#service}

1. 次の構成でsystemdユニットファイル `(/etc/systemd/system/scheduler.service)` 作成します( `<filesystemowner>` エージェントとAdobe Systemsコマースソフトウェアがインストールされているディレクトリを所有するUNIX®ユーザーに置き換えます)。 エージェントをルートユーザーとしてダウンロードした場合は、ディレクトリとネストされたファイルを所有者変更します。

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

1. サービスLaunch。

   ```bash
   systemctl daemon-reload
   ```

   ```bash
   systemctl start scheduler
   ```

   ```bash
   systemctl enable scheduler
   ```

1. サービスが起動および実行されていることを検証します。

   ```bash
   journalctl -u scheduler | grep "Application is going to update" | tail -1 && echo "Agent is successfully installed"
   ```

### Cron {#cron}

root 権限がない場合、または root としてサービスを設定する権限がない場合は、cron を代わりに使用できます。

cron スケジュールを更新します。

```bash
( crontab -l ; echo "* * * * * flock -n /tmp/swat-agent.lockfile -c '/path/to/agent/scheduler' >> /path/to/agent/errors.log 2>&1" ) | sort - | uniq - | crontab -
```

## Uninstall

次のコマンドを実行して、システムからサービスをアンインストールし、生成されたすべてのファイルを削除します。

1. スケジューラーを停止します。

   ```bash
   systemctl stop scheduler
   ```

1. スケジューラーを無効にします。

   ```bash
   systemctl disable scheduler
   ```

1. スケジューラーサービスの `systemd` 単位ファイルを削除します。

   ```bash
   rm /etc/systemd/system/scheduler.service
   ```

1. `systemd` manager 設定をリロードします。

   ```bash
   systemctl daemon-reload
   ```

1. エラー状態から `systemd` ユニットをリセットします。

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

代わりに cron を使用してエージェントを実行するように設定した場合は、次の手順を使用します。

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

### アクセスキーが正しく解析されていない

アクセスキーが正しく解析されていない場合は、次のエラーが表示される場合があります。

```
ERRO[2022-10-10 00:01:41] Error while refreshing token: error while getting jwt from magento: invalid character 'M' looking for beginning of value
FATA[2022-12-10 20:38:44] bad http status from https://updater.supportinsights.adobe.com/linux-amd64.json: 403 Forbidden
```

このエラーを解決するには、次の手順を試してください。

1. [ スクリプト形式のインストール ](#scripted) を実行し、出力を保存して、出力にエラーがないか確認します。
1. 生成された `config.yaml` ファイルを確認し、Commerce インスタンスと PHP へのパスが正しいことを確認します。
1. スケジューラーを実行しているユーザーが [ ファイルシステム所有者 ](../../installation/prerequisites/file-system/overview.md)Unix グループに属しているか、ファイルシステム所有者と同じユーザーであることを確認します。
1. [Commerce サービスコネクタ ](https://experienceleague.adobe.com/docs/commerce/user-guides/integration-services/saas.html?lang=ja) のキーが正しくインストールされていることを確認し、キーを更新して拡張機能をシステムに接続します。
1. [ アンインストール ](#uninstall) キーを更新した後にエージェントをアンインストールし、[ インストールスクリプト ](#scripted) を使用して再インストールします。
1. スケジューラーを実行して、同じエラーが引き続き表示されるかどうかを確認します。
1. それでも同じエラーが発生する場合は、`config.yaml` のログレベルを上げてデバッグし、サポートチケットを開きます。

### *SIGFAULT* エラー

バイナリの実行時に *SIGFAULT* エラーが表示された場合は、Commerce ファイルとエージェント ファイルのファイル 所有者として実行していないAdobe Systems可能性があります。解決するには、Adobe Systemsコマースファイルが持つファイル所有者と同じユーザーを持つエージェントディレクトリ内のすべてのファイル、およびバイナリもそのユーザーで実行する必要があるかどうかを確認してください。`chown` コマンドを使用して、ファイル所有者を変更し、適切なユーザーに切り替えることができます。デーモン化メカニズム (Cron または System.d) が適切なユーザーの下でプロセスを実行していることを確認してください。

>[!INFO]
>
>[レポートにアクセスして生成する方法 [!DNL Site-Wide Analysis Tool] ](../site-wide-analysis-tool/access.md)を参照してください。
