---
user-guide-title: インストールガイド
user-guide-description: オンプレミスデプロイメント用にAdobe CommerceとMagento Open Sourceをインストールする方法を説明します。
source-git-commit: 949ef8d2036ceeef3cc892a5063ddecc2586a6a9
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 0%

---


# インストールガイド {#installation-guide}

- [概要](overview.md)
- [必要システム構成](system-requirements.md)
- 前提条件 {#prerequisites}
   - [概要](prerequisites/overview.md)
   - ファイルシステム {#file-system}
      - [概要](prerequisites/file-system/overview.md)
      - [権限の設定](prerequisites/file-system/configure-permissions.md)
   - Web サーバー {#web-server}
      - [Nginx](prerequisites/web-server/nginx.md)
      - [Apache](prerequisites/web-server/apache.md)
   - データベースサーバー {#database-server}
      - [MySQL](prerequisites/database/mysql.md)
      - [リモート接続](prerequisites/database/mysql-remote.md)
   - 検索エンジン {#search-engine}
      - [概要](prerequisites/search-engine/overview.md)
      - [AWS OpenSearch](prerequisites/search-engine/aws-opensearch.md)
      - [Nginx の設定](prerequisites/search-engine/configure-nginx.md)
      - [Apache の設定](prerequisites/search-engine/configure-apache.md)
   - [PHP](prerequisites/php-settings.md)
   - [メッセージブローカー](prerequisites/rabbitmq.md)
   - [セキュリティ](prerequisites/security.md)
   - [認証キー](prerequisites/authentication-keys.md)
   - [Adobe Commerce](prerequisites/commerce.md)
   - [オプションのソフトウェア](prerequisites/optional-software.md)
- [クイックスタートのインストール](composer.md)
- [高度なインストール](advanced.md)
- インストール後の手順 {#next-steps}
   - [インストールの確認](next-steps/verify.md)
   - [アプリケーションの設定](next-steps/configuration.md)
   - [umask の設定（オプション）](next-steps/set-umask.md)
   - サンプルデータをインストール（オプション） {#sample-data}
      - [概要](sample-data/overview.md)
      - [Composer パッケージのダウンロード](sample-data/composer-packages.md)
      - [Git リポジトリの複製](sample-data/git-repositories.md)
      - [モジュールを削除または更新](sample-data/remove-or-update.md)
- チュートリアル {#tutorials}
   - [ファイル・システム、メディア、データベースのバックアップとロールバック](tutorials/backup.md)
   - [データベースのステータスを確認](tutorials/database-status.md)
   - [メッセージ消費者行動の設定](tutorials/message-consumers.md)
   - [ロックプロバイダーの設定](tutorials/lock-provider.md)
   - [ストアを設定](tutorials/store.md)
   - [管理者アカウントの作成、編集、ロック解除](tutorials/admin.md)
   - [デプロイメント設定を作成または更新する](tutorials/deployment.md)
   - [データベーススキーマの作成](tutorials/database.md)
   - [管理 URI を表示または変更する](tutorials/admin-uri.md)
   - [メンテナンスモードを有効または無効にする](tutorials/maintenance-mode.md)
   - [モジュールの有効化または無効化](tutorials/manage-modules.md)
   - [拡張機能のインストール](tutorials/extensions.md)
   - [コマースをインストール](tutorials/install.md)
   - [セキュリティを向上させるために docroot を変更](tutorials/docroot.md)
   - [言語パッケージのアンインストール](tutorials/language-packages.md)
   - [モジュールのアンインストール](tutorials/uninstall-modules.md)
   - [Commerce をアンインストールまたは再インストール](tutorials/uninstall.md)
   - [テーマのアンインストール](tutorials/themes.md)
   - [データベーススキーマのアップグレード](tutorials/database-upgrade.md)
