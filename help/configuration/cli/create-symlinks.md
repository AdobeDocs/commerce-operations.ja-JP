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
>開発時に、このコマンドは LESS ファイルのシンボリックリンクを `var/view_preprocessed` および `pub/static` フォルダー。 このプロセスでは、LESS ファイルを CSS ファイルにコンパイルしません。

次の表に、このコマンドのパラメータと値を示します。

| パラメーター | 値 | 必須？ |
| --------- | ----- | --------- |
| `--type` | ソースファイルの種類： [より小さい] （デフォルト：&quot;less&quot;）<br>現在、LESS がサポートされている唯一のファイル・タイプです。 | 不可 |
| `--locale` | ロケールコード<br>ロケールコードのリストを表示するには、を入力します `bin/magento info:language:list` | 不可 |
| `--area` | 領域（`adminhtml` 管理領域については、 `frontend` ストアフロント用）。 | 不可 |
| `--theme` | のテーマ名 `<VendorName>/<theme-name>` 形式。 例： `Magento/blank` または `Magento/backend`. | 不可 |
| `<file>` | CSS 拡張子を使用せずに LESS に変換する CSS ファイルのスペース区切りリスト。 （デフォルトは `css/styles-m css/styles-l`、adminhtml タイプ用 `css/styles css/styles-old`） | 不可 |

例えば、という名前のフロントエンドテーマに LESS ファイルを作成するには、次のように指定します `VendorName/themeName` が含まれる `en_US` という名前の CSS ファイルを使用したロケール `<magento_root>/pub/static/frontend/VendorName/themeName/en_US/css/styles-l.css`を入力し、次のコマンドを入力します。

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
