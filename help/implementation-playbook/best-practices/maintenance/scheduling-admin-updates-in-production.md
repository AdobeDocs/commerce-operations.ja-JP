---
title: 実稼動サイトで管理者の更新をスケジュールする
description: パフォーマンスの低下や停止を防ぐために、重要な更新をAdobe Commerceにスケジュールするためのベストプラクティスについて説明します。
role: Admin, User
feature: Best Practices
exl-id: 41c0cb87-3371-48a7-9913-264f3eea8d8d
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '148'
ht-degree: 0%

---

# 実稼動サイトで管理アップデートをスケジュールする際のベストプラクティス

ピーク外の時間帯にAdobe Commerceサイトで重要な更新や運用をスケジュールし、実稼動サイトでのパフォーマンスの低下や停止を防ぎます。

重要なアクションの例：

- 管理者の設定変更（製品属性の更新、製品サブカテゴリの別のカテゴリへの移動など）
- データのインポートまたはエクスポート操作

重要なアクションにより、キャッシュの無効化とインデックス再作成操作がおこなわれ、応答時間が大幅に長くなり、サイトの停止を引き起こす可能性があります。

## 影響を受ける製品およびバージョン

[サポートされているすべてのバージョン](../../../release/versions.md) /:

- Adobe Commerce an cloud infrastructure
- Adobe Commerceオンプレミス

## 追加情報

- [キャッシュのベストプラクティス](https://docs.magento.com/user-guide/system/cache-management.html#best-practices-for-caching)
- [プライベートコンテンツ：非公開コンテンツを無効にする](https://developer.adobe.com/commerce/php/development/cache/page/private-content/#invalidate-private-content)
- [ハードウェアの推奨事項：キャッシュ](../../../performance/hardware.md#caches)
- [詳細設定：Redis の設定](../../../performance/advanced-setup.md#set-up-redis)
