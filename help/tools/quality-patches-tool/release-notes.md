---
title: リリースノート
description: Adobe Commerceで使用可能なパッチと、それらが解決する問題について説明します。
exl-id: 22262555-f5ea-49ad-98ad-ea8428ef66d5
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '20485'
ht-degree: 0%

---

# リリースノート

この [[!DNL Quality Patches Tool]](https://github.com/magento/quality-patches) は、AdobeとMagento Open Sourceコミュニティが開発した個別のパッチを提供します。 インストールされたバージョンのAdobe Commerceで使用可能な個々のパッチに関する一般情報を適用、元に戻して表示できます。 パッチの開発者に関係なく、Adobe CommerceおよびMagento Open Sourceプロジェクトにパッチを適用できます。 例えば、コミュニティが開発したパッチをAdobe Commerce プロジェクトに適用できます。

>[!INFO]
>
>参照： [パッチの適用](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html#apply-individual-patches) Adobe Commerce プロジェクトにパッチを適用する方法については、を参照してください。 参照： [[!DNL Quality Patches Tool]：パッチの検索](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) リリース済みパッチの完全なリストを確認するには、『 ソフトウェア アップデート ガイド 』を参照してください。

>[!INFO]
>
>詳しくは、 [!DNL quality patches] コミュニティがMagento Open Sourceのために作成したものについては、 [リリースノート](https://github.com/magento/quality-patches/blob/master/community-release-notes.md).

## v1.1.48 {#v1-1-48}

* **ACSD-55566** （Adobe CommerceおよびMagento Open Source >=2.4.3 &lt;2.4.7） – で発生した問題を修正します。 `mergeCart` ミューテーションが「」で失敗する&#x200B;*内部サーバーエラー*」を選択します [!DNL GraphQL] 同じバンドル項目を持つソースと宛先の買い物かごを結合する場合の応答。
* **ACSD-56546** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.7 の場合） – 設定可能な製品およびバンドル製品が **在庫切れ** 次の場合に店先で **製品外設定の表示** 等しい *Disabled*.
* **ACSD-56635** （Adobe Commerce >=2.4.6 &lt;2.4.7 の場合） – でインポートを使用すると、インポートされたお客様が同じメールアドレスで重複する問題を修正しました **アカウント共有** をに設定 *グローバル*.
* **ACSD-56741** （Adobe CommerceおよびMagento Open Source >=2.4.6 &lt;2.4.7） – エラーメッセージ「」を修正&#x200B;*型 null の値の配列オフセットにアクセスしようとしています*」と表示されます `setup:upgrade` データベースにカスタムが含まれている場合 [!DNL MySQL] インデックス化のメカニズムと関係のないトリガー。 [!DNL MView].
* **ACSD-57315** （Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.7 の場合） – で新しいトランザクションが作成される際の問題を修正しました [!DNL PayPal Payflow Pro] 毎回 [!UICONTROL Fetch] ボタンがクリックされた日 **[!UICONTROL View transaction]** 管理画面。
* **ACSD-57337** （Adobe Commerce >=2.4.4 &lt;2.4.6 の場合） – 特定の web サイトへのアクセス制限を持つ管理者ユーザーが、 **[!UICONTROL Companies]** グリッド。
* **ACSD-57394** （Adobe CommerceとMagento Open Source >=2.4.4 &lt;2.4.7 の場合） – で複数の並べ替えフィールドを使用して誤った商品が並べ替えられる問題を修正しました [!DNL GraphQL].
* **ACSD-57565** （Adobe CommerceおよびMagento Open Source >=2.4.6 &lt;2.4.7） – で発生した問題を修正します。 **[!UICONTROL Order]** 期間が更新されるまで、ダッシュボードに間違った注文情報が表示される。 ダッシュボードには、最初の読み込み時に正しい注文統計が表示されるようになりました。
* **ACSD-57854** （Adobe CommerceおよびMagento Open Source >=2.4.5 &lt;2.4.7 の場合） – 製品時の問題を修正しました [!DNL GraphQL] リクエストが、カテゴリ集計で無効なカテゴリを返しました。
* **ACSD-58008** （Adobe Commerce >=2.4.5 &lt;2.4.7 の場合） – 終了日が指定されていない場合に、スケジュールされた更新を更新するとステージングされた項目の以前のバージョンが削除される問題を修正しました。
* 更新されたパッチ：MDVA-39305-V2、ACSD-48627、ACSD-54965

## v1.1.47 {#v1-1-47}

* **ACSD-55241** （Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.7） – 次の問題を修正します *[!UICONTROL Used]* および *[!UICONTROL Times Used]* 複数のアドレスを使用したチェックアウトで属性を使用すると、生成されたクーポンに間違った値が表示される。
* **ACSD-56760** （Adobe Commerce >=2.4.6 &lt;2.4.7 の場合） – 特定の web サイトに限定されている管理者ユーザーが、web ストアが独自のルートカテゴリを持つ場合に、カテゴリ内で新しい商品の並べ替えや追加ができない問題を修正しました。
* **ACSD-56858** （Adobe Commerce >=2.4.2 &lt;2.4.7 の場合） – 制限付きの会社管理者に対して B2B 会社の役割の権限が正しく表示されない問題を修正しました。
* **ACSD-57074** （Adobe CommerceおよびMagento Open Source >=2.4.6 &lt;2.4.7） – で発生した問題を修正します。 *はい/いいえ* カスタム属性： `attrbute_code` の概要 `price_` はインデックス作成で正しく機能せず、このような属性を持つ製品はフロントエンドで使用できません。
* 更新されたパッチ：ACSD-53378、ACSD-51819

## v1.1.46 {#v1-1-46}

* **ACSD-46767** （Adobe CommerceとMagento Open Source >=2.4.4 &lt;2.4.6 の場合） – 商品がまだ在庫にある場合でも、在庫数が変化するとカテゴリページのキャッシュが無効になる問題を修正しました。
* **ACSD-54656** （Adobe Commerce >=2.4.5 &lt;2.4.6 の場合） – チェックアウト時に非表示の Recaptcha が失敗し、注文できなくなる問題を修正しました。
* **ACSD-55100** （Adobe Commerce >=2.4.6 &lt;2.4.7 の場合） – GraphQLが検索結果で 10,000 個を超える商品を返さない問題を修正しました。
* **ACSD-56621** （Adobe Commerce >=2.4.2 &lt;2.4.7 の場合） – 更新された名と姓が会社管理者ユーザーの「挨拶ヘッダー」セクションに反映されない問題を修正しました。
* **ACSD-56842** （Adobe CommerceとMagento Open Source >=2.4.2 &lt;2.4.7） – 実行後に遅延プロキシと遅延プロキシファクトリが見つからない問題を修正しました `setup:di:compile`.
* **ACSD-57003** （Adobe CommerceおよびMagento Open Source >=2.4.6 &lt;2.4.7） – 注文ステータスが次のように変更される問題を修正します *[!UICONTROL Complete]* ～に変わるのではなく *[!UICONTROL Processing]* 注文が一部払い戻され、一部出荷された場合。
* 更新されたパッチ：ACSD-50260-v2、ACSD-54966

## v1.1.45 {#v1-1-45}

* **ACSD-56886** （Adobe CommerceとMagento Open Source >=2.4.2 &lt;2.4.7） – 2 つの子商品のいずれかが予定された更新によって無効になっている場合に、設定可能な商品が在庫切れになる問題を修正しました。
* **ACSD-56616** （Adobe CommerceおよびMagento Open Source >=2.4.5 &lt;2.4.6） – バンドルされた商品が、シンプルな商品が在庫切れになった場合に、ストアフロントに在庫として表示される問題を修正しました。
* **ACSD-56515** （Adobe Commerce >=2.4.2 &lt;2.4.7 の場合） – web サイトレベルの権限を持つ管理者が動的ブロックを追加または編集できない問題を修正しました。
* **ACSD-56447** （Adobe CommerceとMagento Open Source >=2.4.2 &lt;2.4.7 の場合） – 並行する REST web API リクエストを使用して同じ商品を買い物かごに追加すると、買い物かごに 2 つの異なる商品が表示される問題を修正しました。
* **ACSD-56415** （Adobe CommerceおよびMagento Open Source >=2.4.5 &lt;2.4.7） – 部分価格インデックスのパフォーマンスが次の理由で低下する問題を修正しました。 `DELETE` データベースにインデックス作成の必要な部分価格データが大量にある場合にクエリします。
* **ACSD-54965** （Adobe Commerce >=2.4.5 &lt;2.4.6 の場合） – 商品がカスタム在庫のみに割り当てられると、ビジュアルマーチャンダイジンググリッドに正しい在庫が表示されない問題を修正しました。
* **ACSD-52824** （Adobe Commerce >=2.4.5 &lt;2.4.7 の場合） – 会社の設定で支払い方法を無効にすると、会社の顧客に PayPal Express、Google Pay、Apple Pay のボタンが表示される問題を修正しました。
* 更新されたパッチ：ACSD-56193

## v1.1.44 {#v1-1-44}

* **ACSD-56790** （Adobe CommerceおよびMagento Open Source >=2.4.6 &lt;2.4.7） – を使用してカテゴリ製品を並べ替える際に、ユーザーが管理ダッシュボードにリダイレクトされる問題を修正しました **在庫切れを一番下に移動** オプションと `Invalid security or form key. Please refresh the page` エラーが画面の上部に表示されます。
* **ACSD-56280** （Adobe Commerce >=2.4.4 &lt;2.4.7 の場合） – ギフトレジストリから商品を注文すると例外が発生する問題を修正しました。
* **ACSD-56246** （Adobe CommerceおよびMagento Open Source >=2.4.6 &lt;2.4.7 の場合） – 商品のスケジュールされた更新がアクティブになると、カスタム複数選択属性からデータが削除される問題を修正しました。
* **ACSD-56193** （Adobe CommerceとMagento Open Source >=2.4.2 &lt;2.4.4 の場合） – ページビルダーを使用して、カテゴリの説明でスケジュール済みブロックを使用すると、Varnish/Fastly キャッシュが更新されない問題を修正しました。
* **ACSD-56158** （Adobe CommerceおよびMagento Open Source >=2.4.5 &lt;2.4.7） – 「買い物かご」クエリによって各税務処理基準の合計税額が返される問題を修正します。
* **ACSD-56023** （Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.7 の場合） – キャッシュが有効な場合に CMS ページでウィジェットコンテンツが更新されない問題を修正しました。
* **ACSD-55427** （Adobe Commerce >=2.4.5 &lt;2.4.7 の場合） – 管理者ユーザーが管理者の商品ページで共有カタログの商品の割り当てを解除できない問題を修正しました。
* **ACSD-55352** （Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.7） – 顧客報酬ポイントを含む部分的なクレジットメモを作成した後、注文ステータスが「クローズ」に変わり、クレジットメモオプションが管理者の注文ページに表示されなくなる問題を修正しました。
* **ACSD-55231** （Adobe Commerce >=2.4.2 &lt;2.4.7 の場合） – クイックオーダー機能を使用して買い物かごに商品を追加できない問題を修正しました。
* **ACSD-54283** （Adobe Commerce >=2.4.3 &lt;2.4.4 の場合） – デフォルト（一般グループ）の Shared Catalog に割り当てられていない Products/Categories が、XML サイトマップに引き続き含まれる問題を修正しました。
* 更新されたパッチ：ACSD-52041、ACSD-54040、ACSD-51819

## v1.1.43 {#v1-1-43}

* **ACSD-54972** （Adobe CommerceとMagento Open Source >=2.4.2 &lt;2.4.7 の場合） – カテゴリ URL を変更した後、正規カテゴリ URL が更新されない問題を修正しました。
* **ACSD-53636** （Adobe CommerceおよびMagento Open Source >=2.4.3 &lt;2.4.5） – 特別価格の子商品を持つ設定可能な商品の商品一覧ページに通常価格が表示されない問題を修正しました。
* **ACSD-54885** （Adobe CommerceとMagento Open Source >=2.4.2 &lt;2.4.7 の場合） – 管理者ユーザーがを使用している際の複数アドレスのチェックアウトの問題を修正しました *顧客としてログイン* 機能。
* **ACSD-55610** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.7） – 部分的にキャンセルされた注文に間違った割引額が含まれる問題を修正しました。
* **ACSD-55334** （Adobe CommerceおよびMagento Open Source >=2.4.3 &lt;2.4.7 の場合） - GraphQL レスポンスの翻訳辞書を使用したラベルの翻訳を修正します。
* **ACSD-54739** （Adobe Commerce >=2.4.5 &lt;2.4.7 の場合） – 関連する商品ルールに商品の在庫ステータス条件が適用されない問題を修正しました。
* **ACSD-53925** （Adobe CommerceとMagento Open Source >=2.4.2 &lt;2.4.7 の場合） – 次の場合に、管理者が製品カルーセルで CMS ブロックを保存できない問題を修正しました `catalog_product_price` dimensions-mode をに設定 *web サイト*.
* **ACSD-52714** （Adobe CommerceとMagento Open Source >=2.4.2 &lt;2.4.7 の場合） – 日付フォーマットがに設定されている場合に、管理グリッドで日付フィルターが機能しない問題を修正しました *Y-m-d*.
* **ACSD-55055** （Adobe CommerceとMagento Open Source >=2.4.2 &lt;2.4.7） – ショッピングカート内の買い物かご価格ルールに製品属性を読み込むパフォーマンスを向上させます。
* **ACSD-53790** （Adobe Commerce >=2.4.6 &lt;2.4.7 の場合） – REST API を使用して 1 つの商品に対して複数の RMA を作成できる問題を修正しました。
* **ACSD-56090** （Adobe CommerceとMagento Open Source >=2.4.2 &lt;2.4.5 の場合） - GraphQL リクエストが、特にリクエストされたストアデータではなく、すべてのストアのデータで応答する問題を修正しました。
* **ACSD-54983** （Adobe Commerce >=2.4.2 &lt;2.4.7 の場合） – ユーザーステータスがに設定されている場合に、GraphQL リクエストで会社のユーザー UID を取得できない問題を修正しました *[!UICONTROL Inactive]*.
* **ACSD-53309** （Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.7） – で税金が完全に適用されない問題を修正しました *[!UICONTROL Regular Price]* カスタマイズ可能なオプションが選択されている場合のラベル。
* **ACSD-55305** （Adobe Commerce >=2.4.4 &lt;2.4.7 の場合） – 次の問題を修正します *[!UICONTROL Edit Company User]* のポップアップ **[!UICONTROL myAccount]** > **[!UICONTROL Company Structure]** 画面にローダーが表示されると、ページがフリーズする。
* 更新されたパッチ：ACSD-49013

## v1.1.42 {#v1-1-42}

* **ACSD-53658** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.7） – 次の問題を修正します *[!UICONTROL Recently Viewed]* 商品データがストア表示で正しく更新されない。
* **ACSD-54626** （Adobe Commerce >=2.4.6 &lt;2.4.7 の場合） – 新しい発注書ルールを作成できない問題を修正しました（`createPurchaseOrderApprovalRule`）に設定する必要があります。 `NUMBER_OF_SKUS` 属性の基準 [!DNL GraphQL].
* **ACSD-53845** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.7） – を修正します。 [!DNL MySQL] の場合の接続タイムアウトの問題 `consumer max_messages` = 0。
* **ACSD-54890** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.7）の場合 – 次の問題を修正します `aggregate_sales_report_bestsellers_data` 原因 [!DNL MySQL] が原因のエラー `/tmp` ディスクの空き領域が不足しています。
* **ACSD-55112** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.7）の場合：の問題を修正します。 *[!UICONTROL Submit review]* ボタンは、次の操作を行わずに複数回クリックできます [!DNL Google reCAPTCHA v3] 検証。
* **ACSD-54264** （Adobe Commerce >=2.4.4-p5 &lt;2.4.5） || >=2.4.5-p4 &lt;2.4.6 || >=2.4.6-p2 &lt;2.4.7） – エラーメッセージが表示される問題を修正しました *「リクエストされた属性は更新できません。 行 ID: store_id&quot;* 顧客が別のストア表示から交渉可能な見積もりでチェックアウトを試みたときに表示されます。
* **ACSD-54418** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.7） – 動的に価格が設定されるバンドルの各子製品に誤って定額の割引額が適用される問題を修正しました。
* **ACSD-55238** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.7 の場合） – 空の商品の保存に関する修正 *[!UICONTROL Meta Description]*.
* **ACSD-54966** （Adobe CommerceおよびMagento Open Source >=2.4.5 &lt;2.4.7 の場合） – 前回の注文が失敗した場合に、お客様ごとの使用制限があるクーポンコードが再利用できない問題を修正しました。
* **ACSD-54060** （Adobe CommerceとMagento Open Source >=2.4.3 &lt;2.4.7 の場合） – 別のスコープに割り当てられた別の商品の子である場合に、制限付き管理者が商品を保存できない問題を修正しました。
* **ACSD-48910** （Adobe CommerceとMagento Open Source >=2.4.5 &lt;2.4.6） – 複数のソースに割り当てられたバンドル商品が、注文の請求および出荷後に（まだ数量がゼロ以外の場合でも）在庫切れになる問題を修正しました。
* **ACSD-55381** （Adobe Commerce >=2.4.2 &lt;2.4.7 の場合） – クエリ中に内部サーバーエラーが発生する問題を修正しました `configurable_product_option_uid` および `configurable_product_option_value_uid` からのフィールド [!DNL B2B] *[!UICONTROL Requisition list]* 経由 [!DNL GraphQL].
* **ACSD-55628** （Adobe Commerce >=2.4.4-p2 &lt; 2.4.5 の場合） || >=2.4.5-p1 &lt; 2.4.6） – 会社登録フォームへのファイルのアップロードと、ストアフロントの顧客属性のファイルの置き換えを修正しました。
* 更新されたパッチ：ACSD-51240、ACSD-51890、ACSD-53098

## v1.1.41 {#v1-1-41}

* **ACSD-54376** （Adobe Commerce >=2.4.2 &lt;2.4.7 の場合） – 商品が既に買い物かごに追加された後に共有カタログから削除された場合に、買い物かごで発生する問題を修正します。
* **ACSD-53722** （Adobe Commerce >=2.4.4 &lt;2.4.7） – 様々な範囲の予定アップデートがアクティブになると、バンドルされた製品オプションの価格が$0 に変わる問題を修正しました。
* **ACSD-53643** （Adobe Commerce >=2.4.3 &lt;2.4.7 の場合） – 商品が無効または在庫切れの状態で発注書を送信すると、注文の合計が正しく表示されない問題を修正しました。 を非表示にすることで修正されます。 *[!UICONTROL Place Order]* このような発注書のボタン。
* **ACSD-54067** （Adobe CommerceとMagento Open Source >=2.4.0 &lt;2.4.7 の場合） – モバイルデバイスで商品ビデオが再生されない問題を修正しました。
* **ACSD-55414** （Adobe CommerceとMagento Open Source >=2.4.0 &lt;2.4.6） – MariaDB が EAV entity_id を文字列から整数にキャストしようとした際のパフォーマンスを向上させます。
* **ACSD-51819** （Adobe Commerce >=2.4.4 &lt;2.4.4-p4 の場合） – 同じ見積書 ID で複数の注文を行うことができる問題を修正しました。
* **ACSD-53118** （Adobe Commerce >=2.4.0 &lt;2.4.7 の場合） – 次の問題を修正します *[!UICONTROL Cart Price Rule]* 製品の属性が空の場合に、クーポンコードを使用して適用されます。
* **ACSD-54324** （Adobe Commerce >=2.4.5 &lt;2.4.7 の場合） – GraphQLの requisition_lists リクエストでページネーションの設定が考慮されず、すべての結果が返される問題を修正しました。
* 更新されたパッチ：MDVA-42855-v2

## v1.1.40 {#v1-1-40}

* **ACSD-54680** （Adobe Commerce >=2.4.0 &lt;2.4.6 の場合） – 複数のソースが割り当てられている商品に対して送信された B2B 見積もりを処理できない問題を修正しました。
* **ACSD-54040** （Adobe Commerce >=2.4.4-p5 &lt;2.4.5） || >=2.4.5-p4 &lt;2.4.6） – 問題を修正しました *[!UICONTROL Created]* b2B モジュールが有効な場合、注文の詳細のフィールドが空白になる。
* **ACSD-54319** （Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.6） – で製品価格がゼロと表示される問題を修正しました *[!UICONTROL Product in Cart]* レポート。
* **ACSD-53378** （Adobe CommerceおよびMagento Open Source >=2.4.5 &lt;2.4.7） – 大きなアドレス帳を持つお客様のチェックアウトページの読み込み時間を改善します。
* **ACSD-52657** （Adobe CommerceとMagento Open Source >=2.4.5 &lt;2.4.7 の場合） – サブドメインを使用するセカンダリ storreview で minicart が更新されない問題を修正しました。
* **ACSD-53414** （Adobe Commerce >=2.4.6 &lt;2.4.7 の場合） – 制限付き管理者ユーザーが、権限適用範囲外の CMS ページを表示できる問題を修正しました。
* **ACSD-54472** （Adobe Commerce >=2.4.6 &lt;2.4.7 の場合） – 拒否された会社の顧客が引き続き認証を行い、ブロックされた会社と拒否された会社の顧客が引き続き注文を行える問題を修正しました。 このパッチは、GraphQL エンドポイントの検証をさらに強化します。
* **ACSD-52801** （Adobe CommerceとMagento Open Source >=2.4.4 &lt;2.4.7 の場合） – GraphQLで商品を検索する際に部分一致を行うオプションを追加します。
* **ACSD-55004** （Adobe CommerceおよびMagento Open Source >=2.4.6 &lt;2.4.7 の場合） – インポートファイルのアップロード中に、で設定された値を超えるバリデーターがクラッシュする問題を修正しました `php.ini`.
* **ACSD-54989** （Adobe Commerce >=2.4.4-p5 &lt;2.4.5） || >=2.4.5-p4 &lt;2.4.6 || >=2.4.6-p2 &lt;2.4.7） – 次の場合に会社管理者が注文できない問題を修正しました *[!UICONTROL Enable Purchase Orders]* はに設定されています。 *[!UICONTROL Yes]* および *[!UICONTROL Purchase Order]* はに設定されています。 *[!UICONTROL No]*.
* **ACSD-54007** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.7 の場合） – エラーを修正します *配列キー「_scope」が定義されていません* 顧客データの読み込み時に表示されます。
* **ACSD-55031** （Adobe CommerceおよびMagento Open Source >=2.4.5 &lt;2.4.6） – を修正します。 *タイプ「mixed」は nullable にできません* コンパイル中のエラー。
* **ACSD-54961** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.7 の場合） – 制限付き管理者ユーザーがを一括更新できない問題を修正しました *製品レビュー* ステータス。
* **ACSD-55256** （Adobe CommerceとMagento Open Source >=2.4.6 &lt;2.4.7 の場合） – 最初の画像のみが画像スライダーに正常に表示される問題を修正しました。
* 更新されたパッチ：ACSD-52041、ACSD-54106

## v1.1.39 {#v1-1-39}

* **ACSD-53704** （Adobe Commerce >=2.4.0 &lt;2.4.7 の場合） – 報酬ポイントの有効期限が切れた後に、報酬ポイントのバランス履歴が誤って計算される問題を修正しました。
* **ACSD-53583** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.7） – の部分的なインデックス再作成のパフォーマンスを向上します。 *カテゴリ製品* および *製品カテゴリ* インデクサー。
* **ACSD-54026** （Adobe Commerce >=2.4.6 &lt;2.4.7 の場合） – で間違ったエラーメッセージを修正します。 `updateCompanyRole` 許可されていないユーザーに対するGraphQL リクエスト。
* **ACSD-54106** （Adobe CommerceとMagento Open Source >=2.4.1 &lt;2.4.5 の場合） – トルコ語のアクセント記号用にカテゴリ商品を名前で並べ替えると正しく表示されない問題を修正しました。
* **ACSD-52219** （Adobe CommerceとMagento Open Source >=2.4.5 &lt;2.4.7 の場合） – ブックマークビューを頻繁に切り替えると、保存された管理グリッドのフィルターが期待どおりに動作しない問題を修正しました。
* **ACSD-54342** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.7 の場合） – 誤ったエラーメッセージを修正します *データ構造のエラー：値が混在しています* 有効なデータのない CSV ファイルを読み込む場合。
* **ACSD-54660** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.6 の場合） – 新しい入力属性が追加されました *並べ替え* GraphQLで顧客の注文を並べ替えるには `sort_field` および `sort_direction`.
* **ACSD-54776** （Adobe Commerce >=2.4.5 &lt;2.4.7 の場合） – チェックされていない場合の問題を修正します *[!UICONTROL Use Default Value]* また、デフォルト以外の製品フィールドの値は、2 番目の web サイト、ストア、ストアの表示では保存されません。
* **ACSD-53998** （Adobe CommerceおよびMagento Open Source >=2.4.4-p2 &lt;2.4.5 || >=2.4.5-p1 &lt;2.4.7） – 問題を修正しました **[!UICONTROL Dynamic Block]** に基づく **[!UICONTROL Customer Segment]** は、カスタマーアカウントからログアウトした後、正しく機能しません。
* **ACSD-53204** （Adobe CommerceおよびMagento Open Source >=2.4.6 &lt;2.4.7） – 修正点 *商品を保存できません。* を使用して製品ギャラリーに画像を追加する同時リクエストを行う際にエラーが発生する `rest/V1/products/<sku>/media` エンドポイント。
* **ACSD-47657** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.7） – AWS資格情報のキャッシングメカニズムを追加しました。 資格情報プロバイダーは、Magentoキャッシュを使用して、EC2 設定用にAWSから取得した資格情報をキャッシュするようになりました。
* パッチを更新：ACSD-51984、ACSD-51574。

## v1.1.38 {#v1-1-38}

* **ACSD-53098** （Adobe CommerceおよびMagento Open Source >=2.4.3 &lt;2.4.4 の場合） – 部分的なインデックスの実行時に、共有カタログに割り当てられた商品がストアフロントに表示されない問題を修正しました。
* **ACSD-54018** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.4.6 の場合） – パフォーマンスに関する問題を修正します。 [!UICONTROL Product List] ウィジェット条件で非グローバル属性を使用するウィジェット。
* **ACSD-54111** （Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.6 の場合） – 透かし画像の縦横比が商品画像と一致しない場合に、商品のサムネール画像がストアフロントに表示されない問題を修正しました。
* **ACSD-47669** （Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.6） – 修正点 *整合性制約違反：1452 子行を追加または更新できません：外部キー制約が失敗します* 製品の CSV を読み込む際にエラーが発生する。
* **ACSD-53347** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.4.7） – price indexer の実行に時間がかかりすぎる問題を修正しました。
* **ACSD-52287** （Adobe Commerce >=2.3.7 &lt;2.4.7 の場合） – 非同期グリッドインデックス作成が有効な場合に、アーカイブされたオーダーグリッドで誤ったオーダーステータスの問題を修正します。
* **ACSD-52929** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.4.7 の場合） – インベントリインデクサーが非同期モードで設定されている場合に、デフォルトのソースアイテムを再インデックス化する冗長リクエストの問題を修正しました。
* **ACSD-53824** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.7） – 次の問題を修正します `UpdateMultiselectAttributesBackendTypes` 移行データの修正プログラムが、次の期間にデータベース トランザクション サイズの制限を超えました `setup:upgrade`.

## v1.1.37 {#v1-1-37}

* **ACSD-52613** （Adobe CommerceとMagento Open Source >=2.4.6 &lt;2.4.7 の場合） – に対して更新がおこなわれなくてもキャッシュとインデックスが更新される問題を修正しました `Inventory_source` rest API による項目。
* **ACSD-51884** （Adobe CommerceとMagento Open Source >=2.3.7 &lt;2.4.7 の場合） – resize コマンドの実行後に商品の画像キャッシュパスが正しくなくなる問題を修正しました。
* **ACSD-53628** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.4.7 の場合） - CSV 販売注文レポートに間違った特殊文字が表示される問題を修正しました。
* **ACSD-53148** （Adobe CommerceとMagento Open Source >=2.4.4 &lt;2.4.7） – 同じ設定可能な商品を買い物かごに追加するためにGraphQLで並行してリクエストを 2 回行うと、同じ商品 SKU を持つ 2 つの異なる商品が買い物かごに入るという問題を修正しました。
* **ACSD-52606** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.7 の場合） – エラーメッセージが表示される問題を修正しました *注文を受け取る準備ができていません* ユーザーがクリックしたときに表示されます。 **[!UICONTROL Notify Order is Ready for Pickup]**.
* **ACSD-51574** （Adobe CommerceとMagento Open Source >=2.4.2 &lt;2.4.7 の場合） – 同じ名前の別の画像に置き換えた後に、フロントエンドで画像が更新されない問題を修正します。
* **ACSD-53728** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.4.7） – 製品の EAV インデクサーの実行に時間がかかる問題を修正しました。
* **ACSD-53979** （Adobe CommerceおよびMagento Open Source >=2.4.6 &lt;2.4.7 の場合） – ようこそメッセージに一重引用符が含まれている場合にホームページで発生する JS の問題を修正します。
* **ACSD-52085** （Adobe CommerceおよびMagento Open Source >=2.4.5 &lt;2.4.7 の場合） – 設定可能な特別価格の商品が商品のカルーセルに表示されない問題を修正しました。
* **ACSD-53795** （Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.7 の場合） – で無効なデータタイプに関する問題を修正しました `indexer_update_all_views` cron ジョブ。
* **ACSD-52143** （Adobe CommerceおよびMagento Open Source >=2.4.6 &lt;2.4.7 の場合） – 製品の読み込み後にカスタムオプションが削除される問題を修正しました。
* **ACSD-53750** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.7） – を修正します。 *壊れたパイプまたは閉じた接続* マルチスレッド中のエラー `catalog_product_price` 再インデックス。
* **ACSD-49843** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.4.0） || >=2.4.1 &lt;2.4.7） – 注文した品目がでオンライン支払い方法で自動請求された後、製品のダウンロードのリンクが使用できなくなる問題を修正しました **[!UICONTROL Payment Action]** = **[!UICONTROL Sale]** の設定が有効になっています。
* **ACSD-47054** （Adobe Commerce >=2.4.2 &lt;2.4.6 の場合） – プレビューの再インデックスがすべてのストアに対して再インデックスを実行して、速度が低下する問題を修正しました。
* ACSD-46541、ACSD-47079 の新しいバージョンを追加しました。
* ACSD-49970-v3 は ACSD-54095 に置き換えられました。

## v1.1.36 {#v1-1-36}

* **ACSD-53239** （Adobe CommerceおよびMagento Open Source >=2.4.3 &lt; 2.4.6 の場合） – インベントリインデクサーがスケジュールに従って更新モードですべてのキャッシュをクリーンアップする問題を修正しました。
* **ACSD-50887** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.7 の場合） – product 属性プロパティが存在する問題を修正しました *[!UICONTROL Use in Search Results Layered Navigation]* はに設定できます。 *はい* なし *[!UICONTROL Use in search]* オプションの設定 *はい*.
* **ACSD-51846** （Adobe CommerceおよびMagento Open Source >=2.4.3-p2 &lt;2.4.6） – を修正します。 *内部エラー* rest API ペイロードのすべてのレベルが検証されるわけではないために発生する問題。
* **ACSD-52906** （Adobe Commerce >=2.3.7 &lt;2.4.7 の場合） – 同じカスタマーセグメントに属するログインしたユーザーが一部のページで不適切なキャッシングを行うと、X-Magento変動 cookie が正しく設定されない問題を修正しました。
* **ACSD-52736** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.4.6） – の問題を修正します。 *買い物かご価格ルール* 設定可能な製品数量の要件が含まれていますが、期待どおりに動作しません。
* **ACSD-47875** （Adobe CommerceとMagento Open Source >=2.3.7 &lt;2.4.7 の場合） – 在庫管理で、管理者ユーザーが特定のストア表示範囲について、管理者から顧客の買い物かごに商品を追加できない問題を修正しました。
* **ACSD-53176** （Adobe Commerce >=2.3.7 &lt;2.4.5 の場合） – 問題を修正します。次の場合に適用されます。 *関連する製品ルール* （を使用） *が次の 1 つ：* 条件が製品と一致しません。
* **ACSD-51666** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.4.7） – エラーを修正します *セッションの有効期限が切れています。もう一度ログインしてください。* これは、ユーザーがログインを試みた後で発生します。
* MDVA-39305-v2 の新しいバージョンを追加しました。
* ACSD-19640 の要件を更新しました。

## v1.1.35 {#v1-1-35}

* **ACSD-51899** （Adobe CommerceとMagento Open Source >=2.4.0 &lt;2.4.7 の場合） – チェックアウト配送手順のデフォルトの配送先住所に、以前に選択した店舗内の集荷先住所が自動入力される問題を修正しました。
* **ACSD-52041** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.7 の場合） – エラーメッセージが表示される問題を修正します。 *[エラー] [!DNL Page Builder] は、ロックを解除せずに 5 秒間レンダリングしていました。* で編集したコンテンツを保存すると Chrome ブラウザーに表示される [!DNL Page Builder].
* **ACSD-52095** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.4.6） – の場合、の問題を修正します。 `manage_stock` 製品の書き出し後、CSV ファイルの値が正しく 0 に設定されていませんでした。
* **ACSD-51358** （Adobe Commerce >=2.4.5 &lt;2.4.7 の場合） – 終了日を指定せずにスケジュール済み更新を削除すると、同じエンティティの他のスケジュール済み更新が削除される問題を修正しました。
* **ACSD-48070** （Adobe Commerce >=2.3.7 &lt;2.4.7 の場合） – スケジュールされた更新を編集すると例外がトリガーされる問題を修正しました。
* **ACSD-51890** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.7）の場合：の問題を修正します。 [!UICONTROL Submit review] ボタンは、次の操作を行わずに複数回クリックできます [!DNL Google reCAPTCHA] v3 検証。
* **ACSD-51984** （Adobe Commerce >=2.4.5 &lt;2.4.7 の場合） – チェックされていない場合の問題を修正します *[!UICONTROL Use Default Value]* および *[!UICONTROL non-default product field]* 2 つ目の web サイト、ストア、ストア表示の値は保存されません。
* **ACSD-52398** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.7 の場合） – エラーを修正します *リクエストされた数量は使用できません* この問題は、ストアフロントで買い物かごにバンドルされた製品の数量を更新しようとした場合に発生します。
* **ACSD-52786** （Adobe CommerceおよびMagento Open Source >=2.4.5 &lt;2.4.6 の場合） – カタログルール条件の問題を修正しました *SKU が* 特定の SKU で始まるすべての製品に適用されます。
* **ACSD-52921** （Adobe CommerceとMagento Open Source >=2.4.5 &lt;2.4.7 の場合） – 在庫切れの設定可能な商品が買い物かごにある場合に、GraphQLに買い物かごの詳細をリクエストすると内部エラーが発生する問題を修正しました。
* **ACSD-51683** （Adobe CommerceとMagento Open Source >=2.4.6 &lt;2.4.7 の場合） – GraphQLを使用してカスタマイズ可能なオプションを買い物かごに追加できない問題を修正しました。
* **ACSD-52133** （Adobe CommerceおよびMagento Open Source >=2.4.6 &lt;2.4.7 の場合） – アップグレード後にカスタマーアカウントを保存できない問題を修正しました。
* **ACSD-52202** （Adobe CommerceおよびMagento Open Source >=2.4.3 &lt;2.4.7） – 注文のフルフィルメント時にデフォルト以外の在庫が 0 数量に変更された場合に、デフォルトの売り上げ可能在庫が誤って 0 に変わる問題を修正します。
* **ACSD-51265** （Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.7） – の問題を修正しました。 `catalog_product_price` システムにバンドルされた製品が多すぎる場合のインデックス再作成のパフォーマンス。
* **ACSD-52831** （Adobe Commerce >=2.3.7 &lt;2.4.7 の場合） – 次の場合に顧客が交渉可能な見積書を注文できない問題を修正しました [!DNL Google reCAPTCHA v3 Invisible] が有効になっています。
* **ACSD-51845** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.7） – 階層価格と異なる属性セットを持つ後続の製品を非同期の一括 REST API で更新できない問題を修正しました。
* **ACSD-52815** （Adobe CommerceとMagento Open Source >=2.3.7 &lt;2.4.7） – デフォルト以外のソースの数量フィールドの入力で、デフォルトの在庫の 8 桁とは異なり、最大 6 桁しかサポートされない問題を修正しました。
* **ACSD-51149** （Adobe Commerce >=2.3.7 &lt;2.4.7 の場合） – 有効なカタログアクセス権を使用したスケジュール済みインポートエクスポートによってインデクサーが無効になり、Cron によるキャッシュフラッシュが発生する問題を修正しました。
* **ACSD-50815** （Adobe CommerceおよびMagento Open Source >=2.4.5 &lt;2.4.6） – 新しいバンドル商品オプションで、シンプルな商品の 10 進数の数量を使用できない問題を修正しました。
* ACSD-47803 のバージョンを更新しました。
* ACSD-51892 のタイトルを更新しました。
* ACSD-51379 を更新しました。
* ACSD-49970-v2 を更新しました。

## v1.1.34 {#v1-1-34}

* **ACSD-52277** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.7 の場合） – 管理者で新しい注文を作成する際にストアビューを選択した後、管理者ユーザーが適切にリダイレクトされない問題を修正しました。
* **ACSD-50813** （Adobe Commerce >=2.4.5 &lt;2.4.7 の場合） – 管理者が SKU にスラッシュを含むバンドル製品を追加できなかった問題を修正しました。 [!UICONTROL Add Products by SKU] 管理注文に対する機能。
* **ACSD-51630** （Adobe CommerceおよびMagento Open Source >=2.4.3 &lt;2.4.7） – 大量のシステムメッセージが原因で管理ページのダウンロードが遅くなる問題を修正しました。
* **ACSD-51853** （Adobe CommerceおよびMagento Open Source >=2.4.1 &lt;2.4.7 の場合） – コピーしたテキストスタイルが [!UICONTROL Page Builder].
* **ACSD-52160** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.7） – 買い物かご価格ルールに対する商品検証結果が、ルール条件「If an item is FOUND/NOT FOUND in the cart with All/Any these conditions true」に基づいて適切に評価されなかった問題を修正しました。
* **ACSD-51636** （Adobe Commerce >=2.4.5 &lt;2.4.7 の場合） – 必要な役割と権限がすべて揃っているにもかかわらず、会社管理者が顧客アカウントセクションから新しいユーザーを追加できない問題を修正しました。
* **ACSD-51739** （Adobe Commerce >=2.4.6 &lt;2.4.7 の場合） –  `structure_id` は、CompanyTeam GraphQL リクエストでリクエストされます。
* **ACSD-51857** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.7 の場合） – のパフォーマンスが遅い問題を修正しました `aggregate_sales_report_bestsellers_data` 大規模な販売注文に関する cron レポート `sales_order_item` データベース テーブルは、メイン データ クエリの書き込み方法が原因でした。
* **ACSD-48448** （Adobe CommerceとMagento Open Source >=2.4.2 &lt;2.4.7） – 注文のキャンセル中に競合状態の問題が発生し、でエントリが重複する問題を修正しました。 `inventory_reservation` テーブル。
* **ACSD-52689** （Adobe CommerceとMagento Open Source >=2.4.3 &lt;2.4.6） – REST API を使用してAmazon S3 ストレージに画像をアップロードできない問題を修正しました。
* **B2B-2674** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.7 の場合） – 1customAttributeMetadata1 GraphQL クエリにキャッシュ機能を追加します。
* ACSD-44938 の新しいバージョンを追加しました。
* ACSD-46988 の要件を追加しました。

## v1.1.33 {#v1-1-33}

* **ACSD-50478** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.5 の場合） - DB ダンプにトリガーとエラーが含まれる場合にデータベース・ロールバック・コマンドを修正します。 *区切り文字* SQL コマンド。
* **ACSD-50512** （Adobe Commerce >=2.4.5 &lt;2.4.7 の場合） – を修正します。 *エラー：ダウンロード可能なリンクは製品に関連していません。 リンクを確認して、もう一度試してください。* ダウンロード可能な製品のステージング更新の開始日を更新するときに発生するエラー。
* **ACSD-50949** （Adobe CommerceとMagento Open Source >=2.4.2 &lt;2.4.7 の場合） - SKU フィルターと一緒に使用した場合に、詳細検索で価格フィルターが適切な結果を返さない問題を修正しました。
* **ACSD-51645** （Adobe CommerceおよびMagento Open Source >=2.4.6 &lt;2.4.7 の場合） – 新しい買い物かご価格ルールを保存する際にスローされるエラー（拡張子が `Magento_OfflineShipping` が無効になっています。
* **ACSD-50895** （Adobe Commerce >=2.4.5 &lt;2.4.7 の場合） – 問題を修正します。次の場合に適用されます。 [!DNL Google Analytics] 次の場合、3 GTM タグは実行されません。 [!DNL Google Analytics] 4 GTM が設定されていません。
* **ACSD-51102** （Adobe Commerce >=2.4.2 &lt;2.4.7 の場合） – 予定されている更新によってルールが有効になっている場合に、多数の商品に適用されるカタログルールが正しくインデックス化されない問題を修正しました。
* **ACSD-50368** （Adobe CommerceおよびMagento Open Source >= 2.4.3 &lt;2.4.5 の場合） – お客様の `group_id` は、非同期 REST API または非同期バルク REST API を使用して顧客が作成された場合、無視されます。
* **ACSD-51497** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.4.0） || >= 2.4.1 &lt;2.4.7） – 顧客がドロップダウンタイプのカスタム属性でカタログページを並べ替えることができない問題を修正しました。
* **ACSD-51408** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt; 2.4.7 の場合） – 注文項目のステータスが正しくに設定されない問題を修正しました *[!UICONTROL Backordered]*.
* **ACSD-51735** （Adobe CommerceとMagento Open Source >=2.4.4 &lt;2.4.5 の場合） – 注文項目のステータスが正しく設定されない問題を修正しました *[!UICONTROL Ordered]* 商品の在庫が *0*.
* **ACSD-51792** （Adobe CommerceおよびMagento Open Source >=2.4.5 &lt;2.4.6 の場合） – ページに次の場合にインプレッションイベントが発生しない問題を修正しました [!DNL Google Tag Manager] 4 が有効になっています。
* **ACSD-51471** （Adobe Commerce >=2.4.3 &lt;2.4.7 の場合） – 自身に予定アップデートがあるシンプルな商品を使用しているバンドル商品の場合、管理者ユーザーが予定アップデートを保存できない問題を修正しました。
* **ACSD-51700** （Adobe CommerceとMagento Open Source >=2.4.3 &lt;2.4.7 の場合） – 管理画面でダウンロード可能な商品編集ページでストアビューを切り替えると発生するエラーを修正しました。
* **ACSD-51120** （Adobe Commerce >=2.3.7 &lt;2.4.3 の場合） – ステージングアップデートにより更新された CMS ブロックを含む CMS ページのGraphQL GETリクエストのキャッシュがクリアされない問題を修正しました。
* **ACSD-51240** （Adobe Commerce >=2.4.4 &lt;2.4.6 の場合） – 会社登録フォームから登録した場合に、アップロードされたファイルが見つからない問題を修正しました。
* **ACSD-51907** （Adobe Commerce >=2.4.2 &lt;2.4.3 の場合） – 制限付き管理者ユーザーが、オフラインでの払い戻しでクレジットメモを作成できない問題を修正しました。
* **ACSD-52148** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.4 の場合） – 次の問題を修正します [!DNL Google V3 reCAPTCHA] 管理者ログインが失敗する場合があります。
* **ACSD-51431** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.4.7）の場合 – インデクサーのステータスがの問題を修正しました *動作* 変更ログに新しいエントリがない場合でも同様です。
* **ACSD-51892** （Adobe CommerceおよびMagento Open Source >=2.4.6 &lt;2.4.7） – config ファイルが複数回読み込まれるパフォーマンスの問題を修正しました。
* 非推奨（廃止予定）の ACSD-51114。

## v1.1.32 {#v1-1-32}

* **ACSD-49628** （Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.7） – で発生した問題を修正します。 [!UICONTROL Page Builder's] 複数のエラーがあると、管理者はコンテンツ権限のない製品を保存できません。
* **ACSD-51305** （Adobe CommerceとMagento Open Source >=2.4.6 &lt;2.4.7） – 在庫切れの設定可能な子プロダクトがGraphQL レスポンスで使用できない問題を修正しました。
* **ACSD-50621** （Adobe Commerce >=2.3.7 &lt;2.4.7 の場合） – 問題を修正します。次の場合に適用されます。 [!UICONTROL Tier Prices] 複数の web サイト環境で編集しようとすると、共有カタログ内の様々な web サイトが表示されません。
* **ACSD-51041** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.4.0） || >=2.4.1 &lt;2.4.6） – 価格インデクサーのパフォーマンスを向上させます。
* **ACSD-51379** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.4.7 の場合） – でページテキストコンテンツに変更が加えられる問題を修正しました [!UICONTROL Page Builder] は保存されません。
* **ACSD-49480** （Adobe CommerceとMagento Open Source >=2.4.4 &lt;2.4.6）の場合 – 買い物かごに対して買い物かごの価格ルールが 1 つだけ適用される問題を修正しました。
* **ACSD-51230** （Adobe Commerce >=2.3.7 &lt;2.4.7 の場合） – 簡単な商品の一部の返金が注文から処理されると、ギフトカードアカウントが削除される問題を修正しました。
* **ACSD-51238** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.7 の場合） – 設定可能な商品を更新して価格を編集すると、在庫ソースが削除される問題を修正しました。
* **ACSD-50794** （Adobe Commerce >=2.4.1 &lt;2.4.7） – GraphQLからギフトメッセージやギフトラッピングの詳細を削除しても、データベースで更新されない問題を修正しました。
* **ACSD-51528** （Adobe CommerceおよびMagento Open Source >=2.4.5 &lt;2.4.7 の場合） – 次の問題を修正します *x_forwarded_for* に null 値を含む列 *sales_order* テーブル。
* **ACSD-50849** （Adobe Commerce >=2.4.4 &lt;2.4.6） – キャッシュをクリアした後に新しい商品をカテゴリに追加すると、既存の商品の位置と選択が一致しなくなる問題を修正しました。
* **ACSD-51294** （Adobe CommerceおよびMagento Open Source >=2.4.5 &lt;2.4.7） – GTM/GA の価格、数量、税、送料、売上高がに文字列として送信される問題を修正しました。 [!DNL Google Analytics] と GTM です。
* **ACSD-51204** （Adobe CommerceおよびMagento Open Source >=2.4.3 &lt;2.4.7） – クレジットメモを作成した後、完全に売れた商品が在庫に戻らない問題を修正しました。
* **ACSD-51291** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.4-p4） || >=2.4.5 &lt;2.4.5-p3） - 1 つの web サイトへのアクセスを制限された管理者が、複数の web サイトに割り当てられた製品に画像/ビデオを追加できる問題を修正しました。
* ACSD-50336 の新しいバージョンを追加しました。
* パッチ ACSD-49970 を交換してください。

## v1.1.31 {#v1-1-31}

* **ACSD-50345** （Adobe CommerceおよびMagento Open Source >=2.4.3 &lt;2.4.4 || >=2.4.4-p1 &lt;2.4.6） – 支払いに失敗した後、Recaptcha v2 がリロードされない問題を修正しました。
* **ACSD-50817** （Adobe CommerceとMagento Open Source >=2.3.7 &lt;2.4.7） – Cron ジョブを最適化する `sales_clean_quotes` より速く実行します。
* **ACSD-49392** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.4.0） || >= 2.4.1 &lt;2.4.7） – バンドルされた製品の部分払い戻しの後に注文ステータスがクローズに変更される問題を修正しました。
* **ACSD-51036** （Adobe CommerceとMagento Open Source >=2.4.4 &lt;2.4.5） – REST API の同時呼び出し時の競合状態によって、の出荷ステータス情報が上書きされる問題を修正しました [!UICONTROL Items Ordered] テーブル。
* **ACSD-50858** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.7） – バナーコンテンツの読み込みのパフォーマンスを向上します。
* MDVA-39305-v2、ACSD-45169 の新しいバージョンを追加しました。
* パッチ ACSD-50260-v2 を更新しました。

## v1.1.30 {#v1-1-30}

* **ACSD-50336** （Adobe CommerceおよびMagento Open Source >=2.4.4-p1 &lt;2.4.4-p3）の場合 – 商品が再入荷したり、価格が変更されたりしたときに商品のアラートメールが送信されない問題を修正しました。
* **ACSD-50367** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.4.7 の場合） – 値のない複数選択の顧客住所属性が作成される場合に、顧客住所の書き出しが機能しない問題を修正しました。
* **ACSD-49877** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.4.7）の場合 – モバイルでビデオの自動再生が機能しない問題を修正しました [!DNL Safari] ビデオがストリーミングサービスではなく、リモートビデオファイルに直接リンクされている場合。
* **ACSD-50165** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.7 の場合） – エラーを修正します *ファイルを削除できません。 警告！unlink：そのようなファイルまたはディレクトリはありません* は、管理者から JS/CSS キャッシュをフラッシュします。
* **ACSD-49737** （Adobe CommerceとMagento Open Source >=2.4.1-p1 &lt;2.4.7） – カードによる支払いが失敗した後に、クーポンが誤って使用とマークされる問題を修正しました。
* **ACSD-50814** （Adobe CommerceおよびMagento Open Source >=2.4.6 &lt;2.4.7 の場合） – 管理者ユーザーがクレジットメモを作成できない問題を修正しました。
* **ACSD-50116** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.4.7 の場合） – 管理者ユーザーがサブカテゴリレベル 3 以下の URL 書き換えを作成できない問題を修正しました。
* **ACSD-49513** （Adobe CommerceおよびMagento Open Source >=2.4.3 &lt;2.4.5） – 0 バイトのファイルが原因でリモートストレージの同期が失敗する問題を修正しました。
* **ACSD-46683** （Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.7） – 配送料が表示される問題を修正しました *まだ計算されていません*.
* **ACSD-49129** （Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.6） – で発生した問題を修正します。 *[!UICONTROL content]* 属性（base64 画像コード）が `rest/V1/products/sku/media` 製品メディア API の応答。
* **ACSD-50276** （Adobe Commerce >=2.4.0 &lt;2.4.7 の場合） – 複数選択の顧客属性が作成された場合に、顧客登録フォームがストアフロントで機能しない問題を修正しました。
* **ACSD-50527** （Adobe Commerce >=2.3.7 &lt;2.4.7 の場合） – 空の動的ブロックを含んだページを保存したときに発生するエラーを修正します。
* **ACSD-49973** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.5） – GraphQLを通じてバンドル商品を取得するパフォーマンスを向上させます。
* **ACSD-51114** （Adobe CommerceとMagento Open Source >=2.4.3 &lt;2.4.7）の場合 – 非同期インデックス作成が有効になっている場合に、大きなカタログからランダムな商品が消える問題を修正しました。 大規模なカタログの非同期インデックス再作成のパフォーマンスを向上します。
* **B2B-2598** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.7） – キャッシュ機能をに追加 [!UICONTROL availableStores], [!UICONTROL countries], [!UICONTROL country], [!UICONTROL currency]、および [!UICONTROL storeConfig] GraphQL クエリ。
* MDVA-42806、ACSD-48627、ACSD-46815 の新しいバージョンを追加しました。
* ACSD-49773、ACSD-47179、ACSD-48300 のパッチメタデータを更新しました。

## v1.1.29 {#v1-1-29}

* **ACSD-49389** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.7） – 注文が受け取り可能でない場合に、API によって受け取り可能なメールが送信される問題を修正しました。
* **ACSD-49822** （Adobe Commerce >=2.3.7 &lt;2.4.7 の場合） – で更新が行われる問題を修正しました [!UICONTROL Requisition List] ページが「」に反映されない [!UICONTROL Print Requisition List].
* **ACSD-48771** （Adobe CommerceおよびMagento Open Source >=2.4.5 &lt;2.4.7 の場合） – 列ブロックコンテンツタイプを古いものからアップグレードする際の問題を修正しました [!DNL Page Builder] バージョン。
* **ACSD-49464** （Adobe Commerce >=2.3.7 &lt;2.4.7 の場合） - orderId が異なる場合に、請求書、出荷、クレジットメモがアーカイブから戻されない問題を修正しました。
* **ACSD-49773** （Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.6 の場合） - AWS S3 をリモートストレージとして使用した場合に製品の書き出しが失敗する問題を修正しました。
* **ACSD-49748** （Adobe Commerce >=2.3.7 &lt;2.4.7 の場合） – 招待状を送信できない問題を修正しました。
* **ACSD-49502** （Adobe Commerce >=2.4.3 &lt;2.4.7 の場合） – ダウンロード可能な商品にステージングアップデートが適用された後、ダウンロード可能なリンクが適切に更新されない問題を修正しました。
* **ACSD-49527** （Adobe Commerce >=2.4.2 &lt;2.4.7 の場合） – GraphQLの会社ロールでページネーションが正しく表示されない問題を修正しました。
* **ACSD-49706** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.4.7 の場合） – 値が選択されていないときに、ビジュアルスウォッチ属性のデフォルト値が保存される問題を修正しました。
* **ACSD-49835** （Adobe CommerceおよびMagento Open Source >=2.4.5 &lt;2.4.7 の場合） – デフォルトのチェックボックス値を使用が複数選択属性のストアレベルで正しく保存されない問題を修正しました。
* **ACSD-49898** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.6） – バンドルされた商品の特別価格が 1000 を超えると、商品グリッドが例外をスローする問題を修正しました。
* **ACSD-50234** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.4.5 の場合） – で注文する場合に、確認メールに間違ったお客様の名前が表示される問題を修正します。 [!DNL PayPal].
* **ACSD-49960** （Adobe CommerceおよびMagento Open Source >=2.4.5 &lt;2.4.7 の場合） – お客様の注文グリッドで日付によるフィルタリングが機能しない問題を修正しました。
* **ACSD-49849** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.4.6） – 顧客の電子メールが置き換えられた問題を修正しました [!DNL PayPal] で注文する際のメール [!DNL PayPal Express] GraphQL経由
* **ACSD-49839** （Adobe Commerce >=2.3.7 &lt;2.4.7 の場合） – 製品の SKU に一重引用符または二重引用符がある場合に、共有カタログの価格と構造が管理者でエラーをスローする問題を修正しました。
* **ACSD-49970** （Adobe CommerceとMagento Open Source >=2.4.5 &lt;2.4.7 の場合） – GraphQL エラーの誤った処理を次の場合に修正します [!DNL New Relic] レポートが有効になっています。
* **ACSD-50260** （Adobe CommerceとMagento Open Source >=2.4.5 &lt;2.4.7 の場合） – GraphQL製品の検索結果が 10,000 件のみに制限される問題を修正しました。
* **ACSD-48813** （Adobe CommerceとMagento Open Source >=2.4.3 &lt;2.4.7 の場合） – 属性の検索重み付けに基づいて検索で関連する結果が表示されない問題を修正しました。

## v1.1.28 {#v1-1-28}

* **ACSD-48204** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.4.3 の場合） – Yes/No 属性に基づいて作成されたカタログ価格ルールが選択したスコープを考慮しない問題を修正します。
* **ACSD-47704** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.4.7） – バンドルされた商品に在庫商品のみの価格が表示される問題を修正しました。
* **ACSD-49370** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.4.7）の場合 – の問題を修正します。 *日時* 製品属性にはが含まれています *FilterMatchTypeInput* GraphQL スキーマにと入力します。
* **ACSD-48807** （Adobe CommerceとMagento Open Source >=2.4.1 &lt;2.4.7 の場合） - GraphQLを使用してカスタマープロダクションレビューが storereview でフィルタリングされない問題を修正しました。
* **ACSD-49433** （Adobe CommerceとMagento Open Source >=2.4.3 &lt;2.4.7）の場合 – オープン金額を含むギフトカードの買い物かごに、デフォルト金額が小計として表示される問題を修正しました。
* **ACSD-48866** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.4.7） – カテゴリの RSS フィードをリクエストするとエラーが発生する問題を修正しました。
* **ACSD-48784** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.4.7）の場合 – 顧客セグメント価格が顧客グループ間で誤ってキャッシュされる問題を修正しました。
* **ACSD-48857** （Adobe CommerceおよびMagento Open Source >=2.4.3 &lt;2.4.7 の場合） – ページビルダーで編集した後、ユーザーが変更を保存できない問題を修正しました。
* **ACSD-49065** （Adobe CommerceとMagento Open Source >=2.3.7 &lt;2.4.7 の場合） – カスタム在庫にのみ割り当てられている場合に、管理者に見積もり品目が表示されない問題を修正しました。
* **ACSD-49179** （Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.7） – 店舗によって通貨が異なる場合に、「注文レポート」に誤った金額が表示される問題を修正しました。
* **ACSD-49286** （Adobe CommerceとMagento Open Source >=2.4.3 &lt;2.4.7 の場合） – ページに複数の商品ウィジェットが存在する場合に、商品が買い物かごに 2 回追加される問題を修正しました。
* **ACSD-49574** （Adobe Commerce >=2.4.4 &lt;2.4.7 の場合） – GraphQLを使用して、買い物かごでのギフトカード製品のアップデートをサポートする機能を追加しました。
* パッチを更新しました：ACSD-48694。

## v1.1.27 {#v1-1-27}

* **ACSD-48362** （Adobe Commerce >=2.4.1 &lt;2.4.7 の場合） – 交渉可能な見積もりを使用して注文を行う際に、新しい配送先住所の代わりにデフォルトの配送先住所が使用される問題を修正しました。
* **ACSD-48059** （Adobe Commerce >=2.3.7 &lt;2.4.7 の場合） – マーチャントが「」を保存できない問題を修正しました[!UICONTROL Match product by rule]」というエラーメッセージが表示されます。
* **ACSD-48216** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.3.8） || >=2.4.0 &lt;2.4.7） – 問題を修正しました。ここで [!UICONTROL AUTO_INCREMENT] の [!UICONTROL inventory_source_item] テーブルの増加 [!UICONTROL UPDATE] 操作。
* **ACSD-47908** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.3.8） || >=2.4.0 &lt;2.4.7） – チェックアウト時の出荷手順でソースと数量を選択する際に、「0 以下の値が想定されます」というエラーを修正しました。
* **ACSD-49497** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.4.6） – 出荷後に注文が処理中ステータスのままになり、部分的な払い戻しが適用される問題を修正しました。
* **ACSD-48694** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.3.8） || >=2.4.1 &lt;2.4.7） – 「無効な状態変更がリクエストされました」というエラーによって、お客様の注文が妨げられる問題を修正しました。
* **ACSD-49013** （Adobe CommerceおよびMagento Open Source >=2.4.3 &lt;2.4.7 の場合） – 一括 API を使用して顧客を作成する際に、メールの確認が web サイトのロケールに翻訳されない問題を修正しました。
* **ACSD-48164** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.4.7 の場合） – 制限付き管理者が web サイトレベルの値を保存できない問題を修正しました。
* **ACSD-48404** （Adobe CommerceとMagento Open Source >=2.4.0 &lt;2.4.4 の場合） – ブラウザーの「戻る」ボタンを押したときに「カテゴリのページネーションを保存」がエラーを発生させる問題を修正しました。
* **ACSD-48634** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.4.7 の場合） – 「」の場合にステージングアップデートページで発生する JS エラーを修正しました[!UICONTROL Google Analytics Content Experiments]」が有効になっています。
* **ACSD-49042** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.5 の場合） – 順不同の商品をストアフロントから注文できない問題を修正しました。
* パッチを更新：ACSD-48366、ACSD-48661。

## v1.1.26 {#v1-1-26}

* **ACSD-47937** （Adobe CommerceおよびMagento Open Source 2.4.4 用） || >=2.4.5 &lt;2.4.6） – アプリケーションレベルのキャッシュが原因で価格下落通知が常に送信されない問題を修正しました。
* **ACSD-48661** （Adobe CommerceとMagento Open Source >=2.3.7 &lt;2.4.7） – 会社のクレジット制限が 999 を超える場合、コンマ区切り記号を使用すると、検証エラーが原因で会社を保存できない問題を修正しました。
* **ACSD-48773** （Adobe CommerceとMagento Open Source >=2.4.2 &lt;2.4.7 の場合） – 報酬ポイントのメールテンプレートが間違ったストアから取得される問題を修正しました。
* **ACSD-48587** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.4.7 の場合） – products ウィジェットのマッチングルールのHTML特殊文字によって、一致する商品が表示されない問題を修正しました。
* **ACSD-48212** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.4.6 の場合） – 商品の読み込みによって商品が誤ったソースに割り当てられる問題を修正しました。
* **ACSD-47988** （Adobe CommerceとMagento Open Source >=2.3.7 &lt;2.4.6 の場合） – 製品の書き出しで、ページビルダーの製品説明からHTMLタグがトリミングされる問題を修正しました。
* **ACSD-48366** （Adobe CommerceとMagento Open Source >=2.4.4 &lt;2.4.6 の場合） – ストックに戻るメールテンプレートに商品イメージが表示されない問題を修正しました。
* **ACSD-48417** （Adobe CommerceとMagento Open Source >=2.4.5 &lt;2.4.7 の場合） – 商品のスケジュールを変更して別の商品を保存した後に SQL エラーが表示される問題を修正しました。

## v1.1.25 {#v1-1-25}

* **ACSD-48058** （Adobe CommerceとMagento Open Source >=2.4.5 &lt;2.4.6 の場合） – バンドル製品がどの web サイトにも割り当てられていない場合に、製品の価格の再インデックスが機能しない問題を修正しました。
* **ACSD-48262** （Adobe CommerceとMagento Open Source >=2.4.5 &lt;2.4.6 の場合） – 「1 ページあたりの全商品の許可」設定が「はい」に設定されている場合に、フロントエンドに商品が表示されない問題を修正しました。
* **ACSD-48293** （Adobe CommerceとMagento Open Source >=2.4.3 &lt;2.4.4） – 完売した子商品が在庫に戻ったときに複合商品が在庫切れになる問題を修正しました。
* **ACSD-47520** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.6 の場合） – クレジットメモを作成したときに顧客が報酬ポイントを失う問題を修正しました。
* **ACSD-48044** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.4 の場合） – 複数送料の 1 回の注文に複数のギフトカードを適用すると、注文できなくなる問題を修正しました。
* **ACSD-48300** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.6 の場合） – 設定可能な商品が削除された場合に戻り値を作成できない問題を修正しました。
* **ACSD-47910** （Adobe CommerceとMagento Open Source >=2.4.4 &lt;2.4.6） – それぞれのエンティティグリッドで、注文、請求書、出荷、およびクレジットメモが見つからない問題を修正します。
* **ACSD-47292** （Adobe CommerceとMagento Open Source >=2.4.4 &lt;2.4.6） – 「在庫切れの商品を表示」が「はい」に設定されている場合に、GraphQL レスポンスで在庫切れのバンドル商品が使用できない問題を修正しました。
* **ACSD-48234** （Adobe CommerceとMagento Open Source >=2.4.5 &lt;2.4.6 の場合） – 「在庫切れを表示」オプションが有効になっている場合に、カタログ検索結果に誤ったカテゴリ項目数が表示される問題を修正しました。
* **ACSD-48313** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.5 の場合） – 属性値にコンマが含まれている場合に、「configurable_variations」列が解析されない問題を修正しました。 「additional_attributes」にも同じ解析アルゴリズムを使用します。
* **ACSD-48627** （Adobe CommerceとMagento Open Source >=2.4.5 &lt;2.4.6 の場合） – 在庫切れの設定可能な商品が、GraphQL リクエストを送信して買い物かごの詳細を取得する際にエラーを発生させる問題を修正しました。
* パッチを更新しました：MDVA-39384。

## v1.1.24 {#v1-1-24}

* **ACSD-45168** （Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.6） – を持つ製品で SEO に対応する URL が生成されない問題を修正しました。 *url_key* ストアビューレベルで上書きされた属性。
* **ACSD-46865** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.6） – 非同期インデックス作成が有効な場合に、出荷およびクレジットメモグリッドが入力されない問題を修正しました。
* **ACSD-47004** （Adobe CommerceとMagento Open Source >=2.4.2 &lt;2.4.6） – VAT ID のない請求先住所に VAT が適用されない問題を修正しました。
* **ACSD-47803** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.6） – 在庫切れの設定可能な商品スウォッチが使用可能と表示される問題を修正しました。
* **ACSD-47137** （Adobe CommerceとMagento Open Source >=2.4.4 &lt;2.4.6） – pub/media フォルダーが非常に大きい場合に、画像ギャラリーの読み込み速度を向上させます。
* **ACSD-46770** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.6 の場合） – 管理者向けの注文メールが、 *E メールでの注文の確認* をオフにします。
* **ACSD-47955** （Adobe CommerceとMagento Open Source >=2.4.4 &lt;2.4.6 の場合） – GraphQLで買い物かごの割引が正しく表示されない問題を修正しました。
* **ACSD-46617** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.6 の場合） – 次の問題を修正します *チェックアウトを続行* 小計が設定されたよりも大きい場合でも、ボタンはグレー表示されます *最小注文金額*.
* **ACSD-47079** （Adobe CommerceとMagento Open Source >=2.4.4 &lt;2.4.5 の場合） - REST APIPOST/rest/V1/inventory/source-items を使用してサブプロダクトのストックステータスが変更された場合に、複合プロダクト（バンドル、グループ化、設定可能）のストックステータスが更新されない問題を修正しました。
* **ACSD-47336** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.6） – 修正点 *エラーが発生しました。* Commerce管理者で通知を無効にするとエラーが発生する。
* **ACSD-47559** （Adobe CommerceとMagento Open Source >=2.4.0 &lt;2.4.6 の場合） – メールテンプレートのプレビューエリアが完全には表示されない問題を修正しました。
* **ACSD-47920** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.6） –  *ゲストのチェックアウトを許可* はオフになっています。
* 交換したパッチ：MDVA-39305、MDVA-42855。

## v1.1.23 {#v1-1-23}

* **ACSD-47179** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.6 の場合） – 特定の範囲へのアクセスが制限されている管理者が製品レビューを削除できない問題を修正しました。
* **ACSD-47107** （Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.5 の場合） – カスタム商品オプションにカタログ価格ルール割引が適用される問題を修正しました。
* **ACSD-47232** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.6） – 合計重量条件を含むクーポンを管理者に適用できない問題を修正しました。
* **ACSD-46519** （Adobe CommerceとMagento Open Source >=2.4.1 &lt;2.4.6 の場合） – GraphQL categoryList リクエストがアンカカテゴリに対して誤った product_count を返す問題を修正しました。
* **ACSD-47027** （Adobe CommerceとMagento Open Source >=2.4.2 &lt;2.4.6 の場合） – 低速の updateCompanyRole GraphQL リクエストを修正します。
* **ACSD-47666** （Adobe CommerceとMagento Open Source >=2.4.0 &lt;2.4.6 の場合） – フィルター機能が管理者/ システム /権限/ ユーザーロール / ロールユーザーのグリッドで機能しない問題を修正しました。
* **ACSD-47497** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.6 の場合） – 管理下の設定に「サービス」タブが表示されない問題を修正しました。
* パッチを更新しました：ACSD-47743。
* 交換したパッチ：MDVA-42807。

## v1.1.22 {#v1-1-22}

* **ACSD-47444** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.3 の場合） – を修正します。 _ブール型の値の配列オフセットにアクセスしようとしています_ php 7.4 上で既知の製品に対して存在しない特定のカテゴリパスにアクセスする際にエラーが発生します。
* **ACSD-47332** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.6） – UTC で 00:00～00:59 の間に動作している場合にのみ報告されるエラーで cron が失敗する問題を修正しました。
* **ACSD-47280** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.6 の場合） – 特定の範囲で共有カタログ機能を無効にしても正しく機能しない問題を修正しました。
* **ACSD-47106** （Adobe CommerceとMagento Open Source >=2.4.4 &lt;2.4.6 の場合） – 会社作成ページの新しいカスタム属性に値を保存できない問題を修正しました。
* パッチを更新しました：ACSD-45143。

## v1.1.21 {#v1-1-21}

* **ACSD-46809** （Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.6 の場合） – 多数の商品ソースを割り当てたときにエラーが発生する問題を修正しました。
* **ACSD-46856** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.6） – システム /設定/インポート/詳細価格を選択して、パフォーマンスアップデート層の価格を改善します。
* **ACSD-46541** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.4 の場合） – 注文項目が削除された場合に、管理者ユーザーがクレジットメモを作成できない問題を修正しました。
* **ACSD-46581** （Adobe CommerceとMagento Open Source >=2.4.0 &lt;2.4.6） – ショッピングカートで国を選択した後、推定税合計が更新されない問題を修正しました。
* **ACSD-46618** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.6 の場合） – ログインしているユーザーの商品リストウィジェットに誤ったキャッシュ価格が表示される問題を修正しました。
* **ACSD-46674** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.6 の場合） – 画像タイプのカスタムオプションが顧客のメールでHTMLとして表示される問題を修正しました。
* **ACSD-46988** （Adobe CommerceとMagento Open Source >=2.4.4 &lt;2.4.6 の場合） - GraphQLの「通貨」 API リクエストがカスタム通貨に対して NULL 値を返す問題を修正しました。
* **ACSD-47076** （Adobe CommerceとMagento Open Source >=2.4.1 &lt;2.4.5） – ストアフロントで Vimeo の動画を再生できない問題を修正しました。
* **ACSD-45071** （Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.4 の場合） – インポート時にデフォルトソースが商品に追加される問題を修正しました。
* **AC-3023** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.6） – DHL スキームを最新バージョン 10.0 に更新します。
* パッチを更新しました：MDVA-42584。
* 交換したパッチ：MDVA-36572、ACSD-45241。

## v1.1.20 {#v1-1-20}

* **ACSD-46520** （*Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.5*） – 店舗クレジットを使用して返金すると、ユーザーに間違った注文ステータスが表示される問題を修正しました。
* **ACSD-46703** （*Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.6*） – 製品の編集ページにカスタムオプションをドラッグ&amp;ドロップできない問題を修正しました。
* **ACSD-44851** （*Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.6*） – サブカテゴリを持つカテゴリを開いたり展開したりできない問題を修正しました。
* **ACSD-46815** （*Adobe CommerceおよびMagento Open Source >=2.4.5 &lt;2.4.6*） – カテゴリツリーリクエストが 20 個のカテゴリに制限される問題を修正しました。
* **ACSD-45675** （*Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.6*） – 製品の書き出しでをカテゴリ名として使用する問題を修正します *デフォルトのストア表示* スコープ。
* **ACSD-46869** （*Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.6*） – 買い物かごの中の設定可能な製品が経由で更新されない問題を修正しました *PUT REST API* 製品数量を変更せずにお申し出ください。
* **MDVA-42768-V2** （*Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.3*） – 設定可能な製品に標準価格が次のように表示される問題を修正します *0* 条件 *在庫切れを表示* 等しい *はい*.
* 更新されたパッチ：MDVA-44562、ACSD-46213、MDVA-41305、MDVA-38346、MDVA-13203。
* 非推奨パッチ：MDVA-42768。

## v1.1.19 {#v1-1-19}

* **ACSD-46213** （*Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.3*） – カテゴリツリーリクエストが 20 個のカテゴリに制限される問題を修正しました。
* **ACSD-45781** （*Adobe CommerceおよびMagento Open Source >=2.4.1 &lt;2.4.2*） – モバイルでストアフロント検索フィールドが表示されない問題を修正しました。
* **ACSD-46192** （*Adobe CommerceおよびMagento Open Source >=2.3.6 &lt;2.4.5*） – を使用したの問題を修正します `async/bulk/V1/configurable-products/bySku/options` エンドポイント。
* **ACSD-46404** （*Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.5*） – 管理者ユーザーが 2.4.4 にアップグレードした後でログインできない問題を修正しました。
* 更新されたパッチ：MDVA-41305、MDVA-38626、MDVA-38728、MDVA-41061-V4、MDVA-42269、MDVA-39305。

## v1.1.18 {#v1-1-18}

* **ACSD-45817** （*Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.4*） – 特定のストアのGraphQL商品ミューテーションが、リクエストされたストアに割り当てられていないものを含め、設定可能なすべてのバリアントを返す問題を修正しました。
* **ACSD-46146** （*Adobe CommerceおよびMagento Open Source >=2.3.0 &lt;2.4.6*） – 管理者から注文した後に、2 通の注文確認メールが送信される問題を修正しました。
* **ACSD-45255** （*Adobe Commerce >=2.4.3 &lt;2.4.6*） – 制限付き管理者ユーザーに関する低在庫レポート ページの例外を修正します。
* **ACSD-45488** （*Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.6*） – 複数のソースを持つ設定可能な製品が、在庫として自動的に返されない問題を修正しました。
* **ACSD-45754** （*Adobe CommerceおよびMagento Open Source >=2.3.1 &lt;2.4.6*） – クーポンを買い物かごに適用した後に報酬ポイントが追加されない問題を修正しました。
* **ACSD-45849** （*Adobe Commerce >=2.4.3 &lt;2.4.4*） – ステージング更新が適用された後にビデオメタデータが失われる問題を修正しました。
* **ACSD-45257** （*Adobe CommerceおよびMagento Open Source >=2.3.4 &lt;2.4.4*） – GraphQLで買い物かごの割引が正しく表示されない問題を修正しました。
* **ACSD-44938** （*Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.4*） – の問題を修正します。 `VAT_ID` は、ゲストユーザーのGraphQL リクエストでは適用できません。
* パッチを更新しました：MDVA-43417。

## v1.1.17 {#v1-1-17}

* **ACSD-45241** （*Adobe CommerceおよびMagento Open Source >=2.3.5 &lt;2.4.4*） – クレジットメモを作成した後に、仮想製品の在庫数が誤って計算される問題を修正します。
* **ACSD-43887** （*Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.5*） – 会社の発注書が有効になっている場合に、チェックアウトの支払いページに誤った詳細が表示される問題を修正しました。
* **ACSD-45143** （*Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.5*） – 問題を修正します。 `setShippingAddressesOnCart` ミューテーションでは、数値地域コードをに設定することはできません。 *地域*.
* **ACSD-44591** （*Adobe CommerceおよびMagento Open Source >=2.4.3 &lt;2.4.6*） - CAPTCHA 確認が行われずに注文した場合に発生するエラーを修正します。
* **ACSD-45520** （*Adobe CommerceおよびMagento Open Source >=2.3.0 &lt;2.4.6*） – ユーザーが買い物かごから設定可能な製品を編集する際に、製品の詳細ページでスウォッチオプションが事前に選択されていない問題を修正しました。
* **ACSD-45169** （*Adobe CommerceおよびMagento Open Source >=2.4.1 &lt;2.4.6*） – の問題を修正します。 [!DNL Visual Merchandiser] では、ステージング更新が適用された後、設定可能な製品の正しい在庫と価格が表示されません。
* **ACSD-45424** （*Adobe CommerceおよびMagento Open Source >=2.3.4 &lt;2.4.6*） – 部分的な払い戻し（クレジットメモ）の後に、誤った予約報酬が作成される問題を修正します。
* **MDVA-42807** （*Adobe CommerceおよびMagento Open Source >=2.3.1 &lt;2.4.6*） – カスタムの通貨記号がストアフロントに表示されない問題を修正しました。
* パッチを更新しました：MDVA-42689、AC-3022。

## v1.1.16 {#v1-1-16}

* **MDVA-44703** （*Adobe CommerceおよびMagento Open Source >=2.4.3 &lt;2.4.4*） – 制限された管理者ユーザーの注文レポートの注文合計が誤って計算される問題を修正します。
* **MDVA-44940** （*Adobe CommerceおよびMagento Open Source >=2.4.3 &lt;2.4.4*） – カテゴリを管理者から保存する際に発生する SQL エラーを修正します。
* **MDVA-44562** （*Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.2-p2*）：デフォルト以外のストア表示から発生したGraphQL リクエストにかかわらず、見積書品目のデフォルト以外のストア ID がデフォルトのストア ID で上書きされる問題を修正しました。
* **MDVA-43167** （*Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.4*） – 管理者ユーザーがすべての注文を選択した際に、管理者の注文グリッドの一括アクションが複数ページに適用されない問題を修正しました。
* **MDVA-44044** （*Adobe CommerceおよびMagento Open Source >=2.3.0 &lt;2.4.2-p2*） – 製品を新しい web サイトに割り当てた後に、製品がカテゴリページに表示されない問題を修正しました。
* **MDVA-42509** （*Adobe CommerceおよびMagento Open Source >=2.3.3 &lt;2.4.4*） – クイックオーダーの CSV をアップロードできなかったことで、 *Cookie を送信できません* エラー。
* パッチを更新：MDVA-41061、MDVA-42584。
* 新しいのプレフィックス [!DNL Quality Patches Tool] パッチの変更元 *MDVA* 対象： *ACSD* 内部プロセスが変更されたためです。

## v1.1.15 {#v1-1-15}

* **MDVA-40961** （*Adobe CommerceおよびMagento Open Source >=2.4.3 &lt;2.4.4*） – 商品の最小数量が既に買い物かごに含まれている場合に、その商品を買い物かごに追加できない問題を修正しました。
* **MDVA-44887** （*Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.5*） – を修正します。 *不明な SyntaxError：予期しないトークン「const」* 管理パネルにエラーが発生しました。
* **MDVA-43718** （*Adobe CommerceおよびMagento Open Source >=2.3.0 &lt;2.4.5*） – 修正点 *コンシューマーは %resources へのアクセスを許可されていません。* カスタム統合から共有カタログにアクセスすると表示されるエラー。
* **MDVA-44660** （*Adobe CommerceおよびMagento Open Source >=2.4.2-p1 &lt;2.4.5*） – アクセント記号が大きい問題を修正します ``` ` ``` 顧客の姓と名には使用できませんでした。
* **MDVA-40896** （*Adobe CommerceおよびMagento Open Source >=2.4.3 &lt;2.4.4*） – を修正します。 *エラー：TypeError：引数 3 がMagentoに渡されました* 非同期製品バルク API のエラー。
* **MDVA-38559** （*Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.3*） – を修正します。 */V1/customers/search API* 複数のサブスクリプションを使用しているお客様の場合、エラーが発生します。
* **MDVA-44533** （*Adobe CommerceおよびMagento Open Source >=2.3.1 &lt;2.4.4*） – 割引がバンドルの子製品に誤って適用される問題を修正します。
* パッチを更新：MDVA-41061、MDVA-42269。

## v1.1.14 {#v1-1-14}

* **MDVA-43983** （*Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.5*） – 製品の問題を修正しました *個別に表示されない* カタログの詳細検索結果には、引き続き表示されます。
* **MDVA-44100** （*Adobe CommerceおよびMagento Open Source >=2.4.3 &lt;2.4.5*） – すべての FPT が買い物かごの最後の製品に割り当てられ、他の製品でリセットされる問題を修正します。
* **MDVA-43605** （*Adobe CommerceおよびMagento Open Source >=2.3.1 &lt;2.4.5*） - Rest API を使用する際に、注文データが行の合計に対して負の値を返す問題を修正しました。
* **MDVA-43102** （*Adobe CommerceおよびMagento Open Source >=2.3.1 &lt;2.4.5*） – REST API を使用して払い戻しを行った際に、販売可能数量が正しく更新されない問題を修正しました。
* **MDVA-43178** （*Adobe CommerceおよびMagento Open Source >=2.4.3-p2 &lt;2.4.5*） - GraphQLでカスタムストアのカスタムトークンを取得できない問題を修正しました。
* **MDVA-43859** （*Adobe CommerceおよびMagento Open Source >=2.4.1 &lt;2.4.5*） – エラーが発生した問題を修正します *customerId =の該当するエンティティがありません* 削除された顧客がログインしようとすると、がログに記録されます。
* **MDVA-44147** （*Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.5*） – GraphQL リクエストが購買依頼リストを返さない問題を修正します。
* **MDVA-44505** （*Adobe CommerceおよびMagento Open Source >=2.4.1 &lt;2.4.3*） – 報酬ポイントの適用GraphQLが総計を更新しない問題や、注文処理中に店舗クレジットが複数回適用される問題を修正します。
* 更新されたパッチ：MDVA-29148、MDVA-36464-V5、MDVA-42584、MDVA-39993-V2。

## v1.1.13 {#v1-1-13}

* **MDVA-42969** （*Adobe CommerceおよびMagento Open Source >=2.4.1 &lt;2.4.3*） – 顧客セグメントがに設定されている場合にのみ、関連製品ルールが機能する問題を修正します *すべて*.
* **MDVA-39605** （*Adobe CommerceおよびMagento Open Source >=2.3.4 &lt;2.4.5*） - Redis キャッシュ TTL （有効期限）の値が間違っている問題を修正しました。
* **MDVA-43862** （*Adobe CommerceおよびMagento Open Source >=2.3.3 &lt;2.4.5*） – GraphQLが原因で顧客が買い物かごの商品を更新できない問題を修正しました *UpdateCartItems ミューテーション* エラー。
* **MDVA-43824** （*Adobe CommerceおよびMagento Open Source >=2.3.6 &lt;=2.3.7-p3 || >=2.4.1 &lt;2.4.5*） – 割引付きの注文のキャンセル時にエラーが表示される問題を修正しました。
* **MDVA-43451** （*Adobe CommerceおよびMagento Open Source >=2.4.3 &lt;2.4.5*） – エラーが発生した問題を修正します *リクエストされたストアが見つかりませんでした。 ストアを確認して、もう一度試してください。* 特定の web サイトの共有カタログを設定する際に表示されます。
* **MDVA-43491** （*Adobe CommerceおよびMagento Open Source >=2.3.5 &lt;2.4.5*） – マルチストア web サイトの製品をインポートした際に、ベース画像ラベルが更新されない問題を修正しました。
* **MDVA-43601** （*Adobe CommerceおよびMagento Open Source >=2.3.0 &lt;2.4.5*） – 完全な再インデックス後にトリガーが見つからない問題を修正します。
* **MDVA-42046** （*Adobe CommerceおよびMagento Open Source >=2.3.4 &lt;=2.3.5-p2 || >=2.4.0 &lt;2.4.5*） – 製品の更新時に、日付入力フィールドを持つ製品属性に間違った値が割り当てられる問題を修正しました。
* **MDVA-43935** （*Adobe CommerceおよびMagento Open Source >=2.4.1 &lt;2.4.5*） – アップセル製品が 2 回表示される問題を修正しました。
* **MDVA-44188** （*Adobe CommerceおよびMagento Open Source >=2.4.3 &lt;2.4.5*） – システムから発行される、次を含むメールの問題を修正しました `.-` のアドレスは送信されません。
* **MDVA-42283** （*Adobe CommerceおよびMagento Open Source >=2.3.0 &lt;2.4.5*） – フランス語ロケールの管理順序グリッドの日時形式が無効な問題を修正しました。
* 更新されたパッチ：MDVA-41061-V2、MDVA-36309、MDVA-30862、MDVA-39713。
* にパッチメタデータを追加しました [!DNL Site-Wide Analysis Tool].

## v1.1.12 {#v1-1-12}

* **MDVA-39713** （*Adobe CommerceおよびMagento Open Source >=2.3.0 &lt;2.3.6*） – ユーザーがスケジュールされたアクティブな更新の開始時刻を編集できる問題を修正します。
* **MDVA-42410** （*Adobe CommerceおよびMagento Open Source >=2.3.0 &lt;2.4.5*） – クーポンレポートにデフォルトの基本通貨のみが表示される問題を修正しました。
* **MDVA-41136** （*Adobe CommerceおよびMagento Open Source >=2.3.0 &lt;2.4.5*） – 有効期限がの問題を修正します `mage-cache-sessid` が拡張されないので、顧客データがクリーンアップされます。
* **MDVA-39993** （*Adobe CommerceおよびMagento Open Source >=2.3.5 &lt;=2.3.7-p2 || >=2.4.0 &lt;2.4.4*） – API を通じて行われたインベントリの変更が、フロントエンドの製品ページに反映されない問題を修正しました。
* **MDVA-42855** （*Adobe CommerceおよびMagento Open Source >=2.4.3 &lt;2.4.5*） – チェックアウト時に新しい顧客アドレスがアドレス帳に保存されない問題を修正しました。
* **MDVA-42645** （*Adobe CommerceおよびMagento Open Source >=2.4.3 &lt;2.4.5*） – ストアクレジット機能が無効になっている場合に、管理者が報酬ポイントを返金できない問題を修正します。
* **MDVA-43414** （*Adobe CommerceおよびMagento Open Source >=2.3.6 &lt;=2.3.7-p2*） – を実行した際に発生する PHP の致命的エラーを修正する `inventory.reservations.updateSalabilityStatus` 数値 SKU でコンシューマーをキューに登録します。
* **MDVA-41628** （*Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.5*） – 新しいモジュールが追加されると、既存の制限付き管理者ユーザーが新しいリソースにアクセスできる問題を修正しました。
* **MDVA-43348** （*Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.5*） – ギフトカードのGraphQL リクエストが、次の場合にエラーを表示する問題を修正しました `gift_card_options` contain *uid*.
* **MDVA-39546** （*Adobe CommerceおよびMagento Open Source >=2.3.0 &lt;2.4.5*） – ステージング更新の開始日を、編集中の現在の日付より前の日付に設定できてしまう問題を修正しました。
* **MDVA-42950** （*Adobe CommerceおよびMagento Open Source >=2.3.0 &lt;2.4.5*） – 製品ページでビデオが再生されない問題を修正しました。
* **MDVA-42689** （*Adobe CommerceおよびMagento Open Source >=2.3.0 &lt;2.4.4*） – Adobe Commerceでエラーがスローされる問題を修正しました *整合性制約違反* 読み込み中に製品カテゴリの更新中にエラーが発生しました。
* **MDVA-41229** （*Adobe CommerceおよびMagento Open Source >=2.3.0 &lt;2.4.5*） – 設定可能な製品の読み込み後、バックエンドで使用可能な画像がフロントエンドに表示されない問題を修正しました。
* **MDVA-43731** （*Adobe CommerceおよびMagento Open Source >=2.4.3 &lt;2.4.4*） – の問題を修正します。 *シノニムの検索* 値をに追加すると機能しなくなる *一致する最小用語*.
* **MDVA-43232** （*Adobe CommerceおよびMagento Open Source >=2.3.4 &lt;2.4.5*） – で製品を並べ替える際の問題を修正しました [!DNL Visual Merchandiser] [ 下/上に特別価格を適用 ] を選択すると、カテゴリの保存中にエラーが発生します。
* **MDVA-43726** （*Adobe CommerceおよびMagento Open Source >=2.3.3 &lt;2.4.3*） – 部分的な再インデックス後に、ストアレベル属性の一致に基づくカタログ価格ルールが適用されない問題を修正しました。
* パッチを更新：MDVA-36464、MDVA-37478、MDVA-38608。
* にパッチメタデータを追加しました [!DNL Site-Wide Analysis Tool].

## v1.1.11 {#v1-1-11}

* **MDVA-42790** （*Adobe CommerceおよびMagento Open Source >=2.4.3 &lt;2.4.5*） – 特定の web サイトの製品価格属性を REST API で更新できない問題を修正しました。
* **MDVA-41350** （*Adobe CommerceおよびMagento Open Source >=2.3.0 &lt;2.4.5*） – 制限付きアクセスを持つ管理者ユーザーが、SKU によって役割の範囲外の製品を順番に追加する際に例外がスローされる問題を修正しました。
* **MDVA-42269** （*Adobe CommerceおよびMagento Open Source >=2.4.3-p1 &lt;2.4.5*） – により管理者ユーザーが管理者にログインできない問題を修正しました *TypeError: strtotime （）は、パラメータ 1 が文字列であること、指定された null であることを想定しています* エラー。
* **MDVA-40830** （*Adobe CommerceおよびMagento Open Source >=2.3.0 &lt;2.4.5*） – 発注時に店舗クレジットが複数回適用される問題を修正します。
* **MDVA-42237** （*Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.5*） – 下位製品価格が変更された後、設定可能な製品特別価格が更新されない問題を修正しました。
* **MDVA-42520** （*Adobe CommerceおよびMagento Open Source >=2.4.3 &lt;2.4.4*） – 次の場合に税率が 2 回適用される問題を修正します *国境を越えた貿易を可能にする* が使用されます。
* 更新されたパッチ：MDVA-27239、MDVA-39305、MDVA-41236、MDVA-36832。
* 非推奨パッチ：MDVA-37725。

## v1.1.10 {#v1-1-10}

* **MDVA-38728** （*Adobe CommerceおよびMagento Open Source >=2.3.2 &lt;2.4.5*） – 属性の一括更新によって、変更後にのみデフォルトストアの URL 書き換えが作成される問題を修正しました *製品の表示*.
* **MDVA-43091** （*Adobe CommerceおよびMagento Open Source >=2.4.3 &lt;2.4.4*） – バックエンドで管理者からバンドル製品を注文するとエラーが発生する問題を修正します *この商品には小数点以下の数量を使用できません*.
* **MDVA-40816** （*Adobe CommerceおよびMagento Open Source >=2.3.0 &lt;2.4.5*） – 関連する製品ルールで、ルール条件で定義されていないカテゴリの製品が表示される問題を修正しました。
* **MDVA-41305** （*Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.5*） – GraphQL mutation がウィッシュリストに追加された後、設定可能な商品オプションを返さない問題を修正しました。
* **MDVA-39181** （*Adobe CommerceおよびMagento Open Source >=2.4.1 &lt;2.4.5*） – 関連する製品ルールで、ルール条件で定義されていないカテゴリの製品が表示される問題を修正しました。
* **MDVA-42584** （*Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.3*） – インポートまたは API を使用して数量と在庫ステータスを変更した後、バックエンドの設定可能な在庫ステータスが更新されない問題を修正しました。
* **MDVA-40175** （*Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.3*） – の問題を修正します。 *クリックして配送方法を変更* には、並べ替え時に管理者で出荷方法を選択するラジオボタンが表示されません。
* **MDVA-42768** （*Adobe CommerceおよびMagento Open Source >=2.3.4 &lt;2.4.5*） – 設定可能な製品で、次の場合に標準価格が 0 と表示される問題を修正しました *在庫切れを表示* はい。
* **MDVA-43201** （*Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.4*） – 特定のロケールで DOB 属性を使用した場合に、顧客ログインでエラーが発生する問題を修正しました。
* パッチを更新：MDVA-35092、MDVA-33970。

## v1.1.9 {#v1-1-9}

* **MDVA-38346** （*Adobe CommerceおよびMagento Open Source >=2.3.0 &lt;2.4.5*） – Adobe Commerceのタイムゾーンがローカル環境のタイムゾーンと異なる場合に、日付フィルターが正しく機能しない問題を修正しました。
* **MDVA-42657** （*Adobe CommerceおよびMagento Open Source >=2.4.1 &lt;2.4.5*） – 管理者ユーザーが顧客セグメント条件でカテゴリを選択できない問題を修正しました。
* **MDVA-42806** （*Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.4*） – が発生した問題を修正します *新しい会社登録* メールは、REST API で既存の会社が更新されるたびに送信されます。
* **MDVA-37984** （*Adobe CommerceおよびMagento Open Source >=2.4.1 &lt;2.4.5*） – 問題を修正します。 [!DNL Visual Merchandiser] *ルールで製品を一致* 機能は、ステージング更新で製品を正しくフィルタリングしない。
* **MDVA-40488** （*Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.4*） – 在庫切れの子製品を含む設定可能な製品が正しい価格範囲で表示されない問題を修正しました。
* **MDVA-42507** （*Adobe CommerceおよびMagento Open Source >=2.4.3 &lt;2.4.5*） – 買い物かごルールに対してステージング更新を適用した後に、フルページキャッシュがクリーンアップされる問題を修正しました。
* **MDVA-39163** （*Adobe CommerceおよびMagento Open Source >=2.3.5 &lt;2.4.5*） – 新しいユーザーが登録され、買い物かごの製品がゲストセッションから来ている場合に発送方法を使用できない問題を修正しました。
* **MDVA-38626** （*Adobe CommerceおよびMagento Open Source >=2.3.3 &lt;2.4.5*） – 管理者ユーザーがコマンドを使用してバックエンドに注文できない問題を修正しました [!DNL PayPal Payflow Pro] 支払い。
* **MDVA-38666** （*Adobe CommerceおよびMagento Open Source >=2.3.2 &lt;2.3.6*） – 管理者ユーザーが顧客の買い物かごで設定可能な製品オプションを変更できない問題を修正しました。
* **MDVA-38526** （*Adobe CommerceおよびMagento Open Source >=2.4.1 &lt;2.4.4*） – 管理者ユーザーがにアクセスできない問題を修正しました [!DNL Site-Wide Analysis tool].
* パッチを更新しました：MDVA-40101。

## v1.1.8 {#v1-1-8}

* **MDVA-41215** （*Adobe CommerceおよびMagento Open Source >=2.3.0 &lt;2.4.4*） – を設定した後に、ユーザーが 500 エラーを取得する問題を修正します *mage-messages* cookie （既に存在するが、新しいメッセージがない場合）。
* **MDVA-41139** （*Adobe CommerceおよびMagento Open Source >=2.4.3 &lt;2.4.4*） – 製品のインポート後、ソースの 1 つに対して単純な製品の数量=0 が設定されると、設定可能な製品の在庫切れになる問題を修正します。
* **MDVA-42326** （*Adobe CommerceおよびMagento Open Source >=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*） – 永続買い物かごが有効になっている場合でも、セッションタイムアウト後に顧客がチェックアウト時にエラーが発生する問題を修正しました。
* **MDVA-42341** （*Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.4*） – 問題を修正します。 `categoryList` リクエストにストアヘッダーがある場合、GraphQL クエリで結果がフィルタリングされない。
* **MDVA-38393** （*Adobe CommerceおよびMagento Open Source >=2.3.0 &lt;2.4.4*） – 設定可能な製品の単純な製品の名前が変更された場合に、その製品のカタログルールが機能しなくなる問題を修正しました。
* **MDVA-39153** （*Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.4*） – 管理者で並べ替え中に割引額が正しく計算されない問題を修正します。
* パッチを更新：MDVA-28993、MDVA-41061、MDVA-35984。

## v1.1.7 {#v1-1-7}

* **MDVA-39711** （*Adobe CommerceおよびMagento Open Source >=2.3.0 &lt;2.4.3*） – 管理者ユーザーが web サイトを削除した後で、顧客のグリッドにアクセスできない問題を修正しました。
* **MDVA-40311** （*Adobe CommerceおよびMagento Open Source >=2.4.2-p2 &lt;2.4.4*） – 管理者ユーザーがエラーメッセージを取得する問題を修正しました *セキュリティまたはフォーム キーが無効です。 ページを更新してください* 管理者にログインした後、カスタム管理パスが設定され、秘密鍵が有効になっている場合。
* **MDVA-41631** （*Adobe CommerceおよびMagento Open Source >=2.4.1 &lt;2.4.4*） – オプションを指定せずに注文情報を取得しようとするとエラーが発生する問題を修正しました *電話番号* GraphQLを通じた価値。
* **MDVA-27239** （*Adobe CommerceおよびMagento Open Source >=2.3.0 &lt;2.3.6*） – クロスセル製品が表示されない問題を修正しました。
* 更新されたパッチ：MDVA-37068、MDVA-35254、MDVA-41164、MDVA-37916、MDVA-37478、MDVA-34551、MDVA-31791。

## v1.1.6 {#v1-1-6}

* **MDVA-40550** （*Adobe CommerceおよびMagento Open Source >=2.3.5 &lt;2.4.4*） – インデックス再作成中にフロントエンドで製品が見つからない問題を修正します。
* **MDVA-40120** （*Adobe CommerceおよびMagento Open Source >=2.4.1 &lt;2.4.4*） - GraphQLで DESC/ASC で並べ替えても、同じ関連度や価格の商品で動作しない問題を修正しました。
* **MDVA-41399** （*Adobe CommerceおよびMagento Open Source >=2.3.3 &lt;2.4.2*） – 管理者ユーザーがにアクセスできない問題を修正しました *買い物かごの管理* 顧客がウィッシュリストに商品を追加する場合は、ページに移動します。
* **MDVA-40609** （*Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.3*） – 無効な製品データがに存在しない問題を修正しました `cataloginventory_stock_status` インデックステーブル。無効な製品数が正しく表示されません。
* **MDVA-39031** （*Adobe CommerceおよびMagento Open Source >=2.4.1 &lt;2.4.4*） – 対象の web サイトに割り当てられていない場合でも、GraphQLを使用して買い物かごに商品を追加することが可能な問題を修正しました。
* **MDVA-41597** （*Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.4*） – GraphQLを使用して設定可能な複数の商品を買い物かごに追加した際に、ユーザーにエラーが発生する問題を修正しました。
* **MDVA-27456** （*Adobe CommerceおよびMagento Open Source >=2.3.5 &lt;2.3.7*） – 読み込もうとするとユーザーにエラーが発生する問題を修正しました [!DNL Swagger].
* **MDVA-32776** （*Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.2*） – 注文されても出荷されなかった場合に、在庫ステータスが更新されない問題を修正します。
* **MDVA-30862** （*Adobe CommerceおよびMagento Open Source >=2.3.4 &lt;2.4.0*） – 印刷されたPDF請求書の注文日が正しくない問題を修正します。
* のインデックスページの改善 [!DNL Quality Patch Tool]. の便利な検索とフィルタリングを追加しました [!DNL quality patches] （ツールの最新バージョン）。
* パッチを更新：MDVA-33382、MDVA-39482。

## v1.1.5 {#v1-1-5}

* **MDVA-41236** （*Adobe CommerceおよびMagento Open Source >=2.3.0 &lt;2.4.4*） – 終了日が以前に削除されている場合、製品の新しいスケジュール済み更新を作成または既存のスケジュール済み更新を編集できない問題を修正しました。
* **MDVA-41046** （*Adobe CommerceおよびMagento Open Source >=2.3.0 &lt;2.4.4*） – カスタムオプションを使用したシンプルな製品を、設定可能な製品やグループ化された製品に割り当てることができる問題を修正しました。
* **MDVA-40545** （*Adobe CommerceおよびMagento Open Source >=2.3.0 &lt;2.4.4*） – 同じページに複数のノードがある場合でも、ページの最初のノードのみが取得される問題を修正しました。
* **MDVA-41164** （*Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.3-p1*） – 管理者ユーザーが、ファイルまたは画像タイプのカスタム顧客属性を持つ会社を保存または編集できない問題を修正します。
* **MDVA-39229** （*Adobe CommerceおよびMagento Open Source >=2.3.0 &lt;2.4.4*） – カタログルールのステージング更新の開始時刻を更新した後に、次のエラーが表示される問題を修正します。 *Cron ジョブ staging_synchronize_entities_period にエラーがあります。アクティブな更新は削除できません。*
* **MDVA-40619** （*Adobe CommerceおよびMagento Open Source >=2.3.0 &lt;2.4.4*） – CMS ページでインライン編集を試みると、CMS ページ階層を変更したために 500 エラーが発生する問題を修正しました。
* **MDVA-41061** （*Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.3*） – 管理者から製品を保存すると、在庫のステータスが販売可能にリセットされる問題を修正しました。
* **MDVA-31763** （*Adobe CommerceおよびMagento Open Source >=2.3.0 &lt;2.4.4*） – カタログ価格ルールが手動で再インデックス化されるまで元に戻される（または適用されない）問題を修正します。
* **MDVA-37748** （*Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.3*） – 共有カタログに割り当てられていない商品がGraphQL クエリから返される問題を修正しました。

## v1.1.4 {#v1-1-4}

* **MDVA-40399** （*Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.4*） – REST API を使用して同じ注文の部分的な請求書を同時に作成できない問題を修正しました。
* **MDVA-40101** （*Adobe CommerceおよびMagento Open Source >=2.3.2 &lt;2.4.0*） – を使用した注文が成功した後、商品がミニカートから削除されない問題を修正しました [!DNL PayPal Express] チェックアウト。
* **MDVA-40401** （*Adobe CommerceおよびMagento Open Source >=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*） – 注文に失敗してもクーポンの使用価値が変更される問題を修正しました。
* **MDVA-40537** （*Adobe CommerceおよびMagento Open Source >=2.3.4 &lt;=2.4.0-p1*） – 同じ URL キーを持つ複数の CMS ページが存在する場合、ストア表示の作成時にユーザーにエラーが発生する問題を修正しました。
* **MDVA-37725** （*Adobe CommerceおよびMagento Open Source >=2.3.0 &lt;=2.4.3-p1 の場合*） – デフォルト以外の web サイトから送信される非同期注文メールにデフォルト web サイトのロゴ URL が含まれる問題を修正しました。
* **MDVA-39482** （*Adobe CommerceおよびMagento Open Source >=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*） – バックオーダーが有効な場合に、「0」の数量で読み込んだ製品の在庫切れになる問題を修正しました。
* **MDVA-40435** （*Adobe CommerceおよびMagento Open Source >=2.3.4 &lt;2.4.4*） – GraphQL経由で適用した場合に、動的価格を含むバンドル製品の誤った割引という問題を修正しました。
* **MC-42528** （*Adobe CommerceおよびMagento Open Source >=2.4.3 &lt;=2.4.3-p1*） – 問題を修正します。 `categoryList` GraphQL クエリを実行すると、割り当て済みカテゴリと未割り当てカテゴリの両方が返されます。
* **MDVA-29400** （*Adobe CommerceおよびMagento Open Source >=2.3.0 &lt;=2.3.7-p1 || >=2.4.0 &lt;=2.4.0-p1*） – で行われた重複した注文の問題を修正しました [!DNL PayPal Express Checkout].
* **MDVA-26005** （*Adobe CommerceおよびMagento Open Source >=2.3.4 &lt;=2.3.5-p2*） – カート価格ルール条件でカテゴリツリーのカテゴリを選択できない問題を修正しました。
* **MDVA-25631** （*Adobe CommerceおよびMagento Open Source >=2.3.3 &lt;=2.3.5-p2 の場合*） – 多数の顧客を含む顧客セグメントの編集および保存のパフォーマンスを向上させます。

## v1.1.3 {#v1-1-3}

* **MDVA-40262** （*Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.4*） – 管理者の一般的な検索用語にGraphQL検索クエリが表示されない問題を修正しました。
* **MDVA-40601** （*Adobe CommerceおよびMagento Open Source >=2.3.1 &lt;=2.4.2-p2 の場合*） - GraphQLを通じてスケジュールされた更新によって変更されたカテゴリに関する情報を取得しようとするとエラーが発生する問題を修正しました。
* **MDVA-37234** （*Adobe CommerceおよびMagento Open Source >=2.3.5 &lt;2.4.0 || >=2.4.1 &lt;=2.4.2-p2*） – 同じ SKU で買い物かごに項目を複数回追加（並列リクエスト）すると、同じ買い物かご ID で重複行項目が作成される問題を修正しました。
* **MDVA-33606** （*Adobe CommerceおよびMagento Open Source >=2.4.1 &lt;=2.4.2-p2 の場合*） – ユーザーがを取得する問題を修正しました *一意の制約違反* 階層に割り当てられた CMS ページを保存中にエラーが発生する。
* **MDVA-31590** （*Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;=2.4.1-p1 の場合*） – ユーザーが MySQL 非同期キューを使用して属性を一括で更新できない問題を修正しました。
* **MDVA-36309** （*Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;=2.4.2-p2 の場合*） – 管理グリッドで属性による製品検索が遅くなる問題を修正しました。

## v1.1.2 {#v1-1-2}

* **MDVA-38929** （*Adobe CommerceおよびMagento Open Source >=2.3.0 &lt;2.4.4*） – 注文がストアクレジットから支払われるときに、FPT の請求書に間違った総計が表示される問題を修正します。
* **MDVA-37364** （*Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;=2.4.3 の場合*） – 日付タイプのカスタム顧客属性によって、顧客のグリッド UI が機能しなくなる問題を修正しました。
* **MDVA-39195** （*Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;=2.4.2-p2 の場合*） – の問題を修正します。 *カートに追加* 買い物かごへのリダイレクトが有効な場合、ボタンがカテゴリページで非アクティブになりました。
* **MDVA-37115** （*Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;=2.4.2-p2 の場合*） – が不要な問題を修正しました *0 のみ左* 設定可能な製品ページに通知が表示されます。
* **MDVA-39521** （*Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.4*） – GraphQL経由で、空の電話番号を持つ配送先住所をカートに入力できない問題を修正しました。
* **MDVA-39384** （*Adobe CommerceおよびMagento Open Source >=2.3.1 &lt;=2.3.6 || >=2.4.1 &lt;=2.4.3*） – 会社ユーザーのカスタム顧客属性が保存されない問題を修正しました。
* **MDVA-39043** （*Adobe CommerceおよびMagento Open Source >=2.3.4 &lt;=2.4.3 の場合*） – 制限付きアクセスを持つ管理者ユーザーがを追加しようとするとエラーが発生する問題を修正しました *製品* cms ページへのウィジェット。
* **MDVA-39966** （*Adobe CommerceおよびMagento Open Source >=2.3.0 &lt;=2.3.5-p2 || >=2.4.0 &lt;=2.4.0-p1*） – 間違ったロケールをデプロイする問題を修正しました。
* **MDVA-38852** （*Adobe CommerceおよびMagento Open Source >=2.3.0 &lt;=2.3.5-p2*） – 複数の並列注文がある場合に、更新のためにカタログ在庫がテーブルをロックしてパフォーマンスが大幅に低下する問題を修正しました。
* **MDVA-39986** （*Adobe CommerceおよびMagento Open Source >=2.4.1 &lt;2.4.3*） – Safari ブラウザーを使用してMacOSの管理者に注文できない問題を修正しました。
* **MDVA-38447** （*Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.4*） – 2 つの問題を修正します。ここで、 *個別に表示されない* 設定可能な子製品がGraphQL response で返され、カテゴリフィルターを使用してGraphQL製品クエリの MySQL クエリを最適化します。
* **MDVA-40134** （*Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.3*） – 共有カタログが有効な場合に、GraphQLが関連商品を返さない問題を修正しました。
* **MDVA-39935** （*Adobe CommerceおよびMagento Open Source >=2.4.1 &lt;2.4.4*） – GraphQLが web サイトレベルで無効になっている設定可能な子製品を返す問題を修正しました。

## v1.1.1 {#v1-1-1}

* **MDVA-36021** （*Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.4*） – 問題を修正します。 *メンバー関数 getId （）の呼び出し* 管理者の注文の詳細ページにエラーが表示されます。
* **MDVA-34948** （*Adobe CommerceおよびMagento Open Source >=2.3.6 &lt;=2.3.6-p1 || >=2.4.0 &lt;=2.4.0-p1*） – などの長時間実行されるクエリの問題を修正します `GET_LOCK`.
* **MDVA-39305** （*Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;=2.4.2-p1*） – 登録ユーザーがGoogle ReCaptcha を有効にしてログインできない問題を修正しました。
* **MDVA-37897** （*Adobe CommerceおよびMagento Open Source >=2.3.0 &lt;2.4.4*） – 最近表示された項目ウィジェットからオプションを含む製品を追加しようとすると、誤ったリダイレクトで問題が修正されます。

## v1.1.0 {#v1-1-0}

* ユーザーエクスペリエンスを向上させ、必要なパッチを顧客が簡単に検索できるように、パッチカテゴリが導入されました。
* この `patches.json` ファイル名がに変更されました `support-patches.json`.
* **MDVA-38799** （*Adobe Commerce >=2.3.0 &lt;2.4.3*） – ステージング更新プログラムの作成後にダウンロード可能な製品が保存されなかった問題を修正しました。
* **MDVA-37592** （*Adobe Commerce >=2.3.6 &lt;=2.4.2-p1 の場合*） – 共有カタログに価格ゼロの製品で価格で並べ替えても正しく機能しない問題を修正しました。
* **MDVA-38827** （*Adobe Commerce >=2.3.3-p1 &lt;2.4.4*） – 顧客がエラーメッセージを含む注文出荷メールを受け取る問題を修正します。

## v1.0.26 {#v1-0-26}

* **MDVA-38468** （*Adobe Commerce >=2.3.2 &lt;=2.3.5-p2 の場合*） – CMS ページを保存する際のエラーを修正します。 *同じ ID のアイテム PAGE_ID が既に存在します*.
* **MDVA-34680** （*Adobe Commerce >=2.3.6 &lt;=2.3.7 の場合 || >=2.4.1 &lt;2.4.3*） – 顧客グリッドで顧客アカウントの作成時間が正しくフィルタリングされない問題を修正しました。
* **MDVA-37068** （*Adobe Commerce >=2.3.1 &lt;2.4.4*） – 買い物かごに仮想製品のみが含まれている場合に誤った税率が表示される問題を修正します。
* **MDVA-38608** （*Adobe Commerce >=2.3.0 &lt;2.4.3*） – 再インデックスが正常に終了しなかった場合に、一時テーブルが削除されない問題を修正します。
* **MDVA-38308** （*Adobe Commerce >=2.3.5 &lt;=2.3.6-p1 の場合 || >=2.4.0 &lt;=2.4.1-p1 || >=2.4.2 &lt;2.4.4*） – の追加に関連する問題を修正しました。 [!DNL Vimeo] ビデオから製品。

## v1.0.25 {#v1-0-25}

* **MDVA-37916** （*Adobe Commerce >=2.3.6 &lt;2.4.3*） – を使用する際に、顧客が支払い確認ページに移動しない問題を修正します [!DNL Paypal Payment Advanced] メソッド。
* **MDVA-37082** （*Adobe Commerce >=2.3.0 &lt;2.4.3*） – グループ化された製品のカスタム在庫を保存すると、フロントエンドで製品の在庫切れが表示される問題を修正しました。
* **MDVA-36572** （*Adobe Commerce >=2.3.5 &lt;2.4.3*） – クレジットメモの更新によってデータベースで製品予約の重複が更新されなくなった問題を修正します。
* **MDVA-38132** （*Adobe Commerce >=2.3.3 &lt;2.4.3*） – が原因で管理パネルにアクセスできない問題を修正します。 *リダイレクトが多すぎます* エラー。
* **MDVA-38270** （*Adobe Commerce >=2.4.1 &lt;2.4.3*） – GraphQLで注文合計にギフトカードの情報が見つからない問題を修正しました。

## v1.0.24 {#v1-0-24}

* **MDVA-37779** （*Adobe Commerce >=2.4.2 &lt;=2.4.4 の場合*） – web サイト ID がストア ID と一致しない場合に、GraphQLを使用して設定可能な商品を買い物かごに追加する問題を修正しました。
* **MDVA-36832** （*Adobe Commerce >=2.3.4 &lt;=2.4.2-p1 の場合*） – ビューの幅が 768 px の場合にページ上で画像が重複する問題を修正しました。
* **MDVA-37874** （*Adobe Commerce >=2.3.6 &lt;=2.3.7 の場合 || >=2.4.1 &lt;=2.4.2-p1*） – の問題を修正します。 *買い物かご全体に対する固定割引金額* は、複数のオプションを含むバンドル製品に誤って適用されます。
* **MDVA-37913** （*Adobe Commerce >=2.3.0 &lt;=2.4.0-p1 の場合*） – ダウンロード可能な製品が API を介して更新されるとダウンロード可能なリンクが消える問題を修正しました。
* **MDVA-34330** （*Adobe Commerce >=2.3.1 &lt;=2.4.2-p1 の場合*） – 注文グリッド内の注文が管理者のタイムゾーンに従ってフィルタリングされない問題を修正しました。

## v1.0.23 {#v1-0-23}

* **MDVA-37478** （*Adobe Commerce >=2.3.0 &lt;=2.3.7 の場合*） – で注文した部分的な請求書を作成する際に、Adobe Commerceがエラーをスローする問題を修正しました *分割払い* rest API による支払い方法。
* **MDVA-37362** （*Adobe Commerce >=2.3.4 &lt;=2.4.2-p1 の場合*） – GraphQL応答で設定可能な商品オプション値とバリアント属性値が空だった問題を修正しました。
* **MDVA-37288** （*（Adobe Commerce 2.4.2 の場合）*） - GraphQL リクエスト後に間違った階層価格が返される問題を修正しました。
* **MDVA-37225** （*Adobe Commerce >=2.4.1 &lt;=2.4.2-p1 の場合*） – 読み込まれた SKU に整数値がある場合に、クイックオーダーの作成中にアップロードプロセスが停止する問題を修正しました。
* **MDVA-37224** （*Adobe Commerce >=2.3.3 &lt;=2.4.2-p1 の場合*） – で顧客が交渉可能な見積もりを支払えない問題を修正しました [!DNL PayFlow Pro] 別の製品がカートに入った状態。
* **MDVA-36286** （*Adobe Commerce >=2.3.6 &lt;=2.4.2-p1 の場合*） – 同じ SKU のサブカテゴリ内で位置が異なる場合に、ページビルダー製品ウィジェットのプレビューが壊れる問題を修正しました。
* **MDVA-30186** （*Adobe Commerce >=2.3.4 &lt;=2.3.5-p2、>=2.4.0 &lt;=2.4.0-p1、>=2.4.2 &lt;=2.4.2-p1 の場合*） – 属性オプションが、GraphQL応答で属性項目数ではなくオプション値で並べ替えられる問題を修正しました。

## v1.0.22 {#v1-0-22}

* **MDVA-36718** （*Adobe Commerce >=2.3.0 &lt;=2.4.2 の場合*） - API 経由で変更した後も古いカスタムオプションが残る問題を修正しました。
* **MDVA-35773** （*Adobe Commerce >=2.3.6 &lt;=2.3.6-p1 の場合 || >=2.4.1 &lt;=2.4.2*） – 受注に対する請求書で 100% 割引の総計がゼロとして表示されない問題を修正します。
* **MDVA-36833** （*（Adobe Commerce 2.4.2 の場合）*） – 共有カタログから一部の製品を除外した後、ページあたりの製品の乱数を検索結果に表示する問題を修正しました。
* **MDVA-37182** （*Adobe Commerce >=2.4.1 &lt;=2.4.2 の場合*） – 両方で誤った検索結果が取得される問題を修正します [!DNL Elasticsearch] バージョン 6 およびバージョン 7。
* **MDVA-36253** （*Adobe Commerce >=2.4.0 &lt;=2.4.1-p1 の場合*） – 項目を削除した後、ミニ買い物かごに間違った小計が表示される問題を修正します。
* **MDVA-36853** （*（Adobe Commerce 2.4.2 の場合）*） – 大きなメディアギャラリーを読み込むと画像が表示されない問題を修正しました。

## v1.0.21 {#v1-0-21}

* **MDVA-34665** （*Adobe Commerce >=2.3.4 &lt;=2.3.4-p2 の場合*） – カテゴリページにバンドル製品が見つからない問題を修正します。
* **MDVA-36615** （*（Adobe Commerce 2.4.2 の場合）*） – 管理製品グリッドの製品数が間違っている問題を修正します。
* **MDVA-36464** （*Adobe Commerce >=2.4.0 &lt;=2.4.2 の場合*） – メール通知設定がストア表示レベルで機能しない問題を修正します。
* **MDVA-36138** （*Adobe Commerceの場合^2.3.2*） – 配送料が調整されず、カート内のすべてのアイテムが送料無料カートルールの対象にならない場合に全額配送料が顧客に表示される問題を修正しました。
* **MDVA-36424** （*Adobe Commerce >=2.3.0 &lt;=2.3.3-p1 の場合 || >=2.0.0 &lt;2.2.0*） – バックエンドのベース URL がストアフロントのベース URL と異なる場合に、コンテンツを繰り返し編集すると、ページビルダー要素に添付されたメディア画像が消える問題を修正しました。
* **MDVA-35984** （*Adobe Commerce ^2.4.0*） – 同じ製品に対して複数の同時出荷を作成した後、誤った製品数量と販売可能数量の問題を修正します。

## v1.0.20 {#v1-0-20}

* **MDVA-36170** （*Adobe Commerce >=2.3.4 &lt;2.4.2*） – カテゴリのキャッシュタグを使用してGraphQL クエリがキャッシュされない問題が修正されます。
* **MDVA-33168** （*Adobe Commerce >=2.3.3 &lt;2.4.2*） - API を使用して製品属性を更新すると、他のすべての属性が空の値に変更される問題を修正します。
* **MDVA-19640** （*Adobe Commerceの場合 >=2.3.0*） – の問題を修正します。 [!DNL Advanced Reporting] はデータを表示していません。
* **MDVA-11189** （*Adobe Commerce >=2.3.0 &lt;2.3.5*） – CSV ファイルを読み込んで製品ストックを更新した後の問題を、から行を修正しました `cataloginventory_stock` テーブルが削除されます。
* **MDVA-26639** （*Adobe Commerce >=2.3.3-p1 &lt;2.3.6*） – 新しい注文確認メールテンプレートを作成した場合、注文メールに注文項目が見つからない問題を修正します。
* **MDVA-15546** （*Adobe Commerceの場合 >=2.3.0*） – 注文 a の作成後に発生する問題を修正します *句があいまいな列 entity_id* エラーが例外ログに表示されます。
* **MDVA-21095** （*Adobe Commerce >=2.3.0 &lt;2.3.5*） – クエリ時の問題を修正します `INSERT INTO search_tmp` 属性の値を一括更新した後は終了しません。
* **MDVA-23845** （*Adobe Commerce >=2.3.2-p2 &lt;2.3.5*） - JavaScript の縮小が有効になると、メールテンプレートをプレビューできなくなる問題を修正しました。
* **MDVA-22026** （*Adobe Commerce >=2.3.2 &lt;2.3.4*） – 外部 URL からの画像を含めて CSV ファイルから製品を読み込めない問題を修正しました。
* **MDVA-22383** （*Adobe Commerce >=2.3.0 &lt;2.3.4*） – 製品の保存に時間がかかり、ページが破損する問題を修正しました。
* **MC-41359** （*Adobe Commerceの場合 >=2.3.6-p1 &lt;2.3.7, >=2.4.2 &lt;2.4.3*） – 間違った SameSite cookie パラメーター設定の問題を修正します。

## v1.0.19 {#v1-0-19}

* **MDVA-33614** （*（Adobe Commerce 2.4.1 の場合）*） – ページビルダーで次のエラーがスローされる問題を修正しました。 *ページビルダーの起動中にエラーが発生しました。 テクニカル サポート担当者に問い合わせてください。*
* **MDVA-35356** （*Adobe Commerce >=2.3.0 &lt;2.4.3*） – 部分的に請求された注文のキャンセル後に、誤ったストアクレジット返品の問題を修正します。
* **MDVA-33289** （*Adobe Commerce >=2.4.0 &lt;2.4.3*） – チェックアウト時に未加工の JavaScript コードが請求先住所 UI に表示される問題を修正しました [!DNL Google Tag Manager] が有効になっています。
* **MDVA-35982** （*Adobe Commerce >=2.3.0 &lt;2.4.3*） – 特定の web サイトに制限されている管理者ユーザーが、同じ web サイトで注文した商品の発送を作成できない問題を修正しました。
* **MDVA-35155** （*Adobe Commerce >=2.3.0 &lt;2.3.6*） – オプションタイトルが変更された場合、バンドル製品を購入できない問題を修正しました。
* **MDVA-35910** （*Adobe Commerce >=2.4.1 &lt;2.4.3*） – 顧客としてログイン機能を無効にした後に新しい顧客アカウントを作成できない問題を修正しました。
* **MDVA-34474** （*Adobe Commerce >=2.3.0 &lt;2.4.3*） – API を使用して製品を要求リストに追加する際の問題を修正しました。
* **MDVA-34591** （*Adobe Commerce >=2.3.0 &lt;2.4.3*） – の買い物かごルールの割引計算が正しくないという問題を修正します *最大数量割引の適用対象* および *割引数量ステップ（購入 X）*.
* **MDVA-33704** （*Adobe Commerce >=2.4.0 &lt;2.4.3*） – 問題を修正します。 *店舗での受け取り* 出荷オプションは使用可能に構成されていますが、表示されません。
* **MDVA-34928** （*Adobe Commerce >=2.3.5 &lt;2.3.5-p2*） – ストアクレジットが支払いから削除された後、ページローダーが無期限に表示される問題を修正します。
* **MDVA-35254** （*Adobe Commerce >=2.3.1 &lt;2.4.3*） – チェックアウト中の CAPTCHA の問題を修正します。
* **MDVA-35569** （*Adobe Commerce >=2.3.4 &lt;2.4.2*） – 問題を修正します。 *固定製品税* 状態が指定されている場合、GraphQLの応答でフィールドが入力されない。
* **MDVA-35847** （*Adobe Commerce >=2.4.1 &lt;2.4.3*） – カスタム顧客属性が使用されている場合に、会社ユーザーフォームが壊れる B2B の問題を修正します。
* **MDVA-31307** （*Adobe Commerce >=2.4.0 &lt;2.4.2*） – 問題がある場合に修正します *メモリ不足* キャッシュされたブロックの動的 CSP 許可リストへの登録に関する問題が原因で、特定のカテゴリでエラーが発生する。

## v1.0.18 {#v1-0-18}

* **MDVA-32655** （*Adobe Commerce >=2.3.0 &lt;2.4.3*） – 不正な修正 *件のが進行中* メッセージのステータスが正しい *完了* 消費者向けメッセージ `quoteItemCleaner` 複数の製品を削除した後。
* **MDVA-34102** （*Adobe Commerce >=2.3.0 &lt;2.4.3*） – 管理領域の製品グリッドおよび製品を編集ページで、無効な製品のデフォルト在庫の数量がゼロになる問題を修正します。
* **MDVA-35286** （*Adobe Commerce >=2.4.0 &lt;2.4.2*） – 顧客がカートにバンドルされた製品を持っており、複数のアドレスのチェックアウトから Onepage のチェックアウトに切り替えた場合にエラーが発生する問題を修正しました。
* **MDVA-35312** （*Adobe Commerce >=2.4.1-p1 &lt;2.4.2*） – 空のGraphQL リクエストの場合に応答コード 500 を修正します。
* **MDVA-34189** （*Adobe Commerce >=2.3.4 &lt;2.4.3*） – 最初のバイトが 503 番目のタイムアウトになる問題を修正します [!DNL Visual Merchandiser] 「管理者カテゴリ」ページの読み込み時のクエリ。
* **MDVA-34695** （*Adobe Commerce >=2.3.0 &lt;2.4.1*） – 負の値を修正 `children_count` カテゴリの削除後。

## v1.0.17 {#v1-0-17}

* **MDVA-34012** （*Adobe Commerce >=2.3.1 &lt;2.4.3*） – 問題を修正します。 *デフォルト値を使用* スケジュールされた変更が適用されると、チェックボックスがオフになります。 この問題は、スケジュールされた変更が有効でなくなった時点で表示されます。
* **MDVA-35064** （*Adobe Commerce >=2.3.3 &lt;2.4.3*） – API を使用して作成された設定可能な製品の URL の書き換えが生成されない問題を修正しました。
* **MDVA-34943** （*Adobe Commerce >=2.3.0 &lt;2.4.2*） – クイックオーダーが以前に入力した SKU をキャッシュする問題を修正しました。
* **MDVA-35197** （*Adobe Commerce >=2.3.5 &lt;2.4.0*） – 以前に追加した商品が在庫切れになった場合に、GraphQLを使用して買い物かごに追加するとエラーが発生する問題を修正しました。
* **MDVA-34850** （*Adobe Commerce >=2.3.1 &lt;2.4.0*） – 設定可能な商品の在庫切れオプションが、打ち消し線として表示されるのではなく、表示されない問題を修正しました。
* **MDVA-34867** （*Adobe Commerce >=2.3.0 &lt;2.4.3*） – 予定されている更新の条件フィールドセットの値が保存されない問題を修正します。
* **MDVA-35092** （*Adobe Commerce >=2.3.5 &lt;2.4.3*） – ユーザーが追加できない問題を修正しました [!DNL Vimeo] が非推奨（廃止予定）になったビデオ [!DNL Vimeo] API です。

## v1.0.16 {#v1-0-16}

* **MDVA-33453** （*Adobe Commerce >=2.3.6 &lt;2.4.3*） – 一致する製品の価格が web サイトごとに異なる場合に、ページビルダー製品のコンテンツタイプのプレビューが壊れる問題を修正しました。
* **MDVA-32634** （*Adobe Commerceの場合^2.3.1*） – 問題を修正します。 `url_path` すべてのストアに割り当てられたカテゴリは、階層内でカテゴリを移動した後も変更されません。
* **MDVA-33344** （*Adobe Commerce ^2.3.0*） – ハードコードされた問題を修正します `rma_item` データベースの値の代わりに、エンティティのデフォルトの属性セット ID が使用されます。
* **MDVA-34192** （*Adobe Commerce >=2.3.4 &lt;2.4.3*） – dd/mm/yyyy 形式を使用して顧客の生年月日を変更/指定できない問題を修正しました。
* **MDVA-34847** （*Adobe Commerce ^2.3.0*） – カスタム権限を持つ管理者ユーザーの管理コレクションで、SQL 条件に対するストア ID 型の変換を整数に修正します。
* **MDVA-34886** （*Adobe Commerceの場合^2.3.2*） – 次の場合に検索で結果が返されない問題を修正しました *重み* 製品属性は検索可能として設定されています。

## v1.0.15 {#v1-0-15}

* **MDVA-33559** （*Adobe Commerce >=2.3.0 &lt;2.4.3*） – の問題を修正しました。 [!DNL PayPal Payflow Pro] リダイレクトパラメーターリスト形式エラーで支払いが失敗しました。
* **MDVA-34023** （*Adobe Commerce >=2.3.0 &lt;2.4.3*） – エラーが発生した問題を修正します *addressId を持つそのようなエンティティはありません* は、訪問者のブラウザーでランダムに表示されます。
* **MDVA-32759** （*Adobe Commerce >=2.3.1 &lt;2.4.3 （B2B 拡張機能を使用）*） – 共有カタログによって既存の階層の価格が削除される問題を修正しました。
* **MDVA-33482** （*Adobe Commerceの場合^2.3.5*）：部分請求書に対してクレジット・メモを生成すると、その部分請求書の税金ではなく、合計受注の税金が生成される問題を修正します。
* **MDVA-33393** （*Adobe Commerce >=2.3.0 &lt;2.4.2*） – エラーを修正します *入力された countryId は存在しません*.
* **MDVA-33632** （*Adobe Commerce >=2.3.0 &lt;2.3.7*） – 例外メッセージが表示される問題を修正します *この商品は在庫切れです* 在庫切れの製品を並べ替えようとした際に、が管理者ユーザーに表示されるようになりました。
* **MDVA-34469** （*Adobe Commerce >=2.4.1 &lt;2.4.2*） – 複数のストア表示を使用すると、顧客の買い物かごでGraphQLの突然変異が失敗する問題を修正しました。
* **MDVA-33976** （*Adobe Commerce >=2.3.0 &lt;2.3.7*） – バンドル製品から 2 番目のオプションを削除した後、バンドル製品がストアフロントで在庫切れと表示される問題を修正します。
* **MDVA-33894** （*Adobe Commerce >=2.4.0 &lt;2.4.1 （B2B 拡張機能を使用）*） – 複数の製品の追加や削除、SKU の大文字と小文字の区別など、クイックオーダー機能に関する複数の問題を修正します。
* **MDVA-27664** （*Adobe Commerce >=2.3.4 &lt;2.3.6*） – 顧客登録フォームでエラーが表示される問題を修正します。 *エラー – 生年月日は今日より大きくしないでください。*
* **MDVA-33970** （*Adobe Commerce >=2.3.4 &lt;2.4.2*） – 価格属性の範囲が web サイトに設定されている場合に、クレジットメモに間違った通貨記号が表示される問題を修正します。
* **MDVA-33992** （*Adobe Commerce >=2.3.0 &lt;2.4.2*） – チェックアウト時に B2B 特別価格が正しく表示されない問題を修正しました。
* **MDVA-34100** （*Adobe Commerce >=2.3.4 &lt;2.4.2 （B2B 拡張機能を使用）*） – 会社構造ページから会社アカウントを作成できない問題を修正しました。

## v1.0.14 {#v1-0-14}

* **MDVA-31969** （*Adobe Commerce >=2.3.3 &lt;2.3.5, >=2.4.0 &lt;2.4.2*） – 製品を CSV ファイルから読み込んだ後の画像の重複の問題を修正しました。
* **MDVA-33382** （*Adobe Commerce >=2.3.0 &lt;2.4.2*） – 製品をカテゴリから削除した後のインデクサーの無効化の問題を修正します。
* **MDVA-28511** （*Adobe Commerce >=2.3.5 &lt;2.3.6*） – 完了できない問題を修正しました [!DNL PayPal] 「名前」フィールドに特定の文字（アクセント付き大文字など）が含まれている場合はチェックアウトします。
* **MDVA-31519** （*Adobe Commerce >=2.3.5 &lt;2.3.6*） – サイト全体の販売ルールが使用されている場合に、ゲストのチェックアウトで待機タイムアウトの問題を修正します。
* **MDVA-33281** （*Adobe Commerce >=2.3.4 &lt;2.3.6*） – で致命的なエラーが発生する問題を修正します `inventory:reservation:list-inconsistencies` sku パラメータータイプが間違っているので。
* **MDVA-24201** （*Adobe Commerce >=2.3.0 &lt;2.3.5*） – 手動で再インデックス化するまで、価格がスケジュールされた買い物かご価格ルールを反映しない問題を修正しました。
* **MDVA-32694** （*Adobe Commerce >=2.3.0 &lt;2.3.6 || >= 2.4.0 &lt;2.4.2*） – 管理者ユーザーが、デフォルトでないストアに関連する製品を譲渡可能な見積もりに追加できない問題を修正しました。
* **MDVA-33516** （*Adobe Commerce >=2.3.0 &lt;2.3.6*） – 購買依頼リストでバンドル製品を編集するとエラーが発生する問題を修正します。
* **MDVA-33975** （*Adobe Commerce >=2.3.4 &lt;2.4.2*） – GraphQL リクエストでの価格計算に関する複数の問題を修正します。

## v1.0.13 {#v1-0-13}

* **MDVA-30858** （*Adobe Commerce >=2.3.0 &lt;2.4.2*） – の問題を修正しました。 [!DNL PayPal] 以下では決済レポートを使用できません **報告書** > **売上** > **[!DNL PayPal]** 想定どおりの決済。
* **MCP-87** （*Adobe Commerce >=2.3.1 &lt;2.4.2*） – 大規模なプロファイル向けのカテゴリ製品およびストックインデクサーのインデクシング時間を改善しました。
* **MDVA-33106** （*Adobe Commerce >=2.3.0 &lt;2.4.2*） – 再スケジュールされた製品の変更が cron の後で消去される問題を修正します `run` コマンドが実行されます。
* **MDVA-19391** （*Adobe Commerce >=2.3.0 &lt;2.3.5*） – の問題を修正します。 `analytics_collect_data` の説明レコードが NULL なため、がエラーをスローしています `catalog_category_entity_text` テーブル。
* **MDVA-20376** （*Adobe Commerce >=2.3.2 &lt;2.3.4*） – の問題を修正します。 *customerId = 1 の該当するエンティティがありません* のエラー `exception.log` （注文配置後にログインした顧客の場合）
* **MDVA-23764** （*Adobe Commerce >=2.3.2 &lt;2.3.5*） – のバグを修正しました。 `JsFooterPlugin.php` これは、ダイナミック ブロックの表示に影響します。
* **MDVA-13203** （*Adobe Commerce >=2.3.0 &lt;2.4.2*） – 問題を修正します。 *整合性制約違反 search_tmp_ table* 完全な再インデックス後にエラーが表示される。
* **MDVA-23426** （*Adobe Commerce >=2.3.3 &lt;2.3.5*） – Adobe Commerceから送信される通知メールに、コンテンツが添付ファイルとして追加された空白の本文が含まれる問題を修正しました。
* **MDVA-22150** （*Adobe Commerce >=2.3.1 &lt;2.3.4*） – 設定可能な製品が買い物かごにあり、クーポンが適用されている顧客が、その設定可能な製品が管理者で無効になっている場合にログインできない問題を修正しました。
* **MDVA-32545** （*Adobe Commerce >=2.3.0 &lt;2.4.2*） – 管理者から注文を作成する際に請求書が自動的に送信されない問題を修正しました。
* **MDVA-32714** （*Adobe Commerce >=2.3.4 &lt;2.4.1*） – GraphQL製品クエリで顧客グループ価格が機能しない問題を修正しました。

## v1.0.12 {#v1-0-12}

* **MDVA-31399** （*Adobe Commerce >=2.3.2 &lt;2.4.2*） – を追加します。 *小計 税）* 価格設定ルール条件のオプション。
* **MDVA-31236** （*Adobe Commerce >=2.4.0 &lt;2.4.2*） – カスタムリソースアクセス権を持つ管理者が 2FA を設定したり、ログインしたりできない問題を修正しました。
* **MDVA-30845** （*Adobe Commerce >=2.3.5 &lt;2.3.7*） – 問題を修正します。 *申し訳ありませんが、現在この注文で利用できる見積もりはありません* ups XML/USPS/DHL への接続に失敗するとエラーが表示され、他の配送方法はありません。
* **MDVA-32133** （*Adobe Commerce >=2.4.0 &lt;2.4.1*） – 特定の場合にページビルダーからメディアギャラリーが読み込まれない問題を修正します。
* **MDVA-12304** （*Adobe Commerceの場合 >=2.3.0*） – 最大 cookie 数を 50 から 200 に増やします。
* **MDVA-32632** （*Adobe Commerce >=2.3.2 &lt;2.3.5*） – 注文が支払いシステムに表示されるが、Adobe Commerceには表示されない問題を修正しました。
* **MDVA-32449** （*Adobe Commerce >=2.3.0 &lt;2.3.6 || 2.4.0 || >=2.4.1 &lt;2.4.2 （B2B 拡張機能あり）*） – 注文履歴の読み込みに時間がかかる、またはまったく読み込まれない問題を修正します。
* **MDVA-32739** （*Adobe Commerce >=2.3.0 &lt;2.4.2*） – 非同期メール通知を有効にすると、古い販売メールが送信される問題を修正しました。

## v1.0.11 {#v1-0-11}

* **MC-38509** （*Adobe Commerce 2.3.6, 2.4.1 の場合*） – 問題を修正します。 *アカウントの作成* 内の無効なデータを修正した後も、ボタンが無効のままになる *新しい顧客アカウントを作成* フォーム。
* **MDVA-31006** （*Adobe Commerce 2.3.0, 2.3.1 の場合*） – を使用して注文した後に重複した注文が表示される問題を修正しました [!DNL Paypal Express] 支払い。
* **MDVA-25602** （*（Adobe Commerce 2.3.0 の場合）*） – の問題を修正しました。 [!DNL PayPal Payflow Pro] 支払い方法と cookie の処理方法 `SameSite=Lax` chrome 80 ブラウザーおよび API 応答のデフォルトでは、カスタマーログインページにリダイレクトされます。

## v1.0.10 {#v1-0-10}

パッチバージョンのマイナーな修正

## v1.0.9 {#v1-0-9}

* **MDVA-31363** （*Adobe Commerce >=2.3.2 &lt;2.4.2*） – 次の場合に、クーポン付きの買い物かご価格ルールがGraphQLで適用されない問題を修正しました *買い物かご全体に対する固定金額割引* action が使用されます。
* **MDVA-30889** （*Adobe Commerce >=2.3.0 &lt;2.4.2*） – 仮想およびシンプル製品をオプションとして使用してバンドルを請求した後にエラーが発生する問題を修正します。
* **MDVA-31791** （*Adobe Commerce >=2.3.4 &lt;2.3.5*） – ターゲットルールまたはリンクされた製品が使用された場合の製品ページのパフォーマンスを向上させます。
* **MDVA-31168** （*Adobe Commerce >=2.3.0 &lt;2.4.2*） – 製品の書き出し CSV ファイルが表示されず、メモリ割り当てエラーが発生する問題を修正しました。
* **MDVA-32313** （*Adobe Commerce >=2.3.0 &lt;2.3.4*） – 設定可能な製品が、間違った設定オプションを使用してウィッシュリストに追加される可能性がある問題を修正しました。
* **MDVA-31759** （*Adobe Commerce >=2.3.0 &lt;2.4.2*） – 製品がで更新されない問題を修正しました *dropdown* および *テキスト領域* csv 読み込み時の属性値。
* **MDVA-32012** （*Adobe Commerce >=2.3.0 &lt;2.4.2*） – 韓国とアルゼンチンの郵便番号を検証できない問題を修正しました。
* **MDVA-31640** （*Adobe Commerce >=2.3.1 &lt;2.3.6 || >=2.4.0 &lt;2.4.1*） – REST API で特別価格を更新できない問題を修正しました。
* **MDVA-28651** （*Adobe Commerce >=2.3.0 &lt;2.3.6 || >2.4.0 （B2B 拡張機能を使用）*） – REST API を使用して交渉可能な引用符を読み込む際に、パフォーマンスの問題がある問題を修正します。

## v1.0.8 {#v1-0-8}

* **MDVA-31242** （*Adobe Commerce >=2.3.0 &lt;2.4.1 （B2B 拡張機能を使用）*） – クレジット メモ グリッドに間違った通貨記号が表示される問題を修正します。
* **MDVA-31295** （*Adobe Commerce >=2.3.0 &lt;2.4.2*） – 部分的な注文が完了し、項目に課税する際に報酬ポイントが計算されない問題を修正しました。
* **MDVA-30112** （*Adobe Commerce >=2.3.4 &lt;2.4.2*） – 注文数がを超えた場合の問題を修正します *バンチサイズ* 値、Adobe Commerceは次の条件を使用して注文を検討します *保留中* ステータスが矛盾しています。
* **MDVA-31150** （*Adobe Commerce >=2.3.0 &lt;2.4.2*） – 請求書が Rest API 呼び出しによって転記され、注文がストアクレジットおよびギフトカードのアカウントによって部分的に支払われた場合に、ストアクレジットおよびギフトカードの残高がGET請求書 Rest API 呼び出しによって返されない問題を修正します。
* **MDVA-30963** （*Adobe Commerce >=2.3.2 &lt;2.4.2*） – 製品のフィルター結果に、指定した値のみが含まれるように設定される問題を修正しました *すべてのストア表示* 管理者の範囲には、ストア表示レベルで上書きされた値を持つ製品を含めます。
* **MDVA-29954** （*Adobe Commerce >=2.3.0 &lt;2.3.6 || 2.4.0 || 2.4.2 （B2B 拡張機能を使用）*） – 問題を修正します。 *新しい会社登録リクエスト* および *あなたは会社にリンクされています* 間違ったアドレスからメールが送信される。
* **MDVA-28357** （*Adobe Commerce >=2.3.2 &lt;2.3.6 || >=2.4.0 &lt;2.4.1*） – 標準アナライザーを、の SKU フィールド用のキーワードトークナイザーのカスタムアナライザーに置き換えます [!DNL ElasticSearch] ワイルドカード検索クエリを実行するためのインデックスが、ハイフン（「–」）を含む SKU で機能するようになりました。

## v1.0.7 {#v1-0-7}

* **MDVA-30972** （*Adobe Commerce >=2.3.0 &lt;2.4.2*） – カスタム注文のステータスがに変更された問題を修正します *処理* webapi を使用した部分出荷作成後。
* **MDVA-30428** （*Adobe Commerce >=2.3.4 &lt;2.3.5*） – この製品がカスタムインベントリソースに割り当てられている場合、顧客がウィッシュリストに製品を追加できない問題を修正しました。
* **MDVA-30594** （*Adobe Commerce >=2.3.0 &lt;2.4.2*） - FPT が設定されている場合、チェックアウト時に複数のアドレスを持つ注文を保存できなかった問題を修正しました。
* **MDVA-29148** （*Adobe Commerce >=2.3.0 &lt;2.4.2*） – API 呼び出し（の製品カスタム属性）を使用して製品を作成する際の問題を修正しました `\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend` （Multiselect と同様に）ペイロードに値が指定されていない場合、タイプはそのデフォルト値を使用しません。
* **MDVA-30837** （*Adobe Commerce >=2.3.1 &lt;2.3.5*） – 設定を追加しました。 *金額に税金を含む：Yes/No* （送料無料の方法の設定）を参照してください。 条件 *金額に税を含める* はに設定されています。 *はい*&#x200B;の場合、最小注文額は小計+税として計算されます。 条件 *金額に税を含める* はに設定されています。 *不可*、最小注文額は小計として計算されます
* **MDVA-25028** （*Adobe Commerce >=2.3.2 &lt;2.3.3 || >=2.3.5 &lt;2.3.6*） – を使用して注文する際の問題を修正します [!DNL PayPal Payflow Pro] 不正フィルターがトリガーされた場合、が不正疑いステータスに設定されない。
* **MDVA-31224** （*Adobe Commerce >=2.3.3 &lt;2.3.5*） – のパフォーマンスを向上させます。 `catalog_product_price` バンドル製品の再インデックス操作。
* **MDVA-31321** （*Adobe Commerce >=2.3.2 &lt;2.3.5*） – 次の場合に空白ページを修正します（エラー） *すべてを表示* が選択されました。 [!DNL Elasticsearch] 製品 id の大きなリストを返します。 このシナリオでは、order by 句が間違った SQL 形式に変換されます。
* **MDVA-30815** （*Adobe Commerce >=2.3.2 &lt;2.3.4*） – 検索結果ページに表示する検索結果の数を変更すると、Adobe Commerceで空白ページが表示される問題を修正しました。 [!DNL Elasticsearch] ページごとに表示される検索結果の数を変更した場合に、カテゴリページの結果が正しく表示されるようになりました。
* **MDVA-30782** （*Adobe Commerce >=2.3.5 &lt;2.4.2*） – 買い物かごのルールに関係なく、動的ブロックが表示される問題を修正しました。
* **MDVA-31021** （*Adobe Commerce >=2.3.0 &lt;2.4.2*） – パフォーマンスの問題がに存在する問題を修正します `module-catalog-import-export/Model/Import/Product/Option.php`. に 100,000 件以上のレコードがある場合 `catalog_product_option` 表：単一製品の新しい CSV の検証に要する時間は 10 秒未満です。
* **MDVA-31007** （*Adobe Commerce >=2.4.0 &lt;2.4.1*） – カスタムアドレス属性がマイアカウント領域の注文詳細ページとバックエンドに正しく表示されない問題を修正しました。
* **MDVA-29389** （*Adobe Commerce >=2.3.0 &lt;2.4.2*） – 詳細レポートの問題を修正します。ここでは、 `analytics_collect_data` cronjob の発言： *ポートは、ホストパラメーター（localhost:3306 など）内で設定する必要があります*.
* **MDVA-31343** （*Adobe Commerce >=2.3.4 &lt;2.3.6*） – 削除された本文クラスの問題を修正します `page-layout-category-full-width` カテゴリがスケジュールされたとき。
* **MDVA-30945** （*Adobe Commerce >=2.3.0 &lt;2.4.2*） – 買い物かごを更新したときに致命的なエラーメッセージが表示される問題を修正しました `Call to a member function getValue() on null in module-configurable-product CartItemProcessor.php`.

## v1.0.6 {#v1-0-6}

* **MDVA-28993** （*Adobe Commerce >=2.3.4 &lt;2.4.0*） –  *Minimum should match* の機能と部分検索 [!DNL Elasticsearch] エンジン。 検索クエリでのハイフンの問題を解決します。
* **MDVA-30102** （*Adobe Commerce >=2.3.2 &lt;=2.4.0 の場合*） – レイアウトキャッシュに TTL がないので、Redis キャッシュがすばやく増加する問題を修正します。
* **MDVA-30599** （*Adobe Commerce >=2.3.4 &lt;=2.4.0 の場合*） - API を使用して作成されたゲストの見積が、ログインした顧客の見積りとして誤ってマークされる問題を修正しました。
* **MDVA-29446** （*Adobe Commerce >=2.3.3 &lt;=2.4.0 の場合*） – 適用できない配送方法の価格がチェックアウト時にゼロと表示される問題を修正しました。
* **MDVA-30357** （*Adobe Commerce >=2.3.2 &lt;=2.4.0 の場合*） – cron でサイトマップを生成する際に、誤った画像 URL が作成される問題を修正します。
* **MDVA-30565** （*Adobe Commerce >=2.3.2 &lt;=2.3.3-p1 の場合*） – の問題を修正します。 *cartid = 0 のそのようなエンティティはありません* 永続ショッピングカートが有効になっている場合、ストアフロントのチェックアウト時にゲスト顧客にエラーが表示されます。
* **MDVA-29787** （*Adobe Commerce >=2.3.0 &lt;=2.4.0 の場合*） – 次の場合に関連製品のターゲットルールが機能しない問題を修正しました *が次の 1 つ：* 条件は、表示する製品の定義に使用します。
* **MDVA-30977** （*Adobe Commerce >=2.3.4 &lt;=2.3.5-p2 の場合*） – 再インデックス後にカテゴリにランダムな製品が見つからない問題を修正しました。
* **MDVA-28202** （*Adobe Commerce >=2.3.4 &lt;=2.4.2 の場合*） – MSI を使用する場合に、レイヤーナビゲーションで設定可能な製品が正しくフィルタリングされない問題を修正しました。
* **MDVA-28300** （*Adobe Commerce >=2.3.0 &lt;2.3.6*） – GQL リクエストにカタログ価格ルールからの価格変更が反映されない問題を修正しました。
* **MDVA-31006** （*Adobe Commerce >=2.3.2 &lt;=2.4.2 の場合*） – を使用して注文した後に重複した注文が表示される問題を修正しました [!DNL Paypal Express] 支払い。

## v1.0.5 {#v1-0-5}

* **MDVA-30841** （*Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*） – 階層型ナビゲーションの問題を修正します。ここでは、 *不可* 次の場合、ブール型の製品属性の値はレイヤーナビゲーションに含まれませんでした [!DNL Elasticsearch] は検索エンジンとして使用されました。
* **MDVA-28191** （*Adobe Commerce >=2.3.3 &lt;2.4.2*） – 管理者を介した注文の作成中に支払い方法が読み込まれない問題を修正しました。
* **MDVA-29959** （*Adobe Commerce >=2.3.0 &lt;=2.3.3-p1 （B2B 拡張機能を使用）*） – 管理者ユーザーがに制限される問題を修正しました *会社* 会社アカウントを削除する権限はありません。
* **MDVA-30265** （*Adobe Commerce >=2.3.3 &lt;2.4.2*） – 請求書の作成後に出荷トラッキング リンクが機能しなくなる問題を修正します。
* **MDVA-28409** （*Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*） – 問題を修正します。 `sales_clean_quotes` cron ジョブが次の条件で失敗 *メモリ不足* データベース内の期限切れの引用符の数が多い場合のエラー。
* **MDVA-30593** （*Adobe Commerce >=2.3.0 &lt;2.3.4*）：見積もりの有効期間の設定に従って期限切れになった見積もりがクリーンアップされない問題を修正します。
* **MDVA-30107** （*Adobe Commerce >=2.3.0 &lt;2.3.6*） – ストアビューに異なるベース URL を使用した場合に、ストアスイッチャーが期待どおりに動作しない問題を修正しました。
* **MDVA-28763** （*Adobe Commerce >=2.3.2 &lt;2.3.4*） – REST API を複数回使用して製品情報を更新すると、製品画像が重複する問題を修正しました。
* **MDVA-30284** （*Adobe Commerce >=2.3.0 &lt;2.4.2*） – カタログ検索インデクサーが次の理由で失敗する問題を修正しました *[!DNL Elasticsearch]エラー：インデックスの合計フィールド数の制限を超えています。*
* **MDVA-29042** （*Adobe Commerce >=2.3.3 &lt;=2.3.4-p2 （B2B 拡張機能を使用）*） – カタログの権限がに変更された問題を修正しました *許可* 共有カタログに新しい製品が追加された後、自動的に。
* **MDVA-30428** （*Adobe Commerce >=2.3.3 &lt;2.4.2*） – この製品がカスタムインベントリソースに割り当てられている場合、顧客がウィッシュリストに製品を追加できない問題を修正しました。
* **MDVA-28661** （*Adobe Commerce >=2.3.0 &lt;2.4.2 （B2B 拡張機能を使用）*） – 会社管理者が変更された後、会社ユーザーの会社アカウントセクションにエラーがスローされる問題を修正しました。

## v1.0.4 {#v1-0-4}

* **MDVA-30195** （*Adobe Commerce 2.3.1 - 2.3.4-p2 の場合*） – データベース名が長すぎると cron ジョブが失敗し、フロントエンドでカテゴリが更新されない問題を修正しました。
* **MDVA-30106** （*Adobe Commerce ^2.3.0*） – チェックアウト時の支払いが読み込まれない問題を修正しました *null のプロパティ「length」を読み取れません* js コンソールでエラーが発生しました。
* **MDVA-28656** （*Adobe Commerce >=2.3.1 &lt;2.3.6 || >=2.4.0 &lt;2.4.2*） – 支払情報が不要な注文があった場合（100% 割引など）、その注文の請求書が作成された場合に、注文ステータスが次のように変更される問題を修正します *クローズ* 「完了」ではなく、
* **MDVA-30209** （*Adobe Commerce 2.3.0 ～ 2.3.3-p1 の場合*） – 顧客がアカウント情報を更新した場合に、顧客グループがデフォルトに変更される問題を修正します。
* **MDVA-30123** （*Adobe Commerce >=2.3.4 &lt;2.4.2*） – 属性オプションラベルがGraphQL クエリに対して正しく翻訳されない問題を修正しました。
* **MDVA-29996** （*Adobe Commerce >=2.3.3 &lt;2.4.2*） – カテゴリ権限を有効にした後、カテゴリページがフルページキャッシュによってキャッシュされない問題を修正しました。
* **MDVA-30164** （*Adobe Commerce >=2.3.1 &lt;2.4.2*） – カスタム顧客属性が存在する場合に、顧客グリッドから顧客レコードを書き出すことができない問題を修正しました。
* **MDVA-30444** （*Adobe Commerce >=2.3.0 &lt;2.4.1*） - GraphQLを使用して注文した場合に、確認メールが送信されない問題を修正しました。
* **MDVA-30490** （*Adobe Commerce 2.3.4 - 2.3.5-p2 の場合*） – 製品の 1 つに空の短い説明がある場合、製品比較が 500 エラーページをスローする問題を修正しました。
* **MDVA-30232** （*Adobe Commerce >=2.3.1 &lt;2.4.1*） – 元の注文にギフトカードが含まれている場合、再注文できない問題を修正しました。
* **MDVA-29965** （*Adobe Commerce >=2.3.3 &lt;2.4.0*） – 製品を買い物かごに追加する際に、顧客が無効なフォームキーを取得するエラーが修正されました。
* **MDVA-30008** （*Adobe Commerce >=2.3.0 &lt;2.4.2*） – 公開カタログ内の製品に対して管理 API を通じて注文を行うことができない B2B の問題を修正しました。
* **MDVA-22469** （*Adobe Commerce 2.3.2-p2 - 2.3.3-p1 の場合*） – Adobe Commerce 2.3.3 にアップグレードした後、管理パネルでページビルダーが機能せず、一部の JS ファイルや CSS ファイルが読み込まれない問題を修正しました。
* **MC-35984** （*Adobe Commerce >=2.4.0 &lt;2.4.1*） – 返品承認（RMA）用の出荷ラベルを作成した後、マーチャントが返品ページのページ要素を操作できなかった問題を修正しました。

## v1.0.3 {#v1-0-3}

* **MDVA-25602** （*Adobe Commerce 2.3.0 ～ 2.3.4 の場合*） – の問題を修正しました。 [!DNL PayPal Payflow Pro] 支払い方法と cookie の処理方法 `SameSite=Lax` chrome 80 ブラウザーおよび API 応答のデフォルトでは、カスタマーログインページにリダイレクトされます。
* **MDVA-26694** （*Adobe Commerce >=2.3.0 &lt;2.3.6 || 2.4.0*） – 製品およびカタログのキャッシュが毎日期限切れになるが、スケジュールされている有効期限が異なる問題を修正します。
* **MDVA-27825** （*Adobe Commerce >=2.3.0 &lt;2.4.1*） – メモリリークが原因で大量データの書き出しに失敗する問題を修正しました。
* **MDVA-29085** （*Adobe Commerce >=2.3.0 &lt;=2.3.5-p1 の場合*） – 会社が API で作成されている場合に、新しい会社のメールが必須で送信されない B2B の問題を修正しました。
* **MDVA-29344** （*Adobe Commerce >=2.3.5 &lt;=2.4.0-p1 の場合*） – テキストをヘッダー要素からテキスト要素にコピーした後にページビルダーが停止する問題を修正しました。
* **MDVA-29835** （*Adobe Commerce >2.3.1 &lt;2.4.2*） – ギフトカードの注文に 1 つではなく 2 つのコードが含まれていた問題を修正しました。
* **MDVA-30052** （*Adobe Commerce >=2.3.2-p2 &lt;2.3.5*） – プライベートコンテンツ（ローカルストレージ）が正しく入力されず、パフォーマンスの問題が発生する問題を修正します。
* **MDVA-30131** （*Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*） – 階層型ナビゲーションの問題を修正します。ここでは、 *不可* 次の場合、ブール型の製品属性の値はレイヤーナビゲーションに含まれませんでした [!DNL Elasticsearch] は検索エンジンとして使用されました。
* **MDVA-35514** （*Adobe Commerce >=2.4.0 &lt;2.4.1*） – パッケージを作成モーダルウィンドウで出荷ラベルを作成し、注文した製品をパッケージに追加する問題を修正しました。
