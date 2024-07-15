---
title: LESS ファイルへのシンボリックリンクの作成
description: LESS ファイルへのシンボリックリンクを作成する方法を説明します。
exl-id: 58a6123a-28b4-445b-b3f9-f524233ac127
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 0%

---

# LESS ファイルへのシンボリックリンクの作成

{{file-system-owner}}

LESS ファイルへのシンボリックリンクを作成するには：

コマンドオプション：

```bash
bin/magento dev:source-theme:deploy [--type="..."] [--locale="..."] [--area="..."] [--theme="..."] [file1] ... [fileN]
```

>[!INFO]
>
>開発時に、`var/view_preprocessed` フォルダーおよび `pub/static` フォルダーに LESS ファイルのシンボリックリンクを作成します。 このプロセスでは、LESS ファイルを CSS ファイルにコンパイルしません。

次の表に、このコマンドのパラメータと値を示します。

| パラメーター | 値 | 必須？ |
| --------- | ----- | --------- |
| `--type` | ソースファイルのタイプ：[less] （デフォルト：「less」） <br> 現在、サポートされているファイルタイプは LESS のみです。 | 不可 |
| `--locale` | ロケールコード<br> ロケールコードのリストを表示するには、`bin/magento info:language:list` と入力します | 不可 |
| `--area` | 領域（管理領域の `adminhtml`、ストアフロントの `frontend`）。 | 不可 |
| `--theme` | テーマ名（`<VendorName>/<theme-name>` 形式）。 例えば、`Magento/blank` や `Magento/backend` です。 | 不可 |
| `<file>` | CSS 拡張子を使用せずに LESS に変換する CSS ファイルのスペース区切りリスト。 （adminhtml タイプ `css/styles css/styles-old` の場合、デフォルトは `css/styles-m css/styles-l`） | 不可 |

例えば、`<magento_root>/pub/static/frontend/VendorName/themeName/en_US/css/styles-l.css` という CSS ファイルを使用して、`en_US` ロケールの `VendorName/themeName` という名前のフロントエンドテーマに対して LESS ファイルを作成するには、次のコマンドを入力します。

```bash
bin/magento dev:source-theme:deploy --type="less" --locale="en_US" --area="frontend" --theme="VendorName/themeName" css/styles-l
```

成功を確認する次のメッセージが表示されます。

```terminal
Processed Area: frontend, Locale: en_US, Theme: VendorName/themeName, File type: less.
-> css/styles-l.less
Successfully processed.
```

管理者 HTML 用の LESS ファイルを作成するには、次の手順に従います。

```bash
bin/magento dev:source-theme:deploy --locale="en_US" --area="adminhtml" --theme="Magento/backend" css/styles css/styles-old
```
