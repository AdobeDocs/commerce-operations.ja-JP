---
title: LESS ファイルへのシンボリックリンクの作成
description: Adobe Commerce開発用にLESS ファイルへのシンボリックリンクを作成する方法を説明します。 スタイルシートのリンクや開発ワークフローの最適化についてご紹介します。
exl-id: 58a6123a-28b4-445b-b3f9-f524233ac127
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 0%
---
# LESS ファイルへのシンボリックリンクの作成

{{file-system-owner}}

LESS ファイルへのシンボリックリンクを作成するには：

コマンドオプション：

```shell
bin/magento dev:source-theme:deploy [--type="..."] [--locale="..."] [--area="..."] [--theme="..."] [file1] ... [fileN]
```

>[!INFO]
>
>このコマンドは、開発中に、`var/view_preprocessed`および`pub/static` フォルダー内のLESS ファイルのシンボリックリンクを作成します。 このプロセスでは、LESS ファイルをCSS ファイルにコンパイルしません。

次の表に、このコマンドのパラメーターと値を示します。

| パラメーター | 値 | 必要ですか？ |
| --------- | ----- | --------- |
| `--type` | ソースファイルの種類：[less] （デフォルト：「less」） <br>現在、サポートされているファイルタイプはLESSのみです。 | いいえ |
| `--locale` | ロケールコード。<br> ロケールコードのリストを表示するには、`bin/magento info:language:list`と入力します | いいえ |
| `--area` | 管理領域（`adminhtml`、ストアフロントの`frontend`）。 | いいえ |
| `--theme` | `<VendorName>/<theme-name>`形式のテーマ名。 例：`Magento/blank`または`Magento/backend` | いいえ |
| `<file>` | CSS拡張機能なしでLESSに変換するCSS ファイルのスペース区切りリスト。 （adminhtml タイプ `css/styles css/styles-old`のデフォルトは`css/styles-m css/styles-l`です） | いいえ |

例えば、`<magento_root>/pub/static/frontend/VendorName/themeName/en_US/css/styles-l.css`という名前のCSS ファイルを使用して、`en_US` ロケールの`VendorName/themeName`という名前のフロントエンドテーマのLESS ファイルを作成するには、次のコマンドを入力します。

```shell
bin/magento dev:source-theme:deploy --type="less" --locale="en_US" --area="frontend" --theme="VendorName/themeName" css/styles-l
```

成功を確認するには、次のメッセージが表示されます。

```text
Processed Area: frontend, Locale: en_US, Theme: VendorName/themeName, File type: less.
-> css/styles-l.less
Successfully processed.
```

Adminhtml用にLESS ファイルを作成するには：

```shell
bin/magento dev:source-theme:deploy --locale="en_US" --area="adminhtml" --theme="Magento/backend" css/styles css/styles-old
```
