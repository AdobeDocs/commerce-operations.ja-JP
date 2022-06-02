---
title: '"[!DNL Upgrade Compatibility Tool] レポート»'
description: 次の手順に従って、 [!DNL Upgrade Compatibility Tool] をAdobe Commerceプロジェクトに追加します。
source-git-commit: e539824b336978debd6e6adc538cd8bad367eff1
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 0%

---


# レポート

{{commerce-only}}

分析の結果、 [!DNL Upgrade Compatibility Tool] は、各ファイルの重大度、エラーコード、エラーの説明を指定した問題のリストを含むレポートをエクスポートします。

次の例を参照してください。

```terminal
File: /app/code/Custom/CatalogExtension/Controller/Index/Index.php
------------------------------------------------------------------
 * [WARNING][1131] Line 23: Extending from class 'Magento\Framework\App\Action\Action' that is @deprecated on version '2.4.2'
 * [ERROR][1429] Line 103: Call method 'Magento\Framework\Api\SearchCriteriaBuilder::addFilters' that is non API on version '2.4.2'
 * [CRITICAL][1110] Line 60: Instantiating class/interface 'Magento\Catalog\Model\ProductRepository' that does not exist on version '2.4.2'
```

次を確認します。 [エラーメッセージの参照](../upgrade-compatibility-tool/error-messages.md) トピックを参照してください。

また、このレポートには、次の内容を示す詳細な概要も含まれます。

- *現在のバージョン*:現在インストールされているバージョン。
- *ターゲットバージョン*:アップグレード先のバージョン。
- *実行時間*:分析がレポートの作成に要した時間 (mm:ss)。
- *更新が必要なモジュール*:互換性の問題があり、更新が必要なモジュールの割合。
- *更新が必要なファイル*:互換性の問題が含まれ、更新が必要なファイルの割合。
- *重大なエラーの合計*:検出された重大なエラーの数。
- *合計エラー数*:見つかったエラーの数。
- *合計警告数*:見つかった警告の数。

次の例を参照してください。

```terminal
 ----------------------------- ------------------
  Current version               2.4.2
  Target version                2.4.3
  Execution time                1m:10s
  Modules that require update   78.33% (47/60)
  Files that require update     21.62% (115/532)
  Total critical issues         35
  Total errors                  201
  Total warnings                103
 ----------------------------- ------------------
```

>[!NOTE]
>
>デフォルトでは、 [!DNL Upgrade Compatibility Tool] では、次の 2 つの異なる形式でレポートがエクスポートされます。 `json` および `html`.

## JSON ファイル

JSON ファイルには、出力に表示される情報とまったく同じものが含まれます。

- 特定された問題のリスト。
- 分析の概要。

発生した問題ごとに、問題の重大度や説明などの詳細情報がレポートに表示されます。

このレポートを別の出力フォルダーにエクスポートするには、次のコマンドを実行します。

```bash
bin/uct upgrade:check <dir> --json-output-path[=JSON-OUTPUT-PATH]
```

引数は次のようになります。

- `<dir>`:Adobe Commerceインストールディレクトリ。
- `[=JSON-OUTPUT-PATH]`:書き出すパスディレクトリ `.json` 出力ファイル。

>[!NOTE]
>
>出力フォルダーのデフォルトのパスは、 `var/output/[TIME]-results.json`.

## HTMLレポート

HTMLファイルには、分析の概要と、特定された問題のリストも含まれています。 HTMLレポートは、コマンドラインインターフェイスでツールを実行中、または [!DNL Site-Wide Analysis Tool].

![HTMLレポート — 概要](../../assets/upgrade-guide/uct-html-summary.png)

特定された問題を、 [!DNL Upgrade Compatibility Tool] 分析：

![HTMLレポート — 詳細](../../assets/upgrade-guide/uct-html-details.png)

HTMLレポートには、次の 4 つの異なるグラフも含まれます。

- **問題の重要度別のモジュール**:モジュール別の重大度の配分を表示します。
- **問題の重要度別のファイル**:ファイル別の重大度を表示します。
- **問題の総数別に並べられたモジュール**:警告、エラー、重大なエラーを考慮して、最も問題が発生した 10 個のモジュールを表示します。
- **相対的なサイズと問題を持つモジュール**:モジュールに含まれるファイルが多いほど、その円が大きくなります。 モジュールの問題が多いほど、その円が赤く表示されます。

これらのグラフでは、最も問題が発生したパーツや、アップグレードを実行するためにより多くの作業が必要なパーツを（一目で）特定できます。

![HTMLレポート — 図](../../assets/upgrade-guide/uct-html-diagrams.png)

レポートに表示される問題を、最小の問題レベルに応じてフィルタリングできます。 デフォルト値は `WARNING`.

右上隅にドロップダウンがあり、必要に応じて別のドロップダウンを選択できます。 識別された問題のリストは、それに応じてフィルタリングされます。

![HTMLレポート — ドロップダウンの使用方法](../../assets/upgrade-guide/uct-html-filtered-issues-list.png)

問題レベルが低い問題は削除されますが、通知が表示されるので、モジュールごとに識別された問題を常に把握できます。

また、図は、 `Modules with relative sizes and issues`( `min-issue-level` 最初に設定されました。

異なる結果を表示する場合は、コマンドを再実行して、 `--min-issue-level` オプション。

![HTMLレポート — バブルチャート図](../../assets/upgrade-guide/uct-html-filtered-diagrams.png)

このレポートを別の出力フォルダーにエクスポートするには、次の手順を実行します。

```bash
bin/uct upgrade:check <dir> --html-output-path[=HTML-OUTPUT-PATH]
```

引数は次のようになります。

- `<dir>`:{{site.data.var.ee}} のインストールディレクトリ。
- `[=HTML-OUTPUT-PATH]`:書き出すパスディレクトリ `.html` 出力ファイル。

>[!NOTE]
>
> 出力フォルダーのデフォルトのパスは、 `var/output/[TIME]-results.html`.
