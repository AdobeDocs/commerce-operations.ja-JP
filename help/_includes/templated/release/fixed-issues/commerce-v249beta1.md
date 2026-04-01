---
source-git-commit: 34e2262ad8b4fa1a2e7ade8d3b16258f9873822d
workflow-type: tm+mt
source-wordcount: '26949'
ht-degree: 0%

---
# Adobe Commerceで修正された問題（v2.4.9-beta1）

## v2.4.9-beta1で修正された問題

Adobe Commerce 2.4.9-beta1 コアコードの560の問題を修正しました。 このリリースに含まれる修正された問題のサブセットについて、以下で説明します。

### API

#### 「Special Price To Date」は、「applySpecialPrice」で誤って検証されています

システムは特別価格に関して正常に機能しており、製品の特別価格は、管理者またはREST APIによるサードパーティシステムによって設定された日付に期限切れになります

_AC-13130 - [GitHub issue](https://github.com/magento/magento2/issues/39169) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/39690)_

#### WebAPI パラドックスによる[WebAPI]のお客様のメール確認

確認の前にトークンを必要とする認証のパラドックスにより、顧客がWebAPIを介してアカウントをアクティブ化できない問題を修正しました。 このアップデートにより、未確認の顧客はAPIを通じてアカウントを正常にアクティベートできるようになり、一貫性のある機能的な確認フローを実現できます。

_AC-13281 - [GitHub issue](https://github.com/magento/magento2/issues/39255) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/c95ed7d7)_

#### 支払い情報のみを含むREST APIを使用して注文を作成する際に、管理ダッシュボードに請求先住所エラーが表示されない

請求先住所なしでAPI経由で注文を作成し、管理者ダッシュボードがクラッシュする問題を修正しました。
請求先住所のない注文は制限され、作成されなくなります。

_AC-14049 - [GitHub issue](https://github.com/magento/magento2/issues/39651) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/36d4d6fb)_

#### Rest APIでの製品のカートへの追加の問題

特定のweb サイトに割り当てられていない製品をカートに追加して購入できる問題を修正しました。
これで、「追加しようとしている製品は使用できません」というエラーメッセージが表示されます。

_AC-15054 - [GitHub issue](https://github.com/magento/magento2/issues/40029) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/f5cc09fc)_

#### ストアラベルを更新すると、属性オプションラベルが上書きされる

REST APIを介して複数選択製品属性を更新すると、すべてのstore_labelsが上書きされ、既存のストア固有のラベルが削除される問題を修正しました。
これで、デフォルトのストアビューラベルを更新する際に、Magentoは、提供されたラベルを完全に上書きするのではなく、既存のラベルと結合します。
これにより、更新後も、他のストアビューのストア固有のラベルがそのまま維持されます。

_AC-15208 - [GitHub issue](https://github.com/magento/magento2/issues/40093) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/36d4d6fb)_

#### [問題]明確化属性オプションは既に応答が存在します

システムは、「新しいファイル名を取得」という厄介なフレーズを、より明確で文法的に正しいバージョンに置き換えました。「新しいファイル名を取得します。既に存在する場合」 これにより、読みやすさとユーザー理解が向上します。
属性オプションの応答についても同様です。

_AC-15473 - [GitHub issue](https://github.com/magento/magento2/issues/39943) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/39941)_

#### /V1/products/special-price API エンドポイントの内部サーバーエラー

/V1/products/special-priceおよび関連する価格APIに対する形式が正しくないリクエストで、null TypeErrorが原因で500の内部サーバーエラーが返される問題を修正しました。
現在では、APIが入力を適切に検証し、無効なペイロードに対して400 エラーを返すようになり、エラー処理とAPIの信頼性が向上しています。

_AC-6419 - [GitHub issue](https://github.com/magento/magento2/issues/35934) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/a7ef6300)_

#### `/V1/order/&lbrace;orderId&rbrace;/ship` API エンドポイントの内部サーバーエラー

システムは、`/V1/order/{orderId}/ship` API エンドポイントの内部サーバーエラーを修正し、リクエストの形式が正しくないときに400 エラーを返すようになりました。

_AC-6420 - [GitHub issue](https://github.com/magento/magento2/issues/35931) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/38282)_

#### /V1/creditmemo API エンドポイントの内部サーバーエラー

/V1/creditmemo APIに対する形式が正しくないリクエストが500の内部サーバーエラーを返す問題を修正しました。
これで、APIはリクエストを適切に検証し、無効なペイロードに対して400 エラーを返すようになり、エラー処理と安定性が向上しました。

_AC-6422 - [GitHub issue](https://github.com/magento/magento2/issues/35924) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/a7ef6300)_

#### Rest APIとMagento バックエンドでは、新しい属性を作成する際に、attribute_codeに異なる検証方法を使用します

Magento管理者がattribute_codeで大文字を許可したが、REST APIが製品属性の作成中に大文字を拒否する不整合を修正しました。
現在では、AdminとREST APIの両方が同じ検証に従い、大文字の属性を正常に作成できるようになりました。

_AC-6660 - [GitHub issue](https://github.com/magento/magento2/issues/33138) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/8670a2b4)_

#### REST APIによる属性作成と更新の検証が異なる

REST APIによる属性作成中に一貫性のない検証が行われ、backend_typeが正しく割り当てられなかった問題を修正しました。
これで、有効な場合は正しいバックエンドタイプが設定され、無効な値に対して例外がスローされるか、指定されていない場合は適切にフォールバックされ、一貫した属性動作が保証されます。

_AC-6885 - [GitHub issue](https://github.com/magento/magento2/issues/36327) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/64823f95)_

#### 無効なリクエスト本文またはパラメーターが「内部サーバーエラー」の原因となる

形式が正しくないリクエスト本文またはパラメーターが、「400 Bad Request」という明確な応答を返すようになりました。
以前は、様々なREST API エンドポイント（/V1/carts/search、/V1/orders、/V1/productsなど）に不正なリクエスト本文またはパラメーターを送信すると、一般的な「内部サーバーエラー」（500）が発生し、入力の問題を診断するのが困難でした。
現在、Adobe Commerceは「400 Bad Request」応答を返し、リクエストが無効な場合に明確なフィードバックを提供します。

_AC-746 - [GitHubの問題](https://github.com/magento/magento2/issues/32784) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/f1adb44e)_

#### `/orders` （または`/orders/:id`）エンドポイントに「state」フィールドと「status」フィールドがありません

データベース値がnullの場合、`/orders`および`/orders/{id}` API応答で状態フィールドとステータス フィールドが省略される問題を修正しました。
現在では、両方のフィールドが一貫して応答で返され、API ドキュメントへの準拠を確保し、データの信頼性を向上させています。

_AC-9244 - [GitHub issue](https://github.com/magento/magento2/issues/37807) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/01cee3c3)_

#### 非同期バルク操作は、async.magento.configurableproduct.api.optionrepositoryinterface.save.postのオープン状態のままです

Bulk API エンドポイントは、リクエスト本文が配列でない場合にエラーをスローするようになりました。したがって、バルクアイテムキーは0から始まる連続した数値である必要があります。 以前は、一括リクエストで送信された任意のアイテムキーが原因で、一括項目のステータスが更新されませんでした。

_ACP2E-3544 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/9608ca21)_

#### searchCriteriaを使用して現在のストアから考慮されないis_subscribed値に関する[CLOUD] API REST バグ

API REST Customer クエリーは、searchCriteriaを使用して、正しいストアから正しい「is_subscribed」値を取得します
以前は、API REST顧客クエリでis_subscribed&quot;値を取得する際にストアを考慮していませんでした。

_ACP2E-3621 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/9608ca21)_

#### async.operations.allは、1つのSKUに複数のエントリを作成できます

同じ製品を保存して更新する同時リクエストは、データの不整合や製品の重複につながる競合状態を防ぐためにシリアル化されるようになりました

_ACP2E-3744 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/520f9e30)_

#### 注文「base_row_total」と「row_total」は、REST API応答で1つの商品価格を表示します

複数の同じ項目が注文された場合に備えて、注文の詳細に対するREST api応答に、「base_row_total」属性と「row_total」属性の正しい値が含まれるようになりました

_ACP2E-3874 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/4ca73607)_

#### REST API エンドポイント export-stock-salable-qtyが誤った項目total_countを返す

total_countがページサイズに誤って制限される在庫エクスポート在庫販売可能数量APIのページネーションの問題を修正しました。 以前は、/rest/all/V1/inventory/export-stock-salable-qty/website/base エンドポイントをpage_size=5などのページネーションパラメーターと共に使用する場合、レスポンスのtotal_count フィールドには、検索条件に一致する実際の製品総数ではなく5が返されていました。 この修正の後、total_count フィールドに、page_size パラメーターに関係なく使用可能な製品総数が正しく反映されるようになり、すべてのMagento REST API エンドポイントで一貫したページネーション動作が保証されるようになりました。

_ACP2E-4086 - [GitHub コードの貢献度](https://github.com/magento/inventory/commit/5632fb5e)_

#### カート項目REST APIのカスタムオプション IDに関する検証の問題。

REST API V1/guest-carts/&lt;cartId>/items/およびV1/carts/mine/items/は、「product_options.extension_attributes.custom_options」を検証するようになりました。*.option_id&quot;を使用して、買い物かご商品SKUの有効なoption_idを参照します。 以前は、このパラメーターは処理され、検証なしでデータベースに保存されていました。

_ACP2E-4138 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/a1c57b2e)_

#### 買い物かごから商品を取得し、ストアヘッダーの言語を変更しても変更されない

GraphQL customerCart クエリで、ストアヘッダーの値に従って商品属性値が返されるようになりました。 以前は、GraphQLを使用してカートから商品を取得する際に、ストアヘッダーの言語を変更しても、更新された言語が反映されず、ローカライズに一貫性がありませんでした。

_ACP2E-4227 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/6e134409)_

#### ギフトカード製品のREST API /media エンドポイントが失敗する – 「製品を保存できません」が返される

修正の前は、グローバルスコープに金額を含まないギフトカード商品を作成できました。 修正により、グローバルスコープの金額をチェックする検証が追加されました。

_ACP2E-4395_

### API、カート、チェックアウト

#### 出荷情報の場合、REST APIを使用してサーバーサイド検証が機能しない

REST APIで、出荷先住所情報の検証が管理者バックエンドで定義された属性設定に準拠しない問題を修正しました。 検証は、設定された設定に従って適切に行われるようになりました。

_ACP2E-4156 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/45cbf9b6)_

### API、カタログ

#### デフォルトのweb サイト/ストアの改行価格API エンドポイントの削除

以前は、デフォルトの基本web サイトを削除し、セカンダリ web サイトをデフォルト web サイトとして使用していたため、セカンダリ web サイトの階層の価格を更新しようとしたときにエラーが発生していました。 ただし、この修正を適用した後は、基本web サイトが削除または非アクティブ化された場合でも、ティア価格を正常に更新できます。

_ACP2E-4334 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/0a3b7032)_

### API, フレームワーク

#### アプリケーションサーバーでのRedisRequestLogger\RedisClient （レート制限）例外

修正後、PHP redis拡張機能がインストールされている場合は、レート制限機能をGraphQL アプリケーションサーバーと一緒に使用できます。

_ACP2E-4237 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/e885088b)_

### API、インポート/エクスポート

#### Async Invoice Refund APIは、オンライン返金ではなくオフライン返金を作成します

`is_online` パラメーターを持つ返品要求が正しく処理されなかった非同期返品処理を修正しました。

_ACP2E-4394 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/61c96348)_

### API、注文

#### [CLOUD]注文情報の問題で、注文000075568ージの行の合計表示が発生する

注文API応答のrow_total_incl_tax値が、項目が完全に割引されたときに0.00ではなく、ほぼゼロの残存値として返された問題を修正します。

_ACP2E-3950 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/462ede94)_

### アカウント

#### [問題] カタログウィジェットテンプレートオプションのタイプミスを修正

カタログウィジェットのテンプレートオプションのタイプミスが修正されました。

_AC-11576 - [GitHub issue](https://github.com/magento/magento2/issues/38185) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/38178)_

#### [問題] バックエンド グリッドの不要な間隔を削除しました

選択した項目がある場合、バックエンドグリッドの不要な間隔が削除されるようになりました

_AC-11579 - [GitHub issue](https://github.com/magento/magento2/issues/38502) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/32622)_

#### マルチバイト文字を使用する場合、保存された顧客グループコードが入力と一致しません

マルチバイト文字を使用する顧客グループコードが切り捨てられ、入力された値と一致しない問題を修正しました。 このアップデートにより、完全な入力が正しく保存され、マルチバイト名を持つ顧客グループを正確に作成できるようになります。

_AC-13335 - [GitHub issue](https://github.com/magento/magento2/issues/39342) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/a06a4a57)_

#### @および.swiss ドメインを含む管理パネルでお客様の電子メールを更新する際の問題

管理パネルで、特殊文字と.swiss ドメインを含む顧客メールが受け付けられるようになりました。
以前は、max@möstermann.swissなどのアドレスに顧客の電子メールを更新すると、無効なホスト名とTLDに関するエラーが発生して失敗していました。
AC-13409

_AC-13409 - [GitHub issue](https://github.com/magento/magento2/issues/39394) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/d3ea191d)_

#### ニュースレター購読対応スイッチがweb サイト/ストアごとに機能しない

グローバルレベルで無効になっている複数のweb サイト/ストアビューがある場合、システムはニュースレターの購読を正しく処理します

_AC-14283 - [GitHub issue](https://github.com/magento/magento2/issues/39751) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/39752)_

#### 「製品が表示されました」顧客セグメント条件の廃止

「製品が表示されました」顧客セグメントの条件は非推奨になりました。
以前は、この条件を使用すると、大量のMySQL クエリが原因でサイトが停止する可能性がありました。 この条件は非推奨とマークされ、サポートされなくなりました。

_AC-14542_

#### [問題]電子メールの開示を削除しました

入力された電子メールが顧客の存在に関わらず、アカウントの確認に必要でない場合に、誤った電子メールを示すエラーメッセージが表示されるようになりました。

_AC-14561 - [GitHub issue](https://github.com/magento/magento2/issues/39574) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/39570)_

#### GraphQLのミューテーション `updateProductsInWishlist`を使用してウィッシュリスト項目のコメントをクリアできません

ウィッシュリストコメントがGraphQLの変更によって更新されない問題を修正しました。
コメントが正しく更新され、API応答とストアフロントの両方に反映されるようになりました。

_AC-14682 - [GitHub issue](https://github.com/magento/magento2/issues/39911) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/36d4d6fb)_

#### モバイルで削除された製品は、再ログインするまでWebのミニ比較セクションに表示されます

これで、ミニ比較セクションを含め、モバイルとwebの両方のすべての比較ビューから製品がすぐに消えるようになりました。

_AC-14703 - [GitHub issue](https://github.com/magento/magento2/issues/39905) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/40023)_

#### 「いいえ」に設定すると、接頭辞/接尾辞の設定が無視される

設定で無効にした場合でも、顧客名の接頭辞/接尾辞が引き続き注文で表示される問題を修正しました。
これで、プリフィックス/サフィックス値は、設定に基づいて注文の詳細から削除されます。

_AC-15074 - [GitHub issue](https://github.com/magento/magento2/issues/40036) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/a3b1abc2)_

#### ストアフロント顧客アカウント登録：メールアドレス形式が異なるドメイン形式で変換される

このバグは、ドメイン内の特殊文字（例：òbe.com）を含む顧客メールが自動的にパンニーコード形式（tec55241@xn--adbe-mqa.com）に変換される問題を修正しました。
Magento 2.4.9-alpha3では、この修正により、このようなメール IDが変更されずに有効な状態に保たれ、配信エラーが発生しないようにします。

_AC-15177 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/68a45d0a)_

#### 登録フォームに検証メッセージがありません（mage-error）

顧客アカウント作成ページの必須フィールドで、空のままにすると検証メッセージが表示されない問題を修正しました。
現在では、すべての空のフィールドまたは正しくないフィールドに対して、適切なエラーメッセージが表示されます。

_AC-15185 - [GitHub issue](https://github.com/magento/magento2/issues/40076) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/36d4d6fb)_

#### 注文キャンセル モーダルのタイトルに翻訳がありません

システムは、ストアフロントの注文キャンセルモーダルで欠落している翻訳を修正するようになりました。 お客様がマイアカウント/マイオーダーのページから「キャンセル」ボタンをクリックすると、キャンセル理由を求めるモーダルが表示されます。 ただし、モーダルタイトルは以前はハードコードされており、翻訳できませんでした。 この変更により、モーダルタイトルで適切な翻訳方法が使用されるようになります。

_AC-15260 - [GitHub issue](https://github.com/magento/magento2/issues/40098) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/40100)_

#### Magento 2.4.8-p1でのログイン後の問題

Magento 2.4.8-p1で、ログイン後も「アカウントを作成」リンクがホームページに表示されたままになる問題を修正しました。
これで、他のページと一致して、ログイン後にリンクが正しく非表示になりました。

_AC-15292 - [GitHub issue](https://github.com/magento/magento2/issues/40120)_

#### [問題]お客様を削除する前にisSecureAreaを設定しました

現在、システムは正常に動作しており、このPR セットは削除プロセス用のSecureAreaであり、お客様は正常に再登録できます。

_AC-15723 - [GitHub issue](https://github.com/magento/magento2/issues/40211) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/38462)_

#### 顧客アカウントの作成中に現在の領域エラーが発生した場合、[Cloud]削除操作は禁止されています

無効なアドレスを持つ顧客を保存すると、無関係な「現在の領域に対する削除操作は禁止されています」ではなく、無効な理由を説明するメッセージが返されます。

_ACP2E-3791 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/6ea61121)_

#### &#39;eav&#39; キャッシュが無効になっている場合、[B2B] Webapi リクエストは、ログインした顧客に対して無限ループになります

修正後、Eav キャッシュを無効にしても、特定のREST リクエスト中に無限ループが発生することはありません。

_ACP2E-4191 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/45cbf9b6)_

#### ロケールの読み込み中にエラーが発生しました

アラビア語のロケールを使用する際に顧客アカウントの作成が失敗し、ストアフロントに「生年月日」属性が表示されるように設定されていた問題を修正しました。 この設定でアカウントを正常に作成できるようになりました。

_ACP2E-4311 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/2687b487)_

#### アカウント情報を更新する際のエラー「無効な日付」

お客様は、アラビア語ロケールを使用する際に、アカウントを正常に更新できるようになりました。 以前は、アカウント情報を保存しようとしましたが、無効な日付エラーが原因で生年月日が失敗しました。

_ACP2E-4344 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/31258bf6)_

#### 招待状の送信機能の警告メッセージ

「招待メールにカスタムメッセージを追加する顧客を許可」設定が無効になっている場合に、招待を送信ページでメールフィールドを追加する際に、警告メッセージ「最大X メールアドレスが許可」が表示されない問題を修正しました。
以前は、カスタムメッセージが有効になっている場合にのみ警告が表示され、一貫性のないユーザーエクスペリエンスが作成されていました。 これで、カスタムメッセージの設定設定に関係なく、メールの最大限警告が一貫して表示されるようになりました。

_ACP2E-4374_

### アカウント、管理者UI

#### [Cloud] CartIdを持つそのようなエンティティはありません

同じセッションで2つの会社管理者アカウントを使用して「顧客としてログイン」を使用すると、「cartIdを持つエンティティがありません」というエラーが発生する問題を解決しました。

_ACP2E-4137 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/e885088b)_

#### 顧客作成フォームのエラーメッセージが翻訳されない

顧客検証エラーメッセージが異なるインターフェイス間で適切に翻訳およびフォーマットされない問題を修正しました。 検証エラーにより、ストアフロント、adminhtml、rest api、graphqlなど、アプリケーションのすべての領域で正しく翻訳されたメッセージが表示されるようになりました。

_ACP2E-4354 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/31258bf6)_

### 管理者UI

#### カテゴリ製品グリッド/ステータスと表示可能列は、名前で並べ替えると空になります

製品名で並べ替える際に、カテゴリ製品グリッドのステータス列と表示列が空で表示される問題を修正しました。
グリッドは、並べ替え後のすべての列データを正しく表示するようになり、管理者パネルに正確な製品情報が表示されるようになりました。

_AC-10659 - [GitHub issue](https://github.com/magento/magento2/issues/38233) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/3cf1a106)_

#### メールテンプレート store-switcher

非推奨のjQuery コードが原因で、ニュースレター電子メールテンプレートのプレビューのストアスイッチャーがクリックされたときに開かない問題を修正しました。 読み込みイベントを更新すると、ユーザーがストアスイッチャーに期待どおりにアクセスできるように、適切な機能が復元されました。

_AC-12334 - [GitHub issue](https://github.com/magento/magento2/issues/38892) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/8670a2b4)_

#### 買い物かごページと商品ページのFPT値は、シンプルな商品の同じ設定で異なります

FPT値が、シンプルな商品のカートページと商品ページで一貫するようになりました。
以前は、固定製品税（FPT）の値は、同じ設定が適用された場合でも、買い物かごと製品ページの間の小数点以下桁が異なる場合がありました。
AC-13066

_AC-13066 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/8953613e)_

#### スウォッチモジュールが無効になっている場合、複数選択/選択属性オプションを保存できない

スウォッチモジュールが無効になっている場合、複数選択/選択属性オプションを保存できるようになりました。
以前は、スウォッチモジュールを無効にすると、新しい複数選択/選択属性オプションを作成する際に例外が発生していました。
AC-13071

_AC-13071 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/8953613e)_

#### カート ページと製品ページのFPT値は、動的な製品の同じ構成で異なります

FPT値が、動的な商品のカートページと商品ページで一貫するようになりました。
以前は、FPT （固定製品税）の値は、同じ設定の買い物かごと製品ページの間の小数点以下桁が異なる場合がありました。
AC-13075

_AC-13075 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/8953613e)_

#### 日付UI コンポーネントで日付形式が尊重されない

日付UI コンポーネントが設定された形式を無視し、誤った値を表示する問題を解決しました。 この修正により、表示と入力の両方で、指定された形式（Y-m-dなど）を日付フィールドが尊重されるようになりました。

_AC-13174 - [GitHub issue](https://github.com/magento/magento2/issues/39218) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/913bf1a6)_

#### ソースを削除するオプションがありません

管理UIにインベントリソースの「削除」オプションを追加し、管理者が追加のソースを有効または無効にするのではなく、削除できるようにしました。 この機能強化により、未使用のソースをより適切に制御できるようになり、在庫管理が改善されます。

_AC-13354 - [GitHub issue](https://github.com/magento/magento2/issues/32362) - [GitHub コードの貢献度](https://github.com/magento/inventory/commit/1b6c8a3e)_

#### 管理画面のカテゴリーツリーが展開されず、レベル 3から選択したすべてのネストされたカテゴリが表示されない

管理者カテゴリーツリーが展開されず、レベル 3を超える選択したネストされたカテゴリが表示される問題を修正しました。 修正後、選択したすべてのカテゴリが自動的に拡張され、カテゴリ関連の条件をまたいで可視性と使いやすさが向上します。

_AC-13363 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/913bf1a6)_

#### [問題]役割ツリーでユーザーエクスペリエンスを向上させる

このプルリクエストでは、すべての項目を折りたたむ、すべての項目を展開する、選択した項目を含む分岐を展開するボタンが追加されます。 この機能は、カテゴリーツリー（カタログ/在庫/カテゴリ）で提供される機能と似ています

_AC-14020 - [GitHub issue](https://github.com/magento/magento2/issues/39654) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/36511)_

#### 読み込み/書き出しのアクションログがシステム/アクションログ/レポートグリッドに作成されない

読み込み/書き出し管理アクションのログを実装し、システム/アクションログ/レポートに表示できるようにしました。 これにより、以前は見つからなかったインポートアクティビティを記録することで、監査の追跡が改善されます。

_AC-14266 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/b5e99d20)_

#### Symfony\Component\Mime\Exception\LogicException: &quot;Sender&quot; ヘッダーは&quot;Symfony\Component\Mime\Header\MailboxHeader&quot;のインスタンスである必要があります（&quot;Symfony\Component\Mime\Header\MailboxListHeader&quot;を取得）

カスタムのリターンパスアドレスがSMTP用に設定されている場合に、Adobe Commerceが登録メールを正常に送信するようになりました。 以前、Vanilla Adobe Commerce 2.4.8でsystem/smtp/set_return_pathを2に設定し、system/smtp/return_path_emailをカスタムアドレスに設定した場合、お客様の登録は完了しましたが、登録メールは送信されませんでした。Adobe Commerceは次のエラーを記録しました。Symfony\Component\Mime\Exception\LogicException:「Sender」ヘッダーは「Symfony\Component\Mime\Header\MailboxHeader」のインスタンスである必要があります（取得しました「Symfony\Component\Mime\Header\MailboxListHeader」）。

_AC-14520 - [GitHub issue](https://github.com/magento/magento2/issues/39823) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/1e14bd72)_

#### 更新注文で最新のカスタム属性データが取得されない

注文ページを更新しても最新の顧客カスタム属性データが表示されない問題を修正しました。修正後、更新された属性値が、注文をキャンセルして再作成することなく反映されるようになりました。

_AC-14690 - [GitHub issue](https://github.com/magento/magento2/issues/30301)_

#### [問題]非推奨のエスケーパーを置き換える

非推奨のgetEscaper （）を削除し、コンストラクタのインジェクションを介して追加しました。

_AC-15132 - [GitHub issue](https://github.com/magento/magento2/issues/40062) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/38135)_

#### モバイルビューで商品カテゴリと重なるウェルカムメッセージ

ウェルカム名がモバイルビューの製品カテゴリと重なり、クリックがブロックされるUIの問題を修正しました。
これにより、カテゴリーが包括的に表示され、重複の問題なくクリックできるようになりました。

_AC-15166 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/1b1baf1d)_

#### Ui フォームのリセットボタンが期待どおりに機能しない

ページ全体を再読み込みせずにリセットボタンをクリックすると、フォームデータがリセットされるので、システムは正常に動作しています。

_AC-15204 - [GitHub issue](https://github.com/magento/magento2/issues/40092) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/40094)_

#### [問題] PageCache/AccessList: CIDR サポートの追加

システムがネットワーク内のパージ要求を受け付けるようになったため、CIDR範囲を提供するだけがより簡単になりました。

_AC-15804 - [GitHub issue](https://github.com/magento/magento2/issues/39953) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/37809)_

#### [問題] キャッシュ管理ボタンに説明タイトルを追加する

カーソルを移動すると、システムによってキャッシュ管理ボタンに説明タイトルが追加されるようになりました

_AC-16212 - [GitHub issue](https://github.com/magento/magento2/issues/38607) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/38598)_

#### グリッドを使用して税率を一括削除する機能を提供します

管理者ユーザーは、「管理者税率」グリッドから複数の税率を同時に削除できるようになりました。  [GitHub-33399](https://github.com/magento/magento2/issues/33399)

_AC-2238 - [GitHubの問題](https://github.com/magento/magento2/issues/33399) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/33484) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/5cd64dd0)_

#### 管理画面の静的グリッドにホバーカラーが適用されない

管理者の静的グリッドの行にホバーカラーが期待どおりに適用されるようになりました。[GitHub-35358](https://github.com/magento/magento2/issues/35358)

_AC-2916 - [GitHub issue](https://github.com/magento/magento2/issues/35358) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/35384)_

#### Google reCAPTCHA管理パネルのexception.logの「reCAPTCHA パラメーターを解決できません」エントリ

Google V3 reCAPTCHA管理者ログイン用の`var/log/exception.log` ファイルのreCAPTCHA エラーが解決され、エラーメッセージは記録されません。 以前は、管理者ユーザーが&#x200B;**Configuration** > **Security** > **Google reCAPTCHA Admin Panel**&#x200B;の設定を行うと、数秒ごとに次のエラーがスローされていました：`main.ERROR: Can not resolve reCAPTCHA parameter. {"exception":"[object] (Magento\Framework\Exception\InputException(code: 0): Can not resolve reCAPTCHA parameter. at /home/xxxxxxx/public_html/vendor/magento/module-re-captcha-ui/Model/CaptchaResponseResolver.php:25)"} []`。  [GitHub-34975](https://github.com/magento/magento2/issues/34975)

_AC-3179 - [GitHubの問題](https://github.com/magento/magento2/issues/34975) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/4f7e5983) - [GitHub コードの貢献度](https://github.com/magento/security-package/commit/804dbc2a)_

#### 条件SKUを持つカート価格ルールでは、SKUの「先頭のゼロ」は考慮されません（SKU:01234は1234と同じです）

SKUの「先頭のゼロ」を考慮した条件SKUを持つカート価格ルールが正しく処理されるようになりました

_AC-9428 - [GitHub issue](https://github.com/magento/magento2/issues/37919) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/39525)_

#### Multiselectのデフォルト属性オプションの値の動作に関する問題

複数のオプション属性のデフォルト値を修正する前は、正しく保存されていませんでした。 これで、修正後、値はデータベースに正しく保存されます。

_ACP2E-3523 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/9608ca21)_

#### バックエンド管理メニューの字幕が表示されない

メインメニューグループのすべてのタイトルが適切に表示されるようになりました。 以前は、メインメニューの2列目または3列目にリンクのグループが1つしか含まれていない場合、グループのタイトルは表示されませんでした。

_ACP2E-3540_

#### 管理画面から製品数量を買い物かごに戻す際の問題

管理者から注文を作成する場合、サイドバーの顧客カート内の商品は、注文に追加しても消えません。

_ACP2E-3563 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/c8ba4ab1)_

#### 制限付き管理者ユーザーは、製品ステータスを一括更新できません

カスタム管理者は、web サイトレベルのプロパティであるため、製品ステータスを一括更新できます。 ステータスは、制限付き管理者がアクセス権を持つweb サイトでのみ更新されます。

_ACP2E-3772_

#### [ ステージング 2] ストアド カードは管理パネルに表示されません

アップグレード後に「ストアドカード」支払いオプションがバックエンドの注文配置フォームに表示されなくなった問題を修正します。

_ACP2E-3830 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/7accebfa)_

#### 制限付き管理者ユーザーは、ストア固有の権限にもかかわらず、デフォルト設定を保存または更新できます

制限付き管理者ユーザーが、特定のweb サイトスコープのみに割り当てられていたにもかかわらず、「デフォルト設定」スコープを表示および更新しようとすると、混乱が生じる可能性がある問題を修正します。

_ACP2E-4011 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/2a1e1e55)_

#### ストアビューのスコープに対してDBに保存された設定可能な製品価格が原因で、カテゴリ内の製品の並べ替え機能で、保存された価格がフロントエンドに関係しない問題が発生する

web サイトごとに価格が設定され、管理UIの設定可能な製品編集ページでストアビューが選択されている場合に、設定可能な製品の「デフォルト値を使用」チェックボックスを削除しました。

_ACP2E-4036 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/fab20b00)_

#### [QUANS]管理者パスワードポリシーがPCI DSS 4.0認定に準拠していません（12文字以上）

管理者は、ストア/設定/詳細/管理者/セキュリティを通じて、管理者ユーザーの最小パスワード長の要件を設定できるようになりました。 この機能強化により、既存のパスワードポリシーを維持しながら、セキュリティの柔軟性が向上します。 検証は、管理者ユーザーの作成/変更および設定の保存中に実施され、ユーザーエクスペリエンスを向上させるためにリアルタイムのフロントエンド検証が行われます。

_ACP2E-4044 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/47721be6)_

#### 管理者インターフェイスの言語が日本語の場合の日付フィルターの問題

誕生日フィルターと列では、「お客様以降」フィルター/列と同じ統合形式M/d/yを使用します

_ACP2E-4052 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/52f46328)_

#### 管理者グリッドヘッダーの両側に表示される白いブロック

管理者グリッドの視覚的な整列の問題を修正しました。 以前は、管理パネルで製品グリッドを水平方向にスクロールすると、グリッドヘッダーの左側と右側に白いブロックが正しく表示されなくなっていました。 スクロール時にグリッドヘッダー要素が適切な垂直方向の整列を維持するようになり、管理者が大規模な製品カタログを管理する際に、よりクリーンなビジュアル体験を提供するようになりました。

_ACP2E-4104_

#### 2.4.8-p1/ 2.4-developでUi コンポーネントのfileUploaderが正しく動作しない

複数の選択を使用してカスタム ui コンポーネントのファイルアップロードを改善し、アップロード領域のクリック時のアップロードを許可しました。

_ACP2E-4162 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/ee918f0d)_

#### [Prem]で新しく作成された注文/会社/顧客は、選択プロセス中に「すべてを選択」スコープに自動的に含まれます

古い管理グリッドページですべてのレコードを手動で選択すると、一括操作を実行する際にすべてのレコードが誤って削除される問題を修正しました。 以前は、選択した項目の数が合計数に一致すると、グリッドが自動的に「すべてを選択」モードに切り替わり、明示的に選択した項目だけでなく、すべてのレコードに一括操作が影響を与えていました。

_ACP2E-4202 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/6e134409)_

#### ACP2E-3362のソリューションは、MariaDB 10.6で動作が遅い

多数の履歴検索リクエストが発生した場合のフロントエンド検索ページのパフォーマンスが向上しました。

_ACP2E-4225 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/ab891304)_

#### クレジットメモグリッドのストアタイムゾーンに従って日付フィルターが機能しない

修正前の日付属性によるフィルタリングリストでは、選択した日付と保存日の間のタイムゾーンの違いにより、欠落した項目が発生していました。修正日フィルターが適切に適用された後に、次に行います。

_ACP2E-4239 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/0a8c9a9a)_

#### pagebuilderがインストールされている場合、ファイルアップローダーダイアログが2回開きます

カスタムコンポーネントの「アップロードを修正」ボタンが2回トリガーする前。 修正が完了すると、「アップロード」ボタンが期待どおりに機能します。

_ACP2E-4241 - [GitHub コードの貢献度](https://github.com/magento/magento2-page-builder/commit/5c4ae802)_

#### 顧客データを変更する際に、削除された顧客属性の検証エラーが発生する。

修正の前に、削除された複数の属性オプションが含まれている場合、顧客と顧客アドレスの保存に失敗しました。 修正の後、複数の属性オプションがまだ存在する場合でも、両方を正常に保存できます。

_ACP2E-4281 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/0a8c9a9a)_

#### 製品イメージの変更がアクションログに記録されない

製品イメージのアップロードと削除が管理者アクションログで追跡されない問題を修正しました。 以前は、管理者が製品に新しい画像を追加したり、製品のメディアギャラリーから既存の画像を削除したりすると、これらの変更はログシステムに記録されませんでした。 画像の役割（メインの製品画像、サムネール、小さな画像として画像を割り当てることなど）に対する変更のみがログに記録されていました。 現在では、画像の追加や削除を含むすべてのメディアギャラリーの変更が管理者アクションログに適切に記録され、製品画像管理アクティビティの監査証跡が完全に表示されるようになりました。

_ACP2E-4302_

#### 管理者ダッシュボードのJS警告：「ローダーを開始する必要がありますが、DOMにローダーが見つかりませんでした」

管理者ダッシュボードでチャートが有効になっている場合にブラウザーコンソールに表示されるJavaScriptの警告を修正しました。 以前は、チャートが有効になっている管理者ダッシュボードにアクセスする際に、古いデバッグチェックで、機能が正しく動作していたにもかかわらず、「ローダーを開始する予定ですが、DOMにローダーが見つかりませんでした」と誤って警告されていました。

_ACP2E-4336 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/2687b487)_

#### [CLOUD]の設定と、ストア設定で既定のチェックイン済み使用を使用する場合に編集可能な依存関係の設定

「デフォルト/Web サイトを使用」がオンになっているにもかかわらず、システム設定フィールドがページ読み込み後に有効になる場合がある問題を修正しました。

_ACP2E-4337 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/31258bf6)_

#### 管理者ダッシュボードの順序グラフが最終的なサイズにアニメーション化されます

管理者ダッシュボードの順序グラフが、不要なサイズ変更アニメーションを必要とせずに即座に表示されるようになりました。

_ACP2E-4398 - [GitHubの問題](https://github.com/magento/magento2/issues/38860) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/f7bbcb4e)_

#### JS エラーにより、ページビルダーでモバイルビューにコンテンツを保存できません（TypeError：未定義のプロパティを読み取れません）

モバイルビューでバナーを追加する際に、ページビルダーでページを保存できない問題を修正しました。

_ACP2E-4399 - [GitHubの問題](https://github.com/magento/magento2/issues/38565) - [GitHub コードの貢献度](https://github.com/magento/magento2-page-builder/commit/bdac5bca)_

### 管理UI、B2B

#### B2B Login as Customer headerにはMagentoのブランディングが残っています

以前のストアフロントのヘッダーには、「&lt;store name>に&lt;customer name>として接続されました」とMagento ブランディングが表示されていました。 これは修正され、ヘッダーはADOBEのブランディングで表示されます。

_AC-14361 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/fadcfa8b)_

### 管理者UI、カタログ

#### カタログルールがアクティブでリアルタイムモードが有効になっている場合、製品の保存が失敗する

カタログルールインデックス作成を製品トランザクションから切り離すことにより、製品の保存操作中にDDL トランザクションエラーが発生し、カタログルールインデックス作成が失敗する問題を修正しました。

_ACP2E-4378 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/f7bbcb4e)_

### 管理者UI、コンテンツ

#### 画像の挿入中に「メディアアセットパスのレンディションを作成できません」という例外が発生する

Media Gallery Image Optimization設定の「最大幅」および「最大高さ」の値を削除すると、画像最適化プロセス中にエラーが発生しなくなります。

_ACP2E-3781 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/520f9e30)_

### 管理者UI、注文

#### 管理者注文の作成：20以上の製品を追加する場合のセッションサイズオーバーフロー（セッションサイズが256 KBの制限を超えています）

管理者の注文作成時にセッションサイズオーバーフローが発生する問題を解決しました。これにより、大きなHTMLのレスポンスがJSON リクエストのセッションに保存されるのを防ぎ、管理者がログアウトしなくても一括製品の追加がスムーズに動作するようになりました。

_AC-15893_

### 管理者UI, セキュリティ

#### 弱いパスワード管理

同じパスワードを使用している場合、管理者ユーザーを保存できません。 以前は、適切な検証なしに正常に保存されていました。

_ACP2E-3657 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/df92debe)_

### 管理者UI、セキュリティ、ステージングとプレビュー

#### コンテンツのステージング用のアクションログ

アクションログには、ステージング更新アクティビティが表示されます。 以前は、ステージング更新ログは管理者アクションログに記録されていませんでした。

_ACP2E-3679_

### 管理者UI、税金

#### 税率の管理UI エラー

このチケットは、国の切り替え（米国から英国など）が以前に選択した米国の状態→まだ表示され、誤解を招くユーザーが表示される税率管理UIの問題を修正しました。
2.4.9-alpha3では、選択した国にステートがない場合、「ステート」フィールドが*にリセットされるようになりました。

_AC-8440 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/a3b1abc2)_

### 分析/レポート

#### [問題] Google Analyticsのみを使用する場合にAnalytics用のscpが追加されました

このPRにより、CSP ホワイトリストがGoogle Analytics モジュールに追加され、Google Adwordsの依存関係がなくても独立して機能できるようになります。 Google Adwords モジュールが無効になっている場合でも、Google Analyticsが正しく機能するようになりました。

_AC-16311 - [GitHub issue](https://github.com/magento/magento2/issues/40051) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/40032)_

#### 管理者アクションログユーザーレポートに、フィルターの適用時に使用されたフィルターの詳細が表示されない

この修正を行う前は、フィルタリングパラメーターが管理者アクティビティレポートに記録されていませんでした。 修正が完了すると、すべてのリクエストデータがログに記録されます。

_ACP2E-4099_

#### 詳細レポート CSV ファイルでファイル ヘッダーが重複して、空のレポートが発生する

修正後、高度なレポート機能で生成されたレポートに、行数がバッチサイズを超える場合に重複したヘッダー行が含まれなくなりました。

_ACP2E-4187 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/45cbf9b6)_

#### カート放棄レポートに無効な文字が含まれています

CSV ファイルとして書き出されたカート放棄レポートに、MS Excelで開いたときにインド ルピーなどの通貨記号の適切にレンダリングされた文字が含まれるようになりました。

_ACP2E-4288 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/0a8c9a9a)_

#### MDVA-19640 2.4.8互換のアップデート

この修正により、分析cronのジョブタスクがデフォルトグループから分析グループに移動します

_ACP2E-4309 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/c135fc3a)_

#### カナダのWeb サイト/通貨の管理画面で注文/請求書レポートに収益が表示されない

注文に関連するレポートの中には、店舗の通貨レートを適用していないものもありました。 修正後、レポートは設定されたストア率を適切に適用します。

_ACP2E-4361 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/31258bf6)_

### B2B

#### PayFlow Pro クレジットカードの支払い方法を使用して交渉可能な見積もりを使用してチェックアウトに進む

Adobe Commerceは、Payflow Pro クレジットカード支払い方法を使用して交渉可能な見積もりからチェックアウトする際に、注文を正常に配置するようになりました。 以前、B2B機能が有効になっていて、購入者が交渉可能な見積もりからチェックアウトに進んだ場合、Payflow Proを選択して「注文する」をクリックすると、エラーメッセージなしでページが無期限に読み込まれ続け、注文は作成されませんでした。 AC-11973

_AC-11973_

#### Quoteの名前変更後の成功メッセージが断続的に消える

ストアフロントで交渉可能な見積もりまたは見積もりテンプレートの名前を変更すると、Adobe Commerceに成功メッセージが一貫して表示されるようになりました。 以前は、バイヤーが交渉可能な見積もりの名前を変更すると、成功メッセージが断続的に表示されず（多くの場合、ほぼ即座にクリアされます）、名前変更操作自体が成功したにもかかわらず、このメッセージが失敗するのを待つ自動テストも発生していました。 AC-13447

_AC-13447_

#### ゲストチェックアウトの会社フィールドの検証が失敗する

ゲストチェックアウトで、会社フィールドが正しく検証されるようになりました。
以前は、company属性が必要な場合、ゲストチェックアウトは失敗し、フィールドに入力された場合でも「会社は必須の値です」というエラーが表示されていました。
AC-14987

_AC-14987 - [GitHub issue](https://github.com/magento/magento2/issues/40011) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/f1adb44e)_

#### 制限付き管理者は、共有カタログに会社を割り当てることができません

制限付き管理者ユーザーが会社を共有カタログに割り当てる際に例外が発生した問題を修正しました。この更新により、割り当てがエラーなく正しく機能するようになります。

_AC-15662_

#### カテゴリ権限が有効になっている場合に、グループ化された製品を購買リストに追加する際の例外

製品オプションを配列として安全に処理し、すべての製品タイプを例外なく追加できるようにすることで、カテゴリ権限が有効になっている購買リストにグループ化された製品を追加する際に発生するTypeErrorを修正しました。

_AC-15862_

#### Rest API products-render-infoは、ログインした顧客に誤った最終価格を返します

チケットにRest API製品の修正があります – render-info ログインした顧客に誤った最終価格を返します

_AC-5979 - [GitHub issue](https://github.com/magento/magento2/issues/35757)_

#### 「購買依頼リストに追加」ボタンは、カテゴリーページから追加しようとすると消えます

「購買依頼リストに追加」ボタンは、修正されたカテゴリーページから追加しようとすると消え、カテゴリーページに購買依頼ボタンが表示されます

_AC-8575_

#### 総計には税額は含まれません

注文には、クロスボーダー取引が有効になっている既存の発注からの発注の正しい合計が含まれます。

_ACP2E-3727_

#### REST APIを介してB2B共有カタログのカテゴリを割り当て解除すると、動作が遅くなる

これで、B2Bでカテゴリの割り当てを解除すると、パフォーマンスが大幅に向上しました。 以前は、B2B共有カタログでカテゴリの割り当てを解除するのに長い時間がかかっていました。

_ACP2E-3796_

### B2B、カート、チェックアウト

#### 管理者機能「顧客としてログイン」からB2B企業ユーザーにログインすると、StorefrontにcartId = X エラーを持つエンティティが表示されません

「お客様としてログイン」機能を使用する場合、管理者バックエンドから正常にログインした後、「cartId = Xを持つそのようなエンティティはありません」エラーが表示されなくなりました。

_ACP2E-3994 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/2a1e1e55)_

#### 請求先住所が見つからない場合は、「実店舗配送」の配送方法で注文を行うことができません

配達方法として「実店舗内ピックアップ」が選択されている場合、チェックアウト時に請求先住所が自動的に入力されない問題を解決しました。 請求先住所がなければ、チェックアウトを完了できませんでした。

_ACP2E-4030 - [GitHub コードの貢献度](https://github.com/magento/inventory/commit/42d23211)_

### カート/チェックアウト

#### Magento 2.4.7 アップデート（ミニ）買い物かごに小数点以下の数量は許可されていません

ロケールがNL （オランダ語）の場合、ミニカートの小数点で数量を更新する際に、Magentoが正しく処理するようになりました

_AC-13238 - [GitHub issue](https://github.com/magento/magento2/issues/39236) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/39669)_

#### [問題] チェックアウト契約書モデルにEventPrefixとEventObjectを追加

チェックアウト契約モデルにEventPrefixとEventObjectが含まれるようになり、イベントをイベントのプレフィックスでトリガーできるようになりました。 この機能強化により、チェックアウト契約書イベントを操作する際の開発者の柔軟性が向上します。 以前、チェックアウト契約モデルはEventPrefixとEventObjectをサポートしていなかったため、イベント処理をカスタマイズする機能が制限されていました。

_AC-13252 - [GitHub issue](https://github.com/magento/magento2/issues/32510) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/32451)_

#### [問題]開発者エクスペリエンス：Quote AbstractItem コードスタイル （SwiftOtterのSOP-348）

このプルリクエストは、抽象Item メソッドに対する誤解を招くメソッド宣言を修正します。

_AC-13334 - [GitHub issue](https://github.com/magento/magento2/issues/39340)_

#### グループ化された製品フロントエンドの数量検証がありません

システムは正常に動作しており、負の数量と最大数量を追加しようとすると検証エラーが表示されます

_AC-13524 - [GitHub issue](https://github.com/magento/magento2/issues/39479) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/39480)_

#### [問題] subtotal.phtmlの更新

Subtotal.phtmlが正しい間隔で更新されます

_AC-13907 - [GitHub issue](https://github.com/magento/magento2/issues/39619) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/39612)_

#### ゲストと一緒に注文できません

Adobe Commerceでは、管理者で必要に応じてミドルネーム フィールドが設定されている場合に、ゲストの買い物客が正常に注文できるようになりました。 以前、Adobe Commerce 2.4.8-beta1 （PHP 8.3/8.4）では、ミドルネームを必要に応じて設定し、ゲストとしてチェックアウトすると、ミドルネームが指定された場合でも注文が行われず、チェックアウトの完了がブロックされていました。 AC-14241

_AC-14241 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/27217d0e)_

#### [Graphql]は、null以外のフィールド「SelectedCustomizableOption.label」に対してnullを返すことができません

選択したオプションが存在しなくなった場合、システムはメッセージを含む内部サーバーエラーをスローしません

_AC-14256 - [GitHub issue](https://github.com/magento/magento2/issues/39729) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/39888)_

#### 1つのウィッシュリスト項目が無効な場合、GraphQL addWishlistItemsToCartで既存のカート項目の数量を更新できない（Magento 2.4.7-p3）

無効な設定可能な製品が検出されたときに、GraphQL addWishlistItemsToCartの突然変異が処理を停止する問題を修正しました。 修正後、有効なウィッシュリスト項目がカートに追加され、数量が更新され、無効な項目はスキップされて適切なエラーが返されます。

_AC-14464 - [GitHub issue](https://github.com/magento/magento2/issues/39820) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/3cf1a106)_

#### [2.4.8]市区町村名に0 ～ 9、アンパサンド、完全停止、かっこ付きの数字がある場合、注文を行うことはできません

「。」、「&amp;」、括弧などの特殊文字を含む市区町村名のチェックアウトが失敗する問題を修正しました。
現在、このような都市名を持つ注文は、検証エラーなしで正常に配置されます。

_AC-14495 - [GitHub issue](https://github.com/magento/magento2/issues/39854) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/b9f5d6f7)_

#### 見積もりアドレス 2.4.8にゲストプレフィックスが保存されない

チェックアウト時にゲスト顧客の接頭辞（Mr/Mrs）が保存されるようになりました。
以前は、ゲスト顧客が選択した挨拶は最終的な注文に達する前に失われ、他のすべての住所フィールドは正しく転送されていました。
AC-14705

_AC-14705 - [GitHub issue](https://github.com/magento/magento2/issues/39915) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/f1adb44e)_

#### 数量条件を含むセールスルール サブセレクトが適用に失敗しました

チェックアウト時に、製品のサブセレクション条件を含むカート価格ルールが適用されない問題を修正しました。
これで、設定されたルールに従って割引が正常に適用されます。

_AC-14884 - [GitHub issue](https://github.com/magento/magento2/issues/39965) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/fe72c407)_

#### [問題] クラス属性のスペースを削除します

クラス属性の余分なスペースが削除されるようになりました

_AC-14939 - [GitHub issue](https://github.com/magento/magento2/issues/39977) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/39970)_

#### Graphql - Backorderが有効になっている場合に結合カートが正しく機能しない

GraphQLを介した買い物かごの結合中に、ゲストカートのアイテムが顧客カートと結合されない問題を修正しました。
現在、顧客カートは、ゲストカートと顧客カートの両方から組み合わされた数量を正しく反映します。

_AC-15148 - [GitHub issue](https://github.com/magento/magento2/issues/40064) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/a3b1abc2)_

#### [統合] [ チェックアウト ]依存ディレクティブが、失敗した支払い電子メールテンプレートで更新されました

依存ディレクティブを正しく処理するように更新された支払い電子メールテンプレートが失敗しました。
「修正」を選択すると、配送先住所と配送方法が適切に表示されます。
以前は、これらのフィールドは失敗した支払いメールにありません。

_AC-15363 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/36d4d6fb)_

#### ログイン後に自分のアカウントページをリダイレクトするチェックアウトに進みます

セッションの有効期限が切れた後、チェックアウトログインではなくマイアカウントログインページにユーザーがリダイレクトされ、ログインフォームを使用してチェックアウトに正しく移動される問題を修正しました。

_AC-15962_

#### 固定製品税が有効になっている場合、[買い物かご] ショッピングカートページが読み込まれません

固定製品税（FPT）が有効になっている場合にショッピングカートページが無限ロードに入る問題を修正しました。 この問題は、商品価格と同じHTML要素に税金が含まれているため、小計の計算が正しくなかったことが原因で、中央小計と概算小計の間に不一致が生じたことです。 修正後、カートは正しく読み込まれ、正確な合計が表示されます。

_AC-16096 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/01cee3c3)_

#### 買い物かご価格ルール アクション「買い物かごの価格」条件、適用しない場合

「カート内の価格より低い」条件のカート価格ルールが、対象外の製品に誤って適用される問題を修正しました。
これにより、カートの商品価格が設定されたルール条件を満たさない場合、クーポンが適切に検証され、拒否されるようになりました。

_AC-6997 - [GitHub issue](https://github.com/magento/magento2/issues/36433) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/01cee3c3)_

#### [問題] base_priceではなく見積もり項目の価格を設定します

フロントエンドの1つのweb サイトに複数の通貨がある場合、見積もり項目の価格がbase_priceに設定された場合、その価格は正しく処理されます

_AC-9985 - [GitHub issue](https://github.com/magento/magento2/issues/38094) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/36878)_

#### 期限切れの永続的な見積もりは、cron ジョブ sales_clean_quotesによってクリーンアップされません

期限切れの永続的な引用符は、「persistent_clear_expired」 cron ジョブの実行時にクリアされるようになりました。 以前は、期限切れの永続的な引用符は、他のcron ジョブでクリアされていませんでした。

_ACP2E-3493 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/11be3dff)_

#### 非アクティブな会社のチェックアウト時に「エラーが発生しました」エラーが発生する

修正前は、ログインユーザー会社が有効になっていない場合、カートページでログアウトアクションが正しく完了していませんでした。 これで、会社が利用できなくなった場合、ログアウトが適切に実行されます。

_ACP2E-3541 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/df92debe)_

#### 「複数のアドレスでチェックアウト」すると、アドレス選択が保存されない

マルチシッピングオプションをキャンセルする際の修正前は、マルチシッピングに戻す際にアドレスが事前に選択されていませんでした。 これで、デフォルトのアドレスは、マルチシッピング画面で行われた選択のいずれかに置き換えられます。

_ACP2E-3646 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/6ea61121)_

#### 1つのストアビューで注文が作成された場合、最近の注文が他のストアビューに表示されない[Cloud]

「マイアカウント」ページに、同じストア内の他のストアビューからの最近の注文が表示されない問題を解決しました。 注文取得ロジックが更新され、「マイオーダー」ページの動作に合わせて、すべてのストアビューで一貫した注文の表示が可能になりました。

_ACP2E-3807 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/a20a6ff2)_

#### として表示する数量  バンドル製品を追加する際に、管理者用カスタマーショッピングカートセクションで0をクリックします  

顧客アクティビティの「ショッピングカート」セクションに、正しい数量が表示されるようになりました。 以前は、数量は0として表示されていました。

_ACP2E-3872 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/3ad96f6a)_

#### [Cloud]送料無料の割引は、買い物かごが要件を満たさなくなったときに正しく削除されません

小計（除く。 カート価格ルールの税）には、以前のルールの割引が組み込まれるようになりました。

_ACP2E-3973 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/6dd3fa99)_

#### マルチシッピングで同じ顧客の重複した注文が見つかりました

複数の配送先住所を持つ注文を同時にリクエストすると、同じ顧客に対して注文が重複することがなくなりました

_ACP2E-4117 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/a1c57b2e)_

#### [Cloud] Stock制限を超えた通知メッセージは、在庫切れのしきい値に達すると2回表示されます

カートの更新で重複したエラーバナーが表示される問題を修正しました。 以前は、AJAXの検証エラーの後、バックエンドでフォームの送信中に同じメッセージが再度追加されたため、買い物客には2つの同じアラートが表示されていました。 ここで、バックエンドの追加メッセージをスキップして、カートページを1つの明確なエラーバナーに保ちます。

_ACP2E-4192 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/e885088b)_

#### 請求情報の場合、サーバー側の検証は出荷情報REST APIを使用して機能しません

顧客アドレスデータ検証が改善され、チェックアウト用のRESTとGraphQl間の一貫性が向上しました。

_ACP2E-4223 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/0a8c9a9a)_

#### [Cloud] カート ページでのバンドル製品価格の問題

複数通貨ストアのカートページでのバンドル製品価格の問題を修正しました

_ACP2E-4245 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/cbca0396)_

#### 買い物かごのストア範囲の問題の管理

これで、デフォルト以外のweb サイトに割り当てられている顧客のショッピングカートを管理する際に、管理者ユーザーにショッピングカートエラーが表示されるようになりました。 以前は、エラーは表示されませんでした。

_ACP2E-4348 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/31258bf6)_

#### 一部の請求書のキャンセル後にクーポンの時間を設定_used リセット

注文が部分的にキャンセルされたときに、クーポンのtimes_used数が正しく更新されるようになりました。

_ACP2E-4365 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/61c96348)_

### カート&amp;チェックアウト、GraphQL

#### GraphQL経由で注文する際に、メッセージをエラーコードにマッピングする際にエラーが発生する

GraphQLが存在しないカートまたは非アクティブなカートの注文を呼び出すと、すべてのストアビューでCART_NOT_ACTIVEまたはCART_NOT_FOUND エラーコードが正しく返されるようになり、翻訳されたエラーメッセージが以前に未定義コードになった問題を修正しました。

_ACP2E-3942 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/7accebfa)_

#### [GraphQl] カート クエリ カート アイテムの割引に関する問題（仮想見積もり）

GraphQLの買い物かごクエリで、バーチャル見積もりに対して誤った割引額が返される問題を解決しました。 以前は、対象外の特定のバーチャル商品に誤って割引が適用されていました。

_ACP2E-4248 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/cbca0396)_

#### [Cloud] ACSD-68499_2.4.8-p2は別の問題を作成します

数量が不足している項目に対するgraphQL リクエストが行われた場合、エラーコードを含む適切なエラーメッセージが返され、リクエストされた数量が利用可能な場合は、カートの更新が成功しました。

_ACP2E-4404 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/1c547060)_

### カート&amp;チェックアウト、GraphQL、在庫/MSI

#### 売上可能な在庫が多い場合でも、CartItemInterfaceのis_available属性はfalseを返します

is_available属性は、販売可能な在庫が多い場合にtrueを返します。 以前は、常にfalseが返されていました。

_ACP2E-3885 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/3ad96f6a)_

### カートとチェックアウト、在庫/MSI

#### 414 「受け取り場所の検索」エンドポイントで大きなカートサイズのエラー

多くの商品がカートに入っている場合に、長いURLが原因で、「店舗で選択」を使用してチェックアウト中に店舗を選択する際に失敗しなくなりました。
以前は、ストアの選択中に生成されたURLが長すぎるため、414 エラーが発生し、顧客がチェックアウトを完了できなくなっていました。

_ACP2E-4266 - [GitHub コードの貢献度](https://github.com/magento/inventory/commit/ae1f272f)_

### カート&amp;チェックアウト、注文、製品

#### 注文請求書が失敗した場合でも、ギフトカードの電子メールが送信されます

この修正の実施前は、請求書の作成後にギフトカードの電子メールが送信されていました。 ただし、修正が適用された後、請求書が正常に保存され、コミットされた後、ギフトカードの電子メールが送信されるようになりました。

_ACP2E-3905_

### カート&amp;チェックアウト、プロモーション

#### ギフトカードの表示残高は、ウェブサイトの範囲によって制限されません

割り当てられたWeb サイト範囲でのギフトカードのバランスチェックが制限されました。

_ACP2E-4379_

### カート&amp;チェックアウト、SEO

#### セカンダリ web サイトから購入した際の電子メール内の誤ったギフトカードコード URL

以前は、デフォルト以外のストアのマルチストア設定とギフトカードでは、ギフトカードの要求が常にデフォルトのweb サイトにリダイレクトされていました。 この修正が適用された後、電子メールはギフトカードの請求リンクを正しい範囲またはweb サイトにリダイレクトします。

_ACP2E-3699_

### カート&amp;チェックアウト、セキュリティ

#### [CLOUD] Sri パッチを実装した後の最初の試行で、チェックアウトページにJS ファイルの404が表示される

修正前のMixinは、最小化とバンドルが有効になっている場合、カートとチェックアウトに読み込まれませんでした。 修正後、すべてのMixinが期待どおりに読み込まれます。

_ACP2E-4128 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/e457c5e2)_

### カートとチェックアウト、配送

#### [Mainline] カート価格ルールはマルチシッピングを尊重していません

この修正を実施する前は、サブセレクト条件が適用され、送料無料が有効になっている場合、複数配送商品のカート価格ルールが正しく適用されませんでした。 ただし、修正が適用されたため、複数配送カートのカート価格ルールが意図したとおりに機能するようになりました。

_ACP2E-3666 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/b12ffe36)_

### カタログ

#### 同じクエリを持つ同じページに対してキャッシュ fpcを複製

同じクエリパラメーターを持つページの順序や末尾の文字に関係なく、同じフルページキャッシュ（FPC）が正しく識別され、使用されるようになりました。 これにより、ページキャッシュフォルダーサイズが不必要に増加するのを防ぐことができます。 以前は、クエリパラメーターの順序が異なる場合や、末尾の文字がある場合は、同じページに対して異なるFPC識別子を作成し、ページキャッシュフォルダーサイズが増加していました。

_AC-10722 - [GitHub issue](https://github.com/magento/magento2/issues/38269) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/38270)_

#### catalog_product_entity_int テーブルに必要な列のインデックスがありません

catalog_product_entity_int テーブルに必要な列のインデックスが欠落していることに対応しました

_AC-10844 - [GitHub issue](https://github.com/magento/magento2/issues/38315) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/38316)_

#### カタログ URL リソース （_getCategories）のスコープのバグ

このPRは、ストア スコープでカテゴリ URL リソースに値が定義されていない場合、デフォルト スコープにフォールバックを追加します。

_AC-11011 - [GitHub issue](https://github.com/magento/magento2/issues/38393) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/38394)_

#### [問題] OpenGraphで価格を表示できるかどうかを確認する

価格を非表示にするプラグインを使用し、この変更価格がOG タグに表示されない場合、システムは正常に機能しています。

_AC-11635 - [GitHub issue](https://github.com/magento/magento2/issues/38512) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/38510)_

#### 表示価格に税を追加する際の価格の丸め問題

価格に税金を追加する際の価格に関する丸め問題が修正されました

_AC-11725 - [GitHub issue](https://github.com/magento/magento2/issues/18025) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/35730)_

#### [問題] カスタムカタログルール条件を許可

厳格なタイプのチェックにより、カスタムカタログルールの条件を使用できない問題を解決しました。 この修正により、クラスの等価チェックがinstanceofに置き換えられ、カスタム条件クラスが正しく機能し、ルールの検証とインデックス作成が正常に実行されるようになります。

_AC-13338 - [GitHub issue](https://github.com/magento/magento2/issues/39339) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/913bf1a6)_

#### ウィッシュリストに追加すると、設定可能な製品のオプションが失われる

製品をウィッシュリストに追加した後、設定可能な製品オプションが失われる問題を修正しました。 これにより、選択したオプションが保持され、ユーザーにオプションの再選択を促すことなく、商品をスムーズにカートに追加することができます。

_AC-13373 - [GitHub issue](https://github.com/magento/magento2/issues/39363) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/cc0ec250)_

#### コンフィグ可能な製品の子製品（シンプルな製品）の特別価格が正しく表示されない

「製品リストで使用」が「いいえ」に設定されている場合、製品リストページに設定可能な製品の子（シンプル）製品の特別価格が正しく表示されない問題を修正しました。 現在では、特別価格が通常価格と合わせて適切に表示され、商品タイプ全体で一貫した価格表示が可能です。

_AC-13594 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/3cf1a106)_

#### [ バグ ] REST API：特別価格を更新しても、すべてのストアビューの値が設定されない

REST APIは、web サイト内のすべてのストアビューの特別価格を更新するようになりました。
以前は、REST APIを介して特別価格を更新することは、指定されたストアビューにのみ影響し、web サイトのすべてのストアビューには影響しませんでした。
AC-13671

_AC-13671 - [GitHub issue](https://github.com/magento/magento2/issues/39521) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/7bdafaa2)_

#### 価格範囲とconfig.phpの問題

Magento 2.4.2では、config.phpを使用して価格範囲を変更しても、価格属性のcatalog_eav_attributeのis_global値が正しく更新されません。
その結果、商品価格はグローバルに維持され、価格範囲がweb サイトに設定されている場合でもweb サイトごとに保存できません。
この回避策では、データベースのis_global列を手動で更新する必要がありますが、これは実稼動環境には適していません。
この動作は、Magentoのデフォルトのデザインと一致しています。このデザインでは、価格範囲はグローバルまたはWeb サイトのいずれかですが、ストアビューごとに異なります。

_AC-13857 - [GitHub issue](https://github.com/magento/magento2/issues/33559)_

#### [\Magento\ConfigurableProduct\Model\Product\Type\Configurable] PHP エラーが見つかりません

ループ変数名を変更して、後続の呼び出しで使用する特定の製品の「_cache_instance_product_ids」データを正しく追加しました。

_AC-14159 - [GitHub issue](https://github.com/magento/magento2/issues/39641) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/39642)_

#### Elastic Searchは、商品のデフォルトの並べ替え順序を妨げます（新しい順から古い順への変更）

システムが並べ替えデータベース内の最新の製品（entity_idが最も高い製品）が最初に表示されます

_AC-14411 - [GitHub issue](https://github.com/magento/magento2/issues/31043) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/36900)_

#### ストア切り替え後のページは、2.4.8のキャッシュ（ストアスイッチャーが機能しない）から取得されます

キャッシュが手動でクリアされるまで、ストアフロントヘッダーからのストアビューの切り替えが機能しない問題を修正しました。
現在、キャッシュクリーンを必要とせずにストアビューの切り替えが正しく機能します。

_AC-14426 - [GitHub issue](https://github.com/magento/magento2/issues/39806)_

#### min-width: （@screen__l）の.less スタイルは無視されます。

カテゴリーページの1行に3つの製品のみが表示される問題を修正しました。
現在では、1行につき4つの商品が期待どおりに表示されています。

_AC-14463 - [GitHub issue](https://github.com/magento/magento2/issues/39817) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/b9f5d6f7)_

#### ホームページや他のページにはウィッシュリスト数が表示されない（お客様メニューのウィッシュリストページを除く）

ウィッシュリスト数がウィッシュリスト以外のページで空の括弧として表示される問題を修正しました。
これで、すべてのページの「My Wish List」の横に正しいウィッシュリスト項目数が表示されるようになりました。

_AC-14607 - [GitHub issue](https://github.com/magento/magento2/issues/39892) - [GitHub コード投稿](https://github.com/magento/magento2/commit/a3b1abc2) - [GitHub コード投稿](https://github.com/magento/magento2/commit/b3774fbe)_

#### catalog_product_save_before observerは、ストアレベルの値なしでREST APIを使用すると、日付関連のエラーをスローします（getFinalPrice （）の問題）

このPRは、日付がDateTimeInterface インスタンスとして提供される場合に適切な書式設定を確保するために、SpecialFromDateの処理を調整します。 これにより、特定のシナリオでgetFinalPrice （）の実行中に発生するエラーを防ぐことができます。

_AC-14847 - [GitHub issue](https://github.com/magento/magento2/issues/39959) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/40003)_

#### 緊急 – 追加する製品にカスタマイズ可能なオプションがある場合、バンドルに製品を追加できません

カスタマイズ可能なオプションを持つ製品をバンドル製品に追加できない問題を修正しました。
以前は、そのような製品は、バンドル作成の「製品をオプションに追加」リストから除外されていました。
現在では、カスタマイズ可能なオプションを備えた商品は、カスタムオプションを含めずにバンドルに追加できるようになり、適切な在庫管理が可能になっています。
これにより、商品の重複や在庫レベルへの影響を回避しながら、バンドルを作成できます。

_AC-14958 - [GitHub issue](https://github.com/magento/magento2/issues/39993)_

#### 負の`?p=` クエリ文字列が原因でElasticsearchが例外になる

システムは、カテゴリページ内の負の？p=値に対処するようになり、現在は例外となり、有効なリクエストと見なされます

_AC-15191 - [GitHub issue](https://github.com/magento/magento2/issues/40079) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/40080)_

#### 1つのオプションを持つコンフィグ可能な製品に対しては、「できるだけ低い」価格ラベルが表示されます

設定可能な製品で、PDP/PLPに「As low as」という誤ったラベルが付いた価格が表示される問題を修正しました。
現在、商品は誤解を招くようなラベルを付けることなく、正しい価格（500 ドル）を示しています。

_AC-15237 - [GitHub issue](https://github.com/magento/magento2/issues/40104) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/a3b1abc2)_

#### 「比較に追加」ボタンに間違ったメソッドが呼び出されました

\Magento\Catalog\Ui\DataProvider\Product\Listing\Collector\Url::collect （）で使用されるメソッドを修正しました。
以前は、getAddToCompareButton （）ではなく、getAddToCartButton （）が誤って呼び出されていました。
この変更により、製品リストの「比較に追加」ボタンをレンダリングする際の正しい動作が保証されます。
機能的な動作の変更は導入されません。アップデートにより、開発者エクスペリエンスとコードの正確性が向上します。

_AC-15323 - [GitHub issue](https://github.com/magento/magento2/issues/39754) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/a3b1abc2)_

#### 異なるストアビューで、異なる通貨のショッピングカートに誤った商品価格が表示される

ストアビュー間で異なる通貨を使用する場合に、ショッピングカートに誤った製品価格が表示される問題を修正しました。 修正後、カートには、設定された通貨に基づいて正しい変換済み価格が表示され、商品ページとカートの一貫性が確保されます。

_AC-15385 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/a8cf637b)_

#### FPTが有効になっている場合に、設定可能な製品の「低価格」表示が間違っている

FPTが有効になっている場合の設定可能な製品の「できるだけ低い」価格が、税金が2回適用されていることが原因であることを確認しました。この修正により、最終的な価格計算が税金構成を尊重し、正しい価格が表示されるようになりました。

_AC-15718 - [GitHub issue](https://github.com/magento/magento2/issues/40171) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/a06a4a57)_

#### Eav\Model\Entity\Collection\AbstractCollectionの_loadAttributesの時間の複雑さは、買い物かごや属性の商品数と共に増加します

このPRにより、Eav\Model\Entity\Collection\AbstractCollectionの_loadAttributesが最適化されました。ネストされたループを配列結合（+）に置き換え、_setItemAttributeValueへの呼び出しを減らすことで、大規模な製品カートのパフォーマンスが向上しました。

_AC-15833 - [GitHub issue](https://github.com/magento/magento2/issues/40216) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/40217)_

#### コレクションキャッシュと設定可能な製品ギャラリーの間のバグのあるインタラクション

media_gallery_imagesが常にコレクションとして扱われ、キャッシュデータの破損による致命的なエラーが発生するのを防ぐため、設定可能な製品ギャラリーのキャッシュの問題を解決しました。

_AC-16066 - [GitHub issue](https://github.com/magento/magento2/issues/33965) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/3b5ac075)_

#### 製品ページで属性を作成する際に、ドロップダウンオプションの削除が機能しない

説明はありません。

_AC-16437_

#### URLの書き換えにより、製品ページでエラーが発生する

URLの書き換えが発生したときに製品ページが正常に読み込まれるようになりました

_AC-2950 - [GitHub issue](https://github.com/magento/magento2/issues/35371) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/39670)_

#### カテゴリーに製品を追加する際の[Cloud]のバグ

ポップアップグリッドを使用して商品をカテゴリに追加する際に、ページネーションとレコード数のラベルが正しく機能するようになりました。 以前は、ページサイズと同じ項目を持つ1つのページのみを読み込むと、項目選択ドロップダウンに問題が発生していました。

_ACP2E-3526_

#### indexer_update_all_views cron error with MAGE_INDEXER_THREADS_COUNT

Customer Segment インデクサーを使用したMAGE_INDEXER_THREADS_COUNT > 2の問題を修正しました

_ACP2E-3538 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/9608ca21)_

#### ページビルダー製品ウィジェットの条件に「条件の組み合わせ」を追加する際の例外

この問題は、欠落または不完全な条件をスキップするチェックを追加することで修正されました。 以前は、システム内の不完全な条件の処理により、エラーログが生成されていました。

_ACP2E-3545 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/11be3dff)_

#### 属性セットの読み込み時にブラウザーがクラッシュする

4Kを超える製品属性がある場合、属性セット編集ページでブラウザーがクラッシュしなくなりました

_ACP2E-3633 - [GitHubの問題](https://github.com/magento/magento2/issues/38810) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/b12ffe36)_

#### [CLOUD]製品URLの書き換えが新しいストア用に作成されていません：Live Blockerに移行

新しいストアの製品URL書き換えが正常に作成されました。
以前の操作は、メモリリークまたはタイムアウトで終了しました。

_ACP2E-3669 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/df92debe)_

#### オプションが機能しない場合の属性のデフォルト値

以前は、product select属性のデフォルト値を変更すると、以前の値を持つ配列要素として表示されていました。 この修正が適用された後、製品属性値を更新すると、eav_attribute テーブルに単一の要素として保存されます。

_ACP2E-3688 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/520f9e30)_

#### 千の区切り記号が原因で編集時にギフトカードの検証が失敗する

ギフトカードの金額が1000以上の場合に、ギフトカードの商品タイプが保存される問題を修正しました。

_ACP2E-3704_

#### [Mainline] [CLOUD] イメージのサイズ変更は、400 GBを超えるディスク領域を消費します

修正後、`catalog:images:resize` フラグで使用される`--skip_hidden_images` コマンドは、画像が存在しないweb サイトの画像キャッシュを生成しません。

_ACP2E-3869 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/9ad7d277)_

#### ダイナミック画像生成大量の画像を生成する

修正後、製品が割り当てられているweb サイトに対してのみ画像が生成されます。

_ACP2E-3927 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/fab20b00)_

#### 指定されたCountryIDは存在しません – アイルランド （IE）

修正後、アイルランドの郵便番号を使用して受け取り場所を検索できます。

_ACP2E-3932 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/4ca73607) - [GitHub コードの貢献度](https://github.com/magento/inventory/commit/d2f1d6c6)_

#### レイアウト構造が正しくないため、フロントエンドで500 エラーが発生する

レイアウトに誤ったレイアウト構造がキャッシュされているため、ページが500 エラーコードを返す問題を修正しました

_ACP2E-4040 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/47721be6)_

#### 製品ビューのレポートが正しくありません。GAと比較して数が少なくなっています

report_viewed_product_index テーブルに製品ページビュー数が正しく表示されないバグを修正しました。

_ACP2E-4045 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/6e134409)_

#### 「スケジュール済み更新」の「カタログ価格ルール割引金額」フィールドの検証エラー

以前は、この問題を修正する前に、カタログ価格ルールのスケジュール更新で、割引金額がby_fixedの場合、validation-number-range ルールが原因で適切に検証されませんでした。 この修正が適用された後、固定価格カタログ価格ルールに対して検証が適切に機能します。

_ACP2E-4054 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/6dd3fa99)_

#### VAT API レート制限によりVAT検証が失敗する – トリガーが誤って正のカスタマーグループの変更を示す

Europa Vat検証ツールへのリクエストを最適化し、「レート制限」エラーが少ない

_ACP2E-4072 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/ee918f0d)_

#### 実稼動環境で最大の書き込みセット サイズ エラーをトリガーするコア インデクサーの一括削除

データ量に基づいて2つの削除戦略を実装することで、カタログルール製品インデックスのクリーンアップを最適化します。

_ACP2E-4085 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/0a3b7032)_

#### 無効にした後、製品が在庫切れとして表示される

修正後、無効な製品は製品ウィジェットに表示されません。

_ACP2E-4136 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/a1c57b2e)_

#### 重複したエントリを含む[Cloud] エラー（temp_category_descendants_%）

ネストされたカテゴリの数が多い環境の作成時にスケジュールされた更新でエントリが重複する問題を修正しました

_ACP2E-4159 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/a1c57b2e)_

#### [CLOUD]異なるストアの製品数の比較不一致の問題

別のストアビューに切り替えた後、製品リストが正しく機能するようになりました

_ACP2E-4249 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/98f028ab)_

#### 設定可能な製品作成時に、制限付き管理者ユーザーに表示される「新規属性を追加」ボタン

「新しい属性を追加」ボタンは、設定可能な製品作成時に一般管理者ユーザーにのみ表示されるようになりました。
以前は「新しい属性を追加」ボタンが制限付き管理者ユーザーに表示されていました

_ACP2E-4279_

#### 「画像とビデオ」で画像の役割の割り当てに「デフォルトを使用」するオプションがありません

「デフォルト値を使用」オプションが製品画像およびビデオセクションに追加され、デフォルトスコープからの設定の継承が可能になりました。

_ACP2E-4280 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/61c96348)_

#### 顧客グループの更新後もウィッシュリストに表示される制限付きカテゴリー製品

修正の前は、カテゴリの権限が顧客のウィッシュリスト項目に正しく適用されていませんでした。 修正が完了すると、ウィッシュリストのアイテムが適切に表示され、webとGraphQLの両方にページが割り当てられます。

_ACP2E-4294 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/c135fc3a)_

#### [Cloud] PDPおよびPLPでのバンドル製品価格の問題

通常価格のバンドル商品の価格は、デフォルト以外の通貨のPDP/PLPで正しく表示されます

_ACP2E-4298 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/0a3b7032)_

#### お客様は、お客様グループの変更後、アクセスできない製品を注文できます

以前は、管理者から顧客グループを変更する場合、フロントエンドカタログとカートにカタログ権限の変更が反映されませんでした。 ただし、この修正を適用すると、顧客グループが管理者から変更されたときに、更新されたカタログ権限に従ってフロントエンドの見積もりが変更されるようになりました。

_ACP2E-4300 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/f7bbcb4e)_

#### 高いメモリ使用量が原因でインデックス再作成が停止しました

カタログルールインデクサーが過剰なメモリを消費し、完了に失敗して、不安定およびメモリ不足エラーが発生する問題を修正しました。

_ACP2E-4303 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/c135fc3a)_

#### [CMS]の更新スケジュール済みプレビューリンクがメンテナンスページにリダイレクトされます

ホームページの定期アップデートプレビュー設定可能な製品を含むリンクでは、製品のリストが正しく表示されます。 以前は、ユーザーをメンテナンスページにリダイレクトしていました

_ACP2E-4401 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/1c547060)_

#### 関連製品は自動的に削除されます

ターゲットルールに一致する関連製品が、再インデックスプロセス全体で正しく関連付けられたままになりました

_ACP2E-4430_

### カタログ、GraphQL

#### GraphQlの無効な割引計算

カタログの価格に税金が含まれるように設定されている場合、GraphQLに割引率と基準価格が正しく表示されるようになりました。 以前は、20%ではなく19.99%を表示するなど、丸め付けのエラーが発生していました。

_ACP2E-3993 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/e457c5e2)_

#### GetCart GraphQL Media Gallery フィールドは、キャッシュフラッシュ後に空のデータを返します

修正後、製品のmedia_galleryは、カートリクエストのGraphQL応答で期待どおりに返されます。

_ACP2E-4185 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/45cbf9b6)_

### カタログ、GraphQL、検索

#### 製品graphqlがカテゴリ集計で無効なカテゴリを返しました

修正後、無効になったカテゴリは、製品GraphQl リクエストに対して返されません。

_ACP2E-2885 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/b12ffe36)_

### カタログ、パフォーマンス

#### 管理画面のカテゴリーの読み込みが非常に遅い

カテゴリの読み込みパフォーマンスが大幅に向上しました。 以前は、タイムアウトの問題の原因となったカテゴリの読み込みに時間がかかっていました。

_ACP2E-3891 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/4ca73607)_

### カタログ，価格設定

#### 子商品に適用されたカタログ価格ルールの割引が正しくありません

両方のルールが同じ優先度を持つ場合に、バリエーションのカタログ価格ルールが親の設定可能な製品によって上書きされる問題を修正します。

_ACP2E-3693 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/a20a6ff2)_

#### [Cloud] バンドル製品価格の問題

特別価格のバンドル商品の価格は、デフォルト以外の通貨のPDP/PLPで正しく表示されます

_ACP2E-4110 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/6e134409)_

### カタログ，製品

#### [ ランダムなバグ ] Fotorama ライブラリが読み込まれていません

これで、Fotorama ライブラリが適切に読み込まれ、添付されたすべての画像が画像ギャラリーに適切に表示されるようになりました。 以前は、Fotorama ライブラリが正しく読み込まれない問題が原因で、最初の画像のみが表示されていました。

_AC-12124 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/45b51c9c) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/27217d0e)_

#### 「製品を手動で追加」リンクは常に表示されます

既存の設定なしで設定可能な製品を作成する際に、「製品を手動で追加」リンクが表示されない問題を修正しました。 リンクが常に表示されるようになったため、管理者はダミー設定を作成することなく、簡単な製品を簡単に関連付けることができます。

_AC-13866 - [GitHub issue](https://github.com/magento/magento2/issues/39595) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/ef666cd9)_

#### バックエンドで製品を編集すると、製品オプションの価格から余分な小数点以下桁が削除されます

管理者が製品オプションの価格を小数点以下桁に切り捨てた場合の問題を修正しました。 現在では、小数点以下桁の精度が高い価格が保持され、保存後も正確な値が保持されます。

_AC-14050 - [GitHub issue](https://github.com/magento/magento2/issues/39655) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/3b5ac075)_

#### 関連商品ルールを介した関連商品が、GraphQLを介してPDPに表示されない

以前は、この修正が適用される前に、ルールに一致する製品に対して相対プロダクトルールが空/nullを返していました。 この修正を適用すると、製品の相対ルールが一致した製品に対して正常に返されます。

_ACP2E-3949_

### カタログ、返品

#### バンドル製品行の[Cloud]注文返品ページが自動的に選択解除される

以前は、管理パネルのグリッドビューでバンドル製品「一緒に出荷」リターンの場合、「アイテムを選択」オプションがあり、バンドル製品「一緒に出荷」オプションに混乱が生じていました。 この修正が適用された後、バンドル製品の出荷の場合、「項目を選択」オプションは表示されません。

_ACP2E-4180_

### カタログ、検索

#### RestApi リクエスト &#39;/rest/default/V1/categories?searchCriteria%5Bpage_size%5D=1&#39;がタイムアウトエラーで失敗します

カテゴリ REST API リクエストがタイムアウトエラーで失敗しなくなりました。
以前は、/rest/default/V1/categories?searchCriteria[page_size]=1へのリクエストは、特定のコード変更後にタイムアウトすると失敗する可能性がありました。
AC-13358

_AC-13358 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/7bdafaa2)_

### コンテンツ

#### graphql （magento 2.4.6-p4） – アクティブステータスではないcms ページを取得しようとするとエラーが発生する

無効なCMS ページに対するGraphQL クエリで内部サーバーエラーが返される問題を修正しました。
これで、クエリはエラーなしで適切な応答を取得します。

_AC-12302 - [GitHub issue](https://github.com/magento/magento2/issues/38877) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/1b1baf1d)_

#### ウィッシュリスト共有フォームでは、名前フィールドにランダムなコードを含めることができます

ウィッシュリスト共有フォームで、悪意のあるコードがメッセージフィールドに入力され、メールで送信される可能性がある、サーバー側テンプレート挿入（SSTI）のクリティカルな脆弱性を修正しました。 このアップデートにより、入力の検証が追加され、テンプレートのディレクティブや安全でないパターンがブロックされるようになりました。これにより、無効なコンテンツが検出されたときにエラーメッセージが表示されるようになりました。

_AC-12730 - [GitHub issue](https://github.com/magento/magento2/issues/39024) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/01cee3c3)_

#### テーマにcsp_whitelist.xmlを配置すると、機能せず、断続的な問題が発生します

Web サイト領域ごとにCSP ホワイトリストのキャッシュを実装しました。

_AC-13069 - [GitHub issue](https://github.com/magento/magento2/issues/38933) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/39672)_

#### magento 2.4.7 p2にアップグレードすると、新しくアップロードされたファイルのメディアギャラリーが表示されない

新しくアップロードしたファイルが、アップグレード後にメディアギャラリーに表示されるようになりました。
以前は、Magento 2.4.7 p2にアップグレードした後、新しくアップロードされた画像は、手動シンクが実行されるまでメディアギャラリーに表示されませんでした。
AC-13262

_AC-13262 - [GitHub issue](https://github.com/magento/magento2/issues/39275)_

#### メディアギャラリーに、同じ名前で大文字と小文字が異なるディレクトリの誤った画像が表示される

このシステムでは、メディアギャラリー内の特定のディレクトリにアップロードされたファイルが、同様の名前で大文字と小文字が異なるディレクトリでも表示される問題に対処できるようになりました。

_AC-13489 - [GitHub issue](https://github.com/magento/magento2/issues/39382) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/39502)_

#### beからギャラリー画像を完全に削除すると、スコープの役割/タイプが設定され（ベース/小/サムネール）、「古い」役割/タイプを再追加した後に表示されます

システムは、ストアスコープで期待どおりに動作しています。デフォルトのスコープに従って、新しく追加された画像の役割やタイプを画像が継承します

_AC-13556 - [GitHub issue](https://github.com/magento/magento2/issues/39481) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/39680)_

#### フィールド値に[が含まれている場合、管理者パネル ]の`listing component`小さなバグ `\` フィルターをヒットできません

スラッシュを含むページタイトルをフィルタリングしているとき、システムは正常に動作しています（例：Magento\Store）

_AC-13661 - [GitHub issue](https://github.com/magento/magento2/issues/39513) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/39535)_

#### Error: &quot;Magento_Catalog/js/validate-product&quot; for admin content pagebuilder with products loadのスクリプトエラー

このPRは、製品条件でページビルダーを編集する際のcatalogAddToCartのスクリプトエラーを修正します

_AC-13891 - [GitHub issue](https://github.com/magento/magento2/issues/39604) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/39677)_

#### 製品ウィジェットの設定時にcatalogAddToCart スクリプトエラーが発生する。

ページビルダーで「条件の組み合わせ」を使用して製品ウィジェットを設定する際に発生したスクリプトエラーを修正しました。 この問題は、フロントエンド JS ファイルが見つからないことが原因で発生し、コンソールエラーが発生しました。 修正後、ウィジェットはコンソールエラーなしで正しく読み込まれます。

_AC-13892 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/528af81a)_

#### 同じ識別子を持つウィジェット内の選択をブロック

同じ識別子ブロックがある場合に、ウィジェットを作成する際に、選択ブロックが正しく処理されるようになりました

_AC-14132 - [GitHub issue](https://github.com/magento/magento2/issues/39692) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/39722)_

#### &quot;0&quot; IDのCMS ページが存在しません&quot; ログフラッド

管理者ユーザーを作成した後、システムは期待どおりに動作し、新しいページを作成する場合system.logにエラーメッセージが表示されません

_AC-14254 - [GitHub issue](https://github.com/magento/magento2/issues/39743) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/39746)_

#### [GraphQl] ルートクエリの無限ループ

このチケットは、同じリクエストパスとターゲットパスを持つGraphQL ルートクエリが無限ループを引き起こし、最終的にタイムアウトする問題を修正しました。
2.4.9-alpha3では、クエリはループではなく正しいエラー応答を返すようになりました。

_AC-14269 - [GitHub issue](https://github.com/magento/magento2/issues/39707) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/68a45d0a)_

#### 存在しないサイトマップは製品画像で対応

「既存でないサイトマップにアクセスすると、応答：404 NOT FOUND」の製品画像が返されるようになりました

_AC-14295 - [GitHub issue](https://github.com/magento/magento2/issues/39756) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/40135)_

#### カタログリンクウィジェットで不正なURLが使用される

カタログ製品リンクとカタログカテゴリリンクを追加した後、システムがウィジェットを正しく処理し、html ソースにも正しいURLが表示されるようになりました

_AC-14437 - [GitHub issue](https://github.com/magento/magento2/issues/39464) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/39710)_

#### テーブルの接頭辞は考慮されません

管理者にデザイン/設定テーマグリッドを読み込む際に、Adobe Commerceがデータベーステーブルのプレフィックスを正しく尊重するようになりました。 以前は、Adobe Commerce 2.4.8でapp/etc/env.phpで設定されたテーブルプレフィックスを使用していたため、コンテンツ/デザイン/設定に移動すると、テーブルプレフィックスが考慮されず、テーマのグリッドがレンダリングされなかったため、エラーが発生していました。

_AC-14556 - [GitHub issue](https://github.com/magento/magento2/issues/39847) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/1bc2d6d0)_

#### 定数IMAGE_FILE_NAME_PATTERNをpublic visibleに変更して、柔軟性を高めます

GenerateRenditions.phpの定数IMAGE_FILE_NAME_PATTERNを公開し、開発者が画像レンディションを扱う際により柔軟に作業できるようにしました。 この修正プログラムは、Magento 2.4.9-alpha3に含まれており、フルユニットテストと統合テストをカバーしています。

_AC-15338 - [GitHub issue](https://github.com/magento/magento2/issues/39733) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/68a45d0a)_

#### 複数配送のレビュー注文ページに間違った配送方法が表示される

複数配送チェックアウトで、レビュー注文ページに誤った送料（10 INRではなく5 INR）が表示される問題を修正しました。更新により、各住所に正しい送料が表示されるようになりました。

_AC-15664 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/3cf1a106)_

#### bin/magento config:show （またはset） design/theme/theme_idが失敗する

構成が存在しているにもかかわらず、CLI コマンド bin/magento config:showおよびconfig:setがdesign/theme/theme_id パスに対して失敗する問題を修正しました。
これで、コマンドは正常に実行され、エラーなしでテーマ IDの表示と設定が可能になります。

_AC-5915 - [GitHub issue](https://github.com/magento/magento2/issues/35751) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/64823f95)_

#### 幅が比較的小さい画像をアップロードできません

システムは、幅が比較的小さい画像のサイズを高さに合わせて変更できなくなります。

_ACP2E-3558 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/9608ca21)_

#### ユーザーがウィジェット権限を持っていない場合、ページビルダーの製品コンポーネントは機能しません

修正が行われる前は、権限を持たずにウィジェットにアクセスする際に、ページが汎用エラーをスローし、「読み込み」GIFが表示されていました。 修正の後、モーダルウィンドウが「申し訳ありません、このコンテンツを表示するには権限が必要です」と表示されます。 メッセージ：

_ACP2E-3664 - [GitHub コードの貢献度](https://github.com/magento/magento2-page-builder/commit/bd9181b6)_

#### リモートストレージパスのスタイル設定の設定パスが正しくない

修正の後、リモートストレージパスのスタイル設定を設定すると、実際のAWS S3 パススタイル設定に影響します。

_ACP2E-3734 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/df92debe)_

#### GraphQLでページビルダー製品ウィジェットの順序が適用されない

GraphQLの「ルート」クエリ応答で、Page Builder Products コンテンツタイプ内の正しい並べ替え順序で商品が返されない問題を修正します。

_ACP2E-3898 - [GitHub コードの貢献度](https://github.com/magento/magento2-page-builder/commit/bd9181b6)_

#### ICU ライブラリバージョンによる英語以外のストアフロントの価格表示の問題

修正後、製品価格はヘブライ語（イスラエル）ロケールで正しく表示されます。

_ACP2E-3938 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/7accebfa)_

#### ストア コードのクリアされたデザイン設定の更新

設定キャッシュが正しく更新されないため、ストア表示コードを更新するとデザイン設定設定がクリアされる問題を修正しました。

_ACP2E-3941 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/462ede94)_

#### コンテンツのステージングのプレビューが検索結果で機能しない

ステージングプレビューで検索すると、選択した範囲に従って商品が返されるようになりました。 以前は、検索でデフォルトの範囲が返され、選択したストアは無視されていました。

_ACP2E-4095_

#### ページビルダー – 製品状態ロジックの問題（またはロジックが誤って少ない製品を示す動作）

グローバルスコープを持つ属性が「Match Any」条件で使用されている場合、ページビルダー製品ウィジェットが正しい結果を返すようになりました

_ACP2E-4096 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/e457c5e2)_

#### 製品カルーセルでページビルダーに誤った製品が追加される

修正の前は、子のいずれかがフィルター条件を満たした場合、設定可能な製品がPageBuilder製品カルーセルリストに自動的に含まれていました。 現在、修正後、子製品が自分で表示されていない場合にのみ、親製品が含まれます。

_ACP2E-4341 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/61c96348)_

#### 複数のカテゴリがカテゴリ条件にリストされている場合、製品リストウィジェットが誤った結果を返す

「カタログ製品リスト」ウィジェットで、「カテゴリが1つである」という条件にリストされた複数のカテゴリが表示される場合、正確な結果が表示されるようになりました。 以前は、リストの最初のカテゴリのみが処理されていました。

_ACP2E-4353 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/0a3b7032) - [GitHub コードの貢献度](https://github.com/magento/magento2-page-builder/commit/1c1b3419)_

#### [Cloud] Media Gallery フォルダーの作成には、新規メディアギャラリーでdelete_folder権限が必要です。create_folderのみを持つ役割はフォルダーを作成できません

以前は、この修正が実装される前は、content create folder権限のみを持つ管理者ユーザーがCMS media galleryにフォルダーを作成できませんでした。 ただし、修正後、メディアギャラリーのコンテンツ作成者は、フォルダーの作成権限のみでフォルダーを作成できるようになりました。

_ACP2E-4376 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/61c96348)_

#### [QUANS] CMS ページの複製

この修正の前は、カスタムレイアウトの更新を含むcms ページの複製に失敗していました。 カスタムレイアウトの更新を含むCMS ページを、エラーなしで複製できるようになりました。

_ACP2E-4449 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/f7bbcb4e)_

#### Web サイトレベルの権限を持つ管理者は、動的ブロックを編集できません

これで、web サイト範囲の権限を持つ管理者ユーザーは、アクセス可能なストアードビューでバナーのコンテンツを編集できるようになりました。

_ACP2E-4468_

### 顧客/顧客

#### 管理者がCMS Page Contentを介してCustomerCustomAttribute ブロックを追加するストアフロントの例外

CMS ページコンテンツを介してCustomerCustomAttribute ブロックを追加すると、ストアフロントの例外が発生し、ページの読み込みが妨げられる問題を修正しました。
ストアフロントが正常に表示され、コンテンツをレンダリングできない場合に有意義なメッセージを表示するようになり、重大なエラーを回避できるようになりました。

_AC-11004_

#### ユーザーがログインしてからログアウトしてからログインするたびに、オンライン管理グリッドに重複した行が表示されるようになりました

お客様がログアウトして再度ログインしたときに、お客様のオンライン管理グリッドに重複する行が表示される問題を修正しました。
グリッドは、重複したエントリを作成する代わりに、既存のレコードを最新のアクティビティで更新し、正確な顧客セッションの追跡を確実にします。

_AC-11511 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/528af81a)_

#### StorefrontのDOB属性の最小値と最大値の検証が機能しない

このバグは、Date of Birth （DOB）属性の最小日付検証と最大日付検証がストアフロントで機能しない問題を修正しました（管理画面では機能していましたが）。
2.4.9-alpha3で、DOBを持つ顧客を許可された範囲外に保存する際に、検証が正しくブロックされ、エラーメッセージが表示されるようになりました。

_AC-13535 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/68a45d0a)_

#### 顧客としてログインする権限が取り消されたときに、管理パネルの警告画面にAjax 401 エラーが表示される

このバグは、お客様としてログインを取り消した場合に、生のHTMLを含むAjax 401 エラーが警告ポップアップに表示される問題を修正しました。
修正が完了すると、生のHTMLではなく、通常の警告メッセージが正しく表示されるようになりました。
ソリューションはMagento 2.4.9-alpha3で提供されました

_AC-15336 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/68a45d0a)_

### フレームワーク

#### 無効化されたモジュールのコードをコンパイル中

このプルリクエストエスケープは、コードのコンパイル前にモジュールを無効にしました。

_AC-10933 - [GitHub issue](https://github.com/magento/magento2/issues/38241) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/39723)_

#### カスタム DB トリガーでコマンド setup:upgradeを実行するとエラーが発生する

カスタムデータベーストリガーは、セットアップ :upgrade中にエラーを引き起こさなくなりました。
以前は、カスタムデータベーストリガー（ストアテーブルのAFTER INSERTなど）でbin/magento setup:upgradeを実行すると、次のエラーが発生する可能性がありました。
「警告：357行目のvendor/magento/framework/Mview/View/Subscription.phpのnull型の値で配列オフセットにアクセスしようとしています」
AC-11487

_AC-11487 - [GitHub issue](https://github.com/magento/magento2/issues/38481)_

#### [問題] メソッドの署名をインターフェイスと一致させます

getAttributesのメソッド署名がインターフェイスと一致するようになり、メソッドを上書きする際のエラーを防ぐことができます。 以前は、getAttributes メソッドを上書きしようとすると、メソッド署名の不整合がエラーを引き起こしていました。

_AC-11578 - [GitHub issue](https://github.com/magento/magento2/issues/38501) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/31955)_

#### Web サイト/グループ/ストアエンティティのフォームは、拡張属性の複数の値のフォーム要素で拡張できません

このPRは、複数値のフォーム要素がweb サイト/グループ/ストアフォームにデータを送信することを可能にします。

_AC-11657 - [GitHub issue](https://github.com/magento/magento2/issues/24070) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/24094)_

#### [問題] UI コンポーネントのvalidate-emails ルールを修正

UI コンポーネントに入力された複数の電子メールアドレスが正しく検証されるようになりました。これにより、各電子メールが適切にトリミングおよび検証されるようになりました。 以前は、システムがメールアドレスのトリミングに誤った方法を使用していたため、検証エラーが発生する可能性がありました。

_AC-11719 - [GitHub issue](https://github.com/magento/magento2/issues/38528) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/33470)_

#### [問題] スコープリゾルバーの使用状況の削除

このPRは、現在のストアではなく、管理者URL設定をグローバルに解決します

_AC-11736 - [GitHub issue](https://github.com/magento/magento2/issues/38566) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/38554)_

#### [問題]冗長なメソッドの削除

コード品質：機能を追加せずに親メソッドのみを呼び出すAsynchronousOperationsおよびSales コンポーネントの冗長メソッドを削除し、コードの保守を改善しました。

_AC-11915 - [GitHub issue](https://github.com/magento/magento2/issues/29748) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/29147)_

#### Magento_Theme title.phtml テンプレートがPHP 8.2では無効です

このプルリクエストは、php 8.xでnullの見出しで作成されたCMS ページがtrim （）にnullを渡すとスローされる場合の問題を修正します。例外：非推奨の機能：trim （）：文字列タイプのパラメーター#1 （$string）にnullを渡す

_AC-12856 - [GitHub issue](https://github.com/magento/magento2/issues/39092) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/39398)_

#### フィールドアイテムの下にコメントが含まれるetc/adminhtml/system.xml ファイルでxsd検証が失敗する。

このPRは、コメントノードのphpstormのXML スキーマ定義を修正します

_AC-12945 - [GitHub issue](https://github.com/magento/magento2/issues/39148) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/39867)_

#### デフォルトのNginx設定によるセットアップルートを介したMagentoのバージョンの公開

現在、システムは正常に動作しており、サイトが実行中のMagentoの正確なバージョンを公開していません

_AC-13205 - [GitHub issue](https://github.com/magento/magento2/issues/39227) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/39228)_

#### [問題] オブジェクト引数を名前付きパラメーターとして展開する

このシステムでは、名前付きパラメーターを含む配列を解凍するPHP 8.1機能が利用され、array_values呼び出しの必要性がなくなり、全体的なパフォーマンスが向上する可能性があります。 以前は、システムはarray_valuesを呼び出してオブジェクト引数を展開する必要がありました。

_AC-13210 - [GitHub issue](https://github.com/magento/magento2/issues/39233) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/37411)_

#### [問題] リファクタリング見積もりアドレスがメソッドを検証しています

このPRには、doValidate メソッドの読みやすさの改善が含まれています。

_AC-13214 - [GitHub issue](https://github.com/magento/magento2/issues/38230) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/38219)_

#### Magento オプション —magento-init-params cliの実行時に使用したことがない場合は、

—magento-init-params オプションが、CLI コマンドの実行時に使用されるようになりました。
以前は、CLI コマンドに – magento-init-paramsを渡しても、MAGE_MODEなどのパラメーターには影響がありませんでした。
AC-13231

_AC-13231 - [GitHub issue](https://github.com/magento/magento2/issues/39248) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/132b9e68)_

#### getItemsByColumnValueの型宣言が正しくありません

システムは、getItemsByColumnValue関数の入力パラメーター$valueを配列ではなくプリミティブ型として正しく定義し、関数が期待されるコレクションを返すようにしました。 以前は、単一の値を持つ配列を入力パラメーターとして使用した場合、関数はnullを返し、IDEはそれをエラーとしてマークしていました。

_AC-13240 - [GitHub issue](https://github.com/magento/magento2/issues/33070) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/33120)_

#### ロックプロバイダーにファイルストレージを使用する場合、クリーンアップが発生することなく、増え続けるファイルのディレクトリが表示されます

このプルリクエストは、1日に1回実行される新しいcronjobを導入し、過去24時間以内に変更されていないロックファイルを検索するため、安全に削除できます。 これにより、ロックファイルディレクトリの内容が制御されます。
このcronjobは、ロックプロバイダーがファイルを使用するように設定されている場合にのみ実行され、他のファイルのいずれかが使用されている場合（データベース – デフォルト、zookeeper、またはキャッシュ）には実行されません

_AC-13367 - [GitHub issue](https://github.com/magento/magento2/issues/39369) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/39372)_

#### [問題] クリーンアップ：メソッド呼び出しから無効な戻り値を使用しないでください。

このPRはマイナークリーンアップを行います。 何も返さない（void）メソッドを呼び出して、その結果値を使用することもあります。 これは本当に必要ありません。

_AC-13664 - [GitHub issue](https://github.com/magento/magento2/issues/39524) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/39516)_

#### Magento 2.4.7のマルチストア実装のFPCに関連付けられたキャッシュキー

マルチストア設定のフルページキャッシュ（FPC）キャッシュキーにMAGE_RUN_CODEとMAGE_RUN_TYPEが含まれず、以前のバージョンと比較してキャッシュキーの動作に一貫性がない問題を修正しました。 キャッシュキーにストアコンテキストが正しく含まれるようになり、ストア間のキャッシュの適切な分離が保証されます。

_AC-13719 - [GitHub issue](https://github.com/magento/magento2/issues/39456) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/ae6f305b)_

#### [問題] [PHPDOC] Magento\Framework\Message\ManagerInterfaceの不正なphpdocを修正

このPRは、\Magento\Framework\Message\ManagerInterfaceに対する不正なphpdocを修正し、\Magento\Framework\Message\Manager内のすべての重複したphpdocを削除します（inheritdoc構文を使用）。

_AC-14312 - [GitHub issue](https://github.com/magento/magento2/issues/39593) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/39153)_

#### 大量のアップデートを行う顧客の場合、部分的なインデックス作成が機能しなくなります

部分的なインデックス作成は、多数の更新を行う顧客に対して機能するようになりました。
以前は、changelog テーブルのversion_id カラムの最大値に達すると、インデックスの更新が停止していました。
AC-14424

_AC-14424 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/7bdafaa2)_

#### Magento 2.4.8では、セマンティックバージョンに従わない開発パッケージを使用します

Magento 2.4.8では、PHP 8.4との互換性を確保するために、pdepend/pdependおよびphpmd/phpmd （3.x-dev）の開発版が必要です。
これらの開発バージョンは、SemVer準拠のパッケージを想定しているサードパーティ製ツールと競合し、一部のアップグレードを妨げます。
一時的な回避策として、composer.jsonの開発バージョン（例：「3.x-dev as 3.99.0」）にエイリアスを設定し、セマンティックバージョンを満たしながら互換性を確保する必要があります。
これにより、安定したリリースが利用可能になるまで、PHP 8.4がサポートされ、競合を回避できます。

_AC-14519 - [GitHub issue](https://github.com/magento/magento2/issues/39796)_

#### 配送ラベルをダウンロードした後、配送料と処理価格が一致しなかった配送金額が表示されます。

配送ラベルの金額が配送および処理価格と一致するようになりました。
以前は、配送ラベルをダウンロードした後、表示された金額が配送および処理価格と一致しませんでした。
AC-14560

_AC-14560_

#### MView メカニズムは、トリガーの実行時にエラーを無視します

MView メカニズムで、トリガーの実行時にエラーが正しく報告されるようになりました。
以前は、トリガーの実行中のエラーはサイレントに無視され、通知なしでインデックス更新が欠落する可能性がありました。
AC-14567

_AC-14567 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/ae6f305b)_

#### [問題] レイアウト XML結合の読み込み中に不要な例外が多数発生しないようにします

このPRは新しい関数を導入します（B/C compatの場合は、保護された_loadXmlStringを上書きせず、例外をスローしません）

_AC-14580 - [GitHub issue](https://github.com/magento/magento2/issues/39877) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/37570)_

#### [問題] モジュール Vault グラフ Qlでコンストラクターのプロパティ プロモーションを使用する

このPRは、コンストラクタープロパティをVaultGraphQl モジュールのプロパティプロモーションに置き換えます

_AC-14616 - [GitHub issue](https://github.com/magento/magento2/issues/39900) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/36996)_

#### [問題] モジュールフロントエンドレイアウトのコード冗長性を削除しました。

このPRでは、Magento_Msrp、Magento_LoginAsCustomerAssistance、Magento_NewsletterおよびMagento_Sitemap モジュールのフロントエンドレイアウトのテーマレイアウトに対するコードの冗長性が削除されます。

_AC-14625 - [GitHub issue](https://github.com/magento/magento2/issues/30673) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/30644)_

#### [問題] `CommandListInterface` APIの一部としてコンストラクターを含める、インラインドキュメントを拡張

このPR アップデートでは、Magento\Framework\Console\CommandListをAPIとしてマークし、コンストラクターをCommandListInterfaceに導入して拡張性を向上させます。 また、コンソールコマンドを拡張する開発者の明瞭性とメンテナンス性を向上させるために、インラインドキュメントを改善します。

_AC-14680 - [GitHub issue](https://github.com/magento/magento2/issues/31102) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/37901)_

#### [問題] Microsoft IISに関連するコードを削除

このPRは、Microsoft Windows OSがサポートされていないことを示すMagento システム要件ドキュメントに従って、Microsoft IISに関連するコードをクリーンアップします

_AC-14702 - [GitHub issue](https://github.com/magento/magento2/issues/39910) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/39894)_

#### Magnifier.js構文エラー

システム拡大機能は、以前と同じように動作し続ける必要があり、拡大鏡オプションはグローバルスコープで使用できません

_AC-14722 - [GitHub issue](https://github.com/magento/magento2/issues/36200) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/39321)_

#### `setup:db:status` CLI コマンドのBackport Verbose Mode

`setup:db:status` CLI コマンドで詳細モードがサポートされるようになりました。
以前は、アップグレードに必要なデータベースの変更を把握することが困難でした。 ここで、`bin/magento setup:db:status -v`を実行すると、スキーマとデータの違いに関する詳細な情報が得られます。
AC-14807

_AC-14807 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/7bdafaa2)_

#### tlsおよび2.4.8を使用したSMTP メール送信

TLSを使用したSMTP メール送信が正常に機能するようになりました。
以前は、TLSを使用してSMTP経由でメールを送信すると、「エラー:1408F10B:SSL ルーチン :ssl3_get_record:間違ったバージョン番号」というエラーが発生していました。
AC-14883

_AC-14883 - [GitHub issue](https://github.com/magento/magento2/issues/39947) - [GitHub コード投稿](https://github.com/magento/magento2/commit/3717e6cb) - [GitHub コード投稿](https://github.com/magento/magento2/commit/d3ea191d)_

#### [問題]静的コンテンツデプロイでの同時実行の問題を修正

このPRは、テーマが親とどのように定義されているかに応じて、複数の同時プロセスがスピンアップして同じテーマパッケージを処理するバグを修正します。

_AC-14944 - [GitHub issue](https://github.com/magento/magento2/issues/39990) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/39954)_

#### [問題] PHP バージョン &lt; 8.1の従来の互換性コードを削除

このプルリクエストは、PHP &lt;8.1で実行するように設計されたコードを削除します。
また、すべてのPHP バージョンで利用可能であるため、PHP_VERSION_IDの問い合わせ可用性のチェックを削除しました

_AC-14971 - [GitHub issue](https://github.com/magento/magento2/issues/39891) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/39882)_

#### ログイン時にFPCが機能しない

フルページキャッシュ（FPC）が、ログインした顧客に対して正しく動作するようになりました。
以前は、ログイン後にホームページがキャッシュから読み込まれず、x-magento-cache-debug ヘッダーにHITではなくMISSが表示されていました。
AC-14999

_AC-14999 - [GitHub issue](https://github.com/magento/magento2/issues/40007)_

#### 特定のphp クラスに汎用タイプを追加して、静的分析のサポートを改善します

システムは、汎用型の定義を使用して、メソッド呼び出しが返す正確なクラスとして解釈することで、これを大幅に改善できるようになりました

_AC-15013 - [GitHub issue](https://github.com/magento/magento2/issues/40017) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/40119)_

#### [問題]により、SchemaBuilderの処理エラーが改善されました

このPRは、db スキーマのエラーメッセージ処理を改善します。 これにより、手間をかけずに問題を特定できます。

_AC-15020 - [GitHub issue](https://github.com/magento/magento2/issues/39816) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/39799)_

#### Rest API: メンバー関数getVideoProvider （）をnullで呼び出します

子製品がYouTube ビデオのみを持ち、他の画像を持たない場合に、設定可能な製品子APIを呼び出すと500 Internal Server Errorが返される問題を修正しました。
このエラーは、ExternalVideoEntryConverterのnull参照によって発生しました。
現在、APIは、エラーをスローすることなく、外部ビデオデータを含むメディアギャラリーエントリを持つ子製品を正しく返します。
これにより、REST APIを介して子製品のすべてのメディアタイプを適切に取得できます。

_AC-15046 - [GitHub issue](https://github.com/magento/magento2/issues/40021)_

#### [W3C] Cookie スクリプトタグ宣言からテキスト/JavaScriptを削除

このPRにより、不要なtype=&quot;text/javascript&quot;属性がHTML5準拠のcookie スクリプトタグから削除されました。

_AC-15061 - [GitHub issue](https://github.com/magento/magento2/issues/39982) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/39983)_

#### [問題] PHPDoc コメントのタイプミスを修正

このPRはphpdocの中のタイプミスを修正します

_AC-15075 - [GitHub issue](https://github.com/magento/magento2/issues/40042) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/38809)_

#### [問題] フレーズ呼び出しのスプリント使用率の削除

このPRは、Magento コアのフレーズ関数呼び出しのsprintfの使用を削除します。

_AC-15183 - [GitHub issue](https://github.com/magento/magento2/issues/40050) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/40033)_

#### アクティブなアプリケーションロックを持つマルチスレッドインデクサーで、すべての無効なインデックスを再インデックスできません

この問題は、use_application_lockが有効になっている場合のマルチスレッドインデクサーのエラーを修正しました。
以前は、DB ロックは並列処理中に失われていたため、インデクサーは「作業中」状態のままになり、SQL エラーをスローしていました（テーブルが見つかりません）。
Magento 2.4.9-alpha3では、この修正により、アプリケーションロックを有効にしてインデクサーが正しくインデックス付けされるようになります。

_AC-15270 - [GitHub issue](https://github.com/magento/magento2/issues/40102) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/68a45d0a)_

#### Magento\Framework\Escaperの戻り値の型が不明または無効です

システムは、レベル 5でphpstanを使用して静的分析を実行する場合、エスケーパーメソッドの型を受け入れます

_AC-15272 - [GitHub issue](https://github.com/magento/magento2/issues/40012) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/40114)_

#### [問題] キュー固有の設定がデフォルトの最大メッセージ値を超えることを許可します

システムは、キュー固有の設定がデフォルトの最大メッセージ値を超えることを許可するようになりました

_AC-15284 - [GitHub issue](https://github.com/magento/magento2/issues/40121) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/40110)_

#### [問題] varnishを使用すると、同じクエリを持つ同じページのキャッシュ fpcが重複します

このPRは、クエリパラメーターの順序を正規化し、同一のリクエストに対して一貫したキャッシュキーを確保することで、Varnishを使用する際の重複するフルページキャッシュエントリを修正します。
異なるシーケンス内の同じパラメーターを持つURLのキャッシュヒット率とパフォーマンスを改善します。

_AC-15325 - [GitHub issue](https://github.com/magento/magento2/issues/39706) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/39704)_

#### コミュニティテーマには、Commerce エディションモジュールのリソースが含まれています

Commerceのみのスタイルリソースをコミュニティテーマから削除し、それぞれのモジュールディレクトリに移動しました。 これにより、未使用のCSSがCommunity Editionにバンドルされるのを防ぎ、不要なペイロードを減らし、デッドスタイルのルールを排除しながら、Commerce モジュールが有効になっている場合の適切なスタイル設定を確保します。

_AC-15347 - [GitHub issue](https://github.com/magento/magento2/issues/21446) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/9bcd880a)_

#### [問題] ストア コードをUrlに追加するには、グローバルにする必要があります

このPRでは、コアコードのグローバルスコープを使用して、「ストアのコードをURLに追加」設定を取得することを確認することで、問題を解決します

_AC-15365 - [GitHub issue](https://github.com/magento/magento2/issues/40069) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/40065)_

#### [問題]宣言されていないプラグインが無効になっていない場合にのみログに記録します

このPRは、実際に宣言されておらず、使用されていない（有効でインスタンスが欠落している）プラグインを修正してログに記録します。

_AC-15386 - [GitHub issue](https://github.com/magento/magento2/issues/40086) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/40081)_

#### [問題]小さなクリーンアップ、重複したキーを配列から削除

これで、システムは小さなクリーンアップを実行し、Arrayに関連するエラーが見つからず、値「Weight （および上記）」を持つ2つの重複したキーを持っています

_AC-15414 - [GitHub issue](https://github.com/magento/magento2/issues/39851) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/39844)_

#### Magento 2.4.8-p2、magento/framework バージョン 103.0.8-p2：存在しないメソッドを呼び出すEmailMessage クラス

EmailMessage クラスがメール本文の取得を正しく処理するようになりました。
以前、magento/framework バージョン 103.0.8-p2のMagento 2.4.8-p2では、Magento\Framework\Mail\EmailMessage クラスがSymfony メールメッセージオブジェクトに存在しないメソッド （getTextBody）を呼び出そうとしていました。 これにより、サードパーティのモジュールやカスタマイズがこの方法を利用してメール処理を行っていた場合にエラーが発生しました。
これで、EmailMessage クラスは未定義のメソッドを呼び出さなくなったので、これらのエラーを防ぐことができます。 AC-15446

_AC-15446 - [GitHub issue](https://github.com/magento/magento2/issues/40170) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/e9412b24)_

#### [Magento 2.3.x] Data/Schema Patches getAliases （）が`setup:upgrade`中にエラーを引き起こす

getAliases （）はセットアップ :upgrade中にエラーを引き起こし、このPRは同じことを修正します

_AC-15559 - [GitHub issue](https://github.com/magento/magento2/issues/31396) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/38239)_

#### 操作のための照合順序の不正な組み合わせ

説明はありません。

_AC-15614 - [GitHub issue](https://github.com/magento/magento2/issues/40138) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/44329e9d)_

#### [問題] [PHPDOC]不正なphpdocを修正Magento\Framework\DB\Adapter\AdapterInterface::quoteColumnAs （）

このPRは、\Magento\Framework\DB\Adapter\AdapterInterface::quoteColumnAs （）のPHPDocを更新して、文字列に加えて$alias パラメーターをnullにできることを正しく反映します。 これにより、PHPStanの問題がレベル 5以上で解決され、コード品質ツールの互換性が向上します。

_AC-15626 - [GitHub issue](https://github.com/magento/magento2/issues/39598) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/39581)_

#### urlrewrite モジュールの照合順序が正しくありません

説明はありません。

_AC-15647 - [GitHub issue](https://github.com/magento/magento2/issues/40189) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/44329e9d)_

#### 条件が`\Magento\Framework\Escaper::escapeScriptIdentifiers`で満たされることはありません

\Magento\Framework\Escaper::escapeScriptIdentifiersの到達不能な条件を修正しました。falseのチェックをnullに置き換え、preg_replaceの戻り値と整合させ、機能に影響を与えることなくコードの精度を向上させました。

_AC-15667 - [GitHub issue](https://github.com/magento/magento2/issues/40195) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/cc0ec250)_

#### Varnish 7.3 （最新バージョン） – サブカテゴリーのリンク / デフォルトカテゴリーのオプションがストアフロントのホームページに表示されない

Varnish 7.3を使用する際に、ストアフロントのホームページにサブカテゴリリンクが見つからないことが、Magentoのコードの欠陥ではなく、ESI リクエスト処理とサーバー設定が原因であることが確認されました。この問題は、コアコードの変更を必要とせずに、推奨されるVarnish設定の調整によって解決されます。

_AC-15674 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/3cf1a106) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/9a62604c)_

#### [問題] `cache_invalidate` ログに追加のデバッグデータを追加します

このPRにより、cache_invalidate ログが強化され、完全なキャッシュのパージ用にリクエストコンテキストとスタックトレースが含まれるようになり、デバッグと可視性が向上しました。
これにより、既存の機能を変更することなく、予期しないフルキャッシュの無効化のソースを特定することができます。

_AC-15719 - [GitHub issue](https://github.com/magento/magento2/issues/40204) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/40196)_

#### [問題] コンポーザーのオートローダーの除外リストを少し改善しました。

このPRにより、コンポーザーのオートローダーの除外が調整され、テストクラスがスキップされ、不要なクラスマップエントリが減り、PSR-4警告が発生しないようにします。

_AC-15743 - [GitHub issue](https://github.com/magento/magento2/issues/40109) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/40107)_

#### [問題] `db_schema.xml`を使用した`comment=""`の宣言がダウンタイムなしのデプロイメントを壊さないようにします

システムは、comment=&quot;&quot;を含むdb_schema.xml宣言がダウンタイムなしのデプロイメントを壊さないようにしました

_AC-15980 - [GitHub issue](https://github.com/magento/magento2/issues/40254) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/40242)_

#### `\Magento\Framework\Filesystem\Glob::glob(...)` キャッシュをクリアできません

このPR アップデートでは、\Magento\Framework\Filesystem\Globで使用される内部静的キャッシュをクリアする方法が導入され、ファイル構造が変更されたときに新鮮で正確な結果を保証します。 特に、テストのシナリオや長期的なプロセスにおいて、最新の結果を得る必要がある場合は、信頼性と開発者のエクスペリエンスを向上できます。

_AC-15989 - [GitHub issue](https://github.com/magento/magento2/issues/35741) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/35742)_

#### ReadME Leaders link urlに永続的なリダイレクトがあります

永続的にリダイレクトされたURLと期限切れのURLを正しい作業リンクに置き換え、コントリビューターとメンテナのページが適切に開くように、README リーダーリンクを更新しました。

_AC-16046 - [GitHub issue](https://github.com/magento/magento2/issues/40292) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/913bf1a6)_

#### [問題] [PHPDOC]不正なphpdocを修正Magento\Eav\Model\ResourceModel\Entity\Attribute\Collection

属性コレクションのjoinLeft （）のPHPDoc注釈を修正して、適切な配列定義を許可し、コードの正確性とPHPStanなどのツールとの互換性を向上しました。

_AC-16187 - [GitHub issue](https://github.com/magento/magento2/issues/40354) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/39155)_

#### 1回のコマンドエラーで、後続のCLI コマンドの実行を停止せずにエラー（ファイルまたはstderr）が記録されていることを確認します。

システムは、1回のコマンド失敗で、後続のCLI コマンドの実行を停止せずにエラー（ファイルまたはstderr）が記録されることを確認するようになりました

_AC-16244 - [GitHub issue](https://github.com/magento/magento2/issues/40006) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/40063)_

#### [問題] PageCache カーネルの$maxAgeにint タイプを追加

このPRにより、PageCache カーネルの$maxAge パラメーターが整数として厳密に型指定され、タイプの安全性が向上し、キャッシュ処理におけるPHPStan/static分析エラーを防ぐことができます。

_AC-16313 - [GitHub issue](https://github.com/magento/magento2/issues/40438) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/36600)_

#### 偽のモジュールには拡張リポジトリのdev/ディレクトリが必要

説明はありません。

_AC-16487_

#### カートに追加イベント：空の価格

カートへの追加プロセス中に、checkout_cart_product_add_after イベントオブザーバーで製品価格がnullとして返される問題を修正しました。
現在では、基準価格と関連する価格値が正しく取得され、観察者やカスタム実装が正確なデータを利用できるようになります。

_AC-5966 - [GitHub issue](https://github.com/magento/magento2/issues/35638) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/3b5ac075)_

#### PHP8.1型のバグ修正

関連付けられた製品は、厳密な処理モードがアクティブでない場合や製品情報が利用可能な場合に、falseではなく空の配列に初期化されるようになりました。 この変更により、関連する製品の後続のロジック処理が一貫して動作するようになり、製品準備プロセスの安定性と予測可能性が向上します。

_AC-6017 - [GitHub issue](https://github.com/magento/magento2/issues/35808) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/35842)_

#### &#39;Magento\Customer\Api\Data\GroupInterface&#39;型が必要です。 「Magento\Customer\Model\Group」が見つかりました。

GroupFactoryを使用してGroupRepositoryInterfaceを介して顧客グループを保存すると、タイプエラーが発生する問題を修正しました。
以前は、リポジトリはGroupInterfaceを想定していましたが、グループモデルインスタンスが渡され、致命的なエラーが発生しました。
これで、適切なインターフェイス実装を行うことで、リポジトリを通じて顧客グループを正常に保存できるようになりました。
これにより、顧客グループをプログラムで作成または更新する際のIDE警告とランタイムエラーが解決されます。

_AC-6909 - [GitHub issue](https://github.com/magento/magento2/issues/36269)_

#### creditmemosでのフィールド検証

必須のカスタムフィールドが入力された後でも、クレジットメモ ページのフィールド検証で送信が妨げられる問題を修正しました。
これで、検証が正しく機能し、すべての必須フィールドが完了すると、送信ボタンが有効になります。

_AC-8308 - [GitHub issue](https://github.com/magento/magento2/issues/37182) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/64823f95)_

#### [問題] フレームワークから禁止されている`@author` タグを削除（パート 3）

特定のモジュールから禁止されている`@author` タグを削除することで、コーディング標準に準拠するようになり、全体的なコード品質が向上しました。 以前は、一部のモジュールにこのタグが存在することは、確立されたコーディング標準に違反していました。

_AC-8343 - [GitHub issue](https://github.com/magento/magento2/issues/37270) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/37020)_

#### [問題] モジュール send friend graph qlでコンストラクタープロパティのプロモーションを使用する

現在は、「send friend」GraphQLモジュールにコンストラクタプロパティのプロモーションを利用し、コードの読みやすさを向上させ、複雑さを軽減しています。 以前は、モジュールは多数の行を占めるプロパティを使用していたため、コードがより複雑になり、読みにくくなっていました。

_AC-8346 - [GitHub issue](https://github.com/magento/magento2/issues/37235) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/37197)_

#### [問題]禁止されている`@author` タグを削除

このPRは`@author` タグをコードベースから削除します

_AC-8349 - [GitHub issue](https://github.com/magento/magento2/issues/37266) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/37016)_

#### [問題]禁止されている`@author` タグを削除

このPRは`@author` タグをコードベースから削除します

_AC-8350 - [GitHub issue](https://github.com/magento/magento2/issues/37265) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/37015)_

#### [問題]禁止されている`@author` タグを`Magento_Downloadable`から削除

特定のモジュールから禁止されている`@author` タグを削除することで、コーディング標準に準拠するようになり、全体的なコード品質が向上しました。 以前は、一部のモジュールにこのタグが存在することは、確立されたコーディング標準に違反していました。

_AC-8355 - [GitHub issue](https://github.com/magento/magento2/issues/37251) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/37001)_

#### [問題]禁止されている`@author` タグを削除

特定のモジュールから禁止されている`@author` タグを削除することで、コードの品質と一貫性が向上し、コーディング標準に準拠するようになりました。 以前は、一部のモジュールにこのタグが存在することは、確立されたコーディング標準に違反していました。

_AC-8358 - [GitHub issue](https://github.com/magento/magento2/issues/37264) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/37014)_

#### [問題]禁止されている`@author` タグを削除

このPRは`@author` タグをコードベースから削除します

_AC-8359 - [GitHub issue](https://github.com/magento/magento2/issues/37262) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/37012)_

#### [問題]禁止されている`@author` タグを削除

特定のモジュールから禁止されている`@author` タグを削除することで、コーディング標準に準拠するようになり、全体的なコード品質が向上しました。 以前は、一部のモジュールにこのタグが存在することは、確立されたコーディング標準に違反していました。

_AC-8360 - [GitHub issue](https://github.com/magento/magento2/issues/37261) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/37011)_

#### [問題]禁止されている`@author` タグを削除

特定のモジュールから禁止されている`@author` タグを削除することで、よりクリーンで標準化されたコードを確保し、コーディング標準に準拠するようになりました。 以前は、一部のモジュールにこのタグが存在することは、確立されたコーディング標準に違反していました。

_AC-8361 - [GitHub issue](https://github.com/magento/magento2/issues/37260) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/37010)_

#### [問題]禁止されている`@author` タグを削除

このPRは`@author` タグをコードベースから削除します

_AC-8362 - [GitHub issue](https://github.com/magento/magento2/issues/37259) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/37009)_

#### [問題]禁止されている`@author` タグを削除

特定のモジュールから禁止されている`@author` タグを削除することで、コーディング標準に準拠するようになり、全体的なコード品質が向上しました。 以前は、一部のモジュールにこのタグが存在することは、確立されたコーディング標準に違反していました。

_AC-8363 - [GitHub issue](https://github.com/magento/magento2/issues/37258) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/37008)_

#### [問題] `@author`および`Magento_Backup`から禁止されている`Magento_Bundle` タグを削除

このPRは`@author` タグをコードベースから削除します

_AC-8367 - [GitHub issue](https://github.com/magento/magento2/issues/37244) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/36979)_

#### [問題]禁止されている`@author` タグを削除

特定のモジュールから禁止されている`@author` タグを削除することで、コーディング標準に準拠するようになり、全体的なコード品質が向上しました。 以前は、一部のモジュールにこのタグが存在することは、確立されたコーディング標準に違反していました。

_AC-8375 - [GitHub issue](https://github.com/magento/magento2/issues/37257) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/37007)_

#### [問題]禁止されている`@author` タグを削除

特定のモジュールから禁止されている`@author` タグを削除することで、コーディング標準に準拠するようになり、全体的なコード品質が向上しました。 以前は、一部のモジュールにこのタグが存在することは、確立されたコーディング標準に違反していました。

_AC-8376 - [GitHub issue](https://github.com/magento/magento2/issues/37256) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/37006)_

#### [問題]禁止されている`@author` タグを削除

特定のモジュールから禁止されている`@author` タグを削除することで、コーディング標準に準拠するようになり、全体的なコード品質が向上しました。 以前は、一部のモジュールにこのタグが存在することは、確立されたコーディング標準に違反していました。

_AC-8400 - [GitHub issue](https://github.com/magento/magento2/issues/37254) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/37004)_

#### [問題]禁止されている`@author` タグを削除

特定のモジュールから禁止されている`@author` タグを削除することで、コーディング標準に準拠するようになり、全体的なコード品質が向上しました。 以前は、一部のモジュールにこのタグが存在することは、確立されたコーディング標準に違反していました。

_AC-8401 - [GitHub issue](https://github.com/magento/magento2/issues/37255) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/37005)_

#### [問題] サービス URL生成の拡張性の向上

このシステムでは、プラグインを介してサービス URL生成機能をカスタマイズできるようになり、より保守しやすい修正アプローチを促進しています。 以前は、この機能のカスタマイズは環境設定を通じて行われていましたが、これは効率的でも維持可能でもありませんでした。

_AC-8813 - [GitHub issue](https://github.com/magento/magento2/issues/37404) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/37403)_

#### [問題] カタログ検索での変数名の修正

検索エンジンモジュール内の変数が正しく命名されるようになり、コードの明確性とメンテナンス性が向上しました。 以前は、検索エンジンモジュールに無関係な変数名$defaultCountryが使用されていたため、混乱が生じていました。

_AC-9215 - [GitHub issue](https://github.com/magento/magento2/issues/37810) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/33533)_

#### allow_parallel_generationは環境変数で設定する必要があります

修正の後、「MAGENTO_DC_CACHE__ALLOW_PARALLEL_GENERATION」環境変数を使用して、「allow_parallel_generation」設定を設定できます。

_ACP2E-3673 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/b12ffe36)_

#### [Cloud] db_schema.xml ファイルを使用してテーブル列の型をIntからDecimalに変更すると、Magento 2でエラーが発生する

列データタイプの変更が正しく機能しません。 以前は、エラーがスローされました。属性「identity」は許可されていません。

_ACP2E-3709 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/df92debe)_

#### Adobeでの新しい通貨（XCG）のサポート

カリビアンギルダー（XCG）が通貨リストに追加されます。

_ACP2E-3790 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/520f9e30)_

#### 新しい検証の追加によるアップグレード 2.4.7-p5の問題

スキーマの作成中または更新中に、未定義の配列キー「列」がクラッシュするSchemaBuilder クラスの問題を修正しました。 これは、「列」キーを含まないテーブルデータを処理する際に発生しました。

_ACP2E-3871 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/9ad7d277)_

#### [QUANS]無効なS3 アクセスキーが原因の可能性があるサーバーの問題

AWS S3の資格情報が正しくないと、ストアフロントでページが無限に読み込まれなくなりました。

_ACP2E-3890 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/2a1e1e55)_

#### [QUANS] [Cloud] Minify jsが機能しない

JS縮小が有効になっている場合、次のJS ファイルが完全かつ正しく縮小されるようになりました。mage/backend/tabs.min.j、jquery/jquery.validate.min.js、Magento_PageBuilder/js/form/element/validator-rules-mixin.min.js。 結果として、ページビルダーCSS クラスのフィールド検証は期待どおりに機能します。

_ACP2E-3925 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/47721be6)_

#### PHP8.4非推奨エラー：Adobe Commerce 2.4.8へのアップグレード後のE_USER_ERROR

*リリースノートは必要ありません*
お客様向けのシナリオは、この修正の影響を受けません。

_ACP2E-3963 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/7accebfa)_

#### Cron ジョブがデータベース テーブルをクリアしません – Galera クラッシュによる停止の原因

Changelog テーブルのクリーンアップは、大量の削除操作を避けるために一括実行されるようになりました。

_ACP2E-3995 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/52f46328)_

#### 縮小されていないJSは、「jsの縮小を有効にする」を無視して読み込まれることがあります

修正前は、縮小を有効にしていても、一部のJS ファイルが「min」プレフィックスなしでリクエストされ、404 ステータスコードが生成されていました。 修正後、縮小が有効になっている場合、縮小されていないJS リソースは要求されません。

_ACP2E-4058 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/6dd3fa99)_

#### カスタム属性グループの日付属性が管理者にDatepickerを表示できない

カスタム属性グループに割り当てたときに、日付属性のカレンダーポップアップが画面に表示されない問題を修正しました。

_ACP2E-4060 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/6dd3fa99)_

#### 実稼動ACL権限チェックによるパフォーマンスの低下 – populateAcl メソッドがボトルネックになる

最適化されたACL ルール処理

_ACP2E-4114 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/98f028ab)_

#### AC-15867 + ACP2E-4296およびSCD コンパクトの最新バージョンでチェックアウトが読み込まれない

修正の前は、head セクションを通じてカスタム JavaScriptを読み込むと、問題が発生する可能性がありました。 新しい設定の導入後、このようなスクリプトは自動的に延期され、Magento 2 フレームワークとの互換性が高まります。

_ACP2E-4319 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/1c547060)_

#### 非推奨化警告：既存のロケールを変更するには、moment.updateLocale （localeName, config）を使用します。 moment.defineLocale （localeName, config）

修正前は、非推奨の警告がブラウザーコンソールにスローされていました。 修正の後、このような警告は表示されなくなりました。

_ACP2E-4338 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/2687b487)_

#### REST APIを介して製品の変更を保存する際に[CLOUD] DateTimeZone エラーが発生しました

修正の前に、コード「default」を持つストアがない場合、製品アップデート REST API リクエストでエラーが生成されます。 修正の後、「デフォルト」ストアが存在するかどうかに関係なく、製品の更新リクエストが正常に実行されるようになりました。

_ACP2E-4339_

#### MariaDB 10.11との非互換性

以前は、MariaDB 10.11を使用している場合、最新のMagento 2 バージョンのインストールに失敗し、セットアッププロセスが完了しませんでした。 この問題は、インストール時にMariaDB 10.11.xをサポートするようにデータベースの互換性処理を更新することで解決されました。

_ACP2E-4367 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/31258bf6)_

### フレームワーク、検索

#### Opensearch 2.19.1 illegal_argument_exceptionを単価カテゴリで使用

Opensearchは、同じ価格のすべての製品を含むカテゴリに対してillegal_argument_exceptionをスローしなくなりました。 以前は、この例外「[from] パラメーターを負にすることはできません」が指定されていました。

_ACP2E-3896 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/3ad96f6a)_

### GraphQL

#### GraphQLでの注文は、無効な配送方法で成功します

無効または無効な配送方法を使用して、GraphQL経由で注文を行う可能性がある問題を修正しました。
これで、選択した配送方法が検証され、利用できない場合はエラーが返され、注文の作成が妨げられます。

_AC-10472 - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/38268) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/a8cf637b)_

#### GraphQl クエリの実行中にスローされる例外

GraphQL クエリで無効な並べ替えパラメーターが原因で例外がスローされる問題を修正しました。修正後、エラーや例外ログを生成することなく、クエリが正常に実行されます。

_AC-14835 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/a8cf637b)_

#### Custom_attributesV2を含むAddProductsToCartの変更を介してギフトカード製品をカートに追加する際の内部サーバーエラー

custom_attributesV2を使用してGraphQLを介してカートにギフトカード（および同様のカスタムオプション）商品を追加する際にトリガーされる内部サーバーエラーを解決しました。この修正により、複雑な属性値が適切に処理され、商品をエラーなく追加できるようになりました。

_AC-15856 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/7fa400a7)_

#### `Country` クエリのNull フィールド

仮想アイテム、返金、および発送済みアイテムを含む注文が、発送済み数量の計算に仮想アイテムが含まれていることを確認し、注文状態を正しく完了に移行できる処理中に残る問題を修正しました。

_AC-7731 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/ef666cd9)_

#### 「number」属性を持つGraphQL クエリ「customerOrders」が内部サーバーエラーの原因になる

GraphQL customerOrders クエリで、数値フィールドのリクエスト時に内部サーバーエラーが返される問題を修正しました。
これで、リゾルバーは注文増分IDを正しく返し、クエリを正常に実行して注文番号を取得できるようにします。

_AC-8949 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/3b5ac075)_

#### 注文プレースメントのGraphQL応答に例外メッセージが含まれていない

別の形式でエラーを返していた以前の変更を元に戻しました。 現在では、GraphQL スキーマを壊すことなく、一貫した方法で潜在的なエラーが返されます。 これは既知のBICとして追加され、PMによって次のように承認されます：https://jira.corp.adobe.com/browse/ACP2E-3399?focusedId=45248897&page=com.atlassian.jira.plugin.system.issuetabpanels:comment-tabpanel#comment-45248897

_ACP2E-3399 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/9608ca21)_

#### 注文プレースメントのGraphQL Responseは部分的にローカライズされています

placeOrder GraphQlの変異によって返されたエラーは、完全にローカライズされませんでした。 多言語コンテキストでは、エラーが適切に翻訳されます。

_ACP2E-3506 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/9608ca21)_

#### GraphQL APIを並べ替える同時呼び出し – 同じ商品が異なる行に追加される

Reorder GraphQL APIへの同時呼び出しで、同じプロダクトが異なる行として追加され、データの不整合が生じる問題を修正します。

_ACP2E-3774 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/c8ba4ab1)_

#### updateCustomerEmail GraphQL mutation （Change email Address）がメール通知をトリガーしません

以前は、アカウントのメールアドレスを正常に更新した後、メールは顧客に送信されませんでした。 修正が適用された後、お客様はメールアドレスの更新に成功した後、メール通知を受け取れるようになりました。

_ACP2E-3785 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/c8ba4ab1)_

#### updateGiftRegistryの変更によるギフトレジストリでの動的属性の更新がない

以前は、updateGiftRegistryの変更によるこの修正の前に、GraphQLの変更によるギフトレジストリのカスタム属性の変更や更新は行われていませんでした。 この修正を適用した後、updateGiftRegistryの変更を通じて、ギフトレジストリの動的属性を正常に更新できます。

_ACP2E-3805_

#### 製品が削除されたときにcustomerOrders graphqlからエラーが返される

customerOrders graphql リクエストでは、注文の製品が削除されても、エラーがスローされなくなりました。 以前は、「内部サーバーエラー」エラーがスローされていました。

_ACP2E-3936_

#### Customer Order GraphQL：関連する商品の商品カテゴリを取得する「個別に表示されない」

修正前は、注文に非表示の製品が含まれている場合、そのカテゴリにはCustomer Order GraphQl応答に空の配列が表示されていました。
修正が完了すると、製品が非表示の場合でも、Customer Order GraphQl リクエストの応答に製品カテゴリが含まれるようになりました。

_ACP2E-3945 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/2a1e1e55)_

#### GraphQL リクエストで1つのweb サイト内のストアビュー間でウィッシュリスト項目が共有されない

修正前は、ウィッシュリスト項目はストア IDでフィルタリングされていました。 修正の後、ウィッシュリストのアイテムはweb サイトでフィルタリングされるようになりました。

_ACP2E-3987 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/2a252ae6)_

#### 実稼動環境で[Cloud] getRemoteAddressが127.0.0.1を返す

以前は、アプリケーションサーバーの使用時にリモートアドレスが正しく判断されていませんでした。 修正が完了すると、リモートアドレスが適切に決定され、nginxおよびヘッダー設定の適切なヘッダー設定と組み合わされます。

_ACP2E-3991 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/47721be6)_

#### [QUANS] GQLの注文プレースメントの例外の処理動作の復帰を確認します

placeOrder突然変異の後方互換性のない変更に対処しました。

_ACP2E-4031 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/52f46328)_

#### GraphQL経由で注文する際に、翻訳されたメッセージをエラーコードにマッピングする問題

翻訳された例外メッセージを使用してGraphQL リクエストのエラーコードをマッピングし、既知のエラーに対して不明なエラーコードが発生する問題を修正しました。

_ACP2E-4033 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/fab20b00)_

#### 日付に対して[CLOUD]の顧客注文フィルターが機能しない

修正後、日付範囲フィルターを使用してGraphQLで注文を取得すると、正しい結果が返されます。

_ACP2E-4090 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/a1c57b2e)_

#### ACP2E-4031で発生した問題への対処

修正前は、エラーノードの位置は、2.4.7および2.4.9のバージョンとのシームレスな互換性を提供していませんでした。 修正の後、エラーノードは両方のバージョンに対応するように適切に配置されます。

_ACP2E-4115 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/e457c5e2)_

#### Graphql呼び出しで子がinstockを持っている場合でも、「在庫切れ」を示すバンドルの親

修正後、GraphQLを使用して商品リストをリクエストすると、バンドル商品の正しい在庫状況が返されます。

_ACP2E-4168 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/a1c57b2e) - [GitHub コードの貢献度](https://github.com/magento/inventory/commit/5632fb5e)_

#### SWATでのGraphQL Exception

修正後、GraphQL リクエストの応答は、HTTP仕様を通じてGraphQLと連携されます。 リクエストを解析できない、リクエストが許可されていない、またはリクエストに別の一般的な問題がある場合は、4XX応答コードが返されます。 リクエストが解析され、処理できる場合は、200の応答コードが返されます。

_ACP2E-4194 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/45cbf9b6)_

#### リストがお客様に割り当てられた後、製品が比較リストから削除されない

ゲストユーザーの比較リストを顧客アカウントに割り当てた後、ゲストとして追加された製品を顧客が削除できるようになりました。
以前は、ゲストが追加した項目が割り当て後にお客様のアカウントに正しくリンクされていなかったため、削除操作に失敗しました。

_ACP2E-4244 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/c135fc3a)_

#### updateCartItems GraphQLの誤ったエラー応答

以前は、数量が不足している項目に対するgraphQL リクエストを行うと、項目が利用できない場合でも、要求された数量と価格の計算とともに、エラーコードを含む適切なエラーメッセージが返されていました。 この修正が適用された後、エラーコードを含む適切なエラーメッセージが返され、応答でアイテムの数量が使用できない場合は、古い値に設定されるようになりました。

_ACP2E-4283 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/cbca0396)_

#### MergeGuestOrder プラグインのクロスサイトゲストオーダー割り当てバグ

修正が行われる前は、ゲスト注文のお客様の割り当てでは、アカウント共有オプションを検討していませんでした。 修正の後、顧客と注文ストアが一致する場合は、注文が顧客に割り当てられます（顧客アカウント共有オプションが「Web サイトごと」に設定されている場合）。

_ACP2E-4312 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/c135fc3a)_

### GraphQL、インベントリ/MSI

#### Magento 2 GraphQLのonly_x_left_in_stockの問題 – しきい値を使用する場合の誤った計算

MinQtyの二重控除が正しくないため、only_x_left_in_stock GraphQL フィールドがnullを返した問題を修正しました。計算が修正され、しきい値に基づいて正確な在庫値が返されるようになりました。

_AC-15832 - [GitHub コードの貢献度](https://github.com/magento/inventory/commit/35458c7f)_

#### GraphQL mergeCart突然変異の不一致

修正後、GraphQL リクエストは、在庫構成を考慮して、製品数量を適切に確認します。

_ACP2E-4184 - [GitHub コードの貢献度](https://github.com/magento/inventory/commit/5632fb5e)_

### GraphQL，製品

#### MediaGalleryInterfaceにmedia_typeがない製品graphql

MediaGallery GraphQL リクエストに、商品画像タイプの「types」フィールドが含まれるようになりました。 以前は、この「タイプ」フィールドはMediaGallery GraphQL リクエストには存在しませんでした。

_ACP2E-3880 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/3ad96f6a)_

### GraphQL, セキュリティ

#### GraphQLを介したお客様のパスワードリセットでは、制限が適用されません

GraphQLの変更を通じて行われたお客様のパスワードリセット要求が、ストア/設定/お客様/お客様設定/パスワードオプションで設定されたパスワードリセット制限に準拠しない問題を解決しました。 これらの設定が正しく適用されるようになりました。

_ACP2E-3992 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/6dd3fa99)_

### インポート/エクスポート

#### [問題] パラメーターの種類を修正

読み込み/書き出しモジュールで、文字列として以前に定義された値が配列として正しく設定されるようになったパラメータータイプの不一致を修正しました。 これにより、書き出しコントローラから期待される入力と一致し、静的解析の警告を防ぐことができます。

_AC-11665 - [GitHub issue](https://github.com/magento/magento2/issues/38529) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/64823f95)_

#### [問題] Copyedit: &quot;coping&quot;を&quot;copying&quot;に変更

PRは、「コピー」のスペルを修正するためにマイナーコピーエディットを修正します

_AC-13300 - [GitHub issue](https://github.com/magento/magento2/issues/39311) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/39307)_

#### REST エンドポイント製品インポート Jsonで必須フィールドが検証されない

インポートプロセス（管理者またはAPI）を使用して新しい製品を作成する際に、「名前」フィールドが必須になりました。 修正の前に、名前のない新しい製品を作成した可能性があります。これにより、管理者インターフェイスが壊れ、無効な製品が作成されます。

_ACP2E-3660 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/df92debe)_

#### 書き出しプロセスにWeb サイトフィルターオプションがありません

商品の書き出しを作成する際に、web サイトで商品をフィルタリングできるようになりました。

_ACP2E-3720 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/520f9e30)_

#### AC-13913の重複 – 静的属性クリーニングを非同期で実行します。

修正の後、\Magento\CatalogImportExport\Model\Import\Product\Type\AbstractTypeの多数のインスタンスが作成された場合、「未定義の配列キー「apply_to」エラーはありません。

_ACP2E-3752 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/520f9e30)_

#### Csv製品の読み込み：スウォッチ画像の設定を解除できません

修正前は、製品の読み込みを通じて製品のスウォッチ画像を更新できませんでした。 修正の後、製品スウォッチの画像列に設定された空のマーカーを付けると、画像は非表示に設定されます。

_ACP2E-3972 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/2a1e1e55)_

#### 製品インポートは、ストア範囲に空のURLを生成します

url_keyがインポートデータソースに空の値を持つ場合、ストアビューの製品URL キーは、デフォルトスコープで設定された値を継承するようになりました。 ストアビューレコードのデータソースの読み込みでurl_keyを空の値に設定すると、url_keyがそのスコープの空の値で上書きされます。

_ACP2E-4038 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/52f46328)_

#### 複数選択属性が必要に応じて設定されている場合、製品インポートプロセスでエラーが発生する

複数選択タイプの必要な属性が含まれている場合に、製品の読み込みに失敗する問題を解決しました。 データ検証が正しく通過し、製品インポートプロセスが正常に完了するようになりました。

_ACP2E-4057 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/a1c57b2e)_

#### [CLOUD]在庫の管理時に「取り寄せ注文なし」が選択されている商品は、引き続き、お客様がインポート時に在庫量を超えて注文できるようにしています

修正後、製品の「allow_backorders」属性の許容できない値をインポートできなくなりました。

_ACP2E-4116 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/a1c57b2e)_

#### 説明の長さが65,536文字を超えているため、製品の読み込みに失敗します検証

修正後、値が65,536文字を超えるテキストタイプの製品属性を読み込むことができます。

_ACP2E-4119 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/a1c57b2e)_

#### 製品のYes-No属性のエクスポートフィルターが期待どおりに機能しない

修正の後、Yes/No属性でフィルタリングされた書き出された製品には、適用されたフィルターを尊重する期待される製品が含まれます。

_ACP2E-4160 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/ee918f0d)_

#### インポートによるweb サイトごとのバンドルオプションの価格の更新に関する問題

Web サイトごとにバンドルオプションの選択価格をエクスポートおよびインポートできるようになりました

_ACP2E-4243 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/98f028ab)_

#### 大文字のメールアドレスを持つ顧客を読み込めません

アカウント共有がグローバルに設定されている場合に、大文字のメールを含む顧客を読み込む際に発生する未定義の配列キーエラーを修正しました。 メールの正規化がインポートプロセス全体で一貫するようになり、メールのケースに関係なく顧客をインポートできるようになりました。 web サイトレベルのアカウント共有行動は変わりません。

_ACP2E-4373 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/31258bf6)_

### インポート/エクスポート、顧客/顧客

#### 管理者は、生年月日が現在の日付より大きい顧客をインポートできます

管理者が将来、生年月日が設定された顧客を読み込むことができる問題を修正しました。 これにより、読み込み中にDOBが検証され、無効なレコードのエラーが表示され、将来の生年月日を持つ顧客が読み込まれるのを防ぎ、正確な顧客データを確保できるようになりました。

_AC-13641 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/8670a2b4)_

### 在庫/MSI

#### チェックアウト時にアドレスが変更された場合、最大検索半径を尊重しないストアピックアップ

配送先住所が変更された場合、「店舗で選択」で事前に選択した店舗が更新されます。 以前は、ストアを事前に選択した後、新しい配送先住所が選択したストアの半径内にない場合でも、変更はありませんでした

_ACP2E-3728 - [GitHub コードの貢献度](https://github.com/magento/inventory/commit/07620383)_

#### ホームページとチェックアウトにリダイレクトした後にストアが利用できない

お客様が支払いページに移動してからホームページに戻り、最後にチェックアウトページに戻った場合、以前に選択したストアが「店舗で選択」の配送で事前選択されるようになりました。 以前は、チェックアウトページに戻った後、「店舗で選択」で選択した店舗がクリアされていました。

_ACP2E-3793 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/a20a6ff2) - [GitHub コードの貢献度](https://github.com/magento/inventory/commit/62c0d79b)_

#### 在庫削除操作が完了していません

修正後、ソース項目を削除しても完全なインデックスは作成されず、影響を受ける製品のみが更新され、パフォーマンスが向上します。

_ACP2E-3917 - [GitHub コードの貢献度](https://github.com/magento/inventory/commit/ee0bf4ad)_

#### [MSI]お客様が注文が受け取り準備完了の通知を非同期で受け取った場合、管理画面に表示されない

注文履歴に追加されたお客様に関する通知は、注文が受け取り準備完了に関する通知を非同期で受け取りました

_ACP2E-3968 - [GitHub コードの貢献度](https://github.com/magento/inventory/commit/29653b1d)_

#### 見積書の読み込み時に重複した在庫状況クエリ

ストアフロントに見積もりを読み込む際にcataloginventory_stock_status クエリが重複して実行され、冗長なDB呼び出しが発生する問題を修正しました。

_ACP2E-4102 - [GitHub コードの貢献度](https://github.com/magento/inventory/commit/fc15a9ae)_

#### パッチ後のACP2E-4118：管理者の在庫しきい値の変更により、販売可能な数量がマイナスになり、在庫ステータスが一致しない

グローバルな在庫設定の数量、バックオーダー、在庫切れしきい値がインポートによって更新されると、在庫在庫ステータスが自動的に調整されるようになりました。

_ACP2E-4142 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/a1c57b2e) - [GitHub コードの貢献度](https://github.com/magento/inventory/commit/5632fb5e)_

#### [CLOUD]管理者レポートに、在庫の更新時に詳細が表示されない

製品の在庫ソースの変更は、現在、ログモジュールによってログに記録されています。 修正前は、製品を保存し、在庫関連の変更を実行する際に、詳細がログに記録されていませんでした。

_ACP2E-4167 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/cbca0396) - [GitHub コードの貢献度](https://github.com/magento/inventory/commit/76b88f7c)_

#### 在庫中としてマークされている間にバンドル商品がカートに追加できない

バンドル商品の在庫状況に、子商品の予約と在庫切れのしきい値が正しく反映されるようになりました。
以前は、バンドル商品は、1つ以上の子商品に十分な販売量がない場合でも「在庫」と表示されていました。 これにより、バンドルをカートに追加する際に「販売に十分な商品がありません」というエラーが発生しました。

_ACP2E-4220 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/cbca0396) - [GitHub コードの貢献度](https://github.com/magento/inventory/commit/76b88f7c)_

#### 子がカスタムソース/在庫に割り当てられている場合、CSVから読み込んだ後、グループ化された製品がPDPで「在庫切れ」と表示される（手動でインデックスを再作成した後に修正）

修正の後、インポートを使用して複合製品を作成すると、自動的に在庫のインデックス再作成が実行され、手動でインデックス再作成を行う必要なく製品を利用できるようになります。

_ACP2E-4233 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/98f028ab) - [GitHub コードの貢献度](https://github.com/magento/inventory/commit/5704166a)_

#### [MSI]最新のメインライン変更に関連するMFTF テストに失敗しました。

修正ゲストが配送先住所なしで実店舗内ピックアップを選択する前に、請求先住所にストアの住所が自動入力され、変更できないため、請求書の詳細が誤っていました。 このシナリオで修正請求先住所が編集可能になり、ゲストが自分の詳細を入力できるようになりました。 登録したユーザーには、ストアの代わりに保存された請求先住所が表示されます。

_ACP2E-4260 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/ab891304) - [GitHub コードの貢献度](https://github.com/magento/inventory/commit/13e432a6)_

#### バーチャルギフトカード用に誤った在庫予約が作成される

この修正を実施する前は、複数のアイテムを含むバーチャルギフトカードの数量が、在庫予約に正確に反映されていませんでした。 しかし、修正が適用された後、在庫予約と在庫の数量が同期されるようになりました。

_ACP2E-4267 - [GitHub コードの貢献度](https://github.com/magento/inventory/commit/5704166a)_

#### 在庫予約補償コマンドがNullおよび存在しない製品参照で失敗する

処理された組み合わせに注文IDが欠落している場合に、在庫予約補償CLIで例外がスローされる問題を修正しました

_ACP2E-4301 - [GitHub コードの貢献度](https://github.com/magento/inventory/commit/76b88f7c)_

#### SKU ケースを変更した後、製品は在庫切れになっています

SKU ケースを変更すると、ストアフロントで商品の在庫切れが発生しなくなります。

_ACP2E-4375 - [GitHub コードの貢献度](https://github.com/magento/inventory/commit/0836c2ed)_

#### 無効なデータを含む価格/価格ファセットによる注文

この修正を行う前は、子商品がカスタムソースで在庫を持っている場合、バンドル価格は適切にインデックス化されていませんでした。 修正が完了すると、子製品の在庫割り当てにかかわらず、バンドル価格が適切にインデックス化されるようになりました。

_ACP2E-4380 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/1c547060) - [GitHub コードの貢献度](https://github.com/magento/inventory/commit/1f83ed24)_

#### ステージングの更新中にSKU変更後の数量を含む在庫ステータスが誤って「在庫中」にリセットされる

アクティブなスケジュール済みアップデートを持つ製品のSKU変更が禁止されるようになりました。保存は明確なエラーで失敗し、アクティブなアップデート中は管理SKU フィールドが無効になります。 これにより、ステージング ロールバック中にSKUの変更によって発生するMSI インベントリの不整合を防ぐことができます。

_ACP2E-4389_

### 注文

#### AbstractAddress setData （&#39;custom_attributes&#39;, AttributeValue[]）はcustomAttributesを壊します

アドレスのカスタム属性が、チェックアウトおよびAPIの操作中に正しく処理されるようになりました。
以前は、$address->setCustomAttributes （&#39;custom_attributes&#39;, $attributes）を使用すると、カスタム属性の処理が壊れ、属性値が誤って構造化される可能性がありました。
AC-10568

_AC-10568 - [GitHub issue](https://github.com/magento/magento2/issues/31644)_

#### お客様が見積もり注文に設定されている場合は、引き続きゲスト注文です

説明はありません。

_AC-11689 - [GitHub issue](https://github.com/magento/magento2/issues/38540)_

#### バーチャル、返金、発送の商品を組み合わせると、注文が完了しない

仮想アイテム、返金、および発送済みアイテムを含む注文が、発送済み数量の計算に仮想アイテムが含まれていることを確認し、注文状態を正しく完了に移行できる処理中に残る問題を修正しました。

_AC-11691 - [GitHub issue](https://github.com/magento/magento2/issues/38547)_

#### v2.4.7-p1 Magento reorder -1注文番号

システムは期待どおりに動作しており、バックエンドからの再発注後、注文番号は一意の8桁になります

_AC-12854 - [GitHub issue](https://github.com/magento/magento2/issues/39089) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/39399)_

#### Adobeのクレジットカード支払い方法でチェックアウトする際に、商品カスタムオプションファイルをアップロードできない

Adobeのクレジットカード支払い方法でチェックアウトする際に、商品カスタムオプションファイルのアップロードが保持されるようになりました。
以前は、この支払い方法を使用する際にファイルのアップロードが失われましたが、他の人と協力していました。
AC-14306

_AC-14306 - [GitHub issue](https://github.com/magento/magento2/issues/39647)_

#### 管理者注文 – 遺言書を検索できません

管理者注文グリッドで顧客名（例：「Will」）で注文を検索しても結果が返されない問題を修正しました。 修正後、顧客名でフィルタリングすると、関連する注文が正しく表示されます。

_AC-14360 - [GitHub issue](https://github.com/magento/magento2/issues/36596) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/a8cf637b)_

#### Magento 2.4.8 GraphQL – 注文アイテム order_dateの形式が間違っています

GraphQL応答のorder_date フィールドがyyyy-mm-dd形式で返される問題を修正しました。
これで、order_dateがdd-mm-yyyy形式で正しく表示されるようになりました。

_AC-14431 - [GitHub issue](https://github.com/magento/magento2/issues/39805) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/a3b1abc2)_

#### null以外のフィールド \&quot;AppliedCoupon.code\&quot;の予期しない問題に対してnullを返すことができません

お客様の注文を照会する際に、Adobe CommerceがGraphQLを通じて適用されたクーポンコードを正しく返すようになりました。 以前のAdobe Commerce 2.4.8では、applied_coupons.code フィールドを使用した注文の取得（例えば、customer.orders クエリを介して）は、内部サーバーエラーで失敗する可能性があり、「AppliedCoupon.code」というnull以外のフィールドに対してnullを返せない」というメッセージが表示され、applied_couponsはクーポンコードを含むリストではなく[null]として返されていました。 AC-14484

_AC-14484 - [GitHub issue](https://github.com/magento/magento2/issues/39841) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/97b2ea42)_

#### ストア設定で有効になっているにもかかわらず、管理者注文ビューから送信時に出荷メールが送信されない

これで、注文が行われたストア設定で出荷確認メールが有効になるので、出荷確認メールが送信されるようになりました。

_AC-14563 - [GitHub issue](https://github.com/magento/magento2/issues/39861) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/39897)_

#### 日付のフィルタリングは、フィールド名があいまいであるため機能しません

Magento 2.4.7-p6では、Braintree モジュールとの結合によるエラーの原因として、日付による注文グリッドのフィルタリングが報告されました。
この問題は、日付フィルターを適用する際に、braintree_transaction_detailsおよびsales_order テーブルを結合するクエリに関するものです。
Adobe Commerceエンジニアリングはこのケースをレビューしましたが、環境のエラーを再現できませんでした。
期待される動作は、日付でフィルタリングすると、エラーなしでフィルターに一致する注文が返されるということです。

_AC-15037 - [GitHub issue](https://github.com/magento/magento2/issues/40024)_

#### バックオフィスでの注文作成。少なくとも1つの商品にカスタムオプションが含まれている場合、不要な追加商品が注文に追加されます

カスタムオプションを含む複数の製品を含むバックオフィスで注文を作成すると、意図せず追加の製品が追加され、エラーが発生する問題を修正しました。 選択した商品のみが追加され、予期しない商品を含まない注文の作成が可能になりました。

_AC-15286 - [GitHub issue](https://github.com/magento/magento2/issues/40122) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/b5e99d20)_

#### Magento2：プロモーションルールを作成できません

このPR修正により
\Magento\SalesRule\Model\Rule\Condition\Product::loadAttributeOptions メソッドの\Magento\Catalog\Model\ResourceModel\Eav\Attributeではなく\Magento\Catalog\Model\ResourceModel\Eav\Attribute モデル

_AC-15358 - [GitHub issue](https://github.com/magento/magento2/issues/12176) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/30479)_

#### Magentoは$invoice = $this->_invoiceService->prepareInvoice （$order）を呼び出した後、$orderのエンティティタイプを変更しました。

サブカテゴリの既存のスケジュールされた更新を編集すると、データベース内の親カテゴリのchildren_countが誤って増加する問題を修正しました。 更新を保存した後に、不正確なカテゴリ階層データが発生しました。 修正後、子カウントは正しいままになり、予期せず増加することはなくなります。

_AC-15401 - [GitHub issue](https://github.com/magento/magento2/issues/40154)_

#### 商品が部分的に返金された場合、注文は発送後も「処理中」の状態のままになります

注文の一部を返金し、残りを発送した後、注文が「処理中」ステータスのままになる問題を修正しました。 出荷量と返品数の合計が請求金額と一致すると、注文ステータスが「完了」に正しく更新され、正確な注文ライフサイクル管理が保証されます。

_AC-15419 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/cc0ec250)_

#### バックエンドからセールスメールを送信すると、常に成功します（無効にした場合も）

バックエンドの販売メール通知を修正し、メールサービスの結果を検証して、注文または請求書のメールが無効になっていて送信されていない場合にユーザーに通知されるようにすることで、正確なメッセージを表示できるようにしました。

_AC-16059 - [GitHub issue](https://github.com/magento/magento2/issues/40309) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/c95ed7d7)_

#### 新しいweb サイトとソースに割り当てられた製品の要求リストを作成できません

「URLにストアコードを追加」が有効になっている場合に、新しいweb サイトとソースに割り当てられた製品に対して購買リストを作成できない問題を修正しました。 ストア コードがAPI リクエストから削除され、不正なエラーが発生したため、問題が発生しました。 修正後、正しいストアコンテキストが保持され、要求リストが正常に作成されます。

_AC-16226_

#### カスタム価格0は、再発注時に元の価格にリセットされます。

カスタム価格が0の製品が再発注時に元の価格に戻った問題を修正しました。
これにより、カスタム価格が正しく保持され、商品を再注文する際の正確な価格設定が保証されます。

_AC-8147 - [GitHub issue](https://github.com/magento/magento2/issues/36970) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/01cee3c3)_

#### 無効な支払い方法が機能している注文の発注

GraphQLを介して無効な支払い方法を使用して注文が行われる問題を修正しました。
現在は、利用不可の支払い方法を設定または使用しようとするとエラーが返され、注文が作成できなくなりました。

_AC-9605 - [GitHub issue](https://github.com/magento/magento2/issues/37983) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/a8cf637b)_

#### [Cloud]一部のインライン Javascriptは、magento 2.4.6-p7へのアップグレード後に機能しません

管理画面の「SKUで注文に追加」の「削除」ボタンをクリックすると、SKUが削除されるようになりました。 以前は、「SKUで注文に追加」の「削除」ボタンをクリックしても、SKUは削除されませんでした。

_ACP2E-3515_

#### gift_cardsのシリアル化されたデータがsales_order テーブルで一貫性がありません

sales_order テーブルのgift_cards データが正しくシリアル化されるようになりました。 以前は、注文が更新されるたびにシリアル化されていました。

_ACP2E-3662_

#### 処理中に注文ステータスが停止する

修正前は、「一緒に出荷」オプションが有効になっているバンドル製品を注文する場合、請求書と出荷後に注文ステータスが自動的に「完了」に切り替わらなかった。 修正が完了すると、注文が請求され、発送された後、注文ステータスは自動的に「完了」に切り替わります。

_ACP2E-3947 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/2a252ae6)_

#### [Cloud]Magento OOTB コード – メールテンプレート設定の問題

修正前は、非同期メール送信を使用する際に、配送メールが店舗の注文と一致していませんでした。 これで、修正後、適切な店舗の配送メール注文が配信されます。

_ACP2E-3998 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/462ede94)_

#### 請求書のキャンセルは404にリダイレクトされます

「取り込まない」タイプで行われた請求書の取り消しは、404 ページにつながりません。

_ACP2E-4001 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/2a1e1e55)_

#### Sales Archive Cron ジョブでDB ロックの問題が発生している

修正が行われる前は、アーカイブ cronに配置されたバインドされていないDELETE クエリがGaleraで問題を引き起こしていました。 更新後、削除クエリは制限付きで実行されるようになりました。

_ACP2E-4010_

#### REST APIを使用した設定可能なオプションによる更新された注文に関する問題

REST API エンドポイントを使用して注文を更新する際に、受注項目に既存の製品オプションを保持します。

_ACP2E-4061 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/6dd3fa99)_

#### ストア固有の送信者は、ギフトカードのメールには使用されません

以前は、別のストアから請求書を作成した後にギフトカードのメールテンプレートを送信する場合、管理設定の所有者の名前が、顧客がメールを受信したときにメールヘッダーに反映されることはありませんでした。 この修正が適用された後、メールヘッダーに適切なストアオーナーのメール情報が含まれるようになりました。

_ACP2E-4310_

#### ID別のセールス非同期挿入は、cron実行ごとに100件に制限されています

セールスグリッド非同期挿入の処理を改善しました。 1回のcron実行では、実行ごとに厳密に100行ではなく、保留中のすべての行が一括で挿入されるようになりました。

_ACP2E-4360 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/31258bf6)_

#### 「IDが「1」の製品は存在しません」というエラーメッセージ。 exception.logに繰り返し記録されます

修正の前に、最後に注文したアイテムのセクションで削除された製品が発生したときに、重大なエラーが記録されました。 修正後、マーチャントはdi.xmlの`skipDeletedProductLogging` パラメーターを使用して、削除された製品をログに記録するかスキップするかを設定できます。 デフォルトでは、後方互換性のために動作は変更されませんが、マーチャントはパラメーターを`true`に設定して、削除された製品をサイレントスキップし、ログノイズを防ぐことができます。

_ACP2E-4366 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/61c96348)_

#### 2回目のクレジットメモの払い戻しに対する二重税

前回のクレジットメモが注文ビューページから作成された後、請求書から部分的な払い戻しを作成する際のクレジットメモの誤った税計算を修正しました。

_ACP2E-4384 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/61c96348)_

### 注文，価格設定

#### 管理者がリターンの作成時に誤った通貨記号を表示する

異なる通貨（EUR/USD/GBP）を使用した複数のweb サイト設定では、管理画面の返品商品選択ページに正しい通貨記号が表示されるようになりました。 以前は、デフォルトの通貨記号が表示されていました。

_ACP2E-3658 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/df92debe)_

### 注文、返品

#### オフライン払い戻しのクレジットメモを作成する際にエラーが発生しました

「Dynamic Price = No」という設定でバンドル製品のクレジットメモの作成に失敗する問題を修正しました。 クレジットメモをエラーなしで正常に作成できるようになりました。

_ACP2E-4157 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/45cbf9b6)_

### その他

#### 「Cap Reward Points Balance At」の値を空のままにすることはできません – 保存

Adobe Commerceでは、リワードポイントの残高の上限フィールドを空のままにしながら、リワードポイントの残高の引き換えしきい値を設定できるようになりました。 以前は、店舗/設定/顧客/報酬ポイントで報酬ポイントを設定する際に、報酬ポイント残高の引き換えしきい値に正の数値を入力し、Cap報酬ポイント残高を空白のままにすると、検証エラーが発生しました。「\&quot;Cap Reward Points Balance\」は無効です。 残高は正の数値または空のままにする必要があります。 確認して、もう一度試してください。」と表示され、キャップなしで設定を保存できないようにします。 ACP2E-3977

_ACP2E-3977_

### その他の開発者向けツール

#### [問題]保護されたメンバー$_urlHelperの型ヒントが正しくありません

システムは、間違った型ヒントを正しい型ヒントで修正するようになりました。これはコンストラクタでも使用されます

_AC-10716 - [GitHub issue](https://github.com/magento/magento2/issues/32503) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/32496)_

#### [問題]未使用のコードのクリーンアップ。

未使用のインポートに関する未使用コードが削除されるようになりました。

_AC-10980 - [GitHub issue](https://github.com/magento/magento2/issues/38424) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/33499)_

#### Lighthouse アクセシビリティ エラー

システムはアクセシビリティスコアが100で合格しました

_AC-12783 - [GitHub issue](https://github.com/magento/magento2/issues/39054) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/39164)_

#### Captcha ストアフロント設定を無効にしてもcaptcha js ファイルを読み込む

captchaを無効にした場合、システムがcaptcha js ファイルを読み込めなくなりました
ストアフロント用

_AC-14267 - [GitHub issue](https://github.com/magento/magento2/issues/32987) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/39154)_

#### [問題] アクセシビリティ：メニューでWAI-ARIA ロールのネストが間違っています

メニューエラーでWAI-ARIAの役割が間違ってネストされることなく、システムがLighthouseのアクセシビリティを生成し、レポートが緑色になる

_AC-15082 - [GitHub issue](https://github.com/magento/magento2/issues/40045) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/38617)_

#### Magento管理者の電子メールプレビューでコンソールエラーが発生する

メールテンプレートのプレビュー中にコンソールエラーが発生することはありません

_AC-9245 - [GitHub issue](https://github.com/magento/magento2/issues/37820) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/37933)_

### お支払い/お支払い方法

#### バックエンドで正常に設定している間、Paylater メッセージがストアフロントに表示されない

バックエンドで設定されているにもかかわらず、PayPal Pay Later メッセージがホームページとカートページに表示されない問題を修正しました。 デフォルトのアドレスを持たないゲストまたは顧客に対して購入者の国がnullの場合、バナーをレンダリングできませんでした。 修正後、ストアフロントに「Pay Later」メッセージが正しく表示されます。

_AC-12335 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/528af81a)_

### 支払い

#### [問題] オフラインの請求書キャプチャを修正（404）

Magento管理者からオフラインの支払い方法の請求書をキャプチャする際の404 ページエラーを修正しました

_AC-13336 - [GitHub issue](https://github.com/magento/magento2/issues/39298) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/39297)_

#### PayPalの不明なIPNがアプリケーション IPN プロセッサを不正使用する

IPN ハンドラーが、サポートされていないIPN タイプまたは不明なIPN タイプを無視するようになりました。 500 エラーを返す代わりに、問題をログに記録し、中断なく処理を続行します。

_ACP2E-4049 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/6dd3fa99)_

#### PayflowProの保存されたカードトークンが支払いに失敗しました

PayPal PayFlow Pro トランザクション ID （PNREF）は、12か月間の固定期間のリファレンストランザクションで使用できるようになりました。 有効期限が切れると、保存されたカードは表示されなくなり、再度追加する必要があります。 以前は、元の取引で使用された支払いカードの有効期限によって有効性が決定されていました。

_ACP2E-4064 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/52f46328)_

#### Adminで注文時にVaulted Cardの問題が発生する

支払いアクションの設定が異なるweb サイトに保存されているクレジットカードで注文を行っても、エラーや間違ったトランザクションタイプが発生しなくなりました

_ACP2E-4270 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/0a8c9a9a)_

#### [Cloud] PayflowProが保存したカード （Vault）の最後の4桁が注文に表示されない

PayflowProの承認支払いアクションを使用する場合と一致する、Sales支払いアクションで保存されたカードを使用する場合、カード情報が適切に保持され、表示されるようになりました。

_ACP2E-4346 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/0a3b7032)_

### パフォーマンス

#### [問題] Store.phpの更新

このPRは、現在のストア解決をスキップすることでパフォーマンスを向上させます。

_AC-14791 - [GitHub issue](https://github.com/magento/magento2/issues/39949) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/38717)_

#### [問題]静的サイトに対するキャッシュ制御の不変の使用の更新

このPRでは、ページ読み込みのたびに静的コンテンツが変更されるまで検証しないことで、パフォーマンスが向上します。

_AC-15171 - [GitHub issue](https://github.com/magento/magento2/issues/39486) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/39484)_

#### [問題] isCacheable呼び出しの結果をキャッシュして、パフォーマンスを向上させます

このPRでは、isCacheable （） メソッドのキャッシュが追加され、レイアウトレンダリングプロセスの結果が追加され、冗長なチェックを減らし、ページレンダリング全体のパフォーマンスが向上します。

_AC-16054 - [GitHub issue](https://github.com/magento/magento2/issues/40156) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/40112)_

#### [問題]非同期注文グリッド処理のパフォーマンスが大幅に改善されました

このPRでは、一時的なキャッシュベースのlast_updated_at ルックアップを、フラグテーブルに保存された永続的なDB-backed フラグに置き換えることで、Magentoの非同期注文グリッド処理のパフォーマンス最適化を導入します。 これにより、キャッシュのフラッシュやデプロイメントの後でも、最後に処理されたタイムスタンプが常に保持されるため、大規模なsales_order データセットで不要なテーブル全体のスキャンを防ぐことができます。 これにより、非同期グリッドの更新が効率的かつ予測可能になり、特に注文頻度の高い大量店舗で顕著に見られます。

_AC-16109 - [GitHub issue](https://github.com/magento/magento2/issues/40282) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/40271)_

#### カテゴリ権限モジュールでキャッシュを防止する可能性があります

顧客セグメントで3rd パーティのコントローラーが正しくキャッシュされるようになりました

_ACP2E-3721_

#### [CLOUD] カテゴリーに商品を追加できません

Visual Merchandiserを使用して商品をカテゴリに追加する際のパフォーマンスが向上しました。

_ACP2E-3946 - [GitHub コードの貢献度](https://github.com/magento/inventory/commit/29653b1d)_

#### [Cloud] cache_invalidate over 10K logs

以前は、PLPまたはカート訪問のたびにキャッシュがクリアされ、不要なパフォーマンスのオーバーヘッドが発生していました。 これらのページで、ターゲットルールキャッシュが無効化されなくなり、ブラウジング効率が向上しました。

_ACP2E-4059_

#### [Cloud] php-fpmがmax_execution_timeを尊重していません

デプロイメント設定は、1回のリクエストで1回ロードされるようになりました。

_ACP2E-4201_

#### ACP2E-3995後の変更ログ クリーンアップ パフォーマンスの問題

修正の後、indexer_clean_all_changelogs cron ジョブは変更ログを完全にクリーンアップし、バッチ処理を維持します。

_ACP2E-4211 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/ee918f0d)_

#### [CLOUD] 2.4.8へのアップグレード後、Fastly キャッシュが機能しない

キャッシュ可能なページが正しく保存されず、Fastly キャッシュからサービスが提供されず、キャッシュ動作が一貫性がなく、パフォーマンスが低下する問題を解決しました。

_ACP2E-4324 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/2687b487)_

#### redis キーとキャッシュキーの作成が増加した理由を調べます

修正前は、リモートストレージのメタデータに使用されるキャッシュキーが期限切れになっていませんでした。 修正の後、依存関係インジェクションを通じてそのようなキャッシュキーのTTLを設定できます。

_ACP2E-4345 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/0a3b7032)_

### 価格

#### 価格は常に0のためバンドル製品アイテムなしで動的価格で注文rest API

注文REST APIは、バンドル製品アイテムの正しい価格を動的な価格なしで返すようになりました。
以前は、REST APIを介して注文を書き出す場合、バンドルページに表示されている実際の価格ではなく、動的な価格設定を使用しないバンドル製品アイテムの価格は常に0として返されていました。
AC-11925

_AC-11925 - [GitHub issue](https://github.com/magento/magento2/issues/38687) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/7da46f52)_

#### 作成時に価格属性に割り当てられた範囲が正しくありません

新しく作成された価格属性が、設定に関係なくストアビューの範囲に誤って割り当てられる問題を修正しました。修正後、属性の範囲がデフォルトでカタログの価格範囲の設定（グローバルまたはWeb サイト）と一致するようになりました。

_AC-14945 - [GitHub issue](https://github.com/magento/magento2/issues/39986) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/8670a2b4)_

#### 「特別価格開始日」が「終了日」より後の場合でも、一括処理を使用して製品を保存しています

検証なしで無効な特別価格日付範囲で製品を保存できる問題を修正しました。
次のエラーメッセージが表示されます。「開始日が開始日より後であるか、または開始日と同じであることを確認してください」

_AC-15252 - [GitHub issue](https://github.com/magento/magento2/issues/40113) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/36d4d6fb)_

#### paypal express チェックアウトを完了した後の配送詳細情報が一致しません（交渉可能な見積もり）。

この問題は、承認済みの交渉可能な見積もりに対するPayPal Express チェックアウトを完了する際の送料の不一致を修正しました。
修正の前に、出荷量が誤って2倍になり（5 ドルではなく10 ドルを表示）、合計が膨らんでいました。
Magento 2.4.9-alpha3の修正により、正しい送料が適用されます

_AC-15280_

#### タイムゾーンが異なるweb サイトでは、特別価格は適用されません

修正の前に、現在のストアのタイムスタンプの範囲で特別価格日付の有効性が作成されました。 修正の後、デフォルトのストアタイムゾーンが考慮されます。

_ACP2E-4002_

#### 特別価格が適用されていても、通常の価格は表示されません。

特別価格が適用されたときに通常価格が表示されない問題を解決しました。 通常の価格が、予想通り特別価格と一緒に正しく表示されるようになりました。

_ACP2E-4100 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/47721be6)_

### 製品

#### フロントエンドで動作が悪い設定可能な製品

カラースウォッチ属性が含まれている場合に、設定可能な製品で誤ったフロントエンド動作が表示され、価格、ドロップダウンレイアウト、必須フィールドインジケーターが正しく表示されない問題を修正しました。
現在、設定可能な製品は、適切な価格設定、調整されたドロップダウン、期待されるUI動作により正しくレンダリングされます。

_AC-1014 - [GitHub issue](https://github.com/magento/magento2/issues/14296) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/ef666cd9)_

#### 在庫切れ商品を表示するオプションを有効にして、テスト在庫およびテスト web サイトに割り当てられた設定可能な商品の価格引用文字列が一致しません

すべての子製品の価格が同じ場合に、設定可能な製品の実際の価格設定に合わせて、失敗したテストを更新しました。
アサーションは、表示された価格を正しく検証し、機能に影響を与えずに誤ったテスト失敗を防ぐようになりました。

_AC-10843 - [GitHub コードの貢献度](https://github.com/magento/inventory/commit/1ccc786b)_

#### テストケース AC-6158の設定可能な製品に対しては、「As low as」ラベルが引き続き表示されます

各バリエーションとカテゴリ割り当てを含む設定可能な製品（P1～P7）を実装および検証しました。 カテゴリーCの商品については、正しいストアフロント価格の表示と「できるだけ低い」ラベル動作を保証。

_AC-10847 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/a3b1abc2)_

#### 選択したオプションを含まない元の価格で計算された階層価格とカタログ価格ルールの割引率。

階層価格およびカタログ価格ルールの割引率に、選択したカスタムオプションが含まれるようになりました。
以前は、選択したカスタムオプションを考慮せずに元の製品価格でパーセンテージ割引を計算していたため、最終的な価格が誤っていました。
AC-12004

_AC-12004 - [GitHub issue](https://github.com/magento/magento2/issues/38750)_

#### [問題]検証評価が機能しません。レビュー評価のセレクターが変更されました

セレクターが変更されたためにレビューの評価の検証がトリガーされない問題を修正しました。 以前は、評価を選択せずにレビューを保存することができました。 修正後、検証は正しく機能し、評価が選択されていない限り、レビューを保存できません。

_AC-12686 - [GitHub issue](https://github.com/magento/magento2/issues/33424) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/528af81a)_

#### Magento 2.4.7分が許可されていません商品の注文数量が不足しています

システムは正常に動作しており、ページソースに製品の最小数量が正しく表示されている

_AC-12909 - [GitHub issue](https://github.com/magento/magento2/issues/39142) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/39480)_

#### 製品コレクション - addMediaGalleryDataは、コレクションが読み込まれる可能性がある場合または読み込まれる場合にgetSizeを呼び出します（追加のDB クエリを避けるためにcountを使用できます）

このPRでは、media_gallery フィールドが含まれているProduct Graphqlを呼び出す際に製品コレクションが既に読み込まれている場合、count （）を使用して追加のクエリ呼び出しを削減します。

_AC-13055 - [GitHub issue](https://github.com/magento/magento2/issues/39111) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/39681)_

#### Magentoのリンクされた商品の無効なSKU処理

SKUの検証が無効なため、SKUが「0」の製品を関連アイテム、アップセルまたはクロスセルのアイテムとしてリンクできない問題を修正しました。 このアップデートにより、このような製品が正常にリンクできるようになり、製品をエラーなく保存できるようになります。

_AC-13311 - [GitHub issue](https://github.com/magento/magento2/issues/39329) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/a8cf637b)_

#### 管理パネルの製品ページのカスタマイズ可能なオプション グリッドに関する問題

タイプ ドロップダウンを使用してカスタマイズ可能なオプションを作成する場合、システムは期待どおりに動作します

_AC-14003 - [GitHub issue](https://github.com/magento/magento2/issues/39640) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/39694)_

#### すべての製品属性がグローバルスコープに設定されている場合の管理製品ページエラー

すべての製品属性がグローバルスコープに設定されている場合に、管理者製品編集ページにエラーが表示される問題を修正しました。 このエラーは、空のデータベースクエリが原因で発生したため、ページを使用できません。 修正後、製品ページは正しくレンダリングされ、製品は問題なく作成できます。

_AC-14011 - [GitHub issue](https://github.com/magento/magento2/issues/39646)_

#### [2.4.8] cron ジョブ catalog_product_alertのコールバックが見つかりません

製品アラートのcron ジョブの名前がproduct_alertに変更された後、Adobe Commerceで誤ったcatalog_product_alert cron ジョブがスケジュールされるのを正しく防止できるようになりました。 以前は、Adobe Commerce 2.4.8で、Stores/Configuration/Catalog/Product Alerts Run Settingsを設定すると、core_config_dataにcatalog_product_alert cron エントリが作成され、cronを実行すると、エラーMagento_Cron.CRITICALが記録されていました。例外：有効なproduct_alert ジョブが正しく実行されていても、cron job catalog_product_alertのコールバックが見つかりません。

_AC-14494 - [GitHub issue](https://github.com/magento/magento2/issues/39800) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/1bc2d6d0)_

#### 「購買リストのページ印刷」オプションが機能しない

リクエストリストページの「印刷」オプションが正しく機能するようになりました。
以前は、「印刷」をクリックすると、「アプリケーションの実行中にエラーが発生しました」というエラーが表示されていました。 詳しくは、例外ログを参照してください。」
AC-14711

_AC-14711_

#### [製品比較]比較リストは使用できません

同じ商品が異なるストアビューから追加された場合、比較リストが使用できなくなる問題を修正しました。修正後、比較リストが正しく読み込まれ、特定のストアに基づいてアイテムが表示されます。

_AC-14885 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/8670a2b4)_

#### リポジトリ経由で製品をリクエストする際の追加ログが失敗する

SKUまたはIDが見つからない場合のProductRepository::getおよびgetByIdのエラーメッセージを改善しました。
以前は、例外で、エラーの原因となったSKUまたはIDに関するコンテキストが提供されませんでした。
現在、例外メッセージには、不足しているSKUまたはIDが含まれており、デバッグと開発者エクスペリエンスの向上に役立っています。
この変更は、APIの機能的な動作には影響しません。

_AC-15199 - [GitHub issue](https://github.com/magento/magento2/issues/40090) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/1b1baf1d)_

#### 属性セットが存在しないエラーがページを壊す

URLに無効な属性セット IDを入力すると致命的なエラーが発生する問題を修正しました。システムは、ページを壊す代わりに、属性セットが存在しないことを示す適切なエラーメッセージを表示するようになりました。

_AC-15753 - [GitHub issue](https://github.com/magento/magento2/issues/40213) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/a06a4a57)_

#### 返金で負の数量は常に割引を返金

マイナスの数量を持つクレジットメモを作成すると、誤って割引金額が返金される問題を修正しました。
現在、割引はマイナスの数量に対して返金されず、返品数量は正しくゼロに設定されています。

_AC-9424 - [GitHub issue](https://github.com/magento/magento2/issues/37917) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/ef666cd9)_

#### ページビルダーで製品ウィジェットが含まれている場合、スロークエリが実行される

商品SKUを含む商品ウィジェット作成用のクエリが最適化されます。

_ACP2E-3449 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/df92debe)_

#### 設定可能な製品として追加すると、製品画像のサイズが変更されない

以前は、管理パネルの「設定」で追加した画像は、最大アップロードサイズ制限に準拠していなかったため、不整合や管理の問題が発生する可能性がありました。 現在では、アップロード中に画像のサイズが自動的に変更され、最大サイズ制限に準拠するように修正され、プロセスが合理化され、システム標準が維持されています。

_ACP2E-3504 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/df92debe)_

#### 他のお客様の比較リストのすべての項目は、管理者経由でログインした後、お客様に割り当てられます

以前、管理者がバックエンドで「顧客としてログイン」機能を使用すると、以前にログインした顧客の比較リストの製品が、現在偽装された顧客に誤って割り当てられました。  修正が完了すると、比較リストが正しく読み込まれ、正しいログイン顧客が表示されます。

_ACP2E-3818 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/462ede94)_

#### 限定的な役割で設定可能な製品を編集すると、シンプルな製品が割り当て解除される

この修正の前に、制限付き管理者ユーザーが、管理者ユーザーがアクセスできない単純な製品を含む設定可能な製品を保存する場合は、保存時に設定可能な製品から削除されました。 修正後、設定可能な製品は、完全な右の管理者から保存されたように保存されます。

_ACP2E-4081_

#### [B2B]共有カタログの保存で非推奨の機能エラーが返される

管理者は、共有カタログから製品の割り当てを正常に解除できます。
以前は、共有カタログから多数の長い製品SKUを持つ製品を割り当て解除すると、エラーが発生していました

_ACP2E-4097 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/ab891304)_

#### [Cloud] サイトマップ生成のパフォーマンスが大幅に低下しています

画像を使用した製品のサイトマップ生成で、急激な減速が発生することはなくなりました。 以前は、画像インクルージョンが有効になっているストアのサイトマップを生成すると、処理時間が長くなっていました。

_ACP2E-4153 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/e457c5e2)_

#### 顧客セグメントの並べ替え順序の不整合により、一部のページで常にX-Magento-Vary Cookieが再生成されます

X-Magento-Vary cookieが製品ページで1回設定されるようになりました。以前は、お客様セグメントの一部の設定で、PDPの読み込み中にcookieが数回設定されていました

_ACP2E-4261_

### 製品，税金

#### 固定製品税（FPT）が設定可能な製品と別に表示されない

オプションを選択した後、設定可能な製品に対して固定製品税（FPT）が個別に表示されない問題を修正しました。 これで、簡単な製品の表示形式と一致するFPTの分類が、製品リスト ページと詳細ページに正しく表示されるようになりました。

_AC-13171 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/b5e99d20)_

### プロモーション

#### 他のルールが既に適用されている場合、購入X買い物かご価格ルールに間違った割引が追加される

別のルールで既に値下げされた後でも、購入X買い物かご価格ルールで元の製品価格を使用して割引が計算される問題を修正しました。 更新により、2番目のルールが調整された価格に割引が適用され、複数のプロモーションがアクティブな場合に正確な合計割引が適用されるようになりました。

_AC-12325 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/8670a2b4)_

#### GraphQlの顧客リクエストを介した顧客の注文に対する注文品目割引applied_toの取得中にエラーが発生しました

以前、GraphQlを介した顧客の注文に対する割引applied_to顧客リクエストの内部サーバーエラーが発生した場合、これは修正され、適用された割引を含む適切な顧客注文データが取得されます

_AC-14888 - [GitHub issue](https://github.com/magento/magento2/issues/39963) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/fe72c407)_

#### GraphQl顧客リクエストによる顧客注文の注文項目クーポンコードの取得中にエラーが発生しました

GraphQLを介してクーポンの詳細を含む注文を取得すると、内部サーバーエラーが返される問題を修正しました。
これで、クエリは正常に実行され、応答で正しいクーポン情報が返されます。

_AC-14889 - [GitHub issue](https://github.com/magento/magento2/issues/39962) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/fe72c407)_

#### ACP2E-2926の修正後、各チェックアウトリクエストで顧客セグメントが照合され、不要な処理が発生します

顧客セグメント機能に、パフォーマンスを向上させるキャッシュメカニズムが追加されました。

_ACP2E-4299_

#### `[Cloud][experienceleague]` カタログ価格ルールが適用されていません

以前は、`special_price`がweb サイトレベルでのみ設定されていた場合（「すべてのストアビュー」ではなく）、カタログ価格の修正ルールは適用されませんでした。 Web サイトのデフォルトストアを最初に確認して`special_price`をweb サイトレベルで設定すると、カタログ価格ルールの修正が正しく適用されるようになりました。

_ACP2E-4372 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/61c96348)_

### SEO

#### DynamicStorage.findProductRewriteByRequestPath （）にentity_type フィルタリングが存在しないため、CMS ページはカテゴリ URLの商品として扱われます

DynamicStorageでentity_typeによるフィルタリングが行われず、CMS ページがカテゴリ URL内の商品として誤って処理される問題を修正しました。形式が正しくないURLでは、CMS コンテンツを提供する代わりに404が正しく返されるようになりました。

_AC-14991 - [GitHub issue](https://github.com/magento/magento2/issues/39996) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/64823f95)_

#### 製品URLでカテゴリーパスを有効にすると、ストアスイッチャーが複数の方法で壊れます

製品URLでカテゴリーパスを有効にすると、ストアスイッチャーが失敗する問題を修正しました。ストアの切り替えにより、ホームページにリダイレクトしたり、エラーを返したりすることなく、ストアビュー間で製品URLが正しく解決されるようになりました。

_AC-15110 - [GitHub issue](https://github.com/magento/magento2/issues/40037) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/a7ef6300)_

#### ProductRepository getByIdの未定義の配列キー

この問題は、ProductRepository::getById （）が123abcなどの無効なIDで呼び出され、「未定義の配列キー」エラーが発生した場合に発生しました。
Magento 2.4.9-alpha3での修正の後、そのようなリクエストは例外をスローする代わりに404 ページを正しく返すようになりました。
QAは有効なIDと不正なIDの両方で確認され、それ以上の問題は観察されませんでした。

_AC-15345 - [GitHub issue](https://github.com/magento/magento2/issues/40146) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/68a45d0a)_

#### Storefront compare productでGoogle SEO エラーが発生する – リンクがクロールできない

href属性が見つからないか、正しくバインドされていないため、ストアフロントの「製品を比較」リンクを検索エンジンでクロールできないSEOの問題を解決しました。 このアップデートにより、リンクに有効なクロール可能なURLが含まれるようになり、サイトの見つけやすさが向上し、Google SEO監査に合格できます。

_AC-15547 - [GitHub issue](https://github.com/magento/magento2/issues/40185) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/c95ed7d7)_

#### REST APIを介した製品url_keyの更新では、301 URLの書き換えが生成されない

REST APIを使用して製品のURL キーを更新する場合、「URL キーが変更された場合はURLの永続的なリダイレクトを作成」設定を「はい」に設定すると、製品URLの書き換えは、古いURLから新しいURLへのリダイレクトを作成します。

_ACP2E-3900 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/462ede94)_

#### [Cloud] サイトマップの生成は終了しません

修正の前は、カタログに100万個以上の製品が含まれている場合、サイトマップの生成を正常に終了できませんでした。 修正の後、サイトマップの生成は、メモリ割り当ての少ない、1店舗あたり100万点もの商品で終了します。

_ACP2E-3902 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/52f46328)_

#### [Cloud] Store SwitcherがFAQ ページのENからFRに機能しない

ストアビューを切り替えると、対応する翻訳されたCMS ページではなく、ユーザーがホームページにリダイレクトされる問題を修正しました。 ストアスイッチャーは、正しいリダイレクトを確保するために、ターゲットストアでのURL書き換えをチェックするようになりました（例：英語のFAQ ページ→フランス語のFAQ ページ）。

_ACP2E-4112_

#### [Cloud]古いサイトマップ生成を無効にする

標準サイトマップ生成プロセスと新しく実装されたバッチモードを切り替えるための新しい設定オプションが利用可能になりました。 この機能強化により、サイトマップ作成ワークフローの柔軟性と拡張性が向上しました。

_ACP2E-4132 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/45cbf9b6)_

#### 不審なリクエストがexception.logに例外をスローしています

悪意のあるURL要求または形式が正しくないURL要求がデータベースの照合エラーを引き起こし、例外ログを入力する問題を修正しました。
以前は、無効な文字エンコーディングまたはサポートされていない文字を含む不審なリクエストを受け取ると、システムがそれらをデコードして処理しようとするため、MySQL照合競合が発生していました。

_ACP2E-4328 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/2687b487)_

### 営業担当者

#### 注文状態ドロップダウンで値を選択すると、注文状態が消える

注文状態の割り当てが期待どおりに機能するようになりました。
以前は、カスタム注文ステータスを割り当てる際に、ステータスの割り当てを解除すると、「処理中」状態がドロップダウンから消えてしまい、再割り当てが不可能でした。
AC-15010

_AC-15010_

#### 注文レベルでギフトメッセージが有効になっていても、ユーザーがデータを入力せず、注文を行わない場合、管理者に顧客の名前と姓が表示されます。

ギフトメッセージが入力されていない場合でも、ギフトメッセージの送信者フィールドと受信者フィールドに顧客名が自動的に入力される問題を修正しました。ユーザーが詳細を提供しない限り、フィールドは空のままになります。

_AC-15140 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/a8cf637b)_

### 検索

#### カタログ検索の「フォームの再送信を確認」と「カテゴリページを記憶」を使用

ツールバーの設定を変更した後、商品ページからカタログ検索結果ページに戻っても、「カテゴリーページを記憶」が有効になっている場合に、「フォームの再送信を確定」ダイアログがトリガーされなくなりました。
以前は、並べ替え順序などのツールバーパラメーターを変更した後に検索結果ページに戻ると、ブラウザーエラーまたはフォームの再送信に関する警告が発生していました。

_ACP2E-4208 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/e885088b)_

#### 集計された検索フィールド「_search」は、検索クエリでは使用されなくなりました

現在、フルテキスト検索では、検索可能なすべてのフィールドで条件が一致する必要がある場合は、1つのフィールドで条件を満たすことを要求するのではなく、一致する製品を返します。

_ACP2E-4285 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/cbca0396)_

### セキュリティ

#### 内部サーバーエラー

非同期REST エンドポイント POST /rest/default/async/V1/carts/mine/itemsを使用すると、Magentoがお客様のカートに商品を正常に追加するようになりました。 以前は、この非同期「カートに追加」リクエストにより内部サーバーエラーが発生し、Magentoは次のエラーを記録しました。エラー：app/code/Magento/Quote/Model/Quote/Item/AbstractItem.php:162のnullでメンバー関数setFinalPrice （）への呼び出し。

_AC-16344 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/8670a2b4)_

#### SRI ハッシュに含まれていないバンドル/マージ済みJS

修正前は、生成されたバンドルまたは結合されたファイルがSRI ハッシュリストに追加されていませんでした。 これで、ファイルがSRI ハッシュに正しく追加されるようになりました。

_ACP2E-3854 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/4ca73607)_

#### [CLOUD] newrelicで書き込み可能な権限の問題が発生しました

修正前は、ログは例外で乱雑になっていました。 修正を適用した後、ログはクリーンになり、例外がなくなりました。

_ACP2E-4296 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/61c96348)_

### 発送

#### 少数のクレジットメモ後に発送する数量が正しくありません

複数のクレジットメモの後に出荷予定数量の値が誤って計算され、払い戻されたアイテムを出荷できる問題を修正しました。
これにより、発送済みの商品や返品された商品にもとづいて、残りの発送可能数量を正確に更新し、無効な発送を防ぐことができます。

_AC-1479 - [GitHub issue](https://github.com/magento/magento2/issues/34289) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/913bf1a6)_

#### 配送方法の読み込みに関する潜在的なパフォーマンスの問題

アクティブな配送業者のみが要求されたときに読み込まれるようにすることで、配送方法の読み込みプロセスを最適化しました。 以前は、すべての出荷方法の工場が初期化され、不要なパフォーマンスのオーバーヘッドが発生していました。 この修正により、アクティブな配送業者のみを条件付きで読み込むことで、読み込み時間とリソースの使用量を削減することで、効率が向上します。

_AC-15415 - [GitHub issue](https://github.com/magento/magento2/issues/40153) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/cc0ec250)_

#### [問題]商用の宛先は住宅用として扱ってはなりません

商用宛先が誤って住宅として扱われたUPS REST出荷統合の問題を修正しました。 ResidentialAddressIndicatorは、居住地の住所に対してのみUPS料金請求に含まれるようになり、意図しない居住地の追加料金を防ぎ、正確な商業送料を確保します。

_AC-16285 - [GitHub issue](https://github.com/magento/magento2/issues/40314) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/40307)_

#### UPS配送ラベルの作成時の例外

警告の修正：UPS出荷ラベル作成時の配列から文字列への変換

_ACP2E-3676 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/b12ffe36)_

#### [QUANS] - Magento_Fedex コアモジュールは、リクエストを送信して新しいトークンを取得する前に、有効なアクティブトークンをチェックしますか？

Adobe Commerceは、アクセストークンに対してFedEx API サービスに多くのリクエストを行うことができなくなりました。 以前は、アクセストークンはまだ有効でしたが、Adobe Commerceは常にFedEx APIに新しいリクエストを行い、レート制限の問題が発生していました。

_ACP2E-3930 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/4ca73607)_

### ステージングとプレビュー

#### カタログ価格ルールの影響を受けるカート内の商品の価格は、ステージング更新によってルールが調整されたときに変更されません

ステージング更新を通じてカタログ価格ルールを変更した後、カート内の製品価格が完全に更新されない問題を修正しました。 以前は、更新された価格は概要セクションにのみ表示されていましたが、中央のカートブロックには古い値が表示されていました。 この修正されたルールにより、カート全体の商品価格が正しく更新されるようになりました。

_AC-15304 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/913bf1a6)_

#### カテゴリの予定更新が削除された場合、親カテゴリの子の量は減少しません

カテゴリのスケジュールされた更新を削除しても、親カテゴリの子カウントが減少せず、スケジュールされた更新またはサブカテゴリが削除されたときにカウントが正しく更新される問題を修正しました。

_AC-15670 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/ef666cd9)_

#### カテゴリのスケジュールされた更新を編集すると、子の量が親カテゴリに追加されます

サブカテゴリの既存のスケジュールされた更新を編集すると、データベース内の親カテゴリのchildren_countが誤って増加する問題を修正しました。 更新を保存した後に、不正確なカテゴリ階層データが発生しました。 修正後、子カウントは正しいままになり、予期せず増加することはなくなります。

_AC-16239 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/8670a2b4)_

#### スケジュールされた更新をプレビューすると、興味のあるストアビューではなく、アルファベット順で最初のストアビューが開きます

修正の前に、スケジュールされた更新のプレビューが、割り当てられたストアビューではなく、アルファベット順で最初のストアビューで開かれました。
修正後、CMS ブロックのステージング更新に割り当てられたストアビューで、プレビューが正しく開くようになりました。

_ACP2E-3671 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/b12ffe36)_

#### Staging_apply_version Cron動作の問題 – special_priceは無視されます

修正後、予定製品の更新により特別価格を変更した後、見積もり合計が再計算されます。

_ACP2E-3674_

#### カテゴリ権限が有効になっている予定製品アップデートをプレビューできません

修正の前は、有効にする製品の将来性がプレビューモードで表示されていませんでした。 現在のステータスが無効になっている場合でも表示されます。

_ACP2E-3786 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/7accebfa)_

#### 範囲は、プレビュー中に異なるストアビューを表示しています

修正の前に、cms ブロックとcms ページのコンテンツのステージング更新プレビューが、コンテンツ ステージングダッシュボードからアクセスしたときにcms ブロックまたはページで割り当てられたストアとは異なるストアで開いている可能性があります。 修正の後、cms ブロックまたはページにステージング更新で特定のストアのみが割り当てられている場合、コンテンツステージングダッシュボードのプレビューが開き、正しいストアが選択されます。

_ACP2E-3815_

#### カタログ価格ルールの割引金額フィールドの検証がありません

以前は、ステージングスケジュール更新のdiscount_amount フィールドが、現在の検証ルールで正しく検証されませんでした。 ただし、修正を適用した後、discount_amount フィールドが適切に検証されます。

_ACP2E-3867 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/462ede94)_

#### 別の管理者ドメインを使用する場合、チェックアウト時にステージング更新プレビューが壊れる

お客様は、ストアベース URLが管理者URLと異なる場合、ストアプレビューモードでログインしてカートを表示できます。

_ACP2E-3906_

#### コンテンツ ステージング ダッシュボードの時間の表示が正しくありません

「コンテンツステージングダッシュボード」の「開始時間」および「終了時間」日付フィルターに、正しい日時が表示されるようになりました。 以前は、日付ピッカーで日時を選択した後に誤った日時が表示されていました

_ACP2E-3969_

#### 範囲は、スケジュールされた更新製品とカテゴリのプレビュー中に異なるストアビューを表示しています

この修正の前に、カテゴリと製品のプレビューリンクが正しいストアに対して生成されませんでした。 この修正の後、プレビューリンクは、プレビューが作成されたストアを自動的に選択します。

_ACP2E-4053_

#### スケジュールされた更新を含むバンドル製品は、製品の保存アクションの「バンドルアイテム」オプションを削除します

バンドル製品オプションまたはスケジュールされた更新で関連する製品を削除しても、元のバンドルオプションおよび関連する製品に影響が及ぶことがなくなり、その逆も同様です。 また、元の製品のバンドル生産オプションを削除し、更新をスケジュールした後に別のオプションに置き換えても、新しく追加されたオプションが削除されなくなりました

_ACP2E-4212 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/ab891304)_

#### 適用されたクーポンが適用された直後に消えるプロモーションプレビューモードの問題。

修正前は、ステージングプレビューモードでバウチャーコードを正しく使用できませんでした。 修正が完了すると、チェックアウトページにバウチャーコードが正しく適用されるようになりました。

_ACP2E-4226_

#### スケジュール更新プレビューでWeb サイト間を移動できない

この修正の前に、カスタムドメインを持つストアのコンテンツをプレビューしようとすると、スケジュールされた更新プレビューが壊れます。 この修正の後、カスタムストアドメインをそのままプレビューし、プレビューiframe内で移動できます。 この修正プログラムは、製品、カテゴリ、CMS ページ、CMS ブロックを対象としており、`{{store url}}`Adobe Commerce変数およびマークアップタグ [に記載されているように、](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/variables/markup-tags)個のマークアップタグを使用したナビゲーションリンクをサポートしています。

_ACP2E-4308 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/0a3b7032)_

### 税

#### 誤った注文の合計、ラウンドは価格計算に適用されません。

price_after_discount、discount_amountおよびtax amountを計算する際に、システムが正しく処理されるようになりました。
注文の実際の合計

_AC-11389 - [GitHub issue](https://github.com/magento/magento2/issues/38455) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/39687)_

#### [問題]修正：クレジットメモ項目のbase_weee_tax_applied_row_amnt値が正しくありません

base_weee_tax_applied_row_amntの適切なセッターを使用してクレジットメモの計算を修正し、税額が払い戻された数量のみを反映するようにしました。 以前は、行の金額で、クレジットメモの一部の金額ではなく、注文総額が誤って使用されていました。

_AC-12049 - [GitHub issue](https://github.com/magento/magento2/issues/38765) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/3b5ac075)_

#### ギフト包装がカートから削除された場合、税額は更新されません

setGiftOptionsOnCart GraphQLのミューテーションを介してギフトのラッピングを削除すると、Magentoでカートの税金合計が正しく更新されるようになりました。 以前は、ギフト包装オプションを選択した後、「giftWrappingId」を渡して設定を解除していた場合、変数入力に「null」を指定すると、見積もりの税額は更新されず、Magentoはギフト包装が適用されなかったにもかかわらず、ギフト包装の合計にギフト包装税を含め続けました。

_AC-14637_

#### ミニカートに入っている商品は、換金せずに外貨価格を表示します

ミニカートで通貨が正しく変換され、設定されたコンバージョン率に基づいて正確な金額が表示されるようになりました。

_ACP2E-4364 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/1c547060)_

### テストフレームワーク

#### [問題] MFTF テスト AdminSetUpWatermarkForSwatchImageTestから重複した&lt;severity> タグを削除します

システムは、AdminSetUpWatermarkForSwatchImageTestに1つの重大度タグのみを含むようになり、コードの明確性と一貫性が向上しました。 以前は、このテストには2つの同一の重要度タグが含まれていましたが、これは不要であり、混乱につながる可能性がありました。

_AC-11873 - [GitHub issue](https://github.com/magento/magento2/issues/38504) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/31862)_

#### [問題] Lib/internal/Magento/Framework/App/Test/Unit/_files/app/etc/en...

ユニットテストの実行時に生成されるファイル「env.php」がシステムによって無視されるようになりました。これにより、テストの実行後もGit ステータスがクリーンのままになります。 以前は、単体テストを実行すると、新しいファイル「env.php」が生成され、git ステータスに新しいファイルが見つかり、ファイルが汚れているように見えます。

_AC-13293 - [GitHub issue](https://github.com/magento/magento2/issues/39304) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/37631)_

#### [問題] インターセプターでの統合テストの問題を修正

システムは、統合テストで\Magento\TestFramework\App\Config\Interceptorを正しく識別して処理するようになり、クラスのプラグインが存在する場合でも、テストが必要なデータにアクセスできるようにします。 以前、システムは\Magento\TestFramework\App\Configが\Magento\TestFramework\App\Config\Interceptorである可能性を考慮できなかったため、$data プロパティにアクセスしようとするとエラーが発生しました。

_AC-13305 - [GitHub issue](https://github.com/magento/magento2/issues/39324) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/37187)_

#### [問題] MFTF：有効なCaptchaを使用した友達へのメール送信フォーム

このテストケースでは、CAPTCHAが有効になっている場合の「Email to Friend」フォームの機能を解決し、フォーム送信プロセスが正しく機能し、誤ったCAPTCHA値と正しい値の両方で機能することを確認します。

_AC-13492 - [GitHub issue](https://github.com/magento/magento2/issues/39462) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/32830)_

#### [ クラウドネイティブサービス ] CNS ビルド失敗 – 2.4.9-beta1 – 統合

説明はありません。

_AC-16427_

#### コンポーザーのビルドでハードコードされたフィクスチャーのパスが失敗する

説明はありません。

_AC-16488_

#### PHPUnit設定ファイルがPR ビルドとComposer ビルドで一致しない

説明はありません。

_AC-16501_

#### [問題] magento/magento2#: GraphQlの変異。 Customer storeConfig設定の追加のテスト範囲。

次のcustomer storeConfig オプションの追加のテストカバレッジが追加されました。
required_character_classes_number
minimum_password_length

_AC-9370 - [GitHub issue](https://github.com/magento/magento2/issues/37915) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/28761)_

#### AC 2.4.7-p3での環境固有の単体テストの失敗

この問題は、すべてのバージョンと環境で再生されない単体テストのエラーを修正します。 以前は、ライブラリのバージョンが異なるか、後のバージョンで追加された機能が欠落しているため、一部の単体テストが失敗していました。

_ACP2E-3712 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/9ad7d277)_

#### [単体テスト ] Magento\GiftCardImportExport\Test\Unit\Model\Import\Product\Type\GiftCardTest::testIsRowValid

ランダムに失敗した単体テストの修正が提供されました

_ACP2E-4263_

### UI フレームワーク

#### [問題]より少ないファイルから重複した変数を削除する

システムは、より少ないファイルから重複した変数を削除し、よりクリーンで効率的なコードを保証するようになりました。 以前は、これらの重複した変数は、より少ないファイルに存在していたため、コードの冗長性が不要でした。

_AC-11743 - [GitHub issue](https://github.com/magento/magento2/issues/31154) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/31150)_

#### 動的行のWYSIWYGが空です

動的行内のWYSIWYG フィールドが正しく初期化され、入力されるようになりました。
以前は、動的行（デザイン設定フォームなど）のWYSIWYG フィールドが空のように見えたり、特定のアクションの後にコンテンツが失われたりしていたため、データを復元するために手動で操作する必要がありました。
AC-12336

_AC-12336 - [GitHub issue](https://github.com/magento/magento2/issues/38893) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/7bdafaa2)_

#### [問題] MIME タイプのタイプミスを修正

Gif画像のMIME タイプとタイプミスを正しく処理して修正しました

_AC-8001 - [GitHub issue](https://github.com/magento/magento2/issues/36899) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/36669)_

#### [問題]禁止されている`@author` タグを`Magento_Backend`から削除

このPRは`@author` タグをコードベースから削除します

_AC-8814 - [GitHub issue](https://github.com/magento/magento2/issues/37522) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/36976)_

#### [問題] レビューリスト Ajaxへの直接アクセスを避ける

システムが正しく処理し、レビューリストへの直接アクセスを回避Ajax

_AC-9381 - [GitHub issue](https://github.com/magento/magento2/issues/37920) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/33876)_

#### 共有Cookieを使用したマルチストア設定でヘッダーのログイン/ログアウトが更新されない

ログアウト時に、設定に従ってログインヘッダーが正しく更新されます。 顧客アカウントがグローバルに共有されている場合、customer-data.jsはCookieを使用して「mage-customer-login」値を保存します。 ローカルストレージは、それ以外の場合に使用されます。

_ACP2E-4149 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/e885088b)_

#### [Mobile] Fotoramaは、画像ビューアのクローズアクションでミニカートを開くことができます

Fotoramaの問題を修正しました。 以前は、画像ビューアのクローズアクションでミニカートが開いていました

_ACP2E-4231 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/e885088b)_

#### 結合されたjs ファイルは、ストアが多いプロジェクトで適切に生成されません。

複数のストアが設定されている場合に、JavaScript ファイルの結合が正しく機能するようになりました。
以前は、マルチストア設定でファイルが正しく結合できなかったため、結果が不完全または一貫性を失っていました。

_ACP2E-4246 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/ab891304)_

### アップグレード – 互換性のアップグレード ツール

#### 非推奨の機能：動的プロパティの作成Magento\Framework\Acl:$_roleRegistry

非推奨の機能エラーにより、アップグレード後に管理者パネルにアクセスできなくなります。
以前は、Magento 2.4.6にアップグレードした後、管理者パネルにアクセスしようとすると、次のエラーが発生する可能性がありました。
「非推奨の機能：動的プロパティの作成Magento\Framework\Acl::$_roleRegistryは、186行目のvendor/magento/framework/Session/SessionManager.phpで非推奨です。」
これにより、管理者はログインできなくなりました。
AC-12343

_AC-12343 - [GitHub issue](https://github.com/magento/magento2/issues/37469)_

#### GUIDはセキュリティで保護された形式として保存されません

説明はありません。

_AC-15809_

#### 間違った重大な問題を含む互換性ツールのアップグレード

該当なし

_ACP2E-3856_
