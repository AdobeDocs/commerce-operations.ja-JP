---
title: 設定のベストプラクティス
description: これらのベストプラクティスを使用して、Adobe CommerceまたはMagento Open Sourceのデプロイメントの応答時間を最適化します。
feature: Best Practices, Configuration
exl-id: 4cb0f5e7-49d5-4343-a8c7-b8e351170f91
source-git-commit: 602a1ef82fcb8d30ff027db0fe0aacb981c7e08e
workflow-type: tm+mt
source-wordcount: '1425'
ht-degree: 0%

---

# 設定のベストプラクティス

コマースには、ページでの応答時間を改善し、スループットを高めるために使用できる多くの設定とツールが用意されています。

## Cron ジョブ

におけるすべての非同期操作 [!DNL Commerce] Linux で実行される `cron` コマンド。 参照： [Cron の設定と実行](../configuration/cli/configure-cron-jobs.md) を正しく設定してください。

## インデクサー

インデクサーはどちらでも実行できます **[!UICONTROL Update on Save]** または **[!UICONTROL Update on Schedule]** モード。 この **[!UICONTROL Update on Save]** モードでは、カタログや他のデータが変更されるたびに直ちにインデックスが作成されます。 このモードでは、ストア内の更新操作とブラウジング操作が低強度であることを前提としています。 これにより、高負荷時に重大な遅延が発生し、データが使用できなくなる可能性があります。 を使用することをお勧めします。 **スケジュールに従って更新** パフォーマンス上の理由から、にはデータ更新に関する情報が格納され、特定の cron ジョブを通じてバックグラウンドで部分的にインデックス化が実行されます。 それぞれのモードは変更できます [!DNL Commerce] 個別ののインデクサー  **[!UICONTROL System]** > [!UICONTROL Tools] > **[!UICONTROL Index Management]** 設定ページ。 この [!UICONTROL Customer Grid] インデックスは、常にに設定する必要があります **[!UICONTROL Update on Save]** モード。

>[!TIP]
>
>MariaDB 10.4 および 10.6 でのインデックス再作成は、他の MariaDB または [!DNL MySQL] バージョン。 デフォルトの MariaDB 設定を変更することをお勧めします。その方法については、で説明されています。 [インストールの前提条件](../installation/prerequisites/database/mysql.md).

## キャッシュ

実稼動環境でストアを起動する場合は、以下からすべてのキャッシュをアクティベートします。 **[!UICONTROL System]** > [!UICONTROL Tools] > **[!UICONTROL Cache Management]** ページ。 を使用することを強くお勧めします。 [!DNL Varnish]これは効率的な実稼動ページキャッシュソリューションなので、

## 非同期メール通知

「非同期メール通知」設定を有効にすると、チェックアウトと注文処理のメール通知を処理するプロセスがバックグラウンドに移動します。 この機能を有効にするには、に移動してください。 **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Sales] > [!UICONTROL Sales Emails] > [!UICONTROL General Settings] >[!UICONTROL Asynchronous Sending]**. 参照： [販売メール](https://docs.magento.com/user-guide/configuration/sales/sales-emails.html) が含まれる _Magento Open Sourceユーザーガイド_ を参照してください。

## 非同期順序データ処理

店頭での集中的な販売が同時に発生する場合があります [!DNL Commerce] は集中的な注文処理を実行しています。 以下を設定できます [!DNL Commerce] 対応するテーブルの読み取り操作と書き込み操作の競合を避けるために、データベースレベルでこれらの 2 つのトラフィックパターンを区別します。 順序データは非同期で保存およびインデックス作成できます。 注文は一時的なストレージに配置され、衝突することなく注文管理グリッドに一括で移動されます。 このオプションは、 **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Advanced] > [!UICONTROL Developer] > [!UICONTROL Grid Settings] >[!UICONTROL Asynchronous indexing]**. 参照： [スケジュールされたグリッドの更新](https://docs.magento.com/user-guide/sales/order-grid-updates-schedule.html) が含まれる _Magento Open Sourceユーザーガイド_ を参照してください。

>[!WARNING]
>
>この **[!UICONTROL Developer]** タブとオプションは、でのみ使用できます。 [開発者モード](../configuration/cli/set-mode.md). [クラウドインフラストラクチャー上のAdobe Commerce](https://devdocs.magento.com/cloud/requirements/cloud-requirements.html#cloud-req-test) はサポートしていません `Developer` モード。

## 非同期設定の保存

多数のストアレベル設定を含むプロジェクトの場合、ストア設定の保存に法外な時間がかかったり、タイムアウトが発生したりする可能性があります。 この _非同期設定_ モジュールは、コンシューマーを使用してメッセージキュー内の保存を処理する cron ジョブを実行することで、非同期設定の保存を有効にします。 AsyncConfig は **disabled** デフォルトでは。

コマンドラインインターフェイスを使用して AsyncConfig を有効にできます。

```bash
bin/magento setup:config:set --config-async 1
```

この `set` コマンドは、次の内容を `app/etc/env.php` ファイル：

```conf
...
   'config' => [
       'async' => 1
   ]
```

次のコンシューマーを開始して、キュー内のメッセージの処理を先入れ先出し方式で開始します。

```bash
bin/magento queue:consumers:start saveConfigProcessor --max-messages=1
```

## 延期された在庫更新

売上が集中する状況では、 [!DNL Commerce] 注文に関連する在庫の更新を延期できます。 これにより、操作の数が最小限に抑えられ、注文配置プロセスが高速化されます。 ただし、このオプションはリスクが高く、店舗でバックオーダーが有効になっている場合にのみ使用できます。これは、このオプションによって在庫数がマイナスになる可能性があるためです。 このオプションにより、店舗のチェックアウトフローのパフォーマンスが大幅に向上し、必要に応じて簡単に在庫を補充できます。 サイトで延期された在庫の更新を有効にするには、次に移動します： **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Catalog] > [!UICONTROL Inventory] > [!UICONTROL Product Stock Options] >[!UICONTROL Use Deferred Stock Update]**. 参照： [在庫の管理](https://docs.magento.com/user-guide/catalog/inventory.html) が含まれる _Adobe Commerce ユーザーガイド_ を参照してください。

>[!INFO]
>
>このオプションは、次の場合にのみ使用できます **[!UICONTROL Backorder with any mode]** がアクティブ化されました。

>[!INFO]
>
>このオプションはでも機能します [非同期注文の配置](high-throughput-order-processing.md#asynchronous-order-placement) ～と組み合わせて [Inventory management](https://experienceleague.adobe.com/docs/commerce-admin/inventory/guide-overview.html).

## クライアントサイドの最適化設定

のストアフロントの応答性を向上させるには [!DNL Commerce] インスタンスで、デフォルトまたは開発者モードの管理者に移動し、次の設定を変更します。

**[!UICONTROL Stores]-> [!UICONTROL Configuration] -> [!UICONTROL Advanced] -> [!UICONTROL Developer]:**

| 設定グループ | 設定 | 値 |
| ------------------- | -------------------------- | ------ |
| グリッド設定 | 非同期インデックス作成 | Enable （有効） |
| CSS 設定 | CSS ファイルの縮小 | はい |
| [!DNL JavaScript] 設定 | 縮小 [!DNL JavaScript] ファイル | はい |
| [!DNL JavaScript] 設定 | Enable （有効） [!DNL JavaScript] バンドル | はい |
| テンプレート設定 | HTMLの縮小 | はい |

>[!INFO]
>
>この **[!UICONTROL Developer]** タブとオプションは、でのみ使用できます。 [開発者モード](../configuration/cli/set-mode.md). [Adobe [!DNL Commerce] クラウドインフラストラクチャー上](https://devdocs.magento.com/cloud/requirements/cloud-requirements.html#cloud-req-test) はサポートしていません `Developer` モード。

をアクティブ化したとき **[!UICONTROL Enable [!DNL JavaScript] Bundling]** オプションを使用すると、Commerce は、ストアフロントページに読み込まれる 1 つまたは一連のバンドルにすべての JS リソースを結合できます。 JS をバンドルすると、サーバーへのリクエストが少なくなり、ページのパフォーマンスが向上します。 また、ブラウザーが最初の呼び出し時に JS リソースをキャッシュし、それ以降のすべてのブラウジングで再利用するのに役立ちます。 このオプションでも、すべての JS がテキストとして読み込まれるので、遅延評価が行われます。 ページで特定のアクションがトリガーされた後にのみ、コードの分析と評価が開始されます。 ただし、すべての JS コンテンツが最初の呼び出しで読み込まれるので、最初のページの読み込み時間が非常に重要なストアには、この設定はお勧めしません。

>[!INFO]
>
>参照： [クラウドインフラストラクチャー上のAdobe CommerceおよびAdobe Commerceでの CSS と JavaScript ファイルの最適化](https://support.magento.com/hc/en-us/articles/360044482152) css と JavaScript の最適化について詳しくは、Adobe Commerce ヘルプセンター_を参照してください。

### バンドルのヒント

* 縮小とバンドルには、サードパーティのツールを使用することをお勧めします [r.js](https://requirejs.org/)）に設定します。 [!DNL Commerce] 組み込みのメカニズムは最適ではなく、フォールバックの代替手段として出荷されます。
* JS のバンドルを使用する代わりに HTTP/2 プロトコルをアクティブ化することもできます。 このプロトコルは、多くの同じ利点を提供します。 これは、クラウドインフラストラクチャプロジェクトのAdobe Commerceでは、デフォルトで有効になっています。
* JS ファイルと CSS ファイルの結合など、非推奨の設定は使用しないことをお勧めします。これらの設定は、ページのHEADセクションで同期的に読み込まれる JS 用にのみ設計されているからです。 この手法を使用すると、バンドルが発生し、requireJS ロジックが正しく機能しない可能性があります。

## 顧客セグメントの検証

多数の [顧客セグメント](https://docs.magento.com/user-guide/marketing/customer-segments.html) 顧客のログインや買い物かごへの製品の追加など、顧客のアクションにより、パフォーマンスが大幅に低下する場合があります。

顧客処理トリガー顧客セグメントの検証プロセス。これにより、パフォーマンスが低下する可能性があります。 デフォルトでは、Adobe Commerceは各セグメントをリアルタイムで検証し、一致する顧客セグメントと一致しない顧客セグメントを定義します。

パフォーマンスの低下を防ぐには、 **[!UICONTROL Real-time Check if Customer is Matched by Segment]** へのシステム設定オプション **不可** 単一の組み合わせ条件 SQL クエリで顧客セグメントを検証する。

この最適化を有効にするには、次に移動してください： **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Customers] > [!UICONTROL Customer Configuration] > [!UICONTROL Customer Segments] >[!UICONTROL Real-time Check if Customer is Matched by Segment]**.

この設定により、システム内に多数の顧客セグメントがある場合の顧客セグメント検証のパフォーマンスが向上します。 ただし、では動作しません [データベースの分割](../configuration/storage/multi-master.md) 実装する場合、または登録ユーザーがいない場合。

## データベースのメンテナンススケジュール {#database}

ステージングインスタンスと実稼動インスタンスには、定期的なデータベースバックアップを実行することをお勧めします。 バックアップ操作の I/O 集約性により、バックアップの遅延や潜在的な問題が発生する場合があります。 複数の環境に対してデータベースプロセスを同時に実行すると、使用可能なリソースの競合が原因で、実行速度が低下する可能性があります。

パフォーマンスを向上させるには、バックアップを一度に 1 つずつ、ピーク以外の時間に連続して実行するようにスケジュールします。 この方法では、I/O 競合が回避され、特に小規模なインスタンスや大規模なデータベースの場合に完了までの時間が短縮されます。

例えば、ストアへの訪問回数が少ない場合は、実稼動データベースのバックアップをスケジュールし、その後にステージングデータベースをバックアップすることをお勧めします。

## グリッド内の製品数を制限

大規模なカタログの製品グリッドのパフォーマンスを向上させるには、グリッド内の製品数を **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Advanced] > [!UICONTROL Admin] > [!UICONTROL Admin Grids] >[!UICONTROL Limit Number of Products in Grid]** システム設定。

このシステム設定は、デフォルトでは無効になっています。 有効にすると、グリッド内の製品数を特定の値に制限できます。 **[!UICONTROL Records Limit]** は、カスタマイズ可能な設定で、デフォルトの最小値はです。 `20000`.
いつ **[!UICONTROL Limit Number of Products in Grid]** 設定が有効になっており、グリッド内の製品数がレコード制限を超えている場合、限られたレコードのコレクションが返されます。 制限に達すると、検出された合計レコード数、選択したレコード数、ページネーション要素がグリッドヘッダーに表示されなくなります。

グリッド内の製品の総数が制限されている場合、製品グリッドのマスアクションには影響しません。 製品グリッドのプレゼンテーションレイヤーにのみ影響します。 例えば、次の数には制限があります。 `20000` 製品グリッドで、ユーザーがクリックする **[!UICONTROL Select All]**、を選択します **[!UICONTROL Update attributes]** 一括アクションを実行し、一部の属性を更新します。 その結果、の限定されたコレクションではなく、すべての製品が更新されます `20000` レコード。

製品グリッドの制限は、UI コンポーネントで使用される製品コレクションにのみ影響します。 その結果、すべての商品グリッドがこの制限の影響を受けるわけではありません。 を使用している場合のみ `Magento\Catalog\Ui\DataProvider\Product\ProductCollection`.
製品グリッドのコレクションは、次のページでのみ制限できます。

* カタログ製品グリッド
* 関連/アップセル/クロスセル製品グリッドの追加
* バンドル製品への製品の追加
* 製品をグループ製品に追加
* 管理者による注文の作成ページ

製品グリッドを制限しない場合は、結果コレクションで使用する項目を次よりも少なくするために、フィルターをより正確に使用することをお勧めします **[!UICONTROL Records Limit]**.
