---
title: URN 蛍光ペン
description: IDE で URN ハイライトを設定する方法を説明します。
exl-id: 6389ab58-af70-4b33-800e-be3191c5a4cc
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 0%

---

# URN ハイライトの概要

{{file-system-owner}}

コマースコードは、すべての XSD スキーマを [URN (Uniform Resource Name)](https://www.ietf.org/rfc/rfc2141.txt). コードを開発し、XSD を参照する必要がある場合、このコマンドは、URN を認識してハイライト表示するように統合開発環境 (IDE) を設定します。 これにより、開発が容易になります。

デフォルトでは、PhpStorm のような IDE は URN を認識するように設定されておらず、その結果、次のように赤いテキストで表示されます。

![PhpStorm が URN を認識するように設定されていません](../../assets/configuration/urn-before.png)

The `bin/magento dev:urn-catalog:generate` コマンドを使用すると、IDE（現在は PhpStorm と Visual Studio Code のみ）で次のように URN を認識し、ハイライト表示できます。

![IDE が URN を認識できるようにする](../../assets/configuration/urn-after.png)

特に、このコマンドは次の PhpStorm 設定を作成します。

![PhpStorm の設定例](../../assets/configuration/urn-settings.png)

## IDE の設定

現在は、PhpStorm と Visual Studio Code のみがサポートされています。

コマンドの構文：

```bash
bin/magento dev:urn-catalog:generate <path>
```

ここで、 `<path>` は、PhpStorm へのパスです。 `misc.xml` ファイル。プロジェクトのルートを基準とした場所です。 通常、 `<path>` 次に該当 `.idea/misc.xml`.

>[!INFO]
>
>「スキーマと DTD」を最新の状態に保つには、 `dev:urn-catalog:generate` コマンドを実行します。 `*.xsd` ファイル。
