---
title: 静的ビューファイルのデプロイメント戦略
description: Commerce アプリケーションのデプロイメント戦略について説明します。
feature: Configuration, Deploy, Extensions
exl-id: 12ebbd36-f813-494f-9515-54ce697ca2e4
source-git-commit: 403a5937561d82b02fd126c95af3f70b0ded0747
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---

# 静的ビューファイルのデプロイメント戦略

静的ビューファイルをデプロイする場合、3 つの方法から 1 つを選択できます。 それぞれに、様々なユースケースに最適なデプロイメント結果が得られます。

- [標準](#standard-strategy)：通常のデプロイメントプロセス。
- [クイック](#quick-strategy) （_default_）：複数のロケールのファイルがデプロイされる場合に、デプロイメントに要する時間を最小限に抑えます。
- [コンパクト](#compact-strategy)：公開済みのビューファイルに必要な領域を最小限に抑えます。

次の節では、実装の詳細と各戦略の機能について説明します。

## 標準戦略

標準戦略を使用すると、すべてのパッケージのすべての静的ビューファイルがデプロイされます。つまり、によって処理されます [`\Magento\Framework\App\View\Asset\Publisher`](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/View/Asset/Publisher.php).

詳しくは、を参照してください [静的表示ファイルのデプロイ](../cli/static-view-file-deployment.md).

## 迅速な戦略

クイック戦略は、次のアクションを実行します。

1. テーマごとに任意のロケールが 1 つ選択され、標準戦略と同様に、このロケールのすべてのファイルがデプロイされます。
1. テーマのその他すべてのロケールに対して：

   1. デプロイされたロケールを上書きするファイルが定義され、デプロイされます。
   1. その他のファイルはすべて、すべてのロケールで類似していると見なされ、デプロイされたロケールからコピーされます。

>[!INFO]
>
>作成者： _similar_&#x200B;つまり、ロケール、テーマまたはエリアに依存しないファイルを指します。 これらのファイルには、CSS、画像、フォントが含まれる場合があります。

このアプローチにより、多くのファイルが複製されますが、複数のロケールで必要なデプロイメント時間が最小限に抑えられます。

## コンパクト戦略

コンパクト化の方法では、類似ファイルを次の場所に保存することでファイルの重複を回避します。 `base` サブディレクトリ。

最も最適化された結果を得るために、類似性を保つための 3 つの範囲（領域、テーマ、ロケール）が割り当てられます。 この `base` これらのスコープのすべての組み合わせに対してサブディレクトリが作成されます。

ファイルは、次のパターンに従ってこれらのサブディレクトリにデプロイされます。

| パターン | 説明 |
| ------- | ----------- |
| `<area>/<theme>/<locale>` | 特定の領域、テーマおよびロケールに固有のファイル |
| `<area>/<theme>/default` | 特定の領域の特定のテーマのすべてのロケールに類似したファイル。 |
| `<area>/Magento/base/<locale>` | 特定の領域とロケールに固有のファイルですが、すべてのテーマで類似しています。 |
| `<area>/Magento/base/default` | 特定の領域に固有で、すべてのテーマとロケールで類似したファイル。 |
| `base/Magento/base/<locale>` | ファイルは、すべての領域とテーマで似ていますが、特定のロケールに固有です。 |
| `base/Magento/base/default` | すべての領域、テーマ、ロケールで同様です。 |

### デプロイされたファイルのマッピング

コンパクト戦略で使用されるデプロイメントへのアプローチとは、ファイルが基本テーマおよびロケールから継承されることを意味します。 これらの継承リレーションは、領域、テーマ、およびロケールの組み合わせごとにマップ ファイルに格納されます。 PHP と JS には別個のマップファイルがあります。

- `map.php`
- `requirejs-map.js`

この `map.php` ファイルの利用者 [`Magento\Framework\View\Asset\Repository`](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/View/Asset/Repository.php) 正しい URL を作成します。

この `requirejs-map.js` によって使用されます `baseUrlResolver` requireJS のプラグイン。

例 `map.php`:

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

例 `requirejs-map.js`:

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

静的ビューファイルへの URL を作成するには、を使用します [`\Magento\Framework\View\Asset\Repository::createAsset()`](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/View/Asset/Repository.php#L211-L244).

静的ファイルが見つからず、ページのレンダリング中に表示されない問題を回避するために、URL 連結を使用しないでください。
