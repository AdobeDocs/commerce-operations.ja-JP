---
title: メッセージキューコンシューマー
description: Adobe Commerce メッセージキューコンシューマーについて、関連する機能やシステム設定などを説明します。
exl-id: 7fd7ab3f-581f-493c-956c-731f111d1b14
source-git-commit: 95ea96a566b0579a22b2ba738bd4a4bceef8cd9c
workflow-type: tm+mt
source-wordcount: '824'
ht-degree: 0%

---

# メッセージキューコンシューマー

次の表は、すべてのメッセージキューコンシューマーを特定し、その実行内容およびコンシューマーに関連付けられた管理システムの設定を示しています。

| 消費者と説明 | Adobe Commerce | B2B のAdobe Commerce | Magento Open Source |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------|-------------------------|---------------------|
| `async.operations.all` | + | + | + |
| 品目のインポートまたはエクスポート、一括スケールでの価格の変更、倉庫への製品の割り当てなど、[ 一括操作 ](https://developer.adobe.com/commerce/php/development/components/message-queues/bulk-operations/) の個々のタスクごとにメッセージを作成します。 管理システム設定で [**[!UICONTROL Admin bulk operations]**](https://experienceleague.adobe.com/ja/docs/commerce-admin/config/catalog/inventory#admin-bulk-operations) オプションが&#x200B;**[!UICONTROL Run asynchronously]**&#x200B;に設定されている場合は必須です。 |                |                         |                     |
| `codegeneratorProcessor` | + | + | + |
| バックグラウンドで非同期にクーポンを生成します。 [ バッチクーポン生成 ](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart-coupon.html?lang=ja#method-2%3A-generate-a-batch-of-coupons) 機能を使用するために必要です。 |                |                         |                     |
| `commerce.eventing.event.publish` | + | + |                     |
| [Adobe Commerce用Adobe I/O Events](https://developer.adobe.com/commerce/events/get-started/) に優先度として登録されているイベントを確認します。 |
| `exportProcessor` | + | + | + |
| 大きなデータセット（例：200,000 個の製品）の [ 書き出し ](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-export.html?lang=ja) 中に接続タイムアウトが発生するのを防ぎます。 |                |                         |                     |
| `inventoryQtyCounter` | + | + |                     |
| 注文または製品の削除後に、在庫インデックスを非同期で修正します。 管理者設定で「[**[!UICONTROL Use deferred stock update]**](https://experienceleague.adobe.com/ja/docs/commerce-admin/config/catalog/inventory#product-stock-options)」オプションが有効な場合は必須です。 [ パフォーマンスのベストプラクティス ](https://experienceleague.adobe.com/docs/commerce-operations/performance-best-practices/configuration.html?lang=ja#deferred-stock-update) を参照してください。 |                |                         |                     |
| `inventory.source.items.cleanup` | + | + | + |
| 製品が削除されると、製品 SKU ごとにソース項目を非同期で削除します。 管理システムの設定で「[**[!UICONTROL Synchronize with Catalog]**](https://experienceleague.adobe.com/ja/docs/commerce-admin/config/catalog/inventory) stock」オプションが有効になっている場合は必須です。 |                |                         |                     |
| `inventory.mass.update` | + | + | + |
| は、従来の在庫項目の処理、従来の在庫項目の更新、デフォルトのソース項目の更新、特定の製品 SKU の在庫のインデックス再作成を非同期で行います。 管理システム設定で [**[!UICONTROL Run asynchronously]**](https://experienceleague.adobe.com/ja/docs/commerce-admin/config/catalog/inventory#admin-bulk-operations) 一括操作が有効な場合に必要です。 |                |                         |                     |
| `inventory.reservations.cleanup` | + | + | + |
| 製品の削除後に、製品 SKU によって予約を非同期で削除します。 管理システムの設定で「[**[!UICONTROL Synchronize with Catalog]**](https://experienceleague.adobe.com/ja/docs/commerce-admin/config/catalog/inventory) stock」オプションが有効になっている場合は必須です。 |                |                         |                     |
| `inventory.reservations.update` | + | + | + |
| 製品が削除された後に、製品 SKU によって予約を非同期に更新します。 管理システムの設定で「[**[!UICONTROL Synchronize with Catalog]**](https://experienceleague.adobe.com/ja/docs/commerce-admin/config/catalog/inventory) stock」オプションが有効になっている場合は必須です。 |                |                         |                     |
| `inventory.reservations.updateSalabilityStatus` | + | + | + |
| 在庫に割り当てられた各製品の販売可能数量を非同期で更新します。 [!DNL Inventory Management] を使用している場合、このコンシューマーは常に起動および実行されている必要があります。 |                |                         |                     |
| `inventory.indexer.sourceItem` | + | + | + |
| ソースアイテムのインデックスを非同期で再作成します。 管理システム設定で [**[!UICONTROL Stock/Source reindex strategy]**](https://experienceleague.adobe.com/ja/docs/commerce-admin/config/catalog/inventory#inventory-indexer-settings) が&quot;[!UICONTROL asynchronous]&quot;に設定されている場合に必要です。 |                |                         |                     |
| `inventory.indexer.stock` | + | + | + |
| Stock のインデックスを非同期で再作成します。 管理システム設定で [**[!UICONTROL Stock/Source reindex strategy]**](https://experienceleague.adobe.com/ja/docs/commerce-admin/config/catalog/inventory#inventory-indexer-settings) が&quot;[!UICONTROL asynchronous]&quot;に設定されている場合に必要です。 |                |                         |                     |
| `matchCustomerSegmentProcessor` | + | + |                     |
| 一時データベーステーブルを作成し、各 [ 顧客セグメント ](https://experienceleague.adobe.com/ja/docs/commerce-admin/customers/segments/customer-segments) をそのテーブルに移動し、セグメント ID に一致するすべてのセグメントを削除して、セグメント ID をインジケーターとして使用して顧客セグメントにコピーします。 これはすべてトランザクションで行われるので、何かが失敗した場合、トランザクションはこの実行前の状態にロールバックされます。 トランザクションの後、コンシューマーは一時テーブルを削除します。 |                |                         |                     |
| `media.content.synchronization` | + | + | + |
| 商品、カテゴリ、CMS ブロック、CMS ページに割り当てられたメディアへのリンクが、アセットに正しく割り当てられていることを確認します。 使用されなくなった古いアセットを削除します。 |                |                         |                     |
| `media.gallery.renditions.update` | + | + | + |
| メディアアセットのパスを生成および検証します。 アセットの絶対パスは、メディアディレクトリ内からサーバー上のどこにあるかによって決まります。 画像は（必要に応じて）サイズ変更され、生成されたパス内のメディアディレクトリにコピーされます。 |                |                         |                     |
| `media.gallery.synchronization` | + | + | + |
| `media_gallery_asset` データベース テーブルにイメージ ファイルをインポートします。 |                |                         |                     |
| `media.storage.catalog.image.resize` | + | + | + |
| カタログ画像を非同期に [ サイズ変更 ](https://developer.adobe.com/commerce/frontend-core/guide/themes/configure/#resize-catalog-images) します。 |                |                         |                     |
| `negotiableQuotePriceUpdate` |                | + |                     |
| 交渉可能な見積の価格を更新します。 管理システム設定で「[**[!UICONTROL Quotes]**](https://experienceleague.adobe.com/ja/docs/commerce-admin/b2b/quotes/quotes)」オプションが有効になっている場合は必須です。 |                |                         |                     |
| `placeOrderProcessor` | + | + |                     |
| 注文を非同期的に処理 [ します ](https://developer.adobe.com/commerce/php/module-reference/module-async-order/) 注文を受信済みとしてマークし、メッセージキューに配置して、先入れ先出し方式で処理します。 顧客は成功メッセージを表示する前にバックエンド処理が完了するのを待つ必要がないので、処理可能な注文の数を改善するための [ ベストプラクティス ](../../implementation-playbook/best-practices/maintenance/order-processing-configuration.md) と見なされます。 |                |                         |                     |
| `product_action_attribute.update` | + | + | + |
| 管理者を使用して [ 更新を行う ](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/bulk-product-attribute-update.html?lang=ja) と、製品属性に対する変更がデータベースに非同期で書き込まれます。 |                |                         |                     |
| `product_action_attribute.website.update` | + | + | + |
| 管理者を使用して [ 更新を行う ](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/bulk-product-attribute-update.html?lang=ja) と、データベース内の特定のストア表示の製品属性に対する変更が非同期で書き込まれます。 |                |                         |                     |
| `product_alert` | + | + | + |
| 製品価格および在庫変更に関する通知メールを顧客に送信します。 管理システムの設定で「[**[!UICONTROL Product Alerts]**](https://experienceleague.adobe.com/docs/commerce-admin/inventory/configuration/product-alerts/alert-setup.html?lang=ja)」オプションが有効な場合に必要です。 |                |                         |                     |
| `purchaseorder.toorder` |                | + |                     |
| 発注書を [order](https://experienceleague.adobe.com/ja/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow#approval-rules) に変換します。 管理システム設定で「[**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html?lang=ja)」オプションが有効になっている場合は必須です。 |                |                         |                     |
| `purchaseorder.transactional.email` |                | + |                     |
| 発注書 E メールを送信します。 管理システム設定で「[**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html?lang=ja)」オプションが有効になっている場合は必須です。 |                |                         |                     |
| `purchaseorder.validation` |                | + |                     |
| 関連する [ 承認ルール ](https://experienceleague.adobe.com/ja/docs/commerce-admin/b2b/purchase-orders/account-dashboard-approval-rules) に対して発注書を検証します。 管理システム設定で「[**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html?lang=ja)」オプションが有効になっている場合は必須です。 |                |                         |                     |
| `saveConfigProcessor` | + |                         | + |
| 保存ジョブをメッセージキューに配置すると、ストア設定の変更を非同期に保存できます。これにより、多数のストアレベル設定を含むデプロイメントのパフォーマンスが向上します。 [`AsyncConfig`](../../performance/configuration.md#asynchronous-configuration-save) モジュールを使用するために必要です。 |                |                         |                     |
| `sales.rule.update.coupon.usage` | + | + | + |
| 1 回限りのクーポンを複数回使用できる問題を防ぎます。 |                |                         |                     |
| `sharedCatalogUpdateCategoryPermissions` |                | + |                     |
| 共有カタログ カテゴリに割り当てられているカテゴリを更新します。 管理システム設定で「[**[!UICONTROL Shared Catalogs]**](https://experienceleague.adobe.com/ja/docs/commerce-admin/b2b/shared-catalogs/catalog-shared)」オプションが有効になっている場合は必須です。 |                |                         |                     |
| `sharedCatalogUpdatePrice` |                | + |                     |
| 共有カタログ内の各製品の価格を更新します。 管理システム設定で「[**[!UICONTROL Shared Catalogs]**](https://experienceleague.adobe.com/ja/docs/commerce-admin/b2b/shared-catalogs/catalog-shared)」オプションが有効になっている場合は必須です。 |                |                         |                     |
| `quoteItemCleaner` | + | + |                     |
| 商品がカタログから削除された場合、または買い物かごから削除された場合に、無効または非アクティブな価格見積を削除します。 管理システム設定で「[**[!UICONTROL Quotes]**](https://experienceleague.adobe.com/ja/docs/commerce-admin/b2b/quotes/quotes)」オプションが有効になっている場合は必須です。 |                |                         |                     |
| `sales.rule.quote.trigger.recollect` | + | + | + |
| アクティブな買い物かご価格ルールの変更を反映するように、アクティブな買い物かご設定を更新します。 [**[!UICONTROL Catalog price rules]**](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/catalog-rules/price-rules-catalog.html?lang=ja) の更新時に必須です。 |                |                         |                     |

{style="table-layout:auto"}
