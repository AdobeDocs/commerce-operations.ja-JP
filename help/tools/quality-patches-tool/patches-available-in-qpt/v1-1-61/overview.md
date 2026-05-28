---
title: 概要： [!DNL Quality Patches Tool]  （QPT） v1.1.61
description: このサブセクションでは、 [!DNL Quality Patches Tool]  （QPT） v1.1.61で使用可能なパッチによって修正された問題について詳しく説明します。
feature: Tools and External Services
role: Admin, Developer
exl-id: 065235fb-12e3-448b-bc37-51efdf95393a
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---

# 概要：[!DNL Quality Patches Tool] （QPT） v1.1.61

このサブセクションでは、[!DNL Quality Patches Tool] （QPT） v1.1.61で利用可能なパッチによって修正された問題について詳しく説明します。

QPT v1.1.61には、次のパッチが含まれています。

1. **ACP2E-3689**：より深いレベルでのカテゴリーツリー表示と、アンカー/アンカー以外の関係の反映に関する複数の問題を修正します。
1. **ACP2E-3705**: `MAGE_INDEXER_THREADS_COUNT`が設定されているときに`indexer_update_all_views` cronの実行が失敗する問題を修正します。
1. **ACSD-63883**: [!DNL GraphQL]応答で[!UICONTROL Requisition List]が誤った`items_count`を返す問題を修正します。
1. **ACSD-63974**: ストアフロントの[!UICONTROL Requisition List] グリッドにページネーション機能を追加し、すべてのレコードを一度に読み込むのではなく、ページあたりのレコード数に制限されているレコードの一部のみを表示することで、[!UICONTROL Requisition List] ページの読み込みに時間がかかりすぎる問題を修正します。
1. **ACSD-64178**：製品属性が数千ある場合、[!UICONTROL Attribute Set]編集ページの読み込みが遅くなる問題を修正します。
1. **ACSD-64209**: cron スケジューラーがステータス **[!UICONTROL ordered]**&#x200B;の引用符を除外せずに、すべての交渉可能な引用符を取得し、電子メールまたは電子メールがトリガーされる問題を修正します。
1. **ACSD-64431**: リクエストにクーポンコード情報を含む`placeOrder`の突然変異は、内部エラーをスローしなくなり、注文が正常に配置されたことを示します。
1. **ACSD-64467**：ストアビューレベルにカテゴリの説明を保存した後、WYSIWYG エディターが空で表示される問題を修正します。
1. **ACSD-64546**: UPS出荷ラベルの作成中に、UIで一般的なエラーメッセージが発生し、*配列から文字列への変換*&#x200B;の例外がログに保存される問題を修正し、実際のエラーがUIに表示され、正しいエラーメッセージがログに保存されるようにします。
1. **ACSD-64684**：数値&#x200B;*1000 （1,000）*&#x200B;のコンマ（千区切り記号）により、*999*&#x200B;より大きい値のギフトカードを編集および保存する際に検証エラーが発生する問題を修正します。

左側のメニューを使用して、特定のパッチページに移動します。
