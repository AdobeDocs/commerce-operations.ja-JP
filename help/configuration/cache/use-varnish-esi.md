---
title: Vanish ESI ブロック
description: Edge Side のインクルードと、それらを使用して Web ページを埋め込む方法について説明します。
badge: label="寄稿：Konstantin G." type="Informative" url="https://github.com/goivvy" tooltip="コンスタンティン G."
feature: Configuration, Cache
exl-id: 7dccafa5-df79-4690-be5c-ff774c66bb2a
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 0%

---

# Vanish ESI ブロック

Edge Side Includes(ESI) は、他の Web ページに Web ページを含めるために使用できる特別なディレクティブです。

例：

```html
<div>
  <esi:include src="http://domain.com/index.php/page_cache/block/esi/blocks"/>
</div>
```

ワニスは次の内容を取り出す `http://domain.com/index.php/page_cache/block/esi/blocks` をクリックし、 `<esi>` タグに貼り付けます。

## Commerce および Vanish ESI

次の条件を満たすと、Commerce フレームワークは ESI タグを作成します。

- キャッシュアプリケーションはに設定されています。 `Varnish Cache`
- XML レイアウト `block` 要素が `ttl` 属性

### 例

`cms_index_index.xml`:

```xml
  <referenceContainer name="content">
      <block class="Magento\Framework\View\Element\Template" template="Magento_Paypal::esi.phtml" ttl="30"/>
   </referenceContainer>
```

上記の例では、 `block` 要素は、 `esi.phtml` テンプレートをホームページに追加すると、30 秒ごとに自動的に更新されます。

## 制限事項

現在、Vanish は HTTPS 経由で ESI をサポートしていないので、自動的に HTTP に切り替わります。

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
