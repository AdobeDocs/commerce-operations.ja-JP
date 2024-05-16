---
title: 画像を最適化してレスポンシブなサイトを実現
description: 画像を最適化する手順を説明し、Fastly の画像最適化を使用してAdobe Commerce サイトでの応答時間を最適化します。
role: Developer, Admin
feature: Best Practices
exl-id: ada8b987-97ed-4232-9e1b-7e0a791a0807
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 0%

---

# 画像を最適化してレスポンシブなサイトを実現

クラウドインフラストラクチャデプロイメントでのAdobe Commerceの場合は、画像をアップロードする前に最適化することで、サイトの応答時間を短縮します。 次に、Fastly 画像の最適化を使用して、画像配信を高速化し、画像ソースセットのメンテナンスを簡素化します。

## 影響を受ける製品とバージョン

[サポートされているすべてのバージョン](../../../release/versions.md) （件中）:

クラウドインフラストラクチャー上のAdobe Commerce


## 画像の最適化と圧縮

Commerce サイトに画像をアップロードする前に、パフォーマンスと表示品質のバランスを取るために画像を最適化および圧縮します。 これにより、スペースを増やし、ページ読み込み時間を短縮できます。

- PNG 形式では、単色の領域が大きい画像に対して、より小さいサイズの画像が配信されます。

- JPEGフォーマットは、他のすべての画像タイプに対して、より小さいサイズの画像を配信します。 最も高い圧縮率を使用します（著しい劣化は発生しません）。 これは通常 60～80% です。

## Fastly での画像の最適化の有効化と設定

Adobe Commerce Cloud プロジェクト用に Fastly サービスを設定したら、以下を参照してください。 [Fastly 画像の最適化](https://devdocs.magento.com/cloud/cdn/fastly-image-optimization.html) を参照して、画像の最適化を有効にして設定します。

## 追加情報

- [Fastly の設定](https://devdocs.magento.com/cloud/cdn/configure-fastly.html)
- [画像の最適化が不十分だと、パフォーマンスの問題が発生する場合があります](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/file-storage-low-specific-page-loads-are-slow.html)
