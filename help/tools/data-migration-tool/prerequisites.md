---
title: "[!DNL Data Migration Tool] 前提条件"
description: 「 [!DNL Data Migration Tool] Magento1 とMagento2 の間でデータを転送する。」
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 0%

---


# [!DNL Data Migration Tool] 前提条件

移行を開始する前に、次の要件を満たしていることを確認してください。

## Magento2 系

* 次の条件を満たすようにMagento2 システムを設定します。 [システム要件](../../installation/system-requirements.md).

   既存のMagento1 システムと少なくとも一致するトポロジと設計を使用します。

* [インストールMagento2](../../installation/overview.md).

## Cron

Magento2 の cron ジョブを開始しないでください。

## データベース

* インストール後、バックアップまたは [ダンプ](https://dev.mysql.com/doc/refman/8.0/en/mysqldump.html) Magento2 データベースをできるだけ早く作成します。 これにより、移行が成功しなかった場合に、初期データベース状態を復元できます。

* 次を確認します。 [!DNL Data Migration Tool] には、Magento1 とMagento2 データベースを接続するためのネットワークアクセス権があります。

   ファイアウォールでポートを開き、移行ツールがデータベースと通信できるようにします。

* MySQL アカウントに、データベースにアクセスするために必要な権限がすべて付与されていることをMagentoしてください。

Magento1 データベースでバイナリログが有効になっている場合は、グローバル [`log_bin_trust_function_creators`](https://dev.mysql.com/doc/refman/5.7/en/server-system-variables.html#sysvar_log_bin_trust_function_creators) MySQL システム変数をに設定する `1`または [SUPER 権限](https://dev.mysql.com/doc/refman/5.7/en/privileges-provided.html#priv_super) をアカウントに追加します。

* 移行前に、Magento2 ストアで新しいエンティティ（製品、カテゴリ、属性）を作成することはお勧めしません。これは、 [!DNL Data Migration Tool] これらの新しいエンティティは、Magento1 の古いエンティティで上書きされます。

## 拡張機能

Magento1 の拡張機能コードをMagento2 に移行します。

最新の拡張機能バージョンを見つけるには、 [!DNL [Commerce Marketplace]](https://marketplace.magento.com/) または、拡張機能プロバイダーにお問い合わせください。

また、 [!DNL [Code Migration Tool]](https://github.com/magento-commerce/code-migration/blob/develop/README.md).
