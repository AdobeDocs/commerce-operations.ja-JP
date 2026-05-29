---
title: ローンチ後のサポートとメンテナンス
description: Adobe Commerceストアの最適なパフォーマンスとセキュリティを確保するために、ローンチ後のサポートとメンテナンスに関する包括的なベストプラクティスを提供します。
role: Admin, User, Developer
feature: Best Practices
exl-id: f02a13ca-c851-4508-a2bd-e5bc196a330c
source-git-commit: 60444d3ef7208d12af3f06af6e3cab2cae93700b
workflow-type: tm+mt
source-wordcount: '2382'
ht-degree: 0%

---

# Adobe Commerceのローンチ後のサポートとメンテナンス

Adobe Commerceをスムーズに運用し、優れたパフォーマンスを発揮し、セキュリティを維持して、ビジネス目標を達成し続けるためには、ローンチ後のサポートとメンテナンスが不可欠です。 この段階では、継続的なモニタリング、最適化、バグ修正、アップデート、ユーザーサポートが必要です。 次のセクションでは、**ローンチ後のサポート**&#x200B;を主要なカテゴリに分割します。

## 定期的なサイト監視とパフォーマンス最適化

### パフォーマンス監視

- **サイトの読み込み速度と読み込みテスト**: Adobe Commerceはリソースを大量に消費する可能性があるため、定期的なパフォーマンスモニタリングが重要です。

   - **使用するツール**：すべてのAdobe Commerceのクラウドインフラストラクチャプロジェクトには、New Relicへのアクセスが含まれており、Commerce アプリケーションおよびクラウドインフラストラクチャ内のパフォーマンスの監視とイベントの調査に役立ちます。 その他のツールには、Google PageSpeed InsightsやGTMetrixなどがあります。

   - **監視対象**：クラウドインフラストラクチャ上のAdobe Commerceについて監視する主な項目は次のとおりです。

      - **正常性に関する通知**: ディスク容量と環境の正常性に関するアラート。

      - **観察**：効果的なサイト管理のために、複数のソースからのログデータを組み合わせた包括的な監視。

      - **New Relic サービス**：主要な指標に焦点を当てて、ステージングと実稼動環境のパフォーマンスを監視します。

      - **管理アラートポリシー**: パフォーマンスに影響を与えるインフラストラクチャまたはアプリケーションの問題について、トリガー通知に対して事前に定義されたしきい値を持つ指標を追跡します。

  >[!TIP]
  >
  >_クラウドガイド_&#x200B;の[&#x200B; パフォーマンスモニタリング &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/monitor/performance)を参照してください。


- **データベースパフォーマンスの最適化**: Adobe Commerce Cloudでデータベースパフォーマンスを最適化するには、次の操作を実行します。

   - **MySQL クエリの監視と最適化**：動作の遅いクエリを特定して解決します。これは、MySQLのSHOW FULL PROCESSLIST コマンドとEXPLAIN コマンドを使用して実行できます。 より複雑な設定の場合、Pro アーキテクチャのユーザーはPercona Toolkitを使用して、パフォーマンスの問題に対するクエリログを分析できます。

   - **インデックス管理**：すべてのテーブルにプライマリキーが含まれていることを確認し、重複するインデックスを削除します。これにより、効率が低下し、同時に書き込み中に競合が発生する可能性があります。

   - **Cron ジョブの最適化**: Cron ジョブは、特にインデックス作成などのバックグラウンドタスクが頻繁に発生する場合は、パフォーマンスへの影響を最小限に抑えるために、オフピーク時間中にスケジュールする必要があります。

  >[!TIP]
  >
  >データベース パフォーマンスの問題を解決するための[&#x200B; ベストプラクティス &#x200B;](resolve-database-performance-issues.md)を参照してください。

- **CDN**&#x200B;を監視：Adobe Commerce CloudでFastly CDNのパフォーマンスを監視するには、次の操作を実行します。

   - **New Relicを使用してモニタリング**: Adobe Commerceでは、ステージング環境と実稼動環境のFastly パフォーマンスやその他の指標をモニタリングするためのNew Relicを提供しています。 このツールは、サーバーの健全性、CDN キャッシュ、ネットワーク要求に関するインサイトを時系列で提供し、パターンの特定とCDN設定の最適化に役立ちます。

   - **Fastly ログ分析**: Adobe Commerce Cloud Pro プロジェクトの場合、New Relic ログを使用してFastly CDNおよびWAF ログ データを確認および分析し、パフォーマンスの傾向、セキュリティイベント、エラーまたは遅延の問題を診断できます。

   - **cURL コマンドを使用**: Fastly固有のヘッダーを使用してcURL コマンドを実行し、サイトのキャッシュ ステータスを調べます。 キー応答ヘッダーには、キャッシュとモジュールの状態を検証するための`X-Cache` （HIT/MISS）、`Fastly-Module-Enabled`、`Fastly-Magento-VCL-Uploaded`、`Cache-Control`が含まれます。 Adobeには、ステージング環境と実稼動環境の両方のcURL コマンドのサンプルが用意されています。

   - **ヘッダー情報を確認**: `Cache-Control`、`Pragma`、`X-Magento-Tags`などのヘッダーを調べて、キャッシュされたコンテンツに対する適切なキャッシュ動作とタグ処理を確認します。 適切なヘッダー値は、キャッシュ設定がCDN全体で効果的に適用されているかどうかを示します。

   - **Fastlyのデバッグとテスト**:Fastlyのデバッグ機能を使用して、キャッシュのヒット率とミス率、キャッシングロジック、誤ったヘッダー応答に関する問題を特定し、トラブルシューティングします。これは、設定の問題や、想定されるキャッシングルールとの不整合を示す可能性があります。

これらの監視手順は、最適なCDN パフォーマンスを維持し、サイトの速度と信頼性に影響を与える問題に対処するのに役立ちます。

>[!TIP]
>
>_クラウドガイド_&#x200B;の[Fastly サービスの概要](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly)を参照してください。

#### 定期的なセキュリティ監視

Adobe Commerce Cloudでは、定期的なセキュリティモニタリングを維持するために、Adobeでは、継続的なスキャン、ロギング、プロアクティブなセキュリティプラクティスを含む多面的なアプローチをお勧めします。 継続的なセキュリティを確保するための主な取り組みには、次のようなものがあります。

- **セキュリティスキャン**: Adobeのセキュリティスキャンツールを使用して、Commerce サイト全体で既知の脆弱性とマルウェアを監視します。 このツールは、潜在的なセキュリティリスクとコンプライアンスの問題に関するアラートを提供します。

- **定期的なパッチとアップデートのメンテナンス**:Adobeのセキュリティパッチとアップデートが利用可能になったときに適用します。 最新のAdobe Commerce バージョンにアップグレードすると、最新のセキュリティ対策が確実に実行されます。

- **監査とログの監視**: New Relic ログ （Pro プロジェクトで使用可能）などのツールを活用して、ステージング環境と実稼動環境の両方のセキュリティログを一元化および分析し、潜在的なセキュリティ問題と侵害の可視性を向上させます。

- **アカウントとアクセス管理**：不正または古いアカウントを削除するために、ユーザーと管理者アカウントを定期的に監査します。 管理者ユーザー向けの多要素認証（MFA）でアクセス制御を強化します。

- **Web アプリケーションファイアウォール（WAF）**：統合されたFastly WAFを使用して、不正なデータ抽出の試みなどの悪意のあるトラフィックパターンによる脅威を検出し、軽減します。

- **カスタムコードと拡張機能のセキュリティ**：定期的なコード監査を実施し、Adobeによって検証された拡張機能を制限することで、カスタムコードまたはサードパーティの拡張機能を保護します。

>[!TIP]
>
>_管理者システムガイド_&#x200B;の「[&#x200B; セキュリティ &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security)」を参照してください。

#### エラーログと監視

Adobe Commerce Cloudでのエラーログを監視するために、Adobeには、効果的なトラブルシューティングとパフォーマンス管理のためのツールとベストプラクティスがいくつか用意されています。

- **New Relicを使用したログの集約**: New Relicは、インフラストラクチャ、CDN、WAFに関連するログを含む、Adobe Commerce アプリケーションからのログを収集して一元化します。 この設定により、エラーの追跡、ダッシュボードの作成、ログのクエリが合理化され、アプリケーションのパフォーマンスと問題についてより詳細なインサイトを得ることができます。 New Relic Logsへのアクセスにより、様々な属性によってログを検索およびフィルタリングして、問題を迅速に診断できます。

- **エラーログタイプ**:Adobe Commerce Cloudの主要なエラーログには、デプロイメントフィードバックを含む`cloud.log`と、デプロイメントの警告とエラーを記録する`cloud.error.log`が含まれます。 デバッグ用のその他の特定のログには、`debug.log`、`system.log`および`exception.log`が含まれ、それぞれCommerce プラットフォーム全体でエラーおよびイベントのトラッキングに個別の役割を果たします。

- **Monologを使用したカスタムログ**: Adobe Commerceでは、Monologを使用したカスタムログ記録がサポートされています。これにより、開発者は、ファイル、データベース、アラートなど、様々な宛先にログメッセージを送信できます。 この柔軟性は、開発環境と実稼動環境のさまざまな監視ニーズに対応する高度なログ戦略の構築に役立ちます。

- **サイト全体の分析ツールによる例外の監視**: サイト全体の分析ツールは、例外ログの監視と管理に役立ち、デプロイメントおよびアプリケーションイベントで繰り返し発生する問題を特定します。 頻繁に発生する問題を特定し、優先順位付けやパフォーマンスに影響を与える重要な問題への対処を容易にします。

>[!TIP]
>
>Adobe Commerce Cloudでのログ記録とエラートラッキングの方法について詳しくは、[New Relic ログ管理](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/monitor/new-relic/log-management)および[例外モニタリング &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/site-wide-analysis-tool/exceptions)を参照してください。

### セキュリティとアップデート

#### セキュリティパッチとアップデート

引き続き最新情報を入手し、Adobe Commerce クラウドシステムのセキュリティを確保するために、セキュリティパッチとアップデートを監視するための主な方法を以下に示します。

- **Adobe Commerce セキュリティ アラートを購読する**: [Adobeからの通知を登録すると、セキュリティ上の脆弱性に関する情報を常に入手できます](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security)。

- **リリースノート**&#x200B;を確認：バージョン （2.3.5-p1など）に「 – pN」でタグ付けされた[&#x200B; セキュリティパッチリリースノート &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/security-patches/overview)を定期的に確認し、重要な修正と改善を含みます。

- **セキュリティパッチを迅速に適用**：セキュリティパッチが利用可能になればすぐに適用します。 これには、最新バージョンへのアップデートや、特定のパッチファイルの適用が含まれます。

- **クラウドパッチを使用**: Adobe Commerce Cloudの場合、セキュリティパッチはCloud Tools Suiteにバンドルできます。 これらの修正を受け取るには、スイートまたはCommerce バージョンをアップグレードしてください。

- **自動パッチ管理**：一元化されたパッチャーなどのツールを使用して、[複数のストアをまたいでパッチを自動的に管理および適用することを検討する](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/maintenance/patching-at-scale)。

>[!TIP]
>
>パッチの適用とセキュリティの維持について詳しくは、[&#x200B; セキュリティパッチリリースノート &#x200B;](../../../release/release-notes/security/overview.md)および[&#x200B; セキュリティパッチの適用方法](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/how-to-obtain-and-apply-security-patches)を参照してください。 また、[&#x200B; サイト全体の分析ツール &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/site-wide-analysis-tool/access)のレポートを確認する必要があります。

#### PCI認定

Adobe Commerce CloudのPCI認定を維持するには、次の重要なベストプラクティスに従ってください。

- **クレジットカード情報を保護**: Adobe Commerce内にクレジットカード情報を保存しないでください。 ストレージが必要な場合は、暗号化およびトークン化された方法を使用して保護します。

- **安全な送信プロトコルを使用**：暗号化と適切なキー管理を使用して、常にTLSなどの安全なプロトコルを介して支払いデータを送信します。

- **Web アプリケーション ファイアウォール （WAF）**&#x200B;を利用する：Fastlyを搭載したWAF サービスは、PCI DSS 6.6の要件を満たすのに役立ち、悪意のあるトラフィックがサイトに到達する前にブロックすることで、一般的な脆弱性から保護します。 詳細については、[こちら](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/planning/payment-processing-storage)および[こちら](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly-waf-service)を参照してください。

- **アクセス制限**：許可された担当者のみが機密性の高い支払いデータにアクセスできるようにし、[&#x200B; アクセス制御を適用して露出リスクを低減します](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/planning/payment-processing-storage)。

- **定期的なセキュリティスキャン**：定期的なPCI ASV スキャンを実行し、[環境を監視](https://experienceleague.adobe.com/en/docs/commerce-operations/security-and-compliance/shared-responsibility)して、潜在的な脆弱性に対処します。

>[!TIP]
>
>Adobe CommerceでPCI認定を維持するための詳細なガイドラインについては、[決済処理とストレージに関するベストプラクティス &#x200B;](../planning/payment-processing-storage.md)を参照してください。

### ユーザーおよびカスタマーサポート

#### 設定

- **サポートチャネル**：次のようなカスタマーサポートチャネルを実装します。

   - **ライブチャット**: ライブチャットのサポートを提供して、すぐにサポートを受けることができます。 人気のあるソリューションには、Zendesk、Intercom、Tidioなどがあります。

   - **メールサポート**:FreshdeskやZoho Deskなどのサポートチケットシステムを使用して、顧客からの問い合わせを効果的に管理します。

   - **電話サポート**：大規模な顧客基盤がある場合は、営業時間中に電話サポートを提供することを検討してください。

#### 管理者ユーザートレーニング

- **社内トレーニング**: Adobe Commerce管理者の使用方法、注文処理、製品管理、カスタマーサービスの問題の処理方法に関するトレーニングをスタッフに提供します。

- **ドキュメント**：よくある質問（FAQ）、トラブルシューティング、一般的なタスクについては、社内のナレッジベースまたはユーザーマニュアルを維持します。

#### 顧客体験の最適化

- **調査とフィードバック**：調査を使用して顧客のフィードバックを収集し、顧客体験を最適化します。 Adobe Commerceは、SurveyMonkeyやGoogle Formsなどのツールとの統合をサポートしています。

- **レビュー管理**：製品のカスタマーレビューと評価を管理します。 満足そうな顧客がレビューを投稿するように促し、否定的なレビューには適切に対応します。

- **Personalization**: パーソナライズされた商品レコメンデーションやターゲットを絞ったプロモーションなどのパーソナライズ機能を実装します。

### 継続的なストアのメンテナンスと最適化

#### SEO （検索エンジン最適化）

- **コンテンツの最適化**：商品の説明、ブログ投稿、カテゴリーページを定期的に更新して、検索エンジンにとって新鮮で関連性の高いコンテンツを維持します。

- **SEO監査**: Google Search ConsoleやScreaming Frogなどのツールを使用して、SEOの問題（壊れたリンク、メタデータの欠落、重複コンテンツなど）を特定し、定期的なSEO監査を実施します。

- **URL構造**：クリーンで論理的なURL構造を維持し、リンク切れやリダイレクトがないことを確認します。

#### CRO （コンバージョン率最適化）

- **A/B テスト**：商品ページやチェックアウトプロセスなど、様々なページ要素に対してA/B テストを実行して、コンバージョン率を向上させます。

- **カート放棄**: カート放棄の電子メール キャンペーンまたは出口意図ポップアップを実装して、失われた売上を回復します。

- **チェックアウトの最適化**：手順の数を減らし、ゲストチェックアウトを提供してコンバージョンを改善することで、チェックアウトプロセスを簡素化します。

#### マーケティング統合

- **メールキャンペーン**：ウェルカムメール、カート放棄メール、購入後のフォローアップ用の自動メールマーケティングフローを設定します。 Adobe、Marketo、Mailchimp、Klaviyoなどのプラットフォームは、Adobe Commerceと緊密に統合されています。

- **ソーシャルメディアと広告の統合**: Facebook、Instagram、Google Adsなどのプラットフォームと統合して、ターゲットを絞ったキャンペーンを実施し、パフォーマンスを追跡します。

#### モバイル最適化

- **モバイルの応答性**：サイトのモバイルの応答性と使いやすさを定期的にテストします。 モバイルコマースが成長していることを考えると、継続的な成功にはモバイルファーストのアプローチが不可欠です。

- **モバイルパフォーマンス**: Googleのモバイルフレンドリーなテストおよびパフォーマンスツールを使用して、モバイルストア体験を最適化します。

### 拡張と新機能の開発

- **トラフィック処理の自動スケーリング**:

   - Adobe Commerce Cloudは、リアルタイムのトラフィック要求にもとづいてサーバーリソース（web ノードなど）を動的に調整する自動スケーリングをサポートしており、ストアで手作業なしに高い訪問者数に対応できるようになります。 _クラウドガイド_&#x200B;の「[自動スケーリング &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/autoscaling)」を参照してください。

   - web層とサービス層は独立して拡張でき、トラフィックを増やすためにweb ノードを追加し、ピーク時にバックエンドのパフォーマンスのためにデータベースノードやサービスノードを拡張します。 _クラウドガイド_&#x200B;の「[&#x200B; スケールアーキテクチャ &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture)」を参照してください。

- **パフォーマンス監視**:

   - **New Relic**&#x200B;を使用して、リアルタイムのパフォーマンス指標（CPUの使用状況、トラフィックレベルなど）をモニタリングし、必要に応じて調整します。

   - 本番環境での問題を回避するために、拡張する前にステージング環境でパフォーマンスをテストします。

- **新機能の開発**:

   - **AI主導のパーソナライゼーション**、**サブスクリプション管理**、カスタムソリューションなどの高度な機能を統合します。

   - 本番環境にデプロイする前に、ステージング環境の機能を継続的にテストおよび調整し、ダウンタイムを最小限に抑えます。

- **進行中のサイトメンテナンス**:

   - システムのログとパフォーマンス指標を定期的に確認し、改善すべき領域を特定します。

   - インフラストラクチャの拡張性を維持し、新しいビジネス要件や成長に適応できるようにします。

>[!TIP]
>
>詳細なガイダンスについては、[&#x200B; メンテナンスのベストプラクティス &#x200B;](overview.md)、[&#x200B; パーソナライゼーション &#x200B;](https://business.adobe.com/blog/the-latest/adobe-commerce-continues-investment-in-composable-development-tools-and-ai-powered-personalization)および[機能開発](https://business.adobe.com/blog/the-latest/adobe-commerce-continues-investment-in-composable-development-tools-and-ai-powered-personalization)を参照してください。

### レポートと分析

- **Adobe Commerce Intelligence:** Adobe Commerceのコア機能であるCommerce Intelligenceは、複数のデータソースにまたがるベストプラクティスのインサイトを提供し、マーチャントが科学的なデータに基づいた意思決定を行い、明確で情報に基づいたアクションを実行できるようにします。 [_Commerce Intelligence ユーザーガイド_](https://experienceleague.adobe.com/en/docs/commerce-business-intelligence/mbi/getting-started)を参照してください。

- **Adobe Analytics:** Adobe Analyticsは、オンラインストアのパフォーマンスを追跡、分析、最適化するための強力なソリューションを提供します。 Adobe Analyticsは、コマース企業が、顧客行動、商品のパフォーマンス、コンバージョン率などの主要指標に関するより深いインサイトを得られるように支援し、データ主導の意思決定を可能にします。

- **Google Analytics:** Google Analyticsを使用して、お客様の行動、トラフィックソース、コンバージョン率を追跡します。

- **その他のCommerce Intelligence ツール：** Adobe Commerceには、高度なレポート機能が含まれています。 この機能を使用すると、製品、注文、顧客データに基づく一連の動的レポートにアクセスできます。ビジネスのニーズに合わせてパーソナライズされたダッシュボードを使用できます。詳しくは、_管理者ユーザーガイド_&#x200B;の[高度なレポート &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting)を参照してください。

### まとめ

ローンチ後のサポートとメンテナンスは、継続的な取り組みです。Adobe Commerceストアのパフォーマンスを継続的に維持し、安全を維持し、ビジネスニーズに適応させるために、定期的な注意が必要です。 サイトのモニタリング、カスタマーサポート、最適化、更新に対する体系化されたアプローチを導入することは、長期的な成功を収めるために不可欠です。
