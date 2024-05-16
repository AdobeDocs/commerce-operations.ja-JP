---
title: 必要システム構成
description: このリファレンスを使用して、Adobe Commerce リリースでテストされた必須のソフトウェア依存関係を特定します。
exl-id: 008c9edc-7d72-403c-847f-0e3b77bbb197
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '728'
ht-degree: 0%

---

# 必要システム構成

Adobe Commerceでテストしたソフトウェアの依存関係とサービスの概要を次に示します。

クラウドインフラストラクチャ上のCommerceの依存関係には、いくつかの違いがあります。 クラウドインフラストラクチャー上のAdobe Commerceのサービスのバージョンと互換性のサポートは、テストしてホストされるクラウド環境にデプロイしたサービスによって決まり、Adobe Commerceのオンプレミスデプロイメントでサポートされているバージョンとは異なる場合があります。 例えば、オンプレミスデプロイメントではElasticsearch 7.17 がCommerce 2.4.4 でサポートされていますが、Cloud Infrastructure 上のCommerce 2.4.4 では OpenSearch 1.2 がサポートされています。

次の表は、特定のAdobe Commerce リリースでAdobeがテストした、サードパーティ製ソフトウェアの依存関係のバージョンを示しています。

Adobeでは、次の表に示すシステム要件の組み合わせのみをサポートしています。 例えば、2.4.5 は MariaDB 10.4 で完全にテストされています。Adobeでは、2.4.5 にアップグレードする前に MariaDB 10.4 にアップグレードすることをお勧めします。

>[!BEGINTABS]

>[!TAB クラウド上のCommerce]

この [Commerce on Cloud テンプレート](https://github.com/magento/magento-cloud) は、特定のCommerce バージョンと互換性のあるサービスのデフォルト設定を提供します。

{{$include /help/_includes/templated/cloud-requirements-table.md}}

サービスとバージョンの定義： [この `services.yaml` ファイル](https://github.com/magento/magento-cloud/blob/master/.magento/services.yaml). クラウドインフラストラクチャー上のCommerce 2.4.6 のデフォルトのサービス設定は、次のとおりです。

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

参照： [サービスの設定](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/services-yaml.html) が含まれる _クラウドインフラストラクチャー上の Commerce_ ガイド。

>[!TAB Commerce オンプレミス]

{{$include /help/_includes/templated/system-requirements-table.md}}

>[!ENDTABS]

## PHP 設定

PHP の設定には、以下のような設定があります。 `memory_limit` の設定。Adobe Commerceを使用する際によく発生する問題を回避できます。 参照： [必要な PHP 設定](prerequisites/php-settings.md).

クラウド設定のガイダンスについては、を参照してください [PHP 設定](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/php-settings.html) が含まれる _クラウドインフラストラクチャー上の Commerce_ ガイド。

### PHP OPcache

次のことを確認することをお勧めします [PHP OPcache](https://www.php.net/manual/en/intro.opcache.php) は、パフォーマンス上の理由から有効になっています。 OPcache は多くの PHP ディストリビューションで有効になっています。 この `opcache` 拡張機能は、クラウドインフラストラクチャー上のCommerceにデフォルトでインストールされます。

オンプレミスの場合は、PHP OPcache がインストールされていることを確認してください。 [PHP 設定](prerequisites/php-settings.md). パフォーマンス設定に関する具体的なガイダンスについては、次のソフトウェア推奨事項を参照してください [PHP 設定](https://experienceleague.adobe.com/docs/commerce-operations/performance-best-practices/software.html#php-settings) が含まれる _パフォーマンスのベストプラクティス_ ガイド。

OPcache を個別にインストールする必要がある場合は、 [PHP OPcache ドキュメント](https://www.php.net/manual/en/opcache.setup.php).

### PHP プロセスコントロール

{{php-process-control}}

### PHPUnit

PHPUnit v9 （コマンドラインツールとして）。

### PHP 拡張機能

この [PHP のインストール](prerequisites/php-settings.md) これらの拡張機能をインストールする手順を含めます。

>[!TIP]
>
>クラウドインフラストラクチャーの PHP 拡張機能については、を参照してください。 [PHP 拡張モジュールを有効にする](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/php-settings.html#enable-extensions) が含まれる _クラウドインフラストラクチャー上の Commerce_ ガイド。

>[!BEGINTABS]

>[!TAB クラウド上のCommerce]

次の表に、Cloud Platform にAdobe Commerceをデプロイする際にサポートされる PHP 拡張機能を示します。

{{$include /help/_includes/templated/php-extensions-cloud.md}}

>[!TAB Commerce オンプレミス]

{{$include /help/_includes/templated/php-extensions.md}}

こちらを参照してください [php の公式ドキュメント](https://www.php.net/manual/en/extensions.php) （インストールの詳細）。

>[!ENDTABS]

## その他

このセクションでは、他のすべてのタイプの必須およびオプション ソフトウェアのサポートと互換性について説明します。

>[!NOTE]
>
>Adobe Commerceの最新の 2.4.x パッチリリースには、次の要件が適用されます。 該当する場合は、クラウドインフラストラクチャー上のCommerceに関するガイダンスを提供します。

### ブラウザー

ストアフロントおよび管理者：

- Microsoft Edge （最新および以前のメジャーバージョン）
- Firefox （最新および以前のメジャーバージョン、あらゆるオペレーティングシステム）
- Chrome （最新および以前のメジャーバージョン、任意のオペレーティングシステム）
- Safari （最新および以前のメジャーバージョン、macOSのみ）
- iOS用 Safari （ストアフロント用の最新および以前のメジャーバージョン）
- Android 版 Chrome （ストアフロント用の最新および以前のメジャーバージョン）

### メールサーバー

メール転送エージェント（MTA）または SMTP サーバー。 クラウドインフラストラクチャー上のCommerceでは次を使用します [SendGrid メールサービス](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/sendgrid.html).

### メモリ

Commerce Marketplaceや他のソースから入手したアプリケーションや拡張機能をアップグレードするには、最大 2 GB の RAM が必要になる場合があります。 2 GB 未満の RAM を搭載したシステムを使用する場合は、 [ファイルをスワップ](https://support.magento.com/hc/en-us/articles/360032980432)そうしないと、アップグレードが失敗する可能性があります。

### オペレーティングシステム （Linux x86 ～ 64）

Linux ディストリビューション（RedHat Enterprise Linux （RHEL）、CentOS、Ubuntu、Debian など）。 Microsoft Windows とmacOSはサポートされていません。

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
- Transport Layer Security （TLS）要件 – PayPal および `repo.magento.com` どちらも TLS 1.2 以降が必要です。

クラウドインフラストラクチャー上のCommerceについては、以下を参照してください。 [Fastly 設定](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html) が含まれる _クラウドインフラストラクチャー上の Commerce_ ガイド。

### Xdebug

Adobe Commerceの場合は、を使用します [php_xdebug 2.5.x](https://xdebug.org/download) またはそれ以降（開発環境のみ。パフォーマンスに悪影響を与える可能性があります）。

Cloud 上のAdobe Commerceについては、を参照してください。 [Xdebug の設定](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/debug.html) が含まれる _クラウドインフラストラクチャー上の Commerce_ ガイド。

>[!NOTE]
>
>に既知の問題があります `xdebug` これは、Adobe Commerceのインストールや、インストール後のストアフロントまたは管理者へのアクセスに影響を与える可能性があります。 参照： [～に影響を及ぼす既知の問題 `xdebug` インストール](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/known-issues-that-affect-installation.html) が含まれる _コマースサポートのナレッジベース_.
