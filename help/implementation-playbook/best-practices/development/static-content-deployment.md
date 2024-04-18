---
title: 静的コンテンツのデプロイメントのベストプラクティス
description: Adobe Commerce ストアフロントに静的コンテンツが表示されない問題を回避する方法を説明します。
role: Developer
feature: Best Practices
exl-id: 9f521963-6fe4-4844-b2d1-fd457b706900
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---

# 静的コンテンツのデプロイメントのベストプラクティス

この記事では、静的コンテンツが web サイトで使用できない問題を回避するための、Adobe Commerceの静的コンテンツのデプロイ（SCD）のベストプラクティスについて説明します。

## 影響を受ける製品とバージョン

[サポートされているすべてのバージョン](../../../release/versions.md) （件中）:

* クラウドインフラストラクチャー上のAdobe Commerce
* Adobe Commerce オンプレミス

## ベストプラクティス

Web サイトで静的コンテンツを使用できない問題を回避するには、次のベストプラクティスに従って、静的コンテンツが正しく設定され、デプロイされていることを確認します。

1. 必ず次のデプロイメントガイドラインに従ってください。
   * Adobe Commerceのオンプレミス（すべてのバージョン）については、を参照してください。 [デプロイメントの概要](../../../configuration/deployment/overview.md) 開発者向けドキュメントを参照してください。
   * クラウドインフラストラクチャー上のAdobe Commerce（すべてのバージョン）については、を参照してください。 [クラウドのデプロイメントプロセス](https://devdocs.magento.com/cloud/deploy/cloud-deployment-process.html) および [静的コンテンツのデプロイメント戦略](https://devdocs.magento.com/cloud/deploy/static-content-deployment.html) 開発者向けドキュメントを参照してください。

1. クラウドインフラストラクチャー上のAdobe Commerce（すべてのバージョン）の場合は、ece-tools を最新リリースにしてください。 以下を参照してください。 [ece-tools バージョンの更新](https://devdocs.magento.com/cloud/release-notes/ece-release-notes.html) 開発者向けドキュメントを参照してください。
1. クラウドインフラストラクチャー上のAdobe Commerce（すべてのバージョン）の場合は、デプロイメントフェーズではなくビルドフェーズで静的コンテンツがデプロイされていることを確認します。 以下を参照してください。 [ストア設定の設定管理 – 静的コンテンツのデプロイメントのパフォーマンス](https://devdocs.magento.com/cloud/live/sens-data-over.html#cloud-confman-scd-over) 開発者向けドキュメントを参照してください。
1. 長時間実行されている cron ジョブがないことを確認し、長時間実行されている cron プロセスを強制終了します。 長時間実行される cron ジョブは CPU リソースを消費する可能性があり、デプロイメント時間が大幅に長くなる可能性があります。
1. Adobe Commerce オンプレミス（すべてのバージョン）の場合は、 `php` cli のプロセスが以下にアクセスできる： `pub/static` ディレクトリ。 そうしないと、静的コンテンツのデプロイでそのディレクトリにファイルを書き込めない問題が発生する可能性があります。 詳しくは、以下を参照してください。 [ファイルシステムのアクセス権限](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/file-system-permissions.html) 開発者向けドキュメントを参照してください。
1. を確実に `generated` ディレクトリはビルド間で共有ディレクトリではありません。共有ディレクトリがない場合、ビルドがランダムに失敗する可能性があります。 詳しくは、以下を参照してください。
   * Adobe Commerce オンプレミス（すべてのバージョン）: [技術的詳細](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/technical-details.html) 開発者向けドキュメントを参照してください。
   * クラウドインフラストラクチャー上のAdobe Commerce（すべてのバージョン）: [デプロイメントプロセス – フェーズ 2：構築](https://devdocs.magento.com/cloud/reference/discover-deploy.html#cloud-deploy-over-phases-build) 開発者向けドキュメントを参照してください。

1. SCD 戦略を確認します。 この *クイック* デフォルトは「戦略」です。 詳しくは、以下を参照してください。
   * Adobe Commerce オンプレミス（すべてのバージョン）: [静的ファイルのデプロイメント戦略](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/static-view/static-view-file-strategy.html) 開発者向けドキュメントを参照してください。
   * クラウドインフラストラクチャー上のAdobe Commerce（すべてのバージョン）: [変数のデプロイ - SCD\_STRATEGY](https://devdocs.magento.com/cloud/env/variables-deploy.html#scd_strategy) 開発者向けドキュメントを参照してください。

## 追加情報

開発者向けドキュメントでは、

* [静的コンテンツコンテナ](https://developer.adobe.com/commerce/admin-developer/pattern-library/containers/static-content/)
* [静的コンテンツ署名](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cache/static-content-signing.html)
* [変数のデプロイ - STATIC\_CONTENT\_SYMLINK](https://devdocs.magento.com/cloud/env/variables-deploy.html#static_content_symlink)
* [デプロイメントフロー](../../../performance/deployment-flow.md)
* [ダウンタイムなしのデプロイメント](https://devdocs.magento.com/cloud/deploy/reduce-downtime.html)
* [クラウドデプロイメントの最適化](https://devdocs.magento.com/cloud/deploy/optimize-cloud-deployment.html)
