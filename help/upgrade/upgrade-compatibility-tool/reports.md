---
title: '[!DNL Upgrade Compatibility Tool] 報告書'
description: を実行するには、次の手順に従います [!DNL Upgrade Compatibility Tool] Adobe Commerce プロジェクトで、を行います。
exl-id: a2272339-46d6-443b-bd53-286b72f13d4e
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '584'
ht-degree: 0%

---

# レポート

{{commerce-only}}

分析の結果、 [!DNL Upgrade Compatibility Tool] では、重要度、エラーコード、エラーの説明を指定して、各ファイルの問題のリストを含むレポートを書き出すことができます。 この [!DNL Upgrade Compatibility Tool] レポートを次の 2 つの異なる形式に書き出します。

- A [JSON ファイル](reports.md#json-file).
- An [HTMLレポート](reports.md#html-report).

レポートの次のコマンドラインインターフェイスの例を参照してください。

```terminal
File: /app/code/Custom/CatalogExtension/Controller/Index/Index.php
------------------------------------------------------------------
 * [WARNING][1131] Line 10: Extending from class 'Magento\Framework\App\Action\Action' that is @deprecated on version '2.4.4'
 * [ERROR][1328] Line 10: Implemented interface 'Magento\Framework\App\Action\HttpGetActionInterface' that is non API on version '2.4.4'
```

を確認します [エラーメッセージの参照](../upgrade-compatibility-tool/error-messages.md) このレポートで生成される様々なエラーの詳細については、を参照してください。

このレポートには、次の項目を示す詳細なサマリーも含まれています。

- *現在のバージョン*：現在インストールされているバージョン
- *ターゲットバージョン*：アップグレード先のバージョン。
- *実行時間*：分析がレポートの作成にかかった時間（mm:ss）。
- *更新が必要なモジュール*：互換性の問題が含まれており、更新が必要なモジュールの割合。
- *更新が必要なファイル*：互換性の問題を含み、更新が必要なファイルの割合。
- *重大なエラーの合計*：見つかった重大なエラーの数。
- *合計エラー数*：見つかったエラーの数。
- *警告の合計*：見つかった警告の数。
- *メモリのピーク時の使用率*：の最大メモリ量 [!DNL Upgrade Compatibility Tool] が実行中に到達しました。

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

JSON ファイルの出力は、 [!DNL Upgrade Compatibility Tool] をコマンドラインインターフェイスで使用します。 この `JSON` ファイルには、に表示されるものとまったく同じ情報が含まれています [!DNL Upgrade Compatibility Tool] 出力：

- 特定された問題のリスト。
- 分析の概要です。

発生した問題ごとに、問題の重大度や説明などの詳細情報がレポートに表示されます。

これをエクスポートするには `JSON` ファイルを別の出力フォルダーに：

```bash
bin/uct upgrade:check <dir> --json-output-path[=JSON-OUTPUT-PATH]
```

ここで、引数は次のようになります。

- `<dir>`:Adobe Commerce インストールディレクトリ。
- `[=JSON-OUTPUT-PATH]`：をエクスポートするパスディレクトリ `JSON` 出力ファイル。

>[!NOTE]
>
> 出力フォルダーのデフォルトのパスはです。 `var/output/[TIME]-results.json`.

## HTMLレポート

HTMLレポートは、ツールをコマンドラインインターフェイスまたは経由で実行しているときに取得できます。 [!DNL Site-Wide Analysis Tool]. HTMLレポートには、次の内容も含まれます。

- 特定された問題のリスト。
- 分析の概要です。

![HTMLレポート – 概要](../../assets/upgrade-guide/uct-html-summary.png)

特定されたイシューは、次の時間帯に簡単に移動できます [!DNL Upgrade Compatibility Tool] 分析。

最小イシューレベルに応じて、レポートに表示されるイシューをフィルタリングできます（デフォルト値は `WARNING`）に設定します。

右上隅にドロップダウンがあり、別のレベルを選択できます。 識別された問題のリストは、それに応じてフィルタリングされます。

![HTMLレポート – ドロップダウンの使用状況](../../assets/upgrade-guide/uct-html-filtered-issues-list.png)

>[!NOTE]
>
> 問題レベルが低い問題は除外されますが、通知が届くので、モジュールごとに特定された問題を常に認識できます。

HTMLレポートには、次の 4 つの異なるグラフも含まれます。

- **問題の重要度別のモジュール**：モジュール別に重大度分布を表示します。
- **問題の重大度別のファイル**：ファイル別に重大度の分布を表示します。
- **問題の総数で並べ替えられたモジュール**：警告、エラー、重要なエラーを考慮して、最も侵害されたモジュール 10 個を表示します。
- **相対的なサイズと問題を持つモジュール**：モジュールに含まれるファイルが多いほど、円は大きくなります。 モジュールの問題が多いほど、その円は赤く表示されます。

これらのグラフを使用すると、最も侵害されているモジュールと、アップグレードの実行に追加の作業が必要なモジュールを識別できます。

![HTMLレポート – 図](../../assets/upgrade-guide/uct-html-diagrams.png)

HTMLレポート図も、次の点を除き、それに応じて更新されます `Modules with relative sizes and issues`。これは、で生成されます。 `min-issue-level` それは組織的に作られた。

に対して異なる結果を確認したい場合 `Modules with relative sizes and issues` 図です。コマンドを再実行して、に別の値を指定する必要があります `--min-issue-level` オプション。

![HTMLレポート – バブル・チャート図](../../assets/upgrade-guide/uct-html-filtered-diagrams.png)

このHTMLレポートを別の出力フォルダーにエクスポートするには：

```bash
bin/uct upgrade:check <dir> --html-output-path[=HTML-OUTPUT-PATH]
```

ここで、引数は次のようになります。

- `<dir>`:Adobe Commerce インストールディレクトリ。
- `[=HTML-OUTPUT-PATH]`：をエクスポートするパスディレクトリ `.html` 出力ファイル。

>[!NOTE]
>
> 出力フォルダーのデフォルトのパスはです。 `var/output/[TIME]-results.html`.
