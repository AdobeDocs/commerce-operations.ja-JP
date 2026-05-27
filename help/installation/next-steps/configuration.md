---
title: アプリケーションの設定
description: Adobe Commerce オンプレミスのデプロイメントに必要なインストール後の設定について説明します。
feature: Install, Configuration
exl-id: b1808664-10ec-4147-8251-a99f8b58f4be
source-git-commit: 84a20012a81278cc95587ec14281b05330261687
workflow-type: tm+mt
source-wordcount: '819'
ht-degree: 0%

---

# アプリケーションの設定

Adobe Commerceのインストールが完了したら、設定する必要があります。 このトピックでは、推奨される設定設定をいくつか紹介します。

## cronの設定

UNIX タスクスケジューラーのcronは、アプリケーションの日常業務に不可欠です。 インデックス再作成、ニュースレター、電子メール、サイトマップなどのスケジュールを設定できます。 *crontab*&#x200B;はcron設定です。

*crontab*&#x200B;にAdobe Commerce サービスをインストールする必要があります。または、一部のコア機能（および一部のサードパーティ拡張機能）が正しく機能しません。

crontabを削除してコマンドラインからcronを実行する方法など、cronについて詳しくは、[cronの設定と実行](../../configuration/cli/configure-cron-jobs.md)を参照してください。

## セキュリティ設定と推奨事項

インストール後は、以下をお勧めします。

* ファイルの所有権と権限が[適切に設定されていることを確認してください](../prerequisites/file-system/configure-permissions.md)
* [&#x200B; デフォルトの管理者URI](../tutorials/admin-uri.md)を`admin`から別の場所に変更することを強くお勧めします
* [`X-Frame-Option` HTTP ヘッダー](../../configuration/security/xframe-options.md)が正しく設定されていることを確認してください。
* [&#x200B; テンプレートを保護する](https://developer.adobe.com/commerce/php/development/security/cross-site-scripting)することによって、クロスサイトスクリプティング（XSS）に対する予防策を講じる

GitHub リポジトリ [&#128279;](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository)を複製してインストールした場合は、アプリケーションをデプロイするときに、実稼動環境に必要なファイルとフォルダーのみを含めるようにしてください。 不要なファイルやフォルダーは、セキュリティリスクを引き起こす可能性があります。

## Apache サーバーの書き換えを有効にする

Apache Web サーバーを使用する場合は、ページを適切に表示するためにサーバーの書き換えを有効にする必要があります。 それ以外の場合は、スタイルやその他の問題のないページが表示されます。

[Apache サーバーの書き換えの節](../prerequisites/web-server/apache.md#apache-rewrites-and-htaccess)

## マルチウェブノード環境でのキャッシュ

複数のweb ノードがある場合は、web ノード間に同期がないので、*アプリケーションのデフォルトのファイルキャッシュを使用できません*。 つまり、1つのweb ノードのアクティビティは、そのweb ノードのファイルシステムにのみ書き込まれます。 その後のアクティビティが別のweb ノードで実行された場合、不要なファイルが書き込まれたり、エラーが発生したりする可能性があります。

代わりに、デフォルトキャッシュとページキャッシュの両方に[Redis](../../configuration/cache/config-redis.md)を使用してください。

## サーバー設定

この節では、アプリケーションを実行するサーバーに対して検討すべき設定について簡単に説明します。 これらの設定の中には、アプリケーションに直接関連するものではなく、候補としてのみ提供されるものもあります。

### ログの回転

UNIX `logrotate` ユーティリティを使用すると、大量のログ ファイルを生成するシステムを管理できます。 ログファイルの自動回転、圧縮、削除、郵送が可能になります。 各ログファイルは、毎日、毎週、毎月、またはログファイルが指定されたサイズを超えた場合に処理できます。

詳しくは、次のいずれかを参照してください。

* [方法：10の例を含む究極のログ回転コマンドのチュートリアル](https://www.thegeekstuff.com/2010/07/logrotate-examples)
* [Stack Exchange](https://unix.stackexchange.com/questions/85662/how-to-properly-automatically-manually-rotate-log-files-for-production-rails-app)
* [`logrotate`のman ページ](https://linuxconfig.org/logrotate-8-manual-page)

>[!AVAILABILITY]
>
>Adobe Commerce on Cloud Infrastructure プロジェクトには、次の可用性に関する情報が適用されます。
>
>* スターター環境にはログのローテーションがありません。
>
>* Pro統合環境では、ログローテーションを設定できません。 カスタムソリューション/スクリプトを実装し、必要に応じてスクリプトを実行するように[cron](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/configure/app/properties/crons-property)を設定する必要があります。

### 様々なサービスが通信できるようにiptables ルールを設定します

1台のサーバーまたは複数のサーバーがある場合でも、サービスが通信できるようにするには、ファイアウォールでポートを開く必要があります。 例えば、Solr検索エンジンをAdobe Commerceで使用する場合は、Web サーバーと通信できるようにSolr検索エンジンを有効にする必要があります。 複数のweb ノードがある場合は、それらのノードが互いに通信できるようにする必要があります。

詳細：

* Ubuntu: [Ubuntu ドキュメント ページ &#x200B;](https://help.ubuntu.com/community/IptablesHowTo)。
* CentOS: [CentOS ハウツー](https://wiki.centos.org/HowTos%282f%29Network%282f%29IPTables.html)。

### セキュリティ強化Linux （SELinux）ルール

SELinuxを使用するかどうかに関する推奨事項はありませんが、使用する場合は、iptablesの設定と同様に、サービスを設定して相互に通信する必要があります。

詳細：

* Ubuntu: [Debian ハンドブック &#x200B;](https://debian-handbook.info/browse/stable/sect.selinux.html)
* CentOS: [CentOS wiki](https://wiki.centos.org/HowTos/SELinux)

### 電子メールサーバーの設定

Adobe Commerceには電子メールサーバーが必要です。 特定のサーバーはお勧めしませんが、次のいずれかを試すことができます。

* CentOSのポストフィックス （[Digital Ocean tutorial](https://www.digitalocean.com/community/tutorials/how-to-install-postfix-on-centos-6)、[CentOS ドキュメント &#x200B;](https://www.centos.org)）
* UbuntuのPostfix （[Digital Ocean tutorial](https://www.digitalocean.com/community/tutorials/how-to-install-and-setup-postfix-on-ubuntu-14-04)、[Ubuntu ドキュメント &#x200B;](https://help.ubuntu.com/community/MailServer)）

### 検索エンジンを調整してパフォーマンスを向上させます。

2.4.0以降のすべてのインストールには、ElasticsearchまたはOpenSearchが必要です。

* [検索エンジンのインストールと設定](../../configuration/search/overview-search.md)

### メッセージキューの設定

バージョン 2.3.0以降、Adobe Commerceにはメッセージキュー機能が含まれています。 以前のバージョンでは、Adobe Commerceでのみ使用できます。

* [[!DNL RabbitMQ]](../../configuration/queues/message-queue-framework.md)

## Adobe Commerceの設定のみ

Adobe Commerceを使用する場合にのみ、次の設定を行うことができます。

* [チェックアウト、注文管理、その他のデータベーステーブルのデータベースの分割](../../configuration/storage/multi-master.md)
