---
title: '[!DNL Data Migration Tool]の前提条件'
description: Magento 1とMagento 2の間でデータを転送するために[!DNL Data Migration Tool]を使用する前に行う必要があることについて説明します。
exl-id: 42dfa1ca-41ed-453d-a3e4-41ff36817ca3
topic: Commerce, Migration
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 0%
---
# [!DNL Data Migration Tool]の前提条件

移行を開始する前に、次の要件が満たされていることを確認してください。

## Magento 2 システム

* Magento 2 システムを[&#x200B; システム要件](../../installation/system-requirements.md)を満たすように設定します。

  既存のMagento 1 システムと少なくとも一致するトポロジとデザインを使用します。

* [Magento 2](../../installation/overview.md)をインストールします。

## Cron

Magento 2 cron ジョブを開始しないでください。

## データベース

* インストール後、できるだけ早くMagento 2 データベースをバックアップまたは[&#x200B; ダンプ &#x200B;](https://dev.mysql.com/doc/refman/8.0/en/mysqldump.html)します。 これにより、移行が成功しなかった場合は、データベースの初期ステートを復元できます。

* [!DNL Data Migration Tool]にMagento 1およびMagento 2 データベースを接続するためのネットワーク アクセス権があるかどうかを確認します。

  ファイアウォールでポートを開き、移行ツールがデータベースと通信できるようにします。

* MySQL アカウントに、Magento データベースにアクセスするために必要なすべての権限が付与されていることを確認します。

Magento 1 データベースでバイナリロギングが有効になっている場合は、グローバル [`log_bin_trust_function_creators`](https://dev.mysql.com/doc/refman/5.7/en/server-system-variables.html#sysvar_log_bin_trust_function_creators) MySQL システム変数を`1`に設定するか、アカウントに[SUPER権限](https://dev.mysql.com/doc/refman/5.7/en/privileges-provided.html#priv_super)を付与します。

* 移行前にMagento 2 ストアで新しいエンティティ （製品、カテゴリ、属性）を作成することは推奨しません。そのような新しいエンティティは、Magento 1の古いエンティティで[!DNL Data Migration Tool]によって上書きされるからです。

## 拡張機能

Magento 1拡張機能コードをMagento 2に移行します。

最新の拡張機能バージョンを見つけるには、[[!DNL [Commerce Marketplace]]](https://commercemarketplace.adobe.com//)にアクセスするか、拡張機能プロバイダーにお問い合わせください。

[[!DNL [Code Migration Tool]]](https://github.com/magento-commerce/code-migration/blob/develop/README.md)を使用することもできます。
