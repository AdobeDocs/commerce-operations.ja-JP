---
source-git-commit: cfaa71f84f7d27d41c9d991aceef0087ee3d8ec0
workflow-type: tm+mt
source-wordcount: '8487'
ht-degree: 0%

---
# Magento Open Source リリースノート（v2.4.8-beta2）

## v2.4.8-beta2 のハイライト

Magento Open Source 2.4.8 リリースには、次の 30 のハイライトが適用されます。

### Braintree

* _BUNDLE-3400_：サポートされていない LPM を削除する
   * _GitHub コードの投稿_:<https://github.com/magento/ext-braintree/pull/208>
* _BUNDLE-3401_:Googleのペイマーク
   * _GitHub コードの投稿_:<https://github.com/magento/ext-braintree/pull/208>
* _BUNDLE-3402_:Appleのペイマーク
   * _GitHub コードの投稿_:<https://github.com/magento/ext-braintree/pull/208>
* _BUNDLE-3403_:Googleへの送料支払いに関するコールバック
   * _GitHub コードの投稿_:<https://github.com/magento/ext-braintree/pull/208>
* _BUNDLE-3404_：後払いメッセージ
   * _GitHub コードの投稿_:<https://github.com/magento/ext-braintree/pull/208>
* _BUNDLE-3405_:「JS-SDK」ボタン
   * _GitHub コードの投稿_:<https://github.com/magento/ext-braintree/pull/208>
* _BUNDLE-3406_:Braintree拡張機能内のコードを最適化する
   * _GitHub コードの投稿_:<https://github.com/magento/ext-braintree/pull/208>
* _BUNDLE-3407_:Braintreeの PHP および JS SDKの更新
   * _GitHub コードの投稿_:<https://github.com/magento/ext-braintree/pull/208>
* _BUNDLE-3408_：行項目（GooglePay）
   * _GitHub コードの投稿_:<https://github.com/magento/ext-braintree/pull/208>
* _BUNDLE-3409_：行項目（Apple Pay）
   * _GitHub コードの投稿_:<https://github.com/magento/ext-braintree/pull/208>
* _BUNDLE-3420_：パッケージトラッキング
   * _GitHub コードの投稿_:<https://github.com/magento/ext-braintree/pull/208>

### フレームワーク

* _AC-12012_:Nginx のバージョンを 1.24 から 1.26 にアップデートします
* _AC-12028_: 2.4.8 および 2.4.7 の最新バージョンの Composer 2.8 との互換性を追加
* _AC-12029_:Varnish 7.6 との互換性を確認
* _AC-12970_:PHPUnit 10 アップグレード パート 2 – 非推奨（廃止予定）の削除
   * _修正点_: phpunit/phpunit composer の依存関係を互換性のあるバージョンに更新しました – &quot;phpunit/phpunit&quot;:&quot;10.x&quot;
* _AC-13076_：利用可能な最新バージョンで、すべての js ライブラリと npm 依存関係を更新します
   * _修正点_: composer バージョンのサポートは、composer バージョン 2.2.x まででした。 また、サポートが 2.4.x バージョンにも拡張されました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/19844aa0>
* _AC-13077_：すべてのバンドルされた拡張機能および統合コンポーネントは、PHP 8.4 と互換性があります
* _AC-13078_：すべてのAdobe Commerce ツールは PHP 8.4 と互換性があります
* _AC-13079_：すべてのAdobe Commerce プロジェクトラミナス/dependencies は PHP 8.4 と互換性があります
* _AC-13256_:TinyMCE 依存関係をバージョン 7 からバージョン 6.8.5 にダウングレードする
* _AC-13276_:PHP 8.4 の非推奨（廃止予定）には、Adobe Commerceの重大な変更が必要です
* _AC-8828_:MySQL のデフォルトの照合順序を utf8mb4 に設定する

### その他

* _AC-12133_:Adobe Commerce 2.4.8 コアコードは、PHP 8.4 と互換性があります
* _AC-12972_:2.4.8-beta2 コア品質の改善
* _AC-13038_: composer.json とすべての関連サポートから PHP 8.1 を削除する
* _AC-13448_:2.4.8 に階層的な価格の運用パフォーマンス向上パッチを提供
   * _修正点_：このシステムでは、「/V1/products/tier-prices」 REST API エンドポイントを使用した場合に、パフォーマンスの問題やサイトの応答性の低下を引き起こすことなく、階層価格をより効率的に一括更新できるようになりました。 以前は、このエンドポイントを使用して多数の価格を更新すると、パフォーマンスの問題やサイトの応答が失われる可能性がありました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/082d981c>
* _AC-13550_:Magento Open Source リポジトリから、Adobeの機密著作権表示をすべて削除します
   * _修正点_:Adobeの著作権機密情報はすべてオープンソースリポジトリから削除され、Adobeの著作権が縮小された形式でのみ使用されるようになりました。 以前は、公開リポジトリ内の一部のファイルにAdobeの著作権機密情報が含まれていたため、コミュニティからのエスカレーションが発生していました。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/39493>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/4bca5dfe>

### セキュリティ

* _AC-10982_: [2FA] ユニバーサルプロンプトをサポートする Duo Web SDKとの統合
   * _修正注_：未定

### テストフレームワーク

* _AC-9037_:Adobe Commerce ソースコードのAdobe著作権を使用する機能

### UI フレームワーク

* _AC-12944_:Adobe Commerce から TinyMCE 5 を削除する

## v2.4.8-beta2 の問題を修正しました

Magento Open Source 2.4.8 コアコードの 159 の問題を修正しました。 このリリースで修正された問題の一部を以下に示します。

### API

* _ACP2E-3236_:SKU がペイロードにない場合、非同期操作は失敗します
   * _メモを修正_:SKU がペイロードにない場合の製品保存エラーにより、非同期および同期操作が以前に失敗しました。 修正後、非同期および同期製品の保存 rest api 操作が失敗し、関連する例外メッセージが表示されます。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/66dea0de>
* _ACP2E-3376_: [CLOUD] REST API を使用して基本価格を更新できません（「catalog_product_entity_decimal」の「value_id」の値が正しく増分されません。）
   * _修正点_：この修正の前は、rest api /rest/default/V1/products/base-prices が呼び出されたときに、値の間にギャップを残して誤って増分 ID が増加していました。 修正後、ID は期待どおりに増分されます。 また、value_id フィールドの範囲が拡大されました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/d50f6b5d>
* _ACP2E-3486_：製品 RestAPI の日付と時刻の属性にデフォルト値が設定されない
   * _メモの修正_:RestAPI を使用して、日付と日時の属性のデフォルト値が正しく設定されるようになりました
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/1984c61c>

### API、買い物かご、チェックアウト

* _ACP2E-3343_：重大な 500 エラー：Magento\Framework\Webapi\Exception Accept HTTP ヘッダーに関連するもの
   * _修正点_：修正後に、「Accept」ヘッダーを指定する際に問題はありません。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/1366ae5e>

### アカウント

* _AC-10886_：管理者パスワードの更新。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/38352>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/4bca5dfe>
* _AC-11718_:URL が大文字の場合のリダイレクトループ
   * _メモの修正_：システムで URL の大文字が自動的に小文字に変換されるようになり、ホームページにアクセスする際にリダイレクトループが発生しなくなりました。 以前は、セキュアなベース URL に大文字が含まれていると、ホームページにアクセスしようとすると、継続的なリダイレクトループが発生していました。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/38538>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/38539>
* _AC-13000_：顧客オプトインチェックボックスとしてログインが翻訳可能ではない
   * _メモの修正_：システムの「顧客オプトインチェックボックスとしてログイン」および「顧客としてログイン」チェックボックスツールヒントのフィールドを「ストア表示」範囲で設定できるようになり、様々なストア表示の翻訳が可能になりました。 以前は、これらのフィールドは「Web サイト」の範囲でのみ設定され、個々のストア表示の翻訳を防いでいました。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/32329>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/32359>
* _ACP2E-3329_: ログイン後、ゲストユーザーとして比較リストに追加された製品が表示されません。
   * _修正点_：顧客としてログインする前に製品比較リストに追加された製品は、ログイン後も保持されるようになりました。
以前は、ログイン後、ゲストユーザーとして比較リストに追加された製品が表示されていませんでした。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3433_：国の設定を許可すると、顧客アドレス設定で問題が発生する
   * _修正メモ_：現在、「国を許可」設定を選択しても、指定された範囲以外で表示される国には影響しません。 以前は許可する国の設定が、指定されたスコープ外の顧客アドレス属性に影響していました
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/078c387e>

### アカウント，API, GraphQL

* _ACP2E-3246_：カスタマー API - ログインに成功した後、ログインエラー番号を 0 にリセットできない
   * _修正点_:API エンドポイントを介してユーザーが正常にログインした後、カスタマーエンティティテーブルのエラー番号が 0 にリセットされるようになりました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/ec7e32a9>

### アカウント、管理 UI、B2B

* _ACP2E-3038_：制限付き管理者ユーザーは、カスタムの共有カタログを常に表示できるわけではありません
   * _修正メモ_：制限付き管理者ユーザーは、特定のストアにアクセスできる場合、製品が割り当てられている顧客およびすべての共有カタログを一貫して表示および管理できるようになりました。 以前は、特定のストアへのアクセス権を持つ制限付きの管理者ユーザーは、製品が割り当てられたすべての共有カタログを表示できなかったり、保存できなかった顧客を表示できたりして、システムの不整合が発生していました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/7377de59>

### 管理 UI

* _AC-10705_:[ 問題 ] 「データを再読み込み」ボタンに対する権限チェックを追加
   * _メモの修正_：システムには、「データのリロード」ボタンに対する権限チェックが含まれるようになりました。適切な権限を持つユーザーのみがデータを表示してアクセスできるようにします。 以前は、「データの再読み込み」ボタンがすべてのユーザーに対して表示され、クリック可能であったため、必要な権限を持たないユーザーがクリックすると「許可されていない」ページが表示されていました。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/38283>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/38279>
* _AC-13131_:[ 問題 ] 修正警告：未定義の配列キー「フィルター」
   * _メモの修正_：新しいユーザーがまだブックマークと対話していないシナリオをシステムが処理し、未定義の配列キー「フィルター」の警告がログに記録されなくなりました。 以前は、この警告は、新規ユーザーがブックマークでやり取りしなかった場合にログに記録されていました。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/39013>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/38996>
* _AC-13529_:Validate.php ファイルのコード変更が原因で、特殊文字を含む製品の csv ファイルの読み込みに失敗する
   * _メモの修正_：特殊文字を含む製品の CSV ファイルを正しく検証および読み込むようになり、データ転送が成功しました。 以前は、特殊文字を含む製品の CSV ファイルを読み込もうとすると、エラーが発生し、読み込みプロセスが妨げられていました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/6cfb9b6b>
* _AC-7962_：携帯電話表示でチェックアウトの支払い時に、出荷へのリンクがない
   * _メモの修正_：システムのモバイル表示で、チェックアウトタイトル/リンク「送料」と「確認と支払い」がページの上部に常に表示されるようになり、ユーザーがステップ間を簡単に移動し、必要な修正を行えるようになりました。 以前は、これらのタイトルやリンクはモバイル表示では非表示になっていたため、ユーザーが現在の手順を把握したり前の手順に戻ったりするのが困難でした。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/36856>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/36982>
* _AC-8109_：顧客注文クエリの出荷コメント created_at は、店舗で設定されたタイムゾーンではなく、+0 タイムゾーンで返されます
   * _メモの修正_：顧客の注文クエリを使用する際に、顧客が設定したタイムゾーンで、出荷コメントの「created_at」フィールドが正しく表示されるようになりました。 以前は、「created_at」フィールドは、顧客が設定したタイムゾーンに関係なく、+0 タイムゾーンで表示されていました。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/36947>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/37642>
* _ACP2E-3294_：配送先住所の状態が自動更新されない
   * _修正点_：修正前は、配送先住所の地域（または地域 ID）が住所請求情報と同期していませんでした。 請求先住所情報が変更されると、配送先住所のリージョンとリージョン ID の両方が正しく更新されるようになりました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3364_：管理者ユーザーの追加/編集時にリセットボタンが機能しない
   * _修正点_：以前は、管理者ユーザーの追加/編集ページで「リセット」ボタンが機能しませんでした。 これで、管理パネルのシステム/権限/すべてのユーザーの下で、リセット ボタンが管理者ユーザーを追加/編集ページで正しく機能するようになりました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3392_:「買い物かごで許可された最大数量」の検証が壊れています
   * _メモの修正_：以前は、空の値を配置 `Maximum Qty Allowed in Shopping Cart` ると、空の値はここでは受け入れられませんが、例外はスローされませんでした。 この修正が適用された後、空の文字列を指定すると例外がスローされ、製品を保存できなくなります。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/d50f6b5d>
* _ACP2E-3408_:[Pagebuilder プレビュー UI の問題 ] ページビルダー列のボタンが正しく配置されない
   * _メモの修正_：ページビルダー列のボタンの位置が正しく調整されるようになりました。 以前は、ページビルダーの列内で位置がずれていました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2-page-builder/commit/1a52ef4c>
* _ACP2E-3431_：注文された製品レポートがエクスポートされない。 代わりに 404 エラー。
   * _修正点_:CSV および XML を除く、注文された製品レポートが期待どおりに動作するようになりました
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/88660e79>
* _ACP2E-3457_:Js の縮小後にコンソール内で TinyMCE JS エラーが発生し、実稼動モードで有効になる
   * _修正点_：以前は、管理パネル内の実稼動モードでJavaScriptの縮小を有効にすると、TinyMCE 7 に関連するJavaScript エラーがブラウザーコンソールに表示され、機能とユーザーエクスペリエンスに影響を与えていました。 この問題が解決され、JS の縮小が有効になっている場合でも TinyMCE 7 がエラーを起こすことなくスムーズに動作するようになりました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/56463d5e>
* _ACP2E-3459_:ACP2E-3375 修正を完全に完了するための追加変更のリクエスト
   * _修正メモ_ : 「– 
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/d50f6b5d>

### 管理 UI、支払い/支払い方法、注文

* _AC-13520_:PayPal スマートボタンの注文後、「トランザクション」タブにトランザクション認証が表示されない
   * _メモの修正_:PayPal スマートボタンを使用して注文した後、「トランザクション」タブにトランザクション認証が正しく表示されるようになりました。 以前は、「認証」ボタンをクリックすると、認証トランザクションが「トランザクション」タブに表示されず、「認証」タイプの新しいトランザクションが作成されていませんでした。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/6cfb9b6b>

### 管理 UI、ステージングおよびプレビュー

* _ACP2E-3424_: [Cloud] 画像が欠落しているテンプレートを削除すると、pub/media が削除されます
   * _メモの修正_：この修正の前に、pagebuilder テンプレートのプレビュー画像名が見つからなかった場合、pub/media フォルダーが削除されました。 修正後は、テンプレートのみが削除され、見つかった場合はプレビュー画像が削除されます。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2-page-builder/commit/0986853b>

### 分析/レポート

* _AC-9922_:Google Analytics CSP Error https://region1.analytics.google.com
   * _修正点_:Google Analyticsが有効な場合、システムは正しく「https://region1.analytics.google.com&#39;」への接続を許可し、コンテンツセキュリティポリシー（CSP）エラーを防ぐようになりました。 以前は、Google Analyticsを有効にして EU から web サイトを表示すると、「https://region1.analytics.google.com&#39;」への接続が拒否されて、CSP コンソールエラーが発生していました。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/37750>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/38991>
* _ACP2E-3183_:NewRelic ブラウザーで inlineJS スクリプトを監視すると、CSP エラーが発生する
   * _修正メモ_:CSP （コンテンツセキュリティポリシー）に準拠するために、NewRelic ブラウザー監視スクリプトが APM エージェントではなくアプリケーションによって挿入されるようになりました。 以前は、APM エージェントによって挿入された NewRelic ブラウザー監視スクリプトが CSP に準拠しておらず、スクリプトが実行されませんでした。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/66dea0de>
* _ACP2E-3189_：販売注文量が多いプロジェクトでは、sales_bestsells_aggregated_daily テーブルへの INSERT クエリの処理が遅くなる
   * _修正点_：以前はベストセラーの毎日の集計レポートは、大量の注文を生成するのに多くの時間がかかっていました。 これで、レポートがタイムリーに生成されます。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/7377de59>
* _ACP2E-3276_：間違った通貨記号を示す注文レポート
   * _メモの修正_：注文レポートの注文金額の通貨記号が、通貨/オプション/ベースから誤って取得されていました。 正確なレポートを作成するために、通貨/オプション/デフォルトを使用するように修正されました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/fd5cf3af>
* _ACP2E-3302_: [Cloud] クーポン使用状況レポートの計算が正しくありません
   * _修正点_: クーポンレポート・グリッドの売上合計は、「割引税補償金額」と「出荷割引税補償金額」の両方を組み込むことで正確に計算されるようになりました。 以前は、これらの金額が計算から欠落していたため、売上合計と受注データの間に不一致がありました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/d75cff27>
* _ACP2E-3339_：共有「&lt;project_id>/var/tmp」に関する問題
   * _メモの修正_:Analytics DataExport の一時ファイルは、sys tmp ディレクトリを使用します。このディレクトリは、頻繁なアクセスと変更に適しています。 同じサーバーで複数のインスタンスが実行されている場合の競合を避けるために、tmp パスはインスタンスの一意の ID を使用するように更新されました
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/a4cf5e62>

### Analytics/レポート、クラウド

* _ACP2E-3187_：バックグラウンド トランザクションで NR のメトリックが誤解を招く可能性がある – ACP2E-3067 のフォローアップ
   * _メモの修正_：バックグラウンドトランザクション（cron）では、設定で定義されたNew Relic アプリ名を使用します
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/ec7e32a9>

### B2B

* _ACP2E-2139_：共有カタログに割り当てられた製品が、部分的なインデックスが実行されたときにフロントエンドに反映されない
   * _メモの修正_:REST API を介して共有カタログに割り当てられた製品が、部分的なインデックス作成の完了後、直ちにストアフロントに表示されるようになりました。 以前は、製品は、完全な再インデックス後にのみ表示されていました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/7377de59>
* _ACP2E-3247_: sales_clean_quotes cron は、まだ承認されていない発注書からの見積を削除します
   * _修正メモ_：現在の発注書で使用されている見積は、cron ジョブ sales_clean_quotes によって削除されません
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/581b7ef1>

### バンドル

* _AC-10826_：ストアフロントバンドルチェックボックス検証エラーメッセージ数が 1 を超える
   * _修正メモ_：バンドルされた製品のチェックボックスオプションを選択せずに、「買い物かごに追加」ボタンをクリックしても、検証エラーメッセージが 1 つだけ表示されるようになりました。 以前は、システムには、選択されていない各チェックボックスに対して複数の検証エラーメッセージが表示されていました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/3ea26621>

### 買い物かごとチェックアウト

* _AC-11914_: [ 問題 ] 販売ルール CartFixed 計算：割引額が正しくない
   * _修正点_：システムで買い物かごの固定金額を使用して、販売ルールの割引額が正しく計算され、買い物かごの品目の変更に関係なく正確な割引が適用されるようになりました。 以前は、買い物かごの商品が変更されると割引額が正しく変化せず、予想よりも大幅に大きな割引が発生する場合がありました。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/38694>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/581b7ef1>
* _AC-12479_：利用条件チェックボックスでストアフロントのHTMLが許可されない
   * _修正点_：ストアフロントの「利用規約」チェックボックステキストでHTMLの書式設定がサポートされるようになり、カスタマイズと読みやすさが強化されました。 以前は、チェックボックステキストは、使用されるHTML タグを無視して、プレーンテキスト形式で表示されていました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/6cfb9b6b>
* _AC-12541_：ログインしたユーザー用に作成された買い物かご価格ルールが、ログインしていないユーザーに対して正しく適用されない
   * _修正メモ_:Cookie の有効期限が原因で自動的にログアウトされた場合、ログインしたユーザーの買い物かご価格ルールが正しく削除され、ログインしていないユーザーに割引が適用されなくなりました。 以前は、ユーザーがログアウトした場合でも買い物かごの価格ルールが適用され、ログインしていないユーザーには誤った割引が適用されていました。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/38944>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/7d5e3906>
* _AC-13302_:[ 問題 ] [ 機能 ] パフォーマンスの最適化を実現し、大規模な買い物かごに入れるのを防ぎます。
   * _修正メモ_：このシステムは、重複する getActions 呼び出しを防ぎ、買い物かごの操作の速度と効率を向上させることで、大きな買い物かごのパフォーマンスを最適化するようになりました。 以前は、複数のアイテムを含む買い物かごの場合、getActions 関数が複数回呼び出され、システムのパフォーマンスが低下していました。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/39292>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/39290>
* _ACP2E-3176_: [Cloud] クイックオーダーによる大量の SKU パフォーマンス
   * _修正メモ_：買い物かごの価格ルールの条件で使用される属性がすべての製品に存在しない場合や MAP （Minimum advertised price）機能が有効な場合のチェックアウトのパフォーマンスが向上しました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/66dea0de>
* _ACP2E-3211_：カート内の重複項目
   * _修正メモ_：複数の並列リクエストを正しく処理して同じ製品を 1 つの行項目に買い物かごに追加できるようになり、同じ SKU で別々の行項目を作成できなくなりました。 以前は、同じ製品をストアフロントの買い物かごに追加するリクエストを並行して行うと、同じ SKU に対して複数の行項目が発生していました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/66dea0de>
* _ACP2E-3296_：姓名に入力されたメールに対して、チェックアウト注文のメール確認が送信されます
   * _メモの修正_：チェックアウト注文のメール確認は、以前は名前（名）フィールドと名前（姓）フィールドにメールのようなパターンを入力して送信されていましたが、送信されなくなりました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3402_：チェックアウトの配送先住所フォームが間違った住所で更新される
   * _修正点_:shippingAddressFromData は、web サイトごとのローカルストレージに保存されるようになりました。 以前は、URL にストアコードが使用され、同じゲストセッション中に複数の web サイトからチェックアウトが開始された場合、チェックアウト中に間違った web サイトの住所が発送先住所フォームに自動入力される可能性がありました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3407_：ギフトカード製品 |買い物かごへの結合でギフト カードを結合しています
   * _修正点_：ギフトカード製品がカートに正しく結合されるようになりました
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/88660e79>
* _ACP2E-3488_：既存の見積もりデータが更新または表示されず、代わりに、トリガー_recollect = 1 の場合に新しい見積もりレコードが作成されます
   * _修正点_：製品を買い物かごに追加した後、製品を削除した結果、顧客の買い物かご項目が表示されなくなりました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/1984c61c>

### カタログ

* _AC-11970_:1 つのチェックボックスが選択されたカスタムオプションで、設定可能な製品を並べ替えることができません
   * _修正点_：システムは、単一の選択されたチェックボックスカスタムオプションを使用して、設定可能な製品の並べ替えを正しく処理し、バスケットの作成を成功させられるようになりました。 以前は、このような製品を並べ替えようとするとエラーが発生し、アイテムを買い物かごに追加できませんでした。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/38736>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/1d144bce>
* _AC-13068_：ドロップダウンオプションが見つからない
   * _メモの修正_：値が 20 を超える新しい属性を作成する際に、ドロップダウンのすべての値が正しく表示されるようになりました。 以前は、最初の 20 個の値または選択した別のページ値のみが表示され、残りの値は欠落していました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/47b448e2>
* _AC-13296_:[ 問題 ] カテゴリのランタイムキャッシュに現在のストア ID を使用
   * _メモの修正_：システムでは、カテゴリランタイムキャッシュに現在のストア ID を正しく使用するようになり、エミュレーションが使用される場合やカスタムコードがカテゴリを異なるストアに保存する場合に、データの上書きを防ぎます。 以前は、ランタイムに保存されたオブジェクトは間違ったストアから取得されていた可能性があり、データのオーバーライドが発生していました。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/39310>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/36394>
* _AC-13324_: bin/magento sampledata:deploy —no-update が例外をスロー
   * _修正点_:sampledata:deploy コマンドで – no-update オプションを使用する場合、システムがブール値を正しく受け入れるようになり、サンプルデータのデプロイ中にエラーが発生しなくなりました。 以前は、システムが誤って整数値を期待していたので、このコマンドを使用する際にエラーがスローされていました。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/39344>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/39345>
* _AC-13355_:[ 問題 ]EAV キャッシュタイプの使用を修正
   * _修正点_：システムは、関連するすべての場所で EAV キャッシュタイプを正しく使用するようになり、一貫性のある効率的なデータキャッシュを確保します。 以前は、EAV キャッシュタイプは一貫して使用されていなかったので、データキャッシュの非効率性と不整合が発生する可能性がありました。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/32322>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/31264>
* _AC-13596_：空のデータを使用したカタログの詳細検索は、検索結果ページに移動します [2.4.dev ブランチ ]
   * _メモの修正_：システムでは、「詳細検索」ページのユーザーが正しく保持され、データを入力せずに検索を実行しようとするとエラーメッセージが表示されるようになりました。 以前は、空の検索を実行すると、ユーザーに検索を変更するように促すメッセージが表示されて、カタログの詳細検索ページにリダイレクトされていました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/6cfb9b6b>
* _ACP2E-3103_：新製品キャッシュが原因で、RSS フィードが新製品で更新されない
   * _メモの修正_：製品を新規および保存済みとして設定した場合、新製品用の Rss フィードが更新されるようになりました
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/d01ee51e>
* _ACP2E-3198_: [cloud] 実際のモバイルデバイスでの 2 本指のズームと移動の問題
   * _メモを修正_：システムは、モバイルデバイスで一貫した画像ズーム機能を保証し、スムーズで予測可能なユーザーエクスペリエンスを提供するようになりました。 以前は、画像のズーム機能に一貫性がなく、モバイルデバイスで表示すると特定のポイント後に突然ズームアウトしていました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/1366ae5e>
* _ACP2E-3282_：共有カタログから製品の割り当てを解除しても、ウィッシュリストの製品がクリアされない
   * _メモの修正_：共有カタログで製品を使用できない場合、ウィッシュリストに項目が表示されなくなりました。 以前は、ウィッシュリストに実際に使用可能な項目がない場合でも、ウィッシュリストページに「1 項目」というカウントが誤って表示されていました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3286_：関連製品すべての問題を選択/すべての問題を選択解除
   * _注意を修正_：以前は、製品が手動で選択されている場合、関連製品の「すべてを選択」/「すべてを選択解除」ボタンが正しく機能しませんでした。 修正後は、手動で選択した場合でも、これらのボタンが一貫して機能するようになり、すべての製品が適切に選択または選択解除されるようになります。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/fd5cf3af>
* _ACP2E-3336_: [Cloud] Stock アラートメールを間違った言語に翻訳
   * _修正点_：異なる言語で複数のストアが表示されている web サイトの在庫/価格アラートを送信する場合、アラートが作成されたストア表示の言語がメールで使用されます。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/a4cf5e62>、<https://github.com/magento/inventory/commit/9f3e63d1>
* _ACP2E-3350_：無効なカテゴリの名前は、カテゴリツリーでグレー表示されなくなりました
   * _メモの修正_：以前は、無効なカテゴリは、カテゴリツリーでグレー表示されていませんでした。 現在は、グレーの効果で表示されています。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/d75cff27>
* _ACP2E-3410_：設定可能な製品編集フォームの読み込みが原因で、タイムアウトとメモリ不足が発生する
   * _修正メモ_：修正前は、設定可能な製品バリエーションは、可能なすべての属性オプションの組み合わせに基づいて構築されていました。 属性に多くのオプションがある場合、これは長くリソースを消費する操作につながりました。 現在は、設定可能な製品バリエーションは、既存の子製品属性に基づいて構築されています。 これにより、計算がはるかに少なくなり、リソースの使用率が向上します。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3454_：スウォッチを使用する際に、Fotorama がビデオを正しく読み込まず、URL でオプションが事前に選択されている
   * _メモの修正_：選択したオプションが URL に含まれている場合、製品ビデオが設定可能な製品詳細ページで正しくレンダリングされるようになりました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3461_:PageBuilder カルーセルウィジェットに、条件に一致しない製品が表示される
   * _修正点_：ウィジェットで使用される製品リストがカテゴリ条件に従うようになりました
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3469_：グループ内のすべての製品で、無効な数量がある場合に検証エラーがトリガーされる
   * _修正点_：以前は発生していなかった、1 つの製品の数量が無効な場合、グループ内のすべての製品に対して検証エラーが正しくトリガーされるようになりました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/56463d5e>
* _ACP2E-3516_: インデクサー処理が終了しても、一時テーブルはクリーンアップされません
   * _メモの修正_：インデクサープロセスが終了すると、CatalogRule インデクサーの一時テーブルがクリーンアップされるようになりました
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/1984c61c>
* _ACP2E-3520_: [QUANS] 2.4.7-p3 でのコアユニットのテストエラー
   * _修正点_：このテストは単体テストの改善なので、リリースノートは必要ありません。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/1984c61c>

### カタログ、コンテンツ

* _ACP2E-3063_: [Cloud] キャッシュが無効化されません。
   * _メモの修正_：以前は、デザインレイアウトを更新してCMS ページを保存すると、フロントエンドに適切に反映されていませんでした。 この修正が適用された後、デザインレイアウトを変更してCMSページを保存すると、適切なデザインレイアウトがフロントエンドに表示されます。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/66dea0de>
* _ACP2E-3131_: コンテンツウィジェットで [ クラウド ] アンカー/アンカー以外のカテゴリが反転されました
   * _注意を修正_：以前は、「表示オン」 > 「アンカーカテゴリ」を選択すると、アンカーとアンカー以外の間の親子関係を反映していないすべてのカテゴリが表示されていました。 この修正を適用すると、[ 表示オン ] > [ アンカーカテゴリ ] にはアンカーカテゴリ（選択可能）のみが表示され、[ 表示オン ] > [ アンカーなしカテゴリ ] にはアンカーなしカテゴリ（選択可能）が表示されます
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/7377de59>
* _ACP2E-3152_：ウィジェットで機能しないカテゴリ
   * _修正点_：以前は、アンカー/非アンカーの異なるカテゴリ用にCMS ブロックを保存した場合、フロントエンドに表示されたときに、子カテゴリに対して機能しませんでした。 この修正が適用されると、ブロックが様々なカテゴリのフロントエンドに表示されます。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/d01ee51e>

### カタログ、GraphQL

* _ACP2E-3312_：階層価格がGraphQL製品で誤った値を返す（ストアフロントと比較）
   * _修正メモ_：修正後、Graphql リクエストに対して返される製品の階層価格には、1 項目あたりの価格があります。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/1366ae5e>

### カタログ、検索

* _ACP2E-3345_: オブジェクトの作成中にタイプ エラーが発生しました：Magento\CatalogSearch\Model\Indexer\Fulltext\Interceptor例外
   * _修正点_：修正後、$data を指定せずにMagento\CatalogSearch\Model\Indexer\Fulltext クラスのインスタンスを作成できます。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/1366ae5e>
* _ACP2E-3521_:Magento Admin で保存した後、フロントエンドに製品の [CLOUD] 問題が表示されない
   * _メモの修正_：修正後は、長い名前の子製品を持つ設定可能な製品は、ストアフロントで見逃されません。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/1984c61c>

### コンテンツ

* _AC-12692_：ウィジェットカテゴリツリーが正しくレンダリングされない
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/39008>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/58e40ceb>
* _AC-13054_：デザイン設定ページでテーマを変更すると、「デフォルト値を使用しています」というメッセージが表示されない
   * _メモの修正_：デザイン設定ページで選択したテーマに応じて、「デフォルト値を使用」メッセージを表示する別の列がシステムに含まれるようになりました。 これにより、デフォルト値のステータスが明確に表示され表示されます。 以前は、「デフォルト値を使用」というメッセージが表示されなかったので、選択したテーマのステータスに混乱が生じていました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/47b448e2>
* _AC-13569_:[ 問題 ]TinyMCE プラグインとの下位互換性を（その後も）復元します。
   * _修正点_：システムは TinyMCE プラグインとの下位互換性を回復し、別の場所からウィジェットを使用するときにプラグイン内で定義された関数を呼び出すことができるようになりました。 以前は、TinyMCE バージョンの変更により、プラグインがウィジェットをオブジェクトとして返さなくなり、ウィジェットインスタンスで特定の関数を呼び出そうとした場合にエラーが発生していました。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/39262>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/39258>
* _ACP2E-3122_: [CLOUD] 画像をアップロード ボタンが機能しない
   * _注意を修正_：以前は、PageBuilder のバナーとスライダーの「画像をアップロード」ボタンが期待どおりに動作しませんでしたが、現在は、キーを押すとローカルファイルマネージャーが開き、アップロードする画像を選択できます。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2-page-builder/commit/476ef8ea>
* _ACP2E-3275_: [Cloud] – 最新の変更がCMS Slider に反映されない
   * _修正点_：この問題は、スライドの編集画面で保存イベントがトリガーされている間にスライダーリストが確実に更新されることで修正されました。 以前は、トリガーとなって問題が発生していました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2-page-builder/commit/ae2cdeb0>
* _ACP2E-3326_：ページビルダーを使用してCMS ブロックを特定の順序で挿入すると、CSM ページでエラーが発生します
   * _注意を修正_：以前は PHP と OS （Linux）の一部のバージョンでは、PageBuilder を介して他の cms ブロックを参照するブロックのレンダリングは、「不明なエラーが発生しました。 もう一度やり直してください。」というエラーメッセージが表示されます。 これで、cms ブロックのコンテンツが、PageBuilder が制御するコンテンツ内で正しくレンダリングされるようになりました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2-page-builder/commit/ae2cdeb0>
* _ACP2E-3430_：フォントサイズが欠落している TinyMCE 7 を使用した最新のセキュリティ更新
   * _修正点_：フォントサイズおよびフォントファミリセレクターがWYSIWYG Editor で使用できるようになりました。 この修正を行う前は、TinyMCE 7 ではエディターインターフェイスで使用できませんでした。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/d50f6b5d>、<https://github.com/magento/magento2-page-builder/commit/2c2f7a0e>

### 顧客/顧客

* _AC-8499_：国のドロップダウンが変更された場合、地域テキストフィールドがリセットされない
   * _メモの修正_：ドロップダウンメニューで国が変更されると、システムによって地域テキストフィールドがリセットされ、以前の値が保持されなくなりました。 以前は、ドロップダウンリストから国を変更しても地域フィールドがリセットされず、最後に保存された値が保持されていました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/3ea26621>
* _AC-9240_：顧客を削除しても、ログインして削除された顧客のストアフロント上のブラウザーセッションデータがすべて消去されない
   * _メモの修正_：顧客を削除すると、ログインして削除された顧客のすべてのブラウザーセッションデータが期待どおりにストアフロントからクリーンアップされるようになりました。 買い物客は買い物を続けることができ、ブラウザーはそのセッションをゲストセッションとして扱います。 以前は、ログインした買い物客のカスタマーアカウントが管理者から削除されると、買い物客のブラウザーがJavaScript エラーをスローしていました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/7d5e3906>

### フレームワーク

* _AC-10738_:Varnish 設定によって、すべてのマーケティングパラメーターが除外されるわけではありません
   * _メモの修正_：システムは、ワニス設定のすべての一般的なマーケティングパラメーターを正しく除外し、正確なトラッキングと分析を確保できるようになりました。 以前は、gad_source、srsltid、msclkid などの特定のマーケティングパラメーターが除外されていなかったので、データ収集が不正確になる可能性がありました。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/38298>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/39188>
* _AC-11592_:[ 問題 ] セットアップ :di: コンパイル時に有効な環境設定のみを許可
   * _修正点_：存在しないクラスまたは明確に除外されたクラスにプリファレンスが作成された場合、システムは setup:di:compile コマンド中にエラーをスローするようになりました。これによって、有効なプリファレンスのみが許可されます。 以前は、これらのシナリオはサイレントに失敗し、元のクラスに関連付けられたプラグインが役に立たない可能性がありました。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/38517>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/33161>
* _AC-11809_:[ 問題 ]XML を使用してカスタム属性を現在のリンクに渡す
   * _メモの修正_：システムでは、カスタム属性を XML 経由で現在のリンクに渡すことができるようになり、リンクが現在のページの場合でもこれらの属性が正しく表示されるようになります。 以前は、getAttributesHtml （） メソッドが現在のリンクに使用されていないので、現在のページリンクにカスタム属性が表示されていませんでした。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/38500>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/30070>
* _AC-12127_:[ 問題 ] 設定ミスの無限ループを回避
   * _メモの修正_：システムは、仮想タイプ設定での自己参照マッピングを防ぐことで、無限ループを回避できるようになりました。 これにより、自己参照ノードを逆参照しようとするときに、アプリケーションが無限ループで動かなくなるのを防ぎます。 以前は、仮想タイプの設定が自己参照の場合、アプリケーションが無期限にスピンしていました。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/38822>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/38794>
* _AC-12299_:Magento\Csp\Model\Mode\Data\ModeConfiguredにオブジェクトマネージャーが使用されていない
   * _メモの修正_：システムは、ModeConfigured オブジェクトを作成する際にオブジェクトマネージャーを正しく使用し、このオブジェクトでプラグインを使用できるようになりました。 以前は、Object Manager は使用されていなかったので、プラグインが ModeConfigured オブジェクトに適用されませんでした。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/38875>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/38886>
* _AC-12540_：製品在庫および価格アラートの不正確なドキュメントブロックコメント
   * _修正メモ_：製品在庫および価格アラート内の deleteCustomer メソッドのドキュメントブロックコメントが修正され、メソッドが web サイトからの顧客ではなく、特定の顧客および web サイトに関連付けられたすべての在庫製品または価格アラートを削除することを正確に反映するようになりました。 以前は、コメントは、その方法がウェブサイトから顧客を削除するためのものであると不正確に述べていました。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/38939>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/39001>
* _AC-12857_:PHP 8.2.15 で FTP 拡張機能が削除されました
   * _メモの修正_：システムでは、composer.json ファイルの依存関係として FTP 拡張機能を含むようになり、FTP 経由で CSV インポートを正常に設定できるようになりました。 以前は、FTP 経由で CSV の読み込みを設定しようとすると、PHP パッケージに FTP 拡張機能がないのでエラーがスローされていました。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/39083>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/47b448e2>
* _AC-12964_:dev:di:info CLI コマンドの領域を定義する機能
   * _修正点_：このシステムでは、開発者が dev:di:info CLI コマンドの領域を定義できるようになり、開発とデバッグプロセスが強化されました。 以前は、このコマンドでは GLOBAL 領域の情報しか表示できませんでした。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/38758>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/38759>
* _AC-13279_:[ 問題 ] すべてのマーケティング get パラメーターを削除して、キャッシュを最小限に抑えてください
   * _修正メモ_：システムは、キャッシュ使用率を最適化するために、すべてのマーケティング get パラメーターを削除するようになり、Varnish が使用されているときに使用されるロジックをミラーリングします。 以前は、これらのパラメーターを使用すると、キャッシュが肥大化してパフォーマンスが低下する可能性がありました。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/39266>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/39099>
* _AC-13345_:[ 問題 ] [PHPDOC] 不正な phpdoc Magento\Directory\Model\AllowedCountries::getAllowedCountries （）
   * _修正メモ_: AllowedCountries::getAllowedCountries （） メソッドの PHPDoc が修正され、正確な情報が提供されるようになり、ドキュメントの明確性と有用性が向上しました。 以前は、このメソッドの PHPDoc に誤った情報が含まれていたため、メソッドの混乱や誤用が発生する可能性がありました。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/39246>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/39241>
* _AC-13348_: [ 問題 ] サポートされなくなった PHP バージョンのコードを削除します。
   * _修正点_:Magentoでサポートされなくなった PHP バージョンのコードの削除
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/39361>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/39202>
* _AC-13417_:[ 問題 ] ImageMagick アダプターを php8 と互換性のあるものにする（float から int への暗黙的な変換）
   * _修正点_: システムは、画像サイズを計算する際に float の数値を正しく処理し、float から int への暗黙的な変換によるエラーを防ぐことで、PHP8 との互換性を確保するようになりました。 以前は、画像の寸法を計算すると浮動小数になり、暗黙的に丸めるとエラーが発生する場合がありました。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/39402>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/37362>
* _AC-13537_:[ 問題 ] [PHPDOC] 不正な phpdoc Magento\Framework\App\Config\ScopeConfigInterfaceを修正
   * _修正メモ_：この更新では、getValue および isSetFlag メソッドの$scopeCode 引数のタイプを正確に反映するように、Magento\Framework\App\Config\ScopeConfigInterfaceの PHPDoc アノテーションが修正されます。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/39492>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/39199>
* _AC-8662_: [ 問題 ] cron エラーログの改善
   * _修正メモ_：システムは、cron プロセスの STDERR と STDOUT の両方を取得してログに記録するようになりました。これにより、cron プロセスが失敗した場合に役立つ診断情報が提供されます。 以前は、cron プロセス内のエラーメッセージは記録されず、別のプロセスで実行されている cron グループの STDERR と STDOUT が失われていました。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/37453>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/32690>
* _ACP2E-3230_：外部キーの場合、db_schema.xml を使用した列の長さの変更が機能しない
   * _メモの修正_：宣言型スキーマを使用して外部キーの列を変更しても、MariaDB でエラーが発生しなくなりました
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3361_：注文レコードの保存時に、一部のリレーションレコードが DB に保存されます
   * _メモを修正_：修正前は、不要な UPDATE クエリがトリガーされていましたが、これはパフォーマンスに影響を与える可能性があります。 修正後、不要な UPDATE クエリが削除されました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/1366ae5e>
* _ACP2E-3375_: [CLOUD] 管理者のコンソールには、多くの JavaScript エラーがあります
   * _メモを修正_：以前は、管理パネルのコンソールに多数の Javascript エラーがありました。 これで、管理パネルのコンソールにJavaScript エラーが表示されず、デフォルトのJavaScript機能がすべて問題なく正常に実行されます。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/d75cff27>
* _ACP2E-3387_: [Cloud] Magento: キューメッセージが削除されました
   * _メモの修正_：キューメッセージが正しくクリアされるようになりました。 修正の前は、SQL キューシステムが使用されていたので、クリーニング キューメッセージが同時に実行されている場合は、新しいメッセージが削除される可能性がありました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/d50f6b5d>

### フレームワーク、UI フレームワーク

* _ACP2E-3324_：ロックされていても、設定値を上書きする可能性があります
   * _修正点_：以前は、この修正では、bin/magento config:set コマンドでデザイン設定を設定できず、ロックされた値を表示しているフォームを操作することで変更することができました。 cli で – lock-env または – lock-conf を使用して設定したロックされた値の修正後は、更新できません。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/55615e61>

### GraphQL

* _ACP2E-2974_：カスタマーリターン属性の翻訳が、それぞれの StoreView のGraphQL API に反映されない
   * _修正点_：お客様の返品属性の翻訳は、それぞれのストアビューのGraphQL API に反映されます。
以前は、それぞれの StoreView の Customer Return 属性は、GraphQL API には反映されていませんでした。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/ec7e32a9>
* _ACP2E-3215_：マルチサイト設定でのユーザー認証とクロスサイトトークンアクセスに関する [Cloud] の問題
   * _修正点_：マルチサイト設定での GraphQl 顧客情報および買い物かごクエリで、デフォルト以外の web サイトに顧客が存在するかどうかを確認します。
以前は、クエリは、マルチサイト設定のデフォルト以外の web サイトに顧客が存在することを確認することなく機能していました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3255_: [GRAPHQL] customerCart の取得時には、モデル値を指定する必要があります
   * _修正点_:GraphQLの「customerCart」クエリで、データベースで見積もりが使用できない場合でも、空の買い物かごを作成できるようになりました。 以前は、空の買い物かごの作成中に国の検証の問題が発生したため、この操作は失敗していました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/fd5cf3af>
* _ACP2E-3380_: [GraphQl] ウィッシュリスト項目は、GraphQl 経由では表示されますが、ストアフロントでは表示されません
   * _メモの修正_:GraphQL経由でリクエストした際に、商品が正しくリストされないウィッシュリストを作成します。 現在は、指定されたストアコンテキストに基づいてウィッシュリスト製品がフィルタリングされています。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/55615e61>
* _ACP2E-3404_: [GraphQL] コンテンツと件名/リンクのパスワード E メールの不整合をリセットします
   * _修正メモ_：この問題は、Web サイトストアに関係なく、パスワードリセットリクエストの送信時に、顧客のアカウントが登録されている正しいストアをシミュレートすることで解決されました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3419_: [Cloud] 製品GraphQLのクエリを実行すると、現在の web サイトに割り当てられていない関連製品が返される
   * _メモの修正_：以前は、graphQL クエリの場合、マルチストア関連製品が製品クエリで正しく表示されませんでした。 この修正を適用した後、製品に対して、graphQL はマルチストア関連製品をクエリし、適切に表示します。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3447_:GraphQL ヘッダーに間違ったストア ID を使用すると、致命的なメモリエラーが発生する
   * _修正点_:GraphQL リクエストで間違ったストアコードを送信しても、メモリが過度に消費されなくなりました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/d50f6b5d>
* _ACP2E-3467_:2.4.7 で空の Graphql 応答に対して行われる [Cloud] 500 の応答
   * _修正メモ_：修正後、無効な Graphql リクエストは exception.log ファイルに記録されません。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/1984c61c>

### GraphQL、検索

* _ACP2E-948_：商品リストのGraphQL クエリが total_count 10,000 商品のみに制限される
   * _修正点_：修正後、検索結果が 10000 個の製品に限定されず、カウントが 10000 個を超えても検索条件に一致するすべての製品を取得できるようになります。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/a4cf5e62>

### GraphQL、テストフレームワーク

* _ACP2E-3363_: Magento\GraphQl\App\GraphQlCustomerMutationsTest.php統合テスト エラー
   * _修正メモ_ : 「– 
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/a4cf5e62>

### インポート/エクスポート

* _ACP2E-3172_：読み込みボタンがない
   * _メモの修正_:CSV 内の正しいレコードと正しくないレコードでデータをチェックした後に、「読み込み」ボタンが見つからない問題を解決します。 以前は、CSV 内の正しいレコードと正しくないレコードでデータをチェックした後、読み込みボタンが表示されていませんでした。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/1819fe73>
* _ACP2E-3382_：書き出された顧客住所はインポートできません
   * _メモの修正_：顧客アドレスのインポートは期待どおりに続行されます。 以前は、Share Customer Accounts = Global の場合、顧客住所読み込みファイルが検証に合格せず、デフォルトの Web サイトの国が制限されている Web サイトが 2 つあり、読み込まれる住所が許可されている国が異なる別の Web サイトの住所であった場合です
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/ec7e32a9>
* _ACP2E-3448_: [Cloud] CSV ファイルの誤った数量でエラーが発生しませんでした
   * _メモの修正_：在庫ソースの読み込みが行われると、数量列の数値以外の値に対して検証エラーがスローされるようになりました。 以前は、「数量」列に数値でない在庫ソースを読み込むと、数量が 0 に設定されていました。
   * _GitHub コードの投稿_:<https://github.com/magento/inventory/commit/5b21b7af>
* _ACP2E-3475_：製品の書き出しが原因で、4G メモリ制限があっても OOM が発生する
   * _修正点_：この修正の前は、4G で使用可能なメモリがあっても、製品属性に何千ものオプション値がある場合、製品の書き出しは失敗していました。 この修正後、製品の書き出しが csv ファイルの書き出しを終了する必要があります。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/1984c61c>

### インポート/エクスポート、パフォーマンス

* _ACP2E-3476_: [Cloud] 製品のインポート時間が大幅に長くなりました
   * _修正点_：修正点より前は、10,000 個を超えるエントリを含むカタログ製品の読み込みで、時間が大幅に短縮されていました。 修正後、カタログ製品のインポートはタイムリーに実行されます。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/87d012e5>

### インストールと管理

* _AC-13242_:MariaDB 11.4 + 2.4.8-beta1 でMagentoのアップグレードに失敗する
   * _メモを修正_：アップグレードはエラーなしで行われます。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/7b336d0a>

### インベントリ/MSI

* _ACP2E-3335_: MSI 受け取りストアが有効な場合、注文を出荷できません
   * _修正点_：店頭での受け取りで多くのソースが発生した場合の、作成された配送の在庫パフォーマンスが向上しました
   * _GitHub コードの投稿_:<https://github.com/magento/inventory/commit/9f3e63d1>
* _ACP2E-3355_:Cron の再インデックスで、フロントエンドの製品可用性を更新できない
   * _メモを修正_：以前は、REST API を使用してバックオーダーのステータスを更新した後、製品はフロントエンドで在庫切れのままでした。 REST API を使用してバックオーダーのステータスを更新すると、製品が在庫として表示されるようになりました。
   * _GitHub コードの投稿_:<https://github.com/magento/inventory/commit/e6fe0aa7>
* _ACP2E-3357_:MSI が有効な場合に、設定可能な画像に画像を追加しても機能しない。
   * _メモの修正_：インベントリモジュールが使用される場合、設定可能な製品の画像のアップロードが期待どおりに動作するようになりました。 以前は、画像のアップロードが機能しませんでした
   * _GitHub コードの投稿_:<https://github.com/magento/inventory/commit/fdf409aa>

### インベントリ/MSI、検索

* _ACP2E-3413_:SKU が検索可能な属性として設定されていない場合、すべての製品のインデックスは [is_out_of_stock] = 1 になります
   * _修正点_：修正後、SKU が検索できない場合でも、カタログ検索インデックスの「is_out_of_stock」は正しく表示されます。
   * _GitHub コードの投稿_:<https://github.com/magento/inventory/commit/5b21b7af>

### 順序

* _ACP2E-3311_: [Cloud] デフォルトの請求先住所のみが設定されていない場合、1 つのストアで管理者に注文を作成できない
   * _メモの修正_：関連するエラーメッセージが「同じメールアドレスを持つ顧客が関連する web サイトに既に存在します。」 顧客がデフォルトの請求先住所を持たず、別の店舗で注文を作成しようとすると、が表示されます。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/d75cff27>
* _ACP2E-3416_：管理者が重複した注文リクエストを送信しました
   * _メモの修正_：以前は、管理パネルの「注文を送信」ボタンを複数回クリックするか、「Enter」キーを繰り返し押してアクティブ化すると、重複する送信や注文の送信でエラーが発生する可能性がありました。 オーダーが完全に処理されるまで追加のアクションを防ぎ、1 つのオーダーのみが送信されるようにします。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3425_：管理者は、支払い方法がなくても注文できます
   * _修正注意_：使用可能な支払のリストに支払方法が再び表示される際に、以前に選択した支払方法が保持されるようになりました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/d50f6b5d>

### 注文、支払い

* _ACP2E-3233_：管理者は、支払い方法がなくても注文できます
   * _メモの修正_：以前は、マーチャントは、支払い方法を選択せずに管理パネルから注文を行うことができました。 今、マーチャントは注文を進めるために支払い方法を必要とします。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/fd5cf3af>

### その他の開発者ツール

* _AC-12731_:dev/css/use_css_critical_path と組み合わせた CSP の問題
   * _メモの修正_:「dev/css/use_css_critical_path」設定が有効な場合でも、システムはチェックアウトページで CSS ファイルを非同期で正しく読み込むようになり、これらのページが適切な CSS スタイルでレンダリングされるようになります。 以前は、制限されたコンテンツセキュリティポリシー（CSP）によりインライン JavaScriptが実行できず、CSS ファイルが期待どおりに読み込まれませんでした。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/39020>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/39040>
* _AC-13398_：仮想タイプを使用してプラグインを設定する場合、setup:di:compile コマンドでインターセプターメソッドを正しく生成できない
   * _修正メモ_：仮想タイプを使用してプラグインを設定する際に、システムがインターセプターメソッドを正しく生成し、事前コンパイル済みまたはランタイムコンパイル済みにかかわらず、一貫した結果が得られるようになりました。 以前は、ランタイムのコンパイルと比較して事前コンパイルすると、システムが誤った結果を生成していました。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/33980>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/38141>

### 支払額

* _ACP2E-3143_: PayPal 注文の払い戻しによりクレジット メモが重複する
   * _修正メモ_:PayPal 支払いサービスの IPN 作成クレジットメモの同時実行問題を修正しました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/d01ee51e>
* _ACP2E-3163_:Paypal で買い物かご価格ルールが機能しない
   * _修正注意_：お支払い方法で割引が適用されると、PayPal 側に正しい金額が表示されます
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/7377de59>
* _ACP2E-3208_:[Cloud] 特定の役割を持つユーザーはログインできません
   * _修正点_:PayPal セクションのアクセス権のみを含む役割を持つ管理者ユーザーは、エラーなくログインできるようになりました
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/66dea0de>

### パフォーマンス

* _AC-11932_：デフォルトの製品属性設定の問題
   * _メモの修正_：製品属性のデフォルトオプションの選択を解除できるようになり、属性に必ずしもデフォルトが設定されるわけではありません。 以前は、製品属性にデフォルトが設定されると、選択を解除する方法がなく、属性は常にデフォルトが設定されていました。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/38703>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/7d5e3906>
* _AC-13471_:Magento CLI での Symfony の CommandLoaderInterface のサポート
   * _修正点_：この変更により、必要になるまでコマンドの初期化を延期できるので、Magento CLI アプリの初期化時間が短縮されます。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/29266>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/29355>

### 製品

* _AC-13173_:[ 問題 ]PHPDoc ブロックの誤字を修正
   * _メモの修正_：システムは、$helper 変数宣言の PHPDoc 内の不明な参照変数を正しく削除し、コードの明確さと精度を向上させました。 以前は、PHPDoc 内のこの不明な参照変数が、コードの混乱や不正確な可能性を引き起こしていました。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/38961>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/38940>
* _AC-13423_:[ 問題 ]Magentoのバンドルの破損とダウンロード可能な製品ページのレイアウトが修正されました >= 2.4.7
   * _修正点_：バンドルおよびダウンロード可能な製品ページのレイアウトが修正され、すべてのデバイスで一貫した正しい表示が保証されました。 以前は、これらのページでは、製品情報メディアブロックの配置が変更されたことで、レイアウトの問題が発生していました。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/39403>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/6cfb9b6b>

### プロモーション

* _ACP2E-3139_：割引数量ステップ（購入 X）属性を含む販売ルールが原因で、他のルールが適用されない
   * _修正注意_：カート内の商品の数量がルールを適用するのに十分でない場合、以前に適用されたルールはカート価格ルールによってキャンセルされません。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/d01ee51e>
* _ACP2E-3332_：固定金額割引および「最大数量割引が適用される」販売ルールを発行します
   * _修正メモ_：製品の限られた数量に対して固定金額割引を適用するように設定されている場合、買い物かごルール割引が適用される問題を修正しました。 以前は、「最大数量割引が適用先」の値を使用して、ルールの割引の計算だけでなく、買い物かごでの現在の品目の価格を計算していました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3349_：買い物かごルール「買い物かご全体に対する固定金額割引」  アクションが割引を正しく適用しない
   * _注意を修正_：クーポンコードは、管理領域から注文を作成するために使用される場合、大文字または小文字に関係なく適切に検証されます。 以前は、クーポンコードが設定済みの買い物かごルールコードの大文字と小文字が完全に一致しない場合、そのクーポンコードは検証されませんでした。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3374_：バックエンドでは、（期待される管理値ではなく）製品属性のデフォルトのストア値
   * _メモの修正_：バックエンドでは、製品属性のデフォルトのストア値の代わりに管理値が使用されるようになりました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3377_：買い物かごルール「買い物かご全体に対する固定金額割引」アクションで、バンドル製品を追加する際に、割引が正しく適用されません
   * _修正点_：固定金額の買い物かごルールがバンドル製品に正しく適用されていませんでした。 これで、合計割引額を計算する際に、バンドルの子製品が考慮され、適切な割引計算が行われます。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/1366ae5e>
* _ACP2E-3403_：割引計算の誤った買い物かご価格ルール
   * _修正事項_：固定金額割引が正しく計算されるようになりました。 この修正の前は、バンドル製品の固定金額割引が正しく合計されていませんでした。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/0b488dd1>
* _ACP2E-3406_：ルール条件内のネストされたカテゴリが表示されない
   * _修正メモ_：レベル 3 カテゴリの下にネストされたカテゴリが、カテゴリ条件のマーケティングルールに表示されない問題を修正しました
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/88660e79>
* _ACP2E-3432_: usage_limit および uses_per_customer が salesrule_coupon テーブルで更新されない
   * _修正メモ_：買い物かご価格ルールでクーポンごとの使用状況と顧客ごとの使用状況を更新すると、既存の自動生成クーポンに影響するようになりました。 以前は、新しい値が新しいクーポンにのみ影響していました
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/88660e79>
* _ACP2E-3456_：買い物かごの価格ルールで「次と等しいか、次よりも大きい」条件を使用している場合、親カテゴリが考慮されません。
   * _修正注意_：詳細条件で使用される場合、買い物かご価格ルールが親カテゴリを正しく考慮するようになりました
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/93359343>
* _ACP2E-3463_：優先度の割引計算が無効です
   * _修正注意_：買い物かごの割引タイプ全体に固定金額が適用されている場合、以前のプロモーションで既に割引された買い物かご項目の金額が適切に計算されていませんでした。 今では、割引は正しく合計されます。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3498_：複数の買い物かご価格ルールを割引/特別価格の製品と同時に適用した場合の、誤った割引値
   * _修正点_：修正前は、複数が適用されている場合、買い物かごルール全体の固定金額が適切に適用されていませんでした。 現在、固定金額割引の買い物かごルールが適切に適用されています。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/1984c61c>

### 検索

* _AC-13053_:「検索語句を入力して、もう一度試してください」を取得しています。 2.4.8-beta1 のストアフロントの詳細検索ページでエラーが発生する
   * _メモの修正_：製品属性が「いいえ」に設定されている場合、「詳細検索」ページに検索結果が正しく表示されるようになりました。 以前は、製品属性を「いいえ」に設定して検索を実行すると、「検索語句を入力して、もう一度試してください」というエラーメッセージが表示されていました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/3ea26621>
* _AC-13721_:magento/module-open-search が、存在しない opensearch-php ブランチに依存する
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/05dc0bbf>
* _ACP2E-3362_：サイズが大きい場合、search_query テーブルは読み込み時間のフロントエンドに大きな影響を与えます
   * _メモを修正_：検索リストのページの読み込み時間が改善されました。 この修正を行う前は、クエリが最適化されていないので、検索リストページの表示が遅延していました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/55615e61>

### セキュリティ

* _ACP2E-3273_:ReCaptcha V2 がドイツ語のチェックアウトで正しく表示されません
   * _メモの修正_：以前は、チェックアウトからのメールアドレスの下にある recaptcha は、ドイツ語などの長い単語を含む言語ではスタイルが設定されていないように見えます。 この後、recaptcha は、残りの領域からのすべての recaptcha 要素と同じように見えます。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/7377de59>

### 送料

* _ACP2E-3340_:FedEx Track API が REST 資格情報で機能しない
   * _修正点_：以前の FedEx 統合では、トラッキング API 用に追加の API キーは必要ありませんでした。 トラッキング API キーをサポートする新しい設定が追加されました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/ec7e32a9>
* _ACP2E-3354_: [Cloud] FedEx ネゴシエートされたレートが REST で返されない
   * _修正点_：修正の前は、FedEx のドキュメントに従っても、応答に送信されなかった FedEx アカウント固有のレートが送信されていました。 修正後、アカウント固有のレートは、我々の側からの要求を変更することによって、応答に送信されます。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/55615e61>

### ステージングとプレビュー

* _ACP2E-3453_：一意のカスタムカテゴリ属性を使用している場合は、スケジュールされた更新を更新できません
   * _メモの修正_：カテゴリに一意の属性がある場合、カテゴリのスケジュールされた更新を更新できなかった問題を修正しました
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/078c387e>

### 税

* _ACP2E-3193_：固定製品税（FPT）が設定可能な製品で機能しない
   * _修正点_：設定可能な製品バリエーションの FPT が正しく機能するようになりました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/ec7e32a9>

### テストフレームワーク

* _AC-13362_:[ 問題 ] PHPDoc 修正スペル
   * _修正点_:PHPDoc のスペル修正により、IDE の非推奨メソッドが正しく認識されるようになりました。 以前は、PHPDoc のスペルエラーにより、IDE が特定のメソッドを非推奨として認識しなくなっていました。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/31399>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/31398>
* _AC-13478_:MAGETWO-95118：セッションの有効期限が切れた後に、永続的な買い物かごで動作を確認しています
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/7d5e3906>
* _ACP2E-3458_: [MFTF] StorefrontCheckoutProcessForQuoteWithoutNegotiatedPricesTest
   * _修正点_：修正された mftfs
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/078c387e>

### UI フレームワーク

* _AC-12432_: Ui コンポーネントファイルフィールド
   * _メモの修正_：システムは、UI コンポーネントフォームのファイルフィールドを正しく検証し、ファイルを選択したときにフォームをエラーなしで送信できるようになりました。 以前は、ファイルが選択されている場合でも検証が失敗し、フォームが送信されませんでした。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/38908>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/39004>
* _AC-12645_:[ 問題 ]js コンソールの日付形式が改善されました：12 時間から 24 時間に切り替え…
   * _メモを修正_:js コンソールの日付形式を改善しました：12 時間から 24 時間に切り替えます
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/38983>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/38972>
* _AC-12650_:[ 問題 ] 開発者モードで、より少ないファイル数で sourceMap の生成を追加
   * _修正メモ_：デベロッパーモードの場合、ファイル数の少ないファイルに対してソースマップが生成されるようになり、スタイルのソースを簡単に識別できるようになりました。 以前は、サーバーサイドの LESS コンパイルを使用して開発者モードでシステムを実行する場合、スタイルのソースを特定するのは困難でした。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/38982>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/38977>
* _AC-13459_：最小在庫しきい値を使用した「在庫切れ」の並べ替えで一貫性のない動作が発生する
   * _メモの修正_：システムでは、設定された最小在庫しきい値に準拠し、在庫切れの項目を一貫してリストの下部に移動し、在庫レベルに基づいてカタログ内の製品を正しく並べ替えるようになりました。 以前は、並べ替え動作に一貫性がなく、アイテムが在庫レベルに基づいて正しい順序で表示されないことがありました。また、カテゴリ階層を保存、更新、または変更した後、並べ替えの変更が予期せず発生する可能性がありました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/47b448e2>
* _AC-13472_:require.js の読み込み問題に関するエラーレポートの改善を目的とした提案
   * _修正メモ_：この PR により、requirejs でコンポーネントの読み込みに失敗した場合のエラーメッセージが改善されます。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/36761>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/38971>
* _AC-9168_: [ 問題 ] 不要なスクリプトを削除するレビューの概要
   * _修正点_：より効率的で読み取り可能なコードを提供するために、インライン CSS スタイルを使用する代わりに、評価セクションから不要なJavaScript スクリプトを削除することで、ページの読み込み時間が最適化されるようになりました。 以前は、評価セクションにJavaScript スクリプトを使用すると、ページの読み込み時間が遅くなる可能性がありました。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/37776>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/34643>
* _ACP2E-3367_: サイトヘッダー |お客様からのお知らせセクションを区切る特殊文字
   * _修正点_：修正後、特殊文字が「ようこそ」セクションに正しく表示されます。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/1366ae5e>
