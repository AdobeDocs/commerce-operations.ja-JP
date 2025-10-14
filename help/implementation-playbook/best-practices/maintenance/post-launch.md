---
title: ローンチ後のサポートとメンテナンス
description: 包括的なローンチ後のサポートおよびメンテナンスのベストプラクティスにより、Adobe Commerce ストアの最適なパフォーマンスとセキュリティを確保します。
role: Admin, User, Developer
feature: Best Practices
exl-id: f02a13ca-c851-4508-a2bd-e5bc196a330c
source-git-commit: 60444d3ef7208d12af3f06af6e3cab2cae93700b
workflow-type: tm+mt
source-wordcount: '2116'
ht-degree: 0%

---

# Adobe Commerceのローンチ後のサポートとメンテナンス

ローンチ後のサポートとメンテナンスは、Adobe Commerceストアをスムーズに実行し、パフォーマンスを向上させ、セキュリティを維持し、ビジネス目標を継続的に達成するために重要です。 このフェーズには、継続的な監視、最適化、バグ修正、アップデート、ユーザーサポートが含まれます。 次の節では **ローンチ後のサポート** を主要なカテゴリに分類しています。

## 定期的なサイト監視とパフォーマンスの最適化

### パフォーマンス監視

- **サイトのスピードと負荷のテスト**:Adobe Commerceはリソースを大量に消費する可能性があるので、定期的なパフォーマンスモニタリングが重要です。

   - **使用するツール**：クラウドインフラストラクチャプロジェクト上のすべてのAdobe Commerceには、Commerce アプリケーションおよびクラウドインフラストラクチャ内のパフォーマンスのモニタリングおよびイベントの調査を支援する、New Relicへのアクセスが含まれます。 その他のツールには、Google PageSpeed Insights や GTMetrix などがあります。

   - **監視対象**：クラウドインフラストラクチャー上のAdobe Commerceを監視する主な項目は次のとおりです。

      - **正常性通知**：ディスク容量と環境の正常性に関するアラート。

      - **監視**：複数のソースからのログデータを組み合わせた包括的な監視により、効果的なサイト管理を実現。

      - **New Relic サービス**：主要指標に焦点を当て、ステージング環境と実稼動環境でパフォーマンスを監視します。

      - **Managed alerts policy**：事前定義されたしきい値を使用してメトリクスをトラッキングし、パフォーマンスに影響を与えるインフラストラクチャまたはアプリケーションの問題をトリガーに通知します。

  >[!TIP]
  >
  >[&#x200B; クラウドガイド &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce-cloud-service/user-guide/monitor/performance) パフォーマンス監視 _を参照してください_。


- **データベースパフォーマンスの最適化**:Adobe Commerce Cloud でデータベースのパフォーマンスを最適化するには、次を実装します。

   - **MySQL クエリの監視と最適化**：低速なクエリを特定して解決します。この処理は、MySQL の SHOW FULL PROCESSLIST コマンドと EXPLAIN コマンドを使用して実行できます。 より複雑な設定の場合、Pro アーキテクチャのユーザーは Percona Toolkit を使用して、パフォーマンスの問題に関するクエリログを分析できます。

   - **インデックス管理**：すべてのテーブルにプライマリキーが含まれていることを確認し、重複したインデックスを削除します。これにより、効率が低下し、同時書き込み時に競合が発生する可能性があります。

   - **Cron ジョブの最適化**：特にインデックス作成などのバックグラウンドタスクが頻繁に行われる場合に、パフォーマンスへの影響を最小限に抑えるために、Cron ジョブをピーク外の時間にスケジュールする必要があります。

  >[!TIP]
  >
  >[&#x200B; データベースパフォーマンスの問題を解決するためのベストプラクティス &#x200B;](resolve-database-performance-issues.md) を参照してください。

- **CDN の監視**:Adobe Commerce Cloud で Fastly CDN パフォーマンスを監視するには、次の操作を実行します。

   - **監視へのNew Relicの活用**:Adobe Commerceでは、ステージング環境と実稼動環境で Fastly のパフォーマンスやその他の指標を監視するためのNew Relicを提供しています。 このツールは、サーバーの正常性、CDN キャッシュ、およびネットワークリクエストに関するインサイトを経時的に提供し、パターンの特定と CDN 設定の最適化に役立ちます。

   - **Fastly ログ分析**:Adobe Commerce Cloud Pro プロジェクトの場合、New Relic ログを使用して、Fastly CDN およびWAFのログデータを確認および分析し、パフォーマンスのトレンド、セキュリティイベントをトラッキングしたり、エラーや待ち時間の問題を診断したりできます。

   - **cURL コマンドの使用**:Fastly 固有のヘッダーを使用して cURL コマンドを実行し、サイトのキャッシュステータスを調べます。 主な応答ヘッダーには、キャッシュとモジュールのステータスを確認するための `X-Cache` （HIT/MISS）、`Fastly-Module-Enabled`、`Fastly-Magento-VCL-Uploaded`、`Cache-Control` が含まれます。 Adobeには、ステージング環境と実稼動環境の両方に対して、サンプル cURL コマンドが用意されています。

   - **ヘッダー情報の確認**:`Cache-Control`、`Pragma`、`X-Magento-Tags` などのヘッダーを検査して、キャッシュされたコンテンツの適切なキャッシュ動作とタグ処理を確認します。 ヘッダーの値が適切な場合は、キャッシュ設定が CDN 全体に効果的に適用されるかどうかを示します。

   - **Fastly デバッグとテスト**:Fastly のデバッグ機能を使用して、キャッシュの HIT 率と MISS 率、キャッシュロジック、誤ったヘッダー応答に関する問題を特定してトラブルシューティングします。これらの問題は、設定の問題や期待されるキャッシュルールとの不一致を示す場合があります。

これらの監視手順は、最適な CDN パフォーマンスを維持し、サイトの速度と信頼性に影響を与える問題に対処するのに役立ちます。

>[!TIP]
>
>[&#x200B; クラウドガイド &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce-cloud-service/user-guide/cdn/fastly) の _Fastly サービスの概要_ を参照してください。

#### 定期的なセキュリティ監視

Adobe Adobe Commerce Cloud で定期的にセキュリティを監視するには、継続的なスキャン、ログ、プロアクティブなセキュリティプラクティスを含む多面的なアプローチをお勧めします。 継続的なセキュリティを確保するための主なアクションを次に示します。

- **セキュリティスキャン**: Adobeのセキュリティスキャンツールを使用すると、Commerce サイト全体に既知の脆弱性とマルウェアが存在するかどうかを監視できます。 このツールは、潜在的なセキュリティリスクやコンプライアンスの問題に関するアラートを提供します。

- **定期的なパッチおよびアップデートのメンテナンス**:Adobeのセキュリティパッチおよびアップデートが利用可能になった時点で適用します。 最新バージョンのAdobe Commerceにアップグレードすることで、脅威に対する最新の防御が保証されます。

- **監査とログ監視**: New Relic ログ（Pro プロジェクトで利用可能）などのツールを活用して、ステージング環境と実稼動環境の両方からセキュリティログを一元化および分析し、潜在的なセキュリティの問題や侵害の可視性を高めます。

- **アカウントとアクセス管理**：ユーザーおよび管理者アカウントを定期的に監査して、権限のないアカウントや古いアカウントを削除します。 管理者ユーザー向けの多要素認証（MFA）によるアクセス制御の強化。

- **Web アプリケーションファイアウォール（WAF）**：統合された Fastly WAFを使用して、権限のないデータ抽出の試行など、悪意のあるトラフィックパターンによる脅威を検出し、軽減します。

- **カスタムコードと拡張機能のセキュリティ**：定期的なコード監査を実施し、Adobeが検証する拡張機能に限定することで、カスタムコードまたはサードパーティの拡張機能を保護します。

>[!TIP]
>
>[Admin Systems Guide](https://experienceleague.adobe.com/ja/docs/commerce-admin/systems/security/security) の _Security_ を参照してください。

#### エラーのログと監視

Adobe Commerce Cloud でエラーログを監視するために、Adobeでは、効果的なトラブルシューティングとパフォーマンス管理に役立つツールとプラクティスをいくつか用意しています。

- **New Relicを使用したログ集計**:New Relicは、インフラストラクチャ、CDN、WAFに関連するログを含め、Adobe Commerce アプリケーションからログを収集し、一元化します。 この設定により、効率化されたエラートラッキング、ダッシュボードの作成およびログのクエリが可能になり、アプリケーションのパフォーマンスと問題に関するより深いインサイトが得られます。 New Relic ログにアクセスすると、様々な属性でログを検索およびフィルタリングして、問題をすばやく診断できます。

- **エラーログタイプ**:Adobe Commerce Cloud の主なエラーログには、デプロイメントのフィードバックを含む `cloud.log` と、デプロイメントの警告とエラーを記録する `cloud.error.log` が含まれます。 デバッグのその他の具体的なログとしては、`debug.log`、`system.log`、`exception.log` があり、それぞれがCommerce プラットフォーム全体でのエラーとイベントのトラッキングで異なる役割を果たします。

- **Monolog によるカスタムログ**:Adobe Commerceは、Monolog を介したカスタムログをサポートしています。 この柔軟性は、開発環境と実稼動環境での様々な監視ニーズに対応する高度なログ戦略を構築する際に役立ちます。

- **サイト全体の分析ツールを使用した例外の監視**: サイト全体の分析ツールは、例外ログを監視および管理し、デプロイメントおよびアプリケーションイベント全体で繰り返し発生する問題を特定するのに役立ちます。 このツールは、頻繁に発生する問題に焦点を当て、パフォーマンスに影響を与える重要な問題の優先順位付けと対処を容易にします。

>[!TIP]
>
>Adobe Commerce Cloud のログとエラートラッキングのプラクティスについて詳しくは、[New Relicのログ管理 &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce-cloud-service/user-guide/monitor/new-relic/log-management) と [&#x200B; 例外のモニタリング &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/site-wide-analysis-tool/exceptions) を参照してください。

### セキュリティとアップデート

#### セキュリティパッチおよびアップデート

常に最新の情報を入手し、Adobe Commerce クラウドシステムのセキュリティを確保するには、セキュリティパッチおよびアップデートを監視するための重要なプラクティスを次に示します。

- **Adobe Commerce セキュリティアラートへの登録**:[Adobeからの通知を登録 &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce-admin/systems/security/security) して、セキュリティの脆弱性に関する情報を入手します。

- **リリースノートを確認**：バージョン（2.3.5-p1 など）に対して「– pN」がタグ付けされた [&#x200B; セキュリティパッチリリースノート &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce-operations/release/notes/security-patches/overview) を定期的に確認し、重要な修正と改善を含めます。

- **セキュリティパッチの迅速な適用**：セキュリティパッチが利用可能になり次第、適用します。 これには、最新バージョンへのアップデートや、特定のパッチファイルの適用が含まれます。

- **クラウドパッチを使用**: Adobe Commerce Cloud の場合、セキュリティパッチはクラウドツールスイート内にバンドルできます。 これらの修正を受け取るには、スイートまたはCommerceのバージョンをアップグレードしてください。

- **自動パッチ管理**：一元化されたパッチャーなどのツールを使用して [&#x200B; 複数のストアにわたってパッチを自動的に管理および適用 &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce-operations/implementation-playbook/best-practices/maintenance/patching-at-scale) することを検討してください。

>[!TIP]
>
>パッチの適用とセキュリティの維持に関する詳細と手順については、[&#x200B; セキュリティパッチのリリースノート &#x200B;](../../../release/release-notes/security/overview.md) および [&#x200B; セキュリティパッチの適用方法 &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce-knowledge-base/kb/how-to/how-to-obtain-and-apply-security-patches) を参照してください。 また、[Site-Wide Analysis Tool](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/site-wide-analysis-tool/access) レポートも確認する必要があります。

#### PCI コンプライアンス

Adobe Commerce Cloud で PCI コンプライアンスを確保するには、次の主要なプラクティスに従います。

- **カード所有者データの保護**：カード所有者データをAdobe Commerce内に保存しないでください。 ストレージが必要な場合は、暗号化およびトークン化された方法を使用してストレージを保護します。

- **安全な送信プロトコルを使用**：常に暗号化と適切な鍵管理を使用して、TLS などの安全なプロトコルで支払いデータを送信します。

- **Web アプリケーションファイアウォールの利用（WAF）**:Fastly を搭載したWAF サービスは、PCI DSS 6.6 の要件を満たすのに役立ち、サイトに到達する前に悪意のあるトラフィックをブロックすることで一般的な脆弱性から保護します。 詳しくは [&#x200B; こちら &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce-operations/implementation-playbook/best-practices/planning/payment-processing-storage) および [&#x200B; こちら &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce-cloud-service/user-guide/cdn/fastly-waf-service) を参照してください。

- **アクセスの制限**：権限のある担当者のみが機密性の高い支払いデータにアクセスできるようにし、[&#x200B; アクセス制御を適用して漏洩のリスクを軽減 &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce-operations/implementation-playbook/best-practices/planning/payment-processing-storage) します。

- **通常のセキュリティスキャン**：通常の PCI ASV スキャンを実行し、[&#x200B; 環境を監視 &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce-operations/security-and-compliance/shared-responsibility) て潜在的な脆弱性に対処します。

>[!TIP]
>
>Adobe Commerceへの PCI コンプライアンスを維持するためのガイドラインについて詳しくは、[&#x200B; 支払い処理とストレージのベストプラクティス &#x200B;](../planning/payment-processing-storage.md) を参照してください。

### ユーザーおよびカスタマーサポート

#### 設定

- **サポートチャネル**：次のようなカスタマーサポートチャネルを実装します。

   - **ライブチャット**：すぐにサポートを受けられるライブチャットサポートを提供します。 一般的なソリューションには、Zendesk、Intercom、Tidio などがあります。

   - **メールサポート**:Freshdesk や Zoho Desk などのサポートチケットシステムを使用して、顧客の問い合わせを効果的に管理します。

   - **電話サポート**：顧客が多い場合は、営業時間内の電話サポートの提供を検討してください。

#### 管理者ユーザートレーニング

- **内部トレーニング**: Adobe Commerce Admin の使用方法、注文の処理方法、商品の管理方法、カスタマーサービスの問題の処理方法についてスタッフをトレーニングします。

- **ドキュメント**：よくある質問（FAQ）、トラブルシューティング、一般的なタスクについては、内部のナレッジベースまたはユーザーマニュアルを参照してください。

#### カスタマーエクスペリエンスの最適化

- **調査とフィードバック**：調査を使用して顧客のフィードバックを収集し、顧客体験を最適化します。 Adobe Commerceは、SurveyMonkey やGoogle Formsなどのツールとの統合をサポートしています。

- **レビュー管理**：製品に関する顧客のレビューおよび評価を管理します。 満足している顧客が否定的なレビューに適切に対応しながら、レビューを残すよう促します。

- **Personalization**: パーソナライズされた商品レコメンデーションやターゲットを絞ったプロモーションなど、パーソナライズ機能を実装します。

### 継続的なストアのメンテナンスと最適化

#### 検索エンジン最適化（SEO）

- **コンテンツの最適化**：製品説明、ブログ投稿、カテゴリページを定期的に更新して、コンテンツを最新の状態に保ち、検索エンジンに関連性の高いものにします。

- **SEO 監査**: Google Search Console や Screaming Frog などのツールを使用して定期的な SEO 監査を実行し、SEO の問題（リンクの破損、メタデータの欠落、コンテンツの重複など）を特定します。

- **URL 構造**：明確で論理的な URL 構造を維持し、壊れたリンクやリダイレクトがないことを確認します。

#### コンバージョン率の最適化（CRO）

- **A/B テスト**：製品ページやチェックアウトプロセスなど、様々なページ要素に対して A/B テストを実行し、コンバージョン率を向上させます。

- **買い物かご放棄**：買い物かご放棄に関するメールキャンペーンまたは出口意図のポップアップを実装して、失われた販売を回復します。

- **チェックアウトの最適化**：手順を減らし、ゲストチェックアウトを提供してコンバージョンを向上させることで、チェックアウトプロセスを簡略化します。

#### マーケティング統合

- **メールキャンペーン**：ウェルカムメール、放棄された買い物かごメールおよび購入後のフォローアップの自動メールマーケティングフローを設定します。 Adobe Marketo、Mailchimp、Klaviyo などのプラットフォームは、Adobe Commerceと適切に統合されています。

- **ソーシャルメディアと広告の統合**:Facebook、Instagram、Google広告などのプラットフォームと統合して、ターゲットキャンペーンを実行し、パフォーマンスを追跡します。

#### モバイルの最適化

- **モバイルの応答性**：サイトのモバイルの応答性と操作性を定期的にテストします。 モバイルコマースが成長していることから、継続的に成功するにはモバイルファーストのアプローチが不可欠です。

- **モバイルのパフォーマンス**:Googleのモバイルに適したテストツールやパフォーマンスツールを使用して、モバイルストアのエクスペリエンスを最適化します。

### スケーリングと新機能の開発

- **トラフィック処理のための自動スケーリング**:

   - Adobe Commerce Cloud は、自動スケーリングをサポートし、リアルタイムのトラフィック要求に基づいてサーバーリソース（web ノードなど）を動的に調整し、ストアが手動の介入なしに大量の訪問者を処理できるようにします。 [&#x200B; クラウドガイド &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce-cloud-service/user-guide/architecture/autoscaling) の _自動スケーリング_ を参照してください。

   - Web 層とサービス層は独立して拡張でき、トラフィック増加のために Web ノードを追加したり、ピーク時にバックエンドのパフォーマンスのためにデータベースまたはサービスノードを拡張したりできます。 [&#x200B; クラウドガイド &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture) の _拡張アーキテクチャ_ を参照してください。

- **パフォーマンス監視**:

   - **New Relic** を使用して、リアルタイムのパフォーマンス指標（CPUの使用状況、トラフィックレベルなど）をモニタリングし、必要に応じて調整を行います。

   - 実稼動環境の問題を回避するために、スケーリングの前にステージング環境でパフォーマンスをテストします。

- **新機能の開発**:

   - **AI 駆動型パーソナライゼーション**、**サブスクリプション管理**、カスタムソリューションなどの高度な機能を統合します。

   - 実稼動環境にデプロイする前に、ステージング環境の機能を継続的にテストして調整し、ダウンタイムを最小限に抑えます。

- **継続的なサイトメンテナンス**:

   - システムログとパフォーマンス指標を定期的に確認し、改善すべき領域を特定します。

   - インフラストラクチャの拡張性を維持し、新しいビジネス要件や成長に対応できるようにします。

>[!TIP]
>
>詳しいガイダンスについては、[&#x200B; メンテナンスのベストプラクティス &#x200B;](overview.md)、[&#x200B; パーソナライゼーション &#x200B;](https://business.adobe.com/blog/the-latest/adobe-commerce-continues-investment-in-composable-development-tools-and-ai-powered-personalization)、および [&#x200B; 機能開発 &#x200B;](https://business.adobe.com/blog/the-latest/adobe-commerce-continues-investment-in-composable-development-tools-and-ai-powered-personalization) を参照してください。

### レポートと分析

- **Adobe Commerce Intelligence:** Adobe Commerceのコア機能であるCommerce Intelligenceは、複数のデータソースにわたるベストプラクティスのインサイトを提供し、マーチャントが科学的なデータに基づいた意思決定を行い、明確で十分な情報に基づいたアクションを実行できるようにします。 [_Commerce Intelligence ユーザーガイド_](https://experienceleague.adobe.com/ja/docs/commerce-business-intelligence/mbi/getting-started) を参照してください。

- **Adobe Analytics:** Adobe Analyticsは、オンラインストアのパフォーマンスをトラッキング、分析および最適化する強力なソリューションを提供します。 Adobe Analyticsを利用すると、e コマース企業は顧客の行動、商品のパフォーマンス、コンバージョン率などの主要指標に関するより深いインサイトを得ることができ、データに基づいた意思決定が可能になります。

- **Google Analytics:** Google Analyticsを使用して、顧客の行動、トラフィックソースおよびコンバージョン率をトラッキングします。

- **その他のCommerce Intelligence ツール：** Adobe Commerceには、高度なレポート機能が含まれています。 この機能を使用すると、製品、注文、顧客データに基づく動的レポートスイートにアクセスでき、ビジネスニーズに合わせてカスタマイズされたダッシュボードを利用できます。詳しくは、『 [&#x200B; 管理者ユーザーガイド &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting) の高度なレポート _を参照してください_。

### まとめ

ローンチ後のサポートおよびメンテナンスは継続的な取り組みであり、Adobe Commerceストアのパフォーマンスを維持し、安全を維持し、ビジネスのニーズに応じて対応できるよう、定期的な対応が必要です。 サイト監視、カスタマーサポート、最適化、更新に対して構造化されたアプローチを実装することは、長期的な成功にとって重要です。
