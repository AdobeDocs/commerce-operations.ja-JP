---
title: プライベートコンテンツブロックのベストプラクティス
description: ストアフロントのパフォーマンスを最適化するために、プライベートコンテンツブロックを設定するためのベストプラクティスを説明します。
role: Developer
feature: Best Practices
exl-id: a6d2f324-f9b9-4b2b-997f-36df02c37465
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: cdfd3bc1-dc23-5cf0-b965-d3c0c55cde67
    internal-label: Best Practices
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 0%
---
# プライベートコンテンツブロックのベストプラクティス

プライベートコンテンツブロックに`_isScopePrivate`変数が含まれている場合、ブロックはキャッシュできません。 プライベートブロックはキャッシュされないため、Adobe Commerceは各カスタマーリクエストに対して同じデータを取得する必要があり、サーバーの負荷が増加します。

プライベートコンテンツに`_isScopePrivate`変数を使用する代わりに、ブロックとテンプレートを作成して、ユーザーに依存しないデータを表示します。 このデータは、Adobe Commerce UI コンポーネントによってユーザー固有のデータに置き換えられ、事前レンダリングのデータをより効率的に処理します。 手順については、_[!DNL Commerce PHP Extensions Guide]_&#x200B;の[&#x200B; プライベートコンテンツ &#x200B;](https://developer.adobe.com/commerce/php/development/cache/page/private-content)を参照してください。

## 影響を受ける製品とバージョン

[&#x200B; サポートされているすべてのバージョン &#x200B;](../../../release/versions.md) /:

- Adobe Commerce on cloud infrastructure
- Adobe Commerce オンプレミス

## 潜在的なパフォーマンスへの影響

`_isScopePrivate`個の変数を含むプライベートコンテンツブロックを持つサイトは、AJAX リクエストをトリガーして、各カスタマーリクエストに対して同じデータを取得します。 これにより、レスポンス時間が増加し、顧客登録、ショッピングカートの更新、注文送信、支払いトランザクションなど、よりビジネスに不可欠なストアフロント業務を処理するために使用できる追加リソースが追加されます。

## 追加情報

- [プライベートコンテンツ](../../../performance/configuration.md#client-side-optimization-settings)
- _[!DNL Commerce PHP Extensions Guide]_&#x200B;の[&#x200B; キャッシュ可能ブロックとプライベートブロック &#x200B;](https://developer.adobe.com/commerce/php/development/cache/page/private-content#cacheable-and-private-blocks)
