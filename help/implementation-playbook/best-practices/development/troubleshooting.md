---
title: トラブルシューティングのベストプラクティス
description: Adobe Commerceの実装に関する問題のトラブルシューティング方法について説明します。
role: Developer
feature: Best Practices
exl-id: 6690eccf-d58d-4cbd-b278-90d020ee7c63
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
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
| デプロイメントの問題 | **デプロイメントのベストプラクティスに従う。サポートチケットの** 13 % には、デプロイメントの問題が関係しています。 ベストプラクティスが更新され、これらの原因の多くを防ぐ方法が追加されました。 | 開発者向けドキュメントの [ ビルドとデプロイメントのベストプラクティス ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/best-practices#best-practices)。 |
| サイトダウンの問題 | **サイトのダウンに関するトラブルシューティングを使用します。** Cron は長時間実行される可能性があり、互いにオーバーランする可能性があります。 これらは、多くの障害やパフォーマンスの問題の原因になります。 | [ サイトダウンのトラブルシューティング ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/site-down-or-unresponsive/magento-site-down-troubleshooter.html?lang=en) および [Cron ジョブのリセット方法 ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html?lang=en) に関するサポートナレッジベースを参照してください。 |
| パフォーマンスの問題 | **Adobe Commerce バナーを使用していない場合は、無効にします。** バナーが有効でも使用されていない場合、リソースは不要な場合にデータベースへの検索に使用され、パフォーマンスの問題が発生します。 | [ パフォーマンスを向上させるために、Adobe Commerce バナー出力を無効にする ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/disable-magento-banner-output-to-improve-site-performance.html) については、サポートナレッジベースを参照してください。 |
| 問題の検索 | **MySQL カタログ検索エンジンは、Adobe Commerce 2.4.0 で削除されました** バージョン 2.4.0 をインストールする前に、Elasticsearch ホストをセットアップして設定する必要があります。開発者向けドキュメントのElasticsearchのインストールと設定を参照してください。 | 開発者向けドキュメントの [Elasticsearch サービスの設定 ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/service/elasticsearch) を参照してください。 |
| カスタムエラー | **ピーク時にデプロイしないでください。** ユーザーを追加および削除すると、デプロイメントがトリガーされます。 | 開発者向けドキュメントの [ ダウンタイムなしのデプロイメント ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/reduce-downtime)。 |
| データベースのエラーと問題 | **データベースの問題が原因で、デプロイメント（フック後の問題）、パフォーマンス、サイトのダウンが発生する。** 多くは、エラーまたはデータベースの容量割り当ての不足を伴います。 | 開発者向けドキュメントの [MariaDB エラーコード ](https://mariadb.com/kb/en/library/mariadb-error-codes/#mariadb-specific-error-codes); [ ストレージ容量の管理 ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space) （データベースを含む）。 |
| 設定の問題 | **保存時にインデックスを作成するのではなく、スケジュールでインデックスを作成します。** これは最も効率的なインデックス設定です。 保存時にインデックスを作成すると、完全なインデックス再作成が行われます。 | 開発者向けドキュメントの [ インデクサーの設定 ](../../../configuration/cli/manage-indexers.md#configure-indexers) を参照してください。 |
| カスタムコードの問題 | **低速のクエリログを調べて、完了に時間がかかりすぎているプロセスを特定し、強制終了する可能性がないか確認します。クエリの処理に時間がかかり** データベースのデッドロックが発生して、サイトの停止やパフォーマンスの問題が発生する可能性があります。 | [MySQL で時間のかかるクエリとプロセスの確認に時間がかかりすぎる ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/database/checking-slow-queries-and-processes-mysql.html) |
| 拡張の問題 | **現在Commerce Marketplaceにある検証済みの拡張機能のみを使用してください。** | [Adobe Commerceの拡張機能 ](https://marketplace.magento.com/extensions.html) |
| リソースの問題 | **使用可能なメモリと容量を監視し、ストレージを最適化します。** 大量のリソースを消費するアクション（デプロイメントなど）の前に、使用可能な領域がある場合があります。 ファイルストレージの最適化が悪い（例えば、大きくてリッチな画像が多すぎる）場合も、容量不足の原因となります。 リソースが少ないと、パフォーマンスの問題、サイトの停止、デプロイメントの停止、デプロイメントの失敗が発生します。 | [ ディスク容量の管理 ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space) 開発者向けドキュメント。[ ファイルストレージが少ない/使い果たされている、特定のページの読み込みが遅い ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/file-storage-low-specific-page-loads-are-slow.html?lang=en) については、サポートナレッジベースを参照してください。 |
