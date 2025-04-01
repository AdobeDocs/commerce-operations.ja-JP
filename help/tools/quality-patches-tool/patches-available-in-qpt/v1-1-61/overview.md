---
title: 概要： [!DNL Quality Patches Tool]  （QPT） v1.1.61
description: ここでは、 [!DNL Quality Patches Tool]  （QPT） v1.1.61 で使用可能なパッチによって修正された問題について詳しく説明します。
feature: Tools and External Services
role: Admin, Developer
source-git-commit: 0800285df83eb3e3ffcfb003bf984248b750db32
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 0%

---

# 概要：[!DNL Quality Patches Tool] （QPT） v1.1.61

このサブセクションでは、[!DNL Quality Patches Tool] （QPT） v1.1.61 で使用可能なパッチによって修正された問題について詳しく説明します。

QPT v1.1.61 には、次のパッチが含まれています。

1. **ACP2E-3689**：カテゴリツリーがより深いレベルに表示され、アンカー/アンカー以外の関係が反映される複数の問題を修正しました。
1. **ACP2E-3705**:`MAGE_INDEXER_THREADS_COUNT` が設定されている場合に、`indexer_update_all_views` cron 実行が失敗する問題を修正しました。
1. **ACSD-63883**:[!DNL GraphQL] 応答で [!UICONTROL Requisition List] が誤った `items_count` を返す問題を修正しました。
1. **ACSD-63974**：項目が多すぎると [!UICONTROL Requisition List] ページの読み込みに時間がかかりすぎる問題を修正しました。ストアフロントの [!UICONTROL Requisition List] グリッドにページネーション機能を追加すると、すべてのレコードを一度に表示するのではなく、1 ページあたりのレコード数に制限されているレコードの部分のみを表示します。
1. **ACSD-64178**：何千もの製品属性がある場合に、[!UICONTROL Attribute Set] 編集ページの読み込みに時間がかかる問題を修正しました。
1. **ACSD-64209**:Cron スケジューラーがステータス **[!UICONTROL ordered]** の引用符を除外せずに交渉可能なすべての引用符を取得し、メールまたはメールがトリガーされる問題を修正しました。
1. **ACSD-64431**:`placeOrder` クエストにクーポンコード情報が含まれているクーポン変異は、内部エラーをスローしなくなりましたが、代わりに注文が正常に行われたことを示しています。
1. **ACSD-64467**：カテゴリの説明をストア表示レベルで保存した後、WYSIWYG エディターが空のように表示される問題を修正しました。
1. **ACSD-64546**：汎用のエラーメッセージが UI で発生し、UPS 出荷ラベルの作成中に *配列から文字列への変換* 例外がログに保存される問題を修正しました。実際のエラーが UI に表示され、正しいエラーメッセージがログに保存されるようにします。
1. **ACSD-64684**：数値 *1,000）のコンマ（千区切り記号）により* 999 *を超える値のギフトカードを編集および保存する際に検証エラーが発生する問題を修正しました*

左側のメニューを使用して、特定のパッチページに移動します。
