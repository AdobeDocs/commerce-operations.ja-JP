---
title: 静的コンテンツ展開のベストプラクティス
description: Adobe Commerce ストアフロントに静的コンテンツが表示されない問題を回避する方法について説明します。
role: Developer
feature: Best Practices
exl-id: 9f521963-6fe4-4844-b2d1-fd457b706900
source-git-commit: f9a135fc63574ccbecd3f564a87fc5c4ac03f009
workflow-type: tm+mt
source-wordcount: '586'
ht-degree: 0%

---

# 静的コンテンツ展開のベストプラクティス

ここでは、Adobe Commerceの静的コンテンツデプロイ（SCD）のベストプラクティスについて説明し、静的コンテンツがweb サイトで利用できない問題を回避するのに役立ちます。

## 影響を受ける製品とバージョン

[&#x200B; サポートされているすべてのバージョン &#x200B;](../../../release/versions.md) /:

* Adobe Commerce on cloud infrastructure
* Adobe Commerce オンプレミス

## ベストプラクティス

Web サイトで静的コンテンツが使用できない問題を回避するには、次のベストプラクティスに従って、静的コンテンツが正しく設定され、デプロイされていることを確認します。

1. デプロイメントガイドラインに従ってください。
   * Adobe Commerce オンプレミス（すべてのバージョン）については、開発者向けドキュメントの[&#x200B; デプロイメントの概要](../../../configuration/deployment/overview.md)を参照してください。
   * クラウドインフラストラクチャ上のAdobe Commerce（すべてのバージョン）については、開発者向けドキュメントの[&#x200B; クラウド展開プロセス &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/process)および[静的コンテンツ展開戦略](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/static-content)を参照してください。

1. Adobe Commerce on cloud infrastructure （すべてのバージョン）の場合は、ece-toolsが最新リリースであることを確認してください。 詳しくは、開発者用ドキュメントの[e-tools バージョン &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/release-notes/ece-tools-package)を更新してください。
1. Adobe Commerce on cloud infrastructure （すべてのバージョン）の場合は、デプロイメントフェーズではなく、ビルドフェーズで静的コンテンツがデプロイされていることを確認します。 ストア設定の[構成管理 – 静的コンテンツのデプロイメントのパフォーマンス &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure-store/store-settings#cloud-confman-scd-over)を開発者向けドキュメントで参照してください。
1. 長時間実行しているcron ジョブがなく、長時間実行しているcron プロセスを強制終了します。 長期にわたるcronの作業は、CPUのリソースを消費し、デプロイメントにかかる時間が大幅に長くなる可能性があります。
1. Adobe Commerce オンプレミス（すべてのバージョン）の場合、CLIの`php` プロセスが`pub/static` ディレクトリにアクセスできることを確認します。 それ以外の場合、静的コンテンツデプロイがそのディレクトリにファイルを書き込むことができないという問題に直面する可能性があります。 詳しくは、開発者ドキュメントの[&#x200B; ファイルシステムのアクセス権限](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/file-system-permissions.html)を参照してください。
1. `generated` ディレクトリがビルド間で共有ディレクトリでないことを確認してください。そうしないと、ビルドがランダムに失敗する可能性があります。 詳細：
   * Adobe Commerce オンプレミス（すべてのバージョン）: [技術情報](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/technical-details.html)については、開発者用ドキュメントをご覧ください。
   * クラウド インフラストラクチャ上のAdobe Commerce（すべてのバージョン）: [&#x200B; デプロイメント プロセス – フェーズ 2: ビルド &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/best-practices#cloud-deploy-over-phases-build) （開発者用ドキュメント）

1. SCD戦略の確認。 *quick*&#x200B;戦略がデフォルトです。 詳細：
   * Adobe Commerce オンプレミス（すべてのバージョン）: [静的ファイルのデプロイメント戦略](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/static-view/static-view-file-strategy.html)については、開発者用ドキュメントをご覧ください。
   * クラウドインフラストラクチャ上のAdobe Commerce（すべてのバージョン）: [&#x200B; デプロイ変数 – SCD\_STRATEGY](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#scd_strategy)については、開発者用ドキュメントを参照してください。

## 追加情報

アドビの開発者ドキュメントには、次のようなものがあります。

* [静的コンテンツコンテナ](https://developer.adobe.com/commerce/admin-developer/pattern-library/containers/static-content)
* [静的コンテンツ署名](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cache/static-content-signing.html)
* [変数のデプロイ - STATIC\_CONTENT\_SYMLINK](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#static_content_symlink)
* [デプロイメントフロー](../../../performance/deployment-flow.md)
* [ダウンタイムのゼロ導入](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/reduce-downtime)
* [クラウド導入の最適化](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/optimization)
