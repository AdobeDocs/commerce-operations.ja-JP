---
title: 本番サイトでの管理者更新のスケジュール
description: パフォーマンスの低下や停止を防ぐために、Adobe Commerceの重要な更新をスケジュールするためのベストプラクティスについて説明します。
role: Admin, User
feature: Best Practices
exl-id: 41c0cb87-3371-48a7-9913-264f3eea8d8d
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: cdfd3bc1-dc23-5cf0-b965-d3c0c55cde67
    internal-label: Best Practices
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
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

[&#x200B; サポートされているすべてのバージョン &#x200B;](../../../release/versions.md) /:

- Adobe Commerce on cloud infrastructure
- Adobe Commerce オンプレミス

## 追加情報

- [キャッシュのベストプラクティス](https://experienceleague.adobe.com/ja/docs/commerce-admin/systems/tools/cache-management#best-practices-for-caching)
- [プライベートコンテンツ：プライベートコンテンツを無効にする](https://developer.adobe.com/commerce/php/development/cache/page/private-content#invalidate-private-content)
- [ハードウェアの推奨事項：キャッシュ](../../../performance/hardware.md#caches)
- [アドバンスド設定：Redisの設定](../../../performance/advanced-setup.md#set-up-redis)
