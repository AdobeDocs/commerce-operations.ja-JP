---
title: 概要： [!DNL Quality Patches Tool]  （QPT） v1.1.72
description: このサブセクションでは、 [!DNL Quality Patches Tool]  （QPT） v1.1.72 で使用可能なパッチによって修正された問題について詳しく説明します。
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
source-git-commit: a6a18a4cbab9d2e5a0c4824fc5ad9463f9e61c1c
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---

# 概要：[!DNL Quality Patches Tool] （QPT） v1.1.72

このサブセクションでは、[!DNL Quality Patches Tool] （QPT） v1.1.72 で使用可能なパッチによって修正された問題について詳しく説明します。

QPT v1.1.72 には、次のパッチが含まれています。
1. **ACSD-68040**：多くの履歴検索リクエストにより、フロントエンド検索ページの [!DNL MariaDB] 10.6 および 11.4 でパフォーマンスが低下します。
1. **ACSD-67941**：不明なフィルター名を持つGraphQL リクエストが原因で PHP 例外ログが発生する。
1. **ACSD-68064**：スケジュールされた更新を作成すると、ネストされたカテゴリの数が多い環境でエントリが重複します。
1. **ACSD-66807**:`report_viewed_product_index` のテーブルに表示される製品ページビューの数が正しくありません。
1. **ACSD-67383**：同じセッションで 2 つの会社管理者アカウントを持つ顧客としてログインすると、*cartId のそのようなエンティティがありません* エラーが発生する。
1. **ACSD-67518**：詳細レポートでは、行数がバッチサイズを超えると、重複したヘッダー行が生成されます。
1. **ACSD-67639**:**[!UICONTROL Dynamic Price]** が *No* に設定されているバンドル製品のクレジットメモの作成に失敗する。
1. **[ACSD-67696](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-72/acsd-67696.md)**：キャッシュのフラッシュ後、`media_gallery` エントリが買い物かごGraphQLの商品ノードに返されない。
1. **ACSD-67946**：買い物かごの更新で、重複したエラーバナーが表示される。
1. **ACSD-68011**:`/V1/sharedCatalog/:id/assignProducts` [!DNL REST] API を使用して、存在しない SKU を共有カタログに割り当てることができます。
1. **ACSD-68118**:GraphQL クエリ `customerCart`、ストアヘッダーを反映していない product 属性値を返すため、ローカリゼーションに一貫性がなくなります。
1. **ACSD-68092**：予定されているアップデートとベース製品データの間の不適切な同期により、複数の保存後にバンドル製品オプションが失われる。
1. **ACSD-67424**:`updated_at` `GET /carts/search` API 応答の [!DNL REST] 値が、ネゴシエート可能な引用符を使用するときに **[!UICONTROL Admin panel]** に表示される値と一致しません。
1. **ACSD-67187**：デフォルト以外の web サイトに制限された管理者ユーザーに、「*続行するには少なくとも 1 つの公開共有カタログを作成してください* というエラーが表示され、会社グリッドの「**[!UICONTROL Add New Company]**」ボタンにアクセスできません。

左側のメニューを使用して、特定のパッチページに移動します。
