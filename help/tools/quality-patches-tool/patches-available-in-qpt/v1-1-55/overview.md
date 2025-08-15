---
title: 概要： [!DNL Quality Patches Tool]  （QPT） v1.1.55
description: ここでは、 [!DNL Quality Patches Tool]  （QPT） v1.1.55 で使用可能なパッチによって修正された問題について詳しく説明します。
feature: Tools and External Services
role: Admin, Developer
exl-id: a4895d1b-e8d0-458e-81c8-4b892c116de6
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# 概要：[!DNL Quality Patches Tool] （QPT） v1.1.55

このサブセクションでは、[!DNL Quality Patches Tool] （QPT） v1.1.55 で使用可能なパッチによって修正された問題について詳しく説明します。

QPT v1.1.55 には、次のパッチが含まれています。

1. **ACSD-58383**：同時に実行される 2 つの同一のリクエストで [!DNL REST API] を介して払い戻しを発行すると、重複したクレジットメモが作成される問題を修正しました。
1. **ACSD-58471**：関連するカタログ価格ルールがスケジュールされている際に、動的コンテンツが製品の詳細ページに読み込まれない問題を修正しました。
1. **ACSD-58566**:[!DNL GraphQL] ミューテーションの `created_at` フィールドに対するクエリを実行する際に、`addPurchaseOrderComment` が内部サーバーエラーを返す問題を修正しました。
1. **ACSD-58685**：メール通信が無効になっている場合に開始した販売メールが、メール通信が再度有効になっても送信される問題を修正しました。
1. **ACSD-58735**：制限付きの管理者が、関連する web サイトの [!UICONTROL Admin] の顧客アカウントページで、放棄された買い物かごを表示できない問題を修正しました。
1. **ACSD-58828**：クライアントサイドの検証メッセージと共に、必須フィールドが空のままの場合、サーバーサイドの検証メッセージ *address が必須* が表示される問題を修正しました。 サーバーサイドの検証では、空の必須フィールドに関するメッセージは表示されません。また、クライアントサイドの検証では、「これは必須フィールドです *というエラー通知が処理されます。*
1. **ACSD-60344**：自動承認を含む **[!UICONTROL Purchase Order]** を使用すると、重複注文確認メールが送信される問題を修正しました。
1. **ACSD-61348**：複数の web サイト環境で、ウィッシュリストの項目が [!DNL GraphQL] 経由で表示されるがストアフロントには表示されない問題を修正しました。
1. **ACSD-61534**:`bin/magento config:set` コマンドを使用してデザイン設定を設定できず、ロックされた値をフォーム操作で変更できる問題を修正しました。 [!DNL CLI] または `--lock-env` を使用して `--lock-conf` から設定されたロックされた値は、更新できなくなりました。
1. **ACSD-61785**：ミューテーションと `reward_warning_notification` 呼び出しを使用して [!DNL GraphQL] 属性を更新 [!DNL REST API]、その動作を `reward_update_notification` に合わせることができない問題を修正しました。
1. **ACSD-62591**：テー **[!UICONTROL User Agent Rules]** が設定されている場合に、テーマが正しく切り替わらない問題を修正しました。
1. **ACSD-62793**：書き出されたデータの `datetime` 属性に時間コンポーネントが含まれていない問題を修正しました。 さらに、*[!UICONTROL Fields Enclosure]* が *有効* になっている場合、`additional_attributes` 列内の属性値は二重引用符で囲まれます。
1. **ACSD-62332**：製品リスト [!DNL GraphQL] クエリが 10,000 個の製品の `total_count` に制限されている問題を修正しました。 また、は、[!DNL Live Search] 経由でクエリされ *ときに、検索条件で現在のページがページ* 2 *ではなく* 1[!DNL GraphQL] に設定される問題も修正しました。

左側のメニューを使用して、特定のパッチページに移動します。
