---
title: 静的ビューファイルの展開戦略
description: コマースアプリケーションのデプロイメント戦略についてお読みください。
feature: Configuration, Deploy, Extensions
exl-id: 12ebbd36-f813-494f-9515-54ce697ca2e4
source-git-commit: 403a5937561d82b02fd126c95af3f70b0ded0747
workflow-type: tm+mt
source-wordcount: '482'
ht-degree: 0%

---

# 静的ビューファイルの展開戦略

静的ビューファイルを展開する場合、使用可能な 3 つの方法のいずれかを選択できます。 それぞれが、様々な使用例に最適なデプロイメント結果を提供します。

- [標準](#standard-strategy):通常のデプロイメントプロセス。
- [クイック](#quick-strategy) (_デフォルト_):複数のロケールのファイルがデプロイされる場合に、デプロイに必要な時間を最小限に抑えます。
- [コンパクト](#compact-strategy):パブリッシュされたビューファイルで使用される領域を最小限に抑えます。

次の節では、各戦略の実装の詳細と機能について説明します。

## 標準方法

標準方法を使用すると、すべてのパッケージのすべての静的ビューファイルがデプロイされ、が処理します。 [`\Magento\Framework\App\View\Asset\Publisher`](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/View/Asset/Publisher.php).

詳しくは、 [静的ビューファイルのデプロイ](../cli/static-view-file-deployment.md).

## クイック戦略

クイック戦略では、次の操作を実行します。

1. 各テーマに対して、1 つの任意のロケールが選択され、そのロケールのすべてのファイルが、標準の方法と同様にデプロイされます。
1. テーマのその他すべてのロケールの場合：

   1. デプロイされたロケールを上書きするファイルが定義され、デプロイされます。
   1. その他のファイルはすべてのロケールで類似していると見なされ、デプロイされたロケールからコピーされます。

>[!INFO]
>
>作成者 _類似_&#x200B;の場合、ロケール、テーマ、領域に依存しないファイルを意味します。 これらのファイルには、CSS、画像、フォントが含まれる場合があります。

この方法を使用すると、多数のファイルが重複している場合でも、複数のロケールで必要なデプロイメント時間を最小限に抑えることができます。

## コンパクトな方法

コンパクトな方法では、類似のファイルをに保存することで、ファイルの重複を防ぎます。 `base` サブディレクトリ。

最も最適化された結果を得るには、考えられる類似性用の 3 つのスコープが割り当てられます。領域、テーマおよびロケール。 この `base` これらのスコープのすべての組み合わせに対してサブディレクトリが作成されます。

ファイルは、次のパターンに従って、これらのサブディレクトリにデプロイされます。

| パターン | 説明 |
| ------- | ----------- |
| `<area>/<theme>/<locale>` | 特定の領域、テーマおよびロケールに固有のファイル |
| `<area>/<theme>/default` | 特定の領域の特定のテーマのすべてのロケールに類似したファイル。 |
| `<area>/Magento/base/<locale>` | 特定の領域とロケールに固有のファイルですが、すべてのテーマに類似したファイルです。 |
| `<area>/Magento/base/default` | 特定の領域に固有のファイルで、すべてのテーマとロケールに類似したファイル。 |
| `base/Magento/base/<locale>` | すべての領域とテーマに似ていますが、特定のロケールに固有のファイルです。 |
| `base/Magento/base/default` | すべての領域、テーマ、ロケールで同様です。 |

### デプロイ済みファイルのマッピング

コンパクトな方法で使用されるデプロイメントのアプローチは、ファイルが基本のテーマとロケールから継承されることを意味します。 これらの継承関係は、領域、テーマ、ロケールの組み合わせごとにマップファイルに保存されます。 PHP と JS には、別々のマップファイルがあります。

- `map.php`
- `requirejs-map.js`

この `map.php` ファイルは次の場所で使用されています： [`Magento\Framework\View\Asset\Repository`](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/View/Asset/Repository.php) をクリックして正しい URL を作成します。

この `requirejs-map.js` が `baseUrlResolver` RequireJS 用のプラグインです。

の例 `map.php`:

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

の例 `requirejs-map.js`:

```js
require.config({
    "config": {
       "baseUrlInterceptor": {
            "jquery.js": "../../../../base/Magento/base/en_US/"
        }
    }
});
```

## 拡張機能開発者向けのヒント

静的ビューファイルへの URL を作成するには、 [`\Magento\Framework\View\Asset\Repository::createAsset()`](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/View/Asset/Repository.php#L211-L244).

静的ファイルが見つからず、ページのレンダリング中に表示されない問題を回避するために、URL 連結を使用しないでください。
