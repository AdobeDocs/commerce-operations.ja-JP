---
title: 概要：[!DNL Quality Patches Tool] （QPT） v1.1.31
description: このサブセクションでは、[!DNL Quality Patches Tool] （QPT） v1.1.31で利用可能なパッチによって修正された問題について詳しく説明します。
feature: Tools and External Services
role: Admin
exl-id: d37c7f05-1bf5-495b-9b9e-ac9dd117a3ab
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
source-wordcount: '173'
ht-degree: 0%
---
# 概要：[!DNL Quality Patches Tool] （QPT） v1.1.31

このサブセクションでは、[!DNL Quality Patches Tool] （QPT） v1.1.31で利用可能なパッチによって修正された問題について詳しく説明します。

QPT v1.1.31には、次のパッチが含まれています。

1. **ACSD-50817**：引用テーブルの`store_id`列と`updated_at`列に複合インデックスを追加することで、cron ジョブ `sales_clean_quotes`をより高速に実行するように最適化します。
1. **ACSD-50345**：失敗した支払いを送信した後、[!DNL Google reCAPTCHA v2]がリロードされない問題を修正しました。[!DNL Google reCAPTCHA v3 Invisible]がチェックアウトに取り組んでいないため、注文を行うことができず、[!UICONTROL PlaceOrder] イベントがトリガーされませんでした。
1. **ACSD-49392**：バンドルされた製品の一部払い戻し後、注文状況がクローズに変更される問題を修正します。
1. **ACSD-51036**：同時REST API呼び出し中に競合条件が発生し、[!UICONTROL Items Ordered] テーブルの出荷状況情報が上書きされる問題を修正します。
1. **ACSD-50858**: カード支払いに失敗した後、クーポンが誤って「使用」としてマークされる問題を修正します。

左側のメニューを使用して、特定のパッチページに移動します。
