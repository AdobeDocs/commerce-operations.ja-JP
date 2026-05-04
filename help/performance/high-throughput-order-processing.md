---
title: チェックアウトのパフォーマンスのベストプラクティス
description: Adobe Commerceのチェックアウトパフォーマンスのベストプラクティスについて説明します。 導入に関するガイダンスと最適化戦略。
feature: Best Practices, Orders
exl-id: dc2d0399-0d7f-42d8-a6cf-ce126e0b052d
source-git-commit: 5d94ecbe32b94acf9604db9618a9ae6eb1ae04f9
workflow-type: tm+mt
source-wordcount: '1299'
ht-degree: 0%

---


# チェックアウトのパフォーマンスのベストプラクティス

Adobe Commerceの[&#x200B; チェックアウト &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/point-of-purchase/checkout/checkout-process) プロセスは、ストアフロント体験の重要な側面です。 組み込みの[買い物かご](https://experienceleague.adobe.com/en/docs/commerce-admin/start/storefront/storefront#shopping-cart)機能と[&#x200B; チェックアウト &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-admin/start/storefront/storefront#checkout-page)機能に依存しています。

優れた顧客体験を維持するためには、パフォーマンスが重要です。 チェックアウトパフォーマンスを最適化するには、**ハイスループット注文処理**&#x200B;に対して次のオプションを設定します。

- [AsyncOrder](#asynchronous-order-placement)：キューを使用して注文を非同期で処理します。
- [繰延合計計算](#deferred-total-calculation) - チェックアウトが開始されるまで、注文合計の計算を延期します。
- [&#x200B; カート読み込み時の在庫チェック &#x200B;](#disable-inventory-check) - カート商品の在庫検証をスキップすることを選択します。
- [負荷分散](#load-balancing) - MySQL データベースとRedis インスタンスのセカンダリ接続を有効にします。

カートの非同期注文、繰延合計計算、および在庫チェック設定オプションの読み込みはすべて独立して機能します。 3つの機能をすべて同時に使用することも、任意の組み合わせで機能を有効または無効にすることもできます。

>[!NOTE]
>
>カスタム PHP コードを使用して、組み込みのカート機能とチェックアウト機能をカスタマイズしないでください。 潜在的なパフォーマンスの問題に加えて、カスタム PHP コードを使用すると、複雑なアップグレードとメンテナンスの課題が発生する可能性があります。 これらの問題により、総所有コストが増加します。 PHP ベースのカートとチェックアウトのカスタマイズが避けられない場合は、[Adobe Commerce Marketplace](https://commercemarketplace.adobe.com/)承認済みの拡張機能のみを使用してください。 すべてのMarketplace拡張機能は、Adobe Commerceのコーディング標準とベストプラクティスを満たしていることを確認するために[詳細レビュー](https://developer.adobe.com/commerce/marketplace/guides/sellers/extension-quality-program)の対象となります。

## 非同期注文

_非同期注文_ モジュールは、注文を`received`としてマークし、注文をキューに配置し、キューからの注文を先入れ先出し方式で処理する非同期注文の配置を有効にします。 AsyncOrderはデフォルトで&#x200B;**無効**&#x200B;です。

例えば、顧客がショッピングカートに商品を追加し、**[!UICONTROL Proceed to Checkout]**&#x200B;を選択したとします。 **[!UICONTROL Shipping Address]** フォームに入力し、希望する&#x200B;**[!UICONTROL Shipping Method]**&#x200B;を選択し、支払い方法を選択して注文します。 買い物かごがクリアされ、注文は&#x200B;**[!UICONTROL Received]**&#x200B;としてマークされますが、製品数量はまだ調整されておらず、顧客に販売メールも送信されません。 注文は受け取りましたが、注文が完全に処理されていないため、注文の詳細はまだ利用できません。 `placeOrderProcess` コンシューマーが開始されるまでキューに残り、[在庫チェック &#x200B;](#disable-inventory-check)機能（デフォルトで有効）で注文を確認し、次のように注文を更新します。

- **製品が利用可能** – 注文状況が&#x200B;_保留中_&#x200B;に変更され、製品数量が調整され、注文詳細を含む電子メールが顧客に送信され、正常な注文の詳細が&#x200B;**注文と返品** リストに表示され、再注文などの実行可能なオプションが表示されます。
- **在庫切れまたは供給不足** – 注文状況が&#x200B;_拒否_&#x200B;に変更され、製品数量が調整されず、問題に関する注文詳細を含む電子メールが顧客に送信され、拒否された注文詳細が&#x200B;**注文と返品** リストで利用可能になり、実用的なオプションはありません。

コマンドラインインターフェイスを使用して、これらの機能を有効にするか、[_モジュール参照ガイド_](https://developer.adobe.com/commerce/php/module-reference/)で定義されている対応するREADME ファイルに従って`app/etc/env.php` ファイルを編集します。

**AsyncOrder**&#x200B;を有効にするには：

コマンドラインインターフェイスを使用してAsyncOrderを有効にできます。

```shell
bin/magento setup:config:set --checkout-async 1
```

`set` コマンドは、次の内容を`app/etc/env.php` ファイルに書き込みます。

```conf
...
   'checkout' => [
       'async' => 1
   ]
```

_モジュール参照ガイド_&#x200B;の[AsyncOrder](https://developer.adobe.com/commerce/php/module-reference/module-async-order/)を参照してください。

**AsyncOrder**&#x200B;を無効にするには：

>[!WARNING]
>
>AsyncOrder モジュールを無効にする前に、_all_&#x200B;非同期注文プロセスが完了していることを確認する必要があります。

コマンドラインインターフェイスを使用してAsyncOrderを無効にできます。

```shell
bin/magento setup:config:set --checkout-async 0
```

`set` コマンドは、次の内容を`app/etc/env.php` ファイルに書き込みます。

```conf
...
   'checkout' => [
       'async' => 0
   ]
```

### AsyncOrderの互換性

AsyncOrderは、Adobe Commerce機能の一部をサポートしています。

| カテゴリ | サポートされる機能 |
|------------------|--------------------------------------------------------------------------|
| チェックアウトタイプ | OnePage チェックアウト <br>標準チェックアウト <br>B2B交渉可能な見積もり |
| 支払い方法 | 小切手/マネーオーダー<br>代金引換<br>Braintree<br>PayPal PayFlow Pro |
| 配送方法 | すべての配送方法がサポートされています。 |

次の機能は、AsyncOrderでサポートされている&#x200B;**not**&#x200B;ですが、引き続き同期して動作します。

- サポートされている機能リストに含まれていない支払い方法
- 複数アドレスのチェックアウト
- 管理者注文の作成

#### Web API サポート

AsyncOrder モジュールが有効になっている場合、次のREST エンドポイントとGraphQLの変更が非同期で実行されます。

**REST:**

- [`POST /V1/carts/mine/payment-information`](https://adobe-commerce.redoc.ly/2.4.7-admin/tag/cartsminepayment-information#operation/PostV1CartsMinePaymentinformation)
- [`POST /V1/guest-carts/{cartId}/payment-information`](https://adobe-commerce.redoc.ly/2.4.7-admin/tag/guest-cartscartIdpayment-information#operation/PostV1GuestcartsCartIdPaymentinformation)
- [`POST /V1/negotiable-carts/{cartId}/payment-information`](https://adobe-commerce.redoc.ly/2.4.7-admin/tag/negotiable-cartscartIdpayment-information#operation/PostV1NegotiablecartsCartIdPaymentinformation)

**GraphQL:**

- [`placeOrder`](https://developer.adobe.com/commerce/webapi/graphql/schema/cart/mutations/place-order/)
- [`setPaymentMethodAndPlaceOrder`](https://developer.adobe.com/commerce/webapi/graphql/schema/cart/mutations/set-payment-place-order/)

>[!INFO]
>
>GraphQLでは、交渉可能な見積もり注文の非同期的な配置はサポートしていません。

#### 支払い方法の除外

開発者は、特定の支払い方法を`Magento\AsyncOrder\Model\OrderManagement::paymentMethods` アレイに追加することで、非同期注文から明示的に除外できます。 除外された支払い方法を使用する注文は、同期して処理されます。

### 交渉可能な見積もり非同期注文

_交渉可能な見積もり非同期注文_ B2B モジュールを使用すると、`NegotiableQuote`機能に対して注文項目を非同期で保存できます。 AsyncOrderとNegotiableQuoteを有効にする必要があります。

## 繰延合計計算

_繰延合計計算_ モジュールは、ショッピングカートに対して要求されるまで、または最後のチェックアウト手順の間に合計計算を延期することで、チェックアウトプロセスを最適化します。 有効にすると、顧客がショッピングカートに商品を追加すると、小計のみが計算されます。

既定では、繰延合計計算は&#x200B;**無効**&#x200B;です。 コマンドラインインターフェイスを使用して、これらの機能を有効にするか、[_モジュール参照ガイド_](https://developer.adobe.com/commerce/php/module-reference/)で定義されている対応するREADME ファイルに従って`app/etc/env.php` ファイルを編集します。

**DeferredTotalCalculation**&#x200B;を有効にするには：

DeferredTotalCalculationを有効にするには、コマンドライン・インタフェースを使用します。

```shell
bin/magento setup:config:set --deferred-total-calculating 1
```

`set` コマンドは、次の内容を`app/etc/env.php` ファイルに書き込みます。

```conf
...
   'checkout' => [
       'deferred_total_calculating' => 1
   ]
```

**DeferredTotalCalculation**&#x200B;を無効にするには：

DeferredTotalCalculationは、コマンドライン・インタフェースを使用して無効にできます。

```shell
bin/magento setup:config:set --deferred-total-calculating 0
```

`set` コマンドは、次の内容を`app/etc/env.php` ファイルに書き込みます。

```conf
...
   'checkout' => [
       'deferred_total_calculating' => 0
   ]
```

_モジュール参照ガイド_&#x200B;の[DeferredTotalCalculating](https://developer.adobe.com/commerce/php/module-reference/module-deferred-total-calculating/)を参照してください。

### 固定製品税

繰延合計計算が有効になっている場合、製品をショッピングカートに追加した後、固定製品税（FPT）はミニカートの製品価格とカート小計に含まれません。 ミニカートに商品を追加すると、FPTの計算が遅延します。 最終チェックアウトに進むと、FPTがショッピングカートに正しく表示されます。

## 在庫チェックの無効化

「_カートの在庫を有効にする_」グローバル設定は、商品をカートに読み込む際に在庫チェックを実行するかどうかを決定します。 在庫チェックプロセスを無効にすると、特にカート内のバルク商品を処理する場合に、すべてのチェックアウト手順のパフォーマンスが向上します。

無効にすると、商品をショッピングカートに追加する際に在庫チェックが行われません。 この在庫確認をスキップすると、在庫切れのシナリオによって他の種類のエラーが発生する可能性があります。 在庫確認&#x200B;_Always_&#x200B;は、無効になっている場合でも、注文配置ステップで行われます。

**カート読み込み時に在庫チェックを有効にする**&#x200B;は、デフォルトで有効になっています（Yesに設定）。 カートの読み込み時に在庫チェックを無効にするには、管理UI **ストア** > **構成** > **カタログ** > **在庫** > **在庫オプション** セクションで&#x200B;**[!UICONTROL Enable Inventory Check On Cart Load]**&#x200B;を`No`に設定します。 _ユーザーガイド_&#x200B;の「[&#x200B; グローバルオプションの設定](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/configuration/global-options)および[&#x200B; カタログインベントリ &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/guide-overview)」を参照してください。

## 負荷分散

MySQL データベースとRedis インスタンスのセカンダリ接続を有効にすることで、様々なノード間の負荷のバランスを取ることができます。

Adobe Commerceは、複数のデータベースまたはRedis インスタンスを非同期で読み取ることができます。 クラウドインフラストラクチャでCommerceを使用している場合は、`.magento.env.yaml` ファイルの[MYSQL_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#mysql_use_slave_connection)および[REDIS_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#redis_use_slave_connection)の値を編集して、セカンダリ接続を設定できます。 読み取り/書き込みトラフィックを処理する必要があるのは1つのノードのみなので、変数を`true`に設定すると、読み取り専用トラフィック用のセカンダリ接続が作成されます。 値を`false`に設定して、既存の読み取り専用の接続配列を`env.php` ファイルから削除します。

`.magento.env.yaml` ファイルの例：

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    REDIS_USE_SLAVE_CONNECTION: true
```
