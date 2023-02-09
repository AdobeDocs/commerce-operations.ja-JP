---
title: リリースノート
description: Adobe Commerceで利用可能なパッチと、それらが解決する問題について説明します。
source-git-commit: 76ff1bbcc3a1ca8f73dfdd2ba4f516a201986f62
workflow-type: tm+mt
source-wordcount: '10848'
ht-degree: 0%

---

# リリースノート

この [[!DNL Quality Patches Tool]](https://github.com/magento/quality-patches) は、AdobeとMagento Open Source・コミュニティが開発した個々のパッチを提供します。 インストールされたAdobe CommerceまたはMagento Open Sourceで使用可能なすべての個々のパッチに関する一般情報を、適用、元に戻し、表示できます。 パッチの開発者に関係なく、Adobe CommerceおよびMagento Open Sourceプロジェクトにパッチを適用できます。 例えば、コミュニティが開発したパッチをAdobe Commerceプロジェクトに適用できます。

>[!INFO]
>
>詳しくは、 [パッチの適用](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html#apply-individual-patches) を参照してください。 詳しくは、 [利用可能なパッチ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) リリース済みのパッチの完全なリストを確認するには、『ソフトウェアアップデートガイド』を参照してください。

>[!INFO]
>
>詳しくは、 [!DNL quality patches] コミュニティで作成されたMagento Open Source: [リリースノート](https://github.com/magento/quality-patches/blob/master/community-release-notes.md).

## v1.1.27 {#v1-1-27}

* **ACSD-48362** (Adobe Commerce>=2.4.1 &lt;2.4.7) — 交渉可能な見積もりを使用して注文を行う際に、新しい送付先住所の代わりにデフォルトの送付先住所が使用される問題を修正しました。
* **ACSD-48059** (Adobe Commerce >=2.3.7 &lt;2.4.7) — マーチャントが[!UICONTROL Match product by rule]」と入力します。
* **ACSD-48216** (Adobe CommerceおよびMagento Open Sourceの場合 >=2.3.7 &lt;2.3.8 || >=2.4.0 &lt;2.4.7) - [!UICONTROL AUTO_INCREMENT] の [!UICONTROL inventory_source_item] 表が上がる [!UICONTROL UPDATE] 操作。
* **ACSD-47908** (Adobe CommerceおよびMagento Open Sourceの場合 >=2.3.7 &lt;2.3.8 || >=2.4.0 &lt;2.4.7) — チェックアウト時に出荷ステップのソースと数量を選択する際のエラー「0 以下の値が必要です」を修正しました。
* **ACSD-49497** (Adobe CommerceとMagento Open Source>=2.3.7 &lt;2.4.6) — 出荷後に注文が処理状態のままで、一部払い戻しが適用される問題を修正しました。
* **ACSD-48694** (Adobe CommerceおよびMagento Open Sourceの場合 >=2.3.7 &lt;2.3.8 || >=2.4.1 &lt;2.4.7) - 「無効な状態の変更がリクエストされました」というエラーが発生し、お客様が注文できない問題を修正しました。
* **ACSD-49013** (Adobe CommerceとMagento Open Source>=2.4.3 &lt;2.4.7) — 一括 API を使用して顧客を作成する際に、電子メールによる確認が Web サイトのロケールに翻訳されない問題を修正しました。
* **ACSD-48164** (Adobe CommerceとMagento Open Source>=2.3.7 &lt;2.4.7) — 制限付き管理者が Web サイトレベルの値を保存できない問題を修正しました。
* **ACSD-48404** (Adobe CommerceとMagento Open Source>=2.4.0 &lt;2.4.4.4) — ブラウザーの戻るボタンを押したときに「Remember Category Pagination = Yes」が発生する問題を修正しました。
* **ACSD-48634** (Adobe CommerceおよびMagento Open Source>=2.3.7 &lt;2.4.7) - 「[!UICONTROL Google Analytics Content Experiments]」が有効になっている。
* **ACSD-49042** (Adobe CommerceとMagento Open Source>=2.4.4 &lt;2.4.5) — 無限の逆オーダーを持つ製品を Storefront から並べ替えることができない問題を修正しました。
* 更新済みのパッチ：ACSD-48366、ACSD-48661。

## v1.1.26 {#v1-1-26}

* **ACSD-47937** (Adobe CommerceおよびMagento Open Source2.4.4 の場合 ) || >=2.4.5 &lt;2.4.6) — アプリケーションレベルのキャッシュが原因で価格下落通知が送信されない場合がある問題を修正しました。
* **ACSD-48661** (Adobe CommerceとMagento Open Source>=2.3.7 &lt;2.4.7) — 会社の与信限度額が 999 を超える場合、コンマ区切り文字は検証エラーによる会社の保存を妨げる問題を修正しました。
* **ACSD-48773** (Adobe CommerceとMagento Open Source>=2.4.2 &lt;2.4.7) — 報酬ポイントの E メールテンプレートが間違ったストアから取り出される問題を修正しました。
* **ACSD-48587** (Adobe CommerceとMagento Open Source>=2.3.7 &lt;2.4.7) -HTMLウィジェットの一致ルールで、製品の一致する特殊文字が表示されない問題を修正しました。
* **ACSD-48212** (Adobe CommerceとMagento Open Source>=2.3.7 &lt;2.4.6) — 製品の読み込みによって製品が間違ったソースに割り当てられる問題を修正しました。
* **ACSD-47988** (Adobe CommerceとMagento Open Source>=2.3.7 &lt;2.4.6) — 製品の書き出しで、page builder の製品説明からHTMLタグがトリミングされる問題を修正しました。
* **ACSD-48366** (Adobe CommerceとMagento Open Source>=2.4.4 &lt;2.4.6) — 製品の画像が「Back to Stock」の電子メールテンプレートに表示されない問題を修正しました。
* **ACSD-48417** (Adobe CommerceおよびMagento Open Source>=2.4.5 &lt;2.4.7) — 製品のスケジュール変更を作成して別の製品を保存した後に SQL エラーが表示される問題を修正しました。

## v1.1.25 {#v1-1-25}

* **ACSD-48058** (Adobe CommerceとMagento Open Source>=2.4.5 &lt;2.4.6) — バンドル製品がどの Web サイトにも割り当てられていない場合に、製品価格の再インデックスが機能しない問題を修正しました。
* **ACSD-48262** (Adobe CommerceとMagento Open Source>=2.4.5 &lt;2.4.6) - 「1 ページあたりのすべての製品を許可」設定が「はい」に設定されている場合に、製品がフロントエンドに表示されない問題を修正しました。
* **ACSD-48293** (Adobe CommerceとMagento Open Source>=2.4.3 &lt;2.4.4.4) — 子製品が売り切れた場合に複合製品が在庫切れになる問題を修正しました。
* **ACSD-47520** (Adobe CommerceとMagento Open Source>=2.4.0 &lt;2.4.6) — クレジットメモを作成するとお客様が報酬ポイントを失う問題を修正しました。
* **ACSD-48044** (Adobe CommerceとMagento Open Source>=2.4.0 &lt;2.4.4.4) — 複数のギフトカードを複数の配送で 1 つの注文に適用すると注文が行われない問題を修正しました。
* **ACSD-48300** (Adobe CommerceとMagento Open Source>=2.4.0 &lt;2.4.6) — 設定可能な製品が削除された場合に戻り値を作成できない問題を修正しました。
* **ACSD-47910** (Adobe CommerceおよびMagento Open Source>=2.4.4 &lt;2.4.6) — 各エンティティグリッドで発行されない注文、請求書、出荷およびクレジットメモの問題を修正します。
* **ACSD-47292** (Adobe CommerceとMagento Open Source>=2.4.4 &lt;2.4.6) - 「在庫切れの製品を表示」が「はい」に設定されている場合、GraphQLの応答で在庫切れのバンドル製品が使用できない問題を修正しました。
* **ACSD-48234** (Adobe CommerceとMagento Open Source>=2.4.5 &lt;2.4.6) - 「在庫切れを表示」オプションが有効な場合に、カタログ検索結果で誤ったカテゴリ項目数が表示される問題を修正しました。
* **ACSD-48313** (Adobe CommerceとMagento Open Source>=2.4.0 &lt;2.4.5) — 属性値にコンマが含まれる場合に「configurable_variations」列が解析されない問題を修正しました。 「additional_attributes」にも同じ解析アルゴリズムが使用されます。
* **ACSD-48627** (Adobe CommerceとMagento Open Source>=2.4.5 &lt;2.4.6) — 買い物かごの詳細を取得するGraphQLリクエストの送信時に、在庫切れの設定可能な製品がエラーを引き起こす問題を修正しました。
* 更新されたパッチ：MDVA-39384.

## v1.1.24 {#v1-1-24}

* **ACSD-45168** (Adobe CommerceおよびMagento Open Source>=2.4.2 &lt;2.4.6) - SEO に対応する URL が *url_key* 属性は、store-view レベルで上書きされます。
* **ACSD-46865** (Adobe CommerceとMagento Open Source>=2.4.4 &lt;2.4.6) — 非同期インデックス作成が有効な場合に出荷とクレジットメモのグリッドが入力されない問題を修正しました。
* **ACSD-47004** (Adobe CommerceとMagento Open Source>=2.4.2 &lt;2.4.6) - VAT ID のない請求先住所に VAT が適用されない問題を修正しました。
* **ACSD-47803** (Adobe CommerceとMagento Open Source>=2.4.0 &lt;2.4.6) — 在庫切れの設定可能な製品スウォッチが使用可能な状態で表示される問題を修正しました。
* **ACSD-47137** (Adobe CommerceとMagento Open Source>=2.4.4 &lt;2.4.6) - pub/media フォルダーが非常に大きい場合の画像ギャラリーの読み込み速度が向上します。
* **ACSD-46770** (Adobe CommerceとMagento Open Source>=2.4.0 &lt;2.4.6) - *E メールの注文確認* がオフになっている。
* **ACSD-47955** (Adobe CommerceとMagento Open Source>=2.4.4 &lt;2.4.6) - GraphQLで買い物かごの割引が正しく表示されない問題を修正しました。
* **ACSD-46617** (Adobe CommerceとMagento Open Source>=2.4.0 &lt;2.4.6) - *チェックアウトを続行* ボタンは、小計が設定済みの *最小注文額*.
* **ACSD-47079** (Adobe CommerceとMagento Open Source>=2.4.4 &lt;2.4.5) - REST APIPOST/rest/V1/inventory/source-items を使用して下位製品の在庫ステータスが変更された場合に、複合製品（バンドル、グループ化、設定可能）の在庫ステータスが更新されない問題を修正しました。
* **ACSD-47336** (Adobe CommerceとMagento Open Source>=2.4.0 &lt;2.4.6) — 修正点 *問題が発生しました。* コマース管理で通知を破棄する際にエラーが発生しました。
* **ACSD-47559** (Adobe CommerceとMagento Open Source>=2.4.0 &lt;2.4.6 の場合 ) - 「 Preview Email Template 」領域が完全に表示されない問題を修正しました。
* **ACSD-47920** (Adobe CommerceとMagento Open Source>=2.4.0 &lt;2.4.6) - Rest API を介してゲストユーザーとして注文を行える問題を修正しました。 *ゲストによるチェックアウトを許可* がオフになっている。
* 交換済みのパッチ：MDVA-39305、MDVA-42855。

## v1.1.23 {#v1-1-23}

* **ACSD-47179** (Adobe CommerceとMagento Open Source>=2.4.0 &lt;2.4.6) — 特定の範囲へのアクセスが制限された管理者が製品レビューを削除できない問題を修正しました。
* **ACSD-47107** (Adobe CommerceとMagento Open Source>=2.4.2 &lt;2.4.5) — カタログ価格ルールの割引がカスタム製品オプションに適用される問題を修正しました。
* **ACSD-47232** (Adobe CommerceとMagento Open Source>=2.4.0 &lt;2.4.6) — 管理で合計重み付け条件を持つクーポンを適用できない問題を修正しました。
* **ACSD-46519** (Adobe CommerceとMagento Open Source>=2.4.1 &lt;2.4.6) - GraphQL categoryList リクエストがアンカーカテゴリに対して誤った product_count を返す問題を修正しました。
* **ACSD-47027** (Adobe CommerceおよびMagento Open Source>=2.4.2 &lt;2.4.6) - GraphQLの低速な updateCompanyRole リクエストを修正しました。
* **ACSD-47666** (Adobe CommerceとMagento Open Source>=2.4.0 &lt;2.4.6) — 管理者/システム/権限/ユーザーの役割/役割のユーザーグリッドでフィルター機能が動作しない問題を修正しました。
* **ACSD-47497** (Adobe CommerceとMagento Open Source>=2.4.0 &lt;2.4.6) — 管理者の下の設定で「サービス」タブが表示されない問題を修正しました。
* 更新されたパッチ：ACSD-47743。
* 交換済みのパッチ：MDVA-42807.

## v1.1.22 {#v1-1-22}

* **ACSD-47444** (Adobe CommerceとMagento Open Source>=2.4.0 &lt;2.4.3) - _ブール型の値の配列オフセットにアクセスしようとしています_ PHP 7.4 の既知の製品に対して、存在しない特定のカテゴリパスにアクセスする際にエラーが発生しました。
* **ACSD-47332** (Adobe CommerceとMagento Open Source>=2.4.0 &lt;2.4.6) - 00:00 ～ 00:59 UTC の間で実行した場合にのみ報告されるエラーで cron が失敗する問題を修正しました。
* **ACSD-47280** (Adobe CommerceとMagento Open Source>=2.4.0 &lt;2.4.6) — 特定のスコープで共有カタログ機能を無効にしても正しく機能しない問題を修正しました。
* **ACSD-47106** (Adobe CommerceとMagento Open Source>=2.4.4 &lt;2.4.6) — 会社作成ページで値を新しいカスタム属性に保存できない問題を修正しました。
* 更新されたパッチ：ACSD-45143。

## v1.1.21 {#v1-1-21}

* **ACSD-46809** (Adobe CommerceとMagento Open Source>=2.4.2 &lt;2.4.6) — 多数の製品ソースを割り当てるとエラーが発生する問題を修正しました。
* **ACSD-46856** (Adobe CommerceおよびMagento Open Source>=2.4.0 &lt;2.4.6) - [ システム ] > [ 構成 ] > [ インポート ] > [ アドバンスドプライシング ] から、パフォーマンス更新階層の価格を向上させます。
* **ACSD-46541** (Adobe CommerceとMagento Open Source>=2.4.0 &lt;2.4.4.4) — 注文項目が削除された場合に管理者ユーザーがクレジットメモを作成できない問題を修正しました。
* **ACSD-46581** (Adobe CommerceとMagento Open Source>=2.4.0 &lt;2.4.6) — 買い物かごの国を選択した後も推定税額が更新されない問題を修正しました。
* **ACSD-46618** (Adobe CommerceとMagento Open Source>=2.4.0 &lt;2.4.6) — 製品リストウィジェットがログインしている顧客に対してキャッシュされた価格を正しく表示しない問題を修正しました。
* **ACSD-46674** (Adobe CommerceとMagento Open Source>=2.4.0 &lt;2.4.6) — 画像タイプのカスタムオプションが顧客の電子メールにHTMLとして表示される問題を修正しました。
* **ACSD-46988** (Adobe CommerceとMagento Open Source>=2.4.4 &lt;2.4.6) - GraphQLの「currency」API リクエストがカスタム通貨の NULL 値を返す問題を修正しました。
* **ACSD-47076** (Adobe CommerceとMagento Open Source>=2.4.1 &lt;2.4.5) — ストアフロントで Vimeo ビデオを再生できない問題を修正しました。
* **ACSD-45071** (Adobe CommerceとMagento Open Source>=2.4.2 &lt;2.4.4.4) — 読み込み時にデフォルトのソースが製品に追加される問題を修正しました。
* **AC-3023** (Adobe CommerceとMagento Open Source>=2.4.0 &lt;2.4.6) - DHL スキームを最新バージョン 10.0 に更新します。
* 更新済みのパッチ：MDVA-42584.
* 交換済みのパッチ：ACSD-45241、MDVA-36572。

## v1.1.20 {#v1-1-20}

* **ACSD-46520** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.4.0 &lt;2.4.5*) — ストアクレジットを使用して返金した場合に、ユーザーの注文ステータスが正しくない問題を修正しました。
* **ACSD-46703** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.4.4 &lt;2.4.6*) — 製品の編集ページにカスタムオプションをドラッグ&amp;ドロップできない問題を修正しました。
* **ACSD-44851** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.4.0 &lt;2.4.6*) — サブカテゴリを持つカテゴリを開いたり展開したりできない問題を修正しました。
* **ACSD-46815** (*Adobe CommerceとMagento Open Sourceの場合 >=2.4.5 &lt;2.4.6*) — カテゴリツリーリクエストが 20 個のカテゴリに制限される問題を修正しました。
* **ACSD-45675** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.4.0 &lt;2.4.6*) — 製品エクスポートで、 *デフォルトのストア表示* 範囲。
* **ACSD-46869** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.4.4 &lt;2.4.6*) — 買い物かご内の設定可能な製品が *PUTREST API* リクエストを作成できます。
* **MDVA-42768-V2** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.4.2 &lt;2.4.3*) — 設定可能な製品で標準価格が *0* when *在庫切れの表示* が *はい*.
* 更新済みのパッチ：MDVA-44562、ACSD-46213、MDVA-41305、MDVA-38346、MDVA-13203。
* 非推奨のパッチ：MDVA-42768.

## v1.1.19 {#v1-1-19}

* **ACSD-46213** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.4.2 &lt;2.4.3*) — カテゴリツリーリクエストが 20 個のカテゴリに制限される問題を修正しました。
* **ACSD-45781** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.4.1 &lt;2.4.2*) — ストアの前面検索フィールドがモバイルに表示されない問題を修正しました。
* **ACSD-46192** (*Adobe CommerceとMagento Open Sourceの場合 >=2.3.6 &lt;2.4.5*) — の `async/bulk/V1/configurable-products/bySku/options` endpoint.
* **ACSD-46404** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.4.4 &lt;2.4.5*) - 2.4.4 にアップグレードした後に管理者ユーザーがログインできない問題を修正しました。
* 更新済みのパッチ：MDVA-41305、MDVA-38626、MDVA-38728、MDVA-41061-V4、MDVA-42269、MDVA-39305。

## v1.1.18 {#v1-1-18}

* **ACSD-45817** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.4.2 &lt;2.4.4.4*) — 特定のストアのGraphQL製品のミューテーションが、リクエストされたストアに割り当てられていないバリエーションを含む、設定可能なすべてのバリアントを返す問題を修正しました。
* **ACSD-46146** (*Adobe CommerceとMagento Open Sourceの場合 >=2.3.0 &lt;2.4.6*) — 管理者から注文を入れた後に 2 通の注文確認 E メールが送信される問題を修正しました。
* **ACSD-45255** (*Adobe Commerceの場合 >=2.4.3 &lt;2.4.6*) — 制限付き管理者ユーザーの低在庫レポートページの例外を修正します。
* **ACSD-45488** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.4.2 &lt;2.4.6*) — 複数のソースを持つ設定可能な製品が In Stock に自動的に返されない問題を修正しました。
* **ACSD-45754** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.3.1 &lt;2.4.6*) — カートにクーポンを適用した後に報酬ポイントが追加されない問題を修正しました。
* **ACSD-45849** (*Adobe Commerceの場合 >=2.4.3 &lt;2.4.4.4.4*) — ステージング更新が適用された後にビデオメタデータが失われる問題を修正しました。
* **ACSD-45257** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.3.4 &lt;2.4.4*) - GraphQLで買い物かごの割引が正しく表示されない問題を修正しました。
* **ACSD-44938** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.4.0 &lt;2.4.4*) - `VAT_ID` は、ゲストユーザーのGraphQLリクエストで適用できません。
* 更新済みのパッチ：MDVA-43417.

## v1.1.17 {#v1-1-17}

* **ACSD-45241** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.3.5 &lt;2.4.4*) — クレジットメモを作成した後に仮想製品の在庫数が誤って計算される問題を修正しました。
* **ACSD-43887** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.4.2 &lt;2.4.5*) — 会社の発注書が有効な場合に、チェックアウトの支払いページに間違った詳細が表示される問題を修正しました。
* **ACSD-45143** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.4.0 &lt;2.4.5*) - `setShippingAddressesOnCart` 突然変異は、数値領域コードを *地域*.
* **ACSD-44591** (*Adobe CommerceとMagento Open Sourceの場合 >=2.4.3 &lt;2.4.6*) - CAPTCHA の確認なしで注文がおこなわれた場合に発生するエラーを修正します。
* **ACSD-45520** (*Adobe CommerceとMagento Open Sourceの場合 >=2.3.0 &lt;2.4.6*) — ユーザーが買い物かごから設定可能な製品を編集した際に、製品の詳細ページでスウォッチオプションが事前に選択されていない問題を修正しました。
* **ACSD-45169** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.4.1 &lt;2.4.6*) - [!DNL Visual Merchandiser] ステージング更新が適用された後、設定可能な製品の正しい在庫と価格が表示されません。
* **ACSD-45424** (*Adobe CommerceとMagento Open Sourceの場合 >=2.3.4 &lt;2.4.6*) — 一部払い戻し（クレジットメモ）後に誤った予約補正が作成される問題を修正しました。
* **MDVA-42807** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.3.1 &lt;2.4.6*) — カスタム通貨記号がストア前面に表示されない問題を修正しました。
* 更新済みのパッチ：AC-3022 MDVA-42689.

## v1.1.16 {#v1-1-16}

* **MDVA-44703** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.4.3 &lt;2.4.4*) — 注文件数レポートの注文の合計で、制限された管理者ユーザーに対して誤って計算される問題を修正しました。
* **MDVA-44940** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.4.3 &lt;2.4.4*) — 管理者からカテゴリを保存する際に発生する SQL エラーを修正します。
* **MDVA-44562** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.4.0 &lt;2.4.2-p2*) — デフォルト以外のストア表示からのGraphQL要求にもかかわらず、見積もり項目のデフォルト以外のストア ID がデフォルトのストア ID で上書きされる問題を修正しました。
* **MDVA-43167** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.4.2 &lt;2.4.4.4*) — 管理者ユーザーがすべての注文を選択した場合に、複数ページに対して管理者の注文グリッドの一括アクションが適用されない問題を修正しました。
* **MDVA-44044** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.3.0 &lt;2.4.2-p2*) — 製品が新しい Web サイトに割り当てられた後、カテゴリページに表示されない問題を修正しました。
* **MDVA-42509** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.3.3 &lt;2.4.4*) - CSV をアップロードして注文をすばやく実行できなかった結果、 *Cookie を送信できません* エラー。
* 更新済みのパッチ：MDVA-41061、MDVA-42584。
* 新しい [!DNL Quality Patches Tool] パッチは次の場所から変更されます。 *MDVA* から *ACSD* 内部プロセスの変更による。

## v1.1.15 {#v1-1-15}

* **MDVA-40961** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.4.3 &lt;2.4.4*) — 項目の最小数が既に買い物かごに入っている場合に、追加の項目を買い物かごに追加できない問題を修正しました。
* **MDVA-44887** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.4.4 &lt;2.4.5*) - *不明な構文エラー：予期しないトークン&#39;const&#39;* エラーが発生しました。
* **MDVA-43718** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.3.0 &lt;2.4.5*) — 修正点 *消費者は%resources へのアクセスを許可されていません。* カスタム統合から共有カタログにアクセスする際に表示されるエラー。
* **MDVA-44660** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.4.2-p1 &lt;2.4.5*) — グレーブアクセント文字の問題を修正しました。 ``` ` ``` を顧客の姓と名に使用できなかった問題を修正しました。
* **MDVA-40896** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.4.3 &lt;2.4.4*) - *エラー：TypeError:引数 3 がMagentoに渡されました* 非同期製品一括 API でエラーが発生しました。
* **MDVA-38559** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.4.0 &lt;2.4.3*) - */V1/customers/search API* 複数のサブスクリプションを持つ顧客に対するエラー。
* **MDVA-44533** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.3.1 &lt;2.4.4*) — バンドルの子製品に割引が誤って適用される問題を修正しました。
* 更新済みのパッチ：MDVA-41061、MDVA-42269。

## v1.1.14 {#v1-1-14}

* **MDVA-43983** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.4.2 &lt;2.4.5*) — 製品の問題を修正しました *個別に表示されない* は、「カタログの詳細検索結果」に表示されます。
* **MDVA-44100** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.4.3 &lt;2.4.5*) — すべての FPT が買い物かごの最後の製品に割り当てられ、他の製品にリセットされる問題を修正しました。
* **MDVA-43605** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.3.1 &lt;2.4.5*) - Rest API を使用している場合に、注文データが行の合計に負の値を返す問題を修正しました。
* **MDVA-43102** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.3.1 &lt;2.4.5*) - REST API を使用して返金が行われた場合に販売可能数量が正しく更新されない問題を修正しました。
* **MDVA-43178** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.4.3-p2 &lt;2.4.5*) — カスタムストアの顧客トークンをGraphQLで取得できない問題を修正しました。
* **MDVA-43859** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.4.1 &lt;2.4.5*) — エラーが *customerId =のエンティティはありません* は、削除された顧客がログインしようとしたときに記録されます。
* **MDVA-44147** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.4.2 &lt;2.4.5*) - GraphQL要求が要求リストを返さない問題を修正しました。
* **MDVA-44505** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.4.1 &lt;2.4.3*) - GraphQL Applying Reword Points が総計を更新しない問題、および注文の配置中にストアのクレジットが複数回適用される問題を修正しました。
* 更新済みのパッチ：MDVA-29148、MDVA-36464-V5、MDVA-42584、MDVA-39993-V2。

## v1.1.13 {#v1-1-13}

* **MDVA-42969** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.4.1 &lt;2.4.3*) - 「関連製品ルール」が機能するのは、「顧客セグメント」が「 *すべて*.
* **MDVA-39605** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.3.4 &lt;2.4.5*) - Redis キャッシュの TTL（有効期限）の値が正しくない問題を修正しました。
* **MDVA-43862** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.3.3 &lt;2.4.5*) - GraphQLが原因で買い物かごの項目を更新できない問題を修正しました *UpdateCartItems ミューテーション* エラー。
* **MDVA-43824** (*Adobe CommerceとMagento Open Sourceの場合 >=2.3.6 &lt;=2.3.7-p3 || >=2.4.1 &lt;2.4.5*) — 割引のあるオーダーをキャンセルするとエラーが表示される問題を修正しました。
* **MDVA-43451** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.4.3 &lt;2.4.5*) — エラーが *リクエストされたストアが見つかりませんでした。 ストアを確認し、再度お試しください。* は、特定の web サイト用の共有カタログの設定時に表示されます。
* **MDVA-43491** (*Adobe CommerceとMagento Open Sourceの場合 >=2.3.5 &lt;2.4.5*) — マルチストア Web サイトの製品を読み込む際にベース画像ラベルが更新されない問題を修正しました。
* **MDVA-43601** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.3.0 &lt;2.4.5*) — 完全な再インデックス後にトリガーが見つからない問題を修正しました。
* **MDVA-42046** (*Adobe Commerceの場合はMagento Open Source>=2.3.4 &lt;=2.3.5-p2 || >=2.4.0 &lt;2.4.5*) — 製品の更新中に、日付入力フィールドを含む製品属性に誤った値が割り当てられる問題を修正しました。
* **MDVA-43935** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.4.1 &lt;2.4.5*) — アップセル製品が 2 回表示される問題を修正しました。
* **MDVA-44188** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.4.3 &lt;2.4.5*) — でシステムから発行された電子メールが `.-` のアドレスは送信されません。
* **MDVA-42283** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.3.0 &lt;2.4.5*) — フランス語ロケールの管理順序グリッドの日時形式が無効な問題を修正しました。
* 更新済みのパッチ：MDVA-41061-V2、MDVA-36309、MDVA-30862、MDVA-39713。
* のパッチメタデータを追加しました。 [!DNL Site-Wide Analysis Tool].

## v1.1.12 {#v1-1-12}

* **MDVA-39713** (*Adobe CommerceとMagento Open Sourceの場合 >=2.3.0 &lt;2.3.6*) — ユーザーがアクティブなスケジュール済み更新の開始時間を編集できる問題を修正しました。
* **MDVA-42410** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.3.0 &lt;2.4.5*) — クーポンレポートにデフォルトのベース通貨のみが表示される問題を修正しました。
* **MDVA-41136** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.3.0 &lt;2.4.5*) - `mage-cache-sessid` が拡張されず、顧客データのクリーンアップがおこなわれます。
* **MDVA-39993** (*Adobe Commerceの場合は、Magento Open Source>=2.3.5 &lt;=2.3.7-p2 || >=2.4.0 &lt;2.4.4*) - API を通じておこなわれた在庫の変更がフロントエンドの製品ページに反映されない問題を修正しました。
* **MDVA-42855** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.4.3 &lt;2.4.5*) — チェックアウト時に新しい顧客アドレスがアドレス帳に保存されない問題を修正しました。
* **MDVA-42645** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.4.3 &lt;2.4.5*) — ストアクレジット機能が無効になっている場合に、管理者が報酬ポイントを返金できない問題を修正しました。
* **MDVA-43414** (*Adobe Commerceの場合は、Magento Open Source>=2.3.6 &lt;=2.3.7-p2*) - `inventory.reservations.updateSalabilityStatus` 数値 SKU の消費者をキューに入れます。
* **MDVA-41628** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.4.0 &lt;2.4.5*) — 新しいモジュールが追加されると、既存の制限付き管理者ユーザーが新しいリソースにアクセスできる問題を修正しました。
* **MDVA-43348** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.4.2 &lt;2.4.5*) — ギフトカードのGraphQLリクエストが `gift_card_options` 次を含む *uid*.
* **MDVA-39546** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.3.0 &lt;2.4.5*) — 編集中に、ステージング更新の開始日を現在の日付よりも前の日付に設定できる問題を修正しました。
* **MDVA-42950** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.3.0 &lt;2.4.5*) — 製品ページでビデオが再生されない問題を修正しました。
* **MDVA-42689** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.3.0 &lt;2.4.4*) - Adobe Commerceが *整合性制約違反* 読み込み中に製品カテゴリを更新中にエラーが発生しました。
* **MDVA-41229** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.3.0 &lt;2.4.5*) — 設定可能な製品の読み込み後に、バックエンドで使用可能な画像がフロントエンドに表示されない問題を修正しました。
* **MDVA-43731** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.4.3 &lt;2.4.4*) - *シノニムを検索* が *一致する最小キーワード数*.
* **MDVA-43232** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.3.4 &lt;2.4.5*) — で製品を並べ替える際に発生していた問題を修正しました [!DNL Visual Merchandiser] 「By Special Price To Bottom/Top」は、カテゴリの保存中にエラーを引き起こします。
* **MDVA-43726** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.3.3 &lt;2.4.3*) — 部分的なインデックス再作成の後、ストアレベルの属性一致に基づくカタログ価格ルールが適用に失敗する問題を修正しました。
* 更新済みのパッチ：MDVA-36464、MDVA-37478、MDVA-38608。
* のパッチメタデータを追加しました。 [!DNL Site-Wide Analysis Tool].

## v1.1.11 {#v1-1-11}

* **MDVA-42790** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.4.3 &lt;2.4.5*) - REST API を使用して特定の Web サイトで製品価格属性を更新できない問題を修正しました。
* **MDVA-41350** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.3.0 &lt;2.4.5*) — アクセスが制限された管理者ユーザーが役割範囲外の製品を SKU 別に順に追加した場合に例外が発生する問題を修正しました。
* **MDVA-42269** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.4.3-p1 &lt;2.4.5*) - *TypeError:strtotime() は、パラメータ 1 が文字列である必要があり、null は与えられます* エラー。
* **MDVA-40830** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.3.0 &lt;2.4.5*) — 注文の配置中にストアのクレジットが複数回適用される問題を修正しました。
* **MDVA-42237** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.4.2 &lt;2.4.5*) — 構成可能な製品の特別価格がサブ製品価格の変更後に更新されない問題を修正しました。
* **MDVA-42520** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.4.3 &lt;2.4.4*) - *国境を越えた貿易を有効にする* が使用されます。
* 更新済みのパッチ：MDVA-27239、MDVA-39305、MDVA-41236、MDVA-36832。
* 非推奨のパッチ：MDVA-37725.

## v1.1.10 {#v1-1-10}

* **MDVA-38728** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.3.2 &lt;2.4.5*) — 一括属性の更新で、変更後にデフォルトストアの URL の書き換えが作成される問題を修正しました。 *製品の表示*.
* **MDVA-43091** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.4.3 &lt;2.4.4*) — バックエンドで管理者からバンドル製品を注文するとエラーが発生する問題を修正しました *この製品には小数を使用できません*.
* **MDVA-40816** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.3.0 &lt;2.4.5*) — 関連する製品ルールに、ルール条件で定義されていないカテゴリの製品が表示される問題を修正しました。
* **MDVA-41305** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.4.2 &lt;2.4.5*) - GraphQL mutation がウィッシュリストに追加した後、設定可能な製品オプションを返さない問題を修正しました。
* **MDVA-39181** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.4.1 &lt;2.4.5*) — 関連する製品ルールに、ルール条件で定義されていないカテゴリの製品が表示される問題を修正しました。
* **MDVA-42584** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.4.2 &lt;2.4.3*) - 「読み込み」または「API」を使用して数量と在庫のステータスを変更した後に、バックエンドの設定可能な在庫のステータスが更新されない問題を修正しました。
* **MDVA-40175** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.4.0 &lt;2.4.3*) - *クリックして発送方法を変更* では、並べ替え時に、管理で発送方法を選択するラジオボタンは表示されません。
* **MDVA-42768** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.3.4 &lt;2.4.5*) — の場合に設定可能な製品が通常価格を 0 と表示される問題を修正しました。 *在庫切れの表示* はい。
* **MDVA-43201** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.4.2 &lt;2.4.4.4*) — 特定のロケールで DOB 属性を使用した場合に顧客のログインでエラーが発生する問題を修正しました。
* 更新済みのパッチ：MDVA-35092、MDVA-33970。

## v1.1.9 {#v1-1-9}

* **MDVA-38346** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.3.0 &lt;2.4.5*) - Adobe Commerceのタイムゾーンがローカル環境のタイムゾーンと異なる場合に、日付フィルターが正しく機能しない問題を修正しました。
* **MDVA-42657** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.4.1 &lt;2.4.5*) — 管理者ユーザーが顧客セグメント条件でカテゴリを選択できない問題を修正しました。
* **MDVA-42806** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.4.2 &lt;2.4.4.4*) - *新しい会社の登録* REST API を使用して既存の会社が更新されるたびに、電子メールが送信されます。
* **MDVA-37984** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.4.1 &lt;2.4.5*) - [!DNL Visual Merchandiser] *ルールで製品を照合* の機能では、ステージングアップデートで製品を正しくフィルタリングできません。
* **MDVA-40488** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.4.2 &lt;2.4.4.4*) — 在庫切れの子製品を持つ設定可能な製品が正しい価格範囲で表示されない問題を修正しました。
* **MDVA-42507** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.4.3 &lt;2.4.5*) — 買い物かごルールにステージング更新を適用した後にフルページキャッシュがクリーンアップされる問題を修正しました。
* **MDVA-39163** (*Adobe CommerceとMagento Open Sourceの場合 >=2.3.5 &lt;2.4.5*) — 新しいユーザーが登録されている場合に発送方法が使用できず、買い物かご内の製品がゲストセッションから取得される問題を修正しました。
* **MDVA-38626** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.3.3 &lt;2.4.5*) — 管理者ユーザーが [!DNL PayPal Payflow Pro] 支払い。
* **MDVA-38666** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.3.2 &lt;2.3.6*) — 管理者ユーザーが顧客の買い物かご内の設定可能な製品オプションを変更できない問題を修正しました。
* **MDVA-38526** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.4.1 &lt;2.4.4*) — 管理者ユーザーが [!DNL Site-Wide Analysis tool].
* 更新済みのパッチ：MDVA-40101.

## v1.1.8 {#v1-1-8}

* **MDVA-41215** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.3.0 &lt;2.4.4*) — ユーザーが *mage-messages* cookie を設定します（既に存在するが、新しいメッセージは存在しない場合）。
* **MDVA-41139** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.4.3 &lt;2.4.4*) — いずれかのソースに対して単純な製品の qty=0 の場合に、製品の読み込み後に設定可能な製品が在庫切れになる問題を修正しました。
* **MDVA-42326** (*Adobe Commerceの場合は、Magento Open Source>=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*) — 永続的な買い物かごが有効になっている場合でも、セッションのタイムアウト後に顧客がチェックアウト時にエラーが発生する問題を修正しました。
* **MDVA-42341** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.4.2 &lt;2.4.4.4*) - `categoryList` リクエストに Store ヘッダーがある場合、GraphQLクエリは結果をフィルタリングしません。
* **MDVA-38393** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.3.0 &lt;2.4.4*) — 設定可能な製品の単純な製品名が変更されると、カタログルールが機能しなくなる問題を修正しました。
* **MDVA-39153** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.4.2 &lt;2.4.4.4*) — 管理での並べ替え中に割引額が正しく計算されない問題を修正しました。
* 更新済みのパッチ：MDVA-28993、MDVA-41061、MDVA-35984。

## v1.1.7 {#v1-1-7}

* **MDVA-39711** (*Adobe CommerceとMagento Open Sourceの場合 >=2.3.0 &lt;2.4.3*) - Web サイトを削除した後、管理者ユーザーが顧客のグリッドにアクセスできない問題を修正しました。
* **MDVA-40311** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.4.2-p2 &lt;2.4.4.4*) — 管理者ユーザーがエラーメッセージを受け取る問題を修正しました *無効なセキュリティまたはフォームキーです。 ページを更新してください* 管理者にログインした後、カスタム管理パスが設定され、秘密鍵が有効になっている場合。
* **MDVA-41631** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.4.1 &lt;2.4.4*) — オプションを使用せずに注文情報を取得しようとするとエラーが発生する問題を修正しました *電話* GraphQLを通じて価値を創出
* **MDVA-27239** (*Adobe CommerceとMagento Open Sourceの場合 >=2.3.0 &lt;2.3.6*) — クロス販売製品が表示されない問題を修正しました。
* 更新済みのパッチ：MDVA-37068、MDVA-35254、MDVA-41164、MDVA-37916、MDVA-37478、MDVA-34551、MDVA-31791。

## v1.1.6 {#v1-1-6}

* **MDVA-40550** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.3.5 &lt;2.4.4*) — インデックス再作成中にフロントエンドで製品が見つからない問題を修正しました。
* **MDVA-40120** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.4.1 &lt;2.4.4*) - GraphQLでの DESC/ASC による並べ替えが、関連性や価格が同じ製品で動作しない問題を修正しました。
* **MDVA-41399** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.3.3 &lt;2.4.2*) — 管理者ユーザーが *買い物かごを管理* 顧客がウィッシュリストに製品を追加した場合は、ページを表示します。
* **MDVA-40609** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.4.2 &lt;2.4.3*) — 無効になっている製品データが `cataloginventory_stock_status` インデックステーブル、無効な製品数量が正しく表示されていません。
* **MDVA-39031** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.4.1 &lt;2.4.4*) - GraphQLを使用して買い物かごに製品を追加できる（その製品がターゲット Web サイトに割り当てられていない場合でも）問題を修正しました。
* **MDVA-41597** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.4.2 &lt;2.4.4.4*) - GraphQLを使用して複数の設定可能な製品を買い物かごに追加するとエラーが発生する問題を修正しました。
* **MDVA-27456** (*Adobe CommerceとMagento Open Sourceの場合 >=2.3.5 &lt;2.3.7*) — ユーザーがを読み込もうとするとエラーが発生する問題を修正しました [!DNL Swagger].
* **MDVA-32776** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.4.0 &lt;2.4.2*) — 注文がおこなわれても出荷されない場合に在庫ステータスが更新されない問題を修正しました。
* **MDVA-30862** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.3.4 &lt;2.4.0*) — 印刷されたPDF請求書の注文日が正しくない問題を修正しました。
* のインデックスページを改善しました。 [!DNL Quality Patch Tool]. 次の用途に便利な検索とフィルターを追加しました。 [!DNL quality patches] を更新しました。
* 更新済みのパッチ：MDVA-33382、MDVA-39482。

## v1.1.5 {#v1-1-5}

* **MDVA-41236** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.3.0 &lt;2.4.4*) - 「終了日」が以前に削除されている場合に、製品の新しいスケジュール済み更新を作成したり、既存のスケジュール済み更新を編集したりできない問題を修正しました。
* **MDVA-41046** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.3.0 &lt;2.4.4*) — カスタムオプションを持つシンプルな製品を、設定可能な、またはグループ化された製品に割り当てる際に使用できる問題を修正しました。
* **MDVA-40545** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.3.0 &lt;2.4.4*) — 同じページに複数のノードが存在する場合でも、ページの最初のノードのみが取得される問題を修正しました。
* **MDVA-41164** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.4.2 &lt;2.4.3-p1*) — 管理者ユーザーがファイルまたは画像タイプのカスタム顧客属性を持つ会社を保存または編集できない問題を修正しました。
* **MDVA-39229** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.3.0 &lt;2.4.4*) — カタログルール「Staging Update start time」の更新後に次のエラーが発生する問題を修正しました。 *Cron ジョブ staging_synchronize_entities_period にエラーがあります：アクティブな更新を削除できません。*
* **MDVA-40619** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.3.0 &lt;2.4.4*) - CMS ページ階層を変更すると、CMS ページでインライン編集を試みると 500 エラーが発生する問題を修正しました。
* **MDVA-41061** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.4.2 &lt;2.4.3*) — 製品が管理者から保存されると在庫ステータスがステータスにリセットされる問題を修正しました。
* **MDVA-31763** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.3.0 &lt;2.4.4*) — 手動でインデックスを再作成するまで、カタログ価格ルールが元に戻される（または適用されない）問題を修正しました。
* **MDVA-37748** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.4.2 &lt;2.4.3*) - GraphQLクエリが共有カタログに割り当てられていない製品を返す問題を修正しました。

## v1.1.4 {#v1-1-4}

* **MDVA-40399** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.4.2 &lt;2.4.4.4*) — 同じ注文の一部の請求書を REST API で同時に作成できない問題を修正しました。
* **MDVA-40101** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.3.2 &lt;2.4.0*) — を使用して注文が正常に配置された後に、ミニカートから項目が削除されない問題を修正しました。 [!DNL PayPal Express] チェックアウト。
* **MDVA-40401** (*Adobe Commerceの場合は、Magento Open Source>=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*) — 注文の配置に失敗した場合でもクーポン使用額が変更される問題を修正しました。
* **MDVA-40537** (*Adobe CommerceおよびMagento Open Sourceの場合、>=2.3.4 &lt;=2.4.0-p1*) — 同じ URL キーを持つ複数の CMS ページが存在する場合に、ストア表示の作成時にエラーが発生する問題を修正しました。
* **MDVA-37725** (*Adobe CommerceおよびMagento Open Sourceの場合、>=2.3.0 &lt;=2.4.3-p1*) — デフォルト以外の Web サイトから送信される非同期注文 E メールに、デフォルト Web サイトのロゴ URL が含まれる問題を修正しました。
* **MDVA-39482** (*Adobe Commerceの場合は、Magento Open Source>=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*) — バックオーダーが有効な場合に「0」の数量でインポートされた製品が在庫切れになる問題を修正しました。
* **MDVA-40435** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.3.4 &lt;2.4.4*) - GraphQLを介して動的な価格でバンドル製品の割引が正しくない問題を修正しました。
* **MC-42528** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.4.3 &lt;=2.4.3-p1*) - `categoryList` GraphQLクエリは、割り当て済みカテゴリと未割り当てカテゴリの両方を返します。
* **MDVA-29400** (*Adobe Commerceの場合はMagento Open Source>=2.3.0 &lt;=2.3.7-p1 || >=2.4.0 &lt;=2.4.0-p1*) — での重複した注文の問題を修正しました。 [!DNL PayPal Express Checkout].
* **MDVA-26005** (*Adobe Commerceの場合はMagento Open Source>=2.3.4 &lt;=2.3.5-p2*) — 買い物かご価格ルールの条件で、カテゴリツリー内のカテゴリを選択できない問題を修正しました。
* **MDVA-25631** (*Adobe Commerceの場合はMagento Open Source>=2.3.3 &lt;=2.3.5-p2*)：多数の顧客を含む顧客セグメントの編集と保存のパフォーマンスが向上します。

## v1.1.3 {#v1-1-3}

* **MDVA-40262** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.4.2 &lt;2.4.4.4*) — 管理者による一般的な検索用語にGraphQLの検索クエリが表示されない問題を修正しました。
* **MDVA-40601** (*Adobe Commerceの場合はMagento Open Source>=2.3.1 &lt;=2.4.2-p2*) — ユーザーが、GraphQLを通じてスケジュールされた更新によって変更されたカテゴリに関する情報を取得しようとするとエラーが発生する問題を修正しました。
* **MDVA-37234** (*Adobe CommerceとMagento Open Sourceの場合 >=2.3.5 &lt;2.4.0 || >=2.4.1 &lt;=2.4.2-p2*) — 同じ SKU に対して品目を買い物かごに複数回追加すると、同じ買い物かご ID に対して行項目が重複して作成される問題を修正しました。
* **MDVA-33606** (*Adobe CommerceとMagento Open Sourceの場合は >=2.4.1 &lt;=2.4.2-p2*) — ユーザーが *一意の制約違反* 階層に割り当てられた CMS ページを保存中にエラーが発生しました。
* **MDVA-31590** (*Adobe CommerceおよびMagento Open Sourceの場合、>=2.4.0 &lt;=2.4.1-p1*) - MySQL 非同期キューを使用して属性を一括更新できない問題を修正しました。
* **MDVA-36309** (*Adobe CommerceとMagento Open Sourceの場合 >=2.4.2 &lt;=2.4.2-p2*) — 管理グリッドで属性による製品検索が遅くなる問題を修正しました。

## v1.1.2 {#v1-1-2}

* **MDVA-38929** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.3.0 &lt;2.4.4*) — 注文が店舗クレジットから支払われると、FPT の請求書に誤った総計が表示される問題を修正しました。
* **MDVA-37364** (*Adobe CommerceとMagento Open Sourceの場合 >=2.4.0 &lt;=2.4.3*) — 日付タイプのカスタム顧客属性が顧客のグリッド UI を壊す問題を修正しました。
* **MDVA-39195** (*Adobe CommerceとMagento Open Sourceの場合 >=2.4.2 &lt;=2.4.2-p2*) - *買い物かごに追加* 買い物かごにリダイレクトが有効になっている場合に、カテゴリページでボタンが非アクティブになっていた問題を修正しました。
* **MDVA-37115** (*Adobe CommerceとMagento Open Sourceの場合 >=2.4.2 &lt;=2.4.2-p2*) — 不要な *0 のみ左* 「設定可能な製品」ページに通知が表示されます。
* **MDVA-39521** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.4.0 &lt;2.4.4*) — ユーザーがGraphQLを介して空の電話番号で買い物かごの配送先住所を設定できない問題を修正しました。
* **MDVA-39384** (*Adobe CommerceとMagento Open Sourceの場合 >=2.3.1 &lt;=2.3.6 || >=2.4.1 &lt;=2.4.3*) — 会社ユーザーのカスタム顧客属性が保存されない問題を修正しました。
* **MDVA-39043** (*Adobe CommerceとMagento Open Sourceの場合 >=2.3.4 &lt;=2.4.3*) — 制限付きアクセス権を持つ管理者ユーザーが *製品* ウィジェットを CMS ページに追加します。
* **MDVA-39966** (*Adobe Commerceの場合はMagento Open Source>=2.3.0 &lt;=2.3.5-p2 || >=2.4.0 &lt;=2.4.0-p1*) — 誤ったロケールのデプロイに関する問題を修正しました。
* **MDVA-38852** (*Adobe Commerceの場合はMagento Open Source>=2.3.0 &lt;=2.3.5-p2*) — 複数の並列注文がある場合にパフォーマンスが大幅に低下する更新に対して、カタログ在庫がデザイン別にテーブルをロックする問題を修正しました。
* **MDVA-39986** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.4.1 &lt;2.4.3*) — ユーザーが Safari ブラウザーを使用してMacOSの管理画面で注文できない問題を修正しました。
* **MDVA-38447** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.4.2 &lt;2.4.4.4*) — 次の 2 つの問題を修正しました。ここで、 *個別には表示されません* 設定可能な子製品は、GraphQL応答で返され、カテゴリフィルターを使用してGraphQL製品クエリ用の MySQL クエリを最適化します。
* **MDVA-40134** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.4.2 &lt;2.4.3*) - 「共有カタログ」が有効な場合にGraphQLが関連製品を返さない問題を修正しました。
* **MDVA-39935** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.4.1 &lt;2.4.4*) - GraphQLが Web サイトレベルで無効になっている設定可能な子製品を返す問題を修正しました。

## v1.1.1 {#v1-1-1}

* **MDVA-36021** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.4.0 &lt;2.4.4*) - *メンバー関数 getId() の呼び出し* エラーが管理者の注文の詳細ページに表示されます。
* **MDVA-34948** (*Adobe Commerceの場合はMagento Open Source>=2.3.6 &lt;=2.3.6-p1 || >=2.4.0 &lt;=2.4.0-p1*) — などの長時間実行クエリに関する問題を修正します。 `GET_LOCK`.
* **MDVA-39305** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.4.0 &lt;=2.4.2-p1*) — 有効なGoogle ReCaptcha を使用してログインできない問題を修正しました。
* **MDVA-37897** (*Adobe CommerceおよびMagento Open Sourceの場合 >=2.3.0 &lt;2.4.4*) — 顧客が最近表示されたウィジェットのオプションを使用して製品を追加しようとした際に、誤ったリダイレクトに関する問題を修正しました。

## v1.1.0 {#v1-1-0}

* ユーザーエクスペリエンスを向上させ、必要なパッチを容易にお客様に検索できるように、パッチカテゴリを導入しました。
* この `patches.json` ファイルの名前はに変更されました。 `support-patches.json`.
* **MDVA-38799** (*Adobe Commerceの場合 >=2.3.0 &lt;2.4.3.3*) — ステージングアップデートを作成した後にダウンロード可能な製品が保存されない問題を修正しました。
* **MDVA-37592** (*Adobe Commerceの場合 >=2.3.6 &lt;=2.4.2-p1*) — 価格で並べ替えた場合に、共有カタログに価格が割り当てられていない製品で正しく機能しない問題を修正しました。
* **MDVA-38827** (*Adobe Commerceの場合 >=2.3.3-p1 &lt;2.4.4.4*) — お客様がエラーメッセージを含む注文出荷 E メールを受け取る問題を修正しました。

## v1.0.26 {#v1-0-26}

* **MDVA-38468** (*Adobe Commerceの場合 >=2.3.2 &lt;=2.3.5-p2*) - CMS ページを保存する際のエラーを修正します。 *同じ ID PAGE_ID の項目が既に存在します*.
* **MDVA-34680** (*Adobe Commerceの場合 >=2.3.6 &lt;=2.3.7 || >=2.4.1 &lt;2.4.3*) — 顧客アカウントの作成時間が顧客グリッドで正しくフィルタリングされない問題を修正しました。
* **MDVA-37068** (*Adobe Commerceの場合 >=2.3.1 &lt;2.4.4.4*) — 買い物かごに仮想製品のみが入っている場合に誤った税率が表示される問題を修正しました。
* **MDVA-38608** (*Adobe Commerceの場合 >=2.3.0 &lt;2.4.3.3*) — インデックス再作成が正常に完了しない場合に一時テーブルが削除されない問題を修正しました。
* **MDVA-38308** (*Adobe Commerceの場合 >=2.3.5 &lt;=2.3.6-p1 || >=2.4.0 &lt;=2.4.1-p1 || >=2.4.2 &lt;2.4.4*) - [!DNL Vimeo] 製品に関するビデオ。

## v1.0.25 {#v1-0-25}

* **MDVA-37916** (*Adobe Commerceの場合 >=2.3.6 &lt;2.4.3.3*) - [!DNL Paypal Payment Advanced] メソッド。
* **MDVA-37082** (*Adobe Commerceの場合 >=2.3.0 &lt;2.4.3.3*) — グループ化された製品のカスタム在庫を保存すると、フロントエンドに製品が在庫切れになる問題を修正しました。
* **MDVA-36572** (*Adobe Commerceの場合 >=2.3.5 &lt;2.4.3.3*) — クレジットメモの更新により、データベース内で重複する製品予約の更新がおこなわれなくなった問題を修正しました。
* **MDVA-38132** (*Adobe Commerceの場合 >=2.3.3 &lt;2.4.3.3*) - *リダイレクトが多すぎます* エラー。
* **MDVA-38270** (*Adobe Commerceの場合 >=2.4.1 &lt;2.4.3.3*) - GraphQLでの注文合計にギフトカード情報が表示されない問題を修正しました。

## v1.0.24 {#v1-0-24}

* **MDVA-37779** (*Adobe Commerceの場合 >=2.4.2 &lt;=2.4.4.4*) - Web サイト ID がストア ID と一致しない場合に、GraphQLを介して設定可能な製品を買い物かごに追加する際に発生する問題を修正しました。
* **MDVA-36832** (*Adobe Commerceの場合 >=2.3.4 &lt;=2.4.2-p1*) — 表示の幅が 768px の場合にページで画像が重複する問題を修正しました。
* **MDVA-37874** (*Adobe Commerceの場合 >=2.3.6 &lt;=2.3.7 || >=2.4.1 &lt;=2.4.2-p1*) - *買い物かご全体の固定割引額* が複数のオプションを含むバンドル製品に誤って適用される問題を修正しました。
* **MDVA-37913** (*Adobe Commerceの場合は 2.3.0 &lt;=2.4.0-p1*) — ダウンロード可能な製品が API を介して更新されるとダウンロード可能なリンクが表示されなくなる問題を修正しました。
* **MDVA-34330** (*Adobe Commerceの場合 >=2.3.1 &lt;=2.4.2-p1*) - 「注文」グリッド内の注文が管理者タイムゾーンに従ってフィルタリングされない問題を修正しました。

## v1.0.23 {#v1-0-23}

* **MDVA-37478** (*Adobe Commerceの場合 >=2.3.0 &lt;=2.3.7*) - Adobe Commerceで *アカウントでの支払い* REST API を介した支払い方法。
* **MDVA-37362** (*Adobe Commerceの場合 >=2.3.4 &lt;=2.4.2-p1*) - GraphQLの応答で設定可能な製品オプション値とバリアント属性値が空になっていた問題を修正しました。
* **MDVA-37288** (*(Adobe Commerce 2.4.2 用 )*) - GraphQLのリクエスト後に間違った階層価格が返される問題を修正しました。
* **MDVA-37225** (*Adobe Commerceの場合 >=2.4.1 &lt;=2.4.2-p1*) — 読み込んだ SKU に整数値がある場合に、すばやい注文作成中にアップロードプロセスが停止する問題を修正しました。
* **MDVA-37224** (*Adobe Commerceの場合 >=2.3.3 &lt;=2.4.2-p1*) — 顧客がとの交渉可能な見積もりに対して支払いを行えない問題を修正しました。 [!DNL PayFlow Pro] を別の製品と共に買い物かごに入れます。
* **MDVA-36286** (*Adobe Commerceの場合 >=2.3.6 &lt;=2.4.2-p1*) — 同じ SKU がサブカテゴリ内で異なる位置にある場合に Page Builder 製品ウィジェットのプレビューが壊れる問題を修正しました。
* **MDVA-30186** (*Adobe Commerceの場合は、2.3.4 &lt;=2.3.5-p2, >=2.4.0 &lt;=2.4.0-p1, >=2.4.2 &lt;=2.4.2.2-p1*) - GraphQL応答で属性オプションが、属性項目数ではなくオプション値で並べ替えられる問題を修正しました。

## v1.0.22 {#v1-0-22}

* **MDVA-36718** (*Adobe Commerceの場合 >=2.3.0 &lt;=2.4.2*) - API を使用して変更した後も古いカスタムオプションが残る問題を修正しました。
* **MDVA-35773** (*Adobe Commerceの場合 >=2.3.6 &lt;=2.3.6-p1 || >=2.4.1 &lt;=2.4.2*) - 100%割引の注文に対して、請求書に総計がゼロと表示されない問題を修正しました。
* **MDVA-36833** (*(Adobe Commerce 2.4.2 用 )*) — 共有カタログから一部の製品を除外した後、検索結果で 1 ページあたりの製品の数がランダムに表示される問題を修正しました。
* **MDVA-37182** (*Adobe Commerceの場合 >=2.4.1 &lt;=2.4.2*) — 両方の [!DNL Elasticsearch] バージョン 6 およびバージョン 7。
* **MDVA-36253** (*Adobe Commerceの場合 >=2.4.0 &lt;=2.4.1-p1*) — 項目の削除後にミニカートに間違った小計が表示される問題を修正しました。
* **MDVA-36853** (*(Adobe Commerce 2.4.2 用 )*) — 大きなメディアギャラリーを読み込む際に画像が表示されない問題を修正しました。

## v1.0.21 {#v1-0-21}

* **MDVA-34665** (*Adobe Commerceの場合 >=2.3.4 &lt;=2.3.4-p2*) — カテゴリページにバンドルされている製品が表示されない問題を修正しました。
* **MDVA-36615** (*(Adobe Commerce 2.4.2 用 )*) — 管理製品グリッドでの製品数が正しくない問題を修正しました。
* **MDVA-36464** (*Adobe Commerceの場合 >=2.4.0 &lt;=2.4.2*) — 電子メール通知設定がストア表示レベルで機能しない問題を修正しました。
* **MDVA-36138** (*(Adobe Commerce ^2.3.2 用 )*) — 買い物かご内のすべての品目が無料配送カートルールの対象にならない場合に、送料が調整されず、完全な配送料が顧客に表示される問題を修正しました。
* **MDVA-36424** (*Adobe Commerceの場合 >=2.3.0 &lt;=2.3.3-p1 || >=2.0.0 &lt;2.2.0*) — バックエンドのベース URL がストアフロントのベース URL と異なる場合、コンテンツを繰り返し編集すると、ページビルダーの要素に添付されたメディア画像が消える問題を修正しました。
* **MDVA-35984** (*(Adobe Commerce ^2.4.0 用 )*) — 同じ製品に対して複数の同時出荷を作成した後に、誤った製品数と販売可能数量が発生する問題を修正しました。

## v1.0.20 {#v1-0-20}

* **MDVA-36170** (*Adobe Commerceの場合 >=2.3.4 &lt;2.4.2.2*) — カテゴリキャッシュタグを使用してGraphQLクエリがキャッシュされない問題を修正しました。
* **MDVA-33168** (*Adobe Commerceの場合 >=2.3.3 &lt;2.4.2.2*) - API を使用して製品属性を更新する際に、他のすべての属性が空の値に変更される問題を修正しました。
* **MDVA-19640** (*(Adobe Commerceの場合 )=2.3.0 以降*) - [!DNL Advanced Reporting] にはデータが表示されていません。
* **MDVA-11189** (*Adobe Commerceの場合 >=2.3.0 &lt;2.3.5>*) - CSV ファイルを読み込んで製品在庫を更新した後、 `cataloginventory_stock` テーブルが削除されます。
* **MDVA-26639** (*Adobe Commerceの場合 >=2.3.3-p1 &lt;2.3.6.6*) — 新しい注文確認 E メールテンプレートが作成された場合に、注文の項目が注文メールに含まれない問題を修正しました。
* **MDVA-15546** (*(Adobe Commerceの場合 )=2.3.0 以降*) — 注文 a を作成した後に発生していた問題を修正しました *句があいまいな列 entity_id* エラーが例外ログに表示されます。
* **MDVA-21095** (*Adobe Commerceの場合 >=2.3.0 &lt;2.3.5>*) — クエリ時の問題を修正します `INSERT INTO search_tmp` 一括属性値の更新後には終了しません。
* **MDVA-23845** (*Adobe Commerceの場合 >=2.3.2-p2 &lt;2.3.5.5*) - JavaScript の縮小を有効にした後、電子メールテンプレートをプレビューできない問題を修正しました。
* **MDVA-22026** (*Adobe Commerceの場合 >=2.3.2 &lt;2.3.4>*) - CSV ファイルから製品を読み込むと、外部 URL からの画像が含まれて失敗する問題を修正しました。
* **MDVA-22383** (*Adobe Commerceの場合 >=2.3.0 &lt;2.3.4>*) — 製品の保存に時間がかかり、ページが壊れる問題を修正しました。
* **MC-41359** (*Adobe Commerceの場合 >=2.3.6-p1 &lt;2.3.7, >=2.4.2 &lt;2.4.3.3*) - SameSite cookie パラメーターの設定が正しくない問題を修正しました。

## v1.0.19 {#v1-0-19}

* **MDVA-33614** (*(Adobe Commerce 2.4.1 用 )*) - Page Builder で次のエラーがスローされる問題を修正しました。 *Page Builder の開始中にエラーが発生しました。 テクニカルサポートの担当者にお問い合わせください。*
* **MDVA-35356** (*Adobe Commerceの場合 >=2.3.0 &lt;2.4.3.3*) — 一部請求済みの注文のキャンセル後に、間違った店舗クレジット返却の問題を修正します。
* **MDVA-33289** (*Adobe Commerceの場合 >=2.4.0 &lt;2.4.3.3*) — チェックアウト時に生の JavaScript コードが請求先住所 UI に表示される問題を修正しました。 [!DNL Google Tag Manager] が有効になっている。
* **MDVA-35982** (*Adobe Commerceの場合 >=2.3.0 &lt;2.4.3.3*) — 特定の Web サイトに限定された管理者ユーザーが、同じ Web サイトに配置された注文の出荷を作成できない問題を修正しました。
* **MDVA-35155** (*Adobe Commerceの場合 >=2.3.0 &lt;2.3.6>*) — オプションタイトルが変更された場合にバンドル製品を購入できない問題を修正しました。
* **MDVA-35910** (*Adobe Commerceの場合 >=2.4.1 &lt;2.4.3.3*) - 「顧客としてログイン」機能を無効にした後、新しい顧客アカウントを作成できない問題を修正しました。
* **MDVA-34474** (*Adobe Commerceの場合 >=2.3.0 &lt;2.4.3.3*) - API を使用して製品を購買依頼リストに追加する際の問題を修正しました。
* **MDVA-34591** (*Adobe Commerceの場合 >=2.3.0 &lt;2.4.3.3*) — 買い物かごのルールの割引の計算が正しくない問題を修正しました。 *最大数量割引の適用先* および *割引数量ステップ（購買 X）*.
* **MDVA-33704** (*Adobe Commerceの場合 >=2.4.0 &lt;2.4.3.3*) - *店舗でのピックアップ* 配送オプションが表示されませんが、使用可能に設定されています。
* **MDVA-34928** (*Adobe Commerceの場合 >=2.3.5 &lt;2.3.5-p2>*) — ストアクレジットが支払いから削除された後、ページローダーが無期限に表示される問題を修正しました。
* **MDVA-35254** (*Adobe Commerceの場合 >=2.3.1 &lt;2.4.3.3*) — チェックアウト時の CAPTCHA の問題を修正しました。
* **MDVA-35569** (*Adobe Commerceの場合 >=2.3.4 &lt;2.4.2.2*) - *固定製品税* 状態が指定された場合に、GraphQL応答でフィールドに値が入力されない。
* **MDVA-35847** (*Adobe Commerceの場合 >=2.4.1 &lt;2.4.3.3*) — カスタム顧客属性が使用されている場合に会社ユーザーフォームが壊れる B2B の問題を修正しました。
* **MDVA-31307** (*Adobe Commerceの場合 >=2.4.0 &lt;2.4.2.2*) - *メモリ不足* キャッシュされたブロックの動的 CSP ホワイトリスト登録に関する問題が原因で、特定のカテゴリでのエラーが発生しました。

## v1.0.18 {#v1-0-18}

* **MDVA-32655** (*Adobe Commerceの場合 >=2.3.0 &lt;2.4.3.3*) — 誤った *進行中* 正しいメッセージのステータス *完了* 消費者向けメッセージ `quoteItemCleaner` 複数の製品を削除した後。
* **MDVA-34102** (*Adobe Commerceの場合 >=2.3.0 &lt;2.4.3.3*) — 管理領域の製品グリッドおよび製品の編集ページの無効化された製品に対するデフォルト在庫の数がゼロになっているのを修正します。
* **MDVA-35286** (*Adobe Commerceの場合 >=2.4.0 &lt;2.4.2.2*) — 顧客が買い物かごに製品をバンドルし、複数のアドレスのチェックアウトからオンページチェックアウトに切り替えた場合にエラーが発生する問題を修正しました。
* **MDVA-35312** (*Adobe Commerceの場合 >=2.4.1-p1 &lt;2.4.2.2*) — 空のGraphQLリクエストの場合の応答コード 500 を修正しました。
* **MDVA-34189** (*Adobe Commerceの場合 >=2.3.4 &lt;2.4.3.3*) - 503 の最初のバイトのタイムアウトを修正しました。 [!DNL Visual Merchandiser] は、管理カテゴリページの読み込み時にクエリを実行します。
* **MDVA-34695** (*Adobe Commerceの場合 >=2.3.0 &lt;2.4.1*) — 負の修正 `children_count` カテゴリの削除後。

## v1.0.17 {#v1-0-17}

* **MDVA-34012** (*Adobe Commerceの場合 >=2.3.1 &lt;2.4.3.3*) - *デフォルト値を使用* スケジュールされた変更が適用された後、チェックボックスがオフになります。 スケジュールされた変更が有効にならないと、問題が表示されます。
* **MDVA-35064** (*Adobe Commerceの場合 >=2.3.3 &lt;2.4.3.3*) - API を使用して作成された設定可能な製品で URL の書き換えが生成されない問題を修正しました。
* **MDVA-34943** (*Adobe Commerceの場合 >=2.3.0 &lt;2.4.2.2*) — 以前に入力された SKU をクイックオーダーがキャッシュする問題を修正します。
* **MDVA-35197** (*Adobe Commerceの場合 >=2.3.5 &lt;2.4.0*) — 以前に追加した製品が在庫切れになった場合に、GraphQLを使用して買い物かごに追加するとエラーが発生する問題を修正しました。
* **MDVA-34850** (*Adobe Commerceの場合 >=2.3.1 &lt;2.4.0*) — 設定可能な製品の在庫切れオプションが、ストルーとして表示されずに表示されない問題を修正しました。
* **MDVA-34867** (*Adobe Commerceの場合 >=2.3.0 &lt;2.4.3.3*) — スケジュールされた更新に設定された条件フィールドの値が保存されない問題を修正しました。
* **MDVA-35092** (*Adobe Commerceの場合 >=2.3.5 &lt;2.4.3.3*) — ユーザーが [!DNL Vimeo] 非推奨になったビデオ [!DNL Vimeo] API

## v1.0.16 {#v1-0-16}

* **MDVA-33453** (*Adobe Commerceの場合 >=2.3.6 &lt;2.4.3.3*) — 一致する製品の価格が Web サイトごとに異なる場合に、Page Builder の製品コンテンツタイプのプレビューが壊れる問題を修正しました。
* **MDVA-32634** (*(Adobe Commerce ^2.3.1 用 )*) - `url_path` 階層内でカテゴリを移動した後も、すべてのストアに割り当てられたカテゴリの変更は変更されません。
* **MDVA-33344** (*(Adobe Commerce ^2.3.0 用 )*) — ハードコードされた問題を修正しました `rma_item` データベースの値の代わりに、エンティティのデフォルト属性セット ID が使用されます。
* **MDVA-34192** (*Adobe Commerceの場合 >=2.3.4 &lt;2.4.3.3*) - dd/mm/yyyy 形式を使用して顧客の生年月日を変更または指定できない問題を修正しました。
* **MDVA-34847** (*(Adobe Commerce ^2.3.0 用 )*) — カスタム権限を持つ管理者ユーザー向けの管理コレクションで、SQL 条件に対するストア ID タイプの整数への変換を修正しました。
* **MDVA-34886** (*(Adobe Commerce ^2.3.2 用 )*) — が *重み付け* 製品属性は検索可能として設定されます。

## v1.0.15 {#v1-0-15}

* **MDVA-33559** (*Adobe Commerceの場合 >=2.3.0 &lt;2.4.3.3*) - [!DNL PayPal Payflow Pro] 支払いがリダイレクトパラメータリスト形式エラーで失敗しました。
* **MDVA-34023** (*Adobe Commerceの場合 >=2.3.0 &lt;2.4.3.3*) — エラーが *addressId を持つエンティティはありません* は、訪問者のブラウザーにランダムに表示されます。
* **MDVA-32759** (*Adobe Commerceの場合 >=2.3.1 &lt;2.4.3、B2B 拡張機能*) — 共有カタログが既存の層の価格を削除する問題を修正しました。
* **MDVA-33482** (*(Adobe Commerce ^2.3.5 用 )*) — 部分的な請求書に対してクレジット・メモを生成すると、その部分的な請求書に対する税金ではなく、合計注文に対する税金が発生する問題を修正します。
* **MDVA-33393** (*Adobe Commerceの場合 >=2.3.0 &lt;2.4.2.2*) — エラーを修正します。 *指定された countryId が存在しません*.
* **MDVA-33632** (*Adobe Commerceの場合 >=2.3.0 &lt;2.3.7>*) — 例外メッセージの場所を修正します。 *この製品は在庫切れです* 在庫切れの製品を再注文しようとすると、が管理者ユーザーに表示されるようになりました。
* **MDVA-34469** (*Adobe Commerceの場合 >=2.4.1 &lt;2.4.2.2*) — 複数のストア表示を使用している場合に、顧客の買い物かご上のGraphQLの突然変異が失敗する問題を修正しました。
* **MDVA-33976** (*Adobe Commerceの場合 >=2.3.0 &lt;2.3.7>*) — バンドル製品から 2 番目のオプションを削除した後に、ストアフロントにバンドル製品が在庫切れと表示される問題を修正しました。
* **MDVA-33894** (*(Adobe Commerceの場合 ) 2.4.0 &lt;2.4.1、B2B 拡張機能付き*) — 複数の製品や SKU の大文字と小文字の区別を追加および削除するなど、クイックオーダー機能に関する複数の問題を修正しました。
* **MDVA-27664** (*Adobe Commerceの場合 >=2.3.4 &lt;2.3.6>*) — エラーが表示される原因となる顧客登録フォームの問題を修正します。 *エラー — 生年月日を今日よりも大きくすることはできません。*
* **MDVA-33970** (*Adobe Commerceの場合 >=2.3.4 &lt;2.4.2.2*) — 価格属性の範囲が web サイトに設定されている場合に、クレジットメモに誤った通貨記号が表示される問題を修正します。
* **MDVA-33992** (*Adobe Commerceの場合 >=2.3.0 &lt;2.4.2.2*) - B2B 特別価格がチェックアウト時に正しく表示されない問題を修正しました。
* **MDVA-34100** (*(Adobe Commerceの場合 ) 2.3.4 &lt;2.4.2、B2B 拡張機能付き*) — 会社構造ページから会社アカウントを作成できない問題を修正しました。

## v1.0.14 {#v1-0-14}

* **MDVA-31969** (*Adobe Commerceの場合は 2.3.3 &lt;2.3.5, >=2.4.0 &lt;2.4.2>*) - CSV ファイルから製品を読み込んだ後に画像が重複していた問題を修正しました。
* **MDVA-33382** (*Adobe Commerceの場合 >=2.3.0 &lt;2.4.2.2*) — カテゴリから製品を削除した後にインデクサーが無効化される問題を修正しました。
* **MDVA-28511** (*Adobe Commerceの場合 >=2.3.5 &lt;2.3.6>*) — を完了できない問題を修正しました [!DNL PayPal] 「名前」フィールドに特定の文字（アクセント付き大文字など）が含まれている場合にチェックアウトします。
* **MDVA-31519** (*Adobe Commerceの場合 >=2.3.5 &lt;2.3.6>*) — サイト全体のセールスルールが使用されている場合のゲストチェックアウトでの待機タイムアウトの問題を修正しました。
* **MDVA-33281** (*Adobe Commerceの場合 >=2.3.4 &lt;2.3.6>*) - `inventory:reservation:list-inconsistencies` SKU パラメーターのタイプが正しくない問題を修正しました。
* **MDVA-24201** (*Adobe Commerceの場合 >=2.3.0 &lt;2.3.5>*) — 価格が手動で再インデックスするまで予約済み買い物かごの価格ルールを反映しない問題を修正しました。
* **MDVA-32694** (*Adobe Commerceの場合 >=2.3.0 &lt;2.3.6> || >= 2.4.0 &lt;2.4.2*) — 管理者ユーザーが、デフォルト以外のストアに関連している場合に、製品をネゴシエーション可能な見積もりに追加できない問題を修正しました。
* **MDVA-33516** (*Adobe Commerceの場合 >=2.3.0 &lt;2.3.6>*) — 購買依頼リストでバンドル製品を編集するとエラーが発生する問題を修正しました。
* **MDVA-33975** (*Adobe Commerceの場合 >=2.3.4 &lt;2.4.2.2*) - GraphQLリクエストの価格計算に関連する複数の問題を修正します。

## v1.0.13 {#v1-0-13}

* **MDVA-30858** (*Adobe Commerceの場合 >=2.3.0 &lt;2.4.2.2*) - [!DNL PayPal] 決済レポートは以下で使用できません： **レポート** > **セールス** > **[!DNL PayPal]** 予想通りの決済。
* **MCP-87** (*Adobe Commerceの場合 >=2.3.1 &lt;2.4.2.2*) — 大規模なプロファイル向けのカテゴリ製品および在庫インデクサーのインデクサー作成時間の短縮
* **MDVA-33106** (*Adobe Commerceの場合 >=2.3.0 &lt;2.4.2.2*) - Cron の実行後に再スケジュールされた製品の変更が消去される問題を修正しました `run` コマンドが実行されます。
* **MDVA-19391** (*Adobe Commerceの場合 >=2.3.0 &lt;2.3.5>*) - `analytics_collect_data` は、 `catalog_category_entity_text` 表。
* **MDVA-20376** (*Adobe Commerceの場合 >=2.3.2 &lt;2.3.4>*) - *customerId = 1 のエンティティはありません* エラー `exception.log` （注文の配置後にログインした顧客）
* **MDVA-23764** (*Adobe Commerceの場合 >=2.3.2 &lt;2.3.5>*) - `JsFooterPlugin.php` これはダイナミックブロックの表示に影響を与えます。
* **MDVA-13203** (*Adobe Commerceの場合 >=2.3.0 &lt;2.4.2.2*) - *整合性制約違反 search_tmp_ table* 完全な再インデックスの後にエラーが発生します。
* **MDVA-23426** (*Adobe Commerceの場合 >=2.3.3 &lt;2.3.5>*) - Adobe Commerceから送信される通知 E メールに空の本文が含まれ、コンテンツが添付ファイルとして追加される問題を修正しました。
* **MDVA-22150** (*Adobe Commerceの場合 >=2.3.1 &lt;2.3.4>*) — 管理画面で設定可能な製品が無効になっている場合に、買い物かごに設定可能な製品があり、クーポンが適用されているお客様がログインできない問題を修正しました。
* **MDVA-32545** (*Adobe Commerceの場合 >=2.3.0 &lt;2.4.2.2*) — 管理者からのオーダーを作成する際に請求書が自動的に送信されない問題を修正しました。
* **MDVA-32714** (*Adobe Commerceの場合 >=2.3.4 &lt;2.4.1*) — 顧客グループ価格がGraphQL製品クエリで機能しない問題を修正しました。

## v1.0.12 {#v1-0-12}

* **MDVA-31399** (*Adobe Commerceの場合 >=2.3.2 &lt;2.4.2.2*) - *小計 ( 税 )* オプションを選択して価格ルール条件を設定します。
* **MDVA-31236** (*Adobe Commerceの場合 >=2.4.0 &lt;2.4.2.2*) — カスタムリソースにアクセスできる管理者が 2FA を設定したりログインしたりできない問題を修正しました。
* **MDVA-30845** (*Adobe Commerceの場合 >=2.3.5 &lt;2.3.7>*) - *申し訳ありませんが、現時点でこの注文に使用できる見積もりはありません* UPS XML/USPS/DHL に接続できない場合、エラーが表示され、他の発送方法は使用できません。
* **MDVA-32133** (*Adobe Commerceの場合 >=2.4.0 &lt;2.4.1*) — 場合によってはメディアギャラリーがページビルダーから読み込まれない問題を修正しました。
* **MDVA-12304** (*(Adobe Commerceの場合 )=2.3.0 以降*) - cookie の最大数を 50 から 200 に増やします。
* **MDVA-32632** (*Adobe Commerceの場合 >=2.3.2 &lt;2.3.5>*) — 注文が支払いシステムに表示されるが、Adobe Commerceには表示されない問題を修正しました。
* **MDVA-32449** (*Adobe Commerceの場合 >=2.3.0 &lt;2.3.6> || 2.4.0 || >=2.4.1 &lt;2.4.2 （B2B 拡張機能を使用）*) — 注文履歴の読み込みが非常に遅い、または読み込みがまったく行われない問題を修正しました。
* **MDVA-32739** (*Adobe Commerceの場合 >=2.3.0 &lt;2.4.2.2*) — 非同期電子メール通知を有効にすると、古いセールスメールが送信される問題を修正しました。

## v1.0.11 {#v1-0-11}

* **MC-38509** (*Adobe Commerce 2.3.6 の場合、2.4.1*) - *アカウントの作成* ボタンが *新しい顧客アカウントの作成* フォーム。
* **MDVA-31006** (*Adobe Commerce 2.3.0 の場合， 2.3.1# 2.3.0 ノ場合#*) - [!DNL Paypal Express] 支払い。
* **MDVA-25602** (*(Adobe Commerce 2.3.0 用 )*) - [!DNL PayPal Payflow Pro] の支払い方法とクッキーを `SameSite=Lax` デフォルトでは、Chrome 80 ブラウザーおよび API 応答で、顧客ログインページにリダイレクトされます。

## v1.0.10 {#v1-0-10}

パッチバージョンのマイナーな修正

## v1.0.9 {#v1-0-9}

* **MDVA-31363** (*Adobe Commerceの場合 >=2.3.2 &lt;2.4.2.2*) — クーポン付きの買い物かごの価格ルールが、 *買い物かご全体の固定金額の割引* アクションが使用されます。
* **MDVA-30889** (*Adobe Commerceの場合 >=2.3.0 &lt;2.4.2.2*) — 仮想製品とシンプルな製品をオプションとしてバンドルに請求した後にエラーが発生する問題を修正しました。
* **MDVA-31791** (*Adobe Commerceの場合 >=2.3.4 &lt;2.3.5>*) — ターゲットルールまたはリンクされた製品が使用されている場合の、製品ページのパフォーマンスが向上します。
* **MDVA-31168** (*Adobe Commerceの場合 >=2.3.0 &lt;2.4.2.2*) — 製品の書き出し CSV ファイルが表示されず、メモリ割り当てエラーが発生する問題を修正しました。
* **MDVA-32313** (*Adobe Commerceの場合 >=2.3.0 &lt;2.3.4>*) — 設定可能な製品が誤った設定オプションでウィッシュリストに追加される問題を修正しました。
* **MDVA-31759** (*Adobe Commerceの場合 >=2.3.0 &lt;2.4.2.2*) — 製品が *ドロップダウン* および *textarea* CSV の読み込み時の属性値。
* **MDVA-32012** (*Adobe Commerceの場合 >=2.3.0 &lt;2.4.2.2*) — 韓国とアルゼンチンの郵便番号を検証できない問題を修正しました。
* **MDVA-31640** (*Adobe Commerceの場合 >=2.3.1 &lt;2.3.6> || >=2.4.0 &lt;2.4.1*) — 特別な価格を REST API で更新できない問題を修正しました。
* **MDVA-28651** (*Adobe Commerceの場合 >=2.3.0 &lt;2.3.6> || >2.4.0 （B2B 拡張機能を使用）*) - REST API を介してネゴシエーション可能な引用符を読み込む際にパフォーマンスの問題が発生する問題を修正しました。

## v1.0.8 {#v1-0-8}

* **MDVA-31242** (*(Adobe Commerceの場合 ) 2.3.0 &lt;2.4.1、B2B 拡張機能付き*) — クレジットメモグリッドに誤った通貨記号が表示される問題を修正しました。
* **MDVA-31295** (*Adobe Commerceの場合 >=2.3.0 &lt;2.4.2.2*) — 一部の注文が完了し、項目に課税がかかった場合に報酬ポイントが計算されない問題を修正しました。
* **MDVA-30112** (*Adobe Commerceの場合 >=2.3.4 &lt;2.4.2.2*) — 注文件数が *束サイズ* 値を指定する場合、Adobe Commerceは *保留中* のステータスが不整合です。
* **MDVA-31150** (*Adobe Commerceの場合 >=2.3.0 &lt;2.4.2.2*) — 請求書が Rest API 呼び出しによって転記され、注文が一部店舗クレジットおよびギフトカードアカウントによって支払われた場合に、GETの Invoice Rest API 呼び出しによって店舗クレジットおよびギフトカード残高が返されない問題を修正しました。
* **MDVA-30963** (*Adobe Commerceの場合 >=2.3.2 &lt;2.4.2.2*) — 製品のフィルタリング結果がに指定された値のみを含む問題を修正しました。 *すべてのストア表示* 管理者の範囲に、ストア表示レベルで上書きされた値を持つ製品を含めます。
* **MDVA-29954** (*Adobe Commerceの場合 >=2.3.0 &lt;2.3.6> || 2.4.0 || 2.4.2 （B2B 拡張機能を使用）*) - *新しい会社登録リクエスト* および *会社にリンクされました* 間違ったアドレスから電子メールが送信されます。
* **MDVA-28357** (*Adobe Commerceの場合 >=2.3.2 &lt;2.3.6> || >=2.4.0 &lt;2.4.1*) — 標準のアナライザーを、の SKU フィールドのキーワード tokenizer に置き換えます。 [!DNL ElasticSearch] ワイルドカード検索クエリを、ハイフン (&quot;-&quot;) を含む SKU で機能させるインデックス。

## v1.0.7 {#v1-0-7}

* **MDVA-30972** (*Adobe Commerceの場合 >=2.3.0 &lt;2.4.2.2*) — カスタム注文のステータスが「 *処理中* WebApi を使用した部分出荷の作成後。
* **MDVA-30428** (*Adobe Commerceの場合 >=2.3.4 &lt;2.3.5>*) — この製品がカスタム在庫ソースに割り当てられている場合に、顧客がウィッシュリストに製品を追加できない問題を修正しました。
* **MDVA-30594** (*Adobe Commerceの場合 >=2.3.0 &lt;2.4.2.2*) - FPT が設定されている場合に、複数のアドレスを持つ注文をチェックアウト時に保存できない問題を修正しました。
* **MDVA-29148** (*Adobe Commerceの場合 >=2.3.0 &lt;2.4.2.2*) - API 呼び出しを介して製品を作成する際に発生していた問題（の製品カスタム属性）を修正しました `\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend` （複数選択と同様）タイプは、ペイロードに値が指定されていない場合、デフォルト値を使用しません。
* **MDVA-30837** (*Adobe Commerceの場合 >=2.3.1 &lt;2.3.5>*) — 設定を追加しました。 *税額を含む：はい/いいえ* （無料配送方法の設定） 条件 *税額を含む* が *はい*&#x200B;の場合、最小受注額は小計+税金として計算されます。 条件 *税額を含む* が *いいえ*、最小注文額は小計として計算されます
* **MDVA-25028** (*Adobe Commerceの場合 >=2.3.2 &lt;2.3.3.3 || >=2.3.5 &lt;2.3.6*) — を使用しておこなわれた注文の問題を修正します [!DNL PayPal Payflow Pro] 不正フィルタがトリガーされた場合、は「不正の疑い」ステータスに設定されません。
* **MDVA-31224** (*Adobe Commerceの場合 >=2.3.3 &lt;2.3.5>*) - `catalog_product_price` バンドル製品のインデックス再作成操作。
* **MDVA-31321** (*Adobe Commerceの場合 >=2.3.2 &lt;2.3.5>*) - *すべて表示* が選択されている。 [!DNL Elasticsearch] は、製品 id の大きなリストを返します。 このシナリオでは、order by 句が誤った SQL フォーマットに変換されます。
* **MDVA-30815** (*Adobe Commerceの場合 >=2.3.2 &lt;2.3.4>*) — 検索結果ページに表示する検索結果の数を変更すると、Adobe Commerceで空白のページが表示される問題を修正しました。 [!DNL Elasticsearch] 1 ページあたりに表示される検索結果の数を変更した場合、カテゴリページからの結果が正しく表示されるようになりました。
* **MDVA-30782** (*Adobe Commerceの場合 >=2.3.5 &lt;2.4.2.2*) — 買い物かごルールに関係なく動的ブロックが表示される問題を修正しました。
* **MDVA-31021** (*Adobe Commerceの場合 >=2.3.0 &lt;2.4.2.2*) — でパフォーマンスの問題が発生していた問題を修正しました。 `module-catalog-import-export/Model/Import/Product/Option.php`. に約 100,000 件を超えるレコードがある場合 `catalog_product_option` の表に示すように、1 つの製品を含む新しい CSV が検証されるまでに 10 秒未満で済みます。
* **MDVA-31007** (*Adobe Commerceの場合 >=2.4.0 &lt;2.4.1*) — マイアカウント領域とバックエンドの注文の詳細ページにカスタムアドレス属性が正しく表示されない問題を修正しました。
* **MDVA-29389** (*Adobe Commerceの場合 >=2.3.0 &lt;2.4.2.2*) — 高度なレポート機能で `analytics_collect_data` cronjob は次のように言います。 *ポートは、ホストパラメーター内で設定する必要があります（localhost:3306 など）。*.
* **MDVA-31343** (*Adobe Commerceの場合 >=2.3.4 &lt;2.3.6>*) — 削除された body クラスの問題を修正しました `page-layout-category-full-width` カテゴリがスケジュールされたとき。
* **MDVA-30945** (*Adobe Commerceの場合 >=2.3.0 &lt;2.4.2.2*) — 買い物かごを更新する際に致命的なエラーメッセージが表示される問題を修正しました `Call to a member function getValue() on null in module-configurable-product CartItemProcessor.php`.

## v1.0.6 {#v1-0-6}

* **MDVA-28993** (*Adobe Commerceの場合 >=2.3.4 &lt;2.4.0*) — を実装します。 *最小は一致する必要があります* 機能と部分検索 [!DNL Elasticsearch] エンジン。 検索クエリでハイフンを使用する問題を解決します。
* **MDVA-30102** (*Adobe Commerceの場合 >=2.3.2 &lt;=2.4.0*) — レイアウトキャッシュに TTL がないので、Redis キャッシュが急速に拡大する問題を修正しました。
* **MDVA-30599** (*Adobe Commerceの場合 >=2.3.4 &lt;=2.4.0*) - API を使用して作成されたゲストの引用が、ログインしている顧客の引用として正しくマークされない問題を修正しました。
* **MDVA-29446** (*Adobe Commerceの場合 >=2.3.3 &lt;=2.4.0*) — チェックアウト時に、該当しない発送方法の価格がゼロと表示される問題を修正しました。
* **MDVA-30357** (*Adobe Commerceの場合 >=2.3.2 &lt;=2.4.0*) - cron でサイトマップを生成する際に、間違った画像 URL が作成される問題を修正しました。
* **MDVA-30565** (*Adobe Commerceの場合 >=2.3.2 &lt;=2.3.3-p1*) - *cartid = 0 のエンティティはありません* 永続的な買い物かごが有効になっている場合、ストアフロントのチェックアウト時にゲスト顧客に対してエラーが表示されます。
* **MDVA-29787** (*Adobe Commerceの場合 >=2.3.0 &lt;=2.4.0*) — 関連製品のターゲットルールが機能しない問題を修正しました。 *次のいずれかに該当* 条件は、表示する製品を定義するために使用されます。
* **MDVA-30977** (*Adobe Commerceの場合 >=2.3.4 &lt;=2.3.5-p2*) — インデックス再作成後にカテゴリからランダムな製品が欠落する問題を修正しました。
* **MDVA-28202** (*Adobe Commerceの場合 >=2.3.4 &lt;=2.4.2*) - MSI を使用した場合に、レイヤーナビゲーションで設定可能な製品が正しくフィルタリングされない問題を修正しました。
* **MDVA-28300** (*Adobe Commerceの場合 >=2.3.0 &lt;2.3.6>*) - GQL リクエストがカタログ価格ルールの価格の変更を反映しない問題を修正しました。
* **MDVA-31006** (*Adobe Commerceの場合 >=2.3.2 &lt;=2.4.2*) - [!DNL Paypal Express] 支払い。

## v1.0.5 {#v1-0-5}

* **MDVA-30841** (*Adobe Commerceの場合 >=2.3.4 &lt;2.3.6> || 2.4.0*) — レイヤーナビゲーションで、 *いいえ* ブール型製品属性の値は、階層型ナビゲーションに含まれません ( [!DNL Elasticsearch] は検索エンジンとして使用されました。
* **MDVA-28191** (*Adobe Commerceの場合 >=2.3.3 &lt;2.4.2.2*) — 管理者を介した注文作成中に支払い方法が読み込まれない問題を修正しました。
* **MDVA-29959** (*Adobe Commerceの場合：B2B 拡張機能の場合は 2.3.0 &lt;=2.3.3-p1*) — 制限付き管理者ユーザーが *会社* の権限で会社のアカウントを削除することはできません。
* **MDVA-30265** (*Adobe Commerceの場合 >=2.3.3 &lt;2.4.2.2*) — 請求書の作成後に出荷追跡リンクが機能しなくなる問題を修正しました。
* **MDVA-28409** (*Adobe Commerceの場合 >=2.3.4 &lt;2.3.6> || 2.4.0*) - `sales_clean_quotes` cron ジョブが次の場合に失敗します： *メモリ不足* エラーが発生するのは、データベース内の有効期限切れの引用符の数が多い場合です。
* **MDVA-30593** (*Adobe Commerceの場合 >=2.3.0 &lt;2.3.4>*) - 「Quote Lifetime」設定に従って有効期限が切れた引用符がクリーンアップされない問題を修正しました。
* **MDVA-30107** (*Adobe Commerceの場合 >=2.3.0 &lt;2.3.6>*) — ストアビューに異なるベース URL が使用されている場合に、ストア切り替えボタンが期待どおりに動作しない問題を修正しました。
* **MDVA-28763** (*Adobe Commerceの場合 >=2.3.2 &lt;2.3.4>*) - REST API を複数回使用して製品情報を更新した後に製品画像が複製される問題を修正しました。
* **MDVA-30284** (*Adobe Commerceの場合 >=2.3.0 &lt;2.4.2.2*) — 次の理由でカタログ検索のインデクサーが失敗する問題を修正しました *[!DNL Elasticsearch]エラー：インデックスの合計フィールド数の制限を超えました。*
* **MDVA-29042** (*Adobe Commerceの場合：B2B 拡張機能の場合は 2.3.3 &lt;=2.3.4-p2*) — カタログ権限がに変更された問題を修正しました。 *許可* は、共有カタログに新しい商品が追加された後に、自動的に追加されます。
* **MDVA-30428** (*Adobe Commerceの場合 >=2.3.3 &lt;2.4.2.2*) — この製品がカスタム在庫ソースに割り当てられている場合に、顧客がウィッシュリストに製品を追加できない問題を修正しました。
* **MDVA-28661** (*(Adobe Commerceの場合 ) 2.3.0 &lt;2.4.2、B2B 拡張機能付き*) — 会社管理者を変更した後、「会社ユーザー」の「会社アカウント」セクションでエラーが発生する問題を修正しました。

## v1.0.4 {#v1-0-4}

* **MDVA-30195** (*Adobe Commerce 2.3.1 - 2.3.4-p2 の場合*) — データベース名が長すぎると cron ジョブが失敗し、結果としてフロントエンドでカテゴリが更新されない問題を修正しました。
* **MDVA-30106** (*(Adobe Commerce ^2.3.0 用 )*) — チェックアウト時の支払いが *NULL のプロパティ「length」を読み取れません* JS コンソールでエラーが発生しました。
* **MDVA-28656** (*Adobe Commerceの場合 >=2.3.1 &lt;2.3.6> || >=2.4.0 &lt;2.4.2*) — 支払い情報が不要な注文（100%割引など）で、注文に対して請求書が作成された場合に、注文ステータスが「 *クローズ* を使用します。
* **MDVA-30209** (*Adobe Commerce 2.3.0 - 2.3.3-p1 の場合*) — 顧客がアカウント情報を更新した場合に顧客グループがデフォルトに変更される問題を修正しました。
* **MDVA-30123** (*Adobe Commerceの場合 >=2.3.4 &lt;2.4.2.2*) — 属性オプションラベルがGraphQLクエリで正しく翻訳されない問題を修正しました。
* **MDVA-29996** (*Adobe Commerceの場合 >=2.3.3 &lt;2.4.2.2*) — カテゴリ権限を有効にした後、カテゴリページがフルページキャッシュでキャッシュされない問題を修正しました。
* **MDVA-30164** (*Adobe Commerceの場合 >=2.3.1 &lt;2.4.2.2*) — カスタム顧客属性が存在する場合に、顧客レコードを顧客グリッドからエクスポートできない問題を修正しました。
* **MDVA-30444** (*Adobe Commerceの場合 >=2.3.0 &lt;2.4.1*) - GraphQLを使用しておこなわれた注文に対して確認 E メールが送信されない問題を修正しました。
* **MDVA-30490** (*Adobe Commerce 2.3.4 - 2.3.5-p2 の場合*) — 製品の 1 つに空の短い説明がある場合に製品比較で 500 エラーページがスローされる問題を修正しました。
* **MDVA-30232** (*Adobe Commerceの場合 >=2.3.1 &lt;2.4.1*) — 元の注文にギフトカードが含まれている場合に再注文できない問題を修正しました。
* **MDVA-29965** (*Adobe Commerceの場合 >=2.3.3 &lt;2.4.0*) — 顧客が買い物かごに製品を追加する際に無効なフォームキーエラーが発生する問題を修正しました。
* **MDVA-30008** (*Adobe Commerceの場合 >=2.3.0 &lt;2.4.2.2*) — 公開カタログにある製品に対して Admin API を通じて注文を発行できない B2B の問題を修正しました。
* **MDVA-22469** (*Adobe Commerce 2.3.2-p2 - 2.3.3-p1 の場合*) - Adobe Commerce 2.3.3 にアップグレードした後、Page Builder が管理パネルで機能せず、一部の JS および CSS ファイルが読み込まれない問題を修正しました。
* **MC-35984** (*Adobe Commerceの場合 >=2.4.0 &lt;2.4.1*) - Return Merchandise Authorization(RMA) の送料ラベルを作成した後、マーチャントが返品ページのどのページ要素ともやり取りできない問題を修正しました。

## v1.0.3 {#v1-0-3}

* **MDVA-25602** (*Adobe Commerce 2.3.0 - 2.3.4 の場合*) - [!DNL PayPal Payflow Pro] の支払い方法とクッキーを `SameSite=Lax` デフォルトでは、Chrome 80 ブラウザーおよび API 応答で、顧客ログインページにリダイレクトされます。
* **MDVA-26694** (*Adobe Commerceの場合 >=2.3.0 &lt;2.3.6> || 2.4.0*) — 毎日期限が切れる製品キャッシュとカタログキャッシュの問題を修正しました（ただし、期限が異なるようにスケジュールされている場合）。
* **MDVA-27825** (*Adobe Commerceの場合 >=2.3.0 &lt;2.4.1*) — メモリリークが原因で大量のデータの書き出しに失敗する問題を修正しました。
* **MDVA-29085** (*Adobe Commerceの場合 >=2.3.0 &lt;=2.3.5-p1*) - API で会社が作成された場合に、必須の新しい会社の電子メールが送信されない B2B の問題を修正しました。
* **MDVA-29344** (*Adobe Commerceの場合 >=2.3.5 &lt;=2.4.0-p1*) — ヘッダー要素からテキスト要素にテキストをコピーした後、Page Builder が停止する問題を修正しました。
* **MDVA-29835** (*Adobe Commerceの場合 2.3.1 &lt;2.4.2.2*) — ギフトカードの注文に 1 つではなく 2 つのコードが含まれていた問題を修正しました。
* **MDVA-30052** (*Adobe Commerceの場合 >=2.3.2-p2 &lt;2.3.5.5*) — プライベートコンテンツ（ローカルストレージ）が正しく入力されず、パフォーマンスの問題が発生していた問題を修正しました。
* **MDVA-30131** (*Adobe Commerceの場合 >=2.3.4 &lt;2.3.6> || 2.4.0*) — レイヤーナビゲーションで、 *いいえ* ブール型製品属性の値は、階層型ナビゲーションに含まれません ( [!DNL Elasticsearch] は検索エンジンとして使用されました。
* **MDVA-35514** (*Adobe Commerceの場合 >=2.4.0 &lt;2.4.1*) — 発送ラベルを作成し、パッケージの作成モーダルウィンドウで発注された製品をパッケージに追加する際の問題を修正しました。
