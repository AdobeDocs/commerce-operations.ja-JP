---
title: 静的コンテンツのデプロイメントのベストプラクティス
description: Adobe Commerce ストアフロントに静的コンテンツが表示されない問題を回避する方法を説明します。
role: Developer
feature: Best Practices
exl-id: 9f521963-6fe4-4844-b2d1-fd457b706900
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---

# 静的コンテンツのデプロイメントのベストプラクティス

この記事では、静的コンテンツが web サイトで使用できない問題を回避するための、Adobe Commerceの静的コンテンツのデプロイ（SCD）のベストプラクティスについて説明します。

## 影響を受ける製品とバージョン

[ サポートされているすべてのバージョン ](../../../release/versions.md):

* クラウドインフラストラクチャー上のAdobe Commerce
* Adobe Commerce オンプレミス

## ベストプラクティス

Web サイトで静的コンテンツを使用できない問題を回避するには、次のベストプラクティスに従って、静的コンテンツが正しく設定され、デプロイされていることを確認します。

1. 必ず次のデプロイメントガイドラインに従ってください。
   * Adobe Commerceのオンプレミス（すべてのバージョン）については、開発者向けドキュメントの [ デプロイメントの概要 ](../../../configuration/deployment/overview.md) を参照してください。
   * クラウドインフラストラクチャー上のAdobe Commerce（すべてのバージョン）については、開発者向けドキュメントの [ クラウドのデプロイメントプロセス ](https://experienceleague.adobe.com/ja/docs/commerce-cloud-service/user-guide/develop/deploy/process) および [ 静的コンテンツのデプロイメント戦略 ](https://experienceleague.adobe.com/ja/docs/commerce-cloud-service/user-guide/develop/deploy/static-content) を参照してください。

1. クラウドインフラストラクチャー上のAdobe Commerce（すべてのバージョン）の場合は、ece-tools を最新リリースにしてください。 開発者向けドキュメントの [ece-tools バージョンの更新 ](https://experienceleague.adobe.com/ja/docs/commerce-cloud-service/user-guide/release-notes/ece-tools-package) を参照してください。
1. クラウドインフラストラクチャー上のAdobe Commerce（すべてのバージョン）の場合は、デプロイメントフェーズではなくビルドフェーズで静的コンテンツがデプロイされていることを確認します。 詳しくは、開発者ドキュメントの [ ストア設定の設定管理 – 静的コンテンツのデプロイメントパフォーマンス ](https://experienceleague.adobe.com/ja/docs/commerce-cloud-service/user-guide/configure-store/store-settings#cloud-confman-scd-over) を参照してください。
1. 長時間実行されている cron ジョブがないことを確認し、長時間実行されている cron プロセスを強制終了します。 長時間実行される cron ジョブはCPUのリソースを消費し、デプロイメント時間が大幅に長くなる可能性があります。
1. Adobe Commerce オンプレミス（すべてのバージョン）の場合は、CLI の `php` プロセスが `pub/static` ディレクトリにアクセスできることを確認します。 そうしないと、静的コンテンツのデプロイでそのディレクトリにファイルを書き込めない問題が発生する可能性があります。 詳しくは、開発者向けドキュメントの [ ファイルシステムのアクセス権限 ](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/file-system-permissions.html?lang=ja) を参照してください。
1. `generated` ディレクトリがビルド間の共有ディレクトリでないことを確認します。共有ディレクトリでない場合、ビルドがランダムに失敗する可能性があります。 詳しくは、以下を参照してください。
   * Adobe Commerce オンプレミス（すべてのバージョン）:[ 技術的な詳細 ](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/technical-details.html?lang=ja) については、開発者向けドキュメントを参照してください。
   * クラウドインフラストラクチャー上のAdobe Commerce（すべてのバージョン）:[ デプロイメントプロセス – フェーズ 2：ビルド ](https://experienceleague.adobe.com/ja/docs/commerce-cloud-service/user-guide/develop/deploy/best-practices#cloud-deploy-over-phases-build) に関しては、開発者向けドキュメントを参照してください。

1. SCD 戦略を確認します。 *クイック* 戦略がデフォルトです。 詳しくは、以下を参照してください。
   * Adobe Commerce オンプレミス（すべてのバージョン）：開発者向けドキュメントの [ 静的ファイルのデプロイメント方法 ](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/static-view/static-view-file-strategy.html?lang=ja)。
   * クラウドインフラストラクチャー上のAdobe Commerce（すべてのバージョン）：開発者向けドキュメントの [ 変数のデプロイ - SCD\_STRATEGY](https://experienceleague.adobe.com/ja/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#scd_strategy)。

## 追加情報

開発者向けドキュメントでは、

* [ 静的コンテンツコンテナ ](https://developer.adobe.com/commerce/admin-developer/pattern-library/containers/static-content/)
* [ 静的コンテンツ署名 ](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cache/static-content-signing.html?lang=ja)
* [ 変数のデプロイ - STATIC\_CONTENT\_SYMLINK](https://experienceleague.adobe.com/ja/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#static_content_symlink)
* [デプロイメントフロー](../../../performance/deployment-flow.md)
* [ ダウンタイムなしのデプロイメント ](https://experienceleague.adobe.com/ja/docs/commerce-cloud-service/user-guide/develop/deploy/reduce-downtime)
* [ クラウドデプロイメントの最適化 ](https://experienceleague.adobe.com/ja/docs/commerce-cloud-service/user-guide/develop/deploy/optimization)
