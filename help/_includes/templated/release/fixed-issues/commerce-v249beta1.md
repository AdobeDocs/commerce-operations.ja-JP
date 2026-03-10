---
source-git-commit: 0a22d08d6965c6abc288a1a171d25f4ff8bbd7ce
workflow-type: tm+mt
source-wordcount: '26969'
ht-degree: 0%

---
# Adobe Commerceで修正された問題（v2.4.9-beta1）

## v2.4.9-beta1 の問題を修正しました

Adobe Commerce 2.4.9-beta1 コアコードの 560 の問題を修正しました。 このリリースで修正された問題の一部を以下に示します。

### API

#### 今日までの特別価格は applySpecialPrice で誤って検証されています

システムは特別価格に関して正常に機能しており、製品の特別価格は、管理者または REST API によるサードパーティシステムで設定した日付に期限切れになります

_AC-13130 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39169) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/39690)_

#### [WebAPI]WebAPI paradox を使用した顧客のメール確認

確認前にトークンを必要とする認証パラドックスが原因で、お客様が WebAPI 経由でアカウントをアクティブ化できない問題を修正しました。 この更新により、未確認のお客様は API を使用してアカウントを正常にアクティブ化でき、一貫性のある機能的な確認フローを確保できます。

_AC-13281 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39255) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/c95ed7d7)_

#### 支払い情報のみを使用して REST API を介して注文を作成する場合の、管理ダッシュボードでの請求先住所の欠落エラー

請求先住所のない API を使用して注文を作成すると、管理ダッシュボードがクラッシュする可能性がある問題を修正しました。
現在は、請求先住所のない注文は制限され、作成されなくなります。

_AC-14049 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39651) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/36d4d6fb)_

#### Rest API での買い物かごへの製品追加の問題

特定の web サイトに割り当てられていない製品を引き続き買い物かごに追加して購入できる問題を修正しました。
「追加しようとしている製品は利用できません」というエラーメッセージが表示されます。

_AC-15054 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/40029) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/f5cc09fc)_

#### ストアラベルを更新すると属性オプションラベルが上書きされる

REST API を使用して複数選択の製品属性を更新すると、すべての store_labels が上書きされ、既存のストア固有のラベルが削除される問題を修正しました。
現在は、デフォルトのストア表示ラベルを更新する際に、Magentoは、提供されたラベルを完全に上書きするのではなく、既存のラベルと結合します。
これにより、他のストア表示のストア固有のラベルが更新後もそのままの状態で保持されます。

_AC-15208 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/40093) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/36d4d6fb)_

#### [ 問題 ] 明確になった属性オプションはすでに存在する応答です

「同じファイルが既に存在する場合は新しいファイル名を取得する」という不自然なフレーズを、文法的に正しいより明確なバージョンに置き換えるようになりました。 これにより、読みやすさとユーザーの理解が向上します。
属性オプション応答も同じです。

_AC-15473 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39943) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/39941)_

#### /V1/products/special-price API エンドポイントの内部サーバーエラー

/V1/products/special-price および関連する価格 API への不正なリクエストが、null の TypeError によって 500 内部サーバーエラーを返した問題を修正しました。
現在は、API が入力を適切に検証し、無効なペイロードに対して 400 エラーを返すので、エラー処理と API の信頼性が向上しています。

_AC-6419 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/35934) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/a7ef6300)_

#### `/V1/order/&lbrace;orderId&rbrace;/ship` API エンドポイントの内部サーバーエラー

システムは、API エンドポイントの内部サーバーエラー `/V1/order/{orderId}/ship` 修正し、リクエストの形式が正しくないので 400 エラーを返すようになりました。

_AC-6420 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/35931) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/38282)_

#### /V1/creditmemo API エンドポイントの内部サーバーエラー

/V1/creditmemo API への形式の正しくないリクエストで 500 内部サーバーエラーが返される問題を修正しました。
現在は、API はリクエストを適切に検証し、無効なペイロードに対して 400 エラーを返し、エラー処理と安定性を向上させます。

_AC-6422 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/35924) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/a7ef6300)_

#### Rest API とMagento バックエンドでは、新しい属性を作成する際に attribute_code に異なる検証方法を使用します

Magento管理者が attribute_code で大文字を使用できても、製品属性の作成時に REST API が大文字を拒否するという不整合を修正しました。
現在は、管理者と REST API の両方が同じ検証に従うので、大文字を使用した属性を正常に作成できます。

_AC-6660 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/33138) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/8670a2b4)_

#### REST API を使用した属性の作成と更新の間で異なる検証

REST API を使用した属性の作成中に検証の不一致により、誤った backend_type が割り当てられる問題を修正しました。
現在は、有効な場合は正しいバックエンドタイプが設定され、無効な値の場合は例外がスローされるか、指定されていない場合は適切にフォールバックされるので、属性の一貫性が確保されます。

_AC-6885 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/36327) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/64823f95)_

#### リクエスト本文またはパラメーターの形式が正しくないため、「内部サーバーエラー」が発生する

正しくない形式のリクエスト本文またはパラメーターが、明確な「400 無効なリクエスト」応答を返すようになりました。
以前は、形式の正しくないリクエスト本文やパラメーターを様々な REST API エンドポイント（/V1/carts/search、/V1/orders、/V1/products など）に送信すると、一般的な「内部サーバーエラー」（500）が発生し、入力の問題の診断が困難でした。
Adobe Commerceは「400 件の無効なリクエスト」応答を返し、リクエストが無効な場合にはより明確なフィードバックを提供するようになりました。

_AC-746 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/32784) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/f1adb44e)_

#### `/orders` （または `/orders/:id`）エンドポイントに「state」フィールドと「status」フィールドがありません

データベース値が null の場合に、`/orders` および `/orders/{id}` API 応答で状態フィールドとステータスフィールドが省略される問題を修正しました。
現在は、両方のフィールドが一貫して応答で返されるようになり、API ドキュメントへの準拠を確保し、データの信頼性を向上させます。

_AC-9244 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/37807) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/01cee3c3)_

#### async.magento.configurableproduct.api.optionrepositoryinterface.save.post の非同期一括操作はオープン状態のままになります

リクエスト本文が配列でない場合、Bulk API エンドポイントはエラーをスローするようになりました。そのため、一括項目キーは 0 から始まる連続数である必要があります。 以前は、一括要求で送信された任意の項目キーが原因で、一括項目ステータスが更新されませんでした。

_ACP2E-3544 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/9608ca21)_

#### [CLOUD] is_subscribed 値に関する API REST のバグで、searchCriteria を使用して現在のストアから考慮されていないもの

API REST カスタマークエリは、searchCriteria を使用して、正しいストアから正しい「is_subscribed」値を取得します
以前は、API REST カスタマークエリは、is_subscribed&quot;値を取得する際に保存を考慮していませんでした。

_ACP2E-3621 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/9608ca21)_

#### async.operations.all は、1 つの SKU に対して複数のエントリを作成できます

同じ製品を保存および更新する同時リクエストがシリアル化され、データの不整合や製品の重複を引き起こす競合状態を防ぎます

_ACP2E-3744 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/520f9e30)_

#### 注文「base_row_total」と「row_total」は、REST API 応答で単一項目価格を表示します

複数の同じ項目が注文された場合の、注文詳細の REST API 応答に、「base_row_total」属性と「row_total」属性の正しい値が含まれるようになりました

_ACP2E-3874 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/4ca73607)_

#### REST API エンドポイント export-stock-salable-qty が間違った項目を返す total_count

total_count が誤ってページサイズに制限されていた、在庫書き出し在庫販売可能数量 API のページネーションの問題を修正しました。 以前は、page_size=5 などのページネーションパラメーターを使用して/rest/all/V1/inventory/export-stock-salable-qty/website/base エンドポイントを使用する場合、応答内の total_count フィールドは、検索条件に一致する実際の製品総数ではなく 5 を返していました。 この修正後、total_count フィールドに、page_size パラメーターに関係なく使用可能な製品の合計数が正しく反映されるようになり、すべてのMagento REST API エンドポイントで一貫したページネーション動作が保証されます。

_ACP2E-4086 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/inventory/commit/5632fb5e)_

#### 買い物かご項目 REST API のカスタムオプション ID の検証の問題。

REST API V1/guest-carts/&lt;cartId>/items/および V1/carts/mine/items/は、「product_options.extension_attributes.custom_options」を検証するようになりました。*.option_id」に設定し、買い物かごの商品 SKU の有効な option_id を参照するようにします。 以前は、このパラメーターは処理され、検証なしでデータベースに保存されていました。

_ACP2E-4138 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/a1c57b2e)_

#### 買い物かごから商品を取得してストアヘッダーの言語を変更しても変更されない場合

GraphQL customerCart クエリは、ストアヘッダー値に従って製品属性値を返すようになりました。 以前は、GraphQLを使用して買い物かごから商品を取得する際にストアヘッダーの言語を変更しても、更新された言語が反映されなかったので、ローカリゼーションの一貫性が失われていました。

_ACP2E-4227 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/6e134409)_

#### ギフトカード製品で REST API /メディアエンドポイントが失敗する – 「製品は保存できません」を返します

修正前は、グローバルスコープに金額を含まないギフトカード製品を作成することができました。 この修正により、グローバルスコープで金額を確認する検証が追加されました。

_ACP2E-4395 - [GitHub の問題 &#x200B;](https://mcstaging.panini.it/shp_ita_it/)_

### API、買い物かご、チェックアウト

#### 配送情報の場合、REST API を使用して、サーバーサイドの検証が機能しません

REST API で、配送先住所情報の検証が管理バックエンドで定義された属性設定に従わなかった問題を修正しました。 これで、設定された設定に従って検証が正しく行われます。

_ACP2E-4156 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/45cbf9b6)_

### API、カタログ

#### デフォルトの web サイト / ストアの階層価格 API エンドポイントを削除

以前は、デフォルトのベース web サイトを削除し、セカンダリ web サイトをデフォルト web サイトとして使用すると、セカンダリ web サイトの階層価格を更新しようとするとエラーが発生していました。 ただし、この修正を適用すると、ベース web サイトが削除または非アクティブ化された場合でも、階層価格は正常に更新されます。

_ACP2E-4334 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/0a3b7032)_

### API, フレームワーク

#### アプリケーションサーバーの RedisRequestLogger\RedisClient （レートリミッター）例外

この問題を修正した後、PHP redis の拡張モジュールがインストールされている場合は、レート制限機能をGraphQL Application Server とともに使用することができます。

_ACP2E-4237 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/e885088b)_

### API、読み込み/書き出し

#### Async Invoice Refund API は、オンライン払い戻しではなくオフライン払い戻しを作成します

`is_online` パラメーターを含む払い戻しリクエストが正しく処理されなかった非同期の払い戻し操作を修正しました。

_ACP2E-4394 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/61c96348)_

### API、順序

#### [CLOUD] 注文情報の問題（注文 000075568 の行合計の表示）

項目が完全にディスカウントされた場合に、注文 API 応答の row_total_incl_tax 値が 0.00 ではなく、ゼロに近い残差値として返される問題を修正しました。

_ACP2E-3950 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/462ede94)_

### アカウント

#### [ 問題 ] カタログウィジェットテンプレートオプションの入力ミスを修正する

カタログウィジェットテンプレートオプションの入力ミスが修正されるようになりました。

_AC-11576 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/38185) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/38178)_

#### [ 問題 ] バックエンドグリッドで不要な間隔を削除しました

選択された項目がある場合、バックエンドグリッドで不要な間隔が削除されるようになりました

_AC-11579 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/38502) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/32622)_

#### マルチバイト文字を使用する場合、保存された顧客グループコードが入力と一致しません

マルチバイト文字を使用する顧客のグループコードが切り捨てられ、入力した値と一致しなかった問題を修正しました。 この更新により、完全な入力が正しく保存され、マルチバイト名を持つ顧客グループを正確に作成できるようになります。

_AC-13335 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39342) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/a06a4a57)_

#### 管理パネルでおよび.swiss ドメインを使用して顧客の電子メールを更新する際の問題

管理パネルで、特殊文字と.swiss ドメインを含む顧客メールを受け取れるようになりました。
以前は、max@möstermann.swiss のようなアドレスへの顧客メールの更新は、無効なホスト名と TLD に関するエラーで失敗していました。
AC-13409

_AC-13409 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39394) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/d3ea191d)_

#### ニュースレターの購読が有効なスイッチが web サイト/ストアごとに機能しない

システムは、グローバルレベルで無効にされた複数の web サイト/ストレビューがある場合、ニュースレターの購読を正しく処理します

_AC-14283 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39751) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/39752)_

#### 「製品が表示された」顧客セグメント条件の非推奨（廃止予定）

「製品が表示されました」顧客セグメント条件は非推奨（廃止予定）になりました。
以前は、この条件を使用すると、MySQL クエリが大量に生成されるためにサイトが停止する可能性がありました。 この条件は、非推奨（サポート対象外）としてマークされるようになりました。

_AC-14542_

#### [ 問題 ] 削除された電子メールの開示

入力したメールがアカウントの確認に不要な場合、顧客が存在しているかどうかに関係なく、誤ったメールを示すエラーメッセージを表示するようになりました。

_AC-14561 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39574) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/39570)_

#### `updateProductsInWishlist` GraphQL mutation を使用してウィッシュリスト項目のコメントを消去できない

GraphQLのミューテーションを使用してウィッシュリストのコメントが更新されない問題を修正しました。
これで、コメントが正しく更新され、API 応答とストアフロントの両方に反映されるようになりました。

_AC-14682 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39911) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/36d4d6fb)_

#### モバイルで削除された製品は、再ログインするまで Web のミニ比較セクションに表示されたままになる

ミニ比較セクションを含め、モバイルと web の両方のすべての比較ビューから製品が直ちに消えるようになりました。

_AC-14703 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39905) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/40023)_

#### [ いいえ ] に設定されている場合、接頭辞/接尾辞の設定は無視されます

設定で無効にした場合でも、顧客名のプレフィックス/サフィックスが引き続き注文に表示される問題を修正しました。
現在は、設定に基づいて、プレフィックス/サフィックスの値が注文の詳細から削除されます。

_AC-15074 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/40036) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/a3b1abc2)_

#### ストアフロントの顧客アカウント登録：メールアドレスの形式が別のドメイン形式に変換される

このバグは、ドメイン内の特殊文字（例：tec55241@adòbe.com）を含む顧客メールがパンニーコード形式（tec55241@xn--adbe-mqa.com）に自動変換されている問題を修正しました。
Magento 2.4.9-alpha3 では、この修正により、このようなメール ID が変更されずに有効なままになり、配信エラーが発生するのを防ぐことができます。

_AC-15177 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/68a45d0a)_

#### 登録フォームに検証メッセージがありません（mage-error）

顧客アカウント作成ページの必須フィールドが空のままの場合に検証メッセージが表示されない問題を修正しました。
現在は、すべての空のフィールドまたは間違ったフィールドに対して適切なエラーメッセージが表示されます。

_AC-15185 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/40076) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/36d4d6fb)_

#### 注文キャンセルモーダルタイトルに翻訳がありません

システムは、ストアフロントの注文キャンセルモーダルで、欠落している翻訳を修正するようになりました。 顧客がマイアカウント / マイ注文ページから「キャンセル」ボタンをクリックすると、キャンセルの理由を尋ねるモーダルが表示されます。 ただし、モーダルタイトルは以前はハードコードされており、翻訳できませんでした。 この変更により、モーダルタイトルで適切な翻訳方法が使用されるようになります。

_AC-15260 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/40098) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/40100)_

#### magento 2.4.8-p1 でのログイン後の問題

Magento 2.4.8-p1 で、ログイン後もホームページに「アカウントを作成」リンクが表示される問題を修正しました。
現在は、他のページと一致するように、ログイン後にリンクは正しく非表示になっています。

_AC-15292 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/40120)_

#### [ 問題 ] 顧客を削除する前に isSecureArea を設定してください

システムは正常に動作しており、この PR セットは削除プロセス用に isSecureArea で、顧客は正常に再登録できます。

_AC-15723 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/40211) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/38462)_

#### [ クラウド ] 顧客アカウントの作成中に現在のエリアで発生したエラーに対して、削除操作は禁止されています

修正によって無効なアドレスで顧客を保存すると、無関係な「現在のエリアでは削除操作が禁止されています」ではなく、無効の理由を説明するメッセージが返されます。

_ACP2E-3791 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/6ea61121)_

#### [B2B] 「eav」キャッシュが無効になっている場合、ログインしている顧客の Web API リクエストは無限ループに陥ります

修正後、Eav キャッシュを無効にしても、特定の REST リクエスト中に無限ループに陥ることはありません。

_ACP2E-4191 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/45cbf9b6)_

#### 一部のロケールの読み込みエラー

アラビア語ロケールを使用し、生年月日属性がストアフロントに表示するように設定されている場合に、顧客アカウントを作成できない問題を修正しました。 これで、この設定でアカウントが正常に作成されました。

_ACP2E-4311 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/2687b487)_

#### アカウント情報の更新時のエラー無効日

お客様は、アラビア語ロケールを使用する際にアカウントを正常に更新できるようになりました。 以前は、アカウント情報を保存しようとすると、無効な日付エラーが原因で生年月日が失敗しました。

_ACP2E-4344 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/31258bf6)_

#### 招待状送信機能の実行中に警告メッセージが表示される

「顧客が招待メールにカスタムメッセージを追加することを許可」設定が無効になっている場合に、「招待を送信」ページでメールフィールドを追加すると、「許可される最大 X 個のメールアドレス」という警告メッセージが表示されない問題を修正しました。
以前は、カスタムメッセージが有効な場合にのみ警告が表示され、一貫性のないユーザーエクスペリエンスが作成されていました。 現在は、最大メール制限警告は、カスタムメッセージ設定に関係なく一貫して表示されます。

_ACP2E-4374_

### アカウント、管理 UI

#### [ クラウド ]cartId を持つそのようなエンティティはありません

同じセッションで 2 つの会社管理者アカウントで「顧客としてログイン」を使用すると、「cartId のエンティティがありません」というエラーが発生する問題を解決しました。

_ACP2E-4137 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/e885088b)_

#### 顧客作成フォームのエラーメッセージが翻訳されない

顧客検証エラーメッセージが、異なるインターフェイス間で正しく翻訳および書式設定されなかった問題を修正しました。 検証エラーで、アプリケーションのすべての領域（ストアフロント、adminhtml、rest api および graphql）で正しく翻訳されたメッセージが表示されるようになりました。

_ACP2E-4354 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/31258bf6)_

### 管理 UI

#### カテゴリ製品グリッド/ステータスおよび表示列を名前で並べ替えると、空になる

製品名で並べ替えると、カテゴリ製品グリッドでステータス列と表示列が空のように表示される問題を修正しました。
グリッドに、並べ替え後のすべての列データが正しく表示されるようになり、管理パネルに正確な製品情報が表示されるようになりました。

_AC-10659 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/38233) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/3cf1a106)_

#### メールテンプレートのストアスイッチャー

非推奨の jQuery コードが原因で、ニュースレターメールテンプレートのプレビューのストア切り替えボタンをクリックしても開かない問題を修正しました。 読み込みイベントを更新すると適切な機能が復元され、ユーザーが期待どおりにストア切り替えボタンにアクセスできるようになりました。

_AC-12334 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/38892) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/8670a2b4)_

#### シンプルな製品では、同じ設定で買い物かごページと製品ページの FPT 値が異なります

シンプルな製品の買い物かごページと製品ページで FPT 値が一貫するようになりました。
以前は、固定製品税（FPT）の値は、同じ設定が適用されている場合でも、買い物かごと製品ページの小数点以下の桁数が異なる場合がありました。
AC-13066

_AC-13066 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/8953613e)_

#### スウォッチモジュールが無効の場合、複数選択/選択属性オプションを保存できない

スウォッチモジュールが無効な場合に、複数選択/選択属性オプションを保存できるようになりました。
以前は、スウォッチモジュールを無効にすると、新しい複数選択/選択属性オプションを作成する際に例外が発生していました。
AC-13071

_AC-13071 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/8953613e)_

#### 買い物かごページと製品ページの FPT 値が、動的製品に対して同じ設定で異なる

動的な製品の買い物かごページと製品ページで FPT 値が一貫するようになりました。
以前は、同じ設定で、FPT （固定製品税）の値が買い物かごと製品ページの小数点以下の桁数で異なる場合がありました。
AC-13075

_AC-13075 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/8953613e)_

#### 日付 ui コンポーネントで日付形式が考慮されない

日付 UI コンポーネントで、設定済みの形式が無視され、正しくない値が表示される問題を修正しました。 この修正により、日付フィールドが、表示と入力の両方で指定された形式（Y-m-d など）に従うようになりました。

_AC-13174 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39218) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/913bf1a6)_

#### ソースを削除するオプションはありません

管理 UI でインベントリソースの削除オプションを追加し、管理者が追加のソースを有効または無効にするだけでなく削除できるようにしました。 この機能強化により、未使用のソースをより適切に制御できるので、在庫管理が向上します。

_AC-13354 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/32362) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/inventory/commit/1b6c8a3e)_

#### 管理画面のカテゴリ ツリーが展開されず、レベル 3 から選択したネストされたカテゴリがすべて表示されない

管理者のカテゴリツリーが展開されず、レベル 3 を超える、選択したネストされたカテゴリが表示されない問題を修正しました。 修正後、選択したすべてのカテゴリが自動的に展開され、カテゴリに関連する条件での可視性と操作性が向上します。

_AC-13363 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/913bf1a6)_

#### [ 問題 ] 役割ツリーによるユーザーエクスペリエンスの向上

このプルリクエストでは、すべてを折りたたむ、すべてを展開する、選択した項目で分岐を展開するボタンが追加されます。 この機能は、カテゴリツリーで提供される機能（カタログ/在庫/カテゴリ）と同様です

_AC-14020 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39654) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/36511)_

#### インポート/エクスポート アクションログが、システム/アクションログ/レポートグリッドに作成されない

管理者アクションのインポート/エクスポートのログを実装して、システム/アクションログ/レポートに表示されるようになりました。 これにより、以前は見つからなかったインポートアクティビティが記録され、監査トラッキングが向上します。

_AC-14266 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/b5e99d20)_

#### Symfony\Component\Mime\Exception\LogicException:「Sender」ヘッダーは、「Symfony\Component\Mime\Header\MailboxHeader」のインスタンスである必要があります（「Symfony\Component\Mime\Header\MailboxListHeader」を取得）

SMTP 用にカスタムのリターンパスアドレスが設定されている場合、Adobe Commerceから登録メールが正常に送信されるようになりました。 以前は、vanilla Adobe Commerce 2.4.8 で system/smtp/set_return_path を 2 に、system/smtp/return_path_email をカスタムアドレスに設定すると、お客様の登録は完了しましたが、登録メールが送信されず、Adobe Commerceはこのエラーをログに記録していました。Symfony\Component\Mime\Exception\LogicException:「Sender」ヘッダーは「Symfony\Component\Mime\Header\MailboxHeader」のインスタンスである必要があります（「Symfony\Component\Mime\Header\MailboxListHeader」を取得）。

_AC-14520 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39823) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/1e14bd72) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/1514117f)_

#### 更新順序で最新のカスタム属性データが取得されない

注文ページを更新しても最新の顧客カスタム属性データが表示されない問題を修正しました。修正後、更新された属性値は反映され、注文をキャンセルして再作成する必要がなくなりました。

_AC-14690 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/30301)_

#### [ 問題 ] 非推奨（廃止予定）のエスケープを置換

非推奨（廃止予定）の getEscaper （）を削除し、コンストラクターの挿入を使用して追加しました。

_AC-15132 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/40062) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/38135)_

#### モバイル表示でウェルカムメッセージが製品カテゴリと重なる

モバイル表示で、ようこそ名が製品カテゴリと重なってクリックがブロックされる UI の問題を修正しました。
カテゴリが完全に表示され、クリックできるようになりましたが、重複の問題は発生していません。

_AC-15166 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/1b1baf1d)_

#### Ui フォームのリセットボタンが期待どおりに動作しない

ページ全体を再読み込みせずにリセットボタンをクリックすると、フォームデータがリセットされ、システムは正常に動作するようになりました。

_AC-15204 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/40092) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/40094)_

#### [ 問題 ]PageCache/AccessList:CIDR サポートの追加

システムはネットワーク内のパージリクエストを受け入れるようになりました。CIDR 範囲を指定するだけの方が簡単です。

_AC-15804 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39953) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/37809)_

#### [ 問題 ] キャッシュ管理ボタンに説明タイトルを追加する

カーソルを移動すると、キャッシュ管理ボタンに説明タイトルが追加されるようになりました

_AC-16212 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/38607) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/38598)_

#### グリッドを使用して税率を一括削除する機能の提供

管理者ユーザーは、「管理税率」グリッドから複数の税率を同時に削除できるようになりました。  [GitHub-33399](https://github.com/magento/magento2/issues/33399)

_AC-2238 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/33399) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/33484) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/5cd64dd0)_

#### 管理の静的グリッドにホバーの色が適用されない

管理者の静的グリッドの行に、期待どおりにホバーカラーが適用されるようになりました。[GitHub-35358](https://github.com/magento/magento2/issues/35358)

_AC-2916 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/35358) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/35384)_

#### Google reCAPTCHA 管理パネルの exception.log の「Can not resolve reCAPTCHA parameter」エントリ

Google V3 reCAPTCHA Admin ログインの `var/log/exception.log` ファイルの reCAPTCHA エラーが解決され、エラーメッセージはログに記録されません。 以前は、管理者ユーザーが **Configuration** /{Security **/** 4}Google reCAPTCHA 管理パネル **を設定すると、数秒ごとに次のエラーがスローされていました。**  `main.ERROR: Can not resolve reCAPTCHA parameter. {"exception":"[object] (Magento\Framework\Exception\InputException(code: 0): Can not resolve reCAPTCHA parameter. at /home/xxxxxxx/public_html/vendor/magento/module-re-captcha-ui/Model/CaptchaResponseResolver.php:25)"} []`[GitHub-34975](https://github.com/magento/magento2/issues/34975)

_AC-3179 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/34975) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/4f7e5983) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/security-package/commit/804dbc2a)_

#### 条件 SKU を含む買い物かご価格ルールでは、SKU の「先頭のゼロ」が考慮されません（SKU:01234 は 1234 と同じです）

システムでは、SKU の「先頭のゼロ」を考慮した条件 SKU を使用して、買い物かご価格ルールを正しく処理するようになりました

_AC-9428 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/37919) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/39525)_

#### 複数選択のデフォルト属性オプション値の動作の問題

修正前は、複数のオプション属性のデフォルト値が正しく保存されていませんでした。 修正後、値はデータベースに適切に保存されるようになりました。

_ACP2E-3523 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/9608ca21)_

#### バックエンド管理メニューのサブタイトルが表示されない

メインメニューグループのすべてのタイトルが正しく表示されるようになりました。 以前は、メインメニューの 2 列目または 3 列目にリンクのグループが 1 つしか含まれていない場合、そのグループのタイトルは表示されませんでした。

_ACP2E-3540_

#### 製品数量を管理者から買い物かごに戻す際の問題

管理者から注文を作成する場合、サイドバー上の顧客カート内の製品が注文に追加されても消えません。

_ACP2E-3563 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/c8ba4ab1)_

#### 制限付き管理者ユーザーは、製品ステータスを一括更新できない

カスタム管理者は、web サイトレベルのプロパティなので、製品ステータスを一括更新できます。 ステータスは、制限された管理者がアクセス権を持つ web サイトでのみ更新されます。

_ACP2E-3772_

#### [ ステージング 2] 保管されたカードが管理パネルに表示されない

アップグレード後、「ストアドカード」支払いオプションがバックエンドの注文配置フォームに表示されなくなる問題を修正しました。

_ACP2E-3830 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/7accebfa)_

#### 制限付き管理者ユーザーは、ストア固有の権限にもかかわらず、デフォルト設定を保存または更新できる

制限された管理者ユーザーが、特定の web サイト範囲のみに割り当てられているにもかかわらず、「デフォルト設定」範囲を表示して更新しようとすると、混乱が生じる可能性がある問題を修正しました。

_ACP2E-4011 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/2a1e1e55)_

#### 任意のストア表示範囲について DB に保存された設定可能な製品価格が、フロントエンドで保存された価格に関連がない、カテゴリ内の製品の並べ替え機能で問題が発生する

Web サイトごとに価格が設定され、管理 UI の設定可能な製品の編集ページでストア表示が選択されている場合に、設定可能な製品の「デフォルト値を使用」チェックボックスを削除しました。

_ACP2E-4036 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/fab20b00)_

#### [QUANS]Admin パスワード ポリシーが PCI DSS 4.0 準拠を満たしていません（12 文字以上）

管理者は、ストア/設定/詳細/管理者/セキュリティを使用して、管理者ユーザーのパスワードの最小長の要件を設定できるようになりました。 この機能強化により、既存のパスワードポリシーを維持しながら、セキュリティの柔軟性が向上します。 検証は、管理者ユーザーの作成/変更時と設定保存時の両方で適用され、ユーザーエクスペリエンスを向上させるためのリアルタイムのフロントエンド検証が行われます。

_ACP2E-4044 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/47721be6)_

#### 管理者インターフェイスの言語が日本語の場合の日付フィルターの問題

誕生日フィルターおよび列は、「顧客となった年数」フィルター/列と同じ統合形式 M/d/y を使用します

_ACP2E-4052 - [GitHub の問題 &#x200B;](https://stg1.navi-online.kakuyasu.co.jp/adminCgWN7zCh/admin/system_account/index/key/d6fdbee50ff25178d1fef981ec823c5e82e8cee6959717790031bb900c4d6633/) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/52f46328)_

#### 管理グリッドヘッダーの両側に白いブロックが表示される

管理グリッドの視覚的な位置揃えの問題を修正しました。 以前は、管理パネルで商品グリッドを水平方向にスクロールすると、グリッドヘッダーの左右で白いブロックがずれて表示されていました。 スクロール時にグリッドヘッダー要素が適切な垂直方向の整列を維持するようになり、管理者が大きな製品カタログを管理する際に、視覚的にわかりやすくなりました。

_ACP2E-4104 - [GitHub の問題 &#x200B;](https://mcprod.pap-store.acer.com/index.html)_

#### Ui コンポーネント fileUploader が 2.4.8-p1/ 2.4-develop で正しく動作しない

複数選択でアップロード領域のクリック時にアップロードを許可するカスタム ui コンポーネントのファイルアップロードが改善されました。

_ACP2E-4162 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/ee918f0d)_

#### [ オンプレミス ] 新しく作成された注文/会社/顧客は、選択プロセス中に「すべてを選択」範囲に自動的に含まれます

古い管理グリッドページですべてのレコードを手動で選択すると、一括アクションを実行する際に、すべてのレコードが意図せず削除される問題を修正しました。 以前は、選択した項目の数が合計数と一致すると、グリッドは自動的に「すべてを選択」モードに内部的に切り替わっていたため、一括操作が明示的に選択したレコードだけでなく、すべてのレコードに影響を与えていました。

_ACP2E-4202 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/6e134409)_

#### ACP2E-3362 のソリューションは、MariaDB 10.6 でゆっくりと動作します

履歴検索リクエストが多数ある場合のフロントエンド検索ページのパフォーマンスが向上しました。

_ACP2E-4225 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/ab891304)_

#### クレジットメモグリッドのストアタイムゾーンに従った日付フィルターが機能しない

以前の日付属性別フィルタリングリストでは、選択した日付と保存された日付の間のタイムゾーンの違いにより、項目が欠落していました。現在は、固定日付フィルターが適切に適用された後です。

_ACP2E-4239 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/0a8c9a9a)_

#### pagebuilder がインストールされると、ファイルアップローダダイアログが 2 回開きます

カスタムコンポーネントのアップロードボタンを修正する前に、が 2 回トリガーしていました。 修正後、アップロード ボタンが期待どおりに動作します。

_ACP2E-4241 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2-page-builder/commit/5c4ae802)_

#### 顧客データの変更時に、削除された顧客属性の検証エラーが発生する。

この修正前は、削除された複数の属性オプションが含まれていた場合、顧客と顧客の住所の保存に失敗していました。 修正後、複数の属性オプションが存在する場合でも、両方を正常に保存できます。

_ACP2E-4281 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/0a8c9a9a)_

#### 製品イメージの変更がログに記録されないアクション ログ

製品の画像のアップロードと削除が管理アクションログで追跡されない問題を修正しました。 以前は、管理者が製品に新しい画像を追加したり、製品のメディアギャラリーから既存の画像を削除したりしても、これらの変更はログシステムに記録されませんでした。 画像の役割への変更（画像をメイン製品画像、サムネール、小さい画像として割り当てるなど）のみがログに記録されていました。 画像の追加や削除を含むすべてのメディアギャラリーの変更が管理アクションログに適切に記録されるようになり、製品の画像管理アクティビティに対する完全な監査証跡の可視性が提供されます。

_ACP2E-4302_

#### 管理ダッシュボードでの JS の警告：「ローダーの起動が想定されていましたが、DOM で見つかりませんでした」

管理ダッシュボードでグラフが有効になっている場合に、ブラウザーコンソールに表示されるJavaScriptの警告を修正しました。 以前は、グラフが有効な管理ダッシュボードにアクセスすると、機能が正しく動作しているにもかかわらず、古いデバッグチェックで誤って「ローダーの起動が想定されているのに、dom で見つかりませんでした」と警告されていました。

_ACP2E-4336 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/2687b487)_

#### デフォルトのチェックインストア設定を使用する場合に、依存関係設定を編集可能な [CLOUD] 設定を使用します。

「デフォルト/Web サイトを使用」がオンになっているにもかかわらず、ページの読み込み後にシステム設定フィールドが有効になる場合がある問題を修正しました。

_ACP2E-4337 - [GitHub の問題 &#x200B;](https://mcstaging.pap-store.acer.com) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/31258bf6)_

#### 管理ダッシュボードのオーダーグラフのアニメーションを最終的なサイズに

管理ダッシュボードの順序グラフが即座に表示されるようになり、不要なサイズ変更アニメーションが不要になりました。

_ACP2E-4398 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/38860) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/f7bbcb4e)_

#### JS エラーにより、ページビルダーがモバイルビューでコンテンツを保存できない（TypeError：未定義のプロパティを読み取れない）

モバイル表示でバナーを追加する際に、ページビルダーでページを保存できない問題を修正しました。

_ACP2E-4399 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/38565) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2-page-builder/commit/bdac5bca)_

### 管理 UI、B2B

#### カスタマーヘッダーとしての B2B ログインには、引き続きMagento ブランディングがあります

以前は、ストアフロントのヘッダーに、「現在、&lt; ストア名 > で &lt; 顧客名 > として接続されています」とMagento ブランディングが表示されていました。 （修正）と、ヘッダーがADOBE ブランディングで表示されるようになりました。

_AC-14361 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/fadcfa8b)_

### 管理 UI、カタログ

#### カタログルールがアクティブでリアルタイムモードが有効な場合、製品の保存が失敗する

カタログルールのインデックス作成を製品トランザクションから分離することで、製品の保存操作中にカタログルールのインデックス作成が DDL トランザクションエラーで失敗する可能性がある問題を修正しました。

_ACP2E-4378 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/f7bbcb4e)_

### 管理 UI、コンテンツ

#### 画像挿入中の例外「メディアアセットパスのレンディションを作成できない」

Media Gallery 画像の最適化設定の最大幅と最大高さの値を削除すると、画像の最適化処理中にエラーが発生しなくなりました。

_ACP2E-3781 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/520f9e30)_

### 管理 UI、注文

#### 管理者による注文の作成：20 以上の製品を追加する際にセッションサイズがオーバーフローする（セッションサイズが 256 KB の制限を超えている）

JSON リクエストの大きなHTML応答がセッションに保存されるのを防ぎ、管理者がログアウトしなくても一括製品の追加がスムーズに行われるようにすることで、管理者の注文作成時のセッションサイズのオーバーフローを解決しました。

_AC-15893_

### 管理 UI、セキュリティ

#### 弱いパスワード管理

同じパスワードを使用する場合、管理者ユーザーを保存できません。 以前は、適切な検証なしで正常に保存されていました。

_ACP2E-3657 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/df92debe)_

### 管理 UI、セキュリティ、ステージングおよびプレビュー

#### コンテンツのステージングのアクションログ

アクションログに、ステージング更新アクティビティが表示されるようになりました。 以前は、ステージング更新ログは管理アクションログに記録されていませんでした。

_ACP2E-3679_

### 管理 UI、税

#### 税率管理 ui エラー

このチケットは、国を切り替えても（例：米国から英国→）、以前に選択した米国の州が引き続き表示され、ユーザーを誤解させる税率管理 UI の問題を修正しました。
2.4.9-alpha3 では、選択した国に州がない場合、州フィールドが*にリセットされるようになりました。

_AC-8440 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/a3b1abc2)_

### 分析/レポート

#### [ 問題 ]Google Analyticsのみを使用する場合の scp の許可リストが追加されました。

この PR により、Google Analytics モジュールに CSP 許可リストが追加され、Google Adwords に依存することなく、独立して機能できるようになります。 Google Adwords モジュールが無効になっている場合でも、Google Analyticsが正しく機能するようになりました。

_AC-16311 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/40051) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/40032)_

#### 管理アクションログユーザーレポートには、フィルターの適用時に使用されたフィルターの詳細は表示されません

修正前は、フィルタリングパラメーターが管理者アクティビティレポートに記録されていませんでした。 修正後、すべてのリクエストデータがログに記録されるようになりました。

_ACP2E-4099_

#### 詳細レポートの CSV ファイルのファイルヘッダーが重複して、レポートが空になる

修正後、詳細レポート機能用に生成されたレポートで、行数がバッチサイズを超えた場合に、重複したヘッダー行が含まれなくなりました。

_ACP2E-4187 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/45cbf9b6)_

#### 放棄された買い物かごレポートに無効な文字が含まれています

CSV ファイルとして書き出された放棄された買い物かごレポートに、MS Excel で開いたときのインドルピーなどの通貨記号に対して、適切にレンダリングされた文字が含まれるようになりました。

_ACP2E-4288 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/0a8c9a9a)_

#### MDVA-19640 の 2.4.8 互換性の更新

この修正により、Analytics cron ジョブタスクがデフォルトグループから Analytics グループに移動されます

_ACP2E-4309 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/c135fc3a)_

#### Admin for Canada の web サイト/通貨の注文/請求レポートに売上高が表示されない

一部の注文関連レポートで、ストアの通貨レートが適用されていませんでした。 修正後、レポートには設定済みのストア率が適切に適用されます。

_ACP2E-4361 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/31258bf6)_

### B2B

#### 注文が機能しない PayFlow Pro クレジットカード決済方法を使用して交渉できる見積もりからチェックアウトに進みます

Adobe Commerceは、Payflow Pro クレジットカード支払い方法を使用して交渉可能な見積もりからチェックアウトする際に、正常に注文するようになりました。 以前は、B2B 機能が有効化され、購入者が交渉可能な見積もりからチェックアウトに進んだ場合、Payflow Pro を選択して「注文を行う」をクリックすると、エラーメッセージが表示されずにページが無期限に読み込まれ続け、注文が作成されませんでした。 AC-11973

_AC-11973_

#### 引用符の名前を変更した後の成功メッセージが断続的に消える

交渉可能な見積もりテンプレートまたは見積もりテンプレートがストアフロントで名前を変更した後、Adobe Commerceが常に成功メッセージを表示するようになりました。 以前は、購入者が譲渡可能な見積りの名前を変更すると、成功メッセージが断続的に表示されなくなっていた（多くの場合、すぐに消去される）ので、自動テストが発生し、名前の変更操作自体は成功しても、このメッセージが失敗するのを待っていました。 AC-13447

_AC-13447_

#### ゲストチェックアウトの会社フィールドの検証に失敗する

ゲストのチェックアウトで会社フィールドが正しく検証されるようになりました。
以前は、company 属性が必須の場合、フィールドが入力されていても、ゲストのチェックアウトが次のエラーで失敗していました。「Company is a required value」。
AC-14987

_AC-14987 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/40011) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/f1adb44e)_

#### 制限付き管理者は、会社を共有カタログに割り当てることができません

会社を共有カタログに割り当てる際に、制限付き管理者ユーザーに例外が発生する問題を修正しました。更新により、割り当てがエラーなく正しく動作することが保証されます。

_AC-15662_

#### カテゴリ権限が有効な場合の、グループ化された製品の購買依頼リストへの追加の例外

製品オプションが配列として安全に処理され、すべての製品タイプを例外なく追加できるようにすることで、グループ化された製品をカテゴリ権限が有効な購買依頼リストに追加する際に発生していた TypeError を修正しました。

_AC-15862_

#### ログインした顧客に対して、REST API products-render-info が間違った最終価格を返す

チケットには、Rest API products-render-info の修正があります。ログインした顧客に対して、間違った最終価格を返します

_AC-5979 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/35757)_

#### カテゴリページから追加しようとすると、「購買依頼リストに追加」ボタンが表示されなくなります

以前の「購買依頼リストに追加」ボタンは、現在修正されているカテゴリ・ページから追加しようとすると消え、カテゴリ・ページに購買依頼ボタンが表示されます。

_AC-8575_

#### 総計の計算には税額は含まれません

注文に正しい合計が含まれているのは、クロスボーダー取引が有効な既存の発注書から注文が作成される場合です。

_ACP2E-3727_

#### REST API を使用した B2B 共有カタログのカテゴリの割り当て解除が遅い

B2B でカテゴリの割り当てを解除する際のパフォーマンスが大幅に向上しました。 以前は、B2B 共有カタログのカテゴリの割り当てを解除するのに長い時間がかかっていました。

_ACP2E-3796_

### B2B、買い物かごとチェックアウト

#### 管理機能「顧客としてログイン」から B2B 会社ユーザーにログインすると、cartId = X エラーのエンティティがストアフロントに表示されません

「顧客としてログイン」機能を使用したときに管理者バックエンドから正常にログインすると、「cartId = X のエンティティがありません」エラーが表示されなくなりました。

_ACP2E-3994 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/2a1e1e55)_

#### 請求先住所が不明なため、「店舗での配信」の配送方法で注文することができません

配信方法として店舗での受け取りを選択した場合に、チェックアウト時に請求先住所が自動的に入力されない問題を修正しました。 請求先住所がないと、チェックアウトを完了できません。

_ACP2E-4030 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/inventory/commit/42d23211)_

### 買い物かごとチェックアウト

#### Magento 2.4.7 更新（ミニ）カート 10 進数による数量は許可されていません

ロケールが NL （オランダ語）の場合に、ミニカートの小数を使用して数量を更新する際に、Magentoが正しく処理するようになりました

_AC-13238 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39236) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/39669)_

#### [ 問題 ] チェックアウト契約モデルに EventPrefix と EventObject を追加する

システムには、チェックアウト契約モデルの EventPrefix と EventObject が含まれるようになり、イベントをイベントの接頭辞でトリガーできるようになりました。 この機能強化により、開発者がチェックアウト契約イベントを扱う際の柔軟性が向上します。 以前は、チェックアウト契約モデルは EventPrefix と EventObject をサポートしていなかったので、イベント処理をカスタマイズする機能が制限されていました。

_AC-13252 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/32510) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/32451)_

#### [ 問題 ] 開発者エクスペリエンス：引用 AbstractItem コードスタイル（SwiftOtter の SOP-348）

このプルリクエストは、抽象項目メソッドの誤解を招くメソッド宣言を修正します。

_AC-13334 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39340)_

#### グループ化された製品フロントエンド数量の検証がありません

負の数量と最大数量を追加しようとすると、システムは正常に動作し、検証エラーが表示されるようになりました

_AC-13524 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39479) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/39480)_

#### [ 問題 ] subtotal.phtml の更新

正しい間隔で subtotal.phtml が更新されます

_AC-13907 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39619) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/39612)_

#### ゲストに注文できません

Adobe Commerceでは、管理者でミドルネームのフィールドが必要に応じて設定された場合、ゲストの買い物客が正常に注文できるようになりました。 以前のAdobe Commerce 2.4.8-beta1 （PHP 8.3/8.4）では、ミドルネームを必要に応じて設定し、ゲストとしてチェックアウトすると、ミドルネームが提供された場合でも注文が行われず、チェックアウトの完了がブロックされていました。 AC-14241

_AC-14241 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/27217d0e)_

#### [Graphql]nullable 以外のフィールド「SelectedCustomizableOption.label」で null を返すことができない

選択したオプションが存在しない場合、システムは内部サーバーエラーをスローせず、メッセージが表示されるようになりました

_AC-14256 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39729) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/39888)_

#### 無効なウィッシュリスト項目がある場合、GraphQL addWishlistItemsToCart で既存の買い物かご項目の数量を更新できない（Magento 2.4.7-p3）

無効な設定可能な商品が見つかった場合に、GraphQLの addWishlistItemsToCart ミューテーションが処理を停止した問題を修正しました。 修正後、有効なウィッシュリスト項目が買い物かごに追加され、数量が更新される一方、無効な項目はスキップされ、適切なエラーが返されます。

_AC-14464 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39820) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/3cf1a106)_

#### [2.4.8] 市区町村名に 0～9、アンパサンド、全角またはかっこの数字が含まれている場合、注文を行うことはできません

などの特殊文字を含む都市名のチェックアウトが失敗する問題を修正しました。、&amp;または括弧。
現在は、このような都市名を使用した注文は、検証エラーなしで正常に行われます。

_AC-14495 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39854) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/b9f5d6f7)_

#### ゲストのプレフィックスが見積もりアドレス 2.4.8 に保存されない

ゲスト顧客のプレフィックス（Mr./Mrs.）がチェックアウト時に保存されるようになりました。
以前は、ゲストのお客様が選択した敬称は、最終的な注文に達する前に失われていましたが、他のすべてのアドレスフィールドは正しく転送されていました。
AC-14705

_AC-14705 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39915) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/f1adb44e)_

#### 数量条件を使用した営業ルール副選択の適用に失敗

製品のサブ選択条件を含む買い物かご価格ルールがチェックアウト時に適用されない問題を修正しました。
これで、設定されたルールに従って、割引が正常に適用されます。

_AC-14884 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39965) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/fe72c407)_

#### [ 問題 ] class 属性のスペースを削除する

クラス属性の余分なスペースが削除されるようになりました

_AC-14939 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39977) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/39970)_

#### Graphql - Backorder が有効な場合、結合カートが正しく機能しない

GraphQLを介した買い物かごの結合中に、ゲストの買い物かごの項目が顧客の買い物かごに結合されない問題を修正しました。
現在は、顧客の買い物かごには、ゲストと顧客の両方の買い物かごからの合計数量が正しく反映されています。

_AC-15148 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/40064) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/a3b1abc2)_

#### [ 統合 ] [ チェックアウト ] 失敗した支払いメールテンプレートで更新された依存ディレクティブ

depend ディレクティブを正しく処理するように更新された、失敗した支払 E メール テンプレート。
該当する場合は、配送先住所と配送方法が正しく表示されるように修正しました。
以前は、失敗した支払いメールにこれらのフィールドが見つかりませんでした。

_AC-15363 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/36d4d6fb)_

#### ログイン後、チェックアウトリダイレクト マイアカウントページに進みます

セッションの有効期限が切れた後、ユーザーがチェックアウトログインではなくマイアカウントログインページにリダイレクトされ、ログインフォームでのチェックアウトに正しく対応されていた問題を修正しました。

_AC-15962_

#### [ カート ] 固定製品税が有効になっている場合、買い物かごページが読み込まれない

固定製品税（FPT）が有効になっている場合に、買い物かごページが無限の読み込みに入る問題を修正しました。 この問題は、商品価格と同じHTML要素に税金が含まれているため、中央小計と要約小計の間で不一致が発生したために発生しました。 修正後、買い物かごは正しく読み込まれ、正確な合計が表示されます。

_AC-16096 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/01cee3c3)_

#### 買い物かご価格ルールアクション「買い物かご内の価格」条件、適用時期すべきでない

不適格な製品に、「買い物かごの価格ルールが「買い物かごの価格が次の値を下回る」条件で誤って適用されていた問題を修正しました。
現在は、カートの商品価格が設定されたルール条件を満たさない場合、クーポンは適切に検証され、拒否されます。

_AC-6997 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/36433) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/01cee3c3)_

#### [ 問題 ] base_price ではなく見積品目に価格を設定します

フロントエンドの 1 つの web サイトに複数の通貨がある場合、システムは見積もり品目の価格を価格ではなく base_price に正しく処理します

_AC-9985 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/38094) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/36878)_

#### 期限切れの永続的な見積は、cron ジョブ sales_clean_quotes によってクリーンアップされません

「persistent_clear_expired」 cron ジョブが実行されると、期限切れの永続的な引用符がクリアされるようになりました。 以前は、期限切れの永続的な引用符が他の cron ジョブでクリアされていませんでした。

_ACP2E-3493 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/11be3dff)_

#### 非アクティブな会社のチェックアウトでの「エラーが発生しました」エラー

修正を行う前は、ログアウトアクションは買い物かごページで適切に完了していませんでした（長い間ログインしていたユーザー会社が有効でなくなった場合）。 これで、会社が利用できなくなった場合、ログアウトは正しく実行されます。

_ACP2E-3541 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/df92debe)_

#### 「複数のアドレスでチェックアウト」すると、アドレス選択が保存されない

複数出荷オプションをキャンセルする場合の修正の前は、複数出荷に戻しても、住所は事前に選択されていませんでした。 現在は、デフォルトのアドレスが、複数出荷画面内で選択したアドレスに置き換えられます。

_ACP2E-3646 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/6ea61121)_

#### [ クラウド ] 注文が 1 つのストア表示で作成された場合、最近の注文が他のストア表示に表示されない

「マイアカウント」ページに、同じストア内の他のストア表示からの最近の注文が表示されない問題を修正しました。 注文取得ロジックが更新され、「マイオーダー」ページの動作に合わせて、すべてのストアビューで一貫した注文表示が確保されました。

_ACP2E-3807 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/a20a6ff2)_

#### 次として表示する数量  バンドル製品の追加中に「管理者の顧客の買い物かご」セクションで 0 を選択  

顧客アクティビティの「買い物かご」セクションに、正しい数量が表示されるようになりました。 以前は、数量は 0 と表示されていました。

_ACP2E-3872 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/3ad96f6a)_

#### [ クラウド ] カートが要件を満たさなくなった場合、送料無料の割引が正しく削除されない

小計（除く カート価格ルールの（税金）に、前のルールからの割引が組み込まれるようになりました。

_ACP2E-3973 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/6dd3fa99)_

#### 複数出荷で同じ顧客の重複する注文が見つかりました

複数の配送先住所への注文を同時にリクエストしても、同じ顧客の注文が重複しなくなりました

_ACP2E-4117 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/a1c57b2e)_

#### [ クラウド ] 在庫切れのしきい値に達した場合、在庫数の制限を超えた通知メッセージが 2 回表示されます

買い物かごの更新で重複したエラーバナーが表示される可能性がある問題を修正しました。 以前は、AJAXの検証エラーの後、バックエンドがフォームの送信中に同じメッセージを再度追加したので、買い物客には 2 つの同じアラートが表示されていました。 追加のバックエンドメッセージの追加をスキップして、買い物かごページを単一の明確なエラーバナーに保つようになりました。

_ACP2E-4192 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/e885088b)_

#### 請求情報の場合、出荷情報 REST API を使用したサーバーサイドの検証が機能しません

顧客の住所データの検証が改善され、チェックアウト用に REST と GraphQl 間の一貫性が向上しました。

_ACP2E-4223 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/0a8c9a9a)_

#### [Cloud] 買い物かごページに表示されるバンドル製品価格の問題

複数通貨店舗の買い物かごページのバンドル製品価格の問題を修正しました

_ACP2E-4245 - [GitHub の問題 &#x200B;](https://www.techbuyer.com/) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/cbca0396)_

#### 買い物かごストアの範囲に関する問題の管理

デフォルト以外の web サイトに割り当てられた顧客の買い物かごを管理する際に、買い物かごエラーが管理者ユーザーに表示されるようになりました。 以前は、エラーは表示されていませんでした。

_ACP2E-4348 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/31258bf6)_

#### 部分的な請求書のキャンセル後にクーポン times_used がリセットされる

注文が部分的にキャンセルされた場合に、クーポンの times_used カウントが正しく更新されるようになりました。

_ACP2E-4365 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/61c96348)_

### 買い物かごと、チェックアウト、GraphQL

#### GraphQL経由で注文する際に、メッセージをエラーコードにマッピングする際にエラーが発生する

存在しない買い物かごまたは非アクティブな買い物かごに注文を行うためのGraphQL呼び出しで、すべてのストアビューで CART_NOT_ACTIVE または CART_NOT_FOUND エラーコードが正しく返されるようになりました。翻訳されたエラーメッセージによって、以前に未定義のコードが発生していた問題を修正しました。

_ACP2E-3942 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/7accebfa)_

#### [GraphQl] 買い物かごクエリ仮想引用符に関する買い物かご品目の割引問題

GraphQLの買い物かごクエリで、仮想見積もりについて誤った割引額が返される問題を修正しました。 以前は、適格でない特定の仮想製品に誤って割引が適用されていました。

_ACP2E-4248 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/cbca0396)_

#### [Cloud] ACSD-68499_2.4.8-p2 は別の問題を引き起こします

数量が不十分な項目に対する graphQL リクエストを実行すると、エラーコードを含む適切なエラーメッセージが返され、リクエストした数量が使用可能な場合、買い物かごの更新に成功しました。

_ACP2E-4404 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/1c547060)_

### 買い物かごおよびチェックアウト、GraphQL、在庫/MSI

#### cartItemInterface の is_available 属性は、販売可能な在庫が多い場合でも false を返します

is_available 属性は、販売可能な在庫が多い場合に true を返します。 以前は、常に false を返します。

_ACP2E-3885 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/3ad96f6a)_

### 買い物かごおよびチェックアウト、在庫/MSI

#### 買い物かごのサイズが大きい「ピックアップ場所を検索」エンドポイントで 414 エラーが発生する

多くの製品がカートに入っている場合に、「ストアで選択」を使用してチェックアウト中にストアを選択しても、長い URL が原因で失敗しなくなりました。
以前は、これにより、ストアの選択時に生成された URL が長すぎることが原因で 414 エラーが発生し、顧客がチェックアウトを完了できませんでした。

_ACP2E-4266 - [GitHub の問題 &#x200B;](https://mcstaging.casamyers.com.mx/) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/inventory/commit/ae1f272f)_

### 買い物かごと、チェックアウト、注文、製品

#### 注文請求書が失敗した場合でもギフトカードの E メールが送信される

この修正を実装する前は、請求書が作成された後にギフトカードのメールが送信されていました。 ただし、修正が適用された後、請求書が正常に保存され、コミットされた後に、ギフトカードの E メールが送信されるようになりました。

_ACP2E-3905_

### 買い物かごと、チェックアウト、プロモーション

#### ギフトカードの残高の表示は、Web サイトの範囲で制限されません

割り当てられた Web サイト範囲でギフトカードの残高チェックを制限。

_ACP2E-4379 - [GitHub の問題 &#x200B;](https://www.panini.it)_

### 買い物かごとチェックアウト、SEO

#### セカンダリ Web サイトからで購入した際に、メール内のギフトカードコード URL が正しくない

以前は、デフォルト以外のストアのマルチストア設定とギフトカードは、常にギフトカードの請求をデフォルトの web サイトにリダイレクトしていました。 この修正が適用されると、メールによって、ギフトカードの請求リンクが正しい範囲または web サイトにリダイレクトされます。

_ACP2E-3699_

### 買い物かごと、チェックアウト、セキュリティ

#### [CLOUD] sri パッチを実装した後、最初の試みでチェックアウトページで JS ファイルの 404 を取得する

「修正」より前のバージョンでは、縮小とバンドルが有効な場合、Mixin は買い物かごおよびチェックアウトに読み込まれませんでした。 修正後、すべての Mixin が期待どおりに読み込まれます。

_ACP2E-4128 - [GitHub の問題 &#x200B;](https://ansg.integration-5ojmyuq-f46gejjrfa7be.ap-3.magentosite.cloud/) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/e457c5e2)_

### カートとチェックアウト、送料

#### [ メインライン ] 買い物かご価格ルールが複数配送を考慮していない

この修正を実装する前は、サブ選択条件が適用され、送料無料が有効になっている場合、複数配送商品の買い物かご価格ルールが正しく適用されませんでした。 ただし、修正が適用されたので、複数出荷カートのカート価格ルールが意図したとおりに機能するようになりました。

_ACP2E-3666 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/b12ffe36)_

### カタログ

#### 同じクエリの同じページの重複キャッシュ fpc

同じクエリパラメーターを持つページに対して、ページの順序や末尾の文字に関係なく、同じフルページキャッシュ（FPC）が正しく識別され、使用されるようになりました。 これにより、ページキャッシュフォルダーのサイズが不必要に大きくなるのを防ぎます。 以前は、クエリパラメーターの順序が異なる場合や、末尾に文字がある場合は、同じページに対して異なる FPC 識別子が作成され、ページキャッシュフォルダーのサイズが増えていました。

_AC-10722 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/38269) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/38270)_

#### catalog_product_entity_int テーブルに必要な列のインデックスがありません

catalog_product_entity_int テーブルに必要な列の欠落しているインデックスを追加しました

_AC-10844 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/38315) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/38316)_

#### カタログ URL リソース （_getCategories）のスコープバグ

この PR は、カテゴリ URL リソースのストアスコープで値が定義されていない場合、デフォルトスコープにフォールバックを追加します。

_AC-11011 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/38393) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/38394)_

#### [ 問題 ] OpenGraph で価格を表示できるかどうかを確認してください

価格を非表示にするプラグインを使用すると、システムは正常に機能し、この変更価格は OG タグに表示されません。

_AC-11635 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/38512) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/38510)_

#### 価格を表示するために税金を追加する際の価格の丸め問題

表示価格に税金を追加する際の価格の丸め問題が修正されるようになりました

_AC-11725 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/18025) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/35730)_

#### [ 問題 ] カスタムカタログルール条件を許可する

厳密なタイプの確認が原因でカスタムカタログルール条件が使用できない問題を解決しました。 この修正により、クラスの等価性チェックが instanceof に置き換わり、カスタム条件クラスが正しく機能し、ルールの検証とインデックス作成が成功するようになります。

_AC-13338 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39339) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/913bf1a6)_

#### ウィッシュリストに追加されると、設定可能な製品が失われるオプション

製品をウィッシュリストに追加した後、設定可能な製品オプションが失われる問題を修正しました。 選択したオプションが保持されるようになり、ユーザーにオプションを再選択するよう求めることなく、製品をスムーズに買い物かごに追加できるようになりました。

_AC-13373 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39363) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/cc0ec250)_

#### 設定可能な製品の子製品（単純な製品）の特別価格が正しく表示されない

「製品リストで使用」が「いいえ」に設定されている場合に、設定可能な製品の子（シンプル）製品の特別価格が製品リストページに正しく表示されない問題を修正しました。 現在、特別価格は通常価格と共に適切に表示され、製品タイプ間で一貫した価格表示が保証されています。

_AC-13594 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/3cf1a106)_

#### [ バグ ] REST API：特別価格の更新で、すべてのストアビューの値が設定されない

REST API で、web サイト内のすべてのストアビューの特別価格が更新されるようになりました。
以前は、REST API を使用して特別価格を更新すると、指定したストア表示にのみ影響し、web サイト内のすべてのストア表示には影響しませんでした。
AC-13671

_AC-13671 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39521) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/7bdafaa2)_

#### 価格範囲と config.php の問題

Magento 2.4.2 では、config.php を使用して価格スコープを変更しても、catalog_eav_attribute の is_global 値が price 属性に適切に更新されません。
その結果、製品価格はグローバルに維持され、価格範囲が web サイトに設定されている場合でも、web サイトごとに保存することはできません。
この回避策では、データベースの is_global 列を手動で更新する必要があります。これは、実稼動環境には理想的ではありません。
この動作は、Magentoのデフォルトデザインと一致します。つまり、価格範囲はグローバルまたは web サイトですが、ストアビューごとではありません。

_AC-13857 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/33559)_

#### [\Magento\ConfigurableProduct\Model\Product\Type\Configurable] PHP エラーが通知されませんでした

ループ変数名を変更して、以降の呼び出しで使用される特定の製品に「_cache_instance_product_ids」データを正しく追加しました。

_AC-14159 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39641) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/39642)_

#### Elastic Search は、商品のデフォルトの並べ替え順（新しい順から古い順に変更）に干渉します

データベース内の最新の商品（entity_id が最も大きい商品）が最初に表示されます

_AC-14411 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/31043) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/36900)_

#### 2.4.8 でストアスイッチページがキャッシュから生成された後（ストアスイッチャーが機能しない）

キャッシュが手動でクリアされるまでストアフロントヘッダーからのストアビューの切り替えが機能しない問題を修正しました。
現在は、キャッシュをクリーンにする必要なく、ストア表示の切り替えが正しく機能します。

_AC-14426 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39806)_

#### 最小幅：（@screen__l）の.less スタイルは無視されます

カテゴリページで 1 行に 3 つの製品のみが表示される問題を修正しました。
現在は、期待どおりに 1 行に 4 つの製品が表示されます。

_AC-14463 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39817) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/b9f5d6f7)_

#### 顧客メニューのウィッシュリストページを除く、ホームページやその他のページでウィッシュリスト数が表示されない

ウィッシュリスト以外のページでウィッシュリスト数が空のかっことして表示される問題を修正しました。
すべてのページで、「My Wish List」の横に正しいウィッシュリスト項目数が表示されるようになりました。

_AC-14607 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39892) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/a3b1abc2) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/b3774fbe)_

#### ストアレベルの値を指定せずに REST API を使用すると、catalog_product_save_before オブザーバーが日付関連のエラーをスローする（getFinalPrice （）問題）

この PR は、日付が DateTimeInterface インスタンスとして指定された場合に適切な形式になるように、SpecialFromDate の処理を調整します。 これにより、特定のシナリオで getFinalPrice （）の実行中に発生するエラーを防ぐことができます。

_AC-14847 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39959) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/40003)_

#### 緊急 – 追加する製品にカスタマイズ可能なオプションがある場合、バンドルに製品を追加できない

カスタマイズ可能なオプションを含む製品をバンドル製品に追加できない問題を修正しました。
以前は、このような製品は、バンドル作成の「オプションに製品を追加」リストから除外されていました。
現在は、カスタムオプションを含めずに、カスタマイズ可能なオプションを備えた製品をバンドルに追加できるので、適切な在庫管理が可能です。
これにより、製品の複製や在庫レベルへの影響を受けずにバンドルを作成できます。

_AC-14958 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39993)_

#### クエリ文字列 `?p=` 負の値を指定すると、Elasticsearch例外が発生する

システムは、カテゴリのページネーションで負の？p=値を処理するようになりました。現在は、この処理が例外となり、有効なリクエストと見なされます

_AC-15191 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/40079) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/40080)_

#### 単一のオプションを持つ設定可能な製品の「できるだけ低い」価格ラベルが表示されます

設定可能な製品で、PDP/PLP に誤った「As low as」ラベルが付いた価格が表示される問題を修正しました。
現在、製品は誤解を招くラベルなしで正しい価格（$500）を表示します。

_AC-15237 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/40104) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/a3b1abc2)_

#### 「比較に追加」ボタンに対して誤ったメソッドが呼び出されました

\Magento\Catalog\Ui\DataProvider\Product\Listing\Collector\Url::collect （）で使用されているメソッドを修正しました。
以前は、getAddToCompareButton （）ではなく、getAddToCartButton （）が誤って呼び出されていました。
この変更により、製品リストの「比較に追加」ボタンをレンダリングするための正しい動作が保証されます。
機能的な動作の変更は導入されていません。この更新により、開発者のエクスペリエンスとコードの正確性が向上します。

_AC-15323 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39754) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/a3b1abc2)_

#### 異なるストア表示で、異なる通貨の買い物かごに間違った製品価格が表示される

複数のストア表示で異なる通貨を使用すると、買い物かごに誤った製品価格が表示される問題を修正しました。 修正後、カートには設定された通貨に基づいて正しい換算価格が表示されるようになり、製品ページとカートの一貫性が確保されます。

_AC-15385 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/a8cf637b)_

#### FPT が有効化されている場合に、設定可能な製品の誤った「As low as a」価格表示

FPT が有効化されている場合の設定可能な製品の誤った「安値」が、税金が 2 回適用されたことによって発生したことを確認しました。修正により、最終的な価格計算が税金構成に従い、正しい価格が表示されるようになります。

_AC-15718 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/40171) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/a06a4a57)_

#### Eav\Model\Entity\Collection\AbstractCollectionの_loadAttributes の時間の複雑さは、買い物かごおよび属性の製品数に伴って増加します

この PR では、ネストされたループを配列和集合（+）で置き換え、_setItemAttributeValue への呼び出しを減らすことにより、Eav\Model\Entity\Collection\AbstractCollectionの_loadAttributes が最適化され、大きな製品カートのパフォーマンスが向上しました。

_AC-15833 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/40216) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/40217)_

#### 収集キャッシュと設定可能な製品ギャラリー間のバグ処理されたインタラクション

media_gallery_images が常にコレクションとして扱われ、キャッシュデータの破損による致命的なエラーを防ぐ防御型のチェックを追加することで、設定可能な製品ギャラリーのキャッシュの問題を解決しました。

_AC-16066 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/33965) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/3b5ac075)_

#### 製品ページで属性を作成中にドロップダウンオプションの削除が機能しない

_AC-16437_

#### URL の書き換えが原因で製品ページでエラーが発生する

URL の書き換えがあった場合に、製品ページが正常に読み込まれるようになりました

_AC-2950 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/35371) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/39670)_

#### [Cloud] カテゴリに製品を追加する際のバグ

ポップアップグリッドを使用してカテゴリに製品を追加する際に、ページネーションとレコード数のラベルが正しく機能するようになりました。 以前は、ページサイズと等しい項目を持つ単一ページのみを読み込むと、項目選択ドロップダウンで問題が発生していました。

_ACP2E-3526_

#### mage_INDEXER_THREADS_COUNT で indexer_update_all_views cron エラーが発生する

カスタマーセグメントインデクサーを使用した MAGE_INDEXER_THREADS_COUNT > 2 の問題を修正しました

_ACP2E-3538 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/9608ca21)_

#### ページビルダー製品ウィジェット条件で「条件の組み合わせ」を追加中に例外が発生しました

この問題は、欠落条件や不完全な条件をスキップするチェックを追加することで修正されました。 以前は、これにより、システム内の不完全な条件の処理が原因でエラーログが生成されていました。

_ACP2E-3545 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/11be3dff)_

#### 属性セットを読み込む際にブラウザーがクラッシュする

4k を超える製品属性がある場合に、属性セットの編集ページでブラウザーがクラッシュしなくなりました

_ACP2E-3633 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/38810) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/b12ffe36)_

#### [CLOUD] 新しいストアの製品 URL 書き換えが作成されない：運用開始ブロッカー

新しいストアの製品 URL の書き換えが正常に作成されました。
以前の操作は、メモリリークまたはタイムアウトで終了しました。

_ACP2E-3669 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/df92debe)_

#### オプションの属性のデフォルト値が機能しない

以前は、product select 属性のデフォルト値を変更すると、以前の値を持つ配列要素として表示されていました。 この修正が適用された後、製品属性値を更新すると、eav_attribute テーブルに単一の要素として保存されます。

_ACP2E-3688 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/520f9e30)_

#### 桁区切り記号が原因で編集中にギフト カードの検証が失敗する

ギフトカードの金額が 1000 以上の場合に、ギフトカード製品タイプが保存される問題を修正しました。

_ACP2E-3704_

#### [ メインライン ] [ クラウド ] 画像のサイズ変更に 400 GB を超えるディスク領域を使用

修正後、フラグと共に使用される `catalog:images:resize` コマンド `--skip_hidden_images`、画像が存在しない web サイトの画像キャッシュを生成しません。

_ACP2E-3869 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/9ad7d277)_

#### 動的な画像の生成により、多数の画像が生成される

修正後は、製品が割り当てられている web サイトの画像のみが生成されます。

_ACP2E-3927 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/fab20b00)_

#### 入力された国 ID が存在しません – アイルランド （IE）

修正後、アイルランドの郵便番号を使用して集荷場所を検索できます。

_ACP2E-3932 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/4ca73607) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/inventory/commit/d2f1d6c6)_

#### レイアウト構造が正しくないため、フロントエンドで 500 エラーが発生し、レイアウトにキャッシュされる

間違ったレイアウト構造がレイアウトにキャッシュされているので、ページが 500 エラーコードを返す問題を修正しました

_ACP2E-4040 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/47721be6)_

#### 製品表示数が不正確とレポートされる – GA と比較してカウントが低い

report_viewed_product_index テーブルに正しい製品ページビュー数が表示されないバグを修正しました。

_ACP2E-4045 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/6e134409)_

#### 予定更新のカタログ価格ルール割引額フィールドの検証エラー

以前は、この問題を修正する前に、カタログ価格ルールのスケジュール更新で、割引額が by_fixed の場合、検証番号 – 範囲ルールが原因で適切に検証されませんでした。 この修正が適用されると、固定価格カタログ価格ルールに対して検証が正しく機能します。

_ACP2E-4054 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/6dd3fa99)_

#### VAT API レート・リミッタにより VAT の検証が失敗しました – トリガーの偽陽性の顧客グループの変化

Europa Vat 検証ツールへのリクエストを最適化し、「レート制限」エラーを軽減

_ACP2E-4072 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/ee918f0d)_

#### 実稼動環境での書き込みセットの最大サイズのエラーをトリガーするコアインデクサーの一括削除

データボリュームに基づいて 2 つの削除戦略を実装することで、カタログルール製品インデックスのクリーンアップを最適化します。

_ACP2E-4085 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/0a3b7032)_

#### 無効にすると、製品が在庫切れと表示されます

修正後、無効になった製品は製品ウィジェットに表示されなくなります。

_ACP2E-4136 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/a1c57b2e)_

#### [Cloud] エントリが重複したエラー（temp_category_descendants_%）

ネストされたカテゴリの数が多い環境のスケジュールされた更新を作成する際の重複エントリの問題を修正しました

_ACP2E-4159 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/a1c57b2e)_

#### [CLOUD] 異なるストアの製品数の不一致の問題

別のストレビューに切り替えた後、製品リストの比較が正しく機能するようになりました

_ACP2E-4249 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/98f028ab)_

#### 設定可能な製品の作成時に、制限付き管理者ユーザーに表示される「新しい属性を追加」ボタン

「新しい属性を追加」ボタンが、設定可能な製品の作成中に、一般管理者ユーザーに対してのみ表示されるようになりました。
以前は、制限付き管理者ユーザーに対して「新しい属性を追加」ボタンが表示されていました

_ACP2E-4279_

#### 画像の役割の割り当てに「画像とビデオ」で「デフォルトを使用」するオプションがありません

「デフォルト値を使用」オプションが「製品の画像とビデオ」セクションに追加され、デフォルトの範囲から設定を継承できるようになりました。

_ACP2E-4280 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/61c96348)_

#### 顧客グループの更新後、制限カテゴリの製品はウィッシュリストにまだカウントされる

この修正を行う前は、カテゴリ権限が顧客ウィッシュリスト項目に適切に適用されていませんでした。 修正後、ウィッシュリストの項目が web とGraphQLの両方で正しく表示され、ページ分割されるようになりました。

_ACP2E-4294 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/c135fc3a)_

#### [ クラウド ]PDP と PLP のバンドル製品価格の問題

通常価格のバンドル製品の価格は、デフォルト以外の通貨の PDP/PLP で正しく表示されます

_ACP2E-4298 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/0a3b7032)_

#### 顧客グループの変更後、顧客はアクセスできない製品を注文できる

以前は、管理者から顧客グループを変更すると、フロントエンドカタログと買い物かごにカタログ権限の変更が反映されていませんでした。 ただし、この修正を適用した後、顧客グループが管理者から変更されると、更新されたカタログ権限に従ってフロントエンドの見積もりが変更されるようになりました。

_ACP2E-4300 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/f7bbcb4e)_

#### メモリの使用量が多いため、インデックス再作成が行えませんでした

カタログルールインデクサーが過剰なメモリを消費し、完了に失敗して、不安定になったり、メモリ不足のエラーが発生したりする問題を修正しました。

_ACP2E-4303 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/c135fc3a)_

#### [CMS] スケジュールされた更新のプレビューリンクがメンテナンス ページにリダイレクトされる

設定可能な製品を使用したホームページリンクのスケジュール済み更新プレビューでは、製品のリストが正しく表示されます。 以前は、ユーザーをメンテナンスページにリダイレクトしていました

_ACP2E-4401 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/1c547060)_

#### 関連製品が自動的に削除されます

ターゲットルールと一致する関連製品は、再インデックスプロセス全体を通じて正しく関連付けられたままになりました

_ACP2E-4430_

### カタログ、GraphQL

#### GraphQl の無効な割引計算

カタログ価格に税が含まれるように設定されている場合、GraphQLで割引率と基本価格が正しく表示されるようになりました。 以前は、丸めエラーが発生していました（20% ではなく 19.99% が表示されるなど）。

_ACP2E-3993 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/e457c5e2)_

#### GetCart GraphQL Media Gallery フィールドが、キャッシュフラッシュ後に空のデータを返す

修正後、買い物かごリクエストに対するGraphQLの応答で、製品の media_gallery が期待どおりに返されます。

_ACP2E-4185 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/45cbf9b6)_

### カタログ，GraphQL，検索

#### 製品 graphql が、カテゴリ集計で無効なカテゴリを返しました

修正後、無効なカテゴリは、製品 GraphQl リクエストに対して返されません。

_ACP2E-2885 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/b12ffe36)_

### カタログ、パフォーマンス

#### 管理者のカテゴリの読み込みに時間がかかる

カテゴリ読み込みパフォーマンスが大幅に向上しました。 以前は、カテゴリの読み込みに時間がかかり、タイムアウトの問題が発生していました。

_ACP2E-3891 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/4ca73607)_

### カタログ、価格

#### 子製品に適用されたカタログ価格ルール割引が正しくありません

両方のルールの優先度が同じ場合に、バリエーションのカタログ価格ルールが親の設定可能な製品によって上書きされる問題を修正しました。

_ACP2E-3693 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/a20a6ff2)_

#### [Cloud] バンドル製品価格の問題

特別価格のバンドル製品の価格は、デフォルト以外の通貨の PDP/PLP で正しく表示されます

_ACP2E-4110 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/6e134409)_

### カタログ、製品

#### [ ランダムなバグ ] Fotorama lib が読み込まれない

システムが Fotorama ライブラリが適切に読み込まれ、添付されたすべての画像を期待どおりに画像ギャラリーに表示できるようになりました。 以前は、Fotorama ライブラリが正しく読み込まれないという問題により、最初の画像のみが表示されていました。

_AC-12124 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/45b51c9c) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/27217d0e)_

#### 「製品を手動で追加」リンクは常に表示されているはずです

既存の設定なしで設定可能な製品を作成する場合に、「製品を手動で追加」リンクが表示されない問題を修正しました。 リンクが常に表示されるようになり、管理者はダミーの設定を作成しなくても簡単にシンプルな製品を関連付けることができます。

_AC-13866 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39595) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/ef666cd9)_

#### バックエンドでの商品の編集オプション価格から余分な小数点以下の桁数を削除します

管理者で製品を編集すると、製品オプションの価格が小数点以下 2 桁に切り詰められる問題を修正しました。 システムでは、より高い小数点精度で価格を保持するようになり、保存後も正確な値が保持されるようになりました。

_AC-14050 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39655) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/3b5ac075)_

#### GraphQLを介した PDP に関連製品ルールを介した関連製品が表示されない

以前は、この修正が適用される前に、相対的な製品ルールが、ルールに一致する製品に対して空または null を返していました。 この修正が適用されると、一致した製品に対して、製品の相対ルールが正常に返されます。

_ACP2E-3949_

### カタログ、戻り値

#### [Cloud] バンドル製品行の注文返信ページの選択が自動的に解除される

以前は、管理パネルグリッド表示のバンドル製品の「一緒に出荷」リターンの場合、バンドル製品の「一緒に出荷」オプションの混乱を生み出した「項目を選択」オプションがありました。 この修正が適用されると、バンドル製品の出荷の場合、「項目を選択」オプションが表示されなくなります。

_ACP2E-4180_

### カタログ、検索

#### RestApi リクエスト &#39;/rest/default/V1/categories?searchCriteria%5Bpage_size%5D=1&#39;がタイムアウトエラーで失敗します

カテゴリ REST API リクエストがタイムアウトエラーで失敗しなくなりました。
以前は、/rest/default/V1/categories?searchCriteria[page_size]=1 へのリクエストは、特定のコード変更の後、タイムアウトで失敗する場合がありました。
AC-13358

_AC-13358 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/7bdafaa2)_

### コンテンツ

#### graphql （magento 2.4.6-p4） – ステータスがアクティブでない cms ページを取得しようとするとエラーが発生する

無効なCMS ページのGraphQL クエリで内部サーバーエラーが返される問題を修正しました。
現在は、クエリはエラーなしで適切な応答を取得します。

_AC-12302 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/38877) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/1b1baf1d)_

#### ウィッシュリスト共有フォームの名前フィールドにランダムコードを使用できる

悪意のあるコードがメッセージフィールドに入力され、メールで送信される可能性があるウィッシュリスト共有フォームの重大なサーバーサイドテンプレートインジェクション（SSTI）の脆弱性を修正しました。 この更新により、ブロックテンプレートディレクティブや安全でないパターンに入力検証が追加され、無効なコンテンツが検出された場合にエラーメッセージが表示されるようになりました。

_AC-12730 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39024) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/01cee3c3)_

#### csp_whitelist.xml をテーマに含めると、機能せず、断続的な問題が発生します

Web サイト領域ごとに CSP ホワイトリストのキャッシュを実装しました。

_AC-13069 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/38933) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/39672)_

#### magento 2.4.7 p2 にアップグレードすると、新しくアップロードされたファイルのメディアギャラリーが表示されない

新しくアップロードされたファイルは、アップグレード後にメディアギャラリーに表示されるようになりました。
以前は、Magento 2.4.7 p2 にアップグレードした後、新しくアップロードされた画像は、手動で同期されるまで Media Gallery に表示されませんでした。
AC-13262

_AC-13262 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39275)_

#### Media Gallery は、名前は同じで大文字と小文字が異なるディレクトリから、誤った画像を表示します

メディアギャラリーの特定のディレクトリにアップロードされたファイルが、名前が似ているが大文字と小文字が異なるディレクトリにも表示されるという問題に対処できるようになりました。

_AC-13489 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39382) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/39502)_

#### からギャラリー画像を完全に削除すると、範囲の役割/タイプが設定され続け（ベース/小/サムネール）、「古い」役割/タイプを再度追加した後で表示されます

システムはストア範囲で期待どおりに動作しています。画像は、デフォルトの範囲に従って、新しく追加された画像の役割/種類を継承します。

_AC-13556 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39481) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/39680)_

#### [ 小さなバグ ] フィールド値に `listing component` が含まれている場合、管理パネル `\` のフィルターがヒットしない

スラッシュを含むページタイトルをフィルタリングしている場合（例：Magento\Store）、システムは正常に動作します

_AC-13661 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39513) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/39535)_

#### エラー：商品が読み込まれる管理コンテンツの pagebuilder 用「Magento_Catalog/js/validate-product」のスクリプトエラー

この PR は、製品条件を含むページビルダーを編集する際の catalogAddToCart のスクリプトエラーを修正します

_AC-13891 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39604) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/39677)_

#### 製品ウィジェットを設定する際に、catalogAddToCart スクリプトエラーが発生します。

ページビルダーで製品ウィジェットを「条件の組み合わせ」で設定する際に発生していたスクリプトエラーを修正しました。 この問題は、フロントエンド JS ファイルが見つからないことが原因で、コンソールエラーが発生していました。 修正後、コンソールエラーなしでウィジェットは正しく読み込まれます。

_AC-13892 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/528af81a)_

#### 同じ識別子を持つウィジェットでのブロック選択

同じ識別子ブロックがある場合、ウィジェットの作成中にブロックの選択が正しく処理されるようになりました

_AC-14132 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39692) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/39722)_

#### 「ID が「0」のCMS ページが存在しません」というログフラッド

管理者ユーザーの作成後、および新しいページ system.log を作成する際に、システムは期待どおりに動作しています。エラーメッセージは表示されません

_AC-14254 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39743) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/39746)_

#### [GraphQl] ルートクエリ無限ループ

このチケットでは、リクエストパスとターゲットパスが同じGraphQL ルートクエリによって無限ループが発生し、最終的にタイムアウトした問題を修正しました。
2.4.9-alpha3 では、クエリがループではなく正しいエラー応答を返すようになりました。

_AC-14269 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39707) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/68a45d0a)_

#### 存在しないサイトマップは製品画像で応答します

「404 NOT FOUND」という応答を含む既存のサイトマップの応答にアクセスすると、システムが修正されるようになりました

_AC-14295 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39756) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/40135)_

#### カタログリンクウィジェットで間違った URL が使用されている

カタログの製品リンクとカタログカテゴリリンクを追加した後、システムはウィジェットを正しく処理し、html ソースにも正しい URL が表示されるようになりました

_AC-14437 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39464) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/39710)_

#### テーブルのプレフィックスは考慮されません

Adobe Commerceは、管理でデザイン/設定テーマグリッドを読み込む際に、データベーステーブルのプレフィックスを正しく尊重するようになりました。 以前は、app/etc/env.phpにテーブル接頭辞が設定されているAdobe Commerce 2.4.8 で、コンテンツ/デザイン/設定に移動すると、テーブル接頭辞が考慮されず、テーマのグリッドがレンダリングされないので、エラーが発生していました。

_AC-14556 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39847) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/1bc2d6d0)_

#### 柔軟性を高めるために、定数 IMAGE_FILE_NAME_PATTERN を public visible に変更します

GenerateRenditions.php の定数 IMAGE_FILE_NAME_PATTERN が公開され、開発者が画像レンディションを扱う際の柔軟性が向上しました。 この修正は、Magento 2.4.9-alpha3 に含まれており、完全なユニットおよび統合テストの範囲をカバーしています。

_AC-15338 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39733) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/68a45d0a)_

#### 複数出荷のレビュー注文ページに、間違った出荷方法が表示される

複数出荷のチェックアウトで、レビューオーダーページに誤った送料（10 INR ではなく 5 INR）が表示される問題を修正しました。更新により、各住所に対して正しい送料が表示されます。

_AC-15664 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/3cf1a106)_

#### bin/magento 設定 :show （または設定） design/theme/theme_id が失敗します

設定が存在しているにもかかわらず :showCLI コマンドの bin/magento config および config:set が design/theme/theme_id パスで失敗する問題を修正しました。
これでコマンドが正常に実行され、テーマ ID をエラーなく表示および設定できるようになりました。

_AC-5915 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/35751) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/64823f95)_

#### 幅が比較的小さい画像をアップロードできません

システムは、高さに対して比較的小さい幅の画像のサイズ変更に失敗しなくなりました。

_ACP2E-3558 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/9608ca21)_

#### ユーザーがウィジェット権限を持っていない場合、ページビルダーの製品コンポーネントは機能しません

修正前は、権限のないウィジェットにアクセスすると、ページで一般的なエラーが発生し、「読み込み中」のGIFが表示されていました。 修正後、モーダルウィンドウに「申し訳ありませんが、このコンテンツを表示するには権限が必要です」と表示されます。 メッセージ。

_ACP2E-3664 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2-page-builder/commit/bd9181b6)_

#### リモート ストレージ パスのスタイル構成の構成パスが正しくありません

修正後、リモートストレージパスのスタイル設定を設定すると、実際のAWS S3 パスのスタイル設定に影響します。

_ACP2E-3734 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/df92debe)_

#### GraphQLでページビルダー製品ウィジェットの順序が適用されない

GraphQLの「ルート」クエリ応答で、ページビルダー製品コンテンツタイプ内の正しい並べ替え順で製品が返されなかった問題を修正しました。

_ACP2E-3898 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2-page-builder/commit/bd9181b6)_

#### ICU ライブラリバージョンによる英語以外のストアフロントでの料金表示の問題

修正後、製品価格はヘブライ語（イスラエル）ロケールで正しく表示されます。

_ACP2E-3938 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/7accebfa)_

#### ストアコードをクリアしたデザイン設定の更新

設定キャッシュが正しく更新されないので、ストア表示コードを更新するとデザイン設定がクリアされる問題を修正しました。

_ACP2E-3941 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/462ede94)_

#### コンテンツのステージングプレビューが検索結果で機能しない

ステージングプレビューでの検索で、選択した範囲に従って製品を返すようになりました。 以前は、検索を実行すると、選択したストアに関わらず、デフォルトの範囲で結果が返されていました。

_ACP2E-4095_

#### ページビルダー – 製品状態ロジックの問題（または、ロジックが誤って表示される製品の数が少ない）

グローバルスコープを持つ属性が「任意の条件に一致」で使用された場合、ページビルダー製品ウィジェットが正しい結果を返すようになりました

_ACP2E-4096 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/e457c5e2)_

#### 製品カルーセルがページビルダーに間違った製品を追加する

修正前は、設定可能な製品は、その子のいずれかがフィルター条件を満たすと、PageBuilder の製品カルーセルリストに自動的に含まれていました。 現在は、修正後、子製品が単独で表示されない場合にのみ、親製品が含まれます。

_ACP2E-4341 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/61c96348)_

#### カテゴリ条件に複数のカテゴリがリストされている場合、製品リストウィジェットが誤った結果を返す

「カテゴリがいずれかのカテゴリ」という条件にリストされた複数のカテゴリがある場合、「カタログ製品リスト」ウィジェットに正確な結果が表示されるようになりました。 以前は、リストの最初のカテゴリのみが処理されていました。

_ACP2E-4353 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/0a3b7032) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2-page-builder/commit/1c1b3419)_

#### [Cloud] Media Gallery フォルダーの作成には、新しい Media Gallery で delete_folder 権限が必要です – create_folder のみを持つ役割はフォルダーを作成できません

以前は、この修正が実装される前は、コンテンツ作成フォルダー権限のみを持つ管理者ユーザーは、CMS media gallery にフォルダーを作成できませんでした。 ただし、修正後、メディアギャラリーのコンテンツ作成者は、フォルダー作成権限のみを持つフォルダーを作成できるようになりました。

_ACP2E-4376 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/61c96348)_

#### [QUANS]CMSページの複製

この修正より前は、カスタムレイアウトの更新を含む cms ページの複製は失敗していました。 カスタムレイアウトの更新を含むCMS ページをエラーなく複製できるようになりました。

_ACP2E-4449 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/f7bbcb4e)_

#### Web サイトレベルの権限を持つ管理者がダイナミックブロックを編集できない

Web サイト範囲権限を持つ管理者ユーザーは、アクセス可能な保存されたビューでバナーのコンテンツを編集できるようになりました。

_ACP2E-4468_

### 顧客/顧客

#### 管理者がCMS ページのコンテンツを介して CustomerCustomAttribute ブロックを追加した場合のストアフロントの例外

CMS ページコンテンツを介して CustomerCustomAttribute ブロックを追加するとストアフロント例外が発生し、ページが読み込まれない問題を修正しました。
ストアフロントが正常に表示され、コンテンツをレンダリングできない場合に意味のあるメッセージが表示されるようになり、重大なエラーを回避できるようになりました。

_AC-11004_

#### オンライン管理グリッドに、ユーザーがログイン、ログアウト、ログインするたびに重複行が表示されるようになりました

顧客がログアウトしてログインし直した際に、オンライン管理者グリッドに重複行が表示される問題を修正しました。
グリッドは、重複するエントリを作成するのではなく、既存のレコードを最新のアクティビティで更新するようになり、顧客セッションの正確なトラッキングを実現します。

_AC-11511 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/528af81a)_

#### 最小値と最大値の検証がストアフロントの DOB 属性に対して機能しない

このバグでは、（管理者では機能しているものの）生年月日（DOB）属性の最小および最大日付検証がストアフロントで機能しない問題を修正しました。
2.4.9-alpha3 で、検証により、許容範囲外の DOB を使用して顧客を保存することが正しくブロックされ、エラーメッセージが表示されるようになりました。

_AC-13535 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/68a45d0a)_

#### 管理者パネルの警告画面で、顧客としてログイン権限が取り消されたときに Ajax 401 エラーが読み込まれる

このバグは、ユーザー権限としてログインを取り消すと、生のHTMLを含む Ajax 401 エラーが警告ポップアップに表示される問題を修正しました。
修正後、生のHTMLではなく、通常の警告メッセージが正しく表示されるようになりました。
このソリューションは、Magento 2.4.9-alpha3 で提供されました

_AC-15336 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/68a45d0a)_

### フレームワーク

#### 無効なモジュールのコードを補完しています。

このプルリクエストは、コードのコンパイル前に無効なモジュールをエスケープします。

_AC-10933 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/38241) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/39723)_

#### カスタム DBトリガーでコマンド設定 :upgrade 実行中にエラーが発生しました

カスタムデータベーストリガーで、セットアップ中にエラーが発生しなくなりました :upgrade。
以前は、カスタムデータベーストリガー（例えば :upgrade ストアテーブルに対する AFTER INSERT）で bin/magento setup を実行すると、次のエラーが発生する場合がありました。
「警告：357 行目のvendor/magento/framework/Mview/View/Subscription.phpで null 型の値の配列オフセットにアクセスしようとしています」
AC-11487

_AC-11487 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/38481)_

#### [ 問題 ] メソッドの署名をインターフェイスと一致させる

getAttributes のメソッドシグネチャがインターフェイスと一致するようになり、メソッドを上書きする際のエラーを防ぎます。 以前は、getAttributes メソッドを上書きしようとすると、メソッドのシグネチャの不一致によってエラーが発生していました。

_AC-11578 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/38501) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/31955)_

#### Web サイト/グループ/ストアエンティティフォームは、拡張属性に複数の値フォーム要素を使用して拡張できません

この PR により、複数値のフォーム要素から web サイト/グループ/ストアフォームにデータを送信できるようになります。

_AC-11657 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/24070) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/24094)_

#### [ 問題 ]ui コンポーネントの validate-emails ルールを修正しました

システムは、UI コンポーネントに入力された複数のメールアドレスを正しく検証し、各メールが適切にトリミングおよび検証されていることを確認できるようになりました。 以前は、システムがメールアドレスのトリミングに誤った方法を使用しており、検証エラーが発生する可能性がありました。

_AC-11719 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/38528) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/33470)_

#### [ 問題 ] スコープリゾルバーの使用状況を削除します

この PR は、現在のストアではなく管理者 URL 設定をグローバルに解決します

_AC-11736 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/38566) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/38554)_

#### [ 問題 ] 冗長なメソッドを削除する

コード品質：機能を追加せずに親メソッドのみを呼び出す、AsynchronousOperations コンポーネントと Sales コンポーネントの冗長メソッドを削除し、コードの保守性を向上しました。

_AC-11915 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/29748) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/29147)_

#### Magento_Theme title.phtml テンプレートが PHP 8.2 で無効です

このプルリクエストにより、Php 8.x で null 見出しで作成されたCMSページが trim （）に null を渡すと例外がスローされる問題を修正しました。非推奨の機能：trim （）：文字列型のパラメータ#1 （$string）に null を渡す

_AC-12856 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39092) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/39398)_

#### フィールド項目の下にコメントが含まれているetc/adminhtml/system.xml ファイルで、xsd 検証が失敗します。

この PR により、コメントノード用 phpstorm の XML スキーマ定義が修正されます

_AC-12945 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39148) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/39867)_

#### デフォルトの Nginx 設定を使用したセットアップルートによるMagento バージョンの公開

現在、システムは期待どおりに動作しているので、サイトが動作しているMagentoの正確なバージョンが公開されません

_AC-13205 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39227) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/39228)_

#### [ 問題 ] オブジェクトの引数を名前付きパラメーターとして解凍する

このシステムは現在、PHP 8.1 の名前付きパラメータで配列を展開する機能を利用しています。これにより、array_values を呼び出す必要がなくなり、全体的なパフォーマンスが向上する可能性があります。 以前は、システムでオブジェクト引数をアンパックするために array_values を呼び出す必要がありました。

_AC-13210 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39233) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/37411)_

#### [ 問題 ] 見積もりアドレスのリファクタリングと検証メソッド

この PR には、doValidate メソッドのわかりやすさの向上が含まれています。

_AC-13214 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/38230) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/38219)_

#### Magento オプション —magento-init-params cli 実行時に使用しない場合は、

CLI コマンドの実行時に – magento-init-params オプションが使用されるようになりました。
以前は、CLI コマンドに – magento-init-params を渡しても、MAGE_MODE のようなパラメータには影響を与えませんでした。
AC-13231

_AC-13231 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39248) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/132b9e68)_

#### getItemsByColumnValue の型宣言が間違っています

システムは、getItemsByColumnValue 関数で、入力パラメーター$value を配列ではなくプリミティブ型として正しく定義し、関数が期待されたコレクションを返すようになりました。 以前は、単一の値を持つ配列が入力パラメーターとして使用された場合、関数は null を返し、IDE はエラーとしてマークしていました。

_AC-13240 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/33070) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/33120)_

#### ロックプロバイダーにファイルストレージを使用すると、クリーンアップが行われることなく、ファイルディレクトリが増え続けます

このプルリクエストでは、1 日に 1 回実行される新しい cronjob が導入され、過去 24 時間以内に変更されていないロックファイルが検索されるので、安全に削除できます。 これにより、lock files ディレクトリの内容が制御されます。
この cronjob は、ロックプロバイダーがファイルを使用するように設定されている場合にのみ実行します。他のファイル（データベース – デフォルト、zookeeper、キャッシュ）を使用している場合は実行しません

_AC-13367 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39369) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/39372)_

#### [ 問題 ] クリーンアップ：メソッド呼び出しから void 戻り値を使用しない。

この PR では、小規模なクリーンアップが行われます。 何も（void）返さないメソッドを呼び出し、その結果値を使用することもあります。 これは本当に必要ありません。

_AC-13664 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39524) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/39516)_

#### Magento 2.4.7 マルチストア実装での FPC に関連付けられたキャッシュキー

マルチストア設定のフルページキャッシュ（FPC）キャッシュキーに MAGE_RUN_CODE と MAGE_RUN_TYPE が含まれていなかったので、以前のバージョンと比較してキャッシュキーの動作に一貫性がなかった問題を修正しました。 キャッシュキーにストアコンテキストが正しく含まれるようになり、ストア間で適切なキャッシュ分離が確保されます。

_AC-13719 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39456) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/ae6f305b)_

#### [ 問題 ] [PHPDOC] Magento\Framework\Message\ManagerInterfaceの不正な phpdoc を修正します

この PR は\Magento\Framework\Message\ManagerInterfaceの不正な phpdoc を修正し、\Magento\Framework\Message\Manager内の重複する phpdoc をすべて削除します（inheritdoc syntaxe を使用）。

_AC-14312 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39593) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/39153)_

#### 大量の更新を行っているお客様に対しては、部分的なインデックス作成が機能しなくなります

多数の更新を行う顧客に対して、部分的なインデックス作成が機能するようになりました。
以前は、changelog テーブルの version_id 列の最大値に達すると、インデックスの更新が停止していました。
AC-14424

_AC-14424 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/7bdafaa2)_

#### Magento 2.4.8 では、セマンティックバージョニングに従わない開発パッケージを使用します

Magento 2.4.8 では、PHP 8.4 との互換性を保つため、pdepend/pdepend および phpmd/phpmd （3.x-dev）の開発版が必要です。
これらの開発バージョンは、SemVer 準拠パッケージを想定したサードパーティツールと競合し、一部のアップグレードを防ぎます。
一時的な回避策は、composer.json 内の開発バージョンのエイリアスを作成し（例：「3.x-dev as 3.99.0」）、セマンティックバージョニングを満たしながら互換性を確保することです。
これにより、PHP 8.4 のサポートが確保され、安定したリリースが利用可能になるまで競合が回避されます。

_AC-14519 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39796)_

#### 出荷ラベルをダウンロードした後、私たちはそれが出荷と取り扱い価格と一致していなかったいくつかの出荷金額を見ることができます。

配送ラベルの金額が、配送料と取扱価格に一致するようになりました。
以前は、配送ラベルをダウンロードした後、表示された金額が配送料および取扱価格と一致しませんでした。
AC-14560

_AC-14560_

#### MView の機能は、トリガーの実行時にエラーを無視します

トリガーの実行時に MView メカニズムがエラーを正しく報告するようになりました。
以前は、トリガーの実行中に発生したエラーはサイレントに無視され、通知が行われなくてもインデックスの更新が失われる可能性がありました。
AC-14567

_AC-14567 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/ae6f305b)_

#### [ 問題 ] レイアウト XML 結合の読み込み中に、不要な例外を回避します

この PR は、読み込む新しい関数（B/C 互換では、保護された_loadXmlString を上書きしません）を導入し、例外をスローしません

_AC-14580 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39877) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/37570)_

#### [ 問題 ]Vault Graph Ql モジュールでコンストラクタープロパティのプロモーションを使用する

この PR は、コンストラクタープロパティを VaultGraphQl モジュールのプロパティプロモーションに置き換えます

_AC-14616 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39900) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/36996)_

#### [ 問題 ] モジュールフロントエンドレイアウトのコード冗長性を削除しました。

この PR により、Magento_Msrp、Magento_LoginAsCustomerAssistance、Magento_Newsletter およびMagento_Sitemap モジュールのフロントエンドレイアウトのテーマレイアウトに対するコードの冗長性が解消されます。

_AC-14625 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/30673) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/30644)_

#### [ 問題 ] API の一部としてコンストラクターを含め、インラインドキュメント `CommandListInterface` 拡張する

この PR の更新により、Magento\Framework\Console\CommandListが API としてマークされ、コンストラクターが CommandListInterface に導入されて拡張性が向上しました。 また、コンソールコマンドを拡張する開発者にとって、明確さと保守性を強化するために、インラインドキュメントが改善されます。

_AC-14680 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/31102) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/37901)_

#### [ 問題 ]Microsoft IIS に関連するコードを削除します

この PR により、Microsoft Windows OS がサポートされていないことを示すMagento システム要件ドキュメントに従って、Mircrosoft IIS に関連するコードがクリーンアップされます

_AC-14702 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39910) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/39894)_

#### Magnifier.js 構文エラー

システムの拡大鏡機能は、以前と同じように機能し続ける必要があります。また、拡大鏡オプションはグローバル スコープで使用できません

_AC-14722 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/36200) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/39321)_

#### CLI コマンドのバックポ `setup:db:status` ト詳細モード

`setup:db:status` CLI コマンドで詳細モードがサポートされるようになりました。
これまで、アップグレードに必要なデータベースの変更を理解することは困難でした。 `bin/magento setup:db:status -v` を実行すると、スキーマとデータの違いに関する詳細情報が提供されるようになりました。
AC-14807

_AC-14807 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/7bdafaa2)_

#### tls および 2.4.8 で送信される SMTP メール

TLS を使用した SMTP メール送信が期待どおりに動作するようになりました。
以前は、TLS を使用して SMTP を介してメールを送信すると、「error:1408F10B:SSL routines:ssl3_get_record:wrong version number」というエラーが発生していました。
AC-14883

_AC-14883 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39947) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/3717e6cb) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/8b453942) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/d3ea191d)_

#### [ 問題 ] 静的コンテンツのデプロイにおける同時実行の問題を修正しました

この PR は、テーマが親と共にどのように定義されているかに応じて、複数の同時プロセスがスピンして同じテーマパッケージを処理するバグを修正します。

_AC-14944 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39990) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/39954)_

#### [ 問題 ] 8.1 より前のバージョンの PHP のレガシー互換性コードを削除する

このプルリクエストは、PHP &lt;8.1 で実行するように設計されたコードを削除します。
また、PHP_VERSION_ID の連絡先が利用可能かどうかをチェックする機能を削除しました。これは全ての PHP バージョンで利用可能です

_AC-14971 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39891) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/39882)_

#### ログイン時に FPC が機能しない

ログインしているユーザーに対して、フルページキャッシュ（FPC）が正しく機能するようになりました。
以前は、ログインすると、ホームページはキャッシュから読み込まれず、x-magento-cache-debug ヘッダーに HIT ではなく MISS が表示されていました。
AC-14999

_AC-14999 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/40007)_

#### 静的な分析のサポートを改善するために、特定の php クラスにジェネリック型を追加する

システムでは、汎用型定義を使用して、メソッド呼び出しが返す正確なクラスとして解釈することで、これを大幅に改善するようになりました

_AC-15013 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/40017) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/40119)_

#### [ 問題 ]SchemaBuilder のエラー処理を改善する

この PR により、db スキーマのエラーメッセージ処理が改善されます。 大量のデバッグを行わずに問題を特定するのに役立ちます。

_AC-15020 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39816) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/39799)_

#### Rest API:null でのメンバー関数 getVideoProvider （）の呼び出し

子製品にYouTube ビデオのみが含まれ、他の画像が含まれていない場合に、設定可能な製品の子 API を呼び出すと、500 内部サーバーエラーが返される問題を修正しました。
ExternalVideoEntryConverter の null 参照が原因でエラーが発生しました。
現在は、API は、外部ビデオデータを含むメディアギャラリーエントリを持つ子製品を、エラーを発生させずに正しく返します。
これにより、REST API を使用して、子製品のすべてのメディアタイプが適切に取得されます。

_AC-15046 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/40021)_

#### [W3C] cookie スクリプトタグ宣言から text/javascript を削除

この PR により、HTML5 への準拠を目的として、Cookie スクリプトタグから不要な type=&quot;text/javascript&quot;属性が削除されました。

_AC-15061 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39982) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/39983)_

#### [ 問題 ]PHPDoc コメントの入力ミスをいくつか修正します

この PR により、phpdoc 内のいくつかの入力ミスが修正されます

_AC-15075 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/40042) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/38809)_

#### [ 問題 ] フレーズ呼び出しでの sprintf の使用を削除する

この PR により、Magento コアのフレーズ関数呼び出しでの sprintf の使用が削除されます。

_AC-15183 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/40050) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/40033)_

#### アクティブなアプリケーション ロックを持つマルチスレッド インデクサーで、すべての無効なインデックスを再作成できません

この問題は、use_application_lock が有効な場合に発生していたマルチスレッドインデクサーの失敗を修正しました。
以前は、並列処理中に DB ロックが失われ、インデクサーが「動作」状態のままになり、SQL エラーがスローされていました（テーブルが見つかりません）。
Magento 2.4.9-alpha3 では、この修正により、アプリケーションロックが有効な状態で、インデクサーが正しくインデックス再作成されるようになります。

_AC-15270 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/40102) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/68a45d0a)_

#### Magento\Framework\Escaper の戻り値の型が不明または無効です

レベル 5 で phpstan を用いた静的解析を行う場合、エスケーパ法の型を受け付ける

_AC-15272 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/40012) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/40114)_

#### [ 問題 ] キュー固有の設定が、デフォルトの max-messages 値を超えることを許可します

システムでは、キュー固有の設定がデフォルトの max-messages 値を超えることができるようになりました

_AC-15284 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/40121) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/40110)_

#### [ 問題 ] ニスを使用する際に、同じクエリを持つ同じページの重複したキャッシュ fpc

この PR は、クエリパラメーターの順序を正規化し、同一のリクエストに対して一貫したキャッシュキーを確保することにより、Varnish を使用する際に重複したフルページキャッシュエントリを修正します。
異なるシーケンス内の同じパラメーターを持つ URL のキャッシュヒット率とパフォーマンスを向上させます。

_AC-15325 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39706) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/39704)_

#### コミュニティテーマには、Commerce edition モジュールのリソースが含まれています

コミュニティテーマからCommerce専用のスタイルリソースを、それぞれのモジュールディレクトリに移動して削除しました。 これにより、未使用の CSS がコミュニティ編集にバンドルされるのを防ぎ、不要なペイロードを減らし、Commerce モジュールが有効な場合に適切なスタイル設定を行いながら、無効なスタイルルールを排除します。

_AC-15347 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/21446) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/9bcd880a)_

#### [ 問題 ] Url にストアコードを追加することはグローバルでなければならない

この PR は、「Url にストアコードを追加」設定がコアコードのグローバルスコープを使用して取得されることを確認することにより、問題に対処しています

_AC-15365 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/40069) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/40065)_

#### [ 問題 ] 無効でない場合にのみ、宣言されていないプラグインをログに記録します

この PR により、実際には宣言されておらず、使用されていない（有効なインスタンスと見つからないインスタンス）プラグインが修正されてログに記録されます。

_AC-15386 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/40086) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/40081)_

#### [ 問題 ] 小さなクリーンアップにより、配列から重複したキーが削除される

システムは小規模なクリーンアップを実行し、配列に関連するエラーが見つからず、「Weight （and above）」の値を持つ 2 つの重複キーがあります

_AC-15414 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39851) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/39844)_

#### Magento 2.4.8-p2、magento/framework バージョン 103.0.8-p2：存在しないメソッドを呼び出す EmailMessage クラス

EmailMessage クラスでメール本文の取得を正しく処理できるようになりました。
以前は、magento/framework バージョン 103.0.8-p2 のMagento 2.4.8-p2 で、Magento\Framework\Mail\EmailMessage クラスが Symfony メールメッセージオブジェクト上の存在しないメソッド（getTextBody）を呼び出そうとしていました。 これは、サードパーティのモジュールやカスタマイズがメール処理にこの方法を使用した場合にエラーが発生する原因となりました。
現在は、EmailMessage クラスは未定義のメソッドを呼び出さなくなり、これらのエラーを防いでいます。 AC-15446

_AC-15446 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/40170) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/059fd469) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/e9412b24)_

#### [Magento 2.3.x] データ/スキーマパッチ getAliases （）が `setup:upgrade` 中にエラーを発生させる

getAliases （）はセットアップ中にエラーを引き起こします :upgrade、この PR は同じことを修正します

_AC-15559 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/31396) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/38239)_

#### 操作に対する照合順序の不適切な組み合わせ

_AC-15614 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/40138) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/44329e9d)_

#### [ 問題 ] [PHPDOC] 不正な phpdoc Magento\Framework\DB\Adapter\AdapterInterface::quoteColumnAs （）

この PR は\Magento\Framework\DB\Adapter\AdapterInterface::quoteColumnAs （）の PHPDoc を更新し、string に加えて$alias パラメーターを null にできることを正しく反映します。 これにより、レベル 5 以降の PHPStan の問題が解決され、コード品質ツールの互換性が向上します。

_AC-15626 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39598) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/39581)_

#### urlrewrite モジュールでの照合順序の不適切な組み合わせ

_AC-15647 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/40189) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/44329e9d)_

#### `\Magento\Framework\Escaper::escapeScriptIdentifiers` で条件が満たされたことはありません

\Magento\Framework\Escaper::escapeScriptIdentifiers で到達できない条件を修正しました。false のチェックを null に置き換え、preg_replace の戻り値に合わせ、機能に影響を与えることなくコードの精度を向上させました。

_AC-15667 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/40195) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/cc0ec250)_

#### Varnish 7.3 （最新版） – Sub Categories のリンク/デフォルトのカテゴリのオプションがストア フロント ホーム ページに表示されません

Varnish 7.3 を使用する際にストアフロントのホームページでサブカテゴリリンクが欠落していた原因が、Magento コードの不具合ではなく、ESI のリクエスト処理とサーバー設定であることが確認されました。

_AC-15674 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/3cf1a106) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/9a62604c)_

#### [ 問題 ] ログにデバッグデータ `cache_invalidate` 追加する

この PR により、cache_invalidate ログが強化され、リクエストコンテキストと、完全なキャッシュパージのスタックトレースが含まれるようになり、デバッグと可視性が向上しました。
これは、既存の機能を変更することなく、予期しない完全なキャッシュ無効化の原因を特定するのに役立ちます。

_AC-15719 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/40204) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/40196)_

#### [ 問題 ] コンポーザーのオートローダー除外リストが少し改善されました。

この PR により、テスト クラスをスキップするように Composer オートローダーの除外が絞り込まれ、不要なクラスマップ エントリが減り、PSR-4 の警告が発生しなくなります。

_AC-15743 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/40109) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/40107)_

#### [ 問題 ]`db_schema.xml` での `comment=""` 宣言によってダウンタイムなしのデプロイメントが中断されないようにする

システムは、comment=&quot;&quot;を含む db_schema.xml 宣言によってダウンタイムなしのデプロイメントが中断されるのを防ぐようになりました

_AC-15980 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/40254) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/40242)_

#### `\Magento\Framework\Filesystem\Glob::glob(...)` キャッシュをクリアできません

この PR アップデートにより、\Magento\Framework\Filesystem\Globが使用する内部静的キャッシュをクリアする方法が導入され、ファイル構造が変更された場合に新しく正確な結果が得られるようになりました。 特に、グロブ結果を最新の状態に保つ必要があるテストシナリオや長時間実行されるプロセスにおいて、信頼性と開発者のエクスペリエンスを向上させます。

_AC-15989 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/35741) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/35742)_

#### ReadME リーダーリンクの URL には、永続的なリダイレクトがあります

永続的にリダイレクトされ、期限切れの URL を正しい作業リンクに置き換え、投稿者とメンテナンスページが正しく開くようにすることで、README リーダーリンクを更新しました。

_AC-16046 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/40292) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/913bf1a6)_

#### [ 問題 ] [PHPDOC] 不正な phpdoc Magento\Eav\Model\ResourceModel\Entity\Attribute\Collectionを修正します

属性コレクション内の joinLeft （）の PHPDoc 注釈を修正して、適切な配列定義を可能にし、コードの正確性と PHPStan などのツールとの互換性を高めました。

_AC-16187 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/40354) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/39155)_

#### 1 つのコマンドの失敗が、後続の CLI コマンドの実行を停止することなく、エラー（ファイルまたは stderr）をログに記録することを確認します。

システムは、次の CLI コマンドの実行を停止することなく、1 つのコマンドの失敗でエラー（ファイルまたは stderr）を記録できるようになりました

_AC-16244 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/40006) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/40063)_

#### [ 問題 ] PageCache カーネルの$maxAge に int タイプを追加します

この PR により、PageCache カーネルの$maxAge パラメーターが、型の安全性を向上させ、キャッシュ処理での PHPStan/静的分析エラーを防ぐために、厳密に整数として入力されるようになります。

_AC-16313 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/40438) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/36600)_

#### フェイクモジュールには、拡張機能リポジトリ内の dev/ ディレクトリが必要です

_AC-16487_

#### 買い物かごに追加イベント：空の価格

買い物かごへの追加プロセス中に、checkout_cart_product_add_after イベントのオブザーバーで製品価格が null として返される問題を修正しました。
現在は、基本価格と関連する価格の値が正しく取得され、オブザーバーやカスタム実装で正確なデータを利用できるようになります。

_AC-5966 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/35638) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/3b5ac075)_

#### PHP8.1 タイプのバグ修正

関連する製品は、厳密な処理モードがアクティブでない場合や製品情報が使用可能な場合、false ではなく空の配列に初期化されるようになりました。 この変更により、関連する製品を処理する後続のロジックが一貫して動作し、製品準備プロセスの安定性と予測可能性が向上します。

_AC-6017 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/35808) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/35842)_

#### タイプ「Magento\Customer\Api\Data\GroupInterface」が必要です。 「Magento\Customer\Model\Group」が見つかりました。

GroupFactory を使用して GroupRepositoryInterface を介して顧客グループを保存すると、タイプエラーが発生する問題を修正しました。
以前は、リポジトリは GroupInterface を想定していましたが、グループモデルインスタンスが渡され、致命的なエラーが発生していました。
現在は、適切なインターフェイス実装を確保することにより、リポジトリを通じて顧客グループを正常に保存できます。
これは、顧客グループをプログラムで作成または更新する際の IDE の警告および実行時エラーを解決します。

_AC-6909 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/36269)_

#### 資格情報に関するフィールド検証

必須のカスタムフィールドが入力された後でも、クレジットメモページのフィールド検証が送信されない問題を修正しました。
これで、検証が正しく機能し、すべての必須フィールドが入力されると、送信ボタンが有効になります。

_AC-8308 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/37182) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/64823f95)_

#### [ 問題 ] フレームワークから禁止されている `@author` タグを削除する（パート 3）

システムは、特定のモジュールから禁止されている `@author` タグを削除することで、コーディング標準に準拠するようになり、全体的なコード品質が向上します。 以前は、一部のモジュールにこのタグが含まれていることは、確立されたコーディング標準に違反していました。

_AC-8343 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/37270) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/37020)_

#### [ 問題 ] 友人グラフ ql を送信モジュールでコンストラクタープロパティのプロモーションを使用する

「友達に送信」GraphQLモジュールのコンストラクタープロパティの昇格を利用して、コードの読みやすさを向上し、複雑さを軽減するようになりました。 以前は、このモジュールは、多数の行を占めるプロパティを使用していたので、コードがより複雑で読みにくくなっていました。

_AC-8346 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/37235) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/37197)_

#### [ 問題 ] 禁止された `@author` タグを削除する

この PR は、コードベースから `@author` タグを削除します

_AC-8349 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/37266) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/37016)_

#### [ 問題 ] 禁止された `@author` タグを削除する

この PR は、コードベースから `@author` タグを削除します

_AC-8350 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/37265) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/37015)_

#### [ 問題 ] `@author` から禁止されている `Magento_Downloadable` タグを削除する

システムは、特定のモジュールから禁止されている `@author` タグを削除することで、コーディング標準に準拠するようになり、全体的なコード品質が向上します。 以前は、一部のモジュールにこのタグが含まれていることは、確立されたコーディング標準に違反していました。

_AC-8355 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/37251) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/37001)_

#### [ 問題 ] 禁止された `@author` タグを削除する

このシステムは、特定のモジュールから禁止されている `@author` タグを削除することで、コーディング標準に準拠するようになり、コードの品質と一貫性を向上させます。 以前は、一部のモジュールにこのタグが含まれていることは、確立されたコーディング標準に違反していました。

_AC-8358 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/37264) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/37014)_

#### [ 問題 ] 禁止された `@author` タグを削除する

この PR は、コードベースから `@author` タグを削除します

_AC-8359 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/37262) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/37012)_

#### [ 問題 ] 禁止された `@author` タグを削除する

システムは、特定のモジュールから禁止されている `@author` タグを削除することで、コーディング標準に準拠するようになり、全体的なコード品質を向上させます。 以前は、一部のモジュールにこのタグが含まれていることは、確立されたコーディング標準に違反していました。

_AC-8360 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/37261) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/37011)_

#### [ 問題 ] 禁止された `@author` タグを削除する

このシステムは、特定のモジュールから禁止されている `@author` タグを削除することで、コーディング標準に準拠するようになり、よりクリーンで標準化されたコードを保証します。 以前は、一部のモジュールにこのタグが含まれていることは、確立されたコーディング標準に違反していました。

_AC-8361 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/37260) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/37010)_

#### [ 問題 ] 禁止された `@author` タグを削除する

この PR は、コードベースから `@author` タグを削除します

_AC-8362 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/37259) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/37009)_

#### [ 問題 ] 禁止された `@author` タグを削除する

システムは、特定のモジュールから禁止されている `@author` タグを削除することで、コーディング標準に準拠するようになり、全体的なコード品質が向上します。 以前は、一部のモジュールにこのタグが含まれていることは、確立されたコーディング標準に違反していました。

_AC-8363 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/37258) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/37008)_

#### [ 問題 ] `@author` および `Magento_Backup` から禁止されている `Magento_Bundle` タグを削除する

この PR は、コードベースから `@author` タグを削除します

_AC-8367 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/37244) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/36979)_

#### [ 問題 ] 禁止された `@author` タグを削除する

システムは、特定のモジュールから禁止されている `@author` タグを削除することで、コーディング標準に準拠するようになり、全体的なコード品質が向上します。 以前は、一部のモジュールにこのタグが含まれていることは、確立されたコーディング標準に違反していました。

_AC-8375 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/37257) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/37007)_

#### [ 問題 ] 禁止された `@author` タグを削除する

システムは、特定のモジュールから禁止されている `@author` タグを削除することで、コーディング標準に準拠するようになり、全体的なコード品質が向上します。 以前は、一部のモジュールにこのタグが含まれていることは、確立されたコーディング標準に違反していました。

_AC-8376 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/37256) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/37006)_

#### [ 問題 ] 禁止された `@author` タグを削除する

システムは、特定のモジュールから禁止されている `@author` タグを削除することで、コーディング標準に準拠するようになり、全体的なコード品質が向上します。 以前は、一部のモジュールにこのタグが含まれていることは、確立されたコーディング標準に違反していました。

_AC-8400 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/37254) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/37004)_

#### [ 問題 ] 禁止された `@author` タグを削除する

システムは、特定のモジュールから禁止されている `@author` タグを削除することで、コーディング標準に準拠するようになり、全体的なコード品質が向上します。 以前は、一部のモジュールにこのタグが含まれていることは、確立されたコーディング標準に違反していました。

_AC-8401 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/37255) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/37005)_

#### [ 問題 ] サービス URL 生成の拡張性を向上させる

プラグインを使用してサービス URL 生成機能をカスタマイズできるようになり、メンテナンス性の高い変更アプローチが促進されます。 以前は、この機能のカスタマイズは、環境設定を通じて実現されていましたが、これはそれほど効率的でも保守的でもないかもしれません。

_AC-8813 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/37404) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/37403)_

#### [ 問題 ] カタログ検索の変数名を修正する

システムが検索エンジンモジュール内の変数に正しく名前を付け、コードの明確さと保守性が向上しました。 以前は、無関係な変数名$defaultCountry が検索エンジンモジュールで使用され、混乱を招いていました。

_AC-9215 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/37810) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/33533)_

#### allow_parallel_generation は、環境変数を使用して設定する必要があります

修正後、「MAGENTO_DC_CACHE__ALLOW_PARALLEL_GENERATION」環境変数を使用して「allow_parallel_generation」設定を指定できます。

_ACP2E-3673 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/b12ffe36)_

#### [Cloud] Magento 2 で db_schema.xml ファイルを使用してテーブル列のタイプを Int から Decimal に変更すると、エラーが発生する

列データタイプの変更が正しく機能しない。 以前は、次のエラーがスローされていました：属性「identity」は許可されていません。

_ACP2E-3709 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/df92debe)_

#### Adobeでの新通貨（XCG）のサポート

カリビアンギルダー（XCG）が通貨リストに追加されました。

_ACP2E-3790 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/520f9e30)_

#### 新しい検証が追加されたことによるアップグレード 2.4.7-p5 の問題

SchemaBuilder クラスで、未定義の配列キー「列」がスキーマの作成中または更新中にクラッシュする問題を修正しました。 これは、「列」キーを含まないテーブルデータを処理しているときに発生しました。

_ACP2E-3871 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/9ad7d277)_

#### [QUANS]Server の問題。無効な S3 アクセス キーが原因である可能性があります。

AWS S3 の資格情報が正しくなければ、ページがストアフロントに無限に読み込まれなくなりました。

_ACP2E-3890 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/2a1e1e55)_

#### [QUANS][Cloud] Minify js が機能しない

JS の縮小が有効な場合、mage/backend/tabs.min.j、jquery/jquery.validate.min.js およびMagento_PageBuilder/js/form/element/validator-rules-mixin.min.js の JS ファイルが完全かつ正しく縮小されるようになりました。 その結果、ページビルダー CSS クラスフィールド検証が期待どおりに動作します。

_ACP2E-3925 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/47721be6)_

#### PHP8.4 非推奨エラー：Adobe Commerce 2.4.8 へのアップグレード後の E_USER_ERROR

*リリースノートは必要ありません*
お客様が直面するシナリオは、この修正の影響を受けません。

_ACP2E-3963 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/7accebfa)_

#### Cron ジョブでデータベース・テーブルがクリアされない：Galera のクラッシュによる停止が発生

大量の削除操作を避けるために、変更ログテーブルのクリーンアップがバッチで実行されるようになりました。

_ACP2E-3995 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/52f46328)_

#### 縮小されていない JS は、「enable js の縮小」を無視して読み込まれることがあります。

修正の前は、縮小化を有効にしていた場合でも、一部の JS ファイルが「min」プレフィックスを付けずにリクエストされ、結果としてステータスコード 404 が返されていました。 修正後、縮小が有効になっている場合、縮小されていない JS リソースはリクエストされません。

_ACP2E-4058 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/6dd3fa99)_

#### カスタム属性グループの日付属性で、管理者に日付選択を表示できない

カスタム属性グループに割り当てたときに、日付属性のカレンダーポップアップが画面の外に表示される問題を修正しました。

_ACP2E-4060 - [GitHub の問題 &#x200B;](https://integration-5ojmyuq-3ssteurpe3xzy.us-5.magentosite.cloud/) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/6dd3fa99)_

#### 実稼動 ACL 権限チェックがパフォーマンスの低下の原因である – populateAcl メソッドがボトルネック

最適化された ACL ルール処理

_ACP2E-4114 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/98f028ab)_

#### AC-15867 + ACP2E-4296 および SCD Compact の最新バージョンでチェックアウトが読み込まれない

この修正を行う前は、head セクションを介してカスタム JavaScript を読み込むと、問題が発生する場合がありました。 新しい設定の導入後は、これらのスクリプトを自動的に延期できるため、Magento 2 フレームワークとの互換性が向上します。

_ACP2E-4319 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/1c547060)_

#### 非推奨の警告：既存のロケールを変更するには moment.updateLocale （localeName, config）を使用します。 moment.defineLocale （localeName, config）

修正前は、ブラウザーコンソールに非推奨の警告が表示されていました。 現在は、修正後に、そのような警告は表示されません。

_ACP2E-4338 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/2687b487)_

#### REST API を使用して製品の変更を保存する際に [CLOUD] DateTimeZone エラーが発生する

修正する前に、コード「default」を含むストアがない場合、製品の更新 REST API リクエストはエラーを生成します。 現在は、修正後、「デフォルト」ストアが存在するかどうかに関係なく、製品の更新リクエストは正常に実行されます。

_ACP2E-4339_

#### MariaDB 10.11 との非互換性

以前は、MariaDB 10.11 を使用する際に最新バージョンのMagento 2 をインストールできず、セットアッププロセスが完了しませんでした。 この問題は、インストール時に MariaDB 10.11.x をサポートするようにデータベースの互換性処理を更新することで解決されました。

_ACP2E-4367 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/31258bf6)_

### フレームワーク、検索

#### Opensearch 2.19.1 は、1 つの価格のカテゴリに対して illegal_argument_exception を返します。

Opensearch は、同じ価格を持つすべての製品を含むカテゴリに対して illegal_argument_exception をスローしなくなりました。 以前は、「[from] パラメーターは負にできません」という例外がありました。

_ACP2E-3896 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/3ad96f6a)_

### GraphQL

#### GraphQLへの注文が正常に行われず、発送方法が無効になる

無効または無効な発送方法を使用すると、GraphQL経由で注文される可能性がある問題を修正しました。
現在は、選択した発送方法が検証され、使用できない場合はエラーが返されるので、注文を作成できません。

_AC-10472 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/38268) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/a8cf637b)_

#### GraphQl クエリの実行中に例外がスローされる

無効な並べ替えパラメーターが原因でGraphQL クエリが例外をスローした問題を修正しました。修正後、クエリは、エラーや例外ログを生成せずに正常に実行されます。

_AC-14835 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/a8cf637b)_

#### custom_attributesV2 を含む AddProductsToCart ミューテーションを介してギフトカード製品を買い物かごに追加する際の内部サーバーエラー

custom_attributesV2 を使用して、GraphQLを介してギフトカード（および同様の custom-option）商品を買い物かごに追加する際にトリガーされる内部サーバーエラーを修正しました。

_AC-15856 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/7fa400a7)_

#### クエリのフィールド `Country`Null

仮想品目、払い戻し品目、出荷品目を含む注文が、出荷数量計算に仮想品目が含まれることで処理中のままになり、注文の状態が正しく完了する問題を修正しました。

_AC-7731 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/ef666cd9)_

#### 「number」属性を持つGraphQL クエリ「customerOrders」が原因で、内部サーバーエラーが発生する

GraphQL customerOrders クエリが、数値フィールドをリクエストする際に内部サーバーエラーを返す問題を修正しました。
現在は、リゾルバーが注文増分 ID を正しく返し、クエリが正常に実行されて注文番号を取得できるようになりました。

_AC-8949 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/3b5ac075)_

#### GraphQLの注文配置に対する応答に例外メッセージが含まれていない

別の形式でエラーを返していた以前の変更を元に戻しました。 潜在的なエラーが、GraphQLのスキーマを壊すことなく、一貫した方法で返されるようになりました。 これは既知の BIC として追加する必要があり、https://jira.corp.adobe.com/browse/ACP2E-3399?focusedId=45248897&page=com.atlassian.jira.plugin.system.issuetabpanels:comment-tabpanel#comment-45248897 で PM により承認されています。

_ACP2E-3399 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/9608ca21)_

#### 注文配置に対するGraphQL応答が部分的にローカライズされている

placeOrder GraphQl ミューテーションによって返されたエラーが完全にローカライズされていませんでした。 現在は、多言語コンテキストで、エラーが適切に翻訳されています。

_ACP2E-3506 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/9608ca21)_

#### GraphQL API を並べ替えるための同時呼び出し – 同じ商品が別の行に追加される

GraphQL API の並べ替えの同時呼び出しによって、同じ商品が異なる行として追加され、データの不一致が発生する問題を修正しました。

_ACP2E-3774 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/c8ba4ab1)_

#### updateCustomerEmail GraphQL mutation （Change email Address）がメール通知をトリガーしない

以前は、アカウントのメールアドレスを正常に更新した後、メールが顧客に送信されませんでした。 修正が適用された後、お客様はメールアドレスを正常に更新した後、メール通知を受信するようになりました。

_ACP2E-3785 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/c8ba4ab1)_

#### updateGiftRegistry 変更を介してギフトレジストリで動的属性が更新されない

以前は、この修正前は updateGiftRegistry のミューテーションによって、ギフトレジストリのカスタム属性がGraphQL ミューテーションによって変更または更新されていませんでした。 この修正が適用されると、updateGiftRegistry ミューテーションを使用して、ギフトレジストリの動的属性を正常に更新できます。

_ACP2E-3805 - [GitHub の問題 &#x200B;](https://mcstaging.briscoes.co.nz/)_

#### 製品が削除されると customerOrders graphql がエラーを返す

注文の製品が削除されても、customerOrders の graphql リクエストでエラーがスローされなくなりました。 以前は、「内部サーバーエラー」エラーがスローされていました。

_ACP2E-3936_

#### 顧客注文GraphQL：関連付けられた商品の商品カテゴリを取得すると、「個別に表示されない

修正の前は、注文に非表示の製品が含まれている場合、そのカテゴリには、顧客注文 GraphQl 応答で空の配列が表示されます。
現在は、修正後に、製品が非表示になっていても、顧客注文 GraphQl リクエストの応答に製品カテゴリが含まれるようになりました。

_ACP2E-3945 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/2a1e1e55)_

#### ウィッシュリスト項目は、GraphQL リクエストの 1 つの web サイト内のストアビュー間で共有されません

修正する前は、ウィッシュリストの項目はストア ID でフィルタリングされていました。 修正後、ウィッシュリストの項目が web サイトでフィルタリングされるようになりました。

_ACP2E-3987 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/2a252ae6)_

#### 実稼動環境の [Cloud] getRemoteAddress の戻り 127.0.0.1

この修正以前は、アプリケーションサーバーを使用したときに、リモートアドレスが正しく決定されませんでした。 修正後、nginx およびヘッダー設定の適切なヘッダー設定と組み合わせて、リモートアドレスが適切に決定されます。

_ACP2E-3991 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/47721be6)_

#### [QUANS] GQL 注文プレースメントの例外処理の動作の復帰を確認する

placeOrder ミューテーションに対して後方互換性のない変更を処理しました。

_ACP2E-4031 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/52f46328)_

#### GraphQL経由で注文すると、翻訳されたメッセージがエラーコードにマッピングされる問題

GraphQL リクエストのエラーコードのマッピングに翻訳済み例外メッセージが使用され、既知のエラーで不明なエラーコードが発生する問題を修正しました。

_ACP2E-4033 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/fab20b00)_

#### [CLOUD] 日付に対して顧客注文フィルターが機能しない

修正後、日付範囲フィルターを使用してGraphQLから注文を取得すると、正しい結果が返されます。

_ACP2E-4090 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/a1c57b2e)_

#### ACP2E-4031 で発生した問題に対処します

修正が行われる前は、エラーノードの位置は 2.4.7 および 2.4.9 バージョンとのシームレスな互換性を提供していませんでした。 修正後、両方のバージョンに対応するようにエラーノードが適切に配置されます。

_ACP2E-4115 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/e457c5e2)_

#### Graphql 呼び出しに子インスタンスがあっても在庫切れを示すバンドルの親

修正後、GraphQLを使用して商品リストをリクエストすると、バンドル商品の正しい在庫ステータスが返されます。

_ACP2E-4168 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/a1c57b2e) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/inventory/commit/5632fb5e)_

#### SWAT のGraphQLの例外

修正後、GraphQL リクエストの応答は、HTTP 仕様におけるGraphQLと連携されます。 リクエストの解析が不可能な場合や、リクエストが許可されていない場合、またはリクエストに別の一般的な問題がある場合に、4XX 応答コードが返されます。 リクエストが解析され、処理できる場合は、200 の応答コードが返されます。

_ACP2E-4194 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/45cbf9b6)_

#### リストが顧客に割り当てられた後、製品が比較リストから削除されない

ゲストユーザーの比較リストを顧客アカウントに割り当てた後に、ゲストとして追加された製品を顧客が削除できるようになりました。
以前は、ゲストが追加した項目が割り当て後に顧客のアカウントに正しくリンクされていなかったので、削除操作に失敗していました。

_ACP2E-4244 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/c135fc3a)_

#### updateCartItems GraphQLの誤ったエラー応答

以前は、数量が不十分な項目に対して graphQL リクエストを行った場合、その項目が利用できなかった場合でも、リクエストされた数量と価格の計算と共に、エラーコードを含む適切なエラーメッセージが返されていました。 この修正が適用された後、エラーコードを含む適切なエラーメッセージが返され、応答で使用できない場合、項目の数量が古い値に設定されるようになりました。

_ACP2E-4283 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/cbca0396)_

#### MergeGuestOrder プラグインのクロスウェブサイト ゲスト注文割り当てバグ

修正前は、ゲスト注文の顧客の割り当てでは、アカウント共有オプションを検討していませんでした。 修正後、顧客と注文ストアが一致する場合、注文が顧客に割り当てられます（顧客アカウント共有オプションが「Web サイトごと」に設定されている場合）。

_ACP2E-4312 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/c135fc3a)_

### GraphQL、インベントリ/MSI

#### Magento 2 GraphQLの only_x_left_in_stock の問題 – しきい値を使用する際の計算が正しくない

MinQty の二重控除が正しくないため、only_x_left_in_stock GraphQL フィールドが null を返す問題を修正しました。しきい値に基づいて正確な在庫値を返すようになりました。

_AC-15832 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/inventory/commit/35458c7f)_

#### GraphQL mergeCart のミューテーションの不一致

修正後、結合カートのGraphQLリクエストは、在庫設定を考慮して、製品数量を適切にチェックします。

_ACP2E-4184 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/inventory/commit/5632fb5e)_

### GraphQL、商品

#### 製品 graphql の MediaGalleryInterface に media_type がありません

MediaGallery GraphQL リクエストに、商品の画像タイプの「タイプ」フィールドが含まれるようになりました。 以前は、この「types」フィールドは MediaGallery GraphQL リクエストに存在しませんでした。

_ACP2E-3880 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/3ad96f6a)_

### GraphQL、セキュリティ

#### GraphQLを使用したカスタマーパスワードのリセットが制限に従わない

GraphQLの変更点を通じて行われたお客様のパスワードリセットリクエストが、ストア/設定/お客様/お客様の設定/パスワードリセットのオプションで設定されたパスワードリセット制限に準拠しない問題を修正しました。 これらの設定が正しく適用されるようになりました。

_ACP2E-3992 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/6dd3fa99)_

### インポート/エクスポート

#### [ 問題 ] パラメータータイプを修正する

以前に文字列として定義された値が配列として正しく設定されるインポート/エクスポートモジュールのパラメータータイプの不一致を修正しました。 これにより、書き出しコントローラからの期待される入力に合わせることができ、静的解析の警告を回避できます。

_AC-11665 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/38529) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/64823f95)_

#### [ 問題 ] Copyedit:「coping」を「copying」に変更します

PR では、「コピー」のスペルを修正するためにマイナーコピー編集を修正しました

_AC-13300 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39311) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/39307)_

#### REST エンドポイント製品の読み込み JSON が必須フィールドを検証しない

読み込みプロセス（管理者または API）を使用して新しい製品を作成する際に、名前フィールドが必要になりました。 修正前に、名前のない新しい製品を作成できたことがありました。これは管理インターフェイスを壊し、無効な製品を作成したことになります。

_ACP2E-3660 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/df92debe)_

#### 書き出しプロセスで web サイトフィルターオプションが見つからない

製品の書き出しを作成する際に、web サイトで製品をフィルタリングできるようになりました。

_ACP2E-3720 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/520f9e30)_

#### AC-13913 の複製 – 静的属性の非同期クリーニング。

修正後、\Magento\CatalogImportExport\Model\Import\Product\Type\AbstractTypeのインスタンスが多数作成される場合に、「未定義の配列キー「apply_to」」エラーは発生しません。

_ACP2E-3752 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/520f9e30)_

#### Csv 製品の読み込み：スウォッチ画像の設定を解除できない

修正前は、製品の読み込みを通じて製品のスウォッチ画像を更新することはできませんでした。 ここで、修正後、製品スウォッチの画像列に設定済みの空のマーカーをマークすると、画像は非表示に設定されます。

_ACP2E-3972 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/2a1e1e55)_

#### 製品の読み込みによってストア範囲の空の URL が生成される

インポートデータソースで url_key に空の値がある場合、ストア表示の製品 URL キーがデフォルトのスコープに設定された値を継承するようになりました。 以前は、ストア表示レコードのデータソースをインポートで url_key を空の値に設定すると、そのスコープで url_key が空の値で上書きされていました。

_ACP2E-4038 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/52f46328)_

#### 複数選択属性が必要に応じて設定されている場合、製品の読み込みプロセスでエラーが発生します

複数選択タイプの必須属性が含まれていた場合に、製品の読み込みに失敗する問題を修正しました。 データの検証が正しく合格し、製品の読み込みプロセスが正常に完了するようになりました。

_ACP2E-4057 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/a1c57b2e)_

#### [CLOUD] 在庫管理でバックオーダーが選択されていない製品でも、インポート時に在庫レベルを超えて注文できます

修正後は、製品の「allow_backorders」属性に使用できない値をインポートできなくなりました。

_ACP2E-4116 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/a1c57b2e)_

#### 説明の長さが 65,536 文字を超えているため、製品の読み込みが失敗する検証

修正後、値が 65,536 文字を超えるテキストタイプの製品属性を読み込むことができます。

_ACP2E-4119 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/a1c57b2e)_

#### 製品のフィルタのエクスポート Yes-No 属性が期待どおりに機能しない

修正後、Yes/No 属性でフィルタリングされたエクスポートされた製品には、適用されたフィルターに従って期待される製品が含まれます。

_ACP2E-4160 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/ee918f0d)_

#### 読み込みを使用した web サイトごとのバンドルオプション価格の更新の問題

Web サイトごとのバンドルオプション選択価格の書き出しと読み込みが可能になりました

_ACP2E-4243 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/98f028ab)_

#### 大文字のメールアドレスを使用した顧客をインポートできない

アカウント共有がグローバルに設定されている場合に、大文字のメールで顧客を読み込む際の未定義の配列キーエラーを修正しました。 メールの正規化が読み込みプロセス全体で一貫するようになり、メールのケースに関係なく顧客を読み込めるようになりました。 Web サイトレベルのアカウント共有の動作は変わりません。

_ACP2E-4373 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/31258bf6)_

### インポート/エクスポート、顧客/顧客

#### 管理者は、生年月日が現在の日付より後の顧客をインポートできます

管理者が将来、生年月日が設定された顧客をインポートできる問題を修正しました。 このシステムでは、読み込み時に DOB を検証し、無効なレコードに関するエラーを表示し、将来の生年月日を持つ顧客が読み込まれないようにすることで、正確な顧客データを確保できるようになりました。

_AC-13641 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/8670a2b4)_

### インベントリ/MSI

#### チェックアウト時にアドレスが変更された場合、ストアピックアップが最大検索半径を考慮しない

配送先住所が変更された場合、「店舗で選択」で事前に選択された店舗が更新されるようになりました。 以前は、ストアが事前に選択されると、新しい配送先住所が選択したストアの半径内にない場合でも、ストアは変更されませんでした

_ACP2E-3728 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/inventory/commit/07620383)_

#### ホームページにリダイレクトしてチェックアウトした後は、利用できるストアはありません

以前に選択したストアは、お客様が支払いページに移動してからホームページに戻り、最後にチェックアウトページに戻った場合、「店舗で選択」配送で事前選択されるようになりました。 以前は、チェックアウトページに繰り返し戻った後に、「店舗で選択」で選択した店舗がクリアされていました。

_ACP2E-3793 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/a20a6ff2) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/inventory/commit/62c0d79b)_

#### 在庫の削除操作が完了していません

修正後、ソース項目を削除しても完全な再インデックスは実行されず、影響を受ける製品のみが更新されてパフォーマンスが向上します。

_ACP2E-3917 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/inventory/commit/ee0bf4ad)_

#### [MSI] お客様に注文の受け取りの準備が完了したことが非同期で通知されたかどうかを管理画面に表示しない

注文の履歴通知に、顧客に関する注文の受け取り準備が完了したという通知が非同期で追加されました

_ACP2E-3968 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/inventory/commit/29653b1d)_

#### 見積もり読み込み時の重複した在庫ステータスクエリ

ストアフロントで見積もりを読み込む際に cataloginventory_stock_status クエリが重複して実行され、冗長な DB 呼び出しが発生する問題を修正しました。

_ACP2E-4102 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/inventory/commit/fc15a9ae)_

#### パッチ後 ACP2E-4118：管理者で在庫しきい値を変更すると、販売可能数量がマイナスになり、在庫ステータスが一致しなくなります

グローバルな在庫設定の数量、バックオーダー、在庫切れのしきい値が読み込みによって更新されると、在庫在庫ステータスが自動的に調整されるようになりました。

_ACP2E-4142 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/a1c57b2e) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/inventory/commit/5632fb5e)_

#### [CLOUD] 管理レポートが、インベントリの更新時に詳細を表示しない

製品インベントリソースの変更は、ログモジュールによってログに記録されるようになりました。 修正前は、製品を保存してインベントリ関連の変更を実行すると、詳細がログに記録されていませんでした。

_ACP2E-4167 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/cbca0396) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/inventory/commit/76b88f7c)_

#### バンドル製品が、在庫としてマークされているときに買い物かごに追加できない

バンドル製品の在庫ステータスが、子製品の予約と在庫切れのしきい値を正しく反映するようになりました。
以前は、1 つ以上の子製品に十分な販売可能量がない場合でも、バンドル製品は「在庫中」とマークされていました。 これにより、バンドルを買い物かごに追加する際に「販売するのに十分なアイテムがありません」エラーが発生していました。

_ACP2E-4220 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/cbca0396) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/inventory/commit/76b88f7c)_

#### 子がカスタムソース/在庫に割り当てられた場合、グループ化された製品が CSV からの読み込み後、PDP で誤って在庫切れと表示される（手動の再インデックス後に修正）

修正後、import を使用して複合製品を作成すると、自動的に stock のインデックスが再作成されるので、手動でインデックスを再作成しなくても製品を使用できるようになります。

_ACP2E-4233 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/98f028ab) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/inventory/commit/5704166a)_

#### [MSI] 最新のメインラインの変更に関連する MFTF テストが失敗します。

修正の前に、配送先住所のない店舗での受け取りを選択したお客様は、請求先住所に店舗の住所が自動入力されていましたが、変更できず、請求書の詳細が正しくないという問題がありました。 請求先住所の修正がこのシナリオで編集可能になり、ゲストが独自の詳細を入力できるようになりました。 登録ユーザーには、ストアの代わりに保存された請求先住所が表示されます。

_ACP2E-4260 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/ab891304) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/inventory/commit/13e432a6)_

#### 仮想ギフト カードに対して作成された在庫予約が正しくありません

この修正を実装する前は、複数の項目を含む仮想ギフトカードの数量が在庫予約に正確に反映されていませんでした。 しかし、修正適用後、在庫予約と在庫の数量が同期しました。

_ACP2E-4267 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/inventory/commit/5704166a)_

#### 在庫予約報酬コマンドが Null および存在しない製品参照で失敗する

処理された組み合わせに注文 ID がない場合に在庫予約報酬 CLI で例外がスローされる問題を修正しました

_ACP2E-4301 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/inventory/commit/76b88f7c)_

#### SKU ケースを変更した後、製品の在庫切れになります

SKU のケースを変更しても、ストアフロントで製品が在庫切れになることがなくなりました。

_ACP2E-4375 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/inventory/commit/0836c2ed)_

#### 無効なデータを含む価格/価格ファセットによる注文

修正前は、子製品がカスタムソースで在庫を持っている場合、バンドル価格のインデックスが正しく作成されていませんでした。 現在は、修正後に、子製品の在庫割り当てに関わらず、バンドル価格のインデックスが正しく作成されます。

_ACP2E-4380 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/1c547060) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/inventory/commit/1f83ed24)_

#### ステージング更新中に、在庫ステータスが SKU の変更後の数量で誤って在庫中にリセットされる

スケジュール済みのアクティブな更新を含む製品で、SKU の変更が禁止されるようになりました。保存は明確なエラーで失敗し、アクティブな更新中は管理者の SKU フィールドが無効になります。 これにより、ステージングロールバック中に SKU の変更によって発生する MSI インベントリの不整合を防止できます。

_ACP2E-4389_

### 順序

#### AbstractAddress setData （&#39;custom_attributes&#39;, AttributeValue[]）は customAttributes を解除します

アドレスのカスタム属性が、チェックアウトおよび API 操作中に正しく処理されるようになりました。
以前は、$address->setCustomAttributes （&#39;custom_attributes&#39;, $attributes）を使用すると、カスタム属性の処理が中断され、属性値が正しく構造化されていませんでした。
AC-10568

_AC-10568 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/31644)_

#### お客様が見積もり注文に設定されている場合も、ゲスト注文です

_AC-11689 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/38540)_

#### 仮想品目、払戻品目、出荷品目を混在させる場合、注文は完了しません

仮想品目、払い戻し品目、出荷品目を含む注文が、出荷数量計算に仮想品目が含まれることで処理中のままになり、注文の状態が正しく完了する問題を修正しました。

_AC-11691 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/38547)_

#### v2.4.7-p1 Magentoの並べ替え–1 の注文番号

システムは期待どおりに動作しており、バックエンドから並べ替えた後、注文番号は一意の 8 桁になります

_AC-12854 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39089) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/39399)_

#### Adobeのクレジットカードによるお支払い方法でチェックアウトすると、商品のカスタムオプションファイルのアップロードが失われる

Adobeのクレジットカードによるお支払い方法でチェックアウトする際、商品のカスタムオプションファイルのアップロードが保持されるようになりました。
以前は、この支払い方法を使用するとファイルのアップロードが失われましたが、他の人と協力しました。
AC-14306

_AC-14306 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39647)_

#### 管理者注文 – Will を検索できません

管理注文グリッドで顧客名（「Will」など）で注文を検索しても、結果が返されない問題を修正しました。 修正後、顧客名でフィルタリングすると、関連する注文が正しく表示されます。

_AC-14360 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/36596) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/a8cf637b)_

#### Magento 2.4.8 GraphQL – 注文項目 order_date の形式が正しくない

GraphQL応答の order_date フィールドが yyyy-mm-dd 形式で返される問題を修正しました。
これで、order_date が dd-mm-yyyy 形式で正しく表示されます。

_AC-14431 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39805) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/a3b1abc2)_

#### Nullable でないフィールド \&quot;AppliedCoupon.code\&quot;で予期しない問題が発生した場合は null を返すことができません

Adobe Commerceは、顧客の注文をクエリする際に、GraphQLを通じて適用されたクーポンコードを正しく返すようになりました。 以前Adobe Commerce 2.4.8 では、applied_coupons.code フィールドを使用した注文の取得（例えば、customer.orders クエリを使用）が内部サーバーエラーで失敗し、Cannot return null for non-nullable field &quot;AppliedCoupon.code&quot;というメッセージが表示される場合がありました。また、applied_coupons はクーポンコードを含んだリストではなく [null] として返されました。 AC-14484

_AC-14484 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39841) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/97b2ea42)_

#### ストア設定で有効になっているにもかかわらず、管理者の注文表示から送信されたときに出荷 E メールが送信されない

注文が行われた店舗設定で出荷確認メールが有効になっているので、システムが出荷確認メールを送信するようになりました。

_AC-14563 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39861) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/39897)_

#### フィールド名があいまいなため、日付のフィルタリングは機能しません

Magento 2.4.7-p6 では、日付でオーダーグリッドをフィルタリングすると、Braintree モジュールとの結合が原因でエラーが発生することが報告されました。
この問題では、日付フィルターを適用する際に、braintree_transaction_details テーブルと sales_order テーブルを結合するクエリが発生していました。
Adobe Commerceのエンジニアリングチームはケースを確認したが、エラーを再現できなかった。
期待される動作は、日付別のフィルタリングでは、エラーなくフィルターに一致する注文を返す必要があることです。

_AC-15037 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/40024)_

#### 複数の製品がバックオフィスにあり、1 つ以上にカスタムオプションが含まれている場合、注文を作成すると、不要な追加製品が注文に追加されます

カスタムオプションを含む製品を含む複数の製品を含むバックオフィスで注文を作成すると、意図せずに製品が追加され、エラーが発生する問題を修正しました。 選択した製品のみが追加され、予期しないアイテムを含まない注文を作成できるようになりました。

_AC-15286 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/40122) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/b5e99d20)_

#### Magento2：プロモーションルールを作成できない

この PR は修正され、
メソッド \Magento\SalesRule\Model\Rule\Condition\Product::loadAttributeOptions の\Magento\Catalog\Model\ResourceModel\Eav\Attributeではなく、\Magento\Catalog\Model\ResourceModel\Eav\Attribute モデル

_AC-15358 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/12176) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/30479)_

#### Magentoが呼び出しの後に$order のエンティティタイプを変更しました$invoice = $this->_invoiceService->prepareInvoice （$order）;

サブカテゴリの既存のスケジュールされた更新を編集すると、データベース内の親カテゴリの children_count が誤って増加する問題を修正しました。 この問題により、更新を保存した後にカテゴリ階層データが不正確になりました。 修正後も、子のカウントは正しいままで、予期しない増分は行われません。

_AC-15401 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/40154)_

#### 商品が部分的に払い戻された場合、注文は配送後「処理中」ステータスのままになります

品目を部分的に払い戻し、残りを出荷した後も、注文が処理中ステータスのままになる問題を修正しました。 出荷済数量と払戻済数量の合計が請求済数量と一致すると、受注ステータスが正しく「完了」に更新され、正確な受注ライフサイクル管理が保証されるようになりました。

_AC-15419 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/cc0ec250)_

#### バックエンドから販売メールを送信すると、常に成功します（無効な場合も同様）

メールサービスの結果を検証し、注文や請求書のメールが無効になって送信されなかった場合にユーザーに通知することで、正確なメッセージを表示するように、バックエンドの販売メール通知を修正しました。

_AC-16059 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/40309) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/c95ed7d7)_

#### 新しい Web サイトとソースに割り当てられた製品の要求リストを作成できません

「URL にストアコードを追加」が有効になっている場合に、新しい web サイトとソースに割り当てられた製品の購買依頼リストを作成できない問題を修正しました。 問題は、API リクエストからストアコードが削除され、承認されていないエラーが発生したために発生しました。 修正後、正しいストア・コンテキストが保持され、購買依頼リストが正常に作成されます。

_AC-16226_

#### カスタム価格 0 は、並べ替え時に元の価格にリセットされます。

カスタム価格が 0 の製品が並べ替え中に元の価格に戻る問題を修正しました。
現在は、カスタム価格が正しく保持され、商品を並べ替える際の正確な価格設定が保証されています。

_AC-8147 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/36970) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/01cee3c3)_

#### 無効な支払い方法で注文を行う

GraphQLを介して無効なお支払い方法を使用して注文される可能性がある問題を修正しました。
現在は、利用できない支払い方法を設定または使用しようとするとエラーが返され、注文を作成できません。

_AC-9605 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/37983) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/a8cf637b)_

#### [Cloud] magento 2.4.6-p7 にアップグレードした後、一部のインライン Javascript が機能しない

管理者の「Add to Order by SKU」の「delete」ボタンをクリックすると、SKU が削除されるようになりました。 以前は、「Add to Order by SKU」の「delete」ボタンをクリックしても、SKU が削除されませんでした。

_ACP2E-3515_

#### gift_cards のシリアル化されたデータが sales_order テーブルで矛盾しています

sales_order テーブルの gift_cards データが正しくシリアル化されるようになりました。 以前は、注文が更新されるたびにシリアル化されていました。

_ACP2E-3662_

#### 処理中に注文ステータスがスタックしました

修正前は、「一緒に出荷」オプションが有効になっているバンドル製品を注文しても、請求書と出荷後に注文ステータスが自動的に「完了」に切り替わっていませんでした。 現在は、修正後、注文が請求および出荷された後、注文ステータスが自動的に「完了」に切り替わります。

_ACP2E-3947 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/2a252ae6)_

#### [Cloud]Magento OOTB コード – メールテンプレートの設定の問題

修正前は、非同期メール送信を使用する場合、出荷メールとストアオーダーが一致していませんでした。 修正後、適切な店舗出荷メール注文が配信されます。

_ACP2E-3998 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/462ede94)_

#### 404 への請求書リダイレクトの取消

「取得なし」タイプで作成された請求書の取消は、404 ページにはつながりません。

_ACP2E-4001 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/2a1e1e55)_

#### Sales Archive Cron ジョブが原因で DB ロックの問題が発生

この修正以前は、アーカイブ cron の順序アーカイブにあるバインドされていないDELETE クエリが Galera で問題を引き起こしていました。 更新後、削除クエリが制限付きで実行されるようになりました。

_ACP2E-4010_

#### REST API を使用した設定可能なオプションを含む更新済み注文の問題

Rest api エンドポイントを使用して注文を更新する際に、販売注文項目の既存の製品オプションを保持します。

_ACP2E-4061 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/6dd3fa99)_

#### ストア固有の送信者はギフト カード E メールには使用されません

以前は、別の店舗から請求書を作成した後にギフトカードの電子メールテンプレートを送信する場合、顧客が電子メールを受信したときに、管理設定での所有者の名前が電子メールヘッダーに反映されませんでした。 この修正が適用された後、適切なストア所有者のメール情報がメールヘッダーに含まれるようになりました。

_ACP2E-4310_

#### Sales async by id insert は、cron 実行あたり 100 エントリに制限されています

販売グリッドの非同期挿入の処理を改善しました。 1 回の cron 実行で、保留中の行がすべて、実行ごとに厳密に 100 行ではなくバッチで挿入されるようになりました。

_ACP2E-4360 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/31258bf6)_

#### エラーメッセージ「ID 「1」の製品は存在しません。」 が exception.log に繰り返し記録されている

修正前は、最後に注文された項目セクションで削除された製品が発生したときに重要なエラーがログに記録されていました。 修正後、マーチャントは、di.xml の `skipDeletedProductLogging` パラメーターを使用して、削除された製品をログに記録するかスキップするかを設定できます。 デフォルトでは、後方互換性のために動作は変更されませんが、マーチャントはパラメーターを `true` に設定して、削除された製品をサイレントにスキップし、ログノイズを防ぐことができます。

_ACP2E-4366 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/61c96348)_

#### 2 番目のクレジット メモ払い戻しに対する二重税

以前のクレジット・メモが受注ビュー・ページから作成された後に請求書から一部払戻を作成する場合のクレジット・メモの誤った税金計算を修正しました。

_ACP2E-4384 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/61c96348)_

### オーダー、価格設定

#### 返品の作成時に、管理者がに間違った通貨記号を表示する

通貨（EUR/USD/GBP）が異なる複数の web サイトを設定する場合、管理者の返品製品選択ページに正しい通貨記号が表示されるようになりました。 以前は、デフォルトの通貨記号が表示されていました。

_ACP2E-3658 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/df92debe)_

### 注文、返品

#### オフライン払い戻し用のクレジットメモを作成する際にエラーが発生する

動的価格= No に設定されているバンドル製品のクレジットメモの作成に失敗する問題を修正しました。 エラーなく正常にクレジットメモを作成できるようになりました。

_ACP2E-4157 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/45cbf9b6)_

### その他

#### 「キャップ報酬ポイント残高」の値を空のままにすることはできません – 保存済み

Adobe Commerceでは、マーチャントが報酬ポイント残高償還しきい値の値を設定しながら、「キャップ報酬ポイントの残高」フィールドを空のままにできるようになりました。 以前は、ストア/設定/顧客/報酬ポイントで報酬ポイントを設定する際に、報酬ポイント残高償還しきい値に正の数を入力し、キャップ報酬ポイント残高を空白のままにすると、検証エラーがトリガーされていました。「キャップ報酬ポイント残高\」が無効です。 残高は正の数にするか、空のままにする必要があります。 確認して、もう一度試してください。」というメッセージが表示されるので、マーチャントはキャップなしで設定を保存できません。 ACP2E-3977

_ACP2E-3977_

### その他の開発者ツール

#### [ 問題 ] 保護されたメンバー$_urlHelper の間違ったタイプヒント

システムは、誤ったタイプヒントを正しいヒントで修正するようになりました。これは、コンストラクターでも使用されます

_AC-10716 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/32503) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/32496)_

#### [ 問題 ] 未使用のコードをクリーンアップしています。

未使用の読み込みに関する未使用のコードが削除されるようになりました。

_AC-10980 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/38424) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/33499)_

#### Lighthouse アクセシビリティの失敗

システムはアクセシビリティスコア 100 で合格するようになった

_AC-12783 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39054) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/39164)_

#### Captcha storefont 設定を無効にしても captcha js ファイルを読み込む

Captcha を無効にした場合、システムは captcha js ファイルを読み込まなくなりました
保存用

_AC-14267 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/32987) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/39154)_

#### [ 問題 ] アクセシビリティ：WAI-ARIA の役割のメニューでのネストが正しくない

システムは、メニューエラーで WAI-ARIA の役割のネストが正しくなく、レポートが緑色であるにもかかわらず、lighthouse のアクセシビリティを生成するようになりました

_AC-15082 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/40045) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/38617)_

#### Magento管理者のメールのプレビューでコンソールエラーが発生する

メールテンプレートをプレビューしている間、コンソールエラーはスローされません

_AC-9245 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/37820) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/37933)_

### 支払い/支払い方法

#### バックエンドで正常に設定されている場合、Paylater メッセージがストアフロントに表示されません

バックエンドで設定されているにもかかわらず、PayPal Pay Later メッセージがホームページと買い物かごページに表示されない問題を修正しました。 デフォルトのアドレスがないゲストまたは顧客の購入者の国が null の場合、バナーがレンダリングに失敗しました。 修正後、「後で支払う」メッセージがストアフロントに正しく表示されます。

_AC-12335 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/528af81a)_

### 支払額

#### [ 問題 ] オフライン請求書キャプチャの修正（404）

Magento管理者からオフライン支払い方法用の請求書をキャプチャする際の 404 ページエラーを修正します

_AC-13336 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39298) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/39297)_

#### PayPal からの不明な IPN がアプリケーション IPN プロセッサーを悪用する

IPN ハンドラは、サポートされていない IPN タイプまたは不明な IPN タイプを無視するようになりました。 500 エラーを返す代わりに、問題をログに記録し、中断することなく処理を続行します。

_ACP2E-4049 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/6dd3fa99)_

#### PayflowPro 保存済みカードトークンは支払いに失敗しました

PayPal PayFlow Pro のトランザクション ID （PNREF）が、12 か月の固定期間の参照トランザクションで使用できるようになりました。 有効期限が切れると、保存されたカードは表示されなくなり、再度追加する必要があります。 以前は、有効性は元のトランザクションで使用される支払いカードの有効期限によって決定されていました。

_ACP2E-4064 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/52f46328)_

#### 管理者に注文する際のヴォールトされたカードの問題

異なる支払いアクション設定を使用している web サイトの下で、保存されたクレジットカードを使用して注文を行っても、エラーやトランザクションタイプが間違うことがなくなりました

_ACP2E-4270 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/0a8c9a9a)_

#### [Cloud] PayflowPro 保存カード（Vault）の最後の 4 桁が順序で表示されない

保存されたカードを Sales 支払いアクションで使用する場合、カード情報が適切に保持および表示されるようになりました。これは、PayflowPro の Authorization 支払いアクションを使用する場合の動作と一致します。

_ACP2E-4346 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/0a3b7032)_

### パフォーマンス

#### [ 問題 ] Store.php の更新

この PR は、現在のストアの解決をスキップすることでパフォーマンスを向上させます。

_AC-14791 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39949) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/38717)_

#### [ 問題 ] 静的サイトの use キャッシュコントロールを更新すると、変更できません

この PR は、変更されない限り、各ページ読み込みの静的コンテンツを検証しないことで、パフォーマンス向上を実現します。

_AC-15171 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39486) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/39484)_

#### [ 問題 ] パフォーマンスを向上させるために、isCacheable 呼び出しの結果をキャッシュする

この PR により、isCacheable （） メソッドのキャッシュが追加された結果、レイアウトレンダリングプロセスで冗長なチェックが減り、ページレンダリングの全体的なパフォーマンスが向上します。

_AC-16054 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/40156) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/40112)_

#### [ 問題 ] 非同期順序グリッド処理のパフォーマンスが若干向上

この PR では、一時的なキャッシュベースの last_updated_at ルックアップを、フラグテーブルに格納された永続的な DB ベースのフラグに置き換えることにより、Magentoの非同期注文グリッド処理のパフォーマンスを最適化しています。 これにより、キャッシュのフラッシュやデプロイメント後もシステムが最後に処理されたタイムスタンプを一貫して保持し、大規模な sales_order データセットに対する不要なフルテーブルスキャンを防ぐことができます。 その結果、非同期グリッドの更新は、特に注文アクティビティが頻繁に発生する大量のストアで、より効率的で予測可能になります。

_AC-16109 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/40282) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/40271)_

#### カテゴリ権限モジュールがキャッシュを防ぐ可能性があります

サードパーティコントローラーが、顧客セグメントと正しくキャッシュされるようになりました

_ACP2E-3721_

#### [CLOUD] カテゴリに製品を追加できない

ビジュアルマーチャンダイザーを通じてカテゴリに製品を追加する際のパフォーマンスが向上しました。

_ACP2E-3946 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/inventory/commit/29653b1d)_

#### 10,000 件を超えるログを [Cloud] cache_invalidate

以前は、各 PLP または買い物かごへの訪問でキャッシュがクリアされたため、不要なパフォーマンスのオーバーヘッドが発生していました。 これらのページでは、ターゲットルールキャッシュが無効化されなくなり、閲覧効率が向上します。

_ACP2E-4059_

#### [Cloud] php-fpm が max_execution_time を考慮しない

デプロイメント設定は、1 回のリクエストで 1 回読み込まれるようになりました。

_ACP2E-4201_

#### ACP2E-3995 後の変更ログのクリーンアップパフォーマンスの問題

修正後、indexer_clean_all_changelogs cron ジョブは changelogs を完全にクリーンアップし、バッチ処理を維持します。

_ACP2E-4211 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/ee918f0d)_

#### [CLOUD] 2.4.8 にアップグレードした後、Fastly キャッシュが機能しません

キャッシュ可能なページが Fastly キャッシュから適切に保存または提供されなかったので、キャッシュ動作に一貫性がなく、パフォーマンスが低下していた問題を修正しました。

_ACP2E-4324 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/2687b487)_

#### Redis キーとキャッシュキーの作成理由を調査します。

修正前は、リモートストレージメタデータに使用されるキャッシュキーの有効期限は切れていませんでした。 修正後、依存関係のインジェクションを使用して、このようなキャッシュキーの TTL を設定できるようになりました。

_ACP2E-4345 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/0a3b7032)_

### Pricing

#### Rest API 注文の動的価格なしのバンドル製品項目の場合、価格は常に 0 です

注文 REST API で、動的価格なしでバンドル製品項目の正しい価格を返すようになりました。
以前は、REST API を介して注文を書き出す場合、動的価格のないバンドル製品項目の価格が、バンドルページに表示される実際の価格ではなく、常に 0 として返されていました。
AC-11925

_AC-11925 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/38687) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/7da46f52)_

#### 作成時に価格属性に間違ったスコープが割り当てられる

設定に関係なく、新しく作成した価格属性が誤ってストアビュー範囲に割り当てられていた問題を修正しました。修正後、属性範囲は、デフォルトでカタログの価格範囲設定（グローバルまたは web サイト）に従うようになりました。

_AC-14945 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39986) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/8670a2b4)_

#### 一括処理を使用して、特別価格の開始日が終了日より後の場合でも、製品が保存されている

検証を行わずに、製品を無効な特別価格の日付範囲で保存できる問題を修正しました。
「終了日が開始日より後であるか、開始日と同じであることを確認してください」というエラーメッセージが表示されるようになりました。

_AC-15252 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/40113) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/36d4d6fb)_

#### 交渉が可能な見積もりの Paypal エクスプレスチェックアウトを完了した後、配送の詳細が一致しません。

この問題は、承認された交渉可能な見積もりの PayPal エクスプレスチェックアウトを完了する際の送料の不一致を修正しました。
修正前は、送料が誤って 2 倍になり（$5 ではなく$10 を表示）、合計が水増しされていました。
Magento 2.4.9-alpha3 の修正により、正しい送料が適用されます

_AC-15280_

#### 異なるタイムゾーンで作成された web サイトでは、特別価格は適用されません

修正前は、現在のストアのタイムスタンプの範囲で特別な価格日付の有効性が作成されていました。 修正後、デフォルトのストアタイムゾーンが考慮されます。

_ACP2E-4002_

#### 特別価格が適用されていても、通常の価格は表示されません。

特別価格が適用されたときに通常価格が表示されない問題を修正しました。 通常価格が、期待どおりの特別価格と正しく表示されるようになりました。

_ACP2E-4100 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/47721be6)_

### 製品

#### フロントエンドの動作が正しくない、設定可能な製品

カラースウォッチ属性が含まれている場合に、設定可能な製品で誤ったフロントエンド動作が表示され、価格、ドロップダウンレイアウト、必須フィールドのインジケーターが正しく表示されない問題を修正しました。
現在は、設定可能な製品が、適切な価格、調整されたドロップダウン、期待される UI 動作で正しくレンダリングされます。

_AC-1014 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/14296) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/ef666cd9)_

#### 在庫切れ製品の表示オプションを有効にしたテスト在庫およびテスト web サイトに割り当てられた設定可能な製品の価格アサーション文字列の不一致

すべての子製品の価格が同じ場合に、設定可能な製品の実際の価格設定動作に合わせるために、失敗したテストを更新しました。
アサーションで表示価格が正しく検証され、機能に影響を与えずに誤ったテストの失敗を防ぐことができるようになりました。

_AC-10843 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/inventory/commit/1ccc786b)_

#### テストケース AC-6158 の設定可能な製品には、引き続き「As low as」ラベルが表示されます

各バリエーションおよびカテゴリ割り当てによって、設定可能な製品（P1～P7）を実装および検証しました。 カテゴリ C の製品について、正しい店頭価格の表示と「できるだけ低い」ラベルの動作を確認しました。

_AC-10847 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/a3b1abc2)_

#### オプションを選択せずに、元の価格に基づいて計算された、階層価格およびカタログ価格ルールに対する割引率。

階層価格とカタログ価格ルールの割引率に、選択したカスタムオプションが含まれるようになりました。
以前は、選択したカスタムオプションを考慮せずに元の製品価格に対して割引率が計算されていたため、最終的な価格が正しくありませんでした。
AC-12004

_AC-12004 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/38750)_

#### [ 問題 ] validate-rating が機能せず、レビュー評価のセレクターが変更される

セレクターが変更されたので、レビュー評価の検証がトリガーされなかった問題を修正しました。 以前は、評価を選択せずにレビューを保存できていました。 修正後は、検証は正しく機能し、評価が選択されていない限り、レビューを保存できなくなります。

_AC-12686 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/33424) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/528af81a)_

#### Magento 2.4.7 minAllowed missing product order qty

システムは正常に動作し、ページソースは製品の最小数量を正しく表示している

_AC-12909 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39142) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/39480)_

#### 製品コレクション – コレクションが読み込まれる可能性がある場合または読み込まれる場合に、addMediaGalleryData が getSize を呼び出します（カウントを使用して、追加の DB クエリを回避できます）

この PR により、media_gallery フィールドを含んだ製品 Graphql を呼び出す際に製品コレクションが既に読み込まれている場合、count （）を使用して追加のクエリ呼び出しが削減されます。

_AC-13055 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39111) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/39681)_

#### Magentoのリンクされた製品の SKU 処理が無効です

SKU の検証が無効なため、SKU が「0」の製品を関連、アップセル、クロスセルの項目としてリンクできない問題を修正しました。 このアップデートにより、そのような製品を正常にリンクでき、製品をエラーなく保存できるようになります。

_AC-13311 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39329) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/a8cf637b)_

#### 管理パネルの製品ページのカスタマイズ可能オプショングリッドに関する問題

タイプがドロップダウンのカスタマイズ可能なオプションを作成する場合、システムは期待どおりに動作します

_AC-14003 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39640) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/39694)_

#### すべての製品属性がグローバルスコープに設定されている場合の管理製品ページエラー

すべての製品属性がグローバルスコープに設定されている場合に、管理者の製品の編集ページにエラーが表示される問題を修正しました。 このエラーは、空のデータベースクエリが原因でページを使用できなくなりました。 修正後、製品ページが正しくレンダリングされ、問題なく製品を作成できるようになります。

_AC-14011 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39646)_

#### [2.4.8] cron job catalog_product_alert のコールバックが見つかりません

製品アラート cron ジョブの名前が product_alert に変更された後、Adobe Commerceは誤った catalog_product_alert cron ジョブがスケジュールされるのを正しく防ぐようになりました。 以前は、Adobe Commerce 2.4.8 で、Stores/Configuration/Catalog/Catalog/Product Alerts Run Settings を設定すると、core_config_data で catalog_product_alert cron エントリが作成され、cron が実行されるとMagento_Cron.CRITICAL: Exception: No callbacks found for cron job catalog_product_alert but but those the valid product_alert jobs were running correctly.

_AC-14494 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39800) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/1bc2d6d0)_

#### 購買依頼リスト・ページ印刷オプションが機能しない

「購買依頼リスト」ページの「印刷」オプションが正しく機能するようになりました。
以前は、「印刷」をクリックすると、「アプリケーションの実行中にエラーが発生しました。 詳しくは、例外ログを参照してください。
AC-14711

_AC-14711_

#### [ 製品比較 ] 比較リストを使用できなくなります

同じ製品が異なるストア表示から追加されると比較リストが使用できなくなる問題を修正しました。修正後、比較リストは正しく読み込まれ、特定のストアに基づいて項目が表示されます。

_AC-14885 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/8670a2b4)_

#### リポジトリーを介した製品のリクエスト時に追加のログに失敗する

SKU または ID が見つからない場合の ProductRepository::get および getById のエラーメッセージを改善しました。
以前は、例外には、エラーの原因となった SKU や ID に関するコンテキストが提供されていませんでした。
現在は、例外メッセージに欠落した SKU または ID が含まれるようになり、デバッグと開発者エクスペリエンスの向上に役立っています。
この変更は、API の機能動作には影響しません。

_AC-15199 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/40090) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/1b1baf1d)_

#### 「属性セットが存在しません」エラーが発生すると、ページが破損する

URL に無効な属性セット ID を入力すると致命的なエラーが発生する問題を修正しました。ページを分割する代わりに、属性セットが存在しないことを示す適切なエラーメッセージが表示されるようになりました。

_AC-15753 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/40213) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/a06a4a57)_

#### マイナスの数量による払い戻しによる払い戻し差額

負の数量のクレジット メモを作成すると、割引額が誤って返金される問題を修正しました。
現在は、マイナスの数量に対する割引は払い戻されず、払い戻し数量は正しくゼロに設定されています。

_AC-9424 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/37917) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/ef666cd9)_

#### 製品ウィジェットが pagebuilder を介して含まれる場合、低速クエリが実行される

製品 SKU を含む製品ウィジェットの作成用のクエリが最適化されています。

_ACP2E-3449 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/df92debe)_

#### 設定可能な製品として追加された場合、製品画像のサイズが変更されない

以前は、管理パネルの設定を通じて追加された画像が最大アップロードサイズの制限に準拠しておらず、不整合や管理の課題が発生する可能性がありました。 最大サイズ制限に準拠するためにアップロード中に画像のサイズが自動的に変更されるように修正が実装され、プロセスが合理化され、システム標準が維持されるようになりました。

_ACP2E-3504 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/df92debe)_

#### 他の顧客比較リストのすべての項目は、管理者を介してログインした後、顧客に割り当てられます

以前は、管理者がバックエンドで「顧客としてログイン」機能を使用すると、以前にログインした顧客の比較リストの製品が、現在なりすまされている顧客に誤って割り当てられました。  修正後、正しくログインしている顧客の比較リストが正しく読み込まれます。

_ACP2E-3818 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/462ede94)_

#### 設定可能な製品が制限付き役割で編集された場合、単純な製品の割り当てが解除される

この修正の前は、制限付きの管理者ユーザーが、管理者ユーザーがアクセス権を持たないシンプルな製品を含む設定可能な製品を保存する場合、保存時に設定可能な製品から削除されていました。 修正後、設定可能な製品は、完全な権限を持つ管理者によって保存されたとおりに保持されます。

_ACP2E-4081_

#### [B2B] 共有カタログの保存で非推奨（廃止予定）の機能が返されるエラー

管理者は、共有カタログから製品の割り当てを正常に解除できます。
以前は、共有カタログから長い製品 SKU の数が多い製品を割り当て解除すると、エラーが発生していました

_ACP2E-4097 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/ab891304)_

#### [ クラウド ] サイトマップの生成パフォーマンスが大幅に低下している

画像を含んだ製品のサイトマップの生成で、急激な減速が発生しなくなりました。 以前は、画像を含める処理が有効なストアのサイトマップを生成すると、処理時間が長くなっていました。

_ACP2E-4153 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/e457c5e2)_

#### 顧客セグメントの並べ替え順に一貫性がないと、一部のページで X-Magento-Vary cookie が常に再生成されます

X-Magento-Vary cookie が商品ページに 1 回設定されるようになりました。以前は、一部のカスタマーセグメントの設定では、PDP 読み込み中に cookie が数回設定されていました

_ACP2E-4261_

### 製品、税

#### 固定製品税（FPT）が、設定可能な製品と別に表示されない

オプションを選択した後、設定可能な製品の固定製品税（FPT）が個別に表示されない問題を修正しました。 これで、FPT 分類が製品リストおよび詳細ページに正しく表示され、シンプルな製品の表示形式に一致します。

_AC-13171 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/b5e99d20)_

### プロモーション

#### 購入 X 買い物かご価格ルールが、他のルールが既に適用されている場合に、誤った割引を追加する

別のルールによって既に割引が適用されていた後でも、「購入 X 買い物かご価格」ルールによって元の製品価格を使用して割引が計算される問題を修正しました。 更新により、2 番目のルールで調整済みの価格に割引が適用され、複数のプロモーションがアクティブな場合に正確な割引合計が得られるようになりました。

_AC-12325 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/8670a2b4)_

#### GraphQl 顧客リクエスト経由で顧客注文の注文品目割引 applied_to を取得中にエラーが発生しました

以前は、GraphQl 顧客リクエストを介した顧客注文の割引が applied_to であった場合、内部サーバーエラーが発生していましたが、このエラーが修正され、割引が適用された適切な顧客注文データが取得されるようになりました

_AC-14888 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39963) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/fe72c407)_

#### GraphQl 顧客リクエスト経由で顧客注文の注文項目クーポンコードを取得中にエラーが発生しました

GraphQLを介してクーポンの詳細を含む注文を取得すると、内部サーバーエラーが返される問題を修正しました。
これで、クエリが正常に実行され、応答に正しいクーポン情報が返されます。

_AC-14889 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39962) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/fe72c407)_

#### ACP2E-2926 の修正後、顧客セグメントが各チェックアウトリクエストで照合されるので、不要な処理が発生します

顧客セグメント機能に、パフォーマンスを向上させるキャッシュメカニズムが含まれるようになりました。

_ACP2E-4299_

#### [Cloud][experienceleague] カタログ価格ルールが適用されていません

以前は、カタログ価格ルールが適用されなか `special_price` たが、Web サイトレベルでのみ設定された場合（「すべてのストアビュー」では設定されなかった）。 Web サイトのデフォルトストアを最初に確認することで、`special_price` が web サイトのレベルで設定されている場合に、カタログ価格ルールを修正しても正しく適用されるようになりました。

_ACP2E-4372 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/61c96348)_

### SEO

#### DynamicStorage.findProductRewriteByRequestPath （）に entity_type フィルタリングが欠落しているので、CMS ページがカテゴリ URL の商品として扱われます

DynamicStorage が entity_type でフィルタリングされず、CMS ページがカテゴリ URL 内の商品として誤って扱われる問題を修正しました。不正な形式の URL はCMS コンテンツを提供する代わりに正しく 404 を返すようになりました。

_AC-14991 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39996) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/64823f95)_

#### 製品 url でカテゴリパスを有効にすると、ストアのスイッチャーが複数の方法で機能しなくなる

製品 URL のカテゴリパスを有効にするとストア切り替えボタンが失敗する問題を修正しました。ストア切り替えにより、ホームページにリダイレクトしたりエラーを返したりすることなく、ストア表示をまたいで製品 URL を正しく解決できるようになりました。

_AC-15110 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/40037) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/a7ef6300)_

#### ProductRepository getById の配列キーが定義されていません

この問題は、ProductRepository::getById （）が 123abc のような無効な ID で呼び出され、「未定義の配列キー」エラーが発生する場合に発生していました。
Magento 2.4.9-alpha3 の修正後、このようなリクエストは、例外をスローする代わりに 404 ページを正しく返すようになりました。
QA が有効な ID と不正な形式の ID の両方で確認され、それ以上の問題は観察されませんでした。

_AC-15345 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/40146) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/68a45d0a)_

#### ストアフロントの比較製品でGoogle SEO エラーが発生する – リンクはクロールできません

href 属性が見つからないか、適切にバインドされていないことが原因で、ストアフロントの「製品を比較」リンクが検索エンジンでクロールできない SEO の問題を解決しました。 更新により、リンクに有効な、クロール可能な URL が含まれるようになり、サイトの検出性が向上し、Google SEO 監査に合格するのに役立ちます。

_AC-15547 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/40185) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/c95ed7d7)_

#### REST API を使用した製品の URL キーの更新で、301 URL の書き換えが生成されない

「URL キーが変更された場合に URL の永続的なリダイレクトを作成」設定を「はい」に設定して、REST API を介して製品の URL キーを更新する場合、製品 URL の書き換えは、古い URL から新しい URL へのリダイレクトを作成します。

_ACP2E-3900 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/462ede94)_

#### [ クラウド ] サイトマップの生成が終了しない

この修正より前は、カタログに 100 万個を超える製品が含まれている場合、サイトマップの生成を正常に完了できませんでした。 修正後、サイトマップの生成はメモリ割り当てが少なくなり、1 ストアあたり 100 万個もの製品で完了します。

_ACP2E-3902 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/52f46328)_

#### よくある質問（FAQ）ページで、[ クラウド ] ストアスイッチャーが EN から FR に変わらない

ストアビューを切り替えると、対応する翻訳済みCMS ページではなくホームページにユーザーがリダイレクトされる問題を修正しました。 ストアスイッチャーは、正しいリダイレクトを確実にするためにターゲットストアの URL 書き換えをチェックするようになりました（例：英語の FAQ ページ→フランス語の FAQ ページ）。

_ACP2E-4112 - [GitHub の問題 &#x200B;](https://adobe-ent.crm.dynamics.com/main.aspx?appid=f2e74f34-7119-ea11-a811-000d3a5936c5&forceUCI=1&pagetype=entityrecord&etn=incident&id=3e1df344-8a69-f011-bec3-6045bd04f475)_

#### [ クラウド ] 古いサイトマップ生成を無効にします

標準のサイトマップ生成プロセスと新しく実装されたバッチモードを切り替える新しい設定オプションが使用できるようになりました。 この機能強化により、サイトマップ作成ワークフローの柔軟性と拡張性が向上します。

_ACP2E-4132 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/45cbf9b6)_

#### 疑わしい要求が exception.log に例外をスローする

悪意のあるまたは形式が正しくない URL リクエストが原因で、データベース照合エラーが発生し、例外ログがいっぱいになる問題を修正しました。
以前は、無効な文字エンコーディングまたはサポートされていない文字を含んだ疑わしいリクエストを受け取ると、システムがそれらをデコードして処理しようとするため、MySQL 照合の競合が発生していました。

_ACP2E-4328 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/2687b487)_

### 売上

#### 注文状態ドロップダウンで値を選択すると、注文状態が表示されなくなります

注文ステータスの割り当てが期待どおりに動作するようになりました。
以前は、カスタム注文ステータスを割り当てる際に、ステータスの割り当てを解除すると、「処理中」状態がドロップダウンに表示されなくなり、再割り当てできなくなる場合がありました。
AC-15010

_AC-15010_

#### ギフトメッセージが注文レベルで有効になっていても、ユーザーがデータを入力して注文しない場合、管理者の名前と名前の宛先から顧客の姓と名が表示されます。

ギフトメッセージが入力されていない場合でも、ギフトメッセージの送信者フィールドと受信者フィールドに顧客名が自動的に入力される問題を修正しました。ユーザーが詳細を入力しない限り、フィールドは空のままになります。

_AC-15140 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/a8cf637b)_

### 検索

#### カタログ検索時の「フォームの再送信を確認する」に「カテゴリのページネーションを記憶する」を使用

ツールバーの設定を変更した後に製品ページからカタログ検索結果ページに戻っても、「カテゴリのページネーションを保存」が有効になっている場合に「フォームの再送信を確認」ダイアログがトリガーされなくなりました。
以前は、並べ替え順序などのツールバーパラメーターを変更した後に検索結果ページに戻ると、ブラウザーエラーやフォームの再送信に関する警告が発生していました。

_ACP2E-4208 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/e885088b)_

#### 集計検索フィールド「_search」は、検索クエリでは使用されなくなりました

現在の全文検索では、単一のフィールドで条件を満たすことを要求するのではなく、検索可能なすべてのフィールドで最小一致条件を一括して満たす必要がある場合、一致する製品を返すようになりました。

_ACP2E-4285 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/cbca0396)_

### セキュリティ

#### 内部サーバーエラー

非同期 REST エンドポイント POST /rest/default/async/V1/carts/mine/items を使用する場合、Magentoで顧客の買い物かごに商品が正常に追加されるようになりました。 以前は、この非同期「買い物かごに追加」リクエストで内部サーバーエラーが発生し、Magentoで次のエラーがログに記録されていました。Error: app/code/Magento/Quote/Model/Quote/Item/AbstractItem.php:162 のメンバー関数 setFinalPrice （）の呼び出しが null で行われました。

_AC-16344 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/8670a2b4)_

#### バンドルまたは結合された JS が SRI ハッシュの一部ではない

修正前は、生成されたバンドルまたは結合ファイルが SRI ハッシュリストに追加されていませんでした。 現在、ファイルは SRI ハッシュに適切に追加されています。

_ACP2E-3854 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/4ca73607)_

#### [CLOUD] Newrelic に書き込み可能な権限の問題が発生しました

修正前は、ログは例外で散乱していました。 修正を適用すると、ログがクリーンになり、例外がなくなりました。

_ACP2E-4296 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/61c96348)_

### 送料

#### 数件の資格情報の後に出荷する数量が正しくありません

複数のクレジット メモの後で数量と出荷額が正しく計算されず、払い戻された品目を出荷できなかった問題を修正しました。
現在は、出荷済み品目と払い戻し済み品目に基づいて出荷可能残数量が正確に更新されるので、無効な出荷を防ぐことができます。

_AC-1479 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/34289) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/913bf1a6)_

#### 出荷方法の読み込み時に発生する可能性のあるパフォーマンスの問題

リクエスト時にアクティブな通信事業者のみが読み込まれるようにすることで、発送方法の読み込みプロセスを最適化しました。 以前は、すべての配送方法のファクトリが初期化されたため、不要なパフォーマンスオーバーヘッドが発生していました。 この修正により、アクティブな配送業者のみを条件付きで読み込み、読み込み時間とリソース使用量を削減することで、効率が向上します。

_AC-15415 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/40153) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/cc0ec250)_

#### [ 問題 ] 商業用地を居住地として扱ってはならない

UPS REST 配送の統合で、商用宛先が誤って住宅として扱われる問題を修正しました。 ResidentialAddressIndicator は、意図しない居住地追加料金を防ぎ、正確な商業配送料を確保するために、居住地住所に対してのみ UPS 料金リクエストに含まれるようになりました。

_AC-16285 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/40314) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/40307)_

#### UPS 出荷ラベルの作成中に例外が発生しました

修正警告：UPS 出荷ラベルの作成中に配列から文字列への変換が行われました

_ACP2E-3676 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/b12ffe36)_

#### [QUANS] - Magento_Fedex コアモジュールは、新しいトークンを取得するリクエストを送信する前に、有効なアクティブなトークンを確認しますか？

Adobe Commerceは、アクセストークンに対して FedEx API サービスへのリクエストを多数行わなくなりました。 以前は、アクセストークンがまだ有効でも、Adobe Commerceは常に FedEx API に新しいリクエストを行うので、レート制限の問題が発生していました。

_ACP2E-3930 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/4ca73607)_

### ステージングとプレビュー

#### カタログ価格ルールの影響を受ける買い物かご内の製品の価格が、ステージング更新によってルールが調整された場合、変更されない

ステージング更新を通じてカタログ価格ルールを変更した後、買い物かご内の製品価格が完全には更新されない問題を修正しました。 以前は、更新された価格は概要セクションにのみ表示されていましたが、中央の買い物かごブロックには古い値が表示されていました。 これで、改訂されたルールによって、買い物かご全体の製品価格が正しく更新されます。

_AC-15304 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/913bf1a6)_

#### カテゴリのスケジュールされた更新が削除されても、親カテゴリの子の量は減りません

カテゴリの予定された更新を削除しても親カテゴリの子カウントが減らず、予定された更新またはサブカテゴリが削除されたときにカウントが正しく更新される問題を修正しました。

_AC-15670 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/ef666cd9)_

#### カテゴリのスケジュールされた更新を編集する際に、親カテゴリに子の金額が追加されます

サブカテゴリの既存のスケジュールされた更新を編集すると、データベース内の親カテゴリの children_count が誤って増加する問題を修正しました。 この問題により、更新を保存した後にカテゴリ階層データが不正確になりました。 修正後も、子のカウントは正しいままで、予期しない増分は行われません。

_AC-16239 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/8670a2b4)_

#### スケジュールされた更新をプレビューすると、関心のあるストア表示ではなく、アルファベット順で最初のストア表示が開きます

修正を行う前は、スケジュールされた更新のプレビューが、割り当てられたストア表示ではなく、アルファベット順の最初のストア表示で開いていました。
修正後、CMS ブロックのステージング更新に割り当てられたストアビューでプレビューが正しく開くようになりました。

_ACP2E-3671 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/b12ffe36)_

#### Staging_apply_version Cron の動作の問題 – special_price 無視

修正後、見積の合計は、スケジュールされた製品の更新によって特別価格を変更した後に再計算されます。

_ACP2E-3674_

#### カテゴリ権限が有効になっているスケジュールされた製品アップデートをプレビューできない

修正前は、今後も有効になる製品がプレビューモードで表示されていませんでした。 現在のステータスが無効な場合でも表示されるようになりました。

_ACP2E-3786 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/7accebfa)_

#### プレビュー中、スコープに異なるストア表示が表示される

修正前に、cms ブロックと cms ページのコンテンツのステージング更新プレビューが、コンテンツのステージングダッシュボードからアクセスしたときに cms ブロックまたはページに割り当てられたストアとは別のストアで開いていた可能性があります。 修正後、ステージング更新で cms ブロックまたはページに特定のストアのみが割り当てられている場合、コンテンツのステージングダッシュボードからのプレビューが開いて、正しいストアが選択されます。

_ACP2E-3815_

#### カタログ価格ルール割引金額フィールドの検証がありません

以前は、ステージングスケジュールの更新の discount_amount フィールドが、現在の検証ルールで正しく検証されていませんでした。 ただし、修正を適用すると、discount_amount フィールドは適切に検証されます。

_ACP2E-3867 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/462ede94)_

#### 別の管理ドメインを使用している場合、チェックアウト時にステージング更新のプレビューが壊れる

顧客は、ストアのベース URL が管理 URL と異なる場合、ログインして買い物かごをストアプレビューモードで表示できます。

_ACP2E-3906_

#### コンテンツのステージングダッシュボードに間違った時間が表示される

「コンテンツのステージングダッシュボード」の「開始時刻」と「終了時刻」の日付フィルターに、正しい日時が表示されるようになりました。 以前は、日付選択で日時を選択すると、誤った日時が表示されていました

_ACP2E-3969_

#### スケジュールされた更新の製品およびカテゴリのプレビュー中、スコープに異なるストア表示が表示されます

以前は、カテゴリと製品のプレビューリンクが正しいストアに対して生成されていませんでした。 この修正後、プレビューリンクは、プレビューが作成されたストアを自動的に選択します。

_ACP2E-4053_

#### スケジュールされたアップデートを含むバンドル製品で、製品保存アクション時に「バンドル項目」オプションが削除される

スケジュールされたアップデートでバンドル製品オプションまたは関連製品を削除しても、元のバンドルオプションおよび関連製品には影響しなくなりました（その逆も同様です）。 また、元の製品からバンドルの実稼動オプションを削除し、アップデートをスケジュールした後で別のオプションに置き換えても、新しく追加されたオプションが削除されなくなりました

_ACP2E-4212 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/ab891304)_

#### プロモーションプレビューモードで、適用したクーポンが適用後すぐに表示されない問題。

修正前は、ステージングプレビューモードでバウサーコードを正しく使用できませんでした。 現在は、修正後に、割引券コードがチェックアウトページに正しく適用されます。

_ACP2E-4226_

#### スケジュール更新プレビューで web サイト間を移動できない

この修正前は、カスタムドメインを持つストアのコンテンツをプレビューしようとすると、スケジュールされた更新のプレビューが壊れてしまっていました。 この修正後、カスタムストアドメインをそのままプレビューし、プレビュー iframe 内で移動できます。 この修正プログラムは、製品、カテゴリ、CMSページ、CMSブロックを対象とし、`{{store url}}`Adobe Commerce Variables and Markup Tags[&#x200B; に記載されている &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/variables/markup-tags) のマークアップタグを使用したナビゲーションリンクをサポートします。

_ACP2E-4308 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/0a3b7032)_

### 税

#### 注文の合計が正しくない場合、ラウンドは価格計算に適用されません。

price_after_discount、discount_amount、および tax の金額を計算する際に、システムが正しく処理するようになりました。
注文の実際の合計

_AC-11389 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/38455) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/39687)_

#### [ 問題 ] 修正：クレジット・メモ項目の base_weee_tax_applied_row_amnt 値が正しくありません

base_weee_tax_applied_row_amnt に適切な setter を使用してクレジット・メモ計算を修正し、税金の値に払い戻し済数量のみが反映されるようにします。 以前は、行の金額に、一部のクレジット・メモ金額ではなく完全な受注値が誤って使用されていました。

_AC-12049 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/38765) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/3b5ac075)_

#### ギフト包装が買い物かごから削除されると、税額は更新されません

setGiftOptionsOnCart GraphQLミューテーションでギフトラッピングが削除された場合、Magentoが買い物かごの税金の合計を正しく更新するようになりました。 以前は、ギフトラップが選択され、ミューテーション入力で「giftWrappingId: null」を渡して設定を解除すると、見積もりの税額が更新されず、Magentoは、ギフトラップが適用されていなくても、買い物かごの合計にギフトラップ税を引き続き含めていました。

_AC-14637_

#### ミニカートのアイテムは、換算なしの外貨価格を表示します

ミニカートで通貨が正しく変換され、設定されたコンバージョンレートに基づいて正確な金額が表示されるようになりました。

_ACP2E-4364 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/1c547060)_

### テストフレームワーク

#### [ 問題 ] MFTF テスト AdminSetUpWatermarkForSwatchImageTest から重複した &lt;severity> タグを削除する

システムの AdminSetUpWatermarkForSwatchImageTest に重大度タグが 1 つだけ含まれるようになり、コードの明確さと一貫性が向上しました。 以前は、このテストには 2 つの同じ重要度タグが含まれていましたが、これは不要であり、混乱を招く可能性がありました。

_AC-11873 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/38504) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/31862)_

#### [ 問題 ] lib/internal/Magento/Framework/App/Test/Unit/_files/app/etc/en...

単体テストの実行時に生成されるファイル「env.php」が無視されるようになり、テストの実行後も Git のステータスがクリーンなままになります。 以前は、単体テストを実行すると新しいファイル「env.php」が生成され、git ステータスに新しいファイルが見つかり、ダーティに見えるようになりました。

_AC-13293 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39304) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/37631)_

#### [ 問題 ] インターセプターの統合テストの問題を修正しました

統合テストで\Magento\TestFramework\App\Config\Interceptorが正しく識別および処理されるようになりました。これにより、クラスにプラグインが存在する場合でもテストで必要なデータにアクセスできるようになります。 以前は、システムは\Magento\TestFramework\App\Configが\Magento\TestFramework\App\Config\Interceptorである可能性を考慮に入れることができず、$data プロパティにアクセスしようとするとエラーが発生していました。

_AC-13305 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39324) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/37187)_

#### [ 問題 ] MFTF:Captcha が有効な友達フォームにメールを送信する

テストケースでは、CAPTCHA が有効な場合の「Email to Friend」フォームの機能について説明し、間違った CAPTCHA 値と正しい CAPTCHA 値の両方でフォーム送信プロセスが正しく動作することを確認します。

_AC-13492 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39462) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/32830)_

#### [ クラウドネイティブサービス ]CNS ビルドエラー – 2.4.9-beta1 – 統合

_AC-16427_

#### Composer ビルドでの固定パスの失敗

_AC-16488_

#### PR ビルドと Composer ビルドの PHPUnit 構成ファイルの不一致

_AC-16501_

#### [ 問題 ]magento/magento2#:GraphQl の突然変異。 顧客の storeConfig 設定に関する追加のテストカバレッジ。

次のお客様の storeConfig オプションに対して、テスト範囲が追加されます。
required_character_classes_number
minimum_password_length

_AC-9370 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/37915) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/28761)_

#### AC 2.4.7-p3 での環境固有の単体テストの失敗

この問題は、すべてのバージョンと環境で再現されない単体テストのエラーを修正します。 以前は、修正するために、ライブラリバージョンが異なったり、新しいバージョンで追加された機能が欠落していたりしたために、一部の単体テストが失敗していました。

_ACP2E-3712 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/9ad7d277)_

#### [ 単体テスト ] Magento\GiftCardImportExport\Test\Unit\Model\Import\Product\Type\GiftCardTest::testIsRowValid

ランダムに失敗する単体テストの修正が提供されました

_ACP2E-4263_

### UI フレームワーク

#### [ 問題 ] より少ないファイルの 1 つから重複した変数を削除する

システムは、より少ないファイルから重複した変数を削除するようになり、よりクリーンで効率的なコードを保証します。 以前は、これらの重複した変数が less ファイルに含まれていたため、コードに不要な冗長性が生じていました。

_AC-11743 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/31154) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/31150)_

#### 動的行のWYSIWYGが空です

動的行のWYSIWYG フィールドが正しく初期化され、入力されるようになりました。
以前は、動的な行のWYSIWYG フィールド（デザイン設定フォームなど）が空のように見えたり、特定の操作の後にコンテンツが失われたりする場合があり、データを復元するには手動の操作が必要でした。
AC-12336

_AC-12336 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/38893) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/7bdafaa2)_

#### [ 問題 ] MIME タイプタイプの修正

システムは、gif 画像の MIME タイプとタイプミスを正しく処理して修正しました

_AC-8001 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/36899) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/36669)_

#### [ 問題 ] `@author` から禁止されている `Magento_Backend` タグを削除する

この PR は、コードベースから `@author` タグを削除します

_AC-8814 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/37522) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/36976)_

#### [ 問題 ] レビューリストの Ajax に直接アクセスできないようにする

システムは Ajax を正しく処理し、レビューリストへの直接アクセスを避けます

_AC-9381 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/37920) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/33876)_

#### 共有 Cookie を使用したマルチストア設定でヘッダーのログイン/ログアウトが更新されない

ログアウト時に、設定に従ってログインヘッダーが正しく更新される。 カスタマーアカウントがグローバルに共有されている場合、customer-data.js は cookie を使用して「mage-customer-login」値を保存します。 それ以外の場合は、ローカルストレージが使用されます。

_ACP2E-4149 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/e885088b)_

#### [ モバイル ]Fotorama は画像ビューアの閉じるアクションでミニカートを開くことができます

Fotorama の問題を修正しました。 以前は、画像ビューアの閉じるアクションでミニカートが開いていました

_ACP2E-4231 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/e885088b)_

#### 結合された js ファイルが、多くのストアを持つプロジェクトで正しく生成されない。

複数のストアが設定されている場合、JavaScript ファイルの結合が正しく機能するようになりました。
以前は、複数ストアの設定でファイルが正しく結合されず、結果が不完全であったり、一貫性がなかったりすることがありました。

_ACP2E-4246 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/ab891304)_

### アップグレード：互換性アップグレードツール

#### 非推奨（廃止予定）の機能：動的プロパティ Magento\Framework\Acl::$_roleRegistry の作成

非推奨（廃止予定）の機能エラーで、アップグレード後に管理パネルにアクセスできなくなりました。
以前は、Magento 2.4.6 にアップグレードした後に管理パネルにアクセスしようとすると、次のエラーが発生する可能性がありました。
「非推奨の機能：動的プロパティ Magento\Framework\Acl::$_roleRegistry の作成は、vendor/magento/framework/Session/SessionManager.phpの 186 行目で非推奨になりました」
これにより、管理者はログインできませんでした。
AC-12343

_AC-12343 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/37469)_

#### GUID がセキュリティで保護された形式として保存されていません

_AC-15809_

#### アップグレード互換性ツールの重大な問題が間違っています

該当なし

_ACP2E-3856_
