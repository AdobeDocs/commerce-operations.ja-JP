---
title: ベストプラクティスのトラブルシューティング
description: Adobe Commerceの実装に関する問題のトラブルシューティング方法について説明します。
role: Developer
feature: Best Practices
exl-id: 6690eccf-d58d-4cbd-b278-90d020ee7c63
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '523'
ht-degree: 0%

---

# ベストプラクティスのトラブルシューティング

クラウドインフラストラクチャの問題に関するAdobe Commerceの効果的なトラブルシューティングをおこなうには、次のベストプラクティスに従います。

## 影響を受ける製品およびバージョン

Adobe Commerce an cloud infrastructure

## ベストプラクティス

| 問題のタイプ | ベストプラクティス | リソース |
|----------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| デプロイメントの問題 | **デプロイメントのベストプラクティスに従います。** サポートチケットの 13%にデプロイメントの問題が含まれています。 ベストプラクティスが更新され、これらの原因の多くを回避する方法が含まれるようになりました。 | [ビルドとデプロイメントのベストプラクティス](https://devdocs.magento.com/cloud/reference/discover-deploy.html#best-practices) （開発者向けドキュメント）。 |
| サイトダウンの問題 | **[ サイトダウントラブルシュータ ] を使用します。** Cron は長時間実行され、お互いにオーバーランする可能性があります。 多くの機能停止やパフォーマンスの問題の原因となります。 | [サイトダウンのトラブルシューティング](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/site-down-or-unresponsive/magento-site-down-troubleshooter.html?lang=en) および [cron ジョブのリセット方法](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html?lang=en) をサポートナレッジベースに追加しました。 |
| パフォーマンスの問題 | **Adobe Commerceバナーを使用していない場合は、無効にします。** バナーが有効で使用されていない場合、リソースは不要な場合にデータベースに対する検索を実行するために使用され、パフォーマンスの問題が発生します。 | [パフォーマンスを向上させるには、Adobe Commerce Banner の出力を無効にします](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/disable-magento-banner-output-to-improve-site-performance.html) をサポートナレッジベースに追加しました。 |
| 検索の問題 | **MySQL カタログ検索エンジンは、Adobe Commerce 2.4.0 で削除されました。** Elasticsearch2.4.0 をインストールする前に、バージョンホストを設定しておく必要があります。開発者向けドキュメントのElasticsearchのインストールと設定に関する説明を参照してください。 | [Elasticsearchサービスの設定](https://devdocs.magento.com/cloud/project/services-elastic.html) （開発者向けドキュメント）。 |
| カスタムエラー | **ピーク時にはデプロイしない。** ユーザーを追加および削除すると、デプロイメントのトリガーが設定されます。 | [ダウンタイムなしの導入](https://devdocs.magento.com/cloud/deploy/reduce-downtime.html) （開発者向けドキュメント）。 |
| データベースのエラーと問題 | **データベースの問題は、導入（フック後の問題）、パフォーマンス、サイト停止の状況を引き起こします。** 多くの場合、エラーやデータベース容量の割り当てが不十分になります。 | [MariaDB エラーコード](https://mariadb.com/kb/en/library/mariadb-error-codes/#mariadb-specific-error-codes); [ストレージ容量の管理](https://devdocs.magento.com/cloud/project/manage-disk-space.html) （データベースを含む）を開発者向けドキュメントに追加しました。 |
| 設定の問題 | **保存時にインデックスの代わりにスケジュール別にインデックスを作成します。** これは、最も効率的なインデックス作成設定です。 保存時のインデックスは、完全なインデックス再作成の原因となります。 | [インデクサーの設定](../../../configuration/cli/manage-indexers.md#configure-indexers) （開発者向けドキュメント）。 |
| カスタムコードの問題 | **処理に時間がかかるクエリログで、完了までに時間がかかりすぎるプロセスを特定して強制終了する機会がないかを確認します。** クエリが遅いと、データベースのデッドロックが発生し、サイトのダウンやパフォーマンスの問題が発生する場合があります。 | [MySQL での処理に時間がかかる、処理に時間がかかるクエリの確認](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/database/checking-slow-queries-and-processes-mysql.html) |
| 拡張機能の問題 | **現在、検証済みの拡張機能のみをCommerce Marketplaceで使用します。** | [Adobe Commerceの拡張機能](https://marketplace.magento.com/extensions.html) |
| リソースの問題 | **使用可能なメモリと容量を監視し、ストレージを最適化します。** 大量のリソースを消費するアクション（デプロイメントなど）の前に空き容量がある場合があります。 ファイルストレージの最適化が不十分な場合（例えば、大きすぎるリッチ画像が多すぎる場合）も、容量不足の原因となる可能性があります。 リソースが少ないと、パフォーマンスの問題、サイトの停止、デプロイメントの停止、デプロイメントの失敗が発生します。 | [ディスク容量の管理](https://devdocs.magento.com/cloud/project/manage-disk-space.html) （開発者向けドキュメント） [ファイルストレージが少ない/消費されている、特定のページの読み込みが遅い](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/file-storage-low-specific-page-loads-are-slow.html?lang=en) をサポートナレッジベースに追加しました。 |
