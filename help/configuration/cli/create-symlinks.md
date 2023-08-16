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

LESS ファイルへの symlink を作成するには、次の手順に従います。

コマンドオプション：

```bash
bin/magento dev:source-theme:deploy [--type="..."] [--locale="..."] [--area="..."] [--theme="..."] [file1] ... [fileN]
```

>[!INFO]
>
>開発時に、このコマンドは LESS ファイルのシンボリックリンクを `var/view_preprocessed` および `pub/static` フォルダー。 このプロセスは、LESS ファイルを CSS ファイルにコンパイルしません。

次の表で、このコマンドのパラメータと値を説明します。

| パラメーター | 値 | 必須？ |
| --------- | ----- | --------- |
| `--type` | ソースファイルのタイプ： [より小さい] （デフォルト： &quot;less&quot;）<br>現在、LESS はサポートされる唯一のファイルタイプです。 | いいえ |
| `--locale` | ロケールコード。<br>ロケールコードのリストを表示するには、次のように入力します。 `bin/magento info:language:list` | いいえ |
| `--area` | 領域 (`adminhtml` 行政区域の `frontend` ストアフロント用 )。 | いいえ |
| `--theme` | のテーマ名 `<VendorName>/<theme-name>` 形式を使用します。 例： `Magento/blank` または `Magento/backend`. | いいえ |
| `<file>` | LESS に変換する CSS ファイルのスペース区切りリスト（CSS 拡張子を除く）。 ( デフォルトは `css/styles-m css/styles-l`、 adminhtml タイプの場合 `css/styles css/styles-old`) | いいえ |

例えば、次の名前のフロントエンドテーマの LESS ファイルを作成するには、次のように指定します。 `VendorName/themeName` （内） `en_US` ロケールで、 `<magento_root>/pub/static/frontend/VendorName/themeName/en_US/css/styles-l.css`、次のコマンドを入力します。

```bash
bin/magento dev:source-theme:deploy --type="less" --locale="en_US" --area="frontend" --theme="VendorName/themeName" css/styles-l
```

成功を確認する次のメッセージが表示されます。

```terminal
Processed Area: frontend, Locale: en_US, Theme: VendorName/themeName, File type: less.
-> css/styles-l.less
Successfully processed.
```

adminhtml 用の LESS ファイルを作成するには、次の手順に従います。

```bash
bin/magento dev:source-theme:deploy --locale="en_US" --area="adminhtml" --theme="Magento/backend" css/styles css/styles-old
```
