---
title: レイアウトファイルの変換
description: XML レイアウトファイルを変換します。
exl-id: 9852b735-9b4b-43ce-887f-5c37d398bbf7
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '82'
ht-degree: 0%

---

# XML レイアウトファイルの変換

{{file-system-owner}}

対応する XSLT （Extensible Stylesheet Language Transformations） スタイルシートを更新する場合は、このコマンドを使用してレイアウト XML ファイルを更新します。

- [レイアウトの説明](https://developer.adobe.com/commerce/frontend-core/guide/layouts/xml-instructions/)
- [レイアウトファイルタイプ](https://developer.adobe.com/commerce/frontend-core/guide/layouts/types/)

コマンドオプション：

```bash
bin/magento dev:xml:convert [-o|--overwrite] {xml file} {xslt stylesheet}
```

ここで、

- `{xml file}` – 変換するレイアウト XML ファイルの完全パスとファイル名です（必須）
- `{xslt stylesheet}` – 変換に使用する XSLT スタイルシート ファイルの完全パスとファイル名（必須）
- `-o|--overwrite` – 既存の XML ファイルを上書きするには、このオプションを含めます
