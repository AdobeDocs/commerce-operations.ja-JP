---
title: 概要： [!DNL Quality Patches Tool]  （QPT） v1.1.71
description: このサブセクションでは、 [!DNL Quality Patches Tool]  （QPT） v1.1.71で使用可能なパッチによって修正された問題について詳しく説明します。
feature: Tools and External Services
role: Admin, Developer
source-git-commit: 4660942d90435eaeb6960206c29733bed6453b6a
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 0%

---

# 概要：[!DNL Quality Patches Tool] （QPT） v1.1.71

このサブセクションでは、[!DNL Quality Patches Tool] （QPT） v1.1.71で利用可能なパッチによって修正された問題について詳しく説明します。

QPT v1.1.71には、次のパッチが含まれています。


* **ACSD-60624**: [!DNL Page Builder]の画像、バナー、スライダーのセクションで、空のコンテンツのアップロードに失敗しました
* **ACSD-67089**: `inventory/export-stock-salable-qty` APIのページネーションの問題により、`total_count`がページサイズに誤って制限されています。
* **ACSD-67093**：日付範囲フィルターを使用して[!DNL GraphQL]経由で注文を取得すると、誤った結果が返されます。
* **ACSD-67459**：説明が65,536文字を超える製品は読み込めません。
* **ACSD-67603**：画像を含める機能が有効になっている製品のサイトマップ生成時間が長い
* **ACSD-67643**：ネストされたカテゴリの数が多い環境で、スケジュールされた更新中に重複するエントリが作成されます。
* **ACSD-67652**：親商品と子商品の在庫がある場合でも、[!DNL GraphQL]回の通話でバンドル商品のステータスが在庫切れとして返されます。
* **ACSD-67904**：市区町村名に数字（0 ～ 9）、アンパサンド （&amp;）、ピリオド （。）、括弧（）が含まれている場合、注文を行うことはできません。

左側のメニューを使用して、特定のパッチページに移動します。
