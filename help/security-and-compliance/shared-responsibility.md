---
title: 共有責任セキュリティと運用モデル
description: Adobe Commerce on cloud infrastructure プロジェクトに関与する各パーティのセキュリティ上の責任について説明します。
exl-id: f3cc1685-e469-4e30-b18e-55ce10dd69ce
source-git-commit: fcaf6ff1dce1c1a5084307cd366ca58d71a8f4e4
workflow-type: tm+mt
source-wordcount: '2850'
ht-degree: 0%

---

# 共有責任セキュリティと運用モデル

クラウドインフラストラクチャー上のAdobe Commerceは、責任分担のセキュリティと運用モデルに基づく、サービスとしてのプラットフォーム（PaaS）製品です。 これらの責務は、Adobe、マーチャント、Cloud Service プロバイダーおよびコンテンツ配信ネットワーク（CDN）プロバイダーの間で共有されます。 各関係者は、Adobe Commerce アプリケーションと、クラウドインフラストラクチャにデプロイされたマーチャント固有のコードおよび拡張機能を保護および運用する明確な責任を負います。

この共有モデルを使用すると、マーチャントは、運用に関する責任とコストを最小限に抑えながら、ビジネス要件を満たす柔軟性とカスタマイズ性に優れた拡張性の高いソリューションを設計および実装できます。

>[!VIDEO](https://video.tv.adobe.com/v/3458392/?learn=on&enablevpops)

一般に、Adobeは次の役割を担います。

- セキュアなコアアプリケーションコードの開発と保守
- プラットフォームのセキュリティの維持
- プラットフォームが SOC 2 および PCI に準拠し、PCI に準拠したテクノロジーコンポーネント（PHP、Redis など）と互換性があることを確認する
- コアプラットフォームに関するセキュリティ課題への対応
- クラウドサービスプロバイダーおよび CDN パートナーと協力して、発生した問題を解決する

マーチャントは、次の操作を行います。

- カスタムコードのセキュリティ維持とサードパーティアプリケーションとの統合
- 安全なアプリケーション開発の確保
- 加盟店の支払い処理者から要求があった場合に PCI 認定を取得する
- セキュリティインシデントへの対応と対応

## Adobeの責任

Adobeは、クラウドインフラストラクチャ環境におけるAdobe Commerceのセキュリティと可用性、およびコアソリューションコードに対して責任を負います。 さらに、Adobeは、クラウドインフラストラクチャソリューション上のAdobe Commerceのセキュリティを維持するために必要な、次のようなアクティビティおよびメカニズムを管理する責任を負います。

- クラウドデータストレージや検索機能など、クラウドインフラストラクチャー上のAdobe Commerceでサポートされているアプリケーションに対するサーバーレベルのセキュリティとパッチの適用
- クラウドインフラストラクチャコードでのコア Adobe Commerceの侵入テストとスキャンの実施
- パブリッククラウドサービスプロバイダーの IAM （Identity and Access Management）ソリューションおよび権限管理（PCI コンプライアンス要件）に関する半年ごとのレビューと監査の実施
- Adobeの社員や請負業者を含む、権限を持つユーザーの半年ごとのレビューおよび監査を実施（PCI コンプライアンス要件）
- バックアップ/リストア機能に関する年 1 回のテストとドキュメント化の実施
- サーバーおよび境界ファイアウォールの構成
- クラウドインフラストラクチャリポジトリ上のAdobe Commerceの接続と設定
- Adobeの担当範囲内の領域における災害復旧（DR）計画の定義、テスト、導入、文書化
- グローバルプラットフォーム web アプリケーションファイアウォール（WAF）ルールの定義
- オペレーティングシステム（OS）の堅牢化
- クラウドインフラストラクチャー上のAdobe Commerceを使用した、コンテンツ配信ネットワーク（CDN）およびアプリケーションパフォーマンス管理（APM）ソリューションの統合の実装と管理
- Cloud Infrastructure コード上のコア Adobe Commerceに対して、定期的なセキュリティ更新およびその他の更新を行います（パッチの適用はマーチャントの責任です）。
- マーチャントサポートの管理とアクセス制御のサポート（Zendesk など）
- クラウドインフラストラクチャプラットフォームインフラストラクチャ上のAdobe Commerceに関するセキュリティインシデントの監視、ログ記録、修正
- プラットフォームの運用を監視し、クラウドインフラストラクチャー上のマーチャントに対して 24 時間年中無休のAdobe Commerceのサポートを提供
- 実稼動環境とステージング環境のプロビジョニング
- プラットフォームの運用とインフラストラクチャに対する潜在的なセキュリティ上の脅威の評価
- マーチャントとのサービスレベル契約（SLA）に記載されているように、コンピューティング、ストレージ、グリッド、その他のリソースを拡張する
- DNS の設定（クラウドインフラストラクチャプラットフォームインフラストラクチャ上のAdobe Commerceのみ）
- プラットフォームのセキュリティの脆弱性に対するテスト

Adobeは、Adobe Commerce ソリューションに使用されるインフラストラクチャとサービスについて、PCI 認定を維持しています。  マーチャントは、カスタムコード、システムおよびネットワークプロセス、組織のコンプライアンスに責任を負います。

また、Adobeは、該当するSLAで合意された通りにマーチャントのインフラストラクチャの可用性を確保します。

## 販売者の責任

マーチャントは、クラウドインフラストラクチャソリューション上のAdobe Commerceのカスタマイズされた特定のインスタンスに対して、次のセキュリティのベストプラクティスに従う責任があります。

- 必要なAdobe Commerce on cloud infrastructure 設定ファイルのリポジトリへの追加
- Adobeによるリリース直後に、カスタム Adobe Commerce on cloud infrastructure ソリューションにセキュリティおよび他のパッチを適用する
- ベンダーがリリースした直後に、すべてのカスタム拡張機能およびコードにセキュリティおよびその他のパッチを適用する
- カスタム Varnish VCL ファイルを作成、配置、テストする
- すべてのカスタム拡張機能とコードを含む、クラウドインフラストラクチャソリューション上でカスタマイズされたAdobe Commerceの設計、テーマ設定、インストール、統合、保護
- クラウドインフラストラクチャ設定、アプリケーション、およびプラットフォーム上のAdobe Commerceのマーチャントインスタンスへのユーザーアクセスの許可と取り消し
- 加盟店の内部ネットワーク、サーバー、インフラストラクチャ、およびクラウドインフラストラクチャプラットフォーム上のAdobe Commerce上に構築されたカスタムアプリケーションに関連するセキュリティの問題の処理
- クラウドインフラストラクチャー上のAdobe Commerceのコマンドライン統合（CLI）ツールのインストール
- PCI-DSS ガイドラインの定義に従って、カスタマイズされたアプリケーションおよびその他の内部プロセスの必要なレベルの PCI コンプライアンスを維持する

  >[!NOTE]
  >
  >確認が必要な領域を最小限に抑えるために、マーチャントの PCI コンプライアンスは、Adobe Commerceとクラウドホスティングプロバイダーの PCI 認定に基づいて構築されています。

- PCI ASV スキャンの実行と、クラウドインフラストラクチャコードおよびプラットフォーム上のコアAdobe Commerceの問題の修正
- 侵入テスト、脆弱性スキャン、ログなど、セキュリティ上の脅威となる可能性のあるすべてのアプリケーションアクティビティを監視する
- セキュリティに関するインシデントの監視と対応（法医学、修正、および販売員のクラウドインフラストラクチャソリューションおよびユーザーアカウントに関するAdobe Commerceに関するレポートを含む）
- DNS プロバイダーを取得し、マーチャント固有の DNS レコードを設定および管理する
- カスタマイズされたアプリケーションでのパフォーマンステストの実行
- Platform アカウント、インスタンスへのアクセス、アプリケーションへのアクセスの保護
- カスタムアプリケーションのテストと QA
- マーチャントがクラウドインフラストラクチャアプリケーション上のAdobe Commerceに接続するシステムまたはネットワークのセキュリティの維持

## Cloud Service プロバイダーの責任

Adobeは、Adobe Commerceのクラウドサーバーインフラストラクチャをクラウドインフラストラクチャ上にホストするために、確立されたクラウドサービスプロバイダーを利用しています。 これらのプロバイダーは、ルーティング、スイッチング、およびファイアウォール システムや侵入検知システム（IDS）を介した境界ネットワーク セキュリティを含む、ネットワークのセキュリティを担当します。 また、クラウドサービスプロバイダーは、Adobe Commerce on cloud infrastructure ソリューションをホスティングするデータセンターの物理的セキュリティと、データセンターの環境セキュリティも担当します。

クラウドサービスプロバイダーは、次の責任も負います。

- クラウドサービスに関する PCI DSS、SOC 2、ISO 27001 認定の維持
- ハイパーバイザの保護
- 物理アクセスとネットワーク・アクセスの両方を含むデータ・センターの保護

## CDN プロバイダーの責任

クラウドインフラストラクチャー上のAdobe Commerce ソリューションでは、CDN プロバイダーを使用して、ページ読み込み時間の短縮、コンテンツのキャッシュ、古いコンテンツの即時パージを行います。 また、これらのプロバイダーは、CDN に直接関連する、または CDN に影響を与えるセキュリティの問題や、CDN WAFのルールを定義および管理する責任も負います。

## セキュリティ責任の概要

>[!BEGINSHADEBOX]

次の概要の表では、RACI モデルを使用して、Adobe、マーチャントおよび Cloud Service プロバイダー間で共有されるセキュリティ責任を示します。

**R** – 担当
**A** — Accountable
**C** – 問い合わせ
**I** – 情報

>[!ENDSHADEBOX]

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
    <td>クラウドインフラストラクチャパッチへのAdobe Commerceの適用</td>
    <td>C</td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>サポートサービス <br> （Nginx や MySQL など）へのパッチの適用</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>接触チャネルWAFルールの定義</td>
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
    <td>Platform WAF ルールのデプロイ</td>
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
    <td>クラウドインフラストラクチャー上のAdobe Commerce パッチのリリース</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>スケーリング（コンピューティングとストレージ）</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>拡大縮小（PaaS とグリッド）</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>repo.magento.comを含むソースコードへのアクセスの確保</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>クラウドインフラストラクチャ CLI ツールへのAdobe Commerceのインストール</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Adobe Commerce on cloud infrastructure 設定ファイルのリポジトリーへの追加</td>
    <td>C</td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>マーチャントのプロジェクトの作成（オンボーディング UI）</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>クラウドインフラストラクチャー上のAdobe Commerceへのリポジトリの接続</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>ソースリポジトリの設定 <sup>1</sup></td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>リリースマネージャーのユーザーの作成（オンボーディング UI）</td>
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
    <td>クラウドインフラストラクチャー上のAdobe Commerceのカスタマイズ</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>クラウドインフラストラクチャー上でのカスタマイズされたAdobe Commerceのパフォーマンステスト</td>
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
    <td>カスタムアプリケーションのテーマ設定とデザイン</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
    <tr>
    <td>カスタム Varnish VCL の作成、デプロイ、テスト</td>
    <td>C</td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>DNS の設定（Platform インフラストラクチャのみ）</td>
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
    <td>CDN<sup>2</sup> のサポート</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td>C</td>
  </tr>
  <tr>
    <td>New Relicの APM およびインフラストラクチャアプリケーションの設定</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>New Relicの APM およびインフラストラクチャアプリケーションのインストール</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>New Relicの APM およびインフラストラクチャアプリケーションのサポート</td>
    <td>R</td>
    <td>C</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Nginx<sup>3</sup> の設定</td>
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
    <td>クラウドインフラストラクチャー上の Zendesk for Adobe Commerceへのアクセス</td>
    <td>R</td>
    <td>C</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>販売者のセキュリティ問題の解決</td>
    <td>C</td>
    <td>R</td>
    <td></td>
    <td>C</td>
  </tr>
  <tr>
    <td>クラウドインフラストラクチャー上のAdobe Commerceのセキュリティの問題の解決</td>
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
    <td>APM セキュリティの問題の解決</td>
    <td>A</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>セキュリティ調査によるAdobeの支援（ソフトウェア）</td>
    <td>R</td>
    <td>C</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Adobeのセキュリティリサーチの支援（スキャン/監査）</td>
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
    <td>クラウドインフラストラクチャー上のAdobe Commerceの修正 PCI スキャン <sup>4</sup></td>
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
    <td>OS およびプラットフォームの秘密鍵の管理</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>クラウドインフラストラクチャー上のAdobe Commerceの暗号化キーの管理</td>
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
    <td>クラウドインフラストラクチャー上のAdobe Commerceに対する IAMand 権限の管理</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>サポートのアクセス制御の管理（テレポート）</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>マーチャントのサポートとアクセスの制御</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Adobe DR 計画およびバックアップ/リストアの年間テストと文書化</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>ディザスタリカバリ計画の年 1 回のテストと文書化</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
</tbody>
<tfoot>
  <tr>
    <td colspan="5">
      <p><sup><strong>1</strong></sup> Adobe Commerce on Cloud Infrastructure リポジトリーがメインリポジトリーとして使用されている場合のみ。 その他の外部リポジトリの使用は、マーチャントの単独の責任です。</p>
      <p><sup><strong>2</strong></sup> Adobeは、CDN プロバイダーに関する問題に対してレベル 1 のサポートを提供します。</p>
      <p><sup><strong>3</strong></sup> マーチャントは、マーチャントがアプリケーション用に設定する Ngnix 制御に対して責任を負います。</p>
      <p><sup><strong>4</strong></sup> PCI の場合、侵入テストの要件はAdobeとマーチャントの間で共有されます。</p>
    </td>
  </tr>
</tfoot>
</table>

## 運用責任の概要

>[!BEGINSHADEBOX]

次の概要の表では、クラウドインフラストラクチャ上でAdobeを開発、デプロイ、メンテナンス、保護する際の、Adobe Commerceとマーチャントの運用上の責任を明確にします。

>[!ENDSHADEBOX]

### コーディングと開発

#### コアAdobe Commerceコード

|     | Adobe | 商人 |
| --- | --- | --- |
| Adobe Commerce Core へのアップデートとパッチの公開 | R |     |
| ファイルシステムの可用性とパッチ適用 | R |  |
| ECE ツールへのアップデートとパッチの公開 | R |     |
| コア Adobe Commerce アプリケーションの品質 | R |     |

{style="table-layout:auto"}

#### コードリポジトリー

|     | Adobe | 商人 |
| --- | --- | --- |
| repo.magento.comの提供状況 | R |     |
| Cloud Git サーバー上のAdobe Commerceの可用性 | R |     |
| マーチャントが選択した他のコードリポジトリ（GitHub、Bitbucket、ホストされた Git サーバー） |     | R |

{style="table-layout:auto"}

#### Cloud Docker

|     | Adobe | 商人 |
| --- | --- | --- |
| Cloud Docker コンテナをダウンロード可能にする | R |   |
| Cloud Docker のデプロイメントとセットアップ（オプション） |     | R |
| その他のローカル開発設定 |     | R |

{style="table-layout:auto"}

#### COMMERCE CLOUD CLI

|     | Adobe | 商人 |
| --- | --- | --- |
| ECE ツールの継続的な品質と更新 | R |   |
| 最新バージョンの ECE ツールのインストール |     | R |

{style="table-layout:auto"}

#### カスタマイズ

|  | Adobe | 商人 |
| --- | --- | --- |
| カスタム Adobe Commerce モジュールおよびコード |     | R |
| 拡張機能 |     | R |
| カスタム統合 |     | R |

{style="table-layout:auto"}

#### デプロイメント

|     | Adobe | 商人 |
| --- | --- | --- |
| コードを構築およびデプロイするためのインフラストラクチャの可用性 | R |   |
| インフラストラクチャの継続的な品質のビルド&amp;デプロイ設定パイプライン | R |   |
| ビルドおよび静的コンテンツのデプロイメントの設定 |     | R |
| デプロイメントガバナンスプロセスの構築と実行：条件と変更管理 |     | R |
| ステージング環境へのデプロイ |     | R |
| 実稼動環境へのデプロイ |     | R |
| 実稼動のロールバック |     | R |

{style="table-layout:auto"}

#### 環境の同期

マーチャントは、環境間でデータを同期する役割を担います。

#### パッチ適用

|     | Adobe | 商人 |
| --- | --- | --- |
| ECE-Tools へのアップデートとパッチのインストール |     | R |
| Adobe Commerce Core へのアップデートとパッチのインストール |     | R |

#### Web サイトの可用性

|  | Adobe | 商人 |
| --- | --- | --- |
| カスタマイズされたAdobe Commerce アプリケーションおよび関連する web サイト |     | R |

#### パフォーマンス

|     | Adobe | 商人 |
| --- | --- | --- |
| コアアプリケーションのチューニングと最適化 | R |   |
| カスタムコードのチューニングと最適化 |     | R |
| カスタム Adobe Commerce コード |     | R |
| 負荷テスト |     | R |
| パフォーマンステスト |     | R |

{style="table-layout:auto"}


#### ログと監視

|     | Adobe | 商人 |
| --- | --- | --- |
| ログの回転 | R |   |
| カスタム Adobe Commerce アプリケーション | | R |
| New Relic サービスの可用性：<br>APM アプリケーションとエージェントの統合、インフラストラクチャアプリケーション、<br> ログと統合 | R |   |
| New Relic アラートの設定 |     | R |
| PaaS サーバーへのNew Relic エージェントのデプロイ | R |  |

{style="table-layout:auto"}

#### デバッグとイシューの分離

|     | Adobe | 商人 |
| --- | --- | --- |
| デバッグとイシューの分離 | R | R |
| デバッグと問題の分離プロセスをタイムリーにサポート |     | R |

{style="table-layout:auto"}

### アプリケーションとサービスの設定

#### Commerce アプリケーション

|     | Adobe | 商人 |
| --- | --- | --- |
| アプリケーション設定 |     | R |
| Adobe Commerce アプリケーションへのドメインの追加（ベース URL） |     | R |
| デプロイされたAdobe Commerce バージョンでサポートされているサービスバージョンを使用するように PaaS を設定する <br><br> 例えば、Commerceの異なるバージョンは、PHP、Redis などの特定のバージョンと互換性があります。 |     | R |

{style="table-layout:auto"}

#### Cron ジョブを使用したタスクスケジュール

|     | Adobe | 商人 |
| --- | --- | --- |
| デフォルトの cron ジョブの可用性 | R | |
| カスタム cron ジョブの継続的な品質 |  | R |

{style="table-layout:auto"}

#### メッセージ キューフレームワーク用メッセージ ブローカ

|     | Adobe | 商人 |
| --- | --- | --- |
| RabbitMQ サービスの提供 | R |   |
| デフォルトの RabbitMQ 設定 | R |   |
| RabbitMQ の継続的な品質とパッチ適用 | R |   |
| インストールされたAdobe Commerceと互換性のある RabbitMQ バージョンをインストールするために、サービスリクエストを送信します。 |   | R |

{style="table-layout:auto"}

#### PHP サービス

|     | Adobe | 商人 |
| --- | --- | --- |
| PHP の可用性 | R |   |
| デフォルトの PHP 設定 | R |     |
| カスタム PHP 設定の構成 |     | R |
| PHP バージョンとインストールされたAdobe Commerce バージョンの互換性を維持するための YAML ファイルの設定 |    | R |

{style="table-layout:auto"}

#### データベースサービス

|     | Adobe | 商人 |
| --- | --- | --- |
| Galera および MariaDB サービスの可用性 | R | |
| デフォルトのデータベース設定の継続的なメンテナンス <br><br> コアテーブルのインデックス作成と最適化、デフォルトのシステム管理者設定の最適化） | R |   |
| マーチャントデータと変更された設定の継続的なメンテナンス <br><br> （正規化されたテーブルとフラットテーブルの設定、カスタムおよびサードパーティ製テーブルのインデックス作成と最適化、データのアーカイブまたは削除、システム管理設定の設定） |     | R |
| Galera と MySQL の設定 | R |   |
| Galera と MariaDB の継続的な品質とパッチ適用 | R |   |
| 継続的なインフラストラクチャの最適化 | R |   |
| 処理に時間のかかるクエリの特定と修正 |     | R |
| インストールされたAdobe Commerceと互換性のある MariaDB バージョンをインストールするサービス リクエストを送信します。 |     | R |
| マーチャント固有のデータ保持ポリシーの設定と管理（Adobeのデータ保持ポリシーは、マーチャント契約で定義されます） |     | R |

{style="table-layout:auto"}

#### CDN サービス

|     | Adobe | 商人 |
| --- | --- | --- |
| CDN の可用性と品質 | R |   |
| Fastly サービス設定（拡張機能/API 経由） |     | R |
| Fastly 拡張機能の品質 | R |   |
| Fastly 統合 VCL スニペット（Fastly 拡張機能にバンドル）の品質 | R |   |
| ページキャッシュの最適化 |     | R |
| サービス、CDN およびインフラストラクチャへのドメインの追加 | R |   |
| カスタム VCL スニペット |     | R |
| WAFとWAFのルール | R |   |

{style="table-layout:auto"}

#### キャッシュサービス

|     | Adobe | 商人 |
| --- | --- | --- |
| Redis サービスの可用性 | R |   |
| デフォルト Redis 設定の構成 | R |   |
| Redis の継続的な品質とパッチ適用 | R |   |
| インストールされたAdobe Commerceバージョンと互換性のある Redis バージョンをインストールするために、サービスリクエストを送信します。 |     | R |

{style="table-layout:auto"}

#### 検索サービス

|     | Adobe | 商人 |
| --- | --- | --- |
| Elasticsearchの提供状況 | R |   |
| デフォルトのElasticsearch設定の指定 | R |   |
| インストールされたAdobe Commerceと互換性のあるElasticsearchのバージョンをインストールするために、サービスリクエストを送信する |  | R |

{style="table-layout:auto"}

#### メールサービス

|     | Adobe | 商人 |
| --- | --- | --- |
| SendGrid メールサービスとその統合の可用性 | R |   |
| 制限に対するマーチャントの SendGrid 使用状況の監視 | R |   |
| マーチャントは、送信トランザクションメールに対してのみサービスを使用する責任を負います <br> サービスはマーケティングメールの送信をサポートしていません。 |     | R |
| オプションのサードパーティ電子メールサービスの設定 |     | R |

{style="table-layout:auto"}

#### サードパーティのサービス

|     | Adobe | 商人 |
| --- | --- | --- |
| サードパーティのサービスの可用性と品質 |     | R |

{style="table-layout:auto"}

### Commerce サービス拡張機能

#### 事前通知サービス

|     | Adobe | 商人 |
| --- | --- | --- |
| Advanced Reporting Service の可用性 | R |   |
| 高度なレポートの設定は高度なレポート作成条件に準拠 |     | R |

{style="table-layout:auto"}

#### Commerce Intelligence

|     | Adobe | 商人 |
| --- | --- | --- |
| Adobe Commerce Business Intelligence サービスの可用性 | R |   |
| MBI データ同期プロセス | R |   |
| MBI 同期の問題の検出 | R |   |
| Adobe Commerce Cloud Pro、スターター、オンプレミス、非Adobe Commerceへの MBI データ同期の設定 <br> データしきい値を超えた場合の API、データ品質とフォーマット、マーチャントネットワーク、<br>Adobe Commerce Cloud DB 内外の DB 接続） |     | R |
| Adobe Commerce Cloud Pro への MBI データ同期の設定 <br> （Adobe Commerce Cloud データベース設定） | R |   |

{style="table-layout:auto"}

#### 製品レコメンデーション

|     | Adobe | 商人 |
| --- | --- | --- |
| Product Recommendations サービスの可用性 | R |   |

{style="table-layout:auto"}

#### Live Search

|     | Adobe | 商人 |
| --- | --- | --- |
| Live Search サービスの可用性 | R |   |

{style="table-layout:auto"}

#### 製品レコメンデーションとライブ検索出力を強化するストアフロントイベントの品質（データ収集）

|     | Adobe | 商人 |
| --- | --- | --- |
| コアテーマ（Luma） | R |   |
| カスタムテーマ |  | R |
| コア PWAの実装 | R |   |
| カスタム PWAの実装 |  | R |
| コア AEM EDS の実装（Commerce Boilerplate） | R |   |
| カスタム AEM EDS の実装 |  | R |
| その他のカスタムストアフロントの実装 |  | R |

{style="table-layout:auto"}

### ネットワークサービス

#### 画像の最適化

|     | Adobe | 商人 |
| --- | --- | --- |
| 画像最適化の可用性と品質 | R |  |
| 画像の最適化の設定 |     | R |

{style="table-layout:auto"}

#### SSL 証明書

|     | Adobe | 商人 |
| --- | --- | --- |
| SSL 専用証明書 – 有効期限 | R |  |
| SSL 証明書のプロビジョニング | R |  |
| EV/固有の SSL 証明書（デフォルトで指定されたものを除く）の購入と管理およびAdobeへの提供 |     | R |

{style="table-layout:auto"}

#### Web アプリケーションファイアウォール（WAF）

|     | Adobe | 商人 |
| --- | --- | --- |
| WAFの提供と設定 | R |  |
| WAF ルールの誤検出への対処 | R | |
| WAF ルールの偽陽性のレポート |     | R |
| WAFのルールチューニング （サポート対象外） |     |     |
| WAF/CDN ログ |     | R |

{style="table-layout:auto"}

#### DDOS

|     | Adobe | 商人 |
| --- | --- | --- |
| プロアクティブな IP ブロッキング |     | R |
| ボットの保護 |     | R |
| DDOS 検出 – レイヤ 3-4 | R |   |
| DDOS 検出 – レイヤ 7 |     | R |
| DDOS 応答 | R |   |

{style="table-layout:auto"}

#### プライベートリンク

|     | Adobe | 商人 |
| --- | --- | --- |
| Adobeが所有するVPCでの PrivateLink 接続の設定と管理（使用する場合） | R |   |
| マーチャントが所有するVPCでの PrivateLink 接続の設定と管理（使用する場合） |     | R |
| SSH （非プライベートリンク）の可用性 | R |   |
| Adobe Commerce Cloud Service エンドポイントに対する PrivateLink インバウンドの設定 | R |   |
| Adobe Commerce Cloud Service エンドポイントへの PrivateLink インバウンドの受け入れ |     | R |
| マーチャントのVPC サービスエンドポイントに対する PrivateLink インバウンドの設定 |     | R |
| マーチャントのVPC サービスエンドポイントに対する PrivateLink インバウンドの受け入れ | R |   |
| PrivateLink 統合の設定（アカウントへのエンドポイント） |     | R |
| PrivateLink エンドポイント <br><br> （すべての VPN 接続を含む）用のマーチャント所有VPCの設定 |     | R |

{style="table-layout:auto"}

### システムとインフラストラクチャ

#### アプリサーバー

|     | Adobe | 商人 |
| --- | --- | --- |
| Nginx の提供状況 | R |   |
| Nginx の設定 | R |   |
| Nginx の継続的な品質とパッチ適用 | R |   |

{style="table-layout:auto"}

#### オペレーティングシステム

|     | Adobe | 商人 |
| --- | --- | --- |
| オペレーティングシステムの可用性 | R |   |
| オペレーティングシステムの継続的な品質とパッチ適用 | R |   |

{style="table-layout:auto"}

#### バックアップ、高可用性、フェイルオーバー

|     | Adobe | 商人 |
| --- | --- | --- |
| スナップショットおよびバックアップ・プロセスの可用性 | R |   |
| Cloud Pro ステージング環境および実稼動環境のバックアップのスケジュール設定 | R |   |
| Cloud Starter および Pro 統合環境のバックアップのスケジュール |     | R |
| HA/フェイルオーバーの可用性 | R |   |

{style="table-layout:auto"}

#### クラウドサーバーとスケーリング

|     | Adobe | 商人 |
| --- | --- | --- |
| CPUのリソース、データセンター、ディスク容量の可用性 | R |   |
| サージ容量の可用性と実行、または緊急アップサイジング | R |   |
| サージ容量を要求しています |     | R |
| 制限に照らした vCPU 使用率の監視 | R |   |

{style="table-layout:auto"}
