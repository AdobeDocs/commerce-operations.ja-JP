---
title: アップグレード範囲について
description: Adobe Commerce、Magento Open Sourceのカスタムモジュール、またはサードパーティの拡張機能に影響を与える可能性のある、リリースにおける後方互換性のない変更について説明します。
source-git-commit: 682963fb66519097e54f14f2b84ed71528030054
workflow-type: tm+mt
source-wordcount: '928'
ht-degree: 0%

---


# アップグレードの範囲の理解

以下を確認します。 [リリースノート](https://devdocs.magento.com/guides/v2.4/release-notes/bk-release-notes.html) を参照して、サードパーティ製モジュールやカスタムモジュールに影響を及ぼす可能性のある機能強化、バグ修正、既知の問題など、リリースの範囲を理解してください。

## 後方互換性のない変更

Adobe CommerceおよびMagento Open Sourceリリースには、後方互換性のない変更が含まれている場合があります。 後方互換性のない変更に関するドキュメントを確認するには、以下を参照してください。

- **[主な変更点](https://devdocs.magento.com/guides/v2.4/release-notes/backward-incompatible-changes/index.html)** — 大きな影響を及ぼし、詳細な説明と特別な手順が必要な変更により、サードパーティ製モジュールが引き続き動作するようにします。
- **[軽微な変更の参照](https://devdocs.magento.com/guides/v2.4/release-notes/backward-incompatible-changes/reference.html)** — コードベースから生成された参照ドキュメントで、クラス、API メンバーシップ、データベース、依存関係インジェクション、インターフェイス、レイアウト、システム、XSD に対する小さな変更を説明します。

## サードパーティの拡張機能

Adobe Commerce Marketplace の新しい互換性ポリシーにより、 _すべて_ リストに記載された拡張機能は、GA 日から 30 日以内にリリースされた最新バージョンと互換性があります。 このため、可能な限り Marketplace からサードパーティの拡張機能を入手することが重要です。

## カスタムモジュール

すべてのカスタムモジュールは、アップグレード先のターゲットバージョンと照合する必要があります。 これは、アップグレードの最も時間とリソースを消費するプロセスです。 カスタムモジュールを評価する際は、後方互換性のない変更を探し、コントローラの分解などの新しい慣行に注意する必要があります。 詳しくは、 [リリースノート](https://devdocs.magento.com/guides/v2.4/release-notes/bk-release-notes.html). また、フォローしていることを確認してください [ベストプラクティス](https://developer.adobe.com/commerce/php/best-practices/extensions/) モジュール開発用。

## [!DNL Upgrade Compatibility Tool]

この [!DNL Upgrade Compatibility Tool] は、潜在的なアップグレードの問題についてインスタンスを分析するコマンドラインツールです。 インストールした現在のバージョンと、アップグレード先のバージョンとの間の問題を確認します。

このツールを使用すると、チームがアップグレードの範囲と影響を把握するのに必要な作業を削減できます。 アップグレード時に一般的なコードの問題を回避し、識別された問題の解決方法を明確に示します。 また、アップグレードを成功させるために必要な最も重要な問題を優先させ、アップグレード時の時間とコストの両方を節約するのに役立ちます。

以下の節で [!DNL Upgrade Compatibility Tool]. 詳しくは、 [!DNL Upgrade Compatibility Tool] [ガイド](../upgrade-compatibility-tool/overview.md) を参照してください。

### ツールをダウンロード

ツールをダウンロードするには、Composer を使用します。 PHP 7.3 以降、少なくとも 2GB の RAM、Node.js(GraphQLの互換性を確認している場合 )、Adobe Commerceライセンスが必要です。

```bash
composer create-project magento/upgrade-compatibility-tool uct --repository https://repo.magento.com
```

### ツールを実行

インスタンスを分析し、エラー、警告、および重要な問題を確認するには、次の手順を実行します。

```bash
bin/uct upgrade:check <dir> -c <coming version> 
```

>[!NOTE]
>
> この `<dir>` 引数は、コードベースが保存されるディレクトリです。 この `-c` オプションは、コードベースと指定したバージョンを比較します。

チームが対処する最も重要な問題を特定するには、次の手順に従います。

```bash
bin/uct upgrade:check /path/to/magento/ --ignore-current-compatibility-issues –min-issue-level critical --vanilla-dir /path/to/vanilla/code/ /path/to/magento/app/code/Vendor/
```

このコマンドで使用するその他のオプションを次に示します。

- `--ignore-current-version-compatibility-issues` — 現在のバージョンに対する既知の重要な問題、エラー、警告をすべて抑制します。 アップグレードしようとしているバージョンに対してのみエラーが発生します。

- `--min-issue-level` — 最小問題レベルを設定して、アップグレードで最も重要な問題のみを優先順位付けできるようにします。 オプションは、警告、エラー、および重大度が昇順の重大度です。

- `-m | [=MODULE-PATH]` — 特定のベンダー、モジュール、ディレクトリのみを分析する場合は、パスもオプションとして指定できます。

- `--vanilla-dir` — コアコードで、非標準的な機能の実装やカスタマイズを確認できます。 これらは事前にクリーンアップしておくことが重要です。 ご使用のバージョンのバニラインスタンスが、参照用に自動的にダウンロードされます。

   >[!NOTE]
   >
   > これは、 `core:code:changes` 」コマンドを使用 )。

### 出力の分析

この [!DNL Upgrade Compatibility Tool] では、影響を受けるコードやモジュール、重大度、問題の説明を、発生したすべての問題について特定する JSON ファイルを書き出します。 また、複雑性スコアを含む概要レポートを出力し、最新バージョンにアップグレードするのに必要な事項をチームがおおまかに把握できます。 複雑性のスコアが低いほど、アップグレードを実行するのが容易になります。

次の出力は、サマリレポートの例を示しています。

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

特定されたツールに関するすべての問題が、特定のエラーコードと共にレポートに表示されます。 以下を使用： [エラーメッセージリファレンス](../upgrade-compatibility-tool/error-messages.md) を参照して、各問題の詳細を確認します。 Adobeでは、修正手順を計画できるように、各問題の種類を修正するための提案も提供されています。

レポートを使用して、アップグレードのためのコードの更新に要する労力を見積もります。 経験に基づいて、特定された問題の合計数と問題の重大度に基づいて、アップグレードに必要な作業を見積もることができます。 これはコマンドラインツールなので、これを自動テストおよびコードチェックスイートに組み込み、JSON 出力を使用してレポートを生成できます。

各アップグレードプロジェクトの結果を保存して、今後のアップグレード結果と以前の結果を比較できるようにすることをお勧めします。 継続的に使用すると、ツールが提供する概要レポートから次のバージョンにアップグレードするのに必要な作業のレベルを十分に把握できるようになります。

また、アップグレードの作業中は、ツールを定期的に実行して、進行状況を確認することをお勧めします。 問題の数は、修正に伴って減少します。 これは、チームが作業を配布する最適な方法を決定するのにも役立ちます。

この [!DNL Upgrade Compatibility Tool] はで引き続き改善されます。今後のリリースには、できるだけ早く問題を修正できるように autofix などの機能が含まれる予定です。 2022 年 1 月にリリースされた最新の改善点には、PHP 8.1 の互換性テストとHTMLの視覚化機能が含まれており、アップグレードに手間がかかる領域を迅速に特定できます。
