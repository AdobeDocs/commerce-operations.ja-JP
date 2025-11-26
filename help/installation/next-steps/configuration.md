---
title: アプリケーションの設定
description: Adobe Commerceのオンプレミスデプロイメントに必要なインストール後設定について説明します。
feature: Install, Configuration
exl-id: b1808664-10ec-4147-8251-a99f8b58f4be
source-git-commit: 84a20012a81278cc95587ec14281b05330261687
workflow-type: tm+mt
source-wordcount: '713'
ht-degree: 0%

---

# アプリケーションの設定

Adobe Commerceのインストールが完了したら、設定する必要があります。 このトピックでは、いくつかの推奨設定を示します。

## cron の設定

UNIX のタスク・スケジューラである cron は、アプリケーションの日常業務にとって重要な役割を果たします。 インデックス再作成、ニュースレター、メール、サイトマップなどのスケジュールを設定します。 *crontab* は cron 設定です。

*crontab* でAdobe Commerce サービスをインストールする必要があります。インストールしないと、一部のコア機能（および一部のサードパーティの拡張機能）が正しく機能しません。

crontab を削除してコマンドラインから cron を実行する方法など、cron について詳しくは、[cron の設定と実行 ](../../configuration/cli/configure-cron-jobs.md) を参照してください。

## セキュリティ設定と推奨事項

インストール後は、次の操作をお勧めします。

* ファイルの所有権と権限が [ 適切に設定されていることを確認 ](../prerequisites/file-system/configure-permissions.md) ます
* [ デフォルトの管理者 URI の ](../tutorials/admin-uri.md) から別の場所への変更 `admin` を強くお勧めします
* [`X-Frame-Option` HTTP ヘッダー ](../../configuration/security/xframe-options.md) が正しく設定されていることを確認します。
* クロスサイトスクリプティング（XSS）に対する予防策として、テンプレートを保護 [ します ](https://developer.adobe.com/commerce/php/development/security/cross-site-scripting)

[GitHub リポジトリをクローン ](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository) してインストールした場合は、アプリケーションをデプロイする際に、実稼動環境に必要なファイルとフォルダーのみが含まれていることを確認してください。 不要なファイルやフォルダーがあると、セキュリティリスクが生じる可能性があります。

## Apache サーバーの書き換えを有効にする

Apache web サーバーを使用する場合は、ページを正しく表示するためのサーバー書き換えを有効にする必要があります。 そうでない場合は、スタイルやその他の問題がないページが表示されます。

[Apache サーバーの書き換えに関する節](../prerequisites/web-server/apache.md#apache-rewrites-and-htaccess)

## マルチ Web ノード環境でのキャッシュ

複数の web ノードがある場合、web ノード間で同期が行われないので、アプリケーションのデフォルトのファイルキャッシュを使用 *できません*。 つまり、1 つの web ノードのアクティビティは、その web ノードのファイルシステムにのみ書き込まれます。 後続のアクティビティを別の web ノードで実行すると、不要なファイルが書き込まれたり、エラーが発生したりする可能性があります。

代わりに、デフォルトキャッシュとページキャッシュの両方に [Redis](../../configuration/cache/config-redis.md) を使用します。

## サーバー設定

このセクションでは、アプリケーションが実行されるサーバーで考慮すべき設定について簡単に説明します。 これらの設定の一部は、アプリケーションに直接関係しないものもあり、単なる提案として提供されています。

### ログローテーション

UNIX `logrotate` ユーティリティを使用すると、多数のログ・ファイルを生成するシステムを管理できます。 ログファイルのローテーション、圧縮、削除、メーリングを自動的に行うことができます。 各ログ ファイルは、毎日、毎週、毎月、またはログ ファイルが指定したサイズを超えたときに処理できます。

詳しくは、次のいずれかを参照してください。

* [HowTo: Ultimate log rotate コマンドのチュートリアルと 10 の例 ](https://www.thegeekstuff.com/2010/07/logrotate-examples)
* [ スタック交換 ](https://unix.stackexchange.com/questions/85662/how-to-properly-automatically-manually-rotate-log-files-for-production-rails-app)
* [`logrotate` man ページ ](https://linuxconfig.org/logrotate-8-manual-page)

>[!AVAILABILITY]
>
>クラウドインフラストラクチャプロジェクトのAdobe Commerceには、次の可用性に関する情報が適用されます。
>
>* スターター環境にはログローテーションがありません。
>
>* Pro 統合環境では、ログローテーションを設定できません。 必要に応じて、カスタムのソリューション/スクリプトを実装し、スクリプトを実行するには [cron を設定 ](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/app/properties/crons-property) する必要があります。

### 様々なサービスが通信できるように iptables ルールを設定します

サーバーが 1 台でも複数でも、サービスが通信できるようにするには、ファイアウォールでポートを開く必要があります。 例えば、Adobe Commerceで Solr 検索エンジンを使用する場合、web サーバーと通信するには有効にする必要があります。 複数の web ノードがある場合、それらを相互に通信できるようにする必要があります。

詳細情報：

* Ubuntu: [Ubuntu ドキュメントページ ](https://help.ubuntu.com/community/IptablesHowTo)。
* CentOS: [CentOS のハウツー ](https://wiki.centos.org/HowTos%282f%29Network%282f%29IPTables.html)。

### Security Enhanced Linux （SELinux）ルール

SELinux を使用するかどうかの推奨事項はありません。ただし、使用する場合は、iptables の設定と同様に、相互に通信するようにサービスを設定する必要があります。

詳細情報：

* Ubuntu: [Debian ハンドブック ](https://debian-handbook.info/browse/stable/sect.selinux.html)
* CentOS: [CentOS の wiki](https://wiki.centos.org/HowTos/SELinux)

### メールサーバーの設定

Adobe Commerceにはメールサーバーが必要です。 特定のサーバーを使用することはお勧めしませんが、次のいずれかを試すことができます。

* CentOS の Postfix （[Digital Ocean チュートリアル ](https://www.digitalocean.com/community/tutorials/how-to-install-postfix-on-centos-6)、[CentOS ドキュメント ](https://www.centos.org)）
* Ubuntu の Postfix （[Digital Ocean チュートリアル ](https://www.digitalocean.com/community/tutorials/how-to-install-and-setup-postfix-on-ubuntu-14-04)、[Ubuntu ドキュメント ](https://help.ubuntu.com/community/MailServer)）

### 検索エンジンを絞り込んで、パフォーマンスを向上させます。

2.4.0 以降、すべてのインストールにElasticsearchまたは OpenSearch が必要です。

* [検索エンジンのインストールと設定](../../configuration/search/overview-search.md)

### メッセージキューの設定

バージョン 2.3.0 以降、Adobe Commerceにはメッセージキュー機能が含まれています。 以前のバージョンでは、Adobe Commerceでのみ使用できます。

* [[!DNL RabbitMQ]](../../configuration/queues/message-queue-framework.md)

## Adobe Commerceのみの設定

以下を設定できるのは、Adobe Commerceを使用する場合のみです。

* [チェックアウト、注文管理、その他のデータベース テーブル用にデータベースを分割します](../../configuration/storage/multi-master.md)
