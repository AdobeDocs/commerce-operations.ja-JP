---
title: 必要システム構成
description: Adobe Commerceのソフトウェアの依存関係とシステム要件について説明します。 テスト済みの設定を確認して、デプロイメント環境との互換性を確保します。
exl-id: 008c9edc-7d72-403c-847f-0e3b77bbb197
source-git-commit: 8b1a202fde89ab05626194aff010111577ef6993
workflow-type: tm+mt
source-wordcount: '818'
ht-degree: 0%

---

# 必要システム構成

Adobe Commerceでテストしたソフトウェアの依存関係とサービスの概要を次に示します。

Commerce on Cloud の依存関係にはいくつかの違いがあります。 Cloud 上のAdobe Commerceのサービスバージョンと互換性のサポートは、テストしてホストされたクラウド環境にデプロイしたサービスによって決まり、Adobe Commerceのオンプレミスデプロイメントでサポートされているバージョンとは異なる場合があります。 例えば、オンプレミスデプロイメントではElasticsearch 7.17 がCommerce 2.4.4 でサポートされていますが、Cloud 上の 2.4.4 Adobe Commerceでは OpenSearch 1 がサポートされています。

>[!NOTE]
>
>システム要件は、Adobe Commerceのリリース版にのみ適用されます。 Betaまたはアーリーアクセス版は含まれません。 Adobe Commerceの最新のリリースバージョンについて詳しくは、[&#x200B; リリースノート &#x200B;](../release/release-notes/overview.md) を参照してください。

次の表は、Adobeが特定のAdobe Commerce リリースでテストした、サードパーティ製ソフトウェアの依存関係のバージョンを示しています。

Adobeは、次の表に示すシステム要件の組み合わせのみをサポートしています。 例えば、2.4.5 は MariaDB 10.4 で完全にテストされています。Adobeでは、2.4.5 にアップグレードする前に MariaDB 10.4 にアップグレードすることをお勧めします。

アップグレードプロセスをスムーズにし、デプロイメントのエラーを防ぐために、Adobeでは、RabbitMQ バージョンを増分的にアップグレードすることをお勧めします。 例えば、バージョン 3.8 から 4.1 にアップグレードする場合は、最初に 3.8 から 3.9 にアップグレードし、次に 3.9 から 3.10 にアップグレードする必要があります。 バージョン 3.13 に達した後にのみ、バージョン 4.1 へのアップグレードを続行する必要があります。

>[!BEGINTABS]

>[!TAB  クラウド上のCommerce]

[Commerce on Cloud テンプレートは &#x200B;](https://github.com/magento/magento-cloud) 特定のCommerce バージョンと互換性のあるサービスのデフォルト設定を提供します。

{{$include /help/_includes/templated/cloud-requirements-table.md}}

サービスとバージョンは [`services.yaml` ファイル &#x200B;](https://github.com/magento/magento-cloud/blob/master/.magento/services.yaml) で定義されます。 クラウドインフラストラクチャー上のCommerce 2.4.6 のデフォルトのサービス設定は、次のとおりです。

```yaml
mysql:
    type: mysql:10.6
    disk: 5120

redis:
    type: redis:7.0

opensearch:
    type: opensearch:2
    disk: 1024
```

クラウドインフラストラクチャー上の [2&rbrace;Commerce](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/services-yaml.html?lang=ja) ガイドの &lbrace; サービスの設定 _を参照してください。_

>[!TAB Commerce オンプレミス ]

{{$include /help/_includes/templated/system-requirements-table.md}}

>[!ENDTABS]

## PHP 設定

PHP には `memory_limit` 設定など特定の設定があり、Adobe Commerceを使用する際の一般的な問題を回避するのに役立ちます。 [&#x200B; 必要な PHP 設定 &#x200B;](prerequisites/php-settings.md) を参照してください。

クラウド設定のガイダンスについては、[Cloud Infrastructure でのCommerce](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/php-settings.html?lang=ja) ガイドの _PHP 設定_ を参照してください。

### PHP OPcache

パフォーマンス上の理由から、[PHP OPcache](https://www.php.net/manual/en/intro.opcache.php) が有効になっていることを確認することをお勧めします。 OPcache は多くの PHP ディストリビューションで有効になっています。 `opcache` 拡張機能は、クラウドインフラストラクチャー上のCommerceにデフォルトでインストールされます。

オンプレミスの場合は、PHP OPcache がインストールされていることを確認します。[PHP 設定 &#x200B;](prerequisites/php-settings.md) を参照してください。 パフォーマンス設定に関する具体的なガイダンスについては、『 [&#x200B; パフォーマンスのベストプラクティス &#x200B;](https://experienceleague.adobe.com/docs/commerce-operations/performance-best-practices/software.html?lang=ja#php-settings) ガイドの _PHP 設定_ に関するソフトウェアの推奨事項を参照してください。

OPcache を個別にインストールする必要がある場合は、[PHP OPcache のドキュメント &#x200B;](https://www.php.net/manual/en/opcache.setup.php) を参照してください。

### PHP プロセスコントロール

{{php-process-control}}

### PHPUnit

PHPUnit v9 （コマンドラインツールとして）。

### PHP 拡張機能

[PHP のインストール手順 &#x200B;](prerequisites/php-settings.md) には、これらの拡張機能をインストールする手順が含まれています。

>[!TIP]
>
>クラウドインフラストラクチャーでの PHP 拡張機能については、[&#x200B; クラウドインフラストラクチャー上のCommerce](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/php-settings.html?lang=ja#enable-extensions) ガイドの _PHP 拡張機能を有効にする_ を参照してください。

>[!BEGINTABS]

>[!TAB  クラウド上のCommerce]

次の表に、Cloud Platform にAdobe Commerceをデプロイする際にサポートされる PHP 拡張機能を示します。

{{$include /help/_includes/templated/php-extensions-cloud.md}}

>[!TAB Commerce オンプレミス ]

{{$include /help/_includes/templated/php-extensions.md}}

インストールの詳細については、[PHP の公式ドキュメント &#x200B;](https://www.php.net/manual/en/extensions.php) を参照してください。

>[!ENDTABS]

## その他

このセクションでは、他のすべてのタイプの必須およびオプション ソフトウェアのサポートと互換性について説明します。

>[!NOTE]
>
>Adobe Commerceの最新の 2.4.x パッチリリースには、次の要件が適用されます。 該当する場合は、クラウドインフラストラクチャー上のCommerceに関するガイダンスを提供します。

### ブラウザー

ストアフロントおよび管理者：

- Microsoft Edge（最新および以前のメジャーバージョン）
- Firefox （最新および以前のメジャーバージョン、あらゆるオペレーティングシステム）
- Chrome（最新および以前のメジャーバージョン、あらゆるオペレーティングシステム）
- Safari （最新および以前のメジャーバージョン、macOSのみ）
- iOS用 Safari （ストアフロント用の最新および以前のメジャーバージョン）
- Android用のChrome（ストアフロント用の最新および以前のメジャーバージョン）

### メールサーバー

メール転送エージェント（MTA）または SMTP サーバー。 クラウドインフラストラクチャー上のCommerceでは、[SendGrid メールサービス &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/sendgrid.html?lang=ja) を使用します。

### メモリ

Commerce Marketplaceやその他のソースから取得したアプリケーションや拡張機能をアップグレードするには、最大 2 GB の RAM が必要になる場合があります。 RAM が 2 GB 未満のシステムを使用している場合は、[&#x200B; スワップファイル &#x200B;](https://support.magento.com/hc/en-us/articles/360032980432) を作成します。そうしないと、アップグレードに失敗する可能性があります。

### オペレーティングシステム （Linux x86 ～ 64）

Linux ディストリビューション（RedHat Enterprise Linux （RHEL）、CentOS、Ubuntu、Debian など）。

Microsoft Windows とmacOSはサポート **対象外** です。

Adobe Commerceには、一部の操作で次のシステムツールが必要です。

- [[!DNL bash]](https://www.gnu.org/software/bash/)
- [[!DNL gzip]](https://www.gzip.org/)
- [[!DNL lsof]](https://linux.die.net/man/8/lsof)
- [[!DNL mysql]](https://www.mysql.com/)
- [[!DNL mysqldump]](https://dev.mysql.com/doc/refman/8.0/en/mysqldump.html)
- [[!DNL nice]](https://linux.die.net/man/1/nice)
- [[!DNL php]](https://www.php.net/)
- [[!DNL sed]](https://www.gnu.org/software/sed/manual/sed.html)
- [[!DNL tar]](https://linux.die.net/man/1/tar)

### SSL

- HTTPS には有効なセキュリティ証明書が必要です。
- 自己署名 SSL 証明書はサポートされていません。
- Transport Layer Security （TLS）要件 – PayPal と `repo.magento.com` の両方で TLS 1.2 以降が必要です。

クラウドインフラストラクチャー上のCommerceについては、[&#x200B; クラウドインフラストラクチャー上のCommerce](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=ja) ガイドの _Fastly 設定_ を参照してください。

### Xdebug

Adobe Commerceの場合は、[php_xdebug 2.5.x](https://xdebug.org/download) 以降を使用します（開発環境のみ。パフォーマンスに悪影響を与える可能性があります）。

Cloud 上のAdobe Commerceについては、[Cloud Infrastructure 上のCommerce](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/debug.html?lang=ja) ガイドの _Xdebug の設定_ を参照してください。

>[!NOTE]
>
>`xdebug` には既知の問題があり、Adobe Commerceのインストールや、インストール後のストアフロントまたは管理者へのアクセスに影響を与える可能性があります。 [3&rbrace;Commerce サポートナレッジベース `xdebug` の &#x200B;](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/known-issues-that-affect-installation.html?lang=ja) インストールに影響を与える既知の問題 _を参照してください。_


<!-- Last updated from includes: 2025-10-09 19:48:53 -->
