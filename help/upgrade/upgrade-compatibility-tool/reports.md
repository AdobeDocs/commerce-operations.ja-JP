---
title: '"[!DNL Upgrade Compatibility Tool] レポート»'
description: 次の手順に従って、 [!DNL Upgrade Compatibility Tool] をAdobe Commerceプロジェクトに追加します。
source-git-commit: 147ecbc66eaf370e7ffaad0b6fce8b41f40b70df
workflow-type: tm+mt
source-wordcount: '583'
ht-degree: 0%

---


# レポート

{{commerce-only}}

分析の結果、 [!DNL Upgrade Compatibility Tool] では、各ファイルの重大度、エラーコード、エラーの説明を指定した問題のリストを含むレポートをエクスポートできます。 この [!DNL Upgrade Compatibility Tool] では、次の 2 つの異なる形式でレポートがエクスポートされます。

- A [JSON ファイル](reports.md#json-file).
- An [HTMLレポート](reports.md#html-report).

次のレポートのコマンドラインインターフェイスの例を参照してください。

```terminal
File: /app/code/Custom/CatalogExtension/Controller/Index/Index.php
------------------------------------------------------------------
 * [WARNING][1131] Line 10: Extending from class 'Magento\Framework\App\Action\Action' that is @deprecated on version '2.4.4'
 * [ERROR][1328] Line 10: Implemented interface 'Magento\Framework\App\Action\HttpGetActionInterface' that is non API on version '2.4.4'
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
- *メモリのピーク使用量*:最大メモリ量 [!DNL Upgrade Compatibility Tool] 実行中に到達しました。

次のコマンドラインインターフェイスの例を参照してください。

```terminal
 ----------------------------- ----------------- 
  Current version               2.4.1            
  Target version                2.4.4            
  Execution time                1m:8s            
  Modules that require update   71.67% (43/60)   
  Files that require update     18.05% (96/532)  
  Total critical issues         24               
  Total errors                  159              
  Total warnings                53               
  Memory peak usage             902.00 MB        
 ----------------------------- ----------------- 
```

## JSON ファイル

JSON ファイルの出力は、 [!DNL Upgrade Compatibility Tool] コマンドラインインターフェイス上で この `JSON` ファイルには、 [!DNL Upgrade Compatibility Tool] 出力：

- 特定された問題のリスト。
- 分析の概要。

発生した問題ごとに、問題の重大度や説明などの詳細情報がレポートに表示されます。

これを書き出すには `JSON` ファイルを別の出力フォルダーに配置します。

```bash
bin/uct upgrade:check <dir> --json-output-path[=JSON-OUTPUT-PATH]
```

引数は次のようになります。

- `<dir>`:Adobe Commerceインストールディレクトリ。
- `[=JSON-OUTPUT-PATH]`:書き出すパスディレクトリ `JSON` 出力ファイル。

>[!NOTE]
>
> 出力フォルダーのデフォルトのパスは、 `var/output/[TIME]-results.json`.

## HTMLレポート

HTMLレポートは、コマンドラインインターフェイスでツールを実行中、または [!DNL Site-Wide Analysis Tool]. HTMLレポートには、次のものも含まれます。

- 特定された問題のリスト。
- 分析の概要。

![HTMLレポート — 概要](../../assets/upgrade-guide/uct-html-summary.png)

特定された問題を、 [!DNL Upgrade Compatibility Tool] 分析。

最小問題レベル ( デフォルト値は `WARNING`) をクリックします。

右上隅にドロップダウンがあり、別のレベルを選択できます。 識別された問題のリストは、それに応じてフィルタリングされます。

![HTMLレポート — ドロップダウンの使用方法](../../assets/upgrade-guide/uct-html-filtered-issues-list.png)

>[!NOTE]
>
> 問題レベルが低い問題は削除されますが、通知が表示されるので、モジュールごとに識別された問題を常に把握できます。

HTMLレポートには、次の 4 つの異なるグラフも含まれます。

- **問題の重要度別のモジュール**:モジュール別の重大度の配分を表示します。
- **問題の重要度別のファイル**:ファイル別の重大度を表示します。
- **問題の総数別に並べられたモジュール**:警告、エラー、重大なエラーを考慮して、最も問題が発生した 10 個のモジュールを表示します。
- **相対的なサイズと問題を持つモジュール**:モジュールに含まれるファイルが多いほど、その円が大きくなります。 モジュールの問題が多いほど、その円が赤く表示されます。

これらのグラフでは、最も問題が発生したモジュールや、アップグレードを実行するためにより多くの作業が必要なモジュールを特定できます。

![HTMLレポート — 図](../../assets/upgrade-guide/uct-html-diagrams.png)

HTMLレポート図も、 `Modules with relative sizes and issues`( `min-issue-level` それは通常設置されていた

異なる結果を表示するには、 `Modules with relative sizes and issues` 図に示すように、コマンドを再実行して、 `--min-issue-level` オプション。

![HTMLレポート — バブルチャート図](../../assets/upgrade-guide/uct-html-filtered-diagrams.png)

このHTMLレポートを別の出力フォルダーに書き出すには：

```bash
bin/uct upgrade:check <dir> --html-output-path[=HTML-OUTPUT-PATH]
```

引数は次のようになります。

- `<dir>`:Adobe Commerceインストールディレクトリ。
- `[=HTML-OUTPUT-PATH]`:書き出すパスディレクトリ `.html` 出力ファイル。

>[!NOTE]
>
> 出力フォルダーのデフォルトのパスは、 `var/output/[TIME]-results.html`.
