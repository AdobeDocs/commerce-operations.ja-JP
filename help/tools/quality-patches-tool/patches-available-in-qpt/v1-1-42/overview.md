---
title: 概要： [!DNL Quality Patches Tool]  （QPT） v1.1.42
description: このサブセクションでは、 [!DNL Quality Patches Tool]  （QPT） v1.1.42で使用可能なパッチによって修正された問題について詳しく説明します。
feature: Tools and External Services
role: Admin, Developer
exl-id: 40db5196-0ba3-49c4-97b7-32f146c67f95
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 0%

---

# 概要：[!DNL Quality Patches Tool] （QPT） v1.1.42

このサブセクションでは、[!DNL Quality Patches Tool] （QPT） v1.1.42で利用可能なパッチによって修正された問題について詳しく説明します。

QPT v1.1.42には、次のパッチが含まれています。

1. **ACSD-53658**: *[!UICONTROL Recently Viewed]*&#x200B;製品データがストアビューで正しく更新されない問題を修正します。
1. **ACSD-54626**: GraphQLを使用して`NUMBER_OF_SKUS`属性を持つ新しい発注ルール （`createPurchaseOrderApprovalRule`）を作成できない問題を修正しました。
1. **ACSD-53845**: `consumer max_messages` = 0の場合のMySQL接続タイムアウトの問題を修正します。
1. **ACSD-54890**: `/tmp` ディスクの空き容量が不足しているため、`aggregate_sales_report_bestsellers_data`がMySQL エラーを引き起こす問題を修正します。
1. **ACSD-55112**: [!DNL Google reCAPTCHA v3]検証なしで&#x200B;*[!UICONTROL Submit review]* ボタンを複数回クリックできる問題を修正します。
1. **ACSD-54264**: エラーメッセージ *要求された属性を更新できない問題を修正します。 お客様が別のストアビューから交渉可能な見積もりを使用してチェックアウトしようとすると、行ID : store_id*&#x200B;が表示されます。
1. **ACSD-54418**：動的に価格が設定されたバンドルの各子製品に固定額の割引が誤って適用される問題を修正します。
1. **ACSD-55238**：空の製品メタディスクリプションを保存する際の問題を修正します。
1. **ACSD-54966**：前回の注文が失敗した場合、顧客ごとに使用制限のあるクーポンコードを再利用できない問題を修正します。
1. **ACSD-54060**：制限付き管理者が、別のスコープに割り当てられた別の製品の子である場合に製品を保存できない問題を修正します。
1. **ACSD-48910**：注文が請求され、発送された後、ゼロ以外の数量を持つ場合でも、複数のソースに割り当てられたバンドル製品が在庫切れになる問題を修正します。
1. **ACSD-55381**: B2B *[!UICONTROL Requisition list]*&#x200B;から`configurable_product_option_uid`および`configurable_product_option_value_uid` フィールドをGraphQL経由でクエリする際に発生する内部サーバーエラーを修正します。
1. **ACSD-55628**：会社登録フォームにファイルをアップロードし、ストアフロントの顧客属性のファイルを置き換える問題を修正しました。

左側のメニューを使用して、特定のパッチページに移動します。
