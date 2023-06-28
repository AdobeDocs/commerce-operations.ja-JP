---
title: Adobe Managed Services
description: Adobe Managed Services がAdobe Commerceの実装をサポートおよび維持するために役立つ方法について説明します。
exl-id: b600b0e3-c6fd-4b86-ad2a-a445e599f1bd
feature: Services
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '1108'
ht-degree: 0%

---


# Adobe Managed Services

Adobe Commerceは、標準搭載の堅牢な機能、広範なカスタマイズ可能なオプション、サードパーティの統合を含む、e コマース機能を提供するためのプラットフォームです。

Adobe Managed Services は、クラウドインフラストラクチャ Pro プラン上のAdobe Commerceに対して、ホストおよび管理されたアプリケーションおよびインフラストラクチャを提供します。

## メリット

![Adobe Managed Services の利点を示す解説図](../../assets/playbooks/managed-services-benefits.png)

### 実装オプションの比較

Adobe Managed Services は、次のようなオンプレミスおよび非管理クラウド実装に対する主なメリットを提供します。

- **サービス・レベル・ターゲット (SLT) の強化** — 標準のAdobe Commerceサポートよりも応答時間が速くなります。
- **SLA(Service Level Agreement) の強化**— 99.99%のインフラストラクチャレベルを 99.99%に上回る、クラウドインフラストラクチャ上の通常のAdobe Commerceのお客様に適したアプリケーションレベル
- **指定されたクラウドの専門知識**— Managed Servicesは、お客様に、アプリケーションおよびクラウドインフラストラクチャのエキスパートとして機能する、カスタマーサクセスエンジニア (CSE) を提供します。 CSE は、お客様およびそのパートナーと連携し、顧客に対して、次のようなベストプラクティスとガイダンスを提供して、市場投入までの時間を短縮します。
   - オンボーディングプロセスのガイドとサポート
   - プロビジョニングとプラットフォーム設定の管理
   - 統合とカスタマイズに関するアーキテクチャの原則についてアドバイスする
   - インシデント管理とビジネス継続性の促進
   - 計画、実行、監視を通じてイベント・サポートを提供
   - クラウドのサポートと専門知識（プロアクティブな最適化、レポート作成、ベストプラクティス）

Managed Servicesの主なメリットの詳細な比較については、以下の解説図を確認してください。

![Adobe Managed Services と他のAdobe Commerce実装オプションの比較を示す解説図](../../assets/playbooks/managed-services-compare.png)

## 役割と責務

Adobeは、Managed Servicesシステム上のAdobe Commerceのプロビジョニング、開発、ステージングおよび実稼動に関する一連のサービスを提供します。 ソリューションの開発と導入を可能な限り効率的に進めるには、次に説明するように、お客様とパートナーが自分の役割を理解し、果たすことが重要です。

<table>
    <thead>
        <tr>
            <th></th>
            <th>顧客</th>
            <th>パートナー</th>
            <th>カスタマーサクセスエンジニア</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td colspan="4" style="background:lightgray;"><strong>プロビジョニング</strong></td>
        </tr>
        <tr>
            <td>クラウド地域の選択</td>
            <td>所有者</td>
            <td>寄稿者</td>
            <td>アドバイザー</td>
        </tr>
        <tr>
            <td>インスタンスのプロビジョニング</td>
            <td></td>
            <td></td>
            <td>所有者</td>
        </tr>
        <tr>
            <td>内部ネットワークの設定とセキュリティ</td>
            <td></td>
            <td></td>
            <td>所有者</td>
        </tr>
        <tr>
            <td>Adobe Commerce Application Provisioning</td>
            <td></td>
            <td></td>
            <td>所有者</td>
        </tr>
        <tr>
            <td>Adobe Commerce Source Code Access</td>
            <td></td>
            <td></td>
            <td>所有者</td>
        </tr>
        <tr>
            <td>CDN サービスのプロビジョニング</td>
            <td></td>
            <td></td>
            <td>所有者</td>
        </tr>
        <tr>
            <td>ローカル開発環境</td>
            <td>寄稿者</td>
            <td>所有者</td>
            <td></td>
        </tr>
        <tr>
            <td colspan="4" style="background:lightgray;"><strong>開発と QA</strong></td>
        </tr>
        <tr>
            <td>要件の収集とプロジェクト管理</td>
            <td>寄稿者</td>
            <td>所有者</td>
            <td>アドバイザー</td>
        </tr>
        <tr>
            <td>アプリケーション開発</td>
            <td>寄稿者</td>
            <td>所有者</td>
            <td>アドバイザー</td>
        </tr>
        <tr>
            <td>アプリケーションテスト</td>
            <td>寄稿者</td>
            <td>所有者</td>
            <td>アドバイザー</td>
        </tr>
        <tr>
            <td colspan="4" style="background:lightgray;"><strong>ステージングと移行</strong></td>
        </tr>
        <tr>
            <td>開発、統合、ステージングへのコードのデプロイメント</td>
            <td>寄稿者</td>
            <td>所有者</td>
            <td>アドバイザー</td>
        </tr>
        <tr>
            <td>コンテンツのデプロイ</td>
            <td>寄稿者</td>
            <td>所有者</td>
            <td>アドバイザー</td>
        </tr>
        <tr>
            <td>ユーザー受け入れテストの開発</td>
            <td>所有者</td>
            <td>寄稿者</td>
            <td>アドバイザー</td>
        </tr>
        <tr>
            <td>ユーザー受け入れテスト</td>
            <td>所有者</td>
            <td>寄稿者</td>
            <td>アドバイザー</td>
        </tr>
        <tr>
            <td>カスタム監視の要件</td>
            <td>寄稿者</td>
            <td>所有者</td>
            <td>アドバイザー</td>
        </tr>
        <tr>
            <td>お客様が指定する SSL 証明書</td>
            <td>所有者</td>
            <td></td>
            <td>寄稿者</td>
        </tr>
        <tr>
            <td>パフォーマンスと負荷テストの開発</td>
            <td>寄稿者</td>
            <td>所有者</td>
            <td>アドバイザー</td>
        </tr>
        <tr>
            <td>パフォーマンスと負荷のテスト</td>
            <td>寄稿者</td>
            <td>所有者</td>
            <td>アドバイザー</td>
        </tr>
        <tr>
            <td>カスタマイズ開発と QA</td>
            <td>寄稿者</td>
            <td>所有者</td>
            <td>アドバイザー</td>
        </tr>
        <tr>
            <td>Runbook completion</td>
            <td>所有者</td>
            <td>寄稿者</td>
            <td>寄稿者</td>
        </tr>
        <tr>
            <td>Runbook レビュー</td>
            <td></td>
            <td></td>
            <td>所有者</td>
        </tr>
        <tr>
            <td colspan="4" style="background:lightgray;"><strong>起動</strong></td>
        </tr>
        <tr>
            <td>運用開始チェックリスト</td>
            <td>寄稿者</td>
            <td>寄稿者</td>
            <td>所有者</td>
        </tr>
        <tr>
            <td>運用開始イベントの会議室</td>
            <td>寄稿者</td>
            <td>寄稿者</td>
            <td>所有者</td>
        </tr>
        <tr>
            <td>実稼動コードのデプロイメント</td>
            <td>寄稿者</td>
            <td>寄稿者</td>
            <td>所有者</td>
        </tr>
        <tr>
            <td colspan="4" style="background:lightgray;"><strong>実稼動</strong></td>
        </tr>
        <tr>
            <td>本番インフラストラクチャの監視</td>
            <td></td>
            <td></td>
            <td>所有者</td>
        </tr>
        <tr>
            <td>主なアプリケーションの監視</td>
            <td>寄稿者</td>
            <td>寄稿者</td>
            <td>所有者</td>
        </tr>
        <tr>
            <td>実稼動イベントの応答</td>
            <td>寄稿者</td>
            <td>寄稿者</td>
            <td>所有者</td>
        </tr>
        <tr>
            <td>インフラストラクチャおよびオペレーティング・システム・レベルのメンテナンス</td>
            <td></td>
            <td></td>
            <td>所有者</td>
        </tr>
        <tr>
            <td>カスタムコードのメンテナンスおよびセキュリティパッチ</td>
            <td>寄稿者</td>
            <td>所有者</td>
            <td>アドバイザー</td>
        </tr>
        <tr>
            <td>Adobe Commerce製品のアップデートとアップグレードへのアクセス権の提供</td>
            <td>寄稿者</td>
            <td>寄稿者</td>
            <td>所有者</td>
        </tr>
        <tr>
            <td>Adobe Commerce製品のアップデートとアップグレードの適用</td>
            <td>寄稿者</td>
            <td>所有者</td>
            <td>アドバイザー</td>
        </tr>
        <tr>
            <td>承認ボードを変更して実稼動環境の展開を承認</td>
            <td>寄稿者</td>
            <td>寄稿者</td>
            <td>所有者</td>
        </tr>
        <tr>
            <td>本番アプリケーションの管理</td>
            <td>所有者</td>
            <td>寄稿者</td>
            <td>アドバイザー</td>
        </tr>
        <tr>
            <td>本番インフラストラクチャの調整</td>
            <td>寄稿者</td>
            <td>寄稿者</td>
            <td>所有者</td>
        </tr>
        <tr>
            <td>本番アーキテクチャの拡張</td>
            <td></td>
            <td></td>
            <td>所有者</td>
        </tr>
        <tr>
            <td>本番バックアップとリカバリ</td>
            <td></td>
            <td>寄稿者</td>
            <td>所有者</td>
        </tr>
        <tr>
            <td colspan="4" style="background:lightgray;"><strong>セキュリティとコンプライアンス</strong></td>
        </tr>
        <tr>
            <td>SOC-2 サービスの監査</td>
            <td></td>
            <td></td>
            <td>所有者</td>
        </tr>
        <tr>
            <td>インフラストラクチャの PCI 認定</td>
            <td></td>
            <td></td>
            <td>所有者</td>
        </tr>
        <tr>
            <td>カスタマイズされたアプリケーションの PCI 認定</td>
            <td>所有者</td>
            <td>寄稿者</td>
            <td></td>
        </tr>
        <tr>
            <td>コアアプリケーションのセキュリティ監査</td>
            <td>所有者</td>
            <td>寄稿者</td>
            <td>アドバイザー</td>
        </tr>
        <tr>
            <td>カスタマイズと拡張機能のセキュリティ監査</td>
            <td>所有者</td>
            <td>寄稿者</td>
            <td></td>
        </tr>
        <tr>
            <td>お客様のアプリケーションインスタンスの侵入テスト</td>
            <td>所有者</td>
            <td>寄稿者</td>
            <td></td>
        </tr>
        <tr>
            <td>Web アプリケーションファイアウォールルール (WAF)</td>
            <td>寄稿者</td>
            <td>寄稿者</td>
            <td>所有者</td>
        </tr>
        <tr>
            <td>侵入検知の監視</td>
            <td></td>
            <td></td>
            <td>所有者</td>
        </tr>
        <tr>
            <td>アプリケーションと DB イベントの監視</td>
            <td>寄稿者</td>
            <td>寄稿者</td>
            <td>所有者</td>
        </tr>
        <tr>
            <td>Web アプリケーションファイアウォールイベントの監視</td>
            <td>寄稿者</td>
            <td>寄稿者</td>
            <td>所有者</td>
        </tr>
        <tr>
            <td>ユーザー管理と SSO 統合</td>
            <td>所有者</td>
            <td>寄稿者</td>
            <td>寄稿者</td>
        </tr>
        <tr>
            <td>セキュリティイベント応答</td>
            <td>寄稿者</td>
            <td>寄稿者</td>
            <td>所有者</td>
        </tr>
        <tr>
            <td>企業のネットワークやリソースへの接続を設定、保護、維持する </td>
            <td>所有者</td>
            <td>アドバイザー</td>
            <td>アドバイザー</td>
        </tr>
    </tbody>
</table>

## セキュリティ

Managed ServicesのAdobeセキュリティスタックは、自動化と一貫性を使用してあらゆるレベルでセキュリティを構築し、ヒューマンエラーを減らします。 開発チームと運用チームは、異なるレベルのスタックからセキュリティ制御を自動的に継承します。

Amazon Web ServicesやMicrosoft Azure などの Platform パートナーは、プラットフォームのカスタマイズを適用する際に、セキュリティを最大限に活用し、AdobeのManaged Servicesチームは、コンプライアンス、ログ、認証、スキャン、監視、サーバセキュリティとセキュアなアプリケーション設定などのコアセキュリティサービスを提供します。 詳しくは、 [Adobe Commerce Security](https://business.adobe.com/products/magento/secure-ecommerce.html) を参照してください。

次の図に、Adobe Managed Services セキュリティテクノロジースタックを示します。

![Adobe Managed Services セキュリティスタックを示す図](../../assets/playbooks/managed-services-security-stack.svg)

## アップグレード支援

Managed Servicesチームは、アップグレードプロセスの計画と支援を支援する上で積極的な役割を果たしています。 カスタマーサクセスエンジニア (CSE) は、プロジェクトマネージャーや開発者 ( 社内の主題エキスパート、Adobe認定パートナー、Adobeコンサルティングの専門家 ) を含むアップグレードプロジェクトチームと連携し、アップグレード時のベストプラクティスの適切な計画と遵守を支援します。

Managed Services CSE はAdobe Commerceのお客様と連携して、大規模な環境でアップグレードを実行してきました。 担当の CSE は、エキスパートの知識を活用して、アップグレードの成功を最大化し、ダウンタイムを最小限に抑え、全体的なリスクを軽減するのに役立ちます。 さらに、Managed Services CSE は、アップグレードのために専用のステージング環境と連携して動作するので、アップグレードの検証中に既存の実稼動プロセスに影響を与えることはありません。

Adobeは、Managed Servicesシステムのプロビジョニング、開発、ステージングおよび実稼動に関する一連のサービスを提供します。 次の表に、アップグレードプロセスで各参加者が果たす役割の概要を示します。

<table>
<thead>
  <tr>
    <th>手順</th>
    <th>タスク</th>
    <th>顧客</th>
    <th>開発パートナー*</th>
    <th>Managed Services</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td rowspan="3">アップグレードの計画</td>
    <td>アップグレードプロジェクト計画の作成</td>
    <td>所有者</td>
    <td>寄稿者</td>
    <td>寄稿者<br />CSE には、アップグレードテンプレートとアップグレード計画のサンプルが用意されています。では、アドバイスとベストプラクティスに関するヒントを提供しています。</td>
  </tr>
  <tr>
    <td>必要なインフラストラクチャの変更を特定</td>
    <td></td>
    <td>寄稿者</td>
    <td>所有者<br />CSE は、適切なサイズ設定を確保するために、ステージングおよび実稼動インフラストラクチャをレビューします。</td>
  </tr>
  <tr>
    <td>アップグレードの複雑さの評価<br />パッケージ、問題と修正点、サードパーティ製およびカスタムモジュールの特定と文書化</td>
    <td>寄稿者</td>
    <td>所有者</td>
    <td>寄稿者<br />CSE は、アップグレード互換性ツールのレポートと推奨事項を提供しています。</td>
  </tr>
  <tr>
    <td rowspan="3">アップグレードを実行</td>
    <td>インフラストラクチャサービスのアップグレード<br />[MariaDB、Redis、Open Search、Rabbit MQ]（ステージングと実稼動）</td>
    <td></td>
    <td></td>
    <td>所有者<br />CSE は、インフラストラクチャサービスのアップグレードを調整します。<br />CSE は、アップグレードのための会議会議のイベントをスケジュールします。<br />CSE は、実稼動環境からステージング環境へのデータ移行を支援します。</td>
  </tr>
  <tr>
    <td>コマースコードベースとカスタマイズを更新する。コードのリコンパイルとコードリファクタリング</td>
    <td>寄稿者</td>
    <td>所有者</td>
    <td></td>
  </tr>
  <tr>
    <td>アップグレード後のチェックとトラブルシューティングの実行</td>
    <td></td>
    <td>所有者</td>
    <td>寄稿者<br />CSE は、アップグレード後の Runbook を実行して、アップグレードに関連する問題を検出し、修正します。</td>
  </tr>
  <tr>
    <td rowspan="3">UAT と Launch</td>
    <td>パフォーマンステストとセキュリティテストの実行</td>
    <td>寄稿者</td>
    <td>所有者</td>
    <td>寄稿者<br />CSE は、アプリケーションとインフラストラクチャのパフォーマンスを監視することで、負荷テストを支援します。<br />CSE は、Commerce Security スキャンツールの設定に役立ちます。</td>
  </tr>
  <tr>
    <td>ステージングでのユーザー受け入れテスト</td>
    <td>所有者</td>
    <td>寄稿者</td>
    <td>寄稿者<br />CSE が、アップグレード後にアプリケーションとインフラストラクチャが正しく実行されていることを検証します。</td>
  </tr>
  <tr>
    <td>実稼動環境に起動</td>
    <td>寄稿者</td>
    <td>所有者</td>
    <td>寄稿者<br />CSE は、ローンチ会議の会議イベントをスケジュールします。</td>
  </tr>
  <tr>
    <td>運用開始後</td>
    <td></td>
    <td>寄稿者</td>
    <td>寄稿者</td>
    <td>所有者<br />CSE はアプリケーションとインフラストラクチャのパフォーマンスを監視します。</td>
  </tr>
</tbody>
</table>
