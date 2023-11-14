---
title: アプリケーションの設定
description: Adobe CommerceおよびMagento Open Sourceのオンプレミスデプロイメントに必要なインストール後の設定について説明します。
feature: Install, Configuration
exl-id: b1808664-10ec-4147-8251-a99f8b58f4be
source-git-commit: 40d850add2ef8c51e9192758135768306b163780
workflow-type: tm+mt
source-wordcount: '730'
ht-degree: 0%

---

# アプリケーションの設定

Adobe CommerceまたはMagento Open Sourceのインストールが完了したら、設定する必要があります。 このトピックでは、推奨される設定をいくつか示します。

## cron の設定

UNIX タスクスケジューラ (cron) は、アプリケーションの日常的な操作にとって重要です。 インデックスの再作成、ニュースレター、電子メール、サイトマップなどのスケジュールを設定します。 A *crontab* は cron 設定です。

Adobe CommerceおよびMagento Open Sourceサービスは、 *crontab*、または一部のコア機能（および一部のサードパーティ拡張機能）が正しく機能しない問題を修正しました。

crontab を削除し、コマンドラインから cron を実行する方法など、cron の詳細については、 [cron の設定と実行](../../configuration/cli/configure-cron-jobs.md).

## セキュリティ設定と推奨事項

インストール後に、次の操作をお勧めします。

* ファイルの所有権と権限が正しく設定されていることを確認します。
* を強くお勧めします [デフォルトの管理 URI の変更](../tutorials/admin-uri.md) から `admin` 他のものに対して
* 次を確認します。 [`X-Frame-Option` HTTP ヘッダー](../../configuration/security/xframe-options.md) が適切に設定されている。
* クロスサイトスクリプティング (XSS) に対する注意事項： [テンプレートの保護](https://developer.adobe.com/commerce/php/development/security/cross-site-scripting/)

を次の方法でインストールした場合： [GitHub リポジトリのクローン作成](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)を使用する場合は、アプリケーションをデプロイする際に、実稼動環境に必要なファイルおよびフォルダーのみを含めるようにしてください。 不要なファイルやフォルダーを使用すると、セキュリティリスクが高まる可能性があります。

## Apache サーバーの書き換えを有効にする

Apache Web サーバーを使用する場合、ページを正しく表示するには、サーバーによる書き換えを有効にする必要があります。 そうしないと、スタイルやその他の問題のないページが表示されます。

[Apache サーバーの書き換えに関する節](../prerequisites/web-server/apache.md#apache-rewrites-and-htaccess)

## マルチ Web ノード環境でのキャッシュ

複数の Web ノードがある場合、 *できません* web ノード間で同期がおこなわれないので、アプリケーションのデフォルトのファイルキャッシュを使用します。 つまり、1 つの Web ノード上のアクティビティは、その Web ノードのファイルシステムにのみ書き込まれます。 後続のアクティビティを別の Web ノードで実行すると、不要なファイルが書き込まれたり、エラーが発生したりする場合があります。

代わりに、 [レディス](../../configuration/cache/config-redis.md) デフォルトのキャッシュとページキャッシュの両方に対して。

## サーバー設定

このセクションでは、アプリケーションが実行されるサーバーに対して考慮する必要のある設定について簡単に説明します。 これらの設定の一部は、アプリケーションと直接関係がないので、提案としてのみ提供されます。

### 対数のローテーション

UNIX `logrotate` ユーティリティを使用すると、大量のログファイルを生成するシステムを管理できます。 ログファイルの自動回転、圧縮、削除、メーリングが可能です。 各ログファイルは、日別、週別、月別、またはログファイルが指定のサイズを超えた場合に処理できます。

詳しくは、次のいずれかを参照してください。

* [HowTo:10 例を含む最終的なログ回転コマンドのチュートリアル](https://www.thegeekstuff.com/2010/07/logrotate-examples)
* [スタック Exchange](https://unix.stackexchange.com/questions/85662/how-to-properly-automatically-manually-rotate-log-files-for-production-rails-app)
* [`logrotate` man ページ](https://linuxconfig.org/logrotate-8-manual-page)

### 様々なサービスの通信を可能にする iptables ルールを設定します。

1 台のサーバが存在するか、複数のサーバが存在するかに関わらず、サービスの通信を有効にするには、ファイアウォールでポートを開く必要があります。 例えば、Adobe Commerceで Solr 検索エンジンを使用する場合、Solr 検索エンジンを有効にして Web サーバーとの通信を可能にする必要があります。 複数の Web ノードがある場合は、それらが相互に通信できるようにする必要があります。

詳細情報：

* Ubuntu: [Ubuntu ドキュメントページ](https://help.ubuntu.com/community/IptablesHowTo).
* CentOS: [CentOS のハウツー](https://wiki.centos.org/HowTos%282f%29Network%282f%29IPTables.html).

### セキュリティ強化 Linux(SELinux) ルール

SELinux を使用するかどうかに関する推奨事項はありませんが、SELinux を使用する場合は、iptables を設定するのと同様に、相互に通信するサービスを設定する必要があります。

詳細情報：

* Ubuntu: [Debian ハンドブック](https://debian-handbook.info/browse/stable/sect.selinux.html)
* CentOS: [CentOS Wiki](https://wiki.centos.org/HowTos/SELinux)

### 電子メールサーバーを設定する

Adobe CommerceとMagento Open Sourceには電子メールサーバーが必要です。 特定のサーバーを推奨するわけではありませんが、次のいずれかを試すことができます。

* CentOS の Postfix ([Digital Ocean チュートリアル](https://www.digitalocean.com/community/tutorials/how-to-install-postfix-on-centos-6), [CentOS ドキュメント](https://www.centos.org))
* Ubuntu の Postfix ([Digital Ocean チュートリアル](https://www.digitalocean.com/community/tutorials/how-to-install-and-setup-postfix-on-ubuntu-14-04), [Ubuntu ドキュメント](https://help.ubuntu.com/community/MailServer))

### 検索エンジンを絞り込んでパフォーマンスを向上：

2.4.0 以降のすべてのインストールで、Elasticsearchまたは OpenSearch が必要です。

* [検索エンジンのインストールと設定](../../configuration/search/overview-search.md)

### メッセージキューの設定

バージョン 2.3.0 以降、Adobe CommerceおよびMagento Open Sourceにはメッセージキュー機能が含まれています。 以前のバージョンでは、Adobe Commerceでのみ使用できます。

* [[!DNL RabbitMQ]](../../configuration/queues/message-queue-framework.md)

## Adobe Commerceのみの設定

次の設定は、Adobe Commerceを使用する場合にのみ指定できます。

* [チェックアウト、注文管理、その他のデータベーステーブル用にデータベースを分割](../../configuration/storage/multi-master.md)
