---
title: 概要： [!DNL Quality Patches Tool]  （QPT） v1.1.64
description: このサブセクションでは、 [!DNL Quality Patches Tool]  （QPT） v1.1.64で利用可能なパッチによって修正された問題について詳しく説明します。
feature: Tools and External Services
role: Admin, Developer
exl-id: e86b8557-a14a-40e2-a181-56efa4383a1c
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 0%

---

# 概要：[!DNL Quality Patches Tool] （QPT） v1.1.64

このサブセクションでは、[!DNL Quality Patches Tool] （QPT） v1.1.64で利用可能なパッチによって修正された問題について詳しく説明します。

QPT v1.1.64には、次のパッチが含まれています。

1. **ACP2E-3838**: [!DNL Page Builder]個のCORS エラーにより、実稼動モードで管理パネルに変更を保存できない問題を修正します。
1. **ACP2E-3841**: `subselect`条件が使用され、**[!UICONTROL Free Shipping]**&#x200B;が有効になっている場合に、複数配送の商品のカート価格ルールが正しく適用されない問題を修正しました。
1. **ACSD-63139**：製品属性に数千のオプション値が含まれている場合に製品の書き出しが失敗する問題を修正します。
1. **ACSD-65100**: **[!UICONTROL Media Gallery Image Optimization]**&#x200B;設定の&#x200B;**[!UICONTROL Maximum Width]**&#x200B;と&#x200B;**[!UICONTROL Maximum Height]**&#x200B;の値を削除すると、画像の最適化プロセス中にエラーが発生する問題を修正します。
1. **ACSD-65127**：実稼動モードでJavaScriptの縮小を有効にすると、[!DNL TinyMCE] 6でブラウザーコンソールにエラーが発生し、機能とユーザーエクスペリエンスに影響が及ぶ問題を修正します。
1. **ACSD-65787**: テーブル データの処理中に未定義の配列キー&#x200B;*列*&#x200B;が原因で、スキーマの作成中または更新中に`SchemaBuilder` クラスがクラッシュする問題を修正します。
1. **ACSD-65223**: [!DNL B2B]件の発注に対して手動で選択した条件と契約書がエラーになる問題を修正します。
1. **ACSD-65540**: `company_structure` テーブルの更新時に`REGEXP_LIKE`関数が存在しないためにSQL構文エラーが発生する問題を修正します。
1. **ACSD-65684**: `company_structure` テーブルで多数のレコード（～100,000個以上）を処理する際に、`Magento_Company` モジュールを[!DNL B2B] 1.5.2に更新した後にアップグレードするのに非常に長い時間がかかっていたパフォーマンスの問題を修正しました。

左側のメニューを使用して、特定のパッチページに移動します。
