---
source-git-commit: bfad68a46b9b1a79a702f04efd39129decda1a1c
workflow-type: tm+mt
source-wordcount: '647'
ht-degree: 0%

---
# Magento Open Source リリースノート（v2.4.9-alpha2）

## v2.4.9-alpha2 のハイライト

Magento Open Source 2.4.9-alpha2 リリースには、次のハイライトが適用されます。

### フレームワーク

#### OpenSearch 3 のサポートを追加

Adobe Commerce 2.4.9 は、OpenSearch 3.x と完全に互換性を持つようになりました。この更新により、マーチャントは、OpenSearch 2.x との下位互換性を維持しながら、パフォーマンスの向上、セキュリティ、長期的なサポートのメリットを得ることができます。

_AC-11846_

#### Nginx のバージョンを 1.26 から 1.28 にアップデートします

現在サポートされているすべてのバージョンのAdobe Commerceの開発およびテスト環境で使用される Nginx のバージョンは、入手可能な最新の安定した Nginx リリースに合わせて 1.26 から 1.28 に更新されました。
PR レベルのテストが Nginx 1.28 で実行され、すべてのAdobe Commerce バージョンの完全な互換性とサポートが確認されるようになりました。

_AC-14104_

#### 最新バージョンの調査 jquery-validate

jQuery 検証ライブラリをバージョン 1.21.0 にアップグレードして、フォームの検証機能を強化し、ユーザーエクスペリエンスを向上し、管理インターフェイスとフロントエンドインターフェイスの両方ですべてのAdobe Commerce フォームに最新のブラウザー互換性を確保しました。

_AC-14403 - [GitHub コードの投稿 ](https://github.com/magento/magento2/commit/98b2848a)_

#### 最新バージョンの jquery-ui を調査する

jQuery UI ライブラリをバージョン 1.14.1 にアップグレードして、ユーザーインターフェイスウィジェットを強化し、アクセシビリティを向上し、すべてのAdobe Commerce管理コンポーネントとフロントエンドインターフェイスコンポーネントで最新のブラウザー互換性を確保しました。

_AC-14417 - [GitHub コードの投稿 ](https://github.com/magento/magento2/commit/77c589a6)_

#### 最新バージョン less.js を調査します。

Less.js CSS プリプロセッサーをバージョン 4.2.2 にアップグレードして、CSS コンパイルのパフォーマンスを高め、構文のサポートを強化し、すべてのAdobe Commerce フロントエンドおよび管理テーマにわたってテーマのビルドプロセスを最新化しました。

_AC-14418 - [GitHub コードの投稿 ](https://github.com/magento/magento2/commit/98b2848a)_

#### 最新バージョン moment-timezone-with-data.js を調査します。

Moment Timezone ライブラリをバージョン 0.5.43 にアップグレードして、タイムゾーン処理機能を強化し、最新の IANA タイムゾーンデータベース変更でタイムゾーンデータを更新し、Adobe Commerceの国際およびマルチタイムゾーン操作すべてで日付/時刻の処理の精度を高めました。

_AC-14419 - [GitHub コードの投稿 ](https://github.com/magento/magento2/commit/98b2848a)_

#### 最新バージョンの underscore.js の調査

Underscore.js ユーティリティライブラリをバージョン 1.13.7 にアップグレードして、JavaScriptの機能プログラミング機能を強化し、データ操作のパフォーマンスを向上し、Adobe Commerceのすべてのフロントエンドコンポーネントと管理インターフェイスコンポーネントにおける最新のブラウザー互換性を確保しました。

_AC-14420 - [GitHub コードの投稿 ](https://github.com/magento/magento2/commit/98b2848a)_

#### TinyMCE からHugerte.orgへの移行

TinyMCE 5 および 6 のサポート終了と TinyMCE 7 とのライセンス非互換性により、現在のAdobe Commerce WYSIWYG エディターの実装は、TinyMCE からオープンソースの HugeRTE エディター（https://hugerte.org/）に移行されます。
この移行により、Adobe Commerceはオープンソースのライセンスに引き続き準拠し、既知の TinyMCE 6 の脆弱性を回避し、マーチャントやデベロッパー向けに最新のサポートされている編集機能を提供します。

_AC-14568_

#### 2.4.9-alpha2 に Valkey 8.x の完全なサポートを追加

Adobe Commerce 2.4.9 では、Valkey に対して完全な CLI コマンドがサポートされており、現在の既存の Redis 機能をミラーリングします。 管理者とクラウドの設定が更新され、シームレスな Valkey 設定が可能になりました。
この更新により、Adobe Commerceは Valkey 8.x をサポートすることで、将来にわたって利用でき、パフォーマンスが向上します。これにより、マーチャントやデベロッパーは Redis に代わる信頼性の高い製品を入手できます。

_AC-14604_

### その他

#### CNS のビルドおよびテスト用のAWS Valkey 8.x サービスのアップデート

CNS ビルド用のAWS Valkey 8.x サービスの更新

_AC-14470_

#### 2.4.9-alpha2 - 8 月のコア品質の改善

_AC-14700_

### セキュリティ

#### 2.4.9-alpha2 のセキュリティの改善

_AC-14610_

### 送料

#### 古い Web ツール API から新しい RESTful USPS API への USPS 統合の移行

USPS が 2026 年 1 月 25 日（PT）までに従来の Web Tools API の廃止を発表したことに準拠するために、Adobe Commerce USPS 統合は、新しい RESTful USPS API に移行されました。
主な機能強化：
- デュアル API のサポート：管理者ユーザーは、設定を使用して、従来の Web ツール API と新しい RESTful USPS API のどちらかを選択できるようになりました。
- 認証のアップグレード：安全な API アクセスを実現するために OAuth 2.0 を実装しました。
- データフォーマットの改善：よりクリーンで効率的な通信のために、XML から JSON に移行されました。
- 新しい管理フィールド：
ゲートウェイ REST URL （モード：開発またはライブに基づく）
クライアント ID と秘密鍵
勘定科目タイプ、勘定科目番号
CRID、MID、メーラー識別コード
国際出荷用の AES/ITN
REST 固有の許可されている発送方法
この移行により、Adobe Commerceが USPS 標準に引き続き準拠し、システムの信頼性が向上し、マーチャント向けの将来的な配達確認の出荷統合が実現します。

_AC-13257_
