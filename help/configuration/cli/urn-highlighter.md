---
title: URN ハイライター
description: Adobe Commerce開発用の IDE で URN のハイライト表示を設定する方法を説明します。 XSD スキーマの設定と開発の最適化について説明します。
exl-id: 6389ab58-af70-4b33-800e-be3191c5a4cc
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '187'
ht-degree: 0%

---

# URN ハイライターの概要

{{file-system-owner}}

Commerce コードは、すべての XSD スキーマを [Uniform Resource Name （URN） ](https://www.ietf.org/rfc/rfc2141.txt) として参照します。 コードを開発していて、XSD を参照する必要がある場合、このコマンドは、URN を認識して強調表示するように統合開発環境（IDE）を設定します。 これにより、開発が容易になります。

デフォルトでは、PhpStorm などの IDE は URN を認識するように設定されていないため、次のように赤いテキストで表示されます。

![URN を認識するように PhpStorm が設定されていません ](../../assets/configuration/urn-before.png)

`bin/magento dev:urn-catalog:generate` コマンドを使用すると、IDE （現在は PhpStorm と Visual Studio Code のみ）で次のような URN を認識して強調表示できます。

![URN を認識する IDE の有効化 ](../../assets/configuration/urn-after.png)

具体的には、このコマンドは次の PhpStorm 設定を作成します。

![PhpStorm の設定例 ](../../assets/configuration/urn-settings.png)

## IDE の設定

現在、PhpStorm と Visual Studio Code のみがサポートされています。

コマンド構文：

```bash
bin/magento dev:urn-catalog:generate <path>
```

ここで、`<path>` は PhpStorm `misc.xml` ファイルへのパスです。このファイルは、プロジェクトのルートからの相対パスで配置されます。 通常、`<path>` は `.idea/misc.xml` です。

>[!INFO]
>
>「スキーマと DTD」を最新の状態に保つには、`dev:urn-catalog:generate` ファイルを含むCommerce 2 モジュールを追加、変更、削除するたびに `*.xsd` コマンドを実行します。
