---
title: 実稼動サイトでの管理者更新のスケジュール設定
description: Adobe Commerceの重要な更新をスケジュールして、パフォーマンスの低下や停止を防ぐためのベストプラクティスを説明します。
role: Admin, User
feature: Best Practices
exl-id: 41c0cb87-3371-48a7-9913-264f3eea8d8d
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 1%

---

# 実稼動サイトで管理者による更新をスケジュールするためのベストプラクティス

Adobe Commerce サイトの重要な更新や操作をピーク外の時間帯にスケジュールして、実稼動サイトのパフォーマンスの低下や停止を防ぎます。

重要なアクションの例：

- 管理者設定の変更（製品属性の更新、製品サブカテゴリの別のカテゴリへの移動など）
- データのインポートまたはエクスポート操作

重要なアクションは、キャッシュの無効化やインデックス再作成操作につながり、サイトの停止を引き起こす可能性のある応答時間が大幅に長くなります。

## 影響を受ける製品とバージョン

[ サポートされているすべてのバージョン ](../../../release/versions.md):

- クラウドインフラストラクチャー上のAdobe Commerce
- Adobe Commerce オンプレミス

## 追加情報

- [ キャッシュのベストプラクティス ](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/cache-management#best-practices-for-caching)
- [ プライベートコンテンツ：プライベートコンテンツを無効にする ](https://developer.adobe.com/commerce/php/development/cache/page/private-content/#invalidate-private-content)
- [ハードウェアの推奨事項：キャッシュ](../../../performance/hardware.md#caches)
- [詳細設定：Redis の設定](../../../performance/advanced-setup.md#set-up-redis)
