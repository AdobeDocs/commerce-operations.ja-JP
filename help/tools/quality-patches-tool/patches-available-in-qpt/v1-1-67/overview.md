---
title: 概要： [!DNL Quality Patches Tool]  （QPT） v1.1.67
description: ここでは、 [!DNL Quality Patches Tool]  （QPT） v1.1.67 で使用可能なパッチによって修正された問題について詳しく説明します。
feature: Tools and External Services
role: Admin, Developer
exl-id: 47f6b57d-b945-4e77-8630-2df709a3469e
source-git-commit: d025c8a6e451ff41ec4b50cf633927e52b9429f0
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 0%

---

# 概要：[!DNL Quality Patches Tool] （QPT） v1.1.67

このサブセクションでは、[!DNL Quality Patches Tool] （QPT） v1.1.67 で使用可能なパッチによって修正された問題について詳しく説明します。

QPT v1.1.67 には、次のパッチが含まれています。
1. **AC-14985**:TLS を使用して SMTP メールを送信する際にエラーが発生する。
1. **AC-14984**: php-amqplib/php-amqplib ^3.2.0 での SSL 接続の問題。
1. **ACSD-65935**：商品 `customerOrders` 削除されたときに、GraphQL クエリが内部サーバーエラーを返しました。
1. **ACSD-66049**：英語以外のストアフロントで、ICU ライブラリのバージョンが原因で誤った価格が表示される。
1. **ACSD-66084**:`row_total_incl_tax` は、注文 API 応答で完全に割引された項目に対して、0.00 ではなく、ゼロに近い残差値を返します。
1. **ACSD-66118**：設定キャッシュが更新されない場合、**[!UICONTROL Store View]** コード **[!UICONTROL Design Configuration]** 更新すると設定がクリアされます。
1. **ACSD-66139**:GraphQLが、注文処理中に、存在しない買い物かごや非アクティブな買い物かごに対して UNDEFINED エラーを返す。
1. **ACSD-66301**:Commerce管理で注文から買い物かごに商品を移動すると、数量が一致しません。
1. **ACSD-66434**：会社のGraphQL クエリに顧客 ID がありません。
1. **ACSD-66441**：マルチストア設定で、レイヤーナビゲーションに間違った属性オプションが表示される。

左側のメニューを使用して、特定のパッチページに移動します。
