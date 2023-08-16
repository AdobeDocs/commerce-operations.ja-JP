---
title: レイアウトファイルの変換
description: XML レイアウトファイルを変換します。
exl-id: 9852b735-9b4b-43ce-887f-5c37d398bbf7
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '94'
ht-degree: 0%

---

# XML レイアウトファイルの変換

{{file-system-owner}}

対応する XSLT(Extensible Stylesheet Language Transformations) スタイルシートを更新する場合は、このコマンドを使用してレイアウト XML ファイルを更新します。

- [レイアウトの手順](https://developer.adobe.com/commerce/frontend-core/guide/layouts/xml-instructions/)
- [レイアウトファイルの種類](https://developer.adobe.com/commerce/frontend-core/guide/layouts/types/)

コマンドオプション：

```bash
bin/magento dev:xml:convert [-o|--overwrite] {xml file} {xslt stylesheet}
```

次の場合：

- `{xml file}` — 変換するレイアウト XML ファイルのフルパスとファイル名（必須）
- `{xslt stylesheet}` — 変換に使用する XSLT スタイルシートファイルのフルパスとファイル名（必須）
- `-o|--overwrite` — 既存の XML ファイルを上書きするには、このオプションを含めます
