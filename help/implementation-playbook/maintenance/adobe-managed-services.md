---
title: AdobeManaged Services
description: Adobe Managed ServicesがAdobe Commerceの実装のサポートと管理にどう役立つかを説明します。
exl-id: b600b0e3-c6fd-4b86-ad2a-a445e599f1bd
feature: Services
source-git-commit: 486e789787c9c08b27b4aae8e601680138956b88
workflow-type: tm+mt
source-wordcount: '1171'
ht-degree: 0%

---


# AdobeManaged Services

Adobe Commerceは、堅牢な標準機能、広範なカスタマイズ機能オプション、サードパーティとの統合など、e コマース機能を提供するためのプラットフォームです。

Adobe Managed Servicesは、Adobe Commerce on cloud infrastructure Pro プラン向けに、ホストされ管理されるアプリケーションおよびインフラストラクチャを提供します。

## 利点

![Adobe Managed Servicesのメリットを示すインフォグラフィック &#x200B;](../../assets/playbooks/managed-services-benefits.png)

### 実装オプションの比較

Adobe Managed Servicesには、オンプレミスおよび非管理のクラウド実装に比べて、次のような主なメリットがあります。

- **SLT （Enhanced Service Level Target）** – 標準のAdobe Commerceのサポートよりも迅速な応答時間。
- **SLA （Enhanced Service Level Agreement）**:99.9% のアプリケーションレベル。クラウドインフラストラクチャを利用するお客様の通常のAdobe Commerceは、99.99% のインフラストラクチャレベルを上回ります。
- **指定クラウド専門知識** - Managed Servicesは、アプリケーションおよびクラウドインフラストラクチャーのエキスパートとして機能する指定カスタマーサクセスエンジニア（CSE）をお客様に提供します。 CSE はお客様とそのパートナーと協力し、市場投入までの時間を短縮するためのベストプラクティスとガイダンスを提供します。これには以下が含まれます。
   - オンボーディングプロセスのガイドとサポート
   - プロビジョニングと Platform 設定の管理
   - 統合とカスタマイズのアーキテクチャ原則に関するアドバイス
   - インシデント管理とビジネス継続性を推進
   - 計画、実行、監視を通じてイベントをサポート
   - クラウドのサポートと専門知識（プロアクティブな最適化、レポート、ベストプラクティス）

Managed Servicesの主なメリットの詳細な比較については、次の表を確認してください。

| 機能 | Adobe Commerce オンプレミス | クラウド上のAdobe Commerce | Managed ServicesのAdobe Commerce |
|---------|---------------------------|-------------------------|-----------------------------------|
| Adobeの企業向けソフトウェア | ✓ | ✓ | ✓ |
| Adobe Developer App Builder | | ✓ | ✓ |
| 安全で専用のクラウドインフラストラクチャ | | ✓ P1:1 時間 | ✓ P1:15 分 |
| インシデントのサービスレベルターゲットの強化 | | ✓ | ✓ |
| サージ容量の監視と対応 | | ✓ | ✓ |
| インフラストラクチャのセキュリティ | | ✓ | ✓ |
| インフラストラクチャレベル 99.99% SLA | | ✓ | ✓ |
| アプリケーションレベル 99.9% SLA | | | ✓ |
| 指定インフラストラクチャ・エキスパート・リソース（カスタマー・サクセス・エンジニア） | | | ✓ |
| 予定イベント管理 | | | ✓ |
| カスタマイズされたサイト監視およびパーソナライズされた Runbook | | | ✓ |
| アップグレードとパッチ適用のデプロイメント支援 | | | ✓ |
| 運用開始プロセスの調整 | | | ✓ |
| 専任のエスカレーション管理 | | | ✓ |
| アプリケーションの監視と支援 | | | ✓ |

## 役割と責務

Adobeでは、Managed Services システム上のAdobe Commerceのプロビジョニング、開発、ステージング、実稼働に関する一連のサービスを提供しています。 ソリューションの開発とデプロイメントをできるだけ効率的に進めるには、顧客とパートナーが、次の役割を理解し果たすことが重要です。

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
            <td>クラウドリージョン選択</td>
            <td>所有者</td>
            <td>投稿者</td>
            <td>顧問</td>
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
            <td>Adobe Commerce アプリケーションプロビジョニング</td>
            <td></td>
            <td></td>
            <td>所有者</td>
        </tr>
        <tr>
            <td>Adobe Commerce Sourceのコードアクセス</td>
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
            <td>投稿者</td>
            <td>所有者</td>
            <td></td>
        </tr>
        <tr>
            <td colspan="4" style="background:lightgray;"><strong>開発と QA</strong></td>
        </tr>
        <tr>
            <td>要件の収集とプロジェクト管理</td>
            <td>投稿者</td>
            <td>所有者</td>
            <td>顧問</td>
        </tr>
        <tr>
            <td>アプリケーション開発</td>
            <td>投稿者</td>
            <td>所有者</td>
            <td>顧問</td>
        </tr>
        <tr>
            <td>アプリケーションテスト</td>
            <td>投稿者</td>
            <td>所有者</td>
            <td>顧問</td>
        </tr>
        <tr>
            <td colspan="4" style="background:lightgray;"><strong>ステージングと移行</strong></td>
        </tr>
        <tr>
            <td>開発、統合およびステージングへのコードのデプロイメント</td>
            <td>投稿者</td>
            <td>所有者</td>
            <td>顧問</td>
        </tr>
        <tr>
            <td>コンテンツのデプロイメント</td>
            <td>投稿者</td>
            <td>所有者</td>
            <td>顧問</td>
        </tr>
        <tr>
            <td>受け入れテストの開発</td>
            <td>所有者</td>
            <td>投稿者</td>
            <td>顧問</td>
        </tr>
        <tr>
            <td>ユーザー受け入れテスト</td>
            <td>所有者</td>
            <td>投稿者</td>
            <td>顧問</td>
        </tr>
        <tr>
            <td>カスタム監視要件</td>
            <td>投稿者</td>
            <td>所有者</td>
            <td>顧問</td>
        </tr>
        <tr>
            <td>お客様が提供する SSL 証明書</td>
            <td>所有者</td>
            <td></td>
            <td>投稿者</td>
        </tr>
        <tr>
            <td>パフォーマンスと負荷のテストの開発</td>
            <td>投稿者</td>
            <td>所有者</td>
            <td>顧問</td>
        </tr>
        <tr>
            <td>パフォーマンステストと負荷テスト</td>
            <td>投稿者</td>
            <td>所有者</td>
            <td>顧問</td>
        </tr>
        <tr>
            <td>カスタマイズの開発と QA</td>
            <td>投稿者</td>
            <td>所有者</td>
            <td>顧問</td>
        </tr>
        <tr>
            <td>Runbookの完了</td>
            <td>所有者</td>
            <td>投稿者</td>
            <td>投稿者</td>
        </tr>
        <tr>
            <td>Runbook レビュー</td>
            <td></td>
            <td></td>
            <td>所有者</td>
        </tr>
        <tr>
            <td colspan="4" style="background:lightgray;"><strong>ローンチ</strong></td>
        </tr>
        <tr>
            <td>運用開始チェックリスト</td>
            <td>投稿者</td>
            <td>投稿者</td>
            <td>所有者</td>
        </tr>
        <tr>
            <td>運用開始イベントの会議室</td>
            <td>投稿者</td>
            <td>投稿者</td>
            <td>所有者</td>
        </tr>
        <tr>
            <td>実稼動コードのデプロイメント</td>
            <td>投稿者</td>
            <td>投稿者</td>
            <td>所有者</td>
        </tr>
        <tr>
            <td colspan="4" style="background:lightgray;"><strong>実稼動</strong></td>
        </tr>
        <tr>
            <td>実稼動インフラストラクチャの監視</td>
            <td></td>
            <td></td>
            <td>所有者</td>
        </tr>
        <tr>
            <td>プリンシパルアプリケーションの監視</td>
            <td>投稿者</td>
            <td>投稿者</td>
            <td>所有者</td>
        </tr>
        <tr>
            <td>実稼動イベントの応答</td>
            <td>投稿者</td>
            <td>投稿者</td>
            <td>所有者</td>
        </tr>
        <tr>
            <td>インフラストラクチャおよびオペレーティングシステムレベルのメンテナンス</td>
            <td></td>
            <td></td>
            <td>所有者</td>
        </tr>
        <tr>
            <td>カスタムコードのメンテナンスとセキュリティパッチ</td>
            <td>投稿者</td>
            <td>所有者</td>
            <td>顧問</td>
        </tr>
        <tr>
            <td>Adobe Commerce製品のアップデートとアップグレードへのアクセスを提供する</td>
            <td>投稿者</td>
            <td>投稿者</td>
            <td>所有者</td>
        </tr>
        <tr>
            <td>Adobe Commerce製品のアップデートとアップグレードの適用</td>
            <td>投稿者</td>
            <td>所有者</td>
            <td>顧問</td>
        </tr>
        <tr>
            <td>実稼動デプロイメントを承認するように承認ボードを変更</td>
            <td>投稿者</td>
            <td>投稿者</td>
            <td>所有者</td>
        </tr>
        <tr>
            <td>本番アプリケーションの管理</td>
            <td>所有者</td>
            <td>投稿者</td>
            <td>顧問</td>
        </tr>
        <tr>
            <td>本番インフラストラクチャの調整</td>
            <td>投稿者</td>
            <td>投稿者</td>
            <td>所有者</td>
        </tr>
        <tr>
            <td>実稼動アーキテクチャの拡張</td>
            <td></td>
            <td></td>
            <td>所有者</td>
        </tr>
        <tr>
            <td>本番環境のバックアップとリカバリ</td>
            <td></td>
            <td>投稿者</td>
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
            <td>投稿者</td>
            <td></td>
        </tr>
        <tr>
            <td>コアアプリケーションのセキュリティ監査</td>
            <td>所有者</td>
            <td>投稿者</td>
            <td>顧問</td>
        </tr>
        <tr>
            <td>カスタマイズと拡張機能のセキュリティ監査</td>
            <td>所有者</td>
            <td>投稿者</td>
            <td></td>
        </tr>
        <tr>
            <td>お客様のアプリケーションのインスタンスの侵入テスト</td>
            <td>所有者</td>
            <td>投稿者</td>
            <td></td>
        </tr>
        <tr>
            <td>Web アプリケーションファイアウォールルール（WAF）</td>
            <td>投稿者</td>
            <td>投稿者</td>
            <td>所有者</td>
        </tr>
        <tr>
            <td>侵入検出の監視</td>
            <td></td>
            <td></td>
            <td>所有者</td>
        </tr>
        <tr>
            <td>アプリケーションおよび DB イベントの監視</td>
            <td>投稿者</td>
            <td>投稿者</td>
            <td>所有者</td>
        </tr>
        <tr>
            <td>Web アプリケーションファイアウォールイベントの監視</td>
            <td>投稿者</td>
            <td>投稿者</td>
            <td>所有者</td>
        </tr>
        <tr>
            <td>ユーザー管理と SSO 統合</td>
            <td>所有者</td>
            <td>投稿者</td>
            <td>投稿者</td>
        </tr>
        <tr>
            <td>セキュリティ イベントの応答</td>
            <td>投稿者</td>
            <td>投稿者</td>
            <td>所有者</td>
        </tr>
        <tr>
            <td>企業ネットワークおよびリソースへの接続の設定、保護、および維持 </td>
            <td>所有者</td>
            <td>顧問</td>
            <td>顧問</td>
        </tr>
    </tbody>
</table>

## セキュリティ

Managed ServicesのAdobe セキュリティスタックは、自動化と一貫性を使用して各レベルでセキュリティを構築し、人為的エラーを減らします。 開発チームと運用チームは、異なるスタックレベルからセキュリティ制御を自動的に継承します。

Amazon Web ServicesやMicrosoft Azure などの Platform パートナーは、プラットフォームのカスタマイズを適用する際に最大限のセキュリティの適用を確保し、Adobe Managed Services チームは、コンプライアンス、ログ、認証、スキャン、モニタリング、サーバーセキュリティおよび安全なアプリケーション設定などの主要なセキュリティサービスを提供します。 詳しくは、[Adobe Commerce セキュリティ &#x200B;](https://business.adobe.com/products/magento/secure-ecommerce.html) を参照してください。

次の図に、Adobe Managed Servicesのセキュリティテクノロジースタックを示します。

![Adobe Managed Servicesのセキュリティスタックを示す図 &#x200B;](../../assets/playbooks/managed-services-security-stack.svg)

## アップグレードの支援

Managed Services チームは、アップグレードプロセスの計画と支援で積極的な役割を果たします。 カスタマーサクセスエンジニア（CSE）は、プロジェクトマネージャーや開発者（社内主題専門家、Adobe認定パートナー、Adobe Consultingのプロフェッショナル）などのアップグレードプロジェクトチームと協力して、アップグレード中にチームが適切な計画を立て、ベストプラクティスに従うのを支援します。

Managed Services CSE はAdobe Commerceのお客様と協力して、大規模環境でアップグレードを実行してきました。 CSE は、専門知識を活用してアップグレードの成功を最大化すると同時に、ダウンタイムを最小限に抑え、全体的なリスクを軽減できるよう支援します。 さらに、Managed Services CSE はアップグレードに専用のステージング環境と連携するので、アップグレードの検証中に既存の実稼動プロセスが影響を受けることはありません。

Adobeでは、Managed Services システムのプロビジョニング、開発、ステージング、実稼働に関する一連のサービスを提供しています。 次の表に、アップグレードプロセスで各参加者が果たす役割の概要を示します。

<table>
<thead>
  <tr>
    <th>ステップ</th>
    <th>タスク</th>
    <th>顧客</th>
    <th>開発パートナー*</th>
    <th>Managed Services</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td rowspan="3">アップグレードの計画</td>
    <td>アップグレード プロジェクト計画の作成</td>
    <td>所有者</td>
    <td>投稿者</td>
    <td>Contributor<br />CSE は、アップグレードテンプレートとアップグレードプランのサンプルを提供し、アドバイスとベストプラクティスのヒントを提供します。</td>
  </tr>
  <tr>
    <td>必要なインフラストラクチャの変更の決定</td>
    <td></td>
    <td>投稿者</td>
    <td>所有者 <br />CSE は、ステージングインフラストラクチャと実稼動インフラストラクチャをレビューして、適切なサイジングを確保します。</td>
  </tr>
  <tr>
    <td>アップグレードの複雑さの評価 <br /> パッケージ、問題と修正、サードパーティおよびカスタムモジュールの特定と文書化</td>
    <td>投稿者</td>
    <td>所有者</td>
    <td>Contributor<br />CSE は、アップグレード互換性ツールのレポートと推奨事項を提供します。</td>
  </tr>
  <tr>
    <td rowspan="3">アップグレードの実行</td>
    <td>インフラストラクチャサービスのアップグレード <br />[MariaDB、Redis、Open Search、Rabbit MQ] （ステージングと実稼動）</td>
    <td></td>
    <td></td>
    <td>所有者 <br />CSE がインフラストラクチャサービスのアップグレードを調整します。<br />CSE は、会議ミーティングのイベントをアップグレード用にスケジュールします。<br />CSE は、実稼動環境からステージング環境へのデータ移行を支援します。</td>
  </tr>
  <tr>
    <td>Commerceのコードベースとカスタマイズの更新、コードの再コンパイルとコードリファクタリング</td>
    <td>投稿者</td>
    <td>所有者</td>
    <td></td>
  </tr>
  <tr>
    <td>アップグレード後のチェックとトラブルシューティングの実行</td>
    <td></td>
    <td>所有者</td>
    <td>Contributor<br />CSE は、アップグレード後の Runbook を実行して、アップグレードに関連する問題を検出し修正します。</td>
  </tr>
  <tr>
    <td rowspan="3">UAT と Launch</td>
    <td>パフォーマンステストとセキュリティテストの実行</td>
    <td>投稿者</td>
    <td>所有者</td>
    <td>Contributor<br />CSE は、アプリケーションとインフラストラクチャのパフォーマンスを監視することで、負荷テストを支援します。<br />CSE は、Commerce セキュリティスキャンツールの設定を支援します。</td>
  </tr>
  <tr>
    <td>ステージングでのユーザー受け入れテスト</td>
    <td>所有者</td>
    <td>投稿者</td>
    <td>Contributor<br />CSE は、アップグレード後にアプリケーションとインフラストラクチャが正しく実行されていることを検証します。</td>
  </tr>
  <tr>
    <td>実稼動環境にローンチ</td>
    <td>投稿者</td>
    <td>所有者</td>
    <td>Contributor<br />CSE は、会議の開始を会議イベントのスケジュールを設定します。</td>
  </tr>
  <tr>
    <td>ローンチ後</td>
    <td></td>
    <td>投稿者</td>
    <td>投稿者</td>
    <td>所有者 <br />CSE は、アプリケーションとインフラストラクチャのパフォーマンスを監視します。</td>
  </tr>
</tbody>
</table>
