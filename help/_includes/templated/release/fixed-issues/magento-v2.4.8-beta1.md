---
source-git-commit: cb3392b7716667201305b7502f6c9c31bc7d1a23
workflow-type: tm+mt
source-wordcount: '14443'
ht-degree: 0%

---
# Magento Open Sourceリリースノート（v2.4.8-beta1）

## ハイライト

Magento Open Source 2.4.8 リリースには、次の 49 のハイライトが適用されます。

### フレームワーク

* _AC-10721_：最新バージョンへのアップグレード中の league/flysystem Composer 依存関係のアップグレード
   * _修正点_:2.x league/flysystem Composer の依存関係を最新バージョン 3.x にアップグレードします
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/91cb4d46>
* _AC-11495_:2.4.8-beta1 プラットフォームコンポーネントのアップグレード
* _AC-11673_: php-amqplib/php-amqplib 最新バージョンを調べます
   * _修正点_：最新バージョン php-amqplib/php-amqplib :^3.x を更新しました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/de4dfb8e>
* _AC-11723_: phpunit 10 互換性のための統合テスト フレームワークのリファクタリング - IntegrationTest.php が見つかりません
   * _修正点_:PHPUnit 9 は、Adobe Commerceの Integration および WebAPI Test Framework の変更により、PHPUnit 10 にアップグレードされます。 PHPUnit 10 の変更には下位互換性があります。
   * _GitHub コードの投稿_:&lt;https://github.com/magento/magento2/ （内部、結合前） >
* _AC-11813_:phpunit 10 互換の WebApi テストフレームワーク - SOAPおよび B2B モジュールとのRabbitMQ接続に関する問題
   * _修正点_:PHPUnit 9 は、Adobe Commerceの Integration および WebAPI Test Framework の変更により、PHPUnit 10 にアップグレードされます。 PHPUnit 10 の変更には下位互換性があります。
   * _GitHub コードの投稿_:&lt;https://github.com/magento/magento2/ （内部、結合前） >
* _AC-11816_:MySQL 8.4 LTS との互換性を追加
* _AC-11911_：ライブラリへの移行後の jQuery/fileuploader CSS のクリーンアップ
   * _修正点_:jQuery/fileUploader ライブラリは Uppy ライブラリに移行されたので、このライブラリを削除しました
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/7cabfb46>
* _AC-11995_:MagentoCE 向けに MySQL 8.4 LTS との互換性を追加
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/672a2e61>
* _AC-12014_:elasticsearch 8 モジュールを非推奨としてマークする
* _AC-12015_:jsTree ライブラリへの移行後の ExtJs フォルダーのクリーンアップ
   * _メモの修正_：関連機能が jsTree に移行されたので、extJs フォルダーを削除しました
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/7cabfb46>
* _AC-12022_：モノログ/モノログシステムの依存関係を最新のメジャーバージョンにアップグレード
   * _修正点_：システムを更新して「monolog/monolog:^3.x」ライブラリの最新のメジャーバージョンを使用するようにし、互換性とパフォーマンスの向上を確保しました。 以前は、システムは「monolog/monolog」ライブラリの古いバージョンを使用していましたが、潜在的な問題や制限につながる可能性がありました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/edcd0dcc>
* _AC-12023_:wikimedia/less.phpの依存関係を最新のメジャーバージョンにアップグレードします
   * _修正点_：システムを更新して「wikimedia/less.php」ライブラリの最新のメジャーバージョン 5.x を使用するようにし、互換性と最新機能を確保しました。 以前は、システムは古いバージョンのライブラリを使用しており、セキュリティの問題が発生する可能性がありました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/edcd0dcc>
* _AC-12024_:jquery/validate ライブラリの依存関係を最新のマイナーバージョンにアップグレードします
   * _修正点_:jquery/validate ライブラリの依存関係を最新のマイナーバージョン 1.20.0 にアップグレードします
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/de4dfb8e>
* _AC-12025_:moment.js システムの依存関係を最新のマイナーバージョンにアップグレードします
   * _修正点_:moment.js システムの依存関係を最新のマイナーバージョン 2.30.1 にアップグレードします
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/de4dfb8e>
* _AC-12032_:MySQL 8.4 LTS for EE との互換性を追加
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/672a2e61>
* _AC-12034_:MySQL 8.4 LTS for B2B との互換性を追加
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/672a2e61>
* _AC-12074_：バンドル拡張機能用に MySQL 8.4 LTS との互換性を追加
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/672a2e61>
* _AC-12085_:CE 用 MariaDB 11.4 LTS との互換性を追加
   * _修正点_:Adobe Commerceと拡張機能で MariaDB 11.4 がサポートされるようになりました
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/b34c0a75>
* _AC-12165_：購読者の最適化 – PhpUnit10
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/90e25b6b>
* _AC-12267_:Redis セッションの接続再試行をサポートし、colinmollenhour/php-redis-session-abstract v2.0.0 と互換性があります
   * _修正点_:adobe commerce と互換性のある colinmollenhour/php-redis-session-abstract v2.0.0 の最新バージョンを更新しました
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/672a2e61>
* _AC-12268_:League/flysystem Composer の依存関係を最新バージョンにアップグレード
   * _修正点_:2.x league/flysystem Composer の依存関係を最新バージョン 3.x にアップグレードします
* _AC-12576_:MySQL 8.4 LTS での自動化テストの失敗を調査します
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/672a2e61>
* _AC-12595_:MariaDB 11.4 LTS For EE との互換性を追加
   * _修正点_:Adobe Commerceと拡張機能で MariaDB 11.4 がサポートされるようになりました
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/b34c0a75>
* _AC-12693_:MySQL 8.4 LTS を使用したデータ移行ツール（DMT）の調査
* _AC-12715_：最新バージョンへのアップグレード中の laminas composer の依存関係の更新
   * _修正点_：システムは最新バージョンの laminas composer 依存関係をサポートするようになりました。
ラミナス/ラミナス – サービスマネガー
ラミナス/ラミナス サーバ
laminas/laminas-stdlib
ラミナス/ラミナスバリデーター
互換性と最新機能の確保。 以前は、これらの依存関係を最新バージョンに更新すると、後方互換性の問題が発生し、テストが失敗する可能性がありました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/b34c0a75>
* _AC-12752_：データ移行ツール用に MariaDB 11.4 LTS との互換性を追加
   * _修正点_:Adobe Commerceと拡張機能で MariaDB 11.4 がサポートされるようになりました
* _AC-12823_：コンポーネントのアップグレード中に phpunit パッチが更新されたことで単体テストが失敗したことを調査します
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/b34c0a75>
* _AC-12897_:MySQL 8.4 との SVC および EAT ツールの互換性
* _AC-12898_:MySQL 8.4 と UCT ツールの互換性
   * _修正メモ_：アップグレード互換性ツール（UCT）は MySQL 8.4 と互換性を持つようになり、このバージョンで実行されているインスタンスのスムーズな操作と互換性チェックが可能になりました。 以前は、UCT ツールはテストされておらず、MySQL 8.4 との互換性も確認されていません。
* _AC-9749_: PHPUnit 10 アップグレード
   * _修正点_: phpunit/phpunit composer の依存関係を互換性のあるバージョンに更新しました – &quot;phpunit/phpunit&quot;:&quot;10.x&quot;

### インストールと管理

* _AC-6819_：インデクサーをデフォルトで「スケジュールに従って更新」に設定します

### 順序

* _ACP2E-2709_: [ 機能リクエスト ] 顧客が、注文詳細ページの「コメントを送信」ボタンは混乱しており、別のページに変更する必要があると提案しています
   * _メモの修正_：混乱を最小限に抑えるために、注文詳細ページの「コメントを送信」ボタンのラベルが「更新」に変更されました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/488c1034>

### その他

* _AC-11420_：新しいバージョンのAdobe Commerceがインストールされると、セットインデクサーがデフォルトで準備完了ステータスに表示される
   * _注意を修正_：インストールのMagento後、インデクサーのステータスはデフォルトで *準備完了* 状態である必要があります。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/71432aeb>
* _AC-11421_：既存のMagentoインストールで、サードパーティのインデクサーモジュールをインストールすると、インデクサーがデフォルトでスケジュールに従って更新されます。
   * _メモの修正_：新しいインデクサーはすべて、デフォルトで [ スケジュールに従って更新 ] モードになっています。 以前は、デフォルトのモードは [ 保存時に更新 ] でした。 カスタムインデクサーでも同様です。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/71432aeb>
* _AC-12480_:Elasticsearch 7 および 8 のオプションは、管理設定に非推奨（廃止予定）として付属している必要があります。
   * _メモを修正_：管理設定オプションの「Elasticsearch 8」オプションに非推奨のテキストが表示され、Elasticsearch 8 は使用を推奨するオプションではなくなったことをユーザーに知らせます。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/0611e750>
* _AC-12481_：管理者設定で「Elasticsearch」オプションが選択されている場合にテキストメモを追加
   * _修正点_:Adobe Commerce管理者に、elasticsearch がAdobeでサポートされなくなり、非推奨になったことを知らせるテキストメモが追加されました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/0611e750>
* _AC-12870_:MariaDB 11.4 との SVC および EAT ツールの互換性
   * _修正点_:MariaDB 11.4 との SVC および EAT ツールの互換性
* _AC-12876_:UCT ツールと MariaDB 11.4 の互換性
* _LYNX-374_:GraphQL経由の Document Email Confirmation
* _LYNX-376_:GraphQLでの reCAPTCHA の設定の取得
* _LYNX-409_:「買い物かご項目を更新」ミューテーションに対する DB クエリの最適化

### セキュリティ

* _AC-11041_:2024 年 6 月リリースからの 2.4.8-beta1 のセキュリティの改善
* _AC-11864_:2024 年 8 月リリースからの 2.4.8-beta1 のセキュリティの改善
* _AC-12346_:2024 年 10 月リリースからの 2.4.8-beta1 のセキュリティの改善
* _AC-12691_:[2.4.8-beta1] 顧客更新 REST API エンドポイントが機能しない
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/a4102373>、<https://github.com/magento/magento2/commit/a4102373>

### UI フレームワーク

* _AC-12726_:[2.4.8-beta1]TinyMCE 5 から TinyMCE 7 への移行
   * _修正点_:TinyMCE 5 を TinyMCE 7.3.0 に移行し、Adobe Commerceでサポート対象バージョンにする。以前のシステムでは 5.10.2 を使用していたが、これは古くなり、セキュリティの脆弱性が報告されていた
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/edcd0dcc>
* _AC-12825_:[2.4.8-beta1]TinyMCE 5 から TinyMCE 7 ページビルダーへの移行
   * _修正点_:TinyMCE 5 を TinyMCE 7.3.0 に移行し、Adobe Commerceでサポート対象バージョンにする。以前のシステムでは 5.10.2 を使用していたが、これは古くなり、セキュリティの脆弱性が報告されていた
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/edcd0dcc>
* _AC-12844_:[2.4.8-beta1]TinyMCE 5 の TinyMCE 7 への移行 – Magento2-infra – 禁止された単語
   * _修正点_:TinyMCE 5 を TinyMCE 7.3.0 に移行し、Adobe Commerceでサポート対象バージョンにする。以前のシステムでは 5.10.2 を使用していたが、これは古くなり、セキュリティの脆弱性が報告されていた
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/edcd0dcc>
* _AC-12901_:Require.js を最新バージョン 2.3.7 にアップグレード（セキュリティの脆弱性 CVE-2024-38999）
   * _メモの修正_:require.js を最新バージョン 2.3.7 に更新しました。以前のバージョンでセキュリティの脆弱性が報告されました
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/b34c0a75>

## 修正された問題

Magento Open Source 2.4.8 コアコードの 253 の問題を修正しました。 このリリースで修正された問題の一部を以下に示します。

### API

* _AC-10042_: /V1/transactions REST API は、parent_txn_id = txn_id の場合にエラーを返します
   * _注意の修正_：親トランザクション ID がトランザクション ID と同じである親および子の概念トランザクションをシステムが正しく処理できるようになり、/V1/transactions REST API エンドポイントに対するクエリ時に無限ループが発生するのを防ぎます。 以前は、このシナリオでは、最大実行時間を超えているので、致命的なエラーが発生していました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/1bafc571>
* _AC-11878_:2.4.7 の [Graphql] タイプの問題
   * _修正点_:GraphQL クエリの実行時に GetCustomSelectedOptionAttributes 関数の整数値を正しく処理し、タイプ関連のエラーが発生しなくなりました。 以前は、GetCustomSelectedOptionAttributes を integer 引数と共に使用するGraphQL クエリを呼び出すと、type エラーが発生していました。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/38662>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/38663>
* _ACP2E-2927_: [REST API]：設定可能な製品の設定を追加した後、ストア表示で「デフォルト値を使用」がチェックされたままにならない
   * _修正点_：この問題は、デフォルト以外のストア向けのカスタマイズ可能なオプションに対して正しいデータベースエントリを確保することで修正されました。 「管理者/カタログ/製品編集/カスタマイズ可能なオプション」セクションのカスタムストアのチェックボックスは、カスタムストアのオプションタイトルがデフォルトストアと同じであっても、データベースエントリが不正確なために以前はオフになっていました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/3056e9cb>
* _ACP2E-2969_:Oauth1 を使用する場合、REST API が SKU でスラッシュ（/）を使用してリクエストを行うことができない
   * _修正点_：修正前は、SKU に「/」が含まれている製品に対して API 呼び出しを成功させることができませんでした。 これで、SKU にスラッシュが含まれている場合でも、製品の詳細に対して成功した API GET リクエストを発行できます。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/b21e5d91>
* _ACP2E-3079_:「validateDefaultAddress」が有効な場合、REST API を使用して更新すると顧客アドレスの更新が失敗する
   * _メモの修正_:API ペイロードに見つからない ID キーの問題が解決された後、API エンドポイントが意図したとおりに機能するようになりました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/9af794a4>
* _ACP2E-3091_: [Cloud] Tier Prices Api で重複した web サイトグループ価格の顧客グループを作成しています。
   * _修正メモ_：現在、Tier Price Rest Api では、重複する web サイトグループ価格の顧客グループを作成できません。
以前は、製品保存中に管理者の検証に合格しない Tier Prices Api で、Duplicate website group price customer group を作成することができました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/148c3ead>
* _ACP2E-3130_: REST API を使用してステータスの注文コメントを追加できない
   * _メモの修正_：この問題は、現在の状態のみの場合、注文の変更ステータスを許可することで解決されました。 以前は、同じ状態の注文であっても、注文の状態を尊重したり、注文の状態の変更を防いだりしていませんでした。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/93d50f8d>

### アカウント

* _AC-10782_：顧客住所フォームの名前フィールドにランダムコードを使用できる
   * _メモの修正_：システムは、顧客アドレスフォームの名フィールドと姓フィールドの入力を検証するようになったので、ランダムコードが使用されなくなります。 以前は、システムはエラーをスローせずにこれらのフィールドにランダムなコードを使用することができました。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/38331>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/38345>
* _AC-10990_：アカウントの追加アドレスが保存時にクラッシュする
   * _メモの修正_：地域フィールドが表示されない場合でも、システムは顧客アドレスを正しく保存するようになり、保存処理中のクラッシュを防ぎます。 以前は、領域フィールドが表示されていないアドレスを追加または編集しようとすると、例外エラーが発生していました。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/38406>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/38407>
* _AC-11919_：管理者：ページアクションのボタンが右ではなく左にフローティングされる
   * _メモの修正_：システムでは、管理パネルのスティッキーヘッダーの右側にページアクションボタンが正しく配置され、プロフェッショナルなルックアンドフィールが強化されました。 以前は、これらのボタンは、スティッキーヘッダーの左側に誤ってフローティングされていました。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/38701>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/44cef3a9>
* _AC-11999_:magento 2.4:di:7 の dev-info エラー
   * _メモの修正_:dev:di:info コマンドの実行時にコンストラクターパラメーターが正しく表示され、エラーが発生しなくなりました。 以前は、このコマンドを実行すると、引数のタイプの不一致が原因でエラーが発生していました。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/38740>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/0c53bbf7>
* _AC-6071_：ユーザーがログインしたが、フロントエンドに 404 エラーが表示される。
   * _修正点_：顧客がログインした際に、ストアフロントの顧客ダッシュボードページが期待どおりに読み込まれるようになりました。 以前は、ユーザーはログインできましたが、このページでは 404 エラーが表示されていました。 [GitHub-35838](https://github.com/magento/magento2/issues/35838)
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/35838>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/36263>
* _ACP2E-2791_:Admin Edit customer セクションで顧客属性情報を保存できない
   * _メモの修正_：顧客のストア ID が、管理者顧客編集フォームの web サイト範囲ごとに正しく実装されるようになりました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/488c1034>

### 管理 UI

* _AC-11588_：置き換え動作で製品を読み込む際に、データの検証が成功し、「読み込み」ボタンが表示される
   * _修正点_：システムはデータを正しく検証し、「置換」動作を使用して製品の読み込みプロセス中の「読み込み」ボタンを非表示にして、意図しないデータの置換を防ぐようになりました。 以前は、システムがデータを誤って検証し、「読み込み」ボタンを表示したため、データの不一致が発生する可能性がありました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/0574ac23>
* _AC-12167_:[ バグ ]Magento 2.4.7 では、大文字のファイル拡張子を持つ製品写真を使用できません。
   * _修正点_：システムでは、大文字のファイル拡張子を持つ製品画像のアップロードを受け入れるようになり、製品の作成プロセスをスムーズに行えるようになりました。 以前は、ファイル拡張子が大文字の画像のアップロードは拒否され、ユーザーはファイル拡張子を小文字に変更する必要がありました。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/38831>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/c8f87c25>
* _AC-7700_: [ 問題 ] mview でインデクサーの変更ログテーブルを登録解除します
   * _メモの修正_：インデックスが「スケジュールに従って更新」から「保存時に更新」に切り替わると、システムは未使用の変更ログテーブルを自動的に削除するようになりました。インデックスを無効としてマークして、エントリが失われないようにします。 以前は、インデックスを「保存時に更新」に切り替えると、未使用の変更ログテーブルがシステムに残り、変更されたすべてのインデックスが「有効」としてマークされていました。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/29789>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/25859>
* _AC-9843_: i18n:collect-phrases は翻訳の整合性を壊します
   * _注意を修正_:`bin/magento i18n:collect-phrases -o` コマンドは、JavaScript ファイルおよび.phtml ファイルから新しいフレーズを正しく収集して追加し、翻訳が翻訳ファイルに正確に反映されるようになりました。 以前は、JavaScript ファイルの複数行の翻訳語句と.phtml ファイルの語句を翻訳ファイルに含めることができず、翻訳が不完全または誤っていました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/0c53bbf7>
* _ACP2E-2787_：ストア表示名のアポストロフィは「」に置き換えられます
   * _メモの修正_：グリッドのストア表示フィルターにアポストロフィが正しく表示されるようになりました
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/38395>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2847_: favicon アップロードで.ico ファイルの検証に失敗する
   * _修正点_：ファイル検証エラーが「ファイルの検証に失敗しました。 ストア設定の画像処理設定を確認してください。」というエラーメッセージが表示されます。 以前は、単に「ファイルの検証に失敗しました」でした。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2957_: PageBuilder のギャラリーで、新しくアップロードされた画像の代わりに古い画像のサムネールが表示される
   * _メモを修正_：ページビルダーコンテンツのメディアギャラリーから、同じ名前で削除および再アップロードされた画像の画像プレビューを再生成します。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/001e5188>、<https://github.com/magento/magento2-page-builder/commit/60140cd2>
* _ACP2E-2978_：異なる役割スコープを持つ管理者ユーザーが製品を保存すると、製品内の既存の関連製品情報が上書きまたは削除される
   * _修正点_：以前は、修正前にセカンダリ管理者ユーザーが関連製品を変更せずに「保存」ボタンをクリックすると、関連製品がリセットされ、空になっていました。 この修正の後、セカンダリ管理者ユーザーが「保存」ボタンをクリックすると、製品はリセットされず、正常に保存されます。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/3056e9cb>
* _ACP2E-3033_: 200 件を超える注文を書き出すことができません
   * _修正点_：問題を修正するために、HTTP リクエストをGETからPOSTに変更することで、以前に送信した選択された ID のリクエストサイズのサーバー制限が無視されました。 以前は、GETリクエストのサイズに関するサーバーの制限により、問題が発生していました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/93d50f8d>
* _ACP2E-3037_：チェックアウトページの検証メッセージが正しくありません。
   * _メモの修正_:「address」など、必須フィールドが空のままになっている場合、サーバーサイドの検証ではメッセージが表示されません。 クライアントサイドの検証では、「これは、必須フィールドです」という必須フィールドエラー通知が表示されます。 以前は、クライアントサイドの検証メッセージに加えて、必須フィールドが空のままの場合、「address is required」というメッセージが表示されていました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/9af794a4>
* _ACP2E-3125_：管理者ユーザーのパスワードリセットテンプレートの問題
   * _メモの修正_：問題は、正しいキーを使用して解決されました。このキーには、メールテンプレートの管理者ユーザー名が含まれ、件名が正しく完了しています。 以前は、この問題は、使用されていた古いキーに起因していました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/93d50f8d>
* _ACP2E-3149_：顧客セグメント URL での二重スラッシュ
   * _メモの修正_：グリッドで「フィルターをリセット」をクリックした場合、URL に二重スラッシュが表示されません。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/8459b17d>
* _ACP2E-3171_：許可されている特定の国では COD を使用できません
   * _修正メモ_：現金払い注文は、必要に応じて、許可されている特定の国で利用できるようになりました。   AC-3216 は正常に動作しています。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/6f4805f8>
* _ACP2E-3178_: カスタムで作成された注文のステータスを更新できない
   * _修正メモ_ : 「
カスタムで作成した注文ステータスを更新できるようになりました。一方、以前は、現在のステータスが「処理中」または「不正」の場合にのみ、ステータスを変更できました。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/38659>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/8459b17d>

### 管理 UI、パフォーマンス

* _ACP2E-3169_:2.4.5-p8 への更新後、管理者から注文を作成すると 500 エラーが発生します
   * _メモの修正_：以前は、HTMLの縮小を有効にすると、管理者から注文できませんでした。 これで、HTMLの縮小が有効になり、管理者から正常に注文できます。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/b21e5d91>

### 管理 UI、送料

* _ACP2E-2519_：のクーポンコード数が更新されません   複数配送で注文した場合の、「クーポンコードを管理」タブの「使用時間」列。
   * _メモの修正_：以前は、複数配送で注文を行った際に、「クーポンコードの管理」タブの「使用時間」列のクーポンコード数が更新されていませんでした。 現在は、正しい数が「使用時間」の両方に表示され、マルチシッピングで目的の値が反映されています。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/4745100c>

### 分析/レポート

* _ACP2E-2570_：事前レポートが機能しない
   * _メモの修正_：システムは、10,000 個のバッチでレポートを読み込みおよび書き込むことにより、非常に大きなデータセットに対する事前レポートデータファイルの生成をサポートするようになりました。 以前は、詳細レポートモジュールで超大データセットのデータファイルを生成できず、analytics_collect_data cron ジョブの実行中に「MySQL サーバーが停止しました」というエラーが発生していました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/a12063bd>
* _ACP2E-3080_：管理者の注文製品レポートの日付範囲の表示に関する問題。
   * _メモの修正_：ユーザーは、注文済み製品レポートから任意の日付を選択できるようになります。 以前は、テーブルの更新後に「開始日」を選択すると、「終了日」がリセットされていました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/6f4805f8>
* _ACP2E-3096_：間違った curl ヘッダーにより newrelic:create:deploy-marker が機能しない
   * _修正点_：システムで curl ヘッダーが正しくフォーマットされるようになり、newrelic:create:deploy-marker コマンドでNew Relicにデプロイメントマーカーを正常に作成できるようになりました。 以前は、curl ヘッダーが正しくないと、New Relicでデプロイメントマーカーを作成できませんでした。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/37641>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/6a185204>

### 分析/レポート、B2B

* _ACP2E-2300_: B2B - サイトマップに、共有カタログに割り当てられていない製品/カテゴリが含まれています
   * _メモの修正_：サイトマップで生成されるカテゴリと製品を、公開共有カタログおよび/またはカタログカテゴリの権限設定にのみ割り当てられたカテゴリと製品に制限します。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/ea79f7dd>

### Analytics/レポート、クラウド

* _ACP2E-3067_:Magentoは、ほとんどのNew Relic cron トランザクションを破棄します#34108
   * _メモの修正_:AC は cron ジョブ関連のトランザクションを NewRelic に正しくレポートしています。 以前は、一部の cron ジョブ関連のトランザクションは、NR で「OtherTransaction/Action/unknown」と表示されていました
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/35b1b1da>

### B2B

* _ACP2E-3044_:[ マイ注文 ] セクションに不要な罫線が表示される
   * _修正点_：以前は、追加の CSS クラスを適用する追加のコンテナ（注文参照）が作成されていたので、不要な境界線が「自分の注文」セクション内の注文番号の下に表示され、現在表示されません。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/9af794a4>

### B2B, フレームワーク

* _AC-9607_：会社のグリッドをフィルタリングしてから、グリッド CSV の書き出しを試みると、失敗して例外がスローされる
   * _メモの修正_：このシステムでは、「未払い残高」や「会社タイプ」などのフィルターが適用されている場合でも、管理パネルで会社グリッドデータを正常に CSV 書き出すことができるようになりました。 以前は、特定のフィルターを適用してグリッドデータを書き出そうとすると、失敗し、例外がスローされていました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/44cef3a9>

### Braintree

* _BUNDLE-3367_:LPM 経由での支払い
   * _GitHub コードの投稿_:<https://github.com/magento/ext-braintree/pull/204>
* _BUNDLE-3368_：仮想を子製品として設定可能
   * _GitHub コードの投稿_:<https://github.com/magento/ext-braintree/pull/204>
* _BUNDLE-3369_: CVV Verification failed エラー
   * _GitHub コードの投稿_:<https://github.com/magento/ext-braintree/pull/204>
* _BUNDLE-3370_：アカウント領域を介したヴォールティングの問題 247
   * _GitHub コードの投稿_:<https://github.com/magento/ext-braintree/pull/204>
* _BUNDLE-3371_：別の国の住所に発送します
   * _GitHub コードの投稿_:<https://github.com/magento/ext-braintree/pull/204>
* _BUNDLE-3372_：クレジットカード – ティアダウン機能
   * _GitHub コードの投稿_:<https://github.com/magento/ext-braintree/pull/204>
* _BUNDLE-3373_:PayPal Express の配送用コールバック
   * _GitHub コードの投稿_:<https://github.com/magento/ext-braintree/pull/204>

### 買い物かごとチェックアウト

* _AC-10660_：製品の比較ページで買い物かごに製品を追加する際に、例外が正しく処理されない
   * _修正メモ_：製品の比較ページから買い物かごに製品を追加する際に、コントローラにメッセージマネージャーメッセージが表示される場合、例外を適切に処理するようになりました。 以前は、例外があると、JSON エンコードされたページが適切に取得および処理されずに返されていました。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/38200>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/38257>、<https://github.com/magento/magento2/commit/0c53bbf7>
* _AC-10698_: GTag はトランザクションの価格と合計を送信しません。
   * _修正点_:GTag が有効な場合、システムは取引価格と合計をGoogle Tag に正しく送信し、e コマースデータを正確に追跡できるようになりました。 以前は、通貨は、個々の注文に関連付けられるのではなく、「すべて」の注文の一部として誤って送信されていました。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/37348>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/37504>、<https://github.com/magento/magento2/pull/37349>
* _AC-11641_: [ 問題 ] [ チェックアウト ] 失敗した支払いメールテンプレートで更新された依存ディレクティブ
   * _修正点_：仮想製品の支払いに失敗したメールテンプレートから配送先住所と配送方法が正しく省略され、関連する情報のみがメールに含まれるようになりました。 以前は、仮想製品の支払い失敗メールに、配送先住所と配送方法が誤って含まれていました。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/32781>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/32511>
* _AC-11876_:[ 問題 ] 2.4.7 でセールスルールのリグレッションが発生
   * _修正メモ_：システムは販売ルールを正しく検証し、製品条件がどの製品名とも一致しない場合にクーポンコードを買い物かごに適用できないようになりました。 以前は、商品条件が商品名に一致しない場合でも、販売ルールを適用したり、配送額に割引を適用したりすることができました。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/38671>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/0574ac23>
* _AC-11993_:[ 問題 ] 郵便番号が変更され、配送料検証ルールが適用されると、ローダーによって配送方法がブロックされます
   * _修正点_：システムは、配送料検証ルールのないカスタム配送方法を正しく処理するようになりました。これにより、チェックアウト中に配送先住所で郵便番号が変更された後に、ローダーが配送方法をブロックしないようになります。 以前は、チェックアウト時に配送先住所の郵便番号を変更すると、配送料検証ルールのないカスタム配送方法が使用された場合、ローダーは配送方法をブロックし、表示されなくなります。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/38742>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/1bafc571>
* _AC-12170_:Magento 2.4.7 のチェックアウトページで、クーポンコード機能が正しく動作しない
   * _修正点_：仮想製品とダウンロード可能な製品のチェックアウトページで「割引コード / クーポン」入力フィールドが有効になり、ユーザーは期待どおりに割引コードを適用できるようになりました。 以前は、割引コード/クーポン入力が無効になっており、ボタンのタイトルテキストが「クーポンをキャンセル」と表示されているので、ユーザーは割引コードを適用できませんでした。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/38826>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/1bafc571>
* _AC-8103_：アドレスレンダラーの翻訳 VAT
   * _修正点_：このシステムでは、アドレスレンダラーで「VAT」、「T」、「F」のテキストを翻訳できるようになり、ユーザーはこれらの用語をストアの特定の言語に翻訳できます。 以前は、これらの用語は翻訳可能ではなく、ユーザーは回避策を使用する必要がありました。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/36942>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/36943>
* _ACP2E-2055_：時間差がほとんどなく、同時に同じ見積 ID を持つ注文が重複しています
   * _修正メモ_:Adobe Commerceのお客様が同じ QuoteID で重複した注文を受け取った問題を修正しました
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2470_：チェックアウトステップで永続的な買い物かごがクリアされる
   * _修正メモ_：修正後、ログインしていない状態でチェックアウト中に支払い方法を選択しても、永続セッションが終了しません。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-2518_：並べ替えによって、割り当てられていない製品が買い物かごに追加される
   * _修正点_：以前は、異なるストアの製品を他のストアから並べ替えることができました。 この修正が同じストアにのみ適用された後、顧客アカウント共有が有効な場合、同じスコープの製品を並べ替えることができます
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2620_：管理者で、項目を選択する際に左側の「買い物かご」と、右側の「買い物かごに移動」が更新されません
   * _メモの修正_：項目を選択すると、左側の「買い物かご」が更新され、管理画面の右側から「買い物かごに移動」が更新されます。 以前は、変換された買い物かご項目がセッションから空にならないので、この機能は機能しませんでした。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2646_: [Cloud] 複数出荷の最初の注文に販売ルールが適用されない
   * _修正注_：修正後、割引は同じ複数出荷見積の注文ごとに正しく表示されます。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2664_:[Cloud] 実稼動同じ製品を買い物かごに追加する並列リクエストの結果、買い物かごの Rest API で 2 つの異なる項目が発生する
   * _修正メモ_：複数の並列リクエストを正しく処理して同じ製品を 1 つの行項目に買い物かごに追加できるようになり、同じ SKU で別々の行項目を作成できなくなりました。 以前は、REST API を介して同じ製品を買い物かごに追加する並列リクエストを実行すると、同じ SKU に対して複数の行項目が発生していました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2704_:Cookie を送信できません。 並べ替えの試行中の「mage-messages」のサイズ
   * _修正点_：現時点では、並べ替えプロセスで独自のエラーは生成されません。 これは、買い物かごリストのビルトインの項目確認に依存します。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2798_: チェックアウト時にデフォルトの配送先住所が選択されていません
   * _メモの修正_：デフォルトの配送先住所が、有効な住所検索のコンテキストでイベントとして選択されるようになりました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/7e0e5582>
* _ACP2E-2897_:[CLOUD] graphql addProductsToCart api の問題（カスタムオプションあり）
   * _修正点_:GraphQLでは、同じ商品が異なるカスタムオプションで正しく買い物かごに追加される
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/c971859e>
* _ACP2E-2923_：新規顧客としてチェックアウトする際に、アカウントに追加された複数のアドレス
   * _修正メモ_：注文の作成に失敗した場合、システムは新しい顧客アドレスを 1 回だけ保存するようになり、注文の配置エラーが発生した場合に複数の同一のアドレスを作成するのを防ぎます。 以前は、注文が正常に作成されたかどうかに関係なく、注文の発注が試行されるたびに新しい住所が保存されていました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/001e5188>、<https://github.com/magento/inventory/commit/2ebcef39>
* _ACP2E-3004_：ゲストによる注文フォームを使用して顧客の注文を並べ替えると、買い物かごが空になる
   * _注意を修正_：以前は、「注文と返品」ページを通じて並べ替えを配置する際に、顧客はログインページにリダイレクトされていました。 この修正が適用されると、登録された顧客は、並べ替えを配置する際に、買い物かごの表示ページに正しくリダイレクトされます。 フローは、ゲスト顧客と同様に機能します。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/6a185204>
* _ACP2E-3025_：役割リソースが限られている管理者ユーザーが買い物かごを表示できない
   * _メモの修正_：以前は、制限された管理者は、関連する web サイトの管理パネルから放棄された買い物かごを表示できませんでした。 この修正が適用されると、制限された管理者は、管理パネルから放棄された買い物かごを表示できます。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/d1f7dc95>

### カートとチェックアウト、チェックアウト/1 ページチェックアウト

* _AC-9386_: [ ランダムなバグ ] メールフィールドがレンダリングされないか、チェックアウトの送料または支払いページに表示される時間が長くなります
   * _メモの修正_:Commerceでは、チェックアウトの出荷ページと支払いページの「**[!UICONTROL Email]**」フィールドが期待どおりにレンダリングされるようになりました。 以前は、このフィールドは存在しないか、レンダリングに時間がかかっていました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/e1babcfd>

### 買い物かごと、チェックアウト、注文

* _ACP2E-3097_：管理者から注文する際に、日付フィールドを含む複数のカスタマイズ可能オプションが機能しない製品の日付選択
   * _メモの修正_：管理注文作成プロセスで、カスタマイズ可能な複数の日付オプションを含む製品を設定する際に、すべての日付フィールドの日付選択が正しく表示されるようになりました。 以前は、日付選択は、最初の日付フィールドにのみ表示され、残りのフィールドには日付選択が表示されませんでした。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/b21e5d91>

### カートとチェックアウト、送料

* _AC-12119_：設定可能な製品の即時購入の「最も安い送料」が壊れる
   * _注意を修正_：インスタント購入機能で、最も安価な定額料金の方法ではなく、設定可能な製品に対して、より高価な店舗での配信オプションが誤って選択されました。 この修正により、実際の価格に基づいて正しい発送方法が選択されます。」
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/38811>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/38819>、<https://github.com/magento/magento2/commit/29fe9097>

### カタログ

* _AC-10910_: cron_schedule データベーステーブルのクリーンアップで、既存のジョブ以外のジョブがクリーンアップされない
   * _修正点_: システムは cron_schedule データベーステーブルを自動的にクリーンアップし、システムに存在しないジョブのエントリを削除するようになりました。 これにより、テーブルの行の数を最小限に抑えることで、最適なパフォーマンスが確保されます。 以前は、非アクティブまたは削除されたモジュールのジョブのエントリがクリーンアップされなかったので、cron_schedule テーブルに不要なデータが蓄積されていました。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/38217>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/38693>
* _AC-10953_：設定可能な製品から階層価格が削除されない
   * _修正点_：シンプルな製品から設定可能な製品に変換する際に、製品の階層価格をシステムが正しく削除するようになり、フロントエンドでの正確な価格表示を確保しました。 以前は、シンプルな製品から構成可能な製品に製品が変換された際に、構成可能な製品の階層価格が削除されていなかったので、表示される価格に不一致がありました。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/38390>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/38427>
* _AC-11804_：カテゴリ説明デフォルト以外の storereview では、WYSIWYGが空です
   * _メモの修正_：ストアビューレベルでカテゴリを編集する際に、WYSIWYG エディターにカテゴリの説明が正しく保存され、表示されるようになりました。 以前は、カテゴリの説明をストア表示レベルで保存すると、WYSIWYG エディターは空で表示されていました。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/38622>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/38623>
* _AC-12076_:[ 問題 ] 階層型ナビゲーションのフィルター項目の表現を修正
   * _修正点_：システムは、階層化されたナビゲーションフィルター項目で、「項目」および「項目」という単語を正しく使用するようになりました。これにより、フィルターの説明の明確さと精度が向上します。 以前は、これらの単語が誤って使用されていたので、ユーザーがフィルターオプションを移動する際に混乱が生じる可能性がありました。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/38789>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/37852>
* _AC-12164_：カスタムオプションの日時形式が機能しない
   * _メモの修正_：システムは、設定された日付形式を「日付」タイプの製品カスタムオプションに正しく適用し、日付形式がフロントエンドに正しく表示されるようになりました。 以前は、日付形式の設定に対する変更は、日付タイプの製品カスタムオプションのフロントエンドには反映されませんでした。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/32990>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/38925>
* _AC-6738_: eav_attribute_option_value テーブルに一意のキーがありません
   * _メモの修正_：システムでは、「eav_attribute_option_value」テーブルの「option_id」列と「store_id」列に一意のキーが含まれるようになりました。これにより、オプションが同じストアビューで複数の値を持つ可能性を防ぎます。 以前は、コードに不具合があると、同じストアビューに複数の値を持つオプションが発生し、製品や属性を編集する際に問題が発生する可能性がありました。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/24718>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/28796>
* _AC-8297_: [ 問題 ] ハードコードされた値の代わりに、カテゴリ製品インデクサーの表示クラスを使用します
   * _注意を修正_：システムは、ハードコードされた値の代わりに、カテゴリ製品インデクサーの表示クラスを使用するようになり、モジュール性を向上させました。 以前は、カテゴリ製品インデクサーでハードコードされた値が使用され、柔軟性と適応性に制限がありました。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/37200>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/37199>
* _AC-9375_：新製品ウィジェットで通貨コードが変更されない
   * _メモの修正_：フロントエンドで通貨が変更された場合、システムは新製品ウィジェットの通貨コードを正しく更新し、サイト全体での通貨表示の一貫性を確保できるようになりました。 以前は、フロントエンドで通貨を変更しても、新製品ウィジェットに表示される通貨コードには影響しませんでした。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/37898>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/37899>
* _ACP2E-2224_：設定可能な製品の PLP に通常の価格が表示されない
   * _修正点_：特別価格を持つ子製品を持つ設定可能な製品の製品リストページに、通常価格が表示されるようになりました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-2478_：ビジュアルマーチャンダイジンググリッドにストック情報が正しく表示されません
   * _メモの修正_：選択したストアに従って、在庫が表示されるようになりました。
   * _GitHub コードの投稿_:<https://github.com/magento/inventory/commit/bdbf97ea>
* _ACP2E-2621_：ウィジェットのコンテンツが cms ページで更新されない
   * _メモの修正_：商品が新規および保存済みに設定されると、CMSページのウィジェットのコンテンツが更新され、更新された商品コレクションがページに表示されるようになりました。 以前は、キャッシュ内のウィジェットに使用されるキャッシュ ID が正しくないので、新しい製品を表示するようにページが更新されていませんでした。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2630_：バンドル製品の詳細価格を節約する際の問題
   * _修正メモ_：バンドル製品の節約パフォーマンスの向上。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-2652_: [ オンプレミス ] カタログ価格ルールを作成する際に、インデックス再作成プロセスが非効率的です
   * _修正点_：カタログ価格ルールを保存しても、インデクサーは無効にならず、影響を受ける製品のみが再インデックス化されるようになりました
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2679_:CSV 読み込みを使用して日時タイプの製品属性の時刻を更新します
   * _メモの修正_：書き出されたデータに datetime 属性の時間が含まれるようになりました。 また、import を使用して、このような属性の時間を更新することもできます。 また、「Fields Enclosure」が有効になっている場合、「additional_attributes」列の属性値は二重引用符で囲まれます。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/38306>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/ea79f7dd>
* _ACP2E-2689_：リクエストで web サイト ID が間違っている場合、適切なエラーメッセージが表示されない
   * _メモの修正_：リクエストで web サイト ID が間違っている場合に表示される適切なエラーメッセージが追加されました。 以前は、リクエストで web サイト ID が間違っていた場合の検証はありませんでした。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2785_：画像に影響を与えない既存のスケジュール済み更新を削除すると、製品画像が失われます
   * _修正メモ_：ステージング更新の削除中に製品画像が削除されない。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/c8931218>
* _ACP2E-2799_: [Cloud] 階層価格で使用した場合のバンドル製品価格が正しくない
   * _修正点_：以前は、小数点以下 2 桁に切り上げた特定のパーセンテージ割引を計算すると、買い物かごと製品一覧ページ/製品の詳細ページで異なる最終価格が生成されていました。 この修正が適用されると、バンドル製品の最終価格は製品詳細ページ、製品一覧ページ、ミニ買い物かごページの価格と同じになります。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/38091>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-2805_：カタログ・プロモーション・ルールが quantity_and_stock_status 属性で機能しない
   * _注意を修正_：カタログプロモーションルールで quantity_and_stock_status 属性が考慮されるようになりました。これは、以前は管理者側から新しい製品を生成する際には考慮されていませんでした。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/35627>
   * _GitHub コードの投稿_:<https://github.com/magento/inventory/commit/cf34971d>
* _ACP2E-2837_:REST API を使用して価格を更新する際に、製品エンティティ updated_at 列の値が更新されない
   * _メモの修正_：管理者の「最終更新日」列は、REST API で既存の製品を更新しながら、適切な日時に更新されます。 以前は、「最終更新日」列が正しく更新されていませんでした。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2840_：製品のインポートによって、一意でない値を設定できます
   * _メモの修正_：製品のインポート時に、一意の製品属性に対して一意の値の制約が正しく適用され、そのような属性の値が重複しなくなりました。 以前は、製品のインポートによって一意の値を持つように設定された製品属性に一意でない値を設定することができました。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/38445>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/7e0e5582>
* _ACP2E-2843_: フロントエンドの製品は、シングルストアモードが有効な場合に、ストア固有のデータを使用します
   * _メモの修正_：以前は、デフォルトのストア表示でシングルストアモードを有効にしても、変更内容は web サイトレベルの範囲に移行されませんでした。 この修正を適用した後、シングルストアモードを有効にすると、デフォルトのストアビュー固有のデータが web サイトレベル固有のデータと同期され、製品とカテゴリの競合の可能性が解決されます。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/c8931218>
* _ACP2E-2857_:rest API を使用してカテゴリに「デフォルトの並べ替え基準」を設定できない
   * _メモを修正_:REST/SOAP API リクエストを通じて、カテゴリの default_sort_by を正しく更新します
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-2871_: [Cloud] マーチャントは、ウィッシュリスト数に関する問題に直面しています
   * _メモの修正_：あるストアでウィッシュリストに製品を追加しても、同じブラウザーで開いている他のストアのウィッシュリスト数が増加しなくなりました。 以前は、両方のストアが同じブラウザーに読み込まれた場合、ウィッシュリストのカウントは他のストアでも増加していました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/3a7c4d17>
* _ACP2E-2874_：バンドル製品を使用すると、フロントエンドのカテゴリページに空のスロットが表示される
   * _メモの修正_：現在のストアコンテキストで販売できないバンドル製品は、インデックスが作成されなくなりました。
   * _GitHub コードの投稿_:<https://github.com/magento/inventory/commit/bc37ec76>
* _ACP2E-2905_: マルチサイトアーキテクチャにおける [Cloud] の見積もりの問題
   * _修正点_：以前は、通貨や顧客グループが異なる複数の web サイトを対象としたアーキテクチャでは、ストアに割引を正しく適用できませんでした。 この修正が実装されると、顧客グループ価格の割引が異なる複数の web サイトアーキテクチャが様々なストアに正常に適用されます。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/38506>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-2909_: dynamic-rows.js:658 Uncaught TypeError: バンドル製品の編集中に dataRecord.slice がキャッチされました
   * _メモを修正_：バンドル製品からオプションを削除する際に、ブラウザーコンソールで Javascript エラーが発生することはありません。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/38505>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/93d50f8d>
* _ACP2E-2950_: [Cloud] バンドル製品の注文確認の価格が間違っている
   * _メモの修正_：基準通貨以外の通貨を使用した場合、ストアフロントでバンドルオプションの順序が正しく表示されます。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-2956_:YouTube ビデオのバグの追加
   * _メモの修正_：製品画像とビデオはグローバル範囲で設定されます。 製品ビデオを別の範囲ではなく一方の範囲に含めることはできないので、Youtube API キー設定はグローバル範囲に設定されました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-2964_: store_id=0 の [Cloud] URL 更新のみ
   * _メモの修正_:「URL パス」が正しいストア ID で保存されるようになりました。 以前は、ストア ID が正しくなかったので、カテゴリを移動する際にデータベースに間違った URL パスが残っていました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/9af794a4>
* _ACP2E-3009_: async.operations.all が実行され、エラーが作成されました。
   * _メモの修正_:REST API 呼び出しで製品リンクデータが正しくないと、重大なエラーが発生しなくなりました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-3029_:[Cloud] モバイルの問題 PDP 画像をつまむことができないだけです
   * _メモを修正_:Chromeのモバイルビューで、製品詳細ページ画像のピンチズーム機能がサポートされるようになり、モバイルユーザーエクスペリエンスが向上しました。 以前は、Chromeのモバイルビューで画像をダブルタップしても、画像が期待どおりにズームインされませんでした。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/148c3ead>
* _ACP2E-3058_：オプション名 0 の LayeredNavigation にラベルがありません
   * _メモの修正_：この問題は、属性値 0 の空の値チェッカーをスキップすることで解決されました。 以前は、このフィルターは空と見なされ、問題の原因になっていました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/3a7c4d17>
* _ACP2E-3069_：顧客には、他の顧客グループからの価格が表示されます
   * _修正メモ_：リクエストの X-Magento-Vary の古い値が原因で、顧客グループ関連の情報が間違ったセグメントに保存される問題を修正しました
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/d1f7dc95>
* _ACP2E-3076_：バンドルオプションを削除中にエラーが発生する
   * _メモの修正_：エラーをトリガーしたり、ページが応答しなくなったりすることなく、バンドルオプションが正しく削除されるようになりました。 以前は、バンドルオプションを削除しようとすると、「ページが応答しません」エラーが発生し、製品を保存できませんでした。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/6a185204>
* _ACP2E-3100_: [Cloud] 画像ファイルがNew Relic エラーログに存在しません
   * _修正点_：カスタムプレースホルダーイメージがローカルストレージに同期され、AWS S3 などのリモートストレージを使用する場合に正しくレンダリングされるようになりました。 以前は、リモートストレージを使用する際に、カスタムプレースホルダー画像のレンダリングに失敗し、画像表示とエラーログが壊れていました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/d1f7dc95>
* _ACP2E-3126_: [Cloud] Product Media Gallery GQL 応答が画像の位置で並べ替えられていません
   * _修正点_：メディアギャラリー内の項目がGraphQL レスポンス内の位置で正しく並べ替えられ、正確な表示順が確保されるようになりました。 以前は、メディアギャラリー内の項目が位置で並べ替えられていなかったので、表示順序が正しくありませんでした。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/37671>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/b21e5d91>
* _ACP2E-3136_: [Cloud] サブカテゴリ項目が管理バックエンドのウィジェット編集に表示されない
   * _メモの修正_：新しいウィジェットページのカテゴリツリーに、レベル 5 以上のカテゴリを読み込む際の問題が解消されました。 以前は、ツリーをレベル 5 のカテゴリを超えて読み込むと、一部のカテゴリが欠落していました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/148c3ead>

### カタログ、フレームワーク

* _ACP2E-2949_: [Cloud] フォローアップ：データが変更されたかどうかを確認する際のデータ比較の不一致
   * _メモを修正_：以前は、データが変更されずに（int/float/double などの数値データフィールドに対して） save オブジェクトが毎回呼び出されていました。 フラグ _hasDataChanges を true にトリガーし、save 関数を呼び出します。 また、string でカプセル化された浮動小数点数はチェックしません。 この修正が適用されると、データが変更された場合にのみ save 関数が呼び出されます。 int/float/double-check のデータ値を、関数に渡す値と一緒に指定し、厳密な型照合を行います。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/c8931218>

### カタログ、GraphQL

* _ACP2E-3090_:GraphQLでのカテゴリフィルターの処理：includeDirectChildrenOnly および category_uid
   * _メモを修正_:category_uid でフィルタリングしている場合、直接の子カテゴリのみが取得されます。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/93d50f8d>
* _ACP2E-3166_: [Cloud] Graphql 製品の並べ替えが機能しない
   * _修正メモ_：変数にフィールドが渡された場合に、複数のフィールドで並べ替えられる GraphQl 製品が期待どおりに動作するようになりました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/8459b17d>

### カタログ、価格、ステージング、プレビュー

* _ACP2E-2672_: [Cloud] 特別価格 API エンドポイントが、多数の製品を同時に更新するとエラーを返す
   * _修正メモ_：特別価格の一括更新 API を使用すると、製品と日付範囲ごとに複数のスケジュールされた更新ではなく、日付範囲ごとに 1 つのキャンペーンを作成するようになりました。 また、多数の SKU の処理を高速化するための同時 API リクエストもサポートされます。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/f89a447e>

### カタログ、製品

* _AC-7050_：製品を編集のカテゴリ選択ツリーが、カタログ – > カテゴリで設定された順序と同じではありません
   * _メモの修正_：製品の編集セクションのカテゴリ選択ツリーが、カタログ/カテゴリで設定した順序で正しく表示されるようになり、大きなカタログでの製品の管理が容易になりました。 以前は、「カタログ」 > 「カテゴリ」で設定された表示順序に関係なく、製品編集セクションのカテゴリツリーがカテゴリ作成順に表示されていました。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/36101>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/36104>

### カタログ、検索

* _ACP2E-2757_：カテゴリおよび検索に製品が表示されないが、ダイレクトリンクが機能している
   * _修正点_：以前は、price_* attrbute_code を含む Yes/No カスタム属性はインデックス作成で機能しませんでした。 この修正後、Yes/No カスタム属性は期待どおりに動作します。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-3053_：特定のカテゴリページでの [Cloud] Elastic search error
   * _メモの修正_：以前に、設定チケットが記載されていましたが、複数の製品の価格を 0 にすると、フロントエンドカテゴリページで例外がスローされます。 この修正が適用された後、複数の製品価格 0 とフロントエンドでカテゴリページを読み込むと、例外がスローされず、カテゴリページが正常に読み込まれます。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/c8931218>

### Cloud

* _ACP2E-3010_: [Cloud] PHPSESSID は各POSTリクエストを変更しています
   * _修正点_:L2 Redis キャッシュが有効になっており、お客様がバックエンドから更新されている場合、ログインしたお客様のフロントエンドエリアのPOSTリクエストで PHPSESSID が再生成されなくなりました
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/6a185204>

### コンテンツ

* _AC-10539_:[ 問題 ] 最近表示された項目ウィジェットの価格表示の問題
   * _修正点_：システムは、「最近閲覧した製品」ウィジェットに在庫切れのシンプルな製品の価格を正しく表示し、すべてのウィジェットと製品リストページでの一貫性を確保するようになりました。 以前は、価格読み込みテンプレートの条件により、在庫切れのシンプルな製品の価格が「最近閲覧された製品」ウィジェットに表示されていませんでした。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/38167>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/38159>
* _AC-10596_:[ 問題 ] acl.xsd ファイルの誤字と文法を修正します
   * _修正点_：システムが acl.xsd ファイルの誤字および文法エラーを修正し、ドキュメントの明確さと精度が向上しました。 以前は、acl.xsd ファイルに誤字と誤った文法が含まれていたため、混乱が生じる可能性がありました。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/38061>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/38046>
* _AC-10845_:Pagebuilder バナー画像がギャラリーに表示されない
   * _メモの修正_:Pagebuilder ギャラリーの新しく作成されたフォルダーにアップロードされたバナー画像が正しく表示されるようになり、以前のコンソールエラーが解消されました。 この修正を行う前は、新しいフォルダーにバナー画像がアップロードされた場合にギャラリーに表示されず、コンソールエラーの原因となりました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/c8f87c25>
* _AC-12283_:2.4.5-p8 への更新後、「市外局番が設定されていません」
   * _修正点_:Magento_CSP モジュールが有効で、「dev/js/translate_strategy」が「embedded」に設定されている場合、「Area code not set」エラーをトリガーすることなく、静的コンテンツのデプロイメントプロセスが正常に完了するようになりました。 以前は、これらの条件の下では、静的コンテンツのデプロイメントプロセスが失敗し、「市外局番が設定されていません」というエラーが表示されていました。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/38845>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/38922>
* _AC-9638_：製品ページのWYSIWYG エディターで [ 問題 ] ファイルのアップロードが発生する
   * _修正点_：フォルダーツリーが正しく表示され、最初に「画像とビデオ」タブを展開した後でも、商品ページのWYSIWYG エディターで画像のアップロードが可能になりました。 以前は、「画像とビデオ」タブを展開すると、最初にフォルダーツリーが表示されず、WYSIWYG エディターで画像をアップロードしようとするとエラーメッセージが表示されていました。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/38026>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/38025>
* _ACP2E-2392_:[ オンプレミス ] のダイナミックブロックの問題
   * _メモの修正_：動的ブロック内でウィジェットが正しくレンダリングされるようになりました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/a12063bd>
* _ACP2E-2693_: ニュースレターテンプレートの問題が原因で [ クラウド ] フロントエンドが読み込まれない
   * _修正点_:CMSページのコンテンツセクションからブロックを追加しても、例外が発生しなくなりました
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/ea79f7dd>
* _ACP2E-2836_: ACP2E-2836: [Cloud] ログに調査例外が見つかりました：InvalidArgumentException: vendor/magento/module-rule/Model/ConditionFactory.phpにクラスが存在しません
   * _修正点_:PageBuilder 製品のコンテンツ設定で条件を削除しても、ログファイルに例外が記録されなくなりました。 以前は、PageBuilder 製品のコンテンツ設定で条件を削除すると、フロントエンドで問題が発生しなかったにもかかわらず、重要な例外がログに記録されていました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2-page-builder/commit/36c0f5df>
* _ACP2E-2842_: シングル ストア モードに切り替えました – グローバル コンテンツが表示されなくなりました
   * _修正メモ_：シングルストアモードを有効にすると、ストア表示デザイン設定が web サイトデザイン設定と同期され、フロントエンドでコンテンツの更新が表示されるようになりました。 以前は、シングルストアモードに切り替えると、コンテンツの更新がストアフロントに反映されなくなりました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/7e0e5582>
* _ACP2E-2903_：リンクやその他のユーザビリティの問題を追加しようとすると、ページビルダーが画像に置き換わります。
   * _メモを修正_：これで、画像をクリックすると、ページビルダーテキスト要素の wysiwyg エディター内のリンクが、画像のリンク設定ダイアログに適切なデータを読み込むようになります。 また、エディターで画像へのリンクを追加しても、正しく機能するようになりました。 以前は、画像はリンクに置き換えられました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2-page-builder/commit/4d5db10a>
* _ACP2E-2970_:0 バイトの画像がディレクトリに配置されている場合、古いメディアギャラリーで画像のレンダリングに失敗します
   * _修正点_：機能を中断することなく、メディアギャラリーで 0 バイトの画像を処理できるようになりました。これにより、ディレクトリ内の他の画像を表示し、期待どおりに選択できます。 以前は、メディアギャラリーに 0 バイトの画像が存在すると、ディレクトリ内のすべての画像が表示または選択できなくなっていました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/35b1b1da>
* _ACP2E-3064_:CMS ブロックの編集中にページビルダーでエラーが発生する
   * _メモの修正_：システムは、「ページビルダーがロックを解除せずに 5 秒間レンダリングしていた」というエラーをスローせずに、ページビルダーを使用して管理領域で行われた変更を正しく保存するようになりました。 ブラウザーコンソールで、次の操作を行います。 以前は、このエラーは、変更を保存しようとして、コンテンツを正常に更新しようとすると発生していました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/35b1b1da>、<https://github.com/magento/magento2-page-builder/commit/4d5db10a>
* _ACP2E-3092_: [CLOUD] 買い物かごセクションに、チェックアウトまたは買い物かごを編集するボタンがありません
   * _メモの修正_：バンドル製品がエラーなしでウィジェットを介して買い物かごに追加されるようになりました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/b21e5d91>、<https://github.com/magento/magento2-page-builder/commit/4ebe3f1d>
* _ACP2E-3127_: imagecreatetruecolor （）：引数#2 （$height）は 0 より大きくなければなりません。 特定の画像をアップロードできない
   * _メモの修正_：メディアギャラリーを使用して高さが 0 の画像をアップロードする際に、管理者でエラーが発生する問題を解決し、同期コマンドを使用してアセットの同期に成功しました。 以前は、メディアギャラリーを介して画像をアップロードできず、特定の画像がギャラリーにある場合にも同期コマンドが失敗します。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/6f4805f8>
* _ACP2E-3154_:Google Maps API と競合する Prototype.js Array.from
   * _メモの修正_:Google マップが PageBuilder エディターで正しくレンダリングされるようになりました。 以前は、JavaScript エラーにより、Google マップが正しくレンダリングされませんでした。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/148c3ead>

### 顧客/顧客

* _AC-12162_：フロントエンド – お客様の作成ページで生年月日の検証が失敗する
   * _メモの修正_:moment.js システムの依存関係を最新のマイナーバージョンにアップグレードした後、すべての検証が機能することを確認します
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/de4dfb8e>

### フレームワーク

* _AC-10654_:V1/customers/password エンドポイントの質問/問題
   * _修正点_：システムは、API を介してパスワード変更要求を処理する際に、管理 GUI 内で設定された制約に従うようになり、パスワードリセット機能が悪用される可能性を防ぎます。 以前は、API は、管理 GUI で定義されたルールの外でパスワード変更リクエストを処理することができました。これにより、有効なメールがわかっている場合は、常にリセットメールのストリームが可能になる可能性がありました。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/38238>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/0c53bbf7>
* _AC-10721_:
   * _メモの修正_:league/flysystem Composer の依存関係を最新バージョンにアップグレードします
   * _GitHub の問題_:&lt;<https://github.com/magento/magento2/commit/91cb4d46>>
   * _GitHub コードの投稿_:2.x league/flysystem Composer の依存関係を最新バージョン 3.x にアップグレードします
* _AC-10838_：カタログ検索インデックスプロセスのエラーインデックスプロセス
   * _修正点_: システムは、PHP でコンパイルされた libxml のバージョンに関係なく、エラーが発生することなく再インデックスコマンドを正常に完了するようになりました。 以前は、PHP が特定のバージョンの libxml を使用してコンパイルされた場合、re-index コマンドを実行すると、「Catalog Search index process error during indexation process」エラーが発生していました。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/38254>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/38553>、<https://github.com/magento/magento2/commit/0574ac23>
* _AC-10941_：顧客注文クエリに created_at フィルター、status フィルター、grand_total フィルターが追加され、複数のフィルターが修正されて失敗しました
   * _メモの修正_：システムでは、顧客注文クエリで created_at、status、grand_total フィルターの使用をサポートするようになり、複数のフィルターが正しく適用されない問題を解決しました。 以前は、システムはこれらのフィルターをサポートしていなかったので、1 つのクエリで複数が使用された場合、すべてのフィルターを適用できませんでした。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/38392>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/36949>
* _AC-10971_:https://github.com/magento/magento2/issues/38415
   * _修正点_:PHP 8.2/8.3 で、php リンタで失敗する依存関係は一度に 1 つだけである。league/flysystem
   * _GitHub の問題_:&lt;<https://github.com/magento/magento2/commit/672a2e61>>
   * _GitHub コードの投稿_：このシステムは、league/flysystem パッケージをバージョン 3.0.20 に更新することで PHP 8.2/8.3 をサポートするようになりました。これにより、PHP リンティングエラーが発生しなくなります。 以前は、PHP 8.3 で PHP linter を介して PHP ファイルを実行すると、league/flysystem パッケージにエラーが発生していました。
* _AC-10991_：関連/アップセル/クロスセルブロックや価格インデックス作成からのクエリがランダムに氾濫する
   * _メモの修正_：システムは、関連ブロック、アップセルおよびクロスセルブロックからのクエリを最適化し、パフォーマンスを向上させ、過剰なクエリに起因するサイトのダウンを防ぐようになりました。 以前は、これらのブロックからのクエリでシステムが過負荷になり、重大な遅延が発生し、サイトが停止する可能性がありました。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/36667>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/38050>
* _AC-11423_：例外：警告：ICU 74.1 へのアップグレード以降、配列オフセットにアクセスしようとしています… -> Calendar.php （PHP Intl）
   * _メモの修正_：買い物客またはマーチャントがストアフロントまたは管理者：`main.CRITICAL: Exception: Warning: Trying to access array offset on value of type null in /vendor/magento/framework/View/Element/Html/Calendar.php on line 114 in /vendor/magento/framework/App/ErrorHandler.php:62` にアクセスするたびに、Commerceで exception.log に次の例外がログに記録されなくなりました。 [GitHub-38214](https://github.com/magento/magento2/issues/38214)
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/38214>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/38364>
* _AC-11476_:[ 問題 ] フォームに `method` という名前の要素が含まれている場合の顧客データの問題を修正
   * _メモの修正_：システムは、「method」という名前の要素がフォームに存在する場合でも、フォーム送信で「method」属性を正しく識別するようになりました。 これにより、顧客データの正確な処理が保証されます。 以前は、フォーム要素の名前が「method」の場合、フォーム送信で「method」属性を識別する際に干渉し、顧客データ処理で問題が発生する可能性がありました。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/38484>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/38449>
* _AC-11489_:[ 問題 ]\Magento\Framework\Data\Collection::getItemById の PHPDocs を修正
   * _修正メモ_:\Magento\Framework\Data\Collection::getItemById メソッドの PHPDocs が更新されて、null が戻り値の型として含まれるようになりました。静的分析ツールの問題に対処します。 以前は、メソッドの PHPDocs で戻り値の型として null が指定されていなかったので、条件文でメソッドを使用すると静的分析で警告やエラーが発生していました。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/38485>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/38439>
* _AC-11651_: LoggerProxy の__wakeup メソッドの読み取り専用プロパティを変更しようとしてMagentoが発生しました
   * _修正メモ_：システムで、LoggerProxy の__wakeup メソッドで以前は読み取り専用だったプロパティを変更できるようになり、ユーザーに回避策を強制することなくスムーズに操作できるようになりました。 以前は、LoggerProxy の__wakeup メソッドで読み取り専用プロパティの値を再割り当てしようとすると、問題が発生していました。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/38526>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/c8f87c25>
* _AC-11673_:
   * _修正点_: php-amqplib/php-amqplib の最新バージョンを調べてください。
   * _GitHub の問題_:&lt;<https://github.com/magento/magento2/commit/de4dfb8e>>
   * _GitHub コードの投稿_：最新バージョンの php-amqplib/php-amqplib を更新しました：^3.x
* _AC-11681_:[ 問題 ] AC-2039 AC-1667 アップグレード TinyMCE リファレンス
   * _修正メモ_:composer.json の tinymce 最新バージョンを更新しました
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/38533>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/36543>、<https://github.com/magento/magento2/commit/b34c0a75>
* _AC-11696_:ChangelogBatchWalker が複数のスレッドで動作しない
   * _メモの修正_：システムは、MView インデックス化のプロセスフォークをサポートするようになり、複数のスレッドで動作する場合にインデクサーの実行中にエラーが発生するのを防ぎます。 以前は、複数のスレッドで ChangelogBatchWalker を実行すると、他のスレッドが使用しているテーブルが削除され、インデクサーの実行中にエラーが発生していました。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/38246>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/38248>
* _AC-11781_:[ 問題 ] 誤った名前の変数を名前変更
   * _メモの修正_：システムは、払い戻しできる金額を含む変数に正しく名前を付け、デバッグ中の混乱を防ぐようになりました。 以前は、この変数は誤って totalRefund と呼ばれていたため、開発者にとって誤解が生じる可能性がありました。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/38609>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/36205>
* _AC-11808_:
   * _修正点_:Adobe Commerce Core の依存関係リストの調査とアップグレード
   * _GitHub コードの投稿_:Adobe Commerce Core 依存関係リストをアップグレードする必要があります 
* _AC-11819_：一部の設定で 2.4.7 に組み込み FPC キャッシュが壊れる
   * _メモの修正_:MAGE_RUN_CODE パラメーターが設定されている場合、システムがページを正しくキャッシュし、最適なパフォーマンスを確保できるようになりました。 以前は、これらの条件下でページがキャッシュされなかったので、パフォーマンスの問題が発生する可能性がありました。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/38626>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/38646>、<https://github.com/magento/magento2/commit/0c53bbf7>
* _AC-11829_:[ 問題 ] 開発者モードと実稼動モードの間で例外処理の不整合が発生する問題を修正しました
   * _メモの修正_：システムは、開発者モードと実稼動モードの間で一貫して例外を処理し、例外がスローされたときにログインページへの予期しないリダイレクトを防ぐようになりました。 以前は、例外処理に不整合があると、例外メッセージが表示されるのではなく、実稼動モードでログインページにリダイレクトされる場合がありました。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/38639>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/37712>
* _AC-11852_: token_list.phtml の「PayPal アカウント」の翻訳を置き換えます
   * _修正メモ_：システムは、保存済みの支払い方法ページで、トークン化可能なアカウントの支払い方法のセクションに「PayPal アカウント」ではなく「アカウント」とラベルを付けるようになり、その機能をより象徴的なものにしました。 以前は、このセクションは「PayPal アカウント」と特別にラベル付けされていました。これは、他のトークン化可能なアカウントの支払い方法が追加された場合に誤解を招いていました。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/35622>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/37959>
* _AC-11905_:[ 問題 ] 静的コンテンツのデプロイ – タイプエラー
   * _修正点_：静的コンテンツのデプロイメント中に空の LESS ファイルをシステムが正しく処理し、「LESS ファイルが空です」というエラーメッセージが表示されるようになりました。 以前は、デプロイメント中に空の LESS ファイルが見つかった場合、誤ったタイプエラーがスローされていました。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/38682>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/38683>
* _AC-11911_:
   * _修正点_：ライブラリをアップロードするための移行後の jQuery/fileuploader の CSS のクリーンアップ
   * _GitHub の問題_:&lt;<https://github.com/magento/magento2/commit/7cabfb46>>
   * _GitHub コードの投稿_:jQuery/fileUploader ライブラリは Uppy ライブラリに移行されたので、このライブラリを削除しました
* _AC-12002_:[ 問題 ] [ 表示 ] リンクとスクリプトタグの余分なスペースを削除
   * _メモの修正_：システムのリンクタグとスクリプトタグに余分なスペースがなくなり、よりクリーンで効率的なコードが提供されるようになりました。 以前は、link タグと script タグの属性の間に二重のスペースが見つかっていました。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/32920>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/32919>
* _AC-12015_:
   * _修正点_:jsTree ライブラリへの移行後の ExtJs フォルダーのクリーンアップ
   * _GitHub の問題_:&lt;<https://github.com/magento/magento2/commit/7cabfb46>>
   * _GitHub コードの投稿_：関連機能が jsTree に移行されたので、extJs フォルダーを削除しました
* _AC-12022_:
   * _修正点_:monolog/monolog システムの依存関係を最新のメジャーバージョンにアップグレードします
   * _GitHub の問題_:&lt;<https://github.com/magento/magento2/commit/edcd0dcc>>
   * _GitHub コードの投稿_：システムを更新して、「monolog/monolog:^3.x」ライブラリの最新のメジャーバージョンを使用するようにし、互換性とパフォーマンスの向上を図りました。 以前は、システムは「monolog/monolog」ライブラリの古いバージョンを使用していましたが、潜在的な問題や制限につながる可能性がありました。
* _AC-12023_:
   * _修正点_:wikimedia/less.phpの依存関係を最新のメジャーバージョンにアップグレードします
   * _GitHub の問題_:&lt;<https://github.com/magento/magento2/commit/edcd0dcc>>
   * _GitHub コードの投稿_：システムを更新して、「wikimedia/less.php」ライブラリの最新のメジャーバージョン 5.x を使用するようにし、互換性と最新機能を確保しました。 以前は、システムは古いバージョンのライブラリを使用しており、セキュリティの問題が発生する可能性がありました。
* _AC-12024_:
   * _修正点_:jquery/validate ライブラリの依存関係を最新のマイナーバージョンにアップグレードします
   * _GitHub の問題_:&lt;<https://github.com/magento/magento2/commit/de4dfb8e>>
   * _GitHub コードの投稿_:jquery/validate ライブラリの依存関係を最新のマイナーバージョン 1.20.0 にアップグレードします
* _AC-12025_:
   * _修正点_:moment.js システムの依存関係を最新のマイナーバージョンにアップグレードします
   * _GitHub の問題_:&lt;<https://github.com/magento/magento2/commit/de4dfb8e>>
   * _GitHub コードの投稿_:moment.js システムの依存関係を最新のマイナーバージョン 2.30.1 にアップグレードしました
* _AC-12267_:
   * _修正点_:Redis セッションの接続再試行をサポートし、colinmollenhour/php-redis-session-abstract v2.0.0 と互換性があります
   * _GitHub の問題_:&lt;<https://github.com/magento/magento2/commit/672a2e61>>
   * _GitHub コードの投稿_:adobe commerce と互換性のある colinmollenhour/php-redis-session-abstract v2.0.0 の最新バージョンを更新しました
* _AC-12268_:
   * _修正メモ_:League/flysystem Composer の依存関係を最新バージョンにアップグレードします
   * _GitHub コードの投稿_:2.x league/flysystem Composer の依存関係を最新バージョン 3.x にアップグレードします
* _AC-12594_:[ 問題 ] 生成されたデータに対して、一般設定ではなくコンパイル済み設定を使用してください
   * _修正メモ_：システムでは、生成されたデータに対して、一般的な設定の代わりにコンパイル済みの設定を使用するようになりました。これにより、ネットワーク転送が削減され、特定のバージョンのコードに依存するデータのオーバーヘッドが軽減されます。 この変更により、コンテナの入れ替え中に共有インスタンスでキャッシュが上書きされることがなくなり、安定性が向上し、ダウンタイムが短縮されます。 以前は、特定のコアクラスで共有設定タイプが使用されていました。これにより、複数のサーバー間でコードバージョンの違いが原因で、キャッシュの上書きやアプリケーションのダウンタイムが発生する可能性がありました。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/38785>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/29954>
* _AC-12597_:[ 問題 ] e1ccdb で削除された extjs からファイルへの参照を削除…
   * _メモの修正_：システムは、以前に削除された extjs からファイルへの参照を削除するようになり、ブラウザーのコンソールとシステムログファイルのエラーを排除します。 以前は、これらの参照が原因で、参照ファイルが存在しないためにエラーが発生していました。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/38960>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/38951>
* _AC-12715_:
   * _修正メモ_：最新バージョンへのアップグレード中の laminas composer の依存関係を更新します
   * _GitHub の問題_:&lt;<https://github.com/magento/magento2/commit/b34c0a75>>
   * _GitHub コードの投稿_：システムは、laminas composer の最新バージョンの依存関係をサポートするようになりました。
ラミナス/ラミナス – サービスマネガー
ラミナス/ラミナス サーバ
laminas/laminas-stdlib
ラミナス/ラミナスバリデーター
互換性と最新機能の確保。 以前は、これらの依存関係を最新バージョンに更新すると、後方互換性の問題が発生し、テストが失敗する可能性がありました。
* _AC-12778_: [ 問題 ] マイナークリーンアップ：sprintf の誤った使用を修正しました。ここでは 2 つのプレースホルダーしか使用せず、w...
   * _メモの修正_：適切な数のプレースホルダーを持つ sprintf 関数がシステムで正しく使用され、コードのクリーン性と一貫性が向上しました。 以前は、sprintf 関数が余分な引数と共に誤って使用されていました。これにより重大な問題は発生しませんが、正しい使用方法ではありませんでした。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/39062>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/38628>
* _AC-12866_:
   * _修正メモ_：非推奨（廃止予定）の削除 – PhpUnit10 統合テスト
   * _GitHub の問題_:&lt;<https://github.com/magento/magento2/commit/edcd0dcc>>
   * _GitHub コードの投稿_:PHPUnit 非推奨（廃止予定）の解決
* _AC-12868_:
   * _修正メモ_：非推奨（廃止予定）の削除 – PhpUnit10 WebApi テスト
   * _GitHub の問題_:&lt;<https://github.com/magento/magento2/commit/edcd0dcc>>
   * _GitHub コードの投稿_:PHPUnit 非推奨（廃止予定）の解決
* _AC-12869_:[ 問題 ]Magentoモジュールで参照されている誤ったクラスを修正。
   * _修正メモ_：システムはモジュール内のクラスを正しく参照するようになり、よりスムーズな操作を確保し、既存のクラス以外のクラスによるクラッシュを防ぎます。 これには、Indexer モジュールと Creditmemo モジュールのバグ修正、および PrintAction クラスの HttpGetActionInterface の実装が含まれます。 以前は、誤ったクラス参照はエラーやシステムクラッシュの可能性につながり、クレジットメモPDFファイルのファイル名や在庫のインデックス再作成などの特定の機能が期待どおりに動作しませんでした。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/39126>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/37784>
* _AC-6754_:js ファイルの誤字エラー。
   * _メモの修正_:JavaScript ファイルの「サブスクライバー」という用語が正しく使用され、関連する機能が適切に機能するようになりました。 以前は、JavaScript ファイルの入力ミスによって、「subsctibers」という用語が誤って使用されていました。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/36163>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/36171>
* _AC-8353_: [ 問題 ] 禁止されている `@author` タグを削除します
   * _修正点_：システムは、特定のモジュールから禁止されている `@author` タグを削除することで、コーディング標準に準拠するようになり、よりクリーンで標準化されたコードを保証します。 以前は、`@author` タグは一部のモジュールに含まれていましたが、これは確立されたコーディング標準に反していました。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/37253>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/37003>
* _AC-8356_: [ 問題 ] `Magento_Customer` から禁止されている `@author` タグを削除する（パート 2）
   * _修正点_：システムは、特定のモジュールから禁止されている `@author` タグを削除することで、コーディング標準に準拠するようになり、よりクリーンで標準化されたコードを保証します。 以前は、`@author` タグは一部のモジュールに含まれていましたが、これは確立されたコーディング標準に反していました。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/37250>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/37000>
* _AC-8659_: editorconfig 構文のスペースが [{composer,auth}.json のルールを中断します ]
   * _修正メモ_:editorconfig の構文エラーを修正した後、システムで 4 空白のインデントが composer ファイルと auth.json ファイルに正しく適用されるようになりました。 以前は、editorconfig 構文にスペースがあったため、これらのファイルが誤って 2 スペースのインデントでフォーマットされていました。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/37394>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/37395>
* _AC-8984_: [ 問題 ] 特定の setup cli コマンドの出力に、さらに色を追加します
   * _修正点_：特定の設定コマンドラインインターフェイス（CLI）コマンドの出力に色が追加され、読みやすさとユーザーエクスペリエンスが向上しました。 以前は、これらのコマンドの出力は、色の区別がないため読みにくくなっていました。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/29335>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/29298>
* _AC-9630_:Magentoをアップグレードすると、必要な都道府県を含む新しい国が追加されたときに、general/region/state_required がリセットされます。
   * _修正点_：システムでは、必要な状態を持つ新しい国が追加された場合にのみ、変更された国を「general/region/state_required」設定に追加するようになりました。これにより、地域が無効であると想定されるカスタムコードの中断を防ぐことができます。 以前は、必須の状態を持つ新しい国を追加すると、「general/region/state_required」設定が必須の状態を持つデフォルトの国にリセットされ、ショップが壊れる可能性がありました。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/37796>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/38076>
* _AC-9712_: https://github.com/magento/magento2/issues/37841
   * _注意を修正_：複雑な `calc` 式を持つ php と nodejs ライブラリ （grunt）の間の less コンパイルの違い
   * _GitHub の問題_:&lt;<https://github.com/magento/magento2/commit/b34c0a75>>
   * _GitHub コードの投稿_：更新後の php と nodejs ライブラリ（grunt）の less コンパイルの違いを修正しましたwikimedia/less.php:^5.x
* _ACP2E-2692_：部分インデックス作成の実行時に「Base table or view not found」エラーが発生する
   * _修正点_：セカンダリ db 接続の場合、部分再インデックスが大きな変更ログで正しく機能するようになりました
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2844_:MariaDB を 10.5.1 以降にアップグレードした後の問題
   * _修正メモ_:Mysql のアップグレード後に DB の日時値が 000-00-00 00:00:00 に変換される問題を修正しました
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/a12063bd>
* _ACP2E-2855_：データに変更があるかどうかを確認する際のデータ比較でのタイプの不一致
   * _メモを修正_：以前は、データが変更されずに（int/float/double などの数値データフィールドに対して） save オブジェクトが毎回呼び出されていました。 フラグ _hasDataChanges を true にトリガーし、save 関数を呼び出します。 この修正が適用されると、データが変更された場合にのみ save 関数が呼び出されます。 int/float/double-check のデータ値は、関数に渡される値で、厳密な型照合を行います。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-2959_: [Cloud] インポートは、ディレクトリ var では使用できません
   * _メモを修正_：ファイル名に関係なく、製品を正常に読み込むことができます。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/3a7c4d17>
* _ACP2E-2966_: ipad mini では、メニューとヘッダーはモバイルとして読み込まれますが、代わりにデスクトップとして読み込む必要があります。
   * _修正点_：幅 768 px のデバイスがデスクトップとして扱われるようになり、メニューとヘッダーが正しく読み込まれるようになります。 以前は、幅が 768 px のデバイスはモバイルとして扱われ、メニューとヘッダーがモバイル表示に読み込まれる原因となりました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/35b1b1da>、<https://github.com/magento/magento2-page-builder/commit/4d5db10a>

### フレームワーク，GraphQL

* _AC-7976_: [ 問題 ] GraphQL スキーマにカスタムスカラータイプのサポートが導入されました
   * _修正点_:GraphQL スキーマのカスタムスカラータイプがサポートされるようになり、開発者がカスタムスカラータイプと実装を定義できるようになりました。 この機能は、HTML、メール、URL、日付など、検証が必要になる可能性のある値を表現する場合や、EAV 属性などのより高度なケースで特に役立ちます。 以前は、GraphQLでのカスタムスカラータイプの処理はサポートされていませんでした。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/36877>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/34651>、<https://github.com/magento/magento2/commit/0574ac23>

### GraphQL

* _AC-11729_:header_GraphQl は、Magento値が検証に合格しない場合でもヘッダー処理を実行します
   * _修正点_：システムは、ヘッダー処理が 1 回だけ、ヘッダー値が検証に合格した場合にのみ実行されるようにし、セキュリティを強化し、潜在的な脆弱性を防ぐようになりました。 以前は、ヘッダ値が検証に合格しない場合でもヘッダ処理を実行していたため、ヘッダ値の二重処理により、潜在的な脆弱性や予期しない動作が発生する可能性がありました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/c8f87c25>
* _AC-8951_：物理的なギフトカードオプションの並べ替え順序が正しくありません
   * _メモの修正_:GraphQL経由でクエリされた場合、物理的なギフトカード商品のオプションが正しく並べ替えられ、Luma テーマと一貫したレンダリングが保証されるようになりました。 以前は、luma テーマに応じて並べ替え順序が正しくなかったので、送信者名、受信者名、金額などのオプションの表示と順序が正しくありませんでした。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/1bafc571>
* _AC-9157_: [GraphQL] ステージング更新プログラムの作成/編集/移動/削除時に、リゾルバーキャッシュが無効になります
   * _メモの修正_：ステージング更新の作成、編集、移動または削除時に、ただしステージング更新がエンティティに適用された場合にのみ、リゾルバーキャッシュが無効化されないことがシステムにより確認されるようになりました。 以前は、ステージング更新が適用される前であっても、リゾルバーキャッシュが早い段階で無効化されていたため、不要なキャッシュの無効化が行われていました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/0c53bbf7>
* _ACP2E-2642_：コンテンツのステージングの更新で、Fastly キャッシュがクリアされない
   * _メモの修正_:PageBuilder コンテンツ関連のエンティティが更新される際に、PageBuilder コンテンツの応答キャッシュを持つGraphQLが無効になりました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2653_：レイヤーナビゲーションの無効化 – Graphql から集計を削除しない
   * _修正点_：この問題は、「カタログ/階層ナビゲーション/カテゴリフィルターを表示」の管理設定で、GraphQL クエリを通じてカテゴリ集計を含む商品検索をリクエストする際にチェックを適用した後に修正されました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/12e071c3>
* _ACP2E-2928_：価格フィルター {from:&quot;0&quot;} を含んだGraphQL Products 呼び出しで、結果が返されない
   * _メモの修正_：以前は、ゼロ価格のフィルターを使用して検索した Graphql 製品は、例外がスローされたので、結果をまったく返しませんでした。 これで、検索が期待どおりに結果を返します。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/c971859e>
* _ACP2E-3128_:[Cloud] ノードの見積もりを使用した getPurchaseOrder のGraphQL呼び出しの不具合
   * _修正点_：発注書GraphQLの呼び出しでは、内部サーバーエラーが発生することなくタスクを実行できます。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/6f4805f8>
* _ACP2E-3184_:「すべてのストア表示」で製品が有効になっていない場合、[Cloud] 設定可能な製品が実稼動サイトに表示されない
   * _メモの修正_：製品が「すべてのストア表示」では有効になっていなくても、特定のストア表示範囲で有効になっている場合でも、サイト内の設定可能な製品が正しく表示されるようになりました。
以前は、商品が「すべてのストア表示」で無効になっていて、特定のストア表示範囲でのみ有効になっている場合、GraphQLの応答で商品の属性が正しく表示されず、商品が正しく表示されませんでした。
   * _GitHub コードの投稿_:<https://github.com/magento/inventory/commit/3f300077>
* _ACP2E-3190_:[Cloud] 製品の graphql で、同じ単純な製品が複数の設定可能な製品に割り当てられている場合にエラーが発生する
   * _メモを修正_：以前は、同じシンプルな製品を持つ個別の設定可能な製品では、grapQL がエラーを返していました。 この修正が適用された後、同じ単純な製品を持つ様々な設定可能な製品が適用されると、grapQL はエラーなく結果を返します。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/148c3ead>
* _ACP2E-3253_:GraphQLの買い物かご項目 V2 のページネーションが正しく機能しない
   * _修正点_：この問題は、コレクションクエリの現在のページ引数に正しい値を渡すことで修正されました。 以前は、現在のページを設定するために間違った値が渡され、問題が発生していました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/8459b17d>

### GraphQL、インベントリ/MSI

* _ACP2E-2607_：ソースと宛先の買い物かごに同じバンドル項目がある場合、MergeCart ミューテーションが例外をスローする
   * _修正メモ_ : 「– 
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/c971859e>、<https://github.com/magento/inventory/commit/db0620da>

### GraphQL、インベントリ/MSI、パフォーマンス

* _ACP2E-1716_：アップグレード後のサイトダウン
   * _メモを修正_:GraphQl を使用してバンドル製品を取得するパフォーマンスが向上しました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/ba25af8a>、<https://github.com/magento/inventory/commit/bdbf97ea>

### GraphQL, パフォーマンス

* _AC-9569_: [GraphQL リゾルバー ] カスタマーリゾルバーデータがインポートから無効化されません
   * _メモの修正_：読み込みを通じてユーザーが編集または削除された場合、GraphQL カスタマーリゾルバーキャッシュが期待どおりに無効になりました。 以前は、キャッシュは無効化されておらず、読み込み時に顧客データを編集または削除することができました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/0574ac23>

### GraphQL、検索

* _ACP2E-2809_:GraphQLの商品リストで複数のパラメーターで並べ替えても、機能しない
   * _メモを修正_:GraphQl での複数フィールドによる製品の並べ替えが、ドキュメントの説明どおりに動作するようになりました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/c971859e>

### インポート/エクスポート

* _AC-12172_：カスタムオプションタイプ : ファイルを指定した場合の製品の読み込み時の問題（作成された製品にはカスタムオプションの価格が含まれておらず、指定された最初のファイルタイプの拡張子のみが表示される）
   * _メモの修正_：システムは、「ファイル」タイプのカスタムオプションを使用して製品データを正しく読み込み、提供されたすべてのファイル拡張子が表示され、カスタムオプションの価格が含まれるようになりました。 以前は、製品の読み込み時に、タイプ「ファイル」のカスタムオプションに複数のファイル拡張子が指定されている場合、最初の拡張子のみが表示され、カスタムオプションの価格が表示されませんでした。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/38805>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/38926>
* _ACP2E-2710_: インポート履歴グリッドのインポート操作の実行時間が間違っています
   * _メモを修正_：読み込みレポートの実行時間は、管理者ロケールとは無関係に正しく表示されます。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/ea79f7dd>
* _ACP2E-2737_：読み込みを使用して、同じメールアドレスで重複した顧客が作成される
   * _メモの修正_：アカウント共有をグローバルに設定している場合に顧客を読み込むと、システムに存在する読み込まれた顧客が更新されます。
以前に読み込んだ顧客が複製されました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/c971859e>
* _ACP2E-2902_：製品のインポートの追加/更新カスタマイズ可能なオプションの複製
   * _メモの修正_：この問題は、製品オプションの CSV 読み込み時に製品オプションに正しいストアを割り当てることで解決されました。
以前は、は、それぞれのストアではなく管理ストアに割り当てられていました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/3a7c4d17>
* _ACP2E-2990_：顧客の「created_at」日付が、エクスポート時にストアタイムゾーンに変換されない
   * _メモの修正_：列「created_at」の日付値は、顧客の書き出し CSV セクションのストアタイムゾーンに基づいて適切な日付形式に変換されます。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/3056e9cb>
* _ACP2E-3165_: [Cloud] CSV を使用したデータの読み込みで、データのチェック中にエラーが発生します
   * _修正点_:CSV の読み込み中にデータを確認する際にエラーが発生することはありません。 以前は、管理者から CSV を使用して読み込みセクションのデータを確認すると、「このメールと web サイトコードを行が 1 に一致する顧客が見つかりません」というエラーメッセージが表示されていました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/8459b17d>

### インストールと管理

* _ACP2E-2102_：管理パネルに「Vcl for Varnish 7」ボタンが表示されない
   * _メモの修正_：管理パネルに「Export VCL for Varnish 7」ボタンが追加されました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/a4fbf702>

### インベントリ/MSI

* _AC-11593_：属性を含むマップを追加する際に、Google Google API キーが機能しない
   * _修正点_：最新のGoogle Maps API バージョン 3.56 がサポートされるようになり、エラーを発生させることなく、ページビルダーメニューからステージにマップコンテンツブロックを正常に追加できるようになりました。 以前は、Google Maps API バージョンとの互換性の問題により、マップコンテンツブロックを追加できず、「問題が発生しました」というエラーメッセージが表示されていました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/0574ac23>
* _ACP2E-2794_：空のスペースを含む製品リストの [Cloud] に関する重大な問題
   * _修正点_：製品が「在庫切れ」に設定されている場合、システムは製品リストを空のスペースなしで正しく表示するようになり、利用可能な製品を一貫した正確な状態で表示できるようになりました。 以前は、製品を「在庫切れ」に設定すると、製品リストに空のスペースが表示され、レイアウトが中断され、顧客を混乱させる可能性がありました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/ea79f7dd>、<https://github.com/magento/inventory/commit/b59e48ca>

### 順序

* _AC-10828_：バックエンド注文の概要画面：受注品目レベルでバックオーダー数量が表示されない
   * _メモの修正_：バックエンド注文の概要画面の数量列に、バックオーダーされた項目数が表示されるようになりました。 これにより、ユーザーは順番にすべての項目のステータスを正確に追跡できます。 以前は、数量列には注文、請求、出荷された品目の数のみが表示されていましたが、バックオーダーされた品目の数は表示されていませんでした。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/38252>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/38320>
* _AC-10994_:[ 問題 ] 注文アドレスレンダラーで使用されているストア ID が正しくない
   * _メモの修正_：システムは、注文アドレスをレンダリングする際に、注文に関連付けられたストア ID を正しく使用するようになりました。これにより、それぞれのストア ID に従ってアドレスが正しくフォーマットされます。 以前は、システムが現在のストア ID を誤って使用していたので、異なるストアからの複数の注文メールを送信する必要がある場合に、アドレスの形式が正しくなくなる可能性がありました。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/38412>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/37932>
* _AC-11798_:[ 問題 ] 送料が異なる
   * _修正注意_：出荷価格が税金構成の設定に従って印刷されたPDFで正しく表示されるようになり、受注請求書ビュー・ページと印刷された請求書との間の一貫性が確保されます。 以前は、印刷されたPDFに表示される送料は、税設定に関係なく、税金を除外していました。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/38608>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/38595>、<https://github.com/magento/magento2/commit/1bafc571>
* _ACP2E-2622_：既存の注文の詳細で電話番号に対する変更を保存できない
   * _メモの修正_：注文住所の電話フィールドに、国際名のプレフィックス 00 を追加できるようになりました
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/38201>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/12e071c3>
* _ACP2E-2734_：メールの送信に失敗する
   * _メモの修正_：システムには、停止前にメールを送信する試行回数を指定する設定オプション async_sending_attempts が含まれるようになりました。「非同期送信」が有効な場合の、失敗したメールの送信処理が改善されます。 以前は、メールの送信に失敗すると、システムは継続的にメールを再送信しようとするので、システムログでエラーメッセージの無限ループが発生していました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-2756_: [Cloud] 部分的に出荷された注文の一部払い戻し時に、注文ステータスが完了に変更されました
   * _修正注意_：まだ出荷されていない品目がある場合、クレジットメモを発行しても、注文ステータスは「完了」に変更されません。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/7e0e5582>
* _ACP2E-3002_：開発ドキュメントに示されているように、[CLOUD] で管理 UI からのメール送信を無効にできない
   * _メモの修正_：メール通信が無効な場合に、販売メールが送信されるのをシステムが正しく防ぐようになりました。 メール通信を再度有効にすると、これらのメールは送信されなくなります。 以前は、メール通信が無効になっている間に開始した販売メールは、メール通信が再度有効になった場合でも送信されていました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/c8931218>
* _ACP2E-3045_：注文は全額返金されずにクローズされました
   * _修正メモ_：支払がキャプチャされていない注文で出荷が作成された場合、システムは注文ステータスを「処理中」に、請求書ステータスを「保留中」に正しく維持するようになりました。 これにより、注文が全額払い戻された後にのみ「クローズ」とマークされます。 以前は、請求書が保留中の注文に対して出荷を作成すると、注文ステータスが誤って「クローズ」に変更されていました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/6a185204>

### 注文、返品

* _ACP2E-2982_：重複クレジット・メモの受注払戻の結果
   * _修正点_:2 つの同一のリクエストが同時に実行された際に REST API を使用して返金を行うと、重複したクレジットメモが作成されなくなりました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/a4fbf702>

### 注文、税

* _ACP2E-3003_: [CLOUD] クロスボーダー取引を有効にし、クーポン割引を適用する際に、RESTFUL 注文 API の base_row_total が正しくありません
   * _メモの修正_：クロスボーダー取引が有効化され、クーポン割引が適用されている場合、RESTFUL 注文 API から正しい base_row_total が返されるようになりました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/9af794a4>

### その他の開発者ツール

* _AC-10658_:[ 問題 ] visual.phtml のHTML構文エラーを修正しました
   * _メモの修正_:visual.phtml ファイルの開始タグが正しく閉じられ、HTMLの構文が適切に設定されるようになりました。 以前は、開始タグが正しく閉じられず、HTML構文エラーが発生していました。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/38247>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/37457>
* _AC-11474_:[ 問題 ] bin/magento maintenance:status コマンドで「active」が「enabled」に変更されました
   * _メモの修正_：システムは、メンテナンスモードコマンドのステータスを「アクティブ」から「有効」に、および「非アクティブ」から「無効」に変更して、より正確なステータスメッセージを提供するようになりました。 以前は、メンテナンスモードコマンドのステータスメッセージが「アクティブ」または「非アクティブ」と表示されていたので、混乱が生じる可能性がありました。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/38486>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/38410>
* _AC-12571_：カテゴリツリー内を移動すると、Redis で「Redis セッションが同時接続を超えました」というエラーが発生する
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/38851>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/0611e750>

### 支払額

* _ACP2E-2841_：ペイフローは、トランザクションを表示画面の「取得」ボタンをクリックするたびに、新しいトランザクションを作成します
   * _メモの修正_：取引情報を正しく取得できるようになり、取引表示画面で取得ボタンがクリックされるたびに新しい支払い取引が作成されるようになりました。 以前は、取得ボタンをクリックすると、既に支払われた注文の新しい支払いトランザクションが誤って作成されていました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-3028_：カナダの Paypal マーチャントアカウントの PDP に Paylater メッセージが表示されない
   * _修正メモ_：アカウントの請求先住所または発送先から購入者の国を特定できる場合、システムは、カナダの PayPal 加盟店のアカウントに対して PayLater メッセージを製品詳細ページ（PDP）に正しく表示するようになりました。 以前は、パラメーターが見つからないため PayLater メッセージが表示されず、ブラウザーコンソールでエラーが発生していました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/6a185204>

### パフォーマンス

* _AC-12000_:[ 問題 ] コードのクリーンアップを行い、新しい重要なヘッドブロックを追加して、アセット前に重要な css を移動します
   * _修正メモ_：システムに新しい重要なヘッドブロックが含まれ、重要な CSS をアセットの前に移動するようになり、フロントエンドでより多くのカスタマイズとパフォーマンスの最適化が可能になります。 以前は、重要な CSS がアセットの前に配置されていなかったので、カスタマイズと最適化の機会が制限されていました。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/38748>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/35580>
* _AC-12176_:mysql ホストにポート情報が含まれている場合、テーマのコンパイルが中断する
   * _修正メモ_：システムでは、ポート情報を含む MySQL ホスト設定を正しく処理できるようになり、テーマのコンパイルが成功するようになりました。 以前は、データベース接続の MySQL ホスト設定にポート情報が含まれていると、テーマのコンパイルが失敗していました。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/38799>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/38842>
* _ACP2E-2494_：買い物かごルールに製品属性を読み込む際のパフォーマンスの問題
   * _修正点_：販売ルールのクエリパフォーマンスが向上しました。約 150 ミリ秒から 1 桁のミリ秒に向上しました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2673_：価格部分インデックス作成のパフォーマンス
   * _修正点_：インデックス作成プロセス内で使用される削除クエリの一部を最適化することで、価格の部分的なインデックス作成のパフォーマンスが向上しました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2850_：非同期注文処理+利用条件を使用すると、マルチストアセットアップで注文が拒否される
   * _修正点_：契約条件が有効になっているデフォルト以外の web サイトから発注された注文が処理されるようになりました。
それらが自動的に拒否される前に。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-2910_：注文 REST API 呼び出しの実行に時間がかかる
   * _メモの修正_：システムは、妥当な期間内に Order Rest API 呼び出しを実行するようになったので、多数の注文を取得する際のパフォーマンスが向上しました。 以前は、Order Rest API 呼び出しの実行に時間がかかり、多数の注文を取得する際に遅延が発生していました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/001e5188>

### 製品

* _AC-10535_：設定可能な関連HTML名の特殊文字がプロダクトエンティティに変換される。
   * _修正点_：設定可能な商品を編集する際、関連する商品の名前に含まれる特殊文字が正しく保持され、HTMLエンティティに変換されなくなりました。 以前は、設定可能な商品が編集されると、関連する商品名の特殊文字がHTMLエンティティに変換されていました。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/38146>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/38447>
* _AC-10947_:ProductRepository 関数 GetById で正しいキャッシュキーが作成されない
   * _修正メモ_：ストア ID が文字列または整数として渡されたかどうかに関係なく、システムは ProductRepository の関数 GetById にキャッシュキーを正しく作成するようになりました。 これにより、以降の呼び出しでメモリから製品が確実に取得されるので、パフォーマンスが向上します。 以前は、キャッシュキーの作成が正しくないために、同じパラメーターを指定しても、関数が呼び出されるたびにシステムがデータベースから製品を取得していました。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/38384>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/38433>
* _AC-11992_: [ 問題 ] [MFTF]AdminClickAddOptionForBundleItemsActionGroup を追加しました
   * _メモの修正_：システムに AdminClickAddOptionForBundleItemsActionGroup が含まれるようになり、管理パネルの機能が強化されました。 以前は、このアクショングループは使用できませんでした。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/30857>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/30838>
* _AC-5969_: AlertProcessor – 引数#2 （$storeId）は int 型、指定された文字列にする必要があります
   * _メモの修正_：ストア ID が正しいデータタイプであることを確認することで、製品のアラートメールが正しくトリガーされるようになりました。 以前は、ストア識別子のタイプの不一致が原因で、製品アラートメールが送信されていませんでした。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/35602>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/0574ac23>
* _ACP2E-2944_：特定の列で [Cloud] addFilterToMap 関数が機能しない
   * _メモを修正_：カスタムモジュールを注文グリッドで使用できるようになりました。 以前は、カスタムモジュールの使用中にエラーが発生していました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/3a7c4d17>

### プロモーション

* _ACP2E-2602_：招待からアカウントを作成する際に、顧客属性が表示されない
   * _メモの修正_：顧客属性は、招待からアカウントを作成する際に使用できます。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2627_：注文のキャンセルで失敗した支払で、クーポンごとの使用制限を持つクーポンコードがリリースされない
   * _メモの修正_：システムでは、注文の作成またはキャンセル時にクーポンの使用を直ちに更新し、潜在的なデッドロックを防ぐためにルールの使用をキューに追加するようになりました。 これにより、「クーポンごとに使用」の制限を持つクーポンコードがリリースされ、支払いの失敗によって注文がキャンセルされた場合に再利用できるようになります。 以前は、システムはそのような場合に再利用するためにクーポンコードをリリースしていなかったため、クーポンコードが無効であるというエラーメッセージが表示されていました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/c971859e>
* _ACP2E-2811_: [Cloud] カタログのインデックス再作成ルール製品インデクサーが SQLSTATE[HY000 をスローする ]：一般エラー：2006 MySQL サーバーが終了しました。
   * _修正メモ_：システムでは、「Magento\CatalogRule\Model\Indexer\IndexBuilder」の di.xml でカスタムの「batchCount」値を正しく処理するようになったので、大きなカタログのバッチサイズが正しくないことが原因で、カタログルール製品インデクサーのインデックス再作成中に「一般エラー：2006 MySQL サーバーが消失しました」などの SQL エラーが発生するのを防ぎます
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/b2286ecf>

### SEO

* _AC-11907_：アクセントを使用して URL の書き換えを追加すると、読み込みが無限になる
   * _メモの修正_：システムは、URL の書き換えをアクセントで正常に作成および機能するようになり、保存プロセス中に無限の読み込みを防ぎます。 以前は、アクセントを使用して URL の書き換えを追加すると、読み込み制限の問題が発生していました。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/38692>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/44cef3a9>
* _ACP2E-2641_：マルチストアで、第 3 レベルのカテゴリのカテゴリ URL の書き換えが間違っています
   * _メモの修正_：カスタムスコープの URL キーを持つ親を持つ子に対して、正しい URL の書き換えを生成します
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/ea79f7dd>
* _ACP2E-2770_：製品名フィールドの 2 バイト文字（特殊文字）が、バックエンドでの製品の作成をブロックする
   * _メモの修正_：製品 URL に表記変換を適用するかどうかを指定できる新しい設定が追加されました。 設定はこちらから利用できます：ストア/設定/カタログ/カタログ/検索エンジンの最適化：「製品 URL の表記変換を適用」
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/b2286ecf>

### セキュリティ

* _AC-11762_:
   * _修正注意_:BiC の変更後に、正しい説明とデフォルト値を使用して 2FA OTP ウィンドウフィールドを更新します
   * _GitHub コードの投稿_：今から otp_window 期間の入力方法を設定するために更新されたコマンド bin/magento config:set twofactorauth/google/otp_window VALUE
bin/magento config:set twofactorauth/google/leeway VALUE へ
* _AC-11855_:[ 問題 ] フォント CSP ペイロードのポップアップがない
   * _修正メモ_：システムは、コンテンツセキュリティポリシーディレクティブに違反せずにフォント「https://www.paypalobjects.com/webstatic/mktg/2014design/font/PP-Sans/PayPalSansBig-Medium.woff&#39;」を読み込むことができるようになり、Paylater ポップアップが正しく表示されるようになりました。 以前は、コンテンツセキュリティポリシーディレクティブの違反が原因でフォントの読み込みが拒否され、Paylater ポップアップの表示に問題が発生していました。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/38624>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/37401>
* _AC-11937_:
   * _修正注意_:BiC の変更後に、正しい説明とデフォルト値を使用して 2FA OTP ウィンドウフィールドを更新します
   * _GitHub コードの投稿_：今から otp_window 期間の入力方法を設定するために更新されたコマンド bin/magento config:set twofactorauth/google/otp_window VALUE
bin/magento config:set twofactorauth/google/leeway VALUE へ
* _AC-12309_:
   * _修正点_：二要素認証（2FA）のユーザードキュメントを更新し、otp_window コマンドを変更しました
   * _GitHub コードの投稿_:OTP_WINDOW 設定コマンドをhttps://jira.corp.adobe.com/browse/AC-11762に従って変更するために、2 要素認証（2FA）のユーザードキュメントを更新しました。

### 送料

* _AC-10757_:[ 問題 ] tracking.phtml の誤字を修正しました – JS 関数「currier」を「carrier」に名称変更しました
   * _修正点_：注文追跡テンプレートで使用されるJavaScript ハンドラー関数で、スペルミスのある「currier」ではなく「carrier」という用語が正しく使用されるようになりました。これにより、関数の適切な命名とコードの明確さが確保されます。 以前は、スペルミスのある「currier」という用語が使用されていたため、コードベースに混乱と不整合が生じる可能性がありました。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/34523>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/33414>
* _AC-11811_:
   * _修正点_:UPS REST 「出荷には、測定単位として KGS/IN、LBS/CM、または OZS/CM を含めることはできません」
   * _GitHub の問題_:&lt;<https://github.com/magento/magento2/commit/9b1713d8>>
   * _GitHub コードの投稿_:UPS の料金は、チェックアウトと買い物かごに表示されます。
* _AC-11916_:
   * _修正事項_:[QPT] UPS REST 「出荷には、測定単位として KGS/IN、LBS/CM、または OZS/CM を含めることはできません」
   * _GitHub コードの投稿_:UPS の料金は、チェックアウトと買い物かごに表示されます。
* _AC-11938_:UPS REST 「出荷単位として KGS/IN、LBS/CM、または OZS/CM を使用することはできません。」
   * _メモの修正_:UPS の料金がチェックアウトと買い物かごに表示されるようにします。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/38618>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/493e01f5>
* _AC-11983_:
   * _修正事項_:[QPT] UPS REST 「出荷には、測定単位として KGS/IN、LBS/CM、または OZS/CM を含めることはできません」
   * _GitHub コードの投稿_:UPS の料金は、チェックアウトと買い物かごに表示されます。
* _AC-11984_:
   * _修正事項_:[QPT] UPS REST 「出荷には、測定単位として KGS/IN、LBS/CM、または OZS/CM を含めることはできません」
   * _GitHub コードの投稿_:UPS の料金は、チェックアウトと買い物かごに表示されます。
* _ACP2E-2738_：トラッキングウィンドウに間違った配信予定日が表示される
   * _修正点_:Fedex 通信事業者の正しい配送日を表示します。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-2763_：送料無料が適用されていても、テーブルの料金が引き続き表示される
   * _修正注意_：表クーポン適用後に送料無料が利用可能になった場合でも、送料方法が表示されるようになりました
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-2765_: MFTF テスト AdminCreatingShippingLabelTest は、資格情報が Jenkins 環境に追加されていないので失敗します
   * _修正点_: mftf テスト修正
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/ea79f7dd>

### ターゲティング

* _AC-9432_: [ 問題 ] メンテナンス許可リストで CIDR 範囲を使用できるようにします
   * _修正点_：システムでは、メンテナンスモード許可 IP リストでの CIDR 範囲の使用がサポートされるようになり、メンテナンスモードをバイパスする IP アドレスの範囲が有効になりました。 以前は、メンテナンスモードでは、IP リストは個々の IP アドレスにのみメンテナンスモードのバイパスを許可していました。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/37943>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/30699>

### テストフレームワーク

* _AC-11491_:
   * _修正メモ_:[ スキップ ] もう一度スキップを解除する必要があります統合テスト
   * _GitHub の問題_:&lt;<https://github.com/magento/magento2/commit/493e01f5>>
   * _GitHub コードの投稿_：この PR でスキップされたすべての統合テストをスキップ解除 – https://github.com/magento-commerce/magento2ce/pull/8811/
* _AC-11654_:JSON 列タイプが原因で統合テストが testDbSchemaUpToDate に失敗する
   * _メモの修正_：統合テスト中に、システムはデータベーススキーマの JSON 列タイプを正しく認識するようになり、データベーススキーマと宣言型スキーマの不一致によるテストの失敗を防ぎます。 以前は、システムが MariaDB で JSON 列のタイプを LONGTEXT と誤って識別したので、統合テストが失敗していました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/ef81f5a2>

### UI フレームワーク

* _AC-12128_:Prototype.js のセキュリティ脆弱性修正 CVE-2020-27511
   * _修正点_:Prototype.js 1.7.3 のセキュリティ脆弱性 CVE-2020-27511 に対応するようにシステムを更新し、システム全体のセキュリティを強化しました。 このアップデート以前は、細工されたHTMLタグを削除することで、Regular Expression Denial of Service （ReDOS）の影響を受けやすくなっていました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/de4dfb8e>
* _AC-12128_:
   * _Fix note_:Prototype.js のセキュリティ脆弱性の修正 CVE-2020-27511
   * _GitHub の問題_:&lt;<https://github.com/magento/magento2/commit/de4dfb8e>>
   * _GitHub コード投稿_:Prototype.js 1.7.3 のセキュリティ脆弱性 CVE-2020-27511 に対応し、システム全体のセキュリティを強化しました。 このアップデート以前は、細工されたHTMLタグを削除することで、Regular Expression Denial of Service （ReDOS）の影響を受けやすくなっていました。
* _AC-12189_: Grunt Less がソース マップに pub/ プレフィックスを使用する
   * _修正メモ_：システムは、grunt を使用する際に、パスの/pub プレフィックスを付けずに less/css ソースマップを生成するようになりました。これにより、web サーバー設定で回避策を実行する必要がなくなります。 以前は、sourcemaps パスで/pub プレフィックスを使用するには、web サーバーが正しく機能するように特定の設定が必要でした。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/38837>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/38840>
* _AC-1306_：無効なモジュールに静的コンテンツがデプロイされています
   * _修正メモ_：無効なモジュールに関連する CSS が最終的な CSS 出力ファイルから除外されるようになり、不要なスタイルが読み込まれなくなります。 以前は、無効になっているモジュールに関連する CSS が最終的な CSS 出力ファイルに含まれていたため、不要なスタイルが追加で読み込まれていました。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/24666>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/32922>
* _AC-9007_:[ 問題 ] フロントエンドでバックエンドブロックコンテキストを読み込まない
   * _メモの修正_：システムでは、バックエンドのブロックコンテキストがフロントエンドに読み込まれないようにし、不要なバックエンドセッションの作成や、セッションのロックの可能性を防ぐようになりました。 以前は、システムがフロントエンドでバックエンドブロックコンテキストを誤って読み込んでいたため、バックエンドセッションが作成され、セッションロックが発生する可能性がありました。
   * _GitHub の問題_:<https://github.com/magento/magento2/issues/37617>
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/pull/36368>
* _ACP2E-2529_:Recaptcha が有効な場合に、ギフトカードの残高を確認する際の例外
   * _メモの修正_：ユーザーは、表示およびカート編集画面でギフトカードの残高を取得できます。 以前は、これらの詳細は、reCAPTCHA が有効な場合は表示されませんでした。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2-page-builder/commit/4a2795ea>
* _ACP2E-2729_: [ 説明 ] 機能リクエストの ADA コンプライアンス
   * _修正点_：システムは、サポートされていない CSS プロパティを削除し、print.css ファイル内のサポートされているプロパティに置き換えることで、ADA への準拠を確保するようになりました。 以前は、サポートされていない CSS プロパティを使用すると、ブラウザーの互換性の問題が発生していました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-3061_:[Cloud] AC 2.4.4-p8 の effect-drop.js の混乱ライブラリコード
   * _メモを修正_：システムで effect-drop.js ライブラリが正しく実装され、jQuery UI エフェクトが適切に機能するようになりました。 以前は、effect-drop.js ライブラリが effect-clip.js ライブラリで誤って上書きされ、jQuery UI エフェクトで潜在的な問題が発生していました。
   * _GitHub コードの投稿_:<https://github.com/magento/magento2/commit/35b1b1da>
