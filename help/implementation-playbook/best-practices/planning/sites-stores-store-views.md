---
title: サイト、ストア、ストアの表示を設定する際のベストプラクティス
description: サイトのパフォーマンスを最大化するための、サイト、ストア、およびストア表示の設定に関するベストプラクティスについて説明します。
role: Admin
feature: Best Practices
feature-set: Commerce
source-git-commit: 510f2d4cdaec1034cb04a01fab0948c4261c6d10
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 0%

---


# サイト、ストア、ストア表示の設定に関するベストプラクティス

サイトのパフォーマンスを最高にするには、クラウドインフラストラクチャプロジェクト上のAdobe Commerceに対して、最大 50 のサイト、50 のストア、50 のストア表示を設定します。

>[!NOTE]
>
>クラウドインフラストラクチャ上のAdobe Commerceの場合、ベストプラクティスは、特に実稼動環境（場合によってはリソース制約の対象となる Pro アーキテクチャ上のステージング）に適用され、統合環境および開発環境よりも多くのリソースを持ちます。 統合（Pro および Starter）環境とステージング環境 (Starter) の場合、ストア表示数を 5 または 10 未満（技術的な確認が必要）に減らします。

## 影響を受ける製品およびバージョン

[サポートされているすべてのバージョン](../../../release/versions.md) /:

- Adobe Commerce an cloud infrastructure
- Adobe Commerceオンプレミス

## パフォーマンス向上のための戦略

プロジェクトで多数のサイト、ストア、またはストア表示が必要な場合は、次の戦略を使用してパフォーマンスを向上させることができます。

- 論理をカテゴリに移行してカタログを再構築
- 外部価格と PMS(Price Management System) を使用して、価格表をカタログデータから分離します。
- 代替の noSQL データストレージ (Elasticsearchなど ) を使用

## パフォーマンスへの潜在的な影響

Web サイトや店舗はカタログデータの乗数なので、多くの Web サイトや店舗を持つと、次のような方法でサイトのパフォーマンスに悪影響を与える可能性があります。

- インデックステーブルが大きいと、インデックス作成操作の完了に要する時間が長くなります [価格指数].
- アプリケーション設定の取得に要する時間が長くなると、キャッシュされていないカタログページのストアフロント応答時間が短縮されます。
- データは Web サイトごとに個別に保存されるので、管理で保存操作を完了するのに必要な時間が大幅に増加しました。


## 追加情報

- [Web サイト、ストア、ストア表示について](https://devdocs.magento.com/cloud/configure/configure-best-practices.html#sites)
- [複数の Web サイトまたはストアを設定する](https://devdocs.magento.com/cloud/project/project-multi-sites.html)

