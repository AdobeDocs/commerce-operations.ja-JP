---
title: Varnish ESI ブロックの設定
description: Varnish Edge Side Includes （ESI）と、Adobe Commerceのweb ページを埋め込む方法について説明します。 ESI ブロックの実装と最適化について説明します。
badge: label="Konstantin Gによる。" type="Informative" url="https://github.com/goivvy" tooltip="コンスタンティン・G。"
feature: Configuration, Cache
exl-id: 7dccafa5-df79-4690-be5c-ff774c66bb2a
source-git-commit: 605b2e59d200bc8eeab43e91006a3f95e6a6c138
workflow-type: tm+mt
source-wordcount: '140'
ht-degree: 0%

---

# Varnish ESI ブロックの設定 {#varnish-esi-block}

Edge Side Includes （ESI）は、他のweb ページにweb ページを含めるために使用できる特別なディレクティブです。

例：

```html
<div>
  <esi:include src="http://domain.com/index.php/page_cache/block/esi/blocks"/>
</div>
```

Varnishは`http://domain.com/index.php/page_cache/block/esi/blocks`からコンテンツを取得し、`<esi>` タグをそれに置き換えます。

## CommerceとVarnish ESI

次の条件が満たされると、Commerce フレームワークによってESI タグが作成されます。

- キャッシュ アプリケーションは`Varnish Cache`に設定されています
- XML レイアウト `block`要素が`ttl`属性とともに追加されました

### 例

`cms_index_index.xml`:

```xml
  <referenceContainer name="content">
      <block class="Magento\Framework\View\Element\Template" template="Magento_Paypal::esi.phtml" ttl="30"/>
   </referenceContainer>
```

上記の例では、`block`要素が`esi.phtml` テンプレートのコンテンツをホームページに追加し、Varnishが30秒ごとに自動的に更新します。

## 制限

現在、VarnishはHTTPS経由のESIをサポートしていないため、HTTPに自動的に切り替わります。

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
