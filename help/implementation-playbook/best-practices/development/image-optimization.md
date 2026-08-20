---
title: 画像を最適化してレスポンシブなサイトを実現
description: 画像を最適化し、Fastlyの画像最適化を利用して、Adobe Commerceサイトの応答時間を最適化する手順をご紹介します。
role: Developer, Admin
feature: Best Practices
exl-id: ada8b987-97ed-4232-9e1b-7e0a791a0807
source-git-commit: 4266dbeca837bc62e5a76b2ef22b065a3452e088
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 0%

---

# 画像を最適化してレスポンシブなサイトを実現

Adobe Commerce on cloud infrastructureのデプロイメントの場合は、画像をアップロードする前に画像を最適化することで、サイトの応答時間を短縮します。 次に、Fastlyの画像最適化機能を使用して、画像配信の速度を向上させ、画像ソースセットのメンテナンスを簡素化します。

## 影響を受ける製品とバージョン

[&#x200B; サポートされているすべてのバージョン &#x200B;](../../../release/versions.md) /:

Adobe Commerce on cloud infrastructure


## 画像の最適化と圧縮

Commerceのサイトに画像をアップロードする前に、画像を最適化および圧縮して、パフォーマンスと表示画質のバランスを取ります。 これにより、スペースを増やし、ページの読み込み時間を短縮できます。

- PNG形式では、単色の領域が大きい画像に対して、より小さいサイズの画像を提供します。

- JPEG フォーマットでは、他のすべての画像タイプに対して小さいサイズの画像が提供されます。 最も高い圧縮を使用してください（顕著な劣化なし）。 通常は60～80%です。

## Fastlyの画像最適化を有効にして設定する

Adobe Commerce クラウドプロジェクト用のFastly サービスを設定した後、画像の最適化を有効にして設定する手順については、[Fastly画像の最適化](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/cdn/fastly-image-optimization)を参照してください。

## 追加情報

- [Fastlyの設定](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/cdn/setup-fastly/fastly-configuration)
- [画像が最適化されていない場合、パフォーマンスの問題につながる可能性があります](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/file-storage-low-specific-page-loads-are-slow)
