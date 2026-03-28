---
title: メッセージキューコンシューマー
description: Adobe Commerce メッセージキューコンシューマーに関連する機能やシステム設定など、メッセージキューコンシューマーについて説明します。
exl-id: 7fd7ab3f-581f-493c-956c-731f111d1b14
source-git-commit: 7054a5286f01e26e324401f4d8505e4e0faed93e
workflow-type: tm+mt
source-wordcount: '824'
ht-degree: 0%

---

# メッセージキューコンシューマー

次の表は、すべてのメッセージキューコンシューマーを示し、その役割を説明し、関連する管理者システム設定設定を示しています。

| 消費者と説明 | Adobe Commerce | Adobe CommerceとB2Bの統合 | Magento Open Source |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------|-------------------------|---------------------|
| `async.operations.all` | + | + | + |
| 品目のインポートまたはエクスポート、大規模な価格変更、倉庫への製品の割り当てなど、[一括操作](https://developer.adobe.com/commerce/php/development/components/message-queues/bulk-operations/)の各タスクに対するメッセージを作成します。 管理者システム構成設定で&#x200B;[**[!UICONTROL Admin bulk operations]**](https://experienceleague.adobe.com/ja/docs/commerce-admin/config/catalog/inventory#admin-bulk-operations) オプションが&#x200B;**[!UICONTROL Run asynchronously]**&#x200B;に設定されている場合は必須です。 |                |                         |                     |
| `codegeneratorProcessor` | + | + | + |
| バックグラウンドでクーポンを非同期生成します。 [&#x200B; バッチクーポン生成](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart-coupon.html?lang=ja#method-2%3A-generate-a-batch-of-coupons)機能の使用に必要です。 |                |                         |                     |
| `commerce.eventing.event.publish` | + | + |                     |
| Adobe Commerce[の](https://developer.adobe.com/commerce/events/get-started/)Adobe I/O Eventsで優先度として登録されているイベントを確認します。 | | | |
| `exportProcessor` | + | + | + |
| 大規模なデータセット（例：200,000個の製品）の[書き出し](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-export.html?lang=ja)中に接続タイムアウトを防止します。 |                |                         |                     |
| `inventoryQtyCounter` | + | + |                     |
| 注文または商品が削除された後に、在庫指数を非同期で修正します。 管理者設定で&#x200B;[**[!UICONTROL Use deferred stock update]**](https://experienceleague.adobe.com/ja/docs/commerce-admin/config/catalog/inventory#product-stock-options) オプションが有効になっている場合は必須です。 [&#x200B; パフォーマンスのベストプラクティス &#x200B;](https://experienceleague.adobe.com/docs/commerce-operations/performance-best-practices/configuration.html?lang=ja#deferred-stock-update)を参照してください。 |                |                         |                     |
| `inventory.source.items.cleanup` | + | + | + |
| 製品が削除されると、製品SKUによってソース項目が非同期削除されます。 管理者システム構成設定で&#x200B;[**[!UICONTROL Synchronize with Catalog]**](https://experienceleague.adobe.com/ja/docs/commerce-admin/config/catalog/inventory) ストックオプションが有効になっている場合に必要です。 |                |                         |                     |
| `inventory.mass.update` | + | + | + |
| レガシー在庫商品の非同期処理、レガシー在庫商品の更新、デフォルトのソース品目の更新、特定の製品SKUの在庫のインデックス再作成を行います。 管理者システム構成設定で&#x200B;[**[!UICONTROL Run asynchronously]**](https://experienceleague.adobe.com/ja/docs/commerce-admin/config/catalog/inventory#admin-bulk-operations)一括操作が有効になっている場合に必要です。 |                |                         |                     |
| `inventory.reservations.cleanup` | + | + | + |
| 製品が削除された後、製品SKUによって予約を非同期削除します。 管理者システム構成設定で&#x200B;[**[!UICONTROL Synchronize with Catalog]**](https://experienceleague.adobe.com/ja/docs/commerce-admin/config/catalog/inventory) ストックオプションが有効になっている場合に必要です。 |                |                         |                     |
| `inventory.reservations.update` | + | + | + |
| 製品が削除された後、製品SKUによって予約を非同期で更新します。 管理者システム構成設定で&#x200B;[**[!UICONTROL Synchronize with Catalog]**](https://experienceleague.adobe.com/ja/docs/commerce-admin/config/catalog/inventory) ストックオプションが有効になっている場合に必要です。 |                |                         |                     |
| `inventory.reservations.updateSalabilityStatus` | + | + | + |
| 在庫に割り当てられた各製品の販売可能数量を非同期で更新します。 [!DNL Inventory Management]を使用している場合は、このコンシューマーを常に起動して実行する必要があります。 |                |                         |                     |
| `inventory.indexer.sourceItem` | + | + | + |
| ソースアイテムのインデックスを非同期で再作成します。 管理者システム構成設定で&#x200B;[**[!UICONTROL Stock/Source reindex strategy]**](https://experienceleague.adobe.com/ja/docs/commerce-admin/config/catalog/inventory#inventory-indexer-settings)が「[!UICONTROL asynchronous]」に設定されている場合は必須です。 |                |                         |                     |
| `inventory.indexer.stock` | + | + | + |
| 在庫の非同期インデックス作成。 管理者システム構成設定で&#x200B;[**[!UICONTROL Stock/Source reindex strategy]**](https://experienceleague.adobe.com/ja/docs/commerce-admin/config/catalog/inventory#inventory-indexer-settings)が「[!UICONTROL asynchronous]」に設定されている場合は必須です。 |                |                         |                     |
| `matchCustomerSegmentProcessor` | + | + |                     |
| 一時データベーステーブルを作成し、各[顧客セグメント &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce-admin/customers/segments/customer-segments)をその中に移動し、セグメント IDに一致するすべてのセグメントを削除し、セグメント IDを指標として使用して顧客セグメントにコピーします。 これらはすべてトランザクション内で実行されるため、何かが失敗した場合は、トランザクションがこの実行前の状態にロールバックされます。 トランザクションの後、消費者は一時テーブルをドロップします。 |                |                         |                     |
| `media.content.synchronization` | + | + | + |
| 商品、カテゴリ、CMS ブロック、CMS ページに割り当てられたメディアへのリンクが、アセットに正しく割り当てられます。 使用されなくなった古いアセットを削除します。 |                |                         |                     |
| `media.gallery.renditions.update` | + | + | + |
| メディアアセットのパスを生成および検証します。 アセットへの絶対パスは、メディアディレクトリ内からサーバー上のどこに配置されているかによって決まります。 画像は（必要に応じて）サイズ変更され、生成されたパス内のメディアディレクトリにコピーされます。 |                |                         |                     |
| `media.gallery.synchronization` | + | + | + |
| 画像ファイルを`media_gallery_asset` データベース テーブルに読み込みます。 |                |                         |                     |
| `media.storage.catalog.image.resize` | + | + | + |
| 非同期[&#x200B; サイズ変更](https://developer.adobe.com/commerce/frontend-core/guide/themes/configure/#resize-catalog-images) カタログ画像。 |                |                         |                     |
| `negotiableQuotePriceUpdate` |                | + |                     |
| 交渉可能な見積の価格を更新します。 管理者システム構成設定で&#x200B;[**[!UICONTROL Quotes]**](https://experienceleague.adobe.com/ja/docs/commerce-admin/b2b/quotes/quotes) オプションが有効になっている場合に必要です。 |                |                         |                     |
| `placeOrderProcessor` | + | + |                     |
| 非同期で[注文を処理](https://developer.adobe.com/commerce/php/module-reference/module-async-order/)します。これにより、注文を受信としてマークし、メッセージキューに配置し、先入れ先出し方式で処理します。 顧客が成功メッセージを表示する前に、バックエンドのプロセスが完了するのを待つ必要がないため、処理可能な注文数を改善するための[&#x200B; ベストプラクティス &#x200B;](../../implementation-playbook/best-practices/maintenance/order-processing-configuration.md)を検討しました。 |                |                         |                     |
| `product_action_attribute.update` | + | + | + |
| 管理者を使用した後、データベース内の製品属性に対する変更を非同期で[更新を行います](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/bulk-product-attribute-update.html?lang=ja)。 |                |                         |                     |
| `product_action_attribute.website.update` | + | + | + |
| 管理者を使用した後、データベース内の特定のストアビューの製品属性に対する変更を[更新を行う](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/bulk-product-attribute-update.html?lang=ja)に非同期で書き込みます。 |                |                         |                     |
| `product_alert` | + | + | + |
| 商品の価格や在庫の変更に関する通知メールを顧客に送信します。 管理者システム構成設定で&#x200B;[**[!UICONTROL Product Alerts]**](https://experienceleague.adobe.com/docs/commerce-admin/inventory/configuration/product-alerts/alert-setup.html?lang=ja) オプションが有効になっている場合に必須です。 |                |                         |                     |
| `purchaseorder.toorder` |                | + |                     |
| 発注を[注文](https://experienceleague.adobe.com/ja/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow#approval-rules)に変換します。 管理者システム構成設定で&#x200B;[**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html?lang=ja) オプションが有効になっている場合に必要です。 |                |                         |                     |
| `purchaseorder.transactional.email` |                | + |                     |
| 発注書の電子メールを送信します。 管理者システム構成設定で&#x200B;[**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html?lang=ja) オプションが有効になっている場合に必要です。 |                |                         |                     |
| `purchaseorder.validation` |                | + |                     |
| 関連する[承認ルール &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce-admin/b2b/purchase-orders/account-dashboard-approval-rules)に対して発注書を検証します。 管理者システム構成設定で&#x200B;[**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html?lang=ja) オプションが有効になっている場合に必要です。 |                |                         |                     |
| `saveConfigProcessor` | + |                         | + |
| 保存ジョブをメッセージキューに配置することで、ストア設定の変更を非同期で保存します。これにより、多数のストアレベル設定を含むデプロイメントのパフォーマンスを向上できます。 [`AsyncConfig`](../../performance/configuration.md#asynchronous-configuration-save) モジュールを使用する必要があります。 |                |                         |                     |
| `sales.rule.update.coupon.usage` | + | + | + |
| 1回限りのクーポンを複数回使用できる問題を回避します。 |                |                         |                     |
| `sharedCatalogUpdateCategoryPermissions` |                | + |                     |
| 共有カタログ カテゴリに割り当てられたカテゴリを更新します。 管理者システム構成設定で&#x200B;[**[!UICONTROL Shared Catalogs]**](https://experienceleague.adobe.com/ja/docs/commerce-admin/b2b/shared-catalogs/catalog-shared) オプションが有効になっている場合に必要です。 |                |                         |                     |
| `sharedCatalogUpdatePrice` |                | + |                     |
| 共有カタログ内の各製品の価格を更新します。 管理者システム構成設定で&#x200B;[**[!UICONTROL Shared Catalogs]**](https://experienceleague.adobe.com/ja/docs/commerce-admin/b2b/shared-catalogs/catalog-shared) オプションが有効になっている場合に必要です。 |                |                         |                     |
| `quoteItemCleaner` | + | + |                     |
| 商品がカタログから削除されたり、買い物かごから削除されたりすると、無効または非アクティブな価格見積もりを削除します。 管理者システム構成設定で&#x200B;[**[!UICONTROL Quotes]**](https://experienceleague.adobe.com/ja/docs/commerce-admin/b2b/quotes/quotes) オプションが有効になっている場合に必要です。 |                |                         |                     |
| `sales.rule.quote.trigger.recollect` | + | + | + |
| アクティブなショッピングカートを更新して、カート価格ルールの変更を反映します。 [**[!UICONTROL Catalog price rules]**](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/catalog-rules/price-rules-catalog.html?lang=ja)の更新時に必須です。 |                |                         |                     |

{style="table-layout:auto"}
