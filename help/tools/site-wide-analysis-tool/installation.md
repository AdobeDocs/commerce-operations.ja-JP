---
title: インストールガイド
description: このガイドを使用してをインストールします。 [!DNL Site-Wide Analysis Tool] Web サイトの場合
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
>2024 年 4 月 23 日付 [!DNL Site-Wide Analysis Tool] Adobe Commerceのオンプレミス環境のお客様はすべて廃止されます。

この [!DNL Site-Wide Analysis Tool] は、クラウドインフラストラクチャー上のAdobe Commerceのセキュリティと操作性を確保するために、24 時間 365 日、リアルタイムのパフォーマンスモニタリング、レポート、推奨事項を提供します。 また、使用可能なパッチおよびインストール済みのパッチ、サードパーティの拡張機能、Adobe Commerceのインストールに関する詳細情報も提供されます。

>[!INFO]
>
>学ぶ [を有効にする方法](../site-wide-analysis-tool/access.md) この [!DNL Site-Wide Analysis Tool] およびレポートを生成します。

Adobe Commerceをオンプレミスでインストールしている場合は、このツールを使用するために、インフラストラクチャにエージェントをインストールします。 クラウドインフラストラクチャプロジェクトのAdobe Commerceにエージェントをインストールする必要はありません。

## 代理人

この [!DNL Site-Wide Analysis Tool] エージェントでは、 [!DNL Site-Wide Analysis Tool] （Adobe Commerceのオンプレミスインストールの場合）

この [!DNL Site-Wide Analysis Tool] エージェントは、アプリケーションおよびビジネスデータを収集して分析し、インストールの正常性に関する追加のインサイトを提供することで、カスタマーエクスペリエンス（顧客体験）を向上させます。 アプリケーションを監視し、パフォーマンス、セキュリティ、可用性、アプリケーションの問題を特定するのに役立ちます。

エージェントをインストールするには、次の手順が必要です。

1. システム要件を確認します。

1. での API キーの設定 [!UICONTROL Commerce Services Connector] 拡張機能。

1. エージェントをインストールします。

1. エージェントを実行します。

>[!INFO]
>
>このエージェントは、複数ノードのAdobe Commerceのインストールをサポートします。 各ノードにエージェントをインストールして設定します。

## 必要システム構成

エージェントをインストールする前に、オンプレミスインフラストラクチャが次の要件を満たしている必要があります。

- オペレーティングシステム

   - [!DNL Linux x86-64] 配分（例：） [!DNL Red Hat® Enterprise Linux (RHEL)], [!DNL CentOS], [!DNL Ubuntu], [!DNL Debian]、および類似

  >[!IMPORTANT]
  >
  >Adobe Commerceはではサポートされていません [!DNL Microsoft Windows] または [!DNL macOS].

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

エージェントには、 [[!DNL Commerce Services Connector]](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html) お使いのシステムにインストールする拡張機能 [設定済み](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html) （API キーを使用）。 拡張機能がインストールされていることを確認するには、次のコマンドを実行します。

```bash
bin/magento module:status Magento_ServicesId
```

拡張機能をインストールし、別のサービスの既存の API キーを使用して設定した場合は、 **API キーを再生成してください** そして、Adobe Commerce管理者でエージェントの更新を行います。

1. Web サイトの配置先 [メンテナンスモード](../../installation/tutorials/maintenance-mode.md).

1. にログインします [account.magento.com](https://account.magento.com/customer/account/login?_ga=2.164207871.117144580.1649172612-1623400270.1640858671).

   >[!NOTE]
   >
   > アカウントにアクセスできない場合は、を参照してください [Adobe Commerce サポートまたは Cloud アカウントにログインできない](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/unable-to-log-in-to-support-or-cloud-project.html) トラブルシューティングのヘルプ。

1. クリック **[!UICONTROL API Portal]**.

1. クリック **[!UICONTROL Delete]** 既存の API キーの横。

1. [設定](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html) 新しい API キー。

>[!IMPORTANT]
>
> API ポータルで新しいキーを生成した場合、直ちに以下の API キーを更新してください。 [!DNL Admin configuration]. 新しいキーを生成し、のキーを更新しない場合 [!DNL Admin]を使用すると、SaaS 拡張機能は機能しなくなり、貴重なデータが失われます。

拡張機能がインストールされていない場合は、次の手順を使用してインストールします。

1. 拡張機能を `composer.json` ファイルを作成してインストールします。

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

1. [API キーの設定](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html) ：拡張機能をシステムに接続します。

## エージェントのインストール

を作成しました [シェルスクリプト](https://github.com/magento-swat/install-agent-helpers/blob/main/install.sh) 設置を簡単にする。 シェルスクリプトを使用することをお勧めしますが、次の手順に従ってください。 [手動インストール](#manual) 必要に応じて、メソッドを使用します。

>[!INFO]
>
>エージェントのインストール後、新しいリリースが使用可能になると自動的にアップデートされます。

### スクリプト化

1. シェルスクリプトをダウンロードして実行します。

   ```bash
   bash -c "$(wget -qO - https://raw.githubusercontent.com/magento-swat/install-agent-helpers/main/install.sh)"
   ```

   >[!TIP]
   >
   >ルートのAdobe Commerce プロジェクトディレクトリの外部にエージェントをインストールすることをお勧めします。

1. インストールを確認します。

   ```bash
   ./scheduler -v
   ```

   ```bash
   Version: 1.0.1
   Success exit.
   ```

1. エージェントをダウンロードしてインストールした後、 [実行するように設定](#run-the-agent) 次のいずれかの方法を使用します。

   - [サービス](#service) （ルートアクセス権がある場合は推奨）

   - [Cron](#cron)

### 手動 {#manual}

を使用しない場合 [シェルスクリプト](https://github.com/magento-swat/install-agent-helpers/blob/main/install.sh) エージェントをインストールするには、次の手順に従って手動でインストールする必要があります。

1. エージェントのダウンロード先となるディレクトリを作成します。

   >[!TIP]
   >
   >ルートのAdobe Commerce プロジェクトディレクトリの外部にエージェントをインストールすることをお勧めします。

1. バイナリファイルをダウンロードして解凍します。

   >[!INFO]
   >
   >を使用するには [!DNL Site-Wide Analysis Tool]を参照する必要があります。最初に、Adobe Commerce管理者からダッシュボードにアクセスする際に表示される利用条件を読んで、同意する必要があります。

   の場合 **AMD64** アーキテクチャ：

   1. ランチャーアーカイブをダウンロードします。

      ```bash
      curl -O https://updater.supportinsights.adobe.com/launcher/launcher.linux-amd64.tar.gz
      ```

   1. ランチャーアーカイブを解凍します。

      ```bash
      tar -xf launcher.linux-amd64.tar.gz
      ```

   の場合 **ARM64** アーキテクチャ：

   1. ランチャーアーカイブをダウンロードします。

      ```bash
      curl -O https://updater.supportinsights.adobe.com/launcher/launcher.linux-arm64.tar.gz
      ```

   1. ランチャーアーカイブを解凍します。

      ```bash
      tar -xf launcher.linux-arm64.tar.gz
      ```

1. *（オプション）* チェックサムファイルの署名を確認します。

   ```bash
   echo -n "LS0tLS1CRUdJTiBQVUJMSUMgS0VZLS0tLS0KTUlJQ0lqQU5CZ2txaGtpRzl3MEJBUUVGQUFPQ0FnOEFNSUlDQ2dLQ0FnRUE0M2FBTk1WRXR3eEZBdTd4TE91dQpacG5FTk9pV3Y2aXpLS29HendGRitMTzZXNEpOR3lRS1Jha0MxTXRsU283VnFPWnhUbHZSSFhQZWt6TG5vSHVHCmdmNEZKa3RPUEE2S3d6cjF4WFZ3RVg4MEFYU1JNYTFadzdyOThhenh0ZHdURVh3bU9GUXdDcjYramFOM3ErbUoKbkRlUWYzMThsclk0NVJxWHV1R294QzBhbWVoakRnTGxJUSs1d1kxR1NtRGRiaDFJOWZqMENVNkNzaFpsOXFtdgorelhjWGh4dlhmTUU4MUZsVUN1elRydHJFb1Bsc3dtVHN3ODNVY1lGNTFUak8zWWVlRno3RFRhRUhMUVVhUlBKClJtVzdxWE9kTGdRdGxIV0t3V2ppMFlrM0d0Ylc3NVBMQ2pGdEQzNytkVDFpTEtzYjFyR0VUYm42V3I0Nno4Z24KY1Q4cVFhS3pYRThoWjJPSDhSWjN1aFVpRHhZQUszdmdsYXJSdUFacmVYMVE2ZHdwYW9ZcERKa29XOXNjNXlkWApBTkJsYnBjVXhiYkpaWThLS0lRSURnTFdOckw3SVNxK2FnYlRXektFZEl0Ni9EZm1YUnJlUmlMbDlQMldvOFRyCnFxaHNHRlZoRHZlMFN6MjYyOU55amgwelloSmRUWXRpdldxbGl6VTdWbXBob1NrVnNqTGtwQXBiUUNtVm9vNkgKakJmdU1sY1JPeWI4TXJCMXZTNDJRU1MrNktkMytwR3JyVnh0akNWaWwyekhSSTRMRGwrVzUwR1B6LzFkeEw2TgprZktZWjVhNUdCZm00aUNlaWVNa3lBT2lKTkxNa1cvcTdwM200ejdUQjJnbWtldm1aU3Z5MnVMNGJLYlRoYXRlCm9sdlpFd253WWRxaktkcVkrOVM1UlNVQ0F3RUFBUT09Ci0tLS0tRU5EIFBVQkxJQyBLRVktLS0tLQ==" | base64 -d > release.pub
   ```

   ```bash
   openssl dgst -sha256 -verify release.pub -signature launcher.sha256 launcher.checksum
   ```

1. *（オプション）* チェックサムを確認します。

   ```bash
   shasum -a 512 -c launcher.checksum
   ```

1. を作成 `config.yaml` 次の内容のファイル。

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

1. エージェントをダウンロードしてインストールした後、以下を実行する必要があります [実行するように設定](#run-the-agent) 次のいずれかの方法を使用します。

   - [サービス](#service) （ルートアクセス権がある場合は推奨）

   - [Cron](#cron)

## エージェントの実行 {#run-the-agent}

エージェントをサービスとして実行するように設定することをお勧めします。 インフラストラクチャへのアクセスが制限されていて、ルート権限がない場合は、 [cron](#cron) その代わり。

### サービス {#service}

1. システム単位ファイルの作成 `(/etc/systemd/system/scheduler.service)` 次の設定で置き換えます（を `<filesystemowner>` （エージェントおよびAdobe Commerceソフトウェアがインストールされているディレクトリを所有する UNIX® ユーザーの場合） エージェントを root ユーザーとしてダウンロードした場合は、ディレクトリとネストされたファイルの所有者を変更します。

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

1. スケジューラーサービスの削除 `systemd` 単位ファイル。

   ```bash
   rm /etc/systemd/system/scheduler.service
   ```

1. をリロードします。 `systemd` マネージャーの設定。

   ```bash
   systemctl daemon-reload
   ```

1. いずれかをリセット `systemd` 失敗状態からのユニット。

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

```terminal
ERRO[2022-10-10 00:01:41] Error while refreshing token: error while getting jwt from magento: invalid character 'M' looking for beginning of value
FATA[2022-12-10 20:38:44] bad http status from https://updater.supportinsights.adobe.com/linux-amd64.json: 403 Forbidden
```

このエラーを解決するには、次の手順を試してください。

1. 実行 [スクリプトによるインストール](#scripted)出力を保存し、出力でエラーを確認します。
1. 生成されたをレビュー `config.yaml` ファイルを開き、Commerce インスタンスと PHP へのパスが正しいことを確認します。
1. スケジューラーを実行しているユーザーが [ファイルシステム所有者](../../installation/prerequisites/file-system/overview.md) Unix グループまたはは、ファイルシステムの所有者と同じユーザーです。
1. 次のことを確認します [Commerce サービスコネクタ](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html) キーが正しくインストールされており、拡張機能をシステムに接続するために更新してみてください。
1. [Uninstall](#uninstall) キーを更新し、を使用して再インストール後のエージェント [スクリプトをインストール](#scripted).
1. スケジューラーを実行して、同じエラーが引き続き表示されるかどうかを確認します。
1. それでも同じエラーが発生する場合は、でログレベルを上げます。 `config.yaml` をクリックし、サポートチケットをデバッグして開きます。

### *SIGFAULT* エラー

を表示している場合 *SIGFAULT* error バイナリを実行する場合、Adobe Commerceおよび Agent ファイルのファイルオーナーとしてこれを実行しない可能性があります。
これを解決するには、エージェントディレクトリ内のファイルのうち、Adobe Commerce ファイルのファイルオーナーと同じユーザーを持つすべてのファイルが、そのユーザーの下でもバイナリを実行する必要があるかどうかを確認してください。
を使用できます `chown` コマンドを使用してファイルの所有者を変更し、適切なユーザーに切り替えます。
デーモンのメカニズム （Cron または System.d）で、適切なユーザーの下でプロセスが実行されていることを確認します。

>[!INFO]
>
>参照： [アクセス方法 [!DNL Site-Wide Analysis Tool] およびレポートの生成](../site-wide-analysis-tool/access.md).
