---
title: レポート設定のベストプラクティス
description: レポートモジュールを使用しない場合は削除して、サイトのパフォーマンスを最適化します。
role: Admin
feature: Best Practices, Configuration
exl-id: 8c991b8a-affb-4a9e-9383-671f595ff89e
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 0%

---

# レポート設定のベストプラクティス

レポート機能や動的な顧客セグメント機能が必要ないビジネスの場合は、 [レポートの機能](https://docs.magento.com/user-guide/configuration/general/reports.html) ストアのパフォーマンスを向上させる。

## 影響を受ける製品およびバージョン

[サポートされているすべてのバージョン](../../../release/versions.md) /:

- Adobe Commerce an cloud infrastructure
- Adobe Commerceオンプレミス

## レポートを無効にする

レポートや動的顧客セグメントを使用しない場合は、レポート機能を無効にします。

1. 管理者から、に移動します。 **ストア** > **設定** > **設定** > **一般** > **レポート**.
1. の下 **一般オプション**，設定 **レポートを有効にする** から *いいえ*.
1. を実行してキャッシュをフラッシュ `php bin/magento cache:flush` または、以下の管理者 **システム** > **ツール** > **キャッシュ管理**.

## 追加情報

- [Adobe Commerceでのレポートの生成](https://docs.magento.com/user-guide/reports.html)
- [顧客の動的セグメント](https://docs.magento.com/user-guide/marketing/customer-segments.html)
