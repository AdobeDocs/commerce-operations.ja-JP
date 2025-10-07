---
title: レイアウトファイルの変換
description: Adobe Commerce コマンドラインツールを使用して XML レイアウトファイルを変換する方法を説明します。 XSLT スタイルシートの更新とファイル変換プロセスについて説明します。
exl-id: 9852b735-9b4b-43ce-887f-5c37d398bbf7
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '98'
ht-degree: 0%

---

# XML レイアウトファイルの変換

{{file-system-owner}}

対応する XSLT （Extensible Stylesheet Language Transformations） スタイルシートを更新する場合は、このコマンドを使用してレイアウト XML ファイルを更新します。

- [ レイアウトの説明 ](https://developer.adobe.com/commerce/frontend-core/guide/layouts/xml-instructions/)
- [ レイアウトファイルのタイプ ](https://developer.adobe.com/commerce/frontend-core/guide/layouts/types/)

コマンドオプション：

```bash
bin/magento dev:xml:convert [-o|--overwrite] {xml file} {xslt stylesheet}
```

ここで、

- `{xml file}` – 変換するレイアウト XML ファイルのフル・パスとファイル名（必須）
- `{xslt stylesheet}` – 変換に使用する XSLT スタイルシート・ファイルのフル・パスとファイル名（必須）
- `-o|--overwrite` – 既存の XML ファイルを上書きする場合は、このオプションを含めます
