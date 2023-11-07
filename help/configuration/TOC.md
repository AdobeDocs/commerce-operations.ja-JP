---
user-guide-title: 設定ガイド
user-guide-description: Adobe CommerceまたはMagento Open Sourceアプリケーションの機能とサービスを設定します。
feature: Configuration
source-git-commit: b61a2726e1a26229515d28332bbd88ba3d416a98
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 0%

---


# 設定ガイド {#configuration-guide}

+ [概要](overview.md)
+ 一般設定 {#setup}
   + [アプリケーションの初期化とブートストラップ](bootstrap/initialization.md)
   + [アプリケーションモード](bootstrap/application-modes.md)
   + [Bootstrapパラメーター](bootstrap/set-parameters.md)
   + [プロファイル](bootstrap/mage-profiler.md)
   + [基本ディレクトリパス](bootstrap/mage-directory.md)
+ 導入 {#deployment}
   + [デプロイメントの概要](deployment/overview.md)
   + [単一マシンの導入](deployment/single-machine.md)
   + [パイプラインのデプロイメント](deployment/technical-details.md)
   + [前提条件](deployment/prerequisites.md)
   + [開発システムの設定](deployment/development-system.md)
   + [システム設定の作成](deployment/build-system.md)
   + [実稼動システムの設定](deployment/production-system.md)
   + [ファイル・システムのアクセス権限](deployment/file-system-permissions.md)
   + 例 {#examples}
      + [共有設定の使用](deployment/example-shared-configuration.md)
      + [CLI コマンドの使用](deployment/example-using-cli.md)
      + [環境変数の使用](deployment/example-environment-variables.md)
+ キャッシュ {#cache}
   + [キャッシュの概要](cache/caching-overview.md)
   + [キャッシュタイプ](cache/cache-types.md)
   + [キャッシュオプション](cache/cache-options.md)
   + [L2 キャッシュ](cache/level-two-cache.md)
   + レディス {#redis}
      + [Redis を設定](cache/config-redis.md)
      + [デフォルトのキャッシュに Redis を使用](cache/redis-pg-cache.md)
      + [セッションストレージに Redis を使用](cache/redis-session.md)
   + ワニス {#varnish}
      + [ワニスの概要](cache/config-varnish.md)
      + [ワニスを取り付ける](cache/config-varnish-install.md)
   + [Web サーバー](cache/config-varnish-server.md)
   + [Commerce アプリケーションの設定](cache/configure-varnish-commerce.md)
   + [高度なワニス構成](cache/config-varnish-advanced.md)
   + [キャッシュの消去](cache/use-varnish-cache.md)
   + [複数の Vanish インスタンスをキャッシュクリアする](cache/use-multiple-varnish-cache.md)
   + [Vanish の設定を確認](cache/config-varnish-final.md)
   + [Vanish ESI ブロック](cache/use-varnish-esi.md)
   + [静的コンテンツキャッシュ](cache/static-content-signing.md)
+ コマンドライン {#cli}
   + [コマンドラインツール](cli/config-cli.md)
   + [共通コマンド](cli/common-cli-commands.md)
   + [ログを有効にする](cli/enable-logging.md)
   + [キャッシュの管理](cli/manage-cache.md)
   + [インデクサーの管理](cli/manage-indexers.md)
   + [cron ジョブの設定](cli/configure-cron-jobs.md)
   + [コードをコンパイル](cli/code-compiler.md)
   + [操作モード](cli/set-mode.md)
   + [メッセージキューコンシューマーを開始](cli/start-message-queues.md)
   + [URN 蛍光ペン](cli/urn-highlighter.md)
   + [依存関係レポート](cli/dependency-reports.md)
   + [ローカリゼーション](cli/localization.md)
   + 設定の管理 {#configuration-management}
      + [値を設定](cli/set-configuration-values.md)
      + [書き出し設定](cli/export-configuration.md)
      + [データのインポート](cli/import-configuration.md)
   + 静的表示 {#static-view}
      + [デプロイメント戦略](cli/static-view-file-strategy.md)
      + [静的ビューファイルのデプロイ](cli/static-view-file-deployment.md)
   + [シンボリックリンクの作成](cli/create-symlinks.md)
   + [単体テストの実行](cli/unit-tests.md)
   + [レイアウトファイルの変換](cli/convert-layout-files.md)
   + [パフォーマンステスト用のデータを生成](cli/generate-data.md)
   + [サポートユーティリティを実行（コマースのみ）](cli/run-support-utilities.md)
+ 設定ファイル {#files}
   + [デプロイメント用の設定ファイル](reference/deployment-files.md)
   + [設定タイプ](reference/config-create-types.md)
   + [モジュールファイル](reference/module-files.md)
   + [モジュール出力](reference/disable-module-output.md)
   + [config.php](reference/config-reference-configphp.md)
   + [env.php](reference/config-reference-envphp.md)
   + [gitignore](reference/config-reference-gitignore.md)
   + [system.xml](reference/config-reference-systemxml.md)
+ 設定パス {#paths}
   + [一般](reference/config-reference-general.md)
   + [B2B 拡張機能](reference/config-reference-b2b.md)
   + [カタログ](reference/config-reference-catalog.md)
   + [顧客](reference/config-reference-customers.md)
   + [支払い方法](reference/config-reference-payment.md)
   + [セールス](reference/config-reference-sales.md)
   + [サービス](reference/config-reference-services.md)
   + [機密性の高いシステム固有の設定](reference/config-reference-sens.md)
   + [設定の上書き](reference/override-config-settings.md)
+ Cron ジョブ {#crons}
   + [Cron ジョブおよびグループ](cron/custom-cron.md)
   + [Cron リファレンスのカスタマイズ](cron/custom-cron-reference.md)
   + [カスタム Cron ジョブの設定](cron/custom-cron-tutorial.md)
+ ログ {#logs}
   + [カスタマイズされたログ](logs/custom-logging.md)
   + [Logger インターフェイス](logs/logger-interface.md)
   + [データベースアクティビティをログに記録](logs/database-activity.md)
   + [カスタムログファイルに書き込む](logs/custom-log-files.md)
+ メッセージキュー {#message-queues}
   + [メッセージキューフレームワーク](queues/message-queue-framework.md)
   + [メッセージキューの管理](queues/manage-message-queues.md)
   + [Amazon MQ の設定](queues/aws-mq.md)
   + [消費者](queues/consumers.md)
+ 複数のサイト {#multi-sites}
   + [複数のサイトおよびビュー](multi-sites/ms-overview.md)
   + [データベースエンティティ増分 ID](multi-sites/change-increment-id.md)
   + [管理者での設定](multi-sites/ms-admin.md)
   + [Nginx とのセットアップ](multi-sites/ms-nginx.md)
   + [Apache を使用した設定](multi-sites/ms-apache.md)
+ 検索エンジン {#search}
   + [検索エンジンの概要](search/overview-search.md)
   + [検索エンジンの設定](search/configure-search-engine.md)
   + [ストップワードを含むフィルター](search/search-stopwords.md)
+ セキュリティ {#security}
   + [セキュリティの概要](security/overview.md)
   + [パスワードのハッシュ](security/password-hashing.md)
   + [キャッシュ中毒](security/cache-poisoning.md)
   + [セキュア cron PHP](security/secure-cron-php.md)
   + [セキュリティ TXT](security/security-txt.md)
   + [クリックジャックのエクスプロイト](security/xframe-options.md)
+ ストレージ {#storage}
   + [データベースプロファイラー](storage/db-profiler.md)
   + リモートストレージ {#remote-storage}
      + [リモートストレージモジュール](remote-storage/remote-storage.md)
      + [AWS S3 バケット](remote-storage/remote-storage-aws-s3.md)
      + [画像のサイズ変更](remote-storage/remote-storage-image-resize.md)
      + [クラウド用のリモートストレージ](remote-storage/cloud-support.md)
   + セッションストレージ {#session-storage}
      + [セッションストレージの場所](storage/sessions.md)
      + [セッションストレージ用に memcached](storage/memcached.md)
      + [CentOS で memcached](storage/memcache-centos.md)
      + [Ubuntu で memcached](storage/memcache-ubuntu.md)
   + データベースを分割 {#split-db}
      + [分割データベースの概要](storage/multi-master.md)
      + [自動設定](storage/multi-master-masterdb.md)
      + [手動設定](storage/multi-master-manual.md)
      + [分割データベースの検証](storage/multi-master-verify.md)
      + [データベースレプリケーション](storage/multi-master-replication.md)
      + [単一のデータベースに戻す](storage/revert-split-database.md)
+ [運用ガイドに戻る](https://experienceleague.adobe.com/docs/commerce-operations/operational-guides/home.html)