---
title: リリースノート
description: Adobe Commerceで使用可能なパッチと、それらが解決する問題について説明します。
exl-id: 22262555-f5ea-49ad-98ad-ea8428ef66d5
source-git-commit: 811c29c722448a0dc0c9172f58020bd17241513c
workflow-type: tm+mt
source-wordcount: '26381'
ht-degree: 0%

---

# リリースノート

[[!DNL Quality Patches Tool]](https://github.com/magento/quality-patches) は、AdobeとMagento Open Source コミュニティが開発した個別のパッチを提供します。 インストールされたバージョンのAdobe Commerceで使用可能な個々のパッチに関する一般情報を適用、元に戻して表示できます。 パッチは、パッチの開発者に関係なく、Adobe CommerceおよびMagento Open Source プロジェクトに適用できます。 例えば、コミュニティが開発したパッチをAdobe Commerce プロジェクトに適用できます。

>[!INFO]
>
>Adobe Commerce プロジェクトにパッチを適用する手順については、[ パッチの適用 ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ja#apply-individual-patches) を参照してください。 リリース済みパッチの完全なリストを確認するには、『ソフトウェア更新ガイド』の「[[!DNL Quality Patches Tool]：パッチの検索 ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)」を参照してください。

>[!INFO]
>
>コミュニティがMagento Open Source用に作成した [!DNL quality patches] について詳しくは、[ リリースノート ](https://github.com/magento/quality-patches/blob/master/community-release-notes.md) を参照してください。

## v1.1.65 {#v1-1-65}

* **ACP2E-3753** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.8） – マルチストア設定の商品アラートメールが、ストアやテーマの設定に関係なく、常にデフォルトのテーマを使用して送信される問題を修正しました。
* **ACSD-64118** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.7） – 同じ商品を保存および更新する同時リクエストによって、データの一貫性や商品の重複が発生する問題を修正しました。
* **ACSD-64813** （Adobe Commerce >=2.4.4 &lt;2.4.9 の場合） – [!DNL REST] API を使用して [!DNL B2B] の共有カタログからカテゴリの割り当てを解除すると、時間がかかりすぎる、または大きなカタログでタイムアウトする問題を修正しました。
* **ACSD-65202** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.8 の場合） – 「マイアカウント」ページに、同じストア内の他のストアビューからの最近の注文が表示されない問題を修正しました。
* **ACSD-65254** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.8 の場合） - `updateCustomerEmail` [!DNL GraphQL] ミューテーションを使用してアカウントのメールアドレスを更新した後に、メール通知が顧客に送信されない問題を修正しました。
* **ACSD-65331** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.8 の場合） – チェックアウトページに繰り返し戻った後、[!UICONTROL Pick in Store] で選択したストアがクリアされた問題を修正しました。
* **ACSD-65822** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.8 の場合） – バンドルと設定可能な商品の数量が [!UICONTROL Customer's Activities] の買い物かごパネルに正しく表示されない問題を修正しました。
* **ACSD-66093** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.8 の場合） – ゲスト顧客の [!UICONTROL First Name] フィールドと [!UICONTROL Last Name] フィールドにメールアドレスが入力され、注文確認メールが無効になる問題を修正しました。
* 更新されたバージョン：**ACSD-51291**
* 交換済みパッチ：**ACSD-61522**

## v1.1.64 {#v1-1-64}

* **ACP2E-3838** （Adobe CommerceおよびMagento Open Source >=2.4.4-p9 &lt;2.4.4-p13 || >=2.4.5-p8 &lt;2.4.5-p12 || >=2.4.6-p6 &lt;2.4.6-p10 || >=2.4.7 &lt;2.4.7-p5） – 実稼動モードの管理パネルで、[!DNL Page Builder] CORS エラーによって変更が保存されない問題を修正しました。
* **ACP2E-3841** （Adobe CommerceおよびMagento Open Source >=2.4.5 &lt;2.4.8）の場合 – 副選択条件を使用して送料無料を有効にすると、複数配送商品の買い物かご価格ルールが正しく適用されない問題を修正しました。
* **ACSD-63139** （Adobe CommerceおよびMagento Open Source >=2.4.6 &lt;2.4.7 の場合） – 製品属性に何千ものオプション値が含まれている場合に、製品の書き出しが失敗する問題を修正しました。
* **ACSD-65100** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.8 の場合） – [!UICONTROL Media Gallery Image Optimization] 設定で [!UICONTROL Maximum Width] と [!UICONTROL Maximum Height] の値を削除すると、画像の最適化プロセス中にエラーが発生する問題を修正しました。
* **ACSD-65127** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.8） – 実稼動モードでJavaScriptの縮小を有効にすると、[!DNL TinyMCE] 6 でブラウザーコンソールにエラーが発生し、機能とユーザーエクスペリエンスに影響を与える問題を修正しました。
* **ACSD-65787** （Adobe CommerceおよびMagento Open Source >=2.4.7-p5 &lt;2.4.8） – テーブルデータを処理する際に、スキーマの作成中または未定義の配列キー「列」が原因で SchemaBuilder クラスがクラッシュする問題を修正しました。
* **ACSD-65223** （Adobe Commerce、B2B 1.5.1 の場合） - [!DNL B2B] 注書の条件と契約を手動で選択するとエラーが発生する問題を修正しました。
* **ACSD-65540** （Adobe Commerce、B2B 1.5.2 の場合） - `company_structure` テーブルの更新時に `REGEXP_LIKE` 関数がないと SQL 構文エラーが発生する問題を修正しました。
* **ACSD-65684** （Adobe Commerce、B2B 1.5.2 の場合） - `company_structure` テーブルで多数のレコード（約 100,000 以上）を処理する際に、[!DNL B2B] 1.5.2 にアップデートした後に `Magento_Company` モジュールをアップグレードするのに非常に時間がかかるパフォーマンスの問題を修正しました。
* 更新されたバージョン：**ACSD-48234**、**ACSD-51819**、**ACSD-57570**、**ACSD-56415**

## v1.1.63 {#v1-1-63}

* **ACSD-64627** （Adobe Commerce >=2.4.6-p8 &lt;2.4.8 の場合） – 会社構造内でユーザーを追加または編集する際に、カスタムカスタマー属性を保存できない問題を修正しました。
* **ACSD-64753** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.8 の場合） – 「Pickup in Store」で事前に選択したストアが、ストアの半径外にある場合でも、配送先住所が変更されたときに更新されない問題を修正しました。
* **ACSD-65195** （Adobe Commerce >=2.4.4 &lt;2.4.8 の場合） - GraphQL ミューテーション `createCompany` が必要なリージョンのない国でエラーをスローする問題を修正しました。
* **LYNX-839** （Adobe Commerce 2.4.8 用） – GraphQLを通じてお客様のグループ、セグメント、プロモーションルールに関する情報を公開しなくなりました。
* 更新されたバージョン：**MDVA-12304**、**ACSD-48234**、**ACSD-58054**

## v1.1.62 {#v1-1-62}

* **ACSD-63406** （Adobe CommerceおよびMagento Open Source >=2.4.4-p9 &lt;2.4.5 || >=2.4.5-p8 &lt;2.4.6 || >=2.4.6-p6 &lt;2.4.8） - `persistent_clear_expired` cron ジョブの実行時に期限切れの永続的な引用符が cron ジョブでクリアされない問題を修正しました。
* **ACSD-63520** （Adobe CommerceおよびMagento Open Source >=2.4.7 &lt;2.4.8 の場合） – 管理パネルの **[!UICONTROL Configurations]** を使用して追加された画像がアップロードの最大サイズ制限に準拠しない問題を修正しました。
* **ACSD-64523** （Adobe CommerceおよびMagento Open Source >=2.4.7 &lt;2.4.8 の場合） – 読み込みプロセス（管理者または API）を使用して、名前のない新しい商品を作成すると、管理インターフェイスが機能しなくなり、無効な商品になる問題を修正しました。
* **ACSD-64532** （Adobe CommerceおよびMagento Open Source >=2.4.6-p2 &lt;2.4.8） - ENV 変数が「false」に設定されると、ブール値の false ではなく文字列「false」として扱われる問題を修正しました。
* **ACSD-64592** （Adobe Commerce >=2.4.4 &lt;2.4.8 の場合） – デフォルト以外のストアにあるギフトカードのメールの請求リンクで、常にギフトカードの請求がデフォルトの web サイトにリダイレクトされる問題を修正しました。
* **ACSD-65164** （Adobe CommerceおよびMagento Open Source >=2.4.6 &lt;2.4.8 の場合） – 設定可能な商品を 1 つのチェックボックスを選択したカスタムオプションで並べ替えると、「*選択した商品の一部は現在利用できません*」というエラーメッセージが表示される問題を修正しました。
* **ACSD-64732** （Adobe Commerce >=2.4.4 &lt;2.4.8 の場合） – サードパーティのコントローラーがカスタマーセグメントで正しくキャッシュされなかった問題を修正しました。

## v1.1.61 {#v1-1-61}

* **ACP2E-3689** （Adobe CommerceおよびMagento Open Source >=2.4.7 &lt;2.4.8） – カテゴリツリーがより深いレベルに表示され、アンカー/非アンカーの関係が反映される複数の問題を修正しました。
* **ACP2E-3705** （Adobe Commerce >=2.4.7 &lt;2.4.8） – `MAGE_INDEXER_THREADS_COUNT` が設定されている場合に `indexer_update_all_views` cron 実行が失敗する問題を修正しました。
* **ACSD-63883** （Adobe Commerce >=2.4.4 &lt;2.4.7-p4 の場合） – 購買依頼リストがGraphQL応答で誤った `items_count` を返す問題を修正します。
* **ACSD-63974** （Adobe Commerce >=2.4.4 &lt;2.4.8 の場合） – すべてのレコードを一度に表示するのではなく、ページあたりのレコード数に制限されたレコードの一部のみを表示するページネーション機能をストアフロントの購買依頼リストグリッドに追加することで、品目が多すぎると購買依頼リストページの読み込みに時間がかかりすぎる問題を修正しました。
* **ACSD-64178** （Adobe CommerceおよびMagento Open Source >=2.4.7 &lt;2.4.8 の場合） – 何千もの製品属性がある場合に、属性セットの編集ページの読み込みに時間がかかる問題を修正しました。
* **ACSD-64209** （Adobe Commerce >=2.4.4 &lt;2.4.8 の場合） - cron スケジューラーがステータス **[!UICONTROL ordered]** の引用符を除外せずに交渉可能なすべての引用符を取得し、メールまたはメールがトリガーされる問題を修正しました。
* **ACSD-64431** （Adobe CommerceおよびMagento Open Source >=2.4.7 &lt;2.4.8 の場合） – リクエストのクーポンコード情報を含む `placeOrder` ミューテーションで内部エラーがスローされなくなり、代わりに注文が正常に行われたことを示します。
* **ACSD-64467** （Adobe CommerceおよびMagento Open Source >=2.4.7 &lt;2.4.8 の場合） – ストアビューレベルでカテゴリの説明を保存した後、WYSIWYG エディターが空のように表示される問題を修正しました。
* **ACSD-64546** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.8 の場合） - UPS 出荷ラベルの作成時に汎用エラーメッセージが UI で発生し、*配列から文字列への変換* 例外がログに保存される問題を修正しました。実際のエラーは UI に表示され、正しいエラーメッセージがログに保存されるようにします。
* **ACSD-64684** （Adobe Commerce >=2.4.4 &lt;2.4.8） – コンマ（千区切り記号） *1,000）* の値が *999* を超えるギフトカードを編集および保存すると検証エラーが発生する問題を修正しました。
* 更新されたバージョン：**ACSD-49392**、**ACSD-50368**、**ACSD-51819**、**ACSD-54966-V2**、**ACSD-57003**、**ACSD-62979**、**ACSD-64112**
* 交換後のパッチ：**ACSD-49392**、**ACSD-58739**、**ACSD-62689**、**ACSD-64112**
* 非推奨パッチ：**ACSD-46192**, **ACSD-52133**

## v1.1.60 {#v1-1-60}

* **ACSD-63323** （Adobe Commerce >=2.4.7 &lt;2.4.8 の場合） – カテゴリに商品を追加すると、「**[!UICONTROL Select All]**」オプションが機能しない問題を修正しました。 さらに、ポップアップグリッドを使用してカテゴリに製品を追加する際に、ページネーションとレコード数ラベルが正しく機能するようにします。
* **ACSD-63992** （Adobe Commerce >=2.4.4 &lt;2.4.8 の場合） – 管理 UI から、クーポンおよび発送方法に基づく条件を含む買い物かご価格ルールを正しく適用できない問題を修正しました。
* **ACSD-64111** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.8 の場合） – [!DNL Page Builder] で製品コンポーネントのネストされた条件を設定する際にエラーが発生する問題を修正しました。
* **ACSD-64137** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.8 の場合） – オランダ語表記の場合、郵便番号で受け取り場所を検索することが適切に機能しない問題を修正しました。
* **ACSD-64149** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.8 の場合） – いずれかの日付のみを編集した場合に、日付範囲条件を持つカスタマーセグメントを保存できる問題を修正しました。
* 更新されたバージョン：**MDVA-12304**、**ACSD-45049**、**MDVA-43824**、**ACSD-46192**、**ACSD-50368**、**ACSD-52133**、**ACSD-47657**、**ACSD-51819**、**ACSD-54966-V2**、**55628** **45049** **63242** ACSD-1、ACSD-2

## v1.1.59 {#v1-1-59}

* **ACSD-63454** （Adobe CommerceおよびMagento Open Source >=2.4.7 &lt;2.4.8 の場合） – ドロップダウン属性と複数選択属性のデフォルト値がデータベースに正しく保存されない問題を修正しました。
* **ACSD-63574** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.5 の場合） – ページビルダーを使用してバンドル製品リストをブロックに追加するとエラーが発生する問題を修正しました。
* **ACSD-63793** （Adobe CommerceおよびMagento Open Source >=2.4.6 &lt;2.4.8 の場合） – インポートプロセスが異なるブラウザータブで互いに干渉する問題を修正しました。
* **ACSD-64113** （Adobe CommerceおよびMagento Open Source >=2.4.5 &lt;2.4.8 の場合） – メディアギャラリーから高さに対して比較的幅が小さい（またはその逆の）画像をアップロードした場合に、管理者でエラーが発生する問題を修正しました。
* **ACSD-64212** （Adobe CommerceおよびMagento Open Source >=2.4.5 &lt;2.4.8 の場合） – 注文を行った後にGraphQLを介してアカウントを作成した場合に、注文が顧客アカウントに関連付けられていない問題を修正しました。
* **ACSD-63469** （Adobe CommerceおよびMagento Open Source >=2.4.7 &lt;2.4.8） – 複数のルールが適用された場合に、買い物かご全体に対する固定金額の割引が適切に適用されなかった問題を修正しました。
* **ACSD-63870** （Adobe Commerce >=2.4.4 &lt;2.4.4-p11 の場合） – お客様のアクティブセッション中に会社のステータスが変更されると、会社の顧客が適切にログアウトされない問題を修正しました。
* **ACSD-64112** （Adobe Commerce >=2.4.5 &lt;2.4.8 の場合） – `MAGE_INDEXER_THREADS_COUNT` が設定されている場合に `indexer_update_all_views` cron 実行が失敗する問題を修正しました。
* 更新されたバージョン：**ACSD-61622**
* 交換済みパッチ：**ACSD-61553**
* 非推奨パッチ：**ACSD-61199**

## v1.1.58 {#v1-1-58}

* **ACSD-48570** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.7） – **URL にストアコードを追加** が *有効* の場合に「[!UICONTROL Admin] リセットパスワード」リンクをクリックしても、パスワードリセットページにアクセスできない問題を修正しました。
* **ACSD-62118** （Adobe Commerce >=2.4.6 &lt;2.4.8 の場合） – 発注方法を使用して注文を行ったときに `sales_order_tax_item` テーブルが完全に更新されない問題 [!DNL B2B] 修正しました。
* **ACSD-63067** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.8 の場合） – すべての商品の数量が誤ってハイライト表示され、1 つの数量のみが間違っている場合に、グループ化された商品のすべての商品に関して *[!DNL Please specify the quantity of product(s).]* というメッセージが表示される問題を修正しました。
* **ACSD-63090** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.8 の場合） – 商品が買い物かごに追加された後に削除されると、買い物かごの商品が削除される問題を修正しました。
* **ACSD-63182** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.8 の場合） - **[!DNL MSI]** *が有効になっている重複したバンドル製品を保存するとエラーが発生する問題を修正* ました。
* **ACSD-63283** （Adobe Commerce >=2.4.4 &lt;2.4.8 の場合） – ギフトレジストリから商品を注文すると例外が発生する問題と、ギフトレジストリの更新にレジストリに属さない商品が含まれる問題を修正しました。
* **ACSD-63299** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.8 の場合） – 設定可能な商品の特別価格がストアフロントに表示されない問題を修正しました。
* **ACSD-63325** （Adobe CommerceおよびMagento Open Source >=2.4.7 &lt;2.4.8 の場合） – 空の [!DNL GraphQL] リクエストを送信すると `Syntax Error: Unexpected <EOF>` エラーが発生する問題を修正しました。
* **ACSD-63329** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.8 の場合） – [!DNL REST API] を使用して商品を作成する際に、入力タイプが **[!UICONTROL Date]** または **[!UICONTROL Date and Time]** の属性のデフォルト値が設定されない問題を修正しました。
* **ACSD-63572** （Adobe CommerceおよびMagento Open Source >=2.4.5 &lt;2.4.8 の場合） – インデクサープロセスが終了した場合に、`CatalogRule` インデクサーの一時テーブルがクリーンアップされない問題を修正しました。
* **ACSD-63578** （Adobe Commerce >=2.4.4 &lt;2.4.8 の場合） – [!UICONTROL Admin] の **[!UICONTROL Add to Order by SKU]** の「**[!UICONTROL Delete]**」ボタンをクリックしても [!DNL SKU] が削除されない問題を修正しました。
* 更新されたバージョン：**MDVA-39305-V3**
* 交換済みパッチ：**ACSD-56280**
* 非推奨パッチ：**ACSD-62872**

## v1.1.57 {#v1-1-57}

* **ACSD-57570** （Adobe Commerce >=2.4.4 &lt;2.4.4-p10 の場合） – 特定のストアへのアクセスを持つ制限付き管理者ユーザーが、商品が割り当てられているすべての共有カタログを常に表示したり、保存できないお客様を表示したりできず、システムの不整合が発生する問題を修正しました。
* **ACSD-58325** （Adobe Commerce >=2.4.6 &lt;2.4.7 の場合） – 検証エラーの後も「**[!UICONTROL Import]**」ボタンが使用可能な問題を修正しました。
* **ACSD-59083** *（Adobe Commerce >=2.4.4 &lt;2.5.0 の場合） – データベースの更新が同時に実行されている場合に、一部の [!DNL mview] ータベース テーブルまたはビューが見つからない* というエラーが発生する問題を修正しました。
* **ACSD-61622** （Adobe CommerceおよびMagento Open Source >=2.4.6-p1 &lt;2.4.7） – [!DNL FedEx] のアカウント固有のレートが応答で欠落している問題を修正しました。
* **ACSD-61895** （Adobe Commerce >=2.4.4 &lt;2.5.0 の場合） – ルートカテゴリに **allow** 権限がない場合でも、カテゴリ [!DNL GraphQL] クエリが **allow** 権限を持つカテゴリを返す問題を修正しました。
* **ACSD-62212** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.5.0 の場合） - **パスワードを忘れた場合** メールコンテンツがストア表示の言語に翻訳されない問題を修正しました。
* **ACSD-62481** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.5.0 の場合） - **[!UICONTROL Persistence]** が有効になっている場合でも、顧客の買い物かごが空になる問題を修正しました。
* **ACSD-62629** （Adobe CommerceおよびMagento Open Source >=2.4.7 &lt;2.5.0 の場合） – **[!UICONTROL Widgets]** で使用される商品リストがカテゴリ条件を反映しない問題を修正しました。
* **ACSD-62635** （Adobe CommerceおよびMagento Open Source >=2.4.7 &lt;2.5.0 の場合） – マルチストア関連商品が [!DNL GraphQL] 商品クエリに正しく表示されない問題を修正しました。
* **ACSD-62671** （Adobe CommerceおよびMagento Open Source >=2.4.7 &lt;2.5.0 の場合） – [!DNL GraphQL] リクエストが最初の試行で最新のアドレス情報を返さない問題を修正しました。
* **ACSD-62689** （Adobe CommerceおよびMagento Open Source >=2.4.7 &lt;2.5.0 の場合） - *depth 4* の後で、お客様が **[!UICONTROL Related Product Rules and Widgets]** にカテゴリを追加できない問題を修正しました。
* **ACSD-62708** （Adobe CommerceおよびMagento Open Source >=2.4.4-p11 &lt;2.4.5 || >=2.4.5-p10 &lt;2.4.6-p2 || >=2.4.6-p8 &lt;2.4.7-p1） – 管理画面の [!DNL TinyMCE] 7 エディターのフォントサイズが *PX* ではなく *PT* と表示される問題を修正しました。 フォントサイズを *PT* ではなく *PX* で設定できるようになりました。
* **ACSD-62758** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.5.0 の場合） – [!DNL URL] に選択したオプションが含まれている場合、**[!UICONTROL Configurable Product]** の詳細ページで商品ビデオが正しくレンダリングされない問題を修正しました。
* **ACSD-62951** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.5.0 の場合） – クレジット メモのメールが項目と合計を含めずに送信される問題を修正しました。
* **ACSD-62965** （Adobe Commerce >=2.4.7 &lt;2.5.0 の場合） – `LocalizedException` メッセージが注文 [!DNL GraphQL] 応答に含まれない問題を修正しました。
* **ACSD-63286** （Adobe Commerce >=2.4.6 &lt;2.4.7 の場合） - [!DNL API] を介して共有カタログに割り当てられた商品が、手動の再インデックスが実行されるまでストアフロントに表示されない問題を修正しました。
* **ACSD-63326** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.5.0 の場合） – バックエンドから注文した後、[!UICONTROL Admin] が壊れたページにリダイレクトされる問題を修正しました。
* 更新されたバージョン：**ACSD-51739**
* 交換済みパッチ：**MDVA-43451**、**ACSD-62755**

## v1.1.56 {#v1-1-56}

* **ACSD-63244** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.8 の場合） - [!DNL JavaScript] エラーによって [!DNL Google Maps] が正しくレンダリングされない問題を修正しました。 *Uncaught TypeError:this が多数ある問題を修正しました。_each は関数ではなく*[!UICONTROL Admin] パネルのコンソールでエラーが発生します。
* **ACSD-63242** （Adobe CommerceおよびMagento Open Source >=2.4.6-p8 &lt;2.4.7 || >=2.4.7-p3 &lt;2.4.8） - 10,000 個を超えるエントリを含むカタログ製品を追加する際の読み込み速度の問題を修正しました。
* **ACSD-63062** （Adobe CommerceおよびMagento Open Source >=2.4.7 &lt;2.4.8） – 複数の重複するルールが適用される場合に、買い物かごの割引計算が正しく行われない問題を修正しました。
* **ACSD-62979** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.7） – [!DNL GraphQL] ヘッダーで間違った [!UICONTROL Store ID] を使用すると、致命的なメモリエラーが発生する問題を修正しました。
* **ACSD-62971** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.8） - **quantity** 列に数値以外の値が含まれる在庫ソースを読み込むと、**quantity** が *0* に設定される問題を修正しました。
* **ACSD-62872** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.8 の場合） – スケジュールの更新が正しく検証されない場合の一意の属性の検証の問題を修正しました。
* **ACSD-62755** （Adobe CommerceおよびMagento Open Source >=2.4.4-p11 &lt;2.4.5 || >=2.4.5-p10 &lt;2.4.6 || >=2.4.6-p8 &lt;2.4.7 || >=2.4.7-p3 &lt;2.4.8） - [!DNL TinyMCE] 7 で、エディターの初期化設定内でフォントサイズとフォントを特別に追加する必要がある問題を修正しました。
* **ACSD-62670** （Adobe CommerceおよびMagento Open Source >=2.4.4-p11 &lt;2.4.5 || >=2.4.5-p10 &lt;2.4.6 || >=2.4.6-p8 &lt;2.4.7 || >=2.4.7-p3 &lt;2.4.8） - [!UICONTROL Products Ordered] レポートを [!DNL CSV] にエクスポートし、[!DNL XML] がエラーを返す問題を修正しました。
* **ACSD-62577** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.8 の場合） – クエリインデックスとテーブルインデックスの両方を最適化することで、ストアフロント検索クエリのパフォーマンスが遅い問題を修正しました。
* **ACSD-62475** （Adobe CommerceおよびMagento Open Source >=2.4.7 &lt;2.4.8 の場合） – [!UICONTROL Gift Card] 商品がカートに正しく結合されない問題を修正しました。
* **ACSD-62428** （Adobe CommerceおよびMagento Open Source >=2.4.6 &lt;2.4.7 の場合） - [!DNL SKU] が検索可能な属性として設定されていない場合に、カタログ検索インデックスで `is_out_of_stock` が誤った値に設定される問題を修正しました。
* **ACSD-62355** （Adobe CommerceおよびMagento Open Source >=2.4.6 &lt;2.4.8 の場合） – 設定可能な商品が、多くの値を持つ多くの属性に基づいている場合に、設定可能な商品の編集ページの読み込み時間を短縮します。
* **ACSD-61805** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.8 の場合） - [!DNL REST API] を使用してバックオーダーのステータスを更新した後、ストアフロントで商品の在庫切れが発生する問題を修正しました。
* **ACSD-60811** （Adobe CommerceおよびMagento Open Source >=2.4.7 &lt;2.4.8 の場合） – 現在のステータスが *処理中* または *不正* の場合にのみ、カスタム値またはコメントで注文ステータスを更新できる問題を修正しました。
* **ACSD-62952** （Adobe Commerce >=2.4.4 &lt;2.4.8 の場合） – ストアフロントで [!UICONTROL Gift Registry] 日が正しく表示されない問題を修正しました。
* **ACSD-55339** （Adobe Commerce >=2.4.4 &lt;2.4.8 の場合） – 「0」で始まる商品 [!DNL SKU] 「0」を削除し、引用符が更新されない問題を修正しました。
**
* 更新されたパッチ：**ACSD-59514**
* 更新されたバージョン：**ACSD-60816**
* 交換済みパッチ：**ACSD-59967**

## v1.1.55 {#v1-1-55}

* **ACSD-58383** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.8） – 同時に実行される 2 つの同一のリクエストで [!DNL REST API] を介して払い戻しを行うと、重複したクレジットメモが作成される問題を修正しました。
* **ACSD-58471** （Adobe Commerce >=2.4.4 &lt;2.4.8 の場合） – 関連するカタログ価格ルールがスケジュールされている際に、製品の詳細ページに動的コンテンツが読み込まれない問題を修正しました。
* **ACSD-58566** （Adobe Commerce >=2.4.6 &lt;2.4.8 の場合） - `addPurchaseOrderComment` ミューテーションの `created_at` フィールドに対するクエリを実行する際に、[!DNL GraphQL] が内部サーバーエラーを返す問題を修正しました。
* **ACSD-58685** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.8 の場合） – メール通信が無効な場合に、メール通信が再度有効になっても営業メールが送信される問題を修正しました。
* **ACSD-58735** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.8 の場合） – 制限付き管理者が、関連する web サイトの [!UICONTROL Admin] のカスタマーアカウントページで放棄された買い物かごを表示できない問題を修正しました。
* **ACSD-58828** （Adobe CommerceおよびMagento Open Source >=2.4.6 &lt;2.4.8 の場合） – クライアントサイドの検証メッセージと共に、必須フィールドが空のままの場合、サーバーサイドの検証メッセージ *アドレスが必要* が表示される問題を修正しました。 サーバーサイドの検証では、空の必須フィールドに関するメッセージは表示されません。また、クライアントサイドの検証では、「これは必須フィールドです *というエラー通知が処理されます。*
* **ACSD-60344** （Adobe Commerce >=2.4.4 &lt;2.4.8 の場合） – 自動承認された **[!UICONTROL Purchase Order]** を使用したときに重複注文確認メールが送信される問題を修正しました。
* **ACSD-61348** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.8 の場合） – [!DNL GraphQL] を使用するとウィッシュリスト項目が表示されるが、複数の web サイト環境のストアフロントには表示されない問題を修正しました。
* **ACSD-61534** （Adobe CommerceおよびMagento Open Source >=2.4.7 &lt;2.4.8 の場合） – `bin/magento config:set` コマンドを使用してデザイン設定を指定できず、ロックされた値がフォーム操作によって変更される可能性がある問題を修正しました。 `--lock-env` または `--lock-conf` を使用して [!DNL CLI] から設定されたロックされた値は、更新できなくなりました。
* **ACSD-61785** （Adobe Commerce >=2.4.4 &lt;2.4.8 の場合） - [!DNL GraphQL] mutation および [!DNL REST API] 呼び出しを使用して `reward_warning_notification` 属性を更新できず、動作が `reward_update_notification` に合わせられない問題を修正しました。
* **ACSD-62591** （Adobe CommerceおよびMagento Open Source >=2.4.7 &lt;2.4.8 の場合） – テー **[!UICONTROL User Agent Rules]** が設定されたときにテーマが正しく切り替わらない問題を修正しました。
* **ACSD-62793** （Adobe CommerceおよびMagento Open Source >=2.4.7 &lt;2.4.8 の場合） – 書き出されたデータの `datetime` 属性に時間コンポーネントが含まれない問題を修正しました。 さらに、**[!UICONTROL Fields Enclosure]** が *有効* になっている場合、`additional_attributes` 列内の属性値は二重引用符で囲まれます。
* **ACSD-62332** （Adobe Commerce >=2.4.6 &lt;2.4.7 の場合） – 商品リスト [!DNL GraphQL] クエリが 10,000 個の商品の `total_count` に制限されていた問題を修正しました。 [!DNL GraphQL] 経由でクエリされ [!DNL Live Search] ときに、検索条件で現在のページがページ *2* ではなく *1* に設定される問題を修正しました。
* 更新されたバージョン：**ACSD-46581**、**ACSD-49513**、**ACSD-52801**、**ACSD-59514**
* 交換後のパッチ：**ACSD-52801**、**ACSD-55100**
* 非推奨パッチ：**ACSD-52085**, **ACSD-57854**

## v1.1.54 {#v1-1-54}

* **AC-13283** （Adobe CommerceおよびMagento Open Source 2.4.6-p8 の場合） - 2.4.6-p8 に含まれている注文の後方互換性のない変更を元に戻します。
* **ACSD-60267** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.8 の場合） – FPT 付きのシンプルな商品を買い物かごに直接追加する場合に固定商品税（FPT）が正しく適用され、設定可能な商品オプションからこれらの商品を選択する場合に失敗する問題を修正しました。
* **ACSD-61103** （Adobe CommerceおよびMagento Open Source >=2.4.6 &lt;2.4.7 の場合） – ユーザーが API エンドポイントを介して正常にログインした後、`customer_entity` テーブルのエラー数がゼロにリセットされない問題を修正しました。
* **ACSD-61134** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.7 の場合） – 「*[!UICONTROL My billing and shipping address are the same]*」チェックボックスの選択を解除することで、買い物客が請求先住所を更新する際に、チェックアウトワークフローで [!DNL Braintree Vault] の支払い方法の選択が自動的に解除される問題を修正しました。
* **ACSD-61199** （Adobe Commerce >=2.4.4 &lt;2.4.8 の場合） – 既存の階層を使用してCMS ページを編集する際に、「CMS ページの階層」タブに適切なツリー構造が表示されない問題を修正しました。
* **ACSD-61200** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.8） – 売上の *[!UICONTROL Total Amount]* と *[!UICONTROL Total Amount Actual]* の計算で *[!UICONTROL Discount Tax Compensation Amount]* と *[!UICONTROL Shipping Discount Tax Compensation Amount]* が欠落して、受注データに不一致が生じる問題を修正しました。
* **ACSD-61522** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.8 の場合） – ゲスト顧客の *[!UICONTROL First Name]* フィールドと *[!UICONTROL Last Name]* フィールドにメールアドレスを入力し、無効な注文確認メールを送信できる問題を修正しました。
* **ACSD-61756** （Adobe Commerce >=2.4.4 &lt;2.4.7 の場合） - `AdvancedSalesRule` フィルターのパフォーマンスを向上させます。
* **ACSD-61799** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.5 の場合） – 固定割引が適用された複数の買い物かごルールが見積もりに適用される際に、合計割引が正しく計算されない問題を修正しました。
* **ACSD-61845** （Adobe CommerceおよびMagento Open Source >=2.4.7-p1 &lt;2.4.8） – *text/html* accept ヘッダーのみを使用してリクエストが送信された場合に発生するエラーを修正します。
* **ACSD-62056** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.8 の場合） – MSI がインストールされている場合に、設定可能な商品のイメージアップロードが失敗する問題を修正しました。
* **ACSD-62485** （Adobe Commerce >=2.4.4 &lt;2.4.6-p8 の場合） || >=2.4.7 &lt;2.4.8） – 会社が作成されたときに `async.operations.all` の消費者が機能しなくなる問題を修正しました。
* 更新されたバージョン：**ACSD-48661**、**ACSD-55100**、**ACSD-61553**
* 非推奨パッチ：**ACSD-51846**

## v1.1.53 {#v1-1-53}

* **ACSD-48318** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.7 の場合） – 環境エミュレーションのネストが許可されていない問題を修正しました。 これで、`send()` 呼び出し中にエミュレーションが停止した後、`getInfoBlockHtml()` 呼び出し中にエミュレーションが開始されます。
* **ACSD-59930** （Adobe Commerce >=2.4.6 &lt;2.4.8） – 会社の **[!UICONTROL Create]**、**[!UICONTROL Save]** および **[!UICONTROL Delete]** フローのパフォーマンスを向上させます。
* **ACSD-60584** （Adobe CommerceおよびMagento Open Source >=2.4.5 &lt;2.4.7 の場合） – ある web サイトのユーザー用に作成されたアクセストークンが、他の web サイトの顧客情報にアクセスしたり、変更したりできる問題を修正しました。
* **ACSD-60804** （Adobe Commerce >=2.4.4 &lt;2.4.8 の場合） – 削除された会社にリンクされている顧客を編集すると、*メンバー関数の呼び出しが null で `getSuperUserId()` される* エラーが発生する問題を修正しました。
* **ACSD-61133** （Adobe Commerce >=2.4.4-p5 &lt;2.4.5） || >=2.4.5-p4 &lt;2.4.6 || >=2.4.6-p2 &lt;2.4.8） - `sales_clean_quotes` [!DNL cron] が未承認の発注書から見積を削除する問題を修正します。
* **ACSD-61528** （Adobe Commerce >=2.4.6 &lt;2.4.8 の場合） - [!DNL GraphQL] を使用して [!UICONTROL Admin] からロールを取得しても結果が返されない問題を修正しました。
* **ACSD-61553** （Adobe CommerceおよびMagento Open Source >=2.4.5 &lt;2.4.7 の場合） – 優先度や **[!UICONTROL Maximum Qty Discount is Applied To]** が異なる複数のディスカウントが商品に適用される場合に、**[!UICONTROL Cart Price Rule]** ディスカウントが正しく計算されない問題を修正しました。
* **ACSD-61667** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.8） – 店舗での受け取りで多くのソースが発生した場合の出荷を作成するための在庫性能を向上させます。
* **ACSD-61969** （Adobe Commerce >=2.4.7 &lt;2.4.8 の場合） – クーポンコードが設定されたのと完全に一致するように、大文字と小文字を区別するクーポンコードを入力する必要がある問題を修正しました。
* 更新されたバージョン：**ACSD-54989**、**ACSD-60632**

## v1.1.52 {#v1-1-52}

* **BUNDLE-3375** （Adobe CommerceおよびMagento Open Sourceの場合） - [!DNL Braintree] を支払い窓口として使用する場合に、3DS VISA の委任要件を満たすために必要なすべてのフィールドを追加します。
* **ACSD-59366** （Adobe Commerce >=2.4.6 &lt;2.4.8 の場合） – チームリストに表示されないディアクティベートされたユーザーを含むチームを削除しようとするとエラーが発生する問題を修正しました。
* **ACSD-59865** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.7 の場合） – カート内の商品の数量がルールを適用するのに十分でない場合に、以前に適用されたルールが [!UICONTROL Cart Price Rule] ーザーによってキャンセルされない問題を修正しました。
* **ACSD-59925** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.8 の場合） - GraphQLで [!UICONTROL Media Gallery] 内の項目を位置で並べ替える問題を修正しました。
* **ACSD-59952** （Adobe Commerce >=2.4.4 &lt;2.4.8 の場合） – 既存の [!UICONTROL Shared Catalog] ーザーに割り当てられたグループ ID を持つ [!UICONTROL Shared Catalog] ージを作成する際にエラーが発生する問題を修正しました。
* **ACSD-60590** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.7） – 大量の注文に対して [!UICONTROL Bestsellers Aggregated Daily Reports] を生成するパフォーマンスを向上させます。
* **ACSD-60673** （Adobe Commerce >=2.4.4 &lt;2.4.8 の場合） – チェックアウト時に複数の支払い方法の [!UICONTROL Cart Price Rule] が特定の支払い方法に適切に適用されない問題を修正しました。
* **ACSD-60684** （Adobe CommerceおよびMagento Open Source >=2.4.6 &lt;2.4.7） – 複数フィールドでのGraphQL製品の並べ替えが期待どおりに動作しない問題を修正しました。
* **ACSD-60788** （Adobe Commerce >=2.4.7 &lt;2.4.8 の場合） – コンテンツセキュリティポリシー（CSP）のエラーにより、[!DNL Google Tag Manager] のカスタムスクリプトが実行されない問題を修正しました。
* **ACSD-61322** （Adobe Commerce >=2.4.6 &lt;2.4.8 の場合） – デフォルト（一般グループ）の [!UICONTROL Shared Catalog] に割り当てら [!UICONTROL Products/Categories] ていないアセットが、XML サイトマップに引き続き含まれる問題を修正しました。
* **ACSD-61366** （Adobe CommerceおよびMagento Open Source >=2.4.7 &lt;2.4.8 の場合） - DB 接続用にポートが指定されている場合に、`setup:static-content:deploy --jobs 4` コマンドが複数のジョブで実行されて失敗し、「*Port must be configured within host parameter*」エラーが発生する問題を修正しました。
* 更新されたパッチ：ACSD-51857、ACSD-57394

## v1.1.51 {#v1-1-51}

* **ACSD-59786** （Adobe CommerceおよびMagento Open Source >=2.4.6 &lt;2.4.8 の場合） – 有効期限切れの見積もりの見積もり ID を取得しようとすると、GraphQLが内部サーバーエラーを返す問題を修正しました。
* **ACSD-60234** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.8） – 支払い方法で割引が適用されるときに、[!DNL PayPal] に誤った金額が表示される問題を修正しました。
* **ACSD-59967** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.7-p2 の場合） - JavaScript エラーによって [!DNL Google Maps] が正しくレンダリングされない問題を修正しました。
* **ACSD-60326** （Adobe Commerce >=2.4.4 &lt;2.4.8 の場合） – カスタマーリターンステータスのGraphQL クエリでエラーが発生する問題を修正しました。
* **ACSD-60538** （Adobe Commerce >=2.4.7 &lt;2.4.8 の場合） - *[!UICONTROL All Store Views]* で商品が無効になり、特定のストアビュースコープでのみ有効になっている場合、GraphQL レスポンスで商品属性が正しく表示されず、商品が正しく表示されない問題を修正しました。
* **ACSD-60631** （Adobe CommerceおよびMagento Open Source >=2.4.7 &lt;2.4.8） – 同じシンプルな商品が複数の設定可能な商品に割り当てられている場合に、GraphQLがエラーを返す問題を修正しました。
* **ACSD-60632** （Adobe CommerceおよびMagento Open Source >=2.4.5-p8 &lt;2.4.8） – 注文が正常に作成されたかどうかに関係なく、注文を試みるたびに新しいアドレスが保存される問題を修正します。
* **ACSD-60816** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.7 の場合） - APM エージェントによって挿入された [!DNL New Relic Browser Monitoring] スクリプトが CSP （コンテンツセキュリティポリシー）に準拠しておらず、実行が妨げられる問題を修正しました。
* **ACSD-61195** （Adobe CommerceおよびMagento Open Source >=2.4.7 &lt;2.4.8 の場合） – 買い物かごのGraphQL リクエストの最後のページで買い物かごの商品が返されない問題を修正しました。
* 更新されたパッチ：ACSD-59378

## v1.1.50 {#v1-1-50}

* **ACSD-59280** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.5 の場合） – 2.4.4-pX バージョンのインストール時に発生する *未定義メソッド ReflectionUnionType::getName （）の呼び出し* エラーを修正しました。
* **ACSD-45049** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.4-p8 || >=2.4.5 &lt;2.4.6） – 顧客 *[!UICONTROL Is required]* 属性の設定が管理者の web サイト範囲に従って正しく機能しない問題を修正しました。
* **ACSD-46938** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.6） – リク `setup:upgrade` スト中の DB トリガーの再作成のパフォーマンスの問題を修正しました。
* **ACSD-48210** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.7 の場合） – 特定のストアビューで *[!UICONTROL Website Scope]* 属性を更新すると、グローバルスコープの属性値が上書きされる問題を修正しました。
* **ACSD-54887** （Adobe CommerceおよびMagento Open Source >=2.4.4-p4 &lt;2.4.4-p9 || >=2.4.5-p3 &lt;2.4.5-p8 || >=2.4.6-p1 &lt;2.4.6-p6） - [!UICONTROL Persistent Shopping Cart] を有効にしてカスタマーセッションの有効期限が切れた後に、カスタマーショッピングカートがクリアされる問題を修正しました。
* **ACSD-58141** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.8 の場合） - [!DNL L2 Redis cache] が有効になっており、管理者から更新されている場合に、ログインしているお客様のストアフロント領域で PHPSESSID が POST リクエストで再生成される問題を修正しました。
* **ACSD-58352** （Adobe Commerce >=2.4.4 &lt;2.4.7 の場合） – リクエストヘッダーでデフォルト以外のストアビューが指定されている場合に、GraphQL API を介してデフォルトのストアビューの戻り属性ラベルが返される問題を修正しました。
* **ACSD-58442** （Adobe Commerce >=2.4.4 &lt;2.4.7-p1 の場合） – 幅 768 px のデバイスがモバイルとして扱われ、メニューとヘッダーがデスクトップではなくモバイルビューに読み込まれる問題を修正しました。
* **ACSD-58790** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.8 の場合） - [!DNL Chrome] のモバイルビューの製品詳細ページ画像のピンチからズームの機能を修正しました。
* **ACSD-59036** （Adobe CommerceおよびMagento Open Source >=2.4.7 &lt;2.4.8 の場合） – 下限と上限の両方が$0 の商品価格を読み込む場合に発生する例外を修正します。
* **ACSD-59229** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.7 の場合） – リクエストで X-Magento-Vary の古い値が原因で、顧客グループ関連の情報が間違ったセグメントに保存される問題を修正しました。
* **ACSD-59378** （Adobe CommerceおよびMagento Open Source >=2.4.5 &lt;2.4.6 の場合） – ストアレベルの URL 書き換えが読み込み中に誤って更新される問題を修正しました。
* **ACSD-59514** （Adobe Commerce >=2.4.4 &lt;2.4.7-p2 の場合） - Admin 領域内のフォームで、ロックを解除せずにレンダリング中のエラーを 5 秒間スローす *[!DNL Page Builder]問題を修正しまし [!DNL Page Builder]。フォームの送信後にブラウザーコンソールを* リックすると、変更を保存できない。
* **ACSD-60303** （Adobe Commerce >=2.4.4-p9 &lt;2.4.5） || >=2.4.5-p8 &lt;2.4.6 || >=2.4.6-p6 &lt;2.4.8） - HTMLの縮小が有効になっている場合に、管理者から注文できない問題を修正しました。
* **ACSD-60441** （Adobe CommerceおよびMagento Open Source 2.4.4-p9 用） || 2.4.5-p8 || 2.4.6-p6 || 2.4.7-p1） – バックエンドから生成された統合アクセストークンを使用す `V1/customers` 際に、[!DNL REST API] エンドポイントを介して顧客を更新する際の問題を修正しました。
* 更新されたパッチ：ACSD-57003

## v1.1.49 {#v1-1-49}

* **ACSD-56979** （Adobe CommerceおよびMagento Open Source >=2.4.3 &lt;2.4.7 の場合） – ステージングアップデートを削除した後に商品イメージが削除される問題を修正しました。
* **ACSD-57086** （Adobe CommerceおよびMagento Open Source >=2.4.3 &lt;2.4.7 の場合） – 利用条件が有効になっているデフォルト以外の web サイトから注文した注文が正しく処理されない問題を修正しました。
* **ACSD-57588** （Adobe CommerceおよびMagento Open Source >=2.4.6 &lt;2.4.7 の場合） – 複数のアドレスに注文を送信すると、リージョン ID の処理中にエラーがトリガーされる問題を修正しました。
* **ACSD-57643** （Adobe CommerceおよびMagento Open Source >=2.4.6 &lt;2.4.7 の場合） - GraphQLを使用してカスタムオプションを含む商品が買い物かごに誤って追加される問題を修正しました。
* **ACSD-57846** （Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.7） – GraphQL製品で価格ゼロのフィルターを使用して検索した場合、例外が原因で結果が返されない問題を修正しました。
* **ACSD-57941** （Adobe CommerceおよびMagento Open Source >=2.4.6 &lt;2.4.7 の場合） – 製品オプションが各ストアではなく管理ストアに誤って割り当てられる問題を修正しました。
* **ACSD-58375** （Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.7 の場合） – ストア表示レベルで [!DNL YouTube] ビデオを追加する際に、誤った *[!DNL YouTube API Key]* 設定が原因でエラーが発生する問題を修正しました。
* **ACSD-58739** （Adobe CommerceおよびMagento Open Source >=2.4.7 &lt;2.4.8 の場合） – インデックス再作成の一部でエラーがスローされる問題を修正しました。
* **ACSD-58446** （Adobe Commerce >=2.4.6 &lt;2.4.7 の場合） – ステータス（非アクティブ）に関係なく、子ユーザーまたはチームを持つチームを削除すると、UI に一致しない非情報エラーメッセージが表示される問題を修正しました。
* **ACSD-58054** （Adobe Commerce >=2.4.4 &lt;2.4.6 の場合） - API を使用して、非アクティブなお客様のカスタマートークンを生成できる問題を修正しました。
* **ACSD-58163** （Adobe Commerce >=2.4.3 &lt;2.4.7 の場合） – クーポンコードがない場合に、*[!UICONTROL Cart Price Rule]* ーザーが一致する *[!UICONTROL Customer Segment]* カートからゲスト顧客に割引を適用しない問題を修正しました。
* **ACSD-57045** （Adobe Commerce >=2.4.5 &lt;2.4.7 の場合） - *[!UICONTROL Website Root]* を *[!UICONTROL Hierarchy]* からオフにした後に URL の書き換えによって無限ページループが発生する問題を修正しました。
* 更新されたパッチ：ACSD-46815、ACSD-47027、ACSD-51683、ACSD-55031、ACSD-51819、ACSD-54965-v2

## v1.1.48 {#v1-1-48}

* **ACSD-55566** （Adobe CommerceおよびMagento Open Source >=2.4.3 &lt;2.4.7 の場合） – 同じバンドルアイテムを持つソースと宛先の買い物かごを結合する際に、`mergeCart` ミューテーションが [!DNL GraphQL] レスポンスで「*内部サーバーエラー*」で失敗する問題を修正しました。
* **ACSD-56546** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.7 の場合） - **在庫切れの商品設定を表示** が *無効* になっている場合に、設定可能な商品やバンドルの商品がストアフロントに **在庫切れ** と表示される問題を修正しました。
* **ACSD-56635** （Adobe Commerce >=2.4.6 &lt;2.4.7 の場合） - **アカウント共有** を *グローバル* に設定して読み込みを使用すると、読み込まれたお客様が同じメールアドレスで重複する問題を修正しました。
* **ACSD-56741** （Adobe CommerceおよびMagento Open Source >=2.4.6 &lt;2.4.7 の場合） – インデックスメカニズムおよび [!DNL MView] に関連しないカスタム [!DNL MySQL] トリガーがデータベースに含まれている場合に、`setup:upgrade` 行中に表示される「*null 型の値の配列オフセットにアクセスしようとしています*」エラーメッセージを修正しました。
* **ACSD-57315** （Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.7 の場合） – [!DNL PayPal Payflow Pro] で新しいトランザクションが作成された際に、管理者の **[!UICONTROL View transaction]** 画面で「[!UICONTROL Fetch]」ボタンをクリックするたびに発生する問題を修正します。
* **ACSD-57337** （Adobe Commerce >=2.4.4 &lt;2.4.6 の場合） – 特定の web サイトへのアクセス制限を持つ管理者ユーザーが、**[!UICONTROL Companies]** グリッド内のすべての web サイトの会社を表示できる問題を修正しました。
* **ACSD-57394** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.7） – [!DNL GraphQL] で複数の並べ替えフィールドを使用して誤った商品が並べ替えられる問題を修正しました。
* **ACSD-57565** （Adobe CommerceおよびMagento Open Source >=2.4.6 &lt;2.4.7 の場合） – 期間が更新されるまで **[!UICONTROL Order]** ダッシュボードに誤った注文情報が表示される問題を修正しました。 ダッシュボードには、最初の読み込み時に正しい注文統計が表示されるようになりました。
* **ACSD-57854** （Adobe CommerceおよびMagento Open Source >=2.4.5 &lt;2.4.7） – カテゴリ集計で製品 [!DNL GraphQL] リクエストが無効なカテゴリを返した場合の問題を修正しました。
* **ACSD-58008** （Adobe Commerce >=2.4.5 &lt;2.4.7 の場合） – 終了日が指定されていない場合に、スケジュールされた更新を更新するとステージングされた項目の以前のバージョンが削除される問題を修正しました。
* 更新されたパッチ：MDVA-39305-V2、ACSD-48627、ACSD-54965

## v1.1.47 {#v1-1-47}

* **ACSD-55241** （Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.7） – 複数のアドレスを使用したチェックアウトで、生成されたクーポンの *[!UICONTROL Used]* 属性と *[!UICONTROL Times Used]* 属性に誤った値が表示される問題を修正しました。
* **ACSD-56760** （Adobe Commerce >=2.4.6 &lt;2.4.7 の場合） – 特定の web サイトに制限されている管理者ユーザーが、web ストアが独自のルートカテゴリを持つ場合に、カテゴリ内で新しい商品の並べ替えや追加ができない問題を修正しました。
* **ACSD-56858** （Adobe Commerce >=2.4.2 &lt;2.4.7 の場合） – 制限付きの会社管理者に対して B2B 会社の役割の権限が正しく表示されない問題を修正しました。
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

* **ACSD-56886** （Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.7 の場合） – スケジュールされた更新によって 2 つの子商品のいずれかが無効になると、設定可能な商品が在庫切れになる問題を修正しました。
* **ACSD-56616** （Adobe CommerceおよびMagento Open Source >=2.4.5 &lt;2.4.6 の場合） – バンドルされた商品が、シンプルな商品が在庫切れになった場合に、ストアフロントに在庫として表示される問題を修正しました。
* **ACSD-56515** （Adobe Commerce >=2.4.2 &lt;2.4.7 の場合） – web サイトレベルの権限を持つ管理者が動的ブロックを追加または編集できない問題を修正しました。
* **ACSD-56447** （Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.7 の場合） – 並列の REST web API リクエストを使用して同じ商品を買い物かごに追加すると、買い物かごに 2 つの異なる商品が表示される問題を修正しました。
* **ACSD-56415** （Adobe CommerceおよびMagento Open Source >=2.4.5 &lt;2.4.7 の場合） – データベースにインデックスへの部分価格データが大量にある場合に、`DELETE` クエリが原因で部分価格インデックス作成のパフォーマンスが低下する問題を修正しました。
* **ACSD-54965** （Adobe Commerce >=2.4.5 &lt;2.4.6 の場合） – 商品がカスタム在庫のみに割り当てられている場合に、ビジュアルマーチャンダイジンググリッドに正しい在庫が表示されない問題を修正しました。
* **ACSD-52824** （Adobe Commerce >=2.4.5 &lt;2.4.7 の場合） – 会社設定で支払い方法を無効にすると、会社のお客様に PayPal Express、Google Pay、Apple Pay のボタンが表示される問題を修正しました。
* 更新されたパッチ：ACSD-56193

## v1.1.44 {#v1-1-44}

* **ACSD-56790** （Adobe CommerceおよびMagento Open Source >=2.4.6 &lt;2.4.7 の場合） – 「**在庫切れまで下に移動**」オプションを使用してカテゴリ商品を並べ替えると、ユーザーが管理ダッシュボードにリダイレクトされ、`Invalid security or form key. Please refresh the page` エラーが画面の上部に表示される問題を修正しました。
* **ACSD-56280** （Adobe Commerce >=2.4.4 &lt;2.4.7 の場合） – ギフトレジストリから商品を注文すると例外が発生する問題を修正しました。
* **ACSD-56246** （Adobe CommerceおよびMagento Open Source >=2.4.6 &lt;2.4.7 の場合） – スケジュールされた商品のアップデートがアクティブになるとカスタムの複数選択属性からデータが削除される問題を修正しました。
* **ACSD-56193** （Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.4 の場合） – ページビルダーを使用してカテゴリの説明でスケジュール済みブロックを使用すると、Varnish/Fastly キャッシュが更新されない問題を修正しました。
* **ACSD-56158** （Adobe CommerceおよびMagento Open Source >=2.4.5 &lt;2.4.7 の場合） – 「買い物かご」クエリが各税務処理基準の合計税額を返す問題を修正しました。
* **ACSD-56023** （Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.7 の場合） – キャッシュが有効な場合にCMS ページでウィジェットコンテンツが更新されない問題を修正しました。
* **ACSD-55427** （Adobe Commerce >=2.4.5 &lt;2.4.7 の場合） – 管理者ユーザーが、管理者の商品ページの共有カタログから商品の割り当てを解除できない問題を修正しました。
* **ACSD-55352** （Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.7 の場合） – 顧客報酬ポイントを含む部分的なクレジットメモを作成した後、注文ステータスが「クローズ」に変わり、クレジットメモオプションが管理者の注文ページに表示されなくなる問題を修正しました。
* **ACSD-55231** （Adobe Commerce >=2.4.2 &lt;2.4.7 の場合） – クイックオーダー機能を使用して買い物かごに商品を追加できない問題を修正しました。
* **ACSD-54283** （Adobe Commerce >=2.4.3 &lt;2.4.4 の場合） – デフォルト（一般グループ）の Shared Catalog に割り当てられていない Products/Categories が、XML サイトマップに引き続き含まれる問題を修正しました。
* 更新されたパッチ：ACSD-52041、ACSD-54040、ACSD-51819

## v1.1.43 {#v1-1-43}

* **ACSD-54972** （Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.7 の場合） – カテゴリ URL を変更した後に正規カテゴリ URL が更新されない問題を修正しました。
* **ACSD-53636** （Adobe CommerceおよびMagento Open Source >=2.4.3 &lt;2.4.5 の場合） – 特別価格の子商品を持つ設定可能な商品の商品一覧ページに通常価格が表示されない問題を修正しました。
* **ACSD-54885** （Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.7 の場合） – 管理者ユーザーが *顧客としてログイン* 機能を使用している場合の、複数のアドレスのチェックアウトの問題を修正しました。
* **ACSD-55610** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.7） – 部分的にキャンセルされた注文の割引額が正しくない問題を修正しました。
* **ACSD-55334** （Adobe CommerceおよびMagento Open Source >=2.4.3 &lt;2.4.7） – GraphQL レスポンスの翻訳辞書を使用したラベルの翻訳を修正します。
* **ACSD-54739** （Adobe Commerce >=2.4.5 &lt;2.4.7 の場合） – 関連する商品ルールに商品の在庫ステータス条件が適用されない問題を修正しました。
* **ACSD-53925** （Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.7 の場合） - `catalog_product_price` dimensions-mode が *website* に設定されている場合に、管理者が製品カルーセルでCMS ブロックを保存できない問題を修正しました。
* **ACSD-52714** （Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.7 の場合） – 日付フォーマットが *Y-m-d* に設定されている場合に、管理グリッドで日付フィルターが機能しない問題を修正しました。
* **ACSD-55055** （Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.7） – ショッピングカートの買い物かご価格ルールに商品属性を読み込むパフォーマンスを向上しました。
* **ACSD-53790** （Adobe Commerce >=2.4.6 &lt;2.4.7 の場合） - REST API を使用して 1 つの商品に対して複数の RMA を作成できる問題を修正しました。
* **ACSD-56090** （Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.5 の場合） - GraphQL リクエストが、特別にリクエストされたストアデータではなく、すべてのストアのデータで応答する問題を修正しました。
* **ACSD-54983** （Adobe Commerce >=2.4.2 &lt;2.4.7 の場合） – ユーザーステータスが *[!UICONTROL Inactive]* に設定されている場合に、GraphQL リクエストで会社のユーザーUIDを取得できない問題を修正しました。
* **ACSD-53309** （Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.7 の場合） – カスタマイズ可能オプションが選択されている場合に、*[!UICONTROL Regular Price]* ラベルに税金が完全に適用されない問題を修正しました。
* **ACSD-55305** （Adobe Commerce >=2.4.4 &lt;2.4.7 の場合） – **[!UICONTROL myAccount]** > **[!UICONTROL Company Structure]** ページの *[!UICONTROL Edit Company User]* ポップアップが画面のローダーでフリーズする問題を修正しました。
* 更新されたパッチ：ACSD-49013

## v1.1.42 {#v1-1-42}

* **ACSD-53658** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.7 の場合） – ストアビューで商品データが適切 *[!UICONTROL Recently Viewed]* 更新されない問題を修正しました。
* **ACSD-54626** （Adobe Commerce >=2.4.6 &lt;2.4.7 の場合） - [!DNL GraphQL] を使用して `NUMBER_OF_SKUS` 属性を持つ新しい発注書ルール（`createPurchaseOrderApprovalRule`）を作成できない問題を修正しました。
* **ACSD-53845** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.7） – `consumer max_messages` = 0 の場合の [!DNL MySQL] connection timeout の問題を修正しました。
* **ACSD-54890** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.7 の場合） – ディスクの容量が不足しているために `aggregate_sales_report_bestsellers_data` が [!DNL MySQL] エラーを引き起こ `/tmp` 問題を修正しました。
* **ACSD-55112** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.7 の場合） - [!DNL Google reCAPTCHA v3] の検証を行わずに「*[!UICONTROL Submit review]*」ボタンを複数回クリックできる問題を修正しました。
* **ACSD-54264** （Adobe Commerce >=2.4.4-p5 &lt;2.4.5） || >=2.4.5-p4 &lt;2.4.6 || >=2.4.6-p2 &lt;2.4.7） – 「リクエストされた属性を更新できません *というエラーメッセージが表示される問題を修正しました。 行 ID:store_id&quot;* は、顧客が別のストアビューから交渉可能な見積もりでチェックアウトしようとすると表示されます。
* **ACSD-54418** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.7 の場合） – 動的に価格が設定されるバンドルの各子製品に誤って固定額の割引が適用される問題を修正しました。
* **ACSD-55238** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.7 の場合） – 空の商品 *[!UICONTROL Meta Description]* の保存を修正しました。
* **ACSD-54966** （Adobe CommerceおよびMagento Open Source >=2.4.5 &lt;2.4.7 の場合） – 前回の注文が失敗した場合に、お客様ごとの使用制限があるクーポンコードが再利用できない問題を修正しました。
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
* **ACSD-53118** （Adobe Commerce >=2.4.0 &lt;2.4.7 の場合） – 商品に空の属性があり、ルールが無効になっている可能性がある場合に、クーポンコードを使用して *[!UICONTROL Cart Price Rule]* が適用される問題を修正しました。
* **ACSD-54324** （Adobe Commerce >=2.4.5 &lt;2.4.7 の場合） - GraphQLの requisition_lists リクエストでページネーションの設定が考慮されず、すべての結果が返される問題を修正しました。
* 更新されたパッチ：MDVA-42855-v2

## v1.1.40 {#v1-1-40}

* **ACSD-54680** （Adobe Commerce >=2.4.0 &lt;2.4.6 の場合） – 複数のソースが割り当てられている商品に対して送信された B2B 見積もりを処理できない問題を修正しました。
* **ACSD-54040** （Adobe Commerce >=2.4.4-p5 &lt;2.4.5） || >=2.4.5-p4 &lt;2.4.6） - B2B モジュールが有効な場合に、順序の詳細で *[!UICONTROL Created]* フィールドが空白になる問題を修正しました。
* **ACSD-54319** （Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.6） – *[!UICONTROL Product in Cart]* レポートで製品価格がゼロと表示される問題を修正しました。
* **ACSD-53378** （Adobe CommerceおよびMagento Open Source >=2.4.5 &lt;2.4.7） – 大きなアドレス帳を持つお客様のチェックアウトページの読み込み時間を改善します。
* **ACSD-52657** （Adobe CommerceおよびMagento Open Source >=2.4.5 &lt;2.4.7 の場合） – サブドメインを使用するセカンダリストレビューでミニカートが更新されない問題を修正しました。
* **ACSD-53414** （Adobe Commerce >=2.4.6 &lt;2.4.7 の場合） – 制限付き管理者ユーザーが、権限適用範囲外でCMS ページを表示できる問題を修正しました。
* **ACSD-54472** （Adobe Commerce >=2.4.6 &lt;2.4.7 の場合） – 拒否された会社の顧客が認証を行い、ブロックされた会社と拒否された会社の顧客が注文を行える問題を修正しました。 このパッチは、GraphQL エンドポイントの検証をさらに強化します。
* **ACSD-52801** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.7 の場合） - GraphQLで商品を検索する際に部分一致を行うオプションを追加します。
* **ACSD-55004** （Adobe CommerceおよびMagento Open Source >=2.4.6 &lt;2.4.7 の場合） - `php.ini` で設定された値を超える読み込みファイルをアップロードする際にバリデーターがクラッシュする問題を修正しました。
* **ACSD-54989** （Adobe Commerce >=2.4.4-p5 &lt;2.4.5） || >=2.4.5-p4 &lt;2.4.6 || >=2.4.6-p2 &lt;2.4.7） - *[!UICONTROL Enable Purchase Orders]* が *[!UICONTROL Yes]* に設定され、*[!UICONTROL Purchase Order]* が *[!UICONTROL No]* に設定されている場合に、会社管理者が注文できない問題を修正しました。
* **ACSD-54007** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.7 の場合） – カスタマーデータの読み込み時のエラー *&quot;未定義の配列キー&quot;_scope&quot;* を修正しました。
* **ACSD-55031** （Adobe CommerceおよびMagento Open Source >=2.4.5 &lt;2.4.6 の場合） – コンパイル中に *Type &quot;mixed&quot;を nullable にすることはできません* エラーが修正されました。
* **ACSD-54961** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.7 の場合） – 制限付き管理者ユーザーが *製品レビュー* ステータスを一括更新できない問題を修正しました。
* **ACSD-55256** （Adobe CommerceおよびMagento Open Source >=2.4.6 &lt;2.4.7 の場合） – 最初の画像のみが画像スライダーに正常に表示される問題を修正しました。
* 更新されたパッチ：ACSD-52041、ACSD-54106

## v1.1.39 {#v1-1-39}

* **ACSD-53704** （Adobe Commerce >=2.4.0 &lt;2.4.7 の場合） – 報酬ポイントの有効期限が切れた後に、報酬ポイントのバランス履歴が誤って計算される問題を修正しました。
* **ACSD-53583** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.7） – *Category Products* および *Product Categories* インデクサーの部分的なインデックス再作成のパフォーマンスを向上します。
* **ACSD-54026** （Adobe Commerce >=2.4.6 &lt;2.4.7 の場合） – 許可されていないユーザーに対する `updateCompanyRole` GraphQL リクエストで発生する誤ったエラーメッセージを修正します。
* **ACSD-54106** （Adobe CommerceおよびMagento Open Source >=2.4.1 &lt;2.4.5 の場合） – トルコ語のアクセント記号用にカテゴリ商品を名前で並べ替えると問題が発生する問題を修正しました。
* **ACSD-52219** （Adobe CommerceおよびMagento Open Source >=2.4.5 &lt;2.4.7 の場合） – ブックマークビューを頻繁に切り替えると、保存された管理グリッドのフィルターが期待どおりに動作しない問題を修正しました。
* **ACSD-54342** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.7 の場合） – 有効なデータのない CSV ファイルを読み込む際に、誤ったエラーメッセージ *データ構造のエラー：値が混在します* を修正しました。
* **ACSD-54660** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.6） - GraphQLのお客様の注文を `sort_field` と `sort_direction` で並べ替える新しい入力属性 *sort* が追加されました。
* **ACSD-54776** （Adobe Commerce >=2.4.5 &lt;2.4.7 の場合） - 2 つ目の web サイト、ストア、ストア表示で、オフの *[!UICONTROL Use Default Value]* フィールドとデフォルト以外の製品フィールドの値が保存されない問題を修正しました。
* **ACSD-53998** （Adobe CommerceおよびMagento Open Source >=2.4.4-p2 &lt;2.4.5 || >=2.4.5-p1 &lt;2.4.7） – カスタマーアカウントからログアウトした後、**[!UICONTROL Customer Segment]** に基づく **[!UICONTROL Dynamic Block]** が正しく機能しない問題を修正しました。
* **ACSD-53204** （Adobe CommerceおよびMagento Open Source >=2.4.6 &lt;2.4.7 の場合） – 修正点 *商品を保存できません。`rest/V1/products/<sku>/media` エンドポイントを使用して製品ギャラリーに画像を追加する同時リクエストを行う際に* エラーが発生します。
* **ACSD-47657** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.7） – AWS資格情報のキャッシングメカニズムが追加されました。 認証情報プロバイダーは、Magento キャッシュを使用して、AWSから取得した認証情報を EC2 設定用にキャッシュするようになりました。
* パッチを更新：ACSD-51984、ACSD-51574。

## v1.1.38 {#v1-1-38}

* **ACSD-53098** （Adobe CommerceおよびMagento Open Source >=2.4.3 &lt;2.4.4 の場合） – 部分的なインデックスの実行時に、共有カタログに割り当てられた商品がストアフロントに表示されない問題を修正しました。
* **ACSD-54018** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.4.6 の場合） – ウィジェットの条件で非グローバル属性を使用する [!UICONTROL Product List] ウィジェットのパフォーマンスの問題を修正します。
* **ACSD-54111** （Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.6 の場合） – 透かし画像の縦横比が商品画像と一致しない場合に、商品のサムネール画像がストアフロントに表示されない問題を修正しました。
* **ACSD-47669** （Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.6 の場合） – 修正点 *整合性制約違反：1452 子行を追加または更新できない：外部キー制約が失敗する* 商品の CSV を読み込む際にエラーが発生する。
* **ACSD-53347** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.4.7） – price indexer の実行に時間がかかりすぎる問題を修正しました。
* **ACSD-52287** （Adobe Commerce >=2.3.7 &lt;2.4.7 の場合） – 非同期グリッドインデックス作成が有効な場合に、アーカイブされたオーダーグリッドで誤ったオーダーステータスの問題を修正しました。
* **ACSD-52929** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.4.7 の場合） – インベントリインデクサーが非同期モードで設定されている場合に、デフォルトのソースアイテムを再インデックス化する冗長リクエストの問題を修正しました。
* **ACSD-53824** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.7 の場合） – `setup:upgrade` 行中に移行データパッチがデータベーストランザクションサイズの制限 `UpdateMultiselectAttributesBackendTypes` 超える問題を修正しました。

## v1.1.37 {#v1-1-37}

* **ACSD-52613** （Adobe CommerceおよびMagento Open Source >=2.4.6 &lt;2.4.7 の場合） - REST API によって `Inventory_source` の項目が更新されなくてもキャッシュとインデックスが更新される問題を修正しました。
* **ACSD-51884** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.4.7 の場合） - resize コマンドを実行すると、商品イメージのキャッシュパスが正しくなくなる問題を修正しました。
* **ACSD-53628** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.4.7 の場合） - CSV 販売注文レポートに間違った特殊文字が表示される問題を修正しました。
* **ACSD-53148** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.7 の場合） – 設定可能な同じ商品を買い物かごに追加するためにGraphQLで並行してリクエストをおこなった 2 つのリクエストの結果、同じ商品 SKU を持つ 2 つの異なる商品が買い物かごに入れられる問題を修正しました。
* **ACSD-52606** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.7 の場合） – 「注文を受け取る準備ができていません *というエラーメッセージがユーザーが&#x200B;**[!UICONTROL Notify Order is Ready for Pickup]**&#x200B;をクリックすると表示される問題を修正しました*。
* **ACSD-51574** （Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.7 の場合） – 同じ名前の別の画像に置き換えると、フロントエンドで画像が更新されない問題を修正しました。
* **ACSD-53728** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.4.7） – 製品の EAV インデクサーの実行に時間がかかる問題を修正しました。
* **ACSD-53979** （Adobe CommerceおよびMagento Open Source >=2.4.6 &lt;2.4.7 の場合） – ようこそメッセージに一重引用符が含まれている場合にホームページで発生する JS の問題を修正します。
* **ACSD-52085** （Adobe CommerceおよびMagento Open Source >=2.4.5 &lt;2.4.7 の場合） – 設定可能な特別価格の商品が商品のカルーセルに表示されない問題を修正しました。
* **ACSD-53795** （Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.7 の場合） - cron ジョブで無効なデータタイプに関する問題 `indexer_update_all_views` 修正しました。
* **ACSD-52143** （Adobe CommerceおよびMagento Open Source >=2.4.6 &lt;2.4.7 の場合） – 商品の読み込み後にカスタムオプションが削除される問題を修正しました。
* **ACSD-53750** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.7 の場合） – マルチスレッド `catalog_product_price` の再インデックス中に発生した *パイプの破損または接続の切断* エラーを修正します。
* **ACSD-49843** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.4.0 || >=2.4.1 &lt;2.4.7） -**[!UICONTROL Payment Action]** = **[!UICONTROL Sale]** 設定が有効になっているオンライン支払い方法で注文品目の自動請求が行われた後、製品のダウンロードのリンクが使用できなくなる問題を修正しました。
* **ACSD-47054** （Adobe Commerce >=2.4.2 &lt;2.4.6 の場合） – プレビューの再インデックスですべてのストアに対して再インデックスを実行すると、速度が低下する問題を修正しました。
* ACSD-46541、ACSD-47079 の新しいバージョンを追加しました。
* ACSD-49970-v3 は ACSD-54095 に置き換えられました。

## v1.1.36 {#v1-1-36}

* **ACSD-53239** （Adobe CommerceおよびMagento Open Source >=2.4.3 &lt; 2.4.6 の場合） – インベントリインデクサーがスケジュールに従って更新モードですべてのキャッシュをクリーンアップする問題を修正しました。
* **ACSD-50887** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.7 の場合） – product 属性のプロパティ *[!UICONTROL Use in Search Results Layered Navigation]* を *はい* に設定でき、*[!UICONTROL Use in search]* オプションを *はい* に設定できない問題を修正しました。
* **ACSD-51846** （Adobe CommerceおよびMagento Open Source >=2.4.3-p2 &lt;2.4.6） – REST API ペイロードの一部のレベルが検証されないために発生する *内部エラー* 問題を修正しました。
* **ACSD-52906** （Adobe Commerce >=2.3.7 &lt;2.4.7 の場合） – 同じカスタマーセグメントに属するログインした顧客が一部のページで不適切なキャッシュを発生させ、X-Magento-Vary cookie が正しく設定されない問題を修正しました。
* **ACSD-52736** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.4.6 の場合） – 設定可能な製品数量の要件を含む *買い物かご価格ルール* が期待どおりに動作しない問題を修正しました。
* **ACSD-47875** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.4.7） – 在庫管理で、管理者ユーザーが特定のストア表示範囲で管理者から商品を買い物かごに追加できない問題を修正しました。
* **ACSD-53176** （Adobe Commerce >=2.3.7 &lt;2.4.5 の場合） – *が* の *関連商品ルール* 条件が商品に一致しない問題を修正しました。
* **ACSD-51666** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.4.7 の場合） – エラーを修正しました *セッションの有効期限が切れました。もう一度ログインしてください。これは、ユーザーがログインを試みた後で* 生します。
* MDVA-39305-v2 の新しいバージョンを追加しました。
* ACSD-19640 の要件を更新しました。

## v1.1.35 {#v1-1-35}

* **ACSD-51899** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.7 の場合） – チェックアウト発送手順のデフォルトの発送先住所が、以前に選択した店舗内の集荷先住所で自動入力される問題を修正しました。
* **ACSD-52041** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.7 の場合） – ロックを解除せずに 5 秒間レンダリングされ [!DNL Page Builder] エラーメッセージ「*[ERROR]」の問題を修正しました。* で編集したコンテンツを保存すると、Chrome ブラウザーに [!DNL Page Builder] が表示されます。
* **ACSD-52095** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.4.6 の場合） – 商品の書き出し後に CSV ファイルで `manage_stock` 値が正しく 0 に設定されない問題を修正しました。
* **ACSD-51358** （Adobe Commerce >=2.4.5 &lt;2.4.7 の場合） – 終了日を指定せずにスケジュール済み更新を削除すると、同じエンティティの他のスケジュール済み更新が削除される問題を修正しました。
* **ACSD-48070** （Adobe Commerce >=2.3.7 &lt;2.4.7 の場合） – スケジュールされた更新を編集すると例外がトリガーされる問題を修正しました。
* **ACSD-51890** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.7 の場合） - v3 の検証を行わずに「[!UICONTROL Submit review]」ボタンを複数回クリックできる問題 [!DNL Google reCAPTCHA] 修正しました。
* **ACSD-51984** （Adobe Commerce >=2.4.5 &lt;2.4.7 の場合） - 2 番目の web サイト、ストア、ストアビューで、オフの *[!UICONTROL Use Default Value]* と *[!UICONTROL non-default product field]* の値が保存されない問題を修正しました。
* **ACSD-52398** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.7 の場合） – ストアフロントで買い物かごにバンドルされた商品の数量を更新しようとすると発生するエラー *リクエストされた数量は使用できません* を修正しました。
* **ACSD-52786** （Adobe CommerceおよびMagento Open Source >=2.4.5 &lt;2.4.6 の場合） – カタログルールの条件 *SKU* が、特定の SKU で始まるすべての商品に適用される問題を修正しました。
* **ACSD-52921** （Adobe CommerceおよびMagento Open Source >=2.4.5 &lt;2.4.7 の場合） – カートに在庫切れの設定可能な商品がある場合に、GraphQLからカートの詳細をリクエストすると内部エラーが発生する問題を修正しました。
* **ACSD-51683** （Adobe CommerceおよびMagento Open Source >=2.4.6 &lt;2.4.7） – GraphQLを使用してカスタマイズ可能なオプションを買い物かごに追加できない問題を修正しました。
* **ACSD-52133** （Adobe CommerceおよびMagento Open Source >=2.4.6 &lt;2.4.7 の場合） – アップグレード後にカスタマーアカウントを保存できない問題を修正しました。
* **ACSD-52202** （Adobe CommerceおよびMagento Open Source >=2.4.3 &lt;2.4.7） – 注文のフルフィルメント時にデフォルト以外の在庫が 0 数量に変更された場合に、デフォルト在庫の販売可能数量が誤って 0 に変わる問題を修正しました。
* **ACSD-51265** （Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.7 の場合） – システム内にバンドルされた製品が多すぎる場合のインデックス再作成のパフォーマンスの問題を修正しまし `catalog_product_price`。
* **ACSD-52831** （Adobe Commerce >=2.3.7 &lt;2.4.7 の場合） – [!DNL Google reCAPTCHA v3 Invisible] が有効な場合に、お客様が交渉可能な見積書を注文できない問題を修正しました。
* **ACSD-51845** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.7） – 階層価格と異なる属性セットを持つ後続の製品を非同期の一括 REST API で更新できない問題を修正しました。
* **ACSD-52815** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.4.7 の場合） – デフォルト以外のソースの数量フィールドの入力が、デフォルトの在庫の 8 桁とは異なり、最大 6 桁しかサポートしない問題を修正しました。
* **ACSD-51149** （Adobe Commerce >=2.3.7 &lt;2.4.7 の場合） – カタログアクセス権を有効にしたスケジュール済みインポートエクスポートによってインデクサーが無効になり、Cron によるキャッシュフラッシュが発生する問題を修正しました。
* **ACSD-50815** （Adobe CommerceおよびMagento Open Source >=2.4.5 &lt;2.4.6） – 新しいバンドル商品オプションで、シンプルな商品の 10 進数の数量を使用できない問題を修正しました。
* ACSD-47803 のバージョンを更新しました。
* ACSD-51892 のタイトルを更新しました。
* ACSD-51379 を更新しました。
* ACSD-49970-v2 を更新しました。

## v1.1.34 {#v1-1-34}

* **ACSD-52277** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.7 の場合） – 管理者で新しい注文を作成する際にストア表示を選択した後、管理者ユーザーが適切にリダイレクトされない問題を修正しました。
* **ACSD-50813** （Adobe Commerce >=2.4.5 &lt;2.4.7 の場合） – 管理者が、[!UICONTROL Add Products by SKU] 機能を持つ SKU にスラッシュを含むバンドル製品を管理注文に追加できなかった問題を修正しました。
* **ACSD-51630** （Adobe CommerceおよびMagento Open Source >=2.4.3 &lt;2.4.7） – 大量のシステムメッセージが原因で管理ページのダウンロードが遅くなる問題を修正しました。
* **ACSD-51853** （Adobe CommerceおよびMagento Open Source >=2.4.1 &lt;2.4.7 の場合） – [!UICONTROL Page Builder] を使用した際に、コピーされたテキストスタイルが適用されない問題を修正しました。
* **ACSD-52160** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.7 の場合） – 「If an item is FOUND/NOT FOUND in the cart with All/Any these conditions true」というルール条件に基づいて、買い物かご価格ルールに対する商品検証結果が適切に評価されなかった問題を修正しました。
* **ACSD-51636** （Adobe Commerce >=2.4.5 &lt;2.4.7 の場合） – 必要な役割と権限がすべて揃っているにもかかわらず、会社管理者がカスタマーアカウントセクションから新しいユーザーを追加できない問題を修正しました。
* **ACSD-51739** （Adobe Commerce >=2.4.6 &lt;2.4.7 の場合） - CompanyTeam GraphQL リクエストで `structure_id` がリクエストされた場合にエラーが返される問題を修正しました。
* **ACSD-51857** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.7 の場合） – 大規模な sales_order および `sales_order_item` 個のデータベーステーブルに関する `aggregate_sales_report_bestsellers_data` cron レポートのパフォーマンスが遅い原因が、メインデータクエリの記述方法にあった問題を修正しました。
* **ACSD-48448** （Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.7 の場合） – 注文のキャンセル中に競合状態の問題が発生し、`inventory_reservation` テーブルのエントリが重複する問題を修正しました。
* **ACSD-52689** （Adobe CommerceおよびMagento Open Source >=2.4.3 &lt;2.4.6） – REST API を使用してAmazon S3 ストレージに画像をアップロードできない問題を修正しました。
* **B2B-2674** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.7） – 1customAttributeMetadata1 GraphQL クエリにキャッシュ機能を追加します。
* ACSD-44938 の新しいバージョンを追加しました。
* ACSD-46988 の要件を追加しました。

## v1.1.33 {#v1-1-33}

* **ACSD-50478** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.5 の場合） - DB ダンプにトリガーと *区切り文字* SQL コマンドが含まれている場合にデータベースのロールバックコマンドを修正します。
* **ACSD-50512** （Adobe Commerce >=2.4.5 &lt;2.4.7 の場合） – *エラー：ダウンロード可能なリンクは商品に関連していません。 リンクを確認して、もう一度試してください。ダウンロ* ド可能な製品のステージング更新の開始日を更新する際に発生するエラー。
* **ACSD-50949** （Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.7 の場合） - SKU フィルターと共に使用した場合に、詳細検索で価格フィルターが適切な結果を返さない問題を修正しました。
* **ACSD-51645** （Adobe CommerceおよびMagento Open Source >=2.4.6 &lt;2.4.7 の場合） – 拡張機能 `Magento_OfflineShipping` が無効になっている場合に、新しい買い物かご価格ルールを保存する際にスローされるエラーを修正しました。
* **ACSD-50895** （Adobe Commerce >=2.4.5 &lt;2.4.7 の場合） - [!DNL Google Analytics] 4 GTM が設定されていない場合に [!DNL Google Analytics] 3 GTM タグが実行されない問題を修正しました。
* **ACSD-51102** （Adobe Commerce >=2.4.2 &lt;2.4.7 の場合） – 予定されている更新によってルールが有効になっている場合に、多数の商品に適用されるカタログルールが正しくインデックス化されない問題を修正しました。
* **ACSD-50368** （Adobe CommerceおよびMagento Open Source >= 2.4.3 &lt;2.4.5 の場合） – 非同期 REST API または非同期バルク REST API を使用してカスタマーを作成する際にカスタマーの `group_id` が無視される問題を修正しました。
* **ACSD-51497** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.4.0 || >= 2.4.1 &lt;2.4.7） – 顧客がドロップダウンタイプのカスタム属性でカタログページを並べ替えることができない問題を修正しました。
* **ACSD-51408** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt; 2.4.7 の場合） – 注文項目のステータスが正しく *[!UICONTROL Backordered]* に設定されない問題を修正しました。
* **ACSD-51735** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.5 の場合） – 商品の在庫が *0 の場合に、注文商品のステータスが正しく&#x200B;*[!UICONTROL Ordered]*&#x200B;に設定されない問題を修正しました*。
* **ACSD-51792** （Adobe CommerceおよびMagento Open Source >=2.4.5 &lt;2.4.6 の場合） - [!DNL Google Tag Manager] 4 が有効になっているときに、ページにインプレッションイベントが発生しない問題を修正しました。
* **ACSD-51471** （Adobe Commerce >=2.4.3 &lt;2.4.7 の場合） – 自身にスケジュール済みアップデートがあるシンプルな製品を使用しているバンドル製品の場合、管理者ユーザーがスケジュール済みアップデートを保存できない問題を修正しました。
* **ACSD-51700** （Adobe CommerceおよびMagento Open Source >=2.4.3 &lt;2.4.7 の場合） – 管理者でダウンロード可能な商品編集ページでストアビューを切り替えると発生するエラーを修正しました。
* **ACSD-51120** （Adobe Commerce >=2.3.7 &lt;2.4.3 の場合） – ステージングアップデートにより更新されたGraphQL ブロックを含んだCMS ページに対して、CMS GET リクエストのキャッシュがクリアされない問題を修正しました。
* **ACSD-51240** （Adobe Commerce >=2.4.4 &lt;2.4.6 の場合） – 会社登録フォームから登録した場合に、アップロードしたファイルが見つからない問題を修正しました。
* **ACSD-51907** （Adobe Commerce >=2.4.2 &lt;2.4.3 の場合） – 制限付き管理者ユーザーが、オフラインでの返金を含むクレジットメモを作成できない問題を修正しました。
* **ACSD-52148** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.4 の場合） – [!DNL Google V3 reCAPTCHA] Admin のログインが時々失敗する問題を修正しました。
* **ACSD-51431** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.4.7 の場合） - changelog に新しいエントリがない場合でも、インデクサーのステータスが *動作* する問題を修正しました。
* **ACSD-51892** （Adobe CommerceおよびMagento Open Source >=2.4.6 &lt;2.4.7 の場合） – config ファイルが複数回読み込まれるパフォーマンスの問題を修正しました。
* 非推奨（廃止予定）の ACSD-51114。

## v1.1.32 {#v1-1-32}

* **ACSD-49628** （Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.7 の場合） -[!UICONTROL Page Builder's] 数のエラーが原因で、管理者がコンテンツ権限のない商品を保存できない問題を修正しました。
* **ACSD-51305** （Adobe CommerceおよびMagento Open Source >=2.4.6 &lt;2.4.7 の場合） - GraphQL レスポンスで在庫切れの設定可能な子商品が使用できない問題を修正しました。
* **ACSD-50621** （Adobe Commerce >=2.3.7 &lt;2.4.7 の場合） – マルチサイト環境で編集しようとすると、共有カタログ内の様々な web サイトの [!UICONTROL Tier Prices] が表示されない問題を修正しました。
* **ACSD-51041** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.4.0 || >=2.4.1 &lt;2.4.6） – 価格インデクサーのパフォーマンスを向上させます。
* **ACSD-51379** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.4.7 の場合） – [!UICONTROL Page Builder] を使用してページテキストコンテンツに加えられた変更が保存されない問題を修正しました。
* **ACSD-49480** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.6 の場合） – カートに適用されるカート価格ルールが 1 つだけの問題を修正しました。
* **ACSD-51230** （Adobe Commerce >=2.3.7 &lt;2.4.7 の場合） – 簡単な商品の一部の返金が注文から処理されると、ギフトカードアカウントが削除される問題を修正しました。
* **ACSD-51238** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.7） – 設定可能な商品を更新して価格を編集すると、在庫ソースが削除される問題を修正しました。
* **ACSD-50794** （Adobe Commerce >=2.4.1 &lt;2.4.7 の場合） - GraphQLから削除すると、ギフトメッセージやギフトラッピングの詳細がデータベースで更新されない問題を修正しました。
* **ACSD-51528** （Adobe CommerceおよびMagento Open Source >=2.4.5 &lt;2.4.7 の場合） - *x_forwarded_for* 列の *sales_order* テーブルに null 値が含まれる問題を修正しました。
* **ACSD-50849** （Adobe Commerce >=2.4.4 &lt;2.4.6 の場合） – キャッシュをクリアした後に新しい商品をカテゴリに追加すると、既存の商品の位置と選択内容が一致しなくなる問題を修正しました。
* **ACSD-51294** （Adobe CommerceおよびMagento Open Source >=2.4.5 &lt;2.4.7 の場合） - GTM/GA の価格、数量、税、送料、売上高が文字列として [!DNL Google Analytics] と GTM に送信される問題を修正しました。
* **ACSD-51204** （Adobe CommerceおよびMagento Open Source >=2.4.3 &lt;2.4.7 の場合） – クレジットメモを作成した後、完全に売れた商品が在庫に戻らない問題を修正しました。
* **ACSD-51291** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.4-p4 || >=2.4.5 &lt;2.4.5-p3） - 1 つの web サイトへのアクセスを制限された管理者が、複数の web サイトに割り当てられた製品に画像/ビデオを追加できる問題を修正しました。
* ACSD-50336 の新しいバージョンを追加しました。
* パッチ ACSD-49970 を交換してください。

## v1.1.31 {#v1-1-31}

* **ACSD-50345** （Adobe CommerceおよびMagento Open Source >=2.4.3 &lt;2.4.4 || >=2.4.4-p1 &lt;2.4.6） – 支払いに失敗した後、Recaptcha v2 がリロードされない問題を修正しました。
* **ACSD-50817** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.4.7） – Cron ジョブ `sales_clean_quotes` を最適化して、実行速度を向上させます。
* **ACSD-49392** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.4.0 || >= 2.4.1 &lt;2.4.7） – バンドルされた製品の部分払い戻しの後に注文ステータスがクローズに変更される問題を修正しました。
* **ACSD-51036** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.5 の場合） - REST API の同時呼び出し時の競合状態によって、[!UICONTROL Items Ordered] テーブルの配送ステータス情報が上書きされる問題を修正しました。
* **ACSD-50858** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.7） – バナーのコンテンツの読み込みパフォーマンスを向上しました。
* MDVA-39305-v2、ACSD-45169 の新しいバージョンを追加しました。
* パッチ ACSD-50260-v2 を更新しました。

## v1.1.30 {#v1-1-30}

* **ACSD-50336** （Adobe CommerceおよびMagento Open Source >=2.4.4-p1 &lt;2.4.4-p3） – 商品が再入荷したり、価格が変更されたりしたときに商品のアラートメールが送信されない問題を修正しました。
* **ACSD-50367** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.4.7 の場合） – 値のない複数選択の顧客アドレス属性が作成された場合に、顧客アドレスのエクスポートが機能しない問題を修正しました。
* **ACSD-49877** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.4.7 の場合） – ビデオがストリーミングサービスではなくリモートビデオファイルに直接リンクされている場合に、モバイル [!DNL Safari] でビデオの自動再生が機能しない問題を修正しました。
* **ACSD-50165** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.7 の場合） – エラーを修正しました *ファイルを削除できません。 警告！unlink：管理者から JS/CSS キャッシュをフラッシュする際に* そのようなファイルやディレクトリはありません。
* **ACSD-49737** （Adobe CommerceおよびMagento Open Source >=2.4.1-p1 &lt;2.4.7） – カードの支払いに失敗した後、クーポンが誤って使用されているとマークされる問題を修正しました。
* **ACSD-50814** （Adobe CommerceおよびMagento Open Source >=2.4.6 &lt;2.4.7 の場合） – 管理者ユーザーがクレジットメモを作成できない問題を修正しました。
* **ACSD-50116** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.4.7 の場合） – 管理者ユーザーがサブカテゴリレベル 3 以下の URL の書き換えを作成できない問題を修正しました。
* **ACSD-49513** （Adobe CommerceおよびMagento Open Source >=2.4.3 &lt;2.4.5 の場合） - 0 バイトのファイルが原因でリモートストレージの同期が失敗する問題を修正しました。
* **ACSD-46683** （Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.7） – 配送料が *まだ計算されていません* と表示される問題を修正しました。
* **ACSD-49129** （Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.6 の場合） - product media API 応答で *[!UICONTROL content]* 属性（base64 image code）が返されない問題 `rest/V1/products/sku/media` 修正しました。
* **ACSD-50276** （Adobe Commerce >=2.4.0 &lt;2.4.7 の場合） – 複数選択の顧客属性が作成された場合に、ストアフロントで顧客登録フォームが機能しない問題を修正しました。
* **ACSD-50527** （Adobe Commerce >=2.3.7 &lt;2.4.7 の場合） – 空のダイナミックブロックを含んだページを保存したときに発生するエラーを修正しました。
* **ACSD-49973** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.5） - GraphQLを通じてバンドルされた製品を取得する際のパフォーマンスを向上させます。
* **ACSD-51114** （Adobe CommerceおよびMagento Open Source >=2.4.3 &lt;2.4.7 の場合） – 非同期インデックス作成が有効になっている場合に、大きなカタログからランダムな商品が消える問題を修正しました。 大規模なカタログの非同期インデックス再作成のパフォーマンスを向上します。
* **B2B-2598** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.7） – [!UICONTROL availableStores]、[!UICONTROL countries]、[!UICONTROL country]、[!UICONTROL currency] および [!UICONTROL storeConfig] GraphQLのクエリにキャッシュ機能を追加します。
* MDVA-42806、ACSD-48627、ACSD-46815 の新しいバージョンを追加しました。
* ACSD-49773、ACSD-47179、ACSD-48300 のパッチメタデータを更新しました。

## v1.1.29 {#v1-1-29}

* **ACSD-49389** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.7 の場合） – 注文の受け取りの準備が整っていない場合に、API によって受け取り可能なメールが送信される問題を修正しました。
* **ACSD-49822** （Adobe Commerce >=2.3.7 &lt;2.4.7 の場合） – [!UICONTROL Requisition List] ページの更新が [!UICONTROL Print Requisition List] に反映されない問題を修正しました。
* **ACSD-48771** （Adobe CommerceおよびMagento Open Source >=2.4.5 &lt;2.4.7 の場合） – 列ブロックコンテンツタイプを旧バージョンからアップグレードする際の問題を修正し [!DNL Page Builder] した。
* **ACSD-49464** （Adobe Commerce >=2.3.7 &lt;2.4.7 の場合） - orderId が異なる場合に、請求書、出荷、クレジットメモがアーカイブから戻されない問題を修正しました。
* **ACSD-49773** （Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.6 の場合） - AWS S3 をリモートストレージとして使用した場合に製品の書き出しが失敗する問題を修正しました。
* **ACSD-49748** （Adobe Commerce >=2.3.7 &lt;2.4.7 の場合） – 招待状を送信できない問題を修正しました。
* **ACSD-49502** （Adobe Commerce >=2.4.3 &lt;2.4.7 の場合） – ダウンロード可能な製品にステージングアップデートを適用した後、ダウンロード可能なリンクが適切に更新されない問題を修正しました。
* **ACSD-49527** （Adobe Commerce >=2.4.2 &lt;2.4.7 の場合） - GraphQLの会社ロールでページネーションが正しく表示されない問題を修正しました。
* **ACSD-49706** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.4.7 の場合） – 値が選択されていない場合に、ビジュアルスウォッチ属性に対してデフォルト値が保存される問題を修正しました。
* **ACSD-49835** （Adobe CommerceおよびMagento Open Source >=2.4.5 &lt;2.4.7 の場合） – 複数選択属性のストアレベルで「デフォルトを使用」チェックボックスの値が正しく保存されない問題を修正しました。
* **ACSD-49898** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.6 の場合） – バンドルされた商品の特別価格が 1000 を超える場合に、商品グリッドが例外をスローする問題を修正しました。
* **ACSD-50234** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.4.5 の場合） - [!DNL PayPal] で注文する場合に、確認メールに間違ったお客様の名前が表示される問題を修正しました。
* **ACSD-49960** （Adobe CommerceおよびMagento Open Source >=2.4.5 &lt;2.4.7 の場合） – 顧客注文グリッドで日付によるフィルタリングが機能しない問題を修正しました。
* **ACSD-49849** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.4.6） – GraphQL経由で [!DNL PayPal Express] に注文する際に、お客様のメールが [!DNL PayPal] のメールに置き換えられる問題を修正しました。
* **ACSD-49839** （Adobe Commerce >=2.3.7 &lt;2.4.7 の場合） – 製品の SKU に一重引用符または二重引用符が含まれている場合、管理で共有カタログの価格と構造がエラーをスローする問題を修正しました。
* **ACSD-49970** （Adobe CommerceおよびMagento Open Source >=2.4.5 &lt;2.4.7 の場合） - [!DNL New Relic] レポートが有効になっている場合のGraphQL エラーの誤った処理を修正しました。
* **ACSD-50260** （Adobe CommerceおよびMagento Open Source >=2.4.5 &lt;2.4.7 の場合） - GraphQL製品の検索結果が 10,000 件のみに制限される問題を修正しました。
* **ACSD-48813** （Adobe CommerceおよびMagento Open Source >=2.4.3 &lt;2.4.7 の場合） – 属性の検索重み付けに基づいて検索で関連する結果が表示されない問題を修正しました。

## v1.1.28 {#v1-1-28}

* **ACSD-48204** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.4.3 の場合） – Yes/No 属性に基づいて作成されたカタログ価格ルールが選択した範囲を考慮しない問題を修正しました。
* **ACSD-47704** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.4.7 の場合） – バンドル商品に在庫商品のみの価格が表示される問題を修正しました。
* **ACSD-49370** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.4.7 の場合） - GraphQL スキーマで *日時* 製品属性に *FilterMatchTypeInput* タイプが含まれる問題を修正しました。
* **ACSD-48807** （Adobe CommerceおよびMagento Open Source >=2.4.1 &lt;2.4.7） - GraphQLを使用してカスタマープロダクトレビューが storereview でフィルタリングされない問題を修正しました。
* **ACSD-49433** （Adobe CommerceおよびMagento Open Source >=2.4.3 &lt;2.4.7 の場合） – オープン金額を含むギフトカードのデフォルト金額がカートに小計として表示される問題を修正しました。
* **ACSD-48866** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.4.7） – カテゴリの RSS フィードをリクエストするとエラーが発生する問題を修正しました。
* **ACSD-48784** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.4.7 の場合） – 顧客セグメント価格が顧客グループ間で誤ってキャッシュされる問題を修正しました。
* **ACSD-48857** （Adobe CommerceおよびMagento Open Source >=2.4.3 &lt;2.4.7 の場合） – ページビルダーで編集した後、ユーザーが変更を保存できない問題を修正しました。
* **ACSD-49065** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.4.7 の場合） – カスタム在庫にのみ割り当てられている場合に、管理者に見積もり項目が表示されない問題を修正しました。
* **ACSD-49179** （Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.7） – 店舗ごとに異なる通貨の場合に注文レポートに誤った金額が表示される問題を修正しました。
* **ACSD-49286** （Adobe CommerceおよびMagento Open Source >=2.4.3 &lt;2.4.7 の場合） – ページに複数の商品ウィジェットが存在する場合に、買い物かごに商品が 2 回追加される問題を修正しました。
* **ACSD-49574** （Adobe Commerce >=2.4.4 &lt;2.4.7 用） - GraphQLを使用して、買い物かごでのギフトカード製品のアップデートをサポートする機能を追加しました。
* パッチを更新しました：ACSD-48694。

## v1.1.27 {#v1-1-27}

* **ACSD-48362** （Adobe Commerce >=2.4.1 &lt;2.4.7 の場合） – ネゴシエート可能な見積もりを使用して注文を行う際に、新しい配送先住所の代わりにデフォルトの配送先住所が使用される問題を修正しました。
* **ACSD-48059** （Adobe Commerce >=2.3.7 &lt;2.4.7 の場合） – マーチャントがカテゴリの「[!UICONTROL Match product by rule]」を保存できない問題を修正しました。
* **ACSD-48216** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.3.8 || >=2.4.0 &lt;2.4.7） - [!UICONTROL UPDATE] 操作で [!UICONTROL inventory_source_item] テーブルの [!UICONTROL AUTO_INCREMENT] が増加する問題を修正しました。
* **ACSD-47908** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.3.8 || >=2.4.0 &lt;2.4.7） – チェックアウト時の出荷手順でソースと数量を選択する際に、「0 以下の値が想定されます」というエラーを修正しました。
* **ACSD-49497** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.4.6） – 発送後に注文が処理中のままになり、一部返金が適用される問題を修正しました。
* **ACSD-48694** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.3.8 || >=2.4.1 &lt;2.4.7） – 「無効な状態変更がリクエストされました」というエラーによって、お客様の注文が妨げられる問題を修正しました。
* **ACSD-49013** （Adobe CommerceおよびMagento Open Source >=2.4.3 &lt;2.4.7 の場合） – 一括 API を使用して顧客を作成する際に、メールの確認が web サイトのロケールに翻訳されない問題を修正しました。
* **ACSD-48164** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.4.7 の場合） – 制限付き管理者が web サイトレベルの値を保存できない問題を修正しました。
* **ACSD-48404** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.4 の場合） – ブラウザーの「戻る」ボタンを押すと、「カテゴリのページネーションを保存」でエラーが発生する問題を修正しました。
* **ACSD-48634** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.4.7 の場合） – 「[!UICONTROL Google Analytics Content Experiments]」が有効になっている場合に、ステージング更新ページで発生する JS エラーを修正しました。
* **ACSD-49042** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.5 の場合） – 順不同の商品をストアフロントから注文できない問題を修正しました。
* パッチを更新：ACSD-48366、ACSD-48661。

## v1.1.26 {#v1-1-26}

* **ACSD-47937** （Adobe CommerceおよびMagento Open Source 2.4.4 用） || >=2.4.5 &lt;2.4.6） – アプリケーションレベルのキャッシュが原因で価格下落通知が常に送信されない問題を修正しました。
* **ACSD-48661** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.4.7 の場合） – 会社のクレジット制限が 999 を超える場合、コンマ区切り記号が、検証エラーによる会社の保存を防ぐ問題を修正しました。
* **ACSD-48773** （Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.7 の場合） – 報酬ポイントのメールテンプレートが間違ったストアから取得される問題を修正しました。
* **ACSD-48587** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.4.7 の場合） – 商品ウィジェットのマッチングルールのHTML特殊文字によって、一致する商品が表示されない問題を修正しました。
* **ACSD-48212** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.4.6 の場合） – 商品の読み込みによって商品が誤ったソースに割り当てられる問題を修正しました。
* **ACSD-47988** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.4.6 の場合） – 製品の書き出しで、ページビルダーの製品説明からHTML タグがトリミングされる問題を修正しました。
* **ACSD-48366** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.6 の場合） – ストックに戻るメールテンプレートに商品イメージが表示されない問題を修正しました。
* **ACSD-48417** （Adobe CommerceおよびMagento Open Source >=2.4.5 &lt;2.4.7 の場合） – 商品のスケジュールを変更して別の商品を保存した後に SQL エラーが表示される問題を修正しました。

## v1.1.25 {#v1-1-25}

* **ACSD-48058** （Adobe CommerceおよびMagento Open Source >=2.4.5 &lt;2.4.6 の場合） – バンドル商品が Web サイトに割り当てられていない場合に、商品の価格インデックス再作成が機能しない問題を修正しました。
* **ACSD-48262** （Adobe CommerceおよびMagento Open Source >=2.4.5 &lt;2.4.6 の場合） – 「1 ページあたりの全製品を許可」設定が「はい」に設定されている場合に、フロントエンドに製品が表示されない問題を修正しました。
* **ACSD-48293** （Adobe CommerceおよびMagento Open Source >=2.4.3 &lt;2.4.4 の場合） – 完売した子商品が在庫に戻されると複合商品が在庫切れになる問題を修正しました。
* **ACSD-47520** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.6 の場合） – クレジットメモを作成したときに顧客が報酬ポイントを失う問題を修正しました。
* **ACSD-48044** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.4 の場合） – 複数送料の 1 回の注文に複数のギフトカードを適用すると、注文できなくなる問題を修正しました。
* **ACSD-48300** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.6 の場合） – 設定可能な商品が削除された場合に戻り値を作成できない問題を修正しました。
* **ACSD-47910** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.6 の場合） – それぞれのエンティティグリッドで、注文、請求書、出荷、およびクレジットメモが見つからない問題を修正します。
* **ACSD-47292** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.6 の場合） – 「在庫切れの商品を表示」が「はい」に設定されている場合に、GraphQL レスポンスで在庫切れのバンドル商品が使用できない問題を修正しました。
* **ACSD-48234** （Adobe CommerceおよびMagento Open Source >=2.4.5 &lt;2.4.6 の場合） – 「在庫切れを表示」オプションが有効になっている場合に、カタログ検索結果に誤ったカテゴリ項目数が表示される問題を修正しました。
* **ACSD-48313** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.5 の場合） – 属性値にコンマが含まれている場合、「configurable_variations」列が解析されない問題を修正しました。 「additional_attributes」にも同じ解析アルゴリズムを使用します。
* **ACSD-48627** （Adobe CommerceおよびMagento Open Source >=2.4.5 &lt;2.4.6 の場合） – 在庫切れの設定可能な商品が、GraphQL リクエストを送信して買い物かごの詳細を取得する際にエラーを発生させる問題を修正しました。
* パッチを更新しました：MDVA-39384。

## v1.1.24 {#v1-1-24}

* **ACSD-45168** （Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.6 の場合） – ストアビューレベルで上書きされた *url_key* 属性を持つ商品に対して、SEO に対応する URL が生成されない問題を修正しました。
* **ACSD-46865** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.6 の場合） – 非同期インデックス作成が有効な場合に、出荷およびクレジットメモグリッドが入力されない問題を修正しました。
* **ACSD-47004** （Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.6） – VAT ID のない請求先住所に VAT が適用されない問題を修正しました。
* **ACSD-47803** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.6 の場合） – 在庫切れの設定可能な商品スウォッチが利用可能と表示される問題を修正しました。
* **ACSD-47137** （Adobe CommerceおよびMagento Open Sourceの場合 >=2.4.4 &lt;2.4.6） - pub/media フォルダーが非常に大きい場合に、画像ギャラリーの読み込み速度を向上させます。
* **ACSD-46770** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.6 の場合） – *メールでの注文確認* がオフになっている場合でも管理者の注文メールが送信される問題を修正しました。
* **ACSD-47955** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.6 の場合） - GraphQLで買い物かごの割引が正しく表示されない問題を修正しました。
* **ACSD-46617** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.6 の場合） – 小計が設定された *最小注文額* よりも大きい場合でも「チェックアウトを続行 **」ボタンがグレー表示される問題を修正しました。
* **ACSD-47079** （Adobe CommerceおよびMagento Open Sourceの場合 >=2.4.4 &lt;2.4.5） - REST API POST /rest/V1/inventory/source-items を使用してサブプロダクトのストックステータスが変更された場合に、複合プロダクト（バンドル、グループ化、設定可能）のストックステータスが更新されない問題を修正しました。
* **ACSD-47336** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.6 の場合） – 修正点 *問題が発生しました。Commerce Admin で通知を無効にすると* エラーが発生する。
* **ACSD-47559** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.6 の場合） – メールテンプレートのプレビュー領域が完全には表示されない問題を修正しました。
* **ACSD-47920** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.6 の場合） - *Allow Guest Checkout* がオフになっている場合でも、Rest API を介してゲストユーザーとして注文できる問題を修正しました。
* 交換したパッチ：MDVA-39305、MDVA-42855。

## v1.1.23 {#v1-1-23}

* **ACSD-47179** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.6 の場合） – 特定の範囲へのアクセスが制限された管理者が商品レビューを削除できない問題を修正しました。
* **ACSD-47107** （Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.5 の場合） – カスタム商品オプションにカタログ価格ルール割引が適用される問題を修正しました。
* **ACSD-47232** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.6） – 合計重量条件のクーポンを管理者で適用できない問題を修正しました。
* **ACSD-46519** （Adobe CommerceおよびMagento Open Source >=2.4.1 &lt;2.4.6 の場合） - GraphQL categoryList リクエストがアンカカテゴリに対して誤った product_count を返す問題を修正しました。
* **ACSD-47027** （Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.6 の場合） – 低速の updateCompanyRole GraphQL リクエストを修正します。
* **ACSD-47666** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.6 の場合） – 管理者/ システム /権限/ ユーザーロール / ロール / ロールユーザーのグリッドでフィルター機能が機能しない問題を修正しました。
* **ACSD-47497** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.6 の場合） – 管理下の設定に「サービス」タブが表示されない問題を修正しました。
* パッチを更新しました：ACSD-47743。
* 交換したパッチ：MDVA-42807。

## v1.1.22 {#v1-1-22}

* **ACSD-47444** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.3 の場合） – PHP 7.4 で既知の商品の特定の非既存のカテゴリパスにアクセスする場合、_bool 型の値の配列オフセットへのアクセスを試みています_ エラーを修正しました。
* **ACSD-47332** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.6 の場合） - UTC で 00:00～00:59 の間に実行しているときにのみ報告されるエラーで cron が失敗する問題を修正しました。
* **ACSD-47280** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.6 の場合） – 特定の範囲で共有カタログ機能を無効にすると正しく機能しない問題を修正しました。
* **ACSD-47106** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.6 の場合） – 会社作成ページの新しいカスタム属性に値を保存できない問題を修正しました。
* パッチを更新しました：ACSD-45143。

## v1.1.21 {#v1-1-21}

* **ACSD-46809** （Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.6 の場合） – 多数の商品ソースを割り当てたときにエラーが発生する問題を修正しました。
* **ACSD-46856** （Adobe CommerceおよびMagento Open Sourceの場合 >=2.4.0 &lt;2.4.6） – システム /設定/インポート/詳細価格を選択して、パフォーマンスアップデート層の価格を改善します。
* **ACSD-46541** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.4 の場合） – 注文項目を削除すると、管理者ユーザーがクレジットメモを作成できない問題を修正しました。
* **ACSD-46581** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.6 の場合） – ショッピングカートで国を選択した後、推定税合計が更新されない問題を修正しました。
* **ACSD-46618** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.6 の場合） – ログインしたユーザーの商品リストウィジェットに誤ったキャッシュ価格が表示される問題を修正しました。
* **ACSD-46674** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.6 の場合） – 画像タイプのカスタムオプションが顧客のメールでHTMLとして表示される問題を修正しました。
* **ACSD-46988** （Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.6 の場合） - GraphQLの「通貨」 API リクエストがカスタム通貨に対して NULL 値を返す問題を修正しました。
* **ACSD-47076** （Adobe CommerceおよびMagento Open Source >=2.4.1 &lt;2.4.5） – ストアフロントで Vimeo のビデオを再生できない問題を修正しました。
* **ACSD-45071** （Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.4 の場合） – インポート時にデフォルトソースが商品に追加される問題を修正しました。
* **AC-3023** （Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.6）の場合 – DHL スキームを最新バージョン 10.0 に更新します。
* パッチを更新しました：MDVA-42584。
* 交換したパッチ：MDVA-36572、ACSD-45241。

## v1.1.20 {#v1-1-20}

* **ACSD-46520** （*Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.5* の場合） – ストアクレジットを使用して払い戻すと、ユーザーに間違った注文ステータスが表示される問題を修正しました。
* **ACSD-46703** （*Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.6* の場合） – カスタムオプションを商品の編集ページにドラッグ&amp;ドロップできない問題を修正しました。
* **ACSD-44851** （*Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.6* の場合） – サブカテゴリを持つカテゴリを開いたり展開したりできない問題を修正しました。
* **ACSD-46815** （*Adobe CommerceおよびMagento Open Source >=2.4.5 &lt;2.4.6* の場合） – カテゴリツリーリクエストが 20 個に制限されている問題を修正しました。
* **ACSD-45675** （*Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.6* の場合） – 商品の書き出しで *デフォルトストア表示* 範囲のカテゴリ名が使用される問題を修正しました。
* **ACSD-46869** （*Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.6* の場合） – 商品数量を変更しないと、買い物かご内の設定可能な商品が *PUT REST API* リクエストを介して更新されない問題を修正しました。
* **MDVA-42768-V2** （*Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.3* の場合） – *在庫切れを表示* が *はい* の場合に、設定可能な商品に通常の価格が *0* と表示される問題を修正しました。
* 更新されたパッチ：MDVA-44562、ACSD-46213、MDVA-41305、MDVA-38346、MDVA-13203。
* 非推奨パッチ：MDVA-42768。

## v1.1.19 {#v1-1-19}

* **ACSD-46213** （*Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.3* の場合） – カテゴリツリーリクエストが 20 個に制限されている問題を修正しました。
* **ACSD-45781** （*Adobe CommerceおよびMagento Open Source >=2.4.1 &lt;2.4.2* の場合） – モバイルでストアフロント検索フィールドが表示されない問題を修正しました。
* **ACSD-46192** （*Adobe CommerceおよびMagento Open Source >=2.3.6 &lt;2.4.5* の場合） - `async/bulk/V1/configurable-products/bySku/options` エンドポイントを使用した問題を修正しました。
* **ACSD-46404** （*Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.5* の場合） – 2.4.4 にアップグレードした後に管理者ユーザーがログインできない問題を修正しました。
* 更新されたパッチ：MDVA-41305、MDVA-38626、MDVA-38728、MDVA-41061-V4、MDVA-42269、MDVA-39305。

## v1.1.18 {#v1-1-18}

* **ACSD-45817** （*Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.4* の場合） – 特定のストアのGraphQL製品ミューテーションが、リクエストされたストアに割り当てられていないものを含め、設定可能なすべてのバリアントを返す問題を修正しました。
* **ACSD-46146** （*Adobe CommerceおよびMagento Open Source >=2.3.0 &lt;2.4.6* の場合） – 管理者から注文した後に 2 通の注文確認メールが送信される問題を修正しました。
* **ACSD-45255** （*Adobe Commerce >=2.4.3 &lt;2.4.6* の場合） – 制限付き管理者ユーザーの低在庫レポートページの例外を修正します。
* **ACSD-45488** （*Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.6* の場合） – 複数のソースを持つ設定可能な商品が在庫に自動的に返されない問題を修正しました。
* **ACSD-45754** （*Adobe CommerceおよびMagento Open Source >=2.3.1 &lt;2.4.6* の場合） – クーポンを買い物かごに適用した後に報酬ポイントが追加されない問題を修正しました。
* **ACSD-45849** （*Adobe Commerce >=2.4.3 &lt;2.4.4* の場合） – ステージングアップデートの適用後にビデオメタデータが失われる問題を修正しました。
* **ACSD-45257** （*Adobe CommerceおよびMagento Open Source >=2.3.4 &lt;2.4.4* の場合） - GraphQLで買い物かごの割引が正しく表示されない問題を修正しました。
* **ACSD-44938** （*Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.4* の場合） – ゲストユーザーのGraphQL リクエストで `VAT_ID` が適用されない問題を修正しました。
* パッチを更新しました：MDVA-43417。

## v1.1.17 {#v1-1-17}

* **ACSD-45241** （*Adobe CommerceおよびMagento Open Source >=2.3.5 &lt;2.4.4* の場合） – クレジットメモを作成した後に、バーチャル商品の在庫数が誤って計算される問題を修正しました。
* **ACSD-43887** （*Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.5* の場合） – 会社の発注書が有効になっている場合に、チェックアウト時の支払いページに間違った詳細が表示される問題を修正しました。
* **ACSD-45143** （*Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.5* の場合） – `setShippingAddressesOnCart` ミューテーションで数値地域コードを *region* に設定できない問題を修正しました。
* **ACSD-44591** （*Adobe CommerceおよびMagento Open Source >=2.4.3 &lt;2.4.6* の場合） – CAPTCHA の確認が行われないまま注文した場合に発生するエラーを修正します。
* **ACSD-45520** （*Adobe CommerceおよびMagento Open Source >=2.3.0 &lt;2.4.6* の場合） – ユーザーが買い物かごから設定可能な商品を編集したときに、商品の詳細ページでスウォッチオプションが事前に選択されていない問題を修正しました。
* **ACSD-45169** （*Adobe CommerceおよびMagento Open Source >=2.4.1 &lt;2.4.6* の場合） – ステージングアップデートの適用後に、設定可能な商品の正しい在庫と価格が [!DNL Visual Merchandiser] に表示されない問題を修正しました。
* **ACSD-45424** （*Adobe CommerceおよびMagento Open Source >=2.3.4 &lt;2.4.6* の場合） – 一部払い戻し（クレジットメモ）の後で、誤った予約報酬が作成される問題を修正しました。
* **MDVA-42807** （*Adobe CommerceおよびMagento Open Source >=2.3.1 &lt;2.4.6* の場合） – ストアフロントにカスタムの通貨記号が表示されない問題を修正しました。
* パッチを更新しました：MDVA-42689、AC-3022。

## v1.1.16 {#v1-1-16}

* **MDVA-44703** （*Adobe CommerceおよびMagento Open Source >=2.4.3 &lt;2.4.4* の場合） – 制限付き管理者ユーザーに対して注文レポートの注文合計が誤って計算される問題を修正しました。
* **MDVA-44940** （*Adobe CommerceおよびMagento Open Source >=2.4.3 &lt;2.4.4* の場合） – カテゴリを管理者から保存する際に発生した SQL エラーを修正します。
* **MDVA-44562** （*Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.2-p2* の場合） – デフォルト以外のストアビューから発生したGraphQL リクエストにもかかわらず、見積書品目のデフォルト以外のストア ID がデフォルトのストア ID で上書きされる問題を修正しました。
* **MDVA-43167** （*Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.4*） – 管理者ユーザーがすべての注文を選択したときに、複数ページの注文グリッドの一括アクションが適用されない問題を修正しました。
* **MDVA-44044** （*Adobe CommerceおよびMagento Open Source >=2.3.0 &lt;2.4.2-p2* の場合） – 新しい web サイトに割り当てられた後、商品がカテゴリページに表示されない問題を修正しました。
* **MDVA-42509** （*Adobe CommerceおよびMagento Open Source >=2.3.3 &lt;2.4.4* の場合） – クイックオーダーに対して CSV をアップロードできず、「*Cookie を送信できません* というエラーが発生する問題を修正しました。
* パッチを更新：MDVA-41061、MDVA-42584。
* 新しい [!DNL Quality Patches Tool] パッチのプレフィクスは、内部プロセスの変更により *MDVA* から *ACSD* に変更されます。

## v1.1.15 {#v1-1-15}

* **MDVA-40961** （*Adobe CommerceおよびMagento Open Source >=2.4.3 &lt;2.4.4* の場合） – 商品の最小数量が既にカートに含まれている場合に、その商品をカートに追加できない問題を修正しました。
* **MDVA-44887** （*Adobe CommerceおよびMagento Open Source >=2.4.4 &lt;2.4.5* の場合） – *Uncaught SyntaxError：管理パネルの予期しないトークン「const」* エラーを修正します。
* **MDVA-43718** （*Adobe CommerceおよびMagento Open Source >=2.3.0 &lt;2.4.5* の場合） – 修正点 *コンシューマーは %resources へのアクセスを許可されていません。カ* タム統合から共有カタログにアクセスすると表示されるエラー。
* **MDVA-44660** （*Adobe CommerceおよびMagento Open Source >=2.4.2-p1 &lt;2.4.5*） – 顧客の姓と名にアクセント ``` ` ``` を使用できなかった問題を修正しました。
* **MDVA-40896** （*Adobe CommerceおよびMagento Open Source >=2.4.3 &lt;2.4.4* の場合） – *Error: TypeError：引数 3 がMagentoに渡される* というエラーを非同期製品バルク API で修正しました。
* **MDVA-38559** （*Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.3* の場合） – 複数のサブスクリプションを使用しているお客様の場合、*/V1/customers/search API* エラーを修正しました。
* **MDVA-44533** （*Adobe CommerceおよびMagento Open Source >=2.3.1 &lt;2.4.4* の場合） – バンドルの子商品に誤って割引が適用される問題を修正しました。
* パッチを更新：MDVA-41061、MDVA-42269。

## v1.1.14 {#v1-1-14}

* **MDVA-43983** （*Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.5* の場合） – カタログの詳細検索結果に商品が *個別に表示されない* と表示される問題を修正しました。
* **MDVA-44100** （*Adobe CommerceおよびMagento Open Source >=2.4.3 &lt;2.4.5* の場合） – すべての FPT が買い物かごの最後の商品に割り当てられ、他の商品でリセットされる問題を修正しました。
* **MDVA-43605** （*Adobe CommerceおよびMagento Open Source >=2.3.1 &lt;2.4.5* の場合） – Rest API を使用する際に、注文データが行合計に対して負の値を返す問題を修正しました。
* **MDVA-43102** （*Adobe CommerceおよびMagento Open Source >=2.3.1 &lt;2.4.5* の場合） - REST API を使用して払い戻しを行うと、売り上げ可能な数量が正しく更新されない問題を修正しました。
* **MDVA-43178** （*Adobe CommerceおよびMagento Open Sourceの場合 >=2.4.3-p2 &lt;2.4.5*） - GraphQLでカスタムストアのカスタムトークンを取得できない問題を修正しました。
* **MDVA-43859** （*Adobe CommerceおよびMagento Open Source >=2.4.1 &lt;2.4.5* の場合） – 削除されたユーザーがログインしようとすると、エラー *No such entity with customerId =* がログに記録される問題を修正しました。
* **MDVA-44147** （*Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.5* の場合） – GraphQL リクエストが購買依頼リストを返さない問題を修正しました。
* **MDVA-44505** （*Adobe CommerceおよびMagento Open Source >=2.4.1 &lt;2.4.3* の場合） - GraphQLへの報酬ポイントの適用で総計が更新されない問題と、注文処理中に店舗クレジットが複数回適用される問題を修正しました。
* 更新されたパッチ：MDVA-29148、MDVA-36464-V5、MDVA-42584、MDVA-39993-V2。

## v1.1.13 {#v1-1-13}

* **MDVA-42969** （*Adobe CommerceおよびMagento Open Source >=2.4.1 &lt;2.4.3* の場合） – 「顧客セグメント」が「*すべて*」に設定されている場合にのみ、関連商品ルールが機能する問題を修正しました。
* **MDVA-39605** （*Adobe CommerceおよびMagento Open Source >=2.3.4 &lt;2.4.5* の場合） – Redis キャッシュ TTL （有効期限）の値が間違っている問題を修正しました。
* **MDVA-43862** （*Adobe CommerceおよびMagento Open Source >=2.3.3 &lt;2.4.5* の場合） - GraphQL *UpdateCartItems ミューテーション* エラーが原因で顧客が買い物かごの商品を更新できない問題を修正しました。
* **MDVA-43824** （*Adobe CommerceおよびMagento Open Source >=2.3.6 &lt;=2.3.7-p3 || >=2.4.1 &lt;2.4.5*） – 割引が適用された注文のキャンセル時にエラーが表示される問題を修正しました。
* **MDVA-43451** （*Adobe CommerceおよびMagento Open Source >=2.4.3 &lt;2.4.5* の場合） – エラー *リクエストされたストアが見つからなかった問題を修正しました。 ストアを確認して、もう一度試してください。特定の web サイトの共有カタログを設定している間に* が表示されます。
* **MDVA-43491** （*Adobe CommerceおよびMagento Open Source >=2.3.5 &lt;2.4.5* の場合） – マルチストア web サイトの商品を読み込む際にベース画像のラベルが更新されない問題を修正しました。
* **MDVA-43601** （*Adobe CommerceおよびMagento Open Source >=2.3.0 &lt;2.4.5* の場合） – フル再インデックス後にトリガーが見つからない問題を修正しました。
* **MDVA-42046** （*Adobe CommerceおよびMagento Open Source >=2.3.4 &lt;=2.3.5-p2 || >=2.4.0 &lt;2.4.5*） – 製品の更新中に、日付入力フィールドを持つ製品属性に間違った値が割り当てられる問題を修正しました。
* **MDVA-43935** （*Adobe CommerceおよびMagento Open Source >=2.4.1 &lt;2.4.5* の場合） – アップセル商品が 2 回表示される問題を修正しました。
* **MDVA-44188** （*Adobe CommerceおよびMagento Open Source >=2.4.3 &lt;2.4.5* の場合） – アドレスに `.-` が含まれるシステム発行メールが送信されない問題を修正しました。
* **MDVA-42283** （*Adobe CommerceおよびMagento Open Source >=2.3.0 &lt;2.4.5* の場合） – フランス語ロケールの管理注文グリッドの日時形式が無効な問題を修正しました。
* 更新されたパッチ：MDVA-41061-V2、MDVA-36309、MDVA-30862、MDVA-39713。
* [!DNL Site-Wide Analysis Tool] のパッチメタデータを追加しました。

## v1.1.12 {#v1-1-12}

* **MDVA-39713** （*Adobe CommerceおよびMagento Open Source >=2.3.0 &lt;2.3.6* の場合） – スケジュールされたアクティブな更新の開始時刻が編集可能な問題を修正しました。
* **MDVA-42410** （*Adobe CommerceおよびMagento Open Source >=2.3.0 &lt;2.4.5* の場合） – クーポンレポートにデフォルトの基本通貨のみが表示される問題を修正しました。
* **MDVA-41136** （*Adobe CommerceおよびMagento Open Source >=2.3.0 &lt;2.4.5* の場合） - `mage-cache-sessid` ータの有効期限が延長されず、カスタマーデータクリーンアップが発生する問題を修正しました。
* **MDVA-39993** （*Adobe CommerceおよびMagento Open Source >=2.3.5 &lt;=2.3.7-p2 || >=2.4.0 &lt;2.4.4*） - API を使用して行ったインベントリの変更が、フロントエンドの製品ページに反映されない問題を修正しました。
* **MDVA-42855** （*Adobe CommerceおよびMagento Open Source >=2.4.3 &lt;2.4.5* の場合） – チェックアウト時に新しいお客様の住所がアドレス帳に保存されない問題を修正しました。
* **MDVA-42645** （*Adobe CommerceおよびMagento Open Source >=2.4.3 &lt;2.4.5* の場合） – ストアクレジット機能が無効になっている場合に、管理者が報酬ポイントを返金できない問題を修正しました。
* **MDVA-43414** （*Adobe CommerceおよびMagento Open Source >=2.3.6 &lt;=2.3.7-p2* の場合） – `inventory.reservations.updateSalabilityStatus` キューコンシューマーを数値 SKU で実行している際に発生する PHP の致命的エラーを修正します。
* **MDVA-41628** （*Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.5* の場合） – 新しいモジュールが追加されると、既存の制限付き管理者ユーザーが新しいリソースにアクセスできる問題を修正しました。
* **MDVA-43348** （*Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.5* の場合） – *uid* が含まれているとギフトカードのGraphQL リクエストでエラーが表示され `gift_card_options` 問題を修正しました。
* **MDVA-39546** （*Adobe CommerceおよびMagento Open Source >=2.3.0 &lt;2.4.5* の場合） – ステージング更新の開始日を編集中の現在の日付より前の日付に設定できてしまう問題を修正しました。
* **MDVA-42950** （*Adobe CommerceおよびMagento Open Source >=2.3.0 &lt;2.4.5* の場合） – 製品ページでビデオが再生されない問題を修正しました。
* **MDVA-42689** （*Adobe CommerceおよびMagento Open Source >=2.3.0 &lt;2.4.4* の場合） – インポート中に商品カテゴリを更新するとAdobe Commerceが *整合性制約違反* エラーをスローする問題を修正しました。
* **MDVA-41229** （*Adobe CommerceおよびMagento Open Source >=2.3.0 &lt;2.4.5* の場合） – 設定可能な商品の読み込み後、バックエンドで使用可能な画像がフロントエンドに表示されない問題を修正しました。
* **MDVA-43731** （*Adobe CommerceおよびMagento Open Source >=2.4.3 &lt;2.4.4* の場合） – *一致する最小用語* に値が追加されると、*検索シノニム* が機能しなくなる問題を修正しました。
* **MDVA-43232** （*Adobe CommerceおよびMagento Open Source >=2.3.4 &lt;2.4.5* の場合） – [!DNL Visual Merchandiser] の商品を特別価格で下/上に並べ替えると、カテゴリの保存中にエラーが発生する問題を修正しました。
* **MDVA-43726** （*Adobe CommerceおよびMagento Open Source >=2.3.3 &lt;2.4.3* の場合） – ストアレベル属性の一致に基づくカタログ価格ルールが部分的な再インデックス後に適用されない問題を修正しました。
* パッチを更新：MDVA-36464、MDVA-37478、MDVA-38608。
* [!DNL Site-Wide Analysis Tool] のパッチメタデータを追加しました。

## v1.1.11 {#v1-1-11}

* **MDVA-42790** （*Adobe CommerceおよびMagento Open Source >=2.4.3 &lt;2.4.5* の場合） - REST API を使用して特定の web サイトの製品価格属性を更新できない問題を修正しました。
* **MDVA-41350** （*Adobe CommerceおよびMagento Open Source >=2.3.0 &lt;2.4.5* の場合） – アクセスが制限されている管理者ユーザーが、SKU によって役割範囲外の商品を注文で追加すると例外がスローされる問題を修正しました。
* **MDVA-42269** （*Adobe CommerceおよびMagento Open Source >=2.4.3-p1 &lt;2.4.5* の場合） – *TypeError:strtotime （）のパラメーター 1 が文字列（null が指定された* エラーであるため、管理者ユーザーが管理者にログインできない問題を修正しました。
* **MDVA-40830** （*Adobe CommerceおよびMagento Open Source >=2.3.0 &lt;2.4.5* の場合） – 注文処理中にストアクレジットが複数回適用される問題を修正しました。
* **MDVA-42237** （*Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.5* の場合） – サブプロダクト価格が変更された後に、設定可能なプロダクトスペシャル価格が更新されない問題を修正しました。
* **MDVA-42520** （*Adobe CommerceおよびMagento Open Source >=2.4.3 &lt;2.4.4*） – *クロスボーダー取引を有効にする* を使用すると税率が 2 回適用される問題を修正しました。
* 更新されたパッチ：MDVA-27239、MDVA-39305、MDVA-41236、MDVA-36832。
* 非推奨パッチ：MDVA-37725。

## v1.1.10 {#v1-1-10}

* **MDVA-38728** （*Adobe CommerceおよびMagento Open Source >=2.3.2 &lt;2.4.5* の場合） – 一括属性の更新によって *商品の表示* を変更した後にのみデフォルトストアの URL 書き換えが作成される問題を修正しました。
* **MDVA-43091** （*Adobe CommerceおよびMagento Open Source >=2.4.3 &lt;2.4.4* の場合） – バックエンドで管理者からバンドル商品を注文するとエラーが発生する問題を修正しました *この商品に 10 進数の数量を使用できません*。
* **MDVA-40816** （*Adobe CommerceおよびMagento Open Source >=2.3.0 &lt;2.4.5* の場合） – 関連する商品ルールで、ルール条件で定義されていないカテゴリの商品が表示される問題を修正しました。
* **MDVA-41305** （*Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.5* の場合） - GraphQL mutation がウィッシュリストに追加された後に設定可能な商品オプションを返さない問題を修正しました。
* **MDVA-39181** （*Adobe CommerceおよびMagento Open Source >=2.4.1 &lt;2.4.5* の場合） – 関連する商品ルールで、ルール条件で定義されていないカテゴリの商品が表示される問題を修正しました。
* **MDVA-42584** （*Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.3* の場合） – インポートまたは API を使用して数量と在庫ステータスを変更した後、バックエンドの設定可能な在庫ステータスが更新されない問題を修正しました。
* **MDVA-40175** （*Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.3* の場合） – *クリックして発送方法を変更* しても、並べ替え中に管理者に発送方法を選択するラジオボタンが表示されない問題を修正しました。
* **MDVA-42768** （*Adobe CommerceおよびMagento Open Source >=2.3.4 &lt;2.4.5* の場合） – *在庫切れを表示* がはい」の場合に、設定可能な商品に通常価格が 0 と表示される問題を修正しました。
* **MDVA-43201** （*Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.4* の場合） – 特定のロケールで DOB 属性を使用した場合に、カスタマーログインでエラーが発生する問題を修正しました。
* パッチを更新：MDVA-35092、MDVA-33970。

## v1.1.9 {#v1-1-9}

* **MDVA-38346** （*Adobe CommerceおよびMagento Open Source >=2.3.0 &lt;2.4.5* の場合） - Adobe Commerceのタイムゾーンがローカル環境のタイムゾーンと異なる場合に、日付フィルターが正しく機能しない問題を修正しました。
* **MDVA-42657** （*Adobe CommerceおよびMagento Open Source >=2.4.1 &lt;2.4.5* の場合） – 管理者ユーザーがカスタマーセグメント条件でカテゴリを選択できない問題を修正しました。
* **MDVA-42806** （*Adobe CommerceおよびMagento Open Sourceの場合 >=2.4.2 &lt;2.4.4*） – REST API を使用して既存の会社が更新されるたびに *新しい会社登録* メールが送信される問題を修正しました。
* **MDVA-37984** （*Adobe CommerceおよびMagento Open Source >=2.4.1 &lt;2.4.5* の場合） – [!DNL Visual Merchandiser] *ルールに基づいて商品を一致* 機能で、ステージングアップデートを含む商品が正しくフィルタリングされない問題を修正しました。
* **MDVA-40488** （*Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.4*） – 在庫切れの子商品を含む設定可能な商品が正しい価格範囲で表示されない問題を修正しました。
* **MDVA-42507** （*Adobe CommerceおよびMagento Open Source >=2.4.3 &lt;2.4.5* の場合） – カート ルールのステージング更新を適用した後に、フルページのキャッシュがクリーンアップされる問題を修正しました。
* **MDVA-39163** （*Adobe CommerceおよびMagento Open Source >=2.3.5 &lt;2.4.5* の場合） – 新しいユーザーが登録され、買い物かごに入っている商品がゲストセッションから移動した場合に配送方法が使用できない問題を修正しました。
* **MDVA-38626** （*Adobe CommerceおよびMagento Open Source >=2.3.3 &lt;2.4.5* の場合） – 管理者ユーザーが [!DNL PayPal Payflow Pro] の支払いを使用してバックエンドで注文できない問題を修正しました。
* **MDVA-38666** （*Adobe CommerceおよびMagento Open Source >=2.3.2 &lt;2.3.6* の場合） – 管理者ユーザーが顧客の買い物かごで設定可能な商品オプションを変更できない問題を修正しました。
* **MDVA-38526** （*Adobe CommerceおよびMagento Open Source >=2.4.1 &lt;2.4.4* の場合） – 管理者ユーザーが [!DNL Site-Wide Analysis tool] にアクセスできない問題を修正しました。
* パッチを更新しました：MDVA-40101。

## v1.1.8 {#v1-1-8}

* **MDVA-41215** （*Adobe CommerceおよびMagento Open Source >=2.3.0 &lt;2.4.4* の場合） – *mage-messages* cookie が既に存在するが、新しいメッセージがない場合、その設定後に 500 エラーが発生する問題を修正しました。
* **MDVA-41139** （*Adobe CommerceおよびMagento Open Source >=2.4.3 &lt;2.4.4* の場合） – 製品のインポート後に、そのソースの 1 つに対して単純な製品の数量が 0 の場合に、設定可能な製品が在庫切れになる問題を修正しました。
* **MDVA-42326** （*Adobe CommerceおよびMagento Open Source >=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*） – 永続買い物かごが有効になっている場合でも、セッションタイムアウト後に顧客がチェックアウト時にエラーが発生する問題を修正しました。
* **MDVA-42341** （*Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.4* の場合） – リクエストにストアヘッダーがある場合に `categoryList` GraphQL クエリで結果がフィルタリングされない問題を修正しました。
* **MDVA-38393** （*Adobe CommerceおよびMagento Open Source >=2.3.0 &lt;2.4.4* の場合） – 単純な商品の名前が変更された場合に、設定可能な商品に対してカタログルールが機能しなくなる問題を修正しました。
* **MDVA-39153** （*Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.4* の場合） – 管理者での並べ替え中に割引額が正しく計算されない問題を修正しました。
* パッチを更新：MDVA-28993、MDVA-41061、MDVA-35984。

## v1.1.7 {#v1-1-7}

* **MDVA-39711** （*Adobe CommerceおよびMagento Open Source >=2.3.0 &lt;2.4.3* の場合） – 管理者ユーザーが web サイトを削除した後に顧客のグリッドにアクセスできない問題を修正しました。
* **MDVA-40311** （*Adobe CommerceおよびMagento Open Source >=2.4.2-p2 &lt;2.4.4*） – 管理者ユーザーに「無効なセキュリティまたはフォームキー *というエラーメッセージが表示される問題を修正しました。 カスタム管理パスが設定され* 秘密鍵が有効な場合は、管理者にログインした後、ページを更新してください。
* **MDVA-41631** （*Adobe CommerceおよびMagento Open Source >=2.4.1 &lt;2.4.4* の場合） – GraphQLでオプションの *電話* 値を指定せずに注文情報を取得しようとするとエラーが発生する問題を修正しました。
* **MDVA-27239** （*Adobe CommerceおよびMagento Open Source >=2.3.0 &lt;2.3.6* の場合） – クロスセル商品が表示されない問題を修正しました。
* 更新されたパッチ：MDVA-37068、MDVA-35254、MDVA-41164、MDVA-37916、MDVA-37478、MDVA-34551、MDVA-31791。

## v1.1.6 {#v1-1-6}

* **MDVA-40550** （*Adobe CommerceおよびMagento Open Source >=2.3.5 &lt;2.4.4* の場合） – インデックス再作成中にフロントエンドで製品が見つからない問題を修正しました。
* **MDVA-40120** （*Adobe CommerceおよびMagento Open Source >=2.4.1 &lt;2.4.4*） – GraphQLを DESC/ASC で並べ替えても、同じ関連度や価格の商品で機能しない問題を修正しました。
* **MDVA-41399** （*Adobe CommerceおよびMagento Open Source >=2.3.3 &lt;2.4.2* の場合） – お客様がウィッシュリストに商品を追加した場合に、管理者ユーザーが *買い物かごの管理* ページにアクセスできない問題を修正しました。
* **MDVA-40609** （*Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.3* の場合） – 無効な商品データが `cataloginventory_stock_status` インデックステーブルに存在せず、無効な商品の数量が表示される問題を修正しました。
* **MDVA-39031** （*Adobe CommerceおよびMagento Open Source >=2.4.1 &lt;2.4.4* の場合） – ターゲットの web サイトに割り当てられていない場合でも、GraphQLを介して買い物かごに商品を追加することが可能な問題を修正しました。
* **MDVA-41597** （*Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.4* の場合） – GraphQLを使用して複数の設定可能な商品を買い物かごに追加すると、エラーが発生する問題を修正しました。
* **MDVA-27456** （*Adobe CommerceおよびMagento Open Source >=2.3.5 &lt;2.3.7* の場合） – [!DNL Swagger] を読み込もうとするとエラーが発生する問題を修正しました。
* **MDVA-32776** （*Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.2* の場合） – 注文しても出荷されなかった場合に在庫ステータスが更新されない問題を修正しました。
* **MDVA-30862** （*Adobe CommerceおよびMagento Open Source >=2.3.4 &lt;2.4.0* の場合） – 印刷されたPDF請求書に間違った注文日がある問題を修正します。
* [!DNL Quality Patch Tool] のインデックスページを改善しました。 ツールの最新バージョンで、[!DNL quality patches] の便利な検索とフィルタリングを追加しました。
* パッチを更新：MDVA-33382、MDVA-39482。

## v1.1.5 {#v1-1-5}

* **MDVA-41236** （*Adobe CommerceおよびMagento Open Source >=2.3.0 &lt;2.4.4* の場合） – 終了日が以前に削除されている場合に、商品の新しいスケジュール済みアップデートを作成したり、既存のスケジュール済みアップデートを編集したりできない問題を修正しました。
* **MDVA-41046** （*Adobe CommerceおよびMagento Open Source >=2.3.0 &lt;2.4.4* の場合） – カスタムオプションを使用したシンプルな商品を、設定可能な商品やグループ化された商品に割り当てることができる問題を修正しました。
* **MDVA-40545** （*Adobe CommerceおよびMagento Open Source >=2.3.0 &lt;2.4.4* の場合） – 同じページに複数のノードがある場合でも、ページの最初のノードのみが取得される問題を修正しました。
* **MDVA-41164** （*Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.3-p1* の場合） – 管理者ユーザーが、ファイルまたは画像タイプのカスタム顧客属性を持つ会社を保存または編集できない問題を修正しました。
* **MDVA-39229** （*Adobe CommerceおよびMagento Open Source >=2.3.0 &lt;2.4.4* の場合） – カタログルールのステージングの更新開始時刻を更新すると次のエラーが表示される問題を修正しました。*Cron Job staging_synchronize_entities_period にエラーがあります。アクティブな更新を削除できません。*
* **MDVA-40619** （*Adobe CommerceおよびMagento Open Source >=2.3.0 &lt;2.4.4* の場合） – CMS ページでインライン編集を試みると、CMS ページの階層を変更すると 500 エラーが発生する問題を修正しました。
* **MDVA-41061** （*Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.3* の場合） – 管理者から商品を保存すると在庫ステータスがリセットされて販売可能になる問題を修正しました。
* **MDVA-31763** （*Adobe CommerceおよびMagento Open Source >=2.3.0 &lt;2.4.4* の場合） – 手動でインデックスを再作成するまでカタログ価格ルールが元に戻される（または適用されない）問題を修正しました。
* **MDVA-37748** （*Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.3* の場合） - GraphQL クエリが、共有カタログに割り当てられていない商品を返す問題を修正しました。

## v1.1.4 {#v1-1-4}

* **MDVA-40399** （*Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.4*） – REST API を使用して同じ注文の部分的な請求書を同時に作成できない問題を修正しました。
* **MDVA-40101** （*Adobe CommerceおよびMagento Open Source >=2.3.2 &lt;2.4.0* の場合） - [!DNL PayPal Express] チェックアウトを使用して注文が成功した後、ミニカートから商品が削除されない問題を修正しました。
* **MDVA-40401** （*Adobe CommerceおよびMagento Open Source >=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*） – 注文が失敗してもクーポンの使用値が変更される問題を修正しました。
* **MDVA-40537** （*Adobe CommerceおよびMagento Open Source >=2.3.4 &lt;=2.4.0-p1* の場合） – 同じ URL キーを持つ複数のCMS ページが存在する場合に、ストアビューを作成するとエラーが発生する問題を修正しました。
* **MDVA-37725** （*Adobe CommerceおよびMagento Open Source >=2.3.0 &lt;=2.4.3-p1* の場合） – デフォルト以外の web サイトから送信された非同期注文メールにデフォルトの web サイトのロゴ URL が含まれる問題を修正しました。
* **MDVA-39482** （*Adobe CommerceおよびMagento Open Source >=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*） – バックオーダーが有効な場合に、「0」の数量で読み込むと製品の在庫が切れる問題を修正しました。
* **MDVA-40435** （*Adobe CommerceおよびMagento Open Source >=2.3.4 &lt;2.4.4* の場合） - GraphQL経由で適用した場合に、動的価格のバンドル商品が誤って割引される問題を修正しました。
* **MC-42528** （*Adobe CommerceおよびMagento Open Source >=2.4.3 &lt;=2.4.3-p1* の場合） - `categoryList` GraphQL クエリで、割り当て済みカテゴリと未割り当てカテゴリの両方が返される問題を修正しました。
* **MDVA-29400** （*Adobe CommerceおよびMagento Open Sourceの場合 >=2.3.0 &lt;=2.3.7-p1 || >=2.4.0 &lt;=2.4.0-p1*） - [!DNL PayPal Express Checkout] で行われた重複した注文の問題を修正しました。
* **MDVA-26005** （*Adobe CommerceおよびMagento Open Source >=2.3.4 &lt;=2.3.5-p2* の場合） – カート価格ルール条件のカテゴリツリーでカテゴリを選択できない問題を修正しました。
* **MDVA-25631** （*Adobe CommerceおよびMagento Open Source >=2.3.3 &lt;=2.3.5-p2* の場合） – 多数のユーザーを含むカスタマーセグメントの編集および保存のパフォーマンスを向上させます。

## v1.1.3 {#v1-1-3}

* **MDVA-40262** （*Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.4* の場合） – GraphQLの検索クエリが管理者の一般的な検索用語に表示されない問題を修正しました。
* **MDVA-40601** （*Adobe CommerceおよびMagento Open Source >=2.3.1 &lt;=2.4.2-p2* の場合） - GraphQLを使用して、スケジュールされたアップデートによって変更されたカテゴリに関する情報を取得しようとするとエラーが発生する問題を修正しました。
* **MDVA-37234** （*Adobe CommerceおよびMagento Open Source >=2.3.5 &lt;2.4.0 || >=2.4.1 &lt;=2.4.2-p2*） – 同じ SKU で買い物かごに項目を複数回追加（並列リクエスト）すると、同じ買い物かご ID に対して重複した行項目が作成される問題を修正しました。
* **MDVA-33606** （*Adobe CommerceおよびMagento Open Source >=2.4.1 &lt;=2.4.2-p2* の場合） – 階層に割り当てられたCMS ページを保存すると *ユニーク制約違反* エラーが発生する問題を修正しました。
* **MDVA-31590** （*Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;=2.4.1-p1* の場合） – ユーザーが MySQL 非同期キューを使用して属性を一括で更新できない問題を修正しました。
* **MDVA-36309** （*Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;=2.4.2-p2* の場合） – 管理グリッドで属性による商品検索が遅い問題を修正しました。

## v1.1.2 {#v1-1-2}

* **MDVA-38929** （*Adobe CommerceおよびMagento Open Source >=2.3.0 &lt;2.4.4* の場合） – ストアクレジットから注文が支払われた際に、FPT の請求書に間違った総計が表示される問題を修正しました。
* **MDVA-37364** （*Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;=2.4.3* の場合） – 日付タイプのカスタムカスタマー属性によってお客様のグリッド UI が機能しない問題を修正しました。
* **MDVA-39195** （*Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;=2.4.2-p2* の場合） – 「買い物かごにリダイレクト」が有効になっている場合に、カテゴリページで「*買い物かごに追加*」ボタンが非アクティブになる問題を修正しました。
* **MDVA-37115** （*Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;=2.4.2-p2* の場合） – 設定可能な商品ページに不要な *左側が 0 のみ* 通知が表示される問題を修正しました。
* **MDVA-39521** （*Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.4* の場合） – GraphQLを使用して、空の電話番号を含む配送先住所を買い物かごに入力できない問題を修正しました。
* **MDVA-39384** （*Adobe CommerceおよびMagento Open Source >=2.3.1 &lt;=2.3.6 || >=2.4.1 &lt;=2.4.3*） – 会社ユーザーのカスタム顧客属性が保存されない問題を修正しました。
* **MDVA-39043** （*Adobe CommerceおよびMagento Open Source >=2.3.4 &lt;=2.4.3* の場合） – アクセス制限のある管理者ユーザーが *Products* ウィジェットをCMS ページに追加しようとするとエラーが発生する問題を修正しました。
* **MDVA-39966** （*Adobe CommerceおよびMagento Open Sourceの場合 >=2.3.0 &lt;=2.3.5-p2 || >=2.4.0 &lt;=2.4.0-p1*） – 間違ったロケールをデプロイする際の問題を修正しました。
* **MDVA-38852** （*Adobe CommerceおよびMagento Open Source >=2.3.0 &lt;=2.3.5-p2* の場合） – 並列オーダーが複数ある場合にパフォーマンスが大幅に低下する更新のために、カタログ在庫が設計によってテーブルをロックする問題を修正しました。
* **MDVA-39986** （*Adobe CommerceおよびMagento Open Source >=2.4.1 &lt;2.4.3* の場合） – Safari ブラウザーを使用してMacOSの管理者に注文できない問題を修正しました。
* **MDVA-38447** （*Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.4* の場合） - *個別に表示されない* 設定可能な子商品がGraphQL レスポンスで返される場合と、カテゴリフィルターを使用してGraphQL商品クエリ用に MySQL クエリを最適化する場合の 2 つの問題を修正しました。
* **MDVA-40134** （*Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.3* の場合） – Shared Catalog が有効な場合に、GraphQLが関連商品を返さない問題を修正しました。
* **MDVA-39935** （*Adobe CommerceおよびMagento Open Source >=2.4.1 &lt;2.4.4* の場合） – GraphQLが web サイトレベルで無効になっている設定可能な子製品を返す問題を修正しました。

## v1.1.1 {#v1-1-1}

* **MDVA-36021** （*Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.4* の場合） – *メンバー関数 getId （）の呼び出し* エラーが、管理者の注文の詳細ページに表示される問題を修正しました。
* **MDVA-34948** （*Adobe CommerceおよびMagento Open Sourceの場合 >=2.3.6 &lt;=2.3.6-p1 || >=2.4.0 &lt;=2.4.0-p1*） - `GET_LOCK` のような長時間実行されるクエリの問題を修正しました。
* **MDVA-39305** （*Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;=2.4.2-p1* の場合） – 登録ユーザーが有効なGoogle ReCaptcha でログインできない問題を修正しました。
* **MDVA-37897** （*Adobe CommerceおよびMagento Open Source >=2.3.0 &lt;2.4.4* の場合） – 最近表示した項目ウィジェットからオプションを追加しようとすると、誤ったリダイレクトで問題が解決されます。

## v1.1.0 {#v1-1-0}

* ユーザーエクスペリエンスを向上させ、必要なパッチを顧客が簡単に検索できるように、パッチカテゴリが導入されました。
* `patches.json` ファイルの名前は `support-patches.json` に変更されました。
* **MDVA-38799** （*Adobe Commerce >=2.3.0 &lt;2.4.3* の場合） – ステージングアップデートの作成後にダウンロード可能な商品が保存されない問題を修正しました。
* **MDVA-37592** （*Adobe Commerce >=2.3.6 &lt;=2.4.2-p1* の場合） – 共有カタログに価格がゼロの商品を価格で並べ替えても正しく機能しない問題を修正しました。
* **MDVA-38827** （*Adobe Commerce >=2.3.3-p1 &lt;2.4.4*） – エラーメッセージを含む注文出荷メールがお客様に届く問題を修正しました。

## v1.0.26 {#v1-0-26}

* **MDVA-38468** （*Adobe Commerce >=2.3.2 &lt;=2.3.5-p2* の場合） – CMS ページを保存する際のエラーを修正しました。*同じ ID を持つ項目が既に存在します*。
* **MDVA-34680** （*Adobe Commerce >=2.3.6 &lt;=2.3.7 || >=2.4.1 &lt;2.4.3*） – 顧客グリッドで顧客アカウントの作成時間が正しくフィルタリングされない問題を修正しました。
* **MDVA-37068** （*Adobe Commerce >=2.3.1 &lt;2.4.4* の場合） – ショッピングカートにバーチャル商品のみが入っている場合に誤った税率が表示される問題を修正しました。
* **MDVA-38608** （*Adobe Commerce >=2.3.0 &lt;2.4.3* の場合） – 再インデックスが正常に終了しなかった場合に一時テーブルが削除されない問題を修正しました。
* **MDVA-38308** （*Adobe Commerce >=2.3.5 &lt;=2.3.6-p1 || >=2.4.0 &lt;=2.4.1-p1 || >=2.4.2 &lt;2.4.4*） – 製品への [!DNL Vimeo] ビデオの追加に関連する問題を修正しました。

## v1.0.25 {#v1-0-25}

* **MDVA-37916** （*Adobe Commerce >=2.3.6 &lt;2.4.3* の場合） – [!DNL Paypal Payment Advanced] 方式を使用したときに顧客が支払確認ページに移動しない問題を修正しました。
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
* **MDVA-37182** （*Adobe Commerce >=2.4.1 &lt;=2.4.2* の場合） - [!DNL Elasticsearch] version 6 と version 7 の両方で誤った検索結果が取得される問題を修正しました。
* **MDVA-36253** （*Adobe Commerce >=2.4.0 &lt;=2.4.1-p1* の場合） – アイテムを削除した後、ミニカートに間違った小計が表示される問題を修正しました。
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
* **MDVA-23845** （*Adobe Commerce >=2.3.2-p2 &lt;2.3.5* の場合） - JavaScriptの縮小が有効になった後で、メールテンプレートをプレビューできない問題を修正しました。
* **MDVA-22026** （*Adobe Commerce >=2.3.2 &lt;2.3.4* の場合） – 外部 URL からの画像を含めて CSV ファイルから商品を読み込めない問題を修正しました。
* **MDVA-22383** （*Adobe Commerce >=2.3.0 &lt;2.3.4* の場合） – 商品の保存に時間がかかり、ページが壊れる問題を修正しました。
* **MC-41359** （*Adobe Commerce >=2.3.6-p1 &lt;2.3.7, >=2.4.2 &lt;2.4.3*） – SameSite cookie の誤ったパラメーター設定の問題を修正しました。

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
* **MDVA-34928** （*Adobe Commerce >=2.3.5 &lt;2.3.5-p2* の場合） – ストアクレジットが支払いから削除された後、ページローダーが無期限に表示される問題を修正しました。
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
* **MDVA-35197** （*Adobe Commerce >=2.3.5 &lt;2.4.0* の場合） – 以前に追加した商品が在庫切れになった場合に、GraphQLを使用して買い物かごに追加するとエラーが発生する問題を修正しました。
* **MDVA-34850** （*Adobe Commerce >=2.3.1 &lt;2.4.0* の場合） – 設定可能な商品の在庫切れオプションが、打ち消し線として表示されるのではなく、表示されない問題を修正しました。
* **MDVA-34867** （*Adobe Commerce >=2.3.0 &lt;2.4.3* の場合） – スケジュールされた更新に設定された条件フィールドの値が保存されない問題を修正しました。
* **MDVA-35092** （*Adobe Commerce >=2.3.5 &lt;2.4.3* の場合） – 非推奨（廃止予定）の [!DNL Vimeo] API が原因でユーザーが [!DNL Vimeo] ビデオを追加できない問題を修正しました。

## v1.0.16 {#v1-0-16}

* **MDVA-33453** （*Adobe Commerce >=2.3.6 &lt;2.4.3* の場合） – 一致する商品の価格が web サイトごとに異なる場合に、ページビルダー商品のコンテンツタイプのプレビューが機能しない問題を修正しました。
* **MDVA-32634** （*Adobe Commerce ^2.3.1* の場合） – すべてのストアに割り当てられたカテゴリの `url_path` が、階層内でカテゴリを移動した後も変更されない問題を修正しました。
* **MDVA-33344** （*Adobe Commerce ^2.3.0* の場合） – データベースの値の代わりに、ハードコードされた `rma_item` エンティティのデフォルト属性セット ID が使用される問題を修正しました。
* **MDVA-34192** （*Adobe Commerce >=2.3.4 &lt;2.4.3* の場合） – dd/mm/yyyy 形式を使用してお客様の生年月日を変更/指定できない問題を修正しました。
* **MDVA-34847** （*Adobe Commerce ^2.3.0* の場合） – カスタム権限を持つ管理者ユーザーの管理コレクションで、SQL 条件に対するストア ID のタイプ変換を整数に修正しました。
* **MDVA-34886** （*Adobe Commerce ^2.3.2* の場合） - *weight* 商品属性が検索可能として設定されている場合、検索結果を返さない問題を修正しました。

## v1.0.15 {#v1-0-15}

* **MDVA-33559** （*Adobe Commerce >=2.3.0 &lt;2.4.3* の場合） – リダイレクトパラメーターリスト形式エラーで [!DNL PayPal Payflow Pro] の支払いが失敗する問題を修正しました。
* **MDVA-34023** （*Adobe Commerce >=2.3.0 &lt;2.4.3* の場合） – 「addressId のエンティティがありません *」というエラーが訪問者のブラウザーにランダムに表示される問題を修正しました*
* **MDVA-32759** （*Adobe Commerce >=2.3.1 &lt;2.4.3 with B2B extension*） – 共有カタログによって既存の階層価格が削除される問題を修正しました。
* **MDVA-33482** （*Adobe Commerce ^2.3.5* の場合）：部分請求書に対してクレジット・メモを生成すると、その部分請求書の税金ではなく、合計受注の税金が生成される問題を修正します。
* **MDVA-33393** （*Adobe Commerce >=2.3.0 &lt;2.4.2* の場合） – エラーを修正しました *指定された countryId が存在しません*。
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
* **MDVA-33281** （*Adobe Commerce >=2.3.4 &lt;2.3.6* の場合） - SKU パラメータータイプが間違っているために `inventory:reservation:list-inconsistencies` で致命的なエラーが発生する問題を修正しました。
* **MDVA-24201** （*Adobe Commerce >=2.3.0 &lt;2.3.5* の場合） – 手動でインデックスを再作成するまで、価格にスケジュールされた買い物かご価格ルールが反映されない問題を修正しました。
* **MDVA-32694** （*Adobe Commerce >=2.3.0 &lt;2.3.6 || >= 2.4.0 &lt;2.4.2*） – デフォルトでないストアに関連する製品の場合、管理者ユーザーが交渉可能な見積もりに製品を追加できない問題を修正しました。
* **MDVA-33516** （*Adobe Commerce >=2.3.0 &lt;2.3.6* の場合） – 購入リストでバンドル商品を編集するとエラーが発生する問題を修正しました。
* **MDVA-33975** （*Adobe Commerce >=2.3.4 &lt;2.4.2* の場合） – GraphQL リクエストでの価格計算に関する複数の問題を修正しました。

## v1.0.13 {#v1-0-13}

* **MDVA-30858** （*Adobe Commerce >=2.3.0 &lt;2.4.2* の場合） - **レポート** > **営業** > **[!DNL PayPal]** 決済で [!DNL PayPal] 決済レポートが期待どおりに使用できない問題を修正しました。
* **MCP-87** （*Adobe Commerce >=2.3.1 &lt;2.4.2* の場合） – 大規模プロファイル向けのカテゴリ商品および在庫インデクサーのインデクシング時間を改善しました。
* **MDVA-33106** （*Adobe Commerce >=2.3.0 &lt;2.4.2* の場合） – cron `run` コマンドの実行後に、再スケジュールされた商品の変更内容が消去される問題を修正しました。
* **MDVA-19391** （*Adobe Commerce >=2.3.0 &lt;2.3.5* の場合） – `catalog_category_entity_text` テーブルの説明レコードが NULL であることが原因で `analytics_collect_data` がエラーをスローする問題を修正しました。
* **MDVA-20376** （*Adobe Commerce >=2.3.2 &lt;2.3.4* の場合） – 注文後にログインした顧客の `exception.log` ージで、*customerId = 1 のエンティティがありません* エラーの問題を修正しました。
* **MDVA-23764** （*Adobe Commerce >=2.3.2 &lt;2.3.5* の場合） – ダイナミックブロックの表示に影響する `JsFooterPlugin.php` のバグを修正しました。
* **MDVA-13203** （*Adobe Commerce >=2.3.0 &lt;2.4.2* の場合） – フル再インデックス後に *Integrity constraint violation search_tmp_ table* エラーが表示される問題を修正しました。
* **MDVA-23426** （*Adobe Commerce >=2.3.3 &lt;2.3.5* の場合） – Adobe Commerceから送信される通知メールに、コンテンツが添付ファイルとして追加された空白の本文が含まれる問題を修正しました。
* **MDVA-22150** （*Adobe Commerce >=2.3.1 &lt;2.3.4* の場合） – 設定可能な商品が買い物かごにあり、クーポンが適用されている顧客が、その設定可能な商品が管理者で無効になっている場合にログインできない問題を修正しました。
* **MDVA-32545** （*Adobe Commerce >=2.3.0 &lt;2.4.2* の場合） – 管理者から注文を作成したときに請求書が自動送信されない問題を修正しました。
* **MDVA-32714** （*Adobe Commerce >=2.3.4 &lt;2.4.1* の場合） – GraphQLの商品クエリでカスタマーグループの価格が機能しない問題を修正しました。

## v1.0.12 {#v1-0-12}

* **MDVA-31399** （*Adobe Commerce >=2.3.2 &lt;2.4.2* の場合） - *小計を追加します（ 税金）* 価格処理基準条件のオプション。
* **MDVA-31236** （*Adobe Commerce >=2.4.0 &lt;2.4.2* の場合） – カスタムリソースアクセス権を持つ管理者が 2FA を設定したり、ログインしたりできない問題を修正しました。
* **MDVA-30845** （*Adobe Commerce >=2.3.5 &lt;2.3.7* の場合） - *申し訳ありませんが、現時点ではこの注文の見積もりは利用できません* UPS XML/USPS/DHL への接続に失敗するとエラーが表示されます。
* **MDVA-32133** （*Adobe Commerce >=2.4.0 &lt;2.4.1* の場合） – 特定の場合にページビルダーからメディアギャラリーが読み込まれない問題を修正しました。
* **MDVA-12304** （*Adobe Commerce >=2.3.0* の場合） - Cookie の最大数を 50 から 200 に増やします。
* **MDVA-32632** （*Adobe Commerce >=2.3.2 &lt;2.3.5* の場合） – 注文が支払いシステムに表示されるが、Adobe Commerceには表示されない問題を修正しました。
* **MDVA-32449** （*Adobe Commerce >=2.3.0 &lt;2.3.6 || 2.4.0 || >=2.4.1 &lt;2.4.2 with B2B extension*） – 注文履歴の読み込みが非常に遅い、またはまったく読み込まれない問題を修正しました。
* **MDVA-32739** （*Adobe Commerce >=2.3.0 &lt;2.4.2* の場合） – 非同期メール通知を有効にすると古い販売メールが送信される問題を修正しました。

## v1.0.11 {#v1-0-11}

* **MC-38509** （*Adobe Commerce 2.3.6、2.4.1* の場合） - *新規のお客様のアカウントの作成* フォームで無効なデータを修正した後に、「*アカウントの作成*」ボタンが無効のままになる問題を修正しました。
* **MDVA-31006** （*Adobe Commerce 2.3.0、2.3.1* の場合） – 支払いを使用して注文した後に重複した注文が表示される問題 [!DNL Paypal Express] 修正しました。
* **MDVA-25602** （*Adobe Commerce 2.3.0* の場合） – Chrome 80 ブラウザーおよびカスタマーログインページへの API レスポンス リダイレクトで [!DNL PayPal Payflow Pro] の支払い方法に関する問題と、Cookie をデフォルトで `SameSite=Lax` として扱う問題を修正しました。

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

* **MDVA-31242** （*Adobe Commerce >=2.3.0 &lt;2.4.1 with B2B extension*） – クレジット メモ グリッドに間違った通貨記号が表示される問題を修正しました。
* **MDVA-31295** （*Adobe Commerce >=2.3.0 &lt;2.4.2* の場合） – 部分的な注文が完了しても商品に課税されたときに報酬ポイントが計算されない問題を修正しました。
* **MDVA-30112** （*Adobe Commerce >=2.3.4 &lt;2.4.2* の場合） – 注文数が *bunch-size* 値を超えた場合、Adobe Commerceが *pending* ステータスの注文を不整合と見なす問題を修正しました。
* **MDVA-31150** （*Adobe Commerce >=2.3.0 &lt;2.4.2* の場合） – 請求書が Rest API 呼び出しによって転記され、注文が店舗クレジットおよびギフトカードのアカウントによって部分的に支払われた場合に、GETの請求書 Rest API 呼び出しによって店舗のクレジットおよびギフトカードの残高が返されない問題を修正しました。
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
* **MDVA-31224** （*Adobe Commerce >=2.3.3 &lt;2.3.5* の場合） – バンドル商品の `catalog_product_price` の再インデックス操作のパフォーマンスを向上させます。
* **MDVA-31321** （*Adobe Commerce >=2.3.2 &lt;2.3.5* の場合） - *すべて表示* が選択されている場合に空白ページ（エラー）を修正します。 [!DNL Elasticsearch] 製品 id の大きなリストを返します。 このシナリオでは、order by 句が間違った SQL 形式に変換されます。
* **MDVA-30815** （*Adobe Commerce >=2.3.2 &lt;2.3.4* の場合） – 検索結果ページに表示する検索結果の数を変更すると、Adobe Commerceで空白ページが表示される問題を修正しました。 ページご [!DNL Elasticsearch] に表示される検索結果の数を変更した場合に、カテゴリページの結果が正しく表示されるようになりました。
* **MDVA-30782** （*Adobe Commerce >=2.3.5 &lt;2.4.2* の場合） – カートのルールにかかわらず動的ブロックが表示される問題を修正しました。
* **MDVA-31021** （*Adobe Commerce >=2.3.0 &lt;2.4.2* の場合） - `module-catalog-import-export/Model/Import/Product/Option.php` でパフォーマンスの問題が発生している問題を修正しました。 テーブルに 100,000 件を超えるレコードがある場合、1 つの製品 `catalog_product_option` 含む新しい CSV の検証に要する時間は 10 秒未満です。
* **MDVA-31007** （*Adobe Commerce >=2.4.0 &lt;2.4.1* の場合） – カスタムアドレス属性がマイアカウント領域の注文詳細ページとバックエンドに正しく表示されない問題を修正しました。
* **MDVA-29389** （*Adobe Commerce >=2.3.0 &lt;2.4.2* の場合） - `analytics_collect_data` cronjob で *Port はホストパラメーター内で設定する必要がある（localhost:3306 など）と表示される、詳細レポートの問題を修正しました*。
* **MDVA-31343** （*Adobe Commerce >=2.3.4 &lt;2.3.6* の場合） – カテゴリがスケジュールされている際に削除された body クラス `page-layout-category-full-width` の問題を修正しました。
* **MDVA-30945** （*Adobe Commerce >=2.3.0 &lt;2.4.2* の場合） – カート `Call to a member function getValue() on null in module-configurable-product CartItemProcessor.php` をアップデートすると致命的なエラーメッセージが表示される問題を修正しました。

## v1.0.6 {#v1-0-6}

* **MDVA-28993** （*Adobe Commerce >=2.3.4 &lt;2.4.0* の場合） - *一致する必要がある最小* 機能と、[!DNL Elasticsearch] エンジンの部分検索を実装します。 検索クエリでのハイフンの問題を解決します。
* **MDVA-30102** （*Adobe Commerce >=2.3.2 &lt;=2.4.0* の場合） – レイアウトキャッシュに TTL がないので Redis キャッシュがすぐに大きくなる問題を修正しました。
* **MDVA-30599** （*Adobe Commerce >=2.3.4 &lt;=2.4.0* の場合） - API を使用して作成されたゲストの引用符が、ログインしたお客様の引用符として誤ってマークされる問題を修正しました。
* **MDVA-29446** （*Adobe Commerce >=2.3.3 &lt;=2.4.0* の場合） – チェックアウト時に適用できない配送方法の価格がゼロと表示される問題を修正しました。
* **MDVA-30357** （*Adobe Commerce >=2.3.2 &lt;=2.4.0* の場合） - cron でサイトマップを生成する際に誤った画像 URL が作成される問題を修正しました。
* **MDVA-30565** （*Adobe Commerce >=2.3.2 &lt;=2.3.3-p1* の場合） – ストアフロントのチェックアウトで、永続ショッピングカートが有効になっている場合に、ゲストのお客様に *No such entity with cartid = 0* エラーが表示される問題を修正しました。
* **MDVA-29787** （*Adobe Commerce >=2.3.0 &lt;=2.4.0* の場合） – 表示する商品を定義する際に *次のいずれか* 条件を使用した場合に、関連商品のターゲットルールが機能しない問題を修正しました。
* **MDVA-30977** （*Adobe Commerce >=2.3.4 &lt;=2.3.5-p2* の場合） – インデックス再作成後にカテゴリにランダムな商品が見つからない問題を修正しました。
* **MDVA-28202** （*Adobe Commerce >=2.3.4 &lt;=2.4.2* の場合） - MSI を使用したときにレイヤーナビゲーションで設定可能な商品が正しくフィルタリングされない問題を修正しました。
* **MDVA-28300** （*Adobe Commerce >=2.3.0 &lt;2.3.6* の場合） - GQL リクエストにカタログ価格ルールからの価格変更が反映されない問題を修正しました。
* **MDVA-31006** （*Adobe Commerce >=2.3.2 &lt;=2.4.2* の場合） -[!DNL Paypal Express] の支払いを使用して注文した後に重複した注文が表示される問題を修正しました。

## v1.0.5 {#v1-0-5}

* **MDVA-30841** （*Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*） – レイヤーナビゲーションで検索エンジンとして使用された場合に、ブール型の製品属性の *いいえ* 値がレイヤーナビゲーションに含ま [!DNL Elasticsearch] なかった問題を修正しました。
* **MDVA-28191** （*Adobe Commerce >=2.3.3 &lt;2.4.2* の場合） – 管理者を介した注文作成時に支払い方法が読み込まれない問題を修正しました。
* **MDVA-29959** （*Adobe Commerce >=2.3.0 &lt;=2.3.3-p1 with B2B extension* の場合） – *会社* 権限を持つ制限付き管理者ユーザーが会社アカウントを削除できない問題を修正しました。
* **MDVA-30265** （*Adobe Commerce >=2.3.3 &lt;2.4.2* の場合） – 請求書の作成後に出荷トラッキングリンクが機能しなくなる問題を修正しました。
* **MDVA-28409** （*Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*） – データベース内の期限切れの引用符の数が多い場合に、`sales_clean_quotes` cron ジョブが *メモリ不足* エラーで失敗する問題を修正しました。
* **MDVA-30593** （*Adobe Commerce >=2.3.0 &lt;2.3.4* の場合） – 見積もりの有効期間の設定に従って期限切れになった見積もりがクリーンアップされない問題を修正しました。
* **MDVA-30107** （*Adobe Commerce >=2.3.0 &lt;2.3.6* の場合） – ストアビューで異なるベース URL が使用されている場合に、ストアスイッチャーが期待どおりに動作しない問題を修正しました。
* **MDVA-28763** （*Adobe Commerce >=2.3.2 &lt;2.3.4*） – REST API を複数回使用して商品情報をアップデートした後に、商品イメージが重複する問題を修正しました。
* **MDVA-30284** （*Adobe Commerce >=2.3.0 &lt;2.4.2* の場合） – 次の *[!DNL Elasticsearch]エラーが原因でカタログ検索インデクサーが失敗する問題を修正しました：インデックスの合計フィールド数の制限を超えています。*
* **MDVA-29042** （*Adobe Commerce >=2.3.3 &lt;=2.3.4-p2 with B2B extension* の場合） – 新しい商品が共有カタログに追加された後に、カタログの権限が *許可* に自動的に変更された問題を修正しました。
* **MDVA-30428** （*Adobe Commerce >=2.3.3 &lt;2.4.2* の場合） – この商品がカスタムインベントリソースに割り当てられている場合、お客様がウィッシュリストに商品を追加できない問題を修正しました。
* **MDVA-28661** （*Adobe Commerce >=2.3.0 &lt;2.4.2 with B2B extension*） – 会社管理者が変更された後、会社ユーザーの会社アカウントセクションでエラーがスローされる問題を修正しました。

## v1.0.4 {#v1-0-4}

* **MDVA-30195** （*Adobe Commerce 2.3.1 ～ 2.3.4-p2* の場合） – データベース名が長すぎると cron ジョブが失敗し、フロントエンドでカテゴリが更新されない問題を修正しました。
* **MDVA-30106** （*Adobe Commerce ^2.3.0* の場合） - JS コンソールで、チェックアウト時に支払いが読み込まれない問題を修正しました *null のプロパティ「length」を読み取れません*。
* **MDVA-28656** （*Adobe Commerce >=2.3.1 &lt;2.3.6 || >=2.4.0 &lt;2.4.2*） – 支払情報が不要な注文（100% 割引など）が注文され、その注文の請求書が作成された場合、注文のステータスが「完了」ではなく *クローズ* に変わる問題を修正します。
* **MDVA-30209** （*Adobe Commerce 2.3.0～2.3.3-p1* の場合） – お客様がアカウント情報を更新した場合に、お客様グループがデフォルトに変更される問題を修正しました。
* **MDVA-30123** （*Adobe Commerce >=2.3.4 &lt;2.4.2* の場合） - GraphQL クエリで属性オプションラベルが正しく翻訳されない問題を修正しました。
* **MDVA-29996** （*Adobe Commerce >=2.3.3 &lt;2.4.2* の場合） – カテゴリ権限を有効にした後、カテゴリページがフルページキャッシュによってキャッシュされない問題を修正しました。
* **MDVA-30164** （*Adobe Commerce >=2.3.1 &lt;2.4.2* の場合） – カスタム顧客属性が存在する場合に、顧客レコードを顧客グリッドから書き出すことができない問題を修正しました。
* **MDVA-30444** （*Adobe Commerce >=2.3.0 &lt;2.4.1* の場合） - GraphQLを使用して注文した場合に、確認メールが送信されない問題を修正しました。
* **MDVA-30490** （*Adobe Commerce 2.3.4 ～ 2.3.5-p2* の場合） – いずれかの商品の短い説明が空の場合に、商品の比較で 500 エラーページがスローされる問題を修正しました。
* **MDVA-30232** （*Adobe Commerce >=2.3.1 &lt;2.4.1* の場合） – 元の注文にギフトカードが含まれている場合に再注文できない問題を修正しました。
* **MDVA-29965** （*Adobe Commerce >=2.3.3 &lt;2.4.0* の場合） – 商品を買い物かごに追加すると、「無効なフォームキー」エラーが発生する問題を修正しました。
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
