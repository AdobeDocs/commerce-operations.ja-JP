---
title: チェックアウトパフォーマンスのベストプラクティス
description: Adobe Commerce サイトでのチェックアウトエクスペリエンスのパフォーマンスを最適化する方法を説明します。
feature: Best Practices, Orders
exl-id: dc2d0399-0d7f-42d8-a6cf-ce126e0b052d
source-git-commit: e4c1832076bb81cd3e70ff279a6921ffb29ea631
workflow-type: tm+mt
source-wordcount: '1132'
ht-degree: 0%

---


# チェックアウトパフォーマンスのベストプラクティス

この [チェックアウト](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/point-of-purchase/checkout/checkout-process) Adobe Commerceのプロセスは、ストアフロントのエクスペリエンスの重要な側面です。 ビルトインを利用します [カート](https://experienceleague.adobe.com/en/docs/commerce-admin/start/storefront/storefront#shopping-cart) および [チェックアウト](https://experienceleague.adobe.com/en/docs/commerce-admin/start/storefront/storefront#checkout-page) の機能。

パフォーマンスは、ユーザーエクスペリエンスを良好に維持するための鍵です。 をレビュー [パフォーマンスベンチマークサマリ](../implementation-playbook/infrastructure/performance/benchmarks.md) にアクセスして、パフォーマンスの期待の詳細を確認します。 以下のオプションを設定して、チェックアウトパフォーマンスを最適化できます **高スループットのオーダー処理**:

- [AsyncOrder](#asynchronous-order-placement)- キューを使用して注文を非同期で処理します。
- [繰延合計計算](#deferred-total-calculation)- チェックアウトが開始されるまで、注文合計の計算を延期します。
- [買い物かごの積載時の在庫確認](#disable-inventory-check) – 買い物かご品目の在庫検証をスキップする場合に選択します。
- [ロードバランシング](#load-balancing)- MySQL データベースと Redis インスタンスのセカンダリ接続を有効にします。

「AsyncOrder」、「遅延合計計算」および「買い物かごの積荷に関する在庫チェック」設定オプションはすべて個別に機能します。 3 つの機能をすべて同時に使用することも、任意の組み合わせで有効と無効を切り替えることもできます。

>[!NOTE]
>
>組み込みの買い物かごとチェックアウト機能をカスタマイズする場合は、カスタムの PHP コードを使用しないでください。 パフォーマンスの潜在的な問題に加えて、カスタム PHP コードを使用すると、アップグレードやメンテナンスの複雑な課題が発生する可能性があります。 これらの問題により、TCO （総所有コスト）が増加します。 PHP ベースの買い物かごとチェックアウトのカスタマイズが避けられない場合は、を使用します。 [Adobe Commerce Marketplace](https://commercemarketplace.adobe.com/) – 承認された拡張機能のみ。 すべての Marketplace 拡張機能は次の対象です [広範な見直し](https://developer.adobe.com/commerce/marketplace/guides/sellers/extension-quality-program/) Adobe Commerceのコーディング標準とベストプラクティスを満たしていることを確認します。

## 非同期注文の配置

この _非同期順序_ モジュールは、非同期の注文プレースメントを有効にし、注文を `received`、注文をキューに入れ、先入れ先出しでキューからの注文を処理します。 AsyncOrder は **disabled** デフォルトでは。

例えば、顧客が買い物かごに製品を追加して、次を選択します。 **[!UICONTROL Proceed to Checkout]**. 次の項目を記入します **[!UICONTROL Shipping Address]** フォーム、優先項目を選択 **[!UICONTROL Shipping Method]**&#x200B;で、支払い方法を選択し、注文します。 買い物かごがクリアされ、注文はとしてマークされます **[!UICONTROL Received]**&#x200B;ただし、製品数量はまだ調整されておらず、顧客に送信される販売メールでもありません。 注文は受け取られましたが、注文が完全に処理されていないので、注文の詳細はまだ利用できません。 この値は、 `placeOrderProcess` コンシューマーが開始し、で注文を確認します [在庫確認](#disable-inventory-check) 機能（デフォルトで有効）が有効になり、注文が次のように更新されます。

- **使用可能な製品** – 注文のステータスが _保留中_、製品数量が調整され、注文の詳細を記載したメールが顧客に送信され、成功した注文の詳細がで表示できるようになります **注文と返品** 並べ替えなど、アクションにつながるオプションを含むリスト。
- **製品の在庫切れまたは供給不足** – 注文のステータスが _却下_、製品数量が調整されず、イシューに関する注文詳細を記載したメールが顧客に送信され、却下された注文の詳細がで利用できるようになります **注文と返品** アクションにつながるオプションのないリスト。

コマンドラインインターフェイスを使用してこれらの機能を有効にするか、 `app/etc/env.php` で定義された、対応する README ファイルに従ったファイル [_モジュールリファレンスガイド_](https://developer.adobe.com/commerce/php/module-reference/).

**AsyncOrder を有効にするには**:

AsyncOrder は、コマンドラインインターフェイスを使用して有効にできます。

```bash
bin/magento setup:config:set --checkout-async 1
```

この `set` コマンドは、次の内容を `app/etc/env.php` ファイル：

```conf
...
   'checkout' => [
       'async' => 1
   ]
```

参照： [AsyncOrder](https://developer.adobe.com/commerce/php/module-reference/module-async-order/) が含まれる _モジュールリファレンスガイド_.

**AsyncOrder を無効にするには**:

>[!WARNING]
>
>AsyncOrder モジュールを無効にする前に、次のことを確認する必要があります _all_ 非同期注文プロセスが完了しました。

AsyncOrder は、コマンドラインインターフェイスを使用して無効にできます。

```bash
bin/magento setup:config:set --checkout-async 0
```

この `set` コマンドは、次の内容を `app/etc/env.php` ファイル：

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
| チェックアウトタイプ | 1 ページ チェックアウト<br>標準チェックアウト<br>B2B 譲渡可能な見積もり |
| 支払い方法 | 小切手/送金<br>代金引換払い<br>Braintree<br>PayPal PayFlow Pro |
| 発送方法 | すべての配送方法に対応しています。 |

次の機能があります **ではない** asyncOrder でサポートされていますが、同期的に動作し続けます。

- サポートされている機能リストに含まれていない支払方法
- マルチアドレスチェックアウト
- 管理オーダーの作成

#### Web API サポート

AsyncOrder モジュールが有効になっている場合、次の REST エンドポイントとGraphQLの突然変異は非同期で実行されます。

**残り：**

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

開発者は、特定の支払いメソッドをに追加することで、非同期の注文プレースメントから明示的に除外できます。 `Magento\AsyncOrder\Model\OrderManagement::paymentMethods` 配列。 除外された支払方法を使用する注文は、同期的に処理されます。

### 交渉可能な見積もり非同期注文

この _交渉可能な見積もり非同期注文_ B2B モジュールを使用すると、 `NegotiableQuote` 機能。 AsyncOrder および NegotiableQuote を有効にする必要があります。

## 繰延合計計算

この _繰延合計計算_ モジュールは、買い物かごにリクエストされるまで、または最終的なチェックアウト手順で、合計計算を延期することで、チェックアウトプロセスを最適化します。 有効になっている場合、顧客が買い物かごに商品を追加した際に計算されるのは小計のみです。

遅延合計計算： **disabled** デフォルトでは。 コマンドラインインターフェイスを使用してこれらの機能を有効にするか、 `app/etc/env.php` で定義された、対応する README ファイルに従ったファイル [_モジュールリファレンスガイド_](https://developer.adobe.com/commerce/php/module-reference/).

**DeferredTotalCalculation を使用可能にする手順は、次のとおりです**:

DeferredTotalCalculation は、コマンド・ライン・インタフェースを使用して有効にできます。

```bash
bin/magento setup:config:set --deferred-total-calculating 1
```

この `set` コマンドは、次の内容を `app/etc/env.php` ファイル：

```conf
...
   'checkout' => [
       'deferred_total_calculating' => 1
   ]
```

**DeferredTotalCalculation を使用不可にする手順は、次のとおりです**:

DeferredTotalCalculation は、コマンド・ライン・インタフェースを使用して無効にできます。

```bash
bin/magento setup:config:set --deferred-total-calculating 0
```

この `set` コマンドは、次の内容を `app/etc/env.php` ファイル：

```conf
...
   'checkout' => [
       'deferred_total_calculating' => 0
   ]
```

参照： [DeferredTotalCalculating](https://developer.adobe.com/commerce/php/module-reference/module-deferred-total-calculating/) が含まれる _モジュールリファレンスガイド_.

### 固定製品税

繰延合計計算が有効化されている場合、商品を買い物かごに追加した後、固定製品税（FPT）は商品価格とミニ買い物かごの小計に含まれません。 FPT 計算は、商品をミニ買い物かごに追加する際に延期されます。 最終チェックアウトに進んだ後、FPT は買い物かごに正しく表示されます。

## 在庫確認を無効にする

この _カート読み込み時に在庫を有効にする_ グローバル設定は、買い物かごに商品を読み込む際に在庫チェックを実行するかどうかを決定します。 在庫確認プロセスを無効にすると、すべてのチェックアウトステップのパフォーマンスが向上します。特に、買い物かごで一括製品を処理する場合に効果があります。

無効にすると、商品を買い物かごに追加する際に在庫チェックが行われません。 この在庫確認をスキップした場合、在庫切れのシナリオによっては、他のタイプのエラーがスローされる可能性があります。 在庫検査 _常に_ 無効な場合でも、注文配置ステップで発生します。

**買い物かごへの積載時に在庫チェックを有効にする** は、デフォルトで有効になっています（「はい」に設定されています）。 買い物かごを読み込む際に在庫チェックを無効にするには、次を設定します **[!UICONTROL Enable Inventory Check On Cart Load]** 対象： `No` 管理 UI 内 **ストア** > **設定** > **カタログ** > **在庫** > **在庫オプション** セクション。 参照： [グローバルオプションの設定](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/configuration/global-options) および [カタログ在庫](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/guide-overview) が含まれる _ユーザーガイド_.

## ロードバランシング

MySQL データベースと Redis インスタンスのセカンダリ接続を有効にすることで、異なるノード間で負荷を分散させることができます。

Adobe Commerceは、複数のデータベースまたは Redis インスタンスを非同期で読み取ることができます。 クラウドインフラストラクチャでCommerceを使用している場合は、を編集してセカンダリ接続を設定できます。 [MYSQL_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#mysql_use_slave_connection) および [REDIS_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#redis_use_slave_connection) の値 `.magento.env.yaml` ファイル。 読み取り/書き込みトラフィックを処理する必要があるのは 1 つのノードのみなので、変数をに設定します。 `true` その結果、読み取り専用トラフィック用のセカンダリ接続が作成されます。 値をに設定します。 `false` 既存の読み取り専用接続配列を `env.php` ファイル。

の例 `.magento.env.yaml` ファイル：

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    REDIS_USE_SLAVE_CONNECTION: true
```
