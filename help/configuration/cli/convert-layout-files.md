---
title: レイアウトファイルの変換
description: Adobe Commerce コマンドラインツールを使用してXML レイアウトファイルを変換する方法について説明します。 XSLT スタイルシートの更新とファイル変換プロセスについて説明します。
exl-id: 9852b735-9b4b-43ce-887f-5c37d398bbf7
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
