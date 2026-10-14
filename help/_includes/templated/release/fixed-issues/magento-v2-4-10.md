---
source-git-commit: 78a34dc069a30b72a1e0baff36085a2458a05983
workflow-type: tm+mt
source-wordcount: '9924'
ht-degree: 0%
---
# Magento Open Sourceで修正された問題（v2.4.10-alpha1）

## v2.4.10-alpha1で修正された問題

Magento Open Source 2.4.10-alpha1 コアコードの152の問題を修正しました。 このリリースに含まれる修正された問題のサブセットについて、以下で説明します。

### API

#### 文字列の量を持つmin （）によって引き起こされるCreditmemo\Validation\QuantityValidatorの[Issue] TypeError

財務ロギングパイプラインを安定させ、一括自動注文返金中のAPI リクエスト失敗を防ぐために、データタイプのキャスティングガードレールが内部販売クレジットメモ工場と検証レイヤーに追加されました。

_AC-16056 - [GitHub issue](https://github.com/magento/magento2/issues/40302) - [GitHub コード投稿](https://github.com/magento/magento2/pull/40429) - [GitHub コード投稿](https://github.com/magento/magento2/pull/40303)_

#### attribute_idを指定せずにREST API属性の更新が失敗する

attribute_idが指定されていない場合に、REST APIを介して既存の製品属性を更新できない問題を修正しました。 APIがURLからattribute_codeを使用して属性を正しく識別し、正常に更新できるようになりました。

_AC-16424 - [GitHub issue](https://github.com/magento/magento2/issues/40458) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/c10554e1)_

#### REST APIでオプションを更新すると、ビジュアルスウォッチが削除される

カタログデータの整合性を保護し、自動化された統合を合理化するために、EAV スウォッチ管理レイヤーで、標準オプションの更新中に既存のビジュアルまたはテキストスウォッチの値が誤って消去されるバグが解決されました。

_AC-9199 - [GitHub issue](https://github.com/magento/magento2/issues/37794) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/40872)_

#### 1つのSKUが欠落している場合、一括階層価格APIがバッチ全体で失敗する

以前は、ペイロードにSKUが存在しない場合、一括価格更新API （POST /V1/products/tier-prices）がリクエスト全体に失敗し、有効なSKUが更新されずに残っていました。 有効なSKUが正常に処理され、欠落しているSKUがアイテムごとのエラーとして報告されるようになったため、単一の不正なエントリがバッチ全体を中止することはなくなりました。

_ACP2E-4998 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/51f6d191)_

#### 属性の更新が、既存のオプション値IDと一致するラベル値で失敗します

ラベルが既存のオプションのIDに一致する場合に、REST APIを介して新しいドロップダウン/複数選択の製品属性オプションを作成できない問題を修正しました。 以前は、同じオプションをAdmin UIで正常に作成できたにもかかわらず、APIが「既に存在します」エラーを返していました（間違ったオプション IDを返す可能性があります）。

_ACP2E-5107 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/4d0357d7)_

### API、インポートとエクスポート

#### REST APIでは、管理者UIがブロックする間、負の製品価格を許可します

REST API エンドポイントを介した製品の読み込みでは、Admin UIの読み込みの動作と一致して、価格タイプ属性（price、special_price、cost、および関連するMSRP フィールド）に対する負の値が拒否されるようになりました。 以前は、APIは否定的な価格を静かに受け入れ、それらを保持しました。

_ACP2E-4941 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/08b91f1a)_

### API、注文

#### Valkey キャッシュバックエンドと互換性のない注文レート制限機能

以前は、この修正レート制限はサイレントにバイパスされ、設定された制限に関係なく各リクエストが許可されていました。 修正の後、設定された制限を超えるリクエストは、HTTP 429で正しく拒否されます。

_ACP2E-4899 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/9b6a8bd9)_

### アカウント

#### [問題]の修正：ログインフォームのパスワードラベルが正しくありません

顧客ログインページの「パスワード」フィールドに誤ったラベルの関連付けがあった問題を修正しました。 パスワードラベルが「パスワード」フィールドを正しくターゲットにするようになり、自動テストツールで正しく識別できるようになりました。

_AC-16193 - [GitHub issue](https://github.com/magento/magento2/issues/40353) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/64eb754d)_

#### [問題] ファイルのアップロード用にフロントエンド入力タイプを検証する

顧客アドレスファイルのアップロードでは、処理前にターゲット属性の入力タイプがファイルまたは画像であることを検証できるようになりました。そのため、テキストやその他の非ファイル属性をアップロードターゲットとして悪用することはできません。 無効なアップロード試行は、予期せず失敗したり、許可されていないファイルタイプを受け入れたりする代わりに、明確な検証エラーを返します。

_AC-17076 - [GitHub issue](https://github.com/magento/magento2/issues/40795) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/40583)_

#### web サイト Aで生成された顧客トークンは、web サイトのスコープ設定でweb サイト Bで使用できます

複数のweb サイトのインスタンスに対して厳格な顧客データの分離を適用するために、GraphQL認証レイヤーでトークンが別々のバウンダリで誤って検証されていた場合のセキュリティギャップが解決されました。

_AC-17299 - [GitHub issue](https://github.com/magento/magento2/issues/40847) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/40858)_

#### [問題] PHP 8.5の非推奨化を修正：array_key_exists （）のキーパラメーターとしてnullを使用する

PHP 8.5で、ゲストチェックアウト中に顧客ログインが失敗する問題を修正しました。これは、null キーを持つ非推奨のarray_key_exists （）呼び出しによるものです。 顧客ログインが非推奨エラーを生成せずに正常に動作するようになりました。

_AC-17395 - [GitHub issue](https://github.com/magento/magento2/issues/40875) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/515d3dd3)_

#### [問題] magento/magento2: requestPasswordResetEmailおよびresetPassword GraphQLのミューテーションにi18翻訳を追加します

完全にローカライズされたヘッドレスストアフロント体験を実現するために、国際化（i18n）翻訳機能が顧客アカウント回復API エンドポイントに追加されました

_AC-9356 - [GitHub issue](https://github.com/magento/magento2/issues/29658) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/28950)_

### 管理者UI

#### 集計データを使用する場合、ダッシュボードにはデフォルトで「過去7日間」と表示されます

集計販売データが有効になっている場合に、ダッシュボードに「今日」がデフォルトで表示される問題を修正しました。 集約データを使用する場合、ダッシュボードにデフォルトで「過去7日間」が表示されるようになりました。

_AC-13799 - [GitHub issue](https://github.com/magento/magento2/issues/28152) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/29a7cdbe)_

#### 買い物かごページと商品ページのFPT値は、単純な商品の同じ設定で異なります

同じ税構成の製品ページと買い物かごページで、固定製品税（FPT）の値が異なって表示される問題を修正しました。 FPT値は、製品、カタログ、ミニカート、およびショッピングカートのページ全体で一貫して表示されるようになりました。

_AC-17007 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/ecbeba3a)_

#### 遅延設定の実装

既存の設定動作を維持しながら、スコープを設定したシステム設定データを遅延解決することで、設定の読み込みパフォーマンスを向上させるパフォーマンス最適化。

_ACP2E-4751 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/65f660bd)_

#### HugeRTE エディターが絵文字をブロック - JavaScriptの検証に失敗しました

PageBuilder コンテンツタイプモーダル（テキスト、バナー、スライド）内で編集する際に、utf8mb4絵文字（例：🔵⚪🔴）を含むコンテンツの保存がHugeRTEによってブロックされる問題を修正しました。 以前は、これらのモーダルフォームのwysiwyg検証設定で`allowUtf8mb4`が`false`に解決されたため、データベースがutf8mb4を完全にサポートしているインストール環境でも、エディターが4 バイトのUTF-8文字を拒否していました。

_ACP2E-4822 - [GitHub コードの貢献度](https://github.com/magento/magento2-page-builder/commit/f2691e17)_

#### 管理パネルの顧客編集ページで、大きなアドレス帳を持つ顧客を表示すると、管理者がログアウトする

管理パネルの顧客編集ページで大きなアドレス帳を持つ顧客を表示する際に、管理者がログアウトする問題を修正しました

_ACP2E-4875 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/b63925d9)_

#### 受注がSales Gridに表示されない

非同期グリッドインデックスが有効になっている場合に、最新のエンティティに達した後に紐付けカーソルがリセットされ、新しい注文がセールスグリッドに表示されるのが遅くなる問題を修正しました。 次のcron実行時に、新しいエントリがグリッドに表示されるようになりました。

_ACP2E-4893 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/b63925d9)_

### 管理者UI、注文

#### 2つのグループ化された製品が同じシンプルな製品を共有する場合、管理者作成オーダーでグループ化された製品に表示される価格が正しくありません

同じシンプルな製品を共有する2つのグループ化された製品が両方とも買い物かごに追加されずに設定された場合に、管理者作成オーダーのグループ化された製品の価格が誤って計算される問題を修正しました。

_ACP2E-4965 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/08b91f1a)_

### 管理者UI、UI フレームワーク

#### Magento2は、間違ったメニュー宣言でエラーを表示するのではなく、ホームページにリダイレクトします

拡張機能の開発ワークフローを最適化し、安定したバックエンド読み込みを確保するために、構造的ルーティングの欠陥が解決されました。無効な管理者メニューの宣言が、実用的な診断メッセージを表示するのではなく、サイレントブラウザーループの失敗を引き起こしました。

_AC-7543 - [GitHub issue](https://github.com/magento/magento2/issues/36632) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/40881)_

### 分析/レポート

#### [QUANS]高度なレポートで、顧客の電子メール IDと名前を顧客KPI テーブルに表示できます

Adobe Commerceでは、高度なレポートに書き出されたデータに、お客様の名前、名前、姓が含まれるようになり、お客様のKPI テーブルに顧客名が表示されるようになりました。 以前は、エンコードされた顧客識別子のみが書き出されたため、詳細レポートで顧客を名前で識別できませんでした。

_ACP2E-3928 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/4d0357d7)_

#### sales_bestsellers_aggregated_monthlyの重いINSERT

aggregate_sales_report_bestsellers_data cronのパフォーマンスが向上しました。

_ACP2E-4559 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/8d95ae6e)_

#### カートに追加イベントペイロードは、GA4のe コマース形式ではなく、従来のUniversal Analytics Enhanced E コマース形式です。

この問題を解決する前は、Google Tag Managerを通じてGoogle Analytics 4に送信されたe コマースイベントは、従来のUniversal Analytics形式を使用しており、複数のチェックアウトイベントがありませんでした。 この問題を修正した後は、すべてのコマースイベントで正しいGA4 フォーマットが使用され、funnelのチェックアウト全体が追跡されます。

_ACP2E-5176 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/24667df1)_

### B2B，注文

#### 5900万以上の見積もりテーブルのクリーニングに関するヘルプ （sales_clean_quotesを実行できません）

`sales_clean_quotes` cron ジョブが大きな見積もりテーブルを含むインスタンスでタイムアウトする問題を修正しました。 以前は、クリーンアップクエリで`negotiable_quote` テーブルのすべての列が不必要に選択されたため、MySQLは数百万行に対して完全なファイルソートを実行し、各引用符はPHP モデルレイヤーを介して個別に削除され、パフォーマンスコストが増大しました。

_ACP2E-4891 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/b63925d9)_

### カート/チェックアウト

#### 関連製品の「カートに追加」通知

製品とその関連製品を一緒に追加する際に、「カートに追加」通知に関連製品が含まれていない問題を修正しました。
通知に、カートに追加された両方の製品の名前が表示されるようになりました。

_AC-11976 - [GitHub issue](https://github.com/magento/magento2/issues/27164) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/515d3dd3)_

#### [問題]更新CartRepositoryInterface.php

CartRepositoryInterface.phpを更新して、カートを保存するときにスローできる例外を宣言しました。 これにより、インターフェイスは、基礎となるカート保存の実装と一貫性を保ちます。

_AC-13323 - [GitHub issue](https://github.com/magento/magento2/issues/39328) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/29a7cdbe)_

#### チェックアウトの配送手順で新しい住所を追加する際に、マルチストア設定で配送先住所の[Bug]会社フィールドがnullに設定される

複数ストアの設定でチェックアウト時に顧客が新しい配送先住所を追加したときに、「会社」フィールドが保存されない問題を修正しました。 会社の値が、見積もり、注文、顧客アドレス帳に正しく保存されるようになりました。

_AC-13456 - [GitHub issue](https://github.com/magento/magento2/issues/39424) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/515d3dd3)_

#### Paypal/顧客データの不一致（接頭辞、名、姓）

PayPal SEPA チェックアウトフロー中に顧客名の詳細が正しくマッピングされない問題を修正しました。 接頭辞、名、姓が、不一致のない順序で正しく入力されるようになりました。

_AC-15366 - [GitHub issue](https://github.com/magento/magento2/issues/39061) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/ecbeba3a)_

#### バーチャル製品のfree_shipping フラグが正しくありません

複数のアイテムがカートに追加された場合に、仮想製品に対してfree_shipping フラグが正しく設定されない問題を修正しました。 該当する送料無料ルールが適用されると、すべてのアイテムに対してフラグが正しく設定されるようになりました。

_AC-15648 - [GitHub issue](https://github.com/magento/magento2/issues/40184) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/c10554e1)_

#### Guest add-to-cart: mini-cart / customer-data &quot;cart&quot; section under-reports cart as empty despite item being correctly persisted

商品をカートに追加した直後に、ゲストミニカートに商品が反映されない問題を修正しました。 ミニカートカウンターとドロップダウンが正しく更新され、追加された製品がカートに正常に表示されるようになりました。

_AC-17973 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/2b218686)_

#### AJAX add-to-cart インラインエラーメッセージ lost role=&quot;alert&quot; semantics

AJAXのカートへの追加のエラーメッセージがストアフロントに表示されたが、スクリーンリーダーから通知されない問題を修正しました。 適切なアクセシビリティサポートのために、カートへの追加エラーがaccess role=&quot;alert&quot; リージョン内に表示されるようになりました。

_AC-18036 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/2b218686)_

#### 出荷金額に対する後続のルールを破棄する

正確なプロモーション価格と、設定された割引ルールへの厳格な準拠を確保するために、ショッピングカートの価格ルール計算機の欠陥が解決され、優先度の低い配送割引が誤って適用されました

_AC-9612 - [GitHub issue](https://github.com/magento/magento2/issues/37985) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/40869)_

#### エラーがトリガーされたにもかかわらず、作成された注文が重複する

無効な顧客アドレスで注文が引き続き行われる問題を修正しました

_ACP2E-4774 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/8d95ae6e)_

#### Configurable Product&#39;s Performance Impact on checkout （totals-information, estimate-shipping-modules）

修正の前に、合計情報や見積もり出荷方法などのチェックアウトリクエストが、最初の販売可能な子が子リストの後半に表示されたときに、多くの子製品を含む設定可能な製品で大幅に遅くなる可能性があります。 修正後、このパフォーマンスの低下は発生しなくなり、最初のセールス可能な子の位置に関係なく、応答時間は一貫したままになります。

_ACP2E-4805 - [GitHub コードの貢献度](https://github.com/magento/inventory/commit/30fbdb0f)_

#### 買い物かごの合計は、すべての買い物かごのページビューで再計算されます

最適化されたカートは、カートページでのリクエストを集計します。 買い物かごの合計は、買い物かごのページビューごとに2回再計算されます。

_ACP2E-4817 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/b63925d9)_

#### 顧客アドレス属性（EAV）の市区町村およびストリートの検証ルールが、ハードコードされた検証ルールと競合しています。

市区町村検証者が100文字を超える有効な市区町村名を誤って拒否し（データベースの制限は255）、255文字を超える住所がデータベース内でサイレントに切り捨てられる問題を修正しました\
検証エラーを返します。 両方のバリデータは、すべてのアドレステーブルで最も狭いデータベース列の制約に沿った制限を適用するようになりました。

_ACP2E-4861 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/b63925d9)_

#### [Storefront] カートに追加する「リクエストされた数量は使用できません」というメッセージがPDPで断続的にレンダリングされない

在庫切れメッセージ（「リクエストされた数量は利用できません。数量を減らしてください。」）が表示される問題を修正しました。 カートへの追加に失敗した後、製品の詳細ページに断続的に表示されませんでした。 以前は、買い物客が既にカートで全額予約されている商品の「カートに追加」を繰り返しクリックしても、エラーフィードバックがなくても、ページをサイレントに更新することができました。

_ACP2E-5071 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/8d70f246)_

#### ログアウト時の永続性をクリア =はい場合、自然なセッションの有効期限でクリアされた永続的なショッピングカート

ブラウザーのセッションの有効期限が切れたときに永続的なショッピングカートがクリアされる問題を修正しました。 以前は、ログアウト時の永続性をクリアを有効にすると、有効期限が切れたセッションでカートが空になり、買い物客がログアウトしていなくても永続的なCookieが削除されていました。

_ACP2E-5088 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/597c7211)_

#### チェックアウトの再試行時にrestoreQuote （）後にゲストの見積もりcustomer_emailが請求先住所から再同期されない

失敗したゲストチェックアウトを再試行すると、更新された電子メールではなく、以前に入力した電子メールで注文が行われる問題を修正しました。

_ACP2E-5188 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/597c7211)_

### カート&amp;チェックアウト、GraphQL

#### Quote GraphQL APIは、ISO通貨コードではなく通貨オブジェクトを引用フィールドに割り当てることができます

Quote GraphQL APIを更新して、通貨オブジェクトを割り当てる代わりに、見積書のストアと見積通貨フィールドにISO通貨コードを割り当てました。

_ACP2E-5229 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/24667df1)_

### カタログ

#### Magento_ConfigurableProductGraphQl、Magento_MsrpConfigurableProduct、Magento_NewRelicReportingおよびMagento_Swatches モジュールの[Issue] module.xml ファイルの改善。

4つのコアサブモジュールから冗長なMagento_Catalog依存関係を削除することで、モジュール宣言アーキテクチャを最適化しました。 このクリーンアップは、依存関係ツリーの不要な重複に対処し、モジュールの読み込み順序の計算を合理化し、壊れた変更を導入することなく、長期的なフレームワークのメンテナンス性を向上させます。

_AC-10762 - [GitHub issue](https://github.com/magento/magento2/issues/30675) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/30638)_

#### 設定可能なgetUsedProducts関数でメモリリークが発生する可能性があります

複数の設定可能な製品を処理すると、実行時間とメモリ使用量が時間の経過とともに増加する問題を修正しました。
プログレッシブスローダウンやメモリの増加を回避しながら、設定可能な製品を処理できるようになりました。

_AC-10942 - [GitHub issue](https://github.com/magento/magento2/issues/37639) - [GitHub コードの貢献度](https://github.com/magento/inventory/commit/8c058c2e)_

#### アンカー以外のカテゴリに表示されるカテゴリ別のショッピング フィルター

管理画面でカテゴリーフィルターが無効になっている場合でも、アンカー以外のカテゴリに「カテゴリで買い物」フィルターが表示される問題を修正しました。
設定された設定に従って、フィルターがストアフロントで非表示になりました。

_AC-10945 - [GitHub issue](https://github.com/magento/magento2/issues/38379) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/64eb754d)_

#### 見積と見積アイテムのapplied_rule_idsのデータ・タイプが異なる

絶対的なデータベーススキーマの一貫性を確保し、大規模なプロモーションストアでの重要なカートデータのミスマッチを防ぐために、アクティブなプロモ – ション定義を追跡するデータ列が親チェックアウト構造全体に拡張されました。

_AC-14518 - [GitHub issue](https://github.com/magento/magento2/issues/39838) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/40540)_

#### 価格がグローバル スコープの場合、製品コレクション スコープの`decimal`属性を取得できません

正確なストアフロントの価格設定と国際設定での属性レンダリングを確実に行うために、ストア固有の小数点以下の値がデフォルトのグローバル値に誤って置き換えられた場合のコアデータ収集のバグが解決されました。

_AC-15806 - [GitHub issue](https://github.com/magento/magento2/issues/40218) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/40419)_

#### GET パラメーターの処理が正しくない

プラットフォームの安定性を向上させ、チェックアウト funnelを保護するために、ブロックレベルの入力検証レイヤーが追加され、形式が正しくないURL クエリがストアフロントの商品ページをクラッシュするのを防ぐことができます。

_AC-16262 - [GitHub issue](https://github.com/magento/magento2/issues/40405) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/40433)_

#### Magento\SalesRule\Model\Plugin\QuoteConfigProductAttributes::afterGetProductAttributesがすべての買い物かごクエリでトリガーされます

顧客チェックアウト時にデータベースの実行の負担を軽減し、最適化されていないデータベースヒットを排除するために、セールスルール製品設定プラグインが最適化され、条件付きで実行され、キャッシュ構造を活用できるようになりました。

_AC-16559 - [GitHub issue](https://github.com/magento/magento2/issues/40226) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/40251)_

#### [問題] [PHPDOC]関数orderCommentをMagento\Sales\Model\Orderで修正

厳格なタイピング制限を排除し、静的分析精度を高め、PHPStan （レベル 5以上）などの厳格なリンティングエンジンの下で開発者エクスペリエンスを向上させるために、インライン構造文書ブロックがセールスオーダーのコアサブシステム内で標準化されました。

_AC-16759 - [GitHub issue](https://github.com/magento/magento2/issues/39575) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/39572)_

#### [問題] [ バグ ] GraphQL SearchCriteriaValidatorが読み込まれていません – module-graph-ql di.xml配列の上書きによって削除されました

強固なクエリ検証を維持し、プラットフォームガードレールを適用するために、SearchCriteriaValidator レイヤーが誤って無効になっている依存関係インジェクション（DI）設定の欠陥が解決されました。

_AC-16959 - [GitHub issue](https://github.com/magento/magento2/issues/40762) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/40742)_

#### strpos （）はパラメーター1を文字列として指定します| magento/module-eav

ストアフロントの安定性を保護し、中断のない顧客発見体験を提供するために、高度なカタログ検索処理エンジン内で重大なタイプ不一致の欠陥が解決されました。

_AC-1706 - [GitHub issue](https://github.com/magento/magento2/issues/33588) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/40422)_

#### 顧客がページにアクセスすると、空の見積もりレコードが作成される

ストアフロントで製品ページを訪問しても、空の見積もりレコードが作成されない場合があります。
以前は、顧客がストアフロントの商品ページにアクセスすると、空の見積もりレコードが作成されていました

_ACP2E-4682 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/8d95ae6e)_

#### 製品の詳細ページ「Weight」属性に「Additional Information」セクションの単位サフィックスが表示されない

Storefront製品ページのWeight属性で、設定された測定単位（lbsまたはkgs）を使用せずに、「追加情報」または「詳細情報」セクションに生の数値のみが表示される問題を修正しました。

_ACP2E-4808 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/b63925d9)_

#### [Cloud] カタログの価格ルールのアクティベーションは、次の強制再同期までライブサーチに反映されません – 価格フィードの同期遅延

カタログ価格ルールをアクティブ化しても、後で強制的に再同期するまでライブサーチの価格が更新されない問題を修正しました。 価格フィードのインデクサーは、カタログルールインデクサーが終了した前に実行される可能性があります。そのため、書き出された古い価格が実行されます。 未完成の依存関係を持つインデクサーは、次のcron実行に延期されるようになったため、価格フィードは常に最新の価格に対して実行されます。

_ACP2E-5029 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/ec436b10)_

#### 新しく追加された製品画像の代替テキスト（ラベル）が保存されない

メディアギャラリーでのファイル名の競合により、アップロードしたファイルの名前が保存時に変更されたときに、新しくアップロードした製品画像の代替テキスト（ラベル）が保存されない問題を修正しました。 以前は、画像ロールの属性（image、small_image、サムネール）は正しく保存されていましたが、対応する*_ラベル属性はサイレントにドロップされ、ストアフロントの検索ページとリストページでは代替テキストが空のままでした。 ギャラリー作成ハンドラーは、名前が変更されたファイルを元の画像エントリに戻すため、割り当てられたすべての画像ロールに対してラベルが保持されます。 これにより、製品作成時に入力された代替テキストが、ストアフロント全体で確実に保存およびレンダリングされます。

_ACP2E-5216 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/24667df1)_

#### PHP 8.5 &quot;null as array offset&quot;の非推奨化エラーがユーザーに「製品ステータスを編集」リソースが不足している場合に管理者で「製品を追加」ページを開く

以前は、「製品ステータスを編集」権限を持たない管理者ユーザーが製品を追加ページを開くと、「配列オフセットとしてnull」非推奨エラーが発生する可能性がありました。 これは、ユーザーの製品ステータス権限に関係なく、ページが正しく読み込まれるように修正されました。

_ACP2E-5248 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/24667df1)_

### カタログ、GraphQL

#### [GraphQl]製品のクエリ価格フィルターの問題で、adminhtmlに入力された正味価格

価格フィルターを適用する際にGraphQL製品クエリで税金が考慮されない問題を修正しました。
価格フィルターで表示される税込み価格が使用されるようになったため、指定された価格範囲内の商品のみが返されます。

_AC-6883 - [GitHub issue](https://github.com/magento/magento2/issues/36337) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/8b67e8ed)_

### カタログ、SEO

#### すべてのストアビューのurl_key変更でカテゴリ url_pathが同期されない

以前は、「すべてのストアビュー」スコープでカテゴリのURL キーを変更すると、ストア範囲の下位カテゴリに古いurl_pathまたは不正確にプレフィックスされたurl_pathが残る可能性があり、独自のストア固有のurl_path オーバーライドを使用してカテゴリを編集すると、新しく入力したURL キーではなく、編集前のURL キーが取得される可能性がありました。 これは修正されました。URL キーは、正しい親パスを持つ適切な階層順にすべてのストア スコープの子孫に正しくカスケード変更され、カテゴリ独自のストア スコープのurl_path オーバーライドは、変更されたばかりのURL キーを使用して再計算されるので、ストア スコープ URLは保存後すぐに正確な状態を維持します。

_ACP2E-5113 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/597c7211)_

### クラウド，フレームワーク

#### SymfonyL2を有効にしたパフォーマンス回帰と誤ったキャッシュストレージ

L1 キャッシュストレージパスを絶対パス（/dev/shmなど）として設定すると、var/ ディレクトリにサイレントにリダイレクトされる問題と、大きなカタログのキャッシュタグを無効にすると、Redis操作のブロックにより応答時間が大幅に遅れる可能性がある別のパフォーマンス問題を修正しました。

_ACP2E-4989 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/51f6d191)_

### コンテンツ

#### ページビルダーのajax プレビューリクエストで、翻訳キャッシュが無効な場合に500 エラーが返される

翻訳キャッシュが有効か無効かにかかわらず、PageBuilder プレビューが正しくレンダリングされるようになりました。 以前は、翻訳キャッシュが無効になっている場合、PageBuilder プレビューをレンダリングできませんでした。

_ACP2E-5118 - [GitHub コードの貢献度](https://github.com/magento/magento2-page-builder/commit/606e12fd)_

#### 古いメディアギャラリーを有効にすると、Animated GIFのアップロードがPNGに変換されます

従来のメディアギャラリーが有効になっている場合に、メディアギャラリーを介してアップロードされたGIFのアニメーション画像がPNGに変換される問題を修正しました。 以前は、「フロントエンドのサイズ変更を有効にする」をオンにすると、古いメディアギャラリーを通じてアップロードされたアニメーション GIFがアニメーションを失い、静的なPNG ファイルとして保存されていました。 アニメーション GIFがアップロードされ、元の形式で保存されるようになりました。

_ACP2E-5232 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/24667df1)_

### コンテンツ / CMS

#### [問題]画像属性ラベルに単一の見積もりが含まれている場合の製品ギャラリータブの修正

管理パネルで信頼性の高い中断のないカタログ管理エクスペリエンスを実現するために、バックエンドのプロダクトワークスペースのインターフェイスが完全に破損するJavaScriptのフォーマットの欠陥が解決されました

_AC-16474 - [GitHub issue](https://github.com/magento/magento2/issues/40519) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/40870)_

#### [問題] サイズ変更された画像URLにアクセスしたが、まだ存在しない場合のパフォーマンスを改善します。

アセット配信の応答性を最大化し、サーバーディスク I/Oを大幅に削減し、サーバープロセッサーの重大なスパイクを防ぐために、カタログ画像生成サブシステムは、不足しているメディア URLをオンデマンドで厳密に処理するように最適化されています。

_AC-16547 - [GitHub issue](https://github.com/magento/magento2/issues/40399) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/40388)_

#### 回帰：UTF-8でエンコードされていないURI コンポーネントは、2.4.7-p5のCatalogWidgetで「値をシリアル化できません」をスローします

不適切な実稼動web トラフィックに起因する重大なレンダリング失敗を排除するために、カタログウィジェットブロックが強化され、要求されたURL内でUTF-8以外のデータシーケンスを適切に処理できるようになりました。

_AC-17264 - [GitHub issue](https://github.com/magento/magento2/issues/40824) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/40825)_

#### グローバル デザイン設定スコープの編集時に`Using null as an array offset is deprecated, use an empty string instead`

コンテンツ/デザイン/設定でグローバルスコープを編集すると、非推奨のnull配列オフセットが原因で、PHP 8.5でHTTP 500 エラーが返される問題を修正しました。 エラーなしでグローバルデザイン設定が正常に開くようになりました。

_AC-17456 - [GitHub issue](https://github.com/magento/magento2/issues/40886) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/515d3dd3)_

### フレームワーク

#### メディア DB ストレージが使用されていないか無効になっている場合は、media_storage_file_storageからSELECTします

不要なデータベースクエリのオーバーヘッドを削減し、システムのノイズの多いシステム例外を排除するために、メディアファイル同期レイヤーは、システムがローカルファイルシステムを使用するように明示的に設定されている場合に、データベースストレージチェックをバイパスするように最適化されています

_AC-10586 - [GitHub issue](https://github.com/magento/magento2/issues/38116) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/40480)_

#### cookie ストアが配列の場合、例外コンストラクターで致命的なエラーがスローされます

無効なstore cookie値がPHPの致命的なエラーを引き起こす問題を修正しました。
ストア Cookieに無効な値が含まれている場合、「無効なストアパラメーター」例外が正しくスローされるようになりました。

_AC-10888 - [GitHub issue](https://github.com/magento/magento2/issues/38365) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/7aecc9f1)_

#### [問題] Magento\Customer\Model\Address\Configで静的な定数を使用

カスタムアドレス設定クラスで、カスタムアドレステンプレートパスを使用するためにgetFormats （）を複製する必要があった問題を修正しました。 カスタムアドレス設定では、メソッドを複製することなく、静的定数を使用して独自のテンプレートパスを定義できるようになりました。

_AC-12906 - [GitHub issue](https://github.com/magento/magento2/issues/39135) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/29a7cdbe)_

#### 製品コレクションでprocessFilterを使用できません

FilterProcessorを使用して製品コレクションに複数のフィルターを適用すると、PHP エラーが発生する問題を修正しました。 複数のフィルター条件を使用して、製品コレクションを正しくフィルタリングできるようになりました。

_AC-15018 - [GitHub issue](https://github.com/magento/magento2/issues/40014) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/7aecc9f1)_

#### 大きなカタログのインデクサーパフォーマンスに関する潜在的な問題 – CL テーブル全体を一括挿入してロックし、最新バージョンを特定する

大規模なエンタープライズ規模のカタログでデータベースのパフォーマンスを保護するために、システムデータベースインデクサーパイプラインを強化して、スケジュールされたデータ変更をバウンドバッチで解析し、高圧のデータベースロックを排除しました。

_AC-16238 - [GitHub issue](https://github.com/magento/magento2/issues/40331) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/40546)_

#### [問題] パフォーマンスの向上

不要なメモリ割り当てを排除し、ランタイム処理のオーバーヘッドを削減するために、最適化されたPHP ネイティブ動作を利用するために、いくつかのコア文字列操作ルーチンがリファクタリングされました。

_AC-16565 - [GitHub issue](https://github.com/magento/magento2/issues/40383) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/40375)_

#### [問題]非GNU Linux システムでのGLOB_BRACEのサポートの修正

軽量な仮想化環境全体でシームレスなデプロイメント機能を保証するために、Alpine Linux Docker イメージなどの非GNU ライブラリを使用するシステムの実行サポートを完全に復元するクリティカルパス検出バグが修正されました。

_AC-16568 - [GitHub issue](https://github.com/magento/magento2/issues/40552) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/40538)_

#### 組み込みのFPC IDの作成に使用されるクエリにマーケティングパラメーターを追加

キャッシュヒット率を改善し、サーバーのパフォーマンスのリグレッションを排除するために、ネイティブの組み込みフルページキャッシュ（FPC）システムで、マーケティングクエリパラメーターとトラッキングクエリパラメーターが誤ってキャッシュ ID署名に再導入された構造的な欠陥が修正されました。

_AC-16583 - [GitHub issue](https://github.com/magento/magento2/issues/40350) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/40349)_

#### メッセージキュー通信にプロモートされたプロパティを持つプレーンオブジェクトのサポートを追加します

最新のPHP開発プラクティスをサポートし、非同期アーキテクチャワークフローを簡素化するために、フレームワークリフレクションエンジンが強化され、パブリック、プロモート、および読み取り専用のコンストラクタープロパティを使用してデータ転送オブジェクト（DTO）をネイティブに処理できるようになりました。

_AC-16672 - [GitHub issue](https://github.com/magento/magento2/issues/36660) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/40457)_

#### [問題]修正：実際の列タイプのイントロスペクションで、未署名/null可能なプロセッサがスキップされ、デフォルトが使用される

正確なシステム設定トラッキングを確実に行うために、明示的な精度またはスケール属性を欠くDOUBLE UNSIGNED列に対して、宣言型スキーマ検証コマンドが永続的に保留中の変更変更が報告されるデータベース抽象化欠陥が解決されました。

_AC-16758 - [GitHub issue](https://github.com/magento/magento2/issues/40646) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/40582)_

#### [機能]管理者設定の個々の選択オプションの「無効」状態をサポート

バックエンドフォームの柔軟性を高め、詳細なレイアウト制御を開発者に提供するために、フォームレベルのサポートが導入され、個々のオプションタグをフォーム要素内で選択不可としてマークできるようになりました。

_AC-16761 - [GitHub issue](https://github.com/magento/magento2/issues/40564) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/40565)_

#### ⚡ パフォーマンス：StoreManagerのメモが見つからず、Store モジュールのプラグインのオーバーヘッドが発生しています

CPUの実行負荷を大幅に軽減し、不要なアプリケーションメモリの解約を最小限に抑えるために、冗長なストアチェックプロセスを傍受するクリティカルコンフィギュレーション値キャッシングルーチンが実装されました。

_AC-16838 - [GitHub issue](https://github.com/magento/magento2/issues/40706) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/40732)_

#### [問題]の修正：JwkFactoryで停止しているopenssl_free_key （） コードパスを削除します

構造的な技術の負債をクリーンアップし、暗号化ツールを最新の実行プロファイルに合わせるために、従来のリソースを解放するフックがJSON Web キーユーティリティのバックエンドからパージされました。

_AC-16958 - [GitHub issue](https://github.com/magento/magento2/issues/40761) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/40688)_

#### [問題] PHPDoc修正スペル

高いコード品質基準を維持し、統合開発環境（IDE）コードヒント精度を向上させるために、コアフレームワークモジュール全体のインラインコードドキュメントレイヤーに構造的クリーンアップが適用されました。

_AC-16960 - [GitHub issue](https://github.com/magento/magento2/issues/40763) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/40745)_

#### [問題] perf （di:compile）: Type、Config/ReaderおよびClassReaderのReflectionClass インスタンスをキャッシュします

コンパイル時間を大幅に短縮し、継続的インテグレーション （CI） デプロイメントのスループットを最大化するために、内部依存関係インジェクション コンパイラ バックエンド （`setup:di:compile`）が最適化され、冗長なPHP リフレクション サイクルが排除されました。

_AC-17077 - [GitHub issue](https://github.com/magento/magento2/issues/40796) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/40615)_

#### [問題] Filter.phpを更新して`{{block template="Magento_Module::path/to/template.phtml"}}`を許可し、\Magento\Framework\View\Element\Templateを既定のクラスとして設定します

コンテンツ作成を簡素化し、CMS ディレクティブをテンプレートレイアウト標準に合わせるために、コアマークアップタグ処理システムが強化され、明示的なクラス定義なしでブロック宣言をサポートするようになりました。

_AC-17078 - [GitHub issue](https://github.com/magento/magento2/issues/38477) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/38469)_

#### [問題] perf （di:compile）: コンパイル中にインターセプト設定スコープをメモリ化します

サイトのデプロイとバックエンドの自動コンパイルを大幅に高速化するために、依存関係インジェクションコンパイラ （`setup:di:compile`）が最適化され、冗長なXML解析操作がなくなりました。

_AC-17313 - [GitHub issue](https://github.com/magento/magento2/issues/40852) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/40614)_

#### セキュリティ脆弱性を防ぐため、underscore.jsを1.13.8にアップグレードします

バンドルされたUnderscore.js ライブラリ（lib/web/underscore.js）が1.13.7から1.13.8にアップグレードされました。設定変更は必要ありません。

_AC-17349 - [GitHub issue](https://github.com/magento/magento2/issues/40857) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/12d0be1e)_

#### デプロイ先がシンボリックリンクの場合、magento-composer-installerはsetup/（およびその他のマッピングされたdir）を入力せずに残します

デプロイメントの宛先がシンボリックリンクとして設定されている場合、magento-composer-installerがsetup/およびその他のComposer-mapped ディレクトリへの入力に失敗する問題を修正しました。 これにより、ファイルが欠落し、Commerceのデプロイメントが不完全になる可能性があります。

_AC-17360 - [GitHub issue](https://github.com/magento/magento2/issues/40864)_

#### Symfony Cache アダプタを使用する際に、キャッシュプリロードキーにID プレフィックスが不要になりました

Symfony Cache アダプタのプリロードキー（preload_keys）を、キャッシュ ID_prefixなしで設定できるようになりました。 以前は、文書化された設定に従い、各キーのプレフィックス（061_SYSTEM_DEFAULTなど）を含めると、キーがプリロードされなくなっていました。 アプリケーションが要求するキー（SYSTEM_DEFAULTなど）を正確に指定できるようになり、Adobe Commerceはid_prefixを自動的に適用するようになりました。

_AC-17407 - [GitHub issue](https://github.com/magento/magento2/issues/40877) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/3a6b9667)_

#### [問題] カテゴリ属性に「frontend_input」がある場合のPHP 8.5の非推奨化を修正します…

カテゴリ属性にfrontend_inputがnullに設定されていた場合、管理パネルでカテゴリを開くとPHP 8.5でエラーが発生する問題を修正しました。 カテゴリーページが開き、非推奨エラーなしで正常に編集できるようになりました。

_AC-17499 - [GitHub issue](https://github.com/magento/magento2/issues/40908) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/ecbeba3a)_

#### [問題]非推奨のPHPUnit アサーションとtest-stub設定を置き換えます

Magento 2のコアユニットテストスイートを更新し、非推奨の7つのPHPUnit使用を置き換えて、将来のPHPUnit アップグレードに対応しました。 この変更は、テストスタブの`isType()`のアサーションと`with*()`の設定に対応しています。このパターンは、現在のPHPUnit バージョンではトリガーの非推奨化が通知され、PHPUnit 13以降では削除される予定です。

_AC-17750 - [GitHub issue](https://github.com/magento/magento2/issues/41040) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/41033)_

#### GraphQL order_dateおよびcommentのタイムスタンプがen_US以外のロケールで間違ったカレンダー日付を返す（IntlDateFormatterの誤解析） — AC-14431修正が不完全

GraphQLの注文日で、フランス語とドイツ語のロケールに誤ったカレンダー日付が表示される問題を修正しました。
注文日と関連するコメントのタイムスタンプが、正しい日時を返すようになりました。
GraphQLの日付値をアプリケーションで確実に解析できるように、日付形式を改善しました。
en_US ロケールの既存の動作は変更されません。

_AC-18084 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/d10ab92b)_

#### [問題]禁止されている@author タグを削除

中核となる技術ガイドラインとの厳格な整合性を確保するために、複数のシステムモジュールにまたがるインラインリソースドキュメントブロックをクリーンアップするための増分コード保守スイープが完了しました。

_AC-8366 - [GitHub issue](https://github.com/magento/magento2/issues/37248) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/36993)_

#### [問題] `Magento_Catalog`から禁止されている`@author` タグを削除（パート 2）

Magentoの統合コード配信ガイドラインとの完全な整合性を確保するために、追加のクリーンアップパスを実行し、主要なストアフロントリソースモデルをまたいでコンプライアンスに準拠していないファイルコメントを体系的に取り除きました。

_AC-8370 - [GitHub issue](https://github.com/magento/magento2/issues/37247) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/36988)_

#### Tier Price Storage インターフェイス バグの削除すべてのTier Priceが削除されるわけではありません

TierPriceStorageの問題を解決しました。複数のWeb サイトで製品価格を削除すると、割り当てられたWeb サイト IDを考慮するように価格ID照合ロジックを更新して、すべての価格を削除できませんでした。

_AC-9738 - [GitHub issue](https://github.com/magento/magento2/issues/37949) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/40557)_

#### [B2B]発注がActiveMQで販売注文に自動変換されない

ActiveMQをSTOMP プロトコルで使用した場合に、cronで開始されたコンシューマーがメッセージを処理しない問題を修正しました。 その結果、自動承認済みの発注は受注に変換されませんでした。 STOMP キューのメッセージ処理が、DBおよびAMQP キューの実装に対してより信頼性が高く、一貫性を持つようになりました。

_ACP2E-4349 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/08b91f1a) - [GitHub コードの貢献度](https://github.com/magento/inventory/commit/239464da)_

#### 設定されたAWS S3 ストレージでの書き出しエラー

AWS S3 リモートストレージが設定されている場合に、製品の書き出しが正しく機能するようになりました。 以前は、書き出されたファイルは、ストレージドライバーのパス解決が無効なため、S3に書き込めませんでした。

_ACP2E-4786 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/8d95ae6e)_

#### インデクサーが「use_application_lock」および「file」プロバイダーを使用したセルフロックループで停止する

インデクサーのuse_application_lock設定がファイルロックプロバイダーと共に有効になっている場合に、インデックス再作成中にインデクサーが無期限にハングする問題を修正しました。 インデックス再作成の操作が期待どおりに完了しました。

_ACP2E-5027 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/ec436b10)_

#### クラウド UIでMAGENTO_DC変数を設定すると、パフォーマンスが低下する

修正の後、要求されたキーが存在せず、一部の環境変数が定義されるたびに、デプロイメント設定が再読み込みされません。

_ACP2E-5094 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/2b9e8316)_

#### [CLOUD]形式が正しくないURL パスは、URL書き換えルーターで404ではなくHTTP 500を返します

形式が正しくないストアフロント URLが、標準の404が見つからない代わりにHTTP 500 エラーページを返す問題を修正しました。 以前は、特定の形式が正しくないリクエストパスが原因で、URLの書き換え解決中にエラーが発生していました。

_ACP2E-5154 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/4d0357d7)_

#### [CLOUD] PHP 8.5との互換性 – ComponentRegistrar::getPath （） null配列オフセットがクラッシュするsetup:static-content:2.4.9でのデプロイ（コンパクトな戦略）

//@magento_import ディレクティブを使用するモジュール LESS ファイルをコンパイルする際に、「配列オフセットとしてnullを使用する」エラーが発生してPHP 8.5で`setup:static-content:deploy`が失敗する問題を修正しました。 静的コンテンツのデプロイメントがPHP 8.5で正常に完了するようになりました。

_ACP2E-5183 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/597c7211)_

#### [CMS] アンカーhrefの後に別の属性が続くCMS ブロックを保存する際に、偽陽性の「無効なHTML コンテンツが提供されました」

標準のアンカーリンク（例：`&lt;a href="https://example.com/page" target="_blank" rel="noopener">`）を含むCMS コンテンツは、cms/wysiwyg/force_validが有効になっている場合に、誤った「無効なHTML コンテンツが提供されました」検証警告または保存エラーをトリガーしなくなりました。

_ACP2E-5203 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/24667df1)_

### フレームワーク，GraphQL

#### di.xml配列項目は、後の設定で数値キーが使用された場合に置換されます

アーキテクチャデータの整合性を保護し、モジュールの拡張性を向上させるために、数値キー「0」を使用する配列設定がモジュールのコンパイル中にサイレントに上書きまたはドロップされた依存性注入（DI） XML解析エンジン内でコアのバグが解決されました。

_AC-8102 - [GitHub issue](https://github.com/magento/magento2/issues/36861) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/40880)_

### GraphQL

#### 属性コードがモデルの場合、addProductsToCartはcustom_attributesV2でエラーをスローします

製品がコードモデルを持つカスタム属性を持つ場合にaddProductsToCartが内部サーバーエラーを返す問題を修正しました。 custom_attributesV2を使用して、カスタム属性を正しく取得できるようになりました。

_AC-16987 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/809ba93c)_

#### stock_statusがIN_STOCKの場合、GQL数量がnullです

商品GraphQL クエリの数量フィールドで、カスタム MSI在庫に在庫がある商品に対してnullが誤って返されました。 レゾルバは、実際の在庫量を取得する前に、cataloginventory/options/not_available_message設定値で応答をゲートしていました。また、この設定のXML デフォルト（2 - 「販売対象品目が不足しています」）により、管理者による明示的な上書きなしで、任意の新しいストアでnullが返されました。
これで、販売可能な数量が解決された後にチェックが評価されます。 nullは、商品に利用可能な在庫がなく（saleableQty &lt;= 0）、ストアが「販売に十分な品目がありません」と明示的に設定されている場合にのみ返されます。 在庫のある製品は、この設定に関係なく、常に実際の販売可能数量を返します。 設定の読み取りもストアスコープを使用するように修正され、ストアレベルの上書きが尊重されます。

_ACP2E-4840 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/b63925d9)_

#### [CLOUD] BundleProduct items.options.priceは、カタログ価格範囲= Web サイトの場合、Web サイト範囲の価格を無視します

GraphQLのWeb サイトスコープのバンドルオプション価格を修正：カタログの価格範囲がWeb サイトに設定されている場合、GraphQLを介してバンドル商品オプションをクエリすると、web サイトスコープの価格ではなくグローバルの「すべてのストアビュー」価格が返される問題を解決しました。 Magento\BundleGraphQl\Model\Resolver\Links\Collection リゾルバーは、要求されたストア範囲に基づいて価格範囲を適切にチェックし、web サイト固有の選択価格を結合するようになりました。

_ACP2E-5057 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/597c7211)_

#### customerCart GraphQLが競合条件を要求しているため、お客様用に作成されたアクティブなカートが重複しています

リクエストの同時実行に関係なく、顧客ごとに1つのアクティブなカートのみが作成されるようになりました。 以前は、同じ認証済み顧客に対して、アクティブなカートを持たない2つの同時customerCart GraphQL クエリまたはPOST /V1/carts/mine REST リクエストを行うと、データベース内でアクティブなカートレコードが重複する可能性がありました。

_ACP2E-5077 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/8d70f246)_

#### [Cloud]がQuoteGraphQlからのGraphQlNoSuchEntityExceptionをexception.logに記録し、無制限のログ増加を引き起こしました

期限切れまたは無効な買い物かごIDで返されるエラーなど、予想されるGraphQlNoSuchEntityException エラーがvar/log/exception.logに書き込まれる問題を修正しました。 これらの処理されたエラーは、通常のGraphQL エラー応答としてクライアントに返されますが、例外ログには入力されなくなります。

_ACP2E-5122 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/2b9e8316)_

### GraphQL、インベントリ/MSI

#### GraphQL:ProductStock::isProductAvailableでweb サイト IDとして渡されたストア IDが「web サイトが見つかりませんでした」エラーを引き起こす

以前は、ストア IDがweb サイト IDが必要な場所で使用されていたため、商品をカートに追加する際に商品の在庫状況を確認する際に、web サイトが見つからないエラーが発生する可能性がありました。 この問題は修正され、在庫状況チェックで正しいweb サイトのコンテキストが使用されるようになったため、エラーを防ぐことができます。

_ACP2E-5242 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/597c7211)_

### GraphQL，注文

#### [機能要求]配送業者を変更する際に、店舗での受け取りデータの冗長性をクリアします

実店舗での受け取りから宅配方法に切り替えると、受け取り場所と関連する店舗の住所がカートから削除されます。 注文を行う前に、有効な配送先住所を指定する必要があります。

_ACP2E-4973 - [GitHub コードの貢献度](https://github.com/magento/inventory/commit/57047d29)_

### GraphQL，製品

#### ウィッシュリストの値データにキー\&quot;model\&quot;がありません

GraphQLを使用してウィッシュリストの詳細をクエリすると、内部サーバーエラーが返される問題を修正しました。
wishlist クエリが、「Wishlist値データにキーモデルがありません」エラーなしで正常に返されるようになりました。

_AC-8062 - [GitHub issue](https://github.com/magento/magento2/issues/36909) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/515d3dd3)_

### 読み込みと書き出し

#### [問題]読み込みiframeの表示設定を修正

Magento管理パネル内のクリーンで洗練されたユーザーインターフェイスを確保するために、データの検証中にストアマネージャーに内部背景実行フレームが表示されるテンプレートレイアウトの欠陥が解決されました

_AC-13250 - [GitHub issue](https://github.com/magento/magento2/issues/39267) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/39265)_

#### [問題]の修正：製品インポートのハードコード xxh128 ハッシュアルゴリズム

内部サブシステムをクリーンアップし、最新のシステム最適化ベースラインを活用するために、製品インポートコンポーネントが合理化され、単一の永続的なハッシュアルゴリズムを使用できるようになりました。

_AC-16967 - [GitHub issue](https://github.com/magento/magento2/issues/40770) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/40687)_

#### 検証戦略が「エラー時に停止」に設定されている場合、検証エラーの後も読み込みボタンを使用できます

検証戦略が「エラー時に停止」に設定されている場合に、データ検証に失敗した後も検証結果に「読み込み」ボタンが表示されたままになる問題を修正しました。 以前は、すべてのレコードが検証に失敗したにもかかわらず、ボタンが表示され、クリックされる可能性があったため、インポートが直ちに終了しました。

_ACP2E-5124 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/2b9e8316)_

### インストールと管理

#### [Cloud]古い既存のISO再分割コードの修正

13か国の地域コードを更新し、ISO 3166-2標準に一致しました。 以前は、一部の地域コードが標準に一致しなかったため、サードパーティの統合や国際的なコンプライアンスに問題が発生する可能性がありました。 ベルギー、コロンビア、スペイン、フランス、イタリア、ラトビアに新しい地域が追加されました。 オーストリア、コロンビア、コスタリカ、ドイツ、エストニア、スペイン、フィンランド、フランス、インド、アイスランド、ラトビアの地域コードが更新されました。

_ACP2E-4495 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/9b6a8bd9)_

### 在庫/MSI

#### [CLOUD] ギフトカードおよび関連する販売不可のWF-1688

デフォルト以外の在庫/ソースを使用し、関連する（関連またはアップセルまたはクロスセル）商品を保存しても、商品が消えない。

_ACP2E-4741 - [GitHub コードの貢献度](https://github.com/magento/inventory/commit/30fbdb0f)_

#### バンドル製品の在庫状況の不整合

以前は、ストア管理者が管理パネルからバンドル製品の在庫ステータスを手動で更新しても、複数の在庫ソースで構成されたストアのストアフロントには変更が反映されませんでした。 管理者が変更しても、顧客には古い在庫状況が表示され続けます。

この問題は修正されました。 管理パネルで行われたバンドル製品の在庫ステータスの変更が、設定済みのすべての在庫ソースと在庫場所に正しく反映されるようになり、顧客が常にストアフロントで正確な在庫状況を確認できるようになりました。

_ACP2E-4866 - [GitHub コードの貢献度](https://github.com/magento/inventory/commit/db712a46)_

#### GetStockIdForCurrentWebsite.phpによってスローされたNoSuchEntityException 「リクエストされたストアが見つかりませんでした」

無効な？store= クエリパラメーターを持つストアフロントページにアクセスすると、そのようなリクエストごとにNoSuchEntityExceptionがCRITICAL レベルでログに記録される問題を修正しました。 以前は、MSI ストックデータプラグインは、ストアが存在しない場合を処理せずに、生のストアコードをStoreManager::getStore （）に直接渡し、例外ログが乱雑になっていました。

_ACP2E-5003 - [GitHub コードの貢献度](https://github.com/magento/inventory/commit/1bf25e46)_

### 注文

#### スコープがフロントエンドまたはwebapi_rest スコープの場合、注文オブザーバーが実行されない

ストアフロントまたはwebapi_rest スコープを通じて注文をキャンセルしても、キャンセル監視者が正しく実行されない問題を修正しました。 注文がキャンセルされたときに、ギフトカードの金額がお客様の店舗のクレジットに復元されるようになりました。

_AC-16353 - [GitHub issue](https://github.com/magento/magento2/issues/40414) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/64eb754d)_

#### Adminで既存の注文を編集する場合、使用制限のあるカート価格ルールは適用されません（例：「顧客一人あたりの使用数= 1」）。

Adminで既存の注文を編集する際に、使用制限のあるカート価格ルールの割引が削除される問題を修正しました。 使用制限に達した後でも、注文の編集時に元の割引が保持されるようになりました。

_AC-16671 - [GitHub issue](https://github.com/magento/magento2/issues/40624) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/c10554e1)_

#### バンドル製品の管理パネルの最小数量検証エラー

手動見積もりを生成する際にバックエンドの注文処理エクスペリエンスを改善し、機能ブロックを削除するために、管理者注文作成時に子アイテムパラメーターが誤って評価される検証エラーが解決されました。

_AC-17193 - [GitHub issue](https://github.com/magento/magento2/issues/40812) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/40863)_

#### フロントエンドの注文ビューで製品の子アイテム数量の不整合をバンドルする

ストアフロントの注文詳細ページに、各バンドル製品オプションの合計注文数量が表示されるようになりました。 以前は、各子オプションの「数量」列には、オプションごとに発注された合計数量ではなく、親バンドルの発注された数量が表示されていました。

_ACP2E-4820 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/b63925d9)_

#### DeadlockException再試行が欠落している[ASUS] OrderMutex::execute （）が永続的なShipOrder/InvoiceOrder エラーを引き起こします – 

ShipOrderおよびInvoiceOrder操作は、デッドロックの場合に正常に解決されるようになりました。
デッドロックにより、以前のShipOrderおよびInvoiceOrder操作が永続的に失敗しました

_ACP2E-4913 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/51f6d191)_

#### 請求書の生成中に親の設定可能な項目に対するFPT/WEEE行レベルの計算が正しくありません

設定可能な製品の請求書とクレジットメモの総計に、固定製品税額が正しく含まれるようになりました。 以前は、FPT行レベルの金額が親の設定可能な注文項目に反映されていなかったため、請求書とクレジットメモの合計がFPT金額の注文総計よりも低くなっていました。

_ACP2E-4977 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/51f6d191)_

#### 管理者からの注文作成時にページの更新時に変更された製品数量

ページを更新すると、同じSKUが複数回追加される問題を解決しました。

_ACP2E-5046 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/ec436b10)_

#### 同時非同期メール cron ワーカーは、同じ注文に対して重複した注文確認メールを送信します

同時に電子メールを送信するユーザーが、同じ注文に対して重複した注文確認メールを送信する問題を解決しました。

_ACP2E-5059 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/8d70f246)_

#### [CLOUD] sales_clean_quotes cron ジョブがメモリ不足です

多数の期限切れの見積もりをクリーニングする際に、sales_clean_quotes cron ジョブでメモリが不足する問題を修正しました。 以前は、ジョブは処理されたすべての見積もりをメモリに保持し、期限切れのすべての見積もりを削除する前に、致命的なメモリ消耗エラーで終了していました。

_ACP2E-5137 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/4d0357d7)_

### 注文、プロモーション

#### 固定金額カテゴリ カート価格ルールは、ルールがバンドルの親と一致する場合、一致しない動的バンドルの子を割引します

ルールがバンドルの親のみに一致する場合に、カテゴリ条件を持つ固定金額のカート価格ルールが、動的価格バンドルのすべての子に誤って割引を適用する問題を修正しました。 以前は、対象となるカテゴリに属していないバンドルの子には、ゼロの代わりに日割りの割引シェアが付与されていました。

_ACP2E-5075 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/2b9e8316)_

### 支払い

#### config:show コマンドは、新しいバージョンの部分パスでは機能しません

`config:show` コマンドは、支払いなどの部分的な設定パスを受け入れ、そのパスの下に設定値を表示するようになりました。 以前、`php bin/magento config:show`支払いを実行すると、正しい値を表示する代わりにエラー`The "payment" path doesn't exist. Verify and try again.`が返されました。

_AC-13908 - [GitHub issue](https://github.com/magento/magento2/issues/39610) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/40432)_

### パフォーマンス

#### setup:upgradeはインデクサーモードを`schedule`から`save`に変更しています。大幅に遅くなっています

bin/magento setup:upgradeを実行すると、インデクサーモードが「スケジュールに保存」から「保存時に保存」に誤って変更され、データベーストリガーを不必要にドロップして再作成し、ダウンタイムを大幅に削減し、大規模なカタログへのデプロイメント時にパフォーマンスのボトルネックを防ぐ長年の問題を解決しました。

_AC-2423 - [GitHub issue](https://github.com/magento/magento2/issues/33386) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/40643)_

#### Valkey LAYOUT キャッシュキーは、大きな商品カタログに多くのスペースを消費します

以前は、各製品がストアビューごとに独自のレイアウトキャッシュエントリを生成していたため、大規模なカタログでRedis/Valkeyのメモリが過剰に消費されていました。 現在では、LAYOUT キャッシュエントリは、カタログサイズに関係なく、同じタイプ、属性セット、ストアビューを持つ製品間で共有され、キャッシュの増加をバウンディングしています。

_ACP2E-4908 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/9b6a8bd9)_

#### 製品クエリのデッドロックエラー

スケジュールモードの価格インデクサーが同時に実行されたときに発生した、カテゴリ別にフィルタリングされたCatalogWidget製品リストを含むページのInnoDB デッドロックを修正しました。

_ACP2E-5052 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/ec436b10)_

#### [Quans] Adobe Commerce URL解決クエリのパフォーマンス低下

URL ルーティングメタデータ（relative_url、redirect_code、type）のみが要求された場合でも、GraphQL route queryが常にCMS ページコンテンツ全体（ページビルダーウィジェットの実行と製品コレクションの読み込みを含む）をレンダリングする問題を修正しました。 以前は、ページビルダーウィジェットを含むCMS ページのリクエストごとに、不要なウィジェットや製品のレンダリングが発生し、データベースクエリが大幅に増加していました。

_ACP2E-5143 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/597c7211)_

#### 顧客アカウント共有がグローバルに設定されている場合の管理顧客編集パフォーマンスタンク

「顧客アカウントを共有」が「グローバル」に設定されている場合に、読み込み時間とHTTP応答サイズが四分位的に増加する管理者顧客編集ページのパフォーマンスの問題を修正しました。

_ACP2E-5164 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/24667df1)_

### 製品

#### 「価格をクリック」ポップアップ内の「カートに追加」ボタンが機能しない。

製品リストページの「価格をクリック」ポップアップの「カートに追加」ボタンが製品をカートに追加しなかった問題を修正しました。
ポップアップから商品をカートに追加できるようになりました。

_AC-11896 - [GitHub issue](https://github.com/magento/magento2/issues/30356) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/29a7cdbe)_

#### BundleGraphQL リゾルバは、クエリのバッチ処理を無効にして、個別の遅延製品インスタンスを作成します（N+1）

API レスポンスのスループットを大幅に高速化し、サーバーのオーバーヘッドを最小限に抑えるために、GraphQLの解決レイヤーが最適化され、パフォーマンスを低下させるN+1 データベースのリークを排除しながら、バンドル製品に対して真のクエリバッチ処理を実施できるようになりました。

_AC-16647 - [GitHub issue](https://github.com/magento/magento2/issues/40595) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/40867)_

#### EAV SelectおよびMultiselect属性の検証で、値「0」のオプションラベルが正しく拒否されない

データの整合性を改善し、顧客フォームとカタログフォーム全体で予期しない送信エラーを排除するために、正確な文字列値「0」を含むオプションラベルがEAV コアフレームワークによって誤って拒否される検証欠陥が解決されました

_AC-16986 - [GitHub issue](https://github.com/magento/magento2/issues/40634) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/40827)_

#### ユーザーの役割が特定の範囲に制限されている場合、カスタマイズ可能なオプションラベルとカスタマイズ可能なオプションタイトルは保存できません

特定のストアスコープに限定されたアクセス権を持つ管理者ユーザーが編集すると、カスタマイズ可能なオプションラベルとタイトルが元に戻される問題を修正しました。
更新されたラベルとタイトルが、選択したスコープに対して正しく保存されるようになりました。

_AC-2684 - [GitHub issue](https://github.com/magento/magento2/issues/35210)_

#### 製品アラート消費者がストア範囲のシステム/stmp/disableを無視

製品アラート消費者は、ストア範囲のシステム/stmp/無効化の設定を考慮するようになりました。

_ACP2E-4870 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/ec436b10)_

#### 誤ったShort Description ラベルの翻訳を表示するフロントエンド比較ページ

以前は、「製品の比較」ページで、「短い説明」などの比較可能な属性ラベルを使用すると、現在のストアの翻訳ではなく、別のストアビューからの翻訳を表示することができました。 これで、ストア固有の正しい翻訳が表示されます。

_ACP2E-4929 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/08b91f1a)_

#### ページビルダーの製品カルーセルは、カテゴリ位置の並べ替え順序を無視し、代わりにentity_id DESC順序で製品を表示します

ページビルダーカルーセルセットでカテゴリの位置で並べ替えられるように表示された製品が、ストアフロントで間違った順序で表示される問題を修正しました。 製品は、「管理者→ カタログ→カテゴリ→製品」タブで設定された順序で表示されるようになりました。

_ACP2E-4980 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/51f6d191)_

### プロモーションルール

#### 適用されたカート価格ルールの1つに割引数量ステップ値がある場合の誤った割引計算

複数のカート価格ルールが適用され、1つのルールに割引数量ステップ（購入X）値が含まれている場合に、割引が誤って計算される問題を修正しました。
すべての対象数量について、割引が正しく計算されるようになりました。

_AC-12307 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/c10554e1)_

### 返品

#### RMA - Add Return Comments API - メールは送信者（営業担当者）にトリガーされますが、お客様にはトリガーされません

返品APIを介して送信された返品コメントメールが、お客様ではなく営業担当者に送信される問題を修正しました。
お客様への通知が有効になっているAPIを介してリターンコメントが追加されると、お客様にメール通知が届くようになりました。

_AC-1138 - [GitHub issue](https://github.com/magento/magento2/issues/33985)_

### 営業担当者

#### rest api V1/ordersまたはV1/orders/create エンドポイントから注文が行われた場合、`[Order][REST]`件のsales_order_items product_options列にデータがありません

REST APIを介して作成された注文項目にproduct_optionsの完全なデータが含まれていない問題を修正しました。 カスタムオプションラベルと関連するオプションの詳細が、REST APIで作成された注文に対して正しく保存されるようになりました。

_AC-15187 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/8b67e8ed)_

#### 非同期グリッドインデックス作成が、関連付けられたupdate_at タイムスタンプが原因で有効になっている場合、セールスオーダーグリッドが永続的に古いステータスのままになる

非同期グリッドインデックスが有効になっている場合に、セールスオーダーグリッドが古い注文ステータスのままになる問題を修正しました。 同じ秒間に複数の注文が更新される場合など、注文グリッドのステータスが現在の注文ステータスに合わせて正しく更新されるようになりました。

_AC-17118 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/478f8e7c)_

### セキュリティ

#### [問題]更新js.phtml DOM テキストがHTMLとして再解釈されました

プラットフォームのセキュリティベースラインを強化し、悪意のある入力実行のリスクを最小限に抑えるために、動的なDOM更新を処理するプライマリインラインスクリプトテンプレートがリファクタリングされ、クロスサイトスクリプティング（XSS）インジェクションベクターが排除されました。

_AC-12118 - [GitHub issue](https://github.com/magento/magento2/issues/38821) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/38804)_

### 発送

#### USPS REST APIの問題、最大パッケージ重量のレートが正しくありません

注文が複数のパッケージに分割される際の誤った配送見積もりを修正しました（例えば、「最大パッケージ重量」を超える）。 通信事業者は、各パッケージの料金をリクエストし、従来のWeb ツールのフローと一致して金額を合計するようになりました。

_ACP2E-4813 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/6c67a9b5)_

### 税

#### base_wee_tax_applied_amountが親製品に設定されていません

base_weee_tax_applied_amountの値が、子テーブルだけでなく、sales_order_item、sales_invoice_item、sales_creditmemo_itemなどのデータベーステーブルに設定可能な製品に入力されるようになりました

_ACP2E-4922 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/08b91f1a)_

### テストフレームワーク

#### [問題] GraphQLのアップデートでは、大文字と小文字を区別しない部分文字列の比較についてClient.phpがテストされます

GraphQL API テストで、ヘッダーで大文字と小文字が異なる場合にSet-Cookie ヘッダーが認識されない問題を修正しました。 テストがSet-Cookie、set-cookie、およびSET-COOKIE ヘッダーを正しく処理するようになりました。

_AC-15337 - [GitHub issue](https://github.com/magento/magento2/issues/39713) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/c10554e1)_

#### WebAPI GraphQLの機能テストが非常に遅い

ビルド配信の設定を最適化し、継続的インテグレーション（CI）環境を高速化するために、キャッシュのクリア動作を外部システムのコマンド呼び出しからネイティブのインプロセスメモリ処理に移行することで、テストインフラストラクチャのボトルネックが解決されました。

_AC-15395 - [GitHub issue](https://github.com/magento/magento2/issues/39725) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/40804)_

### UI フレームワーク

#### ミニカートは同じページで2回使用することはできません

フロントエンド開発者により高いレイアウト柔軟性を提供するために、長年にわたるコア UIの制限が解決され、複数のミニカートブロック（例えば、ヘッダー内のブロックとフッター内のブロック）が単一ページレイアウト上に独立して存在し、更新できるようになりました。

_AC-12579 - [GitHub issue](https://github.com/magento/magento2/issues/38958) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/40871)_

### from-github

#### [問題]の修正（pagecache）:PATCHをVarnish VCLの有効なHTTP メソッドとして認識します

MagentoのデフォルトのVarnish VCLは、PATCHを有効なHTTP メソッドとして認識するようになりました。そのため、REST APIの部分的な更新リクエスト（例：PATCH /rest/V1/products/:sku）は、パイプではなくバックエンドに渡されます。 これにより、フルページキャッシュがVarnishに設定されている場合に、PATCH呼び出しが失敗したり、正しく動作しなかったりすることが修正されます。

_AC-16954 - [GitHub issue](https://github.com/magento/magento2/issues/40757) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/40657)_

#### [問題] VCLのすべてのgad_* パラメーターを置換します

動的な広告キャンペーンに起因するパフォーマンスの低下を排除するために、アプリケーションのキャッシングレイヤーが更新され、すべてのGoogle Ads Gad_* クエリ文字列が先見的に無視されるようになりました。 これにより、外部キャンペーンリンクでページキャッシュが無効になり、ターゲットページが遅くなるのを防ぐことができます

_AC-16980 - [GitHub issue](https://github.com/magento/magento2/issues/40781) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/40780)_

#### [問題]の修正：ブートストラップの最小PHP バージョン チェックを8.3に更新しました

ランタイムエラーの混乱を防ぎ、開発者インストールのトラブルシューティングを改善するために、システムブートストラップフレームワーク内のネイティブ PHP環境バリデーターは、アプリケーションの実際のコア要件に沿って導入されました。

_AC-17312 - [GitHub issue](https://github.com/magento/magento2/issues/40851) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/40686)_

#### `health_check.php`は、`igbinary`がインストールされ、デフォルトのファイルキャッシュが使用されている場合に500を返します（Varnish 503）

デフォルトのファイルキャッシュバックエンドを使用してigbinaryをインストールすると、health_check.phpがHTTP 500を返す問題を修正しました。 ヘルスチェックは、明示的なバックエンドキーを使用せずに有効なキャッシュ設定を受け入れるようになりました。これにより、Varnishはバックエンドを異常としてマークし、HTTP 503を返さないようになりました。

_AC-17400 - [GitHub issue](https://github.com/magento/magento2/issues/40876) - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/8b67e8ed)_

#### [問題]の修正：gzip タイプを更新し、nginx設定のIE6回避策を削除します

ページの読み込み速度を向上させ、ネットワークアセット配信を最適化するために、フォールバックサーバー設定が近代化され、最新のストアフロントコンポーネントをより適切にサポートし、従来のテクノロジーのオーバーヘッドが削減されました

_AC-17498 - [GitHub issue](https://github.com/magento/magento2/issues/40774) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/40681)_

#### [問題]不安定なgraphql OrderStatusChangeDateTestの修正を試みます。

継続的インテグレーション（CI）の信頼性を向上させ、偽陽性ビルド失敗を減らすために、WebAPI機能テストスイートで競合条件が解決されました。 GraphQL注文ステータス検証テスト（OrderStatusChangeDateTest）では、以前にPHP メモリとMySQL タイムスタンプの間に微妙なタイミング差が生じたため、断続的なエラーが発生していました

_AC-17959 - [GitHub issue](https://github.com/magento/magento2/issues/41126) - [GitHub コードの貢献度](https://github.com/magento/magento2/pull/40618)_
