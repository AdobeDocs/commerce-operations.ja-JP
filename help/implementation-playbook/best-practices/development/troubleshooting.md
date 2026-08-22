---
title: トラブルシューティングのベストプラクティス
description: Adobe Commerceの実装に関する問題のトラブルシューティング方法について説明します。
role: Developer
feature: Best Practices
exl-id: 6690eccf-d58d-4cbd-b278-90d020ee7c63
source-git-commit: 4266dbeca837bc62e5a76b2ef22b065a3452e088
workflow-type: tm+mt
source-wordcount: '597'
ht-degree: 0%

---

# トラブルシューティングのベストプラクティス

クラウドインフラストラクチャの問題に対するAdobe Commerceの効果的なトラブルシューティングについては、次のベストプラクティスに従ってください。

## 影響を受ける製品とバージョン

Adobe Commerce on cloud infrastructure

## ベストプラクティス

| 問題タイプ | ベストプラクティス | リソース |
|----------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| デプロイメントの問題 | **デプロイメントのベストプラクティスに従います。** サポートチケットの13%は、導入の問題が含まれている。 ベストプラクティスが更新され、これらの原因の多くを防ぐ方法が含まれるようになりました。 | ビルドとデプロイメントに関する[&#x200B; ベストプラクティス &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/deploy/best-practices#best-practices)をご覧ください。 |
| サイトダウンの問題 | **サイトのダウントラブルシューティングを使用します。** Cronは長時間実行でき、お互いにオーバーランする可能性があります。 停電やパフォーマンス上の問題の原因が数多くあります。 | [&#x200B; サイトダウンのトラブルシューティング &#x200B;](https://experienceleague.adobe.com/ja/docs/experience-cloud-kcs/kbarticles/ka-27152)と[Cron ジョブをリセットする方法](https://experienceleague.adobe.com/ja/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status) （サポートナレッジベース）。 |
| パフォーマンスの問題 | **Adobe Commerce バナーを使用していない場合は、無効にします。** バナーが有効になっていても使用されていない場合、リソースは必要ないときにデータベースを参照するために使用され、パフォーマンスの問題が発生します。 | [Adobe Commerce バナーの出力を無効にして、パフォーマンスを向上させます](https://experienceleague.adobe.com/ja/docs/experience-cloud-kcs/kbarticles/ka-26909)。詳しくは、サポートナレッジベースを参照してください。 |
| 検索の問題 | **MySQL カタログ検索エンジンがAdobe Commerce 2.4.0で削除されました。** バージョン 2.4.0をインストールする前に、Elasticsearch ホストの設定と設定が必要です。 詳しくは、開発者向けドキュメントの「Elasticsearchのインストールと設定」を参照してください。 | 開発者向けドキュメントの[Elasticsearch サービスの設定](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/configure/service/elasticsearch)。 |
| カスタムエラー | **ピーク時にはデプロイしません。** ユーザーを追加および削除すると、デプロイメントがトリガーになります。 | ダウンタイムのデプロイメントは[不要です](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/deploy/reduce-downtime)。詳しくは、開発者向けドキュメントを参照してください。 |
| データベースのエラーと問題 | **データベースの問題が原因でデプロイメント （フック後の問題）、パフォーマンス、およびサイトのダウンの状況が発生します。** 多くの場合、エラーが発生するか、データベース領域の割り当てが不十分です。 | [MariaDB エラーコード &#x200B;](https://mariadb.com/docs/server/reference/error-codes/mariadb-error-code-reference)、[&#x200B; ストレージスペースの管理](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/storage/manage-disk-space) （データベースを含む）については、開発者向けドキュメントをご覧ください。 |
| 設定の問題 | 保存時のインデックスではなく、スケジュール別の&#x200B;**インデックス。** これは、最も効率的なインデックス設定です。 保存時にインデックスを作成すると、完全なインデックス再作成が行われます。 | 開発者ドキュメントの[&#x200B; インデクサーの設定](../../../configuration/cli/manage-indexers.md#configure-indexers)。 |
| カスタムコードの問題 | **動作の遅いクエリログを確認して、完了に時間がかかりすぎているプロセスを特定し、おそらく終了させる機会を特定します。** クエリが遅いと、データベースのデッドロックが発生し、サイトのダウンやパフォーマンスの問題が発生する可能性があります。 | [MySQLで低速なクエリとプロセスを確認しています](https://experienceleague.adobe.com/ja/docs/commerce-knowledge-base/kb/troubleshooting/database/checking-slow-queries-and-processes-mysql) |
| 拡張機能の問題 | **現在Commerce Marketplaceで検証済みの拡張機能のみを使用します。** | Adobe Commerceの[拡張機能](https://commercemarketplace.adobe.com//extensions.html) |
| リソースの問題 | **使用可能なメモリと容量を監視して、ストレージを最適化します。** 大きなリソースを消費するアクション（デプロイメントなど）の前に、利用可能なスペースがある場合があります。 ファイルストレージの最適化が不十分な場合（例えば、大きすぎるリッチな画像が多すぎる）、スペースが不足する可能性があります。 リソースが少ないと、パフォーマンスの問題、サイトがダウンし、デプロイメントが停止し、デプロイメントでエラーが発生します。 | 開発者向けドキュメントの[&#x200B; ディスク領域の管理](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/storage/manage-disk-space)、[&#x200B; ファイルストレージが少ない/使い果たされている、特定のページの読み込みが遅い](https://experienceleague.adobe.com/ja/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/file-storage-low-specific-page-loads-are-slow)、サポートナレッジベース。 |
