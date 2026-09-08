---
title: 概要： [!DNL Quality Patches Tool]  （QPT） v1.1.41
description: このサブセクションでは、 [!DNL Quality Patches Tool]  （QPT） v1.1.41で使用可能なパッチによって修正された問題について詳しく説明します。
feature: Tools and External Services
role: Admin, Developer
exl-id: 10e1f4f9-8c6b-45b2-b6ed-0758c8019c8c
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '233'
ht-degree: 0%

---

# 概要：[!DNL Quality Patches Tool] （QPT） v1.1.41

このサブセクションでは、[!DNL Quality Patches Tool] （QPT） v1.1.41で利用可能なパッチによって修正された問題について詳しく説明します。

QPT v1.1.41には、次のパッチが含まれています。

1. **ACSD-54376**：商品が既に買い物かごに追加された後に共有カタログから削除されたときに、買い物かごで発生する問題を修正します。
1. **ACSD-53722**：異なるスコープのスケジュールされた更新がアクティブになると、バンドルされた製品オプションの価格が$0に変更される問題を修正します。
1. **ACSD-53643**：無効な商品または在庫切れの商品を含む発注書を配置する際に、注文の合計が正しくない問題を修正します。 このような発注の&#x200B;*[!UICONTROL Place Order]* ボタンを非表示にすることで修正されます。
1. **ACSD-54067**：製品ビデオがモバイルデバイスで再生されない問題を修正します。
1. **ACSD-55414**: MariaDBがEAV entity_idを文字列から整数にキャストしようとすると、パフォーマンスが向上します。
1. **ACSD-51819**：同じ見積もりIDで複数の注文を配置できる問題を修正します。
1. **ACSD-53118**：製品に空の属性がある場合に、クーポンコードを使用して&#x200B;*[!UICONTROL Cart Price Rule]*&#x200B;が適用される問題を修正します。
1. **ACSD-54324**: GraphQL requisition_lists リクエストでページネーション設定が考慮されず、すべての結果が返される問題を修正します。

左側のメニューを使用して、特定のパッチページに移動します。
