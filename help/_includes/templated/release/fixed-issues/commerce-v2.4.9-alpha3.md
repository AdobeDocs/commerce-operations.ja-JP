---
source-git-commit: ae571a9e7ca1234644a3bc9beade447009c58a3d
workflow-type: tm+mt
source-wordcount: '6077'
ht-degree: 0%

---
# Adobe Commerceで修正された問題（v2.4.9-alpha3）

## v2.4.9-alpha3 の問題を修正しました

Adobe Commerce 2.4.9-alpha3 コアコードの 129 の問題を修正しました。 このリリースで修正された問題の一部を以下に示します。

### API

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

#### REST API エンドポイント export-stock-salable-qty が間違った項目を返す total_count

total_count が誤ってページサイズに制限されていた、在庫書き出し在庫販売可能数量 API のページネーションの問題を修正しました。 以前は、page_size=5 などのページネーションパラメーターを使用して/rest/all/V1/inventory/export-stock-salable-qty/website/base エンドポイントを使用する場合、応答内の total_count フィールドは、検索条件に一致する実際の製品総数ではなく 5 を返していました。 この修正後、total_count フィールドに、page_size パラメーターに関係なく使用可能な製品の合計数が正しく反映されるようになり、すべてのMagento REST API エンドポイントで一貫したページネーション動作が保証されます。

_ACP2E-4086 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/inventory/commit/5632fb5e)_

#### 買い物かご項目 REST API のカスタムオプション ID の検証の問題

REST API V1/guest-carts/&lt;cartId>/items/および V1/carts/mine/items/は、「product_options.extension_attributes.custom_options」を検証するようになりました。*.option_id」に設定し、買い物かごの商品 SKU の有効な option_id を参照するようにします。 以前は、このパラメーターは処理され、検証なしでデータベースに保存されていました。

_ACP2E-4138 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/a1c57b2e)_

### アカウント

#### [ 問題 ] バックエンドグリッドで不要な間隔を削除しました

選択された項目がある場合、バックエンドグリッドで不要な間隔が削除されるようになりました

_AC-11579 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/38502) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/32622)_

#### `updateProductsInWishlist` GraphQL mutation を使用してウィッシュリスト項目のコメントを消去できない

GraphQLのミューテーションを使用してウィッシュリストのコメントが更新されない問題を修正しました。
これで、コメントが正しく更新され、API 応答とストアフロントの両方に反映されるようになりました。

_AC-14682 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39911) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/36d4d6fb)_

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

#### magento 2.4.8-p1 でのログイン後の問題

Magento 2.4.8-p1 で、ログイン後もホームページに「アカウントを作成」リンクが表示される問題を修正しました。
現在は、他のページと一致するように、ログイン後にリンクは正しく非表示になっています。

_AC-15292 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/40120)_

### 管理 UI

#### [ 問題 ] 非推奨（廃止予定）のエスケープを置換

この PR は、非推奨の getEscaper （）を削除し、コンストラクターのインジェクションを使用して追加します

_AC-15132 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/40062) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/38135)_

#### モバイル表示で「ようこそ」メッセージが製品カテゴリに重なります。

モバイル表示で、ようこそ名が製品カテゴリと重なってクリックがブロックされる UI の問題を修正しました。
カテゴリが完全に表示され、クリックできるようになりましたが、重複の問題は発生していません。

_AC-15166 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/1b1baf1d)_

#### Google reCAPTCHA 管理パネルの exception.log の「Can not resolve reCAPTCHA parameter」エントリ

Google V3 reCAPTCHA Admin ログインの `var/log/exception.log` ファイルの reCAPTCHA エラーが解決され、エラーメッセージはログに記録されません。 以前は、管理者ユーザーが **Configuration** /{Security **/** 4}Google reCAPTCHA 管理パネル **を設定すると、数秒ごとに次のエラーがスローされていました。**  `main.ERROR: Can not resolve reCAPTCHA parameter. {&quot;exception&quot;:&quot;[object] (Magento\Framework\Exception\InputException(code: 0): Can not resolve reCAPTCHA parameter. at /home/xxxxxxx/public_html/vendor/magento/module-re-captcha-ui/Model/CaptchaResponseResolver.php:25)&quot;} []`[GitHub-34975](https://github.com/magento/magento2/issues/34975)

_AC-3179 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/34975) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/4f7e5983) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/security-package/commit/804dbc2a)_

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

_ACP2E-4052 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/52f46328)_

### 管理 UI、税

#### 税率管理 ui エラー

このチケットは、国を切り替えても（例：米国から英国→）、以前に選択した米国の州が引き続き表示され、ユーザーを誤解させる税率管理 UI の問題を修正しました。
2.4.9-alpha3 では、選択した国に州がない場合、州フィールドが*にリセットされるようになりました。

_AC-8440 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/a3b1abc2)_

### B2B

#### ログインした顧客に対して、REST API products-render-info が間違った最終価格を返す

チケットには、Rest API products-render-info の修正があります。ログインした顧客に対して、間違った最終価格を返します

_AC-5979 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/35757) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/)_

#### カテゴリページから追加しようとすると、「購買依頼リストに追加」ボタンが表示されなくなります

以前の「購買依頼リストに追加」ボタンは、現在修正されているカテゴリ・ページから追加しようとすると消え、カテゴリ・ページに購買依頼ボタンが表示されます。

_AC-8575_

### B2B、買い物かごとチェックアウト

#### 管理機能「顧客としてログイン」から B2B 会社ユーザーにログインすると、cartId = X エラーのエンティティがストアフロントに表示されません

「顧客としてログイン」機能を使用したときに管理者バックエンドから正常にログインすると、「cartId = X のエンティティがありません」エラーが表示されなくなりました。

_ACP2E-3994 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/2a1e1e55)_

### 買い物かごとチェックアウト

#### [ 問題 ] チェックアウト契約モデルに EventPrefix と EventObject を追加する

システムには、チェックアウト契約モデルの EventPrefix と EventObject が含まれるようになり、イベントをイベントの接頭辞でトリガーできるようになりました。 この機能強化により、開発者がチェックアウト契約イベントを扱う際の柔軟性が向上します。 以前は、チェックアウト契約モデルは EventPrefix と EventObject をサポートしていなかったので、イベント処理をカスタマイズする機能が制限されていました。

_AC-13252 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/32510) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/32451)_

#### [Graphql]nullable 以外のフィールド「SelectedCustomizableOption.label」で null を返すことができない

選択したオプションが存在しない場合、システムは内部サーバーエラーをスローせず、メッセージが表示されるようになりました

_AC-14256 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39729) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/39888)_

#### [2.4.8] 市区町村名に 0～9、アンパサンド、全角またはかっこの数字が含まれている場合、注文を行うことはできません

などの特殊文字を含む都市名のチェックアウトが失敗する問題を修正しました。、&amp;または括弧。
現在は、このような都市名を使用した注文は、検証エラーなしで正常に行われます。

_AC-14495 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39854) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/b9f5d6f7)_

#### 数量条件を使用した営業ルール副選択の適用に失敗

製品のサブ選択条件を含む買い物かご価格ルールがチェックアウト時に適用されない問題を修正しました。
これで、設定されたルールに従って、割引が正常に適用されます。

_AC-14884 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39965) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/fe72c407)_

#### Graphql - Backorder が有効な場合、結合カートが正しく機能しない

GraphQLを介した買い物かごの結合中に、ゲストの買い物かごの項目が顧客の買い物かごに結合されない問題を修正しました。
現在は、顧客の買い物かごには、ゲストと顧客の両方の買い物かごからの合計数量が正しく反映されています。

_AC-15148 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/40064) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/a3b1abc2)_

#### [ 統合 ] [ チェックアウト ] 失敗した支払いメールテンプレートで更新された依存ディレクティブ

depend ディレクティブを正しく処理するように更新された、失敗した支払 E メール テンプレート。
該当する場合は、配送先住所と配送方法が正しく表示されるように修正しました。
以前は、失敗した支払いメールにこれらのフィールドが見つかりませんでした。

_AC-15363 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/36d4d6fb)_

#### [ クラウド ] カートが要件を満たさなくなった場合、送料無料の割引が正しく削除されない

小計（除く カート価格ルールの（税金）に、前のルールからの割引が組み込まれるようになりました。

_ACP2E-3973 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/6dd3fa99)_

#### 複数出荷で同じ顧客の重複する注文が見つかりました

複数の配送先住所への注文を同時にリクエストしても、同じ顧客の注文が重複しなくなりました

_ACP2E-4117 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/a1c57b2e)_

### 買い物かごと、チェックアウト、注文、製品

#### 注文請求書が失敗した場合でもギフトカードの E メールが送信される

この修正を実装する前は、請求書が作成された後にギフトカードのメールが送信されていました。 ただし、修正が適用された後、請求書が正常に保存され、コミットされた後に、ギフトカードの E メールが送信されるようになりました。

_ACP2E-3905_

### 買い物かごと、チェックアウト、セキュリティ

#### [CLOUD] sri パッチを実装した後、最初の試みでチェックアウトページで JS ファイルの 404 を取得する

「修正」より前のバージョンでは、縮小とバンドルが有効な場合、Mixin は買い物かごおよびチェックアウトに読み込まれませんでした。 修正後、すべての Mixin が期待どおりに読み込まれます。

_ACP2E-4128 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/e457c5e2)_

### カタログ

#### 価格範囲と config.php の問題

Magento 2.4.2 では、config.php を使用して価格スコープを変更しても、catalog_eav_attribute の is_global 値が price 属性に適切に更新されません。
その結果、製品価格はグローバルに維持され、価格範囲が web サイトに設定されている場合でも、web サイトごとに保存することはできません。
この回避策では、データベースの is_global 列を手動で更新する必要があります。これは、実稼動環境には理想的ではありません。
この動作は、Magentoのデフォルトデザインと一致します。つまり、価格範囲はグローバルまたは web サイトですが、ストアビューごとではありません。

_AC-13857 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/33559)_

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

#### 動的な画像の生成により、多数の画像が生成される

修正後は、製品が割り当てられている web サイトの画像のみが生成されます。

_ACP2E-3927 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/fab20b00)_

#### レイアウト構造が正しくないため、フロントエンドで 500 エラーが発生し、レイアウトにキャッシュされる

間違ったレイアウト構造がレイアウトにキャッシュされているので、ページが 500 エラーコードを返す問題を修正しました

_ACP2E-4040 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/47721be6)_

#### 予定更新のカタログ価格ルール割引額フィールドの検証エラー

以前は、この問題を修正する前に、カタログ価格ルールのスケジュール更新で、割引額が by_fixed の場合、検証番号 – 範囲ルールが原因で適切に検証されませんでした。 この修正が適用されると、固定価格カタログ価格ルールに対して検証が正しく機能します。

_ACP2E-4054 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/6dd3fa99)_

#### 無効にすると、製品が在庫切れと表示されます

修正後、無効になった製品は製品ウィジェットに表示されなくなります。

_ACP2E-4136 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/a1c57b2e)_

#### [Cloud] エントリが重複したエラー（temp_category_descendants_%）

ネストされたカテゴリの数が多い環境のスケジュールされた更新を作成する際の重複エントリの問題を修正しました

_ACP2E-4159 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/a1c57b2e)_

### カタログ、GraphQL

#### GraphQl の無効な割引計算

カタログ価格に税が含まれるように設定されている場合、GraphQLで割引率と基本価格が正しく表示されるようになりました。 以前は、丸めエラーが発生していました（20% ではなく 19.99% が表示されるなど）。

_ACP2E-3993 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/e457c5e2)_

### カタログ、製品

#### GraphQLを介した PDP に関連製品ルールを介した関連製品が表示されない

以前は、この修正が適用される前に、相対的な製品ルールが、ルールに一致する製品に対して空または null を返していました。 この修正が適用されると、一致した製品に対して、製品の相対ルールが正常に返されます。

_ACP2E-3949_

### コンテンツ

#### graphql （magento 2.4.6-p4） – ステータスがアクティブでない cms ページを取得しようとするとエラーが発生する

無効なCMS ページのGraphQL クエリで内部サーバーエラーが返される問題を修正しました。
現在は、クエリはエラーなしで適切な応答を取得します。

_AC-12302 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/38877) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/1b1baf1d)_

#### [GraphQl] ルートクエリ無限ループ

このチケットでは、リクエストパスとターゲットパスが同じGraphQL ルートクエリによって無限ループが発生し、最終的にタイムアウトした問題を修正しました。
2.4.9-alpha3 では、クエリがループではなく正しいエラー応答を返すようになりました。

_AC-14269 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39707) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/68a45d0a)_

#### 柔軟性を高めるために、定数 IMAGE_FILE_NAME_PATTERN を public visible に変更します

GenerateRenditions.php の定数 IMAGE_FILE_NAME_PATTERN は、画像レンディションを扱う際に、開発者がより柔軟に操作できるように公開されました。この修正は、Magento 2.4.9-alpha3 に含まれており、単体テストおよび統合テストの適用範囲が完全です。

_AC-15338 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39733) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/68a45d0a)_

#### コンテンツのステージングプレビューが検索結果で機能しない

ステージングプレビューでの検索で、選択した範囲に従って製品を返すようになりました。 以前は、検索を実行すると、選択したストアに関わらず、デフォルトの範囲で結果が返されていました。

_ACP2E-4095_

#### ページビルダー – 製品状態ロジックの問題（または、ロジックが誤って表示される製品の数が少ない）

グローバルスコープを持つ属性が「任意の条件に一致」で使用された場合、ページビルダー製品ウィジェットが正しい結果を返すようになりました

_ACP2E-4096 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/e457c5e2)_

### 顧客/顧客

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

#### [ 問題 ] メソッドの署名をインターフェイスと一致させる

getAttributes のメソッドシグネチャがインターフェイスと一致するようになり、メソッドを上書きする際のエラーを防ぎます。 以前は、getAttributes メソッドを上書きしようとすると、メソッドのシグネチャの不一致によってエラーが発生していました。

_AC-11578 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/38501) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/31955)_

#### [ 問題 ]ui コンポーネントの validate-emails ルールを修正しました

システムは、UI コンポーネントに入力された複数のメールアドレスを正しく検証し、各メールが適切にトリミングおよび検証されていることを確認できるようになりました。 以前は、システムがメールアドレスのトリミングに誤った方法を使用しており、検証エラーが発生する可能性がありました。

_AC-11719 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/38528) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/33470)_

#### [ 問題 ] 冗長なメソッドを削除する

コード品質：機能を追加せずに親メソッドのみを呼び出す、AsynchronousOperations コンポーネントと Sales コンポーネントの冗長メソッドを削除し、コードの保守性を向上しました。

_AC-11915 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/29748) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/29147)_

#### フィールド項目の下にコメントが含まれているetc/adminhtml/system.xml ファイルで、xsd 検証が失敗します。

この PR により、コメントノード用 phpstorm の XML スキーマ定義が修正されます

_AC-12945 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39148) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/39867)_

#### Magento 2.4.8 では、セマンティックバージョニングに従わない開発パッケージを使用します

Magento 2.4.8 では、PHP 8.4 との互換性を保つため、pdepend/pdepend および phpmd/phpmd （3.x-dev）の開発版が必要です。
これらの開発バージョンは、SemVer 準拠パッケージを想定したサードパーティツールと競合し、一部のアップグレードを防ぎます。
一時的な回避策は、composer.json 内の開発バージョンのエイリアスを作成し（例：「3.x-dev as 3.99.0」）、セマンティックバージョニングを満たしながら互換性を確保することです。
これにより、PHP 8.4 のサポートが確保され、安定したリリースが利用可能になるまで競合が回避されます。

_AC-14519 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39796)_

#### Rest API:null でのメンバー関数 getVideoProvider （）の呼び出し

子製品にYouTube ビデオのみが含まれ、他の画像が含まれていない場合に、設定可能な製品の子 API を呼び出すと、500 内部サーバーエラーが返される問題を修正しました。
ExternalVideoEntryConverter の null 参照が原因でエラーが発生しました。
現在は、API は、外部ビデオデータを含むメディアギャラリーエントリを持つ子製品を、エラーを発生させずに正しく返します。
これにより、REST API を使用して、子製品のすべてのメディアタイプが適切に取得されます。

_AC-15046 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/40021)_

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

#### 更新モジュールの Readmes および修正ドキュメントのリンク

_AC-15340 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/ec9459d0)_

#### [ 問題 ] 無効でない場合にのみ、宣言されていないプラグインをログに記録します

この PR により、実際には宣言されておらず、使用されていない（有効なインスタンスと見つからないインスタンス）プラグインが修正されてログに記録されます。

_AC-15386 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/40086) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/40081)_

#### Magento 2.4.8-p2、magento/framework バージョン 103.0.8-p2：存在しないメソッドを呼び出す EmailMessage クラス

_AC-15446 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/40170) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/059fd469) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/e9412b24)_

#### [Magento 2.3.x] データ/スキーマパッチ getAliases （）が `setup:upgrade` 中にエラーを発生させる

getAliases （）はセットアップ中にエラーを引き起こします :upgrade、この PR は同じことを修正します

_AC-15559 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/31396) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/38239)_

#### タイプ「Magento\Customer\Api\Data\GroupInterface」が必要です。 「Magento\Customer\Model\Group」が見つかりました。

GroupFactory を使用して GroupRepositoryInterface を介して顧客グループを保存すると、タイプエラーが発生する問題を修正しました。
以前は、リポジトリは GroupInterface を想定していましたが、グループモデルインスタンスが渡され、致命的なエラーが発生していました。
現在は、適切なインターフェイス実装を確保することにより、リポジトリを通じて顧客グループを正常に保存できます。
これは、顧客グループをプログラムで作成または更新する際の IDE の警告および実行時エラーを解決します。

_AC-6909 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/36269)_

#### [ 問題 ] 禁止された `@author` タグを削除する

この PR は、コードベースから `@author` タグを削除します

_AC-8349 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/37266) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/37016)_

#### [ 問題 ] 禁止された `@author` タグを削除する

この PR は、コードベースから `@author` タグを削除します

_AC-8350 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/37265) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/37015)_

#### [ 問題 ] 禁止された `@author` タグを削除する

この PR は、コードベースから `@author` タグを削除します

_AC-8359 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/37262) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/37012)_

#### [ 問題 ] 禁止された `@author` タグを削除する

この PR は、コードベースから `@author` タグを削除します

_AC-8362 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/37259) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/37009)_

#### [ 問題 ] `@author` および `Magento_Backup` から禁止されている `Magento_Bundle` タグを削除する

この PR は、コードベースから `@author` タグを削除します

_AC-8367 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/37244) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/36979)_

#### [ 問題 ] カタログ検索の変数名を修正する

システムが検索エンジンモジュール内の変数に正しく名前を付け、コードの明確さと保守性が向上しました。 以前は、無関係な変数名$defaultCountry が検索エンジンモジュールで使用され、混乱を招いていました。

_AC-9215 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/37810) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/33533)_

#### [QUANS]Server の問題。無効な S3 アクセス キーが原因である可能性があります。

AWS S3 の資格情報が正しくなければ、ページがストアフロントに無限に読み込まれなくなりました。

_ACP2E-3890 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/2a1e1e55)_

#### [QUANS][Cloud] Minify js が機能しない

JS の縮小が有効な場合、mage/backend/tabs.min.j、jquery/jquery.validate.min.js およびMagento_PageBuilder/js/form/element/validator-rules-mixin.min.js の JS ファイルが完全かつ正しく縮小されるようになりました。 その結果、ページビルダー CSS クラスフィールド検証が期待どおりに動作します。

_ACP2E-3925 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/47721be6)_

#### Cron ジョブでデータベース・テーブルがクリアされない：Galera のクラッシュによる停止が発生

大量の削除操作を避けるために、変更ログテーブルのクリーンアップがバッチで実行されるようになりました。

_ACP2E-3995 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/52f46328)_

#### 縮小されていない JS は、「enable js の縮小」を無視して読み込まれることがあります。

修正の前は、縮小化を有効にしていた場合でも、一部の JS ファイルが「min」プレフィックスを付けずにリクエストされ、結果としてステータスコード 404 が返されていました。 修正後、縮小が有効になっている場合、縮小されていない JS リソースはリクエストされません。

_ACP2E-4058 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/6dd3fa99)_

#### カスタム属性グループの日付属性で、管理者に日付選択を表示できない

カスタム属性グループに割り当てたときに、日付属性のカレンダーポップアップが画面の外に表示される問題を修正しました。

_ACP2E-4060 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/6dd3fa99)_

### GraphQL

#### 顧客注文GraphQL：関連付けられた商品の商品カテゴリを取得すると、「個別に表示されない

修正の前は、注文に非表示の製品が含まれている場合、そのカテゴリには、顧客注文 GraphQl 応答で空の配列が表示されます。
現在は、修正後に、製品が非表示になっていても、顧客注文 GraphQl リクエストの応答に製品カテゴリが含まれるようになりました。

_ACP2E-3945 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/2a1e1e55)_

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

### GraphQL、インベントリ/MSI

#### GraphQL mergeCart のミューテーションの不一致

修正後、結合カートのGraphQLリクエストは、在庫設定を考慮して、製品数量を適切にチェックします。

_ACP2E-4184 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/inventory/commit/5632fb5e)_

### GraphQL、セキュリティ

#### GraphQLを使用したカスタマーパスワードのリセットが制限に従わない

GraphQLの変更点を通じて行われたお客様のパスワードリセットリクエストが、ストア/設定/お客様/お客様の設定/パスワードリセットのオプションで設定されたパスワードリセット制限に準拠しない問題を修正しました。 これらの設定が正しく適用されるようになりました。

_ACP2E-3992 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/6dd3fa99)_

### インポート/エクスポート

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

### インベントリ/MSI

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

### 順序

#### Magento 2.4.8 GraphQL – 注文項目 order_date の形式が正しくない

GraphQL応答の order_date フィールドが yyyy-mm-dd 形式で返される問題を修正しました。
これで、order_date が dd-mm-yyyy 形式で正しく表示されます。

_AC-14431 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39805) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/a3b1abc2)_

#### ストア設定で有効になっているにもかかわらず、管理者の注文表示から送信されたときに出荷 E メールが送信されない

注文が行われた店舗設定で出荷確認メールが有効になっているので、システムが出荷確認メールを送信するようになりました。

_AC-14563 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39861) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/39897)_

#### フィールド名があいまいなため、日付のフィルタリングは機能しません

Magento 2.4.7-p6 では、日付でオーダーグリッドをフィルタリングすると、Braintree モジュールとの結合が原因でエラーが発生することが報告されました。
この問題では、日付フィルターを適用する際に、braintree_transaction_details テーブルと sales_order テーブルを結合するクエリが発生していました。
Adobe Commerceのエンジニアリングチームはケースを確認したが、エラーを再現できなかった。
期待される動作は、日付別のフィルタリングでは、エラーなくフィルターに一致する注文を返す必要があることです。

_AC-15037 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/40024)_

#### Magento2：プロモーションルールを作成できない

この PR は修正され、
メソッド \Magento\SalesRule\Model\Rule\Condition\Product::loadAttributeOptions の\Magento\Catalog\Model\ResourceModel\Eav\Attributeではなく、\Magento\Catalog\Model\ResourceModel\Eav\Attribute モデル

_AC-15358 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/12176) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/30479)_

#### 404 への請求書リダイレクトの取消

「取得なし」タイプで作成された請求書の取消は、404 ページにはつながりません。

_ACP2E-4001 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/2a1e1e55)_

#### Sales Archive Cron ジョブが原因で DB ロックの問題が発生

この修正以前は、アーカイブ cron の順序アーカイブにあるバインドされていないDELETE クエリが Galera で問題を引き起こしていました。 更新後、削除クエリが制限付きで実行されるようになりました。

_ACP2E-4010_

#### REST API を使用した設定可能なオプションを含む更新済み注文の問題

Rest api エンドポイントを使用して注文を更新する際に、販売注文項目の既存の製品オプションを保持します。

_ACP2E-4061 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/6dd3fa99)_

### その他の開発者ツール

#### [ 問題 ] 未使用のコードをクリーンアップしています。

未使用の読み込みに関する未使用のコードが削除されるようになりました。

_AC-10980 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/38424) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/33499)_

#### [ 問題 ] アクセシビリティ：WAI-ARIA の役割のメニューでのネストが正しくない

システムは、メニューエラーで WAI-ARIA の役割のネストが正しくなく、レポートが緑色であるにもかかわらず、lighthouse のアクセシビリティを生成するようになりました

_AC-15082 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/40045) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/38617)_

#### Magento管理者のメールのプレビューでコンソールエラーが発生する

メールテンプレートをプレビューしている間、コンソールエラーはスローされません

_AC-9245 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/37820) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/37933)_

### 支払額

#### PayPal からの不明な IPN がアプリケーション IPN プロセッサーを悪用する

IPN ハンドラは、サポートされていない IPN タイプまたは不明な IPN タイプを無視するようになりました。 500 エラーを返す代わりに、問題をログに記録し、中断することなく処理を続行します。

_ACP2E-4049 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/6dd3fa99)_

#### PayflowPro 保存済みカードトークンは支払いに失敗しました

PayPal PayFlow Pro のトランザクション ID （PNREF）が、12 か月の固定期間の参照トランザクションで使用できるようになりました。 有効期限が切れると、保存されたカードは表示されなくなり、再度追加する必要があります。 以前は、有効性は元のトランザクションで使用される支払いカードの有効期限によって決定されていました。

_ACP2E-4064 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/52f46328)_

### パフォーマンス

#### [ 問題 ] 静的サイトの use キャッシュコントロールを更新すると、変更できません

この PR は、変更されない限り、各ページ読み込みの静的コンテンツを検証しないことで、パフォーマンス向上を実現します。

_AC-15171 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39486) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/39484)_

#### [CLOUD] カテゴリに製品を追加できない

ビジュアルマーチャンダイザーを通じてカテゴリに製品を追加する際のパフォーマンスが向上しました。

_ACP2E-3946 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/inventory/commit/29653b1d)_

#### 10,000 件を超えるログを [Cloud] cache_invalidate

以前は、各 PLP または買い物かごへの訪問でキャッシュがクリアされたため、不要なパフォーマンスのオーバーヘッドが発生していました。 これらのページでは、ターゲットルールキャッシュが無効化されなくなり、閲覧効率が向上します。

_ACP2E-4059_

### Pricing

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

#### テストケース AC-6158 の設定可能な製品には、引き続き「As low as」ラベルが表示されます

各バリエーションおよびカテゴリ割り当てによって、設定可能な製品（P1～P7）を実装および検証しました。 カテゴリ C の製品について、正しい店頭価格の表示と「できるだけ低い」ラベルの動作を確認しました。

_AC-10847 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/a3b1abc2)_

#### リポジトリーを介した製品のリクエスト時に追加のログに失敗する

SKU または ID が見つからない場合の ProductRepository::get および getById のエラーメッセージを改善しました。
以前は、例外には、エラーの原因となった SKU や ID に関するコンテキストが提供されていませんでした。
現在は、例外メッセージに欠落した SKU または ID が含まれるようになり、デバッグと開発者エクスペリエンスの向上に役立っています。
この変更は、API の機能動作には影響しません。

_AC-15199 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/40090) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/1b1baf1d)_

#### 設定可能な製品が制限付き役割で編集された場合、単純な製品の割り当てが解除される

この修正の前は、制限付きの管理者ユーザーが、管理者ユーザーがアクセス権を持たないシンプルな製品を含む設定可能な製品を保存する場合、保存時に設定可能な製品から削除されていました。 修正後、設定可能な製品は、完全な権限を持つ管理者によって保存されたとおりに保持されます。

_ACP2E-4081_

#### [ クラウド ] サイトマップの生成パフォーマンスが大幅に低下している

画像を含んだ製品のサイトマップの生成で、急激な減速が発生しなくなりました。 以前は、画像を含める処理が有効なストアのサイトマップを生成すると、処理時間が長くなっていました。

_ACP2E-4153 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/e457c5e2)_

### プロモーション

#### GraphQl 顧客リクエスト経由で顧客注文の注文品目割引 applied_to を取得中にエラーが発生しました

以前は、GraphQl 顧客リクエストを介した顧客注文の割引が applied_to であった場合、内部サーバーエラーが発生していましたが、このエラーが修正され、割引が適用された適切な顧客注文データが取得されるようになりました

_AC-14888 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39963) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/fe72c407)_

#### GraphQl 顧客リクエスト経由で顧客注文の注文項目クーポンコードを取得中にエラーが発生しました

GraphQLを介してクーポンの詳細を含む注文を取得すると、内部サーバーエラーが返される問題を修正しました。
これで、クエリが正常に実行され、応答に正しいクーポン情報が返されます。

_AC-14889 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/39962) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/fe72c407)_

### SEO

#### ProductRepository getById の配列キーが定義されていません

この問題は、ProductRepository::getById （）が 123abc のような無効な ID で呼び出され、「未定義の配列キー」エラーが発生する場合に発生していました。
Magento 2.4.9-alpha3 の修正後、このようなリクエストは、例外をスローする代わりに 404 ページを正しく返すようになりました。
QA が有効な ID と不正な形式の ID の両方で確認され、それ以上の問題は観察されませんでした。

_AC-15345 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/40146) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/68a45d0a)_

#### [ クラウド ] サイトマップの生成が終了しない

この修正より前は、カタログに 100 万個を超える製品が含まれている場合、サイトマップの生成を正常に完了できませんでした。 修正後、サイトマップの生成はメモリ割り当てが少なくなり、1 ストアあたり 100 万個もの製品で完了します。

_ACP2E-3902 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/52f46328)_

#### よくある質問（FAQ）ページで、[ クラウド ] ストアスイッチャーが EN から FR に変わらない

ストアビューを切り替えると、対応する翻訳済みCMS ページではなくホームページにユーザーがリダイレクトされる問題を修正しました。 ストアスイッチャーは、正しいリダイレクトを確実にするためにターゲットストアの URL 書き換えをチェックするようになりました（例：英語の FAQ ページ→フランス語の FAQ ページ）。

_ACP2E-4112_

### ステージングとプレビュー

#### 別の管理ドメインを使用している場合、チェックアウト時にステージング更新のプレビューが壊れる

顧客は、ストアのベース URL が管理 URL と異なる場合、ログインして買い物かごをストアプレビューモードで表示できます。

_ACP2E-3906_

#### コンテンツのステージングダッシュボードに間違った時間が表示される

「コンテンツのステージングダッシュボード」の「開始時刻」と「終了時刻」の日付フィルターに、正しい日時が表示されるようになりました。 以前は、日付選択で日時を選択すると、誤った日時が表示されていました

_ACP2E-3969_

#### スケジュールされた更新の製品およびカテゴリのプレビュー中、スコープに異なるストア表示が表示されます

以前は、カテゴリと製品のプレビューリンクが正しいストアに対して生成されていませんでした。 この修正後、プレビューリンクは、プレビューが作成されたストアを自動的に選択します。

_ACP2E-4053_

### UI フレームワーク

#### [ 問題 ] `@author` から禁止されている `Magento_Backend` タグを削除する

この PR は、コードベースから `@author` タグを削除します

_AC-8814 - [GitHub の問題 &#x200B;](https://github.com/magento/magento2/issues/37522) - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/pull/36976)_
