---
title: 概要： [!DNL Quality Patches Tool]  （QPT） v1.1.54
description: このサブセクションでは、 [!DNL Quality Patches Tool]  （QPT） v1.1.54で利用可能なパッチによって修正された問題について詳しく説明します。
feature: Tools and External Services
role: Admin, Developer
exl-id: 1496d15e-edf9-4be0-8e14-ebb2de6f12fe
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 0%

---

# 概要：[!DNL Quality Patches Tool] （QPT） v1.1.54

このサブセクションでは、[!DNL Quality Patches Tool] （QPT） v1.1.54で利用可能なパッチによって修正された問題について詳しく説明します。

QPT v1.1.54には、次のパッチが含まれています。

1. **ACSD-60267**:FPTを含むシンプルな製品をカートに直接追加する際に固定製品税（FPT）が正しく適用されますが、設定可能な製品オプションを使用してこれらの製品を選択する際に失敗する問題を修正します。
1. **ACSD-61103**：顧客がAPI エンドポイントを介して正常にログインした後、`customer_entity` テーブルの失敗数が0にリセットされない問題を修正します。
1. **ACSD-61134**：買い物客が&#x200B;*[!UICONTROL My billing and shipping address are the same]* チェックボックスの選択を解除して請求先住所を更新すると、チェックアウトワークフローで[!DNL Braintree Vault]支払い方法が自動的に選択解除される問題を修正します。
1. **ACSD-61199**：既存の階層を持つCMS ページを編集する際に、「CMS ページ階層」タブに適切なツリー構造が表示されない問題を修正しました。
1. **ACSD-61200**：販売内の&#x200B;*[!UICONTROL Total Amount]*&#x200B;と&#x200B;*[!UICONTROL Total Amount Actual]*&#x200B;の計算に&#x200B;*[!UICONTROL Discount Tax Compensation Amount]*&#x200B;と&#x200B;*[!UICONTROL Shipping Discount Tax Compensation Amount]*&#x200B;が欠落し、販売注文データに矛盾が生じる問題を修正します。
1. **ACSD-61522**: ゲスト顧客の&#x200B;*[!UICONTROL First Name]*&#x200B;および&#x200B;*[!UICONTROL Last Name]* フィールドに電子メールアドレスを入力し、無効な注文確認メールを送信できる問題を修正しました。
1. **ACSD-61756**: `AdvancedSalesRule` フィルターのパフォーマンスを向上させます。
1. **ACSD-61799**：固定割引を含む複数の買い物かごのルールが見積もりに適用される場合に、合計割引が誤って計算される問題を修正します。
1. **ACSD-61845**: *text/html*&#x200B;のaccept ヘッダーのみでリクエストが送信されたときに発生するエラーを修正します。
1. **ACSD-62056**:MSIがインストールされている場合に、設定可能な製品の画像のアップロードが失敗する問題を修正します。
1. **ACSD-62485**：会社が作成されたときに`async.operations.all` コンシューマーが機能しなくなる問題を修正します。

左側のメニューを使用して、特定のパッチページに移動します。
