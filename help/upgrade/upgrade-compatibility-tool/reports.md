---
title: '[!DNL Upgrade Compatibility Tool] レポート'
description: Adobe Commerce上のプロジェクトを実行するには、次  [!DNL Upgrade Compatibility Tool]  手順に従います。
exl-id: a2272339-46d6-443b-bd53-286b72f13d4e
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '584'
ht-degree: 0%

---

# レポート

{{commerce-only}}

分析の結果、[!DNL Upgrade Compatibility Tool] は、重要度、エラーコード、エラーの説明を指定する各ファイルの問題のリストを含むレポートを書き出すことができます。 [!DNL Upgrade Compatibility Tool] では、レポートが次の 2 つの異なる形式で書き出されます。

- [JSON ファイル ](reports.md#json-file)。
- [HTMLレポート ](reports.md#html-report)。

レポートの次のコマンドラインインターフェイスの例を参照してください。

```
File: /app/code/Custom/CatalogExtension/Controller/Index/Index.php
------------------------------------------------------------------
 * [WARNING][1131] Line 10: Extending from class 'Magento\Framework\App\Action\Action' that is @deprecated on version '2.4.4'
 * [ERROR][1328] Line 10: Implemented interface 'Magento\Framework\App\Action\HttpGetActionInterface' that is non API on version '2.4.4'
```

このレポートで生成される様々なエラーの詳細については、「[ エラーメッセージのリファレンス ](../upgrade-compatibility-tool/error-messages.md)」トピックを参照してください。

このレポートには、次の項目を示す詳細なサマリーも含まれています。

- *最新バージョン*：現在インストールされているバージョン。
- *ターゲットバージョン*：アップグレード先のバージョン。
- *実行時間*: レポートの作成に分析にかかった時間（mm:ss）。
- *更新が必要なモジュール*：互換性の問題が含まれており、更新が必要なモジュールの割合。
- *更新が必要なファイル*：互換性の問題が含まれており、更新が必要なファイルの割合。
- *重大なエラーの合計数*：見つかった重大なエラーの数。
- *合計エラー数*：見つかったエラーの数。
- *警告の合計数*：見つかった警告の数。
- *メモリのピーク使用量*：実行中に [!DNL Upgrade Compatibility Tool] ージが到達したメモリの最大量です。

次のコマンドラインインターフェイスの例を参照してください。

```
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

[!DNL Upgrade Compatibility Tool] をコマンドラインインターフェイスで実行している間に、JSON ファイルの出力を取得できます。 `JSON` ファイルには、[!DNL Upgrade Compatibility Tool] の出力で示されたものとまったく同じ情報が含まれています。

- 特定された問題のリスト。
- 分析の概要です。

発生した問題ごとに、問題の重大度や説明などの詳細情報がレポートに表示されます。

この `JSON` ファイルを別の出力フォルダーに書き出すには：

```bash
bin/uct upgrade:check <dir> --json-output-path[=JSON-OUTPUT-PATH]
```

ここで、引数は次のようになります。

- `<dir>`:Adobe Commerce インストールディレクトリ。
- `[=JSON-OUTPUT-PATH]`: `JSON` 出力ファイルをエクスポートするパスディレクトリ。

>[!NOTE]
>
> 出力フォルダーのデフォルトのパスは `var/output/[TIME]-results.json` です。

## HTMLレポート

コマンドラインインターフェイスまたは [!DNL Site-Wide Analysis Tool] を使用してHTMLを実行すると、ツールレポートを取得できます。 HTMLレポートには、次の内容も含まれます。

- 特定された問題のリスト。
- 分析の概要です。

![HTMLレポート – 概要 ](../../assets/upgrade-guide/uct-html-summary.png)

分 [!DNL Upgrade Compatibility Tool] 分析中に、特定された問題を簡単に移動できます。

最小イシューレベルに応じて、レポートに表示されるイシューをフィルタリングできます（デフォルト値は `WARNING`）。

右上隅にドロップダウンがあり、別のレベルを選択できます。 識別された問題のリストは、それに応じてフィルタリングされます。

![HTMLレポート – ドロップダウンの使用状況 ](../../assets/upgrade-guide/uct-html-filtered-issues-list.png)

>[!NOTE]
>
> 問題レベルが低い問題は除外されますが、通知が届くので、モジュールごとに特定された問題を常に認識できます。

HTMLレポートには、次の 4 つの異なるグラフも含まれます。

- **問題の重要度別のモジュール**：モジュール別の重要度の分布を表示します。
- **問題の重大度別のファイル**：ファイルごとの重大度分布を表示します。
- **問題数別に並べ替えられたモジュール**：警告、エラー、重要なエラーを考慮して、最も侵害されたモジュール 10 個を表示します。
- **相対的なサイズと問題を持つモジュール**：モジュールに含まれるファイルが多いほど、円が大きくなります。 モジュールの問題が多いほど、その円は赤く表示されます。

これらのグラフを使用すると、最も侵害されているモジュールと、アップグレードの実行に追加の作業が必要なモジュールを識別できます。

![HTMLレポート – 図 ](../../assets/upgrade-guide/uct-html-diagrams.png)

HTMLレポート図も、それに応じて更新されます。ただし、`Modules with relative sizes and issues` は、組織で設定された `min-issue-level` で生成されます。

`Modules with relative sizes and issues` の図で異なる結果を表示する場合は、コマンドを再実行して、`--min-issue-level` オプションに別の値を指定する必要があります。

![HTMLレポート – バブル チャート図 ](../../assets/upgrade-guide/uct-html-filtered-diagrams.png)

このHTMLレポートを別の出力フォルダーにエクスポートするには：

```bash
bin/uct upgrade:check <dir> --html-output-path[=HTML-OUTPUT-PATH]
```

ここで、引数は次のようになります。

- `<dir>`:Adobe Commerce インストールディレクトリ。
- `[=HTML-OUTPUT-PATH]`: `.html` 出力ファイルをエクスポートするパスディレクトリ。

>[!NOTE]
>
> 出力フォルダーのデフォルトのパスは `var/output/[TIME]-results.html` です。
