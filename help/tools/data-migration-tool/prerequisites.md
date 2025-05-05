---
title: '[!DNL Data Migration Tool] の前提条件'
description: Magento 1 とMagento 2 の間でデータを転送するために  [!DNL Data Migration Tool]  の使用を開始する前に行う必要があることを説明します。
exl-id: 42dfa1ca-41ed-453d-a3e4-41ff36817ca3
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 0%

---

# [!DNL Data Migration Tool] 前提条件

移行を開始する前に、次の要件が満たされていることを確認してください。

## Magento2 系

* [ 必要システム構成 ](../../installation/system-requirements.md) を満たすように、Magento2 システムを設定します。

  既存のMagento1 システムと少なくとも一致するトポロジとデザインを使用します。

* [Magento 2 をインストールします ](../../installation/overview.md)。

## Cron

Magento 2 cron ジョブは開始しないでください。

## データベース

* インストール後、できるだけ早くMagento 2 データベースをバックアップまたは [ ダンプ ](https://dev.mysql.com/doc/refman/8.0/en/mysqldump.html) します。 これにより、移行が成功しなかった場合に、初期のデータベース状態を復元できます。

* Magento1 およびMagento2 のデータベー [!DNL Data Migration Tool] に接続するためのネットワークアクセス権がネットワークに付与されているかどうかを確認します。

  移行ツールがデータベースと通信できるように、ファイアウォールでポートを開きます。

* MySQL アカウントに、Magentoデータベースへのアクセスに必要な権限がすべて付与されていることを確認します。

Magento 1 データベースでバイナリログが有効になっている場合は、グローバル [`log_bin_trust_function_creators`](https://dev.mysql.com/doc/refman/5.7/en/server-system-variables.html#sysvar_log_bin_trust_function_creators) MySQL システム変数を `1` に設定するか、アカウントに [SUPER 権限 ](https://dev.mysql.com/doc/refman/5.7/en/privileges-provided.html#priv_super) を付与します。

* Magento1 の古いエンティティで新しいエンティティが上書きされるので、移行前にMagento2 ストアに新しいエンティティ（製品、カテゴリ、属性）を作 [!DNL Data Migration Tool] することはお勧めしません。

## 拡張機能

Magento 1 の拡張コードをMagento 2 に移行します。

最新の拡張機能バージョンを確認するには、[[!DNL [Commerce Marketplace]]](https://marketplace.magento.com/) を参照するか、拡張機能プロバイダーにお問い合わせください。

[[!DNL [Code Migration Tool]]](https://github.com/magento-commerce/code-migration/blob/develop/README.md) を使用することもできます。
