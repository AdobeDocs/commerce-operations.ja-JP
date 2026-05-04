---
title: レイアウトファイルの変換
description: Adobe Commerce コマンドラインツールを使用してXML レイアウトファイルを変換する方法について説明します。 XSLT スタイルシートの更新とファイル変換プロセスについて説明します。
exl-id: 9852b735-9b4b-43ce-887f-5c37d398bbf7
source-git-commit: f9a135fc63574ccbecd3f564a87fc5c4ac03f009
workflow-type: tm+mt
source-wordcount: '118'
ht-degree: 0%

---

# XML レイアウトファイルの変換

{{file-system-owner}}

対応する拡張可能なスタイルシート言語変換（XSLT）スタイルシートを更新する場合は、このコマンドを使用してレイアウト XML ファイルを更新します。

- [レイアウト手順](https://developer.adobe.com/commerce/frontend-core/guide/layouts/xml-instructions)
- [レイアウトファイルタイプ](https://developer.adobe.com/commerce/frontend-core/guide/layouts/#layout-files-types-and-conventions)

コマンドオプション：

```shell
bin/magento dev:xml:convert [-o|--overwrite] {xml file} {xslt stylesheet}
```

どこで：

- `{xml file}` – 変換するレイアウト XML ファイルの完全なパスとファイル名（必須）
- `{xslt stylesheet}` – 変換に使用するXSLT スタイルシートファイルのフルパスとファイル名（必須）
- `-o|--overwrite` – 既存のXML ファイルを上書きするには、このオプションを含めます
