---
source-git-commit: bfad68a46b9b1a79a702f04efd39129decda1a1c
workflow-type: tm+mt
source-wordcount: '4413'
ht-degree: 0%

---
# Adobe Commerceで修正された問題（v2.4.9-alpha2）

## v2.4.9-alpha2 の問題を修正しました

Adobe Commerce 2.4.9-alpha2 コアコードの 118 の問題を修正しました。 このリリースで修正された問題の一部を以下に示します。

### API

#### 今日までの特別価格は applySpecialPrice で誤って検証されています

システムは特別価格に関して正常に機能しており、製品の特別価格は、管理者または REST API によるサードパーティシステムで設定した日付に期限切れになります

_AC-13130 - [GitHub の問題 ](https://github.com/magento/magento2/issues/39169) - [GitHub コードの投稿 ](https://github.com/magento/magento2/pull/39690)_

#### リクエスト本文またはパラメーターの形式が正しくないため、「内部サーバーエラー」が発生する

_AC-746 - [GitHub の問題 ](https://github.com/magento/magento2/issues/32784) - [GitHub コードの投稿 ](https://github.com/magento/magento2/commit/f1adb44e)_

#### 注文「base_row_total」と「row_total」は、REST API 応答で単一項目価格を表示します

複数の同じ項目が注文された場合の、注文詳細の REST API 応答に、「base_row_total」属性と「row_total」属性の正しい値が含まれるようになりました

_ACP2E-3874 - [GitHub コードの投稿 ](https://github.com/magento/magento2/commit/4ca73607)_

### API、順序

#### [CLOUD] 注文情報の問題（注文 000075568 の行合計の表示）

項目が完全にディスカウントされた場合に、注文 API 応答の row_total_incl_tax 値が 0.00 ではなく、ゼロに近い残差値として返される問題を修正しました。

_ACP2E-3950 - [GitHub コードの投稿 ](https://github.com/magento/magento2/commit/462ede94)_

### アカウント

#### 管理パネルでおよび.swiss ドメインを使用して顧客の電子メールを更新する際の問題

_AC-13409 - [GitHub の問題 ](https://github.com/magento/magento2/issues/39394) - [GitHub コードの投稿 ](https://github.com/magento/magento2/commit/d3ea191d)_

#### ニュースレターの購読が有効なスイッチが web サイト/ストアごとに機能しない

システムは、グローバルレベルで無効にされた複数の web サイト/ストレビューがある場合、ニュースレターの購読を正しく処理します

_AC-14283 - [GitHub の問題 ](https://github.com/magento/magento2/issues/39751) - [GitHub コードの投稿 ](https://github.com/magento/magento2/pull/39752)_

#### 「製品が表示された」顧客セグメント条件の非推奨（廃止予定）

_AC-14542_

#### [ 問題 ] 削除された電子メールの開示

入力したメールがアカウントの確認に不要な場合、顧客が存在しているかどうかに関係なく、誤ったメールを示すエラーメッセージを表示するようになりました。

_AC-14561 - [GitHub の問題 ](https://github.com/magento/magento2/issues/39574) - [GitHub コードの投稿 ](https://github.com/magento/magento2/pull/39570)_

### 管理 UI

#### シンプルな製品では、同じ設定で買い物かごページと製品ページの FPT 値が異なります

_AC-13066 - [GitHub コードの投稿 ](https://github.com/magento/magento2/commit/8953613e)_

#### スウォッチモジュールが無効の場合、複数選択/選択属性オプションを保存できない

_AC-13071 - [GitHub コードの投稿 ](https://github.com/magento/magento2/commit/8953613e)_

#### 買い物かごページと製品ページの FPT 値が、動的製品に対して同じ設定で異なる

_AC-13075 - [GitHub コードの投稿 ](https://github.com/magento/magento2/commit/8953613e)_

#### 管理の静的グリッドにホバーの色が適用されない

管理者の静的グリッドの行に、期待どおりにホバーカラーが適用されるようになりました。[GitHub-35358](https://github.com/magento/magento2/issues/35358)

_AC-2916 - [GitHub の問題 ](https://github.com/magento/magento2/issues/35358) - [GitHub コードの投稿 ](https://github.com/magento/magento2/pull/35384)_

#### 制限付き管理者ユーザーは、製品ステータスを一括更新できない

カスタム管理者は、web サイトレベルのプロパティなので、製品ステータスを一括更新できます。 ステータスは、制限された管理者がアクセス権を持つ web サイトでのみ更新されます。

_ACP2E-3772_

#### [ ステージング 2] 保管されたカードが管理パネルに表示されない

アップグレード後、「ストアドカード」支払いオプションがバックエンドの注文配置フォームに表示されなくなる問題を修正しました。

_ACP2E-3830 - [GitHub コードの投稿 ](https://github.com/magento/magento2/commit/7accebfa)_

### B2B

#### ゲストチェックアウトの会社フィールドの検証に失敗する

_AC-14987 - [GitHub の問題 ](https://github.com/magento/magento2/issues/40011) - [GitHub コードの投稿 ](https://github.com/magento/magento2/commit/f1adb44e)_

### バンドル

#### テーマをまたいだバンドル出力から Hugerte Editor JS ファイルを除外する

_AC-15128 - [GitHub コードの投稿 ](https://github.com/magento/magento2/commit/43648891) - [GitHub コードの投稿 ](https://github.com/magento/magento2/commit/2bc584af)_

### 買い物かごとチェックアウト

#### グループ化された製品フロントエンド数量の検証がありません

負の数量と最大数量を追加しようとすると、システムは正常に動作し、検証エラーが表示されるようになりました

_AC-13524 - [GitHub の問題 ](https://github.com/magento/magento2/issues/39479) - [GitHub コードの投稿 ](https://github.com/magento/magento2/pull/39480)_

#### ゲストのプレフィックスが見積もりアドレス 2.4.8 に保存されない

_AC-14705 - [GitHub の問題 ](https://github.com/magento/magento2/issues/39915) - [GitHub コードの投稿 ](https://github.com/magento/magento2/commit/f1adb44e)_

#### [ 問題 ] base_price ではなく見積品目に価格を設定します

フロントエンドの 1 つの web サイトに複数の通貨がある場合、システムは見積もり品目の価格を価格ではなく base_price に正しく処理します

_AC-9985 - [GitHub の問題 ](https://github.com/magento/magento2/issues/38094) - [GitHub コードの投稿 ](https://github.com/magento/magento2/pull/36878)_

#### [ クラウド ] 注文が 1 つのストア表示で作成された場合、最近の注文が他のストア表示に表示されない

「マイアカウント」ページに、同じストア内の他のストア表示からの最近の注文が表示されない問題を修正しました。 注文取得ロジックが更新され、「マイオーダー」ページの動作に合わせて、すべてのストアビューで一貫した注文表示が確保されました。

_ACP2E-3807 - [GitHub コードの投稿 ](https://github.com/magento/magento2/commit/a20a6ff2)_

#### 次として表示する数量  バンドル製品の追加中に「管理者の顧客の買い物かご」セクションで 0 を選択  

顧客アクティビティの「買い物かご」セクションに、正しい数量が表示されるようになりました。 以前は、数量は 0 と表示されていました。

_ACP2E-3872 - [GitHub コードの投稿 ](https://github.com/magento/magento2/commit/3ad96f6a)_

### 買い物かごと、チェックアウト、GraphQL

#### GraphQL経由で注文する際に、メッセージをエラーコードにマッピングする際にエラーが発生する

存在しない買い物かごまたは非アクティブな買い物かごに注文を行うためのGraphQL呼び出しで、すべてのストアビューで CART_NOT_ACTIVE または CART_NOT_FOUND エラーコードが正しく返されるようになりました。翻訳されたエラーメッセージによって、以前に未定義のコードが発生していた問題を修正しました。

_ACP2E-3942 - [GitHub コードの投稿 ](https://github.com/magento/magento2/commit/7accebfa)_

### 買い物かごおよびチェックアウト、GraphQL、在庫/MSI

#### cartItemInterface の is_available 属性は、販売可能な在庫が多い場合でも false を返します

is_available 属性は、販売可能な在庫が多い場合に true を返します。 以前は、常に false を返します。

_ACP2E-3885 - [GitHub コードの投稿 ](https://github.com/magento/magento2/commit/3ad96f6a)_

### カタログ

#### カタログ URL リソース （_getCategories）のスコープバグ

この PR は、カテゴリ URL リソースのストアスコープで値が定義されていない場合、デフォルトスコープにフォールバックを追加します。

_AC-11011 - [GitHub の問題 ](https://github.com/magento/magento2/issues/38393) - [GitHub コードの投稿 ](https://github.com/magento/magento2/pull/38394)_

#### [ 問題 ] OpenGraph で価格を表示できるかどうかを確認してください

価格を非表示にするプラグインを使用すると、システムは正常に機能し、この変更価格は OG タグに表示されません。

_AC-11635 - [GitHub の問題 ](https://github.com/magento/magento2/issues/38512) - [GitHub コードの投稿 ](https://github.com/magento/magento2/pull/38510)_

#### [ バグ ] REST API：特別価格の更新で、すべてのストアビューの値が設定されない

_AC-13671 - [GitHub の問題 ](https://github.com/magento/magento2/issues/39521) - [GitHub コードの投稿 ](https://github.com/magento/magento2/commit/7bdafaa2)_

#### [\Magento\ConfigurableProduct\Model\Product\Type\Configurable] PHP エラーが通知されませんでした

この PR はループ変数名を変更して、後続の呼び出しで使用される特定の製品に「_cache_instance_product_ids」データを正しく追加します。

_AC-14159 - [GitHub の問題 ](https://github.com/magento/magento2/issues/39641) - [GitHub コードの投稿 ](https://github.com/magento/magento2/pull/39642)_

#### [ メインライン ] [ クラウド ] 画像のサイズ変更に 400 GB を超えるディスク領域を使用

修正後、—skip_hidden_images フラグで使用される `catalog:images:resize` コマンドでは、画像が存在しない Web サイトの画像キャッシュが生成されません。

_ACP2E-3869 - [GitHub コードの投稿 ](https://github.com/magento/magento2/commit/9ad7d277)_

#### 入力された国 ID が存在しません – アイルランド （IE）

修正後、アイルランドの郵便番号を使用して集荷場所を検索できます。

_ACP2E-3932 - [GitHub コードの投稿 ](https://github.com/magento/magento2/commit/4ca73607) - [GitHub コードの投稿 ](https://github.com/magento/inventory/commit/d2f1d6c6)_

### カタログ、パフォーマンス

#### 管理者のカテゴリの読み込みに時間がかかる

カテゴリ読み込みパフォーマンスが大幅に向上しました。 以前は、カテゴリの読み込みに時間がかかり、タイムアウトの問題が発生していました。

_ACP2E-3891 - [GitHub コードの投稿 ](https://github.com/magento/magento2/commit/4ca73607)_

### カタログ、価格

#### 子製品に適用されたカタログ価格ルール割引が正しくありません

両方のルールの優先度が同じ場合に、バリエーションのカタログ価格ルールが親の設定可能な製品によって上書きされる問題を修正しました。

_ACP2E-3693 - [GitHub コードの投稿 ](https://github.com/magento/magento2/commit/a20a6ff2)_

### カタログ、検索

#### RestApi リクエスト &#39;/rest/default/V1/categories?searchCriteria%5Bpage_size%5D=1&#39;がタイムアウトエラーで失敗します

_AC-13358 - [GitHub コードの投稿 ](https://github.com/magento/magento2/commit/7bdafaa2)_

### コンテンツ

#### magento 2.4.7 p2 にアップグレードすると、新しくアップロードされたファイルのメディアギャラリーが表示されない

_AC-13262 - [GitHub の問題 ](https://github.com/magento/magento2/issues/39275)_

#### からギャラリー画像を完全に削除すると、範囲の役割/タイプが設定され続け（ベース/小/サムネール）、「古い」役割/タイプを再度追加した後で表示されます

システムはストア範囲で期待どおりに動作しています。画像は、デフォルトの範囲に従って、新しく追加された画像の役割/種類を継承します。

_AC-13556 - [GitHub の問題 ](https://github.com/magento/magento2/issues/39481) - [GitHub コードの投稿 ](https://github.com/magento/magento2/pull/39680)_

#### [ 小さなバグ ] フィールド値に `listing component` が含まれている場合、管理パネル `\` のフィルターがヒットしない

スラッシュを含むページタイトルをフィルタリングしている場合（例：Magento\Store）、システムは正常に動作します

_AC-13661 - [GitHub の問題 ](https://github.com/magento/magento2/issues/39513) - [GitHub コードの投稿 ](https://github.com/magento/magento2/pull/39535)_

#### 「ID が「0」のCMS ページが存在しません」というログフラッド

管理者ユーザーの作成後、および新しいページ system.log を作成する際に、システムは期待どおりに動作しています。エラーメッセージは表示されません

_AC-14254 - [GitHub の問題 ](https://github.com/magento/magento2/issues/39743) - [GitHub コードの投稿 ](https://github.com/magento/magento2/pull/39746)_

#### カタログリンクウィジェットで間違った URL が使用されている

カタログの製品リンクとカタログカテゴリリンクを追加した後、システムはウィジェットを正しく処理し、html ソースにも正しい URL が表示されるようになりました

_AC-14437 - [GitHub の問題 ](https://github.com/magento/magento2/issues/39464) - [GitHub コードの投稿 ](https://github.com/magento/magento2/pull/39710)_

#### ユーザーがウィジェット権限を持っていない場合、ページビルダーの製品コンポーネントは機能しません

修正前は、権限のないウィジェットにアクセスすると、ページで一般的なエラーが発生し、「読み込み中」のGIFが表示されていました。 修正後、モーダルウィンドウに「申し訳ありませんが、このコンテンツを表示するには権限が必要です」と表示されます。 メッセージ。

_ACP2E-3664 - [GitHub コードの投稿 ](https://github.com/magento/magento2-page-builder/commit/bd9181b6)_

#### GraphQLでページビルダー製品ウィジェットの順序が適用されない

GraphQLの「ルート」クエリ応答で、ページビルダー製品コンテンツタイプ内の正しい並べ替え順で製品が返されなかった問題を修正しました。

_ACP2E-3898 - [GitHub コードの投稿 ](https://github.com/magento/magento2-page-builder/commit/bd9181b6)_

#### ICU ライブラリバージョンによる英語以外のストアフロントでの料金表示の問題

修正後、製品価格はヘブライ語（イスラエル）ロケールで正しく表示されます。

_ACP2E-3938 - [GitHub コードの投稿 ](https://github.com/magento/magento2/commit/7accebfa)_

#### ストアコードをクリアしたデザイン設定の更新

設定キャッシュが正しく更新されないので、ストア表示コードを更新するとデザイン設定がクリアされる問題を修正しました。

_ACP2E-3941 - [GitHub コードの投稿 ](https://github.com/magento/magento2/commit/462ede94)_

### フレームワーク

#### カスタム DBトリガーでコマンド設定 :upgrade 実行中にエラーが発生しました

_AC-11487 - [GitHub の問題 ](https://github.com/magento/magento2/issues/38481)_

#### Web サイト/グループ/ストアエンティティフォームは、拡張属性に複数の値フォーム要素を使用して拡張できません

この PR により、複数値のフォーム要素から web サイト/グループ/ストアフォームにデータを送信できるようになります。

_AC-11657 - [GitHub の問題 ](https://github.com/magento/magento2/issues/24070) - [GitHub コードの投稿 ](https://github.com/magento/magento2/pull/24094)_

#### [ 問題 ] スコープリゾルバーの使用状況を削除します

この PR は、現在のストアではなく管理者 URL 設定をグローバルに解決します

_AC-11736 - [GitHub の問題 ](https://github.com/magento/magento2/issues/38566) - [GitHub コードの投稿 ](https://github.com/magento/magento2/pull/38554)_

#### デフォルトの Nginx 設定を使用したセットアップルートによるMagento バージョンの公開

現在、システムは期待どおりに動作しているので、サイトが動作しているMagentoの正確なバージョンが公開されません

_AC-13205 - [GitHub の問題 ](https://github.com/magento/magento2/issues/39227) - [GitHub コードの投稿 ](https://github.com/magento/magento2/pull/39228)_

#### [ 問題 ] 見積もりアドレスのリファクタリングと検証メソッド

この PR には、doValidate メソッドのわかりやすさの向上が含まれています。

_AC-13214 - [GitHub の問題 ](https://github.com/magento/magento2/issues/38230) - [GitHub コードの投稿 ](https://github.com/magento/magento2/pull/38219)_

#### Magento オプション —magento-init-params cli 実行時に使用しない場合は、

_AC-13231 - [GitHub の問題 ](https://github.com/magento/magento2/issues/39248) - [GitHub コードの投稿 ](https://github.com/magento/magento2/commit/132b9e68)_

#### getItemsByColumnValue の型宣言が間違っています

システムは、getItemsByColumnValue 関数で、入力パラメーター$value を配列ではなくプリミティブ型として正しく定義し、関数が期待されたコレクションを返すようになりました。 以前は、単一の値を持つ配列が入力パラメーターとして使用された場合、関数は null を返し、IDE はエラーとしてマークしていました。

_AC-13240 - [GitHub の問題 ](https://github.com/magento/magento2/issues/33070) - [GitHub コードの投稿 ](https://github.com/magento/magento2/pull/33120)_

#### Magento 2.4.7 マルチストア実装での FPC に関連付けられたキャッシュキー

_AC-13719 - [GitHub の問題 ](https://github.com/magento/magento2/issues/39456) - [GitHub コードの投稿 ](https://github.com/magento/magento2/commit/ae6f305b)_

#### PII を公開するMagento Rest API

_AC-13904 - [GitHub の問題 ](https://github.com/magento/magento2/issues/39336)_

#### 大量の更新を行っているお客様に対しては、部分的なインデックス作成が機能しなくなります

_AC-14424 - [GitHub コードの投稿 ](https://github.com/magento/magento2/commit/7bdafaa2)_

#### モジュール内で「use strict」が不要であることを調査します

_AC-14517 - [GitHub コードの投稿 ](https://github.com/magento/magento2/commit/77c589a6)_

#### 出荷ラベルをダウンロードした後、私たちはそれが出荷と取り扱い価格と一致していなかったいくつかの出荷金額を見ることができます。

_AC-14560_

#### MView の機能は、トリガーの実行時にエラーを無視します

_AC-14567 - [GitHub コードの投稿 ](https://github.com/magento/magento2/commit/ae6f305b)_

#### [ 問題 ] レイアウト XML 結合の読み込み中に、不要な例外を回避します

この PR は、読み込む新しい関数（B/C 互換では、保護された_loadXmlString を上書きしません）を導入し、例外をスローしません

_AC-14580 - [GitHub の問題 ](https://github.com/magento/magento2/issues/39877) - [GitHub コードの投稿 ](https://github.com/magento/magento2/pull/37570)_

#### [ 問題 ]Vault Graph Ql モジュールでコンストラクタープロパティのプロモーションを使用する

この PR は、コンストラクタープロパティを VaultGraphQl モジュールのプロパティプロモーションに置き換えます

_AC-14616 - [GitHub の問題 ](https://github.com/magento/magento2/issues/39900) - [GitHub コードの投稿 ](https://github.com/magento/magento2/pull/36996)_

#### [ 問題 ] モジュールフロントエンドレイアウトのコード冗長性を削除しました。

この PR により、Magento_Msrp、Magento_LoginAsCustomerAssistance、Magento_Newsletter およびMagento_Sitemap モジュールのフロントエンドレイアウトのテーマレイアウトに対するコードの冗長性が解消されます。

_AC-14625 - [GitHub の問題 ](https://github.com/magento/magento2/issues/30673) - [GitHub コードの投稿 ](https://github.com/magento/magento2/pull/30644)_

#### [ 問題 ]Microsoft IIS に関連するコードを削除します

この PR により、Microsoft Windows OS がサポートされていないことを示すMagento システム要件ドキュメントに従って、Mircrosoft IIS に関連するコードがクリーンアップされます

_AC-14702 - [GitHub の問題 ](https://github.com/magento/magento2/issues/39910) - [GitHub コードの投稿 ](https://github.com/magento/magento2/pull/39894)_

#### Magnifier.js 構文エラー

システムの拡大鏡機能は、以前と同じように機能し続ける必要があります。また、拡大鏡オプションはグローバル スコープで使用できません

_AC-14722 - [GitHub の問題 ](https://github.com/magento/magento2/issues/36200) - [GitHub コードの投稿 ](https://github.com/magento/magento2/pull/39321)_

#### CLI コマンドのバックポ `setup:db:status` ト詳細モード

_AC-14807 - [GitHub コードの投稿 ](https://github.com/magento/magento2/commit/7bdafaa2)_

#### tls および 2.4.8 で送信される SMTP メール

_AC-14883 - [GitHub の問題 ](https://github.com/magento/magento2/issues/39947) - [GitHub コードの投稿 ](https://github.com/magento/magento2/commit/3717e6cb) - [GitHub コードの投稿 ](https://github.com/magento/magento2/commit/8b453942) - [GitHub コードの投稿 ](https://github.com/magento/magento2/commit/d3ea191d)_

#### [ 問題 ] 静的コンテンツのデプロイにおける同時実行の問題を修正しました

この PR は、テーマが親と共にどのように定義されているかに応じて、複数の同時プロセスがスピンして同じテーマパッケージを処理するバグを修正します。

_AC-14944 - [GitHub の問題 ](https://github.com/magento/magento2/issues/39990) - [GitHub コードの投稿 ](https://github.com/magento/magento2/pull/39954)_

#### [ 問題 ] 8.1 より前のバージョンの PHP のレガシー互換性コードを削除する

このプルリクエストは、PHP &lt;8.1 で実行するように設計されたコードを削除します。
また、PHP_VERSION_ID の連絡先が利用可能かどうかをチェックする機能を削除しました。これは全ての PHP バージョンで利用可能です

_AC-14971 - [GitHub の問題 ](https://github.com/magento/magento2/issues/39891) - [GitHub コードの投稿 ](https://github.com/magento/magento2/pull/39882)_

#### ログイン時に FPC が機能しない

_AC-14999 - [GitHub の問題 ](https://github.com/magento/magento2/issues/40007) - [GitHub コードの投稿 ](https://github.com/magento/magento2/commit/)_

#### [ 問題 ]SchemaBuilder のエラー処理を改善する

この PR により、db スキーマのエラーメッセージ処理が改善されます。 大量のデバッグを行わずに問題を特定するのに役立ちます。

_AC-15020 - [GitHub の問題 ](https://github.com/magento/magento2/issues/39816) - [GitHub コードの投稿 ](https://github.com/magento/magento2/pull/39799)_

#### CliStateTest の変更による 2.4.9-alpha2-develop の SYNC PR での統合テストの失敗

_AC-15136 - [GitHub コードの投稿 ](https://github.com/magento/magento2/commit/2d0f8066)_

#### PHP8.1 タイプのバグ修正

関連する製品は、厳密な処理モードがアクティブでない場合や製品情報が使用可能な場合、false ではなく空の配列に初期化されるようになりました。 この変更により、関連する製品を処理する後続のロジックが一貫して動作し、製品準備プロセスの安定性と予測可能性が向上します。

_AC-6017 - [GitHub の問題 ](https://github.com/magento/magento2/issues/35808) - [GitHub コードの投稿 ](https://github.com/magento/magento2/pull/35842)_

#### [ 問題 ] フレームワークから禁止されている `@author` タグを削除する（パート 3）

システムは、特定のモジュールから禁止されている `@author` タグを削除することで、コーディング標準に準拠するようになり、全体的なコード品質が向上します。 以前は、一部のモジュールにこのタグが含まれていることは、確立されたコーディング標準に違反していました。

_AC-8343 - [GitHub の問題 ](https://github.com/magento/magento2/issues/37270) - [GitHub コードの投稿 ](https://github.com/magento/magento2/pull/37020)_

#### [ 問題 ] 友人グラフ ql を送信モジュールでコンストラクタープロパティのプロモーションを使用する

「友達に送信」GraphQLモジュールのコンストラクタープロパティの昇格を利用して、コードの読みやすさを向上し、複雑さを軽減するようになりました。 以前は、このモジュールは、多数の行を占めるプロパティを使用していたので、コードがより複雑で読みにくくなっていました。

_AC-8346 - [GitHub の問題 ](https://github.com/magento/magento2/issues/37235) - [GitHub コードの投稿 ](https://github.com/magento/magento2/pull/37197)_

#### [ 問題 ] `@author` から禁止されている `Magento_Downloadable` タグを削除する

システムは、特定のモジュールから禁止されている `@author` タグを削除することで、コーディング標準に準拠するようになり、全体的なコード品質が向上します。 以前は、一部のモジュールにこのタグが含まれていることは、確立されたコーディング標準に違反していました。

_AC-8355 - [GitHub の問題 ](https://github.com/magento/magento2/issues/37251) - [GitHub コードの投稿 ](https://github.com/magento/magento2/pull/37001)_

#### [ 問題 ] 禁止された `@author` タグを削除する

このシステムは、特定のモジュールから禁止されている `@author` タグを削除することで、コーディング標準に準拠するようになり、コードの品質と一貫性を向上させます。 以前は、一部のモジュールにこのタグが含まれていることは、確立されたコーディング標準に違反していました。

_AC-8358 - [GitHub の問題 ](https://github.com/magento/magento2/issues/37264) - [GitHub コードの投稿 ](https://github.com/magento/magento2/pull/37014)_

#### [ 問題 ] 禁止された `@author` タグを削除する

システムは、特定のモジュールから禁止されている `@author` タグを削除することで、コーディング標準に準拠するようになり、全体的なコード品質を向上させます。 以前は、一部のモジュールにこのタグが含まれていることは、確立されたコーディング標準に違反していました。

_AC-8360 - [GitHub の問題 ](https://github.com/magento/magento2/issues/37261) - [GitHub コードの投稿 ](https://github.com/magento/magento2/pull/37011)_

#### [ 問題 ] 禁止された `@author` タグを削除する

このシステムは、特定のモジュールから禁止されている `@author` タグを削除することで、コーディング標準に準拠するようになり、よりクリーンで標準化されたコードを保証します。 以前は、一部のモジュールにこのタグが含まれていることは、確立されたコーディング標準に違反していました。

_AC-8361 - [GitHub の問題 ](https://github.com/magento/magento2/issues/37260) - [GitHub コードの投稿 ](https://github.com/magento/magento2/pull/37010)_

#### [ 問題 ] 禁止された `@author` タグを削除する

システムは、特定のモジュールから禁止されている `@author` タグを削除することで、コーディング標準に準拠するようになり、全体的なコード品質が向上します。 以前は、一部のモジュールにこのタグが含まれていることは、確立されたコーディング標準に違反していました。

_AC-8363 - [GitHub の問題 ](https://github.com/magento/magento2/issues/37258) - [GitHub コードの投稿 ](https://github.com/magento/magento2/pull/37008)_

#### [ 問題 ] 禁止された `@author` タグを削除する

システムは、特定のモジュールから禁止されている `@author` タグを削除することで、コーディング標準に準拠するようになり、全体的なコード品質が向上します。 以前は、一部のモジュールにこのタグが含まれていることは、確立されたコーディング標準に違反していました。

_AC-8375 - [GitHub の問題 ](https://github.com/magento/magento2/issues/37257) - [GitHub コードの投稿 ](https://github.com/magento/magento2/pull/37007)_

#### [ 問題 ] 禁止された `@author` タグを削除する

システムは、特定のモジュールから禁止されている `@author` タグを削除することで、コーディング標準に準拠するようになり、全体的なコード品質が向上します。 以前は、一部のモジュールにこのタグが含まれていることは、確立されたコーディング標準に違反していました。

_AC-8376 - [GitHub の問題 ](https://github.com/magento/magento2/issues/37256) - [GitHub コードの投稿 ](https://github.com/magento/magento2/pull/37006)_

#### [ 問題 ] 禁止された `@author` タグを削除する

システムは、特定のモジュールから禁止されている `@author` タグを削除することで、コーディング標準に準拠するようになり、全体的なコード品質が向上します。 以前は、一部のモジュールにこのタグが含まれていることは、確立されたコーディング標準に違反していました。

_AC-8400 - [GitHub の問題 ](https://github.com/magento/magento2/issues/37254) - [GitHub コードの投稿 ](https://github.com/magento/magento2/pull/37004)_

#### [ 問題 ] 禁止された `@author` タグを削除する

システムは、特定のモジュールから禁止されている `@author` タグを削除することで、コーディング標準に準拠するようになり、全体的なコード品質が向上します。 以前は、一部のモジュールにこのタグが含まれていることは、確立されたコーディング標準に違反していました。

_AC-8401 - [GitHub の問題 ](https://github.com/magento/magento2/issues/37255) - [GitHub コードの投稿 ](https://github.com/magento/magento2/pull/37005)_

#### [ 問題 ] サービス URL 生成の拡張性を向上させる

プラグインを使用してサービス URL 生成機能をカスタマイズできるようになり、メンテナンス性の高い変更アプローチが促進されます。 以前は、この機能のカスタマイズは、環境設定を通じて実現されていましたが、これはそれほど効率的でも保守的でもないかもしれません。

_AC-8813 - [GitHub の問題 ](https://github.com/magento/magento2/issues/37404) - [GitHub コードの投稿 ](https://github.com/magento/magento2/pull/37403)_

#### 新しい検証が追加されたことによるアップグレード 2.4.7-p5 の問題

SchemaBuilder クラスで、未定義の配列キー「列」がスキーマの作成中または更新中にクラッシュする問題を修正しました。 これは、「列」キーを含まないテーブルデータを処理しているときに発生しました。

_ACP2E-3871 - [GitHub コードの投稿 ](https://github.com/magento/magento2/commit/9ad7d277)_

#### PHP8.4 非推奨エラー：Adobe Commerce 2.4.8 へのアップグレード後の E_USER_ERROR

お客様が直面するシナリオは、この修正の影響を受けません。

_ACP2E-3963 - [GitHub コードの投稿 ](https://github.com/magento/magento2/commit/7accebfa)_

### フレームワーク、検索

#### Opensearch 2.19.1 は、1 つの価格のカテゴリに対して illegal_argument_exception を返します。

Opensearch は、同じ価格を持つすべての製品を含むカテゴリに対して illegal_argument_exception をスローしなくなりました。 以前は、「[from] パラメーターは負にできません」という例外がありました。

_ACP2E-3896 - [GitHub コードの投稿 ](https://github.com/magento/magento2/commit/3ad96f6a)_

### GraphQL

#### 製品が削除されると customerOrders graphql がエラーを返す

注文の製品が削除されても、customerOrders の graphql リクエストでエラーがスローされなくなりました。 以前は、「内部サーバーエラー」エラーがスローされていました。

_ACP2E-3936_

#### ウィッシュリスト項目は、GraphQL リクエストの 1 つの web サイト内のストアビュー間で共有されません

修正する前は、ウィッシュリストの項目はストア ID でフィルタリングされていました。 修正後、ウィッシュリストの項目が web サイトでフィルタリングされるようになりました。

_ACP2E-3987 - [GitHub コードの投稿 ](https://github.com/magento/magento2/commit/2a252ae6)_

### GraphQL、商品

#### 製品 graphql の MediaGalleryInterface に media_type がありません

MediaGallery GraphQL リクエストに、商品の画像タイプの「タイプ」フィールドが含まれるようになりました。 以前は、この「types」フィールドは MediaGallery GraphQL リクエストに存在しませんでした。

_ACP2E-3880 - [GitHub コードの投稿 ](https://github.com/magento/magento2/commit/3ad96f6a)_

### インベントリ/MSI

#### ホームページにリダイレクトしてチェックアウトした後は、利用できるストアはありません

以前に選択したストアは、お客様が支払いページに移動してからホームページに戻り、最後にチェックアウトページに戻った場合、「店舗で選択」配送で事前選択されるようになりました。 以前は、チェックアウトページに繰り返し戻った後に、「店舗で選択」で選択した店舗がクリアされていました。

_ACP2E-3793 - [GitHub コードの投稿 ](https://github.com/magento/magento2/commit/a20a6ff2) - [GitHub コードの投稿 ](https://github.com/magento/inventory/commit/62c0d79b)_

### 順序

#### AbstractAddress setData （&#39;custom_attributes&#39;, AttributeValue[]）は customAttributes を解除します

_AC-10568 - [GitHub の問題 ](https://github.com/magento/magento2/issues/31644)_

#### v2.4.7-p1 Magentoの並べ替え–1 の注文番号

システムは期待どおりに動作しており、バックエンドから並べ替えた後、注文番号は一意の 8 桁になります

_AC-12854 - [GitHub の問題 ](https://github.com/magento/magento2/issues/39089) - [GitHub コードの投稿 ](https://github.com/magento/magento2/pull/39399)_

#### Adobeのクレジットカードによるお支払い方法でチェックアウトすると、商品のカスタムオプションファイルのアップロードが失われる

_AC-14306 - [GitHub の問題 ](https://github.com/magento/magento2/issues/39647)_

#### 処理中に注文ステータスがスタックしました

修正前は、「一緒に出荷」オプションが有効になっているバンドル製品を注文しても、請求書と出荷後に注文ステータスが自動的に「完了」に切り替わっていませんでした。 現在は、修正後、注文が請求および出荷された後、注文ステータスが自動的に「完了」に切り替わります。

_ACP2E-3947 - [GitHub コードの投稿 ](https://github.com/magento/magento2/commit/2a252ae6)_

#### [Cloud]Magento OOTB コード – メールテンプレートの設定の問題

修正前は、非同期メール送信を使用する場合、出荷メールとストアオーダーが一致していませんでした。 修正後、適切な店舗出荷メール注文が配信されます。

_ACP2E-3998 - [GitHub コードの投稿 ](https://github.com/magento/magento2/commit/462ede94)_

### その他の開発者ツール

#### [ 問題 ] 保護されたメンバー$_urlHelper の間違ったタイプヒント

システムは、誤ったタイプヒントを正しいヒントで修正するようになりました。これは、コンストラクターでも使用されます

_AC-10716 - [GitHub の問題 ](https://github.com/magento/magento2/issues/32503) - [GitHub コードの投稿 ](https://github.com/magento/magento2/pull/32496)_

### パフォーマンス

#### [ 問題 ] Store.php の更新

この PR は、現在のストアの解決をスキップすることでパフォーマンスを向上させます。

_AC-14791 - [GitHub の問題 ](https://github.com/magento/magento2/issues/39949) - [GitHub コードの投稿 ](https://github.com/magento/magento2/pull/38717)_

### Pricing

#### Rest API 注文の動的価格なしのバンドル製品項目の場合、価格は常に 0 です

_AC-11925 - [GitHub の問題 ](https://github.com/magento/magento2/issues/38687) - [GitHub コードの投稿 ](https://github.com/magento/magento2/commit/7da46f52)_

### 製品

#### オプションを選択せずに、元の価格に基づいて計算された、階層価格およびカタログ価格ルールに対する割引率。

_AC-12004 - [GitHub の問題 ](https://github.com/magento/magento2/issues/38750)_

#### Magento 2.4.7 minAllowed missing product order qty

システムは正常に動作し、ページソースは製品の最小数量を正しく表示している

_AC-12909 - [GitHub の問題 ](https://github.com/magento/magento2/issues/39142) - [GitHub コードの投稿 ](https://github.com/magento/magento2/pull/39480)_

#### Magento Payflow Pro テストの実行中にMagento例外が発生しました

_AC-13681_

#### 管理パネルの製品ページのカスタマイズ可能オプショングリッドに関する問題

タイプがドロップダウンのカスタマイズ可能なオプションを作成する場合、システムは期待どおりに動作します

_AC-14003 - [GitHub の問題 ](https://github.com/magento/magento2/issues/39640) - [GitHub コードの投稿 ](https://github.com/magento/magento2/pull/39694)_

#### 購買依頼リスト・ページ印刷オプションが機能しない

_AC-14711_

#### 他の顧客比較リストのすべての項目は、管理者を介してログインした後、顧客に割り当てられます

以前は、管理者がバックエンドで「顧客としてログイン」機能を使用すると、以前にログインした顧客の比較リストの製品が、現在なりすまされている顧客に誤って割り当てられました。  修正後、正しくログインしている顧客の比較リストが正しく読み込まれます。

_ACP2E-3818 - [GitHub コードの投稿 ](https://github.com/magento/magento2/commit/462ede94)_

### SEO

#### REST API を使用した製品の URL キーの更新で、301 URL の書き換えが生成されない

「URL キーが変更された場合に URL の永続的なリダイレクトを作成」設定を「はい」に設定して、REST API を介して製品の URL キーを更新する場合、製品 URL の書き換えは、古い URL から新しい URL へのリダイレクトを作成します。

_ACP2E-3900 - [GitHub コードの投稿 ](https://github.com/magento/magento2/commit/462ede94)_

### 売上

#### 注文状態ドロップダウンで値を選択すると、注文状態が表示されなくなります

_AC-15010_

### セキュリティ

#### バンドルまたは結合された JS が SRI ハッシュの一部ではない

修正前は、生成されたバンドルまたは結合ファイルが SRI ハッシュリストに追加されていませんでした。 現在、ファイルは SRI ハッシュに適切に追加されています。

_ACP2E-3854 - [GitHub コードの投稿 ](https://github.com/magento/magento2/commit/4ca73607)_

### 送料

#### [QUANS] - Magento_Fedex コアモジュールは、新しいトークンを取得するリクエストを送信する前に、有効なアクティブなトークンを確認しますか？

Adobe Commerceは、アクセストークンに対して FedEx API サービスへのリクエストを多数行わなくなりました。 以前は、アクセストークンがまだ有効でも、Adobe Commerceは常に FedEx API に新しいリクエストを行うので、レート制限の問題が発生していました。

_ACP2E-3930 - [GitHub コードの投稿 ](https://github.com/magento/magento2/commit/4ca73607)_

### ステージングとプレビュー

#### カテゴリ権限が有効になっているスケジュールされた製品アップデートをプレビューできない

修正前は、今後も有効になる製品がプレビューモードで表示されていませんでした。 現在のステータスが無効な場合でも表示されるようになりました。

_ACP2E-3786 - [GitHub コードの投稿 ](https://github.com/magento/magento2/commit/7accebfa)_

#### プレビュー中、スコープに異なるストア表示が表示される

修正前に、cms ブロックと cms ページのコンテンツのステージング更新プレビューが、コンテンツのステージングダッシュボードからアクセスしたときに cms ブロックまたはページに割り当てられたストアとは別のストアで開いていた可能性があります。 修正後、ステージング更新で cms ブロックまたはページに特定のストアのみが割り当てられている場合、コンテンツのステージングダッシュボードからのプレビューが開いて、正しいストアが選択されます。

_ACP2E-3815_

#### カタログ価格ルール割引金額フィールドの検証がありません

以前は、ステージングスケジュールの更新の discount_amount フィールドが、現在の検証ルールで正しく検証されていませんでした。 ただし、修正を適用すると、discount_amount フィールドは適切に検証されます。

_ACP2E-3867 - [GitHub コードの投稿 ](https://github.com/magento/magento2/commit/462ede94)_

### 税

#### 注文の合計が正しくない場合、ラウンドは価格計算に適用されません。

price_after_discount、discount_amount、および tax の金額を計算する際に、システムが正しく処理するようになりました。
注文の実際の合計

_AC-11389 - [GitHub の問題 ](https://github.com/magento/magento2/issues/38455) - [GitHub コードの投稿 ](https://github.com/magento/magento2/pull/39687)_

### テストフレームワーク

#### [ 問題 ] lib/internal/Magento/Framework/App/Test/Unit/_files/app/etc/en...

単体テストの実行時に生成されるファイル「env.php」が無視されるようになり、テストの実行後も Git のステータスがクリーンなままになります。 以前は、単体テストを実行すると新しいファイル「env.php」が生成され、git ステータスに新しいファイルが見つかり、ダーティに見えるようになりました。

_AC-13293 - [GitHub の問題 ](https://github.com/magento/magento2/issues/39304) - [GitHub コードの投稿 ](https://github.com/magento/magento2/pull/37631)_

#### [ 問題 ] インターセプターの統合テストの問題を修正しました

統合テストで\Magento\TestFramework\App\Config\Interceptorが正しく識別および処理されるようになりました。これにより、クラスにプラグインが存在する場合でもテストで必要なデータにアクセスできるようになります。 以前は、システムは\Magento\TestFramework\App\Configが\Magento\TestFramework\App\Config\Interceptorである可能性を考慮に入れることができず、$data プロパティにアクセスしようとするとエラーが発生していました。

_AC-13305 - [GitHub の問題 ](https://github.com/magento/magento2/issues/39324) - [GitHub コードの投稿 ](https://github.com/magento/magento2/pull/37187)_

#### [ 問題 ] MFTF:Captcha が有効な友達フォームにメールを送信する

テストケースでは、CAPTCHA が有効な場合の「Email to Friend」フォームの機能について説明し、間違った CAPTCHA 値と正しい CAPTCHA 値の両方でフォーム送信プロセスが正しく動作することを確認します。

_AC-13492 - [GitHub の問題 ](https://github.com/magento/magento2/issues/39462) - [GitHub コードの投稿 ](https://github.com/magento/magento2/pull/32830)_

#### [TestFramework] phpunit v10 以降の TestCase::getTestResultObject の使用は無効です

_AC-13502 - [GitHub の問題 ](https://github.com/magento/magento2/issues/39463)_

#### AC 2.4.7-p3 での環境固有の単体テストの失敗

この問題は、すべてのバージョンと環境で再現されない単体テストのエラーを修正します。 以前は、修正するために、ライブラリバージョンが異なったり、新しいバージョンで追加された機能が欠落していたりしたために、一部の単体テストが失敗していました。

_ACP2E-3712 - [GitHub コードの投稿 ](https://github.com/magento/magento2/commit/9ad7d277)_

### ツール/DataMigrationTool

#### [ATLH] 違いがない場合の致命的エラー

表示する違いがない場合に、致命的なエラーが表示されなくなった

_ACP2E-3901_

### UI フレームワーク

#### 動的行のWYSIWYGが空です

_AC-12336 - [GitHub の問題 ](https://github.com/magento/magento2/issues/38893) - [GitHub コードの投稿 ](https://github.com/magento/magento2/commit/7bdafaa2)_

#### [ 問題 ] MIME タイプタイプの修正

システムは、gif 画像の MIME タイプとタイプミスを正しく処理して修正しました

_AC-8001 - [GitHub の問題 ](https://github.com/magento/magento2/issues/36899) - [GitHub コードの投稿 ](https://github.com/magento/magento2/pull/36669)_

#### [ 問題 ] レビューリストの Ajax に直接アクセスできないようにする

システムは Ajax を正しく処理し、レビューリストへの直接アクセスを避けます

_AC-9381 - [GitHub の問題 ](https://github.com/magento/magento2/issues/37920) - [GitHub コードの投稿 ](https://github.com/magento/magento2/pull/33876)_

### アップグレード：互換性アップグレードツール

#### 非推奨（廃止予定）の機能：動的プロパティ Magento\Framework\Acl::$_roleRegistry の作成

_AC-12343 - [GitHub の問題 ](https://github.com/magento/magento2/issues/37469)_
