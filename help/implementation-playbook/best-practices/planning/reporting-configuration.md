---
title: レポート設定のベストプラクティス
description: 使用していない場合は、レポートモジュールを削除してサイトのパフォーマンスを最適化します。
role: Admin
feature: Best Practices, Configuration
exl-id: 8c991b8a-affb-4a9e-9383-671f595ff89e
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '121'
ht-degree: 0%

---

# レポート設定のベストプラクティス

ビジネスでレポート機能や動的な顧客セグメント機能が不要な場合は、を無効にします [レポート機能](https://docs.magento.com/user-guide/configuration/general/reports.html) ストアパフォーマンスを向上させる。

## 影響を受ける製品とバージョン

[サポートされているすべてのバージョン](../../../release/versions.md) （件中）:

- クラウドインフラストラクチャー上のAdobe Commerce
- Adobe Commerce オンプレミス

## レポートを無効にする

レポートまたは動的顧客セグメントを使用しない場合は、レポート機能を無効にします。

1. 管理者で、に移動します。 **ストア** > **設定** > **設定** > **一般** > **報告書**.
1. 次の下 **一般オプション**、設定 **レポートを有効にする** 対象： *不可*.
1. 実行によるキャッシュのフラッシュ `php bin/magento cache:flush` または、の管理画面で確認できます。 **システム** > **ツール** > **キャッシュ管理**.

## 追加情報

- [Adobe Commerceでのレポートの生成](https://docs.magento.com/user-guide/reports.html)
- [顧客の動的セグメント](https://docs.magento.com/user-guide/marketing/customer-segments.html)
