---
title: トラブルシューティングのベストプラクティス
description: Adobe Commerceの実装に関する問題のトラブルシューティング方法について説明します。
role: Developer
feature: Best Practices
exl-id: 6690eccf-d58d-4cbd-b278-90d020ee7c63
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---

# トラブルシューティングのベストプラクティス

クラウドインフラストラクチャの問題に関するAdobe Commerceの効果的なトラブルシューティングについては、次のベストプラクティスに従ってください。

## 影響を受ける製品とバージョン

クラウドインフラストラクチャー上のAdobe Commerce

## ベストプラクティス

| 問題タイプ | ベストプラクティス | Resource |
|----------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| デプロイメントの問題 | **デプロイメントのベストプラクティスに従います。** サポートチケットの 13 % には、デプロイメントの問題が含まれます。 ベストプラクティスが更新され、これらの原因の多くを防ぐ方法が追加されました。 | [ビルドとデプロイメントのベストプラクティス](https://devdocs.magento.com/cloud/reference/discover-deploy.html#best-practices) 開発者向けドキュメントを参照してください。 |
| サイトダウンの問題 | **サイトのダウンに関するトラブルシューティングを使用します。** Cron は長時間実行される可能性があり、互いにオーバーランする可能性があります。 これらは、多くの障害やパフォーマンスの問題の原因になります。 | [サイト停止のトラブルシューティング](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/site-down-or-unresponsive/magento-site-down-troubleshooter.html?lang=en) および [cron ジョブのリセット方法](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html?lang=en) サポートナレッジベースで。 |
| パフォーマンスの問題 | **Adobe Commerce バナーを使用していない場合は、無効にします。** バナーが有効でも使用されていない場合、リソースは不要な場合にデータベースに対して検索を実行するために使用され、パフォーマンスの問題が発生します。 | [パフォーマンスを向上させるには、Adobe Commerce バナー出力を無効にします](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/disable-magento-banner-output-to-improve-site-performance.html) サポートナレッジベースで。 |
| 問題の検索 | **MySQL カタログ検索エンジンは、Adobe Commerce 2.4.0 で削除されました。** バージョン 2.4.0 をインストールする前に、Elasticsearch・ホストをセットアップして構成する必要があります。開発者向けドキュメントのElasticsearchのインストールと設定を参照してください。 | [Elasticsearchサービスの設定](https://devdocs.magento.com/cloud/project/services-elastic.html) 開発者向けドキュメントを参照してください。 |
| カスタムエラー | **ピーク時にデプロイしないでください。** ユーザーを追加および削除すると、デプロイメントがトリガーになります。 | [ダウンタイムなしのデプロイメント](https://devdocs.magento.com/cloud/deploy/reduce-downtime.html) 開発者向けドキュメントを参照してください。 |
| データベースのエラーと問題 | **データベースの問題が原因で、デプロイメント（フック後の問題）、パフォーマンス、サイトのダウンが発生する。** 多くは、エラーまたは不十分なデータベース領域割り当てを伴います。 | [MariaDB エラーコード](https://mariadb.com/kb/en/library/mariadb-error-codes/#mariadb-specific-error-codes); [ストレージ容量の管理](https://devdocs.magento.com/cloud/project/manage-disk-space.html) （データベースを含む）を開発者向けドキュメントに記載しています。 |
| 設定の問題 | **保存時のインデックスではなく、スケジュールでインデックスを作成します。** これは、最も効率的なインデックス設定です。 保存時にインデックスを作成すると、完全なインデックス再作成が行われます。 | [インデクサーの設定](../../../configuration/cli/manage-indexers.md#configure-indexers) 開発者向けドキュメントを参照してください。 |
| カスタムコードの問題 | **低速のクエリログを調べて、完了に時間がかかりすぎているプロセスを特定し、強制終了する可能性がないか確認します。** クエリの処理に時間がかかり、データベースのデッドロックが発生して、サイトの停止やパフォーマンスの問題が発生する可能性があります。 | [MySQL で時間のかかるクエリとプロセスのチェックに時間がかかりすぎる](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/database/checking-slow-queries-and-processes-mysql.html) |
| 拡張の問題 | **現在Commerce Marketplace上にある検証済みの拡張機能のみを使用します。** | [Adobe Commerceの拡張機能](https://marketplace.magento.com/extensions.html) |
| リソースの問題 | **使用可能なメモリと容量を監視し、ストレージを最適化します。** 大量のリソースを消費するアクション（デプロイメントなど）の前に、使用可能な領域がある場合があります。 ファイルストレージの最適化が悪い（例えば、大きくてリッチな画像が多すぎる）場合も、容量不足の原因となります。 リソースが少ないと、パフォーマンスの問題、サイトの停止、デプロイメントの停止、デプロイメントの失敗が発生します。 | [ディスク容量の管理](https://devdocs.magento.com/cloud/project/manage-disk-space.html) 開発者向けドキュメント [ファイルストレージが少ない/使い果たされている、特定のページの読み込みが遅い](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/file-storage-low-specific-page-loads-are-slow.html?lang=en) サポートナレッジベースで。 |
