---
title: リリースノート
description: Adobe Commerceで使用可能なパッチと、それらが解決する問題について説明します。
exl-id: 22262555-f5ea-49ad-98ad-ea8428ef66d5
source-git-commit: d870d98caf2b2576f3bf179e860e711d1cea9afc
workflow-type: tm+mt
source-wordcount: '21346'
ht-degree: 0%

---

# リリースノート

[[!DNL Quality Patches Tool]](https://github.com/magento/quality-patches) は、AdobeとMagento Open Sourceコミュニティが開発した個別のパッチを提供します。 インストールされたバージョンのAdobe Commerceで使用可能な個々のパッチに関する一般情報を適用、元に戻して表示できます。 パッチの開発者に関係なく、Adobe CommerceおよびMagento Open Sourceプロジェクトにパッチを適用できます。 例えば、コミュニティが開発したパッチをAdobe Commerce プロジェクトに適用できます。

>[!INFO]
>
>Adobe Commerce プロジェクトにパッチを適用する手順については、[ パッチの適用 ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html#apply-individual-patches) を参照してください。 リリース済みパッチの完全なリストを確認するには、『ソフトウェア更新ガイド』の「[[!DNL Quality Patches Tool]：パッチの検索 ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)」を参照してください。

>[!INFO]
>
>コミュニティによって Magento Open Source 用に作成される [!DNL quality patches] について詳しくは、 [リリースノート](https://github.com/magento/quality-patches/blob/master/community-release-notes.md)を参照してください。

## v1.1.50 {#v1-1-50}

* **ACSD-59280** (Adobe Systems コマースおよび Magento Open Source >=2.4.4 &lt;2.4.5) - Fixes the error *未定義のメソッド ReflectionUnionType::getName()の呼び出し* これは、2.4.4-pX バージョンをインストールするときに発生します。
* **ACSD-45049** (Adobe SystemsコマースおよびMagento Open Source >=2.4.4 &lt;2.4.4-p8 ||=&quot;&quot;>=2.4.5 &lt;2.4.6) - Fixes the issue where a customer *[!UICONTROL Is required]* 属性設定は、管理のWebサイト範囲に従って正しく機能しません。&lt;/2.4.4-p8>
* **ACSD-46938** (Adobe Systemsコマースおよび Magento Open Source >=2.4.4 &lt;2.4.6) - Fixes the issue with the performance of DB triggers recreation during `setup:upgrade`。
* **ACSD-48210** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.7 の場合） – 特定のストアビューで *[!UICONTROL Website Scope]* 属性を更新すると、グローバルスコープの属性値が上書きされる問題を修正しました。
* **ACSD-54887** （Adobe CommerceおよびMagento Open Source >=2.4.4-p4 &lt;2.4.4-p9 || >=2.4.5-p3 &lt;2.4.5-p8 || >=2.4.6-p1 &lt;2.4.6-p6） - [!UICONTROL Persistent Shopping Cart] を有効にしてカスタマーセッションの有効期限が切れた後に、カスタマーショッピングカートがクリアされる問題を修正しました。
* **ACSD-58141** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.8 の場合） - [!DNL L2 Redis cache] が有効になっており、管理者から更新されている場合に、ログインしているお客様のストアフロント領域で PHPSESSID がPOSTリクエストで再生成される問題を修正しました。
* **ACSD-58352** （Adobe Commerce >=2.4.4 &lt;2.4.7 の場合） – リクエストヘッダーでデフォルト以外のストアビューが指定されている場合に、GraphQL API を介してデフォルトのストアビューの戻り属性ラベルが返される問題を修正しました。
* **ACSD-58442** （Adobe Commerce >=2.4.4 &lt;2.4.7-p1 の場合） – 幅 768 px のデバイスがモバイルとして扱われ、メニューとヘッダーがデスクトップではなくモバイルビューに読み込まれる問題を修正しました。
* **ACSD-58790** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.8 の場合） - [!DNL Chrome] のモバイルビューの製品詳細ページ画像のピンチからズームの機能を修正しました。
* **ACSD-59036** （Adobe CommerceおよびMagento Open Source >=2.4.7 &lt;2.4.8） – 下限と上限の両方が$0 の商品価格を読み込む場合に発生する例外を修正します。
* **ACSD-59229** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.7 の場合） – リクエストで X-Magento-Vary の古い値が原因で、お客様グループ関連の情報が間違ったセグメントに保存される問題を修正しました。
* **ACSD-59378** （Adobe CommerceおよびMagento Open Source >=2.4.5 &lt;2.4.6 の場合） – インポート中にストアレベルの URL の書き換えが誤って更新される問題を修正しました。
* **ACSD-59514** （Adobe Commerce >=2.4.4 &lt;2.4.7-p2 の場合） - Admin 領域内のフォームで、ロックを解除せずにレンダリング中のエラーを 5 秒間スローす *[!DNL Page Builder]問題を修正しまし [!DNL Page Builder]。* フォームを送信した後で ブラウザー コンソールに表示されると、変更を保存できません。
* **ACSD-60303** （Adobe Commerce >=2.4.4-p9 &lt;2.4.5） || >=2.4.5-p8 &lt;2.4.6 || >=2.4.6-p6 &lt;2.4.8） - HTMLの縮小が有効になっている場合に、管理者から注文できない問題を修正しました。
* **ACSD-60441** （Adobe CommerceおよびMagento Open Source 2.4.4-p9 用） || 2.4.5-p8 || 2.4.6-p6 || 2.4.7-p1） – バックエンドから生成された統合アクセストークンを使用す `V1/customers` 際に、[!DNL REST API] エンドポイントを介して顧客を更新する際の問題を修正しました。
* 更新されたパッチ：ACSD-57003

## v1.1.49 {#v1-1-49}

* **ACSD-56979** （Adobe CommerceおよびMagento Open Source >=2.4.3 &lt;2.4.7 の場合） – ステージングアップデートを削除した後に商品イメージが削除される問題を修正しました。
* **ACSD-57086** （Adobe CommerceおよびMagento Open Source >=2.4.3 &lt;2.4.7 の場合） – 利用条件が有効になっているデフォルト以外の web サイトから注文した注文が正しく処理されない問題を修正しました。
* **ACSD-57588** (Adobe Systems コマースおよび Magento Open Source >=2.4.6 &lt;2.4.7) - Fixes the issue where shipping an order to multiple addresses triggers an error during region ID processing.
* **ACSD-57643** （Adobe CommerceおよびMagento Open Source >=2.4.6 &lt;2.4.7） – GraphQLを使用してカスタムオプションを含む商品が買い物かごに誤って追加される問題を修正しました。
* **ACSD-57846** （Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.7） – GraphQL製品で価格ゼロのフィルターを使用して検索した場合、例外が原因で結果が返されない問題を修正しました。
* **ACSD-57941** （Adobe CommerceおよびMagento Open Source >=2.4.6 &lt;2.4.7 の場合） – 製品オプションが各ストアではなく管理ストアに誤って割り当てられる問題を修正しました。
* **ACSD-58375** （Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.7 の場合） – ストア表示レベルで [!DNL YouTube] ビデオを追加する際に、誤った *[!DNL YouTube API Key]* 設定が原因でエラーが発生する問題を修正しました。
* **ACSD-58739** (Adobe Systemsコマースおよび Magento Open Source >=2.4.7 &lt;2.4.8) - Fixes the issue where partial reindexing throws an error.
* **ACSD-58446** (Adobe Systems コマース >=2.4.6 の場合 &lt;2.4.7) - Fixes the issue where when deleting a team with child users or teams irrespective of their status (inactive), the system provides an uninformative error message not consistent with the UI.
* **ACSD-58054** (Adobe Systemsコマース >=2.4.4 の場合 &lt;2.4.6) - Fixes the issue where it is possible to generate customer tokens for inactive customers via API.
* **ACSD-58163** (Adobe Systems Commerce >=2.4.3 &lt;2.4.7) - Fixes the issue where a *[!UICONTROL Cart Price Rule]* の場合、クーポンコードのない照合 *[!UICONTROL Customer Segment]* 買い物かごからのゲスト顧客には割引が適用されません。
* **ACSD-57045** (Adobe Systemsコマース >=2.4.5 の場合 &lt;2.4.7) - Fixes the issue where URL rewrites cause infinite page looping after *[!UICONTROL Website Root]* は *[!UICONTROL Hierarchy]* からオフになっています。
* 更新されたパッチ: ACSD-46815、ACSD-47027、ACSD-51683、ACSD-55031、ACSD-51819、ACSD-54965-v2

## v1.1.48 {#v1-1-48}

* **ACSD-55566**(Adobe SystemsコマースおよびMagento Open Source >=2.4.3の場合、&lt;2.4.7) - Fixes the issue where the `mergeCart`同じバンドルアイテムを持つソースカートと宛先カートをマージすると、[!DNL GraphQL]応答で「*内部サーバー エラー*」で突然変異が失敗します。
* **ACSD-56546**(Adobe Systems Commerce および Magento Open Source >=2.4.4 &lt;2.4.7) - Fixes the issue where configurable and bundle products display as **製品コンフィギュレーション外の表示*****無効*ときにストアフロントで Stock** から。
* **ACSD-56635**(Adobe Systemsコマース >=2.4.6 &lt;2.4.7) - Fixes the issue where the imported customer is duplicated with the same email address, when an import is used with **アカウント共有の場合***グローバル*&#x200B;に設定されています。
* **ACSD-56741** (Adobe Systems Commerce および Magento Open Source >=2.4.6 &lt;2.4.7) - Fixes the error message &quot;*null 型の値の配列オフセットにアクセスしようとしています*」は、インデックス作成メカニズムと[!DNL MView]に関連しないカスタム[!DNL MySQL]トリガーがデータベースに含まれている`setup:upgrade`中に表示されます。
* **ACSD-57315** （Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.7 の場合） – [!DNL PayPal Payflow Pro] で新しいトランザクションが作成された際に、管理者の **[!UICONTROL View transaction]** 画面で「[!UICONTROL Fetch]」ボタンをクリックするたびに発生する問題を修正します。
* **ACSD-57337** （Adobe Commerce >=2.4.4 &lt;2.4.6 の場合） – 特定の web サイトへのアクセス制限を持つ管理者ユーザーが、**[!UICONTROL Companies]** グリッド内のすべての web サイトの会社を表示できる問題を修正しました。
* **ACSD-57394** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.7） – [!DNL GraphQL] で複数の並べ替えフィールドを使用して誤った商品が並べ替えられる問題を修正しました。
* **ACSD-57565** （Adobe CommerceおよびMagento Open Source >=2.4.6 &lt;2.4.7） – 期間が更新されるまで **[!UICONTROL Order]** ダッシュボードに誤った注文情報が表示される問題を修正しました。 ダッシュボードには、最初の読み込み時に正しい注文統計が表示されるようになりました。
* **ACSD-57854** （Adobe CommerceおよびMagento Open Source >=2.4.5 &lt;2.4.7） – カテゴリ集計で製品 [!DNL GraphQL] リクエストが無効なカテゴリを返した場合の問題を修正しました。
* **ACSD-58008** (Adobe Systems コマース >=2.4.5 の場合 &lt;2.4.7) - Fixes the issue where updating a scheduled update removed the previous version of a staged item, if no end date was specified.
* 更新されたパッチ:MDVA-39305-V2、ACSD-48627、ACSD-54965

## v1.1.47 {#v1-1-47}

* **ACSD-55241** (Adobe Systemsコマースおよび Magento Open Source >=2.4.2 &lt;2.4.7) - Fixes the issue where *[!UICONTROL Used]* および *[!UICONTROL Times Used]* 属性は、複数のアドレスでのチェックアウト中に使用すると、生成されたクーポンの誤った値を表示します。
* **ACSD-56760** (Adobe Systems コマース >=2.4.6 の場合 &lt;2.4.7) - Fixes the issue where an admin user restricted to a specific website cannot sort or add new products inside a category in case the webstore has its own root category.
* **ACSD-56858** (Adobe Systems Commerce >=2.4.2 の場合 &lt;2.4.7) - Fixes the issue where B2B company role permissions are displayed incorrectly for a restricted company admin.
* **ACSD-57074** （Adobe CommerceおよびMagento Open Source >=2.4.6 &lt;2.4.7 の場合） - `price_` で始まる `attrbute_code` の *はい/いいえ* カスタム属性がインデックス作成で正しく機能せず、そのような属性を持つ製品がフロントエンドで使用できない問題を修正しました。
* 更新されたパッチ：ACSD-53378、ACSD-51819

## v1.1.46 {#v1-1-46}

* **ACSD-46767** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.6 の場合） – 商品がまだ在庫にある場合でも、在庫数が変化するとカテゴリページのキャッシュが無効になる問題を修正しました。
* **ACSD-54656** （Adobe Commerce >=2.4.5 &lt;2.4.6 の場合） – チェックアウト時に非表示の Recaptcha が失敗して注文できなくなる問題を修正しました。
* **ACSD-55100** （Adobe Commerce >=2.4.6 &lt;2.4.7 の場合） – GraphQLが検索結果で 10,000 個を超える商品を返さない問題を修正しました。
* **ACSD-56621** （Adobe Commerce >=2.4.2 &lt;2.4.7 の場合） – 更新された名と姓が会社管理者ユーザーの「挨拶ヘッダー」セクションに反映されない問題を修正しました。
* **ACSD-56842** （Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.7 の場合） – `setup:di:compile` を実行した後、遅延プロキシと遅延プロキシファクトリが見つからない問題を修正しました。
* **ACSD-57003** （Adobe CommerceおよびMagento Open Source >=2.4.6 &lt;2.4.7） – 注文の一部が払い戻され、一部が出荷された場合に、注文ステータスが *[!UICONTROL Processing]* に変わるのではなく、*[!UICONTROL Complete]* に変わる問題を修正しました。
* 更新されたパッチ：ACSD-50260-v2、ACSD-54966

## v1.1.45 {#v1-1-45}

* **ACSD-56886** （Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.7） – スケジュールされた更新によって 2 つの子商品のいずれかが無効になると、設定可能な商品が在庫切れになる問題を修正しました。
* **ACSD-56616** （Adobe CommerceおよびMagento Open Source >=2.4.5 &lt;2.4.6） – バンドルされた商品が、シンプルな商品が在庫切れの場合にストアフロントに在庫として表示される問題を修正しました。
* **ACSD-56515** （Adobe Commerce >=2.4.2 &lt;2.4.7 の場合） – web サイトレベルの権限を持つ管理者が動的ブロックを追加または編集できない問題を修正しました。
* **ACSD-56447** (Adobe Systemsコマースおよび Magento Open Source >=2.4.2 の場合 &lt;2.4.7) - Fixes the issue where adding the same product to the cart via parallel REST web API requests results in two separate items in the cart.
* **ACSD-56415** (Adobe Systemsコマースおよび Magento Open Source >=2.4.5 &lt;2.4.7) - Fixes the issue where the performance of the partial price indexing is slowed down due to a `DELETE` クエリインデックスを作成する部分的な価格データがデータベースに多数ある場合。
* **ACSD-54965** （Adobe Commerce >=2.4.5 &lt;2.4.6 の場合） – 商品がカスタム在庫のみに割り当てられている場合に、ビジュアルマーチャンダイジンググリッドに正しい在庫が表示されない問題を修正しました。
* **ACSD-52824** （Adobe Commerce >=2.4.5 &lt;2.4.7 の場合） – 会社設定で支払い方法を無効にすると、会社のお客様に PayPal Express、Google Pay、Apple Pay のボタンが表示される問題を修正しました。
* 更新されたパッチ：ACSD-56193

## v1.1.44 {#v1-1-44}

* **ACSD-56790** （Adobe CommerceおよびMagento Open Source >=2.4.6 &lt;2.4.7 の場合） – 「**在庫切れまで下に移動**」オプションを使用してカテゴリ商品を並べ替えると、ユーザーが管理ダッシュボードにリダイレクトされ、`Invalid security or form key. Please refresh the page` エラーが画面の上部に表示される問題を修正しました。
* **ACSD-56280** （Adobe Commerce >=2.4.4 &lt;2.4.7 の場合） – ギフトレジストリから商品を注文すると例外が発生する問題を修正しました。
* **ACSD-56246** (Adobe Systemsコマースおよび Magento Open Source >=2.4.6 &lt;2.4.7) - Fixes the issue where data is removed from the custom multi-select attribute when a scheduled update for a product becomes active.
* **ACSD-56193** (Adobe Systemsコマースおよび Magento Open Source >=2.4.2 &lt;2.4.4) - Fixes the issue where the Varnish/Fastly cache is not updated when a scheduled block is used in the category description using Page Builder.
* **ACSD-56158** (Adobe Systems コマースおよび Magento Open Source >=2.4.5 &lt;2.4.7) - Fixes the issue where the &quot;cart&quot; query returns the total tax value for each tax rule.
* **ACSD-56023** (Adobe Systems コマースおよび Magento Open Source >=2.4.2 &lt;2.4.7) - Fixes the issue where widget content is not updating on the CMS page when cache is enabled.
* **ACSD-55427** (Adobe Systems コマース >=2.4.5 の場合 &lt;2.4.7) - Fixes the issue where the admin user cannot unassign a product from a shared catalog from the product page in the Admin.
* **ACSD-55352** （Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.7） – 顧客報酬ポイントを含む部分的なクレジットメモを作成した後、注文ステータスが「クローズ」に変わり、クレジットメモオプションが管理注文ページに表示されなくなる問題を修正しました。
* **ACSD-55231** （Adobe Commerce >=2.4.2 &lt;2.4.7 の場合） – クイックオーダー機能を使用して買い物かごに商品を追加できない問題を修正しました。
* **ACSD-54283** （Adobe Commerce >=2.4.3 &lt;2.4.4 の場合） – デフォルト（一般グループ）の Shared Catalog に割り当てられていない Products/Categories が、XML サイトマップに引き続き含まれる問題を修正しました。
* 更新されたパッチ：ACSD-52041、ACSD-54040、ACSD-51819

## v1.1.43 {#v1-1-43}

* **ACSD-54972** (Adobe Systemsコマースおよび Magento Open Source >=2.4.2 &lt;2.4.7) - Fixes the issue where the canonical category URL doesn&#39;t update after changing the category URL.
* **ACSD-53636** （Adobe CommerceおよびMagento Open Source >=2.4.3 &lt;2.4.5） – 特別価格の子商品を持つ設定可能な商品の商品一覧ページに通常価格が表示されない問題を修正しました。
* **ACSD-54885** （Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.7 の場合） – 管理者ユーザーが *顧客としてログイン* 機能を使用している場合の、複数のアドレスのチェックアウトの問題を修正しました。
* **ACSD-55610** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.7） – 部分的にキャンセルされた注文の割引額が正しくない問題を修正しました。
* **ACSD-55334** （Adobe CommerceおよびMagento Open Source >=2.4.3 &lt;2.4.7） - GraphQL レスポンスの翻訳辞書を使用したラベルの翻訳を修正します。
* **ACSD-54739** （Adobe Commerce >=2.4.5 &lt;2.4.7 の場合） – 関連する商品ルールに商品の在庫ステータス条件が適用されない問題を修正しました。
* **ACSD-53925** （Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.7 の場合） - `catalog_product_price` dimensions-mode が *website* に設定されている場合に、管理者が製品カルーセルでCMS ブロックを保存できない問題を修正しました。
* **ACSD-52714** （Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.7 の場合） – 日付フォーマットが *Y-m-d* に設定されている場合に、管理グリッドで日付フィルターが機能しない問題を修正しました。
* **ACSD-55055** (Adobe Systemsコマースおよび Magento Open Source >=2.4.2 の場合 &lt;2.4.7) - Improves performance of loading product attributes in cart price rules in the shopping cart.
* **ACSD-53790** (Adobe Systems コマース >=2.4.6 の場合 &lt;2.4.7) - Fixes the issue where Multiple RMAs for a single product can be created via REST API.
* **ACSD-56090** (Adobe Systems コマースおよび Magento Open Source >=2.4.2 &lt;2.4.5) - Fixes the issue where the GraphQL request is responding with all stores&#39; data rather than the specifically requested store data.
* **ACSD-54983** (Adobe Systems コマース >=2.4.2 &lt;2.4.7) - Fixes the issue where getting the company user UID with GraphQL request is not possible when the user status is set to *[!UICONTROL Inactive]*。
* **ACSD-53309** （Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.7） – カスタマイズ可能オプションが選択されている場合に、*[!UICONTROL Regular Price]* ラベルに税金が完全に適用されない問題を修正しました。
* **ACSD-55305** （Adobe Commerce >=2.4.4 &lt;2.4.7 の場合） – **[!UICONTROL myAccount]** > **[!UICONTROL Company Structure]** ページの *[!UICONTROL Edit Company User]* ポップアップが画面のローダーでフリーズする問題を修正しました。
* 更新されたパッチ：ACSD-49013

## v1.1.42 {#v1-1-42}

* **ACSD-53658** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.7） – ストアビューで商品データが適切 *[!UICONTROL Recently Viewed]* 更新されない問題を修正しました。
* **ACSD-54626** （Adobe Commerce >=2.4.6 &lt;2.4.7 の場合） - [!DNL GraphQL] を使用して `NUMBER_OF_SKUS` 属性を持つ新しい発注書ルール（`createPurchaseOrderApprovalRule`）を作成できない問題を修正しました。
* **ACSD-53845** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.7） – `consumer max_messages` = 0 の場合の [!DNL MySQL] connection timeout の問題を修正しました。
* **ACSD-54890** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.7） – ディスクの容量が不足しているために `aggregate_sales_report_bestsellers_data` が [!DNL MySQL] エラーを引き起こ `/tmp` 問題を修正しました。
* **ACSD-55112** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.7 の場合） - [!DNL Google reCAPTCHA v3] の検証を行わずに「*[!UICONTROL Submit review]*」ボタンを複数回クリックできる問題を修正しました。
* **ACSD-54264** （Adobe Commerce >=2.4.4-p5 &lt;2.4.5） || >=2.4.5-p4 &lt;2.4.6 || >=2.4.6-p2 &lt;2.4.7） – 「リクエストされた属性を更新できません *というエラーメッセージが表示される問題を修正しました。 行 ID:store_id&quot;* は、顧客が別のストアビューから交渉可能な見積もりでチェックアウトしようとすると表示されます。
* **ACSD-54418** (Adobe Systemsコマースおよび Magento Open Source >=2.4.0 &lt;2.4.7) - Fixes the issue where a fixed amount of discount is incorrectly applied to each child product of the dynamically priced bundle.
* **ACSD-55238** (Adobe Systems コマースおよび Magento Open Source >=2.4.4 &lt;2.4.7) - Fixes saving the empty product *[!UICONTROL Meta Description]*。
* **ACSD-54966** (Adobe Systemsコマースおよび Magento Open Source >=2.4.5 &lt;2.4.7) - Fixes the issue where a coupon code with a limited-use per customer can&#39;t be reused if the previous order failed.
* **ACSD-54060** （Adobe CommerceおよびMagento Open Source >=2.4.3 &lt;2.4.7 の場合） – 別のスコープに割り当てられた別の商品の子である場合、制限付き管理者が商品を保存できない問題を修正しました。
* **ACSD-48910** （Adobe CommerceおよびMagento Open Sourceの場合 >=2.4.5 &lt;2.4.6） – 複数のソースに割り当てられたバンドル製品が、数量がゼロ以外の場合でも、注文が請求および出荷された後に在庫切れになる問題を修正しました。
* **ACSD-55381** （Adobe Commerce >=2.4.2 &lt;2.4.7 用） – [!DNL GraphQL] を使用して [!DNL B2B] *[!UICONTROL Requisition list]* ーバーから `configurable_product_option_uid` フィールドと `configurable_product_option_value_uid` フィールドをクエリする際の内部サーバーエラーを修正します。
* **ACSD-55628** （Adobe Commerce >=2.4.4-p2 &lt; 2.4.5 の場合） || >=2.4.5-p1 &lt; 2.4.6） – 会社登録フォームへのファイルのアップロードと、ストアフロントの顧客属性のファイルの置き換えを修正しました。
* 更新されたパッチ：ACSD-51240、ACSD-51890、ACSD-53098

## v1.1.41 {#v1-1-41}

* **ACSD-54376** （Adobe Commerce >=2.4.2 &lt;2.4.7 の場合） – 商品が既に買い物かごに追加された後に共有カタログから削除された場合に、買い物かごで発生する問題を修正しました。
* **ACSD-53722** （Adobe Commerce >=2.4.4 &lt;2.4.7 の場合） – 異なる範囲のスケジュールされたアップデートがアクティブになると、バンドルされた製品オプションの価格が$0 に変わる問題を修正しました。
* **ACSD-53643** （Adobe Commerce >=2.4.3 &lt;2.4.7 の場合） – 使用不能または在庫切れの商品を含む注文を行った際に、注文の合計が正しく表示されない問題を修正しました。 このような発注書の *[!UICONTROL Place Order]* ボタンを非表示にすることで修正されます。
* **ACSD-54067** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.7 の場合） – モバイルデバイスで商品ビデオが再生されない問題を修正しました。
* **ACSD-55414** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.6） – MariaDB が EAV entity_id を文字列から整数にキャストしようとした際のパフォーマンスを向上させます。
* **ACSD-51819** （Adobe Commerce >=2.4.4 &lt;2.4.4-p4 の場合） – 同じ見積 ID で複数の注文を行える問題を修正しました。
* **ACSD-53118** （Adobe Commerce >=2.4.0 &lt;2.4.7 の場合） – 商品に空の属性がある場合に、クーポンコードを使用して *[!UICONTROL Cart Price Rule]* が適用される問題を修正しました。
* **ACSD-54324** （Adobe Commerce >=2.4.5 &lt;2.4.7 の場合） - GraphQLの requisition_lists リクエストでページネーションの設定が考慮されず、すべての結果が返される問題を修正しました。
* 更新されたパッチ: MDVA-42855-v2

## v1.1.40 {#v1-1-40}

* **ACSD-54680** (Adobe Systems コマース >=2.4.0 の場合 &lt;2.4.6) - Fixes the issue where it is not possible to process a B2B Quote submitted for a product with Multiple Assigned Sources.
* **ACSD-54040** (Adobe Systems Commerce の場合 >=2.4.4-p5 &lt;2.4.5 ||=&quot;&quot;>=2.4.5-p4 B2Bモジュールが有効になっている場合、 &lt;2.4.6) - Fixes the issue where the *[!UICONTROL Created]* フィールドは注文の詳細が空白になります。&lt;/2.4.5>
* **ACSD-54319** (Adobe Systemsコマースおよび Magento Open Source >=2.4.2 &lt;2.4.6) - Fixes the issue where the product price shows zero in the *[!UICONTROL Product in Cart]* レポート用。
* **ACSD-53378** （Adobe CommerceおよびMagento Open Source >=2.4.5 &lt;2.4.7） – 大きなアドレス帳を持つお客様のチェックアウトページの読み込み時間を改善します。
* **ACSD-52657** （Adobe CommerceおよびMagento Open Source >=2.4.5 &lt;2.4.7 の場合） – サブドメインを使用するセカンダリストレビューでミニカートが更新されない問題を修正しました。
* **ACSD-53414** （Adobe Commerce >=2.4.6 &lt;2.4.7 の場合） – 制限付き管理者ユーザーが、権限適用範囲外でCMS ページを表示できる問題を修正しました。
* **ACSD-54472** （Adobe Commerce >=2.4.6 &lt;2.4.7 の場合） – 拒否された会社の顧客が認証を行い、ブロックされた会社と拒否された会社の顧客が注文を行える問題を修正しました。 このパッチは、GraphQL エンドポイントの検証をさらに強化します。
* **ACSD-52801** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.7 の場合） - GraphQLで商品を検索する際に部分一致を行うオプションを追加します。
* **ACSD-55004** （Adobe CommerceおよびMagento Open Source >=2.4.6 &lt;2.4.7 の場合） - `php.ini` で設定された値を超える読み込みファイルをアップロードする際にバリデーターがクラッシュする問題を修正しました。
* **ACSD-54989** （Adobe Commerce >=2.4.4-p5 &lt;2.4.5） || >=2.4.5-p4 &lt;2.4.6 || >=2.4.6-p2 &lt;2.4.7） - *[!UICONTROL Enable Purchase Orders]* が *[!UICONTROL Yes]* に設定され、*[!UICONTROL Purchase Order]* が *[!UICONTROL No]* に設定されている場合に、会社管理者が注文できない問題を修正しました。
* **ACSD-54007** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.7 の場合） – カスタマーデータの読み込み時のエラー *&quot;未定義の配列キー&quot;_scope&quot;* を修正しました。
* **ACSD-55031** （Adobe CommerceおよびMagento Open Source >=2.4.5 &lt;2.4.6 の場合） – コンパイル中に *Type &quot;mixed&quot;を nullable にすることはできません* エラーが修正されました。
* **ACSD-54961** (Adobe Systemsコマースおよび Magento Open Source >=2.4.0 &lt;2.4.7) - Fixes the issue where a restricted admin user cannot mass update the *商品レビュー* ステータスの場合。
* **ACSD-55256** （Adobe CommerceおよびMagento Open Source >=2.4.6 &lt;2.4.7 の場合） – 最初の画像のみが画像スライダーに正常に表示される問題を修正しました。
* 更新されたパッチ：ACSD-52041、ACSD-54106

## v1.1.39 {#v1-1-39}

* **ACSD-53704** （Adobe Commerce >=2.4.0 &lt;2.4.7 の場合） – 報酬ポイントの有効期限が切れた後に、報酬ポイントのバランス履歴が誤って計算される問題を修正しました。
* **ACSD-53583** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.7） – *Category Products* および *Product Categories* インデクサーの部分的なインデックス再作成のパフォーマンスを向上します。
* **ACSD-54026** （Adobe Commerce >=2.4.6 &lt;2.4.7 の場合） – 許可されていないユーザーに対する `updateCompanyRole` GraphQL リクエストで発生する誤ったエラーメッセージを修正します。
* **ACSD-54106** （Adobe CommerceおよびMagento Open Source >=2.4.1 &lt;2.4.5 の場合） – トルコ語のアクセント記号用にカテゴリ商品を名前で並べ替えると問題が発生する問題を修正しました。
* **ACSD-52219** (for Adobe Commerce and Magento Open Source >=2.4.5 &lt;2.4.7) - Fixes the issue where Admin grids saved filters don&#39;t work as expected when frequently switching between bookmark views.
* **ACSD-54342** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.7 の場合） – 有効なデータのない CSV ファイルを読み込む際に、誤ったエラーメッセージ *データ構造のエラー：値が混在します* を修正しました。
* **ACSD-54660** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.6） - GraphQLのお客様の注文を `sort_field` と `sort_direction` で並べ替える新しい入力属性 *sort* が追加されました。
* **ACSD-54776** （Adobe Commerce >=2.4.5 &lt;2.4.7 の場合） - 2 つ目の web サイト、ストア、ストア表示で、オフの *[!UICONTROL Use Default Value]* フィールドとデフォルト以外の製品フィールドの値が保存されない問題を修正しました。
* **ACSD-53998** （Adobe CommerceおよびMagento Open Sourceの場合 >=2.4.4-p2 &lt;2.4.5 || >=2.4.5-p1 &lt;2.4.7） – カスタマーアカウントからログアウトした後、**[!UICONTROL Customer Segment]** に基づく **[!UICONTROL Dynamic Block]** が正しく機能しない問題を修正しました。
* **ACSD-53204** （Adobe CommerceおよびMagento Open Source >=2.4.6 &lt;2.4.7） – 修正点 *商品を保存できません。`rest/V1/products/<sku>/media` エンドポイントを使用して製品ギャラリーに画像を追加する同時リクエストを行う際に* エラーが発生します。
* **ACSD-47657** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.7） – AWS資格情報のキャッシングメカニズムを追加しました。 資格情報プロバイダーは、Magentoキャッシュを使用して、EC2 設定用にAWSから取得した資格情報をキャッシュするようになりました。
* パッチを更新：ACSD-51984、ACSD-51574。

## v1.1.38 {#v1-1-38}

* **ACSD-53098** (Adobe Systemsコマースおよび Magento Open Source >=2.4.3 &lt;2.4.4) - Fixes the issue where products assigned to a shared catalog do not appear on the storefront when a partial index is executed.
* **ACSD-54018** (Adobe Systemsコマースおよび Magento Open Source >=2.3.7 &lt;2.4.6) - Fixes the performance issues with the [!UICONTROL Product List] ウィジェット条件で非グローバル属性を使用するウィジェット。
* **ACSD-54111** (Adobe Systems コマースおよび Magento Open Source >=2.4.2 &lt;2.4.6) - Fixes the issue where the product thumbnail images are not displayed on the storefront when the aspect ratio of the watermark image does not match the product image.
* **ACSD-47669** (Adobe Systems コマースおよび Magento Open Source >=2.4.2 &lt;2.4.6) - Fixes *整合性制約違反: 1452 子行を追加または更新できません。外部キー制約が失敗し* 製品CSVをインポートするときにエラーが発生します。
* **ACSD-53347** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.4.7） – price indexer の実行に時間がかかりすぎる問題を修正しました。
* **ACSD-52287** （Adobe Commerce >=2.3.7 &lt;2.4.7 の場合） – 非同期グリッドインデックス作成が有効な場合に、アーカイブされたオーダーグリッドで誤ったオーダーステータスの問題を修正しました。
* **ACSD-52929** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.4.7 の場合） – インベントリインデクサーが非同期モードで設定されている場合に、デフォルトのソースアイテムを再インデックス化する冗長リクエストの問題を修正しました。
* **ACSD-53824** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.7 の場合） – `setup:upgrade` 行中に移行データパッチがデータベーストランザクションサイズの制限 `UpdateMultiselectAttributesBackendTypes` 超える問題を修正しました。

## v1.1.37 {#v1-1-37}

* **ACSD-52613** （Adobe CommerceおよびMagento Open Source >=2.4.6 &lt;2.4.7） – REST API によって `Inventory_source` の項目が更新されない場合でもキャッシュとインデックスが更新される問題を修正しました。
* **ACSD-51884** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.4.7 の場合） - resize コマンドを実行すると、商品イメージのキャッシュパスが正しくなくなる問題を修正しました。
* **ACSD-53628** (Adobe Systemsコマースおよび Magento Open Source >=2.3.7 &lt;2.4.7) - Fixes the issue where the CSV sales order report shows incorrect special characters.
* **ACSD-53148** (Adobe Systems コマースおよび Magento Open Source >=2.4.4 &lt;2.4.7) - Fixes the issue where two parallel requests in GraphQL for adding the same configurable product to the cart resulted in two separate items on the cart with the same product SKU.
* **ACSD-52606** (Adobe Systems Commerce および Magento Open Source >=2.4.0 &lt;2.4.7) - Fixes the issue where the error message *ご注文は集荷の準備ができていません* は、ユーザーが **[!UICONTROL Notify Order is Ready for Pickup]**&#x200B;をクリックすると表示されます。
* **ACSD-51574** (Adobe Systems コマースおよび Magento Open Source >=2.4.2 &lt;2.4.7) - Fixes the issue where the image is not updated on the frontend after replacing it with another image with the same name.
* **ACSD-53728** (Adobe Systems コマースおよび Magento Open Source >=2.3.7 &lt;2.4.7) - Fixes the issue where the product EAV indexer is taking longer to complete.
* **ACSD-53979** （Adobe CommerceおよびMagento Open Source >=2.4.6 &lt;2.4.7 の場合） – ようこそメッセージに一重引用符が含まれている場合にホームページで発生する JS の問題を修正します。
* **ACSD-52085** （Adobe CommerceおよびMagento Open Source >=2.4.5 &lt;2.4.7 の場合） – 設定可能な特別価格の商品が商品のカルーセルに表示されない問題を修正しました。
* **ACSD-53795** （Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.7） – cron ジョブで無効なデータタイプに関する問題 `indexer_update_all_views` 修正。
* **ACSD-52143** （Adobe CommerceおよびMagento Open Source >=2.4.6 &lt;2.4.7 の場合） – 製品の読み込み後にカスタムオプションが削除される問題を修正しました。
* **ACSD-53750** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.7 の場合） – マルチスレッド `catalog_product_price` の再インデックス中に発生した *パイプの破損または接続の切断* エラーを修正します。
* **ACSD-49843** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.4.0 || >=2.4.1 &lt;2.4.7） -**[!UICONTROL Payment Action]** = **[!UICONTROL Sale]** 設定が有効になっているオンライン支払い方法で注文品目の自動請求が行われた後、製品のダウンロードのリンクが使用できなくなる問題を修正しました。
* **ACSD-47054** （Adobe Commerce >=2.4.2 &lt;2.4.6 の場合） – プレビューの再インデックスですべてのストアに対して再インデックスを実行すると、速度が低下する問題を修正しました。
* ACSD-46541、ACSD-47079 の新しいバージョンを追加しました。
* ACSD-49970-v3 は ACSD-54095 に置き換えられました。

## v1.1.36 {#v1-1-36}

* **ACSD-53239** （Adobe CommerceおよびMagento Open Source >=2.4.3 &lt; 2.4.6 の場合） – インベントリインデクサーがスケジュールに従って更新モードですべてのキャッシュをクリーンアップする問題を修正しました。
* **ACSD-50887** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.7 の場合） – product 属性のプロパティ *[!UICONTROL Use in Search Results Layered Navigation]* を *はい* に設定でき、*[!UICONTROL Use in search]* オプションを *はい* に設定できない問題を修正しました。
* **ACSD-51846** （Adobe CommerceおよびMagento Open Source >=2.4.3-p2 &lt;2.4.6） – REST API ペイロードの一部のレベルが検証されないために発生する *内部エラー* 問題を修正しました。
* **ACSD-52906** （Adobe Commerce >=2.3.7 &lt;2.4.7 の場合） – 同じカスタマーセグメントに属するログインした顧客が一部のページで不適切なキャッシュを発生させ、X-Magento変数 cookie が正しく設定されない問題を修正しました。
* **コンフィギュレーション可能な製品量の要件を含む ACSD-52736** (Adobe Systemsコマースおよび Magento Open Source >=2.3.7 &lt;2.4.6) - Fixes the issue where a *買い物かご価格ルール* が期待どおりに機能しません。
* **ACSD-47875** (Adobe Systemsコマースおよび Magento Open Source >=2.3.7 &lt;2.4.7) - Fixes the issue where admin users are not able to add a product to a customer cart from the Admin for a particular store view scope with inventory management.
* **ACSD-53176**(Adobe Systemsコマース >=2.3.7 &lt;2.4.5) - Fixes the issue where *関連製品ルール**次のいずれか*&#x200B;の条件が製品と一致しません。
* **ACSD-51666** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.4.7 の場合） – エラーを修正しました *セッションの有効期限が切れました。もう一度ログインしてください。これは、ユーザーがログインを試みた後で* 生します。
* MDVA-39305-v2 の新しいバージョンを追加しました。
* ACSD-19640 の要件を更新しました。

## v1.1.35 {#v1-1-35}

* **ACSD-51899** (Adobe Systemsコマースおよび Magento Open Source >=2.4.0 &lt;2.4.7) - Fixes the issue where the default shipping address on the checkout shipping step is auto-populated with a previously selected in-store pickup address.
* **ACSD-52041** (Adobe Systemsコマースおよび Magento Open Source >=2.4.4 &lt;2.4.7) - Fixes the issue where the error message: *[エラー] [!DNL Page Builder] は、ロックを解除せずに 5 秒間レンダリングされていました。*[!DNL Page Builder]で編集内容保存すると、クロム ブラウザーに表示されます。
* **ACSD-52095** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.4.6 の場合） – 商品の書き出し後に CSV ファイルで `manage_stock` 値が正しく 0 に設定されない問題を修正しました。
* **ACSD-51358** （Adobe Commerce >=2.4.5 &lt;2.4.7 の場合） – 終了日を指定せずにスケジュール済み更新を削除すると、同じエンティティの他のスケジュール済み更新が削除される問題を修正しました。
* **ACSD-48070** （Adobe Commerce >=2.3.7 &lt;2.4.7 の場合） – スケジュールされた更新を編集すると例外がトリガーされる問題を修正しました。
* **ACSD-51890** (Adobe Systems コマースおよび Magento Open Source >=2.4.0 の場合 &lt;2.4.7) - Fixes the issue where the [!UICONTROL Submit review] ボタンv3 [!DNL Google reCAPTCHA] 検証なしで複数回クリックできます。
* **ACSD-51984** (Adobe Systems コマース >=2.4.5 の場合 2 番目の Web サイト、ストア および ストア 表示 では、 &lt;2.4.7) - Fixes the issue where unchecked *[!UICONTROL Use Default Value]* および *[!UICONTROL non-default product field]* の値は保存されません。
* **ACSD-52398** (Adobe Systems Commerce および Magento Open Source >=2.4.0 &lt;2.4.7) - Fixes the error *要求された数量は利用できません* で、ストアフロントの買い物かごでバンドルされた製品の量を更新しようとしたときに発生します。
* **ACSD-52786** (Adobe Systems Commerce および Magento Open Source >=2.4.5 &lt;2.4.6) - Fixes the issue where a catalog rule condition *SKUの場合* は、指定されたSKUで始まるすべての商品に適用されます。
* **ACSD-52921** (Adobe Systemsコマースおよび Magento Open Source >=2.4.5 &lt;2.4.7) - Fixes the issue where an internal error occurs if requesting cart details from GraphQL when there is an out-of-stock configurable product in the cart.
* **ACSD-51683** (Adobe Systems コマースおよび Magento Open Source >=2.4.6 &lt;2.4.7) - Fixes the issue where a customizable option can&#39;t be added to the cart using GraphQL.
* **ACSD-52133** （Adobe CommerceおよびMagento Open Source >=2.4.6 &lt;2.4.7）の場合 – アップグレード後にカスタマーアカウントを保存できない問題を修正しました。
* **ACSD-52202** (Adobe Systemsコマースおよび Magento Open Source >=2.4.3 &lt;2.4.7) - Fixes the issue where the salable qty of default stock wrongly changes to 0 when a non-default stock is changed to 0 qty on order fulfillment.
* **ACSD-51265** (Adobe Systems Commerce および Magento Open Source >=2.4.2 の場合 &lt;2.4.7) - Fixes the issue with `catalog_product_price` システムにバンドルされている製品が多すぎる場合のインデックス再作成パフォーマンス。
* **ACSD-52831** (Adobe Systemsコマース >=2.3.7 の場合、 &lt;2.4.7) - Fixes the issue where customers cannot place negotiable quote orders when [!DNL Google reCAPTCHA v3 Invisible] は有効になっています。
* **ACSD-51845** (Adobe Systemsコマースおよび Magento Open Source >=2.4.4 &lt;2.4.7) - Fixes the issue where subsequent products with tier prices and different attribute sets cannot be updated via asynchronous bulk REST API.
* **ACSD-52815** (Adobe Systemsコマースおよび Magento Open Source >=2.3.7 &lt;2.4.7) - Fixes the issue where the input for the quantity field of a non-default source supports only up to 6 digits, unlike 8 for a default stock.
* **ACSD-51149** （Adobe Commerce >=2.3.7 &lt;2.4.7 の場合） – カタログアクセス権を有効にしたスケジュール済みインポートエクスポートによってインデクサーが無効になり、Cron によるキャッシュフラッシュが発生する問題を修正しました。
* **ACSD-50815** （Adobe CommerceおよびMagento Open Source >=2.4.5 &lt;2.4.6） – 新しいバンドル商品オプションで、シンプル商品の 10 進数の数量を使用できない問題を修正しました。
* ACSD-47803 のバージョンを更新しました。
* ACSD-51892 のタイトルを更新しました。
* ACSD-51379 を更新しました。
* ACSD-49970-v2 を更新しました。

## v1.1.34 {#v1-1-34}

* **ACSD-52277** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.7 の場合） – 管理者で新しい注文を作成する際にストア表示を選択した後、管理者ユーザーが適切にリダイレクトされない問題を修正しました。
* **ACSD-50813** （Adobe Commerce >=2.4.5 &lt;2.4.7 の場合） – 管理者が、[!UICONTROL Add Products by SKU] 機能を持つ SKU にスラッシュを含むバンドル製品を管理注文に追加できなかった問題を修正しました。
* **ACSD-51630** （Adobe CommerceおよびMagento Open Source >=2.4.3 &lt;2.4.7） – 大量のシステムメッセージが原因で管理ページのダウンロードが遅くなる問題を修正しました。
* **ACSD-51853** （Adobe CommerceおよびMagento Open Source >=2.4.1 &lt;2.4.7） – [!UICONTROL Page Builder] を使用した際に、コピーしたテキストスタイルが適用されない問題を修正しました。
* **ACSD-52160** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.7 の場合） – 買い物かごの価格ルールに対する商品の検証結果が、ルール条件「If an item is FOUND/NOT FOUND in the cart with All/Any of these conditions true」に基づいて適切に評価されなかった問題を修正しました。
* **ACSD-51636** （Adobe Commerce >=2.4.5 &lt;2.4.7 の場合） – 必要な役割と権限がすべて揃っているにもかかわらず、会社管理者がカスタマーアカウントセクションから新しいユーザーを追加できない問題を修正しました。
* **ACSD-51739** （Adobe Commerce >=2.4.6 &lt;2.4.7 の場合） - CompanyTeam GraphQL リクエストで `structure_id` がリクエストされた場合にエラーが返される問題を修正しました。
* **ACSD-51857** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.7 の場合） – 大規模な sales_order および `sales_order_item` のデータベーステーブルに関する `aggregate_sales_report_bestsellers_data` cron レポートのパフォーマンスが遅い原因が、メインのデータクエリの書き込み方法にあった問題を修正しました。
* **ACSD-48448** （Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.7） – 注文のキャンセル中に競合状態の問題が発生し、`inventory_reservation` テーブルでエントリが重複する問題を修正しました。
* **ACSD-52689** (Adobe Systems コマースおよび Magento Open Source >=2.4.3 &lt;2.4.6) - Fixes the issue where images cannot be uploaded to Amazon S3 storage using REST API.
* **B2B-2674** (Adobe SystemsコマースおよびMagento Open Source > = 2.4.4 &lt;2.4.7) - Add caching capability to the 1customAttributeMetadata1 GraphQL query.
* ACSD-44938 の新しいバージョンを追加しました。
* ACSD-46988 の要件を追加しました。

## v1.1.33 {#v1-1-33}

* **ACSD-50478** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.5 の場合） - DB ダンプにトリガーと *区切り文字* SQL コマンドが含まれている場合に、データベースのロールバックコマンドを修正します。
* **ACSD-50512** （Adobe Commerce >=2.4.5 &lt;2.4.7 の場合） – *エラー：ダウンロード可能なリンクは商品に関連していません。 リンクを確認して、もう一度試してください。ダウンロ* ド可能な製品のステージング更新の開始日を更新する際に発生するエラー。
* **ACSD-50949** （Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.7 の場合） - SKU フィルターと共に使用した場合に、詳細検索で価格フィルターが適切な結果を返さない問題を修正しました。
* **ACSD-51645** （Adobe CommerceおよびMagento Open Source >=2.4.6 &lt;2.4.7 の場合） – 拡張機能 `Magento_OfflineShipping` が無効になっている場合に、新しい買い物かご価格ルールを保存する際にスローされるエラーを修正しました。
* **ACSD-50895** （Adobe Commerce >=2.4.5 &lt;2.4.7 の場合） - [!DNL Google Analytics] 4 GTM が設定されていない場合に [!DNL Google Analytics] 3 GTM タグが実行されない問題を修正しました。
* **ACSD-51102** （Adobe Commerce >=2.4.2 &lt;2.4.7 の場合） – 予定されている更新によってルールが有効になっている場合に、多数の商品に適用されるカタログルールが正しくインデックス化されない問題を修正しました。
* **ACSD-50368** （Adobe CommerceおよびMagento Open Sourceの場合 >= 2.4.3 &lt;2.4.5） – 非同期 REST API または非同期バルク REST API を使用してカスタマーを作成する際にカスタマーの `group_id` が無視される問題を修正しました。
* **ACSD-51497** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.4.0 || >= 2.4.1 &lt;2.4.7） – 顧客がドロップダウンタイプのカスタム属性でカタログページを並べ替えることができない問題を修正しました。
* **ACSD-51408** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt; 2.4.7 の場合） – 注文項目のステータスが正しく *[!UICONTROL Backordered]* に設定されない問題を修正しました。
* **ACSD-51735** (for Adobe Commerce and Magento Open Source >=2.4.4 &lt;2.4.5) - Fixes the issue where the order item status is incorrectly set to *[!UICONTROL Ordered]* when the product stock is *0*.
* **ACSD-51792** (for Adobe Commerce and Magento Open Source >=2.4.5 &lt;2.4.6) - Fixes the issue where a page does not have the impression event when [!DNL Google Tag Manager] 4 is enabled.
* **ACSD-51471** (for Adobe Commerce >=2.4.3 &lt;2.4.7) - Fixes the issue where an admin user cannot save a scheduled update for a bundled product that uses a simple product that itself has a scheduled update.
* **ACSD-51700** (for Adobe Commerce and Magento Open Source >=2.4.3 &lt;2.4.7) - Fixes the error that happens when switching store views on a downloadable product edit page in the admin.
* **ACSD-51120** （Adobe Commerce >=2.3.7 &lt;2.4.3 の場合） – ステージングアップデートにより更新されたGraphQL ブロックを含んだCMS ページのCMS GETリクエストのキャッシュがクリアされない問題を修正しました。
* **ACSD-51240** （Adobe Commerce >=2.4.4 &lt;2.4.6 の場合） – 会社登録フォームから登録した場合に、アップロードしたファイルが見つからない問題を修正しました。
* **ACSD-51907** （Adobe Commerce >=2.4.2 &lt;2.4.3 の場合） – 制限付き管理者ユーザーが、オフラインでの返金を含むクレジットメモを作成できない問題を修正しました。
* **ACSD-52148** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.4 の場合） – [!DNL Google V3 reCAPTCHA] Admin のログインが時々失敗する問題を修正しました。
* **ACSD-51431** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.4.7 の場合） - changelog に新しいエントリがない場合でも、インデクサーのステータスが *動作* する問題を修正しました。
* **ACSD-51892** (for Adobe Commerce and Magento Open Source >=2.4.6 &lt;2.4.7) - Fixes the performance issue where config files load multiple times.
* Deprecated ACSD-51114.

## v1.1.32 {#v1-1-32}

* **ACSD-49628** (for Adobe Commerce and Magento Open Source >=2.4.2 &lt;2.4.7) - Fixes the issue where the [!UICONTROL Page Builder's] multiple errors prevent admin from saving a product without content permissions.
* **ACSD-51305** (for Adobe Commerce and Magento Open Source >=2.4.6 &lt;2.4.7) - Fixes the issue where out-of-stock configurable child products are not available in the GraphQL response.
* **ACSD-50621** （Adobe Commerce >=2.3.7 &lt;2.4.7 の場合） – マルチサイト環境で編集しようとすると、共有カタログ内の様々な web サイトの [!UICONTROL Tier Prices] が表示されない問題を修正しました。
* **ACSD-51041** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.4.0 || >=2.4.1 &lt;2.4.6） – 価格インデクサーのパフォーマンスを向上させます。
* **ACSD-51379** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.4.7） – [!UICONTROL Page Builder] を使用してページテキストコンテンツに加えられた変更が保存されない問題を修正しました。
* **ACSD-49480** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.6 の場合） – カートに適用されるカート価格ルールが 1 つだけの問題を修正しました。
* **ACSD-51230** (for Adobe Commerce >=2.3.7 &lt;2.4.7) - Fixes the issue where the gift card account is deleted when a partial refund of a simple product is processed from an order.
* **ACSD-51238** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.7） – 設定可能な商品をアップデートして価格を編集すると、在庫ソースが削除される問題を修正しました。
* **ACSD-50794** （Adobe Commerce >=2.4.1 &lt;2.4.7 の場合） - GraphQLから削除すると、ギフトメッセージやギフトラッピングの詳細がデータベースで更新されない問題を修正しました。
* **ACSD-51528** （Adobe CommerceおよびMagento Open Source >=2.4.5 &lt;2.4.7 の場合） - *x_forwarded_for* 列が *sales_order* テーブルに null 値を持つ問題を修正しました。
* **ACSD-50849** （Adobe Commerce >=2.4.4 &lt;2.4.6 の場合） – キャッシュをクリアした後に新しい商品をカテゴリに追加すると、既存の商品の位置と選択内容が一致しなくなる問題を修正しました。
* **ACSD-51294** （Adobe CommerceおよびMagento Open Source >=2.4.5 &lt;2.4.7） – GTM/GA の価格、数量、税金、送料、売上高が文字列として [!DNL Google Analytics] および GTM に送信される問題を修正しました。
* **ACSD-51204** (for Adobe Commerce and Magento Open Source >=2.4.3 &lt;2.4.7) - Fixes the issue where a fully sold product doesn&#39;t return back in stock after creating a credit memo.
* **ACSD-51291** (for Adobe Commerce and Magento Open Source >=2.4.4 &lt;2.4.4-p4 || >=2.4.5 &lt;2.4.5-p3) - Fixes the issue where restricted admin with access to one website can add images/videos to the product assigned to multiple websites.
* ACSD-50336 の新しいバージョンを追加しました。
* パッチ ACSD-49970 を交換してください。

## v1.1.31 {#v1-1-31}

* **ACSD-50345** （Adobe CommerceおよびMagento Open Source >=2.4.3 &lt;2.4.4 || >=2.4.4-p1 &lt;2.4.6） – 支払いに失敗した後、Recaptcha v2 がリロードされない問題を修正しました。
* **ACSD-50817** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.4.7） – Cron ジョブ `sales_clean_quotes` ードを最適化して、実行速度を向上させます。
* **ACSD-49392** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.4.0 || >= 2.4.1 &lt;2.4.7） – バンドルされた製品の部分払い戻しの後に注文ステータスがクローズに変更される問題を修正しました。
* **ACSD-51036** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.5） – REST API の同時呼び出し時の競合状態によって、[!UICONTROL Items Ordered] テーブルの配送ステータス情報が上書きされる問題を修正しました。
* **ACSD-50858** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.7） – バナーのコンテンツの読み込みパフォーマンスを向上しました。
* MDVA-39305-v2、ACSD-45169 の新しいバージョンを追加しました。
* パッチ ACSD-50260-v2 を更新しました。

## v1.1.30 {#v1-1-30}

* **ACSD-50336** (Adobe Systemsコマースおよび Magento Open Source >=2.4.4-p1 &lt;2.4.4-p3) - Fixes the issue where product alert emails are not sent when a product is back in stock or the price is changed.
* **ACSD-50367** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.4.7 の場合） – 値のない複数選択の顧客アドレス属性が作成された場合に、顧客アドレスのエクスポートが機能しない問題を修正しました。
* **ACSD-49877** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.4.7 の場合） – ビデオがストリーミングサービスではなくリモートビデオファイルに直接リンクされている場合に、モバイル [!DNL Safari] でビデオの自動再生が機能しない問題を修正しました。
* **ACSD-50165** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.7 の場合） – エラーを修正しました *ファイルを削除できません。 警告！unlink：管理者から JS/CSS キャッシュをフラッシュする際に* そのようなファイルやディレクトリはありません。
* **ACSD-49737** （Adobe CommerceおよびMagento Open Source >=2.4.1-p1 &lt;2.4.7） – カードの支払いに失敗した後、クーポンが誤って使用されているとマークされる問題を修正しました。
* **ACSD-50814** （Adobe CommerceおよびMagento Open Source >=2.4.6 &lt;2.4.7 の場合） – 管理者ユーザーがクレジットメモを作成できない問題を修正しました。
* **ACSD-50116** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.4.7 の場合） – 管理者ユーザーがサブカテゴリレベル 3 以下の URL の書き換えを作成できない問題を修正しました。
* **ACSD-49513** （Adobe CommerceおよびMagento Open Source >=2.4.3 &lt;2.4.5） – 0 バイトのファイルが原因でリモートストレージの同期が失敗する問題を修正しました。
* **ACSD-46683** (Adobe Systems コマースおよび Magento Open Source >=2.4.2 &lt;2.4.7) - Fixes the issue where the shipping price shows *未計算*。
* **ACSD-49129** (Adobe Systems コマースおよび Magento Open Source >=2.4.2 の場合) &lt;2.4.6) - Fixes the issue where the *[!UICONTROL content]* 属性 (base64 イメージ コード) は `rest/V1/products/sku/media` 製品メディア API 応答で返されません。
* **ACSD-50276** (Adobe Systemsコマース >=2.4.0 の場合 &lt;2.4.7) - Fixes the issue where the customer registration form doesn&#39;t work on the storefront if a multi-select customer attribute is created.
* **ACSD-50527** （Adobe Commerce >=2.3.7 &lt;2.4.7 の場合） – 空のダイナミックブロックを含んだページを保存したときに発生するエラーを修正しました。
* **ACSD-49973** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.5） – GraphQLを通じてバンドルされた製品を取得する際のパフォーマンスを向上させます。
* **ACSD-51114** （Adobe CommerceおよびMagento Open Source >=2.4.3 &lt;2.4.7） – 非同期インデックス作成が有効になっている場合に、大きなカタログからランダムな商品が消える問題を修正しました。 大規模なカタログの非同期インデックス再作成のパフォーマンスを向上します。
* **B2B-2598** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.7） – [!UICONTROL availableStores]、[!UICONTROL countries]、[!UICONTROL country]、[!UICONTROL currency] および [!UICONTROL storeConfig] GraphQLの各クエリにキャッシュ機能を追加します。
* MDVA-42806、ACSD-48627、ACSD-46815 の新しいバージョンを追加しました。
* ACSD-49773、ACSD-47179、ACSD-48300 のパッチメタデータを更新しました。

## v1.1.29 {#v1-1-29}

* **ACSD-49389** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.7） – 注文が受け取り可能でない場合に、API によって受け取り可能なメールが送信される問題を修正しました。
* **ACSD-49822** （Adobe Commerce >=2.3.7 &lt;2.4.7 の場合） – [!UICONTROL Requisition List] ページの更新が [!UICONTROL Print Requisition List] に反映されない問題を修正しました。
* **ACSD-48771** （Adobe CommerceおよびMagento Open Source >=2.4.5 &lt;2.4.7 の場合） – 列ブロックコンテンツタイプを旧バージョンからアップグレードする際の問題を修正し [!DNL Page Builder] した。
* **ACSD-49464** （Adobe Commerce >=2.3.7 &lt;2.4.7 の場合） - orderId が異なる場合に、請求書、出荷、クレジットメモがアーカイブから戻されない問題を修正しました。
* **ACSD-49773** （Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.6） – AWS S3 をリモートストレージとして使用した場合に製品の書き出しが失敗する問題を修正しました。
* **ACSD-49748** （Adobe Commerce >=2.3.7 &lt;2.4.7 の場合） – 招待状を送信できない問題を修正しました。
* **ACSD-49502** （Adobe Commerce >=2.4.3 &lt;2.4.7 の場合） – ダウンロード可能な製品にステージングアップデートを適用した後、ダウンロード可能なリンクが適切に更新されない問題を修正しました。
* **ACSD-49527** （Adobe Commerce >=2.4.2 &lt;2.4.7 の場合） - GraphQLの会社ロールでページネーションが正しく表示されない問題を修正しました。
* **ACSD-49706** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.4.7 の場合） – 値が選択されていない場合に、ビジュアルスウォッチ属性に対してデフォルト値が保存される問題を修正しました。
* **ACSD-49835** （Adobe CommerceおよびMagento Open Source >=2.4.5 &lt;2.4.7 の場合） – 複数選択属性のストアレベルで「デフォルトを使用」チェックボックスの値が正しく保存されない問題を修正しました。
* **ACSD-49898** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.6） – バンドルされた商品の特別価格が 1000 を超えると、商品グリッドが例外をスローする問題を修正しました。
* **ACSD-50234** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.4.5 の場合） – [!DNL PayPal] で注文する場合に、確認メールに間違ったお客様の名前が表示される問題を修正しました。
* **ACSD-49960** （Adobe CommerceおよびMagento Open Source >=2.4.5 &lt;2.4.7） – 顧客注文グリッドで日付によるフィルタリングが機能しない問題を修正しました。
* **ACSD-49849** (Adobe Systemsコマースおよび Magento Open Source >=2.3.7 &lt;2.4.6) - Fixes the issue where customer email was replaced with [!DNL PayPal] GraphQL 経由で [!DNL PayPal Express] を使用して注文する場合の電子メール。
* **ACSD-49839** (Adobe Systemsコマース >=2.3.7 の場合 &lt;2.4.7) - Fixes the issue where Shared Catalog Pricing and structure throws an error in Admin when products have single or double quotes in SKU.
* **ACSD-49970** (Adobe Systemsコマースおよび Magento Open Source >=2.4.5 &lt;2.4.7) - Fixes incorrect handling of GraphQL errors when [!DNL New Relic] レポートがオンになっている場合。
* **ACSD-50260** (Adobe Systemsコマースおよび Magento Open Source >=2.4.5 &lt;2.4.7) - Fixes the issue where GraphQL product search results are limited to 10,000 results only.
* **ACSD-48813** (Adobe Systemsコマースおよび Magento Open Source >=2.4.3 の場合 &lt;2.4.7) - Fixes the issue where the search is not showing relevant results based on the search weight of the attributes.

## v1.1.28 {#v1-1-28}

* **ACSD-48204** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.4.3 の場合） – Yes/No 属性に基づいて作成されたカタログ価格ルールが選択した範囲を考慮しない問題を修正しました。
* **ACSD-47704** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.4.7） – バンドル商品に在庫商品のみの価格が表示される問題を修正しました。
* **ACSD-49370** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.4.7 の場合） - GraphQL スキーマで *日時* 製品属性に *FilterMatchTypeInput* タイプが含まれる問題を修正しました。
* **ACSD-48807** (Adobe Systemsコマースおよび Magento Open Source >=2.4.1 &lt;2.4.7) - Fixes the issue where customer Product Reviews are not filtered by storeview via GraphQL.
* **ACSD-49433** (Adobe Systemsコマースおよび Magento Open Source >=2.4.3 &lt;2.4.7) - Fixes the issue where the default amount is shown as subtotal in the cart for gift card with an open amount.
* **ACSD-48866** (Adobe Systemsコマースおよび Magento Open Source >=2.3.7 &lt;2.4.7) - Fixes the issue where an error occurs when requesting RSS feed for categories.
* **ACSD-48784** (Adobe Systemsコマースおよび Magento Open Source >=2.3.7 の場合 &lt;2.4.7) - Fixes the issue where the customer segment prices are incorrectly cached between customer groups.
* **ACSD-48857** (Adobe Systemsコマースおよび Magento Open Source >=2.4.3 の場合 &lt;2.4.7) - Fixes the issue where a user is unable to save changes after editing with Page Builder.
* **ACSD-49065** (Adobe Systemsコマースおよび Magento Open Source >=2.3.7 &lt;2.4.7) - Fixes the issue where quote items are not visible in the Admin if only assigned to the custom stock.
* **ACSD-49179** (Adobe Systemsコマースおよび Magento Open Source >=2.4.2 &lt;2.4.7) - Fixes the issue where the Orders Report shows incorrect amounts in case of different currencies for different stores.
* **ACSD-49286** (Adobe Systemsコマースおよび Magento Open Source >=2.4.3 &lt;2.4.7) - Fixes the issue where a product is added twice to a cart when multiple product widgets are present on the page.
* **ACSD-49574** (Adobe Systems コマース >=2.4.4 の場合 &lt;2.4.7) - Adds functionality to support Gift Card product updates in a cart via GraphQL.
* アップデートされたパッチ:ACSD-48694。

## v1.1.27 {#v1-1-27}

* **ACSD-48362** (Adobe Systems コマース >=2.4.1 の場合 &lt;2.4.7) - Fixes the issue where the default shipping address is used instead of a new one when placing an order using a negotiable quote.
* **ACSD-48059** （Adobe Commerce >=2.3.7 &lt;2.4.7 の場合） – マーチャントがカテゴリの「[!UICONTROL Match product by rule]」を保存できない問題を修正しました。
* **ACSD-48216** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.3.8） || >=2.4.0 &lt;2.4.7） - [!UICONTROL UPDATE] 操作で [!UICONTROL inventory_source_item] テーブルの [!UICONTROL AUTO_INCREMENT] が増加する問題を修正しました。
* **ACSD-47908** (Adobe Systems コマースおよび Magento Open Source >=2.3.7 &lt;2.3.8 ||=&quot;&quot;>=2.4.0 &lt;2.4.7) - Fixes the error &quot;A value less than or equal to 0 is expected&quot; when selecting the source and qty on the shipping step during checkout.&lt;/2.3.8>
* **ACSD-49497** (Adobe Systemsコマースおよび Magento Open Source >=2.3.7 &lt;2.4.6) - Fixes the issue where an order remains in the processing state after shipment and a partial refund is applied.
* **ACSD-48694** (Adobe Systems コマースおよび Magento Open Source >= &lt;2.3.8 ||=&quot;&quot;>2.3.7 =2.4.1 &lt;2.4.7) - Fixes the issue where the error &quot;Invalid state change requested&quot; prevents a customer from placing an order.&lt;/2.3.8>
* **ACSD-49013** （Adobe CommerceおよびMagento Open Source >=2.4.3 &lt;2.4.7） – Bulk API を使用して顧客を作成する際に、メールの確認が Web サイトのロケールに翻訳されない問題を修正しました。
* **ACSD-48164** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.4.7 の場合） – 制限付き管理者が web サイトレベルの値を保存できない問題を修正しました。
* **ACSD-48404** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.4 の場合） – ブラウザーの「戻る」ボタンを押すと、「カテゴリのページネーションを記憶する」がエラーを引き起こす問題を修正しました。
* **ACSD-48634** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.4.7 の場合） – 「[!UICONTROL Google Analytics Content Experiments]」が有効になっている場合に、ステージング更新ページで発生する JS エラーを修正しました。
* **ACSD-49042** (Adobe Systemsコマースおよび Magento Open Source >=2.4.4 &lt;2.4.5) - Fixes the issue where a product with infinite backorder cannot be ordered from the Storefront.
* 更新されたパッチ:ACSD-48366、ACSD-48661。

## v1.1.26 {#v1-1-26}

* **ACSD-47937** (Adobe SystemsコマースおよびMagento Open Source用 2.4.4 || >=2.4.5 &lt;2.4.6) - Fixes the issue where price drop notifications are not always sent due to application-level caching.
* **ACSD-48661** (Adobe Systems コマースおよび Magento Open Source >=2.3.7 &lt;2.4.7) - Fixes the issue where if the company&#39;s credit limit is larger than 999, the comma separator prevents the saving of the company due to a validation error.
* **ACSD-48773** (for Adobe Commerce and Magento Open Source >=2.4.2 &lt;2.4.7) - Fixes the issue where the reward points email template is taken from the wrong store.
* **ACSD-48587** (for Adobe Commerce and Magento Open Source >=2.3.7 &lt;2.4.7) - Fixes the issue where HTML special characters in the products widget matching rules prevent them from displaying matching products.
* **ACSD-48212** (for Adobe Commerce and Magento Open Source >=2.3.7 &lt;2.4.6) - Fixes the issue where product import assigns the product to the wrong source.
* **ACSD-47988** (for Adobe Commerce and Magento Open Source >=2.3.7 &lt;2.4.6) - Fixes the issue where product export trims HTML tags from the page builder product description.
* **ACSD-48366** (Adobe Systemsコマースおよび Magento Open Source >=2.4.4 &lt;2.4.6) - Fixes the issue where the product image is not displayed on the Back to Stock email template.
* **ACSD-48417** （Adobe CommerceおよびMagento Open Source >=2.4.5 &lt;2.4.7） – 商品のスケジュールを変更して別の商品を保存した後に SQL エラーが表示される問題を修正しました。

## v1.1.25 {#v1-1-25}

* **ACSD-48058** （Adobe CommerceおよびMagento Open Source >=2.4.5 &lt;2.4.6 の場合） – バンドル製品がいずれの web サイトにも割り当てられていない場合に、製品の価格インデックスが機能しない問題を修正しました。
* **ACSD-48262** （Adobe CommerceおよびMagento Open Source >=2.4.5 &lt;2.4.6 の場合） – 「1 ページあたりの全製品を許可」設定が「はい」に設定されている場合に、フロントエンドに製品が表示されない問題を修正しました。
* **ACSD-48293** （Adobe CommerceおよびMagento Open Source >=2.4.3 &lt;2.4.4 の場合） – 売り切れた子商品が在庫に戻されると複合商品が在庫切れになる問題を修正しました。
* **ACSD-47520** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.6 の場合） – クレジットメモを作成したときに顧客が報酬ポイントを失う問題を修正しました。
* **ACSD-48044** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.4 の場合） – 複数送料の 1 回の注文に複数のギフトカードを適用すると、注文できなくなる問題を修正しました。
* **ACSD-48300** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.6 の場合） – 設定可能な商品が削除された場合に戻り値を作成できない問題を修正しました。
* **ACSD-47910** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.6） – それぞれのエンティティグリッドで、注文、請求書、出荷、およびクレジットメモが見つからない問題を修正します。
* **ACSD-47292** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.6） – 「在庫切れの商品を表示」が「はい」に設定されている場合に、GraphQL レスポンスで在庫切れのバンドル商品が利用できない問題を修正しました。
* **ACSD-48234** （Adobe CommerceおよびMagento Open Source >=2.4.5 &lt;2.4.6 の場合） – 「在庫切れを表示」オプションが有効になっている場合に、カタログ検索結果に誤ったカテゴリ項目数が表示される問題を修正しました。
* **ACSD-48313** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.5 の場合） – 属性値にコンマが含まれている場合に、「configurable_variations」列が解析されない問題を修正しました。 「additional_attributes」にも同じ解析アルゴリズムを使用します。
* **ACSD-48627** (for Adobe Commerce and Magento Open Source >=2.4.5 &lt;2.4.6) - Fixes the issue where the out-of-stock configurable product causes an error when sending a GraphQL request to get cart details.
* Updated patch: MDVA-39384.

## v1.1.24 {#v1-1-24}

* **ACSD-45168** （Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.6） – ストアビューレベルで上書きされた *url_key* 属性を持つ製品で、SEO に対応する URL が生成されない問題を修正しました。
* **ACSD-46865** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.6 の場合） – 非同期インデックス作成が有効な場合に、出荷およびクレジットメモグリッドが入力されない問題を修正しました。
* **ACSD-47004** （Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.6） – VAT ID のない請求先住所に VAT が適用されない問題を修正しました。
* **ACSD-47803** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.6 の場合） – 在庫切れの設定可能な商品スウォッチが利用可能と表示される問題を修正しました。
* **ACSD-47137** (for Adobe Commerce and Magento Open Source >=2.4.4 &lt;2.4.6) - Improves the loading speed of the image gallery when the pub/media folder is very big.
* **ACSD-46770** (for Adobe Commerce and Magento Open Source >=2.4.0 &lt;2.4.6) - Fixes the issue where admin order emails are sent even when the *Email order confirmation* is unchecked.
* **ACSD-47955** (for Adobe Commerce and Magento Open Source >=2.4.4 &lt;2.4.6) - Fixes the issue where GraphQL does not display the cart discount correctly.
* **ACSD-46617** (for Adobe Commerce and Magento Open Source >=2.4.0 &lt;2.4.6) - Fixes the issue where the *Continue to Checkout* button is greyed out even if the subtotal is greater than the configured *Minimum Order Amount*.
* **ACSD-47079** (for Adobe Commerce and Magento Open Source >=2.4.4 &lt;2.4.5) - Fixes the issue where composite products (bundle, grouped, and configurable) stock status are not updated when sub-product stock status changes via REST API POST /rest/V1/inventory/source-items.
* **ACSD-47336** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.6） – 修正点 *問題が発生しました。Commerce Admin で通知を無効にすると* エラーが発生する。
* **ACSD-47559** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.6 の場合） – メールテンプレートのプレビュー領域が完全には表示されない問題を修正しました。
* **ACSD-47920** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.6 の場合） - *Allow Guest Checkout* がオフになっている場合でも、Rest API を介してゲストユーザーとして注文できる問題を修正しました。
* 交換したパッチ：MDVA-39305、MDVA-42855。

## v1.1.23 {#v1-1-23}

* **ACSD-47179** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.6 の場合） – 特定の範囲へのアクセスが制限された管理者が商品レビューを削除できない問題を修正しました。
* **ACSD-47107** （Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.5 の場合） – カスタム商品オプションにカタログ価格ルール割引が適用される問題を修正しました。
* **ACSD-47232** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.6） – 合計重量条件のクーポンが管理者で適用できない問題を修正しました。
* **ACSD-46519** （Adobe CommerceおよびMagento Open Source >=2.4.1 &lt;2.4.6） – GraphQL categoryList リクエストがアンカカテゴリに対して誤った product_count を返す問題を修正しました。
* **ACSD-47027** （Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.6） – 低速の updateCompanyRole GraphQL リクエストを修正します。
* **ACSD-47666** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.6 の場合） – 管理者/ システム /権限/ ユーザーロール / ロール / ロールユーザーグリッドでフィルター機能が機能しない問題を修正しました。
* **ACSD-47497** (for Adobe Commerce and Magento Open Source >=2.4.0 &lt;2.4.6) - Fixes the issue where the Services tab is not visible in the Configuration under the Admin.
* Updated patch: ACSD-47743.
* 交換したパッチ：MDVA-42807。

## v1.1.22 {#v1-1-22}

* **ACSD-47444** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.3 の場合） – PHP 7.4 で既知の商品の特定の非既存のカテゴリパスにアクセスする場合、_bool 型の値の配列オフセットへのアクセスを試みています_ エラーを修正しました。
* **ACSD-47332** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.6 の場合） - UTC で 00:00～00:59 の間に実行しているときにのみ報告されるエラーで cron が失敗する問題を修正しました。
* **ACSD-47280** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.6 の場合） – 特定の範囲で共有カタログ機能を無効にすると正しく機能しない問題を修正しました。
* **ACSD-47106** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.6 の場合） – 会社作成ページの新しいカスタム属性に値を保存できない問題を修正しました。
* パッチを更新しました：ACSD-45143。

## v1.1.21 {#v1-1-21}

* **ACSD-46809** （Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.6 の場合） – 多数の商品ソースを割り当てたときにエラーが発生する問題を修正しました。
* **ACSD-46856** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.6） – システム /設定/インポート/詳細価格を使用して、パフォーマンスアップデート層の価格を改善します。
* **ACSD-46541** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.4 の場合） – 注文項目を削除すると、管理者ユーザーがクレジットメモを作成できない問題を修正しました。
* **ACSD-46581** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.6） – ショッピングカートで国を選択した後、推定税合計が更新されない問題を修正しました。
* **ACSD-46618** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.6 の場合） – ログインしたユーザーの商品リストウィジェットに誤ったキャッシュ価格が表示される問題を修正しました。
* **ACSD-46674** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.6 の場合） – 画像タイプのカスタムオプションが顧客のメールでHTMLとして表示される問題を修正しました。
* **ACSD-46988** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.6） - GraphQLの「通貨」 API リクエストがカスタム通貨に対して NULL 値を返す問題を修正しました。
* **ACSD-47076** （Adobe CommerceおよびMagento Open Source >=2.4.1 &lt;2.4.5） – ストアフロントで Vimeo の動画を再生できない問題を修正しました。
* **ACSD-45071** （Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.4 の場合） – インポート時にデフォルトソースが製品に追加される問題を修正しました。
* **AC-3023** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.6） – DHL スキームを最新バージョン 10.0 に更新します。
* パッチを更新しました：MDVA-42584。
* 交換したパッチ：MDVA-36572、ACSD-45241。

## v1.1.20 {#v1-1-20}

* **ACSD-46520** （*Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.5* の場合） – ストアクレジットを使用して払い戻すと、ユーザーが誤った注文ステータスを取得する問題を修正しました。
* **ACSD-46703** （*Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.6* の場合） – カスタムオプションを商品の編集ページにドラッグ&amp;ドロップできない問題を修正しました。
* **ACSD-44851** （*Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.6* の場合） – サブカテゴリを持つカテゴリを開いたり展開したりできない問題を修正しました。
* **ACSD-46815** （*Adobe CommerceおよびMagento Open Source >=2.4.5 &lt;2.4.6* の場合） – カテゴリツリーリクエストが 20 個に制限されている問題を修正しました。
* **ACSD-45675** （*Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.6* の場合） – 製品の書き出しで *デフォルトストア表示* 範囲のカテゴリ名が使用される問題を修正しました。
* **ACSD-46869** （*Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.6* の場合） – 製品数量を変更しないと、買い物かご内の設定可能な製品が *PUT REST API* リクエストを介して更新されない問題を修正しました。
* **MDVA-42768-V2** （*Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.3* の場合） - *在庫切れを表示* が *はい* の場合に、設定可能な製品に通常の価格が *0* と表示される問題を修正しました。
* 更新されたパッチ：MDVA-44562、ACSD-46213、MDVA-41305、MDVA-38346、MDVA-13203。
* 非推奨パッチ：MDVA-42768。

## v1.1.19 {#v1-1-19}

* **ACSD-46213** （*Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.3* の場合） – カテゴリツリーリクエストが 20 個に制限されている問題を修正しました。
* **ACSD-45781** （*Adobe CommerceおよびMagento Open Source >=2.4.1 &lt;2.4.2* の場合） – モバイルでストアフロント検索フィールドが表示されない問題を修正しました。
* **ACSD-46192** （*Adobe CommerceおよびMagento Open Source >=2.3.6 &lt;2.4.5* の場合） - `async/bulk/V1/configurable-products/bySku/options` エンドポイントを使用した問題を修正しました。
* **ACSD-46404** （*Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.5* の場合） - 2.4.4 にアップグレードした後に管理者ユーザーがログインできない問題を修正しました。
* 更新されたパッチ：MDVA-41305、MDVA-38626、MDVA-38728、MDVA-41061-V4、MDVA-42269、MDVA-39305。

## v1.1.18 {#v1-1-18}

* **ACSD-45817** （*Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.4*） – 特定のストアのGraphQL製品ミューテーションが、リクエストされたストアに割り当てられていないものを含め、設定可能なすべてのバリアントを返す問題を修正しました。
* **ACSD-46146** （*Adobe CommerceおよびMagento Open Source >=2.3.0 &lt;2.4.6* の場合） – 管理者から注文した後に 2 通の注文確認メールが送信される問題を修正しました。
* **ACSD-45255** （*Adobe Commerce >=2.4.3 &lt;2.4.6* の場合） – 制限付き管理者ユーザーの低在庫レポートページの例外を修正します。
* **ACSD-45488** （*Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.6* の場合） – 複数のソースを持つ設定可能な商品が在庫に自動的に返されない問題を修正しました。
* **ACSD-45754** （*Adobe CommerceおよびMagento Open Source >=2.3.1 &lt;2.4.6* の場合） – クーポンを買い物かごに適用した後に報酬ポイントが追加されない問題を修正しました。
* **ACSD-45849** (*Adobe Systemsコマース用>=2.4.3 &lt;2.4.4*)- ステージングアップデートの適用後にビデオメタデータが失われる問題を修正します。
* **ACSD-45257** (*Adobe Systemsコマースおよび Magento Open Source >=2.3.4 &lt;2.4.4*) - GraphQL が買い物かご割引を正しく表示しない問題を修正します。
* **ACSD-44938** (*Adobe Systemsコマースおよび Magento Open Source >=2.4.0 &lt;2.4.4*) - ゲストユーザーの GraphQL リクエストで `VAT_ID` を適用できない問題を修正します。
* 更新されたパッチ:MDVA-43417。

## v1.1.17 {#v1-1-17}

* **ACSD-45241** （*Adobe CommerceおよびMagento Open Source >=2.3.5 &lt;2.4.4* の場合） – クレジットメモを作成した後に、バーチャル商品の在庫数が誤って計算される問題を修正しました。
* **ACSD-43887** （*Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.5* の場合） – 会社の発注書が有効になっている場合に、チェックアウト時の支払いページに間違った詳細が表示される問題を修正しました。
* **ACSD-45143** （*Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.5* の場合） – `setShippingAddressesOnCart` ミューテーションで数値地域コードを *region* に設定できない問題を修正しました。
* **ACSD-44591** （*Adobe CommerceおよびMagento Open Source >=2.4.3 &lt;2.4.6* の場合） – CAPTCHA の確認が行われないまま注文した場合に発生するエラーを修正します。
* **ACSD-45520** （*Adobe CommerceおよびMagento Open Source >=2.3.0 &lt;2.4.6* の場合） – 買い物かごから設定可能な商品を編集したときに、商品の詳細ページでスウォッチオプションが事前に選択されていない問題を修正しました。
* **ACSD-45169** (*Adobe Systemsコマースおよび Magento Open Source >=2.4.1 &lt;2.4.6*) - ステージング更新が適用された後、コンフィギュレーション可能な製品の正しい在庫と価格が [!DNL Visual Merchandiser] 表示されない問題を修正します。
* **ACSD-45424** (*Adobe Systemsコマースおよび Magento Open Source >=2.3.4 &lt;2.4.6*) - 一部返金 (クレジットメモ) 後に誤った予約補償が作成される問題を修正します。
* **MDVA-42807** (*Adobe Systemsコマースおよび Magento Open Source >=2.3.1 &lt;2.4.6*) - カスタム通貨記号がストア前面に表示されない問題を修正します。
* 更新されたパッチ:MDVA-42689、AC-3022。

## v1.1.16 {#v1-1-16}

* **MDVA-44703** (*Adobe Systemsコマースおよび Magento Open Source >=2.4.3 &lt;2.4.4*) - 制限付き管理ユーザーの注文件数レポートの注文合計が誤って計算される問題を修正します。
* **MDVA-44940** (*Adobe Systemsコマースおよび Magento Open Source >=2.4.3 &lt;2.4.4*) - 管理者からのカテゴリの保存中に発生する SQL エラーを修正します。
* **MDVA-44562** (*Adobe Systemsコマースおよび Magento Open Source >=2.4.0 &lt;2.4.2-p2*&#x200B;の場合) - GraphQL リクエストがデフォルト以外のストア 表示から発信されているにもかかわらず、見積もり品目のデフォルト以外のストア ID がデフォルトのストア ID によって上書きされる問題を修正します。
* **MDVA-43167** (*Adobe Systemsコマースおよび Magento Open Source >=2.4.2 &lt;2.4.4*&#x200B;用) - 管理者ユーザーがすべての注文を選択したときに、管理注文グリッドの一括アクションが複数ページに適用されない問題を修正します。
* **MDVA-44044** (*Adobe Systemsコマースおよび Magento Open Source >=2.3.0 &lt;2.4.2-p2*&#x200B;向け) - 製品が新しい Web サイトに割り当てられた後にカテゴリ ページに表示されない問題を修正します。
* **MDVA-42509** (*for Adobe Commerce and Magento Open Source >=2.3.3 &lt;2.4.4*) - Fixes the issue where a CSV could not be uploaded for a quick order resulting in an *Unable to send the cookie* error.
* Updated patches: MDVA-41061, MDVA-42584.
* The prefix for the new [!DNL Quality Patches Tool] patches will be changed from *MDVA* to *ACSD* due to internal process changes.

## v1.1.15 {#v1-1-15}

* **MDVA-40961** (*for Adobe Commerce and Magento Open Source >=2.4.3 &lt;2.4.4*) - Fixes the issue where an additional item can&#39;t be added to the cart when the minimum qty of the item is already in the cart.
* **MDVA-44887** (*for Adobe Commerce and Magento Open Source >=2.4.4 &lt;2.4.5*) - Fixes the *Uncaught SyntaxError: Unexpected token &#39;const&#39;* error in the Admin panel.
* **MDVA-43718** (*for Adobe Commerce and Magento Open Source >=2.3.0 &lt;2.4.5*) - Fixes *The consumer isn&#39;t authorized to access %resources.* error that appears when accessing a shared catalog from a custom integration.
* **MDVA-44660** (*for Adobe Commerce and Magento Open Source >=2.4.2-p1 &lt;2.4.5*) - Fixes the issue where the grave accent character ``` ` ``` could not be used for a customer&#39;s first and last name.
* **MDVA-40896** (*for Adobe Commerce and Magento Open Source >=2.4.3 &lt;2.4.4*) - Fixes the *Error: TypeError: Argument 3 passed to Magento* error in async product bulk API.
* **MDVA-38559** (*Adobe Systemsコマースおよび Magento Open Source >=2.4.0 &lt;2.4.3*&#x200B;の場合) - 複数の購読を持つ顧客の */V1/customers/検索 API* エラーを修正します。
* **MDVA-44533** (*Adobe Systemsコマースおよび Magento Open Source >=2.3.1 &lt;2.4.4*) - 割引がバンドルの子製品に誤って適用される問題を修正します。
* 更新されたパッチ:MDVA-41061、MDVA-42269。

## v1.1.14 {#v1-1-14}

* **MDVA-43983** (*Adobe Systemsコマースおよび Magento Open Source >=2.4.2 &lt;2.4.5*) - 製品 *個別に可視されていない* がカタログ詳細 Searchの結果に引き続き表示される問題を修正します。
* **MDVA-44100** (*for Adobe Commerce and Magento Open Source >=2.4.3 &lt;2.4.5*) - Fixes the issue where all FPTs are assigned to the last product in the shopping cart and reset for other products.
* **MDVA-43605** (*for Adobe Commerce and Magento Open Source >=2.3.1 &lt;2.4.5*) - Fixes the issue where order data returns negative values for row totals when using Rest API.
* **MDVA-43102** (*for Adobe Commerce and Magento Open Source >=2.3.1 &lt;2.4.5*) - Fixes the issue where the salable quantity is not updated correctly when a refund is done via REST API.
* **MDVA-43178** (*for Adobe Commerce and Magento Open Source >=2.4.3-p2 &lt;2.4.5*) - Fixes the issue where a customer token for a custom store cannot be retrieved in GraphQL.
* **MDVA-43859** (*Adobe Systems Commerce および Magento Open Source >=2.4.1 &lt;2.4.5*) - 削除された顧客がログインしようとすると、エラー *customerId =* のエンティティは記録されません。
* **MDVA-44147** （*Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.5*） – GraphQL リクエストが購買依頼リストを返さない問題を修正しました。
* **MDVA-44505** （*Adobe CommerceおよびMagento Open Source >=2.4.1 &lt;2.4.3* の場合） - GraphQLの報酬ポイントの適用で総計が更新されない問題と、注文処理中に店舗クレジットが複数回適用される問題を修正しました。
* 更新されたパッチ：MDVA-29148、MDVA-36464-V5、MDVA-42584、MDVA-39993-V2。

## v1.1.13 {#v1-1-13}

* **MDVA-42969** （*Adobe CommerceおよびMagento Open Source >=2.4.1 &lt;2.4.3* の場合） – 「顧客セグメント」が「*すべて*」に設定されている場合にのみ、関連製品ルールが機能する問題を修正しました。
* **MDVA-39605** （*Adobe CommerceおよびMagento Open Source >=2.3.4 &lt;2.4.5*） – Redis キャッシュ TTL （有効期限）の値が間違っている問題を修正しました。
* **MDVA-43862** （*Adobe CommerceおよびMagento Open Source >=2.3.3 &lt;2.4.5* の場合） - GraphQL *UpdateCartItems mutation* エラーが原因で顧客が買い物かごの商品を更新できない問題を修正しました。
* **MDVA-43824** （*Adobe CommerceおよびMagento Open Source >=2.3.6 &lt;=2.3.7-p3 || >=2.4.1 &lt;2.4.5*） – 割引が適用された注文のキャンセル時にエラーが表示される問題を修正しました。
* **MDVA-43451** （*Adobe CommerceおよびMagento Open Source >=2.4.3 &lt;2.4.5* の場合） – エラー *リクエストされたストアが見つからなかった問題を修正しました。 ストアを確認して、もう一度試してください。特定の web サイトの共有カタログを設定している間に* が表示されます。
* **MDVA-43491** （*Adobe CommerceおよびMagento Open Source >=2.3.5 &lt;2.4.5* の場合） – マルチストア web サイトの商品を読み込む際にベース画像のラベルが更新されない問題を修正しました。
* **MDVA-43601** （*Adobe CommerceおよびMagento Open Source >=2.3.0 &lt;2.4.5* の場合） – フル再インデックス後にトリガーが見つからない問題を修正しました。
* **MDVA-42046** （*Adobe CommerceおよびMagento Open Source >=2.3.4 &lt;=2.3.5-p2 || >=2.4.0 &lt;2.4.5*） – 製品の更新中に、日付入力フィールドを持つ製品属性に間違った値が割り当てられる問題を修正しました。
* **MDVA-43935** （*Adobe CommerceおよびMagento Open Source >=2.4.1 &lt;2.4.5*） – アップセル製品が 2 回表示される問題を修正しました。
* **MDVA-44188** (*for Adobe Commerce and Magento Open Source >=2.4.3 &lt;2.4.5*) - Fixes the issue where system-issued emails with `.-` in addresses are not sent.
* **MDVA-42283** （*Adobe CommerceおよびMagento Open Source >=2.3.0 &lt;2.4.5* の場合） – フランス語ロケールの管理注文グリッドの日時フォーマットが無効な問題を修正しました。
* 更新されたパッチ：MDVA-41061-V2、MDVA-36309、MDVA-30862、MDVA-39713。
* [!DNL Site-Wide Analysis Tool] のパッチメタデータを追加しました。

## v1.1.12 {#v1-1-12}

* **MDVA-39713** （*Adobe CommerceおよびMagento Open Source >=2.3.0 &lt;2.3.6* の場合） – スケジュールされたアクティブな更新の開始時刻が編集可能な問題を修正しました。
* **MDVA-42410** (*Adobe Systemsコマースおよび Magento Open Source >=2.3.0 &lt;2.4.5*&#x200B;向け) - クーポンレポートにデフォルトの基本通貨のみが表示される問題を修正します。
* **MDVA-41136** （*Adobe CommerceおよびMagento Open Source >=2.3.0 &lt;2.4.5* の場合） - `mage-cache-sessid` ータの有効期限が延長されず、カスタマーデータクリーンアップが発生する問題を修正しました。
* **MDVA-39993** （*Adobe CommerceおよびMagento Open Source >=2.3.5 &lt;=2.3.7-p2 || >=2.4.0 &lt;2.4.4*） - API を使用して行ったインベントリの変更が、フロントエンドの製品ページに反映されない問題を修正しました。
* **MDVA-42855** （*Adobe CommerceおよびMagento Open Source >=2.4.3 &lt;2.4.5* の場合） – チェックアウト時に新しいお客様の住所がアドレス帳に保存されない問題を修正しました。
* **MDVA-42645** （*Adobe CommerceおよびMagento Open Source >=2.4.3 &lt;2.4.5*） – ストアクレジット機能が無効になっている場合に、管理者が報酬ポイントを返金できない問題を修正しました。
* **MDVA-43414** （*Adobe CommerceおよびMagento Open Source >=2.3.6 &lt;=2.3.7-p2* の場合） – `inventory.reservations.updateSalabilityStatus` キューコンシューマーを数値 SKU で実行している際に発生する PHP の致命的エラーを修正します。
* **MDVA-41628** (*Adobe Systemsコマースおよび Magento Open Source >=2.4.0 &lt;2.4.5*&#x200B;用) - 新しいモジュールが追加されたときに、既存の制限付き管理者ユーザーが新しいリソースにアクセスできる問題を修正します。
* **MDVA-43348**(*Adobe Systemsコマースおよび Magento Open Source >=2.4.2 &lt;2.4.5*) - ギフトカード GraphQL リクエスト に *uid* が含まれているとエラーが表示される問題を修正`gift_card_options`。
* **MDVA-39546** (*Adobe Systemsコマースおよび Magento Open Source >=2.3.0 &lt;2.4.5*) - ステージング更新の開始日付が編集中に現在の日付よりも前の日付に設定される可能性がある問題を修正します。
* **MDVA-42950** (*Adobe Systemsコマースおよび Magento Open Source >=2.3.0 &lt;2.4.5*) - 製品ページでビデオが再生されない問題を修正します。
* **MDVA-42689** (*Adobe Systemsコマースおよび Magento Open Source >=2.3.0 &lt;2.4.4*) - インポート中に商品カテゴリを更新する際に Adobe Systems Commerce が *整合性コンストレイント違反* エラーをスローする問題を修正します。
* **MDVA-41229** (*Adobe Systemsコマースおよび Magento Open Source >=2.3.0 &lt;2.4.5*&#x200B;用) - 構成可能な製品のインポート後に、バックエンドで使用可能なイメージがフロントエンドに表示されない問題を修正します。
* **MDVA-43731** （*Adobe CommerceおよびMagento Open Source >=2.4.3 &lt;2.4.4* の場合） – *一致する最小用語* に値が追加されると、*検索シノニム* が機能しなくなる問題を修正しました。
* **MDVA-43232** （*Adobe CommerceおよびMagento Open Source >=2.3.4 &lt;2.4.5*） – [!DNL Visual Merchandiser] の商品を特別価格で下/上に並べ替えると、カテゴリの保存中にエラーが発生する問題を修正しました。
* **MDVA-43726** （*Adobe CommerceおよびMagento Open Source >=2.3.3 &lt;2.4.3* の場合） – ストアレベル属性の一致に基づくカタログ価格ルールが部分的な再インデックス後に適用されない問題を修正しました。
* アップデートされたパッチ:MDVA-36464、MDVA-37478、MDVA-38608。
* [!DNL Site-Wide Analysis Tool]用にメタデータパッチが追加されました。

## v1.1.11 {#v1-1-11}

* **MDVA-42790** （*Adobe CommerceおよびMagento Open Source >=2.4.3 &lt;2.4.5*） – REST API を使用して特定の web サイトの製品価格属性を更新できない問題を修正しました。
* **MDVA-41350** （*Adobe CommerceおよびMagento Open Source >=2.3.0 &lt;2.4.5* の場合） – アクセスが制限されている管理者ユーザーが、SKU によって役割範囲外の商品を注文で追加すると例外がスローされる問題を修正しました。
* **MDVA-42269** （*Adobe CommerceおよびMagento Open Source >=2.4.3-p1 &lt;2.4.5* の場合） – *TypeError:strtotime （）は、パラメーター 1 が文字列である（null が指定されている）ことを予期しているため、管理者ユーザーが管理者にログインできない問題を修正し* す。
* **MDVA-40830** （*Adobe CommerceおよびMagento Open Source >=2.3.0 &lt;2.4.5* の場合） – 注文処理中にストアクレジットが複数回適用される問題を修正しました。
* **MDVA-42237** （*Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.5*） – サブプロダクト価格が変更された後、設定可能なプロダクトスペシャル価格が更新されない問題を修正しました。
* **MDVA-42520** (*Adobe Systemsコマースおよび Magento Open Source >=2.4.3 &lt;2.4.4*) - *クロス境界線トレードを有効にする* が使用されている場合に税率が 2 回適用される問題を修正します。
* 更新されたパッチ：MDVA-27239、MDVA-39305、MDVA-41236、MDVA-36832。
* 非推奨パッチ：MDVA-37725。

## v1.1.10 {#v1-1-10}

* **MDVA-38728** （*Adobe CommerceおよびMagento Open Source >=2.3.2 &lt;2.4.5* の場合） – 一括属性の更新によって *製品の表示* を変更した後にのみデフォルトストアの URL 書き換えが作成される問題を修正しました。
* **MDVA-43091** （*Adobe CommerceおよびMagento Open Source >=2.4.3 &lt;2.4.4*） – バックエンドで管理者からバンドル商品を注文するとエラーが発生する問題を修正しました *この商品に 10 進数の数量を使用できません*。
* **MDVA-40816** （*Adobe CommerceおよびMagento Open Source >=2.3.0 &lt;2.4.5* の場合） – 関連する商品ルールで、ルール条件で定義されていないカテゴリの商品が表示される問題を修正しました。
* **MDVA-41305** （*Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.5*） – GraphQL ミューテーションをウィッシュリストに追加した後、設定可能なプロダクトオプションを返さない問題を修正しました。
* **MDVA-39181** （*Adobe CommerceおよびMagento Open Source >=2.4.1 &lt;2.4.5* の場合） – 関連する商品ルールで、ルール条件で定義されていないカテゴリの商品が表示される問題を修正しました。
* **MDVA-42584** （*Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.3*） – インポートまたは API を使用して数量と在庫ステータスを変更した後、バックエンドの設定可能な在庫ステータスが更新されない問題を修正しました。
* **MDVA-40175** （*Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.3* の場合） – *クリックして発送方法を変更* しても、並べ替え中に管理者に発送方法を選択するラジオボタンが表示されない問題を修正しました。
* **MDVA-42768** (*Adobe Systemsコマースおよび Magento Open Source >=2.3.4 &lt;2.4.5*) - Stock *外 が はい*&#x200B;表示、コンフィギュレーション可能製品に通常価格が 0 と表示される問題を修正します。
* **MDVA-43201** (*Adobe Systemsコマースおよび Magento Open Source >=2.4.2 &lt;2.4.4*) - 特定のロケールで DOB 属性を使用すると、顧客 ログイン でエラーが発生する問題を修正します。
* 更新されたパッチ:MDVA-35092、MDVA-33970。

## v1.1.9 {#v1-1-9}

* **MDVA-38346** （*Adobe CommerceおよびMagento Open Source >=2.3.0 &lt;2.4.5* の場合） - Adobe Commerceのタイムゾーンがローカル環境のタイムゾーンと異なる場合に、日付フィルターが正しく機能しない問題を修正しました。
* **MDVA-42657** （*Adobe CommerceおよびMagento Open Source >=2.4.1 &lt;2.4.5*） – 管理者ユーザーがカスタマーセグメント条件でカテゴリを選択できない問題を修正しました。
* **MDVA-42806** （*Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.4*） – REST API を使用して既存の会社が更新されるたびに *新しい会社登録* メールが送信される問題を修正しました。
* **MDVA-37984** （*Adobe CommerceおよびMagento Open Source >=2.4.1 &lt;2.4.5*） – [!DNL Visual Merchandiser] *ルールによる商品の照合* 機能で、ステージングアップデートを使用して商品が正しくフィルタリングされない問題を修正しました。
* **MDVA-40488** （*Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.4*） – 在庫切れの子商品を含む設定可能な商品が正しい価格範囲で表示されない問題を修正しました。
* **MDVA-42507** （*Adobe CommerceおよびMagento Open Source >=2.4.3 &lt;2.4.5* の場合） – カート ルールのステージング更新を適用した後に、フルページのキャッシュがクリーンアップされる問題を修正しました。
* **MDVA-39163** （*Adobe CommerceおよびMagento Open Source >=2.3.5 &lt;2.4.5* の場合） – 新規ユーザーが登録され、買い物かごに入っている商品がゲストセッションから移動した場合に発送方法が使用できない問題を修正しました。
* **MDVA-38626** （*Adobe CommerceおよびMagento Open Source >=2.3.3 &lt;2.4.5*） – 管理者ユーザーが [!DNL PayPal Payflow Pro] 支払いを使用してバックエンドで注文できない問題を修正しました。
* **MDVA-38666** （*Adobe CommerceおよびMagento Open Source >=2.3.2 &lt;2.3.6*） – 管理者ユーザーが顧客の買い物かごで設定可能な商品オプションを変更できない問題を修正しました。
* **MDVA-38526** （*Adobe CommerceおよびMagento Open Source >=2.4.1 &lt;2.4.4*） – 管理者ユーザーが [!DNL Site-Wide Analysis tool] にアクセスできない問題を修正しました。
* パッチを更新しました：MDVA-40101。

## v1.1.8 {#v1-1-8}

* **MDVA-41215** （*Adobe CommerceおよびMagento Open Source >=2.3.0 &lt;2.4.4* の場合） – *mage-messages* cookie が既に存在するが、新しいメッセージがない場合、その設定後に 500 エラーが発生する問題を修正しました。
* **MDVA-41139** （*Adobe CommerceおよびMagento Open Source >=2.4.3 &lt;2.4.4*） – 製品のインポート後に、そのソースの 1 つに対して単純な製品の数量が 0 の場合に、設定可能な製品が在庫切れになる問題を修正しました。
* **MDVA-42326** （*Adobe CommerceおよびMagento Open Sourceの場合 >=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*） – 永続買い物かごが有効になっている場合でも、セッションタイムアウト後に顧客がチェックアウト時にエラーが発生する問題を修正しました。
* **MDVA-42341** （*Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.4*） – リクエストにストアヘッダーがある場合に `categoryList` GraphQL クエリで結果がフィルタリングされない問題を修正しました。
* **MDVA-38393** （*Adobe CommerceおよびMagento Open Source >=2.3.0 &lt;2.4.4* の場合） – シンプルな商品の名前が変更された場合に、設定可能な商品に対してカタログルールが機能しなくなる問題を修正しました。
* **MDVA-39153** （*Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.4* の場合） – 管理者での並べ替え中に割引額が正しく計算されない問題を修正しました。
* パッチを更新：MDVA-28993、MDVA-41061、MDVA-35984。

## v1.1.7 {#v1-1-7}

* **MDVA-39711** (*Adobe Systemsコマースおよび Magento Open Source >=2.3.0 &lt;2.4.3*) - Web サイトを削除した後、管理者ユーザーが顧客のグリッドにアクセスできない問題を修正します。
* **MDVA-40311** (*Adobe Systemsコマースおよび Magento Open Source >=2.4.2-p2 &lt;2.4.4*) - 管理者ユーザーに *無効なセキュリティまたはフォームキー。 カスタム管理者パスが設定され、秘密鍵が有効になっている場合は、管理者にログインした後にページ* を更新してください。
* **MDVA-41631** (*Adobe Systemsコマースおよび Magento Open Source >=2.4.1 &lt;2.4.4*) - GraphQL を介してオプションの *電話* 値なしで注文情報を取得しようとすると、ユーザーがエラーが発生する問題を修正します。
* **MDVA-27239** （*Adobe CommerceおよびMagento Open Source >=2.3.0 &lt;2.3.6* の場合） – クロスセル商品が表示されない問題を修正しました。
* 更新されたパッチ：MDVA-37068、MDVA-35254、MDVA-41164、MDVA-37916、MDVA-37478、MDVA-34551、MDVA-31791。

## v1.1.6 {#v1-1-6}

* **MDVA-40550** （*Adobe CommerceおよびMagento Open Source >=2.3.5 &lt;2.4.4* の場合） – インデックス再作成中にフロントエンドで製品が見つからない問題を修正しました。
* **MDVA-40120** （*Adobe CommerceおよびMagento Open Source >=2.4.1 &lt;2.4.4*） – GraphQLを DESC/ASC で並べ替えても、同じ関連度や価格の商品で機能しない問題を修正しました。
* **MDVA-41399** （*Adobe CommerceおよびMagento Open Source >=2.3.3 &lt;2.4.2*） – お客様がウィッシュリストに商品を追加した場合に、管理者ユーザーが *買い物かごの管理* ページにアクセスできない問題を修正しました。
* **MDVA-40609** （*Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.3* の場合） – 無効な商品データが `cataloginventory_stock_status` インデックステーブルに存在せず、無効な商品の数量が表示される問題を修正しました。
* **MDVA-39031** （*Adobe CommerceおよびMagento Open Source >=2.4.1 &lt;2.4.4*） – ターゲットの web サイトに割り当てられていなくても、GraphQLを使用して買い物かごに商品を追加できる問題を修正しました。
* **MDVA-41597** （*Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.4*） – GraphQLを使用して設定可能な複数の商品を買い物かごに追加すると、エラーが発生する問題を修正しました。
* **MDVA-27456** （*Adobe CommerceおよびMagento Open Source >=2.3.5 &lt;2.3.7* の場合） – [!DNL Swagger] を読み込もうとするとエラーが発生する問題を修正しました。
* **MDVA-32776** (*Adobe Systemsコマースおよび Magento Open Source >=2.4.0 &lt;2.4.2*) - 注文が行われたが出荷されない場合に在庫ステータスが更新されない問題を修正します。
* **MDVA-30862** （*Adobe CommerceおよびMagento Open Source >=2.3.4 &lt;2.4.0* の場合） – 印刷されたPDF請求書に記載されている間違った注文日の問題を修正します。
* [!DNL Quality Patch Tool] のインデックスページを改善しました。 ツールの最新バージョンで、[!DNL quality patches] の便利な検索とフィルタリングを追加しました。
* パッチを更新：MDVA-33382、MDVA-39482。

## v1.1.5 {#v1-1-5}

* **MDVA-41236** （*Adobe CommerceおよびMagento Open Source >=2.3.0 &lt;2.4.4* の場合） – 終了日が以前に削除されている場合に、商品の新しいスケジュール済みアップデートを作成したり、既存のスケジュール済みアップデートを編集したりできない問題を修正しました。
* **MDVA-41046** （*Adobe CommerceおよびMagento Open Source >=2.3.0 &lt;2.4.4* の場合） – カスタムオプションを使用したシンプルな商品を、設定可能な商品やグループ化された商品に割り当てることができる問題を修正しました。
* **MDVA-40545** （*Adobe CommerceおよびMagento Open Source >=2.3.0 &lt;2.4.4* の場合） – 同じページに複数のノードがある場合でも、ページの最初のノードのみが取得される問題を修正しました。
* **MDVA-41164** （*Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.3-p1* の場合） – 管理者ユーザーが、ファイルまたは画像タイプのカスタム顧客属性を持つ会社を保存または編集できない問題を修正しました。
* **MDVA-39229** （*Adobe CommerceおよびMagento Open Source >=2.3.0 &lt;2.4.4* の場合） – カタログルールのステージングの更新開始時刻を更新すると次のエラーが表示される問題を修正しました。*Cron Job staging_synchronize_entities_period にエラーがあります。アクティブな更新を削除できません。*
* **MDVA-40619** （*Adobe CommerceおよびMagento Open Source >=2.3.0 &lt;2.4.4* の場合） – CMS ページでインライン編集を試みると、CMS ページの階層を変更すると 500 エラーが発生する問題を修正しました。
* **MDVA-41061** (*Adobe Systemsコマースおよび Magento Open Source >=2.4.2 &lt;2.4.3*) - 管理から製品を保存すると、在庫ステータスが販売可能にリセットされる問題を修正します。
* **MDVA-31763** (*Adobe Systemsコマースおよび Magento Open Source >=2.3.0 &lt;2.4.4*&#x200B;用) - 手動でインデックスを再作成するまで、カタログ価格ルールが元に戻される(または適用されない)問題を修正します。
* **MDVA-37748** (*Adobe Systemsコマースおよび Magento Open Source >=2.4.2 &lt;2.4.3*&#x200B;用) - GraphQL クエリが共有カタログに割り当てられていない商品を返す問題を修正します。

## v1.1.4 {#v1-1-4}

* **MDVA-40399** (*Adobe Systemsコマースおよび Magento Open Source >=2.4.2 &lt;2.4.4*) - REST API を介して同じ注文の部分的な請求書を同時に作成できない問題を修正します。
* **MDVA-40101** (*Adobe Systemsコマースおよび Magento Open Source >=2.3.2 &lt;2.4.0*&#x200B;用) - [!DNL PayPal Express] チェックアウトを使用した注文配置が成功した後、品目がミニ買い物かごから削除されない問題を修正します。
* **MDVA-40401** (*Adobe Systemsコマースおよび Magento Open Source >= &lt;=2.3.7-p2 ||=&quot;&quot;>2.3.6 =2.4.1 &lt;2.4.4*) - 注文が失敗した場合クーポン使用値が均等変更される問題を修正します。&lt;/=2.3.7-p2>
* **MDVA-40537** (*Adobe Systemsコマースおよび Magento Open Source >=2.3.4 &lt;=2.4.0-p1*&#x200B;用) - 同じ URL キーを持つ複数の CMS ページが存在する場合、ユーザーがストア 表示を作成するときにエラーが発生する問題を修正します。
* **MDVA-37725** (*Adobe Systemsコマースおよび Magento Open Source >=2.3.0 &lt;=2.4.3-p1*) - 既定以外の Web サイトから送信される非同期注文メールに、既定の Web サイトのロゴ URL が含まれている問題を修正します。
* **MDVA-39482** (*Adobe SystemsコマースおよびMagento Open Source > = 2.3.6 &lt;=2.3.7-p2 ||=&quot;&quot;>= 2.4.1 &lt;2.4.4*&#x200B;の場合) - バックオーダーが有効になっているときに「0」量でインポートすると、製品が在庫切れになる問題を修正します。&lt;/=2.3.7-p2>
* **MDVA-40435** (*Adobe Systemsコマースおよび Magento Open Source >=2.3.4 &lt;2.4.4*) - GraphQL を介して適用された場合に動的価格のバンドル製品の誤った割引の問題を修正します。
* **MC-42528** （*Adobe CommerceおよびMagento Open Source >=2.4.3 &lt;=2.4.3-p1* の場合） - `categoryList` GraphQL クエリで、割り当て済みカテゴリと未割り当てカテゴリの両方が返される問題を修正しました。
* **MDVA-29400** （*Adobe CommerceおよびMagento Open Sourceの場合 >=2.3.0 &lt;=2.3.7-p1 || >=2.4.0 &lt;=2.4.0-p1*） - [!DNL PayPal Express Checkout] で行われた重複した注文の問題を修正しました。
* **MDVA-26005** （*Adobe CommerceおよびMagento Open Source >=2.3.4 &lt;=2.3.5-p2* の場合） – カート価格ルール条件のカテゴリツリーでカテゴリを選択できない問題を修正しました。
* **MDVA-25631** （*Adobe CommerceおよびMagento Open Source >=2.3.3 &lt;=2.3.5-p2* の場合） – 多数のユーザーを含むカスタマーセグメントの編集および保存のパフォーマンスを向上させます。

## v1.1.3 {#v1-1-3}

* **MDVA-40262** （*Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.4* の場合） – GraphQLの検索クエリが管理者の一般的な検索用語に表示されない問題を修正しました。
* **MDVA-40601** (*Adobe Systemsコマースおよび Magento Open Source >=2.3.1 &lt;=2.4.2-p2*) - スケジュールされた更新によって変更されたカテゴリに関する情報を GraphQL 経由で取得しようとすると、ユーザーがエラーが発生する問題を修正します。
* **MDVA-37234** (*Adobe Systemsコマースおよび Magento Open Source >=2.3.5 &lt;2.4.0 ||=&quot;&quot;>=2.4.1 &lt;=2.4.2-p2*) - 同じSKUの買い物かごにアイテムを複数回 (並列リクエスト) 追加すると、同じ買い物かご ID の重複 行項目が作成される問題を修正します。&lt;/2.4.0>
* **MDVA-33606** (*Adobe Systemsコマースおよび Magento Open Source >=2.4.1 &lt;=2.4.2-p2*) - 階層に割り当てられた CMS ページを保存すると、ユーザーが *一意制約違反* エラーが発生する問題を修正します。
* **MDVA-31590** (*Adobe Systemsコマースおよび Magento Open Source >=2.4.0 &lt;=2.4.1-p1*&#x200B;向け) - ユーザーが MySQL 非同期キューを使用して属性を一括更新できない問題を修正します。
* **MDVA-36309** (*Adobe Systemsコマースおよび Magento Open Source >=2.4.2 &lt;=2.4.2-p2*&#x200B;の場合) - 管理グリッドで属性別の製品検索が遅い問題を修正します。

## v1.1.2 {#v1-1-2}

* **MDVA-38929** （*Adobe CommerceおよびMagento Open Source >=2.3.0 &lt;2.4.4* の場合） – 注文がストアクレジットから支払われたときに、FPT の請求書に間違った総計が表示される問題を修正します。
* **MDVA-37364** （*Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;=2.4.3* の場合） – 日付タイプのカスタムカスタマー属性によってお客様のグリッド UI が機能しない問題を修正しました。
* **MDVA-39195** （*Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;=2.4.2-p2* の場合） – 「買い物かごにリダイレクト」が有効になっている場合に、カテゴリページで「*買い物かごに追加*」ボタンが非アクティブになる問題を修正しました。
* **MDVA-37115** （*Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;=2.4.2-p2* の場合） – 設定可能な商品ページに不要な *左側が 0 のみ* 通知が表示される問題を修正しました。
* **MDVA-39521** （*Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.4* の場合） – GraphQL経由で空の電話番号が入った配送先住所をカートにセットできない問題を修正しました。
* **MDVA-39384** （*Adobe CommerceおよびMagento Open Sourceの場合 >=2.3.1 &lt;=2.3.6 || >=2.4.1 &lt;=2.4.3*） – 会社ユーザーのカスタム顧客属性が保存されない問題を修正しました。
* **MDVA-39043** （*Adobe CommerceおよびMagento Open Source >=2.3.4 &lt;=2.4.3* の場合） – アクセス制限のある管理者ユーザーが *Products* ウィジェットをCMS ページに追加しようとするとエラーが発生する問題を修正しました。
* **MDVA-39966** （*Adobe CommerceおよびMagento Open Source >=2.3.0 &lt;=2.3.5-p2 || >=2.4.0 &lt;=2.4.0-p1*） – 間違ったロケールをデプロイする際の問題を修正しました。
* **MDVA-38852** （*Adobe CommerceおよびMagento Open Source >=2.3.0 &lt;=2.3.5-p2* の場合） – 複数の同時注文がある場合にパフォーマンスが大幅に低下する更新のために、カタログ在庫が設計によってテーブルをロックする問題を修正しました。
* **MDVA-39986** （*Adobe CommerceおよびMagento Open Sourceー >=2.4.1 &lt;2.4.3*） – Safari ブラウザーを使用してMacOSの管理者に注文できない問題を修正しました。
* **MDVA-38447** （*Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.4* の場合） – *個別に表示されない* 設定可能な子商品がGraphQL レスポンスで返される場合と、カテゴリフィルターを使用してGraphQL商品クエリの MySQL クエリを最適化する場合の 2 つの問題を修正しました。
* **MDVA-40134** （*Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.3* の場合） – Shared Catalog が有効な場合に、GraphQLが関連商品を返さない問題を修正しました。
* **MDVA-39935** （*Adobe CommerceおよびMagento Open Source >=2.4.1 &lt;2.4.4*） – GraphQLが web サイトレベルで無効になっている設定可能な子製品を返す問題を修正しました。

## v1.1.1 {#v1-1-1}

* **MDVA-36021** (*Adobe Systemsコマースおよび Magento Open Source >=2.4.0 &lt;2.4.4*&#x200B;の場合) - 管理者の注文詳細ページに *メンバー関数 getId() への呼び出し* エラーが表示される問題を修正します。
* **MDVA-34948** (*Adobe Systemsコマースおよび Magento Open Source >= &lt;=2.3.6-p1 ||=&quot;&quot;>2.3.6 =2.4.0 &lt;=2.4.0-p1*) - `GET_LOCK` などの長時間実行されるクエリの問題を修正します。&lt;/=2.3.6-p1>
* **MDVA-39305** （*Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;=2.4.2-p1* の場合） – 登録ユーザーが有効なGoogle ReCaptcha でログインできない問題を修正しました。
* **MDVA-37897** （*Adobe CommerceおよびMagento Open Source >=2.3.0 &lt;2.4.4* の場合） – 最近表示された項目からオプションを追加しようとすると、誤ったリダイレクトで問題が解決されます。

## v1.1.0 {#v1-1-0}

* ユーザーエクスペリエンスを向上させ、必要なパッチを顧客が簡単に検索できるように、パッチカテゴリが導入されました。
* `patches.json` ファイルの名前は `support-patches.json` に変更されました。
* **MDVA-38799** (*Adobe Systemsコマース用>=2.3.0 &lt;2.4.3*)- ステージング更新の作成後にダウンロード可能な製品が保存されなかった問題を修正します。
* **MDVA-37592** (*Adobe Systemsコマース用 >=2.3.6 &lt;=2.4.2-p1*) - 共有カタログに価格がゼロの商品で、価格による並べ替えが正しく機能しない場合の問題を修正します。
* **MDVA-38827** (*Adobe Systemsコマース >=2.3.3-p1 &lt;2.4.4*) - エラーメッセージを含む注文出荷メールを顧客が受け取る問題を修正します。

## v1.0.26 {#v1-0-26}

* **MDVA-38468** (*Adobe Systems コマース用 >=2.3.2 &lt;=2.3.5-p2*) - CMS ページを保存するときのエラーを修正します: *同じ ID を持つアイテムPAGE_ID既に存在します*。
* **MDVA-34680** (*Adobe Systemsコマース用 >= &lt;=2.3.7 ||=&quot;&quot;>2.3.6 =2.4.1 &lt;2.4.3*) - 顧客グリッドで顧客アカウントの作成時間が正しくフィルター処理されない問題を修正します。&lt;/=2.3.7>
* **MDVA-37068** （*Adobe Commerce >=2.3.1 &lt;2.4.4* の場合） – ショッピングカートにバーチャル商品のみが入っている場合に誤った税率が表示される問題を修正しました。
* **MDVA-38608** （*Adobe Commerce >=2.3.0 &lt;2.4.3* の場合） – 再インデックスが正常に終了しなかった場合に一時テーブルが削除されない問題を修正しました。
* **MDVA-38308** （*Adobe Commerce >=2.3.5 &lt;=2.3.6-p1 || >=2.4.0 &lt;=2.4.1-p1 || >=2.4.2 &lt;2.4.4*） – 製品への [!DNL Vimeo] ビデオの追加に関連する問題を修正しました。

## v1.0.25 {#v1-0-25}

* **MDVA-37916** (*Adobe Systemsコマース用 >=2.3.6 &lt;2.4.3*) - [!DNL Paypal Payment Advanced] メソッドの使用時に顧客が支払い確認ページに転送されない問題を修正します。
* **MDVA-37082** （*Adobe Commerce >=2.3.0 &lt;2.4.3*） – グループ化された商品のカスタム在庫を保存すると、フロントエンドに商品の在庫切れが表示される問題を修正しました。
* **MDVA-36572** （*Adobe Commerce >=2.3.5 &lt;2.4.3* の場合） – クレジットメモの更新によってデータベースで商品の重複が更新されなくなった問題を修正しました。
* **MDVA-38132** （*Adobe Commerce >=2.3.3 &lt;2.4.3* の場合） - *リダイレクトが多すぎる* エラーが原因で管理パネルに到達できない問題を修正しました。
* **MDVA-38270** （*Adobe Commerce >=2.4.1 &lt;2.4.3* の場合） - GraphQLで注文合計にギフトカード情報が見つからない問題を修正しました。

## v1.0.24 {#v1-0-24}

* **MDVA-37779** （*Adobe Commerce >=2.4.2 &lt;=2.4.4* の場合） – web サイト ID がストア ID と一致しない場合に、GraphQLを使用して設定可能な商品を買い物かごに追加する問題を修正しました。
* **MDVA-36832** （*Adobe Commerce >=2.3.4 &lt;=2.4.2-p1* の場合） – ビュー幅が 768 px の場合にページ上で画像が重複する問題を修正しました。
* **MDVA-37874** （*Adobe Commerce >=2.3.6 &lt;=2.3.7 || >=2.4.1 &lt;=2.4.2-p1*） – 複数のオプションを含むバンドル製品に *買い物かご全体の固定割引額* が誤って適用される問題を修正しました。
* **MDVA-37913** （*Adobe Commerce >=2.3.0 &lt;=2.4.0-p1* の場合） – ダウンロード可能な商品が API を介して更新されるとダウンロード可能なリンクが消える問題を修正しました。
* **MDVA-34330** （*Adobe Commerce >=2.3.1 &lt;=2.4.2-p1* の場合） – 注文グリッド内の注文が管理者のタイムゾーンに従ってフィルタリングされない問題を修正しました。

## v1.0.23 {#v1-0-23}

* **MDVA-37478** （*Adobe Commerce >=2.3.0 &lt;=2.3.7* の場合） - REST API を使用して *対顧客支払い* 支払い方法で注文した注文の部分請求書を作成する際に、Adobe Commerceがエラーをスローする問題を修正しました。
* **MDVA-37362** （*Adobe Commerce >=2.3.4 &lt;=2.4.2-p1* の場合） - GraphQL応答で設定可能な商品オプション値とバリアント属性値が空だった問題を修正しました。
* **MDVA-37288** （*Adobe Commerce 2.4.2* の場合） - GraphQL リクエスト後に誤った階層価格が返される問題を修正しました。
* **MDVA-37225** （*Adobe Commerce >=2.4.1 &lt;=2.4.2-p1* の場合） – 読み込まれた SKU に整数値がある場合に、クイックオーダーの作成中にアップロードプロセスが停止する問題を修正しました。
* **MDVA-37224** （*Adobe Commerce >=2.3.3 &lt;=2.4.2-p1* の場合） – カート内の別の商品との間で [!DNL PayFlow Pro] との交渉可能な見積もりに対して顧客が支払うことができない問題を修正しました。
* **MDVA-36286** （*Adobe Commerce >=2.3.6 &lt;=2.4.2-p1* の場合） – 同じ SKU のサブカテゴリで異なる位置が使用されている場合に、ページビルダー製品のウィジェットプレビューが機能しなくなる問題を修正しました。
* **MDVA-30186** （*Adobe Commerceの場合 >=2.3.4 &lt;=2.3.5-p2、>=2.4.0 &lt;=2.4.0-p1、>=2.4.2 &lt;=2.4.2-p1*） – GraphQL応答で属性オプションが属性項目数ではなくオプション値で並べ替えられる問題を修正しました。

## v1.0.22 {#v1-0-22}

* **MDVA-36718** （*Adobe Commerce >=2.3.0 &lt;=2.4.2* の場合） - API を使用して変更した後、古いカスタムオプションが残る問題を修正しました。
* **MDVA-35773** （*Adobe Commerce >=2.3.6 &lt;=2.3.6-p1 || >=2.4.1 &lt;=2.4.2*） - 100% 割引の注文について、請求書で総計がゼロと表示されない問題を修正します。
* **MDVA-36833** （*Adobe Commerce 2.4.2* 用） – 共通カタログから一部の商品を除外した後に、ページあたりの商品の乱数が検索結果に表示される問題を修正しました。
* **MDVA-37182** (*Adobe Systemsコマース用>=2.4.1 &lt;=2.4.2*) - バージョン 6 とバージョン 7 の両方で誤った検索結果が得られる問題を修正 [!DNL Elasticsearch] 。
* **MDVA-36253** (*Adobe Systemsコマース用>=2.4.0 &lt;=2.4.1-p1*)- アイテムの削除後にミニ買い物かごに間違った小計が表示される問題を修正します。
* **MDVA-36853** （*Adobe Commerce 2.4.2* 用） – 大きなメディアギャラリーを読み込むと画像が表示されない問題を修正しました。

## v1.0.21 {#v1-0-21}

* **MDVA-34665** （*Adobe Commerce >=2.3.4 &lt;=2.3.4-p2* の場合） – カテゴリページにバンドル製品が見つからない問題を修正しました。
* **MDVA-36615** （*Adobe Commerce 2.4.2* 用） – Admin Product Grid で間違った製品数に関する問題を修正しました。
* **MDVA-36464** （*Adobe Commerce >=2.4.0 &lt;=2.4.2* の場合） – メール通知設定がストアビューレベルで機能しない問題を修正しました。
* **MDVA-36138** （*Adobe Commerce ^2.3.2* の場合） – 送料が調整されず、カート内のすべての商品が送料無料カート ルールに該当しない場合に全送料が表示される問題を修正しました。
* **MDVA-36424** （*Adobe Commerce >=2.3.0 &lt;=2.3.3-p1 || >=2.0.0 &lt;2.2.0*） – バックエンドのベース URL がストアフロントのベース URL と異なる場合に、コンテンツを繰り返し編集すると、ページビルダー要素に添付されたメディア画像が消える問題を修正しました。
* **MDVA-35984** （*Adobe Commerce ^2.4.0* の場合） – 同じ商品に対して複数の同時出荷を作成した後に、誤った数量と販売可能な数量の問題を修正します。

## v1.0.20 {#v1-0-20}

* **MDVA-36170** （*Adobe Commerce >=2.3.4 &lt;2.4.2* の場合） – カテゴリキャッシュタグを使用してGraphQL クエリがキャッシュされない問題を修正しました。
* **MDVA-33168** （*Adobe Commerce >=2.3.3 &lt;2.4.2* の場合） - API を使用して product 属性を更新すると、他のすべての属性が空の値に変更される問題を修正しました。
* **MDVA-19640** （*Adobe Commerce >=2.3.0* の場合） - [!DNL Advanced Reporting] でデータが表示されない問題を修正しました。
* **MDVA-11189** （*Adobe Commerce >=2.3.0 &lt;2.3.5* の場合） - CSV ファイルを読み込んで商品ストックを更新すると、`cataloginventory_stock` テーブルの行が削除される問題を修正しました。
* **MDVA-26639** （*Adobe Commerce >=2.3.3-p1 &lt;2.3.6*） – 新しい注文確認メールテンプレートを作成した場合に、注文メールに注文項目が見つからない問題を修正しました。
* **MDVA-15546** （*Adobe Commerce >=2.3.0* の場合） – オーダーを作成した後、句があいまいな *Column entity_id を指定すると* 例外ログにエラーが表示される問題を修正しました。
* **MDVA-21095** （*Adobe Commerce >=2.3.0 &lt;2.3.5* の場合） – 属性値の一括更新後にクエリ `INSERT INTO search_tmp` が終了しない問題を修正しました。
* **MDVA-23845** (*Adobe Systemsコマース用 >=2.3.2-p2 &lt;2.3.5*) - JavaScript縮小を有効にした後、電子メールテンプレートをプレビューできない問題を修正します。
* **MDVA-22026** (*Adobe Systemsコマース用 >=2.3.2 &lt;2.3.4*) - 外部 URL からの画像を含むCSVファイルからの製品のインポートが失敗する問題を修正します。
* **MDVA-22383** (*Adobe Systemsコマース用 >=2.3.0 &lt;2.3.4*) - 商品の保存に時間がかかり、ページが壊れる問題を修正します。
* **MC-41359** (*Adobe Systemsコマース用 >=2.3.6-p1 &lt;2.3.7,>=2.4.2 &lt;2.4.3*) - SameSite cookie パラメーター設定が正しくない問題を修正します。&lt;/2.3.7,>

## v1.0.19 {#v1-0-19}

* **MDVA-33614** （*Adobe Commerce 2.4.1* の場合） – ページビルダーで次のエラーがスローされる問題を修正しました。*ページビルダーの起動中にエラーが発生しました。 テクニカル サポート担当者にお問い合わせください。*
* **MDVA-35356** （*Adobe Commerce >=2.3.0 &lt;2.4.3* の場合） – 部分的に請求された注文のキャンセル後に、誤ったストアクレジット返品が発生する問題を修正しました。
* **MDVA-33289** （*Adobe Commerce >=2.4.0 &lt;2.4.3* の場合） - [!DNL Google Tag Manager] が有効になっている場合に、チェックアウト時に未加工のJavaScript コードが請求先住所 UI に表示される問題を修正しました。
* **MDVA-35982** （*Adobe Commerce >=2.3.0 &lt;2.4.3* の場合） – 特定の web サイトに限定されている管理者ユーザーが、同じ web サイトで注文した商品の発送を作成できない問題を修正しました。
* **MDVA-35155** （*Adobe Commerce >=2.3.0 &lt;2.3.6* の場合） – オプションタイトルが変更された場合にバンドル商品を購入できない問題を修正しました。
* **MDVA-35910** （*Adobe Commerce >=2.4.1 &lt;2.4.3* の場合） – 「お客様としてログイン」機能を無効にすると新しいお客様アカウントを作成できない問題を修正しました。
* **MDVA-34474** （*Adobe Commerce >=2.3.0 &lt;2.4.3* の場合） - API を使用して商品を購入リストに追加する際の問題を修正しました。
* **MDVA-34591** （*Adobe Commerce >=2.3.0 &lt;2.4.3* の場合） - *最大数量割引が適用される* および *割引数量ステップ（購入 X）* に対する買い物かごルールの割引計算が正しくない問題を修正しました。
* **MDVA-33704** （*Adobe Commerce >=2.4.0 &lt;2.4.3* の場合） – 「*店舗での受け取り*」配送オプションが使用可能に設定されているにもかかわらず表示されない問題を修正しました。
* **MDVA-34928** (*Adobe Systemsコマース用 >=2.3.5 &lt;2.3.5-p2*) - ストア クレジットが支払いから削除された後、ページローダーが無期限に表示される問題を修正します。
* **MDVA-35254** （*Adobe Commerce >=2.3.1 &lt;2.4.3* の場合） – チェックアウト中の CAPTCHA の問題を修正しました。
* **MDVA-35569** （*Adobe Commerce >=2.3.4 &lt;2.4.2* の場合） – state が指定された場合に、GraphQL レスポンスで *固定商品税* フィールドが入力されない問題を修正しました。
* **MDVA-35847** （*Adobe Commerce >=2.4.1 &lt;2.4.3* の場合） – カスタムカスタマー属性が使用されている場合に会社ユーザーフォームが壊れる B2B の問題を修正しました。
* **MDVA-31307** （*Adobe Commerce >=2.4.0 &lt;2.4.2* の場合） – キャッシュされたブロックの動的 CSP 許可リストへの登録で問題が発生したことが原因で、特定のカテゴリで *メモリ不足* エラーが発生する問題を修正しました。

## v1.0.18 {#v1-0-18}

* **MDVA-32655** （*Adobe Commerce >=2.3.0 &lt;2.4.3* の場合） – 複数の商品を削除した後、消費者 `quoteItemCleaner` ーザーに対して誤った *処理中* メッセージステータスを正しい *完了* メッセージに修正します。
* **MDVA-34102** （*Adobe Commerce >=2.3.0 &lt;2.4.3* の場合） – 「Product Grid」ページと「Edit Product」ページで、無効になっている商品のデフォルトの在庫数がゼロになる問題を修正しました。
* **MDVA-35286** （*Adobe Commerce >=2.4.0 &lt;2.4.2* の場合） – お客様が買い物かごにバンドル商品を持っていて、複数のアドレスのチェックアウトから Onepage チェックアウトに切り替えた場合にエラーが発生する問題を修正しました。
* **MDVA-35312** （*Adobe Commerce >=2.4.1-p1 &lt;2.4.2* の場合） – 空のGraphQL リクエストの場合に応答コード 500 を修正します。
* **MDVA-34189** （*Adobe Commerce >=2.3.4 &lt;2.4.3* の場合） – Admin Category ページを読み込む際に、[!DNL Visual Merchandiser] クエリで 503 バイトの最初のタイムアウトが修正されました。
* **MDVA-34695** （*Adobe Commerce >=2.3.0 &lt;2.4.1* の場合） – カテゴリを削除した後の負の `children_count` を修正します。

## v1.0.17 {#v1-0-17}

* **MDVA-34012** （*Adobe Commerce >=2.3.1 &lt;2.4.3* の場合） – スケジュールされた変更が適用されると「*デフォルト値を使用*」チェックボックスがオフになる問題を修正しました。 この問題は、スケジュールされた変更が有効でなくなった時点で表示されます。
* **MDVA-35064** （*Adobe Commerce >=2.3.3 &lt;2.4.3* の場合） – API を使用して作成された設定可能な商品の URL の書き換えが生成されない問題を修正しました。
* **MDVA-34943** （*Adobe Commerce >=2.3.0 &lt;2.4.2* の場合） – クイックオーダーで以前に入力された SKU がキャッシュされる問題を修正しました。
* **MDVA-35197** (*Adobe Systemsコマース用 >=2.3.5 &lt;2.4.0*) - 以前に追加した商品が在庫切れになった場合、GraphQL を使用して買い物かごに追加するときにエラーが発生する問題を修正します。
* **MDVA-34850** (*Adobe Systemsコマース用 >=2.3.1 &lt;2.4.0*) - コンフィギュレーション可能製品の在庫切れオプションが取り消し線として表示されるのではなく、表示されない問題を修正します。
* **MDVA-34867** (*Adobe Systemsコマース用 >=2.3.0 &lt;2.4.3*) - スケジュールされた更新の条件フィールド セットの値が保存されない問題を修正します。
* **MDVA-35092**(*Adobe Systemsコマース用 >=2.3.5 &lt;2.4.3*) - 非推奨の [!DNL Vimeo] API が原因でユーザーが[!DNL Vimeo]ビデオを追加できない問題を修正します。

## v1.0.16 {#v1-0-16}

* **MDVA-33453** （*Adobe Commerce >=2.3.6 &lt;2.4.3* の場合） – 一致する商品の価格が web サイトごとに異なる場合に、ページビルダー商品のコンテンツタイプのプレビューが機能しない問題を修正しました。
* **MDVA-32634** （*Adobe Commerce ^2.3.1* の場合） – すべてのストアに割り当てられたカテゴリの `url_path` が、階層内でカテゴリを移動した後も変更されない問題を修正しました。
* **MDVA-33344** （*Adobe Commerce ^2.3.0* の場合） – データベースの値の代わりに、ハードコードされた `rma_item` エンティティのデフォルト属性セット ID が使用される問題を修正しました。
* **MDVA-34192** （*Adobe Commerce >=2.3.4 &lt;2.4.3* の場合） – dd/mm/yyyy 形式を使用してお客様の生年月日を変更/指定できない問題を修正しました。
* **MDVA-34847** （*Adobe Commerce ^2.3.0* の場合） – カスタム権限を持つ管理者ユーザーの管理コレクションで、SQL 条件に対するストア ID のタイプ変換を整数に修正しました。
* **MDVA-34886** （*Adobe Commerce ^2.3.2* の場合） - *weight* 商品属性が検索可能として設定されている場合、検索結果を返さない問題を修正しました。

## v1.0.15 {#v1-0-15}

* **MDVA-33559** (*Adobe Systemsコマース用 >=2.3.0 &lt;2.4.3*) - リダイレクトパラメーターリスト 形式エラーで [!DNL PayPal Payflow Pro] 支払いが失敗する問題を修正します。
* **MDVA-34023** (*Adobe Systemsコマース用 >=2.3.0 &lt;2.4.3*) - エラー *addressId を持つエンティティはありません* が訪問者のブラウザーにランダムに表示される問題を修正します。
* **MDVA-32759** (*Adobe Systemsコマース用 >=2.3.1 &lt;2.4.3 with B2B extension*) - 共有カタログが既存の階層価格を削除する問題を修正します。
* **MDVA-33482** (*Adobe Systems Commerce ^2.3.5* 用) - 部分的な請求書に対してクレジットメモを生成すると、その部分的な請求書の税金ではなく、注文の合計に対して税金が発生する問題を修正します。
* **MDVA-33393** (*Adobe Systems Commerce 用 >=2.3.0 &lt;2.4.2*) - エラーを修正 *指定された国 ID は存在しません*。
* **MDVA-33632** （*Adobe Commerce >=2.3.0 &lt;2.3.7* の場合） – 在庫切れの商品を再注文しようとすると、例外メッセージ *この商品は在庫切れです* が管理者ユーザーに表示される修正プログラムを提供します。
* **MDVA-34469** （*Adobe Commerce >=2.4.1 &lt;2.4.2* の場合） – 複数のストアビューを使用すると、顧客の買い物かごにGraphQL ミューテーションが失敗する問題を修正しました。
* **MDVA-33976** （*Adobe Commerce >=2.3.0 &lt;2.3.7* の場合） – バンドル製品から 2 つ目のオプションを削除した後、バンドル製品がストアフロントで在庫切れと表示される問題を修正しました。
* **MDVA-33894** （*Adobe Commerce >=2.4.0 &lt;2.4.1 with B2B extension*） – 複数の商品の追加と削除、SKU の大文字と小文字の区別など、クイックオーダー機能に関する複数の問題を修正しました。
* **MDVA-27664** （*Adobe Commerce >=2.3.4 &lt;2.3.6* の場合） – カスタマー登録フォームでエラーが表示される問題を修正しました。*エラー – 生年月日は本日より後にはできません。*
* **MDVA-33970** （*Adobe Commerce >=2.3.4 &lt;2.4.2* の場合） - price 属性のスコープが web サイトに設定されている場合に、クレジットメモに間違った通貨記号が表示される問題を修正しました。
* **MDVA-33992** （*Adobe Commerce >=2.3.0 &lt;2.4.2* の場合） – チェックアウト時に B2B 特別価格が正しく表示されない問題を修正しました。
* **MDVA-34100** （*Adobe Commerce >=2.3.4 &lt;2.4.2 with B2B extension*） – 会社構造ページから会社アカウントを作成できない問題を修正しました。

## v1.0.14 {#v1-0-14}

* **MDVA-31969** （*Adobe Commerce >=2.3.3 &lt;2.3.5, >=2.4.0 &lt;2.4.2* の場合） - CSV ファイルから商品を読み込んだ後の画像の重複の問題を修正しました。
* **MDVA-33382** （*Adobe Commerce >=2.3.0 &lt;2.4.2* の場合） – カテゴリから商品を削除した後のインデクサーの無効化の問題を修正しました。
* **MDVA-28511** （*Adobe Commerce >=2.3.5 &lt;2.3.6* の場合） – 「名前」フィールドに特定の文字（アクセント付き大文字など）が含まれている場合 [!DNL PayPal] チェックアウトを完了できない問題を修正しました。
* **MDVA-31519** （*Adobe Commerce >=2.3.5 &lt;2.3.6* の場合） – サイト全体の販売ルールが使用されている場合の、ゲストのチェックアウトでの待機タイムアウトの問題を修正しました。
* **MDVA-33281** (*Adobe Systemsコマース用 >=2.3.4 &lt;2.3.6*) - SKUパラメーターの型が正しくないために `inventory:reservation:list-inconsistencies` で致命的なエラーが発生する問題を修正します。
* **MDVA-24201** (*Adobe Systemsコマース用 >=2.3.0 &lt;2.3.5*) - 手動でインデックスを再作成するまで、価格がスケジュールされた買い物かご価格ルールを反映しない問題を修正します。
* **MDVA-32694** (*Adobe Systems コマース用 >=2.3.0 &lt;2.3.6 ||=&quot;&quot;>= 2.4.0 &lt;2.4.2*) - 既定ではないストアに関連している場合、管理者ユーザーが交渉可能な見積もりに製品を追加できない問題を修正します。&lt;/2.3.6>
* **MDVA-33516** (*Adobe Systemsコマース用 >=2.3.0 &lt;2.3.6*) - 要求リストのバンドル製品を編集するとエラーが発生する問題を修正します。
* **MDVA-33975** （*Adobe Commerce >=2.3.4 &lt;2.4.2* の場合） – GraphQL リクエストでの価格計算に関する複数の問題を修正しました。

## v1.0.13 {#v1-0-13}

* **MDVA-30858** （*Adobe Commerce >=2.3.0 &lt;2.4.2* の場合） - **レポート** > **営業** > **[!DNL PayPal]** 決済で [!DNL PayPal] 決済レポートが期待どおりに使用できない問題を修正しました。
* **MCP-87** （*Adobe Commerce >=2.3.1 &lt;2.4.2* の場合） – 大規模プロファイル向けのカテゴリ商品および在庫インデクサーのインデクシング時間を改善しました。
* **MDVA-33106** （*Adobe Commerce >=2.3.0 &lt;2.4.2* の場合） – cron `run` コマンドの実行後に、再スケジュールされた商品の変更内容が消去される問題を修正しました。
* **MDVA-19391**(*Adobe Systemsコマース用 >=2.3.0 &lt;2.3.5*) - `catalog_category_entity_text` テーブルの NULL 説明レコードが原因でエラーがスローされる問題を修正`analytics_collect_data`。
* **MDVA-20376** (*Adobe Systems Commerce >=2.3.2 &lt;2.3.4*) - 注文配置後にログインした顧客の`exception.log`に *customerId = 1 のエンティティはありません* というエラーの問題を修正します。
* **MDVA-23764** （*Adobe Commerce >=2.3.2 &lt;2.3.5* の場合） – ダイナミックブロックの表示に影響する `JsFooterPlugin.php` のバグを修正しました。
* **MDVA-13203** （*Adobe Commerce >=2.3.0 &lt;2.4.2* の場合） – フル再インデックス後に *Integrity constraint violation search_tmp_ table* エラーが表示される問題を修正しました。
* **MDVA-23426** （*Adobe Commerce >=2.3.3 &lt;2.3.5* の場合） – Adobe Commerceから送信される通知メールに、コンテンツが添付ファイルとして追加された空白の本文が含まれる問題を修正しました。
* **MDVA-22150** (*Adobe Systemsコマース用>= 2.3.1 &lt;2.3.4*) - 買い物かご で構成可能製品があり、クーポンが適用されている顧客が、その構成可能製品が管理で無効になっている場合、その顧客がログインできない問題を修正します。
* **MDVA-32545** (*Adobe Systemsコマース用 >=2.3.0 &lt;2.4.2*) - 管理者から注文を作成するときに請求書が自動的に送信されない問題を修正します。
* **MDVA-32714** (*Adobe Systemsコマース用 >=2.3.4 &lt;2.4.1*) - GraphQL 製品クエリで顧客 グループ価格が機能しない問題を修正。

## v1.0.12 {#v1-0-12}

* **MDVA-31399** (*Adobe Systemsコマース用 >=2.3.2 &lt;2.4.2*) - *小計を追加します。 税金)* ルール条件の価格を設定するオプション。
* **MDVA-31236** （*Adobe Commerce >=2.4.0 &lt;2.4.2* の場合） – カスタムリソースアクセス権を持つ管理者が 2FA を設定したり、ログインしたりできない問題を修正しました。
* **MDVA-30845** （*Adobe Commerce >=2.3.5 &lt;2.3.7* の場合） - *申し訳ありませんが、現時点ではこの注文の見積もりは利用できません* UPS XML/USPS/DHL への接続に失敗するとエラーが表示されます。
* **MDVA-32133** (*Adobe Systemsコマース用 >=2.4.0 &lt;2.4.1*) - 特定のケースでメディアギャラリーがページビルダーから読み込まれない問題を修正します。
* **MDVA-12304** (*Adobe Systemsコマース用>=2.3.0*)- Cookie の最大数を 50 から 200 に増やします。
* **MDVA-32632** (*Adobe Systemsコマース用 >=2.3.2 &lt;2.3.5*) - 注文が支払システムには表示されるが、Adobe Systems Commerce には表示されない問題を修正します。
* **MDVA-32449** (*Adobe Systemsコマース用 >= &lt;2.3.6 ||=&quot;&quot; 2.4.0=&quot;&quot; ||=&quot;&quot;>2.3.0 =2.4.1 &lt;2.4.2 with B2B extension*) - 注文履歴の読み込みが非常に遅い、またはまったく読み込まれない問題を修正します。&lt;/2.3.6>
* **MDVA-32739** (*Adobe Systemsコマース用 >=2.3.0 &lt;2.4.2*) - 非同期電子メール通知を有効にすると古いセールス電子メールが送信される問題を修正します。

## v1.0.11 {#v1-0-11}

* **MC-38509** (*Adobe Systems Commerce 2.3.6、2.4.1*&#x200B;用) - *新規作成顧客アカウント*&#x200B;フォームで無効データを修正した後&#x200B;*ボタンアカウント*&#x200B;作成が無効のままになる問題を修正します。
* **MDVA-31006** (*Adobe Systems Commerce 2.3.0、2.3.1* 用) - [!DNL Paypal Express] 支払を使用して注文した後に重複した注文が表示される問題を修正します。
* **MDVA-25602** (*Adobe Systems Commerce 2.3.0* 用) - クロム 80 ブラウザーおよび API 応答リダイレクト 顧客 ログイン ページ [!DNL PayPal Payflow Pro] 支払い方法とデフォルトで Cookie を `SameSite=Lax` として扱う問題を修正します。

## v1.0.10 {#v1-0-10}

パッチバージョンのマイナーな修正

## v1.0.9 {#v1-0-9}

* **MDVA-31363** （*Adobe Commerce >=2.3.2 &lt;2.4.2* の場合） - *買い物かご全体に対する固定金額割引* アクションを使用した際に、GraphQL経由でクーポン付きの買い物かご価格ルールが適用されない問題を修正しました。
* **MDVA-30889** （*Adobe Commerce >=2.3.0 &lt;2.4.2* の場合） – バーチャルおよびシンプルな商品をオプションとしてバンドルに対して請求した後にエラーが発生する問題を修正しました。
* **MDVA-31791** （*Adobe Commerce >=2.3.4 &lt;2.3.5*） – ターゲットルールまたはリンクされた商品を使用した場合の商品ページのパフォーマンスを向上させます。
* **MDVA-31168** （*Adobe Commerce >=2.3.0 &lt;2.4.2* の場合） – 製品の書き出し CSV ファイルが表示されず、メモリ割り当てエラーが発生する問題を修正しました。
* **MDVA-32313** （*Adobe Commerce >=2.3.0 &lt;2.3.4* の場合） – 設定可能な商品が間違った設定オプションでウィッシュリストに追加される可能性がある問題を修正しました。
* **MDVA-31759** （*Adobe Commerce >=2.3.0 &lt;2.4.2* の場合） - CSV の読み込み時に、商品が *dropdown* および *textarea* 属性値で更新されない問題を修正しました。
* **MDVA-32012** （*Adobe Commerce >=2.3.0 &lt;2.4.2* の場合） – 韓国とアルゼンチンの郵便番号を検証できない問題を修正しました。
* **MDVA-31640** （*Adobe Commerce >=2.3.1 &lt;2.3.6 || >=2.4.0 &lt;2.4.1*） - REST API で特別価格を更新できない問題を修正しました。
* **MDVA-28651** （*Adobe Commerce >=2.3.0 &lt;2.3.6 || >2.4.0 （B2B 拡張機能*） - REST API を使用して交渉可能な引用符を読み込む際にパフォーマンスの問題が発生する問題を修正しました。

## v1.0.8 {#v1-0-8}

* **MDVA-31242** (*Adobe Systemsコマース用 >=2.3.0 &lt;2.4.1 with B2B extension*) - クレジットメモグリッドに間違った通貨記号が表示される問題を修正しました。
* **MDVA-31295** (*Adobe Systemsコマース用 >=2.3.0 &lt;2.4.2*) - 部分的な注文が完了し、アイテムに課税されるときに報酬ポイントが計算されない問題を修正します。
* **MDVA-30112** （*Adobe Commerce >=2.3.4 &lt;2.4.2* の場合） – 注文数が *bunch-size* 値を超えた場合、Adobe Commerceが *pending* ステータスの注文を不整合と見なす問題を修正しました。
* **MDVA-31150** （*Adobe Commerce >=2.3.0 &lt;2.4.2*） – 請求書が Rest API 呼び出しによって転記され、注文がストアクレジットおよびギフトカードのアカウントによって部分的に支払われた場合に、GET請求書 Rest API 呼び出しによってストアクレジットおよびギフトカードの残高が返されない問題を修正しました。
* **MDVA-30963** （*Adobe Commerce >=2.3.2 &lt;2.4.2* の場合） – 製品のフィルター結果が、管理者の *すべてのストアビュー* 範囲に指定された値のみを含むように設定され、ストアビューレベルで上書きされた値を持つ製品が含まれる問題を修正しました。
* **MDVA-29954** （*Adobe Commerce >=2.3.0 &lt;2.3.6 || 2.4.0 || 2.4.2 （B2B 拡張機能*） - *新しい会社の登録要求* および *会社にリンクされています* メールが間違ったアドレスから送信される問題を修正しました。
* **MDVA-28357** （*Adobe Commerce >=2.3.2 &lt;2.3.6 || >=2.4.0 &lt;2.4.1*） - [!DNL ElasticSearch] インデックスの SKU フィールドで、標準アナライザーをカスタム アナライザーのキーワード トークナイザーに置き換えて、ワイルドカード検索クエリをハイフン（「–」）を含む SKU で機能させます。

## v1.0.7 {#v1-0-7}

* **MDVA-30972** （*Adobe Commerce >=2.3.0 &lt;2.4.2* の場合） - WebApi を使用した部分出荷作成後に、カスタム注文のステータスが *処理中* に変更される問題を修正しました。
* **MDVA-30428** （*Adobe Commerce >=2.3.4 &lt;2.3.5* の場合） – この商品がカスタムインベントリソースに割り当てられている場合、お客様がウィッシュリストに商品を追加できない問題を修正しました。
* **MDVA-30594** （*Adobe Commerce >=2.3.0 &lt;2.4.2* の場合） - FPT が設定されている場合に、チェックアウト時に複数のアドレスを持つ注文を保存できなかった問題を修正しました。
* **MDVA-29148** （*Adobe Commerce >=2.3.0 &lt;2.4.2* の場合） - API 呼び出しを使用して商品を作成する際に、ペイロードに値が指定されていない場合、`\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend` （Multiselect など）タイプの商品カスタム属性がデフォルト値を使用しない問題を修正しました。
* **MDVA-30837** （*Adobe Commerce >=2.3.1 &lt;2.3.5* の場合） – 送料無料の設定に「税金を金額に含める：Yes/No *」という設定を追加しました。* *金額に税金を含む* が *Yes* に設定されている場合、最小受注金額は小計+税金として計算されます。 *金額に税金を含む* が *No* に設定されている場合、最小発注金額は小計として計算されます
* **MDVA-25028** （*Adobe Commerce >=2.3.2 &lt;2.3.3 || >=2.3.5 &lt;2.3.6*） - [!DNL PayPal Payflow Pro] を使用して注文した注文が、不正フィルターがトリガーされたときに不正の疑いがあるステータスに設定されない問題を修正しました。
* **MDVA-31224** (*Adobe Systemsコマース用 >=2.3.3 &lt;2.3.5*) - バンドル製品の `catalog_product_price` インデックス再作成操作のパフォーマンスが向上します。
* **MDVA-31321** (*Adobe Systemsコマース用 >=2.3.2 &lt;2.3.5*) - *すべて表示* が選択されている場合の空白ページ(エラー)を修正します。 [!DNL Elasticsearch] は大量の製品 ID リストを返します。 このシナリオでは、ORDER BY 句が正しくない SQL 形式に変換されます。
* **MDVA-30815** （*Adobe Commerce >=2.3.2 &lt;2.3.4* の場合） – 検索結果ページに表示する検索結果の数を変更すると、Adobe Commerceで空白ページが表示される問題を修正しました。 ページご [!DNL Elasticsearch] に表示される検索結果の数を変更した場合に、カテゴリページの結果が正しく表示されるようになりました。
* **MDVA-30782** （*Adobe Commerce >=2.3.5 &lt;2.4.2* の場合） – カートのルールにかかわらず動的ブロックが表示される問題を修正しました。
* **MDVA-31021** （*Adobe Commerce >=2.3.0 &lt;2.4.2* の場合） - `module-catalog-import-export/Model/Import/Product/Option.php` でパフォーマンスの問題が発生している問題を修正しました。 テーブルに 100,000 件を超えるレコードがある場合、1 つの製品 `catalog_product_option` 含む新しい CSV の検証に要する時間は 10 秒未満です。
* **MDVA-31007** （*Adobe Commerce >=2.4.0 &lt;2.4.1* の場合） – カスタムアドレス属性がマイアカウント領域の注文詳細ページとバックエンドに正しく表示されない問題を修正しました。
* **MDVA-29389** (*for Adobe Commerce >=2.3.0 &lt;2.4.2*) - Fixes the issue with Advanced Reporting where the `analytics_collect_data` cronjob says: *Port must be configured within host parameter (like localhost:3306)*.
* **MDVA-31343** (*for Adobe Commerce >=2.3.4 &lt;2.3.6*) - Fixes the issue with the removed body class `page-layout-category-full-width` when a category is scheduled.
* **MDVA-30945** (*for Adobe Commerce >=2.3.0 &lt;2.4.2*) - Fixes the issue where you receive a fatal error message when updating carts `Call to a member function getValue() on null in module-configurable-product CartItemProcessor.php`.

## v1.0.6 {#v1-0-6}

* **MDVA-28993** (*for Adobe Commerce >=2.3.4 &lt;2.4.0*) - Implements the *Minimum should match* functionality and partial search for [!DNL Elasticsearch] engine. 検索クエリでのハイフンの問題を解決します。
* **MDVA-30102** （*Adobe Commerce >=2.3.2 &lt;=2.4.0* の場合） – レイアウトキャッシュに TTL がないので Redis キャッシュがすぐに大きくなる問題を修正しました。
* **MDVA-30599** （*Adobe Commerce >=2.3.4 &lt;=2.4.0* の場合） - API を使用して作成されたゲストの引用符が、ログインしたお客様の引用符として誤ってマークされる問題を修正しました。
* **MDVA-29446** (*for Adobe Commerce >=2.3.3 &lt;=2.4.0*) - Fixes the issue where the price of not applicable shipping method is shown as zero during checkout.
* **MDVA-30357** (*for Adobe Commerce >=2.3.2 &lt;=2.4.0*) - Fixes the issue with wrong image URLs are created when generating a sitemap by cron.
* **MDVA-30565** （*Adobe Commerce >=2.3.2 &lt;=2.3.3-p1* の場合） – ストアフロントのチェックアウトで、永続ショッピングカートが有効になっている場合に、ゲストのお客様に *No such entity with cartid = 0* エラーが表示される問題を修正しました。
* **MDVA-29787** （*Adobe Commerce >=2.3.0 &lt;=2.4.0* の場合） – 表示する商品を定義する際に *次のいずれか* 条件を使用した場合に、関連商品のターゲットルールが機能しない問題を修正しました。
* **MDVA-30977** （*Adobe Commerce >=2.3.4 &lt;=2.3.5-p2* の場合） – インデックス再作成後にカテゴリにランダムな商品が見つからない問題を修正しました。
* **MDVA-28202** （*Adobe Commerce >=2.3.4 &lt;=2.4.2* の場合） - MSI を使用したときにレイヤーナビゲーションで設定可能な商品が正しくフィルタリングされない問題を修正しました。
* **MDVA-28300** （*Adobe Commerce >=2.3.0 &lt;2.3.6* の場合） - GQL リクエストにカタログ価格ルールからの価格変更が反映されない問題を修正しました。
* **MDVA-31006** (*for Adobe Commerce >=2.3.2 &lt;=2.4.2*) - Fixes the issue where duplicated orders appear after placing an order using [!DNL Paypal Express] payment.

## v1.0.5 {#v1-0-5}

* **MDVA-30841** （*Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*） – レイヤーナビゲーションで検索エンジンとして使用された場合に、ブール型の製品属性の *いいえ* 値がレイヤーナビゲーションに含ま [!DNL Elasticsearch] なかった問題を修正しました。
* **MDVA-28191** （*Adobe Commerce >=2.3.3 &lt;2.4.2* の場合） – 管理者を介した注文作成時に支払い方法が読み込まれない問題を修正しました。
* **MDVA-29959** （*Adobe Commerce >=2.3.0 &lt;=2.3.3-p1 with B2B extension* の場合） – *会社* 権限を持つ制限付き管理者ユーザーが会社アカウントを削除できない問題を修正しました。
* **MDVA-30265** （*Adobe Commerce >=2.3.3 &lt;2.4.2* の場合） – 請求書の作成後に出荷トラッキングリンクが機能しなくなる問題を修正しました。
* **MDVA-28409** （*Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*） – データベース内の期限切れの引用符の数が多い場合に、`sales_clean_quotes` cron ジョブが *メモリ不足* エラーで失敗する問題を修正しました。
* **MDVA-30593** （*Adobe Commerce >=2.3.0 &lt;2.3.4* の場合） – 見積もりの有効期間の設定に従って期限切れになった見積もりがクリーンアップされない問題を修正しました。
* **MDVA-30107** （*Adobe Commerce >=2.3.0 &lt;2.3.6* の場合） – ストアビューで異なるベース URL が使用されている場合に、ストアスイッチャーが期待どおりに動作しない問題を修正しました。
* **MDVA-28763** (*Adobe Systemsコマース用 >=2.3.2 &lt;2.3.4*) - REST API を複数回使用して製品情報を更新した後に製品画像が重複する問題を修正します。
* **MDVA-30284** (*Adobe Systemsコマース用 >=2.3.0 &lt;2.4.2*) - 次の *[!DNL Elasticsearch]エラーが原因でカタログSearchインデクサーが失敗する問題を修正します:インデックスの合計フィールド数の制限を超えました。*
* **MDVA-29042** (*Adobe Systemsコマース用 >=2.3.3 &lt;=2.3.4-p2 with B2B extension*) - 新しい製品が共有カタログに追加された後に、カタログのアクセス許可が自動的に *許可* に変更された問題を修正します。
* **MDVA-30428** (*Adobe Systemsコマース用 >=2.3.3 &lt;2.4.2*) - この商品がカスタム在庫ソースに割り当てられている場合、購入者が商品をウィッシュリストに追加できない問題を修正します。
* **MDVA-28661** (*Adobe Systemsコマース用>=2.3.0 &lt;2.4.2 with B2B extension*)- 管理者が変更された後に会社情報ユーザー会社 アカウントセクションでエラー会社スローされる問題を修正します。

## v1.0.4 {#v1-0-4}

* **MDVA-30195** （*Adobe Commerce 2.3.1 ～ 2.3.4-p2* の場合） – データベース名が長すぎると cron ジョブが失敗し、フロントエンドでカテゴリが更新されない問題を修正しました。
* **MDVA-30106** （*Adobe Commerce ^2.3.0* の場合） - JS コンソールで、チェックアウト時に支払いが読み込まれない問題を修正しました *null のプロパティ「length」を読み取れません*。
* **MDVA-28656** （*Adobe Commerce >=2.3.1 &lt;2.3.6 || >=2.4.0 &lt;2.4.2*） – 支払情報が不要な注文（100% 割引など）が注文され、その注文の請求書が作成された場合、注文のステータスが「完了」ではなく *クローズ* に変わる問題を修正します。
* **MDVA-30209** （*Adobe Commerce 2.3.0～2.3.3-p1* の場合） – お客様がアカウント情報を更新した場合に、お客様グループがデフォルトに変更される問題を修正しました。
* **MDVA-30123** （*Adobe Commerce >=2.3.4 &lt;2.4.2* の場合） - GraphQL クエリで属性オプションラベルが正しく翻訳されない問題を修正しました。
* **MDVA-29996** （*Adobe Commerce >=2.3.3 &lt;2.4.2* の場合） – カテゴリ権限を有効にした後、カテゴリページがフルページキャッシュによってキャッシュされない問題を修正しました。
* **MDVA-30164** （*Adobe Commerce >=2.3.1 &lt;2.4.2* の場合） – カスタム顧客属性が存在する場合に、顧客レコードを顧客グリッドから書き出すことができない問題を修正しました。
* **MDVA-30444** (*Adobe Systems コマース用 >=2.3.0 &lt;2.4.1*) - GraphQL を使用して行われた注文の確認メールが送信されない問題を修正します。
* **MDVA-30490** (*Adobe Systemsコマース 2.3.4 - 2.3.5-p2*) - 製品の 1 つに空の短い説明がある場合、製品比較で 500 エラーページがスローされる問題を修正します。
* **MDVA-30232** (*Adobe Systems コマース用 >=2.3.1 &lt;2.4.1*) - 元の注文にギフトカードが含まれている場合に再注文できない問題を修正します。
* **MDVA-29965** (*Adobe Systems コマース >=2.3.3 &lt;2.4.0*) - 顧客が買い物かごに製品を追加するときに無効なフォーム キー エラーが発生する問題を修正します。
* **MDVA-30008** （*Adobe Commerce >=2.3.0 &lt;2.4.2* の場合） – パブリックカタログ内の商品に対して管理 API を使用して注文できない B2B の問題を修正しました。
* **MDVA-22469** （*Adobe Commerce 2.3.2-p2～2.3.3-p1* の場合） – Adobe Commerce 2.3.3 にアップグレード後に、管理パネルでページビルダーが機能せず、一部の JS ファイルと CSS ファイルが読み込まれない問題を修正しました。
* **MC-35984** （*Adobe Commerce >=2.4.0 &lt;2.4.1* の場合） – 返品承認（RMA）用の出荷ラベルを作成した後に、マーチャントが返品ページのページ要素を操作できなかった問題を修正しました。

## v1.0.3 {#v1-0-3}

* **MDVA-25602** （*Adobe Commerce 2.3.0 ～ 2.3.4* の場合） - Chrome 80 ブラウザーおよびカスタマーログインページへの API レスポンスリダイレクトで、[!DNL PayPal Payflow Pro] の支払い方法と Cookie をデフォルトで `SameSite=Lax` として扱う問題を修正しました。
* **MDVA-26694** （*Adobe Commerce >=2.3.0 &lt;2.3.6 || 2.4.0*） – 製品およびカタログのキャッシュの有効期限が毎日切れる問題を修正しました。ただし、有効期限は別にスケジュールされます。
* **MDVA-27825** （*Adobe Commerce >=2.3.0 &lt;2.4.1* の場合） – メモリリークが原因で大量のデータの書き出しに失敗する問題を修正しました。
* **MDVA-29085** （*Adobe Commerce >=2.3.0 &lt;=2.3.5-p1* の場合） - API で会社が作成された場合に、新しい会社のメールが不要になる B2B の問題を修正しました。
* **MDVA-29344** （*Adobe Commerce >=2.3.5 &lt;=2.4.0-p1* の場合） – テキストをヘッダー要素からテキスト要素にコピーした後にページビルダーが停止する問題を修正しました。
* **MDVA-29835** （*Adobe Commerce >2.3.1 &lt;2.4.2* の場合） – ギフトカードの注文に 1 つではなく 2 つのコードが含まれていた問題を修正しました。
* **MDVA-30052** （*Adobe Commerce >=2.3.2-p2 &lt;2.3.5* の場合） – プライベートコンテンツ（ローカルストレージ）が正しく入力されず、パフォーマンスの問題が発生する問題を修正しました。
* **MDVA-30131** （*Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*） – レイヤーナビゲーションで検索エンジンとして使用された場合に、ブール型の製品属性の *いいえ* 値がレイヤーナビゲーションに含ま [!DNL Elasticsearch] なかった問題を修正しました。
* **MDVA-35514** （*Adobe Commerce >=2.4.0 &lt;2.4.1* の場合） – パッケージを作成モーダルウィンドウで、配送ラベルを作成し、注文した商品をパッケージに追加する問題を修正しました。
