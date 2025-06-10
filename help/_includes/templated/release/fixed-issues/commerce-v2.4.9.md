---
source-git-commit: 21da8a0133c3c70c2c37851aca79e2d5d8f82905
workflow-type: tm+mt
source-wordcount: '3327'
ht-degree: 0%

---
# Adobe Commerceで修正された問題（v2.4.9）

## v2.4.9 で修正された問題

Adobe Commerce 2.4.9 コアコードの 84 の問題を修正しました。 このリリースで修正された問題の一部を以下に示します。

### API

* __async.magento.configurableproduct.api.optionrepositoryinterface.save.post の非同期一括操作はオープン状態のままです__
リクエスト本文が配列でない場合、Bulk API エンドポイントはエラーをスローするようになりました。そのため、一括項目キーは 0 から始まる連続数である必要があります。 以前は、一括要求で送信された任意の項目キーが原因で、一括項目ステータスが更新されませんでした。
  _ACP2E-3544 - [GitHub コードの投稿 ](<https://github.com/magento/magento2/commit/9608ca21>)_
* __[CLOUD] is_subscribed 値に関する API REST のバグで、searchCriteria を使用して現在のストアから考慮されていないもの__
API REST カスタマークエリは、searchCriteria を使用して、正しいストアから正しい「is_subscribed」値を取得します
以前は、API REST カスタマークエリは、is_subscribed&quot;値を取得する際に保存を考慮していませんでした。
  _ACP2E-3621 - [GitHub コードの投稿 ](<https://github.com/magento/magento2/commit/9608ca21>)_
* __async.operations.all は、1 つの SKU に対して複数のエントリを作成できます__
同じ製品を保存および更新する同時リクエストがシリアル化され、データの不整合や製品の重複を引き起こす競合状態を防ぎます
  _ACP2E-3744 - [GitHub コードの投稿 ](<https://github.com/magento/magento2/commit/520f9e30>)_

### アカウント

* __[クラウド ] 顧客アカウントの作成中に現在のエリアで発生したエラーに対して、削除操作は禁止されています__
修正によって無効なアドレスで顧客を保存すると、無関係な「現在のエリアでは削除操作が禁止されています」ではなく、無効の理由を説明するメッセージが返されます。
  _ACP2E-3791 - [GitHub コードの投稿 ](<https://github.com/magento/magento2/commit/6ea61121>)_

### 管理 UI

* __[問題 ] 役割ツリーによるユーザーエクスペリエンスの向上__
このプルリクエストでは、すべてを折りたたむ、すべてを展開する、選択した項目で分岐を展開するボタンが追加されます。 この機能は、カテゴリツリーで提供される機能（カタログ/在庫/カテゴリ）と同様です
  _AC-14020 - [GitHub の問題 ](https://github.com/magento/magento2/issues/39654) - [GitHub コードの投稿 ](<https://github.com/magento/magento2/pull/36511>)_
* __Symfony\Component\Mime\Exception\LogicException: 「Sender」ヘッダーは、「Symfony\Component\Mime\Header\MailboxHeader」のインスタンスである必要があります（「Symfony\Component\Mime\Header\MailboxListHeader」を取得）__
  _AC-14520 - [GitHub の問題 ](https://github.com/magento/magento2/issues/39823) - [GitHub コードの投稿 ](<https://github.com/magento/magento2/commit/1e14bd72>) - [GitHub コードの投稿 ](<https://github.com/magento/magento2/commit/1514117f>)_
* __グリッドを使用して税率を一括削除する機能の提供__
管理者ユーザーは、「管理税率」グリッドから複数の税率を同時に削除できるようになりました。  [GitHub-33399](https://github.com/magento/magento2/issues/33399)
  _AC-2238 - [GitHub の問題 ](https://github.com/magento/magento2/issues/33399) - [GitHub コードの投稿 ](<https://github.com/magento/magento2/pull/33484>) - [GitHub コードの投稿 ](<https://github.com/magento/magento2/commit/5cd64dd0>)_
* __条件 SKU を含む買い物かご価格ルールで、SKU の「先頭のゼロ」が考慮されない（SKU:01234 は 1234 と同じ）__
システムでは、SKU の「先頭のゼロ」を考慮した条件 SKU を使用して、買い物かご価格ルールを正しく処理するようになりました
  _AC-9428 - [GitHub の問題 ](https://github.com/magento/magento2/issues/37919) - [GitHub コードの投稿 ](<https://github.com/magento/magento2/pull/39525>)_
* __複数選択のデフォルト属性オプション値の動作の問題__
修正前は、複数のオプション属性のデフォルト値が正しく保存されていませんでした。 修正後、値はデータベースに適切に保存されるようになりました。
  _ACP2E-3523 - [GitHub コードの投稿 ](<https://github.com/magento/magento2/commit/9608ca21>)_
* __バックエンド管理メニューのサブタイトルが表示されない__
メインメニューグループのすべてのタイトルが正しく表示されるようになりました。 以前は、メインメニューの 2 列目または 3 列目にリンクのグループが 1 つしか含まれていない場合、そのグループのタイトルは表示されませんでした。
  _ACP2E-3540_
* __製品数量を管理者から買い物かごに戻す際の問題__
管理者から注文を作成する場合、サイドバー上の顧客カート内の製品が注文に追加されても消えません。
  _ACP2E-3563 - [GitHub コードの投稿 ](<https://github.com/magento/magento2/commit/c8ba4ab1>)_

### 管理 UI、B2B

* __B2B Login as Customer ヘッダーには、引き続きMagento ブランディングがあります__
以前は、ストアフロントのヘッダーに、「現在、&lt; ストア名 > で &lt; 顧客名 > として接続されています」とMagento ブランディングが表示されていました。 （修正）と、ヘッダーがADOBE ブランディングで表示されるようになりました。
  _AC-14361 - [GitHub コードの投稿 ](<https://github.com/magento/magento2/commit/fadcfa8b>)_

### 管理 UI、コンテンツ

* __画像の挿入中に「メディアアセットパスのレンディションを作成できません」例外が発生する__
Media Gallery 画像の最適化設定の最大幅と最大高さの値を削除すると、画像の最適化処理中にエラーが発生しなくなりました。
  _ACP2E-3781 - [GitHub コードの投稿 ](<https://github.com/magento/magento2/commit/520f9e30>)_

### 管理 UI、セキュリティ

* __脆弱なパスワード管理__
同じパスワードを使用する場合、管理者ユーザーを保存できません。 以前は、適切な検証なしで正常に保存されていました。
  _ACP2E-3657 - [GitHub コードの投稿 ](<https://github.com/magento/magento2/commit/df92debe>)_

### 管理 UI、セキュリティ、ステージングおよびプレビュー

* __コンテンツのステージングのアクションログ__
アクションログに、ステージング更新アクティビティが表示されるようになりました。 以前は、ステージング更新ログは管理アクションログに記録されていませんでした。
  _ACP2E-3679_

### B2B

* __注文場所が機能していません PayFlow Pro クレジットカードによる交渉できる見積もりからチェックアウトに進んでください__
  _AC-11973_
* __引用符の名前を変更した後、成功メッセージが断続的に消える__
  _AC-13447_
* __総計の計算には税額は含まれません__
注文に正しい合計が含まれているのは、クロスボーダー取引が有効な既存の発注書から注文が作成される場合です。
  _ACP2E-3727_
* __REST API を使用した B2B 共有カタログのカテゴリの割り当て解除が遅い__
B2B でカテゴリの割り当てを解除する際のパフォーマンスが大幅に向上しました。 以前は、B2B 共有カタログのカテゴリの割り当てを解除するのに長い時間がかかっていました。
  _ACP2E-3796_
* __B2B の新しいセットアップパッチに関するパフォーマンスの問題__
B2B 1.5.2 にアップデートした後にMagento_Company モジュールをアップグレードすると、company_structure テーブル内の多数のレコード（～100,000）を処理する際に非常に長い時間がかかるパフォーマンスの問題を修正しました。
  _ACP2E-3850_

### 買い物かごとチェックアウト

* __Magento 2.4.7 更新（ミニ）買い物かご 10 進数の数量は許可されていません__
ロケールが NL （オランダ語）の場合に、ミニカートの小数を使用して数量を更新する際に、Magentoが正しく処理するようになりました
  _AC-13238 - [GitHub の問題 ](https://github.com/magento/magento2/issues/39236) - [GitHub コードの投稿 ](<https://github.com/magento/magento2/pull/39669>)_
* __[問題 ]subtotal.phtml の更新__
正しい間隔で subtotal.phtml が更新されます
  _AC-13907 - [GitHub の問題 ](https://github.com/magento/magento2/issues/39619) - [GitHub コードの投稿 ](<https://github.com/magento/magento2/pull/39612>)_
* __ゲストと注文できません__
  _AC-14241 - [GitHub コードの投稿 ](<https://github.com/magento/magento2/commit/27217d0e>)_
* __期限切れの永続的な見積は、cron ジョブ sales_clean_quotes によってクリーンアップされません__
「persistent_clear_expired」 cron ジョブが実行されると、期限切れの永続的な引用符がクリアされるようになりました。 以前は、期限切れの永続的な引用符が他の cron ジョブでクリアされていませんでした。
  _ACP2E-3493 - [GitHub コードの投稿 ](<https://github.com/magento/magento2/commit/11be3dff>)_
* __非アクティブな会社のチェックアウトで「エラーが発生しました」エラーが発生する__
修正を行う前は、ログアウトアクションは買い物かごページで適切に完了していませんでした（長い間ログインしていたユーザー会社が有効でなくなった場合）。 これで、会社が利用できなくなった場合、ログアウトは正しく実行されます。
  _ACP2E-3541 - [GitHub コードの投稿 ](<https://github.com/magento/magento2/commit/df92debe>)_
* __「複数のアドレスでチェックアウト」すると、アドレス選択が保存されない__
複数出荷オプションをキャンセルする場合の修正の前は、複数出荷に戻しても、住所は事前に選択されていませんでした。 現在は、デフォルトのアドレスが、複数出荷画面内で選択したアドレスに置き換えられます。
  _ACP2E-3646 - [GitHub コードの投稿 ](<https://github.com/magento/magento2/commit/6ea61121>)_

### 買い物かごとチェックアウト、SEO

* __セカンダリ web サイトから購入した際に、メール内のギフトカードコード URL が正しくない__
以前は、デフォルト以外のストアのマルチストア設定とギフトカードは、常にギフトカードの請求をデフォルトの web サイトにリダイレクトしていました。 この修正が適用されると、メールによって、ギフトカードの請求リンクが正しい範囲または web サイトにリダイレクトされます。
  _ACP2E-3699_

### カートとチェックアウト、送料

* __[メインライン ] 買い物かご価格ルールが複数出荷を尊重していません__
この修正を実装する前は、サブ選択条件が適用され、送料無料が有効になっている場合、複数配送商品の買い物かご価格ルールが正しく適用されませんでした。 ただし、修正が適用されたので、複数出荷カートのカート価格ルールが意図したとおりに機能するようになりました。
  _ACP2E-3666 - [GitHub コードの投稿 ](<https://github.com/magento/magento2/commit/b12ffe36>)_

### カタログ

* __同じクエリの同じページに対してキャッシュ fpc を複製__
同じクエリパラメーターを持つページに対して、ページの順序や末尾の文字に関係なく、同じフルページキャッシュ（FPC）が正しく識別され、使用されるようになりました。 これにより、ページキャッシュフォルダーのサイズが不必要に大きくなるのを防ぎます。 以前は、クエリパラメーターの順序が異なる場合や、末尾に文字がある場合は、同じページに対して異なる FPC 識別子が作成され、ページキャッシュフォルダーのサイズが増えていました。
  _AC-10722 - [GitHub の問題 ](https://github.com/magento/magento2/issues/38269) - [GitHub コードの投稿 ](<https://github.com/magento/magento2/pull/38270>)_
* __catalog_product_entity_int テーブルに必要な列のインデックスがありません__
catalog_product_entity_int テーブルに必要な列の欠落しているインデックスを追加しました
  _AC-10844 - [GitHub の問題 ](https://github.com/magento/magento2/issues/38315) - [GitHub コードの投稿 ](<https://github.com/magento/magento2/pull/38316>)_
* __URL の書き換えが原因で製品ページがエラーになる__
URL の書き換えがあった場合に、製品ページが正常に読み込まれるようになりました
  _AC-2950 - [GitHub の問題 ](https://github.com/magento/magento2/issues/35371) - [GitHub コードの投稿 ](<https://github.com/magento/magento2/pull/39670>)_
* __[Cloud] カテゴリに製品を追加する際のバグ__
ポップアップグリッドを使用してカテゴリに製品を追加する際に、ページネーションとレコード数のラベルが正しく機能するようになりました。 以前は、ページサイズと等しい項目を持つ単一ページのみを読み込むと、項目選択ドロップダウンで問題が発生していました。
  _ACP2E-3526_
* __indexer_update_all_views MAGE_INDEXER_THREADS_COUNT__ の cron エラー
カスタマーセグメントインデクサーを使用した MAGE_INDEXER_THREADS_COUNT > 2 の問題を修正しました
  _ACP2E-3538 - [GitHub コードの投稿 ](<https://github.com/magento/magento2/commit/9608ca21>)_
* __ページビルダー製品ウィジェットの条件で「条件の組み合わせ」を追加する際の例外__
この問題は、欠落条件や不完全な条件をスキップするチェックを追加することで修正されました。 以前は、これにより、システム内の不完全な条件の処理が原因でエラーログが生成されていました。
  _ACP2E-3545 - [GitHub コードの投稿 ](<https://github.com/magento/magento2/commit/11be3dff>)_
* __属性セットを読み込むとブラウザーがクラッシュする__
4k を超える製品属性がある場合に、属性セットの編集ページでブラウザーがクラッシュしなくなりました
  _ACP2E-3633 - [GitHub の問題 ](https://github.com/magento/magento2/issues/38810) - [GitHub コードの投稿 ](<https://github.com/magento/magento2/commit/b12ffe36>)_
* __[CLOUD] 新しいストアの製品 URL 書き換えが作成されない：運用開始ブロッカー__
新しいストアの製品 URL の書き換えが正常に作成されました。
以前の操作は、メモリリークまたはタイムアウトで終了しました。
  _ACP2E-3669 - [GitHub コードの投稿 ](<https://github.com/magento/magento2/commit/df92debe>)_
* __オプションの属性のデフォルト値が機能しない__
以前は、product select 属性のデフォルト値を変更すると、以前の値を持つ配列要素として表示されていました。 この修正が適用された後、製品属性値を更新すると、eav_attribute テーブルに単一の要素として保存されます。
  _ACP2E-3688 - [GitHub コードの投稿 ](<https://github.com/magento/magento2/commit/520f9e30>)_
* __1,000 個の区切り記号が原因で編集中にギフトカードの検証が失敗する__
ギフトカードの金額が 1000 以上の場合に、ギフトカード製品タイプが保存される問題を修正しました。
  _ACP2E-3704_

### カタログ，GraphQL，検索

* __製品 graphql が、カテゴリ集計で無効なカテゴリを返しました__
修正後、無効なカテゴリは、製品 GraphQl リクエストに対して返されません。
  _ACP2E-2885 - [GitHub コードの投稿 ](<https://github.com/magento/magento2/commit/b12ffe36>)_

### カタログ、製品

* __[ランダムなバグ ] Fotorama lib が読み込まれない__
システムが Fotorama ライブラリが適切に読み込まれ、添付されたすべての画像を期待どおりに画像ギャラリーに表示できるようになりました。 以前は、Fotorama ライブラリが正しく読み込まれないという問題により、最初の画像のみが表示されていました。
  _AC-12124 - [GitHub コードの投稿 ](<https://github.com/magento/magento2/commit/45b51c9c>) - [GitHub コードの投稿 ](<https://github.com/magento/magento2/commit/27217d0e>)_

### コンテンツ

* __csp_whitelist.xml をテーマに含めると、機能せず、断続的な問題が発生します__
Web サイト領域ごとに CSP ホワイトリストのキャッシュを実装しました。
  _AC-13069 - [GitHub の問題 ](https://github.com/magento/magento2/issues/38933) - [GitHub コードの投稿 ](<https://github.com/magento/magento2/pull/39672>)_
* __エラー：商品が読み込まれる管理コンテンツの pagebuilder 用「Magento_Catalog/js/validate-product」のスクリプトエラー__
この PR は、製品条件を含むページビルダーを編集する際の catalogAddToCart のスクリプトエラーを修正します
  _AC-13891 - [GitHub の問題 ](https://github.com/magento/magento2/issues/39604) - [GitHub コードの投稿 ](<https://github.com/magento/magento2/pull/39677>)_
* __同じ識別子を持つウィジェットでのブロック選択__
同じ識別子ブロックがある場合、ウィジェットの作成中にブロックの選択が正しく処理されるようになりました
  _AC-14132 - [GitHub の問題 ](https://github.com/magento/magento2/issues/39692) - [GitHub コードの投稿 ](<https://github.com/magento/magento2/pull/39722>)_
* __テーブルのプレフィックスは考慮されません__
  _AC-14556 - [GitHub の問題 ](https://github.com/magento/magento2/issues/39847) - [GitHub コードの投稿 ](<https://github.com/magento/magento2/commit/1bc2d6d0>)_
* __幅が比較的小さい画像をアップロードできない__
システムは、高さに対して比較的小さい幅の画像のサイズ変更に失敗しなくなりました。
  _ACP2E-3558 - [GitHub コードの投稿 ](<https://github.com/magento/magento2/commit/9608ca21>)_
* __リモートストレージパスのスタイル設定の設定パスが正しくありません__
修正後、リモートストレージパスのスタイル設定を設定すると、実際のAWS S3 パスのスタイル設定に影響します。
  _ACP2E-3734 - [GitHub コードの投稿 ](<https://github.com/magento/magento2/commit/df92debe>)_

### フレームワーク

* __無効なモジュールのコードを補完しています。__
このプルリクエストは、コードのコンパイル前に無効なモジュールをエスケープします。
  _AC-10933 - [GitHub の問題 ](https://github.com/magento/magento2/issues/38241) - [GitHub コードの投稿 ](<https://github.com/magento/magento2/pull/39723>)_
* __Magento_Theme title.phtml テンプレートは PHP 8.2 では無効です__
このプルリクエストにより、Php 8.x で null 見出しで作成されたCMSページが trim （）に null を渡すと例外がスローされる問題を修正しました。非推奨の機能：trim （）：文字列型のパラメータ#1 （$string）に null を渡す
  _AC-12856 - [GitHub の問題 ](https://github.com/magento/magento2/issues/39092) - [GitHub コードの投稿 ](<https://github.com/magento/magento2/pull/39398>)_
* __ロックプロバイダーにファイルストレージを使用すると、クリーンアップが行われることなく、ファイルのディレクトリが増え続けます__
このプルリクエストでは、1 日に 1 回実行される新しい cronjob が導入され、過去 24 時間以内に変更されていないロックファイルが検索されるので、安全に削除できます。 これにより、lock files ディレクトリの内容が制御されます。
この cronjob は、ロックプロバイダーがファイルを使用するように設定されている場合にのみ実行します。他のファイル（データベース – デフォルト、zookeeper、キャッシュ）を使用している場合は実行しません
  _AC-13367 - [GitHub の問題 ](https://github.com/magento/magento2/issues/39369) - [GitHub コードの投稿 ](<https://github.com/magento/magento2/pull/39372>)_
* __[問題 ] クリーンアップ：メソッド呼び出しから void 戻り値を使用しない。__
この PR では、小規模なクリーンアップが行われます。 何も（void）返さないメソッドを呼び出し、その結果値を使用することもあります。 これは本当に必要ありません。
  _AC-13664 - [GitHub の問題 ](https://github.com/magento/magento2/issues/39524) - [GitHub コードの投稿 ](<https://github.com/magento/magento2/pull/39516>)_
* __[問題 ][PHPDOC]Magento\Framework\Message\ManagerInterfaceの不正な phpdoc を修正してください__
この PR は\Magento\Framework\Message\ManagerInterfaceの不正な phpdoc を修正し、\Magento\Framework\Message\Manager内の重複する phpdoc をすべて削除します（inheritdoc syntaxe を使用）。
  _AC-14312 - [GitHub の問題 ](https://github.com/magento/magento2/issues/39593) - [GitHub コードの投稿 ](<https://github.com/magento/magento2/pull/39153>)_
* __composer.json からベータ版の最小安定性を削除__
composer.json からベータ版の最小安定性を削除
  _AC-14450 - [GitHub コードの投稿 ](<https://github.com/magento/magento2/commit/1cbbf187>)_
* __allow_parallel_generation は、環境変数を使用して設定する必要があります__
修正後、「MAGENTO_DC_CACHE__ALLOW_PARALLEL_GENERATION」環境変数を使用して「allow_parallel_generation」設定を指定できます。
  _ACP2E-3673 - [GitHub コードの投稿 ](<https://github.com/magento/magento2/commit/b12ffe36>)_
* __[Cloud] Magento 2 で db_schema.xml ファイルを使用してテーブル列のタイプを Int から Decimal に変更すると、エラーが発生する__
列データタイプの変更が正しく機能しない。 以前は、次のエラーがスローされていました：属性「identity」は許可されていません。
  _ACP2E-3709 - [GitHub コードの投稿 ](<https://github.com/magento/magento2/commit/df92debe>)_
* __Adobeでの新しい通貨（XCG）のサポート__
カリビアンギルダー（XCG）が通貨リストに追加されました。
  _ACP2E-3790 - [GitHub コードの投稿 ](<https://github.com/magento/magento2/commit/520f9e30>)_

### GraphQL

* __GraphQLの注文に対する応答に例外メッセージが含まれていません__
別の形式でエラーを返していた以前の変更を元に戻しました。 潜在的なエラーが、GraphQLのスキーマを壊すことなく、一貫した方法で返されるようになりました。 これは既知の BIC として追加する必要があり、https://jira.corp.adobe.com/browse/ACP2E-3399?focusedId=45248897&amp;page=com.atlassian.jira.plugin.system.issuetabpanels:comment-tabpanel#comment-45248897で PM により承認されています。
  _ACP2E-3399 - [GitHub コードの投稿 ](<https://github.com/magento/magento2/commit/9608ca21>)_
* __注文配置に対するGraphQL応答が部分的にローカライズされています__
placeOrder GraphQl ミューテーションによって返されたエラーが完全にローカライズされていませんでした。 現在は、多言語コンテキストで、エラーが適切に翻訳されています。
  _ACP2E-3506 - [GitHub コードの投稿 ](<https://github.com/magento/magento2/commit/9608ca21>)_
* __GraphQL API を並べ替えるための同時呼び出し – 同じ製品が異なる行に追加される__
GraphQL API の並べ替えの同時呼び出しによって、同じ商品が異なる行として追加され、データの不一致が発生する問題を修正しました。
  _ACP2E-3774 - [GitHub コードの投稿 ](<https://github.com/magento/magento2/commit/c8ba4ab1>)_
* __updateCustomerEmail GraphQL mutation （Change email Address）がメール通知をトリガーしない__
以前は、アカウントのメールアドレスを正常に更新した後、メールが顧客に送信されませんでした。 修正が適用された後、お客様はメールアドレスを正常に更新した後、メール通知を受信するようになりました。
  _ACP2E-3785 - [GitHub コードの投稿 ](<https://github.com/magento/magento2/commit/c8ba4ab1>)_
* __updateGiftRegistry 変更を介してギフトレジストリで動的属性が更新されない__
以前は、この修正前は updateGiftRegistry のミューテーションによって、ギフトレジストリのカスタム属性がGraphQL ミューテーションによって変更または更新されていませんでした。 この修正が適用されると、updateGiftRegistry ミューテーションを使用して、ギフトレジストリの動的属性を正常に更新できます。
  _ACP2E-3805 - [GitHub の問題 ](https://mcstaging.briscoes.co.nz/)_

### インポート/エクスポート

* __[問題 ] Copyedit:「コピー」を「コピー」に変更する__
PR では、「コピー」のスペルを修正するためにマイナーコピー編集を修正しました
  _AC-13300 - [GitHub の問題 ](https://github.com/magento/magento2/issues/39311) - [GitHub コードの投稿 ](<https://github.com/magento/magento2/pull/39307>)_
* __REST エンドポイントの製品読み込み JSON で必須フィールドが検証されない__
読み込みプロセス（管理者または API）を使用して新しい製品を作成する際に、名前フィールドが必要になりました。 修正前に、名前のない新しい製品を作成できたことがありました。これは管理インターフェイスを壊し、無効な製品を作成したことになります。
  _ACP2E-3660 - [GitHub コードの投稿 ](<https://github.com/magento/magento2/commit/df92debe>)_
* __書き出しプロセスで web サイトフィルターオプションが見つからない__
製品の書き出しを作成する際に、web サイトで製品をフィルタリングできるようになりました。
  _ACP2E-3720 - [GitHub コードの投稿 ](<https://github.com/magento/magento2/commit/520f9e30>)_
* __AC-13913 の複製 – 静的属性の非同期クリーニング。__
修正後、\Magento\CatalogImportExport\Model\Import\Product\Type\AbstractTypeのインスタンスが多数作成される場合に、「未定義の配列キー「apply_to」」エラーは発生しません。
  _ACP2E-3752 - [GitHub コードの投稿 ](<https://github.com/magento/magento2/commit/520f9e30>)_

### インベントリ/MSI

* __チェックアウト時にアドレスが変更された場合、ストアピックアップが最大検索半径を考慮しない__
配送先住所が変更された場合、「店舗で選択」で事前に選択された店舗が更新されるようになりました。 以前は、ストアが事前に選択されると、新しい配送先住所が選択したストアの半径内にない場合でも、ストアは変更されませんでした
  _ACP2E-3728 - [GitHub コードの投稿 ](<https://github.com/magento/inventory/commit/07620383>)_

### 順序

* __nullable でないフィールド \&amp;quot;AppliedCoupon.code\&amp;quot；に対して null を返すことはできません__
  _AC-14484 - [GitHub の問題 ](https://github.com/magento/magento2/issues/39841) - [GitHub コードの投稿 ](<https://github.com/magento/magento2/commit/97b2ea42>)_
* __[クラウド ]magento 2.4.6-p7 にアップグレードした後、一部のインライン Javascript が機能しない__
管理者の「Add to Order by SKU」の「delete」ボタンをクリックすると、SKU が削除されるようになりました。 以前は、「Add to Order by SKU」の「delete」ボタンをクリックしても、SKU が削除されませんでした。
  _ACP2E-3515_
* __gift_cards のシリアル化されたデータが sales_order テーブルで矛盾している__
sales_order テーブルの gift_cards データが正しくシリアル化されるようになりました。 以前は、注文が更新されるたびにシリアル化されていました。
  _ACP2E-3662_

### オーダー、価格設定

* __返品の作成時に、管理者がに間違った通貨記号が表示される__
通貨（EUR/USD/GBP）が異なる複数の web サイトを設定する場合、管理者の返品製品選択ページに正しい通貨記号が表示されるようになりました。 以前は、デフォルトの通貨記号が表示されていました。
  _ACP2E-3658 - [GitHub コードの投稿 ](<https://github.com/magento/magento2/commit/df92debe>)_

### その他の開発者ツール

* __Lighthouse アクセシビリティの失敗__
システムはアクセシビリティスコア 100 で合格するようになった
  _AC-12783 - [GitHub の問題 ](https://github.com/magento/magento2/issues/39054) - [GitHub コードの投稿 ](<https://github.com/magento/magento2/pull/39164>)_
* __Captcha storefont 設定を無効にしても captcha js ファイルを読み込む__
Captcha を無効にした場合、システムは captcha js ファイルを読み込まなくなりました
保存用
  _AC-14267 - [GitHub の問題 ](https://github.com/magento/magento2/issues/32987) - [GitHub コードの投稿 ](<https://github.com/magento/magento2/pull/39154>)_

### 包装

* __[パッケージ化 ] magento/magento-coding-standard dependency+ ページビルダーを修正__
  _ACPLTSRV-6383_

### 支払額

* __[問題 ] オフライン請求書キャプチャの修正（404）__
Magento管理者からオフライン支払い方法用の請求書をキャプチャする際の 404 ページエラーを修正します
  _AC-13336 - [GitHub の問題 ](https://github.com/magento/magento2/issues/39298) - [GitHub コードの投稿 ](<https://github.com/magento/magento2/pull/39297>)_

### パフォーマンス

* __カテゴリ権限モジュールがキャッシュを防ぐ可能性がある__
サードパーティコントローラーが、顧客セグメントと正しくキャッシュされるようになりました
  _ACP2E-3721_

### 製品

* __製品コレクション – コレクションが読み込まれる可能性がある場合または読み込まれる場合に、addMediaGalleryData が getSize を呼び出します（カウントを使用して、追加の DB クエリを回避できます）__
この PR により、media_gallery フィールドを含んだ製品 Graphql を呼び出す際に製品コレクションが既に読み込まれている場合、count （）を使用して追加のクエリ呼び出しが削減されます。
  _AC-13055 - [GitHub の問題 ](https://github.com/magento/magento2/issues/39111) - [GitHub コードの投稿 ](<https://github.com/magento/magento2/pull/39681>)_
* __[2.4.8] cron job catalog_product_alert のコールバックが見つかりません__
  _AC-14494 - [GitHub の問題 ](https://github.com/magento/magento2/issues/39800) - [GitHub コードの投稿 ](<https://github.com/magento/magento2/commit/1bc2d6d0>)_
* __低速クエリは、pagebuilder を介して製品ウィジェットが含まれる場合に実行される__
製品 SKU を含む製品ウィジェットの作成用のクエリが最適化されています。
  _ACP2E-3449 - [GitHub コードの投稿 ](<https://github.com/magento/magento2/commit/df92debe>)_
* __設定可能な製品として追加された場合、製品画像のサイズは変更されません__
以前は、管理パネルの設定を通じて追加された画像が最大アップロードサイズの制限に準拠しておらず、不整合や管理の課題が発生する可能性がありました。 最大サイズ制限に準拠するためにアップロード中に画像のサイズが自動的に変更されるように修正が実装され、プロセスが合理化され、システム標準が維持されるようになりました。
  _ACP2E-3504 - [GitHub コードの投稿 ](<https://github.com/magento/magento2/commit/df92debe>)_

### 送料

* __公式ドキュメント内で正しくない % 実装については、ドキュメントを更新する必要があります__
DHL Rest API サポート用に devdoc を更新しました
  _AC-14507_
* __[DHL] - REST と XML API 統合の通常のサイズ設定および価格差異におけるオプションのディメンションを処理__
  _AC-14601 - [GitHub コードの投稿 ](<https://github.com/magento/magento2/commit/1e3bde4c>)_
* __UPS 出荷ラベルの作成中に例外が発生しました__
修正警告：UPS 出荷ラベルの作成中に配列から文字列への変換が行われました
  _ACP2E-3676 - [GitHub コードの投稿 ](<https://github.com/magento/magento2/commit/b12ffe36>)_

### ステージングとプレビュー

* __スケジュールされた更新をプレビューすると、関心のあるストア表示ではなく、アルファベット順で最初のストア表示が開く__
修正を行う前は、スケジュールされた更新のプレビューが、割り当てられたストア表示ではなく、アルファベット順の最初のストア表示で開いていました。
修正後、CMS ブロックのステージング更新に割り当てられたストアビューでプレビューが正しく開くようになりました。
  _ACP2E-3671 - [GitHub コードの投稿 ](<https://github.com/magento/magento2/commit/b12ffe36>)_
* __Staging_apply_version Cron の動作の問題 – special_price 無視__
修正後、見積の合計は、スケジュールされた製品の更新によって特別価格を変更した後に再計算されます。
  _ACP2E-3674_

### 税

* __ギフトラッピングがカートから削除されると、税額は更新されません__
  _AC-14637_
