---
title: コードレビューのベストプラクティス
description: Adobe Commerceプロジェクトの開発段階のコードレビューのベストプラクティスについて説明します。
feature: Best Practices
role: Developer
source-git-commit: 291c3f5ea3c58678c502d34c2baee71519a5c6dc
workflow-type: tm+mt
source-wordcount: '1168'
ht-degree: 0%

---


# Adobe Commerceのコードレビューのベストプラクティス

コードレビューの主な目的は、実装された機能がパフォーマンス、アーキテクチャ、セキュリティの観点から要件を最適に満たしていることを検証することです。

また、コードレビューは、コードがAdobe Commerce開発のベストプラクティスを満たし、理解しやすく、維持が容易で、コーディング標準に従っていることを確認することを目的としています。 ほとんどのコーディング規格は、適切なツールによって自動的にチェックされる必要があります。

## 推奨されるコードレビュープロセス

コードレビュープロセスの概要は、次の手順で構成する必要があります。

1. チェックアウト環境のローカル開発機能ブランチ。
1. コードがレビュー用に送信されてからしばらく経っている場合は、ターゲットブランチ（通常は QA ブランチ）の最新の変更をマージし、リモート機能ブランチ（存在する場合）に更新をプッシュします。
1. 大まかなレビューを実施し、コードがすべての要件を実装していることを検証します。 大きな相違がある場合は、開発者に問い合わせて明確にしてください。
1. コードの実行は任意ですが、コードが期待どおりに動作するかどうか、またはコードがプロセスの効率を容易にするかどうかに疑問がある場合は、実装された機能が主な使用シナリオで期待どおりに動作するかをテストします。 重大な問題が発生した場合は、レビュープロセスを停止し、適切なコメントを付けてチケットを再度開きます。
1. 十分に確認し、このコードがすべての要件を実装していることを検証してください。 問題が発生した場合は、プルリクエストに適切なコメントを追加し、チケットを再度開きます。
1. すべてが正しく表示された場合は、プルリクエストを結合します（または、確立されている場合は次のコードレビューレベルに渡します）。

また、コードレビュープロセスを実装する際は、次の点を考慮してください。

- コードレビューは、チーム内でのコミュニケーションと知識の伝達の主なツールです。 プルリクエストに大きな問題が含まれず、必要なビジネスロジックが実装されている場合でも、プルリクエストを使用して、マージ後にさらに改善を提案できます。

- コードレビューには、開発作業の 10%～20%を超える作業を行うべきではありません。 開発チームは、協力し合う上級エンジニアで構成されていると想定しています。 コードのレビューに時間がかかると、プロジェクトの予算やタイムラインに影響する場合があります。

- コードのレビューで必要となる過度の労力を要する問題に、根本原因を特定して対処します。 通常、要件が開発チケット（コミュニケーションの問題、ユーザー事例の質が低いため）に不完全に変換されているか、コーチングの問題が発生しているためです。 最初のケースでは、チケットに十分な情報があり、チームメンバーが要件を効率的に提供できるかどうかを確認することが推奨されます。 2 つ目のケースでは、上級のエンジニアを含めたり、指導や指導の外で承認を得たりするために、チーム構造を調整する必要が生じる場合があります。

## 影響を受ける製品およびバージョン

[サポートされているすべてのバージョン](../../../release/versions.md) /:

- Adobe Commerce an cloud infrastructure
- Adobe Commerceオンプレミス

## コードレビューで検索する項目

### スタイル

スタイルは、PhpStorm 検査を実行することで自動的にテストできます（以下を参照）。

必ず [PHPMD および PHPCS](https://developer.adobe.com/commerce/php/best-practices/phpstorm/code-inspection/) をクリックし、 [コーディング規格](https://github.com/magento/magento-coding-standard) ツールを CLI から（また、以下で）選択します。 一部の重複がありますが、両方とも固有のテストがあります。

### 規則と構造

規則と構造のレビューは手動で行います。

- クラスの機能は 1 つの責任に制限されますか？
- ディレクトリ構造は意味を持ちますか？
- 機能は、適切なレベル（サーバー、クライアント、CSS、JS、データベース、フレームワーク、インフラストラクチャ）で実行されます。
- バージョン管理は正しいですか？
- コードが型破りに見えるのか、それとも間違った方法で問題を回避しようとしているのか。
- モジュール名、パッケージ名、リポジトリ名の命名規則は正しく適用されますか？
- グローバル CSS スタイルが慎重に適用され、過剰に使用されていないことを確認します。

### 完全性

完全性のレビューは手動でおこないます。

- 設定によってコードを有効または無効にできますか？また、必要なコードはすべて期待どおりに動作しますか？
- チケットに記載されている設定はすべて存在しますか？ 範囲、データタイプ、検証、翻訳、およびデフォルト値を確認します。
- 設定は、常に可能な限り低いレベル（ストアビューレベル、Web サイトレベル、グローバルレベル）で取得されますか？ 設定の取得は、 `system.xml` ファイル。
- 技術仕様のフローチャートのすべてのパスが対象ですか？ その他の技術仕様はすべて対象ですか？
- 新しい機能に対して ACL が定義されているか。
- PhpDocs はクリアされていますか？ コミットメッセージは消去されますか？
- コメントアウトされたコードはありますか。それとも、デバッグコードが表示されますか。

### パフォーマンス

パフォーマンスのレビューは手動でおこない、疑わしいときにコードの実行に助けられます。

- クエリはループで実行されますか？ このループは、編集されたファイルの外側に配置できます。
- どれでも見分けられますか？ `cachable="false"` 属性？ 正しく適用されていますか？

### セキュリティ

セキュリティのレビューは手動でおこない、テキスト検索の支援を受けることができます。 セキュリティチェックの一部は、自動化されたテストによって処理されます。

- 例外は必要に応じて記録されますか？ 適切なタイプの例外が使用されているか。
- 可能 `around` プラグインを避けるには
- プラグインは正しいタイプのデータを返しますか。
- データベース抽象レイヤーを使用して構築する必要のある生の SQL クエリを見つけることができますか。
- 新しいタイプのデータが、あらゆる種類のユーザー、管理者、フロントエンドに公開されているか。 それはセキュリティ上のリスクですか？
- ユーザー生成データは検証されていますか？ cookie の値やサーバーヘッダーを含め、ブラウザーからの取得はすべてユーザー生成と見なされます。

### プライバシーと GDPR

プライバシーに関するレビューと [GDPR](../../../security-and-compliance/privacy/gdpr.md) は手動でおこないます。

- コードは顧客データや電子メールを処理しますか。 特に注意を払う。
- このコードがループで実行できる場合、顧客データがループサイクル間で漏洩する可能性はありますか。
- リスクの指標は、インポート、cron ジョブ、トランザクション E メール、バッチキューハンドラーです。
- ループ内のユーザーデータを分離します。 Adobeでは、ループサイクル内でモデルを作成する際に、ファクトリまたはリポジトリの使用をお勧めします。ループサイクル内では、ループ外からはアクセスできません。

### 指導

指導のレビューは手動でおこないます。

- チームを教育する目標と知識を共有する場所を探します。
- コメントが単なる教育的なもので、基準を満たすのに重要でない場合は、作成者にとってその解決が必須ではないことを示します。
- 素晴らしいものが見つかったら、開発者に、特に開発者にあなたのコメントの 1 つに素晴らしい方法で話しかけた時に伝えてください。 コードレビューは多くの場合、間違いに焦点を当てますが、良い行いに対する奨励と感謝の意を示す必要があります。 時には、指導という点で、彼らが何をしたかを伝えるよりも、開発者に正しいことを伝える方が、もっと価値が高いこともあります。

## 自動処理

開発者は、自動化を使用して、ID コンパイル、データベーススキーマ、コンポーザーの検証、およびコーディング標準への準拠を確認できます。

- DI コンパイル：次の CLI コマンドを実行して、コードが問題なくコンパイルできるかどうかを確認します。

  ```bash
  bin/magento module:disable -n -q --all || exit;
  bin/magento module:enable -n -q --all || exit;
  bin/magento cache:enable -n -q || exit;
  bin/magento cache:flush -n -q || exit;
  rm -rf generated/*
  rm -rf var/view_preprocessed/*
  rm -rf pub/static/*
  rm -rf var/cache/*
  bin/magento deploy:mode:set --skip-compilation production || exit;
  bin/magento setup:di:compile -vv || exit;
  bin/magento setup:static-content:deploy en_US || exit;
  bin/magento deploy:mode:set developer || exit;
  ```

- データベーススキーマ `whitelist.json` — 次の CLI コマンドを実行し、 `db_schema_whitelist.json` ファイルが追加または変更されない。

  ```bash
  bin/magento setup:db-declaration:generate-whitelist --module-name[=MODULE-NAME]
  ```

- コンポーザーの検証 — `composer.json` ファイルを作成するには、 `composer.json` ファイル。

  ```bash
  composer validate
  ```

- コーディング標準 — Coding Standard ツールをインストールして実行し、モジュールに対して実行します。 次のファイルは、入力によって任意の場所で実行できるようにする方法を示しています。 `mcs ./app/code/Vendor/Module/`.

  ```bash
  #!/usr/bin/env bash
  $HOME/web/magento/magento-coding-standard/vendor/bin/phpcs --standard=Magento2 "$@"
  ```

- ププスタン

  ```bash
  ./vendor/bin/phpstan analyze app/code/Vendor/Module
  ```

- PhpStorm の検査

- PhpStorm PHP のコピー/貼り付け検出
