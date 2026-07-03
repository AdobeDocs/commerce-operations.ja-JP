---
user-guide-title: 設定ガイド
user-guide-description: Adobe Commerce アプリケーションの機能とサービスを設定します。
feature: Configuration
source-git-commit: 7171e5abfad69ad0f2d3f4c4b5eb57c13d07feb4
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 0%

---


# 設定ガイド {#configuration-guide}

+ [概要](overview.md)
+ 一般設定 {#setup}
   + [アプリケーションの初期化とブートストラップ](bootstrap/initialization.md)
   + [アプリケーションモード](bootstrap/application-modes.md)
   + [Bootstrap パラメーター](bootstrap/set-parameters.md)
   + [プロファイリング](bootstrap/mage-profiler.md)
   + [ベースディレクトリのパス](bootstrap/mage-directory.md)
+ 展開 {#deployment}
   + [デプロイメントの概要](deployment/overview.md)
   + [単一マシンの導入](deployment/single-machine.md)
   + [パイプラインの展開](deployment/technical-details.md)
   + [前提条件](deployment/prerequisites.md)
   + [開発システムの設定](deployment/development-system.md)
   + [システム設定の構築](deployment/build-system.md)
   + [実稼動システムの設定](deployment/production-system.md)
   + [ファイルシステムアクセス権限](deployment/file-system-permissions.md)
   + 例 {#examples}
      + [共有設定の使用](deployment/example-shared-configuration.md)
      + [CLI コマンドの使用](deployment/example-using-cli.md)
      + [環境変数の使用](deployment/example-environment-variables.md)
+ キャッシュ {#cache}
   + [キャッシュの概要](cache/caching-overview.md)
   + [キャッシュフロントエンドとタイプの設定](cache/cache-types.md)
   + [バックエンドオプションのキャッシュ](cache/cache-options.md)
   + [L2 キャッシュ設定](cache/level-two-cache.md)
   + Redis {#redis}
      + [Redisのインストールとセットアップ](cache/config-redis.md)
      + [デフォルトおよびページキャッシュ用にRedisを設定](cache/redis-pg-cache.md)
      + [セッションストレージ用にRedisを設定する](cache/redis-session.md)
      + [AWS ElastiCacheでのRedisの設定](cache/redis-elasticache-for-ec2.md)
   + バルキー {#valkey}
      + [Valkeyのインストールと設定](cache/config-valkey.md)
      + [デフォルトおよびページキャッシュのValkeyの設定](cache/valkey-pg-cache.md)
      + [セッション ストレージのValkeyの設定](cache/valkey-session.md)
   + Varnish {#varnish}
      + [Varnishの概要](cache/config-varnish.md)
      + [Varnishのインストール](cache/config-varnish-install.md)
      + [Web サーバーの設定](cache/config-varnish-server.md)
      + [Commerce アプリケーションの設定](cache/configure-varnish-commerce.md)
      + [高度なVarnish設定](cache/config-varnish-advanced.md)
      + [Varnish設定の確認](cache/config-varnish-final.md)
      + [Varnishによるキャッシュのクリア](cache/use-varnish-cache.md)
      + [複数のVarnish インスタンスによるキャッシュのクリア](cache/use-multiple-varnish-cache.md)
      + [ニス ESI ブロック](cache/use-varnish-esi.md)
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
   + [URN ハイライター](cli/urn-highlighter.md)
   + [依存関係レポート](cli/dependency-reports.md)
   + [ローカライズ](cli/localization.md)
   + 設定管理 {#configuration-management}
      + [値を設定](cli/set-configuration-values.md)
      + [書き出し設定](cli/export-configuration.md)
      + [データのインポート](cli/import-configuration.md)
   + 静的表示 {#static-view}
      + [デプロイメント戦略](cli/static-view-file-strategy.md)
      + [静的ビューファイルのデプロイ](cli/static-view-file-deployment.md)
   + [シンボリックリンクの作成](cli/create-symlinks.md)
   + [単体テストの実行](cli/unit-tests.md)
   + [レイアウトファイルの変換](cli/convert-layout-files.md)
   + [パフォーマンステスト用のデータ生成](cli/generate-data.md)
   + [サポートユーティリティの実行（Commerceのみ）](cli/run-support-utilities.md)
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
   + [B2B拡張機能](reference/config-reference-b2b.md)
   + [カタログ](reference/config-reference-catalog.md)
   + [顧客](reference/config-reference-customers.md)
   + [支払い方法](reference/config-reference-payment.md)
   + [営業担当者](reference/config-reference-sales.md)
   + [サービス](reference/config-reference-services.md)
   + [機密設定やシステム固有の設定](reference/config-reference-sens.md)
   + [設定設定を上書き](reference/override-config-settings.md)
+ Cron Jobs {#crons}
   + [Cron ジョブとグループ](cron/custom-cron.md)
   + [crons リファレンスのカスタマイズ](cron/custom-cron-reference.md)
   + [カスタム cron ジョブの設定](cron/custom-cron-tutorial.md)
+ ログ {#logs}
   + [カスタマイズされたログ](logs/custom-logging.md)
   + [Logger インターフェイス](logs/logger-interface.md)
   + [ログデータベースアクティビティ](logs/database-activity.md)
   + [カスタムログファイルへの書き込み](logs/custom-log-files.md)
+ メッセージキュー {#message-queues}
   + [メッセージキューフレームワーク](queues/message-queue-framework.md)
   + [メッセージキューの管理](queues/manage-message-queues.md)
   + [Amazon MQの設定](queues/aws-mq.md)
   + [消費者](queues/consumers.md)
+ 複数のサイト {#multi-sites}
   + [複数のサイトとビュー](multi-sites/ms-overview.md)
   + [データベースエンティティ増分ID](multi-sites/change-increment-id.md)
   + [管理者で設定](multi-sites/ms-admin.md)
   + [Nginxで設定する](multi-sites/ms-nginx.md)
   + [Apacheを使用した設定](multi-sites/ms-apache.md)
+ 検索エンジン {#search}
   + [検索エンジンの概要](search/overview-search.md)
   + [検索エンジンを設定](search/configure-search-engine.md)
   + [ストップワードでフィルター](search/search-stopwords.md)
+ セキュリティ {#security}
   + [セキュリティの概要](security/overview.md)
   + [パスワードハッシュ](security/password-hashing.md)
   + [キャッシュポイズニング](security/cache-poisoning.md)
   + [セキュアなcron PHP](security/secure-cron-php.md)
   + [セキュリティ TXT](security/security-txt.md)
   + [クリックジャッキングエクスプロイト](security/xframe-options.md)
+ 保存 {#storage}
   + [データベースプロファイラー](storage/db-profiler.md)
   + リモートストレージ {#remote-storage}
      + [リモートストレージモジュール](remote-storage/remote-storage.md)
      + [AWS S3 バケット](remote-storage/remote-storage-aws-s3.md)
      + [画像のサイズ変更](remote-storage/remote-storage-image-resize.md)
      + [クラウド用リモートストレージ](remote-storage/cloud-support.md)
   + セッションストレージ {#session-storage}
      + [セッションストレージの場所](storage/sessions.md)
      + [セッションストレージ用のmemcached](storage/memcached.md)
      + [centOSでのmemcached](storage/memcache-centos.md)
      + [memcached on Ubuntu](storage/memcache-ubuntu.md)
   + データベースを分割 {#split-db}
      + [分割データベースの概要](storage/multi-master.md)
      + [自動設定](storage/multi-master-masterdb.md)
      + [手動設定](storage/multi-master-manual.md)
      + [スプリットデータベースの検証](storage/multi-master-verify.md)
      + [データベースレプリケーション](storage/multi-master-replication.md)
      + [単一のデータベースに戻す](storage/revert-split-database.md)
+ [業務ガイドに戻る](https://experienceleague.adobe.com/docs/commerce-operations/operational-guides/home.html?lang=ja)
