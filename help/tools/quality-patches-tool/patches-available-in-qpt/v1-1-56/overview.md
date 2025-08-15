---
title: 概要： [!DNL Quality Patches Tool]  （QPT） v1.1.56
description: このサブセクションでは、 [!DNL Quality Patches Tool]  （QPT） v1.1.56 で使用可能なパッチによって修正された問題について詳しく説明します。
feature: Tools and External Services
role: Admin, Developer
exl-id: 6433df73-b6df-4c88-93a4-12ac1e5080ea
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# 概要：[!DNL Quality Patches Tool] （QPT） v1.1.56

このサブセクションでは、[!DNL Quality Patches Tool] （QPT） v1.1.56 で使用可能なパッチによって修正された問題について詳しく説明します。

QPT v1.1.56 には、次のパッチが含まれています。

1. **ACSD-63244**:JavaScript エラーによって [!DNL Google Maps] が正しくレンダリングされない問題と、多くの *Uncaught TypeError：この問題を修正しました。_each は関数ではなく*[!UICONTROL Admin] パネルのコンソールでエラーが発生します。
1. **ACSD-63242**:10,000 個を超えるエントリを持つカタログ製品を追加した場合の、読み込み速度の低下の問題を修正しました。
1. **ACSD-63062**：複数の重複するルールが適用されている場合に、買い物かごの割引計算が正しく実行されない問題を修正しました。
1. **ACSD-62979**:GraphQL ヘッダーで間違った [!UICONTROL Store ID] を使用すると、致命的なメモリエラーが発生する問題を修正しました。
1. **ACSD-62971**: *[!UICONTROL Quantity]* 列に数値以外の値が含まれている在庫ソースをインポートすると、*quantity* が *0* に設定される問題を修正しました。
1. **ACSD-62872**：スケジュールの更新が正しく検証されない一意の属性の検証の問題を修正しました。
1. **ACSD-62755**:[!DNL TinyMCE] 7 で、エディターの初期化設定内でフォントサイズとフォントを特別に追加する必要がある問題を修正しました。
1. **ACSD-62670**:[!UICONTROL Products Ordered] レポートを CSV および XML に書き出すとエラーが返される問題を修正しました。
1. **ACSD-62577**：クエリインデックスとテーブルインデックスの両方を最適化することで、ストアフロント検索クエリのパフォーマンスが遅い問題を修正しました。
1. **ACSD-62475**：買い物かごで [!UICONTROL Gift Card] 製品が正しく結合されない問題を修正しました。
1. **ACSD-62428**:`is_out_of_stock` が検索可能な属性として設定されていない場合に、[!DNL SKU] がカタログ検索インデックスで誤った値に設定される問題を修正しました。
1. **ACSD-62355**：設定可能な製品が、多くの値を持つ多くの属性に基づいている場合、設定可能な製品編集ページの読み込み時間が改善されます。
1. **ACSD-61805**:[!DNL REST API] でバックオーダーのステータスを更新した後、ストアフロントで製品の在庫切れが発生する問題を修正しました。
1. **ACSD-60811**：現在のステータスが *[!UICONTROL Processing]* または *[!UICONTROL Fraud]* の場合にのみ、カスタム値またはコメントで注文ステータスを更新できる問題を修正しました。
1. **ACSD-62952**：ストアフロントに [!UICONTROL Gift Registry] 定日が正しく表示されない問題を修正。
1. **ACSD-55339**:[!DNL SKU]0 *（ゼロ）で始まる製品**0* を削除し、引用符が更新されない問題を修正しました。

左側のメニューを使用して、特定のパッチページに移動します。
