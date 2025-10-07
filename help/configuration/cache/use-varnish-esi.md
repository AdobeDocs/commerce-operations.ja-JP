---
title: ワニス ESI ブロック
description: ワニス Edge サイドインクルード（ESI）と、Adobe Commerce用に web ページを埋め込む方法について説明します。 ESI ブロックの実装と最適化について説明します。
badge: label="執筆：Konstantin G" type="Informative" url="https://github.com/goivvy" tooltip="コンスタンチン G."
feature: Configuration, Cache
exl-id: 7dccafa5-df79-4690-be5c-ff774c66bb2a
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '136'
ht-degree: 0%

---

# ワニス ESI ブロック

Edge サイドインクルード （ESI）は、他の web ページに web ページを含めるために使用できる特別なディレクティブです。

例：

```html
<div>
  <esi:include src="http://domain.com/index.php/page_cache/block/esi/blocks"/>
</div>
```

Varnish は `http://domain.com/index.php/page_cache/block/esi/blocks` からコンテンツを取得し、`<esi>` タグを置き換えます。

## Commerceとワニス ESI

次の条件を満たすと、Commerce フレームワークによって ESI タグが作成されます。

- キャッシュアプリケーションは `Varnish Cache` に設定されています
- `block` 属性を持つ XML レイアウト `ttl` 要素が追加される

### 例

`cms_index_index.xml`:

```xml
  <referenceContainer name="content">
      <block class="Magento\Framework\View\Element\Template" template="Magento_Paypal::esi.phtml" ttl="30"/>
   </referenceContainer>
```

上記の例では、`block` 要素が `esi.phtml` テンプレートからホームページにコンテンツを追加し、Varnish が 30 秒ごとに自動的に更新します。

## 制限事項

現在、Varnish は HTTPS 上の ESI をサポートしていないので、自動的に HTTP に切り替わります。

`Magento\PageCache\Observer\ProcessLayoutRenderElement`:

```php
    private function _wrapEsi(
        \Magento\Framework\View\Element\AbstractBlock $block,
        \Magento\Framework\View\Layout $layout
    ) {
    ....
        // Varnish does not support ESI over HTTPS must change to HTTP
        $url = substr($url, 0, 5) === 'https' ? 'http' . substr($url, 5) : $url;
        return sprintf('<esi:include src="%s" />', $url);
    }
```
