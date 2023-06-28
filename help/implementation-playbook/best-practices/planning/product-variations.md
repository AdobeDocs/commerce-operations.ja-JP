---
title: 製品バリエーション設定のベストプラクティス
description: 設定する製品のバリエーション数を制限して、Adobe Commerceのパフォーマンスを最適化する方法を説明します。
role: Admin
feature: Best Practices, Catalogs
exl-id: a19dd8b4-23b8-498f-be51-a0adfcd12a11
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 0%

---

# 製品バリエーションの設定に関するベストプラクティス

最高のパフォーマンスを得るには、1 つの製品につき最大 50 個のバリエーションを設定します。

## 影響を受ける製品およびバージョン

[サポートされているすべてのバージョン](../../../release/versions.md) /:

- Adobe Commerce an cloud infrastructure
- Adobe Commerceオンプレミス

## 製品バリエーション数の削減

サイトのパフォーマンスを最高にするには、次の戦略を使用して製品のバリエーション数を減らします。

- 異なる製品間でバリエーションの数を配布して、カタログを再構築します。
- 在庫にない設定可能な属性オプションを削除します。
- カスタムオプション、カテゴリ、関連製品、グループ化製品、バンドル製品などの代替機能を使用してバリエーションを管理します。

## パフォーマンスへの影響の可能性

推奨される製品バリエーション数を超えると、次の方法でサイトのパフォーマンスに影響を与える可能性があります。

- 複雑な製品を含む製品の詳細ページとカテゴリページのリクエストとレンダリングに要する時間が長い。
- 管理で保存操作を完了するまでの応答時間が増加しました。
- 製品編集フォームのレンダリング時間が長くなりました。
- チェックアウトが遅い。

## 追加情報

- [設定可能な製品の作成](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/types/product-create-configurable.html)
- [製品の作成](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/product-create.html)

- トレーニング —[Adobe Commerceを使用したカタログと製品の管理](https://learning.adobe.com/catalog/adobe_commerce/cours000000000098643.html)
