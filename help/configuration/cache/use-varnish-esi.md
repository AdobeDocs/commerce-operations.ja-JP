---
title: ワニス ESI ブロック
description: エッジサイドインクルードと、それを使用して web ページを埋め込む方法について説明します。
badge: label="執筆：Konstantin G" type="Informative" url="https://github.com/goivvy" tooltip="コンスタンチン G."
feature: Configuration, Cache
exl-id: 7dccafa5-df79-4690-be5c-ff774c66bb2a
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '129'
ht-degree: 0%

---

# ワニス ESI ブロック

エッジサイドインクルード（ESI）は、web ページを他の web ページに含めるために使用できる特別なディレクティブです。

例：

```html
<div>
  <esi:include src="http://domain.com/index.php/page_cache/block/esi/blocks"/>
</div>
```

ワニスは次の場所からコンテンツを取得します `http://domain.com/index.php/page_cache/block/esi/blocks` を作成して、 `<esi>` これでタグ付けします。

## Commerceとワニス ESI

次の条件を満たすと、Commerce フレームワークによって ESI タグが作成されます。

- キャッシュアプリケーションはに設定されます `Varnish Cache`
- XML レイアウト `block` 要素がで追加される `ttl` 属性

### 例

`cms_index_index.xml`:

```xml
  <referenceContainer name="content">
      <block class="Magento\Framework\View\Element\Template" template="Magento_Paypal::esi.phtml" ttl="30"/>
   </referenceContainer>
```

上記の例では、 `block` 要素が次からコンテンツを追加 `esi.phtml` ホームページおよび Varnish へのテンプレートは、30 秒ごとに自動的に更新されます。

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
