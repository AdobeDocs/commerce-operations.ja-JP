---
title: 必要システム構成
description: Adobe Commerceのソフトウェアの依存関係と必要システム構成について説明します。 デプロイメント環境との互換性については、テスト済みの設定を参照してください。
exl-id: 008c9edc-7d72-403c-847f-0e3b77bbb197
source-git-commit: fdd98cea53f1a060b8b56268250b463c74abaaa1
workflow-type: tm+mt
source-wordcount: '1200'
ht-degree: 0%

---

# 必要システム構成

次に、Adobe Commerce用にテストされたソフトウェアの依存関係とサービスの概要を示します。

Commerce on Cloudの依存関係にはいくつかの違いがあります。 Adobe Commerce on Cloudのサービスバージョンと互換性のサポートは、テスト済みのサービスによって決定され、ホストされたクラウド環境にデプロイされます。また、Adobe Commerce オンプレミスのデプロイメントでサポートされているバージョンと異なる場合があります。

>[!NOTE]
>
>必要システム構成の表は、明示的にラベル付けされたベータ版または早期アクセス版を含む、対象となる特定のAdobe Commerce バージョンを示します。 Adobe Commerceの最新の公開版について詳しくは、[ リリースノート ](../release/release-notes/overview.md)を参照してください。
>
>お使いのCommerceのバージョンとサービスのバージョンが一致しない場合、サポート対象の環境では再現できない動作が生じる可能性があります。 このような場合、サポートは、報告された動作を調査、トラブルシューティング、または検証する前に、サポート対象の設定（例えば、サービスバージョンのアップグレードやダウングレード）に環境を調整することを要求する場合があります。 バージョンが調整されると、サポートは調査を進めることができます。

次の表は、Adobeが特定のAdobe Commerce リリースでテストしたサードパーティソフトウェアの依存関係のバージョンを示しています。

Adobeでは、次の表で説明する必要システム構成の組み合わせのみがサポートされます。 例えば、2.4.9はMariaDB 12.3で完全にテストされています。 Adobeでは、2.4.9にアップグレードする前にMariaDB 12.3にアップグレードすることをお勧めします。

>[!BEGINTABS]

>[!TAB  クラウド上のCommerce]

[Commerce on Cloud テンプレート ](https://github.com/magento/magento-cloud)は、特定のCommerce バージョンと互換性のあるサービスのデフォルト設定を提供します。

{{$include /help/_includes/templated/cloud-requirements-table.md}}

既定の設定では、サービスとバージョンは[`services.yaml` ファイル ](https://github.com/magento/magento-cloud/blob/master/.magento/services.yaml)で定義されます。
詳しくは、*Commerce on Cloud Infrastructure* ガイドの[Configure services](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/service/services-yaml)を参照してください。

>[!TAB Commerce オンプレミス ]

{{$include /help/_includes/templated/system-requirements-table.md}}

**MySQL 8.0は2026年4月30日にサポート終了（EOS）に達しました。**
この日付に続いて、Adobe Commerce 2.4.7、2.4.6、2.4.5、および2.4.4では互換性が提供されません。
mysql 8.0以降にリリースされたMySQL バージョンをサポートします。 Adobeでは
このAdobeの新しいMySQL メジャーバージョンの検証またはサポートの提供
Commerce リリースライン。
バージョン 2.4.7、2.4.6、2.4.5、2.4.4を実行しているすべてのAdobe Commerce オンプレミスのお客様は、以下の点に強く同意します。
データベースサーバーを互換性のあるMariaDB バージョンに移行することをお勧めします。

**Elasticsearch 7.17は、2026年1月15日にサポート終了（EOS）に達しました。**
この日付に続いて、Adobe Commerce 2.4.6、2.4.5、および2.4.4では互換性が提供されません。
Elasticsearch 7以降にリリースされたElasticsearchのバージョンをサポートします。 Adobeでは
このAdobeの新しいElasticsearch メジャーバージョンの検証またはサポートの提供
Commerce リリースライン。
バージョン 2.4.6、2.4.5、2.4.4を実行しているすべてのAdobe Commerce オンプレミスのお客様は、以下の点に強く同意します。
検索インフラストラクチャを互換性のあるOpenSearch バージョンに移行することをお勧めします。

>[!ENDTABS]

>[!AVAILABILITY]
>
><sup>1</sup> MariaDB 12.3とAdobe Commerce 2.4.9の互換性は、5月から6月の期間に予定されているMariaDB 12.3の正式リリース後に確定されます。

## PHP設定

Adobe Commerceを使用する際の一般的な問題を回避するのに役立つ`memory_limit`設定など、PHPの特定の設定があります。 [必要なPHP設定](prerequisites/php-settings.md)を参照してください。

クラウド設定ガイダンスについては、*Commerce on Cloud Infrastructure* ガイドの[PHP settings](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/app/php-settings)を参照してください。

### PHP OPcache

Adobeでは、[PHP OPcache](https://www.php.net/manual/en/book.opcache.php)がパフォーマンス上の理由から有効になっていることを確認することをお勧めします。 OPcacheは多くのPHP ディストリビューションで有効になっています。

- **Cloud インフラストラクチャのデプロイメント**&#x200B;上のAdobe Commerceの場合、`opcache`拡張機能がデフォルトでインストールされます。
- **Adobe Commerce オンプレミス デプロイメントの場合：**
   - [PHP OPcache拡張機能がインストールされていることを確認します](prerequisites/php-settings.md#verify-php-is-installed)。
   - パフォーマンス設定に関する具体的なガイダンスについては、*パフォーマンスのベストプラクティス* ガイドの[PHP設定](../performance/software.md#php-settings)に関するソフトウェアの推奨事項を参照してください。


OPcacheを個別にインストールする必要がある場合は、[PHP OPcache ドキュメント ](https://www.php.net/manual/en/opcache.setup.php)を参照してください。

### PHP プロセス制御

{{php-process-control}}

### PHPUnit

サポートされているPHPUnit メジャーバージョンは、Adobe Commerce リリースによって異なります。 Adobeは、PHPUnit 12では2.4.9、PHPUnit 10では2.4.8-p5、PHPUnit 9では2.4.7-p10～2.4.4-p18をテストします。 リリースのAdobe テスト済み設定に一致するメジャーバージョンで、PHPUnitをコマンドラインツールとしてインストールします。

### PHP拡張機能

[PHPのインストール手順](prerequisites/php-settings.md)には、これらの拡張機能をインストールするための手順が含まれています。

>[!TIP]
>
>クラウドインフラストラクチャのPHP拡張機能については、_Commerce on Cloud Infrastructure_ ガイドの[PHP拡張機能の有効化](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/app/php-settings#enable-extensions)を参照してください。

>[!BEGINTABS]

>[!TAB  クラウド上のCommerce]

次の表は、Adobe CommerceをCloud Platformにデプロイする際にサポートされるPHP拡張機能を示しています。

{{$include /help/_includes/templated/php-extensions-cloud.md}}

>[!TAB Commerce オンプレミス ]

{{$include /help/_includes/templated/php-extensions.md}}

インストールの詳細については、[公式PHP ドキュメント ](https://www.php.net/manual/en/extensions.php)を参照してください。

>[!ENDTABS]

## その他のソフトウェア要件

この節では、その他のすべての種類の必須および任意のソフトウェアのサポートと互換性について説明します。

>[!NOTE]
>
>Adobe Commerceの最新の2.4.x パッチリリースには、次の要件が適用されます。 必要に応じて、Commerce on Cloud インフラストラクチャガイダンスが提供されます。

### ブラウザー

ストアフロントと管理者：

- Microsoft Edge（最新および以前のメジャーバージョン）
- Firefox （すべてのオペレーティングシステムの最新かつ以前のメジャーバージョン）
- Chrome（任意のオペレーティングシステムの最新および以前のメジャーバージョン）
- Safari （macOSの最新および以前のメジャーバージョンのみ）
- Safari for iOS（ストアフロントの最新および以前のメジャーバージョン）
- Chrome for Android（ストアフロントの最新および以前のメジャーバージョン）

### メールサーバー

Mail Transfer Agent （MTA）またはSMTP サーバー。 Commerce on Cloud インフラストラクチャでは、[SendGrid メールサービス ](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/project/sendgrid)を使用しています。

### メモリ

Commerce Marketplaceやその他のソースから取得したアプリケーションや拡張機能をアップグレードするには、最大2 GBのRAMが必要になる場合があります。 2 GB未満のRAMを搭載したシステムを使用している場合は、[ スワップファイル ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/installation-and-upgrade/out-of-memory-error-during-install-or-upgrade)を作成します。 そうしないと、アップグレードが失敗する可能性があります。

### オペレーティングシステム（Linux x86-64）

Red Hat Enterprise Linux （RHEL）、CentOS、Ubuntu、DebianなどのLinux ディストリビューション。

Microsoft WindowsとmacOSは&#x200B;**サポートされていません**。

Adobe Commerceでは、一部の操作に次のシステムツールが必要です。

- [[!DNL bash]](https://www.gnu.org/software/bash/)
- [[!DNL gzip]](https://www.gnu.org/software/gzip/manual/gzip.html)
- [[!DNL lsof]](https://lsof.readthedocs.io/en/stable/manpage/)
- [[!DNL mysql]](https://www.mysql.com/)
- [[!DNL mysqldump]](https://dev.mysql.com/doc/refman/8.4/en/mysqldump.html)
- [[!DNL nice]](https://www.gnu.org/s/coreutils/manual/html_node/nice-invocation.html)
- [[!DNL php]](https://www.php.net/)
- [[!DNL sed]](https://www.gnu.org/software/sed/manual/sed.html)
- [[!DNL tar]](https://www.gnu.org/software/tar/manual/tar.html)

### SSL

- HTTPSには有効なセキュリティ証明書が必要です。
- 自己署名SSL証明書はサポートされていません。
- Transport Layer Security （TLS）要件 – PayPalおよび`repo.magento.com`は、どちらもTLS 1.2以降を必要とします。

Cloud Infrastructure上のCommerceについては、*Cloud Infrastructure上のCommerce* ガイドの[Fastly設定](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/cdn/setup-fastly/fastly-configuration)を参照してください。

### Xdebug

Adobe Commerceの場合は、[php_xdebug 2.5.x](https://xdebug.org/download)以降を使用してください（開発環境のみ、パフォーマンスに悪影響を与える可能性があります）。

Adobe Commerce on Cloudについては、*Commerce on Cloud Infrastructure* ガイドの[Configure Xdebug](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/test/debug)を参照してください。

>[!NOTE]
>
>Adobe Commerceのインストールまたはインストール後のストアフロントまたは管理者へのアクセスに影響を与える可能性がある`xdebug`に既知の問題があります。 _Commerce サポート サポート ナレッジベース_&#x200B;の「`xdebug` インストール ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/known-issues-that-affect-installation)」に影響する[既知の問題を参照してください。

<!-- Last updated from includes: 2026-05-11 20:38:54 -->
