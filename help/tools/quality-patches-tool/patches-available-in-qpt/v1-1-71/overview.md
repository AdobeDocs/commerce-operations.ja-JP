---
title: 概要： [!DNL Quality Patches Tool]  （QPT） v1.1.71
description: ここでは、 [!DNL Quality Patches Tool]  （QPT） v1.1.71 で使用可能なパッチによって修正された問題について詳しく説明します。
feature: Tools and External Services
role: Admin, Developer
source-git-commit: db405ed4cc0f600e24b22242db9e5f48f31c2756
workflow-type: tm+mt
source-wordcount: '178'
ht-degree: 0%

---

# 概要：[!DNL Quality Patches Tool] （QPT） v1.1.71

このサブセクションでは、[!DNL Quality Patches Tool] （QPT） v1.1.71 で使用可能なパッチによって修正された問題について詳しく説明します。

QPT v1.1.71 には、次のパッチが含まれています。


* **ACSD-60624**:**[!UICONTROL Upload Image]** の [!UICONTROL Image]、[!UICONTROL Banner]、[!UICONTROL Slider] の各セクションの空のコンテンツに対して、[!DNL Page Builder] は機能しません。
* **ACSD-67089**:`inventory/export-stock-salable-qty` API のページネーションの問題で、`total_count` がページサイズに誤って制限される。
* **ACSD-67093**：日付範囲フィルターを使用して [!DNL GraphQL] から注文を取得すると、誤った結果が返される。
* **ACSD-67459**：説明が 65,536 文字を超える製品はインポートできません。
* **ACSD-67603**：画像を含めることができる製品のサイトマップ生成で、処理時間が長くなる。
* **ACSD-67643**：ネストされたカテゴリが多数ある環境で、スケジュールされた更新中に重複エントリが作成されます。
* **ACSD-67652**：バンドル製品のステータスが、在庫中の子製品や親製品を含む [!DNL GraphQL] 呼び出しで在庫切れとして返される。
* **ACSD-67904**：市区町村名に数字（0 ～ 9）、アンパサンド （&amp;）、ピリオド （.）、または括弧（）が含まれている場合、注文を行うことはできません。

左側のメニューを使用して、特定のパッチページに移動します。
