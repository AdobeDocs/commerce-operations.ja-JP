---
source-git-commit: 20add0a748e8df38dff48a779c63e1177d2a022d
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 0%

---
# スニペット

## コマースのみ {#commerce-only}

>[!NOTE]
>
>The [!DNL Upgrade Compatibility Tool] は、Adobe Commerceインスタンスでのみ使用できます。

<!-- Configuration guide snippets -->

## ファイルシステムの所有者 {#file-system-owner}

>[!WARNING]
>
>すべてのMagentoCLI コマンドは、 [ファイルシステム所有者](/help/configuration/cli/config-cli.md#prerequisites).

## バックアップコマンド {#tip-backup-command}

>[!TIP]
>
>The `support:backup` コマンドは _not_ が実行したのと同じコードのバックアップ `setup:backup` コマンドを使用します。 The `support:backup` コマンドは、Adobe Commerce Support が調べるためのコードをバックアップすることを目的としています。

## Adobe Commerceのみ {#ee-only}

>[!NOTE]
>
>この機能は、Adobe Commerceインスタンスでのみ使用できます。

## DB の分割は廃止されました {#deprecate-split-db}

>[!IMPORTANT]
>
>データベース分割機能は次のとおりです。 [非推奨](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Split-Database-in-Magento-Commerce/ba-p/465187?_ga=2.128934671.2024864496.1657558157-1596100530.1657558157) (Adobe Commerceのバージョン 2.4.2)。 詳しくは、 [分割データベースから単一のデータベースに戻す](/help/configuration/storage/revert-split-database.md).

<!-- End of Configuration guide snippets -->

## 後方互換性のない変更 {#bics}

>[!NOTE]
>
>Adobe CommerceおよびMagento Open Sourceリリースには、後方互換性のない変更 (BIC) が含まれている場合があります。 後方互換性のない変更を確認するには、 [BIC リファレンス](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/reference/). 後方互換性のない主な問題については、 [BIC ハイライト](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/highlights/). すべてのリリースでメジャー BIC が導入されているわけではありません。

## CVE 通知 {#cve-notice}

>[!NOTE]
>
>2.3.2 リリース以降、アドビは、外部の関係者から報告された各セキュリティバグと共に、インデックス付きの Common Velwability and Exposures(CVE) 番号を割り当てて公開します。 これにより、ユーザーは、デプロイメントにおける宛ててがない脆弱性をより簡単に識別できます。 CVE 識別子について詳しくは、 [CVE](https://cve.mitre.org/).

## その他のリリース情報 {#other-release-info}

>[!NOTE]
>
>これらのリリースノートで説明されている機能強化とバグ修正のコードはAdobe Commerceにバンドルされていますが、これらのプロジェクト (B2B、Page Builder、Progressive Web Application(PWA)Studio など ) も個別にリリースされています。 これらのプロジェクトのバグ修正は、個別のプロジェクト固有のリリース情報に記載されています。この情報は、各プロジェクトのドキュメントに記載されています。 詳しくは、 [製品リリースの概要](/help/release/release-notes/overview.md).
