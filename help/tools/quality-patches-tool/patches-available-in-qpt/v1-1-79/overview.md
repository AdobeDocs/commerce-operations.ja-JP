---
title: 概要：[!DNL Quality Patches Tool] （QPT） v1.1.79
description: このサブセクションでは、[!DNL Quality Patches Tool] （QPT） v1.1.79で利用可能なパッチによって修正された問題について詳しく説明します。
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
subfeature_v2:
  - id: 618ab558-d6ad-5352-99d6-d5702c6fdf80
    internal-label: Tools and External Services
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 5c33cd529bff9208d640cec3c4068f578a9e376c
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%
---
# 概要：[!DNL Quality Patches Tool] （QPT） v1.1.79

このサブセクションでは、[!DNL Quality Patches Tool] （QPT） v1.1.79で利用可能なパッチによって修正された問題について詳しく説明します。

QPT v1.1.79には次のパッチが含まれています。
1. **[ACP2E-4402](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-79/acp2e-4402.md)**：無効として作成された製品が、有効にした後に関連する[!UICONTROL Target Rule]件の結果に再度追加されない問題を修正します。
1. **[ACP2E-4505](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-79/acp2e-4505.md)**：古いデータを含むカテゴリを重複するブラウザータブから保存し、循環依存関係を作成できる問題を修正します。
1. **[ACP2E-4531](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-79/acp2e-4531.md)**: CMS ページのURL キーを変更しても、ページの階層URLが更新されない問題を修正します。
1. **[ACP2E-4601](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-79/acp2e-4601.md)**：支払いトランザクション処理が特定の条件で非効率的に動作する可能性がある問題を修正します。
1. **[ACP2E-4603](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-79/acp2e-4603.md)**: [!UICONTROL Catalog Permissions]製品の再インデックスを実行すると、既存の権限インデックス行が変更されないままになり、更新されたカテゴリ権限の付与が製品に確実に反映されない問題を修正します。
1. **[ACP2E-4706](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-79/acp2e-4706.md)**：管理者スコープで有効になっていない製品が[!UICONTROL Target Rule] インデクサーによってスキップされた問題を修正します。
1. **[ACP2E-4720](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-79/acp2e-4720.md)**: カート割引ルールを適用したバンドル商品に対して送料無料が適切に適用または削除されなかった問題を修正します。
1. **[ACP2E-4475](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-79/acp2e-4475.md)**: [!UICONTROL Display Out of Stock Products] オプションが有効になっている場合に、商品リストページで誤って在庫切れのバンドル商品がフィルタリングされ、価格で並べ替えられる問題を修正します。
1. **[AC-10698](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-79/ac-10698.md)**: システムが通貨を個別の注文に関連付けるのではなく、すべての注文レベルで送信した問題を修正します。 トランザクションの価格と合計が注文ごとに[!DNL Google Tag]に送信されるようになり、e コマースデータの追跡精度が向上しました。
1. **[ACP2E-4411](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-79/acp2e-4411.md)**: カートページおよび複数通貨販売店のミニカートでバンドル商品に誤った価格が表示される問題を修正します。
1. **[ACP2E-4110](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-79/acp2e-4110.md)**: **[!UICONTROL Special Price]**&#x200B;のバンドル製品がデフォルト以外の通貨でPDPおよびPLPに誤った金額を表示する問題を修正します。
1. **[AC-10737](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-79/ac-10737.md)**: `bin/magento setup:db:status` コマンドがJSON データタイプを認識しない問題を修正します。

左側のメニューを使用して、特定のパッチページに移動します。
