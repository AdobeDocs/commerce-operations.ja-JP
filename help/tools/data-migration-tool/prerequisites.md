---
title: '[!DNL Data Migration Tool] 前提条件'
description: の使用を開始する前に行う必要がある操作について説明します [!DNL Data Migration Tool] Magento1 とMagento2 との間でデータを転送する。
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

* 次の条件を満たすようにMagento2 システムを設定します [必要システム構成](../../installation/system-requirements.md).

  既存のMagento1 システムと少なくとも一致するトポロジとデザインを使用します。

* [Magento 2 をインストールします。](../../installation/overview.md).

## Cron

Magento 2 cron ジョブは開始しないでください。

## データベース

* インストール後、または [ダンプ](https://dev.mysql.com/doc/refman/8.0/en/mysqldump.html) Magento2 データベースを早急に作成してください。 これにより、移行が成功しなかった場合に、初期のデータベース状態を復元できます。

* 次のかどうかを確認します [!DNL Data Migration Tool] Magento1 とMagento2 のデータベースを接続するためのネットワーク・アクセスが可能です。

  移行ツールがデータベースと通信できるように、ファイアウォールでポートを開きます。

* MySQL アカウントに、Magentoデータベースへのアクセスに必要な権限がすべて付与されていることを確認します。

Magento1 データベースに対してバイナリ・ロギングが有効になっている場合は、グローバルを設定します [`log_bin_trust_function_creators`](https://dev.mysql.com/doc/refman/5.7/en/server-system-variables.html#sysvar_log_bin_trust_function_creators) MySQL システム変数をに `1`、または [SUPER 権限](https://dev.mysql.com/doc/refman/5.7/en/privileges-provided.html#priv_super) をアカウントに。

* 移行前に、Magento2 ストアに新しいエンティティ（製品、カテゴリ、属性）を作成することはお勧めしません。 [!DNL Data Migration Tool] は、そのような新しいエンティティをMagento 1 の古いエンティティで上書きします。

## 拡張機能

Magento 1 の拡張コードをMagento 2 に移行します。

最新の拡張機能のバージョンを確認するには、次を参照してください： [!DNL [Commerce Marketplace]](https://marketplace.magento.com/) または、拡張機能のプロバイダーにお問い合わせください。

を使用することもできます [!DNL [Code Migration Tool]](https://github.com/magento-commerce/code-migration/blob/develop/README.md).
