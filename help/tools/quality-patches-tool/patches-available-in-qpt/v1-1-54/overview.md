---
title: '概要： [!DNL Quality Patches Tool]  （QPT） v1.1.54'
description: ここでは、 [!DNL Quality Patches Tool]  （QPT） v1.1.54 で使用可能なパッチによって修正された問題について詳しく説明します。
feature: Tools and External Services
role: Admin, Developer
source-git-commit: 4f5ce23584cdb3bc52b8375717ba96c24364423c
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---

# 概要：[!DNL Quality Patches Tool] （QPT） v1.1.54

このサブセクションでは、[!DNL Quality Patches Tool] （QPT） v1.1.54 で使用可能なパッチによって修正された問題について詳しく説明します。

QPT v1.1.54 には、次のパッチが含まれています。

1. **ACSD-60267**：シンプルな製品と FPT を直接買い物かごに追加すると固定製品税（FPT）が正しく適用され、設定可能な製品オプションからこれらの製品を選択すると失敗する問題を修正しました。
1. **ACSD-61103**：お客様が API エンドポイントを介して正常にログインした後、`customer_entity` テーブルの失敗数がゼロにリセットされない問題を修正しました。
1. **ACSD-61134**：買い物客が「[!DNL Braintree Vault]」チェックボックスの選択を解除して請求先住所を更新した際に、チェックアウトワークフローで *[!UICONTROL My billing and shipping address are the same]* 支払い方法が自動的に選択解除される問題を修正しました。
1. **ACSD-61199**：既存の階層を使用してCMS ページを編集する際に、「CMS ページの階層」タブに適切なツリー構造が表示されない問題を修正しました。
1. **ACSD-61200**：売上の *[!UICONTROL Total Amount]* と *[!UICONTROL Total Amount Actual]* の計算で *[!UICONTROL Discount Tax Compensation Amount]* と *[!UICONTROL Shipping Discount Tax Compensation Amount]* が欠落し、受注データに不一致が生じる問題を修正しました。
1. **ACSD-61522**：ゲスト顧客の *[!UICONTROL First Name]* フィールドと *[!UICONTROL Last Name]* フィールドにメールアドレスを入力し、無効な注文確認メールを送信できる問題を修正しました。
1. **ACSD-61756**:`AdvancedSalesRule` フィルターのパフォーマンスが向上します。
1. **ACSD-61799**：固定割引が適用された複数の買い物かごルールが見積もりに適用される際に、合計割引が正しく計算されない問題を修正しました。
1. **ACSD-61845**:*text/html* accept ヘッダーのみを使用してリクエストが送信された場合に発生するエラーを修正します。
1. **ACSD-62056**:MSI がインストールされている場合に、設定可能な製品の画像のアップロードが失敗する問題を修正しました。
1. **ACSD-62485**：会社を作成すると消費者 `async.operations.all` 機能が停止する問題を修正しました。

左側のメニューを使用して、特定のパッチページに移動します。
