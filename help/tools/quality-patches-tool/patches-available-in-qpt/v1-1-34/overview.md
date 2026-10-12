---
title: 概要：[!DNL Quality Patches Tool] （QPT） v1.1.34
description: このサブセクションでは、[!DNL Quality Patches Tool] （QPT） v1.1.34で利用可能なパッチによって修正された問題について詳しく説明します。
feature: Tools and External Services
role: Admin
exl-id: d6cc3161-802c-4a1a-95b1-1eb85715643b
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
subfeature_v2:
  - id: 618ab558-d6ad-5352-99d6-d5702c6fdf80
    internal-label: Tools and External Services
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 0%
---
# 概要：[!DNL Quality Patches Tool] （QPT） v1.1.34

このサブセクションでは、[!DNL Quality Patches Tool] （QPT） v1.1.34で利用可能なパッチによって修正された問題について詳しく説明します。

QPT v1.1.34には、次のパッチが含まれています。

1. **ACSD-52277**：管理者で新しい注文を作成する際に、ストアビューを選択した後に管理者ユーザーが正しくリダイレクトされない問題を修正します。
1. **ACSD-50813**：管理者が[!UICONTROL Add Products by SKU]機能を持つSKUにスラッシュを含むバンドル製品を管理者注文に追加できない問題を修正します。
1. **ACSD-51630**：大量のシステムメッセージによって管理者ページのダウンロードが遅くなる問題を修正します。
1. **ACSD-51853**: [!DNL Page Builder]の使用時にコピーしたテキストスタイルが適用されない問題を修正します。
1. **ACSD-52160**: ルール条件&#x200B;*すべての条件または条件のいずれかがtrue*&#x200B;の場合に商品がカート内で見つかった/見つからなかった場合に、カート価格ルールに対する製品検証結果が適切に評価されない問題を修正します。
1. **ACSD-51636**：管理者が必要な役割と権限をすべて持っているにもかかわらず、顧客アカウントセクションから新しいユーザーを追加できない問題を修正します。
1. **ACSD-51739**: `CompanyTeam` GraphQL リクエストで`structure_id`がリクエストされたときにエラーが返される問題を修正します。
1. **ACSD-51857**: `aggregate_sales_report_bestsellers_data` cron レポートのパフォーマンスが遅く、大きな`sales_order`および`sales_order_item` データベーステーブルに影響する問題を修正します。
1. **ACSD-48448**：注文キャンセル中に競合条件の問題が発生し、*inventory_reservation* テーブルでエントリが重複する問題が発生する問題を修正します。
1. **ACSD-52689**:REST APIを使用して画像を[!DNL Amazon S3] ストレージにアップロードできない問題を修正します。

左側のメニューを使用して、特定のパッチページに移動します。
