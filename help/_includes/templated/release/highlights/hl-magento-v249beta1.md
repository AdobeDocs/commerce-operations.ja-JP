---
source-git-commit: 65a9bd667d434f1deae69798696f66998e6024a0
workflow-type: tm+mt
source-wordcount: '952'
ht-degree: 0%

---
# Magento Open Sourceのハイライト（v2.4.9-beta1）

## v2.4.9-beta1 のハイライト

Magento Open Source 2.4.9-beta1 リリースには次のハイライトが適用されます。

### API

#### ストア表示レベルで製品を更新する際に、REST API で製品ギャラリーの継承を保持できる機能を追加しました。

ストアスコープで REST API を使用して製品を更新しても、media_gallery_entries がペイロードから省略された場合や、NULL に設定されて、そのスコープで製品ギャラリーが変更されない場合、製品の画像やビデオがグローバルスコープからの変更を継承しなくなりました。 さらに、対応するフィールドを NULL に設定することで、REST API を介して製品画像およびビデオのスコープ継承を復元できるようになりました

_ACP2E-4358 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/f7bbcb4e)_

### フレームワーク

#### web-token/jwt-framework の最新のメジャーバージョンを調査します。

継続的なセキュリティレビュープロセスの一環として、将来の互換性を確保し、強力なセキュリティ標準を維持するために、JWT フレームワークの最新のメジャーリリースを評価しました。 このリリースの既存の機能への影響はありません。

_AC-13209 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/2bac8114) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/09b36ebb) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/33b81f28)_

#### carlos-mg89/oauth を PHP のネイティブ関数に置き換える

サードパーティの carlos-mg89/oauth ライブラリをネイティブの PHP OAuth 関数に置き換え、セキュリティを向上させ、外部依存を減らし、プラットフォームの安定性を高めました。

_AC-14075 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/7b8064f7)_

#### 最新バージョンの chart.js を調査

Chart.js JavaScriptのチャートライブラリを最新バージョン 4.4.8 にアップグレードして、グラフのレンダリングパフォーマンスの向上、表示機能の強化、管理ダッシュボードとレポートモジュールのセキュリティの脆弱性への対処をおこないました。

_AC-14304 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/768b4442)_

#### 最新バージョンの jquery/uppy および uppy を調査します。

Uppy ファイルアップロードライブラリをバージョン 4.13.4 にアップグレードして、ファイルアップロード機能を強化し、ユーザーエクスペリエンスを向上し、Adobe Commerce管理インターフェイスとフロントエンドコンポーネント全体でのファイル処理のセキュリティの脆弱性に対処しました。

_AC-14307 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/eb491c05)_

#### 最新バージョンの調査 jquery-validate

jQuery 検証ライブラリをバージョン 1.21.0 にアップグレードして、フォームの検証機能を強化し、ユーザーエクスペリエンスを向上し、管理インターフェイスとフロントエンドインターフェイスの両方ですべてのAdobe Commerce フォームに最新のブラウザー互換性を確保しました。

_AC-14403 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/98b2848a)_

#### 最新バージョンの jquery-ui を調査する

jQuery UI ライブラリをバージョン 1.14.1 にアップグレードして、ユーザーインターフェイスウィジェットを強化し、アクセシビリティを向上し、すべてのAdobe Commerce管理コンポーネントとフロントエンドインターフェイスコンポーネントで最新のブラウザー互換性を確保しました。

_AC-14417 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/77c589a6)_

#### 最新バージョン less.js を調査します。

Less.js CSS プリプロセッサーをバージョン 4.2.2 にアップグレードして、CSS コンパイルのパフォーマンスを高め、構文のサポートを強化し、すべてのAdobe Commerce フロントエンドおよび管理テーマにわたってテーマのビルドプロセスを最新化しました。

_AC-14418 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/98b2848a)_

#### 最新バージョン moment-timezone-with-data.js を調査します。

Moment Timezone ライブラリをバージョン 0.5.43 にアップグレードして、タイムゾーン処理機能を強化し、最新の IANA タイムゾーンデータベース変更でタイムゾーンデータを更新し、Adobe Commerceの国際およびマルチタイムゾーン操作すべてで日付/時刻の処理の精度を高めました。

_AC-14419 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/98b2848a)_

#### 最新バージョンの underscore.js の調査

Underscore.js ユーティリティライブラリをバージョン 1.13.7 にアップグレードして、JavaScriptの機能プログラミング機能を強化し、データ操作のパフォーマンスを向上し、Adobe Commerceのすべてのフロントエンドコンポーネントと管理インターフェイスコンポーネントにおける最新のブラウザー互換性を確保しました。

_AC-14420 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/98b2848a)_

#### 2.4.9-alpha1 で allure-framework/allure-phpunit バージョンを 3 にアップデートし、ネイティブの依存関係を削除。

Adobe Commerce 2.4.9 では、allure-framework/allure-phpunit 依存性がメジャーバージョン 3 にアップグレードされました。これにより、PHP 8.4、PHP 8.5 がサポートされ、Allure ベースのテストレポートスタックが最新化されました。 以前のバージョンの Allure PHPUnit で以前に必要だったネイティブの依存関係は、該当する場合は削除され、セットアップとメンテナンスが簡素化されました。

_AC-14548 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/87b8b34e)_

#### chart.js の依存関係を最新バージョンにアップグレード

chart.js 依存関係が最新バージョン 4.5.0 にアップグレードされます

_AC-15133 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/657f983e)_

#### Adobe Commerce 2.4.9 で Symfony 7.4 LTS と PHP 8.5 の公式サポートを追加

Adobe Commerce 2.4.9 プラットフォームのアップデートの一環として、magento/composer パッケージで使用されるすべての Symfony 依存関係が、最新の Symfony LTS 7.4 バージョンに更新されました。 これにより、Commerceの Composer ツールが現在の Symfony LTS 行に合わせて配置され、古い Symfony バージョンに関連する以前の依存関係の制約が削除されます。 さらに、Symfony コアクラスを拡張するすべてのカスタムクラスでは、Adobe Commerce 2.4.9 にアップグレードする前に、最新の Symfony 要件に合わせて型宣言とメソッド署名を更新しています。これにより、互換性の問題が回避され、更新されたフレームワークコンポーネントにスムーズに移行できます。

_AC-15170 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/c127d10b)_

### その他

#### Captcha/reCaptha が API/GraphQl に対して機能しない

Adobe Commerce 2.4.9 で、「アカウントを作成」フォームに対して CAPTCHA （または reCAPTCHA）が有効になっている場合、REST およびGraphQL API を使用したカスタマーアカウントの作成に対して、同じ CAPTCHA 検証が適用されるようになりました。

_AC-16245 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/fd7f30ee)_

### セキュリティ

#### 非同期/一括要求のパフォーマンスの向上

APSB25-08 セキュリティパッチの後に導入された一括非同期 web エンドポイントのパフォーマンス低下を修正し、実行時間を増やしました。

_AC-14078 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/9a7352b7)_

#### ユーザーごとに有効な 2FA プロバイダーを 1 つだけ設定する必要があります

管理者ユーザーは、管理パネルにアクセスするために、マーチャントで有効な 2FA プロバイダー（Google Authenticator や U2F など）の 1 つのみを設定する必要があります。 必要に応じて、有効なプロバイダーを後で設定できます。 以前は、複数の 2FA プロバイダーが有効になっている場合（例：Google Authenticator と U2F）、すべての管理者ユーザーは、ログインする前に、有効なすべてのプロバイダーを設定する必要がありました。 これにより、すべての要因（U2F のハードウェアキーなど）にアクセスできなかったユーザーにとって摩擦が生じました。

_AC-8253 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/security-package/commit/71e7936b)_

### ステージングとプレビュー

#### [ 機能リクエスト ] モバイル表示でのコンテンツステージングプレビュー

管理パネルのステージングプレビュー機能を使用すると、ブラウザーシミュレーションしたモバイルデバイスプレビューを正確にレンダリングして、モバイルデバイスでステージングの更新がどのように表示されるかを視覚的に表現できるようになりました。

_ACP2E-3397 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/520f9e30)_
