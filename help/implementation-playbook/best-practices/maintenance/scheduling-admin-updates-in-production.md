---
title: 本番サイトでの管理者更新のスケジュール
description: パフォーマンスの低下や停止を防ぐために、Adobe Commerceの重要な更新をスケジュールするためのベストプラクティスについて説明します。
role: Admin, User
feature: Best Practices
exl-id: 41c0cb87-3371-48a7-9913-264f3eea8d8d
source-git-commit: b378f6da50e40b1868ae759cc7f3523a7e3ced4b
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 1%

---

# 実稼動サイトで管理者の更新をスケジュールするためのベストプラクティス

オフピーク時間中にAdobe Commerce サイトの重要な更新と操作をスケジュールして、実稼動サイトのパフォーマンスの低下や停止を防ぎます。

重要なアクションの例：

- 管理者設定の変更（例：製品属性の更新、製品サブカテゴリの別のカテゴリへの移動）
- データのインポートまたはエクスポート操作

重要なアクションは、キャッシュの無効化とインデックス再作成の操作につながり、サイトの停止の原因となる応答時間が大幅に増加します。

## 影響を受ける製品とバージョン

[ サポートされているすべてのバージョン ](../../../release/versions.md) /:

- Adobe Commerce on cloud infrastructure
- Adobe Commerce オンプレミス

## 追加情報

- [キャッシュのベストプラクティス](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/cache-management#best-practices-for-caching)
- [プライベートコンテンツ：プライベートコンテンツを無効にする](https://developer.adobe.com/commerce/php/development/cache/page/private-content#invalidate-private-content)
- [ハードウェアの推奨事項：キャッシュ](../../../performance/hardware.md#caches)
- [アドバンスド設定：Redisの設定](../../../performance/advanced-setup.md#set-up-redis)
