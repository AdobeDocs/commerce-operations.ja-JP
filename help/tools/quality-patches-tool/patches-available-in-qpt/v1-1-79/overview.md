---
title: 概要： [!DNL Quality Patches Tool]  （QPT） v1.1.79
description: このサブセクションでは、 [!DNL Quality Patches Tool]  （QPT） v1.1.79で利用可能なパッチによって修正された問題について詳しく説明します。
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
source-git-commit: a8666ceccfe78536a624c67227692c98a521f555
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---

# 概要：[!DNL Quality Patches Tool] （QPT） v1.1.79

このサブセクションでは、[!DNL Quality Patches Tool] （QPT） v1.1.79で利用可能なパッチによって修正された問題について詳しく説明します。

QPT v1.1.79には次のパッチが含まれています。
1. **ACP2E-4402**：無効として作成された製品が、有効にした後に関連する[!UICONTROL Target Rule]件の結果に再度追加されない問題を修正します。
1. **ACP2E-4505**：古いデータを含むカテゴリを重複するブラウザータブから保存し、循環依存関係を作成できる問題を修正します。
1. **ACP2E-4531**: CMS ページのURL キーを変更しても、ページの階層URLが更新されない問題を修正します。
1. **ACP2E-4601**：支払いトランザクション処理が特定の条件で非効率的に動作する可能性がある問題を修正します。
1. **ACP2E-4603**: [!UICONTROL Catalog Permissions]製品の再インデックスを実行すると、既存の権限インデックス行が変更されないままになり、更新されたカテゴリ権限の付与が製品に確実に反映されない問題を修正します。
1. **ACP2E-4706**: [!UICONTROL Admin] スコープで有効になっていない製品が[!UICONTROL Target Rule] インデクサーによってスキップされた問題を修正します。
1. **ACP2E-4720**: カート割引ルールを適用したバンドル商品に対して送料無料が適切に適用または削除されなかった問題を修正します。
1. **ACP2E-4411**: カートページおよび複数通貨販売店のミニカートでバンドル商品に誤った価格が表示される問題を修正します。
1. **ACP2E-4475**: **[!UICONTROL Display Out of Stock Products]** オプションが有効になっている場合に、商品リストページで誤って在庫切れのバンドル商品がフィルタリングされ、価格で並べ替えられる問題を修正します。
1. **ACP2E-4110**：特別価格のバンドル製品がデフォルト以外の通貨でPDPおよびPLPに誤った金額で表示される問題を修正します。
1. **AC-10698**: システムが通貨を個別の注文に関連付けるのではなく、すべての注文レベルで送信した問題を修正します。 トランザクションの価格と合計が注文ごとに[!DNL Google Tag]に送信されるようになり、e コマースデータの追跡精度が向上しました。
1. **AC-10737**: `bin/magento setup:db:status` コマンドがJSON データタイプを認識しない問題を修正します。

左側のメニューを使用して、特定のパッチページに移動します。
