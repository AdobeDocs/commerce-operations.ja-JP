---
user-guide-title: アップグレードガイド
user-guide-description: Adobe Commerce アプリケーションのアップグレードが非常に重要な理由と、アップグレードを正常に計画および実行する方法を説明します。
feature: Upgrade
topic: Administration, Commerce, Development, Upgrade
source-git-commit: 4616cc6990921b531483213f2904a24b483fb7ac
workflow-type: tm+mt
source-wordcount: '144'
ht-degree: 4%

---


# アップグレードガイド {#upgrade-guide}

- [アップグレードプロセスの概要](overview.md)
- アップグレードジャーニー {#journey}
   - [ジャーニーフェーズ](journey/phases.md)
   - [プロジェクトの開始](journey/project-launch.md)
   - [年度計画](journey/annual-planning.md)
   - [実装](journey/implementation.md)
- 準備 {#prepare}
   - [ベストプラクティス](prepare/best-practices.md)
   - [プラットフォームの変更のレビュー](prepare/platform-changes.md)
   - [アップグレードの前提条件の完了](prepare/prerequisites.md)
   - [Elasticsearchから OpenSearch への移行](prepare/opensearch-migration.md)
   - [RabbitMQ から ActiveMQ への移行](prepare/activemq-migration.md)
   - [アップグレードの範囲について](prepare/scope.md)
- 実装 {#implementation}
   - [アップグレードの実行](implementation/perform-upgrade.md)
- モジュールと拡張機能 {#modules}
   - [アップグレードモジュール](modules/upgrade.md)
   - [モジュールの管理](modules/manage.md)
- パッチ {#patches}
   - [パッチの動作](patches/overview.md)
   - [パッチの適用](patches/apply.md)
- [!DNL Upgrade Compatibility Tool] {#upgrade-compatibility-tool}
   - [概要](upgrade-compatibility-tool/overview.md)
   - [必要システム構成](upgrade-compatibility-tool/prerequisites.md)
   - [!DNL Upgrade Compatibility Tool] の使用 {#use-upgrade-compatibility-tool}
      - [コマンドラインインターフェイスでのツールの実行](upgrade-compatibility-tool/run.md)
      - [との統合  [!DNL Site-Wide Analysis Tool]](upgrade-compatibility-tool/integrate-analysis-tool.md)
      - [Magento PHPStorm プラグイン内でツールを実行します](upgrade-compatibility-tool/run-configuration-phpstorm-plugin.md)
   - 報告書 {#reporting}
      - [レポート](upgrade-compatibility-tool/reports.md)
      - [エラーメッセージ](upgrade-compatibility-tool/error-messages.md)
   - [関連ツール](upgrade-compatibility-tool/related-tools.md)
- 貢献する開発者 {#developer}
   - [Git ベースのインストールのアップグレード](developer/git-installs.md)
   - [モジュールの管理](developer/manage-modules.md)
- トラブルシューティング {#troubleshooting}
   - [現在の検索エンジンはサポートされていません](troubleshooting/search-engine-not-supported.md)
   - [モジュール更新失敗後のロールバック](troubleshooting/roll-back-after-update-failure.md)
   - [アップグレードのメンテナンスモードオプション](troubleshooting/maintenance-mode-options.md)
- リソース {#resources}
   - [推奨読み取り](resources/recommended-reading.md)
   - [Adobe Commerceを使用したプラットフォームの最新化](resources/recommended-upgrade-paths.md)
- [&#x200B; 運用ガイドに戻る &#x200B;](https://experienceleague.adobe.com/docs/commerce-operations/operational-guides/home.html)
