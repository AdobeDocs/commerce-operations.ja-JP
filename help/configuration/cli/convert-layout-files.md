---
title: レイアウトファイルの変換
description: XML レイアウトファイルを変換します。
source-git-commit: 02f02393878d04b4a0fcdae256ac1ac5dd13b7f6
workflow-type: tm+mt
source-wordcount: '94'
ht-degree: 0%

---


# XML レイアウトファイルの変換

{{file-system-owner}}

対応する XSLT(Extensible Stylesheet Language Transformations) スタイルシートを更新する場合は、このコマンドを使用してレイアウト XML ファイルを更新します。

- [レイアウトの手順](https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/layouts/xml-instructions.html)
- [レイアウトファイルの種類](https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/layouts/layout-types.html)

コマンドオプション：

```bash
bin/magento dev:xml:convert [-o|--overwrite] {xml file} {xslt stylesheet}
```

ここで、

- `{xml file}` — 変換するレイアウト XML ファイルのフルパスとファイル名（必須）
- `{xslt stylesheet}` — 変換に使用する XSLT スタイルシートファイルのフルパスとファイル名（必須）
- `-o|--overwrite` — 既存の XML ファイルを上書きするには、このオプションを含めます
