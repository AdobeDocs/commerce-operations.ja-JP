---
title: 共有された責任
description: クラウドインフラストラクチャプロジェクト上のAdobe Commerceに関与する各関係者のセキュリティ責任について説明します。
source-git-commit: d216418c69cb972e93c04b5d5cc0a8ab0495653d
workflow-type: tm+mt
source-wordcount: '1562'
ht-degree: 0%

---


# 共有責任セキュリティモデル

Adobe Commerce on cloud infrastructure は、共有の責任セキュリティモデルに基づく、サービスとしてのプラットフォーム (PaaS) を提供します。 Adobe、マーチャント、クラウドサービスプロバイダー、コンテンツ配信ネットワーク (CDN) プロバイダーは、それぞれ、クラウドインフラストラクチャアプリケーション上のAdobe Commerceのセキュリティと、マーチャント固有のコードおよび拡張機能を維持する責任を負います。

このアプローチにより、マーチャントは、ビジネス要件に最適で、運用上の責任とコストを最小限に抑えながら、柔軟性とカスタマイズ性に優れ、拡張性に優れたソリューションを設計および実装できます。

一般に、Adobeは、安全なコアアプリケーションコードの開発と保守、プラットフォームのセキュリティの維持、プラットフォームの SOC 2 と PCI への準拠と PCI 準拠の技術コンポーネント（PHP、Redis など）との互換性の確保、コアプラットフォームに関するセキュリティの問題への対応を担当します。 Adobeは、クラウドサービスプロバイダーや CDN パートナーと協力して、発生する可能性のある問題を解決することも担当します。

マーチャントは、安全なカスタムコードの維持とサードパーティアプリケーションとの統合を担当し、安全なアプリケーション開発を確保し、マーチャントの支払いプロセッサーから要求された場合は PCI 認定を取得し、セキュリティインシデントに対応します。

## Adobeの責任

Adobeは、クラウドインフラストラクチャ環境上のAdobe Commerceと、クラウドインフラストラクチャソリューションコード上のAdobe Commerceのコアコードのセキュリティと可用性を担当します。 さらに、Adobeは、クラウドインフラストラクチャソリューション上でAdobe Commerceのセキュリティを維持するために必要なアクティビティとメカニズムに責任を負います。以下が含まれます。

- クラウドデータストレージや検索機能など、クラウドインフラストラクチャ上でAdobe Commerceがサポートするアプリケーションに対して、サーバーレベルのセキュリティとパッチを適用する
- クラウドインフラストラクチャコード上でのコアAdobe Commerceの侵入テストとスキャンの実施
- パブリッククラウドサービスプロバイダーの ID およびアクセス管理 (IAM) ソリューションおよび権限管理（PCI コンプライアンス要件）に関する、年次のレビュー/監査を実施
- Adobe従業員や請負業者を含む、認定されたユーザーの半年間のレビュー/監査（PCI コンプライアンス要件）
- バックアップ/リストア機能に関する年次テストとドキュメント化を実施
- サーバーおよび境界ファイアウォールの設定
- クラウドインフラストラクチャリポジトリでのAdobe Commerceの接続と設定
- DR（災害復旧）プランの定義、テスト、導入、文書化は、Adobeの責任範囲内の領域に対して行われます。
- グローバルプラットフォーム Web アプリケーションファイアウォール (WAF) ルールの定義
- オペレーティングシステムの堅牢化 (OS)
- クラウドインフラストラクチャ上のAdobe Commerceとのコンテンツ配布ネットワーク (CDN) およびアプリケーションパフォーマンス管理 (APM) ソリューションの統合の実装と保守
- クラウドインフラストラクチャコード上でのコアAdobe Commerceに対する定期的なセキュリティおよびその他の更新の発行（パッチの適用はマーチャントの責任です）
- マーチャントサポートの管理とアクセス制御のサポート（Zendesk など）
- クラウドインフラストラクチャプラットフォーム上のAdobe Commerceに関するセキュリティインシデントの監視、ログ、修復
- プラットフォームの運用を監視24/7、クラウドインフラストラクチャのマーチャントに対するAdobe Commerceのサポートを提供
- 実稼動環境とステージング環境のプロビジョニング
- プラットフォームの運用とインフラストラクチャに対する潜在的なセキュリティ上の脅威の評価
- マーチャントとの SLA（サービス・レベル契約）に記載されているように、コンピューティング、ストレージ、グリッド、その他のリソースを拡張
- DNS の設定 ( クラウドインフラストラクチャプラットフォームインフラストラクチャ上のAdobe Commerceのみ )
- プラットフォームのセキュリティの脆弱性のテスト

Adobeは、クラウドインフラストラクチャソリューション上でAdobe Commerceの運用に使用されるインフラストラクチャとサービスの PCI 認定を維持しますが、マーチャントは、カスタムコード、システムとネットワークのプロセス、および組織のコンプライアンスを担当します。

Adobeは、適用される SLA に合意されたマーチャントのインフラストラクチャの可用性も確保します。

## 商人の責任

マーチャントは、クラウドインフラストラクチャソリューション上のAdobe Commerceの特定のカスタマイズされたインスタンスに関する、次のセキュリティのベストプラクティスとを担当します。

- 必要なAdobe Commerce on クラウドインフラストラクチャ設定ファイルをリポジトリに追加する
- Adobeによるリリース直後に、カスタムAdobe Commerce on cloud infrastructure ソリューションにセキュリティおよびその他のパッチを適用する
- ベンダーによるリリース直後に、すべてのカスタム拡張機能とコードにセキュリティとその他のパッチを適用する
- カスタム Vanrish VCL ファイルの作成、展開、テスト
- カスタム拡張機能やコードを含む、クラウドインフラストラクチャソリューション上でカスタマイズされたAdobe Commerceの設計、テーマ設定、インストール、統合、保護
- クラウドインフラストラクチャの設定、アプリケーション、およびプラットフォーム上のAdobe Commerceのマーチャントのインスタンスに対するユーザーアクセスの許可と取り消し
- クラウドインフラストラクチャプラットフォーム上のAdobe Commerceで構築された、マーチャントの内部ネットワーク、サーバー、インフラストラクチャ、およびカスタムアプリケーションに関するセキュリティ問題の処理
- クラウドインフラストラクチャのコマンドライン統合 (CLI) ツールへのAdobe Commerceのインストール
- PCI-DSS ガイドラインで定義されている、カスタマイズされたアプリケーションおよびその他の内部プロセスの PCI コンプライアンスの必要なレベルを維持する

  >[!NOTE]
  >
  >マーチャントの PCI コンプライアンスは、クラウドインフラストラクチャ上のAdobe Commerceとクラウドホスティングプロバイダの PCI 認定に基づいて構築され、確認が必要な領域を最小限に抑えます。

- PCI ASV スキャンを実行し、クラウドインフラストラクチャコードとプラットフォーム上のコアAdobe Commerceで問題を修正する
- 侵入テスト、脆弱性スキャン、ログなど、セキュリティ上の脅威を明らかにする可能性のあるすべてのアプリケーションアクティビティの監視
- セキュリティインシデントの監視と対応 ( 商家のAdobe Commerce an cloud infrastructure ソリューションとユーザーアカウントに関する法医学、修復、レポート作成など )
- DNS プロバイダーの取得と、マーチャント固有の DNS レコードの設定と管理
- カスタマイズされたアプリケーションでのパフォーマンステストの実行
- プラットフォームアカウント、インスタンスアクセス、およびアプリケーションへのアクセスの保護
- カスタムアプリケーションのテストと QA
- マーチャントがクラウドインフラストラクチャアプリケーション上のAdobe Commerceに接続するシステムまたはネットワークのセキュリティの維持

## クラウドサービスプロバイダーの責務

Adobeは、クラウドインフラストラクチャ上でAdobe Commerceのクラウドサーバーインフラストラクチャをホストするために、確立されたクラウドサービスプロバイダーに依存しています。 これらのプロバイダは、ファイアウォールシステムや侵入検出システム (IDS) を介したルーティング、スイッチング、境界ネットワークセキュリティを含む、ネットワークのセキュリティを担当します。 クラウドサービスプロバイダーは、クラウドインフラストラクチャソリューション上でAdobe Commerceをホストするデータセンターの物理的セキュリティと、データセンターの環境セキュリティにも責任を負います。

クラウドサービスプロバイダーは、以下も担当します。

- クラウドサービスの PCI DSS、SOC 2、ISO 27001認定の維持
- ハイパーバイザの保護
- 物理アクセスとネットワークアクセスの両方を含むデータセンターの保護

## CDN プロバイダーの責務

Adobe Commerce on cloud infrastructure ソリューションでは、CDN プロバイダーを使用して、ページ読み込み時間を短縮し、コンテンツをキャッシュし、古いコンテンツを即座にパージします。 また、これらのプロバイダーは、CDN に直接関連する（または CDN に影響を与える）セキュリティ上の問題や、CDN WAF ルールの定義と管理を担当します。

## セキュリティ責任のグラフ

次の表は、RACI モデル（R — 責任、A — 責任、C — 相談、I — 情報）を使用して、クラウドインフラストラクチャの共有責任モデルに関するAdobe Commerceのセキュリティ責任に関する各関係者を視覚的に表現しています。

<table>
<thead>
  <tr>
    <th>タスク</th>
    <th>Adobe</th>
    <th>商人</th>
    <th>クラウドサービスプロバイダー</th>
    <th>CDN プロバイダー</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>クラウドインフラストラクチャのパッチにAdobe Commerceを適用する</td>
    <td>C</td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>サポートサービスへのパッチの適用<br>（例：Nginx、MySQL）</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>原点 WAF ルールの定義</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>CDN WAF ルールの定義</td>
    <td>A</td>
    <td></td>
    <td></td>
    <td>R</td>
  </tr>
  <tr>
    <td>プラットフォーム WAF ルールのデプロイ</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>CDN WAF ルールのデプロイ</td>
    <td>A</td>
    <td>I</td>
    <td></td>
    <td>R</td>
  </tr>
  <tr>
    <td>クラウドインフラストラクチャコード上のAdobe Commerceのコアバグの修正</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>クラウドインフラストラクチャのパッチでAdobe Commerceをリリース</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>拡張（計算とストレージ）</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>スケーリング（PaaS/グリッド）</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>repo.magento.comを含むソースコードへのアクセスを確保する</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>クラウドインフラストラクチャへのAdobe Commerceのインストール CLI ツール</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>クラウドインフラストラクチャ設定ファイル上のAdobe Commerceをリポジトリに追加中</td>
    <td>C</td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>マーチャント向けプロジェクトの作成（オンボーディング UI）</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>クラウドインフラストラクチャ上のAdobe Commerceにリポジトリーを接続中</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>ソースリポジトリの設定<sup>1</sup></td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>リリースマネージャー用のユーザーの作成（オンボーディング UI）</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>コードの実稼動環境へのデプロイ</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>ステージングへのコードのデプロイ</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>外部アプリケーションと拡張機能の統合</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>拡張機能のインストール</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>クラウドインフラストラクチャ上のAdobe Commerceのカスタマイズ</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>クラウドインフラストラクチャ上でカスタマイズされたAdobe Commerceのパフォーマンスをテストする</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>カスタマイズされたアプリケーションのテスト</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>カスタムアプリケーションのテーマとデザイン</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
    <tr>
    <td>カスタム Vanrish VCL の作成、展開、およびテスト</td>
    <td>C</td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>DNS の設定（プラットフォームインフラストラクチャのみ）</td>
    <td>R</td>
    <td>C</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>CDN 拡張機能の開発とバグの修正</td>
    <td>A</td>
    <td>C</td>
    <td></td>
    <td>R</td>
  </tr>
  <tr>
    <td>オンボーディング CDN</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>サポート CDN<sup>2</sup></td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td>C</td>
  </tr>
  <tr>
    <td>New Relic APM/インフラストラクチャの設定</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>New Relic APM/インフラストラクチャのインストール</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>New Relic APM/インフラストラクチャのサポート</td>
    <td>R</td>
    <td>C</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Nginx の設定<sup>3</sup></td>
    <td>R</td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>DNS プロバイダーの取得（Pro のみ）</td>
    <td>C</td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>OS の堅牢化</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>実稼動環境とステージング環境のプロビジョニング</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>クラウドインフラストラクチャ上のAdobe Commerceの Zendesk へのアクセス</td>
    <td>R</td>
    <td>C</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>マーチャントセキュリティの問題の解決</td>
    <td>C</td>
    <td>R</td>
    <td></td>
    <td>C</td>
  </tr>
  <tr>
    <td>クラウドインフラストラクチャのセキュリティに関するAdobe Commerceの問題の解決</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>CDN セキュリティの問題の解決</td>
    <td>A</td>
    <td></td>
    <td></td>
    <td>R</td>
  </tr>
  <tr>
    <td>APM のセキュリティ問題の解決</td>
    <td>A</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Adobeのセキュリティ調査（ソフトウェア）の支援</td>
    <td>R</td>
    <td>C</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Adobeのセキュリティ調査（スキャン/監査）の支援</td>
    <td>R</td>
    <td>C</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>PCI ASV スキャンの実行</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>クラウドインフラストラクチャの PCI スキャンに関するAdobe Commerceの修復<sup>4</sup></td>
    <td>R</td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>PaaS PCI スキャンの修正</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>OS とプラットフォームの秘密鍵の管理</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>クラウドインフラストラクチャの暗号化キーでのAdobe Commerceの管理</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>クラウドインフラストラクチャインスタンス上のカスタマイズされたAdobe Commerceのスキャン</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>セキュリティログの監視</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>クラウドインフラストラクチャ上のAdobe Commerceの IAM と権限の管理</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>サポートアクセス制御の管理（テレポート）</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>マーチャントサポートとアクセスの制御</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>AdobeDR 計画とバックアップ/リストアに関する年次テストとドキュメント化</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>災害復旧計画の年次テストとドキュメント化</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
</tbody>
<tfoot>
  <tr>
    <td colspan="5">
      <p><sup><strong>1</strong></sup> クラウドインフラストラクチャ上のAdobe Commerceリポジトリをメインリポジトリとして使用する場合のみ。 他の外部リポジトリの使用は、マーチャントの唯一の責任です。</p>
      <p><sup><strong>2</strong></sup> Adobeは、CDN プロバイダーに関する問題に対してレベル 1 のサポートを提供します。</p>
      <p><sup><strong>3</strong></sup> 一部の Ngnix コントロールは、マーチャントがアプリケーションに対して設定し、その責任を負います。</p>
      <p><sup><strong>4</strong></sup> PCI の場合、侵入テスト要件はAdobeとマーチャント間で共有されます。</p>
    </td>
  </tr>
</tfoot>
</table>
