---
title: 高スループットの注文処理
description: Adobe CommerceまたはMagento Open Sourceのデプロイメントに合わせて、注文の配置とチェックアウトエクスペリエンスを最適化します。
source-git-commit: 6afdb941ce3753af02bde3dddd4e66414f488957
workflow-type: tm+mt
source-wordcount: '1046'
ht-degree: 0%

---


# 高スループットの注文処理

次のモジュールセットを **高スループット順序処理**:

- [AsyncOrder](#asynchronous-order-placement) — キューを使用してオーダーを非同期的に処理します。
- [延期合計計算](#deferred-total-calculation) — チェックアウトが開始されるまで、注文の合計の計算を遅延します。
- [見積もり読み込み時の在庫チェック](#disable-inventory-check) — 買い物かご項目の在庫検証をスキップする場合に選択します。

すべてのフィーチャー（AsyncOrder、遅延合計計算、および在庫チェック）は、独立して動作します。 3 つの機能をすべて同時に使用することも、任意の組み合わせで機能を有効/無効にすることもできます。

## 非同期の注文プレースメント

この _非同期注文_ モジュールは、非同期の注文配置を有効にし、順序を `received`を指定すると、順序がキューに格納され、キュー内の順序が先に出る順に処理されます。 AsyncOrder は **無効** デフォルトでは。

例えば、顧客が買い物かごに製品を追加し、「 」を選択したとします。 **[!UICONTROL Proceed to Checkout]**. 彼らは、 **[!UICONTROL Shipping Address]** フォーム、希望のフォームを選択 **[!UICONTROL Shipping Method]**、支払い方法を選択し、注文をおこないます。 買い物かごがクリアされ、注文は次のマークが付けられます **[!UICONTROL Received]**」と表示される場合は、製品の数量がまだ調整されておらず、顧客に送信されるセールスメールもありません。 注文を受け取りましたが、注文が完全に処理されていないので、注文の詳細はまだ利用できません。 このイベントは、 `placeOrderProcess` 消費者が開始し、 [在庫チェック](#disable-inventory-check) 機能（デフォルトで有効）を使用し、次のように順序を更新します。

- **使用可能な製品** — 注文ステータスが _保留中_&#x200B;製品数が調整され、注文の詳細が記載された E メールが顧客に送信され、成功した注文の詳細が **注文件数と返品数** 並べ替えなど、実行可能なオプションを含むリスト。
- **在庫切れまたは供給不足の製品** — 注文ステータスが _却下_」をクリックすると、製品数が調整されず、問題に関する注文の詳細が記載された E メールが顧客に送信され、却下された注文の詳細が **注文件数と返品数** リストに追加されます。

コマンドラインインターフェイスを使用してこれらの機能を有効にするか、 `app/etc/env.php` ファイルを、 [_モジュールリファレンスガイド_][mrg].

**AsyncOrder を有効にするには**:

AsyncOrder は、コマンドラインインターフェイスを使用して有効にすることができます。

```bash
bin/magento setup:config:set --checkout-async 1
```

この `set` コマンドは次の内容を `app/etc/env.php` ファイル：

```conf
...
   'checkout' => [
       'async' => 1
   ]
```

詳しくは、 [AsyncOrder] 内 _モジュールリファレンスガイド_.

**AsyncOrder を無効にするには**:

>[!WARNING]
>
>AsyncOrder モジュールを無効にする前に、 _すべて_ 非同期の注文プロセスが完了しました。

AsyncOrder は、コマンドラインインターフェイスを使用して無効にできます。

```bash
bin/magento setup:config:set --checkout-async 0
```

この `set` コマンドは次の内容を `app/etc/env.php` ファイル：

```conf
...
   'checkout' => [
       'async' => 0
   ]
```

### AsyncOrder の互換性

AsyncOrder は、限られた [!DNL Commerce] 機能。

| カテゴリ | サポートされる機能 |
|---------------- | -----------------------|
| チェックアウトタイプ | OnePage チェックアウト<br>標準チェックアウト<br>B2B 交渉可能見積書 |
| 支払い方法 | 小切手/送金<br>配送中の現金<br>Braintree<br>PayPal PayFlow Pro |
| 発送方法 | すべての発送方法がサポートされています。 |

次の機能があります。 **not** AsyncOrder でサポートされますが、同期的に動作し続けます。

- サポート対象の機能リストに含まれていない支払い方法
- 複数アドレスのチェックアウト
- 管理者の注文作成

#### Web API のサポート

AsyncOrder モジュールを有効にすると、次の REST エンドポイントと GraphQL 突然変異が非同期で実行されます。

**REST:**

- `POST /V1/carts/mine/payment-information`
- `POST /V1/guest-carts/:cartId/payment-information`
- `POST /V1/negotiable-carts/:cartId/payment-information`

**GraphQL:**

- [`placeOrder`](https://devdocs.magento.com/guides/v2.4/graphql/mutations/place-order.html)
- [`setPaymentMethodAndPlaceOrder`](https://devdocs.magento.com/guides/v2.4/graphql/mutations/set-payment-place-order.html)

>[!INFO]
>
>GraphQL は、非同期的に交渉可能な見積もり注文を配置することをサポートしていません。

#### 支払い方法の除外

開発者は、特定の支払い方法を非同期注文配置から明示的に除外できます。その際、 `Magento\AsyncOrder\Model\OrderManagement::paymentMethods` 配列。 除外された支払い方法を使用する注文は、同期的に処理されます。

### 交渉可能見積非同期注文

この _交渉可能見積非同期注文_ B2B モジュールを使用すると、 `NegotiableQuote` 機能。 AsyncOrder と NegotiableQuote を有効にする必要があります。

## 延期合計計算

この _延期合計計算_ モジュールは、買い物かごに対して要求されるまで、または最終的なチェックアウト手順の間に合計計算を延期することで、チェックアウトプロセスを最適化します。 有効にすると、顧客が買い物かごに商品を追加したときの小計のみが計算されます。

DeferredTotalCalculation は次のとおりです **無効** デフォルトでは。 コマンドラインインターフェイスを使用してこれらの機能を有効にするか、 `app/etc/env.php` ファイルを、 [_モジュールリファレンスガイド_][mrg].

**DeferredTotalCalculation を有効にするには**:

DeferredTotalCalculation は、コマンドラインインターフェイスを使用して有効にできます。

```bash
bin/magento setup:config:set --deferred-total-calculating 1
```

この `set` コマンドは次の内容を `app/etc/env.php` ファイル：

```conf
...
   'checkout' => [
       'deferred_total_calculating' => 1
   ]
```

**DeferredTotalCalculation を無効にするには**:

DeferredTotalCalculation は、コマンドラインインターフェイスを使用して無効にできます。

```bash
bin/magento setup:config:set --deferred-total-calculating 0
```

この `set` コマンドは次の内容を `app/etc/env.php` ファイル：

```conf
...
   'checkout' => [
       'deferred_total_calculating' => 0
   ]
```

詳しくは、 [DeferredTotalCalculting] 内 _モジュールリファレンスガイド_.

### 固定製品税

DeferredTotalCalculation が有効な場合、製品を買い物かごに追加した後、固定製品税 (FPT) は、ミニ買い物かごの製品価格および買い物かごの小計に含まれません。 ミニ買い物かごに商品を追加する際に、FPT の計算が遅延されます。 最終的なチェックアウトに進むと、FPT が買い物かごに正しく表示されます。

## 在庫チェックを無効にする

この _買い物かごへの読み込みの在庫を有効にする_ グローバル設定は、買い物かごに商品を読み込む際に在庫チェックを実行するかどうかを決定します。 在庫チェックプロセスを無効にすると、特に買い物かご内の一括製品を処理する際の、すべてのチェックアウトステップのパフォーマンスが向上します。

無効にした場合、製品を買い物かごに追加する際に在庫チェックが実行されません。 この在庫チェックをスキップした場合、在庫切れのシナリオによっては他のタイプのエラーが発生する場合があります。 在庫チェック _常に_ は、無効な場合でも、注文の配置手順で発生します。

**買い物かごへの読み込み時の在庫の確認を有効にする** デフォルトでは有効（はいに設定）です。 買い物かごの読み込み時に在庫チェックを無効にするには、 **[!UICONTROL Enable Inventory Check On Cart Load]** から `No` 管理 UI で **ストア** > **設定** > **カタログ** > **在庫** > **在庫オプション** 」セクションに入力します。 詳しくは、 [グローバルオプションの設定][global] および [カタログ在庫][inventory] 内 _ユーザーガイド_.

## 負荷分散

MySQL データベースと Redis インスタンスのセカンダリ接続を有効にすると、異なるノード間で負荷を分散するのに役立ちます。

Adobe Commerceは、複数のデータベースまたは Redis インスタンスを非同期で読み取ることができます。 クラウドインフラストラクチャで Commerce を使用している場合は、 [MYSQL_USE_SLAVE_CONNECTION](https://devdocs.magento.com/cloud/env/variables-deploy.html#mysql_use_slave_connection) および [REDIS_USE_SLAVE_CONNECTION](https://devdocs.magento.com/cloud/env/variables-deploy.html#redis_use_slave_connection) 値 `.magento.env.yaml` ファイル。 読み取り/書き込みトラフィックを処理する必要があるノードは 1 つだけなので、変数を `true` その結果、読み取り専用トラフィックのセカンダリ接続が作成されます。 値を `false` 既存の読み取り専用接続配列を `env.php` ファイル。

例 `.magento.env.yaml` ファイル：

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    REDIS_USE_SLAVE_CONNECTION: true
```

<!-- link definitions -->

[Apply patches]: https://devdocs.magento.com/cloud/project/project-patch.html
[global]: https://docs.magento.com/user-guide/catalog/inventory-options-global.html
[inventory]: https://docs.magento.com/user-guide/configuration/catalog/inventory.html
[Install extensions]: https://devdocs.magento.com/extensions/install/
[cloud-extensions]: https://devdocs.magento.com/cloud/howtos/install-components.html

[mrg]: https://developer.adobe.com/commerce/php/module-reference/
[AsyncOrder]: https://devdocs.magento.com/guides/v2.4/mrg/module-async-order.html
[DeferredTotalCalculting]: https://devdocs.magento.com/guides/v2.4/mrg/module-deferred-total-calculating.html
[NegotiableQuoteAsyncOrder]: https://devdocs.magento.com/guides/v2.4/mrg/module-negotiable-quote-async-order.html
