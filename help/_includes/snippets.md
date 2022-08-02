---
source-git-commit: 2c12c6ea6e7b6ffeb07bbda17ded34e39de6656a
workflow-type: tm+mt
source-wordcount: '97'
ht-degree: 0%

---
# スニペット

## コマースのみ {#commerce-only}

>[!NOTE]
>
>この [!DNL Upgrade Compatibility Tool] は、Adobe Commerceインスタンスでのみ使用できます。

<!-- Configuration guide snippets -->

## ファイルシステムの所有者 {#file-system-owner}

>[!WARNING]
>
>すべてのMagentoCLI コマンドは、 [ファイルシステム所有者](/help/configuration/cli/config-cli.md#prerequisites).

## バックアップコマンド {#tip-backup-command}

>[!TIP]
>
>この `support:backup` コマンドは _not_ が実行したのと同じコードのバックアップ `setup:backup` コマンドを使用します。 この `support:backup` コマンドは、Adobe Commerce Support が調べるためのコードをバックアップすることを目的としています。

## Adobe Commerceのみ {#ee-only}

>[!NOTE]
>
>この機能は、Adobe Commerceインスタンスでのみ使用できます。

## DB の分割は廃止されました {#deprecate-split-db}

>[!IMPORTANT]
>
>データベース分割機能は次のとおりです。 [非推奨](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Split-Database-in-Magento-Commerce/ba-p/465187?_ga=2.128934671.2024864496.1657558157-1596100530.1657558157) (Adobe Commerceのバージョン 2.4.2)。 詳しくは、 [分割データベースから単一のデータベースに戻す](/help/configuration/storage/revert-split-database.md).

<!-- End of Configuration guide snippets -->
