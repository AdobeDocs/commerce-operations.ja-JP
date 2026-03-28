---
title: 責任セキュリティと運用モデルの共有
description: Adobe Commerce on cloud インフラストラクチャプロジェクトに関与する各パーティのセキュリティ責任について説明します。
exl-id: f3cc1685-e469-4e30-b18e-55ce10dd69ce
source-git-commit: 7054a5286f01e26e324401f4d8505e4e0faed93e
workflow-type: tm+mt
source-wordcount: '2939'
ht-degree: 0%

---

# 責任セキュリティと運用モデルの共有

Adobe Commerce on cloud infrastructureは、共通の責任セキュリティと運用モデルに依存するPaaS （Platform-as-a-Service）製品です。 これらの責任は、Adobe、マーチャント、クラウドサービスプロバイダー、コンテンツ配信ネットワーク（CDN）プロバイダー間で共有されます。 Adobe Commerceアプリケーションと、クラウドインフラストラクチャにデプロイされたマーチャント固有のコードおよび拡張機能のセキュリティと運用については、各当事者が明確な責任を負います。

この共有モデルにより、販売者は、運用上の責任とコストを最小限に抑えながら、ビジネス要件を満たす柔軟性が高く、カスタマイズ可能で、スケーラブルなソリューションを設計および導入できます。

>[!VIDEO](https://video.tv.adobe.com/v/3458393/?captions=jpn&learn=on&enablevpops)

一般的に、Adobeは次の責任を負います。

- セキュアコアアプリケーションコードの開発と保守
- プラットフォームのセキュリティの維持
- プラットフォームがSOC 2およびPCIに準拠し、PCI準拠のテクノロジーコンポーネント（PHP、Redisなど）と互換性があることを確認する
- コアプラットフォームに関するセキュリティ問題への対応
- クラウドサービスプロバイダーやCDN パートナーと協力して発生した問題を解決する

販売者は次の責任を負います：

- カスタムコードのセキュリティとサードパーティアプリケーションとの統合を維持する
- 安全なアプリケーション開発の確保
- 加盟店の決済代行会社から要求された場合、PCI認証を取得する
- セキュリティインシデントへの対応と対応

## Adobeの責任

Adobeは、Adobe Commerce on cloud インフラストラクチャ環境とコアソリューションコードのセキュリティと可用性を担当します。 さらに、Adobeは、次のようなAdobe Commerce on cloud インフラストラクチャソリューションのセキュリティを維持するために必要なアクティビティと仕組みを担当します。

- クラウドデータストレージや検索機能など、Adobe Commerceがクラウドインフラストラクチャ上でサポートするアプリケーションに対するサーバーレベルのセキュリティとパッチの適用
- クラウドインフラストラクチャコード上のコアAdobe Commerceの侵入テストとスキャンの実施
- パブリッククラウドサービスプロバイダーのIDおよびアクセス管理（IAM）ソリューションと権限管理（PCI コンプライアンス要件）に関する半年ごとのレビューと監査の実施
- Adobeの従業員および請負業者を含む、許可されたユーザーに対して半年に1回のレビューと監査を実施（PCI認定の要件）
- バックアップ/リストア機能に関する年間テストとドキュメント作成
- サーバーおよび境界ファイアウォールの設定
- Adobe Commerce on cloud infrastructure リポジトリの接続と設定
- Adobeの担当範囲内の地域に関する災害復旧（DR）計画を定義、テスト、実施、文書化する
- グローバルプラットフォーム web アプリケーションファイアウォール（WAF）ルールの定義
- オペレーティングシステム（OS）の強化
- Adobe Commerce on cloud infrastructureを使用した、コンテンツ配信ネットワーク（CDN）ソリューションとアプリケーションパフォーマンス管理（APM）ソリューションの統合の実装と維持
- コアのAdobe Commerce on cloud インフラストラクチャコードに対して、定期的にセキュリティやその他のアップデートを発行する（パッチの適用は販売者の責任です）
- 加盟店サポートおよびサポートアクセス制御の管理（例：Zendesk）
- Adobe Commerce on cloud infrastructure インフラストラクチャに関するセキュリティインシデントの監視、ログ記録、および修復
- Adobe Commerce on cloud infrastructureを利用するマーチャントは、プラットフォームの運用を監視し、いつでもサポートを提供できます
- 実稼動環境とステージング環境のプロビジョニング
- プラットフォームの運用とインフラに対する潜在的なセキュリティ脅威を評価する
- 加盟店とのSLA （サービスレベル契約）で説明されているように、コンピューティング、ストレージ、グリッドなどのリソースの拡張
- DNSの設定（クラウドインフラストラクチャインフラストラクチャ上のAdobe Commerceのみ）
- セキュリティ脆弱性に対するプラットフォームのテスト

Adobeでは、Adobe Commerce ソリューションに使用されるインフラストラクチャとサービスに対するPCI認定を維持しています。  加盟店は、カスタムコード、システムおよびネットワークプロセス、組織のコンプライアンスに責任を持ちます。

Adobeは、該当するSLAで合意されている加盟店のインフラストラクチャの可用性も保証します。

## 加盟店の責任

Adobe Commerce on cloud インフラソリューションの特定のカスタムインスタンスについて、次のセキュリティのベストプラクティスを実施します。

- 必要なAdobe Commerce on cloud infrastructure設定ファイルをリポジトリに追加する
- Adobeによるリリース直後に、カスタムのAdobe Commerce on cloud infrastructure ソリューションにセキュリティやその他のパッチを適用する
- ベンダーによるリリース後すぐに、あらゆるカスタム拡張機能とコードにセキュリティやその他のパッチを適用する
- カスタム Varnish VCL ファイルの作成、デプロイ、テスト
- あらゆるカスタム拡張機能やコードを含む、カスタマイズされたAdobe Commerce on cloud インフラストラクチャソリューションの設計、テーマ設定、インストール、統合、保護
- Adobe Commerce on cloud infrastructure configuration, application, and platformのマーチャントのインスタンスへのユーザーアクセス権の付与と取り消し
- Adobe Commerce on cloud infrastructure プラットフォーム上で構築された、加盟店の内部ネットワーク、サーバー、インフラストラクチャ、およびカスタムアプリケーションに関連するセキュリティ問題を処理します
- Adobe Commerce on cloud infrastructure コマンドライン統合（CLI）ツールのインストール
- PCI-DSS ガイドラインで定義されている、カスタマイズされたアプリケーションやその他の社内プロセスのPCI コンプライアンス要件を維持する

  >[!NOTE]
  >
  >確認が必要な項目を最小限に抑えるために、Adobe CommerceのPCI認証とクラウドホスティングプロバイダーに基づいて、加盟店のPCI認定を取得する必要があります。

- PCI ASV スキャンを実行し、クラウドインフラストラクチャのコードとプラットフォーム上のコア Adobe Commerceの問題を修正する
- 侵入テスト、脆弱性スキャン、ログなど、潜在的なセキュリティ脅威を明らかにする可能性のあるすべてのアプリケーションアクティビティを監視します
- 加盟店のAdobe Commerce on cloud インフラストラクチャソリューションとユーザーアカウントに関連するフォレンジック、修復、レポートなど、セキュリティインシデントの監視と対応
- DNS プロバイダーを取得し、マーチャント固有のDNS レコードを設定および管理する
- カスタマイズされたアプリケーションでのパフォーマンステストの実行
- プラットフォームアカウント、インスタンスへのアクセス、アプリケーションへのアクセスの保護
- カスタムアプリケーションのテストとQA
- Adobe Commerce on cloud インフラストラクチャアプリケーションに接続するシステムやネットワークのセキュリティを維持する

## Cloud Service プロバイダーの責任

Adobeは、Adobe Commerceのクラウドサーバーインフラストラクチャをクラウドインフラストラクチャ上でホストするために、確立されたクラウドサービスプロバイダーに依存しています。 これらのプロバイダーは、ファイアウォールシステムや侵入検知システム（IDS）を介したルーティング、スイッチング、周辺ネットワークのセキュリティなど、ネットワークのセキュリティを担当しています。 クラウドサービスプロバイダーは、Adobe Commerce on cloud インフラストラクチャソリューションをホストするデータセンターの物理的なセキュリティと、データセンターの環境セキュリティにも責任を負います。

クラウドサービスプロバイダーには、次のような責任もあります。

- クラウドサービスのPCI DSS、SOC 2、ISO 27001認証を維持する
- ハイパーバイザの保護
- 物理アクセスとネットワークアクセスの両方を含むデータセンターの保護

## CDN プロバイダーの責任

Adobe Commerceのクラウドインフラストラクチャソリューションは、CDN プロバイダーを利用して、ページの読み込み時間を短縮し、コンテンツをキャッシュして、古いコンテンツを即座に削除します。 また、これらのプロバイダーは、CDNに直接関連する、または影響を与えるセキュリティの問題、およびCDN WAF ルールの定義と保守についても責任を負います。

## セキュリティ責任の概要

>[!BEGINSHADEBOX]

次のサマリーテーブルでは、RACI モデルを使用して、Adobe、マーチャント、およびCloud Service プロバイダー間で共有されるセキュリティ責任を示します。

**R** – 責任
**A** – 説明責任
**C** — コンサルテーション済み
**I** – 通知

>[!ENDSHADEBOX]

<table>
<thead>
  <tr>
    <th>タスク</th>
    <th>Adobe</th>
    <th>加盟店</th>
    <th>クラウドサービスプロバイダー</th>
    <th>CDN プロバイダー</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Adobe Commerce オンクラウドインフラストラクチャのパッチの適用</td>
    <td>C</td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>サポートサービスへのパッチの適用<br> （例：NginxまたはMySQL）</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>オリジンWAF ルールの定義</td>
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
    <td>Adobe Commerce on cloud インフラストラクチャのパッチのリリース</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>スケーリング（計算とストレージ）</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>拡大・縮小（PaaSとグリッド）</td>
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
    <td>Adobe Commerce on cloud infrastructure CLI ツールのインストール</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>クラウドインフラストラクチャ設定ファイルへのAdobe Commerceのリポジトリへの追加</td>
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
    <td>クラウドインフラストラクチャ上のAdobe Commerceへのリポジトリの接続</td>
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
    <td>リリースマネージャーのユーザーの作成（オンボーディング UI）</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>本番環境へのコードのデプロイ</td>
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
    <td>外部アプリケーションや拡張機能の統合</td>
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
    <td>クラウド基盤でのAdobe Commerceのカスタマイズ</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>クラウド基盤でのAdobe Commerceのカスタマイズされたパフォーマンスのテスト</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>カスタマイズしたアプリケーションのテスト</td>
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
    <td>カスタム Varnish VCLの作成、デプロイ、テスト</td>
    <td>C</td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>DNSの設定（プラットフォームインフラストラクチャのみ）</td>
    <td>R</td>
    <td>C</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>CDN拡張機能の開発とバグの修正</td>
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
    <td>サポートしているCDN<sup>2</sup></td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td>C</td>
  </tr>
  <tr>
    <td>New Relic APMおよびインフラストラクチャアプリケーションの設定</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>New Relic APMおよびインフラストラクチャアプリケーションのインストール</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>New Relic APMおよびインフラアプリケーションをサポート</td>
    <td>R</td>
    <td>C</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Nginx<sup>3</sup>の設定</td>
    <td>R</td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>DNS プロバイダーの取得（Proのみ）</td>
    <td>C</td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>OSの強化</td>
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
    <td>Zendesk for Adobe Commerce on cloud infrastructureへのアクセス</td>
    <td>R</td>
    <td>C</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>加盟店のセキュリティ問題を解決する</td>
    <td>C</td>
    <td>R</td>
    <td></td>
    <td>C</td>
  </tr>
  <tr>
    <td>クラウドインフラストラクチャのセキュリティ問題に対するAdobe Commerceの解決</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>CDN セキュリティの問題を解決する</td>
    <td>A</td>
    <td></td>
    <td></td>
    <td>R</td>
  </tr>
  <tr>
    <td>APMのセキュリティ問題の解決</td>
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
    <td>セキュリティ調査（スキャン/監査）によるAdobeのサポート</td>
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
    <td>クラウドインフラストラクチャ上のAdobe CommerceのPCI スキャンの修復<sup>4</sup></td>
    <td>R</td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>PaaS PCI スキャンの修復</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>OSとプラットフォームのシークレットの管理</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>クラウドインフラストラクチャ暗号化キーでのAdobe Commerceの管理</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>カスタマイズされたAdobe Commerce on cloud infrastructure インスタンスのスキャン</td>
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
    <td>クラウドインフラストラクチャでのAdobe CommerceのIAMと権限の管理</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>サポートアクセス制御の管理（Teleport）</td>
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
    <td>Adobe DRの計画とバックアップおよび復元に関する年間テストとドキュメント</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>災害復旧計画の年間テストと文書化</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
</tbody>
<tfoot>
  <tr>
    <td colspan="5">
      <p><sup><strong>1</strong></sup> Adobe Commerce オンクラウド インフラストラクチャ リポジトリがメイン リポジトリとして使用されている場合のみ。 その他の外部リポジトリの使用は、販売者の唯一の責任です。</p>
      <p><sup><strong>2</strong></sup> Adobeは、CDN プロバイダーの問題に対してレベル 1のサポートを提供します。</p>
      <p><sup><strong>3</strong></sup>販売者は、アプリケーション用に構成するNgnix コントロールを担当します。</p>
      <p><sup><strong>4</strong></sup> PCIの場合、Adobeと販売店の間で侵入テストの要件が共有されます。</p>
    </td>
  </tr>
</tfoot>
</table>

## 運用上の責任の概要

>[!BEGINSHADEBOX]

次の概要表は、クラウドインフラストラクチャ上のAdobe Commerceの開発、デプロイ、保守、保護におけるAdobeとマーチャントの運用上の責任を明確に示しています。

>[!ENDSHADEBOX]

### コーディングと開発

#### コア Adobe Commerce コード

|     | Adobe | 加盟店 |
| --- | --- | --- |
| アップデートとパッチのAdobe Commerce コアへの公開 | R |     |
| ファイルシステムの可用性とパッチ適用 | R |  |
| ECE-Toolsへのアップデートとパッチの公開 | R |     |
| Core Adobe Commerceのアプリケーション品質 | R |     |

{style="table-layout:auto"}

#### コードリポジトリ

|     | Adobe | 加盟店 |
| --- | --- | --- |
| repo.magento.comの可用性 | R |     |
| Cloud Git Server上のAdobe Commerceの可用性 | R |     |
| その他のマーチャントが選択したコードリポジトリ（GitHub、Bitbucket、ホストされているGit サーバー） |     | R |

{style="table-layout:auto"}

#### Cloud Docker

|     | Adobe | 加盟店 |
| --- | --- | --- |
| Cloud Docker コンテナをダウンロード可能にする | R |   |
| Cloud Dockerのデプロイとセットアップ（オプション） |     | R |
| その他のローカル開発設定 |     | R |

{style="table-layout:auto"}

#### COMMERCE CLOUD CLI

|     | Adobe | 加盟店 |
| --- | --- | --- |
| ECE ツールの継続的な品質と更新 | R |   |
| 最新バージョンのECE ツールのインストール |     | R |

{style="table-layout:auto"}

#### カスタマイズ

|  | Adobe | 加盟店 |
| --- | --- | --- |
| カスタム Adobe Commerce モジュールとコード |     | R |
| 拡張機能 |     | R |
| カスタム統合 |     | R |

{style="table-layout:auto"}

#### 展開

|     | Adobe | 加盟店 |
| --- | --- | --- |
| コードを構築およびデプロイするためのインフラストラクチャの可用性 | R |   |
| インフラストラクチャのビルドとデプロイの設定パイプラインの継続的な品質 | R |   |
| ビルドと静的コンテンツのデプロイメントの設定 |     | R |
| デプロイメントガバナンスプロセスの構築と実行：基準と変更管理 |     | R |
| ステージング環境へのデプロイ |     | R |
| 実稼動環境へのデプロイ |     | R |
| 実稼動ロールバック |     | R |

{style="table-layout:auto"}

#### 環境の同期

マーチャントは、環境間でデータを同期する責任があります。

#### パッチ

|     | Adobe | 加盟店 |
| --- | --- | --- |
| ECE-Toolsへのアップデートとパッチのインストール |     | R |
| Adobe Commerce コアへのアップデートとパッチのインストール |     | R |

#### web サイトの可用性

|  | Adobe | 加盟店 |
| --- | --- | --- |
| カスタマイズされたAdobe Commerce アプリケーションと関連するweb サイト |     | R |

#### パフォーマンス

|     | Adobe | 加盟店 |
| --- | --- | --- |
| 主要アプリケーションの調整と最適化 | R |   |
| カスタムコードの調整と最適化 |     | R |
| カスタム Adobe Commerce コード |     | R |
| 負荷テスト |     | R |
| パフォーマンステスト |     | R |

{style="table-layout:auto"}


#### ログと監視

|     | Adobe | 加盟店 |
| --- | --- | --- |
| ログの回転 | R |   |
| カスタム Adobe Commerce アプリケーション | | R |
| New Relic サービスの可用性：<br>APM アプリケーションとエージェントの統合、インフラストラクチャ アプリケーション、<br> ログと統合 | R |   |
| New Relic アラートの設定 |     | R |
| PaaS サーバーへのNew Relic エージェントのデプロイ | R |  |

{style="table-layout:auto"}

#### デバッグと問題の分離

|     | Adobe | 加盟店 |
| --- | --- | --- |
| デバッグと問題の分離 | R | R |
| デバッグと問題分離プロセスのタイムリーなサポート |     | R |

{style="table-layout:auto"}

### アプリケーションとサービスの設定

#### Commerceアプリ

|     | Adobe | 加盟店 |
| --- | --- | --- |
| アプリケーション設定 |     | R |
| Adobe Commerce アプリケーションへのドメインの追加（ベース URL） |     | R |
| デプロイされたAdobe Commerce バージョンでサポートされているサービス バージョンを使用するようにPaaSを設定する<br><br>例えば、様々なCommerce バージョンは、特定のバージョンのPHP、Redisなどに対応しています。 |     | R |

{style="table-layout:auto"}

#### cron ジョブによるタスクのスケジュール設定

|     | Adobe | 加盟店 |
| --- | --- | --- |
| デフォルトのcron ジョブの可用性 | R | |
| カスタムクローンジョブの継続的な品質 |  | R |

{style="table-layout:auto"}

#### メッセージキューフレームワーク用メッセージブローカー

|     | Adobe | 加盟店 |
| --- | --- | --- |
| RabbitMQ サービスの可用性 | R |   |
| デフォルトのRabbitMQ設定の設定 | R |   |
| RabbitMQの継続的な品質とパッチ適用 | R |   |
| インストール済みのAdobe Commerce バージョンと互換性のあるRabbitMQ バージョンをインストールするには、サービスリクエストを送信します |   | R |

{style="table-layout:auto"}

#### PHP サービス

|     | Adobe | 加盟店 |
| --- | --- | --- |
| PHPの可用性 | R |   |
| デフォルトのPHP設定の設定 | R |     |
| カスタム PHP設定の設定 |     | R |
| インストールされているAdobe Commerceのバージョンと互換性のあるPHPのバージョンを整列させるYAML ファイルの設定 |    | R |

{style="table-layout:auto"}

#### データベースサービス

|     | Adobe | 加盟店 |
| --- | --- | --- |
| GaleraおよびMariaDB サービスの可用性 | R | |
| 既定のデータベース設定の継続的なメンテナンス <br><br> （インデックス作成とコア テーブルの最適化、既定のsys-admin設定の最適化） | R |   |
| マーチャント データの継続的なメンテナンスと変更された設定<br><br> （正規化されたテーブルとフラット テーブルの設定、カスタム テーブルとサードパーティ テーブルのインデックス作成と最適化、データのアーカイブまたは削除、システム管理設定の設定） |     | R |
| GaleraとMySQLの設定 | R |   |
| GaleraとMariaDBの継続的な品質とパッチ適用 | R |   |
| インフラの継続的な最適化 | R |   |
| スロークエリの特定と修正 |     | R |
| インストール済みのAdobe Commerce バージョンと互換性のあるMariaDB バージョンをインストールするには、サービスリクエストを送信します |     | R |
| 加盟店固有のデータ保持ポリシーの設定と管理（Adobeのデータ保持ポリシーは、加盟店契約で定義されています） |     | R |

{style="table-layout:auto"}

#### CDN サービス

|     | Adobe | 加盟店 |
| --- | --- | --- |
| CDNの可用性と品質 | R |   |
| Fastly サービス設定（拡張機能/API経由） |     | R |
| Fastlyの拡張品質 | R |   |
| Fastly統合VCL スニペット（Fastly拡張機能にバンドル）品質 | R |   |
| ページキャッシュの最適化 |     | R |
| サービス、CDN、インフラストラクチャへのドメインの追加 | R |   |
| カスタム VCL スニペット |     | R |
| WAFとWAF ルール | R |   |

{style="table-layout:auto"}

#### キャッシュサービス

|     | Adobe | 加盟店 |
| --- | --- | --- |
| Redis サービスの可用性 | R |   |
| デフォルトのRedis設定の設定 | R |   |
| Redisの継続的な品質とパッチ適用 | R |   |
| インストール済みのAdobe Commerce バージョンと互換性のあるRedis バージョンをインストールするには、サービスリクエストを送信します |     | R |

{style="table-layout:auto"}

#### 検索サービス

|     | Adobe | 加盟店 |
| --- | --- | --- |
| ElasticsearchまたはOpenSearchの可用性 | R |   |
| ElasticsearchまたはOpenSearchのデフォルト設定 | R |   |
| インストール済みのAdobe Commerce バージョンと互換性のあるElasticsearchまたはOpenSearch バージョンをインストールするには、サービスリクエストを送信します |  | R |

{style="table-layout:auto"}

#### メールサービス

|     | Adobe | 加盟店 |
| --- | --- | --- |
| SendGrid メールサービスとその統合の可用性 | R |   |
| 制限に対する加盟店のSendGrid使用状況の監視 | R |   |
| 販売者は、送信するトランザクションメールに対してのみサービスを使用する責任があります<br>このサービスでは、マーケティングメールの送信はサポートされていません。 |     | R |
| オプションのサードパーティのメールサービスの設定 |     | R |

{style="table-layout:auto"}

#### サードパーティサービス

|     | Adobe | 加盟店 |
| --- | --- | --- |
| サードパーティサービスの可用性と品質 |     | R |

{style="table-layout:auto"}

### Commerce Servicesの拡張機能

#### Advance Reporting サービス

|     | Adobe | 加盟店 |
| --- | --- | --- |
| Advanced Reporting Serviceの可用性 | R |   |
| 高度なレポートの設定は、高度なレポートの利用条件に準拠しています |     | R |

{style="table-layout:auto"}

#### Commerce Intelligence

|     | Adobe | 加盟店 |
| --- | --- | --- |
| Adobe Commerce Business Intelligenceのサービスの可用性 | R |   |
| MBI データ同期プロセス | R |   |
| MBI同期の問題を検出しています | R |   |
| Adobe Commerce Cloud Pro、Starter、On Premises、またはAdobe Commerce以外の<br> （API、データの品質とフォーマット、マーチャント ネットワーク、Adobe Commerce DBの内外の<br>DB接続、データしきい値を介した）へのMBI データ同期の設定 |     | R |
| Adobe Commerce Cloud ProへのMBI データ同期の設定<br> （Adobe Commerce Cloud データベース設定） | R |   |

{style="table-layout:auto"}

>[!NOTE]
>
>販売者は、最高レベルの安定性、機能、サポート資格を保証するために、最新バージョンのライブサーチ、商品レコメンデーション、決済サービスを利用する必要があります。
>Adobeは古いバージョンをサポートしておらず、アップグレードすると、最新の機能強化とバグ修正の恩恵を受けることができます。
>サポートされているバージョンについて詳しくは、[Commerce サービスの製品可用性マトリックス &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce-operations/release/product-availability#commerce-services)を参照してください。

#### 商品レコメンデーション

|     | Adobe | 加盟店 |
| --- | --- | --- |
| 商品レコメンデーションサービスの可用性 | R |   |
| 製品レコメンデーションモジュールのアップグレード |   | R |

{style="table-layout:auto"}

#### ライブサーチ

|     | Adobe | 加盟店 |
| --- | --- | --- |
| ライブサーチサービスの可用性 | R |   |
| ライブ検索モジュールのアップグレード |   | R |

{style="table-layout:auto"}

#### ストアフロントイベントの品質（データ収集）により、商品レコメンデーションとライブサーチの出力を強化

|     | Adobe | 加盟店 |
| --- | --- | --- |
| コアテーマ（Luma） | R |   |
| カスタムテーマ |  | R |
| PWAの導入 | R |   |
| PWAのカスタム実装 |  | R |
| コア AEM EDSの実装（Commerce Boilerplate） | R |   |
| カスタム AEM EDSの実装 |  | R |
| その他のカスタムストアフロントの実装 |  | R |

{style="table-layout:auto"}

#### 決済サービス

|     | Adobe | 加盟店 |
| --- | --- | --- |
| 決済サービスの可用性 | R |   |
| 支払いモジュールのアップグレード |   | R |

{style="table-layout:auto"}

### ネットワークサービス

#### 画像の最適化

|     | Adobe | 加盟店 |
| --- | --- | --- |
| 画像の最適化の可用性と品質 | R |  |
| 画像の最適化の設定 |     | R |

{style="table-layout:auto"}

#### SSL証明書

|     | Adobe | 加盟店 |
| --- | --- | --- |
| SSL専用証明書 – 有効期限 | R |  |
| SSL証明書のプロビジョニング | R |  |
| EV/Specific SSL cert （提供されるデフォルト以外）の購入と管理、およびAdobeへの提供 |     | R |

{style="table-layout:auto"}

#### Web Application Firewall （WAF）

|     | Adobe | 加盟店 |
| --- | --- | --- |
| WAFの可用性と設定 | R |  |
| WAF ルールの偽陽性への対処 | R | |
| WAF ルールの誤検出の報告 |     | R |
| WAF ルールの調整（サポートされていません） |     |     |
| WAF/CDN ログ |     | R |

{style="table-layout:auto"}

#### DDOS

|     | Adobe | 加盟店 |
| --- | --- | --- |
| プロアクティブ IP ブロック |     | R |
| ボット保護 |     | R |
| DDOS検出 – レイヤー3-4 | R |   |
| DDOS検出 – レイヤー7 |     | R |
| DDOS対応 | R |   |

{style="table-layout:auto"}

#### プライベートリンク

|     | Adobe | 加盟店 |
| --- | --- | --- |
| Adobeが所有するVPCを使用したPrivateLink接続の設定と管理（使用する場合） | R |   |
| マーチャントが所有するVPCでのPrivateLink接続（使用する場合）の設定とメンテナンス |     | R |
| SSH （非プライベートリンク）の可用性 | R |   |
| Adobe Commerce Cloud Service エンドポイントへのPrivateLink インバウンドの設定 | R |   |
| Adobe Commerce Cloud Service エンドポイントへのPrivateLink インバウンドの受け入れ |     | R |
| MerchantのVPC サービスエンドポイントへのPrivateLink インバウンドの設定 |     | R |
| 加盟店のVPC サービスエンドポイントへのPrivateLink インバウンドの受け入れ | R |   |
| PrivateLink統合の設定（エンドポイントからアカウントへ） |     | R |
| PrivateLink エンドポイント <br><br>用のマーチャント所有のVPCの設定（すべてのVPN接続を含む） |     | R |

{style="table-layout:auto"}

### システムとインフラ

#### App Server

|     | Adobe | 加盟店 |
| --- | --- | --- |
| Nginxの提供開始 | R |   |
| Nginxの設定 | R |   |
| Nginxの継続的な品質とパッチ適用 | R |   |

{style="table-layout:auto"}

#### オペレーティングシステム

|     | Adobe | 加盟店 |
| --- | --- | --- |
| オペレーティングシステムの可用性 | R |   |
| オペレーティングシステムの継続的な品質とパッチ適用 | R |   |

{style="table-layout:auto"}

#### バックアップ、高可用性、フェイルオーバー

|     | Adobe | 加盟店 |
| --- | --- | --- |
| スナップショットとバックアッププロセスの可用性 | R |   |
| Cloud Pro ステージング環境および実稼動環境のバックアップのスケジュール設定 | R |   |
| Cloud Starter環境とPro統合環境のバックアップのスケジュール |     | R |
| HA/フェイルオーバーの可用性 | R |   |

{style="table-layout:auto"}

#### クラウドサーバーと拡張

|     | Adobe | 加盟店 |
| --- | --- | --- |
| CPUのリソース、データセンター、ディスク容量の可用性 | R |   |
| サージキャパシティまたは緊急アップグレードの可用性と実行 | R |   |
| サージキャパシティの要求 |     | R |
| 制限に対するvCPU使用率の監視 | R |   |

{style="table-layout:auto"}
