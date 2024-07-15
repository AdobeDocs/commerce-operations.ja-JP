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
>[!DNL Upgrade Compatibility Tool] は、Adobe Commerce インスタンスでのみ使用できます。

<!-- Configuration guide snippets -->

## ファイルシステムの所有者 {#file-system-owner}

>[!WARNING]
>
>すべてのMagentoCLI コマンドは、[ ファイル・システムのオーナー ](/help/configuration/cli/config-cli.md#prerequisites) によって実行される必要があります。

## バックアップコマンド {#tip-backup-command}

>[!TIP]
>
>`support:backup` コマンドは、`setup:backup` コマンドで実行されるコード バックアップと同じ __ ではない）です。 `support:backup` コマンドは、Adobe Commerce サポートが調査するコードをバックアップすることを目的としています。

## Adobe Commerceのみ {#ee-only}

>[!NOTE]
>
>この機能は、Adobe Commerce インスタンスでのみ使用できます。

## Split DB の廃止 {#deprecate-split-db}

>[!IMPORTANT]
>
>Adobe Commerceのバージョン 2.4.2 では、分割データベース機能は [ 非推奨 ](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Split-Database-in-Magento-Commerce/ba-p/465187?_ga=2.128934671.2024864496.1657558157-1596100530.1657558157) となりました。 [ 分割データベースから単一データベースへの復帰 ](/help/configuration/storage/revert-split-database.md) を参照してください。

<!-- End of Configuration guide snippets -->

## 後方互換性のない変更 {#bics}

>[!NOTE]
>
>Adobe Commerce リリースには、後方互換性のない変更（BIC）が含まれている場合があります。 後方互換性のない変更を確認するには、[BIC リファレンス ](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/reference/) を参照してください。 後方互換性のない主な問題については、[BIC ハイライト ](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/highlights/) で説明しています。 すべてのリリースで主要な BIC が導入されるわけではありません。

## CVE 通知 {#cve-notice}

>[!NOTE]
>
>2.3.2 リリース以降、アドビは、外部関係者からアドビに報告された各セキュリティバグに対して、インデックス付きの Common Vulnerability and Exposures （CVE）番号を割り当て、公開します。 これにより、ユーザーはデプロイメント内の対処されていない脆弱性をより簡単に特定できます。 CVE 識別子について詳しくは、[CVE](https://cve.mitre.org/) を参照してください。

## その他のリリース情報 {#other-release-info}

>[!NOTE]
>
>これらのリリースノートで説明されている機能強化およびバグ修正のコードはAdobe Commerceにバンドルされていますが、これらのプロジェクトの一部（B2B、ページビルダー、Progressive Web Application（PWA） Studio など）も個別にリリースされています。 これらのプロジェクトのバグ修正は、各プロジェクトのドキュメントで利用できる別のプロジェクト固有のリリース情報に記載されています。 [ 製品リリースの概要 ](/help/release/release-notes/overview.md) を参照してください。

## PHP プロセスコントロール {#php-process-control}

インデクサーを並列モードで実行する前に、PHP でプロセス制御サポート （`pcntl`）を有効にする必要があります。 PHP ドキュメントの [ インストール ](https://www.php.net/manual/en/pcntl.installation.php) を参照してください。
