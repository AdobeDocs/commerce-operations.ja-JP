---
title: 概要：[!DNL Quality Patches Tool] （QPT） v1.1.85
description: このサブセクションでは、[!DNL Quality Patches Tool] （QPT） v1.1.85で利用可能なパッチによって修正された問題について詳しく説明します。
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
autotag-review: '2026-11-18T22:14:27.542Z'
TQID: 'https://experienceleague.adobe.com/OmF7Ctss9khE5ONHNnfea0dTaN-1-wGTH-EN-gx5jvo'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
    internal-label: Storefront
  - id: 22bad240-8308-569b-a9d5-578f1ff890ca
    internal-label: Customers
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: df8eaa0e-dd74-553a-8ad5-28129f8e8d3d
    internal-label: Shopping Cart
  - id: a507b1ed-4937-53da-97ae-57d36bd5b9e0
    internal-label: Price Rules
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
  - id: c4f010fa-1478-4300-a88d-706fbc036a7a
    internal-label: APIs and SDKs
  - id: 601e4abe-d9bf-58de-a779-32ed6794dcbe
    internal-label: Data Import/Export
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
  - id: e0ca0e7a-9738-48d1-b98b-615468ab4aaf
    internal-label: REST API
  - id: 618ab558-d6ad-5352-99d6-d5702c6fdf80
    internal-label: Tools and External Services
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
    internal-label: Troubleshooting
source-git-commit: a1cc81ee1a8d0bbcbea322558da75a31e65d66a4
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%
---

# 概要：[!DNL Quality Patches Tool] （QPT） v1.1.85

このサブセクションでは、[!DNL Quality Patches Tool] （QPT） v1.1.85で利用可能なパッチによって修正された問題について詳しく説明します。

QPT v1.1.85には次のパッチが含まれています。

1. **[ACP2E-4929](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-85/acp2e-4929.md)**：製品の比較ページの属性ラベルに、現在のストアビューではなく、別のストアビューからの翻訳が表示される問題を修正しました。
1. **ACP2E-5075**: カテゴリ条件を持つ固定金額カート価格ルールが、ルールがバンドル親製品のみに一致する場合に、動的価格バンドル製品のすべての子に誤って割引が適用される問題を修正します。
1. **ACP2E-5077**：同時`customerCart`件のGraphQL クエリまたは`POST /V1/carts/mine`件のREST リクエストで、アクティブなカートを持たない顧客に対して、重複したアクティブなカートが作成される問題を修正します。
1. **ACP2E-5088**：顧客のセッションの有効期限が切れると、顧客の永続的なショッピングカートがクリアされる問題を修正します。
1. **[ACP2E-3991](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-85/acp2e-3991.md)**: クライアント IP アドレスが正しく決定されない問題を修正します。
1. **ACP2E-5092**: **[!UICONTROL Company Profile]** ページと管理者顧客編集ページで、地域なしで保存された会社のアドレスに後でその国に地域が追加された場合にエラーが表示される問題を修正します。
1. **ACP2E-5124**: **[!UICONTROL Validation Strategy]**&#x200B;が&#x200B;**[!UICONTROL Stop on Error]**&#x200B;に設定されている場合に、検証後に検証結果で&#x200B;**[!UICONTROL Import]** ボタンが引き続き利用できる問題を修正します。
1. **AC-17456**：管理パネルの&#x200B;**[!UICONTROL Design Configuration]** ページで&#x200B;**[!UICONTROL Global]** スコープを編集すると、PHP 8.4および8.5で&#x200B;*HTTP 500* エラーが返される問題を修正しました。
1. **ACP2E-5212**: **[!UICONTROL Quick Order]**&#x200B;が`.csv`拡張子で名前変更されたCSV以外のファイルを受け入れる問題を修正します。
1. **ACP2E-5300**：管理パネル **[!UICONTROL Orders]** グリッドで複数のスペース区切りまたはコンマ区切りの注文番号をキーワード検索すると、一致する注文が返されない問題を修正しました。
1. **ACP2E-5354**:REST APIを使用して顧客を更新すると、企業アカウントに関連付けられた顧客が管理者&#x200B;**[!UICONTROL Customers]** グリッドに複数回表示される問題を修正しました。
1. **ACP2E-5208**：変更がない場合でも、**[!UICONTROL Requisition List]** セクションがすべてのストアフロントページナビゲーションで再読み込みされる問題を修正します。

左側のメニューを使用して、特定のパッチページに移動します。
