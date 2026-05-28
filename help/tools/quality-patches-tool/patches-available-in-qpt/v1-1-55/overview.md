---
title: 概要： [!DNL Quality Patches Tool]  （QPT） v1.1.55
description: このサブセクションでは、 [!DNL Quality Patches Tool]  （QPT） v1.1.55で利用可能なパッチによって修正された問題について詳しく説明します。
feature: Tools and External Services
role: Admin, Developer
exl-id: a4895d1b-e8d0-458e-81c8-4b892c116de6
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# 概要：[!DNL Quality Patches Tool] （QPT） v1.1.55

このサブセクションでは、[!DNL Quality Patches Tool] （QPT） v1.1.55で利用可能なパッチによって修正された問題について詳しく説明します。

QPT v1.1.55には、次のパッチが含まれています。

1. **ACSD-58383**：同時に実行される2つの同じ要求で[!DNL REST API]を介して払い戻しを発行すると、重複したクレジットメモが作成される問題を修正します。
1. **ACSD-58471**：関連するカタログ価格ルールがスケジュールされている場合に、動的コンテンツが製品詳細ページに読み込まれない問題を修正します。
1. **ACSD-58566**: `addPurchaseOrderComment`の突然変異で`created_at` フィールドをクエリする際に[!DNL GraphQL]が内部サーバーエラーを返す問題を修正します。
1. **ACSD-58685**：電子メール通信が無効になっている間に開始されたセールスメールが、電子メール通信が再度有効になった後も送信される問題を修正します。
1. **ACSD-58735**：制限付き管理者が、関連するweb サイトの[!UICONTROL Admin]の顧客アカウントページで放棄されたショッピングカートを表示できない問題を修正します。
1. **ACSD-58828**：必要なフィールドがクライアント側の検証メッセージと共に空のままになっている場合に、サーバー側の検証メッセージ *アドレスが必須*&#x200B;と表示される問題を修正します。 サーバー側の検証では、空の必須フィールドのメッセージは表示されず、クライアント側の検証ではエラー通知が処理され、*これは必須フィールドです。*
1. **ACSD-60344**：自動承認付きの&#x200B;**[!UICONTROL Purchase Order]**&#x200B;を使用する際に重複した注文確認メールが送信される問題を修正します。
1. **ACSD-61348**: ウィッシュリスト項目が[!DNL GraphQL]を介して表示されますが、複数のweb サイト環境のストアフロントでは表示されない問題を修正します。
1. **ACSD-61534**: `bin/magento config:set` コマンドを使用してデザイン設定を設定できず、ロックされた値をフォーム操作で変更できる問題を修正しました。 `--lock-env`または`--lock-conf`で[!DNL CLI]から設定されたロックされた値を更新できなくなりました。
1. **ACSD-61785**: [!DNL GraphQL]の突然変異と[!DNL REST API]の呼び出しにより、`reward_warning_notification`属性を更新できない問題を修正し、その動作を`reward_update_notification`に合わせます。
1. **ACSD-62591**: **[!UICONTROL User Agent Rules]**&#x200B;が設定されているときにテーマが正しく切り替わらない問題を修正します。
1. **ACSD-62793**：書き出されたデータの`datetime`属性に時間コンポーネントが含まれていない問題を修正します。 さらに、*[!UICONTROL Fields Enclosure]*&#x200B;が&#x200B;*enabled*&#x200B;の場合、`additional_attributes`列の属性値は二重引用符で囲まれます。
1. **ACSD-62332**：製品リスト [!DNL GraphQL] クエリが10,000個の製品のうち`total_count`個に制限される問題を修正します。 また、[!DNL Live Search]が[!DNL GraphQL]を介してクエリを実行した場合に、検索条件で現在のページを&#x200B;*2*&#x200B;ではなく&#x200B;*1*&#x200B;に設定する問題を修正しました。

左側のメニューを使用して、特定のパッチページに移動します。
