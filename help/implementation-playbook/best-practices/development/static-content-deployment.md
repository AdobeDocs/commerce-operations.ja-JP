---
title: 静的コンテンツデプロイメントのベストプラクティス
description: 静的コンテンツがAdobe CommerceやMagento Open Sourceストアフロントに表示されない問題を回避する方法を説明します。
role: Developer
feature: Best Practices
exl-id: 9f521963-6fe4-4844-b2d1-fd457b706900
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 0%

---

# 静的コンテンツデプロイメントのベストプラクティス

この記事では、静的コンテンツが Web サイトで使用できない問題を回避するために、Adobe Commerceでの静的コンテンツデプロイ (SCD) のベストプラクティスについて説明します。

## 影響を受ける製品およびバージョン

[サポートされているすべてのバージョン](../../../release/versions.md) /:

* Adobe Commerce an cloud infrastructure
* Adobe Commerceオンプレミス
* Magento Open Source

## ベストプラクティス

静的コンテンツが Web サイトで使用できない問題を回避するには、次のベストプラクティスに従って、静的コンテンツが正しく設定およびデプロイされていることを確認します。

1. デプロイメントのガイドラインに従っていることを確認します。
   * Adobe CommerceのオンプレミスおよびMagento Open Source（すべてのバージョン）の場合、 [デプロイメントの概要](../../../configuration/deployment/overview.md) （開発者向けドキュメント）。
   * クラウドインフラストラクチャ上のAdobe Commerce（すべてのバージョン）については、 [クラウドのデプロイメントプロセス](https://devdocs.magento.com/cloud/deploy/cloud-deployment-process.html) および [静的コンテンツデプロイメント戦略](https://devdocs.magento.com/cloud/deploy/static-content-deployment.html) （開発者向けドキュメント）。

1. Adobe Commerce on cloud インフラストラクチャ（すべてのバージョン）の場合、ece-tools が最新リリースになっていることを確認します。 詳しくは、 [ece-tools のバージョンを更新](https://devdocs.magento.com/cloud/release-notes/ece-release-notes.html) （開発者向けドキュメント）。
1. クラウドインフラストラクチャ上のAdobe Commerce（すべてのバージョン）の場合、静的コンテンツは、デプロイメントフェーズではなく、ビルドフェーズでデプロイする必要があります。 詳しくは、 [ストア設定の設定管理 — 静的コンテンツデプロイメントパフォーマンス](https://devdocs.magento.com/cloud/live/sens-data-over.html#cloud-confman-scd-over) （開発者向けドキュメント）。
1. 長時間実行される cron ジョブがないことを確認し、長時間実行される cron プロセスを強制終了します。 長時間実行される cron ジョブは、CPU リソースを消費し、デプロイメントに要する時間を大幅に長くする可能性があります。
1. Adobe CommerceのオンプレミスおよびMagento Open Source（すべてのバージョン）の場合、 `php` CLI 内のプロセスは、 `pub/static` ディレクトリ。 そうしないと、静的コンテンツのデプロイがそのディレクトリにファイルを書き込めなくなる問題が発生する場合があります。 詳しくは、以下を参照してください。 [ファイルシステムのアクセス権限](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/file-system-permissions.html) （開発者向けドキュメント）。
1. 次を確認します。 `generated` ディレクトリは、ビルド全体で共有ディレクトリではありません。そうしないと、ビルドがランダムに失敗する可能性があります。 詳しくは、以下を参照してください。
   * Adobe CommerceオンプレミスおよびMagento Open Source（すべてのバージョン）: [技術的な詳細](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/technical-details.html) （開発者向けドキュメント）。
   * Adobe Commerce on cloud infrastructure （すべてのバージョン）: [デプロイメントプロセス — フェーズ 2:ビルド](https://devdocs.magento.com/cloud/reference/discover-deploy.html#cloud-deploy-over-phases-build) （開発者向けドキュメント）。

1. SCD 戦略を確認します。 この *クイック* のデフォルトは「方法」です。 詳しくは、以下を参照してください。
   * Adobe CommerceオンプレミスおよびMagento Open Source（すべてのバージョン）: [静的ファイルのデプロイメント戦略](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/static-view/static-view-file-strategy.html) （開発者向けドキュメント）。
   * Adobe Commerce on cloud infrastructure （すべてのバージョン）: [変数をデプロイする — SCD\_STRATEGY](https://devdocs.magento.com/cloud/env/variables-deploy.html#scd_strategy) （開発者向けドキュメント）。

## 追加情報

開発者向けドキュメントでは、次の操作を行います。

* [静的コンテンツコンテナ](https://developer.adobe.com/commerce/admin-developer/pattern-library/containers/static-content/)
* [静的コンテンツ署名](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cache/static-content-signing.html)
* [変数をデプロイ — STATIC\_CONTENT\_SYMLINK](https://devdocs.magento.com/cloud/env/variables-deploy.html#static_content_symlink)
* [デプロイメントフロー](../../../performance/deployment-flow.md)
* [ダウンタイムなしの導入](https://devdocs.magento.com/cloud/deploy/reduce-downtime.html)
* [クラウドデプロイメントの最適化](https://devdocs.magento.com/cloud/deploy/optimize-cloud-deployment.html)
