---
title: 必要システム構成
description: このリファレンスを使用して、Adobe CommerceとMagento Open Sourceのリリースでテストされた、必要なソフトウェアの依存関係を特定します。
exl-id: 008c9edc-7d72-403c-847f-0e3b77bbb197
source-git-commit: 56052a5777b8719d5a9257d0c48e5640a6812a5f
workflow-type: tm+mt
source-wordcount: '761'
ht-degree: 0%

---

# 必要システム構成

次に、Adobe CommerceとMagento Open Sourceでテストされたソフトウェアの依存関係とサービスの概要を示します。

Commerce の Cloud インフラストラクチャへの依存関係には、いくつかの違いがあります。 クラウドインフラストラクチャ上のAdobe Commerceのサービスバージョンと互換性のサポートは、ホストクラウド環境にテストおよびデプロイされたサービスによって決まり、Adobe Commerceオンプレミスデプロイメントでサポートされるバージョンとは異なる場合があります。 例えば、オンプレミスデプロイメントではElasticsearch7.17 が Commerce 2.4.4 でサポートされていますが、Cloud インフラストラクチャでは OpenSearch 1.2 が Commerce 2.4.4 でサポートされています。

次の表に、特定のAdobe CommerceおよびMagento Open SourceリリースでAdobeがテストしたサードパーティソフトウェアの依存関係のバージョンを示します。

Adobeは、次の表に示す必要システム構成の組み合わせのみをサポートします。 例えば、MariaDB 10.4 で 2.4.5 を完全にテストしたとします。Adobeでは、2.4.5 にアップグレードする前に MariaDB 10.4 にアップグレードすることをお勧めします。

>[!BEGINTABS]

>[!TAB Commerce on Cloud]

The [クラウド上のコマーステンプレート](https://github.com/magento/magento-cloud) は、特定のコマースバージョンと互換性のあるサービスのデフォルト設定を提供します。

{{$include /help/_includes/templated/cloud-requirements-table.md}}

サービスとバージョンは、で定義されています。 [の `services.yaml` ファイル](https://github.com/magento/magento-cloud/blob/master/.magento/services.yaml). クラウドインフラストラクチャ上の Commerce 2.4.6 のデフォルトのサービス設定は次のとおりです。

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

詳しくは、 [サービスの設定](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/services-yaml.html) （内） _クラウドインフラストラクチャ上のコマース_ ガイド。

>[!TAB オンプレミスのコマース]

{{$include /help/_includes/templated/system-requirements-table.md}}

>[!ENDTABS]

## PHP 設定

PHP の設定には、 `memory_limit` 設定を使用することで、Adobe CommerceとMagento Open Sourceの使用時に発生する一般的な問題を回避できます。 詳しくは、 [必要な PHP 設定](prerequisites/php-settings.md).

クラウド設定のガイダンスについては、 [PHP 設定](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/php-settings.html) （内） _クラウドインフラストラクチャ上のコマース_ ガイド。

### PHP OPcache

次の点を確認することをお勧めします。 [PHP OPcache](https://www.php.net/manual/en/intro.opcache.php) は、パフォーマンス上の理由から有効になっています。 OPcache は多くの PHP ディストリビューションで有効になっています。 The `opcache` 拡張機能は、デフォルトで Commerce on Cloud インフラストラクチャにインストールされます。

オンプレミスの場合は、PHP OPcache がインストールされていることを確認します。 [PHP 設定](prerequisites/php-settings.md). また、パフォーマンス設定に関する具体的なガイダンスについては、 [PHP 設定](https://experienceleague.adobe.com/docs/commerce-operations/performance-best-practices/software.html#php-settings) （内） _パフォーマンスのベストプラクティス_ ガイド。

OPcache を個別にインストールする必要がある場合は、 [PHP OPcache のドキュメント](https://www.php.net/manual/en/opcache.setup.php).

### PHP プロセス制御

{{php-process-control}}

### PHPUnit

PHPUnit （コマンドラインツールとして） 9.0.0

### PHP 拡張機能

The [PHP のインストール手順](prerequisites/php-settings.md) には、これらの拡張機能をインストールする手順が含まれています。

>[!TIP]
>
>クラウドインフラストラクチャの PHP 拡張については、 [PHP 拡張機能を有効にする](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/php-settings.html#enable-extensions) （内） _クラウドインフラストラクチャ上のコマース_ ガイド。

>[!BEGINTABS]

>[!TAB Commerce on Cloud]

次の表に、クラウドプラットフォームにAdobe Commerceをデプロイする際にサポートされる PHP 拡張を示します。

{{$include /help/_includes/templated/php-extensions-cloud.md}}

>[!TAB オンプレミスのコマース]

{{$include /help/_includes/templated/php-extensions.md}}

参照： [公式の PHP ドキュメント](https://www.php.net/manual/en/extensions.php) インストールの詳細については、を参照してください。

>[!ENDTABS]

## その他

このセクションでは、その他のすべての種類の必須およびオプションソフトウェアのサポートと互換性について説明します。

>[!NOTE]
>
>以下の要件は、Adobe CommerceとMagento Open Sourceの最新 2.4.x パッチリリースに適用されます。 関連する場合、Commerce on Cloud インフラストラクチャガイダンスが提供されます。

### ブラウザー

ストアフロントと管理：

- Microsoft Edge（最新および以前のメジャーバージョン）
- Firefox（最新および以前のメジャーバージョン、任意のオペレーティングシステム）
- Chrome（最新および以前のメジャーバージョン、任意のオペレーティングシステム）
- Safari( 最新および以前のメジャーバージョン。macOSのみ )
- iOS用 Safari（ストアフロント用の最新および以前のメジャーバージョン）
- Android 用 Chrome（ストアフロント用の最新および以前のメジャーバージョン）

### メールサーバー

メール転送エージェント (MTA) または SMTP サーバー。 Commerce on Cloud インフラストラクチャでは、 [SendGrid 電子メールサービス](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/sendgrid.html).

### メモリ

Commerce Marketplaceやその他のソースから入手したアプリケーションや拡張機能をアップグレードする場合、最大 2 GB の RAM が必要になる場合があります。 RAM が 2 GB 未満のシステムを使用している場合は、 [スワップファイル](https://support.magento.com/hc/en-us/articles/360032980432)そうしないと、アップグレードが失敗する場合があります。

### オペレーティングシステム (Linux x86-64)

RedHat Enterprise Linux(RHEL)、CentOS、Ubuntu、Debian などの Linux ディストリビューション。 Microsoft Windows とmacOSはサポートされていません。

Adobe CommerceおよびMagento Open Sourceでは、一部の操作に次のシステムツールが必要です。

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
- トランスポート層セキュリティ (TLS) の要件 — PayPal および `repo.magento.com` どちらも TLS 1.2 以降が必要です。

クラウドインフラストラクチャ上のコマースについては、 [Fastly 設定](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html) （内） _クラウドインフラストラクチャ上のコマース_ ガイド。

### Xdebug

Adobe CommerceとMagento Open Sourceの場合は、 [php_xdebug 2.5.x](https://xdebug.org/download) または後で（開発環境のみ。パフォーマンスに悪影響を与える可能性があります）。

Adobe Commerce on Cloud の場合は、 [Xdebug の設定](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/debug.html) （内） _クラウドインフラストラクチャ上のコマース_ ガイド。

>[!NOTE]
>
>次の既知の問題があります： `xdebug` これは、Adobe CommerceまたはMagento Open Sourceのインストールや、インストール後のストアフロントまたは Admin へのアクセスに影響を与える可能性があります。 詳しくは、 [次に影響する既知の問題： `xdebug` インストール](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/known-issues-that-affect-installation.html) （内） _コマースサポートナレッジベース_.
