---
title: チェックアウトパフォーマンスのベストプラクティス
description: Adobe Commerce サイトでのチェックアウトエクスペリエンスのパフォーマンスを最適化する方法を説明します。
feature: Best Practices, Orders
exl-id: dc2d0399-0d7f-42d8-a6cf-ce126e0b052d
source-git-commit: ee7551374aa6d4ad462dd64ee3d05b934b43ce45
workflow-type: tm+mt
source-wordcount: '1121'
ht-degree: 0%

---


# チェックアウトパフォーマンスのベストプラクティス

Adobe Commerceの [ チェックアウト ](https://experienceleague.adobe.com/ja/docs/commerce-admin/stores-sales/point-of-purchase/checkout/checkout-process) プロセスは、ストアフロントのエクスペリエンスの重要な側面になります。 これは、組み込みの [ 買い物かご ](https://experienceleague.adobe.com/ja/docs/commerce-admin/start/storefront/storefront#shopping-cart) および [ チェックアウト ](https://experienceleague.adobe.com/ja/docs/commerce-admin/start/storefront/storefront#checkout-page) 機能によって異なります。

パフォーマンスは、ユーザーエクスペリエンスを良好に維持するための鍵です。 次のオプションを設定して、チェックアウトのパフォーマンスを最適化できます **高スループットの注文処理**。

- [AsyncOrder](#asynchronous-order-placement) - キューを使用して注文を非同期に処理します。
- [ 遅延合計計算 ](#deferred-total-calculation) - チェックアウトが開始されるまで、受注合計の計算を遅延します。
- [ カート積載時の在庫チェック ](#disable-inventory-check) - カート品目の在庫検証をスキップする場合に選択します。
- [ ロードバランシング ](#load-balancing) - MySQL データベースと Redis インスタンスのセカンダリ接続を有効にします。

「AsyncOrder」、「遅延合計計算」および「買い物かごの積荷に関する在庫チェック」設定オプションはすべて個別に機能します。 3 つの機能をすべて同時に使用することも、任意の組み合わせで有効と無効を切り替えることもできます。

>[!NOTE]
>
>組み込みの買い物かごとチェックアウト機能をカスタマイズする場合は、カスタムの PHP コードを使用しないでください。 パフォーマンスの潜在的な問題に加えて、カスタム PHP コードを使用すると、アップグレードやメンテナンスの複雑な課題が発生する可能性があります。 これらの問題により、TCO （総所有コスト）が増加します。 PHP ベースの買い物かごとチェックアウトのカスタマイズが避けられない場合は、[Adobe Commerce Marketplace](https://commercemarketplace.adobe.com/) 承認済みの拡張機能のみを使用してください。 すべての Marketplace の拡張機能がAdobe Commerceのコーディング標準とベストプラクティスを満たしていることを確認するには、[ 詳細なレビュー ](https://developer.adobe.com/commerce/marketplace/guides/sellers/extension-quality-program/) が必要です。

## 非同期注文の配置

_Async Order_ モジュールは、非同期の注文プレースメントを有効にし、注文を `received` としてマークし、注文をキューに配置し、キューからの注文を先入れ先出し方式で処理します。 AsyncOrder はデフォルトで **無効** です。

例えば、顧客が買い物かごに製品を追加し、**[!UICONTROL Proceed to Checkout]** を選択します。 **[!UICONTROL Shipping Address]** フォームに入力し、希望する **[!UICONTROL Shipping Method]** を選択し、支払い方法を選択して、注文を行います。 買い物かごがクリアされ、注文が **[!UICONTROL Received]** としてマークされますが、製品数量がまだ調整されていないか、顧客に送信される販売メールがありません。 注文は受け取られましたが、注文が完全に処理されていないので、注文の詳細はまだ利用できません。 `placeOrderProcess` のコンシューマーが開始されるまでキューに残り、注文を [ 在庫チェック ](#disable-inventory-check) 機能で検証し（デフォルトで有効）、注文を次のように更新します。

- **製品使用可能** – 注文のステータスが _保留中_ に変わり、製品数量が調整され、注文詳細を記載したメールが顧客に送信され、成功した注文詳細が、並べ替えなどの実用的なオプションを備えた **注文と返品** リストで表示できるようになります。
- **在庫切れまたは供給不足** – 注文のステータスが _却下_ に変わり、製品数量が調整されず、イシューに関する注文詳細を記載したメールが顧客に送信され、却下された注文詳細は **注文と返品** リストで利用できるようになり、実用的なオプションはありません。

コマンドラインインターフェイスを使用してこれらの機能を有効にするか、[_モジュールリファレンスガイド_](https://developer.adobe.com/commerce/php/module-reference/) で定義されている対応する README ファイルに従って `app/etc/env.php` ファイルを編集します。

**AsyncOrder を有効にするには**:

AsyncOrder は、コマンドラインインターフェイスを使用して有効にできます。

```bash
bin/magento setup:config:set --checkout-async 1
```

`set` コマンドは、`app/etc/env.php` ファイルに次の内容を書き込みます。

```conf
...
   'checkout' => [
       'async' => 1
   ]
```

[ モジュールリファレンスガイド ](https://developer.adobe.com/commerce/php/module-reference/module-async-order/) の _AsyncOrder_ を参照してください。

**AsyncOrder を無効にするには**:

>[!WARNING]
>
>AsyncOrder モジュールを無効にする前に、_all_ 非同期の注文プロセスが完了していることを確認する必要があります。

AsyncOrder は、コマンドラインインターフェイスを使用して無効にできます。

```bash
bin/magento setup:config:set --checkout-async 0
```

`set` コマンドは、`app/etc/env.php` ファイルに次の内容を書き込みます。

```conf
...
   'checkout' => [
       'async' => 0
   ]
```

### AsyncOrder の互換性

AsyncOrder では、Adobe Commerce機能の限られたセットをサポートしています。

| カテゴリ | サポートされる機能 |
|------------------|--------------------------------------------------------------------------|
| チェックアウトタイプ | OnePage チェックアウト <br> 標準チェックアウト <br>B2B 譲渡可能見積 |
| 支払い方法 | 小切手/マネーオーダー <br> 代金引換払い <br>Braintree<br>PayPal PayFlow Pro |
| 発送方法 | すべての配送方法に対応しています。 |

次の機能は AsyncOrder ではサポートされていま **んが** 同期的に動作し続けます。

- サポートされている機能リストに含まれていない支払方法
- マルチアドレスチェックアウト
- 管理オーダーの作成

#### Web API サポート

AsyncOrder モジュールが有効になっている場合、次の REST エンドポイントとGraphQLの突然変異は非同期で実行されます。

**REST:**

- [`POST /V1/carts/mine/payment-information`](https://adobe-commerce.redoc.ly/2.4.7-admin/tag/cartsminepayment-information#operation/PostV1CartsMinePaymentinformation)
- [`POST /V1/guest-carts/{cartId}/payment-information`](https://adobe-commerce.redoc.ly/2.4.7-admin/tag/guest-cartscartIdpayment-information#operation/PostV1GuestcartsCartIdPaymentinformation)
- [`POST /V1/negotiable-carts/{cartId}/payment-information`](https://adobe-commerce.redoc.ly/2.4.7-admin/tag/negotiable-cartscartIdpayment-information#operation/PostV1NegotiablecartsCartIdPaymentinformation)

**GraphQL:**

- [`placeOrder`](https://developer.adobe.com/commerce/webapi/graphql/schema/cart/mutations/place-order/)
- [`setPaymentMethodAndPlaceOrder`](https://developer.adobe.com/commerce/webapi/graphql/schema/cart/mutations/set-payment-place-order/)

>[!INFO]
>
>GraphQLでは、交渉可能な見積依頼を非同期で配置することはサポートされていません。

#### 支払方法の除外

開発者は、特定の支払いメソッドを `Magento\AsyncOrder\Model\OrderManagement::paymentMethods` 配列に追加することで、非同期の注文プレースメントから明示的に除外できます。 除外された支払方法を使用する注文は、同期的に処理されます。

### 交渉可能な見積もり非同期注文

_Negotiable Quote Async Order_ B2B モジュールを使用すると、`NegotiableQuote` 機能のために注文項目を非同期で保存できます。 AsyncOrder および NegotiableQuote を有効にする必要があります。

## 繰延合計計算

_遅延合計計算_ モジュールは、買い物かごに対してリクエストされるまで、または最終的なチェックアウト手順で合計計算を延期することで、チェックアウトプロセスを最適化します。 有効になっている場合、顧客が買い物かごに商品を追加した際に計算されるのは小計のみです。

遅延合計計算は、デフォルトで **無効** になっています。 コマンドラインインターフェイスを使用してこれらの機能を有効にするか、[_モジュールリファレンスガイド_](https://developer.adobe.com/commerce/php/module-reference/) で定義されている対応する README ファイルに従って `app/etc/env.php` ファイルを編集します。

**DeferredTotalCalculation を使用可能にする手順は、次のとおりです**。

DeferredTotalCalculation は、コマンド・ライン・インタフェースを使用して有効にできます。

```bash
bin/magento setup:config:set --deferred-total-calculating 1
```

`set` コマンドは、`app/etc/env.php` ファイルに次の内容を書き込みます。

```conf
...
   'checkout' => [
       'deferred_total_calculating' => 1
   ]
```

**DeferredTotalCalculation を使用不可にする手順は、次のとおりです**。

DeferredTotalCalculation は、コマンド・ライン・インタフェースを使用して無効にできます。

```bash
bin/magento setup:config:set --deferred-total-calculating 0
```

`set` コマンドは、`app/etc/env.php` ファイルに次の内容を書き込みます。

```conf
...
   'checkout' => [
       'deferred_total_calculating' => 0
   ]
```

[Module Reference Guide](https://developer.adobe.com/commerce/php/module-reference/module-deferred-total-calculating/) の _DeferredTotalCalculating_ を参照してください。

### 固定製品税

繰延合計計算が有効化されている場合、商品を買い物かごに追加した後、固定製品税（FPT）は商品価格とミニ買い物かごの小計に含まれません。 FPT 計算は、商品をミニ買い物かごに追加する際に延期されます。 最終チェックアウトに進んだ後、FPT は買い物かごに正しく表示されます。

## 在庫確認を無効にする

_買い物かごへの読み込み時に在庫を有効にする_ グローバル設定により、商品を買い物かごに読み込む際に在庫チェックを実行するかどうかが決まります。 在庫確認プロセスを無効にすると、すべてのチェックアウトステップのパフォーマンスが向上します。特に、買い物かごで一括製品を処理する場合に効果があります。

無効にすると、商品を買い物かごに追加する際に在庫チェックが行われません。 この在庫確認をスキップした場合、在庫切れのシナリオによっては、他のタイプのエラーがスローされる可能性があります。 無効の場合でも、注文配置ステップで在庫チェック _常に_ が行われます。

**買い物かごへの積載時に在庫チェックを有効化** は、デフォルトで有効（「Yes」に設定）になっています。 カートを読み込む際に在庫チェックを無効にするには、管理 UI **ストア**/**設定**/**カタログ**/**在庫**/**在庫オプション** セクションで、**[!UICONTROL Enable Inventory Check On Cart Load]** を `No` に設定します。 [ ユーザーガイド ](https://experienceleague.adobe.com/ja/docs/commerce-admin/inventory/configuration/global-options) の [ グローバルオプションの設定 ](https://experienceleague.adobe.com/ja/docs/commerce-admin/inventory/guide-overview) および _カタログ在庫_ を参照してください。

## ロードバランシング

MySQL データベースと Redis インスタンスのセカンダリ接続を有効にすることで、異なるノード間で負荷を分散させることができます。

Adobe Commerceは、複数のデータベースまたは Redis インスタンスを非同期で読み取ることができます。 クラウドインフラストラクチャー上でCommerceを使用している場合は、`.magento.env.yaml` ファイル内の [MYSQL_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/ja/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#mysql_use_slave_connection) と [REDIS_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/ja/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#redis_use_slave_connection) の値を編集することで、セカンダリ接続を設定できます。 読み取り/書き込みトラフィックを処理する必要があるのは 1 つのノードのみです。そのため、変数を `true` に設定すると、読み取り専用トラフィック用のセカンダリ接続が作成されます。 値を `false` に設定して、既存の読み取り専用接続配列を `env.php` ファイルから削除します。

`.magento.env.yaml` ファイルの例：

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    REDIS_USE_SLAVE_CONNECTION: true
```
