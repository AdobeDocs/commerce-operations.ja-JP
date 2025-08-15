---
title: 画像を最適化してレスポンシブなサイトを実現
description: 画像を最適化する手順を説明し、Fastly の画像最適化を使用してAdobe Commerce サイトでの応答時間を最適化します。
role: Developer, Admin
feature: Best Practices
exl-id: ada8b987-97ed-4232-9e1b-7e0a791a0807
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 1%

---

# 画像を最適化してレスポンシブなサイトを実現

クラウドインフラストラクチャデプロイメントでのAdobe Commerceの場合は、画像をアップロードする前に最適化することで、サイトの応答時間を短縮します。 次に、Fastly 画像の最適化を使用して、画像配信を高速化し、画像ソースセットのメンテナンスを簡素化します。

## 影響を受ける製品とバージョン

[ サポートされているすべてのバージョン ](../../../release/versions.md):

クラウドインフラストラクチャー上のAdobe Commerce


## 画像の最適化と圧縮

Commerce サイトに画像をアップロードする前に、パフォーマンスと表示品質のバランスを取るために画像を最適化および圧縮します。 これにより、スペースを増やし、ページ読み込み時間を短縮できます。

- PNG 形式では、単色の領域が大きい画像に対して、より小さいサイズの画像が配信されます。

- JPEG形式では、他のすべての種類の画像に比べて、サイズの小さい画像が配信されます。 最も高い圧縮率を使用します（著しい劣化は発生しません）。 これは通常 60～80% です。

## Fastly での画像の最適化の有効化と設定

Adobe Commerce Cloud プロジェクトに Fastly サービスを設定したら、[Fastly 画像の最適化 ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly-image-optimization) を参照して、画像の最適化を有効にして設定する手順を確認してください。

## 追加情報

- [Fastly のセットアップ ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration)
- [ 画像の最適化が不十分だと、パフォーマンスの問題を引き起こす可能性があります ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/file-storage-low-specific-page-loads-are-slow.html)
