---
title: アップグレードの範囲について
description: Adobe CommerceやMagento Open Sourceのカスタムモジュール、サードパーティの拡張機能に影響を与える可能性のある、リリースにおける後方互換性のない変更について説明します。
exl-id: dab2a14f-dbf0-422e-afb4-642e2220ec7a
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '901'
ht-degree: 0%

---

# アップグレードの範囲を理解する

をレビュー [リリースノート](https://devdocs.magento.com/guides/v2.4/release-notes/bk-release-notes.html) 機能強化、バグ修正、サードパーティやカスタムモジュールに影響を与える可能性のある既知の問題など、リリースの範囲を理解する。

## 後方互換性のない変更

Adobe Commerce リリースには、後方互換性のない変更が含まれている場合があります。 後方互換性のない変更に関するドキュメントを確認します。以下を参照してください。

- **[主な変更点](https://devdocs.magento.com/guides/v2.4/release-notes/backward-incompatible-changes/index.html)** – 大きな影響を与え、詳細な説明とサードパーティのモジュールが引き続き機能するための特別な手順が必要な変更。
- **[マイナー変更参照](https://devdocs.magento.com/guides/v2.4/release-notes/backward-incompatible-changes/reference.html)**- クラス、API メンバーシップ、データベース、依存関係の挿入、インターフェイス、レイアウト、システム、および XSD に対するマイナーな変更を説明するコードベースから生成されたリファレンスドキュメント。

## サードパーティの拡張機能

Adobe Commerce Marketplace の新しい互換性ポリシーにより、次のことが保証されます _all_ リストに表示された拡張機能は、GA 日から 30 日以内の最新のリリースバージョンと互換性があります。 そのため、可能な限り Marketplace を通じてサードパーティの拡張機能を入手することが重要です。

## カスタムモジュール

アップグレード先のターゲットバージョンと照合して、すべてのカスタムモジュールを確認する必要があります。 これは、アップグレードで最も時間とリソースを消費するプロセスです。 カスタムモジュールを評価する場合、後方互換性のない変更を探し、コントローラの分解などの新しい手法に注意する必要があります。 詳しくは、こちらを参照してください。 [リリースノート](https://devdocs.magento.com/guides/v2.4/release-notes/bk-release-notes.html). また、フォローしていることを確認します [ベストプラクティス](https://developer.adobe.com/commerce/php/best-practices/extensions/) （モジュール開発用）

## [!DNL Upgrade Compatibility Tool]

この [!DNL Upgrade Compatibility Tool] は、アップグレードに関する潜在的な問題をインスタンスに分析するコマンドラインツールです。 インストールした現在のバージョンと、アップグレードしようとしているバージョンの間の問題をチェックします。

このツールを使用すると、アップグレードの範囲と影響を理解するためにチームが行う手間を軽減できます。 アップグレード時の一般的なコードの問題を回避し、特定された問題を解決する方法について明確な指示を提供するのに役立ちます。 また、アップグレードを成功させるために必要な最も重要な問題の優先順位を付け、アップグレード時の時間とコストの両方を節約することもできます。

の基本については、次の節を参照してください [!DNL Upgrade Compatibility Tool]. を参照してください。 [!DNL Upgrade Compatibility Tool] [ガイド](../upgrade-compatibility-tool/overview.md) の詳細情報と高度なユースケースをご覧ください。

### ツールのダウンロード

Composer を使用してツールをダウンロードします。 PHP 7.3 以降、少なくとも 2GB の RAM、Node.js （GraphQLとの互換性を確認している場合）、およびAdobe Commerce ライセンスが必要です。

```bash
composer create-project magento/upgrade-compatibility-tool uct --repository https://repo.magento.com
```

### ツールを実行する

インスタンスを分析し、エラー、警告および重大な問題を確認するには：

```bash
bin/uct upgrade:check <dir> -c <coming version> 
```

>[!NOTE]
>
> この `<dir>` 引数は、コードベースが保存されるディレクトリです。 この `-c` オプションを選択すると、コードベースと指定したバージョンが比較されます。

チームが対処すべき最も重要な問題を特定するには：

```bash
bin/uct upgrade:check /path/to/magento/ --ignore-current-compatibility-issues –min-issue-level critical --vanilla-dir /path/to/vanilla/code/ /path/to/magento/app/code/Vendor/
```

このコマンドで使用するその他のオプションを次に示します。

- `--ignore-current-version-compatibility-issues` – 現在のバージョンに対する既知の重大な問題、エラー、警告をすべて抑制します。 アップグレードしようとしているバージョンに対するエラーのみが提供されます。

- `--min-issue-level` – 最小問題レベルを設定して、アップグレードで最も重要な問題にのみ優先順位を付けることができます。 オプションは、警告、エラー、重要で、重要度の高い順に表示されます。

- `-m | [=MODULE-PATH]` – 特定のベンダー、モジュール、またはディレクトリのみを分析する場合は、パスもオプションとして指定できます。

- `--vanilla-dir`- コアコードをチェックして、機能やカスタマイズが非標準で実装されていないか確認できます。 これらは事前にクリーンアップすることが重要です。 お使いのバージョンのバニラインスタンスが参照用に自動的にダウンロードされます。

  >[!NOTE]
  >
  > これは、 `core:code:changes` ツールのコマンド）。

### 出力の分析

この [!DNL Upgrade Compatibility Tool] は、影響を受けるコードまたはモジュール、重大度、問題の説明を検出した場合にその問題を識別する JSON ファイルを発生するごとに書き出します。 また、複雑さスコアを含んだ概要レポートも出力されるので、チームが最新バージョンにアップグレードする際に必要なことを大まかに理解できます。 複雑さのスコアが低いほど、アップグレードの実行が容易になります。

次の出力は、サマリーレポートの例を示しています。

```console
 ------------------------ --------
  Installed version        2.4.2
  Adobe Commerce version   2.4.3
  Running time             0m:48s
  Checked modules          14
  Core checked modules     0
  Core modified files      0
  % core modified files    0.00
  PHP errors found         109
  PHP warnings found       0
  GraphQL errors found     0
  GraphQL warnings found   0
  Total errors found       109
  Total warnings found     0
  Complexity score         218
 ------------------------ --------
```

### ヒントとアドバイス

ツールで特定されたすべての問題は、特定のエラーコードと共にレポートに表示されます。 の使用 [エラーメッセージの参照](../upgrade-compatibility-tool/error-messages.md) 各問題の詳細を確認する。 Adobeでは、是正手順を計画できるように、各問題のタイプを修正する提案も提供します。

レポートを使用して、アップグレード用のコードの更新に要する作業量を見積もります。 経験に基づいて、特定された問題の合計数と問題の重大度に基づいて、アップグレードに必要な労力を見積もることができます。 これはコマンドラインツールなので、これを自動テストおよびコードチェックスイートに組み込み、JSON 出力を使用してレポートを生成できます。

今後のアップグレード結果を以前の結果と比較できるように、各アップグレードプロジェクトの結果を保存することをお勧めします。 使用を続けると、ツールが提供する概要レポートから、次のバージョンへのアップグレードに要する労力のレベルを適切に把握できるようになります。

また、アップグレードに取り組む際は、進行状況を可視化できるように、ツールを定期的に実行することをお勧めします。 問題の数は、修正するにつれて減少する必要があります。 これは、チームが作業を配布する最適なアプローチを決定するのにも役立ちます。

この [!DNL Upgrade Compatibility Tool] 今後のリリースでは、Autofix などの機能が追加され、問題をできる限り迅速に解決できるようになります。 2022 年 1 月にリリースされた最新の機能強化には、PHP 8.1 の互換性テストおよびHTMLのビジュアライゼーション機能が含まれており、アップグレードに多くの労力が必要になる可能性のある領域をすばやく特定するのに役立ちます。
