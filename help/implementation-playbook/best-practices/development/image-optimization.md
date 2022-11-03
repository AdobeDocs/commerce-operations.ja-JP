---
title: よりレスポンシブなサイトに向けて画像を最適化する
description: 画像を最適化し、Fastly 画像の最適化を使用してAdobe Commerce Sites の応答時間を最適化する手順について説明します。
role: Developer, Admin
feature: Best Practices
feature-set: Commerce
source-git-commit: e156fcafc5792036b37d9b199b870f1888c3f1ff
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 0%

---


# よりレスポンシブなサイトに向けて画像を最適化する

クラウドインフラストラクチャ上のAdobe Commerceのデプロイメントの場合は、画像をアップロードする前に最適化することで、サイトの応答時間を短縮します。 次に、Fastly 画像の最適化を使用して、画像の配信を高速化し、画像ソースセットのメンテナンスを簡単にします。

## 影響を受ける製品およびバージョン

[サポートされているすべてのバージョン](../../../release/versions.md) /:

Adobe Commerce an cloud infrastructure


## 画像の最適化と圧縮

コマースサイトに画像をアップロードする前に、画像を最適化および圧縮して、パフォーマンスと表示品質のバランスをとります。 これにより、スペースを増やし、ページ読み込み時間を短縮できます。

- PNG 形式は、大きな領域がべた塗りの画像に対して、より小さいサイズの画像を配信します。

- JPEG形式を使用すると、他のすべての画像タイプに合わせて小さいサイズの画像を配信できます。 最も高い圧縮を使用します（顕著な劣化は発生しません）。 これは通常 60～80%です。

## Fastly 画像の最適化の有効化と設定

Adobe Commerce Cloudプロジェクトの Fastly サービスを設定した後、 [画像の最適化](https://devdocs.magento.com/cloud/cdn/fastly-image-optimization.html) 画像の最適化を有効にして設定する手順については、を参照してください。

## 追加情報

- [Fastly の設定](https://devdocs.magento.com/cloud/cdn/configure-fastly.html)
- [最適化が不十分な画像は、パフォーマンスの問題を引き起こす可能性があります](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/file-storage-low-specific-page-loads-are-slow.html)
