---
title: サイト、ストア、ストアビューの設定に関するベストプラクティス
description: サイト パフォーマンスを最大化するためのサイト、ストア、ストアビューの設定に関するベストプラクティスについて説明します。
role: Admin
feature: Best Practices
exl-id: 3ea0c6c5-15a9-4e77-b4d0-ce15721c7167
source-git-commit: 4266dbeca837bc62e5a76b2ef22b065a3452e088
workflow-type: tm+mt
source-wordcount: '254'
ht-degree: 0%

---

# サイト、ストア、ストアビューの設定に関するベストプラクティス

Adobe Commerce on cloud infrastructureの場合、ベストプラクティスは、実稼動環境（およびリソースの制約を受けるPro アーキテクチャ上のステージング）に特に適用され、統合環境や開発環境よりも多くのリソースが必要になります。

## 影響を受ける製品とバージョン

[&#x200B; サポートされているすべてのバージョン &#x200B;](../../../release/versions.md) /:

- Adobe Commerce on cloud infrastructure
- Adobe Commerce オンプレミス

## パフォーマンスを向上させる戦略

プロジェクトで多数のサイト、ストア、またはストアビューが必要な場合は、次の戦略を使用してパフォーマンスを向上させることができます。

- ロジックをカテゴリーに移行して、カタログを再構築する
- 外部価格と価格管理システム（PMS）を使用して、カタログデータからプライスリストを分離します。
- Elasticsearchなどの代替のnoSQL データストレージを使用する

## 潜在的なパフォーマンスへの影響

web サイトと実店舗は、カタログデータを増やすための乗数です。そのため、多くのweb サイトと実店舗を運営すると、次のようなサイトパフォーマンスに悪影響を及ぼす可能性があります。

- インデックス テーブルが大きいほど、インデックス作成の操作[価格指数]を完了するのに必要な時間が長くなります。
- アプリケーション設定の取得時間が増加すると、キャッシュされていないカタログページのストアフロントの応答時間が低下します。
- Web サイトごとにデータが個別に保存されるため、管理者で保存操作を完了するのに必要な時間が大幅に増加します。


## 追加情報

- [web サイト、実店舗、店舗表示について](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure-store/best-practices)
- [複数のweb サイトや店舗の設定](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure-store/multiple-sites)
