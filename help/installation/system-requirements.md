---
title: 必要システム構成
description: Adobe Commerceのソフトウェアの依存関係と必要システム構成について説明します。 デプロイメント環境との互換性については、テスト済みの設定を参照してください。
exl-id: 008c9edc-7d72-403c-847f-0e3b77bbb197
source-git-commit: d9152906a6fbbd765a60e3aeacdbf7cc7527529d
workflow-type: tm+mt
source-wordcount: '1339'
ht-degree: 0%

---

# 必要システム構成

次の情報は、Adobe Commerceでテストされたソフトウェアの依存関係とサービスをまとめたものです。

Commerce on Cloudの依存関係にはいくつかの違いがあります。 Adobe Commerce on Cloudのサービスバージョンと互換性のサポートは、テスト済みのサービスによって決定され、ホストされたクラウド環境にデプロイされます。また、Adobe Commerce オンプレミスのデプロイメントでサポートされているバージョンと異なる場合があります。

>[!IMPORTANT]
>
>必要システム構成テーブルには、ベータ版または早期アクセスとラベル付けされたリリースなど、適用されるAdobe Commerce バージョンが一覧表示されます。
>最新の公開済みCommerce バージョンについては、[&#x200B; リリースノート &#x200B;](../release/release-notes/overview.md)を参照してください。
>
>サービスのバージョンがCommerceのバージョンでサポートされている設定と一致しない場合、動作がAdobeでテストで再現できるものと異なる場合があります。 Adobe サポートは、報告された動作を調査、トラブルシューティング、または検証する前に、サポートされている設定と環境を整合させるよう求める場合があります。 環境を調整した後、Adobe サポートは調査を続行できます。

次の表は、Adobeが特定のAdobe Commerce リリースでテストしたサードパーティソフトウェアの依存関係のバージョンを示しています。

Adobeは、次の表に示すシステム要件の組み合わせのみをサポートします。 Adobeは、リストされた組み合わせと一致しない設定を検証またはサポートしません。 例えば、Adobe Commerce 2.4.9はMariaDB 12.3でテストされています。 2.4.9にアップグレードする前に、MariaDB 12.3にアップグレードします。

## 最新のCommerce リリースバージョンの必要システム構成

次の表に、サポートされているすべてのCommerce バージョンの最新リリースの必要システム構成を示します。 Adobeでは、すべてのお客様がこれらのバージョンにアップグレードすることをお勧めします。

>[!BEGINTABS]

>[!TAB  クラウド上のCommerce]

[Commerce on Cloud テンプレート &#x200B;](https://github.com/magento/magento-cloud)は、各リリースラインの最新のCommerce バージョンと互換性のあるサービスのデフォルト設定を提供します。

{{$include /help/_includes/templated/cloud-requirements-table.md}}

既定の設定では、サービスとバージョンは[`services.yaml` ファイル &#x200B;](https://github.com/magento/magento-cloud/blob/master/.magento/services.yaml)で定義されます。
詳しくは、「*Commerce on Cloud Infrastructure* ガイドの[Configure services](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/configure/service/services-yaml)」を参照してください。

>[!TAB Commerce オンプレミス ]

{{$include /help/_includes/templated/system-requirements-table.md}}

**MySQL 8.0は2026年4月30日にサポート終了（EOS）に達しました。**
この日付に続いて、Adobe Commerce 2.4.7、2.4.6、2.4.5、および2.4.4では互換性が提供されません。
mysql 8.0以降にリリースされたMySQL バージョンをサポートします。Adobeでは
このAdobeの新しいMySQL メジャーバージョンの検証またはサポートの提供
Commerce リリースライン。
バージョン 2.4.7、2.4.6、2.4.5、2.4.4を実行しているすべてのAdobe Commerce オンプレミスのお客様は、以下の点に強く同意します。
データベースサーバーを互換性のあるMariaDB バージョンに移行することをお勧めします。

Adobe Commerce on Cloudのお客様は、サポートされているバージョンにプラットフォームの依存関係を維持する必要があります。 ライフサイクルポリシーの[Platform依存関係](../release/lifecycle-policy.md#platform-dependencies)を参照してください。

**Elasticsearch 7.17は、2026年1月15日にサポート終了（EOS）に達しました。**
この日付に続いて、Adobe Commerce 2.4.6、2.4.5、および2.4.4では互換性が提供されません。
Elasticsearch 7以降にリリースされたElasticsearchのバージョンをサポートします。Adobeでは
このAdobeの新しいElasticsearch メジャーバージョンの検証またはサポートの提供
Commerce リリースライン。
バージョン 2.4.6、2.4.5、2.4.4を実行しているすべてのAdobe Commerce オンプレミスのお客様は、以下の点に強く同意します。
検索インフラストラクチャを互換性のあるOpenSearch バージョンに移行することをお勧めします。

>[!ENDTABS]

## 以前のCommerce リリースの必要システム構成

次の表に、拡張サポートを含むAdobe Commerce リリースの必要システム構成を示します。 これらの表は、参照目的でのみ提供されます。 Adobeでは、サポートされていないバージョンのソフトウェアの依存関係を使用することはお勧めしません。サポートでは、報告された動作を調査、トラブルシューティング、検証する前に、サポートされている構成に環境を合わせる必要があります。

>[!NOTE]
>
>Adobe Commerce 2.4.6は[延長サポート &#x200B;](../release/lifecycle-policy.md#extended-support)から&#x200B;**2027年8月30日**&#x200B;までで、その後[&#x200B; セキュリティのみの移行期間](../release/lifecycle-policy.md#security-only-transitional-period) ～ **2028年5月31日**&#x200B;が続きます。 これらの規定は、Adobe Commerceのお客様のみが利用できます。 MySQLなどのサードパーティの依存関係のサポートは拡張されません。
>
>Adobe Commerce on Cloudを実行する場合は、**2028年6月1日** [&#x200B; バージョンのアップグレード実施日](../release/version-upgrade-enforcement-policy.md)より前に、サポートされているリリースにアップグレードするか、[!DNL Adobe Commerce as a Cloud Service]に移行する必要があります。 ライフサイクルの全期間については、[&#x200B; サポート終了日](../release/lifecycle-policy.md#end-of-support-dates)の表を参照してください。
>
>この記事の長さを最小限に抑えるために、表を折りたたみます。 ヘッダーを選択して展開します。

+++以前のリリースの要件

>[!BEGINTABS]

>[!TAB  クラウド上のCommerce]

[Commerce on Cloud テンプレート &#x200B;](https://github.com/magento/magento-cloud)は、特定のCommerce バージョンと互換性のあるサービスのデフォルト設定を提供します。

{{$include /help/_includes/templated/cloud-requirements-table-old-releases.md}}

既定の設定では、サービスとバージョンは[`services.yaml` ファイル &#x200B;](https://github.com/magento/magento-cloud/blob/master/.magento/services.yaml)で定義されます。
詳しくは、「*Commerce on Cloud Infrastructure* ガイドの[Configure services](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/configure/service/services-yaml)」を参照してください。

>[!TAB Commerce オンプレミス ]

{{$include /help/_includes/templated/system-requirements-table-old-releases.md}}

**MySQL 8.0は2026年4月30日にサポート終了（EOS）に達しました。**
この日付に続いて、Adobe Commerce 2.4.7、2.4.6、2.4.5、および2.4.4では互換性が提供されません。
mysql 8.0以降にリリースされたMySQL バージョンをサポートします。Adobeでは
このAdobeの新しいMySQL メジャーバージョンの検証またはサポートの提供
Commerce リリースライン。
バージョン 2.4.7、2.4.6、2.4.5、2.4.4を実行しているすべてのAdobe Commerce オンプレミスのお客様は、以下の点に強く同意します。
データベースサーバーを互換性のあるMariaDB バージョンに移行することをお勧めします。

Adobe Commerce on Cloudのお客様は、サポートされているバージョンにプラットフォームの依存関係を維持する必要があります。 ライフサイクルポリシーの[Platform依存関係](../release/lifecycle-policy.md#platform-dependencies)を参照してください。

**Elasticsearch 7.17は、2026年1月15日にサポート終了（EOS）に達しました。**
この日付に続いて、Adobe Commerce 2.4.6、2.4.5、および2.4.4では互換性が提供されません。
Elasticsearch 7以降にリリースされたElasticsearchのバージョンをサポートします。Adobeでは
このAdobeの新しいElasticsearch メジャーバージョンの検証またはサポートの提供
Commerce リリースライン。
バージョン 2.4.6、2.4.5、2.4.4を実行しているすべてのAdobe Commerce オンプレミスのお客様は、以下の点に強く同意します。
検索インフラストラクチャを互換性のあるOpenSearch バージョンに移行することをお勧めします。

>[!ENDTABS]

+++

## PHP設定

Adobe Commerceを使用する際の一般的な問題を回避するのに役立つ`memory_limit`設定など、PHPの特定の設定があります。 [必要なPHP設定](prerequisites/php-settings.md)を参照してください。

クラウド設定ガイダンスについては、*Commerce on Cloud Infrastructure* ガイドの[PHP settings](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/configure/app/php-settings)を参照してください。

### PHP OPcache

Adobeでは、[PHP OPcache](https://www.php.net/manual/en/book.opcache.php)がパフォーマンス上の理由から有効になっていることを確認することをお勧めします。 OPcacheは多くのPHP ディストリビューションで有効になっています。

- **Cloud インフラストラクチャのデプロイメント**&#x200B;上のAdobe Commerceの場合、`opcache`拡張機能がデフォルトでインストールされます。
- **Adobe Commerce オンプレミス デプロイメントの場合：**
  - [PHP OPcache拡張機能がインストールされていることを確認します](prerequisites/php-settings.md#verify-php-is-installed)。
  - パフォーマンス設定に関する具体的なガイダンスについては、*パフォーマンスのベストプラクティス* ガイドの[PHP設定](../performance/software.md#php-settings)に関するソフトウェアの推奨事項を参照してください。


OPcacheを個別にインストールする必要がある場合は、[PHP OPcache ドキュメント &#x200B;](https://www.php.net/manual/en/opcache.setup.php)を参照してください。

### PHP プロセス制御

{{php-process-control}}

### PHPUnit

サポートされているPHPUnit メジャーバージョンは、Adobe Commerce リリースによって異なります。 Adobeは、PHPUnit 12では2.4.9、PHPUnit 10では2.4.8-p5、PHPUnit 9では2.4.7-p10～2.4.4-p18をテストします。 リリースのAdobe テスト済み設定に一致するメジャーバージョンで、PHPUnitをコマンドラインツールとしてインストールします。

### PHP拡張機能

[PHPのインストール手順](prerequisites/php-settings.md)には、これらの拡張機能をインストールするための手順が含まれています。

>[!TIP]
>
>クラウドインフラストラクチャのPHP拡張機能については、_Commerce on Cloud Infrastructure_ ガイドの[PHP拡張機能の有効化](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/configure/app/php-settings#enable-extensions)を参照してください。

>[!BEGINTABS]

>[!TAB  クラウド上のCommerce]

次の表は、Adobe CommerceをCloud Platformにデプロイする際にサポートされるPHP拡張機能を示しています。

{{$include /help/_includes/templated/php-extensions-cloud.md}}

>[!TAB Commerce オンプレミス ]

{{$include /help/_includes/templated/php-extensions.md}}

インストールの詳細については、[公式PHP ドキュメント &#x200B;](https://www.php.net/manual/en/extensions.php)を参照してください。

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

Mail Transfer Agent （MTA）またはSMTP サーバー。 Commerce on Cloud インフラストラクチャでは、[SendGrid メールサービス &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/project/sendgrid)を使用しています。

### メモリ

Commerce Marketplaceやその他のソースから取得したアプリケーションや拡張機能をアップグレードするには、最大2 GBのRAMが必要になる場合があります。 2 GB未満のRAMを搭載したシステムを使用している場合は、[&#x200B; スワップファイル &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce-knowledge-base/kb/troubleshooting/installation-and-upgrade/out-of-memory-error-during-install-or-upgrade)を作成します。 そうしないと、アップグレードが失敗する可能性があります。

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

Cloud Infrastructure上のCommerceについては、*Cloud Infrastructure上のCommerce* ガイドの[Fastly設定](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/cdn/setup-fastly/fastly-configuration)を参照してください。

### Xdebug

Adobe Commerceの場合は、[php_xdebug 2.5.x](https://xdebug.org/download)以降を使用してください（開発環境のみ、パフォーマンスに悪影響を与える可能性があります）。

Adobe Commerce on Cloudについては、*Commerce on Cloud Infrastructure* ガイドの[Configure Xdebug](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/test/debug)を参照してください。

>[!NOTE]
>
>Adobe Commerceのインストールまたはインストール後のストアフロントまたは管理者へのアクセスに影響を与える可能性がある`xdebug`に既知の問題があります。 _Commerce サポート サポート ナレッジベース_&#x200B;の「`xdebug` インストール [&#128279;](https://experienceleague.adobe.com/ja/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/known-issues-that-affect-installation)」に影響する既知の問題を参照してください。

<!-- Last updated from includes: 2026-07-22 16:57:39 -->

