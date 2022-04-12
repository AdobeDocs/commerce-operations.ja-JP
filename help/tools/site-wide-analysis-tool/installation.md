---
title: インストールガイド
description: このガイドを使用して、 [!DNL Site-Wide Analysis Tool] （Web サイト用）
source-git-commit: de2fb829def2cf94c452a06a219d7f29885c8f9f
workflow-type: tm+mt
source-wordcount: '1050'
ht-degree: 0%

---

# インストールガイド

この [!DNL Site-Wide Analysis Tool] では、クラウドインフラストラクチャのインストール時にAdobe Commerceのセキュリティと操作性を確保するための24/7のリアルタイムパフォーマンス監視、レポートおよび推奨事項を提供しています。 また、利用可能なパッチとインストール済みのパッチ、サードパーティの拡張機能、Adobe Commerceのインストールに関する詳細情報も提供されます。

>[!INFO]
>
>学ぶ [有効にする方法](../site-wide-analysis-tool/access.md) の [!DNL Site-Wide Analysis Tool] レポートを生成します。

Adobe Commerceをオンプレミスでインストールしている場合、このツールを使用するには、インフラストラクチャにエージェントをインストールする必要があります。 クラウドインフラストラクチャプロジェクト上のAdobe Commerceにエージェントをインストールする必要はありません。

## エージェント

この [!DNL Site-Wide Analysis Tool] エージェントを使用すると、 [!DNL Site-Wide Analysis Tool] Adobe Commerceのオンプレミスインストールの場合。

この [!DNL Site-Wide Analysis Tool] エージェントは、アプリケーションとビジネスデータを収集し、分析し、インストールの状態に関する追加のインサイトを提供して、顧客体験を向上させます。 アプリケーションを監視し、パフォーマンス、セキュリティ、可用性、アプリケーションの問題を特定します。

エージェントのインストールには、次の手順が必要です。

1. システム要件を確認します。

1. での API キーの設定 [!UICONTROL Commerce Services Connector] 拡張子。

1. エージェントをインストールします。

1. エージェントを実行します。

>[!INFO]
>
>エージェントは、複数ノードのAdobe Commerceインストールをサポートします。 各ノードにエージェントをインストールして設定する必要があります。

## 必要システム構成

オンプレミスのインフラストラクチャは、エージェントをインストールする前に、次の要件を満たす必要があります。

- オペレーティングシステム

   - [!DNL Linux x86-64] 次のような配分： [!DNL RedHat Enterprise Linux (RHEL)], [!DNL CentOS], [!DNL Ubuntu], [!DNL Debian]、類似
   >[!IMPORTANT]
   >
   >Adobe Commerceはではサポートされていません [!DNL Microsoft Windows] または [!DNL macOS].

- Adobe Commerce 2.4.1 以降

- [!DNL Commerce Services Connector extension]

- PHP CLI

- Bash/shell ユーティリティ

   - `grep`

   - `awk`

   - `nice`

   - `grep`

## [!DNL Commerce Services Connector]

エージェントには [[!DNL Commerce Services Connector]](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/saas.html) お使いのシステムにインストールする拡張機能および [設定済み](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/saas.html) と API キーを組み合わせました。 拡張機能がインストールされていることを確認するには、次のコマンドを実行します。

```bash
bin/magento module:status Magento_ServicesConnector
```

拡張機能をインストールし、別のサービスの既存の API キーを使用して設定した場合は、 **API キーを再生成する必要があります** エージェントのAdobe Commerce Admin で更新します。

1. Web サイトを [メンテナンスモード](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html).

1. ログイン [accounts.magento.com](https://account.magento.com/customer/account/login?_ga=2.164207871.117144580.1649172612-1623400270.1640858671).

1. クリック **[!UICONTROL API Portal]**.

1. クリック **[!UICONTROL Delete]** をクリックします。

1. [設定](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/saas.html) 新しい API キー。

>[!IMPORTANT]
>
> API ポータルで新しいキーを生成する場合は、 [!DNL Admin configuration]. 新しいキーを生成し、 [!DNL Admin]を使用した場合、SaaS 拡張機能は機能しなくなり、貴重なデータが失われます。

拡張機能がインストールされていない場合は、次の手順に従ってインストールします。

1. 拡張機能を `composer.json` ファイルを作成し、インストールします。

   ```bash
   composer require magento/services-connector:1.*
   ```

1. 拡張機能を有効にします。

   ```bash
   bin/magento module:enable Magento_ServicesConnector
   ```

1. データベーススキーマを更新します。

   ```bash
   bin/magento setup:upgrade
   ```

1. [API キーの設定](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/saas.html) 拡張機能をシステムに接続する場合。

## エージェントのインストール

以下を作成しました： [シェルスクリプト](https://github.com/magento-swat/install-agent-helpers/blob/main/install.sh) インストールを簡単にする。 シェルスクリプトを使用することをお勧めしますが、次の手順に従うことができます。 [手動設置](#manual) メソッドを使用します。

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
   scheduler -v
   ```

   ```bash
   Version: 1.0.1
   Success exit.
   ```

1. エージェントをダウンロードしてインストールした後、次の操作を行う必要があります。 [実行するように設定](#run-the-agent) 次のいずれかの方法を使用します。

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
      curl -O https://updater.swat.magento.com/launcher/launcher.linux-amd64.tar.gz
      ```

   1. ランチャーアーカイブを解凍します。

      ```bash
      tar -xf launcher.linux-amd64.tar.gz
      ```
   の **ARM64** アーキテクチャ：

   1. ランチャーアーカイブをダウンロードします。

      ```bash
      curl -O https://updater.swat.magento.com/launcher/launcher.linux-arm64.tar.gz
      ```

   1. ランチャーアーカイブをインパックします。

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

1. を作成します。 `config.yaml` ファイルに次の内容を追加します。

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

1. エージェントをダウンロードしてインストールした後、次の操作を行う必要があります。 [実行するように設定](#run-the-agent) 次のいずれかの方法を使用します。

   - [サービス](#service) （ルートアクセス権を持っている場合に推奨）

   - [Cron](#cron)

## エージェントの実行 {#run-the-agent}

エージェントをサービスとして実行するように設定することをお勧めします。 インフラストラクチャへのアクセスが制限されていて、ルート権限がない場合は、 [cron](#cron) 代わりに、

### サービス {#service}

1. systemd ユニットファイルの作成 `(/etc/systemd/system/scheduler.service)` を次の設定に置き換えます ( `<filesystemowner>` エージェントがインストールされているディレクトリを所有する Unix ユーザー )

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

cron スケジュールを更新します。

```bash
( crontab -l ; echo "* * * * * flock -n /tmp/swat-agent.lockfile -c '/path/to/agent/scheduler' >> /path/to/agent/errors.log 2>&1" ) | sort - | uniq - | crontab -
```

## アンインストール

次のコマンドを実行して、システムからサービスをアンインストールし、生成されたすべてのファイルを削除します。

1. スケジューラを停止します。

   ```bash
   systemctl stop scheduler
   ```

1. スケジューラを無効にします。

   ```bash
   systemctl disable scheduler
   ```

1. スケジューラーサービスの `systemd` 単位ファイル。

   ```bash
   rm /etc/systemd/system/scheduler.service
   ```

1. をリロードします。 `systemd` マネージャー設定

   ```bash
   systemctl daemon-reload
   ```

1. リセット `systemd` の単位を失敗状態から取得します。

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

## 設定ファイルを上書き

環境変数を使用して、インストール時に設定ファイルで指定した値を上書きできます。 これにより、以前のバージョンのエージェントとの下位互換性が維持されます。 推奨値については、次の表を参照してください。

| プロパティ | 説明 |
| --- | --- |
| `SWAT_AGENT_APP_NAME` | エージェントのインストール時に指定した会社またはサイト名 |
| `SWAT_AGENT_APPLICATION_PHP_PATH` | PHP CLI インタプリタのパス ( 通常は `/usr/bin/php`) |
| `SWAT_AGENT_APPLICATION_MAGENTO_PATH` | Adobe Commerceアプリケーションがインストールされているルートディレクトリ ( 通常は `/var/www/html`) |
| `SWAT_AGENT_APPLICATION_DB_USER` | Adobe Commerceインストール用のデータベースユーザー |
| `SWAT_AGENT_APPLICATION_DB_PASSWORD` | Adobe Commerceのインストールで指定したユーザーのデータベースパスワード |
| `SWAT_AGENT_APPLICATION_DB_HOST` | Adobe Commerceインストール用のデータベースホスト |
| `SWAT_AGENT_APPLICATION_DB_NAME` | Adobe Commerceインストールのデータベース名 |
| `SWAT_AGENT_APPLICATION_DB_PORT` | Adobe Commerceインストール用のデータベースポート ( 通常は `3306`) |
| `SWAT_AGENT_APPLICATION_DB_TABLE_PREFIX` | Adobe Commerceインストール用の表プレフィックス ( デフォルト値： `empty`) |
| `SWAT_AGENT_APPLICATION_DB_REPLICATED` | Adobe Commerceのインストールにセカンダリデータベースインスタンスがあるかどうか ( 通常は `false`) |
| `SWAT_AGENT_APPLICATION_CHECK_REGISTRY_PATH` | エージェントの一時ディレクトリ ( 通常は `/usr/local/swat-agent/tmp`) |
| `SWAT_AGENT_RUN_CHECKS_ON_START` | 最初の実行時にデータを収集する ( 通常 `1`) |
| `SWAT_AGENT_LOG_LEVEL` | 重大度 ( 通常は `error`) |
| `SWAT_AGENT_ENABLE_AUTO_UPGRADE` | 自動アップグレードを有効にする（アップグレード後に再起動が必要）オプションが無効な場合、エージェントはアップグレードを確認しません。 `true` または `false`) |
| `SWAT_AGENT_IS_SANDBOX=false` | サンドボックスモードを有効にして、ステージング環境でエージェントを使用する |

>[!INFO]
>
>詳しくは、 [アクセス方法 [!DNL Site-Wide Analysis Tool] レポートの生成](../site-wide-analysis-tool/access.md).
