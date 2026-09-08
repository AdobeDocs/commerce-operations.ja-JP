---
title: 概要： [!DNL Quality Patches Tool]  （QPT） v1.1.56
description: このサブセクションでは、 [!DNL Quality Patches Tool]  （QPT） v1.1.56で利用可能なパッチによって修正された問題について詳しく説明します。
feature: Tools and External Services
role: Admin, Developer
exl-id: 6433df73-b6df-4c88-93a4-12ac1e5080ea
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# 概要：[!DNL Quality Patches Tool] （QPT） v1.1.56

このサブセクションでは、[!DNL Quality Patches Tool] （QPT） v1.1.56で利用可能なパッチによって修正された問題について詳しく説明します。

QPT v1.1.56には、次のパッチが含まれています。

1. **ACSD-63244**: JavaScript エラーによって[!DNL Google Maps]が正しくレンダリングされず、*未検出のTypeErrorが多く発生する問題を修正します。this._eachは、[!UICONTROL Admin] パネルのコンソールの関数* エラーではありません。
1. **ACSD-63242**:10,000件を超えるエントリを含むカタログ製品を追加する際の読み込み速度の問題を修正します。
1. **ACSD-63062**：複数の重複するルールが適用される場合に誤ったカート割引の計算が発生する問題を修正します。
1. **ACSD-62979**: GraphQL ヘッダーで間違った[!UICONTROL Store ID]を使用すると致命的なメモリエラーが発生する問題を修正します。
1. **ACSD-62971**: *[!UICONTROL Quantity]*&#x200B;列に数値以外の値を持つ在庫ソースを読み込むと、*数量*&#x200B;が&#x200B;*0*&#x200B;に設定される問題を修正しました。
1. **ACSD-62872**: スケジュールの更新が正しく検証されない一意の属性検証の問題を修正します。
1. **ACSD-62755**: [!DNL TinyMCE] 7で、エディターの初期化設定内にフォントサイズとフォントを特別に追加する必要がある問題を修正します。
1. **ACSD-62670**: [!UICONTROL Products Ordered] レポートのCSVへの書き出しおよびXMLでエラーが返される問題を修正します。
1. **ACSD-62577**: クエリとテーブルの両方のインデックスを最適化することで、ストアフロント検索クエリのパフォーマンスが遅くなる問題を修正します。
1. **ACSD-62475**: [!UICONTROL Gift Card]製品が買い物かごに正しく結合されない問題を修正します。
1. **ACSD-62428**: [!DNL SKU]が検索可能な属性として設定されていない場合に、`is_out_of_stock`がカタログ検索インデックスの誤った値に設定される問題を修正します。
1. **ACSD-62355**：設定可能な製品が多くの値を持つ多くの属性に基づいている場合、設定可能な製品編集ページの読み込み時間を改善します。
1. **ACSD-61805**: [!DNL REST API]経由でバックオーダーのステータスを更新した後、ストアフロントで商品が在庫切れのままになる問題を修正します。
1. **ACSD-60811**：現在のステータスが&#x200B;*[!UICONTROL Processing]*&#x200B;または&#x200B;*[!UICONTROL Fraud]*&#x200B;の場合にのみ、カスタム値またはコメントで注文ステータスを更新できる問題を修正します。
1. **ACSD-62952**: [!UICONTROL Gift Registry]日がストアフロントに不正確に表示される問題を修正します。
1. **ACSD-55339**: *0* （ゼロ）で始まる製品[!DNL SKU]が&#x200B;*0*&#x200B;を削除し、見積が更新されない問題を修正します。

左側のメニューを使用して、特定のパッチページに移動します。
