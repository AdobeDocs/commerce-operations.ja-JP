---
title: URN ハイライター
description: Adobe Commerce開発用IDEでURN強調表示を設定する方法を説明します。 XSD スキーマの設定と開発の最適化について説明します。
exl-id: 6389ab58-af70-4b33-800e-be3191c5a4cc
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
source-wordcount: '191'
ht-degree: 0%
---
# URN ハイライターの概要

{{file-system-owner}}

Commerce コードは、すべてのXSD スキーマを[Uniform Resource Names （URN） &#x200B;](https://www.ietf.org/rfc/rfc2141.txt)として参照します。 コードを開発しており、XSDを参照する必要がある場合、このコマンドは、URNを認識してハイライト表示するように統合開発者環境（IDE）を設定します。 これにより、開発が容易になります。

デフォルトでは、PhpStormのようなIDEはURNを認識するように設定されていないため、次のように赤いテキストで表示されます。

![PhpStormはURN](../../assets/configuration/urn-before.png)を認識するように設定されていません

`bin/magento dev:urn-catalog:generate` コマンドを使用すると、IDE （現在はPhpStormとVisual Studio Codeのみ）で、次のようなURNを認識して強調表示できます。

![IDEでURNを認識できるようにする](../../assets/configuration/urn-after.png)

具体的には、このコマンドは次のPhpStorm設定を作成します。

![PhpStorm設定の例](../../assets/configuration/urn-settings.png)

## IDEの設定

現在、サポートされているのはPhpStormとVisual Studio Codeのみです。

コマンドの構文：

```shell
bin/magento dev:urn-catalog:generate <path>
```

ここで、`<path>`は、プロジェクトのルートに関連するPhpStorm `misc.xml` ファイルへのパスです。 通常、`<path>`は`.idea/misc.xml`です。

>[!INFO]
>
>「スキーマとDTD」を最新の状態に保つには、`*.xsd` ファイルを含むCommerce 2 モジュールを追加、変更、削除するたびに`dev:urn-catalog:generate` コマンドを実行します。
