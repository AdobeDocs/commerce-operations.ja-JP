---
title: 品質管理
description: 実装プロジェクトに関連するAdobe Commerceの品質管理プロセスについて説明します。
exl-id: 0eb62b24-21f6-4cec-8ef9-eeaa1ee6ae52
feature: Build
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '658'
ht-degree: 0%

---

# 品質管理プロセスとツール

![品質管理プロセス図](../../assets/playbooks/quality-control-diagram.svg)

前の図の品質管理プロセスを、次のように簡単に説明します。

<table>
<thead>
  <tr>
    <th>ソフトウェア開発プロセス</th>
    <th>QC ワークフロー</th>
    <th>QC</th>
    <th>QC リーダー</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>開発</td>
    <td>計画</td>
    <td></td>
    <td>テスト計画の確認と投稿</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
    <td>テスト仕様の作成（テストケース/テストシナリオ）</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
    <td>テストデータの準備と取得</td>
  </tr>
  <tr>
    <td></td>
    <td>テスト分析とデザイン</td>
    <td>テスト計画の確認と投稿</td>
    <td>準備、仕様を開始</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>テスト仕様の作成（テストケース/テストシナリオ）</td>
    <td>プロジェクトのテスト戦略を記述またはレビュー</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>テストデータの準備と取得</td>
    <td> 分析、設計を導き、導き、監視</td>
  </tr>
  <tr>
    <td>内部テスト</td>
    <td>テストの実装と実行</td>
    <td>テストの実装、実行、およびログ</td>
    <td>テストの実装と実行の監視</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>パフォーマンスの確認とセキュリティのスキャン — 結果および期待される結果からの逸脱を評価します</td>
    <td>テストの追跡可能性をテストベースに確保し、バグ追跡システムでバグを追跡し続けます。</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>バグをバグ追跡システムに投稿する (Jira/Redmine/Trello)</td>
    <td>PM で定義されたプロジェクト計画に合わせてテストを優先/スケジュール</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>バグ修正後の再テスト（確認テスト）</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>評価とレポート</td>
    <td>QC リードと PM にテストの進捗を報告</td>
    <td>テスト結果と進行状況の評価</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
    <td>テスト中に収集された情報に基づいて、テスト概要レポートを作成します</td>
  </tr>
  <tr>
    <td>UAT</td>
    <td>UAT</td>
    <td>顧客のフィードバックまたは変更要求 (CR) の検証</td>
    <td>フォローアップ</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>ソースコードを変更した後に再テストと回帰テストを実行</td>
    <td>制御</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>テスト仕様の更新</td>
    <td></td>
  </tr>
  <tr>
    <td>メンテナンス</td>
    <td>メンテナンス</td>
    <td>タスクのレビューと投稿</td>
    <td>タスクの時間の確認と見積もり</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>テスト仕様の作成/更新</td>
    <td>フォローアップテストの進行状況</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>次のタスクのテストを実行</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>回帰テストの実行</td>
    <td></td>
  </tr>
</tbody>
</table>

次に類似 [ツール](project-management-tools.md) 開発プロセスで特定し、品質管理テストによく利用するソリューションとプラットフォームの一部を選択しました。

| 目的 | ツール |
|---------------------------|---------------------------------------------------|
| Web サイトパフォーマンスインデックス | Google PageSpeed、Webpagetest、JMeter |
| セキュリティ | Adobe Commerceセキュリティスキャンツール、SonarQube、ZAP |
| 問題管理システム | JIRA |
| UI テスト | 完璧なピクセル、BrowserStack |
| API テスト | Postman、SoapUI |
| 自動化テスト | Selenium |


## Web サイトパフォーマンスインデックス

GooglePageSpeed は、モバイルデバイスとデスクトップデバイスの両方でのページのパフォーマンスをレポートし、そのページの改善方法に関する提案を提供します。

WebPageTest は、実際のブラウザを使用して Web ページにアクセスし、タイミング指標を収集する Web パフォーマンスツールです。

JMeter は、Web アプリケーションに焦点を当てながら、様々なサービスのパフォーマンスを分析および測定する負荷テストツールとして使用できる Apache プロジェクトです。

## セキュリティ

開発プロセスでは SonarQube と ZAP が導入されましたが、QC プロセスにどのように関わるのかについての詳しい情報をここに含めています。

また、SonarQube は、コード品質の継続的な検査にも使用され、バグ、コードスメル、セキュリティの脆弱性を検出するためのコードの静的分析を使用して自動レビューを実行します。

OWASPZAP (Zed Attack Proxy) は、アプリケーションセキュリティに新しい人々と、専門の侵入テスターの両方が使用することを意図しています。 組み込み機能の一部には、プロキシサーバ、従来の Web クローラーとAJAX Web クローラー、自動スキャナー、パッシブスキャナー、強制ブラウジング、Fuzzier、WebSocket サポート、スクリプティング言語、Plug-n-Hack サポートが含まれます。

## UI テスト

Perfect Pixel を使用すると、開発者やマークアップデザイナーは、開発されたHTMLの上に半透明の画像オーバーレイを配置し、それらの画像間でピクセルパーフェクトな比較を実行できます。

BrowserStack は、開発者がオンデマンドブラウザー、オペレーティングシステム、実際のモバイルデバイスをまたいで Web サイトやモバイルアプリケーションをテストできるクラウド Web およびモバイルテストプラットフォームです。

## API テスト

Postmanは、API 開発のコラボレーションプラットフォームです。 Postmanは、API の構築の各手順を簡素化し、コラボレーションを効率化して、より優れた API を作成できるようにします。

SoapUI は、Simple Object Access Protocol(SOAP) および Representational State Transfers(REST) 用のオープンソース Web サービステストアプリケーションです。 その機能は、Web サービスの検査を含む。呼び出し、開発、シミュレーション、およびモッキング。機能テスト；負荷と準拠のテスト。

## 自動化テスト

Selenium は、複数のコンポーネント（Selenium クライアント API、Selenium WebDriver）で構成され、それぞれが Web アプリケーションテストの自動化の開発を支援する特定の役割を果たしています。
