---
title: 必要システム構成
description: Adobe Commerceのソフトウェアの依存関係と必要システム構成について説明します。 テスト済みの設定を確認して、デプロイメント環境との互換性を確保します。
exl-id: 008c9edc-7d72-403c-847f-0e3b77bbb197
source-git-commit: 2657c83d5467e603a681521886e80592e3b335aa
workflow-type: tm+mt
source-wordcount: '819'
ht-degree: 0%

---

# 必要システム構成

次に、Adobe Commerce用にテストされたソフトウェアの依存関係とサービスの概要を示します。

Commerce on Cloudの依存関係にはいくつかの違いがあります。 Adobe Commerce on Cloudのサービスバージョンと互換性のサポートは、テスト済みのサービスによって決定され、ホストされたクラウド環境にデプロイされます。また、Adobe Commerce オンプレミスのデプロイメントでサポートされているバージョンと異なる場合があります。 例えば、Elasticsearch 7.17はオンプレミスデプロイメント用のCommerce 2.4.4でサポートされていますが、OpenSearch 1はCloud上の2.4.4 Adobe Commerceでサポートされています。

>[!NOTE]
>
>必要システム構成の表は、明示的にラベル付けされたベータ版または早期アクセス版を含む、対象となる特定のAdobe Commerce バージョンを示します。 Adobe Commerceの最新の公開版について詳しくは、[&#x200B; リリースノート &#x200B;](../release/release-notes/overview.md)を参照してください。

次の表は、Adobeが特定のAdobe Commerce リリースでテストしたサードパーティソフトウェアの依存関係のバージョンを示しています。

Adobeでは、次の表で説明する必要システム構成の組み合わせのみがサポートされます。 例えば、2.4.5はMariaDB 10.4で完全にテストされています。Adobeでは、2.4.5にアップグレードする前にMariaDB 10.4にアップグレードすることをお勧めします。

スムーズなアップグレードプロセスを確保し、デプロイメントの失敗を防ぐために、Adobeでは、RabbitMQ バージョンを段階的にアップグレードすることをお勧めします。 例えば、バージョン 3.8から4.1にアップグレードする場合、まず3.8から3.9にアップグレードし、次に3.9から3.10にアップグレードする必要があります。 バージョン 3.13に到達した後にのみ、バージョン 4.1へのアップグレードを続行する必要があります。

>[!BEGINTABS]

>[!TAB  クラウド上のCommerce]

[Commerce on Cloud テンプレート &#x200B;](https://github.com/magento/magento-cloud)は、特定のCommerce バージョンと互換性のあるサービスのデフォルト設定を提供します。

{{$include /help/_includes/templated/cloud-requirements-table.md}}

サービスとバージョンは、[`services.yaml` ファイル &#x200B;](https://github.com/magento/magento-cloud/blob/master/.magento/services.yaml)で定義されています。 以下は、Cloud Infrastructure上のCommerce 2.4.6のデフォルトのサービス設定です。

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

[Commerce on Cloud Infrastructure](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/configure/service/services-yaml) ガイドの&#x200B;*Configure services*&#x200B;を参照してください。

>[!TAB Commerce オンプレミス ]

{{$include /help/_includes/templated/system-requirements-table.md}}

>[!ENDTABS]

## PHP設定

Adobe Commerceを使用する際の一般的な問題を回避するのに役立つ`memory_limit`設定など、PHPの特定の設定があります。 [必要なPHP設定](prerequisites/php-settings.md)を参照してください。

クラウド設定ガイダンスについては、[Commerce on Cloud Infrastructure](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/configure/app/php-settings) ガイドの&#x200B;*PHP settings*&#x200B;を参照してください。

### PHP OPcache

Adobeでは、[PHP OPcache](https://www.php.net/manual/en/book.opcache.php)がパフォーマンス上の理由から有効になっていることを確認することをお勧めします。 OPcacheは多くのPHP ディストリビューションで有効になっています。
- **Cloud インフラストラクチャのデプロイメント**&#x200B;上のAdobe Commerceの場合、`opcache`拡張機能がデフォルトでインストールされます。
- **Adobe Commerce オンプレミス デプロイメントの場合：**
   - [PHP OPcache拡張機能がインストールされていることを確認します](prerequisites/php-settings.md#verify-php-is-installed)。
   - パフォーマンス設定に関する具体的なガイダンスについては、[&#x200B; パフォーマンスのベストプラクティス &#x200B;](../performance/software.md#php-settings) ガイドの&#x200B;*PHP設定*&#x200B;に関するソフトウェアの推奨事項を参照してください。


OPcacheを個別にインストールする必要がある場合は、[PHP OPcache ドキュメント &#x200B;](https://www.php.net/manual/en/opcache.setup.php)を参照してください。

### PHP プロセス制御

{{php-process-control}}

### PHPUnit

PHPUnit v9 （コマンドラインツールとして）。

### PHP拡張機能

[PHPのインストール手順](prerequisites/php-settings.md)には、これらの拡張機能をインストールするための手順が含まれています。

>[!TIP]
>
>クラウドインフラストラクチャのPHP拡張機能については、[Commerce on Cloud Infrastructure](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/configure/app/php-settings#enable-extensions) ガイドの&#x200B;_PHP拡張機能の有効化_&#x200B;を参照してください。

>[!BEGINTABS]

>[!TAB  クラウド上のCommerce]

次の表は、Adobe CommerceをCloud Platformにデプロイする際にサポートされるPHP拡張機能を示しています。

{{$include /help/_includes/templated/php-extensions-cloud.md}}

>[!TAB Commerce オンプレミス ]

{{$include /help/_includes/templated/php-extensions.md}}

インストールの詳細については、[公式PHP ドキュメント &#x200B;](https://www.php.net/manual/en/extensions.php)を参照してください。

>[!ENDTABS]

## その他

この節では、その他のすべての種類の必須および任意のソフトウェアのサポートと互換性について説明します。

>[!NOTE]
>
>Adobe Commerceの最新の2.4.x パッチリリースには、次の要件が適用されます。 必要に応じて、Commerce on Cloud インフラストラクチャガイダンスが提供されます。

### ブラウザー

ストアフロントと管理者：

- Microsoft Edge（最新および以前のメジャーバージョン）
- Firefox （最新版と以前のメジャーバージョン。任意のオペレーティングシステム）
- Chrome（最新および以前のメジャーバージョン、任意のオペレーティングシステム）
- Safari （最新および以前のメジャーバージョン、macOSのみ）
- Safari for iOS（最新および以前のメジャーバージョン、ストアフロント用）
- Android用Chrome（最新および以前のメジャーバージョン、ストアフロント用）

### メールサーバー

Mail Transfer Agent （MTA）またはSMTP サーバー。 Commerce on Cloud インフラストラクチャでは、[SendGrid メールサービス &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/project/sendgrid)を使用しています。

### メモリ

Commerce Marketplaceやその他のソースから取得したアプリケーションや拡張機能をアップグレードするには、最大2 GBのRAMが必要になる場合があります。 2 GB未満のRAMを搭載したシステムを使用している場合は、[&#x200B; スワップファイル &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce-knowledge-base/kb/troubleshooting/installation-and-upgrade/out-of-memory-error-during-install-or-upgrade)を作成します。 そうしないと、アップグレードが失敗する可能性があります。

### オペレーティングシステム（Linux x86-64）

RedHat Enterprise Linux （RHEL）、CentOS、Ubuntu、DebianなどのLinux ディストリビューション。

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

Cloud Infrastructure上のCommerceについては、[Cloud Infrastructure上のCommerce](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/cdn/setup-fastly/fastly-configuration) ガイドの&#x200B;*Fastly設定*&#x200B;を参照してください。

### Xdebug

Adobe Commerceの場合は、[php_xdebug 2.5.x](https://xdebug.org/download)以降を使用してください（開発環境のみ、パフォーマンスに悪影響を与える可能性があります）。

Adobe Commerce on Cloudについては、[Commerce on Cloud Infrastructure](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/test/debug) ガイドの&#x200B;*Configure Xdebug*&#x200B;を参照してください。

>[!NOTE]
>
>Adobe Commerceのインストールまたはインストール後のストアフロントまたは管理者へのアクセスに影響を与える可能性がある`xdebug`に既知の問題があります。 [Commerce サポート サポート ナレッジベース `xdebug`の「](https://experienceleague.adobe.com/ja/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/known-issues-that-affect-installation) インストール _」に影響する_&#x200B;既知の問題を参照してください。


<!-- Last updated from includes: 2026-03-13 12:40:18 -->
