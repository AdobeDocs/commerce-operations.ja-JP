---
title: レポート設定のベストプラクティス
description: 使用していない場合は、レポートモジュールを削除してサイトのパフォーマンスを最適化します。
role: Admin
feature: Best Practices, Configuration
exl-id: 8c991b8a-affb-4a9e-9383-671f595ff89e
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '121'
ht-degree: 1%

---

# レポート設定のベストプラクティス

ビジネスでレポート機能や動的な顧客セグメント機能が不要な場合は、[&#x200B; レポート機能 &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce-admin/config/general/reports) を無効にして、ストアのパフォーマンスを向上させます。

## 影響を受ける製品とバージョン

[&#x200B; サポートされているすべてのバージョン &#x200B;](../../../release/versions.md):

- クラウドインフラストラクチャー上のAdobe Commerce
- Adobe Commerce オンプレミス

## レポートを無効にする

レポートまたは動的顧客セグメントを使用しない場合は、レポート機能を無効にします。

1. 管理者から、**ストア**/**設定**/**設定**/**一般**/**レポート** に移動します。
1. **一般オプション** で、**レポートを有効にする** を *いいえ* に設定します。
1. `php bin/magento cache:flush` を実行するか、管理画面の **システム**/**ツール**/**キャッシュ管理** でキャッシュをフラッシュします。

## 追加情報

- [Adobe Commerceでのレポートの生成 &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce-admin/start/reporting/reports-menu)
- [&#x200B; 顧客の動的セグメント &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce-admin/customers/segments/customer-segments)
