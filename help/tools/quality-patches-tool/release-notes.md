---
title: リリースノート
description: Adobe Commerceで使用可能なパッチと、それらのパッチで解決される問題について説明します。
exl-id: 22262555-f5ea-49ad-98ad-ea8428ef66d5
type: Troubleshooting
source-git-commit: 429f0ebebb1d70ace1b81fe1f1a0b38e7998c609
workflow-type: tm+mt
source-wordcount: '31564'
ht-degree: 0%

---

# リリースノート

[[!DNL Quality Patches Tool]](https://github.com/magento/quality-patches)は、AdobeとMagento Open Source コミュニティによって開発された個別のパッチを提供します。 インストールされているバージョンのAdobe Commerceで使用できるすべての個々のパッチに関する一般的な情報を適用、取り消し、表示できます。 パッチを開発したユーザーに関係なく、Adobe CommerceおよびMagento Open Source プロジェクトにパッチを適用できます。 例えば、コミュニティで開発したパッチをAdobe Commerce プロジェクトに適用できます。

>[!INFO]
>
>Adobe Commerce プロジェクトにパッチを適用する手順については、[&#x200B; パッチを適用](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ja#apply-individual-patches)を参照してください。 リリースされたパッチの完全なリストを確認するには、「[[!DNL Quality Patches Tool]: パッチを検索](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)」を参照してください。

>[!INFO]
>
>Magento Open Sourceのコミュニティによって作成された[!DNL quality patches]について詳しくは、[&#x200B; リリースノート &#x200B;](https://github.com/magento/quality-patches/blob/master/community-release-notes.md)を参照してください。

## v1.1.78 {#v1-1-78}

* **ACP2E-4416** （Adobe Commerce >=2.4.4 &lt;2.4.9）の場合 – Adminで作成したときに顧客報酬ポイントが初期化されない問題を修正します。
* **ACP2E-4419** （Adobe Commerce >=2.4.6 &lt;2.4.8の場合） – ストアフロントでreCAPTCHA v2 （「I am not a robot」）の検証が正常に行われた後、チェックアウト時にギフトカードが正しく適用されない問題を修正します。
* **ACP2E-4431** （Adobe Commerce >=2.4.4 &lt;2.4.9）の場合 – リインデックスプロセス中に、ターゲットルールに一致する関連商品が削除される問題を修正します。
* **ACP2E-4448** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.8 &lt;2.4.9） - Redisのリカバリー後にRedisの停止中に行われた設定の変更が反映されず、古い値が保持される問題を修正します。
* **ACP2E-4452** （Adobe Commerceの場合、B2B >=1.5.1 &lt;1.5.3） – クイック注文ページの商品の価格に税金が含まれる問題を修正します。税金の表示設定に関係なく適用されます。
* **ACP2E-4456** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.8 &lt;2.4.9） - GraphQLの突然変異を使用して注文をキャンセルしても、ギフトカードで支払われた注文が完全にクローズド ステータスに移行しない問題を修正します。
* **ACP2E-4507** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.8 &lt;2.4.9） - GraphQLの変更を通じて行われたお客様のパスワードリセットリクエストにパスワードリセット設定が適用されない問題を修正します。
* **ACP2E-4513** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.8 &lt;2.4.9） – 期限切れのCAPTCHA画像がシステムから削除されない問題を修正します。
* **ACP2E-4522** （Adobe Commerce >=2.4.7 &lt;2.4.9）複数の買い物かごの結合または見積もり保存要求を同時に実行すると、quote_coupons テーブルで断続的に重複するキーエラーが発生する問題を修正します。
* **ACP2E-4528** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.8 &lt;2.4.9） – お客様の住所での市区町村検証に関する問題を修正しました。この問題により、スラッシュ（/）文字が使用できるようになり、!、&quot;、#、？などの無効な文字が拒否されるようになりました。
* **ACP2E-4535** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.7 &lt;2.4.9） – パスワードを忘れたフォームを送信すると、セッションが破棄または再生成され（PHPSESSIDの変更）、ゲストカートがクリアされる問題を修正します。
* **ACP2E-4540** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.7 &lt;2.4.9） - Fotorama ライブラリが正しく読み込まれず、最初の添付された画像のみが表示される問題を修正します。
* **ACP2E-4555** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.8 &lt;2.4.9） - &quot;&quot;を含む最新の電話番号の問題を修正します。 または「/」が正しく検証されていません。
* **ACP2E-4565** （Adobe Commerceの場合、B2B >=1.5.0 &lt;1.5.3） - X-Adobe-Company ヘッダーを使用すると、Company GraphQL クエリが「現在のお客様が許可されていません」と返される問題を修正します。
* **ACP2E-4591** （Adobe Commerce >=2.4.4 &lt;2.4.8の場合） – 「初回購入者」など、注文数に基づく顧客セグメントが、REST APIを介して注文された場合に更新されない問題を修正します。
* **ACP2E-4609** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.6 &lt;2.4.9） – 一部の引用符に削除済み商品が含まれている場合に、引用符が表示されない問題を修正します。
* **ACP2E-4613** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.6 &lt;2.4.9） – 大きなメディアディレクトリ構造が原因でgettreeの応答が遅くなり、Media Gallery ディレクトリツリーの読み込み時間が延長される問題を修正します。
* **ACP2E-4628** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.8 &lt;2.4.9） – アカウント共有がグローバルに設定されている場合に、大文字のメールアドレスを持つ顧客を読み込むと未定義の配列キーエラーが発生する問題を修正します。
* **ACP2E-4665** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.8 &lt;2.4.9） - REST APIで要求された場合、製品ギャラリーにビデオを含む設定可能な製品の子製品が一覧表示されない問題を修正します。
* **ACP2E-4732** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.8） - changelog テーブルのversion_id列が最大値に達した場合に、多数の更新を行ったお客様に対して部分的なインデックス作成が停止する問題を修正します。
* **ACP2E-4763** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.8 &lt;2.4.9） – カタログ価格が税金が2回適用されているため、「税金を含む」に設定されている場合に、GraphQL customerOrders クエリが膨張したoriginal_price_including_taxおよびoriginal_row_total_including_tax値を返す問題を修正します。
* **ACSD-60989** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.8） – 宣言型スキーマを使用して外部キーで列を変更すると、MariaDBでエラーが発生する問題を修正します。
* 更新されたバージョン：**ACSD-59280**、**ACSD-45255**、**ACSD-50336**、**ACSD-49737**、**ACSD-50849**、**ACSD-53750**、**ACSD-55031**、**ACSD-51819**、**ACSD-55628**、**ACSD-54965-V2**、**ACSD-56546**、**ACSD-61756**、**ACSD-68040**、**ACSD-62708**、**ACSD-63283**、**ACSD-64732**、**ACSD-65775**、**ACSD-66965**、**ACP2E-4050**
* 置き換えられたパッチ：**ACSD-58446**、**ACSD-67904**

## v1.1.77 {#v1-1-77}

* **ACSD-63687** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.5 &lt;2.4.7） - Redis キャッシュをクリーンアップできないため、誤った価格が表示される問題を修正します。
* **ACSD-68341** （Adobe Commerce >=2.4.4 &lt;2.4.9の場合） - PDPの読み込み中にX-Magento-Vary Cookieが複数回設定され、ストアで複数の顧客セグメントが作成される場合の問題を修正します。
* **ACSD-68537** （Adobe Commerce >=2.4.8 &lt;2.4.9）のお客様のセグメント数が増加すると、チェックアウトのパフォーマンスが低下する問題を修正します。
* **ACSD-68664** （Adobe Commerce >=2.4.6 &lt;2.4.9の場合） – カスタムドメインを持つストアのコンテンツをプレビューしようとすると、スケジュールされた更新プレビューが壊れる問題を修正します。
* **ACSD-68759** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4-p2 &lt;2.4.5 |>=2.4.5-p1 &lt;2.4.9） – アラビア語のロケールを使用すると、お客様アカウントの作成が失敗し、DOB （Date of Birth）属性がストアフロントに表示されるように設定される問題を修正します。
* **ACSD-68892** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.8 &lt;2.4.9） – キャッシュ可能なページがFastly キャッシュに適切に保存または提供されない場合に、キャッシュ動作に一貫性がなく、パフォーマンスが低下する問題を修正します。
* **ACSD-69016** （Adobe Commerce >=2.4.7 &lt;2.4.9）の場合：異なるタイムゾーンで作成されたweb サイトに特別価格が適用されない問題を修正します。
* **ACSD-69020** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.7 &lt;2.4.8） – 子商品のいずれかがフィルタリング条件を満たす場合に、設定可能な商品がPageBuilder商品カルーセルリストに自動的に含まれる問題を修正します。
* **ACSD-69237** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.9） - sales_*_async_insert cron ジョブを通じて処理および挿入できるエントリの数が、1回の実行につき100に制限される問題を修正します。
* **ACSD-69311** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.9） – 請求書から一部払い戻しを作成する際に、以前のクレジットメモが注文ビューページから作成された場合に、クレジットメモで誤った税計算が発生する問題を修正します。
* **ACSD-69351** （Adobe Commerce >=2.4.4 &lt;2.4.9）の場合 – ギフトカードの残高と有効期限が、割り当てられたweb サイトの範囲に従って表示されない問題を修正しました。
* **ACSD-69494** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.8 &lt;2.4.9） – 「is_online」パラメーターを使用した返金要求が正しく処理されない非同期返金処理の問題を修正します。
* 更新されたバージョン：**ACSD-67250**
* 置き換えられたパッチ：**ACSD-62629**、**ACSD-66157**
* 非推奨のパッチ：**ACSD-66157**

## v1.1.76 {#v1-1-76}

* **ACSD-67091** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.8 &lt;2.4.9） – データボリュームに基づいて2つの削除方法を実装することで、カタログルール製品インデックスのクリーンアップを確実に行うための書き込みセットの最大サイズのエラーを修正します。
* **ACSD-67370** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.7 &lt;2.4.9） - PDP/PLPのバンドル商品と複数通貨ストアの買い物かごページに誤った価格が表示される複数の問題を修正します。
* **ACSD-68410** （Adobe Commerceの場合、B2B >=1.3.3 &lt;1.5.3） – 交渉可能な見積もりに対する注文を配置すると、見積にカート行が誤って追加または結合される問題を修正します。 交渉可能な見積もりチェックアウトの最後の手順を終了すると、製品がショッピングカートに正しく追加されるようになりました。
* **ACSD-69086** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.7 &lt;2.4.8） - cron ジョブが変更ログテーブルをクリアできず、大量のデータを処理する際にGalera Clusterがクラッシュする問題を修正します。
* **ACSD-69115** （Adobe Commerce >=2.4.4 &lt;2.4.9の場合） – デフォルト以外のweb サイトに割り当てられたお客様のショッピングカートを管理する際に、管理者ユーザーにショッピングカートのエラーが表示されない問題を修正します。
* **ACSD-69129** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.5 &lt;2.4.7 |>=2.4.8 &lt;2.4.9） – デフォルトの基本web サイトを削除し、セカンダリ web サイトをデフォルトとして使用すると、REST APIを介してセカンダリ web サイトのティア価格を更新しようとしたときにエラーが発生する問題を修正します。
* **ACSD-69203** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.8 &lt;2.4.9） – 複数のカテゴリがカテゴリ条件にリストされている場合に、製品リストウィジェットが誤った結果を返す問題を修正しました。
* **ACSD-69261** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.9） – 一部の請求書および残りの数量キャンセルのシナリオで`times_used`属性が誤って処理されたために、お客様ごとに1回使用するように設定されたカート価格ルールクーポンが複数回再利用された問題を修正します。
* **ACSD-69308** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.9） - `special_price`がweb サイトレベルでのみ設定されていた場合（「すべてのストアビュー」ではない）に、カタログの価格規則が適用されない問題を修正します。 修正の後、最初にweb サイトのデフォルトのストアを確認することで、カタログ価格ルールが正しく適用されます。
* **ACSD-69319** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.7 &lt;2.4.9） – 子商品がカスタムソースで在庫を持っていた場合に、バンドル価格が適切にインデックス化されない問題を修正しました。
* **ACSD-69325** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.7 &lt;2.4.9） - SKU ケースを変更すると、ストアフロントで商品が在庫切れになる問題が修正されました。
* **ACSD-69331** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.5 &lt;2.4.9） – メディアギャラリーのコンテンツ作成者が`create_folder`権限のみを持つフォルダーを作成できない問題を修正しました。 修正の後、彼らは期待どおりにフォルダを作成することができます。
* **ACSD-69333** （Adobe Commerce >=2.4.7 &lt;2.4.9）の場合 – アクティブなスケジュール済みアップデートを含む製品でSKUの変更が許可されていた問題を修正します。 修正の後、アクティブな更新中はSKUの変更が禁止され、明確なエラーで保存が失敗し、管理者SKU フィールドが無効になります。 これにより、ステージング ロールバック中にSKUの変更によって発生するMSI インベントリの不整合を防ぐことができます。
* **ACSD-69541** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.9） – 管理者内の商品の数量を、カートに既に存在する数量よりも少なくすると、GraphQLを介してカート内の商品数量を編集できない問題を修正します。
* 更新されたバージョン：**ACSD-46541**、**ACSD-53750**、**ACSD-66404**
* 置き換えられたパッチ：**ACSD-66404**、**ACSD-68499**

## v1.1.75 {#v1-1-75}

* **ACSD-68289** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.8 &lt;2.4.9） – 検索可能なすべてのフィールドで最低一致条件を満たす場合に、1つのフィールドで条件を満たすことを要求するのではなく、フルテキスト検索で一致する商品が返されるようになった問題を修正しました。
* **ACSD-68359** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.9） - [!UICONTROL Pick in Store]を使用してチェックアウト中にストアを選択する際に、多くの商品がカートに入っているときに長いURLが原因で失敗する問題を修正しました。 以前は、ストアの選択中に生成されたURLが長すぎて&#x200B;*414 エラー*&#x200B;が発生し、顧客がチェックアウトを完了できないことがありました。
* **ACSD-68451** （Adobe Commerceの場合、B2B >=1.5.2-p1 &lt;1.5.3） – 複数のweb サイトで、あるweb サイトで会社管理者がログインし、別のweb サイトで無関係な会社が作成されますが、その無関係な会社に誤ってリンクされる問題を修正します。
* **ACSD-68490** （Adobe Commerce >=2.4.6 &lt;2.4.7）の場合：設定可能な製品作成時に、制限付き管理者ユーザーに[!UICONTROL Add New Attribute] ボタンが表示される問題を修正しました。
* **ACSD-68517** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.7） – カタログおよびカタログの検索ページでフォームの再送信エラーが発生する問題を修正します。
* **ACSD-68573** （Adobe Commerce >=2.4.5 &lt;2.4.9）のお客様のウィッシュリスト項目にカテゴリ権限が正しく適用されなかった問題を修正します。 修正が完了すると、webとGraphQLの両方でウィッシュリスト項目が適切に表示され、ページが設定されます。
* **ACSD-68615** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.9） – 処理済みの組み合わせに注文IDが欠落している場合に、在庫引当補正CLIで例外が表示される問題を修正します。
* **ACSD-68793** （Adobe Commerce、B2B >=1.5.1 &lt;1.5.3の場合） – 有効な商品を共有カタログに割り当てる際に誤って拒否される問題を修正します。
* **ACSD-68925** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.8 &lt;2.4.9） - GraphQL リクエストのレスポンスがHTTP スペックでGraphQLと連携する問題を修正しました。 リクエストを解析できない、不正な場合、または一般的な問題が発生した場合は、4XX応答コードが返されます。 リクエストが解析され、処理できる場合は、200の応答コードが返されます。
* 更新されたバージョン：**MDVA-19640**、**ACSD-47910**、**ACSD-68040**、**ACSD-62965**
* 置き換えられたパッチ：**ACSD-62577**、**ACSD-68011**

## v1.1.74 {#v1-1-74}

* **ACSD-68636** （Adobe Commerce >=2.4.4 &lt;2.4.9の場合） – 請求書が別の店舗から作成された場合に、店舗のオーナーの名前がギフトカードのメールヘッダーに正しく表示されない問題を修正しました。
* **ACSD-68430** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.6 &lt;2.4.8） – レコードに属性コンフィギュレーションから削除された複数の属性オプションが含まれている場合に、顧客または顧客アドレスの保存が失敗する問題を修正します。
* **ACSD-68499** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.9） – 利用可能な在庫を超える数量を更新すると、GraphQL `updateCartItems`突然変異が誤った成功応答を返し、膨らんだ数量と合計が発生する問題を修正します。
* **ACSD-68810** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.8 &lt;2.4.9） - **[!UICONTROL Customer Account Sharing]**&#x200B;設定にもかかわらず、別のweb サイトで作成されたお客様に注文が割り当てられる問題を修正しました。
* 更新されたバージョン：**ACSD-49737**、**ACSD-57003-V2**
* 置き換えられたパッチ：**ACSD-61969**

## v1.1.73 {#v1-1-73}

* **ACSD-67171** （Adobe Commerce >=2.4.4 &lt;2.4.9の場合） - B2B ユーザーがセッションの有効期限が切れたか、チェックアウト時に削除された際に&#x200B;*[!UICONTROL Access Denied]* ページが表示される問題を修正します。
* **ACSD-67908** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.9） – マルチストア設定でJS ファイルが正しく結合されない問題を修正します。
* **ACSD-68190** （Adobe Commerce >=2.4.4 &lt;2.4.7）の場合 – クーポン割引が適用されない、適用された割引がGraphQL カート表示に正しく表示されない、クーポン割引を削除するとクーポン以外の割引が削除される問題を修正しました。
* **ACSD-68206** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.7 &lt;2.4.9） - **[!UICONTROL Rate Limiting]**&#x200B;拡張機能がインストールされた[!DNL PHP Redis]機能でGraphQL アプリケーションサーバーを使用する際のエラーを修正します。
* **ACSD-68356** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.8 &lt;2.4.9） - GraphQL カート クエリで、バーチャル見積もりに対して誤った割引額が返される問題を修正します。
* **ACSD-68391** （Adobe Commerce >=2.4.6-p10 &lt;2.4.9）の場合 – **[!UICONTROL Quick Order]**&#x200B;および&#x200B;**[!UICONTROL Requisition Lists]**&#x200B;でカテゴリ関連の権限が正しく適用されなかった問題を修正します。
* **ACSD-68400** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.8） – バーチャルギフトカードの数量が在庫予約テーブルに正確に反映されない問題を修正します。

## v1.1.72 {#v1-1-72}

* **ACSD-68040** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.7） - [!DNL MariaDB] 10.6および11.4でフロントエンド検索ページのパフォーマンスが低下する問題を修正し、多くの履歴検索リクエストを処理します。
* **ACSD-67941** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.7-p1 &lt;2.4.8） – フィルター名が不明なGraphQL リクエストがPHP例外ログを引き起こす問題を修正します。
* **ACSD-68064** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.7 &lt;2.4.8） – ネストされたカテゴリの数が多い環境で、スケジュールされた更新を作成するとエントリが重複する問題を修正します。
* **ACSD-66807** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.9） - `report_viewed_product_index` テーブルで商品ページビューの数が正しくないことを示す問題を修正します。
* **ACSD-67383** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.8） – 同じセッションで2つの会社管理者アカウントで&#x200B;**[!UICONTROL Login as Customer]**&#x200B;を使用すると、*そのようなエンティティがcartIdを持たない* エラーが発生する問題を修正します。
* **ACSD-67518** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.8 &lt;2.4.9） – 行数がバッチサイズを超えると、高度なレポートで重複したヘッダー行が生成される問題を修正します。
* **ACSD-67639** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.8 &lt;2.4.9） - **[!UICONTROL Dynamic Price]**&#x200B;が&#x200B;*No*&#x200B;に設定されているバンドル商品のクレジットメモの作成が失敗する問題を修正します。
* **ACSD-67696** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.9） – キャッシュフラッシュ後に`media_gallery`個のエントリがCart GraphQL製品ノードに戻らない問題を修正しました。
* **ACSD-67946** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.7 &lt;2.4.9） – カートの更新でエラーバナーが重複して表示される問題を修正します。
* **ACSD-68011** （Adobe Commerceの場合、B2B >=1.5.1 &lt;1.5.3） – 存在しないSKUを`/V1/sharedCatalog/:id/assignProducts` [!DNL REST] APIを介して共有カタログに割り当てることができる問題を修正します。
* **ACSD-68118** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.6 &lt;2.4.9） - `customerCart` GraphQL クエリがストアヘッダーを反映しない商品属性値を返し、ローカライズに一貫性がない問題を修正します。
* **ACSD-68092** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.8 &lt;2.4.9） – スケジュールされた更新とベース製品データ間の同期が正しくないため、複数回の保存の後にバンドル製品オプションが失われる問題を修正します。
* **ACSD-67424** （Adobe Commerceの場合、B2B >=1.5.0 &lt;1.5.3） – 交渉可能な引用符を使用する場合、`updated_at` `GET /carts/search` API応答の[!DNL REST]値が&#x200B;**[!UICONTROL Admin panel]**&#x200B;に表示されている値と一致しない問題を修正します。
* **ACSD-67187** （Adobe Commerce、B2B >=1.5.1 &lt;1.5.3の場合） – デフォルト以外のweb サイトに制限された管理者ユーザーにエラーが表示される問題を修正します。*少なくともパブリック共有カタログを作成して続行してください*。また、会社グリッドの&#x200B;**[!UICONTROL Add New Company]** ボタンにアクセスできません。
* 更新されたバージョン：**ACSD-49737**、**ACSD-53750**、**ACSD-51819**、**ACSD-55566**、**ACSD-62965**、**ACSD-63323**、**ACSD-63406**、**ACSD-66139**、**ACSD-66404**、**ACSD-67659 66301**、**ACSD-11&rbrace;**
* 置換されたパッチ：**ACSD-62577**、**ACSD-63325**、**ACSD-67102**

## v1.1.71 {#v1-1-71}

* **ACSD-60624** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.8） – ページビルダーの&#x200B;**[!UICONTROL Upload Image]**、[!UICONTROL Image]、および[!UICONTROL Banner] セクションの[!UICONTROL Slider]が空のコンテンツで機能しない問題を修正します。
* **ACSD-67089** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.9） - `inventory/export-stock-salable-qty` APIのページネーションの問題を修正します。誤って`total_count`をページサイズに制限します。
* **ACSD-67093** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.8 &lt;2.4.9） – 日付範囲フィルターを使用してGraphQLで注文を取得すると、誤った結果が返される問題を修正します。
* **ACSD-67459** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.5 &lt;2.4.9） – 説明が65,536文字を超える商品を読み込めない問題を修正しました。
* **ACSD-67603** （Adobe Commerce >=2.4.6 &lt;2.4.8の場合） – 画像インクルージョンが有効になっている商品のサイトマップ生成で、処理時間が長くなる問題を修正します。
* **ACSD-67643** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.8 &lt;2.4.9） – ネストされたカテゴリの数が多い環境で、スケジュールされた更新中に重複するエントリが作成される問題を修正します。
* **ACSD-67652** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.8 &lt;2.4.9） – 子と親の商品の在庫がある場合でも、GraphQL呼び出しでバンドル商品のステータスが在庫切れとして返される問題を修正します。
* **ACSD-67904** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.8 &lt;2.4.9） – 市区町村名に数字（0-9）、アンパサンド （&amp;）、ピリオド （。）、かっこ（）が含まれている場合に注文できない問題を修正しました。
* 置き換えられたパッチ：**ACSD-61322**、**ACSD-65848**

## v1.1.70 {#v1-1-70}

* **AC-15210** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.6-p3 &lt;2.4.9） - USPS統合を古いWeb ツール APIから新しいRESTful USPS APIに移行します。
* **ACSD-67102** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.7 &lt;2.4.8） - Adobe Commerce バックエンドが&#x200B;**[!UICONTROL Categories]**&#x200B;の読み込みが非常に遅くなる問題を修正します。
* **ACSD-66120** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.9） – カタログの価格に税金が含まれるように設定されている場合に、[!DNL GraphQL]が誤って割引率と基準価格を表示する問題を修正します。
* **ACSD-66157** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.5 &lt;2.4.9） – 異なるタイムゾーンで作成されたweb サイトに特別価格が適用されない問題を修正します。
* **ACSD-67659** （Adobe CommerceおよびMagento Open Source >=2.4.8 &lt;2.4.9）の場合）翻訳されたエラーメッセージが未定義のエラーコードを返す問題を修正します。
* **ACSD-67166** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.9） – ストアフロントで見積もりを読み込むときに`cataloginventory_stock_status` クエリが複数回実行され、データベース呼び出しが冗長になる問題を修正します。
* **ACSD-67289** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.8 &lt;2.4.9） – 特別価格が適用された場合に通常価格が表示されない問題を修正します。
* **ACSD-67686** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4-p15 &lt;2.4.5 |>=2.4.5-p14 &lt;2.4.6 |>=2.4.6-p12 &lt;2.4.7） – 空の&lt;ph=&#39;190&#39;/>要求を送信する際に`Syntax Error: Unexpected <EOF>` エラーが発生する問題を修正します。[!DNL GraphQL]
* **ACSD-67250** （Adobe Commerce >=2.4.7-p4 &lt;2.4.8の場合） - **[!UICONTROL Shared Catalog]**&#x200B;の保存操作が、影響を受ける項目のみを更新するのではなく、すべての項目を更新する問題を修正し、不要な操作を排除してパフォーマンスを向上させます。
* **ACSD-67030** （Adobe Commerce >=2.4.4 &lt;2.4.9の場合） – 制限付きロール管理者が編集した場合に、シンプルな製品が設定可能な製品から割り当て解除される問題を修正します。
* 更新されたバージョン：**ACSD-54095**、**ACSD-51636**、**ACSD-51739**、**ACSD-66093**
* 置き換えられたパッチ：**ACSD-62415**

## v1.1.69 {#v1-1-69}

* **AC-15223** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.8 &lt;2.4.9） - 2.4.8 ストアフロントで、ストアを切り替えた後、ページがキャッシュから提供され、選択したストアが反映されない問題を修正します。
* **ACP2E-3731** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.9） - **[!UICONTROL Catalog, Search]**&#x200B;の表示を持つ商品の書き出しに、マルチストア環境の他のストアビューのレコードが誤って含まれる問題を修正します。
* **ACP2E-3767** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.9） – バンドル製品の最後のバンドルオプションを削除できない問題を修正しました。
* **ACP2E-3964** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.7 &lt;2.4.8） – ギャラリーにビデオがセットされたときに、設定可能な製品の子製品をREST API経由で一覧表示できない問題を修正しました。
* **ACP2E-3977** （Adobe Commerce >=2.4.4 &lt;2.4.9の場合） - **[!UICONTROL Cap Reward Points Balance At]**&#x200B;が設定されているときに[!UICONTROL Rewards Points Balance Redemption Threshold] フィールドを空にできない問題を修正し、検証エラーを引き起こしました。
* **ACP2E-4050** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.5 &lt;2.4.8） – バンドル商品を使用し、送料無料でサブセレクト条件を使用すると、複数配送の商品にカートの価格規則が正しく適用されない問題を修正します。
* **ACSD-56226** （Adobe Commerce >=2.4.6 &lt;2.4.7）の場合、`synchronous_replication` フラグが有効になっている場合に、スレーブノードのREAD クエリが古いデータを返す問題を修正しました。
* **ACSD-57477** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.6 &lt;2.4.7） – カート関連のリクエストでセールス ルール処理のパフォーマンスが低下する問題を修正します。
* **ACSD-58108** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.6 &lt;2.4.8） – 元の取得テーブルで結合テーブル名が見つからない場合に、注文グリッドのカスタムモジュール拡張機能SQLでエラーが発生する問題を修正します。
* **ACSD-65983** （Adobe Commerce >=2.4.6-p10 &lt;2.4.9の場合） – 管理バックエンドでバンドルされた製品見積を再設定するとエラーが発生する問題を修正します。
* **ACSD-66149** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.8） – サポートされていないIPN タイプまたは不明なIPN タイプに対して、IPN ハンドラーが&#x200B;*500* エラーを返す問題を修正します。
* **ACSD-66153** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.9） – キャッシュされているレイアウト構造が正しくないため、ページが&#x200B;*500* エラーを返す問題を修正します。
* **ACSD-66302** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.8 &lt;2.4.9） – ウィッシュリストのアイテムが、web サイトでフィルタリングされるのではなく、ストア IDで誤ってフィルタリングされる問題を修正します。
* **ACSD-66311** （Adobe Commerce >=2.4.6-p9 &lt;2.4.9の場合） - Web サイトへのアクセスが制限されている管理者ユーザーに対して、会社のグリッドの読み込みが遅くなる問題を修正します。
* **ACSD-66404** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.9） - cron ジョブが変更ログテーブルをクリアできず、大量のデータを処理すると[!DNL Galera Cluster]がクラッシュする問題を修正します。
* **ACSD-66952** （Adobe Commerce >=2.4.4 &lt;2.4.9）は、PLPまたはカートの各訪問でキャッシュがクリアされ、ターゲットルールが設定されたときにパフォーマンスのオーバーヘッドが発生する問題を修正します。
* **ACSD-67264** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.8） – バンドルおよびダウンロード可能な商品ページレイアウトがデバイス間で一貫性がない問題を修正します。
* **ACSD-67347** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.5-p11 &lt;2.4.6） – 特殊文字を含むクーポンが使用され、ファイルのロックが有効になっている場合に、*ロック*&#x200B;を取得できないというエラーが発生して注文が失敗する問題を修正します。
* 置き換えられたパッチ：**ACP2E-3841**

## v1.1.68 {#v1-1-68}

* **ACSD-58131** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.8） – メディアギャラリーに0 バイトの画像が含まれていると、ディレクトリ内のすべての画像が表示または選択できない問題を修正します。
* **ACSD-62415** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.8） - Adobe Commerceのバックエンドでカテゴリが非常に読み込まれない場合の問題を修正します。
* **ACSD-66082** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.6 &lt;2.4.9） – 商品の読み込みによって商品のスウォッチ画像を更新できない問題を修正します。
* **ACSD-66179** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4-p11 &lt;2.4.5 |>=2.4.5-p10 &lt;2.4.6 |>=2.4.6-p8 &lt;2.4.7 |>=2.4.7 |>=2.4.7-p3 &lt;2.4.9） – 「Not Capture」支払いタイプで作成された請求書をキャンセルすると、404 エラーページが表示される問題を修正しました。
* **ACSD-66865** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.7 &lt;2.4.8） – カタログ価格ルールを保存するとインデクサーが無効になり、影響を受ける商品のみを再インデックス化する代わりに使用できる問題を修正します。
* **ACSD-66963** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.7 &lt;2.4.8） – バーチャル商品を含むカートに割引コードが適用された場合に`estimateTotals`変異が割引に対してnullを返す問題を修正します。
* **ACSD-67039** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.8） - `rp_token` システム属性の検証により、お客様のレコードが保存されなかった問題を修正し、ダイアクリティクスの検証が結果として生成されるお客様の電子メールにのみ適用されるようになりました。
* **ACSD-62146** （Adobe Commerce >=2.4.7 &lt;2.4.8の場合） – アドレス検索が有効で「お客様のアドレス数の制限」が1に設定されている場合に、選択した請求先住所がチェックアウト支払いページに表示されなくなる問題を修正します。
* **ACSD-65938** （Adobe Commerce >=2.4.4 &lt;2.4.9の場合） – 請求書の作成に失敗した場合でも、ギフトカードの電子メールが送信される問題を修正します。
* **ACSD-66072** （Adobe Commerce >=2.4.6 &lt;2.4.9の場合） – 「関連する製品ルール」が設定された際に内部サーバーエラーが発生したため、製品詳細ページで関連製品がGraphQLを介して返されない問題を修正します。
* **ACSD-66233** （Adobe Commerce >=2.4.8 &lt;2.4.9の場合） – 「商品を追加」ポップアップの読み込みに失敗したため、管理者ユーザーが商品をカテゴリに追加できなかった問題を修正します。
* **ACSD-66889** （Adobe Commerce >=2.4.4 &lt;2.4.6の場合） – インベントリインデクサープロセスが正常に完了するよう、適切な構造の非推奨コード行を修正します。
* **ACSD-66965** （Adobe Commerce B2B >=1.5.0 &lt;1.5.3）の場合） – リクエストリストのページプリントオプションでエラーが発生する問題を修正します。
* **ACSD-66506** （Adobe Commerce B2B >=1.5.0 &lt;1.5.3の場合） – 以前に割り当てられた共有カタログの製品が削除され、新しい製品が割り当てられたときに発生したバックエンドエラーを修正します。
* **ACSD-66417** （Braintree 4.6.1の場合） – 注文を日付でフィルタリングしようとすると、受注表でエラーがスローされる問題を修正します。
* 更新されたバージョン：**ACSD-60590**、**ACP2E-3705**
* 置き換えられたパッチ：**ACSD-57003**、**ACSD-66434**

## v1.1.67 {#v1-1-67}

* **ACSD-65935** （Adobe Commerce >=2.4.4 &lt;2.4.8の場合） – 製品が削除されたときに`customerOrders` GraphQL クエリが内部サーバーエラーを返す問題を修正します。
* **ACSD-66049** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.5-p3 &lt;2.4.6 || >=2.4.7 &lt;2.4.9） - ICU ライブラリのバージョンにより、英語以外のストアフロントで誤った価格が表示される問題を修正します。
* **ACSD-66084** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.5 &lt;2.4.9） - `row_total_incl_tax`が完全に割引された商品の0.00ではなく、注文API応答でほぼゼロの残存値として返される問題を修正します。
* **ACSD-66118** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.9） – コンフィギュレーション キャッシュが更新されない場合に、ストア ビューのコードを更新すると[!UICONTROL Design Configuration]設定がクリアされる問題を修正しました。
* **ACSD-66139** （Adobe Commerce >=2.4.7 &lt;2.4.8の場合） – 存在しないカートまたは非アクティブなカートの注文を行うためのGraphQL呼び出しで&#x200B;*UNDEFINED* エラーコードが返される問題を修正します。
* **ACSD-66301** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.6-p9 &lt;2.4.7 || >=2.4.7-p4 &lt;2.4.8） - Adminで注文から買い物かごに商品を戻すと、数量が一致しない問題が修正されました。
* **ACSD-66434** （Adobe Commerce >=2.4.6-p8 &lt;2.4.9の場合） – 企業のGraphQL クエリで顧客IDが見つからない問題を修正します。
* **ACSD-66441** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.5 &lt;2.4.8） – マルチストア設定の設定可能な商品をインデックス作成する際に、ストアフロントがレイヤーナビゲーションに誤ったインデックスデータを表示する問題を修正します。
* **AC-14984** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.6-p10 &lt;2.4.7 || >=2.4.8 &lt;2.4.9） - RabbitMQ SSL接続で&#x200B;*無効なフレームタイプ 21*&#x200B;が発生するエラーを修正します。
* **AC-14985** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.8 &lt;2.4.9） - TLSが有効になっている外部`smtp` サーバーを使用する場合にメールが送信されない問題を修正します。
* 更新されたバージョン：**MDVA-12304**、**ACSD-47920**、**ACSD-56447**、**ACSD-61845**、**ACSD-64118**

## v1.1.66 {#v1-1-66}

* **ACP2E-3789** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.5 &lt;2.4.9） – メディア IDが指定されたときに[!DNL WebAPI]重複したメディアファイルを使用して製品を更新する問題を修正します。
* **ACP2E-3918** （Adobe Commerce >=2.4.5 &lt;2.4.9の場合） – デフォルトの請求先住所なしで実店舗受け取りを使用しているログイン企業のお客様のチェックアウトが失敗する問題を修正します。
* **ACSD-65750** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.7 &lt;2.4.9） - Page Builder Products コンテンツタイプでGraphQL `route` クエリが正しく機能しない製品を返す問題を修正します。
* **ACSD-65775** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.8 &lt;2.4.9） - [!DNL REST] API注文の詳細で、同じ商品の複数の数量が注文されたときに誤った`base_row_total`値と`row_total`値が返される問題を修正します。
* **ACSD-65777** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.8 &lt;2.4.9） - `types` GraphQL リクエストで`MediaGallery` フィールドが商品イメージタイプに見つからない問題を修正します。
* **ACSD-65848** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.8 &lt;2.4.9） – サブセレクトを使用して、代わりに結合を使用するメソッドをリファクタリングすることで、カテゴリ内の合計商品数が計算される問題を修正します。
* **ACSD-65913** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.7 &lt;2.4.9） – 同じ価格の商品を含むカテゴリで[!DNL OpenSearch]が&#x200B;*illegal_argument_exception* エラーをスローした問題を修正します。
* **ACSD-66041** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.9） - `CountryID`が見つからなかったため、アイルランド （IE）のポストコードを受け取り場所で検索できない問題を修正しました。
* **ACSD-66212** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.9） - 2回目以降の試行で顧客CSV ファイルを読み込むとエラーが発生する問題を修正します。
* 更新されたバージョン：**MDVA-12304**、**MDVA-19640**、**ACP2E-3841**、**ACSD-65100**、**ACSD-65787**、**ACP2E-3753**、**ACSD-65202**、**ACSD-65331**、**ACSD-65822**

## v1.1.65 {#v1-1-65}

* **ACP2E-3753** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.8） – ストアまたはテーマ設定に関係なく、マルチストア設定の商品アラートメールが常にデフォルトのテーマを使用して送信される問題を修正します。
* **ACSD-64118** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.7） – 同じ商品を保存および更新するための同時要求がデータの不整合または商品の重複につながる問題を修正します。
* **ACSD-64813** （Adobe Commerce >=2.4.4 &lt;2.4.9の場合） - [!DNL B2B] APIを介して[!DNL REST]共有カタログからカテゴリを割り当て解除するのに、長すぎたり、大きなカタログでタイムアウトが発生したりする問題を修正します。
* **ACSD-65202** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.8） – 「マイアカウント」ページに、同じストア内の他のストアビューからの最近の注文が表示されない問題を修正します。
* **ACSD-65254** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.8） - `updateCustomerEmail` [!DNL GraphQL]のミューテーションを使用してアカウントのメールアドレスを更新した後、お客様にメール通知が送信されない問題を修正します。
* **ACSD-65331** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.8） - [!UICONTROL Pick in Store]で選択したストアがチェックアウトページに戻り、繰り返し移動した後にクリアされた問題を修正します。
* **ACSD-65822** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.8） - [!UICONTROL Customer's Activities]のショッピングカートパネルで、バンドルおよび設定可能な商品数量が正しく表示されない問題を修正します。
* **ACSD-66093** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.8） – ゲスト顧客の[!UICONTROL First Name]および[!UICONTROL Last Name] フィールドにメールアドレスを入力すると、注文確認メールが無効になる問題を修正しました。
* 更新されたバージョン：**ACSD-51291**
* 置き換えられたパッチ：**ACSD-61522**

## v1.1.64 {#v1-1-64}

* **ACP2E-3838** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4-p9 &lt;2.4.4-p13 || >=2.4.5-p8 &lt;2.4.5-p12 || >=2.4.6-p6 &lt;2.4.6-p10 || >=2.4.7 &lt;2.4.7-p5） - &lt;ph=&#39;177&#39;/> CORS エラーが実稼動モードでの変更を保存できない問題を修正しました。[!DNL Page Builder]
* **ACP2E-3841** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.5 &lt;2.4.8） – サブセレクト条件を使用し、送料無料が有効になっている場合に、複数配送商品のカート価格ルールが正しく適用されない問題を修正します。
* **ACSD-63139** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.6 &lt;2.4.7） – 製品属性に数千のオプション値が含まれている場合に製品の書き出しが失敗する問題を修正します。
* **ACSD-65100** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.8） - [!UICONTROL Maximum Width]設定の[!UICONTROL Maximum Height]と[!UICONTROL Media Gallery Image Optimization]の値を削除すると、画像の最適化プロセス中にエラーが発生する問題を修正します。
* **ACSD-65127** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.8） – 実稼動モードでJavaScriptの縮小を有効にすると、[!DNL TinyMCE] 6がブラウザーコンソールでエラーが発生し、機能とユーザーエクスペリエンスに影響する問題を修正します。
* **ACSD-65787** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.7-p5 &lt;2.4.8） – スキーマの作成中にSchemaBuilder クラスがクラッシュしたり、テーブルデータの処理中に未定義の配列キー「column」が原因で更新されたりする問題を修正します。
* **ACSD-65223** （Adobe Commerce、B2B 1.5.1の場合） - [!DNL B2B]件の発注に対して手動で選択した条件と契約書がエラーになる問題を修正します。
* **ACSD-65540** （Adobe Commerce、B2B 1.5.2の場合） - `REGEXP_LIKE` テーブルの更新時に`company_structure`関数が存在しないためにSQL構文エラーが発生する問題を修正します。
* **ACSD-65684** （Adobe Commerce、B2B 1.5.2の場合） - `Magento_Company` テーブルで多数のレコード（～100,000+）を処理する際に[!DNL B2B] モジュールを`company_structure` 1.5.2に更新した後にアップグレードするのに非常に長い時間がかかっていたパフォーマンスの問題を修正します。
* 更新されたバージョン：**ACSD-48234**、**ACSD-51819**、**ACSD-57570**、**ACSD-56415**

## v1.1.63 {#v1-1-63}

* **ACSD-64627** （Adobe Commerce >=2.4.6-p8 &lt;2.4.8の場合） – 会社構造内でユーザーを追加または編集する際に、カスタム顧客属性を保存できない問題を修正します。
* **ACSD-64753** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.8） – 「実店舗での受け取り」で事前に選択した店舗が、店舗の半径を超えていても、配送先住所が変更されたときに更新されない問題を修正します。
* **ACSD-65195** （Adobe Commerce >=2.4.4 &lt;2.4.8の場合） - GraphQL変異`createCompany`が必須リージョンのない国にエラーをスローする問題を修正します。
* **LYNX-839** （Adobe Commerce 2.4.8の場合） - GraphQLを使用して、お客様グループ、セグメント、およびプロモーションルール情報の公開を削除しました。
* 更新されたバージョン：**MDVA-12304**、**ACSD-48234**、**ACSD-58054**

## v1.1.62 {#v1-1-62}

* **ACSD-63406** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4-p9 &lt;2.4.5 |>=2.4.5-p8 &lt;2.4.6 |>=2.4.6-p6 &lt;2.4.8） - &lt;ph=&#39;211&#39;/> cron ジョブの実行時に、期限切れの永続的な引用符がcron ジョブによってクリアされない問題を修正します。`persistent_clear_expired`
* **ACSD-63520** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.7 &lt;2.4.8） – 管理パネルの&#x200B;**[!UICONTROL Configurations]**&#x200B;を通じて追加された画像がアップロードサイズの上限に準拠しない問題を修正します。
* **ACSD-64523** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.7 &lt;2.4.8） – インポートプロセス（管理者またはAPI）を通じて名前を付けずに新しい製品を作成できたため、管理者インターフェイスが壊れ、製品が無効になる問題を修正します。
* **ACSD-64532** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.6-p2 &lt;2.4.8） - ENV変数が「false」に設定されている場合に、ブール値「false」ではなく文字列「false」として扱われる問題を修正します。
* **ACSD-64592** （Adobe Commerce >=2.4.4 &lt;2.4.8の場合） – デフォルト以外のストアのギフトカードの電子メールから請求リンクが常にデフォルトのweb サイトにリダイレクトされる問題を修正しました。
* **ACSD-65164** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.6 &lt;2.4.8） - 1つのチェックボックスカスタムオプションを選択した設定可能な商品を再注文する際に、エラーメッセージ *一部の選択された商品オプションが現在利用できない*&#x200B;が発生する問題を修正します。
* **ACSD-64732** （Adobe Commerce >=2.4.4 &lt;2.4.8）のお客様のセグメントでサードパーティ製コントローラが正しくキャッシュされなかった問題を修正します。

## v1.1.61 {#v1-1-61}

* **ACP2E-3689** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.7 &lt;2.4.8） – より深いレベルでのカテゴリーツリー表示と、アンカー/アンカー以外の関係の反映に関する複数の問題を修正します。
* **ACP2E-3705** （Adobe Commerce >=2.4.7 &lt;2.4.8の場合） - `indexer_update_all_views`が設定されているときに`MAGE_INDEXER_THREADS_COUNT` cronの実行が失敗する問題を修正します。
* **ACSD-63883** （Adobe Commerce >=2.4.4 &lt;2.4.7-p4の場合） - GraphQL応答でリクエストリストが正しくない`items_count`を返す問題を修正します。
* **ACSD-63974** （Adobe Commerce >=2.4.4 &lt;2.4.8の場合） – ストアフロントのリクエストリストグリッドにページ作成機能を追加し、すべてのレコードを一度に表示するのではなく、1 ページあたりのレコード数に制限されているレコードの一部のみを表示することで、リクエストリストページの読み込みに時間がかかりすぎる問題を修正します。
* **ACSD-64178** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.7 &lt;2.4.8） – 数千もの製品属性がある場合に、属性セット編集ページが読み込みが遅くなる問題を修正します。
* **ACSD-64209** （Adobe Commerce >=2.4.4 &lt;2.4.8の場合） – ステータス **[!UICONTROL ordered]**&#x200B;の引用符を除外せずに、cron スケジューラーがすべての交渉可能な引用符を取得し、電子メールまたは電子メールがトリガーされる問題を修正します。
* **ACSD-64431** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.7 &lt;2.4.8） – リクエスト内のクーポンコード情報を含む`placeOrder`の突然変異は、内部エラーをスローしなくなり、注文が正常に配置されたことを示します。
* **ACSD-64467** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.7 &lt;2.4.8） – ストアビューレベルでカテゴリの説明を保存した後、WYSIWYG エディターが空で表示される問題を修正します。
* **ACSD-64546** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.8） - UIで一般的なエラーメッセージが発生し、UPSの配送ラベル作成中に&#x200B;*Array to string conversion*&#x200B;例外がログに保存され、実際のエラーがUIに表示され、正しいエラーメッセージがログに保存される問題を修正しました。
* **ACSD-64684** （Adobe Commerce >=2.4.4 &lt;2.4.8）の場合 – *999*&#x200B;より大きい値のギフトカードを編集および保存する際に、数値&#x200B;*1,000）*&#x200B;のコンマ（千区切り記号）が原因で検証エラーが発生する問題を修正しました。
* 更新されたバージョン：**ACSD-49392**、**ACSD-50368**、**ACSD-51819**、**ACSD-54966-V2**、**ACSD-57003**、**ACSD-62979**、**ACSD-64112**
* 置換されたパッチ：**ACSD-49392**、**ACSD-58739**、**ACSD-62689**、**ACSD-64112**
* 非推奨のパッチ：**ACSD-46192**、**ACSD-52133**

## v1.1.60 {#v1-1-60}

* **ACSD-63323** （Adobe Commerce >=2.4.7 &lt;2.4.8の場合） – カテゴリに商品を追加する際に&#x200B;**[!UICONTROL Select All]** オプションが機能しない問題を修正します。 さらに、ポップアップグリッドを使用して製品をカテゴリに追加する際に、ページネーションとレコード数ラベルが正しく機能するようになります。
* **ACSD-63992** （Adobe Commerce >=2.4.4 &lt;2.4.8の場合） - Admin UIで、クーポンと配送方法に基づく条件を含むカート価格ルールを正しく適用できない問題を修正しました。
* **ACSD-64111** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.8） - [!DNL Page Builder]で製品コンポーネントのネストされた条件を設定する際にエラーが発生する問題を修正します。
* **ACSD-64137** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.8） – オランダ語版のローカライゼーションで、郵便番号による受け取り場所の検索が正しく機能しない問題を修正しました。
* **ACSD-64149** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.8） - 1つの日付のみが編集されたときに、日付範囲の条件を持つ顧客セグメントを保存できる問題を修正します。
* 更新されたバージョン：**MDVA-12304**、**ACSD-45049**、**MDVA-43824**、**ACSD-46192**、**ACSD-50368**、**ACSD-52133**、**ACSD-47657**、**ACSD-51819**、**ACSD-54966-V2**、**ACSD-55628**、**ACSD-45049**、**ACSD-63242**

## v1.1.59 {#v1-1-59}

* **ACSD-63454** （Adobe CommerceおよびMagento Open Source >=2.4.7 &lt;2.4.8）は、ドロップダウンおよび複数選択属性のデフォルト値がデータベースに正しく保存されない問題を修正します。
* **ACSD-63574** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.5） – ページビルダーを使用してブロックにバンドル製品リストを追加するとエラーが発生する問題を修正します。
* **ACSD-63793** （Adobe CommerceとMagento Open Sourceの場合>=2.4.6 &lt;2.4.8） – インポートプロセスが異なるブラウザータブで互いに干渉する問題を修正します。
* **ACSD-64113** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.5 &lt;2.4.8） – メディアギャラリーを介して、幅が比較的小さい画像をアップロードする（またはその逆の場合）際に管理者にエラーが発生する問題を修正します。
* **ACSD-64212** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.5 &lt;2.4.8） – 注文が行われた後にアカウントがGraphQLを介して作成された場合に、注文がお客様のアカウントに関連付けられない問題を修正します。
* **ACSD-63469** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.7 &lt;2.4.8） – 複数のルールが適用された場合に、カート全体の固定金額の割引が正しく適用されなかった問題を修正します。
* **ACSD-63870** （Adobe Commerce >=2.4.4 &lt;2.4.4-p11の場合） – カスタマーアクティブセッション中に会社のステータスが変更されたときに、会社のお客様が適切にログアウトされなかった問題を修正します。
* **ACSD-64112** （Adobe Commerce >=2.4.5 &lt;2.4.8の場合） - `indexer_update_all_views`が設定されているときに`MAGE_INDEXER_THREADS_COUNT` cronの実行が失敗する問題を修正します。
* 更新されたバージョン：**ACSD-61622**
* 置き換えられたパッチ：**ACSD-61553**
* 非推奨のパッチ：**ACSD-61199**

## v1.1.58 {#v1-1-58}

* **ACSD-48570** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.7） - [!UICONTROL Admin] ストアコードをURLに追加&#x200B;**が**&#x200B;有効&#x200B;*だった場合に* パスワードリセット リンクをクリックすると、以前はログインページまたは404 ページが表示されていた場合に、パスワードリセットページにアクセスできない問題を修正しました。
* **ACSD-62118** （Adobe Commerce >=2.4.6 &lt;2.4.8の場合） - `sales_order_tax_item`件の注文が発注された際に[!DNL B2B] テーブルが完全に更新されない問題を修正します。
* **ACSD-63067** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.8） – すべての製品数量が誤って強調表示され、1つの数量のみが正しくない場合に、グループ化された製品内のすべての商品に対して&#x200B;*[!DNL Please specify the quantity of product(s).]*&#x200B;というメッセージが表示される問題を修正します。
* **ACSD-63090** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.8） – カートに追加された後、商品が削除されたときにショッピングカートのアイテムが削除される問題を修正します。
* **ACSD-63182** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.8） - **[!DNL MSI]** *enabled*&#x200B;で重複したバンドル製品を保存する際にエラーが発生する問題を修正します。
* **ACSD-63283** （Adobe Commerce >=2.4.4 &lt;2.4.8の場合） – ギフトレジストリから商品を注文すると例外が発生し、ギフトレジストリの更新にレジストリに属しない商品が含まれる問題を修正します。
* **ACSD-63299** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.8） – 設定可能な商品の特別価格がストアフロントに表示されない問題を修正します。
* **ACSD-63325** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.7 &lt;2.4.8） – 空の`Syntax Error: Unexpected <EOF>` リクエストを送信する際に[!DNL GraphQL] エラーが発生する問題を修正します。
* **ACSD-63329** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.8） - **[!UICONTROL Date]**&#x200B;を使用して商品を作成する際に、**[!UICONTROL Date and Time]**&#x200B;または[!DNL REST API]入力タイプの属性のデフォルト値が設定されない問題を修正します。
* **ACSD-63572** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.5 &lt;2.4.8） – インデクサープロセスが終了した場合に`CatalogRule` インデクサー一時テーブルがクリーンアップされない問題を修正します。
* **ACSD-63578** （Adobe Commerce >=2.4.4 &lt;2.4.8の場合） - **[!UICONTROL Delete]**&#x200B;で&#x200B;**[!UICONTROL Add to Order by SKU]**&#x200B;の[!UICONTROL Admin] ボタンをクリックしても[!DNL SKU]が削除されない問題を修正しました。
* 更新されたバージョン：**MDVA-39305-V3**
* 置き換えられたパッチ：**ACSD-56280**
* 非推奨のパッチ：**ACSD-62872**

## v1.1.57 {#v1-1-57}

* **ACSD-57570** （Adobe Commerce >=2.4.4 &lt;2.4.4-p10の場合） – 特定のストアへのアクセス権を持つ制限付き管理者ユーザーが、製品が割り当てられているすべての共有カタログを常に表示できず、保存できないお客様を表示できず、システムに不整合が生じる問題を修正します。
* **ACSD-58325** （Adobe Commerce >=2.4.6 &lt;2.4.7）の場合：検証エラーの後でも&#x200B;**[!UICONTROL Import]** ボタンが使用できる問題を修正します。
* **ACSD-59083** （Adobe Commerce >=2.4.4 &lt;2.5.0の場合） - *の更新が同時に実行されている場合に、一部のデータベース更新操作で* ベーステーブルまたはビューが見つからない[!DNL mview] エラーが発生する問題を修正します。
* **ACSD-61622** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.6-p1 &lt;2.4.7） - [!DNL FedEx]のアカウント固有のレートが応答に欠落している問題を修正します。
* **ACSD-61895** （Adobe Commerce >=2.4.4 &lt;2.5.0の場合） – ルートカテゴリに[!DNL GraphQL]allow **権限がない場合でも、カテゴリ** クエリが&#x200B;**allow**&#x200B;権限を持つカテゴリを返す問題を修正します。
* **ACSD-62212** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.5.0） - **パスワードを忘れた** メールコンテンツがストアビューの言語に翻訳されない問題を修正します。
* **ACSD-62481** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.5.0） - **[!UICONTROL Persistence]**&#x200B;が有効になっている場合でも、顧客のショッピングカートが空になる問題を修正します。
* **ACSD-62629** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.7 &lt;2.5.0） - **[!UICONTROL Widgets]**&#x200B;で使用されている商品リストがカテゴリの条件を反映しない問題を修正します。
* **ACSD-62635** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.7 &lt;2.5.0） - [!DNL GraphQL]商品クエリでマルチストア関連商品が正しく表示されない問題を修正します。
* **ACSD-62671** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.7 &lt;2.5.0） – 最初の試行で[!DNL GraphQL] リクエストが最新のアドレス情報を返さない問題を修正します。
* **ACSD-62689** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.7 &lt;2.5.0） - **[!UICONTROL Related Product Rules and Widgets]**&#x200B;深度4 *の後で*&#x200B;にカテゴリを追加できない問題を修正します。
* **ACSD-62708** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4-p11 &lt;2.4.5 || >=2.4.5-p10 &lt;2.4.6-p2 || >=2.4.6-p8 &lt;2.4.7-p1） – 管理者の7つのエディターフォントサイズに&lt;ph=&#39;152&#39;/>PT&lt;ph=&#39;197&#39;/と&lt;ph>が表示され、&lt;ph> id=&#39;208&#39;/>PX *.***[!DNL TinyMCE]次に、*PT*&#x200B;ではなく&#x200B;*PX*&#x200B;でフォントサイズを設定することもできます。
* **ACSD-62758** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.5.0） - **[!UICONTROL Configurable Product]**&#x200B;の詳細ページで、[!DNL URL]に選択したオプションが含まれている場合に、商品ビデオが正しくレンダリングされない問題を修正します。
* **ACSD-62951** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.5.0） – 項目と合計を含めずにクレジットメモの電子メールが送信される問題を修正します。
* **ACSD-62965** （Adobe Commerce >=2.4.7 &lt;2.5.0の場合） - `LocalizedException` メッセージが注文プレースメント [!DNL GraphQL]応答に含まれていない問題を修正します。
* **ACSD-63286** （Adobe Commerce >=2.4.6 &lt;2.4.7）の場合 – [!DNL API]を介して共有カタログに割り当てられた商品が、手動でインデックス再作成が実行されるまでストアフロントに表示されない問題を修正します。
* **ACSD-63326** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.5.0） – バックエンドから注文を行った後、[!UICONTROL Admin]が壊れたページにリダイレクトされる問題を修正します。
* 更新されたバージョン：**ACSD-51739**
* 置き換えられたパッチ：**MDVA-43451**、**ACSD-62755**

## v1.1.56 {#v1-1-56}

* **ACSD-63244** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.8） - [!DNL JavaScript] エラーにより[!DNL Google Maps]が正しくレンダリングされない問題を修正します。 多くの&#x200B;*Uncaught TypeErrorがある問題を修正します。これは次のとおりです。_eachは* パネルのコンソールの関数[!UICONTROL Admin] エラーではありません。
* **ACSD-63242** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.6-p8 &lt;2.4.7 || >=2.4.7-p3 &lt;2.4.8） - 10,000件を超えるエントリを含むカタログ商品を追加する際の読み込み速度の問題を修正します。
* **ACSD-63062** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.7 &lt;2.4.8） – 複数の重複ルールが適用される場合に誤ったカート割引の計算が発生する問題を修正します。
* **ACSD-62979** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.7） - [!UICONTROL Store ID] ヘッダーで間違った[!DNL GraphQL]を使用すると致命的なメモリエラーが発生する問題を修正します。
* **ACSD-62971** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.8） - **quantity**&#x200B;列の数値を持たないストックソースを読み込むと、**quantity**&#x200B;が&#x200B;*0*&#x200B;に設定される問題を修正します。
* **ACSD-62872** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.8） – スケジュール更新が正しく検証されない一意の属性検証の問題を修正します。
* **ACSD-62755** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4-p11 &lt;2.4.5 |>=2.4.5-p10 &lt;2.4.6 |>=2.4.6-p8 &lt;2.4.7 |>=2.4.7 |>>=2.4.7-p3 &lt;2.4.8） - [!DNL TinyMCE] 7では、エディターの初期設定でフォントサイズとフォントを特別に追加する必要問題が修正されました。
* **ACSD-62670** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4-p11 &lt;2.4.5 |>=2.4.5-p10 &lt;2.4.6 |>=2.4.6-p8 &lt;2.4.7 |>>=2.4.7-p3 &lt;2.4.8） - [!DNL CSV]へのレポート書き出しと&lt;ph=&#39;198&#39;>がエラーを返す問題を修正しました。[!DNL XML]&#x200B;[!UICONTROL Products Ordered]
* **ACSD-62577** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.8） – クエリとテーブルの両方のインデックスを最適化することで、ストアフロント検索クエリのパフォーマンスが低下する問題を修正します。
* **ACSD-62475** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.7 &lt;2.4.8） - [!UICONTROL Gift Card]商品が買い物かごに正しく結合されない問題を修正します。
* **ACSD-62428** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.6 &lt;2.4.7） - `is_out_of_stock`が検索可能な属性として設定されていない場合に、[!DNL SKU]がカタログ検索インデックスで正しくない値に設定される問題を修正します。
* **ACSD-62355** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.6 &lt;2.4.8） – コンフィグ可能な商品が多くの値を持つ多くの属性に基づいている場合に、コンフィグ可能な商品編集ページの読み込み時間を短縮します。
* **ACSD-61805** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.8） - [!DNL REST API]でバックオーダーのステータスを更新した後、ストアフロントで商品が在庫切れのままになる問題を修正します。
* **ACSD-60811** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.7 &lt;2.4.8） – 現在のステータスが&#x200B;*processing*&#x200B;または&#x200B;*fraud*&#x200B;である場合にのみ、カスタム値またはコメントで注文ステータスを更新できる問題を修正します。
* **ACSD-62952** （Adobe Commerce >=2.4.4 &lt;2.4.8の場合） – ストアフロントに[!UICONTROL Gift Registry]日付が不正確に表示される問題を修正します。
* **ACSD-55339** （Adobe Commerce >=2.4.4 &lt;2.4.8）の場合 – 「0」（ゼロ）で始まる商品[!DNL SKU]が「0」を削除し、見積が更新されない問題を修正します。
**
* 更新されたパッチ：**ACSD-59514**
* 更新されたバージョン：**ACSD-60816**
* 置き換えられたパッチ：**ACSD-59967**

## v1.1.55 {#v1-1-55}

* **ACSD-58383** （Adobe CommerceとMagento Open Sourceの場合>=2.4.4 &lt;2.4.8） – 同時に実行される2つの同一リクエストで[!DNL REST API]を介して払い戻しを発行すると、重複したクレジットメモが作成される問題を修正します。
* **ACSD-58471** （Adobe Commerce >=2.4.4 &lt;2.4.8の場合） – 関連するカタログ価格ルールがスケジュールされた場合に、商品の詳細ページで動的コンテンツの読み込みに失敗する問題を修正します。
* **ACSD-58566** （Adobe Commerce >=2.4.6 &lt;2.4.8の場合） - [!DNL GraphQL]のミューテーションで`created_at` フィールドをクエリする際に`addPurchaseOrderComment`が内部サーバーエラーを返す問題を修正します。
* **ACSD-58685** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.8） – メール通信が無効になっている間に開始されたセールスメールが、メール通信が再度有効になった後も送信される問題を修正します。
* **ACSD-58735** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.8） – 制限付き管理者が関連するweb サイトの[!UICONTROL Admin]のお客様アカウントページで放棄されたショッピングカートを表示できない問題を修正します。
* **ACSD-58828** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.6 &lt;2.4.8） – 必要なフィールドが空のままの場合に、クライアントサイドの検証メッセージと共に、サーバーサイドの検証メッセージ *アドレスが必要になる*&#x200B;が表示される問題を修正します。 サーバー側の検証では、空の必須フィールドのメッセージは表示されず、クライアント側の検証ではエラー通知が処理され、*これは必須フィールドです。*
* **ACSD-60344** （Adobe Commerce >=2.4.4 &lt;2.4.8）の場合 – **[!UICONTROL Purchase Order]**&#x200B;を自動承認付きで使用すると、重複した注文確認メールが送信される問題を修正しました。
* **ACSD-61348** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.8） – マルチサイト環境で、ウィッシュリスト項目が[!DNL GraphQL]経由で表示されますが、ストアフロントでは表示されない問題を修正しました。
* **ACSD-61534** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.7 &lt;2.4.8） - `bin/magento config:set` コマンドを使用してデザイン設定を設定できず、ロックされた値がフォーム操作によって変更される可能性がある問題を修正します。 [!DNL CLI]または`--lock-env`で`--lock-conf`から設定されたロックされた値を更新できなくなりました。
* **ACSD-61785** （Adobe Commerce >=2.4.4 &lt;2.4.8の場合） - `reward_warning_notification`属性の更新が[!DNL GraphQL]の突然変異と[!DNL REST API]の呼び出しによって可能ではなかった問題を修正し、その動作を`reward_update_notification`に合わせます。
* **ACSD-62591** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.7 &lt;2.4.8） - **[!UICONTROL User Agent Rules]**&#x200B;が設定されている場合にテーマが正しく切り替わらない問題を修正しました。
* **ACSD-62793** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.7 &lt;2.4.8） – 書き出されたデータ内の`datetime`属性に時間コンポーネントが含まれていない問題を修正します。 さらに、**[!UICONTROL Fields Enclosure]**&#x200B;が&#x200B;*enabled*&#x200B;の場合、`additional_attributes`列の属性値は二重引用符で囲まれます。
* **ACSD-62332** （Adobe Commerce >=2.4.6 &lt;2.4.7）の場合 – [!DNL GraphQL] クエリが10,000個の商品の`total_count`に制限されていた問題を修正します。 [!DNL Live Search]が&#x200B;*を介してクエリを実行した場合に、検索条件で現在のページを* 2 *ではなく* 1[!DNL GraphQL]に設定する問題を修正しました。
* 更新されたバージョン：**ACSD-46581**、**ACSD-49513**、**ACSD-52801**、**ACSD-59514**
* 置き換えられたパッチ：**ACSD-52801**、**ACSD-55100**
* 非推奨のパッチ：**ACSD-52085**、**ACSD-57854**

## v1.1.54 {#v1-1-54}

* **AC-13283** （Adobe CommerceおよびMagento Open Source 2.4.6-p8の場合） - 2.4.6-p8に含まれている下位互換性のない変更内容を元に戻します。
* **ACSD-60267** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.8） - FPTを含むシンプルな商品をカートに直接追加する際に固定商品税（FPT）が正しく適用されますが、設定可能な商品オプションを通じてこれらの商品を選択する際に失敗する問題を修正します。
* **ACSD-61103** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.6 &lt;2.4.7） – お客様がAPI エンドポイントを介して正常にログインした後、`customer_entity` テーブルのエラー数が0にリセットされない問題を修正します。
* **ACSD-61134** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.7） – 買い物客が[!DNL Braintree Vault] チェックボックスの選択を解除して請求先住所を更新すると、チェックアウトワークフローで&#x200B;*[!UICONTROL My billing and shipping address are the same]*&#x200B;支払い方法が自動的に選択解除される問題を修正します。
* **ACSD-61199** （Adobe Commerce >=2.4.4 &lt;2.4.8）の場合） – 既存の階層を持つCMS ページを編集する際に、「CMS page hierarchy」タブに適切なツリー構造が表示されない問題を修正しました。
* **ACSD-61200** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.8） – セールスの&#x200B;*[!UICONTROL Total Amount]*&#x200B;と&#x200B;*[!UICONTROL Total Amount Actual]*&#x200B;の計算に&#x200B;*[!UICONTROL Discount Tax Compensation Amount]*&#x200B;と&#x200B;*[!UICONTROL Shipping Discount Tax Compensation Amount]*&#x200B;が欠落し、受注データに矛盾が生じる問題を修正します。
* **ACSD-61522** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.8） – ゲスト顧客の&#x200B;*[!UICONTROL First Name]*&#x200B;および&#x200B;*[!UICONTROL Last Name]* フィールドに電子メールアドレスを入力して、無効な注文確認メールを送信できる問題を修正しました。
* **ACSD-61756** （Adobe Commerce >=2.4.4 &lt;2.4.7）の場合 – `AdvancedSalesRule` フィルターのパフォーマンスが向上します。
* **ACSD-61799** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.5） – 固定割引を含む複数の買い物かごルールが見積もりに適用される場合に、合計割引が誤って計算される問題を修正します。
* **ACSD-61845** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.7-p1 &lt;2.4.8） - *text/html* accept headerのみを使用してリクエストを送信すると発生するエラーを修正します。
* **ACSD-62056** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.8） - MSIがインストールされている場合に、設定可能な製品の画像のアップロードが失敗する問題を修正します。
* **ACSD-62485** （Adobe Commerce >=2.4.4 &lt;2.4.6-p8 || >=2.4.7 &lt;2.4.8）は、企業が作成されたときに`async.operations.all` コンシューマーが機能しなくなる問題を修正します。
* 更新されたバージョン：**ACSD-48661**、**ACSD-55100**、**ACSD-61553**
* 非推奨のパッチ：**ACSD-51846**

## v1.1.53 {#v1-1-53}

* **ACSD-48318** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.7） – 環境エミュレーションのネストが許可されない問題を修正します。 これで、`send()`呼び出しの間にエミュレーションが停止すると、エミュレーションは`getInfoBlockHtml()`呼び出しの間に開始されます。
* **ACSD-59930** （Adobe Commerce >=2.4.6 &lt;2.4.8の場合） – 会社の&#x200B;**[!UICONTROL Create]**、**[!UICONTROL Save]**、および&#x200B;**[!UICONTROL Delete]** フローのパフォーマンスを向上させます。
* **ACSD-60584** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.5 &lt;2.4.7） – あるWeb サイトでユーザー用に作成されたアクセストークンが、他のWeb サイトの顧客情報にアクセスまたは変更できる問題を修正します。
* **ACSD-60804** （Adobe Commerce >=2.4.4 &lt;2.4.8の場合） – 削除された会社にリンクされているお客様を編集すると、null *で`getSuperUserId()` メンバー関数*&#x200B;への呼び出しが発生する問題を修正します。
* **ACSD-61133** （Adobe Commerceの場合>=2.4.4-p5 &lt;2.4.5 |>=2.4.5-p4 &lt;2.4.6 |>=2.4.6-p2 &lt;2.4.8） - `sales_clean_quotes` [!DNL cron]が未承認の発注から見積もりを削除する問題を修正します。
* **ACSD-61528** （Adobe Commerce >=2.4.6 &lt;2.4.8の場合） - [!UICONTROL Admin]を使用して[!DNL GraphQL]からロールを取得しても結果が返されない問題を修正します。
* **ACSD-61553** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.5 &lt;2.4.7） – 優先度が異なる複数の割引と&#x200B;**[!UICONTROL Cart Price Rule]**&#x200B;が製品に適用された場合に&#x200B;**[!UICONTROL Maximum Qty Discount is Applied To]**&#x200B;割引が誤って計算される問題を修正します。
* **ACSD-61667** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.8） – 実店舗での受け取りを持つ多くのソースの場合、配送を作成する際の在庫パフォーマンスが向上します。
* **ACSD-61969** （Adobe Commerce >=2.4.7 &lt;2.4.8の場合） – クーポンコードが設定されたときと正確に一致するように、大文字と小文字を区別するクーポンコードを入力する必要がある問題を修正しました。
* 更新されたバージョン：**ACSD-54989**、**ACSD-60632**

## v1.1.52 {#v1-1-52}

* **BUNDLE-3375** （Adobe CommerceおよびMagento Open Sourceの場合） - [!DNL Braintree]を支払いゲートウェイとして使用する場合に、3DS VISAの必須フィールドを満たすために必要なすべてのフィールドが追加されます。
* **ACSD-59366** （Adobe Commerce >=2.4.6 &lt;2.4.8の場合） – チームリストに表示されない、非アクティブ化されたユーザーを含むチームを削除しようとしたときにエラーが発生する問題を修正します。
* **ACSD-59865** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.7） – カート内の商品の数量がルールを適用するのに十分でない場合、[!UICONTROL Cart Price Rule]が以前に適用されたルールをキャンセルしない問題を修正します。
* **ACSD-59925** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.8） - [!UICONTROL Media Gallery]の項目をGraphQLの位置で並べ替える際の問題を修正しました。
* **ACSD-59952** （Adobe Commerce >=2.4.4 &lt;2.4.8の場合） – 既存の[!UICONTROL Shared Catalog]に割り当てられたグループ IDで[!UICONTROL Shared Catalog]を作成する際にエラーが発生する問題を修正します。
* **ACSD-60590** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.7） – 大量の注文に対して[!UICONTROL Bestsellers Aggregated Daily Reports]を生成する際のパフォーマンスが向上します。
* **ACSD-60673** （Adobe Commerce >=2.4.4 &lt;2.4.8の場合） – チェックアウト時の複数の支払い方法の[!UICONTROL Cart Price Rule]が特定の支払い方法に適切に適用されない問題を修正します。
* **ACSD-60684** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.6 &lt;2.4.7） – 複数のフィールドによるGraphQL製品の並べ替えが期待どおりに機能しない問題を修正します。
* **ACSD-60788** （Adobe Commerce >=2.4.7 &lt;2.4.8）の場合 – Content Security Policy （CSP）エラーが原因で[!DNL Google Tag Manager]のカスタムスクリプトが実行されない問題を修正します。
* **ACSD-61322** （Adobe Commerce >=2.4.6 &lt;2.4.8の場合） – デフォルト（一般グループ）の[!UICONTROL Products/Categories]に[!UICONTROL Shared Catalog]が割り当てられていない問題が、XML サイトマップに引き続き含まれる問題を修正します。
* **ACSD-61366** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.7 &lt;2.4.8） - DB接続にポートが指定されている場合、`setup:static-content:deploy --jobs 4` コマンドが複数のジョブで実行され、*Portで失敗する問題を修正します。*
* 更新されたパッチ：ACSD-51857、ACSD-57394

## v1.1.51 {#v1-1-51}

* **ACSD-59786** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.6 &lt;2.4.8） – 期限切れの見積もりの見積もりIDを取得しようとすると、GraphQLが内部サーバーエラーを返す問題を修正します。
* **ACSD-60234** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.8） – 支払い方法で割引が適用された場合、[!DNL PayPal]に誤った金額が表示される問題を修正します。
* **ACSD-59967** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.7-p2） - JavaScript エラーによって[!DNL Google Maps]が正しくレンダリングされない問題を修正します。
* **ACSD-60326** （Adobe Commerce >=2.4.4 &lt;2.4.8）のお客様の返品状況に関するGraphQL クエリでエラーが発生する問題を修正します。
* **ACSD-60538** （Adobe Commerce >=2.4.7 &lt;2.4.8）の場合 – *[!UICONTROL All Store Views]*&#x200B;で商品が無効になっていて、特定のストアビュースコープでのみ有効になっている場合、GraphQLの応答に商品属性が正しく表示されず、商品が正しく表示されない問題を修正します。
* **ACSD-60631** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.7 &lt;2.4.8） – 同じ単純な商品が複数の設定可能な商品に割り当てられている場合にGraphQLがエラーを返す問題を修正します。
* **ACSD-60632** （Adobe CommerceおよびMagento Open Source >=2.4.5-p8 &lt;2.4.8）は、注文が正常に作成されたかどうかにかかわらず、注文の配置が試行されるたびに新しいアドレスが保存される問題を修正します。
* **ACSD-60816** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.7） - APM エージェントによって挿入された[!DNL New Relic Browser Monitoring] スクリプトがCSP （Content Security Policy）に準拠しておらず、実行が妨げられる問題を修正します。
* **ACSD-61195** （Adobe CommerceおよびMagento Open Source >=2.4.7 &lt;2.4.8）は、買い物かごGraphQL リクエストの最後のページで買い物かご商品が返されない問題を修正します。
* 更新されたパッチ：ACSD-59378

## v1.1.50 {#v1-1-50}

* **ACSD-59280** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.5） - 2.4.4-pX バージョンのインストール時に発生する&#x200B;*未定義メソッドへの呼び出しReflectionUnionType::getName （）* エラーを修正します。
* **ACSD-45049** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.4-p8 || >=2.4.5 &lt;2.4.6） – 管理者のweb サイトスコープに従って、お客様の&#x200B;*[!UICONTROL Is required]*&#x200B;属性設定が正しく機能しない問題を修正します。
* **ACSD-46938** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.6） - `setup:upgrade`のDB トリガーの再作成のパフォーマンスに関する問題を修正します。
* **ACSD-48210** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.7） – 特定のストアビューで&#x200B;*[!UICONTROL Website Scope]*&#x200B;属性を更新すると、グローバルスコープの属性値が上書きされる問題を修正します。
* **ACSD-54887** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4-p4 &lt;2.4.4-p9 || >=2.4.5-p3 &lt;2.4.5-p8 || >=2.4.6-p1 &lt;2.4.6-p6） – カスタマーセッションの有効期限が切れ、[!UICONTROL Persistent Shopping Cart]が有効になった後にカスタマーショッピングカートがクリアされる問題を修正します。
* **ACSD-58141** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.8） - [!DNL L2 Redis cache]が有効になっていて、お客様が管理者から更新された場合に、ログインしているお客様のストアフロント領域でPHPSESSIDがPOST リクエストで再生成される問題を修正します。
* **ACSD-58352** （Adobe Commerce >=2.4.4 &lt;2.4.7）の場合 – リクエストヘッダーにデフォルト以外のストアビューが指定されている場合に、デフォルトのストアビューの戻り属性ラベルがGraphQL APIを介して返される問題を修正しました。
* **ACSD-58442** （Adobe Commerce >=2.4.4 &lt;2.4.7-p1の場合） – 幅が768pxのデバイスがモバイルとして扱われ、メニューとヘッダーがデスクトップではなくモバイルビューで読み込まれる問題を修正します。
* **ACSD-58790** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.8） - [!DNL Chrome]のモバイルビューで、商品詳細ページの画像にピンチからズームする機能を修正しました。
* **ACSD-59036** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.7 &lt;2.4.8） – 下限と上限の両方が$0に等しい商品の価格を読み込む際に発生する例外を修正します。
* **ACSD-59229** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.7） – リクエストでX-Magento-Varyの古い値が原因で、カスタマーグループに関連する情報が間違ったセグメントに保存される問題を修正します。
* **ACSD-59378** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.5 &lt;2.4.6） – インポート中にストアレベル URLの書き換えが正しく更新されない問題を修正します。
* **ACSD-59514** （Adobe Commerce >=2.4.4 &lt;2.4.7-p2の場合） - [!DNL Page Builder]を持つ管理領域のフォームで、エラー&#x200B;*[!DNL Page Builder]が5秒間ロックを解除せずにレンダリングされていた問題を修正します。フォーム送信後にブラウザーコンソールに*&#x200B;が表示され、変更を保存できません。
* **ACSD-60303** （Adobe Commerce >=2.4.4-p9 &lt;2.4.5 |>=2.4.5-p8 &lt;2.4.6 |>=2.4.6-p6 &lt;2.4.8の場合） - HTMLの縮小が有効になっている場合に管理者からの注文を配置できない問題を修正します。
* **ACSD-60441** （Adobe CommerceおよびMagento Open Source 2.4.4-p9 || 2.4.5-p8 || 2.4.6-p6 || 2.4.7-p1の場合） – バックエンドから生成された統合アクセストークンを使用する場合の`V1/customers` [!DNL REST API] エンドポイントを介した顧客の更新に関する問題を修正します。
* 更新されたパッチ：ACSD-57003

## v1.1.49 {#v1-1-49}

* **ACSD-56979** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.3 &lt;2.4.7） – ステージング更新を削除した後に商品画像が削除される問題を修正します。
* **ACSD-57086** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.3 &lt;2.4.7） – 条件が有効になっているデフォルト以外のweb サイトからの注文が正しく処理されない問題を修正します。
* **ACSD-57588** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.6 &lt;2.4.7） – リージョン ID処理中に複数のアドレスに注文を配送するとエラーがトリガーする問題を修正します。
* **ACSD-57643** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.6 &lt;2.4.7） – カスタムオプションを持つ商品がGraphQL経由でショッピングカートに誤って追加される問題を修正します。
* **ACSD-57846** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.2 &lt;2.4.7） - GraphQL製品がフィルターでゼロ価格で検索しても、例外が原因で結果が返されない問題を修正します。
* **ACSD-57941** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.6 &lt;2.4.7） – 製品オプションがそれぞれのストアではなく管理者ストアに誤って割り当てられる問題を修正します。
* **ACSD-58375** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.2 &lt;2.4.7） – ストアビューレベルで&#x200B;*[!DNL YouTube API Key]* ビデオを追加する際に、間違った[!DNL YouTube]設定がエラーを引き起こす問題を修正します。
* **ACSD-58739** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.7 &lt;2.4.8） – 部分的なインデックス再作成でエラーがスローされる問題を修正します。
* **ACSD-58446** （Adobe Commerce >=2.4.6 &lt;2.4.7）の場合 – ステータス（非アクティブ）に関係なく、子ユーザーまたはチームを含むチームを削除すると、UIと一致しない情報のないエラーメッセージが表示される問題を修正します。
* **ACSD-58054** （Adobe Commerce >=2.4.4 &lt;2.4.6）の場合 – APIを介して非アクティブな顧客の顧客トークンを生成できる問題を修正します。
* **ACSD-58163** （Adobe Commerce >=2.4.3 &lt;2.4.7の場合） – クーポンコードを含まない対応する&#x200B;*[!UICONTROL Cart Price Rule]* カートから&#x200B;*[!UICONTROL Customer Segment]*&#x200B;のゲスト顧客に割引が適用されない問題を修正しました。
* **ACSD-57045** （Adobe Commerce >=2.4.5 &lt;2.4.7）の場合、*[!UICONTROL Website Root]*&#x200B;が&#x200B;*[!UICONTROL Hierarchy]*&#x200B;からオフになった後にURLの書き換えが無限ページループを引き起こす問題を修正します。
* 更新されたパッチ：ACSD-46815、ACSD-47027、ACSD-51683、ACSD-55031、ACSD-51819、ACSD-54965-v2

## v1.1.48 {#v1-1-48}

* **ACSD-55566** （Adobe CommerceとMagento Open Sourceの場合>=2.4.3 &lt;2.4.7） - `mergeCart`のミューテーションが、同じバンドルアイテムを持つソースと宛先のカートをマージする際に&#x200B;*応答の「*&#x200B;内部サーバーエラー[!DNL GraphQL]」で失敗する問題を修正します。
* **ACSD-56546** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.7） - **製品の表示切れ**&#x200B;が&#x200B;**無効**&#x200B;の場合に、ストアフロントで設定可能な製品およびバンドル製品が&#x200B;*在庫切れ*&#x200B;として表示される問題を修正します。
* **ACSD-56635** （Adobe Commerce >=2.4.6 &lt;2.4.7）の場合 – **account sharing**&#x200B;を&#x200B;*Global*&#x200B;に設定してインポートを使用すると、インポートしたお客様が同じ電子メールアドレスで複製される問題を修正します。
* **ACSD-56741** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.6 &lt;2.4.7） – データベースに索引付けメカニズムと関係のないカスタム *トリガーが含まれている場合に*&#x200B;に表示されるエラーメッセージ「`setup:upgrade`型null[!DNL MySQL]」の値で配列オフセットにアクセスしようとしています。[!DNL MView]
* **ACSD-57315** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.2 &lt;2.4.7） – 管理者の[!DNL PayPal Payflow Pro]画面で[!UICONTROL Fetch] ボタンがクリックされるたびに&#x200B;**[!UICONTROL View transaction]**&#x200B;で新しいトランザクションが作成される場合の問題を修正します。
* **ACSD-57337** （Adobe Commerce >=2.4.4 &lt;2.4.6の場合） – 特定のweb サイトへのアクセス制限を持つ管理者ユーザーが、**[!UICONTROL Companies]** グリッド内のすべてのweb サイトから企業を表示できる問題を修正します。
* **ACSD-57394** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.7） - [!DNL GraphQL]の複数の並べ替えフィールドで誤った商品の並べ替えを行う問題を修正します。
* **ACSD-57565** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.6 &lt;2.4.7） - **[!UICONTROL Order]** ダッシュボードに誤った注文情報が表示される問題を、期間が更新されるまで修正します。 ダッシュボードに、最初のロードで正しい注文統計が表示されるようになりました。
* **ACSD-57854** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.5 &lt;2.4.7） – 製品[!DNL GraphQL]要求がカテゴリ集計で無効なカテゴリを返した場合の問題を修正します。
* **ACSD-58008** （Adobe Commerce >=2.4.5 &lt;2.4.7）は、終了日が指定されていない場合に、スケジュールされた更新を更新すると、ステージング済みアイテムの以前のバージョンが削除される問題を修正します。
* 更新されたパッチ：MDVA-39305-V2、ACSD-48627、ACSD-54965

## v1.1.47 {#v1-1-47}

* **ACSD-55241** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.2 &lt;2.4.7） - *[!UICONTROL Used]*&#x200B;および&#x200B;*[!UICONTROL Times Used]*&#x200B;属性で、複数のアドレスを持つチェックアウト時に生成されたクーポンに誤った値が表示される問題を修正します。
* **ACSD-56760** （Adobe Commerce >=2.4.6 &lt;2.4.7）の場合、特定のweb サイトに制限された管理者ユーザーが、web ストアに独自のルートカテゴリがある場合に、カテゴリ内で新製品を並べ替えたり追加したりできない問題を修正します。
* **ACSD-56858** （Adobe Commerce >=2.4.2 &lt;2.4.7）の場合：制限された会社管理者に対してB2B会社のロール権限が正しく表示されない問題を修正します。
* **ACSD-57074** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.6 &lt;2.4.7） - *で始まる*&#x200B;の`attrbute_code`はい/いいえ`price_` カスタム属性がインデックス作成で正しく機能せず、そのような属性を持つ商品がフロントエンドで利用できない問題を修正します。
* 更新されたパッチ：ACSD-53378、ACSD-51819

## v1.1.46 {#v1-1-46}

* **ACSD-46767** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.6） – 在庫量が変更されたときに、商品がまだ在庫がある場合でも、カテゴリーページのキャッシュが無効になる問題を修正します。
* **ACSD-54656** （Adobe Commerce >=2.4.5 &lt;2.4.6）は、チェックアウト時に非表示のRecaptchaが失敗し、注文が行われない問題を修正します。
* **ACSD-55100** （Adobe Commerce >=2.4.6 &lt;2.4.7）の場合 – GraphQLで検索結果に10,000個を超える商品が返されない問題を修正します。
* **ACSD-56621** （Adobe Commerce >=2.4.2 &lt;2.4.7）の場合、更新された名と姓が、会社管理者ユーザーの「挨拶」ヘッダーのセクションに反映されない問題を修正します。
* **ACSD-56842** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.2 &lt;2.4.7） - `setup:di:compile`を実行した後、遅延プロキシと遅延プロキシ ファクトリが見つからない問題を修正します。
* **ACSD-57003** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.6 &lt;2.4.7） – 注文の一部が返金され、部分的に発送された場合に、注文ステータスが&#x200B;*[!UICONTROL Complete]*&#x200B;に変更されるのではなく、*[!UICONTROL Processing]*&#x200B;に変更される問題を修正します。
* 更新されたパッチ：ACSD-50260-v2、ACSD-54966

## v1.1.45 {#v1-1-45}

* **ACSD-56886** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.2 &lt;2.4.7） – スケジュールされた更新によって2つの子商品のうちの1つが無効になった場合に、設定可能な商品が在庫切れになる問題を修正します。
* **ACSD-56616** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.5 &lt;2.4.6） – バンドルされた商品が、シンプルな商品の在庫がなくなったときにストアフロントに在庫として表示される問題を修正します。
* **ACSD-56515** （Adobe Commerce >=2.4.2 &lt;2.4.7）は、web サイトレベルの権限を持つ管理者が動的ブロックを追加または編集できない問題を修正します。
* **ACSD-56447** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.2 &lt;2.4.7） – 同じ商品を並行するREST Web API リクエストを介してカートに追加すると、カート内で2つの商品が別々に表示される問題を修正しました。
* **ACSD-56415** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.5 &lt;2.4.7） – データベースにインデックスの部分価格データが多い場合に、`DELETE` クエリが原因で部分価格インデックスのパフォーマンスが低下する問題を修正します。
* **ACSD-54965** （Adobe Commerce >=2.4.5 &lt;2.4.6）商品がカスタム在庫のみに割り当てられている場合、ビジュアルマーチャンダイジンググリッドに正しい在庫が表示されない問題を修正しました。
* **ACSD-52824** （Adobe Commerce >=2.4.5 &lt;2.4.7）の場合 – PayPal Express、Google Pay、Apple Payの各ボタンが会社のお客様に表示される問題を修正しました。
* 更新されたパッチ：ACSD-56193

## v1.1.44 {#v1-1-44}

* **ACSD-56790** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.6 &lt;2.4.7） - **Move out of Stock to bottom** オプションを使用してカテゴリ商品を並べ替えると、ユーザーが管理者ダッシュボードにリダイレクトされ、画面の上部に`Invalid security or form key. Please refresh the page` エラーが表示される問題を修正します。
* **ACSD-56280** （Adobe Commerce >=2.4.4 &lt;2.4.7）は、ギフトレジストリから商品を注文すると例外が発生する問題を修正します。
* **ACSD-56246** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.6 &lt;2.4.7） – 製品のスケジュールされた更新がアクティブになったときに、カスタムの複数選択属性からデータが削除される問題を修正します。
* **ACSD-56193** （Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.4の場合） – ページビルダーを使用してカテゴリ説明でスケジュールされたブロックを使用すると、Varnish/Fastly キャッシュが更新されない問題を修正します。
* **ACSD-56158** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.5 &lt;2.4.7） – 「買い物かご」クエリが各税規則の合計税額を返す問題を修正します。
* **ACSD-56023** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.2 &lt;2.4.7） – キャッシュが有効になっている場合に、CMS ページでウィジェットコンテンツが更新されない問題を修正します。
* **ACSD-55427** （Adobe Commerce >=2.4.5 &lt;2.4.7）の場合 – Admin ユーザーがAdminの商品ページから共有カタログから商品の割り当てを解除できない問題を修正します。
* **ACSD-55352** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.2 &lt;2.4.7） – 顧客報酬ポイントを含む部分的なクレジットメモを作成した後、注文状況が「クローズ」に変更され、クレジットメモのオプションが「管理者注文」ページから消える問題を修正します。
* **ACSD-55231** （Adobe Commerce >=2.4.2 &lt;2.4.7）の場合 – クイック注文機能を使用して商品をカートに追加できない問題を修正します。
* **ACSD-54283** （Adobe Commerce >=2.4.3 &lt;2.4.4の場合） – デフォルト（一般グループ）のShared Catalogに割り当てられていない製品/カテゴリが、XML サイトマップにまだ含まれている問題を修正します。
* 更新されたパッチ：ACSD-52041、ACSD-54040、ACSD-51819

## v1.1.43 {#v1-1-43}

* **ACSD-54972** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.2 &lt;2.4.7） – カテゴリ URLを変更した後、正規カテゴリ URLが更新されない問題を修正します。
* **ACSD-53636** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.3 &lt;2.4.5） – 特別価格の子商品を持つ設定可能な商品の商品リストページに通常価格が表示されない問題を修正しました。
* **ACSD-54885** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.2 &lt;2.4.7） – 管理者ユーザーが&#x200B;*お客様としてログイン*&#x200B;機能を使用している場合の複数アドレス チェックアウトの問題を修正します。
* **ACSD-55610** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.7） – 部分的にキャンセルされた注文に誤った割引金額が含まれる問題を修正します。
* **ACSD-55334** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.3 &lt;2.4.7） - GraphQL応答の翻訳辞書を使用したラベルの翻訳を修正します。
* **ACSD-54739** （Adobe Commerce >=2.4.5 &lt;2.4.7）の場合：関連する製品ルールに対して製品在庫ステータス条件が適用されない問題を修正します。
* **ACSD-53925** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.2 &lt;2.4.7） - `catalog_product_price` dimensions-modeが&#x200B;*web サイト*&#x200B;に設定されている場合に、管理者が製品カルーセルを使用してCMS ブロックを保存できない問題を修正します。
* **ACSD-52714** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.2 &lt;2.4.7） – 日付書式が&#x200B;*Y-m-d*&#x200B;に設定されている場合に、日付フィルターが管理者グリッドで機能しない問題を修正します。
* **ACSD-55055** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.2 &lt;2.4.7） – ショッピングカートの価格規則に商品属性を読み込む際のパフォーマンスが向上します。
* **ACSD-53790** （Adobe Commerce >=2.4.6 &lt;2.4.7）の場合 – 1つのプロダクトに対する複数のRMAをREST APIで作成できる問題を修正しました。
* **ACSD-56090** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.2 &lt;2.4.5） - GraphQL リクエストが、特定のストアデータではなく、すべてのストアのデータで応答する問題を修正します。
* **ACSD-54983** （Adobe Commerce >=2.4.2 &lt;2.4.7）の場合 – ユーザーステータスが&#x200B;*[!UICONTROL Inactive]*&#x200B;に設定されている場合、GraphQL リクエストで会社ユーザーのUIDを取得できない問題を修正しました。
* **ACSD-53309** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.2 &lt;2.4.7） – カスタマイズ可能なオプションが選択されている場合に、*[!UICONTROL Regular Price]* ラベルで税金が完全に適用されない問題を修正します。
* **ACSD-55305** （Adobe Commerce >=2.4.4 &lt;2.4.7）の場合 – *[!UICONTROL Edit Company User]* > **[!UICONTROL myAccount]** ページの&#x200B;**[!UICONTROL Company Structure]** ポップアップが画面のローダーでフリーズする問題を修正しました。
* 更新されたパッチ：ACSD-49013

## v1.1.42 {#v1-1-42}

* **ACSD-53658** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.7） – ストアビューで&#x200B;*[!UICONTROL Recently Viewed]*&#x200B;商品データが正しく更新されない問題を修正します。
* **ACSD-54626** （Adobe Commerce >=2.4.6 &lt;2.4.7）の場合 – `createPurchaseOrderApprovalRule`を介して`NUMBER_OF_SKUS`属性を持つ新しい発注ルール （[!DNL GraphQL]）を作成できない問題を修正します。
* **ACSD-53845** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.0 &lt;2.4.7） - [!DNL MySQL] = 0の場合の`consumer max_messages`接続タイムアウトの問題を修正します。
* **ACSD-54890** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.0 &lt;2.4.7） - `aggregate_sales_report_bestsellers_data` ディスクの空き容量が不足しているために[!DNL MySQL]が`/tmp` エラーを引き起こす問題を修正します。
* **ACSD-55112** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.0 &lt;2.4.7） - *[!UICONTROL Submit review]* ボタンを[!DNL Google reCAPTCHA v3]検証なしで複数回クリックできる問題を修正します。
* **ACSD-54264** （Adobe Commerce >=2.4.4-p5 &lt;2.4.5 |>=2.4.5-p4 &lt;2.4.6 |>=2.4.6-p2 &lt;2.4.7）の場合） – エラーメッセージ *「リクエストされた属性を更新できません」という問題を修正します。 お客様が別のストアビューから交渉可能な見積もりを使用してチェックアウトしようとすると、行ID: store_id&quot;*&#x200B;が表示されます。
* **ACSD-54418** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.0 &lt;2.4.7） – 動的に価格が設定されたバンドルの各子商品に固定額の割引が誤って適用される問題を修正します。
* **ACSD-55238** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.7） – 空の商品&#x200B;*[!UICONTROL Meta Description]*&#x200B;を保存する際の問題を修正しました。
* **ACSD-54966** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.5 &lt;2.4.7） – 以前の注文が失敗した場合、お客様ごとに使用制限のあるクーポンコードを再利用できない問題を修正します。
* **ACSD-54060** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.3 &lt;2.4.7） – 制限付き管理者が、別のスコープに割り当てられた別の製品の子である場合に、製品を保存できない問題を修正します。
* **ACSD-48910** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.5 &lt;2.4.6） – 注文が請求され、発送された後、ゼロ以外の数量であっても、複数のソースに割り当てられたバンドル商品が在庫切れになる問題を修正しました。
* **ACSD-55381** （Adobe Commerce >=2.4.2 &lt;2.4.7）の場合 – `configurable_product_option_uid` `configurable_product_option_value_uid`から[!DNL B2B]経由で&#x200B;*[!UICONTROL Requisition list]*&#x200B;および[!DNL GraphQL] フィールドをクエリする際の内部サーバーエラーを修正しました。
* **ACSD-55628** （Adobe Commerce >=2.4.4-p2 &lt; 2.4.5 || >=2.4.5-p1 &lt; 2.4.6の場合） – 会社登録フォームにファイルをアップロードし、ストアフロントの顧客属性のファイルを置き換える際の問題を修正しました。
* 更新されたパッチ：ACSD-51240、ACSD-51890、ACSD-53098

## v1.1.41 {#v1-1-41}

* **ACSD-54376** （Adobe Commerce >=2.4.2 &lt;2.4.7）は、既に買い物かごに追加された後に商品が共有カタログから削除されたときに、買い物かごで発生する問題を修正します。
* **ACSD-53722** （Adobe Commerce >=2.4.4 &lt;2.4.7）は、異なるスコープのスケジュールされた更新がアクティブになると、バンドルされた製品オプションの価格が$0に変わる問題を修正します。
* **ACSD-53643** （Adobe Commerce >=2.4.3 &lt;2.4.7）の場合：無効な商品または在庫切れの商品で発注する際に、注文の合計数が正しくない問題を修正します。 このような発注の&#x200B;*[!UICONTROL Place Order]* ボタンを非表示にすることで修正されます。
* **ACSD-54067** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.0 &lt;2.4.7） – モバイルデバイスで商品ビデオが再生されない問題を修正します。
* **ACSD-55414** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.0 &lt;2.4.6） - MariaDBがEAV entity_idを文字列から整数にキャストしようとすると、パフォーマンスが向上します。
* **ACSD-51819** （Adobe Commerce >=2.4.4 &lt;2.4.4-p4の場合） – 同じ見積もりIDで複数の注文を配置できる問題を修正します。
* **ACSD-53118** （Adobe Commerce >=2.4.0 &lt;2.4.7）の場合、商品に空の属性が含まれている場合に&#x200B;*[!UICONTROL Cart Price Rule]*&#x200B;がクーポンコードを使用して適用され、ルールが無効化される問題を修正します。
* **ACSD-54324** （Adobe Commerce >=2.4.5 &lt;2.4.7）の場合 – GraphQL requisition_lists リクエストでページネーション設定が考慮されず、すべての結果が返される問題を修正します。
* 更新されたパッチ：MDVA-42855-v2

## v1.1.40 {#v1-1-40}

* **ACSD-54680** （Adobe Commerce >=2.4.0 &lt;2.4.6の場合） – 複数の割り当てられたソースを持つ商品に対して送信されたB2B見積もりを処理できない問題を修正します。
* **ACSD-54040** （Adobe Commerce >=2.4.4-p5 &lt;2.4.5 || >=2.4.5-p4 &lt;2.4.6）の場合 – B2B モジュールが有効になっている場合に、*[!UICONTROL Created]* フィールドが詳細で空白になる問題を修正します。
* **ACSD-54319** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.2 &lt;2.4.6） - *[!UICONTROL Product in Cart]* レポートで商品の価格がゼロになる問題を修正します。
* **ACSD-53378** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.5 &lt;2.4.7） – 大規模なアドレス帳を持つお客様のチェックアウトページの読み込み時間を短縮します。
* **ACSD-52657** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.5 &lt;2.4.7） – サブドメインを使用するセカンダリストアビューでミニカートが更新されない問題を修正します。
* **ACSD-53414** （Adobe Commerce >=2.4.6 &lt;2.4.7）の場合） – 制限付き管理者ユーザーが権限の範囲外のCMS ページを表示できる問題を修正します。
* **ACSD-54472** （Adobe Commerce >=2.4.6 &lt;2.4.7）は、拒否された会社のお客様が認証を行うことができ、ブロックされた会社と拒否された会社のお客様が注文を行うことができる問題を修正します。 このパッチでは、GraphQL エンドポイントの検証が追加されます。
* **ACSD-52801** （Adobe CommerceとMagento Open Sourceの場合>=2.4.4 &lt;2.4.7） - GraphQLで商品を検索する際に部分的に一致するオプションを追加します。
* **ACSD-55004** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.6 &lt;2.4.7） - `php.ini`で設定された値よりも大きいインポートファイルをアップロードする際にバリデーターがクラッシュする問題を修正します。
* **ACSD-54989** （Adobe Commerce >=2.4.4-p5 &lt;2.4.5 |>=2.4.5-p4 &lt;2.4.6 |>=2.4.6-p2 &lt;2.4.7） - *[!UICONTROL Enable Purchase Orders]*&#x200B;が&#x200B;*[!UICONTROL Yes]*&#x200B;に設定され、*[!UICONTROL Purchase Order]*&#x200B;が&lt;ph id=&#39;196&#39;/に設定されている場合に会社管理者が注文できない問題を修正しました。*[!UICONTROL No]*
* **ACSD-54007** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.0 &lt;2.4.7） – カスタマーデータの読み込みに関する&#x200B;*「未定義の配列キー&quot;_scope&quot;*」のエラーを修正します。
* **ACSD-55031** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.5 &lt;2.4.6） – コンパイル中に&#x200B;*Type &quot;mixed&quot;をnullにできない* エラーが修正されました。
* **ACSD-54961** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.0 &lt;2.4.7） – 制限付き管理者ユーザーが&#x200B;*Product Review* ステータスを一括更新できない問題を修正します。
* **ACSD-55256** （Adobe CommerceおよびMagento Open Source >=2.4.6 &lt;2.4.7）の場合） – 最初の画像のみが画像スライダーに正常に表示される問題を修正します。
* 更新されたパッチ：ACSD-52041、ACSD-54106

## v1.1.39 {#v1-1-39}

* **ACSD-53704** （Adobe Commerce >=2.4.0 &lt;2.4.7）の場合：報酬ポイントの有効期限が切れた後、報酬ポイントの残高の履歴が誤って計算される問題を修正します。
* **ACSD-53583** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.7） - *カテゴリー製品*&#x200B;および&#x200B;*製品カテゴリー*&#x200B;のインデクサーの部分的なインデックス再作成機能を向上させます。
* **ACSD-54026** （Adobe Commerce >=2.4.6 &lt;2.4.7）の場合：権限のないユーザーに対する`updateCompanyRole` GraphQL リクエストの誤ったエラーメッセージを修正します。
* **ACSD-54106** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.1 &lt;2.4.5） – トルコ語のアクセント文字の名前によるカテゴリ商品の並べ替えが正しくない問題を修正します。
* **ACSD-52219** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.5 &lt;2.4.7） – ブックマークビューを頻繁に切り替えると、管理者グリッドが保存したフィルターが期待どおりに機能しない問題を修正します。
* **ACSD-54342** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.0 &lt;2.4.7） – 有効なデータを含まないCSV ファイルを読み込む際に、誤ったエラーメッセージ *データ構造内のエラーが混在する*。
* **ACSD-54660** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.6） - GraphQLのお客様の注文を&#x200B;*および*&#x200B;で並べ替えるために、新しい入力属性`sort_field`sort`sort_direction`を追加しました。
* **ACSD-54776** （Adobe Commerce >=2.4.5 &lt;2.4.7の場合） - 2番目のweb サイト、ストア、ストアビューで、チェックされていない&#x200B;*[!UICONTROL Use Default Value]*&#x200B;とデフォルト以外の製品フィールド値が保存されない問題を修正しました。
* **ACSD-53998** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4-p2 &lt;2.4.5 || >=2.4.5-p1 &lt;2.4.7） - **[!UICONTROL Dynamic Block]**&#x200B;に基づく&#x200B;**[!UICONTROL Customer Segment]**&#x200B;がお客様のアカウントからログアウトした後に正しく機能しない問題を修正します。
* **ACSD-53204** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.6 &lt;2.4.7） - *商品を保存できない問題を修正しました。* エンドポイントを使用して製品ギャラリーに画像を追加する同時要求を行うと、`rest/V1/products/<sku>/media` エラーが発生します。
* **ACSD-47657** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.7） - AWS資格情報のキャッシュメカニズムを追加しました。 認証情報プロバイダーは、EC2設定のためにAWSから取得した認証情報をキャッシュするために、Magento キャッシュを使用するようになりました。
* 更新されたパッチ：ACSD-51984、ACSD-51574。

## v1.1.38 {#v1-1-38}

* **ACSD-53098** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.3 &lt;2.4.4） – 部分的なインデックスが実行されたときに、共有カタログに割り当てられた商品がストアフロントに表示されない問題を修正します。
* **ACSD-54018** （Adobe CommerceおよびMagento Open Sourceの場合>=2.3.7 &lt;2.4.6） – ウィジェット条件で非大域属性を使用する[!UICONTROL Product List] ウィジェットのパフォーマンスの問題を修正します。
* **ACSD-54111** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.2 &lt;2.4.6） – 透かし画像の縦横比が商品画像と一致しない場合に、商品のサムネイル画像がストアフロントに表示されない問題を修正します。
* **ACSD-47669** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.2 &lt;2.4.6） - *完全性制約の違反：1452子行を追加または更新できない：製品CSVの読み込み時に外部キー制約が失敗する* エラーを修正します。
* **ACSD-53347** （Adobe CommerceおよびMagento Open Sourceの場合>=2.3.7 &lt;2.4.7） – 価格インデクサーの実行に時間がかかる問題を修正します。
* **ACSD-52287** （Adobe Commerce >=2.3.7 &lt;2.4.7の場合） – 非同期グリッドインデックス作成が有効になっている場合に、アーカイブされた注文グリッドで誤った注文ステータスが発生する問題を修正します。
* **ACSD-52929** （Adobe CommerceおよびMagento Open Sourceの場合>=2.3.7 &lt;2.4.7） – インベントリインデクサーが非同期モードで設定されている場合に、デフォルトのソース項目をインデックス再作成する冗長なリクエストに関する問題を修正します。
* **ACSD-53824** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.7） - `UpdateMultiselectAttributesBackendTypes`移行データ パッチが`setup:upgrade`中にデータベース トランザクション サイズの制限を超える問題を修正します。

## v1.1.37 {#v1-1-37}

* **ACSD-52613** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.6 &lt;2.4.7） - REST APIによって`Inventory_source`項目に更新が行われない場合でも、キャッシュとインデックスが更新される問題を修正します。
* **ACSD-51884** （Adobe CommerceおよびMagento Open Sourceの場合>=2.3.7 &lt;2.4.7） – 「サイズ変更」コマンドを実行した後にproduct image cache pathが正しくない問題を修正します。
* **ACSD-53628** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.4.7）の場合） - CSV販売注文レポートに誤った特殊文字が表示される問題を修正します。
* **ACSD-53148** （Adobe CommerceとMagento Open Sourceの場合>=2.4.4 &lt;2.4.7） - GraphQLで同じ設定可能な商品をカートに追加するために2つの並行要求が行われ、同じ商品SKUを持つカート上で2つの商品が別々の商品になった問題を修正します。
* **ACSD-52606** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.0 &lt;2.4.7） – ユーザーが&#x200B;*をクリックすると、*&#x200B;ご注文の受け取り準備ができていません&#x200B;**[!UICONTROL Notify Order is Ready for Pickup]**&#x200B;というエラーメッセージが表示される問題を修正します。
* **ACSD-51574** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.2 &lt;2.4.7） – 同じ名前の別の画像に置き換えた後、フロントエンドで画像が更新されない問題を修正します。
* **ACSD-53728** （Adobe CommerceおよびMagento Open Sourceの場合>=2.3.7 &lt;2.4.7） – 製品のEAV インデクサーが完了するのに時間がかかる問題を修正します。
* **ACSD-53979** （Adobe CommerceおよびMagento Open Source >=2.4.6 &lt;2.4.7）の場合、ウェルカムメッセージに引用符が1つ含まれている場合にホームページで発生するJSの問題を修正します。
* **ACSD-52085** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.5 &lt;2.4.7） – 製品のカルーセルに特別価格の設定可能な製品が表示されない問題を修正します。
* **ACSD-53795** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.2 &lt;2.4.7） - `indexer_update_all_views` cron ジョブの無効なデータ型の問題を修正します。
* **ACSD-52143** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.6 &lt;2.4.7） – 製品の読み込み後にカスタムオプションが削除される問題を修正します。
* **ACSD-53750** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.7） – マルチスレッド *のインデックス再作成中に* パイプが壊れているか、接続が閉じられている`catalog_product_price` エラーが発生する問題を修正します。
* **ACSD-49843** （Adobe CommerceおよびMagento Open Sourceの場合>=2.3.7 &lt;2.4.0 |>=2.4.1 &lt;2.4.7） – 注文した商品が&#x200B;**[!UICONTROL Payment Action]** = **[!UICONTROL Sale]**&#x200B;設定を有効にしてオンライン決済方法で自動請求された後、商品のダウンロード時にリンクが利用できない問題を修正します。
* **ACSD-47054** （Adobe Commerce >=2.4.2 &lt;2.4.6）は、すべてのストアでプレビューのインデックス再作成が実行され、速度が低下する問題を修正します。
* ACSD-46541、ACSD-47079の新しいバージョンを追加しました。
* ACSD-49970-v3はACSD-54095に置き換えられました。

## v1.1.36 {#v1-1-36}

* **ACSD-53239** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.3 &lt; 2.4.6） – インベントリインデクサーが「スケジュールに従って更新」モードのすべてのキャッシュをクリーニングする問題を修正します。
* **ACSD-50887** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.0 &lt;2.4.7） - *[!UICONTROL Use in Search Results Layered Navigation]* オプションを&#x200B;*Yes*&#x200B;に設定せずに、product属性プロパティ *[!UICONTROL Use in search]*&#x200B;を&#x200B;*Yes*&#x200B;に設定できる問題を修正しました。
* **ACSD-51846** （Adobe CommerceおよびMagento Open Source >=2.4.3-p2 &lt;2.4.6の場合） - REST API ペイロードのすべてのレベルが検証されないために発生する&#x200B;*内部エラー*&#x200B;の問題を修正します。
* **ACSD-52906** （Adobe Commerce >=2.3.7 &lt;2.4.7の場合） – 同じカスタマーセグメントに属するログイン顧客に対して、X-Magento-Vary Cookieが誤って設定され、一部のページでキャッシュが不適切になる問題を修正します。
* **ACSD-52736** （Adobe CommerceおよびMagento Open Sourceの場合>=2.3.7 &lt;2.4.6） – 設定可能な商品数量の要件を含む&#x200B;*カート価格規則*&#x200B;が期待どおりに機能しない問題を修正します。
* **ACSD-47875** （Adobe CommerceおよびMagento Open Sourceの場合>=2.3.7 &lt;2.4.7） – 管理者ユーザーが、在庫管理を使用して特定のストアビュースコープの管理者から顧客カートに商品を追加できない問題を修正します。
* **ACSD-53176** （Adobe Commerce >=2.3.7 &lt;2.4.5の場合） - *の*&#x200B;関連製品ルール *が*&#x200B;条件の1つに一致しない問題を修正します。
* **ACSD-51666** （Adobe CommerceおよびMagento Open Sourceの場合>=2.3.7 &lt;2.4.7） - *セッションの有効期限が切れているため、再度ログインしてください。顧客がログインしようとすると発生する*。
* MDVA-39305-v2の新しいバージョンを追加しました。
* ACSD-19640の要件を更新しました。

## v1.1.35 {#v1-1-35}

* **ACSD-51899** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.0 &lt;2.4.7） – チェックアウトの配送手順のデフォルトの配送先住所に、以前に選択した実店舗の受け取り先住所が自動入力される問題を修正します。
* **ACSD-52041** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.7） – エラーメッセージ「*[ERROR] [!DNL Page Builder]」が5秒間ロックを解除せずにレンダリングされていた問題を修正しました。*&#x200B;で編集したコンテンツを保存すると、[!DNL Page Builder]がChrome ブラウザーに表示されます。
* **ACSD-52095** （Adobe CommerceおよびMagento Open Sourceの場合>=2.3.7 &lt;2.4.6） – 製品の書き出し後にCSV ファイルで`manage_stock`値が誤って0に設定された問題を修正します。
* **ACSD-51358** （Adobe Commerce >=2.4.5 &lt;2.4.7）は、終了日なしでスケジュールされた更新を削除すると、同じエンティティの他のスケジュールされた更新が削除される問題を修正します。
* **ACSD-48070** （Adobe Commerce >=2.3.7 &lt;2.4.7）の場合 – スケジュールされた更新を編集すると例外がトリガーされる問題を修正します。
* **ACSD-51890** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.0 &lt;2.4.7） - [!UICONTROL Submit review] ボタンを[!DNL Google reCAPTCHA] v3検証なしで複数回クリックできる問題を修正します。
* **ACSD-51984** （Adobe Commerce >=2.4.5 &lt;2.4.7）の場合 – 2番目のweb サイト、ストア、ストアビューで、チェックされていない&#x200B;*[!UICONTROL Use Default Value]*&#x200B;と&#x200B;*[!UICONTROL non-default product field]*&#x200B;の値が保存されない問題を修正しました。
* **ACSD-52398** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.0 &lt;2.4.7） – ストアフロントのカート内の同梱商品の数量を更新しようとしたときに発生するエラー&#x200B;*要求された数量が利用できない*&#x200B;を修正します。
* **ACSD-52786** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.5 &lt;2.4.6） – カタログ ルール条件&#x200B;*SKUが*&#x200B;である問題が、指定されたSKUで始まるすべての商品に適用される問題を修正します。
* **ACSD-52921** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.5 &lt;2.4.7） – カートに在庫切れの設定可能な商品がある場合に、GraphQLからカートの詳細をリクエストする際に内部エラーが発生する問題を修正します。
* **ACSD-51683** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.6 &lt;2.4.7） - GraphQLを使用してカスタマイズ可能なオプションをカートに追加できない問題を修正します。
* **ACSD-52133** （Adobe CommerceおよびMagento Open Source >=2.4.6 &lt;2.4.7）の場合） – アップグレード後にお客様のアカウントを保存できない問題を修正します。
* **ACSD-52202** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.3 &lt;2.4.7） – 注文フルフィルメントでデフォルト以外の在庫が0 qtyに変更された場合に、デフォルト在庫の販売可能数量が誤って0に変わる問題を修正します。
* **ACSD-51265** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.2 &lt;2.4.7） – システムにバンドルされた商品が多すぎる場合の`catalog_product_price` インデックス再作成のパフォーマンスに関する問題を修正します。
* **ACSD-52831** （Adobe Commerce >=2.3.7 &lt;2.4.7）の場合 – [!DNL Google reCAPTCHA v3 Invisible]が有効になっている場合に、お客様が交渉可能な見積もり注文を行えない問題を修正します。
* **ACSD-51845** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.7） – 非同期の一括REST APIを使用して、ティア価格と異なる属性セットを持つ後続の製品を更新できない問題を修正します。
* **ACSD-52815** （Adobe CommerceおよびMagento Open Sourceの場合>=2.3.7 &lt;2.4.7） – デフォルト以外のソースの数量フィールドの入力で、デフォルトの在庫の8桁ではなく、最大6桁しかサポートされない問題を修正します。
* **ACSD-51149** （Adobe Commerce >=2.3.7 &lt;2.4.7の場合） – 有効なカタログ権限を持つスケジュール済みImportExportでインデクサーが無効になり、cronによってフラッシュがキャッシュされる問題を修正します。
* **ACSD-50815** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.5 &lt;2.4.6） – シンプルな商品の小数点以下桁を新しいバンドル商品オプションに使用できない問題を修正しました。
* ACSD-47803のバージョンを更新しました。
* ACSD-51892のタイトルを更新しました。
* ACSD-51379を更新しました。
* ACSD-49970-v2を更新しました。

## v1.1.34 {#v1-1-34}

* **ACSD-52277** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.0 &lt;2.4.7） – 管理者で新しい注文を作成する際に、ストアビューを選択した後、管理者ユーザーが正しくリダイレクトされない問題を修正します。
* **ACSD-50813** （Adobe Commerce >=2.4.5 &lt;2.4.7）の場合：管理者が管理者注文に[!UICONTROL Add Products by SKU]機能を使用して、SKUにスラッシュを含むバンドル製品を管理者注文に追加できなかった問題を修正します。
* **ACSD-51630** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.3 &lt;2.4.7） – 大量のシステムメッセージによって管理者ページのダウンロードが遅くなる問題を修正します。
* **ACSD-51853** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.1 &lt;2.4.7） - [!UICONTROL Page Builder]を使用すると、コピーされたテキストスタイルが適用されない問題を修正しました。
* **ACSD-52160** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.7） – ルール条件「すべての/これらの条件のいずれかがtrueの場合に商品がカートに見つかった/見つからなかった場合」に基づいて、カート価格ルールに対する商品の検証結果が適切に評価されない問題を修正します。
* **ACSD-51636** （Adobe Commerce >=2.4.5 &lt;2.4.7）は、必要な役割と権限をすべて持っているにもかかわらず、会社管理者が顧客アカウントセクションから新しいユーザーを追加できない問題を修正します。
* **ACSD-51739** （Adobe Commerce >=2.4.6 &lt;2.4.7）の場合 – CompanyTeam GraphQL リクエストで`structure_id`がリクエストされたときにエラーが返される問題を修正します。
* **ACSD-51857** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.0 &lt;2.4.7） – 大規模なsales_orderおよび`aggregate_sales_report_bestsellers_data` データベーステーブルに関する`sales_order_item` cron レポートのパフォーマンスが遅い問題を修正します。これは、主なデータクエリの書き方が原因です。
* **ACSD-48448** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.2 &lt;2.4.7） – 注文キャンセル中に競合条件の問題が発生し、`inventory_reservation` テーブルにエントリが重複する問題が発生する問題を修正します。
* **ACSD-52689** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.3 &lt;2.4.6） - REST APIを使用して画像をAmazon S3 ストレージにアップロードできない問題を修正します。
* **B2B-2674** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.7） - 1customAttributeMetadata1 GraphQL クエリにキャッシュ機能を追加します。
* ACSD-44938の新しいバージョンを追加しました。
* ACSD-46988の要件を追加しました。

## v1.1.33 {#v1-1-33}

* **ACSD-50478** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.0 &lt;2.4.5） - DB ダンプにトリガーと&#x200B;*区切り記号* SQL コマンドが含まれている場合のデータベースロールバックコマンドを修正します。
* **ACSD-50512** （Adobe Commerce >=2.4.5 &lt;2.4.7の場合） - *エラーを修正：ダウンロード可能なリンクは商品と関係ありません。 リンクを確認して、もう一度試してください。ダウンロード可能な製品ステージング更新プログラムの開始日を更新する際に発生する* エラー。
* **ACSD-50949** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.2 &lt;2.4.7） - SKU フィルターに沿って使用すると、詳細検索の価格フィルターで適切な結果が返されない問題を修正しました。
* **ACSD-51645** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.6 &lt;2.4.7） – 拡張機能`Magento_OfflineShipping`が無効になっている場合に、新しいカート価格ルールを保存する際にスローされるエラーを修正します。
* **ACSD-50895** （Adobe Commerce >=2.4.5 &lt;2.4.7の場合） - [!DNL Google Analytics] 4 GTMが設定されていない場合、[!DNL Google Analytics] 3 GTM タグが実行されない問題を修正します。
* **ACSD-51102** （Adobe Commerce >=2.4.2 &lt;2.4.7の場合） – ルールがスケジュールされた更新によって有効になっている場合に、多数の製品に適用されるカタログルールが正しくインデックス作成されない問題を修正します。
* **ACSD-50368** （Adobe CommerceおよびMagento Open Sourceの場合>= 2.4.3 &lt;2.4.5） – お客様がAsync REST APIまたはAsync Bulk REST APIを使用して作成された場合に、お客様の`group_id`が無視される問題を修正します。
* **ACSD-51497** （Adobe CommerceおよびMagento Open Sourceの場合>=2.3.7 &lt;2.4.0 |>= 2.4.1 &lt;2.4.7） – ドロップダウンタイプのカスタム属性でカタログページをソートできない問題を修正します。
* **ACSD-51408** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt; 2.4.7の場合） – 注文項目のステータスが&#x200B;*[!UICONTROL Backordered]*&#x200B;に誤って設定される問題を修正します。
* **ACSD-51735** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.5） – 商品の在庫が&#x200B;*[!UICONTROL Ordered]* 0 *の場合に、注文商品のステータスが*&#x200B;に誤って設定される問題を修正します。
* **ACSD-51792** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.5 &lt;2.4.6） - [!DNL Google Tag Manager] 4が有効になっている場合に、ページにインプレッションイベントが表示されない問題を修正します。
* **ACSD-51471** （Adobe Commerce >=2.4.3 &lt;2.4.7の場合） – 管理者ユーザーが、自身がスケジュールされた更新を持つシンプルな製品を使用するバンドル製品のスケジュールされた更新を保存できない問題を修正します。
* **ACSD-51700** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.3 &lt;2.4.7） – 管理画面でダウンロード可能な商品編集ページでストアビューを切り替える際に発生するエラーを修正します。
* **ACSD-51120** （Adobe Commerce >=2.3.7 &lt;2.4.3の場合） – ステージング更新で更新されるCMS ブロックを含むCMS ページで、GraphQL GETのキャッシュがクリアされない問題を修正します。
* **ACSD-51240** （Adobe Commerce >=2.4.4 &lt;2.4.6）は、会社登録フォームを使用して登録を行った場合に、アップロードされたファイルが見つからない問題を修正します。
* **ACSD-51907** （Adobe Commerce >=2.4.2 &lt;2.4.3の場合） – 制限付き管理者ユーザーがオフライン払い戻しを含むクレジットメモを作成できない問題を修正します。
* **ACSD-52148** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.0 &lt;2.4.4） - [!DNL Google V3 reCAPTCHA]管理者ログインが失敗する問題を修正します。
* **ACSD-51431** （Adobe CommerceおよびMagento Open Sourceの場合>=2.3.7 &lt;2.4.7） – 変更ログに新しいエントリがない場合でも、インデクサーステータスが&#x200B;*working*&#x200B;になる問題を修正します。
* **ACSD-51892** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.6 &lt;2.4.7） - config ファイルが複数回読み込まれるパフォーマンスの問題を修正します。
* 非推奨のACSD-51114。

## v1.1.32 {#v1-1-32}

* **ACSD-49628** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.2 &lt;2.4.7） - [!UICONTROL Page Builder's]の複数のエラーにより、管理者がコンテンツ権限を持たずに商品を保存できない問題を修正します。
* **ACSD-51305** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.6 &lt;2.4.7） – 在庫切れの設定可能な子商品がGraphQLの対応で利用できない問題を修正します。
* **ACSD-50621** （Adobe Commerce >=2.3.7 &lt;2.4.7）の場合：複数のweb サイトで編集しようとすると、共有カタログ内の異なるweb サイトの[!UICONTROL Tier Prices]が表示されない問題を修正しました。
* **ACSD-51041** （Adobe CommerceおよびMagento Open Sourceの場合>=2.3.7 &lt;2.4.0 ||>=2.4.1 &lt;2.4.6） – 価格インデックスのパフォーマンスを向上させます。
* **ACSD-51379** （Adobe CommerceおよびMagento Open Sourceの場合>=2.3.7 &lt;2.4.7） - [!UICONTROL Page Builder]を介してページテキストコンテンツに加えた変更が保存されない問題を修正します。
* **ACSD-49480** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.6） – カートに1つのカート価格ルールのみが適用される問題を修正します。
* **ACSD-51230** （Adobe Commerce >=2.3.7 &lt;2.4.7）の場合 – シンプルな商品の部分的な払い戻しが注文から処理される際に、ギフトカードアカウントが削除される問題を修正します。
* **ACSD-51238** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.7） – 設定可能な商品を更新し、価格を編集する際に在庫源が削除される問題を修正します。
* **ACSD-50794** （Adobe Commerce >=2.4.1 &lt;2.4.7）の場合 – GraphQLを介して削除する際に、ギフトメッセージまたはギフトのラッピングの詳細がデータベースで更新されない問題を修正しました。
* **ACSD-51528** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.5 &lt;2.4.7） - *x_forwarded_for*&#x200B;列が&#x200B;*sales_order* テーブルでnull値を持つ問題を修正します。
* **ACSD-50849** （Adobe Commerce >=2.4.4 &lt;2.4.6）は、キャッシュをクリアした後に新しい商品をカテゴリに追加すると、既存の商品の位置と選択が一致しない問題を修正します。
* **ACSD-51294** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.5 &lt;2.4.7） - GTM/GAの価格、数量、税金、配送、および収益が文字列として[!DNL Google Analytics]およびGTMに送信される問題を修正します。
* **ACSD-51204** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.3 &lt;2.4.7） – クレジットメモを作成した後に、完全に販売された商品が在庫に戻らない問題を修正します。
* **ACSD-51291** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.4-p4 || >=2.4.5 &lt;2.4.5-p3） - 1つのweb サイトへのアクセス権を持つ制限付き管理者が、複数のweb サイトに割り当てられた商品に画像/ビデオを追加できる問題を修正します。
* ACSD-50336の新しいバージョンを追加しました。
* ACSD-49970 パッチを置き換えました。

## v1.1.31 {#v1-1-31}

* **ACSD-50345** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.3 &lt;2.4.4 |>=2.4.4-p1 &lt;2.4.6） – 支払い失敗を送信した後にRecaptcha v2がリロードされない問題を修正します。
* **ACSD-50817** （Adobe CommerceおよびMagento Open Sourceの場合>=2.3.7 &lt;2.4.7） - Cron ジョブ `sales_clean_quotes`を高速に実行するように最適化します。
* **ACSD-49392** （Adobe CommerceおよびMagento Open Sourceの場合>=2.3.7 &lt;2.4.0 |>= 2.4.1 &lt;2.4.7） – 同梱商品の一部払い戻し後、注文状況がクローズに変わる問題を修正します。
* **ACSD-51036** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.5） – 同時REST API呼び出し中に競合条件が発生し、[!UICONTROL Items Ordered] テーブルの配送ステータス情報が上書きされる問題を修正します。
* **ACSD-50858** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.7） – バナーのコンテンツを読み込む際のパフォーマンスが向上します。
* MDVA-39305-v2、ACSD-45169の新しいバージョンを追加しました。
* ACSD-50260-v2のパッチを更新しました。

## v1.1.30 {#v1-1-30}

* **ACSD-50336** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4-p1 &lt;2.4.4-p3） – 商品の再入荷や価格の変更の際に商品の通知メールが送信されない問題を修正しました。
* **ACSD-50367** （Adobe CommerceおよびMagento Open Sourceの場合>=2.3.7 &lt;2.4.7） – 値のない複数選択の顧客アドレス属性を作成する場合に、顧客アドレスの書き出しが機能しない問題を修正します。
* **ACSD-49877** （Adobe CommerceおよびMagento Open Sourceの場合>=2.3.7 &lt;2.4.7） – 動画がリモート動画ファイルに直接リンクされていて、ストリーミングサービスではない場合に、モバイル [!DNL Safari]で動画の自動再生が機能しない問題を修正します。
* **ACSD-50165** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.0 &lt;2.4.7） – エラー&#x200B;*ファイルを削除できません。 警告！unlink：管理者からJS/CSS キャッシュをフラッシュする際に、そのようなファイルまたはディレクトリ*&#x200B;がありません。
* **ACSD-49737** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.1-p1 &lt;2.4.7） – カード支払いに失敗した後に、クーポンが誤って「使用」としてマークされる問題を修正します。
* **ACSD-50814** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.6 &lt;2.4.7） – 管理者ユーザーがクレジットメモを作成できない問題を修正します。
* **ACSD-50116** （Adobe CommerceおよびMagento Open Sourceの場合>=2.3.7 &lt;2.4.7） – 管理者ユーザーがサブカテゴリーレベル 3以下のURL書き換えを作成できない問題を修正します。
* **ACSD-49513** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.3 &lt;2.4.5） - 0 バイトのファイルが原因でリモートストレージの同期が失敗する問題を修正します。
* **ACSD-46683** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.2 &lt;2.4.7） – 送料が&#x200B;*まだ計算されていません*&#x200B;と表示される問題を修正します。
* **ACSD-49129** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.2 &lt;2.4.6） - *[!UICONTROL content]*&#x200B;件のproduct media API応答で`rest/V1/products/sku/media`属性（base64 image code）が返されない問題を修正します。
* **ACSD-50276** （Adobe Commerce >=2.4.0 &lt;2.4.7の場合） – 複数選択のお客様属性が作成された場合、お客様登録フォームがストアフロントで機能しない問題を修正します。
* **ACSD-50527** （Adobe Commerce >=2.3.7 &lt;2.4.7）で、空の動的ブロックを含むページを保存する際に発生するエラーを修正します。
* **ACSD-49973** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.5） - GraphQLを使用してバンドルされた商品を取得する際のパフォーマンスが向上します。
* **ACSD-51114** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.3 &lt;2.4.7） – 非同期インデックス作成が有効になっている場合に、大きなカタログからランダムな商品が消える問題を修正します。 大規模なカタログの非同期インデックス再作成のパフォーマンスを向上させます。
* **B2B-2598** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.7） - [!UICONTROL availableStores]、[!UICONTROL countries]、[!UICONTROL country]、[!UICONTROL currency]、および[!UICONTROL storeConfig]個のGraphQL クエリにキャッシュ機能を追加します。
* MDVA-42806、ACSD-48627、ACSD-46815の新しいバージョンを追加しました。
* ACSD-49773、ACSD-47179、ACSD-48300のパッチメタデータを更新しました。

## v1.1.29 {#v1-1-29}

* **ACSD-49389** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.0 &lt;2.4.7） – 注文の受け取り準備が整っていない場合に、受け取り準備完了の電子メールがAPIによって送信される問題を修正します。
* **ACSD-49822** （Adobe Commerce >=2.3.7 &lt;2.4.7）の場合、[!UICONTROL Requisition List] ページの更新が[!UICONTROL Print Requisition List]に反映されない問題を修正しました。
* **ACSD-48771** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.5 &lt;2.4.7） – 古い[!DNL Page Builder]のバージョンから列ブロックコンテンツタイプをアップグレードする際の問題を修正します。
* **ACSD-49464** （Adobe Commerce >=2.3.7 &lt;2.4.7）の場合 – orderIdが異なると、請求書、発送、およびクレジット メモがアーカイブから戻されない問題を修正します。
* **ACSD-49773** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.2 &lt;2.4.6） - AWS S3をリモートストレージとして使用すると、商品の書き出しが失敗する問題を修正します。
* **ACSD-49748** （Adobe Commerce >=2.3.7 &lt;2.4.7）の場合：招待状を送信できない問題を修正します。
* **ACSD-49502** （Adobe Commerce >=2.4.3 &lt;2.4.7）の場合 – ステージング更新がダウンロード可能な商品に適用された後、ダウンロード可能なリンクが正しく更新されない問題を修正します。
* **ACSD-49527** （Adobe Commerce >=2.4.2 &lt;2.4.7）の場合） - GraphQLの会社ロールでページネーションが正しく表示されない問題を修正します。
* **ACSD-49706** （Adobe CommerceおよびMagento Open Source >=2.3.7 &lt;2.4.7）の場合） – 値が選択されていない場合に、デフォルト値が視覚的スウォッチ属性に保存される問題を修正します。
* **ACSD-49835** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.5 &lt;2.4.7） – マルチセレクト属性のストアレベルで「デフォルトのチェックボックスを使用」の値が正しく保存されない問題を修正します。
* **ACSD-49898** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.6） – バンドルされた商品の特別価格が1000を超える場合に、商品グリッドが例外をスローする問題を修正します。
* **ACSD-50234** （Adobe CommerceおよびMagento Open Sourceの場合>=2.3.7 &lt;2.4.5） - [!DNL PayPal]で注文した場合の確認メールの間違った顧客名の問題を修正します。
* **ACSD-49960** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.5 &lt;2.4.7） – カスタマー注文グリッドで日付によるフィルタリングが機能しない問題を修正します。
* **ACSD-49849** （Adobe CommerceおよびMagento Open Sourceの場合>=2.3.7 &lt;2.4.6） - GraphQLを介して[!DNL PayPal]に注文する際にお客様の電子メールが[!DNL PayPal Express]電子メールに置き換えられた問題を修正します。
* **ACSD-49839** （Adobe Commerce >=2.3.7 &lt;2.4.7の場合） – 商品がSKUに一重引用符または二重引用符がある場合に、管理画面でShared Catalog Pricing and structureでエラーがスローされる問題を修正します。
* **ACSD-49970** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.5 &lt;2.4.7） - [!DNL New Relic] レポートがオンになっている場合のGraphQL エラーの誤った処理を修正します。
* **ACSD-50260** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.5 &lt;2.4.7） - GraphQLの商品検索結果が10,000件のみに制限される問題を修正します。
* **ACSD-48813** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.3 &lt;2.4.7） – 属性の検索重みに基づいて、検索で関連する結果が表示されない問題を修正します。

## v1.1.28 {#v1-1-28}

* **ACSD-48204** （Adobe CommerceおよびMagento Open Sourceの場合>=2.3.7 &lt;2.4.3） - Yes/No属性に基づいて作成されたカタログ価格ルールが、選択した範囲を考慮しない問題を修正します。
* **ACSD-47704** （Adobe CommerceおよびMagento Open Sourceの場合>=2.3.7 &lt;2.4.7） – バンドルされた商品が在庫商品の価格のみを表示する問題を修正します。
* **ACSD-49370** （Adobe CommerceおよびMagento Open Sourceの場合>=2.3.7 &lt;2.4.7） - *日付時間*&#x200B;製品属性に&#x200B;*FilterMatchTypeInput* タイプがGraphQL スキーマにある問題を修正します。
* **ACSD-48807** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.1 &lt;2.4.7） - GraphQLを介して、お客様の商品レビューがstoreviewでフィルタリングされない問題を修正します。
* **ACSD-49433** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.3 &lt;2.4.7） – ギフトカードの買い物かごにデフォルトの金額が小計として表示され、開封金額が表示される問題を修正しました。
* **ACSD-48866** （Adobe CommerceおよびMagento Open Sourceの場合>=2.3.7 &lt;2.4.7） – カテゴリのRSS フィードをリクエストする際にエラーが発生する問題を修正します。
* **ACSD-48784** （Adobe CommerceおよびMagento Open Sourceの場合>=2.3.7 &lt;2.4.7） – カスタマーグループ間でカスタマーセグメントの価格が誤ってキャッシュされる問題を修正します。
* **ACSD-48857** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.3 &lt;2.4.7） – ページビルダーで編集した後、変更内容を保存できない問題を修正します。
* **ACSD-49065** （Adobe CommerceおよびMagento Open Sourceの場合>=2.3.7 &lt;2.4.7） – カスタム在庫に割り当てられている場合にのみ、管理者に見積もり項目が表示されない問題を修正します。
* **ACSD-49179** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.2 &lt;2.4.7） – 異なる店舗で異なる通貨を使用している場合に、注文レポートに誤った金額が表示される問題を修正します。
* **ACSD-49286** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.3 &lt;2.4.7） – 複数の商品ウィジェットがページに存在する場合に、商品がカートに2回追加される問題を修正します。
* **ACSD-49574** （Adobe Commerce >=2.4.4 &lt;2.4.7）の場合） - GraphQLを介してギフトカードの商品アップデートをカートでサポートする機能を追加します。
* 更新されたパッチ：ACSD-48694。

## v1.1.27 {#v1-1-27}

* **ACSD-48362** （Adobe Commerce >=2.4.1 &lt;2.4.7の場合） – 交渉可能な見積もりを使用して注文を行う際に、デフォルトの配送先住所が新しい配送先住所の代わりに使用される問題を修正します。
* **ACSD-48059** （Adobe Commerce >=2.3.7 &lt;2.4.7）の場合、マーチャントがカテゴリに「[!UICONTROL Match product by rule]」を保存できない問題を修正しました。
* **ACSD-48216** （Adobe CommerceおよびMagento Open Sourceの場合>=2.3.7 &lt;2.3.8 || >=2.4.0 &lt;2.4.7） - [!UICONTROL AUTO_INCREMENT] テーブルの[!UICONTROL inventory_source_item]が[!UICONTROL UPDATE]操作で増加する問題を修正します。
* **ACSD-47908** （Adobe CommerceおよびMagento Open Sourceの場合>=2.3.7 &lt;2.3.8 || >=2.4.0 &lt;2.4.7） – チェックアウト時に発送元と数量を選択する際のエラー「0以下の値が想定される」を修正します。
* **ACSD-49497** （Adobe CommerceおよびMagento Open Sourceの場合>=2.3.7 &lt;2.4.6） – 発送後も注文が処理中のままになり、部分的な払い戻しが適用される問題を修正します。
* **ACSD-48694** （Adobe CommerceおよびMagento Open Sourceの場合>=2.3.7 &lt;2.3.8 || >=2.4.1 &lt;2.4.7） – 「無効な状態の変更が要求されました」というエラーにより、お客様が注文を行うことができない問題を修正します。
* **ACSD-49013** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.3 &lt;2.4.7） – 一括APIを使用して顧客を作成する際に、メール確認がweb サイトのロケールに変換されない問題を修正します。
* **ACSD-48164** （Adobe CommerceおよびMagento Open Sourceの場合>=2.3.7 &lt;2.4.7） – 制限付き管理者がweb サイトレベルの値を保存できない問題を修正します。
* **ACSD-48404** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.0 &lt;2.4.4） – ブラウザーの戻るボタンを押すと「カテゴリのページネーションを記憶する=はい」というエラーが発生する問題を修正します。
* **ACSD-48634** （Adobe CommerceおよびMagento Open Sourceの場合>=2.3.7 &lt;2.4.7） – 「[!UICONTROL Google Analytics Content Experiments]」が有効になっている場合のステージング更新ページのJS エラーを修正します。
* **ACSD-49042** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.5） – バックオーダーが無限の商品をストアフロントから注文できない問題を修正します。
* 更新されたパッチ：ACSD-48366、ACSD-48661。

## v1.1.26 {#v1-1-26}

* **ACSD-47937** （Adobe CommerceおよびMagento Open Source 2.4.4 || >=2.4.5 &lt;2.4.6）の場合 – アプリケーションレベルのキャッシュにより、値下げ通知が常に送信されない問題を修正します。
* **ACSD-48661** （Adobe CommerceおよびMagento Open Sourceの場合>=2.3.7 &lt;2.4.7） – 会社のクレジット制限が999を超える場合、コンマ区切り記号が検証エラーのために会社の保存を妨げる問題を修正します。
* **ACSD-48773** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.2 &lt;2.4.7） – 報酬ポイントのメールテンプレートが間違ったストアから取得される問題を修正します。
* **ACSD-48587** （Adobe CommerceとMagento Open Sourceの場合>=2.3.7 &lt;2.4.7） - products widgetの一致ルールでHTMLの特殊文字が一致する商品の表示を妨げる問題を修正します。
* **ACSD-48212** （Adobe CommerceおよびMagento Open Sourceの場合>=2.3.7 &lt;2.4.6） – 製品の読み込みが間違ったソースに製品を割り当てる問題を修正します。
* **ACSD-47988** （Adobe CommerceおよびMagento Open Sourceの場合>=2.3.7 &lt;2.4.6） – ページビルダー製品の説明から製品の書き出しがHTML タグをトリミングする問題を修正します。
* **ACSD-48366** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.6） – 「Back to Stock」電子メールテンプレートに商品画像が表示されない問題を修正します。
* **ACSD-48417** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.5 &lt;2.4.7） – 製品のスケジュール変更を作成し、別の製品を保存した後にSQL エラーが表示される問題を修正します。

## v1.1.25 {#v1-1-25}

* **ACSD-48058** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.5 &lt;2.4.6） – バンドル商品がどのweb サイトにも割り当てられていない場合に、商品の価格インデックスが機能しない問題を修正します。
* **ACSD-48262** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.5 &lt;2.4.6） – 「すべての商品をページごとに許可」設定が「はい」に設定されている場合に、フロントエンドに商品が表示されない問題を修正しました。
* **ACSD-48293** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.3 &lt;2.4.4） – 売り切れた子商品を在庫に戻す際に、複合商品が在庫切れになる問題を修正します。
* **ACSD-47520** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.0 &lt;2.4.6） – クレジットメモの作成時にお客様が報酬ポイントを失う問題を修正します。
* **ACSD-48044** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.0 &lt;2.4.4） - 1つの注文に複数のギフトカードを適用して複数配送を行うと、注文が行われない問題を修正しました。
* **ACSD-48300** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.0 &lt;2.4.6） – 設定可能な商品を削除した場合に返品を作成できない問題を修正します。
* **ACSD-47910** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.6） – それぞれのエンティティ グリッドで注文、請求書、出荷、およびクレジット メモが見つからない問題を修正します。
* **ACSD-47292** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.6） – 「在庫切れ商品を表示」が「はい」に設定されている場合に、GraphQLの回答で在庫切れバンドル商品が利用できない問題を修正します。
* **ACSD-48234** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.5 &lt;2.4.6） – 「在庫切れを表示」オプションが有効になっている場合に、カタログの検索結果に誤ったカテゴリ品目数が表示される問題を修正します。
* **ACSD-48313** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.0 &lt;2.4.5） – 属性値にコンマが含まれる場合に「configurable_variations」列が解析されない問題を修正します。 同じ解析アルゴリズムが「additional_attributes」に使用されます。
* **ACSD-48627** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.5 &lt;2.4.6） - GraphQL リクエストを送信してカートの詳細を取得する際に、在庫切れの設定可能な商品がエラーを引き起こす問題を修正します。
* MDVA-39384 パッチを更新しました。

## v1.1.24 {#v1-1-24}

* **ACSD-45168** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.2 &lt;2.4.6） – ストアビューレベルで&#x200B;*url_key*&#x200B;属性がオーバーライドされた商品に対して、SEO対応URLが生成されない問題を修正します。
* **ACSD-46865** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.6） – 非同期インデックス作成が有効になっている場合に、ShipmentおよびCredit Memo グリッドが入力されない問題を修正します。
* **ACSD-47004** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.2 &lt;2.4.6） - VAT IDのない請求先住所にVATが適用されない問題を修正します。
* **ACSD-47803** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.0 &lt;2.4.6） – 在庫切れの設定可能な商品スウォッチが使用可能な状態で表示される問題を修正します。
* **ACSD-47137** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.6） – パブ/メディアフォルダーが非常に大きい場合の画像ギャラリーの読み込み速度を向上させます。
* **ACSD-46770** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.0 &lt;2.4.6） - *Email order confirmation*&#x200B;のチェックがオフになっている場合でも、管理者注文の電子メールが送信される問題を修正します。
* **ACSD-47955** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.6） - GraphQLでカート割引が正しく表示されない問題を修正します。
* **ACSD-46617** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.0 &lt;2.4.6） – 小計が設定された&#x200B;*最小注文額*&#x200B;を超えている場合でも、*チェックアウトを続行* ボタンがグレー表示される問題を修正します。
* **ACSD-47079** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.5） - REST API POST /rest/V1/inventory/source-itemsを介してサブ商品の在庫状況が変更された場合に、複合商品（バンドル、グループ化、設定可能）の在庫状況が更新されない問題を修正します。
* **ACSD-47336** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.0 &lt;2.4.6） - *問題が発生しました。Commerce Adminで通知を閉じる際に* エラーが発生しました。
* **ACSD-47559** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.0 &lt;2.4.6） – 「電子メールテンプレートのプレビュー」領域が完全に表示されない問題を修正します。
* **ACSD-47920** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.0 &lt;2.4.6） - *ゲストチェックアウトを許可*&#x200B;がオフになっている場合でも、Rest APIを介してゲストユーザーとして注文できる問題を修正します。
* 置き換えられたパッチ：MDVA-39305、MDVA-42855。

## v1.1.23 {#v1-1-23}

* **ACSD-47179** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.0 &lt;2.4.6） – 特定のスコープへのアクセスが制限された管理者が製品レビューを削除できない問題を修正します。
* **ACSD-47107** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.2 &lt;2.4.5） – カタログ価格ルールの割引がカスタム製品オプションに適用される問題を修正します。
* **ACSD-47232** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.0 &lt;2.4.6） - Adminで総重量条件を持つクーポンを適用できない問題を修正しました。
* **ACSD-46519** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.1 &lt;2.4.6） - GraphQL categoryList リクエストで、アンカーカテゴリに対して誤ったproduct_countが返される問題を修正します。
* **ACSD-47027** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.2 &lt;2.4.6） – 遅いupdateCompanyRole GraphQL リクエストを修正します。
* **ACSD-47666** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.0 &lt;2.4.6） – 管理者/システム/権限/ユーザーロール/役割/ユーザーユーザーユーザーグリッドでフィルター関数が機能しない問題を修正します。
* **ACSD-47497** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.0 &lt;2.4.6） – 「管理者」の「設定」に「サービス」タブが表示されない問題を修正します。
* 更新されたパッチ：ACSD-47743。
* 置き換えられたパッチ：MDVA-42807。

## v1.1.22 {#v1-1-22}

* **ACSD-47444** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.0 &lt;2.4.3） - PHP 7.4で既知の製品の特定のカテゴリパスにアクセスする際に、_型bool_&#x200B;の値で配列オフセットにアクセスしようとすると発生するエラーを修正します。
* **ACSD-47332** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.0 &lt;2.4.6） - 00:00から00:59 UTCの間で実行した場合にのみ報告されるエラーでcronが失敗する問題を修正します。
* **ACSD-47280** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.0 &lt;2.4.6） – 特定のスコープで共有カタログ機能を無効にしても正しく機能しない問題を修正します。
* **ACSD-47106** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.6） – 企業作成ページの新しいカスタム属性に値を保存できない問題を修正します。
* 更新されたパッチ：ACSD-45143。

## v1.1.21 {#v1-1-21}

* **ACSD-46809** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.2 &lt;2.4.6） – 多数の商品ソースを割り当てる際にエラーが発生する問題を修正します。
* **ACSD-46856** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.0 &lt;2.4.6） - System > Configuration > Import > Advanced Pricingを使用して、階層の価格を更新するパフォーマンスを向上させます。
* **ACSD-46541** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.0 &lt;2.4.4） – 注文項目が削除された場合に管理者ユーザーがクレジットメモを作成できない問題を修正します。
* **ACSD-46581** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.0 &lt;2.4.6） – ショッピングカートで国を選択した後、推定税額が更新されない問題を修正します。
* **ACSD-46618** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.0 &lt;2.4.6） – ログインしたお客様に対して、商品リストウィジェットで誤ったキャッシュ価格が表示される問題を修正します。
* **ACSD-46674** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.0 &lt;2.4.6） – お客様の電子メールで、画像タイプのカスタムオプションがHTMLとして表示される問題を修正します。
* **ACSD-46988** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.6） - GraphQL「currency」 API リクエストがカスタム通貨のNULL値を返す問題を修正します。
* **ACSD-47076** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.1 &lt;2.4.5） - Vimeo ビデオをストアフロントで再生できない問題を修正します。
* **ACSD-45071** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.2 &lt;2.4.4） – インポート時にデフォルトソースが商品に追加される問題を修正します。
* **AC-3023** （Adobe CommerceおよびMagento Open Sourceの場合>=2.4.0 &lt;2.4.6） - DHL スキームを最新バージョン 10.0に更新します。
* 更新されたパッチ：MDVA-42584.
* 置き換えられたパッチ：MDVA-36572、ACSD-45241。

## v1.1.20 {#v1-1-20}

* **ACSD-46520** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.4.0 &lt;2.4.5*） – ストアクレジットを使用して返金された場合に、ユーザーが誤った注文ステータスを受け取る問題を修正します。
* **ACSD-46703** （*for Adobe Commerce and Magento Open Source >=2.4.4 &lt;2.4.6*） – 商品編集ページにカスタムオプションをドラッグ&amp;ドロップできない問題を修正しました。
* **ACSD-44851** （*for Adobe Commerce and Magento Open Source >=2.4.0 &lt;2.4.6*） – サブカテゴリを持つカテゴリを開いたり展開したりできない問題を修正します。
* **ACSD-46815** （*Adobe CommerceおよびMagento Open Source >=2.4.5 &lt;2.4.6*）は、カテゴリツリーのリクエストが20 カテゴリに制限される問題を修正します。
* **ACSD-45675** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.4.0 &lt;2.4.6*） – 商品エクスポートで&#x200B;*デフォルトストアビュー* スコープのカテゴリ名が使用される問題を修正します。
* **ACSD-46869** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.6*） - *PUT REST API* リクエストでカート内の設定可能な商品が商品数量を変更せずに更新されない問題を修正します。
* **MDVA-42768-V2** （*Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.3*） - *在庫切れを表示*&#x200B;が&#x200B;*であるときに、コンフィグ可能な商品が正規価格を* 0 *として表示する問題を修正します。*
* 更新されたパッチ：MDVA-44562、ACSD-46213、MDVA-41305、MDVA-38346、MDVA-13203。
* 非推奨パッチ：MDVA-42768.

## v1.1.19 {#v1-1-19}

* **ACSD-46213** （*Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.3*）は、カテゴリツリーのリクエストが20 カテゴリに制限される問題を修正します。
* **ACSD-45781** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.4.1 &lt;2.4.2*） – ストアフロント検索フィールドがモバイルで表示されない問題を修正します。
* **ACSD-46192** （*Adobe CommerceおよびMagento Open Source >=2.3.6 &lt;2.4.5*）は、`async/bulk/V1/configurable-products/bySku/options` エンドポイントの使用に関する問題を修正します。
* **ACSD-46404** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.5*） – 管理者ユーザーが2.4.4にアップグレードした後にログインできない問題を修正しました。
* 更新されたパッチ：MDVA-41305、MDVA-38626、MDVA-38728、MDVA-41061-V4、MDVA-42269、MDVA-39305。

## v1.1.18 {#v1-1-18}

* **ACSD-45817** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.4.2 &lt;2.4.4*） – 特定のストアのGraphQL製品の変更で、リクエストされたストアに割り当てられていないものを含む、設定可能なすべてのバリエーションが返される問題を修正します。
* **ACSD-46146** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.3.0 &lt;2.4.6*） – 管理者からの注文後に2通の注文確認メールが送信される問題を修正しました。
* **ACSD-45255** （*for Adobe Commerce >=2.4.3 &lt;2.4.6*） – 制限付き管理者ユーザーのLow Stock レポートページの例外を修正します。
* **ACSD-45488** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.4.2 &lt;2.4.6*） – 複数のソースを持つ設定可能な商品が自動的にIn Stockに返されない問題を修正します。
* **ACSD-45754** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.3.1 &lt;2.4.6*） – クーポンをカートに適用した後に報酬ポイントが追加されない問題を修正しました。
* **ACSD-45849** （*for Adobe Commerce >=2.4.3 &lt;2.4.4*） – ステージング更新が適用された後にビデオメタデータが失われる問題を修正します。
* **ACSD-45257** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.3.4 &lt;2.4.4*） - GraphQLでカート割引が正しく表示されない問題を修正します。
* **ACSD-44938** （*for Adobe Commerce and Magento Open Source >=2.4.0 &lt;2.4.4*） – ゲストユーザーのGraphQL リクエストで`VAT_ID`を適用できない問題を修正します。
* 更新されたパッチ：MDVA-43417.

## v1.1.17 {#v1-1-17}

* **ACSD-45241** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.3.5 &lt;2.4.4*） – クレジットメモを作成した後にバーチャル商品の在庫量が誤って計算される問題を修正します。
* **ACSD-43887** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.4.2 &lt;2.4.5*） – 会社の発注書が有効になっている場合に、チェックアウト支払いページに誤った詳細が表示される問題を修正します。
* **ACSD-45143** （*Adobe CommerceおよびMagento Open Source >=2.4.0 &lt;2.4.5*）は、`setShippingAddressesOnCart`変異で数値リージョンコードを&#x200B;*region*&#x200B;として設定できない問題を修正します。
* **ACSD-44591** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.4.3 &lt;2.4.6*） - CAPTCHAの確認なしで注文を行った場合に発生するエラーを修正します。
* **ACSD-45520** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.3.0 &lt;2.4.6*） – ユーザーがショッピングカートから設定可能な商品を編集する際に、商品詳細ページでスウォッチ オプションが事前に選択されない問題を修正します。
* **ACSD-45169** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.4.1 &lt;2.4.6*） – ステージング更新が適用された後、[!DNL Visual Merchandiser]が設定可能な商品の正しい在庫と価格を表示しない問題を修正します。
* **ACSD-45424** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.3.4 &lt;2.4.6*） – 一部払い戻し（クレジットメモ）後に誤った予約報酬が作成される問題を修正します。
* **MDVA-42807** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.3.1 &lt;2.4.6*） – ストアのフロントにカスタム通貨記号が表示されない問題を修正します。
* 更新されたパッチ：MDVA-42689、AC-3022。

## v1.1.16 {#v1-1-16}

* **MDVA-44703** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.4.3 &lt;2.4.4*） – 制限付き管理者ユーザーに対して、注文報告書の注文合計が誤って計算される問題を修正します。
* **MDVA-44940** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.4.3 &lt;2.4.4*） – カテゴリを管理者から保存する際に発生するSQL エラーを修正します。
* **MDVA-44562** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.4.0 &lt;2.4.2-p2*） - GraphQL リクエストがデフォルト以外のストアビューから発生しているにもかかわらず、見積もり項目のデフォルト以外のストア IDがデフォルトのストア IDで上書きされる問題を修正します。
* **MDVA-43167** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.4.2 &lt;2.4.4*） – 管理者ユーザーがすべての注文を選択した場合に、管理者注文グリッドの一括処理がマルチページに適用されない問題を修正します。
* **MDVA-44044** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.3.0 &lt;2.4.2-p2*） – 新しいweb サイトに割り当てられた後、商品がカテゴリーページに表示されない問題を修正します。
* **MDVA-42509** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.3.3 &lt;2.4.4*） – クイックオーダーのためにCSVをアップロードできなかった場合、*cookie* エラーが発生する問題を修正します。
* 更新されたパッチ：MDVA-41061、MDVA-42584。
* 新しい[!DNL Quality Patches Tool] パッチのプレフィックスは、内部プロセスの変更により、*MDVA*&#x200B;から&#x200B;*ACSD*&#x200B;に変更されます。

## v1.1.15 {#v1-1-15}

* **MDVA-40961** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.4.3 &lt;2.4.4*） – 商品の最小数量が既にカートに入っている場合に、追加商品をカートに追加できない問題を修正します。
* **MDVA-44887** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.4.4 &lt;2.4.5*） - Admin パネルで&#x200B;*Uncaught SyntaxError: Unexpected token &#39;const&#39;* エラーが修正されました。
* **MDVA-43718** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.3.0 &lt;2.4.5*） - *コンシューマーが%resourcesへのアクセスを許可されていないことを修正します。カスタム統合から共有カタログにアクセスする際に表示される* エラー。
* **MDVA-44660** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.4.2-p1 &lt;2.4.5*） – お客様の姓と名に重大なアクセント文字``` ` ```を使用できない問題を修正しました。
* **MDVA-40896** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.4.3 &lt;2.4.4*） – 非同期製品の一括APIで&#x200B;*Error: TypeError: Argument 3がMagento*&#x200B;に渡されるエラーを修正します。
* **MDVA-38559** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.4.0 &lt;2.4.3*） - 1つ以上のサブスクリプションを持つお客様の&#x200B;*/V1/customers/search API* エラーを修正します。
* **MDVA-44533** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.3.1 &lt;2.4.4*） – バンドル子商品に誤って割引が適用される問題を修正します。
* 更新されたパッチ：MDVA-41061、MDVA-42269。

## v1.1.14 {#v1-1-14}

* **MDVA-43983** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.4.2 &lt;2.4.5*） – カタログの高度な検索結果に商品&#x200B;*個別に表示されない*&#x200B;が引き続き表示される問題を修正します。
* **MDVA-44100** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.4.3 &lt;2.4.5*） – すべてのFPTがショッピングカート内の最後の商品に割り当てられ、他の商品に対してリセットされる問題を修正します。
* **MDVA-43605** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.3.1 &lt;2.4.5*） - Rest APIを使用する際に、注文データが行合計に対して負の値を返す問題を修正します。
* **MDVA-43102** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.3.1 &lt;2.4.5*） - REST APIで払い戻しが行われたときに販売可能な数量が正しく更新されない問題を修正します。
* **MDVA-43178** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.4.3-p2 &lt;2.4.5*） - GraphQLでカスタムストアの顧客トークンを取得できない問題を修正します。
* **MDVA-43859** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.4.1 &lt;2.4.5*） – 削除されたお客様がログインしようとすると、エラー&#x200B;*No such entity with customerId =*&#x200B;がログに記録される問題を修正します。
* **MDVA-44147** （*for Adobe Commerce and Magento Open Source >=2.4.2 &lt;2.4.5*） - GraphQL リクエストでリクエストリストが返されない問題を修正します。
* **MDVA-44505** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.4.1 &lt;2.4.3*） - GraphQLのリワードポイント適用がGrand Totalを更新せず、注文時にストアクレジットが複数回適用される問題を修正します。
* 更新されたパッチ：MDVA-29148、MDVA-36464-V5、MDVA-42584、MDVA-39993-V2。

## v1.1.13 {#v1-1-13}

* **MDVA-42969** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.4.1 &lt;2.4.3*） – 顧客セグメントが&#x200B;*All*&#x200B;に設定されている場合にのみ関連商品ルールが機能する問題を修正します。
* **MDVA-39605** （*Adobe CommerceおよびMagento Open Source >=2.3.4 &lt;2.4.5*） - Redis キャッシュ TTL （有効期限）の値が正しくない問題を修正します。
* **MDVA-43862** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.3.3 &lt;2.4.5*） - GraphQL *UpdateCartItemsの変更* エラーにより、お客様が買い物かご商品を更新できない問題を修正します。
* **MDVA-43824** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.3.6 &lt;=2.3.7-p3 ||>=2.4.1 &lt;2.4.5&lt;ph=&#39;97&#39;/>） – 割引を含む注文のキャンセル時にエラーが表示される問題を修正します。*
* **MDVA-43451** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.4.3 &lt;2.4.5*） – エラー&#x200B;*リクエストされたストアが見つからなかった問題を修正します。 ストアを確認して、もう一度試してください。特定のweb サイトの共有カタログの設定中に*&#x200B;が表示されます。
* **MDVA-43491** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.3.5 &lt;2.4.5*） – マルチストア web サイトに商品を読み込む際にベース画像ラベルが更新されない問題を修正します。
* **MDVA-43601** （*Adobe CommerceおよびMagento Open Source >=2.3.0の場合>=2.4.5*） – 完全なインデックス再作成後に見つからないトリガーに関する問題を修正します。
* **MDVA-42046** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.3.4 &lt;=2.3.5-p2 ||>=2.4.0 &lt;2.4.5&lt;ph=&#39;97&#39;/>） – 製品の更新中に、日付入力フィールドで誤った値が製品属性に割り当てられる問題を修正します。*
* **MDVA-43935** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.4.1 &lt;2.4.5*） – アップセル商品が2回表示される問題を修正します。
* **MDVA-44188** （*Adobe CommerceおよびMagento Open Source >=2.4.3 &lt;2.4.5*） – システムで発行された`.-`のアドレスのメールが送信されない問題を修正します。
* **MDVA-42283** （*for Adobe Commerce and Magento Open Source >=2.3.0 &lt;2.4.5*） – フランス語ロケールの管理者注文グリッドの日時書式が無効になる問題を修正します。
* 更新されたパッチ：MDVA-41061-V2、MDVA-36309、MDVA-30862、MDVA-39713。
* [!DNL Site-Wide Analysis Tool]のパッチ メタデータを追加しました。

## v1.1.12 {#v1-1-12}

* **MDVA-39713** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.3.0 &lt;2.3.6*） – ユーザーがアクティブなスケジュール済み更新の開始時間を編集できる問題を修正します。
* **MDVA-42410** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.3.0 &lt;2.4.5*） – クーポンレポートでデフォルトの基本通貨のみが表示される問題を修正しました。
* **MDVA-41136** （*Adobe CommerceおよびMagento Open Source >=2.3.0 &lt;2.4.5*） - `mage-cache-sessid`の有効期限が延長されない問題を修正し、お客様のデータのクリーンアップを行います。
* **MDVA-39993** （*for Adobe Commerce and Magento Open Source >=2.3.5 &lt;=2.3.7-p2 || >=2.4.0 &lt;2.4.4*） - APIを介して行われた在庫変更がフロントエンドの商品ページに反映されない問題を修正します。
* **MDVA-42855** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.4.3 &lt;2.4.5*） – チェックアウト時に新しい顧客アドレスがアドレス帳に保存されない問題を修正します。
* **MDVA-42645** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.4.3 &lt;2.4.5*） – ストアクレジット機能が無効になっている場合に、管理者が報酬ポイントを返金できない問題を修正します。
* **MDVA-43414** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.3.6 &lt;=2.3.7-p2*） – 数値SKUで`inventory.reservations.updateSalabilityStatus` キューコンシューマーを実行すると発生するPHPの致命的なエラーを修正します。
* **MDVA-41628** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.4.0 &lt;2.4.5*） – 既存の制限付き管理者ユーザーが新しいモジュールを追加したときに新しいリソースにアクセスできる問題を修正します。
* **MDVA-43348** （*Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.5*）は、`gift_card_options`に&#x200B;*uid*&#x200B;が含まれている場合にギフトカードのGraphQL リクエストでエラーが表示される問題を修正します。
* **MDVA-39546** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.3.0 &lt;2.4.5*） – ステージング更新の開始日を、編集時に現在の日付より前の日付に設定できる問題を修正します。
* **MDVA-42950** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.3.0 &lt;2.4.5*） – 商品ページでビデオが再生されない問題を修正します。
* **MDVA-42689** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.3.0 &lt;2.4.4*） – インポート中に商品カテゴリを更新する際にAdobe Commerceが&#x200B;*Integrity Constraint Violation* エラーをスローする問題を修正します。
* **MDVA-41229** （*for Adobe Commerce and Magento Open Source >=2.3.0 &lt;2.4.5*） – バックエンドで使用可能な画像が、設定可能な製品の読み込み後にフロントエンドに表示されない問題を修正します。
* **MDVA-43731** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.4.3 &lt;2.4.4*） - *一致する最低条件*&#x200B;で値が追加された場合、*検索類義語*&#x200B;が機能しなくなる問題を修正します。
* **MDVA-43232** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.3.4 &lt;2.4.5*） - [!DNL Visual Merchandiser]の商品を特別価格で下/上に並べ替えると、カテゴリの保存中にエラーが発生する問題を修正します。
* **MDVA-43726** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.3.3 &lt;2.4.3*） – ストア レベルの属性に基づくカタログ価格ルールが部分的なインデックス再作成後に一致しない問題を修正します。
* 更新されたパッチ：MDVA-36464、MDVA-37478、MDVA-38608。
* [!DNL Site-Wide Analysis Tool]のパッチ メタデータを追加しました。

## v1.1.11 {#v1-1-11}

* **MDVA-42790** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.4.3 &lt;2.4.5*） - REST APIを使用して、特定のweb サイトの製品価格属性を更新できない問題を修正します。
* **MDVA-41350** （*for Adobe Commerce and Magento Open Source >=2.3.0 &lt;2.4.5*） – アクセスが制限された管理者ユーザーがSKUによってロールスコープ外の商品を注文で追加した場合に例外がスローされる問題を修正します。
* **MDVA-42269** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.4.3-p1 &lt;2.4.5*） - *TypeError: strtotime （）により管理者ユーザーが管理者にログインできない問題を修正します。パラメーター1は文字列で、nullが指定された* エラーです。
* **MDVA-40830** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.3.0 &lt;2.4.5*） – 注文時にストアクレジットが複数回適用される問題を修正します。
* **MDVA-42237** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.4.2 &lt;2.4.5*） – 設定可能な製品特別価格が、そのサブプロダクトプライスの変更後に更新されない問題を修正します。
* **MDVA-42520** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.4.3 &lt;2.4.4*） - *クロスボーダー取引を有効にする*&#x200B;を使用した場合に税率が2回適用される問題を修正します。
* 更新されたパッチ：MDVA-27239、MDVA-39305、MDVA-41236、MDVA-36832。
* 非推奨パッチ：MDVA-37725.

## v1.1.10 {#v1-1-10}

* **MDVA-38728** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.3.2 &lt;2.4.5*） - Mass属性の更新によってDefault StoreのURL書き換えが作成される問題を修正します。*商品の表示*&#x200B;を変更した後にのみ修正します。
* **MDVA-43091** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.4.3 &lt;2.4.4*） – バックエンドで管理者からバンドル商品を注文すると、*この商品に小数点数を使用できない*&#x200B;というエラーが発生する問題を修正します。
* **MDVA-40816** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.3.0 &lt;2.4.5*） – 関連商品ルールで、ルール条件で定義されていないカテゴリの商品が表示される問題を修正します。
* **MDVA-41305** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.4.2 &lt;2.4.5*） - GraphQLの突然変異がウィッシュリストに追加された後、設定可能な製品オプションを返さない問題を修正します。
* **MDVA-39181** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.4.1 &lt;2.4.5*） – 関連商品ルールで、ルール条件で定義されていないカテゴリの商品が表示される問題を修正します。
* **MDVA-42584** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.4.2 &lt;2.4.3*） – インポートまたはAPIで数量と在庫状況を変更した後、バックエンドの設定可能な在庫状況が更新されない問題を修正します。
* **MDVA-40175** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.4.0 &lt;2.4.3*） - *クリックして配送方法を変更*&#x200B;すると、再注文時に管理画面で配送方法を選択するためのラジオボタンが表示されない問題を修正します。
* **MDVA-42768** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.3.4 &lt;2.4.5*） - *在庫切れを表示*&#x200B;が「はい」の場合に、コンフィグ可能な商品が通常価格を0として表示する問題を修正します。
* **MDVA-43201** （*Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.4*）特定のロケールでDOB属性を使用する場合に、顧客ログインでエラーが発生する問題を修正します。
* 更新されたパッチ：MDVA-35092、MDVA-33970。

## v1.1.9 {#v1-1-9}

* **MDVA-38346** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.3.0 &lt;2.4.5*） - Adobe Commerce タイムゾーンがローカル環境のタイムゾーンと異なる場合に、日付フィルターが正しく機能しない問題を修正します。
* **MDVA-42657** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.4.1 &lt;2.4.5*） – 管理者ユーザーがカスタマーセグメント条件でカテゴリを選択できない問題を修正します。
* **MDVA-42806** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.4.2 &lt;2.4.4*） – 既存の会社がREST APIを介して更新されるたびに&#x200B;*新規会社登録* メールが送信される問題を修正します。
* **MDVA-37984** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.4.1 &lt;2.4.5*） - [!DNL Visual Merchandiser] *ルールによる商品の一致*&#x200B;機能で、ステージング更新で商品が正しくフィルタリングされない問題を修正します。
* **MDVA-40488** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.4.2 &lt;2.4.4*） – 在庫切れの子商品を含む設定可能な商品が正しい価格帯で表示されない問題を修正します。
* **MDVA-42507** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.4.3 &lt;2.4.5*） – カートルールにステージング更新を適用した後、ページ全体のキャッシュがクリーニングされる問題を修正します。
* **MDVA-39163** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.3.5 &lt;2.4.5*） – 新しいユーザーが登録され、カート内の商品がゲストセッションから送信されない場合に配送方法が利用できない問題を修正します。
* **MDVA-38626** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.3.3 &lt;2.4.5*） – 管理者ユーザーが[!DNL PayPal Payflow Pro]支払いを使用してバックエンドで注文できない問題を修正します。
* **MDVA-38666** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.3.2 &lt;2.3.6*） – 管理者ユーザーが顧客の買い物かごの設定可能な商品オプションを変更できない問題を修正します。
* **MDVA-38526** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.4.1 &lt;2.4.4*） – 管理者ユーザーが[!DNL Site-Wide Analysis tool]にアクセスできない問題を修正します。
* 更新されたパッチ：MDVA-40101.

## v1.1.8 {#v1-1-8}

* **MDVA-41215** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.3.0 &lt;2.4.4*） - *mage-messages* Cookieが既に存在するが、新しいメッセージがない場合に、ユーザーが500 エラーを取得する問題を修正します。
* **MDVA-41139** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.4.3 &lt;2.4.4*） – シンプルな商品の数量=0がソースの1つに対して商品をインポートすると、設定可能な商品が在庫切れになる問題を修正します。
* **MDVA-42326** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.3.6 &lt;=2.3.7-p2 ||>=2.4.1 &lt;2.4.4&lt;ph=&#39;97&#39;/>） – 永続的なショッピングカートが有効になっている場合でも、セッションのタイムアウト後にチェックアウト時にエラーが発生する問題を修正します。*
* **MDVA-42341** （*for Adobe Commerce and Magento Open Source >=2.4.2 &lt;2.4.4*） – リクエストにStore ヘッダーがある場合、`categoryList` GraphQL クエリで結果がフィルタリングされない問題を修正します。
* **MDVA-38393** （*for Adobe Commerce and Magento Open Source >=2.3.0 &lt;2.4.4*） – シンプルな商品の名前が変更された場合に、カタログ ルールが設定可能な商品で機能しなくなる問題を修正します。
* **MDVA-39153** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.4.2 &lt;2.4.4*） – 管理者での再発注中に割引額が誤って計算される問題を修正します。
* 更新されたパッチ：MDVA-28993、MDVA-41061、MDVA-35984。

## v1.1.7 {#v1-1-7}

* **MDVA-39711** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.3.0 &lt;2.4.3*） – 管理者ユーザーがweb サイトを削除した後に顧客のグリッドにアクセスできない問題を修正します。
* **MDVA-40311** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.4.2-p2 &lt;2.4.4*） – 管理者ユーザーがエラーメッセージ *無効なセキュリティまたはフォームキーを取得する問題を修正します。 カスタム管理者パスが設定され、秘密鍵が有効になっている場合は、管理者にログインした後でページ*&#x200B;を更新してください。
* **MDVA-41631** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.4.1 &lt;2.4.4*） - GraphQLを通じてオプションの&#x200B;*phone*&#x200B;値を指定せずに注文情報を取得しようとすると、エラーが発生する問題を修正します。
* **MDVA-27239** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.3.0 &lt;2.3.6*） – クロスセル商品が表示されない問題を修正します。
* 更新されたパッチ：MDVA-37068、MDVA-35254、MDVA-41164、MDVA-37916、MDVA-37478、MDVA-34551、MDVA-31791。

## v1.1.6 {#v1-1-6}

* **MDVA-40550** （*for Adobe Commerce and Magento Open Source >=2.3.5 &lt;2.4.4*） – インデックス再作成中にフロントエンドで見つからない商品に関する問題を修正します。
* **MDVA-40120** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.4.1 &lt;2.4.4*） - DESC/ASCによるGraphQLの並べ替えが、同じ関連性または価格の商品で機能しない問題を修正します。
* **MDVA-41399** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.3.3 &lt;2.4.2*） – お客様がウィッシュリストに商品を追加した場合、管理者ユーザーが&#x200B;*ショッピングカートの管理* ページにアクセスできない問題を修正します。
* **MDVA-40609** （*Adobe CommerceおよびMagento Open Source >=2.4.2 &lt;2.4.3*） - `cataloginventory_stock_status` インデックステーブルで無効な商品データが存在しない問題を修正し、無効な商品の数量が正しく表示されなくなりました。
* **MDVA-39031** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.4.1 &lt;2.4.4*） – ターゲット web サイトに割り当てられていない場合でも、GraphQLを介して商品をカートに追加できる問題を修正します。
* **MDVA-41597** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.4.2 &lt;2.4.4*） - GraphQLを使用して複数の設定可能な商品をカートに追加する際にエラーが発生する問題を修正します。
* **MDVA-27456** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.3.5 &lt;2.3.7*） - [!DNL Swagger]の読み込み時にエラーが発生する問題を修正します。
* **MDVA-32776** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.4.0 &lt;2.4.2*） – 注文が行われたが発送されなかった場合に、在庫状況が更新されない問題を修正します。
* **MDVA-30862** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.3.4 &lt;2.4.0*） – 印刷されたPDF請求書の誤った注文日に関する問題を修正します。
* [!DNL Quality Patch Tool]のインデックスページを改善しました。 最新バージョンのツールで[!DNL quality patches]の便利な検索とフィルタリングを追加しました。
* 更新されたパッチ：MDVA-33382、MDVA-39482。

## v1.1.5 {#v1-1-5}

* **MDVA-41236** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.3.0 &lt;2.4.4*） – 終了日が以前に削除された場合に、新しい商品を作成したり、既存のスケジュールされた商品の更新を編集したりできない問題を修正します。
* **MDVA-41046** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.3.0 &lt;2.4.4*） – カスタムオプションを持つシンプルな商品が、設定可能/グループ化された商品に割り当てることができる問題を修正します。
* **MDVA-40545** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.3.0 &lt;2.4.4*） – 同じページに複数のノードがある場合でも、ページの最初のノードのみが取得される問題を修正します。
* **MDVA-41164** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.4.2 &lt;2.4.3-p1*） – 管理者ユーザーがファイルまたは画像タイプのカスタム顧客属性を持つ会社を保存または編集できない問題を修正します。
* **MDVA-39229** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.3.0 &lt;2.4.4*） – カタログルールステージングの更新開始時間を更新した後に次のエラーが表示される問題を修正します。*Cron Job staging_synchronize_entities_periodにエラーがあります。アクティブな更新を削除できません。*
* **MDVA-40619** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.3.0 &lt;2.4.4*） - CMS ページでインライン編集を試みたときにCMS ページ階層が変更された場合に500 エラーが発生する問題を修正します。
* **MDVA-41061** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.4.2 &lt;2.4.3*） – 管理者から商品を保存すると、在庫状況が販売可能にリセットされる問題を修正します。
* **MDVA-31763** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.3.0 &lt;2.4.4*） – カタログ価格ルールが手動でインデックス再作成されるまで元に戻される（または適用されない）問題を修正します。
* **MDVA-37748** （*for Adobe Commerce and Magento Open Source >=2.4.2 &lt;2.4.3*） - GraphQL クエリが共有カタログに割り当てられていない商品を返す問題を修正します。

## v1.1.4 {#v1-1-4}

* **MDVA-40399** （*Adobe CommerceとMagento Open Sourceの場合>=2.4.2 &lt;2.4.4*） - REST APIで同じ注文の部分的な請求書を同時に作成できない問題を修正します。
* **MDVA-40101** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.3.2 &lt;2.4.0*） - [!DNL PayPal Express] チェックアウトを使用して注文を完了した後、ミニカートから商品が削除されない問題を修正します。
* **MDVA-40401** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.3.6 &lt;=2.3.7-p2 ||>=2.4.1 &lt;2.4.4&lt;ph=&#39;97&#39;/>） – 注文が失敗した場合でも、クーポン使用価値が変更される問題を修正します。*
* **MDVA-40537** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.3.4 &lt;=2.4.0-p1*） – 同じURL キーを持つ複数のCMS ページが存在する場合に、ストアビューを作成する際にエラーが発生する問題を修正します。
* **MDVA-37725** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.3.0 &lt;=2.4.3-p1*） – デフォルト以外のWeb サイトから送信された非同期注文メールに、デフォルトのWeb サイトのロゴ URLが含まれる問題を修正します。
* **MDVA-39482** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.3.6 &lt;=2.3.7-p2 ||>=2.4.1 &lt;2.4.4*） – バックオーダーが有効になっている場合に「0」の数量でインポートすると、商品が在庫切れになる問題を修正します。
* **MDVA-40435** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.3.4 &lt;2.4.4*） - GraphQLを介して適用した場合に、バンドル商品の誤った割引が適用される問題を修正します。
* **MC-42528** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.4.3 &lt;=2.4.3-p1*） - `categoryList` GraphQL クエリが割り当て済みカテゴリと未割り当てカテゴリの両方を返す問題を修正します。
* **MDVA-29400** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.3.0 &lt;=2.3.7-p1 ||>=2.4.0 &lt;=2.4.0-p1*） - &lt;ph=&#39;158&#39;/>で注文が重複する問題を修正します。[!DNL PayPal Express Checkout]
* **MDVA-26005** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.3.4 &lt;=2.3.5-p2*） – カート価格ルール条件のカテゴリーツリーでカテゴリを選択できない問題を修正します。
* **MDVA-25631** （*for Adobe Commerce and Magento Open Source >=2.3.3 &lt;=2.3.5-p2*） – 多数のお客様を含む顧客セグメントを編集および保存する際のパフォーマンスを向上させます。

## v1.1.3 {#v1-1-3}

* **MDVA-40262** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.4.2 &lt;2.4.4*） - AdminでGraphQL検索クエリが一般的な検索語に表示されない問題を修正します。
* **MDVA-40601** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.3.1 &lt;=2.4.2-p2*） - GraphQLを通じてスケジュールされた更新によって変更されたカテゴリに関する情報を取得しようとするとエラーが発生する問題を修正します。
* **MDVA-37234** （*for Adobe Commerce and Magento Open Source >=2.3.5 &lt;2.4.0 |>=2.4.1 &lt;=2.4.2-p2*） – 同じSKUに商品を複数回カートに追加すると、同じカート IDに対して重複した商品が作成される問題を修正します。
* **MDVA-33606** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.4.1 &lt;=2.4.2-p2*） – 階層に割り当てられたCMS ページを保存する際に&#x200B;*一意の制約の違反*&#x200B;が発生する問題を修正します。
* **MDVA-31590** （*for Adobe Commerce and Magento Open Source >=2.4.0 &lt;=2.4.1-p1*） – ユーザーがMySQL非同期キューを使用して属性を一括で更新できない問題を修正します。
* **MDVA-36309** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.4.2 &lt;=2.4.2-p2*） – 管理者グリッドで属性による商品検索が遅くなる問題を修正します。

## v1.1.2 {#v1-1-2}

* **MDVA-38929** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.3.0 &lt;2.4.4*） – 注文が店舗のクレジットから支払われた場合にFPTの請求書に間違った合計金額が表示される問題を修正します。
* **MDVA-37364** （*for Adobe Commerce and Magento Open Source >=2.4.0 &lt;=2.4.3*） – 日付タイプのカスタム顧客属性が顧客のグリッド UIを壊す問題を修正します。
* **MDVA-39195** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.4.2 &lt;=2.4.2-p2*） – 「買い物かごにリダイレクト」が有効になっている場合に、カテゴリーページで&#x200B;*買い物かごに追加* ボタンが無効になる問題を修正します。
* **MDVA-37115** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.4.2 &lt;=2.4.2-p2*） – コンフィグ可能な製品ページに不要な&#x200B;*左のみ0*&#x200B;の通知が表示される問題を修正します。
* **MDVA-39521** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.4.0 &lt;2.4.4*） – ユーザーがGraphQLを介して空の電話番号を使用してカートに配送先住所を設定できない問題を修正します。
* **MDVA-39384** （*for Adobe Commerce and Magento Open Source >=2.3.1 &lt;=2.3.6 |>=2.4.1 &lt;=2.4.3*） – 会社ユーザーのカスタム顧客属性が保存されない問題を修正します。
* **MDVA-39043** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.3.4 &lt;=2.4.3*） – アクセスが制限された管理者ユーザーが&#x200B;*Products* ウィジェットをCMS ページに追加しようとするとエラーが発生する問題を修正します。
* **MDVA-39966** （*for Adobe Commerce and Magento Open Source >=2.3.0 &lt;=2.3.5-p2 || >=2.4.0 &lt;=2.4.0-p1*） – 誤ったロケールのデプロイに関する問題を修正します。
* **MDVA-38852** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.3.0 &lt;=2.3.5-p2*） – 複数の並列注文の場合に、パフォーマンスを大幅に低下させる更新のために、カタログの在庫がテーブルをロックする問題を修正します。
* **MDVA-39986** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.4.1 &lt;2.4.3*） - Safari ブラウザーを使用してMacOSの管理画面で注文できない問題を修正します。
* **MDVA-38447** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.4.2 &lt;2.4.4*） - 2つの問題を修正しました。GraphQLのレスポンスで&#x200B;*個別に表示されない*&#x200B;設定可能な子商品が返され、カテゴリーフィルターを使用してGraphQL商品クエリ用のMySQL クエリを最適化しました。
* **MDVA-40134** （*for Adobe Commerce and Magento Open Source >=2.4.2 &lt;2.4.3*） - Shared Catalogが有効になっている場合にGraphQLが関連商品を返さない問題を修正します。
* **MDVA-39935** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.4.1 &lt;2.4.4*） - GraphQLがweb サイト レベルで無効な設定可能な子商品を返す問題を修正します。

## v1.1.1 {#v1-1-1}

* **MDVA-36021** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.4.0 &lt;2.4.4*） – メンバー関数getId （） *への呼び出しエラーが管理画面の注文詳細ページに表示される問題を修正します。*
* **MDVA-34948** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.3.6 &lt;=2.3.6-p1 ||>=2.4.0 &lt;=2.4.0-p1*） - `GET_LOCK`のような長時間実行されるクエリの問題を修正します。
* **MDVA-39305** （*Adobe CommerceおよびMagento Open Sourceの場合>=2.4.0 &lt;=2.4.2-p1*） – 登録ユーザーが有効なGoogle ReCaptchaでログインできない問題を修正します。
* **MDVA-37897** （*for Adobe Commerce and Magento Open Source >=2.3.0 &lt;2.4.4*） – お客様が最近表示されたウィジェットからオプションを含む商品を追加しようとすると、誤ったリダイレクトが発生する問題を修正します。

## v1.1.0 {#v1-1-0}

* パッチカテゴリは、ユーザーエクスペリエンスを向上させ、顧客が必要なパッチを簡単に検索できるようにするために導入されました。
* `patches.json` ファイルの名前が`support-patches.json`に変更されました。
* **MDVA-38799** （*for Adobe Commerce >=2.3.0 &lt;2.4.3*） – ステージング更新を作成した後にダウンロード可能な製品が保存されなかった問題を修正します。
* **MDVA-37592** （*for Adobe Commerce >=2.3.6 &lt;=2.4.2-p1*） – 共有カタログに割り当てられた価格がゼロの商品の価格で並べ替えが正しく機能しない問題を修正します。
* **MDVA-38827** （*for Adobe Commerce >=2.3.3-p1 &lt;2.4.4*） – お客様がエラーメッセージを含む注文出荷メールを受信する問題を修正します。

## v1.0.26 {#v1-0-26}

* **MDVA-38468** （*for Adobe Commerce >=2.3.2 &lt;=2.3.5-p2*） - CMS ページを保存する際のエラーを修正します：*同じID PAGE_IDのアイテムが既に存在します*。
* **MDVA-34680** （*for Adobe Commerce >=2.3.6 &lt;=2.3.7 || >=2.4.1 &lt;2.4.3*） – カスタマーグリッドでカスタマーアカウントの作成時間が正しくフィルタリングされない問題を修正します。
* **MDVA-37068** （*for Adobe Commerce >=2.3.1 &lt;2.4.4*） – ショッピングカートにバーチャル商品のみが含まれている場合に、誤った税率が表示される問題を修正します。
* **MDVA-38608** （*for Adobe Commerce >=2.3.0 &lt;2.4.3*） – 再インデックスが正常に完了しなかった場合に一時テーブルが削除されない問題を修正します。
* **MDVA-38308** （*for Adobe Commerce >=2.3.5 &lt;=2.3.6-p1 || >=2.4.0 &lt;=2.4.1-p1 || >=2.4.2 &lt;2.4.4*） - [!DNL Vimeo]のビデオを製品に追加する際の問題を修正します。

## v1.0.25 {#v1-0-25}

* **MDVA-37916** （*for Adobe Commerce >=2.3.6 &lt;2.4.3*） - [!DNL Paypal Payment Advanced]方式を使用しているお客様が支払い確認ページに移動しない問題を修正します。
* **MDVA-37082** （*for Adobe Commerce >=2.3.0 &lt;2.4.3*） – グループ化された商品のカスタムストックを保存すると、商品がフロントエンドで在庫切れになる問題を修正します。
* **MDVA-36572** （*for Adobe Commerce >=2.3.5 &lt;2.4.3*） – クレジットメモの更新により、データベースで重複した商品予約の更新が発生しなくなった問題を修正します。
* **MDVA-38132** （*for Adobe Commerce >=2.3.3 &lt;2.4.3*） - *リダイレクトが多すぎるため、管理パネルにアクセスできない場合の問題を修正します* エラー。
* **MDVA-38270** （*for Adobe Commerce >=2.4.1 &lt;2.4.3*） - GraphQLの注文合計にギフトカード情報が見つからない問題を修正します。

## v1.0.24 {#v1-0-24}

* **MDVA-37779** （*for Adobe Commerce >=2.4.2 &lt;=2.4.4*） - web サイト IDとストア IDが一致しない場合に、GraphQLを介して構成可能な商品をカートに追加する際の問題を修正します。
* **MDVA-36832** （*for Adobe Commerce >=2.3.4 &lt;=2.4.2-p1*） – ビューの幅が768 pxの場合に、画像がページ上で重複する問題を修正します。
* **MDVA-37874** （*for Adobe Commerce >=2.3.6 &lt;=2.3.7 || >=2.4.1 &lt;=2.4.2-p1*） - *カート全体の固定割引額*&#x200B;が複数のオプションを含むバンドル商品に誤って適用される問題を修正しました。
* **MDVA-37913** （*for Adobe Commerce >=2.3.0 &lt;=2.4.0-p1*） – ダウンロード可能な商品がAPIを介して更新された場合に、ダウンロード可能なリンクが消える問題を修正します。
* **MDVA-34330** （*for Adobe Commerce >=2.3.1 &lt;=2.4.2-p1*） – 管理者タイムゾーンに従って、注文グリッドの注文がフィルタリングされない問題を修正します。

## v1.0.23 {#v1-0-23}

* **MDVA-37478** （*for Adobe Commerce >=2.3.0 &lt;=2.3.7*） - REST APIを介して&#x200B;*アカウントの支払い*&#x200B;の支払い方法で行われた注文に対して、Adobe Commerceが部分的な請求書を作成する際にエラーをスローする問題を修正します。
* **MDVA-37362** （*for Adobe Commerce >=2.3.4 &lt;=2.4.2-p1*） - GraphQL応答で設定可能な製品オプション値とバリアント属性値が空だった問題を修正します。
* **MDVA-37288** （*Adobe Commerce 2.4.2*&#x200B;の場合） - GraphQLのリクエスト後に誤った階層の価格が返された問題を修正します。
* **MDVA-37225** （*for Adobe Commerce >=2.4.1 &lt;=2.4.2-p1*） – インポートしたSKUに整数値がある場合に、迅速な注文作成中にアップロードプロセスが停止する問題を修正します。
* **MDVA-37224** （*for Adobe Commerce >=2.3.3 &lt;=2.4.2-p1*） – お客様が別の商品をカートに入れた状態で[!DNL PayFlow Pro]との交渉可能な見積もりに対して支払えない問題を修正します。
* **MDVA-36286** （*for Adobe Commerce >=2.3.6 &lt;=2.4.2-p1*） – 同じSKUがサブカテゴリ内で異なる位置にある場合にページビルダー製品ウィジェットのプレビューが壊れる問題を修正します。
* **MDVA-30186** （*for Adobe Commerce >=2.3.4 &lt;=2.3.5-p2, >=2.4.0 &lt;=2.4.0-p1, >=2.4.2 &lt;=2.4.2-p1*） - GraphQL応答で、属性オプションが属性項目数ではなくオプション値で並べ替えられる問題を修正します。

## v1.0.22 {#v1-0-22}

* **MDVA-36718** （*for Adobe Commerce >=2.3.0 &lt;=2.4.2*） - APIを介して変更した後、古いカスタムオプションが残る問題を修正します。
* **MDVA-35773** （*for Adobe Commerce >=2.3.6 &lt;=2.3.6-p1 || >=2.4.1 &lt;=2.4.2*） - 100%割引の注文の請求書でGrand Totalがゼロとして表示されない問題を修正します。
* **MDVA-36833** （*Adobe Commerce 2.4.2*&#x200B;の場合） – 共有カタログから一部の商品を除外した後、1 ページあたりの商品のランダムな数が検索結果に表示される問題を修正します。
* **MDVA-37182** （*for Adobe Commerce >=2.4.1 &lt;=2.4.2*） – バージョン 6とバージョン 7の両方で誤った検索結果を取得する問題を修正します。[!DNL Elasticsearch]
* **MDVA-36253** （*for Adobe Commerce >=2.4.0 &lt;=2.4.1-p1*） – アイテムの削除後にミニ カートに間違った小計が表示される問題を修正します。
* **MDVA-36853** （*Adobe Commerce 2.4.2*&#x200B;の場合） – 大きなメディアギャラリーを読み込む際に画像が表示されない問題を修正します。

## v1.0.21 {#v1-0-21}

* **MDVA-34665** （*for Adobe Commerce >=2.3.4 &lt;=2.3.4-p2*） – カテゴリーページにバンドルされた商品が見つからない問題を修正します。
* **MDVA-36615** （*Adobe Commerce 2.4.2*&#x200B;の場合） – 管理者製品グリッドの誤った製品数の問題を修正します。
* **MDVA-36464** （*for Adobe Commerce >=2.4.0 &lt;=2.4.2*） – メール通知設定がストアビューレベルで機能しない問題を修正します。
* **MDVA-36138** （*Adobe Commerce ^2.3.2*&#x200B;の場合） – カート内のすべての商品が送料無料カートルールに適格でない場合に、送料が調整されず、完全な送料価格がお客様に表示される問題を修正します。
* **MDVA-36424** （*for Adobe Commerce >=2.3.0 &lt;=2.3.3-p1 || >=2.0.0 &lt;2.2.0*） – バックエンドのベース URLがストアフロントのベース URLと異なる場合に、コンテンツを繰り返し編集すると、ページビルダー要素に添付されたメディア画像が消える問題を修正しました。
* **MDVA-35984** （*Adobe Commerce ^2.4.0*&#x200B;の場合） – 同じ商品に対して複数回の同時出荷を作成した後、誤った商品数量と販売可能な数量の問題を修正します。

## v1.0.20 {#v1-0-20}

* **MDVA-36170** （*for Adobe Commerce >=2.3.4 &lt;2.4.2*） – カテゴリキャッシュタグを使用して、GraphQL クエリがキャッシュされない問題を修正します。
* **MDVA-33168** （*for Adobe Commerce >=2.3.3 &lt;2.4.2*） - APIを介して製品属性を更新する際に、その他のすべての属性が空の値に変更される問題を修正します。
* **MDVA-19640** （*for Adobe Commerce >=2.3.0*） - [!DNL Advanced Reporting]でデータが表示されない問題を修正します。
* **MDVA-11189** （*for Adobe Commerce >=2.3.0 &lt;2.3.5*） - CSV ファイルを読み込んで商品の在庫を更新すると、`cataloginventory_stock` テーブルの行が削除される問題を修正します。
* **MDVA-26639** （*for Adobe Commerce >=2.3.3-p1 &lt;2.3.6*） – 新しい注文確認メールテンプレートが作成された場合、注文商品が注文メールに表示されない問題を修正します。
* **MDVA-15546** （*for Adobe Commerce >=2.3.0*） – 注文を作成した後、*列entity_id where句があいまいな* エラーが例外ログに表示される問題を修正します。
* **MDVA-21095** （*for Adobe Commerce >=2.3.0 &lt;2.3.5*） – クエリ `INSERT INTO search_tmp`が一括属性値の更新後に終了しない問題を修正します。
* **MDVA-23845** （*for Adobe Commerce >=2.3.2-p2 &lt;2.3.5*） - JavaScriptの縮小を有効にした後にメールテンプレートをプレビューできない問題を修正します。
* **MDVA-22026** （*for Adobe Commerce >=2.3.2 &lt;2.3.4*） - CSV ファイルから外部URLの画像を含む商品を読み込む際に失敗する問題を修正しました。
* **MDVA-22383** （*for Adobe Commerce >=2.3.0 &lt;2.3.4*） – 商品の保存に時間がかかり、ページが壊れる問題を修正します。
* **MC-41359** （*for Adobe Commerce >=2.3.6-p1 &lt;2.3.7, >=2.4.2 &lt;2.4.3*） – 誤ったSameSite cookie パラメーター設定の問題を修正します。

## v1.0.19 {#v1-0-19}

* **MDVA-33614** （*Adobe Commerce 2.4.1*&#x200B;の場合） - Page Builderで次のエラーがスローされる問題を修正します。*Page Builderの起動中にエラーが発生しました。 テクニカルサポートの連絡先にお問い合わせください。*
* **MDVA-35356** （*for Adobe Commerce >=2.3.0 &lt;2.4.3*） – 一部の請求済み注文キャンセル後の誤った店舗クレジット返品に関する問題を修正します。
* **MDVA-33289** （*for Adobe Commerce >=2.4.0 &lt;2.4.3*） - [!DNL Google Tag Manager]が有効になっている場合に、チェックアウト時に請求先住所UIに未加工のJavaScript コードが表示される問題を修正します。
* **MDVA-35982** （*for Adobe Commerce >=2.3.0 &lt;2.4.3*） – 特定のweb サイトに制限された管理者ユーザーが、同じweb サイトに配置された注文の配送を作成できない問題を修正します。
* **MDVA-35155** （*for Adobe Commerce >=2.3.0 &lt;2.3.6*） – オプションタイトルが変更された場合にバンドル商品を購入できない問題を修正しました。
* **MDVA-35910** （*for Adobe Commerce >=2.4.1 &lt;2.4.3*） – 「お客様としてログイン」機能を無効にした後、新しい顧客アカウントを作成できない問題を修正します。
* **MDVA-34474** （*for Adobe Commerce >=2.3.0 &lt;2.4.3*） - APIを使用して商品を購買リストに追加する際の問題を修正します。
* **MDVA-34591** （*for Adobe Commerce >=2.3.0 &lt;2.4.3*） - *最大数量の割引が*&#x200B;および&#x200B;*割引数量ステップ （購入X）*&#x200B;に適用される場合の間違ったカートルールの割引計算に関する問題を修正します。
* **MDVA-33704** （*for Adobe Commerce >=2.4.0 &lt;2.4.3*） - *実店舗での受け取り*&#x200B;の配送オプションが表示されない問題を修正します。ただし、利用可能に設定されています。
* **MDVA-34928** （*for Adobe Commerce >=2.3.5 &lt;2.3.5-p2*） – ストアクレジットが支払いから削除された後、ページローダーが無期限に表示される問題を修正します。
* **MDVA-35254** （*for Adobe Commerce >=2.3.1 &lt;2.4.3*） – チェックアウト時のCAPTCHAの問題を修正します。
* **MDVA-35569** （*for Adobe Commerce >=2.3.4 &lt;2.4.2*） – ステートが指定されたときに&#x200B;*固定製品税* フィールドがGraphQL応答に入力されない問題を修正します。
* **MDVA-35847** （*for Adobe Commerce >=2.4.1 &lt;2.4.3*） – カスタム顧客属性が使用されている場合にCompany Users フォームが壊れるB2Bの問題を修正します。
* **MDVA-31307** （*for Adobe Commerce >=2.4.0 &lt;2.4.2*） – キャッシュ ブロックの動的CSP ホワイトリスト登録に関する問題により、特定のカテゴリで&#x200B;*メモリ不足* エラーが発生する問題を修正します。

## v1.0.18 {#v1-0-18}

* **MDVA-32655** （*for Adobe Commerce >=2.3.0 &lt;2.4.3*） – 複数の商品を削除した後、コンシューマー&#x200B;*の正しい* complete *メッセージに対する誤った* in progress`quoteItemCleaner` メッセージのステータスを修正します。
* **MDVA-34102** （*for Adobe Commerce >=2.3.0 &lt;2.4.3*） - Product GridおよびAdmin エリアのEdit Product ページで、無効な商品のデフォルトストックの数量がゼロになる問題を修正しました。
* **MDVA-35286** （*for Adobe Commerce >=2.4.0 &lt;2.4.2*） – お客様が買い物かごに商品をバンドルし、複数アドレスのチェックアウトからワンページチェックアウトに切り替えた場合にエラーが発生する問題を修正します。
* **MDVA-35312** （*for Adobe Commerce >=2.4.1-p1 &lt;2.4.2*） – 空のGraphQL リクエストの場合の応答コード 500を修正します。
* **MDVA-34189** （*for Adobe Commerce >=2.3.4 &lt;2.4.3*） - Admin Category ページの読み込み時に[!DNL Visual Merchandiser] クエリで503の最初のバイトのタイムアウトが発生する問題を修正しました。
* **MDVA-34695** （*for Adobe Commerce >=2.3.0 &lt;2.4.1*） – カテゴリを削除した後の負の`children_count`を修正します。

## v1.0.17 {#v1-0-17}

* **MDVA-34012** （*for Adobe Commerce >=2.3.1 &lt;2.4.3*） – スケジュールされた変更が適用された後、*デフォルト値を使用* チェックボックスがクリアされる問題を修正します。 スケジュールされた変更が有効でなくなると、問題が表示されます。
* **MDVA-35064** （*for Adobe Commerce >=2.3.3 &lt;2.4.3*） - APIで作成された設定可能な製品に対してURLの書き換えが生成されない問題を修正します。
* **MDVA-34943** （*for Adobe Commerce >=2.3.0 &lt;2.4.2*） – クイック注文が以前に入力されたSKUをキャッシュする問題を修正します。
* **MDVA-35197** （*for Adobe Commerce >=2.3.5 &lt;2.4.0*） – 以前に追加した商品が在庫切れになった場合に、GraphQLを使用してカートに追加する際にエラーが発生する問題を修正します。
* **MDVA-34850** （*for Adobe Commerce >=2.3.1 &lt;2.4.0*） – コンフィグ可能な商品の在庫切れオプションが、取り消し線として表示されずに表示されない問題を修正します。
* **MDVA-34867** （*for Adobe Commerce >=2.3.0 &lt;2.4.3*） – スケジュールされた更新に設定された条件フィールドの値が保存されない問題を修正します。
* **MDVA-35092** （*for Adobe Commerce >=2.3.5 &lt;2.4.3*） – 非推奨の[!DNL Vimeo] APIが原因で、ユーザーが[!DNL Vimeo] ビデオを追加できない問題を修正します。

## v1.0.16 {#v1-0-16}

* **MDVA-33453** （*for Adobe Commerce >=2.3.6 &lt;2.4.3*） – 一致する製品の価格がweb サイトごとに異なる場合に、ページビルダー製品のコンテンツタイプのプレビューが壊れる問題を修正します。
* **MDVA-32634** （*Adobe Commerce ^2.3.1*&#x200B;の場合） – 階層内のカテゴリを移動した後、すべてのストアに割り当てられたカテゴリの`url_path`が変更されない問題を修正します。
* **MDVA-33344** （*Adobe Commerce ^2.3.0*&#x200B;の場合） – ハードコードされた`rma_item` エンティティのデフォルト属性セット IDが、データベースの値の代わりに使用される問題を修正します。
* **MDVA-34192** （*for Adobe Commerce >=2.3.4 &lt;2.4.3*） - dd/mm/yyyy形式を使用して、お客様の生年月日を変更または指定できない問題を修正します。
* **MDVA-34847** （*Adobe Commerce ^2.3.0*&#x200B;の場合） – カスタム権限を持つ管理者ユーザーの管理コレクションで、ストア IDのタイプ変換をSQL条件の整数に修正します。
* **MDVA-34886** （*Adobe Commerce ^2.3.2*&#x200B;の場合） - *weight*&#x200B;の製品属性が検索可能として設定されている場合に、検索で結果が返されない問題を修正します。

## v1.0.15 {#v1-0-15}

* **MDVA-33559** （*for Adobe Commerce >=2.3.0 &lt;2.4.3*） – リダイレクトパラメーターリスト形式エラーで[!DNL PayPal Payflow Pro]支払いが失敗する問題を修正します。
* **MDVA-34023** （*for Adobe Commerce >=2.3.0 &lt;2.4.3*） – エラー&#x200B;*No such entity with addressId*&#x200B;が訪問者のブラウザーにランダムに表示される問題を修正します。
* **MDVA-32759** （*for Adobe Commerce >=2.3.1 &lt;2.4.3 with B2B extension*） - Shared Catalogsが既存の階層の価格を削除している問題を修正します。
* **MDVA-33482** （*Adobe Commerce ^2.3.5*&#x200B;の場合） – 部分的な請求書に対してクレジットメモを生成すると、その部分的な請求書に対して税金ではなく合計注文に対して税金が発生する問題を修正します。
* **MDVA-33393** （*for Adobe Commerce >=2.3.0 &lt;2.4.2*） – エラー&#x200B;*提供されたcountryIdが存在しない*&#x200B;を修正します。
* **MDVA-33632** （*for Adobe Commerce >=2.3.0 &lt;2.3.7*） – 在庫切れ商品の再注文を試みたときに、管理者ユーザーに「この商品は在庫切れです」という例外メッセージ *が表示されるようになりました*。
* **MDVA-34469** （*for Adobe Commerce >=2.4.1 &lt;2.4.2*） – 複数のストアビューを使用する場合に、顧客のカートでGraphQLの変更が失敗する問題を修正します。
* **MDVA-33976** （*for Adobe Commerce >=2.3.0 &lt;2.3.7*） – バンドル商品から2番目のオプションを削除した後、ストアフロントでバンドル商品が在庫切れと表示される問題を修正します。
* **MDVA-33894** （*for Adobe Commerce >=2.4.0 &lt;2.4.1 with B2B extension*） – 複数の商品の追加と削除、SKUの大文字と小文字の区別など、クイックオーダー機能に関する複数の問題を修正します。
* **MDVA-27664** （*for Adobe Commerce >=2.3.4 &lt;2.3.6*） – お客様登録フォームの表示エラーの問題を修正します：*エラー – 生年月日を今日より大きくすることはできません。*
* **MDVA-33970** （*for Adobe Commerce >=2.3.4 &lt;2.4.2*） – 価格属性の範囲がweb サイトに設定されている場合に、クレジットメモに誤った通貨記号がある問題を修正します。
* **MDVA-33992** （*for Adobe Commerce >=2.3.0 &lt;2.4.2*） – チェックアウト時にB2B特別価格が正しく表示されない問題を修正しました。
* **MDVA-34100** （*for Adobe Commerce >=2.3.4 &lt;2.4.2 with B2B extension*） – 会社構造ページから会社アカウントを作成できない問題を修正します。

## v1.0.14 {#v1-0-14}

* **MDVA-31969** （*for Adobe Commerce >=2.3.3 &lt;2.3.5, >=2.4.0 &lt;2.4.2*） - CSV ファイルから商品を読み込んだ後に画像が重複する問題を修正します。
* **MDVA-33382** （*for Adobe Commerce >=2.3.0 &lt;2.4.2*） – カテゴリから製品を削除した後にインデクサーが無効化される問題を修正します。
* **MDVA-28511** （*for Adobe Commerce >=2.3.5 &lt;2.3.6*） – 「名前」フィールドに特定の文字（アクセント付きの大文字など）が含まれている場合に[!DNL PayPal] チェックアウトを完了できない問題を修正します。
* **MDVA-31519** （*for Adobe Commerce >=2.3.5 &lt;2.3.6*） – サイト全体の営業ルールを使用している場合のゲストチェックアウトでの待機タイムアウトの問題を修正します。
* **MDVA-33281** （*for Adobe Commerce >=2.3.4 &lt;2.3.6*） - SKU パラメーターの種類が間違っているため、`inventory:reservation:list-inconsistencies`で致命的なエラーが発生する問題を修正します。
* **MDVA-24201** （*for Adobe Commerce >=2.3.0 &lt;2.3.5*） – 手動でインデックスを再作成するまで、価格がスケジュールされたカート価格ルールを反映しない問題を修正します。
* **MDVA-32694** （*for Adobe Commerce >=2.3.0 &lt;2.3.6 || >= 2.4.0 &lt;2.4.2*） – 管理者ユーザーがネゴシエブル見積に商品を追加できない問題を修正します。商品がデフォルト以外のストアに関連している場合に、この問題を修正します。
* **MDVA-33516** （*for Adobe Commerce >=2.3.0 &lt;2.3.6*） – 要件リストでバンドル製品を編集するとエラーが発生する問題を修正します。
* **MDVA-33975** （*for Adobe Commerce >=2.3.4 &lt;2.4.2*） - GraphQL リクエストの価格計算に関する複数の問題を修正します。

## v1.0.13 {#v1-0-13}

* **MDVA-30858** （*for Adobe Commerce >=2.3.0 &lt;2.4.2*） - [!DNL PayPal]決済レポートが&#x200B;**Reports** > **Sales** > **[!DNL PayPal]**&#x200B;決済で利用できない問題を修正します。
* **MCP-87** （*for Adobe Commerce >=2.3.1 &lt;2.4.2*） – 大きなプロファイルのカテゴリ商品とストックインデクサーのインデックス作成時間を改善しました。
* **MDVA-33106** （*for Adobe Commerce >=2.3.0 &lt;2.4.2*） - cron `run` コマンドの実行後に再スケジュールされた製品変更が消去される問題を修正します。
* **MDVA-19391** （*for Adobe Commerce >=2.3.0 &lt;2.3.5*） - `analytics_collect_data`が`catalog_category_entity_text` テーブルの説明レコードがNULLであるため、エラーをスローする問題を修正します。
* **MDVA-20376** （*for Adobe Commerce >=2.3.2 &lt;2.3.4*） – 注文後にログインしたお客様の&#x200B;*で* No such entity with customerId = 1`exception.log` エラーが発生する問題を修正します。
* **MDVA-23764** （*for Adobe Commerce >=2.3.2 &lt;2.3.5*） – 動的ブロックの表示に影響する`JsFooterPlugin.php`のバグを修正します。
* **MDVA-13203** （*for Adobe Commerce >=2.3.0 &lt;2.4.2*） – 完全な再インデックスの後に&#x200B;*Integrity constrain violation search_tmp_ table* エラーが表示される問題を修正します。
* **MDVA-23426** （*for Adobe Commerce >=2.3.3 &lt;2.3.5*） - Adobe Commerceから送信された通知メールに空白の本文が含まれ、内容が添付ファイルとして追加される問題を修正します。
* **MDVA-22150** （*for Adobe Commerce >=2.3.1 &lt;2.3.4*） – カート内の設定可能な商品とクーポンが適用されているお客様が、管理画面でその設定可能な商品が無効になっている場合にログインできない問題を修正します。
* **MDVA-32545** （*for Adobe Commerce >=2.3.0 &lt;2.4.2*） – 管理者から注文を作成する際に請求書が自動的に送信されない問題を修正します。
* **MDVA-32714** （*for Adobe Commerce >=2.3.4 &lt;2.4.1*） - GraphQLの商品クエリでカスタマーグループの価格が機能しない問題を修正します。

## v1.0.12 {#v1-0-12}

* **MDVA-31399** （*for Adobe Commerce >=2.3.2 &lt;2.4.2*） - *小計（Incl）を追加します。 価格ルール条件に対する* オプション。
* **MDVA-31236** （*for Adobe Commerce >=2.4.0 &lt;2.4.2*） – カスタムリソースアクセスを持つ管理者が2FAを設定できない、またはログインできない問題を修正します。
* **MDVA-30845** （*Adobe Commerce >=2.3.5の場合&lt;2.3.7*） - UPS XML/USPS/DHLへの接続に失敗した場合に&#x200B;*申し訳ありません。この時点でこの注文に対する見積もりがありません* エラーが表示され、他の配送方法が利用できない問題を修正しました。
* **MDVA-32133** （*for Adobe Commerce >=2.4.0 &lt;2.4.1*） – ページビルダーからメディアギャラリーが読み込まれない問題を修正します。
* **MDVA-12304** （*for Adobe Commerce >=2.3.0*） - Cookieの最大数を50から200に増やします。
* **MDVA-32632** （*for Adobe Commerce >=2.3.2 &lt;2.3.5*） - Adobe Commerceではなく、決済システムで注文が表示される問題を修正します。
* **MDVA-32449** （*for Adobe Commerce >=2.3.0 &lt;2.3.6 || 2.4.0 |>=2.4.1 &lt;2.4.2 with B2B extension*） – 注文履歴の読み込みが非常に遅い、または読み込みが全くない問題を修正します。
* **MDVA-32739** （*for Adobe Commerce >=2.3.0 &lt;2.4.2*） – 非同期メール通知を有効にすると、古いセールスメールが送信される問題を修正します。

## v1.0.11 {#v1-0-11}

* **MC-38509** （*Adobe Commerce 2.3.6、2.4.1*&#x200B;の場合） - *新規顧客アカウントを作成* フォームで無効なデータを修正した後、*アカウントを作成* ボタンが無効のままになる問題を修正します。
* **MDVA-31006** （*Adobe Commerce 2.3.0、2.3.1*&#x200B;の場合） - [!DNL Paypal Express]支払いを使用して注文を行った後に重複した注文が表示される問題を修正します。
* **MDVA-25602** （*Adobe Commerce 2.3.0*&#x200B;の場合） - [!DNL PayPal Payflow Pro]の支払い方法に関する問題を修正し、Chrome 80 ブラウザーおよびAPI応答がお客様のログインページにリダイレクトされる際に、Cookieをデフォルトで`SameSite=Lax`として扱います。

## v1.0.10 {#v1-0-10}

パッチバージョンの軽微な修正

## v1.0.9 {#v1-0-9}

* **MDVA-31363** （*for Adobe Commerce >=2.3.2 &lt;2.4.2*） - *カート全体の固定金額割引* アクションを使用した場合に、クーポン付きカート価格ルールがGraphQL経由で適用されない問題を修正します。
* **MDVA-30889** （*for Adobe Commerce >=2.3.0 &lt;2.4.2*） – バンドルに対してバーチャルおよびシンプルな商品をオプションとして請求した後にエラーが発生する問題を修正します。
* **MDVA-31791** （*for Adobe Commerce >=2.3.4 &lt;2.3.5*） – ターゲットルールまたはリンクされた商品が使用される場合の商品ページのパフォーマンスを向上させます。
* **MDVA-31168** （*for Adobe Commerce >=2.3.0 &lt;2.4.2*） – 製品エクスポート CSV ファイルが表示されず、メモリ割り当てエラーが発生する問題を修正します。
* **MDVA-32313** （*for Adobe Commerce >=2.3.0 &lt;2.3.4*） – ウィッシュリストに設定可能な商品が誤った設定オプションで追加される可能性がある問題を修正します。
* **MDVA-31759** （*for Adobe Commerce >=2.3.0 &lt;2.4.2*） - CSV読み込み時に&#x200B;*dropdown*&#x200B;および&#x200B;*textarea*&#x200B;属性値で商品が更新されない問題を修正します。
* **MDVA-32012** （*for Adobe Commerce >=2.3.0 &lt;2.4.2*） – 韓国とアルゼンチンの郵便番号を検証できない問題を修正しました。
* **MDVA-31640** （*for Adobe Commerce >=2.3.1 &lt;2.3.6 || >=2.4.0 &lt;2.4.1*） - REST APIで特別価格を更新できない問題を修正しました。
* **MDVA-28651** （*for Adobe Commerce >=2.3.0 &lt;2.3.6 || >2.4.0 with B2B extension*） - REST APIを介して交渉可能な引用符を読み込む際にパフォーマンスの問題が発生する問題を修正します。

## v1.0.8 {#v1-0-8}

* **MDVA-31242** （*for Adobe Commerce >=2.3.0 &lt;2.4.1 with B2B extension*） – クレジットメモのグリッドに間違った通貨記号が表示される問題を修正します。
* **MDVA-31295** （*for Adobe Commerce >=2.3.0 &lt;2.4.2*） – 部分的な注文が完了し、アイテムに課税されたときに報酬ポイントが計算されない問題を修正します。
* **MDVA-30112** （*for Adobe Commerce >=2.3.4 &lt;2.4.2*） – 注文数が&#x200B;*bunch-size*&#x200B;の値を超えた場合、Adobe Commerceは&#x200B;*保留中*&#x200B;の状態の注文を不整合と見なす問題を修正します。
* **MDVA-31150** （*for Adobe Commerce >=2.3.0 &lt;2.4.2*） – 請求書がRest API呼び出しによって転記され、注文が店舗のクレジットカードおよびギフトカードのアカウントによって部分的に支払われた場合に、店舗のクレジットとギフトカードの残高がGET Invoice Rest API呼び出しによって返されない問題を修正しました。
* **MDVA-30963** （*for Adobe Commerce >=2.3.2 &lt;2.4.2*） – 製品フィルターの結果が、Adminの&#x200B;*すべてのストアビュー* スコープに指定された値のみを含むように設定され、ストアビューレベルで上書きされた値を含む製品が含まれる問題を修正します。
* **MDVA-29954** （*for Adobe Commerce >=2.3.0 &lt;2.3.6 || 2.4.0 || 2.4.2 with B2B extension*） - *新規会社登録リクエスト*&#x200B;と&#x200B;*会社にリンクされたときに誤ったアドレスからメールが送信される問題を修正します*。
* **MDVA-28357** （*for Adobe Commerce >=2.3.2 &lt;2.3.6 || >=2.4.0 &lt;2.4.1*） – 標準アナライザーをカスタムアナライザーに置き換え、[!DNL ElasticSearch] インデックスのSKU フィールドのキーワードトークンを使用して、ワイルドカード検索クエリをハイフン （&quot;-&quot;）を含むSKUで動作させます。

## v1.0.7 {#v1-0-7}

* **MDVA-30972** （*for Adobe Commerce >=2.3.0 &lt;2.4.2*） - WebApiを使用した部分的な出荷作成後にカスタム注文ステータスが&#x200B;*Processing*&#x200B;に変更された問題を修正します。
* **MDVA-30428** （*for Adobe Commerce >=2.3.4 &lt;2.3.5*） – この商品がカスタム在庫源に割り当てられている場合、お客様が商品をウィッシュリストに追加できない問題を修正します。
* **MDVA-30594** （*for Adobe Commerce >=2.3.0 &lt;2.4.2*） - FPTが設定されているチェックアウト時に複数のアドレスを持つ注文を保存できない問題を修正します。
* **MDVA-29148** （*for Adobe Commerce >=2.3.0 &lt;2.4.2*） - API呼び出しを使用して商品を作成する際に、ペイロードに値が指定されていない場合、`\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend` （Multiselectなど）型の商品カスタム属性がデフォルト値を使用しない問題を修正します。
* **MDVA-30837** （*for Adobe Commerce >=2.3.1 &lt;2.3.5*） – コンフィギュレーション設定が追加されました&#x200B;*送料無料のコンフィギュレーションで「税額を金額に含める：はい/いいえ*」。 *税額から金額への税額を含める*&#x200B;が&#x200B;*はい*&#x200B;に設定されている場合、最低注文金額は小計+税額として計算されます。 *税額を金額に含める*&#x200B;が&#x200B;*No*&#x200B;に設定されている場合、最低注文金額は小計として計算されます
* **MDVA-25028** （*for Adobe Commerce >=2.3.2 &lt;2.3.3 |>=2.3.5 &lt;2.3.6*） - [!DNL PayPal Payflow Pro]を使用して配置された注文が、不正フィルターがトリガーされたときに不正行為が疑われるステータスに設定されない問題を修正しました。
* **MDVA-31224** （*for Adobe Commerce >=2.3.3 &lt;2.3.5*） – バンドル製品の`catalog_product_price`再インデックス処理のパフォーマンスを向上させます。
* **MDVA-31321** （*for Adobe Commerce >=2.3.2 &lt;2.3.5*） - *すべて表示*&#x200B;が選択されている場合の空白ページ （エラー）を修正します。 [!DNL Elasticsearch]は、製品idの大きなリストを返します。 このシナリオでは、order by句が誤ったSQL形式に変換されます。
* **MDVA-30815** （*for Adobe Commerce >=2.3.2 &lt;2.3.4*） – 検索結果ページに表示する検索結果の数を変更すると、Adobe Commerceで空白ページが表示される問題を修正します。 ページごとに表示される検索結果の数を変更すると、[!DNL Elasticsearch]がカテゴリーページの結果を正しく表示するようになりました。
* **MDVA-30782** （*for Adobe Commerce >=2.3.5 &lt;2.4.2*） – カートルールに関係なく、ダイナミックブロックが表示される問題を修正します。
* **MDVA-31021** （*for Adobe Commerce >=2.3.0 &lt;2.4.2*） – パフォーマンスの問題が`module-catalog-import-export/Model/Import/Product/Option.php`に存在する問題を修正します。 `catalog_product_option` テーブルに最大100,000件を超えるレコードがある場合、単一の製品を含む新しいCSVの検証にかかる時間は10秒未満です。
* **MDVA-31007** （*for Adobe Commerce >=2.4.0 &lt;2.4.1*） – マイアカウントエリアおよびバックエンドの注文詳細ページに、カスタムのアドレス属性が正しく表示されない問題を修正します。
* **MDVA-29389** （*for Adobe Commerce >=2.3.0 &lt;2.4.2*） – アドバンスレポートの問題を修正します。アドバンスレポートでは、`analytics_collect_data` cronjobに次のように表示されます。*Portは、ホストパラメーター（localhost:3306など）*&#x200B;内で設定する必要があります。
* **MDVA-31343** （*for Adobe Commerce >=2.3.4 &lt;2.3.6*） – カテゴリがスケジュールされている場合の削除されたボディクラス `page-layout-category-full-width`の問題を修正します。
* **MDVA-30945** （*for Adobe Commerce >=2.3.0 &lt;2.4.2*） – カート `Call to a member function getValue() on null in module-configurable-product CartItemProcessor.php`の更新時に致命的なエラーメッセージが表示される問題を修正します。

## v1.0.6 {#v1-0-6}

* **MDVA-28993** （*for Adobe Commerce >=2.3.4 &lt;2.4.0*） - *最小値が*&#x200B;機能と一致し、[!DNL Elasticsearch] エンジンの一部を検索する必要があります。 検索クエリのハイフンに関する問題を解決します。
* **MDVA-30102** （*for Adobe Commerce >=2.3.2 &lt;=2.4.0*） – レイアウトキャッシュにTTLがないため、Redis キャッシュが急速に増加する問題を修正します。
* **MDVA-30599** （*for Adobe Commerce >=2.3.4 &lt;=2.4.0*） - APIを使用して作成されたゲスト引用符が、ログインした顧客の引用符として誤ってマークされる問題を修正します。
* **MDVA-29446** （*for Adobe Commerce >=2.3.3 &lt;=2.4.0*） – チェックアウト時に該当しない配送方法の価格がゼロとして表示される問題を修正します。
* **MDVA-30357** （*for Adobe Commerce >=2.3.2 &lt;=2.4.0*） - cronでサイトマップを生成する際に、間違った画像URLが作成される問題を修正します。
* **MDVA-30565** （*for Adobe Commerce >=2.3.2 &lt;=2.3.3-p1*） – ストアフロントチェックアウトで永続的なショッピングカートが有効になっている場合、*そのようなエンティティがcartid = 0* エラーでゲストのお客様に表示されない問題を修正します。
* **MDVA-29787** （*for Adobe Commerce >=2.3.0 &lt;=2.4.0*） - *が*&#x200B;条件の1つで表示される商品を定義する場合に、関連商品のターゲットルールが機能しない問題を修正します。
* **MDVA-30977** （*for Adobe Commerce >=2.3.4 &lt;=2.3.5-p2*） – 再インデックス後にカテゴリにランダムな商品が見つからない問題を修正します。
* **MDVA-28202** （*for Adobe Commerce >=2.3.4 &lt;=2.4.2*） - MSIを使用すると、レイヤーナビゲーションで設定可能な製品が正しくフィルタリングされない問題を修正します。
* **MDVA-28300** （*for Adobe Commerce >=2.3.0 &lt;2.3.6*） - GQL リクエストがカタログ価格ルールからの価格変更を反映しない問題を修正します。
* **MDVA-31006** （*for Adobe Commerce >=2.3.2 &lt;=2.4.2*） - [!DNL Paypal Express]支払いを使用して注文を行った後に重複した注文が表示される問題を修正します。

## v1.0.5 {#v1-0-5}

* **MDVA-30841** （*for Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*） - *が検索エンジンとして使用された場合、ブール型の商品属性の* No[!DNL Elasticsearch]値がレイヤーナビゲーションに含まれなかったレイヤーナビゲーションの問題を修正します。
* **MDVA-28191** （*for Adobe Commerce >=2.3.3 &lt;2.4.2*） – 管理画面での注文作成中に支払い方法が読み込まれない問題を修正します。
* **MDVA-29959** （*for Adobe Commerce >=2.3.0 &lt;=2.3.3-p1 with B2B extension*） - *会社*&#x200B;権限を持つ制限付き管理者ユーザーが会社アカウントを削除できない問題を修正します。
* **MDVA-30265** （*for Adobe Commerce >=2.3.3 &lt;2.4.2*） – 請求書の作成後に出荷追跡リンクが機能しなくなる問題を修正します。
* **MDVA-28409** （*for Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*） – データベース内の期限切れ引用符の数が多い場合に`sales_clean_quotes` cron ジョブが&#x200B;*メモリ不足* エラーで失敗する問題を修正します。
* **MDVA-30593** （*for Adobe Commerce >=2.3.0 &lt;2.3.4*） - Quote Lifetime設定に従って期限切れになった見積もりがクリーンアップされない問題を修正します。
* **MDVA-30107** （*for Adobe Commerce >=2.3.0 &lt;2.3.6*） – ストアビューに異なるベース URLが使用されている場合に、ストアスイッチャーが期待どおりに機能しない問題を修正します。
* **MDVA-28763** （*for Adobe Commerce >=2.3.2 &lt;2.3.4*） - REST APIを複数回使用して商品情報を更新した後、商品画像が重複する問題を修正します。
* **MDVA-30284** （*for Adobe Commerce >=2.3.0 &lt;2.4.2*） – 次の&#x200B;*[!DNL Elasticsearch]エラーによりカタログ検索インデクサーが失敗する問題を修正します。インデックスの合計フィールドの制限を超えています。*
* **MDVA-29042** （*for Adobe Commerce >=2.3.3 &lt;=2.3.4-p2 with B2B extension*） – カタログの権限が、新しい商品が共有カタログに追加された後、自動的に&#x200B;*Allow*&#x200B;に変更された問題を修正します。
* **MDVA-30428** （*for Adobe Commerce >=2.3.3 &lt;2.4.2*） – この商品がカスタム在庫源に割り当てられている場合、お客様が商品をウィッシュリストに追加できない問題を修正します。
* **MDVA-28661** （*for Adobe Commerce >=2.3.0 &lt;2.4.2 with B2B extension*） – 会社管理者が変更された後、会社ユーザー会社アカウントセクションでエラーがスローされる問題を修正します。

## v1.0.4 {#v1-0-4}

* **MDVA-30195** （*for Adobe Commerce 2.3.1 - 2.3.4-p2*） – データベース名が長すぎるとcron ジョブが失敗し、その結果、フロントエンドでカテゴリが更新されない問題を修正します。
* **MDVA-30106** （*Adobe Commerce ^2.3.0*&#x200B;の場合） – チェックアウト時の支払いが&#x200B;*で読み込まれない問題を修正します。JS コンソールでnull* エラーのプロパティ &#39;length&#39;を読み取れません。
* **MDVA-28656** （*for Adobe Commerce >=2.3.1 &lt;2.3.6 || >=2.4.0 &lt;2.4.2*） – 支払い情報なしで注文が行われ（例えば100%割引）、注文の請求書が作成された場合、注文ステータスが「完了」ではなく「&lt;ph=&#39;261&#39;/> クローズ済み&lt;ph=&#39;269&#39;/>」に変更される問題を修正しました。**
* **MDVA-30209** （*Adobe Commerce 2.3.0 ～ 2.3.3-p1*&#x200B;の場合） – お客様がアカウント情報を更新した場合に、お客様グループがデフォルトに変更された問題を修正します。
* **MDVA-30123** （*for Adobe Commerce >=2.3.4 &lt;2.4.2*） - GraphQL クエリで属性オプションラベルが正しく変換されない問題を修正します。
* **MDVA-29996** （*for Adobe Commerce >=2.3.3 &lt;2.4.2*） – カテゴリ権限を有効にした後、カテゴリーページがフルページキャッシュでキャッシュされない問題を修正します。
* **MDVA-30164** （*for Adobe Commerce >=2.3.1 &lt;2.4.2*） – カスタム顧客属性が存在する場合に、顧客レコードを顧客グリッドからエクスポートできない問題を修正します。
* **MDVA-30444** （*for Adobe Commerce >=2.3.0 &lt;2.4.1*） - GraphQLを使用した注文に対して確認メールが送信されない問題を修正します。
* **MDVA-30490** （*Adobe Commerce 2.3.4 - 2.3.5-p2*&#x200B;の場合） – いずれかの商品に空の短い説明がある場合に、商品の比較で500 エラーページがスローされる問題を修正します。
* **MDVA-30232** （*for Adobe Commerce >=2.3.1 &lt;2.4.1*） – 元の注文にギフトカードが含まれている場合に再注文できない問題を修正します。
* **MDVA-29965** （*for Adobe Commerce >=2.3.3 &lt;2.4.0*） – お客様が商品をカートに追加する際に「無効なフォームキー」エラーが表示される問題を修正します。
* **MDVA-30008** （*for Adobe Commerce >=2.3.0 &lt;2.4.2*） – パブリックカタログにある商品のAdmin APIを通じて注文できないB2Bの問題を修正します。
* **MDVA-22469** （*Adobe Commerce 2.3.2-p2 - 2.3.3-p1*&#x200B;の場合） - Adobe Commerce 2.3.3にアップグレードした後、ページビルダーが管理パネルで機能せず、一部のJSおよびCSS ファイルが読み込まれない問題を修正します。
* **MC-35984** （*for Adobe Commerce >=2.4.0 &lt;2.4.1*） – 返品用の配送ラベルを作成した後、返品ページ上の任意のページ要素を加盟店が操作できない問題を修正します（RMA）。

## v1.0.3 {#v1-0-3}

* **MDVA-25602** （*Adobe Commerce 2.3.0 - 2.3.4*&#x200B;の場合） - Chrome 80 ブラウザーおよびAPI応答がお客様のログインページにリダイレクトされる際の[!DNL PayPal Payflow Pro]の支払い方法とCookieをデフォルトで`SameSite=Lax`として扱う問題を修正します。
* **MDVA-26694** （*for Adobe Commerce >=2.3.0 &lt;2.3.6 || 2.4.0*） – 製品およびカタログのキャッシュが毎日期限切れになる問題を修正します。ただし、有効期限が異なる場合があります。
* **MDVA-27825** （*for Adobe Commerce >=2.3.0 &lt;2.4.1*） – メモリリークにより大量のデータの書き出しが失敗した問題を修正します。
* **MDVA-29085** （*for Adobe Commerce >=2.3.0 &lt;=2.3.5-p1*） - APIで会社が作成された場合に必要な新しい会社の電子メールが送信されないB2Bの問題を修正します。
* **MDVA-29344** （*for Adobe Commerce >=2.3.5 &lt;=2.4.0-p1*） – ヘッダーエレメントからテキストエレメントにテキストをコピーした後にページビルダーが停止する問題を修正します。
* **MDVA-29835** （*for Adobe Commerce >2.3.1 &lt;2.4.2*） – ギフトカードの注文に2つのコードが含まれている問題を修正しました。
* **MDVA-30052** （*for Adobe Commerce >=2.3.2-p2 &lt;2.3.5*） – プライベートコンテンツ（ローカルストレージ）が正しく入力されない問題を修正し、パフォーマンスの問題を解決します。
* **MDVA-30131** （*for Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*） - *が検索エンジンとして使用された場合、ブール型の商品属性の* No[!DNL Elasticsearch]値がレイヤーナビゲーションに含まれなかったレイヤーナビゲーションの問題を修正します。
* **MDVA-35514** （*for Adobe Commerce >=2.4.0 &lt;2.4.1*） – パッケージ作成モーダルウィンドウで配送ラベルを作成し、注文した商品をパッケージに追加する際の問題を修正します。
