---
title: メッセージキューコンシューマー
description: Adobe CommerceおよびMagento Open Sourceメッセージキューの消費者（関連する機能やシステム設定を含む）について説明します。
source-git-commit: 2eecaab32b090cfd3c1a8e8832027d3531cf0edc
workflow-type: tm+mt
source-wordcount: '929'
ht-degree: 0%

---


# メッセージキューコンシューマー

次の表に、すべてのメッセージキューコンシューマー、その動作、およびそれらに関連する管理システム設定を示します。

| 消費者と説明 | Adobe Commerce | Adobe Commerceと B2B | Magento Open Source |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------|-------------------------|---------------------|
| `async.operations.all` | + | + | + |
| の個々のタスクにメッセージを作成します [バルク操作](https://developer.adobe.com/commerce/php/development/components/message-queues/bulk-operations/)（品目のインポートまたはエクスポート、一括価格での価格変更、倉庫への製品の割り当てなど）。 必須 [**[!UICONTROL Admin bulk operations]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html?#admin-bulk-operations) オプションが&#x200B;**[!UICONTROL Run asynchronously]**」をクリックします。 |  |  |  |
| `codegeneratorProcessor` | + | + | + |
| バックグラウンドでクーポンを非同期的に生成します。 を使用するために必要 [バッチクーポン生成](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart-coupon.html#method-2%3A-generate-a-batch-of-coupons) 機能。 |  |  |  |
| `exportProcessor` | + | + | + |
| 次の期間中に接続のタイムアウトを防ぐ [書き出し](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-export.html) 大規模なデータセット（200,000 個の製品など）の |  |  |  |
| `inventoryQtyCounter` | + | + |  |
| 注文が行われた後、または製品が削除された後に、在庫指数を非同期で修正します。 必須 [**[!UICONTROL Use deferred stock update]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html#product-stock-options) 」オプションが「管理者」設定で有効になっている。 詳しくは、 [パフォーマンスのベストプラクティス](https://experienceleague.adobe.com/docs/commerce-operations/performance-best-practices/configuration.html#deferred-stock-update). |  |  |  |
| `inventory.source.items.cleanup` | + | + | + |
| 製品が削除されたときに、製品 SKU ごとにソース品目を非同期的に削除します。 必須 [**[!UICONTROL Synchronize with Catalog]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html) 「在庫」オプションは「管理」のシステム設定で有効になっています。 |  |  |  |
| `inventory.mass.update` | + | + | + |
| レガシー在庫品目の非同期処理、レガシー在庫品目の更新、デフォルトのソース品目の更新、特定の製品 SKU の在庫のインデックス再作成をおこないます。 必須 [**[!UICONTROL Run asynchronously]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html#admin-bulk-operations) 一括操作は、管理システムの設定で有効になっています。 |  |  |  |
| `inventory.reservations.cleanup` | + | + | + |
| 製品が削除された後、製品 SKU 別の予約を非同期的に削除します。 必須 [**[!UICONTROL Synchronize with Catalog]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html) 「在庫」オプションは「管理」のシステム設定で有効になっています。 |  |  |  |
| `inventory.reservations.update` | + | + | + |
| 製品が削除された後、製品 SKU 別の予約を非同期的に更新します。 必須 [**[!UICONTROL Synchronize with Catalog]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html) 「在庫」オプションは「管理」のシステム設定で有効になっています。 |  |  |  |
| `inventory.reservations.updateSalabilityStatus` | + | + | + |
| 在庫に割り当てられた各製品の販売可能数量を非同期的に更新します。 次を使用している場合は、このコンシューマーは常に稼動状態である必要があります。 [!DNL Inventory Management]. |  |  |  |
| `inventory.indexer.sourceItem` | + | + | + |
| ソース項目のインデックスを非同期で再作成します。 必須 [**[!UICONTROL Stock/Source reindex strategy]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html#inventory-indexer-settings) が&quot;に設定されている[!UICONTROL asynchronous]」が追加されました。 |  |  |  |
| `inventory.indexer.stock` | + | + | + |
| 在庫を非同期的に再インデックスします。 必須 [**[!UICONTROL Stock/Source reindex strategy]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html#inventory-indexer-settings) が&quot;に設定されている[!UICONTROL asynchronous]」が追加されました。 |  |  |  |
| `matchCustomerSegmentProcessor` | + | + |  |
| 一時データベーステーブルを作成し、各テーブルを移動します [顧客セグメント](https://docs.magento.com/user-guide/marketing/customer-segments.html) このレポートに、セグメント ID に一致するすべてのセグメントを削除し、指標としてセグメント ID を使用して顧客セグメントにコピーします。 これはすべてトランザクションで実行され、何かが失敗した場合、トランザクションは、実行前の状態にロールバックされます。 トランザクションの後、消費者は一時テーブルを破棄します。 |  |  |  |
| `media.content.synchronization` | + | + | + |
| 製品、カテゴリ、CMS ブロック、CMS ページの割り当てられたメディアへのリンクが、アセットに正しく割り当てられていることを確認します。 使用されなくなった古いアセットを削除します。 |  |  |  |
| `media.gallery.renditions.update` | + | + | + |
| メディアアセットのパスを生成および検証します。 アセットの絶対パスは、アセットがサーバー上のメディアディレクトリ内のどこに配置されているかによって決まります。 画像は（必要に応じて）サイズ変更され、生成されたパス内のメディアディレクトリにコピーされます。 |  |  |  |
| `media.gallery.synchronization` | + | + | + |
| 画像ファイルをに読み込みます。 `media_gallery_asset` データベーステーブル。 |  |  |  |
| `media.storage.catalog.image.resize` | + | + | + |
| 非同期 [サイズ変更](https://developer.adobe.com/commerce/frontend-core/guide/themes/configure/#resize-catalog-images) カタログ画像。 |  |  |  |
| `negotiableQuotePriceUpdate` |  | + |  |
| ネゴシエーション可能な見積もりの価格を更新します。 必須 [**[!UICONTROL Quotes]**](https://docs.magento.com/user-guide/sales/quotes.html) オプションが有効になっている場合は、管理システム設定で有効になります。 |  |  |  |
| `placeOrderProcessor` | + | + |  |
| 非同期 [プロセスオーダー](https://developer.adobe.com/commerce/php/module-reference/module-async-order/)を呼び出し、注文を受信済みとマークし、メッセージキューに配置し、先入れ先出しベースで処理します。 考慮される [ベストプラクティス](../../implementation-playbook/best-practices/maintenance/order-processing-configuration.md) を参照してください。 |  |  |  |
| `product_action_attribute.update` | + | + | + |
| 管理者が [更新を行う](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/bulk-product-attribute-update.html). |  |  |  |
| `product_action_attribute.website.update` | + | + | + |
| 管理者が [更新を行う](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/bulk-product-attribute-update.html). |  |  |  |
| `product_alert` | + | + | + |
| 製品価格と在庫の変更に関する通知 E メールを顧客に送信します。 必須 ( [**[!UICONTROL Product Alerts]**](https://experienceleague.adobe.com/docs/commerce-admin/inventory/configuration/product-alerts/alert-setup.html) オプションが有効になっている場合は、管理システム設定で有効になります。 |  |  |  |
| `purchaseorder.toorder` |  | + |  |
| 発注書をに変換します [注文](https://docs.magento.com/user-guide/stores/b2b-purchase-order-flow.html#approval-rules). 必須 [**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html) オプションが有効になっている場合は、管理システム設定で有効になります。 |  |  |  |
| `purchaseorder.transactional.email` |  | + |  |
| 発注書の電子メールを送信します。 必須 [**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html) オプションが有効になっている場合は、管理システム設定で有効になります。 |  |  |  |
| `purchaseorder.validation` |  | + |  |
| 関連するに対して発注を検証します [承認ルール](https://docs.magento.com/user-guide/customers/account-dashboard-approval-rules.html). 必須 [**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html) オプションが有効になっている場合は、管理システム設定で有効になります。 |  |  |  |
| `sales.rule.update.coupon.usage` | + | + | + |
| 次の条件を満たさない [問題](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/coupon-code-used-more-than-once-adobe-commerce.html) ここでは、単一使用のクーポンを複数回使用できます。 |  |  |  |
| `sharedCatalogUpdateCategoryPermissions` |  | + |  |
| 共有カタログカテゴリに割り当てられたカテゴリを更新します。 必須 [**[!UICONTROL Shared Catalogs]**](https://docs.magento.com/user-guide/catalog/catalog-shared.html) オプションが有効になっている場合は、管理システム設定で有効になります。 |  |  |  |
| `sharedCatalogUpdatePrice` |  | + |  |
| 共有カタログ内の各製品の価格を更新します。 必須 [**[!UICONTROL Shared Catalogs]**](https://docs.magento.com/user-guide/catalog/catalog-shared.html) オプションが有効になっている場合は、管理システム設定で有効になります。 |  |  |  |
| `quoteItemCleaner` | + | + |  |
| 商品がカタログから削除されたり、買い物かごから削除されたりした場合に、無効または非アクティブな価格見積もりを削除します。 必須 [**[!UICONTROL Quotes]**](https://docs.magento.com/user-guide/sales/quotes.html) オプションが有効になっている場合は、管理システム設定で有効になります。 |  |  |  |

{style=&quot;table-layout:auto&quot;}
