---
title: サイト、ストア、ストア表示を設定するためのベストプラクティス
description: サイト、ストア、ストア表示を設定してサイトのパフォーマンスを最大化するためのベストプラクティスについて説明します。
role: Admin
feature: Best Practices
exl-id: 3ea0c6c5-15a9-4e77-b4d0-ce15721c7167
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 0%

---

# サイト、ストア、ストア表示を設定するためのベストプラクティス

クラウドインフラストラクチャー上のAdobe Commerceの場合、ベストプラクティスは特に、統合環境や開発環境よりも多くのリソースを持つ実稼動環境（場合によっては Pro アーキテクチャ上のステージング）に適用されます。

## 影響を受ける製品とバージョン

[ サポートされているすべてのバージョン ](../../../release/versions.md):

- クラウドインフラストラクチャー上のAdobe Commerce
- Adobe Commerce オンプレミス

## パフォーマンスを向上させるための戦略

プロジェクトで多数のサイト、ストア、またはストアビューが必要な場合は、次の方法を使用してパフォーマンスを向上させることができます。

- ロジックをカテゴリに移動してカタログを再構築
- 外部価格と価格管理システム（PMS）を使用して、カタログ・データから価格表を分離します。
- Elasticsearchなどの別の noSQL データストレージを使用

## パフォーマンスに与える可能性のある影響

Web サイトやストアはカタログデータの乗数なので、多くの Web サイトやストアを持つと、次の点でサイトのパフォーマンスに悪影響を与える可能性があります。

- インデックス・テーブルが大きくなると、インデックス作成操作の完了に要する時間が長くなります [ 価格インデックス ]。
- アプリケーション設定の取得時間が長くなると、キャッシュされていないカタログページのストアフロントの応答時間が遅くなります。
- データは web サイトごとに個別に保存されるので、管理者が保存操作を完了するのに必要な時間が大幅に増加しました。


## 追加情報

- [Web サイト、ストア、ストア表示について ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure-store/best-practices)
- [ 複数の web サイトまたはストアを設定する ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites)
