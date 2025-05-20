---
title: 概要： [!DNL Quality Patches Tool]  （QPT） v1.1.64
description: ここでは、 [!DNL Quality Patches Tool]  （QPT） v1.1.64 で使用可能なパッチによって修正された問題について詳しく説明します。
feature: Tools and External Services
role: Admin, Developer
source-git-commit: f6013ec84c1b3c65e2fe2ca062616976326d2fef
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 0%

---

# 概要：[!DNL Quality Patches Tool] （QPT） v1.1.64

このサブセクションでは、[!DNL Quality Patches Tool] （QPT） v1.1.64 で使用可能なパッチによって修正された問題について詳しく説明します。

QPT v1.1.64 には、次のパッチが含まれています。

1. **ACP2E-3838**：実稼動モードの管理パネルで、[!DNL Page Builder] CORS エラーによって変更が保存されない問題を修正しました。
1. **ACP2E-3841**：複数の条件を使用し、**[!UICONTROL Free Shipping]** が有効になっている場合に、複数出荷製品の買い物かご価格ルールが正しく適用されない問題 `subselect` 修正しました。
1. **ACSD-63139**：製品属性に何千ものオプション値が含まれている場合に、製品の書き出しが失敗する問題を修正しました。
1. **ACSD-65100**:**[!UICONTROL Media Gallery Image Optimization]** 設定で **[!UICONTROL Maximum Width]** と **[!UICONTROL Maximum Height]** の値を削除すると、画像の最適化プロセス中にエラーが発生する問題を修正しました。
1. **ACSD-65127**：実稼動モードでJavaScriptの縮小を有効にすると、[!DNL TinyMCE] 6 でブラウザーコンソールでエラーが発生し、機能とユーザーエクスペリエンスに影響を与える問題を修正しました。
1. **ACSD-65787**：テーブルのデータを処理する際に、スキーマの作成中または未定義の配列キー *列* が原因で `SchemaBuilder` クラスがクラッシュする問題を修正しました。
1. **ACSD-65223**:[!DNL B2B] 注書の条件と契約を手動で選択するとエラーが発生する問題を修正しました。
1. **ACSD-65540**:`company_structure` テーブルの更新時に `REGEXP_LIKE` 関数がないと SQL 構文エラーが発生する問題を修正しました。
1. **ACSD-65684**:`company_structure` テーブルに大量のレコード（約 100,000 以上）がある場合に、[!DNL B2B] 1.5.2 に更新した後に `Magento_Company` モジュールをアップグレードするのに非常に時間がかかるパフォーマンスの問題を修正しました。

左側のメニューを使用して、特定のパッチページに移動します。
