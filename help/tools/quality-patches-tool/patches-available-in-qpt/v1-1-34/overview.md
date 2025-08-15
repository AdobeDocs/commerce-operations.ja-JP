---
title: 概要： [!DNL Quality Patches Tool]  （QPT） v1.1.34
description: ここでは、 [!DNL Quality Patches Tool]  （QPT） v1.1.34 で使用可能なパッチによって修正された問題について詳しく説明します。
feature: Tools and External Services
role: Admin
exl-id: d6cc3161-802c-4a1a-95b1-1eb85715643b
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 0%

---

# 概要：[!DNL Quality Patches Tool] （QPT） v1.1.34

このサブセクションでは、[!DNL Quality Patches Tool] （QPT） v1.1.34 で使用可能なパッチによって修正された問題について詳しく説明します。

QPT v1.1.34 には、次のパッチが含まれています。

1. **ACSD-52277**：管理者で新しい注文を作成する際に、ストア表示を選択した後、管理者ユーザーが適切にリダイレクトされない問題を修正しました。
1. **ACSD-50813**：管理者が、[!UICONTROL Add Products by SKU] 機能を備えた SKU にスラッシュを含むバンドル製品を管理注文に追加できない問題を修正しました。
1. **ACSD-51630**：大量のシステムメッセージが原因で管理ページのダウンロードが遅くなる問題を修正しました。
1. **ACSD-51853**:[!DNL Page Builder] を使用したときに、コピーしたテキストスタイルが適用されない問題を修正しました。
1. **ACSD-52160**：ルール条件 *これらの条件のすべてを/すべてが true で、買い物かごに商品が見つかった場合/見つからなかった場合* に基づいて、買い物かごの価格ルールに対する製品検証結果が適切に評価されなかった問題を修正しました。
1. **ACSD-51636**：必要な役割と権限をすべて持っているにもかかわらず、管理者が顧客アカウントセクションから新しいユーザーを追加できない問題を修正しました。
1. **ACSD-51739**:`structure_id` GraphQL リクエストで `CompanyTeam` がリクエストされた場合にエラーが返される問題を修正しました。
1. **ACSD-51857**:cron レポートのパフォーマンスが遅いと、大きな `aggregate_sales_report_bestsellers_data` および `sales_order` のデータベーステーブル `sales_order_item` 影響を与える問題を修正しました。
1. **ACSD-48448**：注文のキャンセル中に競合状態の問題が発生し、*inventory_reservation* テーブルのエントリが重複する問題を修正しました。
1. **ACSD-52689**:REST API を使用して画像を [!DNL Amazon S3] ストレージにアップロードできない問題を修正しました。

左側のメニューを使用して、特定のパッチページに移動します。
