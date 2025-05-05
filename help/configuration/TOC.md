---
user-guide-title: 設定ガイド
user-guide-description: Adobe Commerce アプリケーションの機能とサービスを設定します。
feature: Configuration
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 0%

---


# 設定ガイド {#configuration-guide}

+ [概要](overview.md)
+ 一般設定 {#setup}
   + [アプリケーションの初期化とブートストラップ](bootstrap/initialization.md)
   + [アプリケーションモード](bootstrap/application-modes.md)
   + [Bootstrapパラメーター](bootstrap/set-parameters.md)
   + [プロファイル](bootstrap/mage-profiler.md)
   + [ベースディレクトリのパス](bootstrap/mage-directory.md)
+ 展開 {#deployment}
   + [デプロイメントの概要](deployment/overview.md)
   + [単一マシンの導入](deployment/single-machine.md)
   + [パイプラインデプロイメント](deployment/technical-details.md)
   + [前提条件](deployment/prerequisites.md)
   + [開発システムのセットアップ](deployment/development-system.md)
   + [システム設定の作成](deployment/build-system.md)
   + [実稼動システムのセットアップ](deployment/production-system.md)
   + [ファイルシステムのアクセス権限](deployment/file-system-permissions.md)
   + の例{#examples}
      + [共有設定の使用](deployment/example-shared-configuration.md)
      + [CLI コマンドの使用](deployment/example-using-cli.md)
      + [環境変数の使用](deployment/example-environment-variables.md)
+ キャッシュ {#cache}
   + [キャッシュの概要](cache/caching-overview.md)
   + [キャッシュタイプ](cache/cache-types.md)
   + [キャッシュオプション](cache/cache-options.md)
   + [L2 キャッシュ](cache/level-two-cache.md)
   + Redis {#redis}
      + [Redis の設定](cache/config-redis.md)
      + [既定のキャッシュに Redis を使用](cache/redis-pg-cache.md)
      + [セッションストレージに Redis を使用](cache/redis-session.md)
   + ワニス {#varnish}
      + [ワニスの概要](cache/config-varnish.md)
      + [ワニスをインストール](cache/config-varnish-install.md)
   + [Web サーバー](cache/config-varnish-server.md)
   + [Commerce アプリケーションの設定](cache/configure-varnish-commerce.md)
   + [高度なワニス設定](cache/config-varnish-advanced.md)
   + [キャッシュのクリア](cache/use-varnish-cache.md)
   + [複数の Varnish インスタンスをクリアするキャッシュ](cache/use-multiple-varnish-cache.md)
   + [Varnish 設定の確認](cache/config-varnish-final.md)
   + [ワニス ESI ブロック](cache/use-varnish-esi.md)
   + [静的コンテンツキャッシュ](cache/static-content-signing.md)
+ コマンドライン {#cli}
   + [コマンドラインツール](cli/config-cli.md)
   + [一般的なコマンド](cli/common-cli-commands.md)
   + [ログを有効にする](cli/enable-logging.md)
   + [キャッシュの管理](cli/manage-cache.md)
   + [インデクサーの管理](cli/manage-indexers.md)
   + [Cron ジョブの設定](cli/configure-cron-jobs.md)
   + [コードのコンパイル](cli/code-compiler.md)
   + [操作モード](cli/set-mode.md)
   + [メッセージキューコンシューマーの開始](cli/start-message-queues.md)
   + [URN ハイライター](cli/urn-highlighter.md)
   + [依存関係レポート](cli/dependency-reports.md)
   + [場所](cli/localization.md)
   + 設定管理 {#configuration-management}
      + [値を設定](cli/set-configuration-values.md)
      + [書き出し設定](cli/export-configuration.md)
      + [データの読み込み](cli/import-configuration.md)
   + 静的ビュー {#static-view}
      + [デプロイメント戦略](cli/static-view-file-strategy.md)
      + [静的表示ファイルのデプロイ](cli/static-view-file-deployment.md)
   + [シンボリックリンクの作成](cli/create-symlinks.md)
   + [単体テストの実行](cli/unit-tests.md)
   + [レイアウトファイルの変換](cli/convert-layout-files.md)
   + [パフォーマンステスト用のデータの生成](cli/generate-data.md)
   + [サポートユーティリティを実行する（Commerceのみ）](cli/run-support-utilities.md)
+ 設定ファイル {#files}
   + [デプロイメントの設定ファイル](reference/deployment-files.md)
   + [設定タイプ](reference/config-create-types.md)
   + [モジュールファイル](reference/module-files.md)
   + [モジュール出力](reference/disable-module-output.md)
   + [config.php](reference/config-reference-configphp.md)
   + [env.php](reference/config-reference-envphp.md)
   + [ギティニョア](reference/config-reference-gitignore.md)
   + [system.xml](reference/config-reference-systemxml.md)
+ 設定パス {#paths}
   + [一般](reference/config-reference-general.md)
   + [B2B 拡張機能](reference/config-reference-b2b.md)
   + [カタログ](reference/config-reference-catalog.md)
   + [顧客](reference/config-reference-customers.md)
   + [支払い方法](reference/config-reference-payment.md)
   + [売上](reference/config-reference-sales.md)
   + [サービス](reference/config-reference-services.md)
   + [機密およびシステム固有の設定](reference/config-reference-sens.md)
   + [設定を上書き](reference/override-config-settings.md)
+ Cron Jobs {#crons}
   + [Cron ジョブとグループ](cron/custom-cron.md)
   + [Cron リファレンスのカスタマイズ](cron/custom-cron-reference.md)
   + [カスタム cron ジョブの設定](cron/custom-cron-tutorial.md)
+ Logs {#logs}
   + [カスタマイズされたログ](logs/custom-logging.md)
   + [ロガーインターフェイス](logs/logger-interface.md)
   + [データベースアクティビティを記録](logs/database-activity.md)
   + [カスタムログファイルへの書き込み](logs/custom-log-files.md)
+ メッセージキュー {#message-queues}
   + [メッセージキューフレームワーク](queues/message-queue-framework.md)
   + [メッセージキューの管理](queues/manage-message-queues.md)
   + [Amazon MQ の設定](queues/aws-mq.md)
   + [消費者](queues/consumers.md)
+ Multiple sites {#multi-sites}
   + [複数のサイトとビュー](multi-sites/ms-overview.md)
   + [データベース エンティティ増分 ID](multi-sites/change-increment-id.md)
   + [管理者で設定](multi-sites/ms-admin.md)
   + [Nginx を使用したセットアップ](multi-sites/ms-nginx.md)
   + [Apache とのセットアップ](multi-sites/ms-apache.md)
+ 検索エンジン {#search}
   + [検索エンジンの概要](search/overview-search.md)
   + [検索エンジンの設定](search/configure-search-engine.md)
   + [ストップワードによるフィルタリング](search/search-stopwords.md)
+ セキュリティ {#security}
   + [セキュリティの概要](security/overview.md)
   + [パスワードハッシュ](security/password-hashing.md)
   + [キャッシュの被毒](security/cache-poisoning.md)
   + [Cron PHP を保護する](security/secure-cron-php.md)
   + [セキュリティ TXT](security/security-txt.md)
   + [クリックジャッキング攻撃](security/xframe-options.md)
+ ストレージ {#storage}
   + [データベース プロファイラー](storage/db-profiler.md)
   + リモート記憶域 {#remote-storage}
      + [リモートストレージモジュール](remote-storage/remote-storage.md)
      + [AWS S3 バケット](remote-storage/remote-storage-aws-s3.md)
      + [画像のサイズ変更](remote-storage/remote-storage-image-resize.md)
      + [クラウド用リモートストレージ](remote-storage/cloud-support.md)
   + セッションストレージ {#session-storage}
      + [セッションストレージの場所](storage/sessions.md)
      + [セッションストレージ用の memcached](storage/memcached.md)
      + [centOS の memcached](storage/memcache-centos.md)
      + [ubuntu 上の memcached](storage/memcache-ubuntu.md)
   + データベース の分割 {#split-db}
      + [データベースの分割の概要](storage/multi-master.md)
      + [自動設定](storage/multi-master-masterdb.md)
      + [手動設定](storage/multi-master-manual.md)
      + [分割データベースの検証](storage/multi-master-verify.md)
      + [データベースレプリケーション](storage/multi-master-replication.md)
      + [単一データベースに戻す](storage/revert-split-database.md)
+ [ 運用ガイドに戻る ](https://experienceleague.adobe.com/docs/commerce-operations/operational-guides/home.html)