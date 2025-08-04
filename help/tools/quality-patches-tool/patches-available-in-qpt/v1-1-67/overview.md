---
title: 概要： [!DNL Quality Patches Tool]  （QPT） v1.1.67
description: ここでは、 [!DNL Quality Patches Tool]  （QPT） v1.1.67 で使用可能なパッチによって修正された問題について詳しく説明します。
feature: Tools and External Services
role: Admin, Developer
exl-id: 47f6b57d-b945-4e77-8630-2df709a3469e
source-git-commit: 7fd88da04ca147829aa5aa7f90d05d8760ff0f3d
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 0%

---

# 概要：[!DNL Quality Patches Tool] （QPT） v1.1.67

このサブセクションでは、[!DNL Quality Patches Tool] （QPT） v1.1.67 で使用可能なパッチによって修正された問題について詳しく説明します。

QPT v1.1.67 には、次のパッチが含まれています。
1. **AC-14985**:TLS を使用して送信された SMTP メールがエラーを返す。
1. **AC-14984**: php-amqplib/php-amqplib ^3.2.0 での SSL 接続の問題。
1. **ACSD-65935**：商品 `customerOrders` 削除されたときに、GraphQL クエリが内部サーバーエラーを返しました。
1. **ACSD-66049**：英語以外のストアフロントで、ICU ライブラリのバージョンが原因で誤った価格が表示される。
1. **ACSD-66084**:`row_total_incl_tax` は、注文 API 応答で完全に割引された項目に対して、0.00 ではなく、ゼロに近い残差値を返します。
1. **ACSD-66118**：構成キャッシュが更新されない場合、ストア ビューコードを更新すると、デザイン構成の設定がクリアされます。
1. **ACSD-66139**:GraphQLが、注文処理中に、存在しない買い物かごや非アクティブな買い物かごに対して UNDEFINED エラーを返す。
1. **ACSD-66301**：管理で注文から買い物かごに製品を戻すと、数量が一致しません。
1. **[ACSD-66434](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-67/acsd-66434-customer-id-missing-from-company-graphql-queries.md)**：会社のGraphQL クエリに顧客 ID がありません。
1. **ACSD-66441**：マルチストア設定での設定可能な製品のレイヤナビゲーションで、インデックスデータが正しくありません。

左側のメニューを使用して、特定のパッチページに移動します。
