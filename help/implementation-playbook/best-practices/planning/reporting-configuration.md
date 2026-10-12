---
title: レポート設定のベストプラクティス
description: 使用していない場合は、レポートモジュールを削除して、サイトパフォーマンスを最適化します。
role: Admin
feature: Best Practices, Configuration
exl-id: 8c991b8a-affb-4a9e-9383-671f595ff89e
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: cdfd3bc1-dc23-5cf0-b965-d3c0c55cde67
    internal-label: Best Practices
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '148'
ht-degree: 1%
---
# レポート設定のベストプラクティス

ビジネスでレポート機能や動的な顧客セグメント機能が必要ない場合は、[&#x200B; レポート機能](https://experienceleague.adobe.com/ja/docs/commerce-admin/config/general/reports)を無効にして、ストアのパフォーマンスを向上させてください。

## 影響を受ける製品とバージョン

[&#x200B; サポートされているすべてのバージョン &#x200B;](../../../release/versions.md) /:

- Adobe Commerce on cloud infrastructure
- Adobe Commerce オンプレミス

## レポートを無効にする

レポートまたは動的な顧客セグメントを使用しない場合は、レポート機能を無効にします。

1. 管理者から、**ストア** > **設定** > **設定** > **一般** > **レポート**&#x200B;に移動します。
1. **一般オプション**&#x200B;で、**レポートの有効化**&#x200B;を&#x200B;*No*&#x200B;に設定します。
1. `php bin/magento cache:flush`を実行するか、**システム** > **ツール** > **キャッシュ管理**&#x200B;の下の管理者でキャッシュをフラッシュします。

## 追加情報

- [Adobe Commerceでのレポートの生成](https://experienceleague.adobe.com/ja/docs/commerce-admin/start/reporting/reports-menu)
- [動的な顧客セグメント](https://experienceleague.adobe.com/ja/docs/commerce-admin/customers/segments/customer-segments)
