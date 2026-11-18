---
title: 概要：[!DNL Quality Patches Tool] （QPT） v1.1.85
description: このサブセクションでは、[!DNL Quality Patches Tool] （QPT） v1.1.85で利用可能なパッチによって修正された問題について詳しく説明します。
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
source-git-commit: 59431a80af552bd266da55fb49e489453cc64e71
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 0%
---
# 概要：[!DNL Quality Patches Tool] （QPT） v1.1.85

このサブセクションでは、[!DNL Quality Patches Tool] （QPT） v1.1.85で利用可能なパッチによって修正された問題について詳しく説明します。

QPT v1.1.85には次のパッチが含まれています。

1. **ACP2E-4929**: **[!UICONTROL Compare Products]** ページの属性ラベルに、現在のストアビューではなく、別のストアビューからの翻訳が表示される問題を修正しました。
1. **ACP2E-5075**: カテゴリ条件を持つ固定金額カート価格ルールが、ルールがバンドル親製品のみに一致する場合に、動的価格バンドル製品のすべての子に誤って割引が適用される問題を修正します。
1. **ACP2E-5077**：同時`customerCart`件のGraphQL クエリまたは`POST /V1/carts/mine`件のREST リクエストで、アクティブなカートを持たない顧客に対して、重複したアクティブなカートが作成される問題を修正します。
1. **ACP2E-5088**：顧客のセッションの有効期限が切れると、顧客の永続的なショッピングカートがクリアされる問題を修正します。
1. **ACP2E-3991**: クライアント IP アドレスが正しく決定されない問題を修正します。
1. **ACP2E-5092**: **[!UICONTROL Company Profile]** ページと管理者顧客編集ページで、地域なしで保存された会社のアドレスに後でその国に地域が追加された場合にエラーが表示される問題を修正します。
1. **ACP2E-5124**: **[!UICONTROL Validation Strategy]**&#x200B;が&#x200B;**[!UICONTROL Stop on Error]**&#x200B;に設定されている場合に、検証後に検証結果で&#x200B;**[!UICONTROL Import]** ボタンが引き続き利用できる問題を修正します。
1. **AC-17456**：管理パネルの&#x200B;**[!UICONTROL Design Configuration]** ページで&#x200B;**[!UICONTROL Global]** スコープを編集すると、PHP 8.4および8.5で&#x200B;*HTTP 500* エラーが返される問題を修正しました。
1. **ACP2E-5212**: **[!UICONTROL Quick Order]**&#x200B;が`.csv`拡張子で名前変更されたCSV以外のファイルを受け入れる問題を修正します。
1. **ACP2E-5300**：管理パネル **[!UICONTROL Orders]** グリッドで複数のスペース区切りまたはコンマ区切りの注文番号をキーワード検索すると、一致する注文が返されない問題を修正しました。
1. **ACP2E-5354**:REST APIを使用して顧客を更新すると、企業アカウントに関連付けられた顧客が管理者&#x200B;**[!UICONTROL Customers]** グリッドに複数回表示される問題を修正しました。
1. **ACP2E-5208**：変更がない場合でも、**[!UICONTROL Requisition List]** セクションがすべてのストアフロントページナビゲーションで再読み込みされる問題を修正します。

左側のメニューを使用して、特定のパッチページに移動します。
