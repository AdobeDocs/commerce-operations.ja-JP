---
title: 静的ビューファイルの展開戦略
description: Adobe Commerce アプリケーションの静的ビューファイルのデプロイメント戦略について説明します。 様々なユースケースに最適なデプロイメント方法を見つける。
feature: Configuration, Deploy, Extensions
exl-id: 12ebbd36-f813-494f-9515-54ce697ca2e4
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: bcd8874c-7b93-5596-bdaa-22660e84df14
    internal-label: Deploy
  - id: f08fa0de-a550-4acd-b570-f81cf1d03aaf
    internal-label: Commerce ecosystem
subfeature_v2:
  - id: dad884f1-e840-49a1-970e-2f965bdbc410
    internal-label: Extensions
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
source-wordcount: '497'
ht-degree: 0%
---
# 静的ビューファイルの展開戦略

静的ビューファイルをデプロイする場合は、使用可能な3つの戦略のいずれかを選択できます。 それぞれ、異なるユースケースに対して最適なデプロイメント結果を提供します。

- [Standard](#standard-strategy)：通常のデプロイメントプロセス。
- [&#x200B; クイック &#x200B;](#quick-strategy) （_デフォルト_）：複数のロケールのファイルをデプロイする場合に、デプロイに必要な時間を最小限に抑えます。
- [&#x200B; コンパクト &#x200B;](#compact-strategy)：公開されたビューファイルの容量を最小限に抑えます。

以下の節では、各戦略の実装の詳細と機能について説明します。

## 標準戦略

標準戦略を使用すると、すべてのパッケージのすべての静的ビューファイルがデプロイされます。つまり、[`\Magento\Framework\App\View\Asset\Publisher`](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/View/Asset/Publisher.php)によって処理されます。

詳しくは、[静的ビューファイルのデプロイ &#x200B;](../cli/static-view-file-deployment.md)を参照してください。

## クイック戦略

クイック戦略では、次のアクションを実行します。

1. 各テーマについて、任意のロケールが1つ選択され、このロケールのすべてのファイルが標準の戦略のようにデプロイされます。
1. テーマのその他すべてのロケールの場合：

   1. デプロイされたロケールを上書きするファイルが定義され、デプロイされます。
   1. その他のすべてのファイルは、すべてのロケールで類似していると見なされ、デプロイされたロケールからコピーされます。

>[!INFO]
>
>_similar_&#x200B;では、ロケール、テーマ、または領域に依存しないファイルを意味します。 これらのファイルには、CSS、画像、フォントが含まれます。

多くのファイルが重複しますが、この方法により、複数のロケールに必要なデプロイメント時間が最小限に抑えられます。

## コンパクト戦略

コンパクト化戦略では、`base`個のサブディレクトリに類似したファイルを保存することで、ファイルの重複を回避します。

最適化された結果を得るために、可能な類似性の3つのスコープ（エリア、テーマ、ロケール）が割り当てられます。 これらのスコープのすべての組み合わせに対して、`base` サブディレクトリが作成されます。

ファイルは、次のパターンに従ってこれらのサブディレクトリにデプロイされます。

| パターン | 説明 |
| ------- | ----------- |
| `<area>/<theme>/<locale>` | 特定の領域、テーマ、ロケールに固有のファイル |
| `<area>/<theme>/default` | 特定の領域の特定のテーマのすべてのロケールに類似したファイル。 |
| `<area>/Magento/base/<locale>` | 特定の領域とロケールに特化したファイルですが、すべてのテーマで同様です。 |
| `<area>/Magento/base/default` | 特定の領域に特化したファイルですが、すべてのテーマとロケールで同様です。 |
| `base/Magento/base/<locale>` | すべての領域とテーマに類似していますが、特定のロケールに固有のファイルです。 |
| `base/Magento/base/default` | すべての分野、テーマ、ロケールで同様です。 |

### デプロイ済みファイルのマッピング

コンパクト戦略で使用されるデプロイメントに対するアプローチは、ファイルが基本テーマとロケールから継承されることを意味します。 これらの継承リレーションは、エリア、テーマ、ロケールの組み合わせごとにマップファイルに保存されます。 PHPとJSには個別のマップファイルがあります。

- `map.php`
- `requirejs-map.js`

`map.php` ファイルは、[`Magento\Framework\View\Asset\Repository`](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/View/Asset/Repository.php)が正しいURLを作成するために使用します。

`requirejs-map.js`は、`baseUrlResolver` プラグインでRequireJSに使用されています。

例：`map.php`

```php?start_inline=1
return [
    'Magento_Checkout::cvv.png' => [
        'area' => 'frontend',
        'theme' => 'Magento/luma',
        'locale' => 'en_US',
    ],
    '...' => [
        'area' => '...',
        'theme' => '...',
        'locale' => '...'
    ]
];
```

例：`requirejs-map.js`

```js
require.config({
    "config": {
       "baseUrlInterceptor": {
            "jquery.js": "../../../../base/Magento/base/en_US/"
        }
    }
});
```

## 拡張機能の開発者向けヒント

静的ビューファイルのURLを作成するには、[`\Magento\Framework\View\Asset\Repository::createAsset()`](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/View/Asset/Repository.php#L211-L244)を使用します。

ページのレンダリング中に静的ファイルが見つからず、表示されない問題を回避するために、URLの連結を使用しないでください。
