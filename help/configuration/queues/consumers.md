---
title: メッセージキューコンシューマー
description: Adobe Commerce メッセージキューコンシューマーについて、関連する機能やシステム設定などを説明します。
exl-id: 7fd7ab3f-581f-493c-956c-731f111d1b14
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '825'
ht-degree: 0%

---

# メッセージキューコンシューマー

次の表は、すべてのメッセージキューコンシューマーを特定し、その実行内容およびコンシューマーに関連付けられた管理システムの設定を示しています。

| 消費者と説明 | Adobe Commerce | B2B のAdobe Commerce | Magento Open Source |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------|-------------------------|---------------------|
| `async.operations.all` | + | + | + |
| の個々のタスクごとにメッセージを作成します [一括操作](https://developer.adobe.com/commerce/php/development/components/message-queues/bulk-operations/)品目のインポートまたはエクスポート、一括スケールでの価格の変更、倉庫への製品の割当てなど。 次の場合に必須： [**[!UICONTROL Admin bulk operations]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html?#admin-bulk-operations) オプションの設定&#x200B;**[!UICONTROL Run asynchronously]**管理システムの設定で行います。 |                |                         |                     |
| `codegeneratorProcessor` | + | + | + |
| バックグラウンドで非同期にクーポンを生成します。 を使用するために必要です。 [バッチクーポンの生成](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart-coupon.html#method-2%3A-generate-a-batch-of-coupons) 機能 |                |                         |                     |
| `commerce.eventing.event.publish` | + | + |                     |
| で優先度として登録されているイベントを確認します。 [Adobe CommerceのAdobe I/Oイベント](https://developer.adobe.com/commerce/events/get-started/). |
| `exportProcessor` | + | + | + |
| 次の期間の接続タイムアウトを防ぐ [export](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-export.html) （例：200,000 個の製品など）を含む大規模なデータセットです。 |                |                         |                     |
| `inventoryQtyCounter` | + | + |                     |
| 注文または製品の削除後に、在庫インデックスを非同期で修正します。 次の場合に必須： [**[!UICONTROL Use deferred stock update]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html#product-stock-options) オプションは、管理設定で有効になっています。 参照： [パフォーマンスのベストプラクティス](https://experienceleague.adobe.com/docs/commerce-operations/performance-best-practices/configuration.html#deferred-stock-update). |                |                         |                     |
| `inventory.source.items.cleanup` | + | + | + |
| 製品が削除されると、製品 SKU ごとにソース項目を非同期で削除します。 次の場合に必須： [**[!UICONTROL Synchronize with Catalog]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html) stock オプションは、「管理システム」設定で有効になっています。 |                |                         |                     |
| `inventory.mass.update` | + | + | + |
| は、従来の在庫項目の処理、従来の在庫項目の更新、デフォルトのソース項目の更新、特定の製品 SKU の在庫のインデックス再作成を非同期で行います。 次の場合に必須： [**[!UICONTROL Run asynchronously]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html#admin-bulk-operations) 一括操作は、管理システム設定で有効になっています。 |                |                         |                     |
| `inventory.reservations.cleanup` | + | + | + |
| 製品の削除後に、製品 SKU によって予約を非同期で削除します。 次の場合に必須： [**[!UICONTROL Synchronize with Catalog]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html) stock オプションは、「管理システム」設定で有効になっています。 |                |                         |                     |
| `inventory.reservations.update` | + | + | + |
| 製品が削除された後に、製品 SKU によって予約を非同期に更新します。 次の場合に必須： [**[!UICONTROL Synchronize with Catalog]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html) stock オプションは、「管理システム」設定で有効になっています。 |                |                         |                     |
| `inventory.reservations.updateSalabilityStatus` | + | + | + |
| 在庫に割り当てられた各製品の販売可能数量を非同期で更新します。 を使用している場合、このコンシューマーは常に起動して実行されている必要があります [!DNL Inventory Management]. |                |                         |                     |
| `inventory.indexer.sourceItem` | + | + | + |
| ソースアイテムのインデックスを非同期で再作成します。 次の場合に必須： [**[!UICONTROL Stock/Source reindex strategy]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html#inventory-indexer-settings) はに設定されています。[!UICONTROL asynchronous]」と表示されます。 |                |                         |                     |
| `inventory.indexer.stock` | + | + | + |
| Stock のインデックスを非同期で再作成します。 次の場合に必須： [**[!UICONTROL Stock/Source reindex strategy]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html#inventory-indexer-settings) はに設定されています。[!UICONTROL asynchronous]」と表示されます。 |                |                         |                     |
| `matchCustomerSegmentProcessor` | + | + |                     |
| 一時データベース テーブルを作成し、各テーブルを移動します [顧客セグメント](https://docs.magento.com/user-guide/marketing/customer-segments.html) その中に、セグメント ID に一致するすべてのセグメントを削除し、セグメント ID をインジケーターとして使用して、それらを顧客セグメントにコピーします。 これはすべてトランザクションで行われるので、何かが失敗した場合、トランザクションはこの実行前の状態にロールバックされます。 トランザクションの後、コンシューマーは一時テーブルを削除します。 |                |                         |                     |
| `media.content.synchronization` | + | + | + |
| 製品、カテゴリ、CMS ブロック、CMS ページに割り当てられたメディアへのリンクが、アセットに正しく割り当てられていることを確認します。 使用されなくなった古いアセットを削除します。 |                |                         |                     |
| `media.gallery.renditions.update` | + | + | + |
| メディアアセットのパスを生成および検証します。 アセットの絶対パスは、メディアディレクトリ内からサーバー上のどこにあるかによって決まります。 画像は（必要に応じて）サイズ変更され、生成されたパス内のメディアディレクトリにコピーされます。 |                |                         |                     |
| `media.gallery.synchronization` | + | + | + |
| 画像ファイルをに読み込みます `media_gallery_asset` データベーステーブル。 |                |                         |                     |
| `media.storage.catalog.image.resize` | + | + | + |
| 非同期 [サイズ変更](https://developer.adobe.com/commerce/frontend-core/guide/themes/configure/#resize-catalog-images) カタログ画像。 |                |                         |                     |
| `negotiableQuotePriceUpdate` |                | + |                     |
| 交渉可能な見積の価格を更新します。 次の場合に必須： [**[!UICONTROL Quotes]**](https://docs.magento.com/user-guide/sales/quotes.html) 管理システムの設定で、オプションが有効になっている。 |                |                         |                     |
| `placeOrderProcessor` | + | + |                     |
| 非同期 [注文を処理](https://developer.adobe.com/commerce/php/module-reference/module-async-order/)注文を受信済みとしてマークし、メッセージキューに入れて、先入れ先出しで処理します。 が次と見なされます [ベストプラクティス](../../implementation-playbook/best-practices/maintenance/order-processing-configuration.md) 顧客がバックエンドプロセスの完了を待たずに成功メッセージが表示されるため、処理可能な注文の数を改善する場合。 |                |                         |                     |
| `product_action_attribute.update` | + | + | + |
| 管理者を使用して次の操作を行った後、製品属性への変更をデータベースに非同期で書き込む [更新する](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/bulk-product-attribute-update.html). |                |                         |                     |
| `product_action_attribute.website.update` | + | + | + |
| 管理者を使用して次の操作を行った後、データベース内の特定のストア表示の製品属性に対する変更が非同期で書き込まれます [更新する](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/bulk-product-attribute-update.html). |                |                         |                     |
| `product_alert` | + | + | + |
| 製品価格および在庫変更に関する通知メールを顧客に送信します。 必要なときに、 [**[!UICONTROL Product Alerts]**](https://experienceleague.adobe.com/docs/commerce-admin/inventory/configuration/product-alerts/alert-setup.html) 管理システムの設定で、オプションが有効になっている。 |                |                         |                     |
| `purchaseorder.toorder` |                | + |                     |
| 発注書をに変換します [順序](https://docs.magento.com/user-guide/stores/b2b-purchase-order-flow.html#approval-rules). 次の場合に必須： [**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html) 管理システムの設定で、オプションが有効になっている。 |                |                         |                     |
| `purchaseorder.transactional.email` |                | + |                     |
| 発注書 E メールを送信します。 次の場合に必須： [**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html) 管理システムの設定で、オプションが有効になっている。 |                |                         |                     |
| `purchaseorder.validation` |                | + |                     |
| 関連する発注を検証します。 [承認ルール](https://docs.magento.com/user-guide/customers/account-dashboard-approval-rules.html). 次の場合に必須： [**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html) 管理システムの設定で、オプションが有効になっている。 |                |                         |                     |
| `saveConfigProcessor` | + |                         | + |
| 保存ジョブをメッセージキューに配置すると、ストア設定の変更を非同期に保存できます。これにより、多数のストアレベル設定を含むデプロイメントのパフォーマンスが向上します。 を使用するために必要です。 [`AsyncConfig`](../../performance/configuration.md#asynchronous-configuration-save) モジュール。 |                |                         |                     |
| `sales.rule.update.coupon.usage` | + | + | + |
| を禁止します [問題](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/coupon-code-used-more-than-once-adobe-commerce.html) 1 回限りのクーポンを複数回使用できる場合。 |                |                         |                     |
| `sharedCatalogUpdateCategoryPermissions` |                | + |                     |
| 共有カタログ カテゴリに割り当てられているカテゴリを更新します。 次の場合に必須： [**[!UICONTROL Shared Catalogs]**](https://docs.magento.com/user-guide/catalog/catalog-shared.html) 管理システムの設定で、オプションが有効になっている。 |                |                         |                     |
| `sharedCatalogUpdatePrice` |                | + |                     |
| 共有カタログ内の各製品の価格を更新します。 次の場合に必須： [**[!UICONTROL Shared Catalogs]**](https://docs.magento.com/user-guide/catalog/catalog-shared.html) 管理システムの設定で、オプションが有効になっている。 |                |                         |                     |
| `quoteItemCleaner` | + | + |                     |
| 商品がカタログから削除された場合、または買い物かごから削除された場合に、無効または非アクティブな価格見積を削除します。 次の場合に必須： [**[!UICONTROL Quotes]**](https://docs.magento.com/user-guide/sales/quotes.html) 管理システムの設定で、オプションが有効になっている。 |                |                         |                     |
| `sales.rule.quote.trigger.recollect` | + | + | + |
| アクティブな買い物かご価格ルールの変更を反映するように、アクティブな買い物かご設定を更新します。 更新時に必須 [**[!UICONTROL Catalog price rules]**](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/catalog-rules/price-rules-catalog.html). |                |                         |                     |

{style="table-layout:auto"}
