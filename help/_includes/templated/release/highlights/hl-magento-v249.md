---
source-git-commit: 3a341190ff7ab69ad49721f78dfc90bc9ef24b20
workflow-type: tm+mt
source-wordcount: '2138'
ht-degree: 0%

---
# Magento Open Sourceのハイライト（v2.4.9）

## v2.4.9のハイライト

Magento Open Source 2.4.9 リリースには、次のハイライトが適用されます。

### API

#### ストアビューレベルで製品を更新する際に、REST APIで製品ギャラリーの継承を維持する可能性を追加

ストアスコープ内のREST APIを介して製品を更新すると、media_gallery_entriesがペイロードから省略されるか、そのスコープ内の製品ギャラリーの変更を防ぐためにNULLに設定されている場合に、製品の画像やビデオがグローバルスコープからの変更を継承しなくなります。 さらに、対応するフィールドをNULLに設定することで、REST APIを介して製品画像とビデオのスコープ継承を復元できるようになりました。

_ACP2E-4358 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/f7bbcb4e)_

### Braintree

#### アカウントエリアを介したGoogle Payの保管

Adobe Commerce 2.4.9では、BraintreeでGoogle Pay Vaultが有効になっている場合、お客様はアカウントエリアを介してGoogle Pay カードを保管できるようになりました。 保管されている支払い方法の下に保管されているカードが表示され、チェックアウト時に今後の購入に使用でき、お客様が削除できます。 これは、クレジットカードやPayPalにとどまらないサポートを、Google Payにも拡大します。

_バンドル–3459_

#### リアルタイムアカウントアップデータ（RTAU）

Adobe Commerce 2.4.9 for BraintreeのReal Time Account Updater （RTAU）機能により、Vault済みのVisa、Mastercard、Discoverのカード詳細は、カードの有効期限が切れるか交換されたときに自動的に更新されます。 これにより、支払い失敗を最小限に抑え、Magento Vaultを最新の状態に保ち、サポートされていない種類（前払い、Apple Pay、Google Pay）をエラーなくスキップできます。

_バンドル–3462_

#### BRAINTREE カード支払いにおけるELO カードの種類のサポート

Adobe Commerce 2.4.9では、Braintree支払いにELO カードタイプのサポートが追加されました。 管理者は、クレジットカードの設定でELOを有効にできるようになりました。お客様は、チェックアウト時にELO カードを使用して注文を正常に行うことができ、Braintreeを通じてシームレスなトランザクションを実現できます。

_バンドル–3464_

#### 請求時に支払う

Adobe Commerce 2.4.9 （Braintree拡張機能）では、ドイツのバイヤー向けに、新しい現地支払い方式「請求書に応じて支払う」が追加されました。 Pay Upon Invoiceは、PayPal + Ratepay （「Rechnungskauf mit Ratepay」）を搭載したBNPL （BUY NOW, Pay Later）オプションで、顧客がPayPal アカウントを必要とせずに商品を最初に受け取り、30日以内に請求書を支払うことができます。 即時支払いではないため、注文の最終処理はPayPalのサーバーサイドのWebhookによって行われます。

_バンドル–3475_

#### Google Pay Express支払いシートにオファーを追加する

Adobe Commerce 2.4.9のBraintree拡張機能で、Google Pay Express支払いシートでプロモ – ション/オファーコードがサポートされるようになりました。 顧客は、Googleの支払いシート内でMagentoのカート内プロモーションを直接適用、表示、削除できるため、Express チェックアウトの顧客は、標準的なチェックアウトフローと同じ割引やインセンティブを受け取ることができます。

_バンドル–3476_

#### Apple Pay Express支払いシートにオファーを追加する

Adobe Commerce 2.4.9のBraintree拡張機能で、Apple Pay Express支払いシートでプロモ – ション/オファーコードがサポートされるようになりました。 顧客はAppleの支払いシートで直接クーポンを適用できるため、Express Checkoutの利用者は、標準的なチェックアウトフローと同じ割引や施策の恩恵を受けることができます。

_バンドル–3477_

#### ChromeおよびFirefoxでのApple Payでのお支払い

Adobe Commerce 2.4.9のBraintree拡張機能では、Apple PayをSafariだけでなく、ChromeおよびFirefoxで使用できるようになりました。 Apple Pay Expressが有効になっている場合、Appleの支払いボタンは、サポートされているストアフロントの場所をまたいで利用でき、お客様はiPhoneでコードをスキャンして支払いを完了できます。

_バンドル–3478_

#### サーバーサイドの発送コールバック

Adobe Commerce 2.4.9のBraintree拡張機能では、PayPal Expressのシッピングコールバックがクライアントサイドからサーバーサイドに移動されました。 これにより、動的な配送方法、リアルタイムのコスト計算、正確なカートレベルの詳細をPayPal モーダルで直接提供し、信頼性を向上させ、Contact Module サポート、アプリスイッチフロー、Venmo Expressなどの将来の機能の基盤を築きます。

_バンドル–3479_

#### PayPal コンタクトモジュール

Adobe Commerce 2.4.9のBraintree拡張機能では、新しいPayPal Contact Moduleが米国のマーチャント向けに導入されました。 有効にすると、PayPal Expressを使用している購入者は、Express フロー（PDP、ミニカート、カート、チェックアウトエクスプレス）中に、PayPal モーダル内で直接加盟店と共有されたメールアドレスと電話番号を表示して更新できます。 選択した連絡先の詳細は、Adobe Commerce注文に保存されます。

_バンドル–3480_

#### BLIK （Local Payment Method）

Adobe Commerce 2.4.9のBraintree拡張機能では、ポーランド人買い物客に新しいローカル支払い方法としてBLIKが追加されました。 これにより、既存のBraintree Local Payment Methods （LPM）フロー内で安全な銀行ベースのBLIK支払いが可能になり、ポーランドのお客様のチェックアウトの利便性とコンバージョン率が向上します。

_バンドル–3481_

#### カーディナル統合更新CSP ポリシー

Adobe Commerce 2.4.9のBraintree拡張機能では、最新のカーディナル（3-D セキュア）統合要件をサポートするように、コンテンツセキュリティポリシー（CSP）が更新されました。 これにより、3D セキュアフロー中に使用されるすべてのカーディナルホストのスクリプト、iframe、および関連リソースがブラウザーのCSPによって許可され、ブロックされたリクエストや失敗したチャレンジ/検証エクスペリエンスが防がれます。

_バンドル–3485_

### フレームワーク

#### web-token/jwt-framework ライブラリを最新のメジャーバージョンにアップグレードしました

継続的なセキュリティレビュープロセスの一環として、JWT フレームワークの最新のメジャーリリースを評価し、将来の互換性を確保し、強固なセキュリティ標準を維持します。 このリリースの既存の機能に影響はありません。

_AC-13209 - [GitHub コード投稿](https://github.com/magento/magento2/commit/2bac8114) - [GitHub コード投稿](https://github.com/magento/magento2/commit/09b36ebb) - [GitHub コード投稿](https://github.com/magento/magento2/commit/33b81f28)_

#### [ パート 2] – すべてのjs ライブラリとnpm依存関係を、使用可能な最新バージョンに更新します

コンポーザーのバージョンのサポートは、コンポーザーのバージョン 2.2.xまででした。 サポートが2.4.x バージョンにも拡張されました。

_AC-13792 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/19844aa0)_

#### carlos-mg89/oauthをPHP ネイティブ関数に置き換える

サードパーティのcarlos-mg89/oauth ライブラリをネイティブ PHP OAuth関数に置き換えて、セキュリティの向上、外部依存関係の軽減、プラットフォームの安定性の向上を実現しました。

_AC-14075 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/7b8064f7)_

#### jquery/uppyおよびuppy ライブラリを最新バージョンにアップグレードする

Uppy file upload libraryをバージョン 4.13.4にアップグレードし、ファイルのアップロード機能を強化し、ユーザーエクスペリエンスを向上させ、Adobe Commerceの管理インターフェイスとフロントエンドコンポーネント全体でファイル処理のセキュリティ上の脆弱性に対処しました。

_AC-14307 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/eb491c05)_

#### jquery-validate ライブラリを最新バージョンにアップグレードします

jQuery Validate ライブラリをバージョン 1.21.0にアップグレードして、フォーム検証機能を強化し、ユーザーエクスペリエンスを向上させ、管理者インターフェイスとフロントエンドインターフェイスの両方で、すべてのAdobe Commerce フォームで最新のブラウザーの互換性を確保しました。

_AC-14403 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/98b2848a)_

#### jquery-ui ライブラリを最新バージョンにアップグレードする

jQuery UI ライブラリをバージョン 1.14.1にアップグレードし、ユーザーインターフェイスウィジェットを強化して、アクセシビリティを向上させ、すべてのAdobe Commerce管理者およびフロントエンドインターフェイスコンポーネントで最新のブラウザーの互換性を確保しました。

_AC-14417 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/77c589a6)_

#### less.js ライブラリを最新バージョンにアップグレードする

Less.js CSS プリプロセッサをバージョン 4.2.2にアップグレードして、CSS コンパイルのパフォーマンスを向上させ、構文サポートを改善し、すべてのAdobe Commerce フロントエンドと管理テーマでテーマのビルド プロセスを最新化しました。

_AC-14418 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/98b2848a)_

#### moment-timezone-with-data.js ライブラリを最新バージョンにアップグレードする

Moment Timezone ライブラリをバージョン 0.5.43にアップグレードして、タイムゾーン処理機能を強化し、最新のIANA タイムゾーンデータベースの変更でタイムゾーンデータを更新し、Adobe Commerceの国際業務とマルチタイムゾーンオペレーション全体で日付/時刻処理の精度を向上させました。

_AC-14419 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/98b2848a)_

#### underscore.js ライブラリを最新バージョンにアップグレードする

Underscore.js ユーティリティライブラリをバージョン 1.13.7にアップグレードして、JavaScriptの機能プログラミング機能を強化し、データ操作のパフォーマンスを向上させ、すべてのAdobe Commerce フロントエンドおよび管理インターフェイスコンポーネントで最新のブラウザーの互換性を確保しました。

_AC-14420 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/98b2848a)_

#### allure-framework/allure-phpunit バージョンを3に更新し、2.4.9-alpha1のネイティブ依存関係を削除します。

Adobe Commerce 2.4.9では、allure-framework/allure-phpunit依存関係がメジャーバージョン 3にアップグレードされ、PHP 8.4、PHP 8.5のサポートが追加され、Allure ベースのテストレポートスタックが最新化されました。 古いバージョンのAllure PHPUnitで以前に必要だったネイティブ依存関係は、該当する場合は削除され、設定とメンテナンスが簡素化されました。

_AC-14548 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/87b8b34e)_

#### chart.js依存関係を最新バージョンにアップグレードする

chart.js依存関係が最新バージョン 4.5.0にアップグレードされます。

_AC-15133 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/657f983e)_

#### Adobe Commerce 2.4.9でSymfony 7.4 LTSおよびPHP 8.5の公式サポートを追加

Adobe Commerce 2.4.9 プラットフォームのアップデートの一環として、magento/composer パッケージで使用されるすべてのSymfonyの依存関係が最新のSymfony LTS 7.4にアップデートされました。 これにより、Commerce Composer ツールが現在のSymfony LTS ラインに合わせて調整され、古いSymfony バージョンに関連する以前の依存関係の制約が削除されます。 さらに、Symfony コアクラスを拡張するすべてのカスタムクラスでは、Adobe Commerce 2.4.9にアップグレードする前に、最新のSymfony要件に合わせて型宣言とメソッド署名が更新されています。 これにより、互換性の問題を回避し、更新されたフレームワークコンポーネントへのスムーズな移行を実現できます。

_AC-15170 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/c127d10b)_

### GraphQL

#### ClearCart GraphQLの変異がOpen Sourceで使用可能であることを確認します

Adobe Commerce 2.4.9では、clearCart GraphQLの突然変異がすべてのOpen Source ユーザーで使用できるようになりました。 以前は、この変異はAdobe Commerceでのみアクセスできましたが、現在ではOpen Sourceの標準のGraphQL カート機能の一部になっています。
バージョン 2.4.9のOpen Sourceで利用できるようになったことを反映して、ミューテーションのドキュメントが更新されました。
[clearCart GraphQLの変異関連ドキュメント &#x200B;](https://developer.adobe.com/commerce/webapi/graphql/schema/cart/mutations/clear-cart/)を参照してください。

_AC-16683 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/4449d914)_

#### [AC-2.4.9]管理者設定を使用したゲストと顧客カートのロジックの結合

新しい管理者設定オプションが導入され、買い物客がログインしたときにゲストカートと顧客カートを結合する方法を制御できるようになりました。 この機能強化により、ビジネスニーズに最も適したカートの結合動作を柔軟に定義できます。

_LYNX-889_

#### [AC-2.4.9]在庫切れの製品で過去の注文を取得する

過去の注文で在庫切れになった場合でも、商品の詳細が表示されるようになりました。

_LYNX-913_

#### [AC-2.4.9] [CE]見つからないGraphQLの突然変異に対してReCaptchaを実装する

ReCaptcha検証は、updateCustomer、updateCustomerV2、およびcontactUsの突然変異に追加されます。

_LYNX-941_

### その他

#### Captcha / reCAPTCHAがAPI / GraphQLで機能しない

Adobe Commerce 2.4.9では、アカウント作成フォームでCAPTCHA （またはreCAPTCHA）が有効になっている場合、REST APIとGraphQL APIを介したお客様のアカウント作成に対して、同じCAPTCHA検証が適用されるようになりました。

_AC-16245 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/fd7f30ee)_

#### braintree ブランチは、PHP 8.5をサポートして更新する必要があります

Braintree支払い拡張機能が更新され、PHP 8.4との互換性を維持しながら、最新のPHP 8.5 ランタイムをサポートするようになりました。

_バンドル–3493_

#### ウィッシュリストのクリア操作の追加

一括操作をサポートする新しいclearWishlist突然変異を追加し、1回のアクションであらゆるアイテムをウィッシュリストから削除できるようにしました。

_LYNX-790_

#### exchangeExternalCustomerTokenの突然変異の導入

統合トークンを介してユーザーを認証し、顧客トークンと関連する顧客データの両方を返す新しいGraphQL mutation exchangeExternalCustomerTokenが導入されました

_LYNX-815_

#### [AC]適用されたグループ、セグメント、および買い物かごルール IDを返すGraphQL クエリの紹介

適用された顧客グループ、顧客セグメント、カートルールのエンコードされたuidを取得するために公開されたGraphQL クエリ。

_LYNX-867_

#### [AC-2.4.9] OrderTotal.grand_total_excl_tax フィールドを紹介します

新しいフィールド OrderTotal.grand_total_excl_taxがGraphQLの注文応答に追加されました。 このフィールドは、注文の税抜き総計を提供し、APIから直接、税抜き総計にアクセスしやすくします。

利点：

- GraphQLを使用して、任意の注文の税抜き総計を簡単に取得できます。
- 税別の合計を必要とする外部システムとの統合を簡略化します。
- クライアントサイドのカスタム計算の必要性を低減。

_LYNX-892_

### PCI、セキュリティ

#### SRI ストレージをよりパフォーマンス効率の高いものにリファクタリング

SRI ハッシュストレージは、1つの大きなsri-hash.jsonではなく、領域、テーマ、ロケールごとに個別のファイルを生成するようになりました。 この変更により、各ページに関連するハッシュファイルのみが読み込まれるようになり、パフォーマンスが向上し、複数のテーマまたはロケールを持つストアでのメモリ使用量が削減されます。

_AC-16113 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/bc83cd2c)_

### セキュリティ

#### 非同期/一括リクエストのパフォーマンスを向上

APSB25-08 セキュリティパッチ後に導入された一括非同期web エンドポイントのパフォーマンス低下を修正し、実行時間を増やしました。

_AC-14078 - [GitHub コードの貢献度](https://github.com/magento/magento2/commit/9a7352b7)_

#### 1人のユーザーにつき1つの有効な2FA プロバイダーのみを設定する必要があります

管理者ユーザーは、管理者パネルにアクセスするために、マーチャントが有効にしている2FA プロバイダー（Google AuthenticatorやU2Fなど）のうち1つだけを設定する必要があります。 追加の有効なプロバイダーは、必要に応じて後で設定できます。 以前は、複数の2FA プロバイダー（Google AuthenticatorやU2Fなど）が有効になっている場合、すべての管理者ユーザーは、ログインする前にすべての有効なプロバイダーを設定する必要がありました。 これにより、すべての要素（U2Fのハードウェアキーなど）にアクセスできなかったユーザーは摩擦を生み出しました。

_AC-8253 - [GitHub コードの貢献度](https://github.com/magento/security-package/commit/71e7936b)_
