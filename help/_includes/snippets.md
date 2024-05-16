---
source-git-commit: 1eaf2329c16e6dbe3e93cb7fff3a6920b4b8379d
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 0%

---
# スニペット

## Commerceのみ {#commerce-only}

>[!NOTE]
>
>この [!DNL Upgrade Compatibility Tool] は、Adobe Commerce インスタンスでのみ使用できます。

<!-- Configuration guide snippets -->

## ファイルシステムの所有者 {#file-system-owner}

>[!WARNING]
>
>すべてのMagento CLI コマンドは、 [ファイルシステム所有者](/help/configuration/cli/config-cli.md#prerequisites).

## バックアップコマンド {#tip-backup-command}

>[!TIP]
>
>この `support:backup` コマンドは _ではない_ で実行される同じコードバックアップ `setup:backup` コマンド。 この `support:backup` コマンドは、Adobe Commerce サポートによる調査用のコードをバックアップすることを目的としています。

## Adobe Commerceのみ {#ee-only}

>[!NOTE]
>
>この機能は、Adobe Commerce インスタンスでのみ使用できます。

## Split DB の廃止 {#deprecate-split-db}

>[!IMPORTANT]
>
>データベース分割機能は [非推奨](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Split-Database-in-Magento-Commerce/ba-p/465187?_ga=2.128934671.2024864496.1657558157-1596100530.1657558157) （Adobe Commerceのバージョン 2.4.2 でサポート）。 参照： [分割データベースから単一データベースへの復帰](/help/configuration/storage/revert-split-database.md).

<!-- End of Configuration guide snippets -->

## 後方互換性のない変更 {#bics}

>[!NOTE]
>
>Adobe Commerce リリースには、後方互換性のない変更（BIC）が含まれている場合があります。 後方互換性のない変更を確認するには、を参照してください。 [BIC 参照](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/reference/). 主な後方互換性のない問題については、を参照してください。 [BIC ハイライト](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/highlights/). すべてのリリースで主要な BIC が導入されるわけではありません。

## CVE 通知 {#cve-notice}

>[!NOTE]
>
>2.3.2 リリース以降、アドビは、外部関係者からアドビに報告された各セキュリティバグに対して、インデックス付きの Common Vulnerability and Exposures （CVE）番号を割り当て、公開します。 これにより、ユーザーはデプロイメント内の対処されていない脆弱性をより簡単に特定できます。 CVE 識別子について詳しくは、次を参照してください [CVE](https://cve.mitre.org/).

## その他のリリース情報 {#other-release-info}

>[!NOTE]
>
>これらのリリースノートで説明されている機能強化およびバグ修正のコードはAdobe Commerceにバンドルされていますが、これらのプロジェクトの一部（B2B、ページビルダー、Progressive Web Application（PWA） Studio など）も個別にリリースされています。 これらのプロジェクトのバグ修正は、各プロジェクトのドキュメントで利用できる別のプロジェクト固有のリリース情報に記載されています。 参照： [製品リリースの概要](/help/release/release-notes/overview.md).

## PHP プロセスコントロール {#php-process-control}

インデクサーを並列モードで実行する前に、プロセス制御のサポート（`pcntl`）を使用します。 参照： [インストール](https://www.php.net/manual/en/pcntl.installation.php) PHP のドキュメントに書かれています。
