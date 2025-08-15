---
title: 設定のベストプラクティス
description: これらのベストプラクティスを使用して、Adobe Commerce デプロイメントの応答時間を最適化します。
feature: Best Practices, Configuration
exl-id: 4cb0f5e7-49d5-4343-a8c7-b8e351170f91
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '1417'
ht-degree: 0%

---

# 設定のベストプラクティス

Commerceには、応答時間を改善し、スループットを向上させるために使用できる多くの設定やツールが用意されています。

## Cron ジョブ

[!DNL Commerce] での非同期操作はすべて、Linux の `cron` コマンドを使用して実行されます。 正しく設定するには、[cron の設定と実行 ](../configuration/cli/configure-cron-jobs.md) を参照してください。

## インデクサー

インデクサーは、**[!UICONTROL Update on Save]** モードまたは **[!UICONTROL Update on Schedule]** モードで実行できます。 **[!UICONTROL Update on Save]** モードは、カタログまたは他のデータが変更されるたびに、直ちにインデックスを作成します。 このモードでは、ストア内の更新操作とブラウジング操作が低強度であることを前提としています。 これにより、高負荷時に重大な遅延が発生し、データが使用できなくなる可能性があります。 パフォーマンスを上げる目的で **スケジュールに従って更新** を使用することをお勧めします。これは、データ更新に関する情報を保存し、特定の Cron ジョブを通じてバックグラウンドで一部でインデックスを実行するからです。 [!DNL Commerce]/**[!UICONTROL System]**/[!UICONTROL Tools] 設定ページで、各 **[!UICONTROL Index Management]** インデクサーのモードを個別に変更できます。 [!UICONTROL Customer Grid] インデックスは、常に **[!UICONTROL Update on Save]** モードに設定する必要があります。

>[!TIP]
>
>MariaDB 10.4 および 10.6 でのインデックス再作成は、他の MariaDB または [!DNL MySQL] バージョンに比べて時間がかかります。 デフォルトの MariaDB 設定を変更することをお勧めします。その方法については、[ インストールの前提条件 ](../installation/prerequisites/database/mysql.md) を参照してください。

## キャッシュ

実稼動環境でストアを起動する場合は、**[!UICONTROL System]** / [!UICONTROL Tools] / **[!UICONTROL Cache Management]** ページですべてのキャッシュをアクティベートします。 効率的な実稼働ページキャッシュソリューションなので、[!DNL Varnish] を使用することを強くお勧めします。

## 非同期メール通知

「非同期メール通知」設定を有効にすると、チェックアウトと注文処理のメール通知を処理するプロセスがバックグラウンドに移動します。 この機能を有効にするには、**[!UICONTROL Stores]/[!UICONTROL Settings]/[!UICONTROL Configuration]/[!UICONTROL Sales]/[!UICONTROL Sales Emails]/[!UICONTROL General Settings]/[!UICONTROL Asynchronous Sending]** に移動します。 詳しくは、『 [ 管理者ユーザーガイド ](https://experienceleague.adobe.com/en/docs/commerce-admin/config/sales/sales-emails) の _セールスメール_ を参照してください。

## 非同期順序データ処理

ストアフロントで集中的な販売が発生すると同時に、[!DNL Commerce] が集中的な注文処理を実行している場合があります。 データベースレベルでこれら 2 つのトラフィックパターンを区別するように [!DNL Commerce] を設定して、対応するテーブルの読み取り操作と書き込み操作の競合を回避できます。 順序データは非同期で保存およびインデックス作成できます。 注文は一時的なストレージに配置され、衝突することなくOrder Management グリッドに一括で移動されます。 このオプションは、**[!UICONTROL Stores]/[!UICONTROL Settings]/[!UICONTROL Configuration]/[!UICONTROL Advanced]/[!UICONTROL Developer]/[!UICONTROL Grid Settings]/[!UICONTROL Asynchronous indexing]** から有効にできます。 詳しくは、『 [ 管理者ユーザーガイド ](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/order-management/orders/order-scheduled-operations#enable-scheduled-grid-updates-and-reindexing) の _スケジュールされたグリッドの更新_ を参照してください。

>[!WARNING]
>
>「**[!UICONTROL Developer]**」タブとオプションは、[ 開発者モード ](../configuration/cli/set-mode.md) でのみ使用できます。 [ クラウドインフラストラクチャー上のAdobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/overview#cloud-req-test) は `Developer` モードをサポートしていません。

## 非同期設定の保存

多数のストアレベル設定を含むプロジェクトの場合、ストア設定の保存に法外な時間がかかったり、タイムアウトが発生したりする可能性があります。 _Async Config_ モジュールは、コンシューマーを使用してメッセージキュー内の保存を処理する cron ジョブを実行することで、非同期設定の保存を有効にします。 AsyncConfig は、デフォルトでは **無効** になっています。

コマンドラインインターフェイスを使用して AsyncConfig を有効にできます。

```bash
bin/magento setup:config:set --config-async 1
```

`set` コマンドは、`app/etc/env.php` ファイルに次の内容を書き込みます。

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

大量の売上高が発生する場 [!DNL Commerce]、注文に関連する在庫の更新を延期できます。 これにより、操作の数が最小限に抑えられ、注文配置プロセスが高速化されます。 ただし、このオプションはリスクが高く、店舗でバックオーダーが有効になっている場合にのみ使用できます。これは、このオプションによって在庫数がマイナスになる可能性があるためです。 このオプションにより、店舗のチェックアウトフローのパフォーマンスが大幅に向上し、必要に応じて簡単に在庫を補充できます。 サイトで延期された在庫更新を有効化するには、**[!UICONTROL Stores]/[!UICONTROL Settings]/[!UICONTROL Configuration]/[!UICONTROL Catalog]/[!UICONTROL Inventory]/[!UICONTROL Product Stock Options]/[!UICONTROL Use Deferred Stock Update]** に移動します。 詳しくは、&lbrace;2[Adobe Commerce ユーザーガイド ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-cloud) インベントリの管理 _を参照してください。_

>[!INFO]
>
>このオプションは、**[!UICONTROL Backorder with any mode]** がアクティブになっている場合にのみ使用できます。

>[!INFO]
>
>このオプションは、[Inventory management](high-throughput-order-processing.md#asynchronous-order-placement) と組み合わせて [ 非同期注文プレースメント ](https://experienceleague.adobe.com/docs/commerce-admin/inventory/guide-overview.html) でも機能します。

## クライアントサイドの最適化設定

[!DNL Commerce] インスタンスのストアフロントの応答性を改善するには、デフォルトまたは開発者モードで管理者に移動して、次の設定を変更します。

**[!UICONTROL Stores]-> [!UICONTROL Configuration] -> [!UICONTROL Advanced] -> [!UICONTROL Developer]:**

| 設定グループ | 設定 | 値 |
| ------------------- | -------------------------- | ------ |
| グリッド設定 | 非同期インデックス作成 | Enable （有効） |
| CSS 設定 | CSS ファイルの縮小 | はい |
| [!DNL JavaScript] Settings | [!DNL JavaScript] ファイルの縮小 | はい |
| [!DNL JavaScript] Settings | [!DNL JavaScript] バンドルの有効化 | はい |
| テンプレート設定 | HTMLの縮小 | はい |

>[!INFO]
>
>「**[!UICONTROL Developer]**」タブとオプションは、[ 開発者モード ](../configuration/cli/set-mode.md) でのみ使用できます。 [Adobe [!DNL Commerce]  クラウドインフラストラクチャー ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/overview#cloud-req-test) は `Developer` モードをサポートしていません。

「**[!UICONTROL Enable [!DNL JavaScript] Bundling]**」オプションを有効にすると、Commerceで、すべての JS リソースを、ストアフロントページに読み込まれる 1 つまたは一連のバンドルに結合できます。 JS をバンドルすると、サーバーへのリクエストが少なくなり、ページのパフォーマンスが向上します。 また、ブラウザーが最初の呼び出し時に JS リソースをキャッシュし、それ以降のすべてのブラウジングで再利用するのに役立ちます。 このオプションでも、すべての JS がテキストとして読み込まれるので、遅延評価が行われます。 ページで特定のアクションがトリガーされた後にのみ、コードの分析と評価が開始されます。 ただし、すべての JS コンテンツが最初の呼び出しで読み込まれるので、最初のページの読み込み時間が非常に重要なストアには、この設定はお勧めしません。

>[!INFO]
>
>CSS と JavaScript の最適化について詳しくは、Adobe Commerce ヘルプセンターの [ クラウドインフラストラクチャとAdobe Commerce上のAdobe Commerceにおける CSS と JavaScript ファイルの最適化 ](https://support.magento.com/hc/en-us/articles/360044482152) を参照してください。

### バンドルのヒント

* 縮小とバンドルには、サードパーティのツール（[r.js](https://requirejs.org/) など）を使用することをお勧めします。 組み込みメカニズム [!DNL Commerce] 最適ではなく、フォールバックの代替手段として出荷されます。
* JS のバンドルを使用する代わりに HTTP/2 プロトコルをアクティブ化することもできます。 このプロトコルは、多くの同じ利点を提供します。 これは、クラウドインフラストラクチャプロジェクトのAdobe Commerceでは、デフォルトで有効になっています。
* JS ファイルと CSS ファイルの結合など、非推奨の設定は使用しないことをお勧めします。これらの設定は、ページのHEAD セクションで同期的に読み込まれる JS 用にのみ設計されているからです。 この手法を使用すると、バンドルが発生し、requireJS ロジックが正しく機能しない可能性があります。

## 顧客セグメントの検証

多数の [ 顧客セグメント ](https://experienceleague.adobe.com/en/docs/commerce-admin/customers/segments/customer-segments) を持つマーチャントの場合、顧客ログインや買い物かごへの製品の追加など、顧客のアクションによってパフォーマンスが大幅に低下する可能性があります。

顧客処理トリガー顧客セグメントの検証プロセス。これにより、パフォーマンスが低下する可能性があります。 デフォルトでは、Adobe Commerceは各セグメントをリアルタイムで検証し、一致する顧客セグメントと一致しない顧客セグメントを定義します。

パフォーマンスの低下を避けるために、**[!UICONTROL Real-time Check if Customer is Matched by Segment]** システム設定オプションを **いいえ** に設定して、単一の組み合わせ条件 SQL クエリで顧客セグメントを検証できます。

この最適化を有効にするには、**[!UICONTROL Stores]/[!UICONTROL Settings]/[!UICONTROL Configuration]/[!UICONTROL Customers]/[!UICONTROL Customer Configuration]/[!UICONTROL Customer Segments]/[!UICONTROL Real-time Check if Customer is Matched by Segment]** に移動します。

この設定により、システム内に多数の顧客セグメントがある場合の顧客セグメント検証のパフォーマンスが向上します。 ただし、[ 分割データベース ](../configuration/storage/multi-master.md) 実装では動作しません。また、登録済みの顧客がない場合でも動作しません。

## データベースのメンテナンススケジュール {#database}

ステージングインスタンスと実稼動インスタンスには、定期的なデータベースバックアップを実行することをお勧めします。 バックアップ操作の I/O 集約性により、バックアップの遅延や潜在的な問題が発生する場合があります。 複数の環境に対してデータベースプロセスを同時に実行すると、使用可能なリソースの競合が原因で、実行速度が低下する可能性があります。

パフォーマンスを向上させるには、バックアップを一度に 1 つずつ、ピーク以外の時間に連続して実行するようにスケジュールします。 この方法では、I/O 競合が回避され、特に小規模なインスタンスや大規模なデータベースの場合に完了までの時間が短縮されます。

例えば、ストアへの訪問回数が少ない場合は、実稼動データベースのバックアップをスケジュールし、その後にステージングデータベースをバックアップすることをお勧めします。

## グリッド内の製品数を制限

大規模なカタログの製品グリッドのパフォーマンスを向上させるには、**[!UICONTROL Stores]/[!UICONTROL Settings]/[!UICONTROL Configuration]/[!UICONTROL Advanced]/[!UICONTROL Admin]/[!UICONTROL Admin Grids]/[!UICONTROL Limit Number of Products in Grid]** システム設定設定を使用して、グリッド内の製品数を制限することをお勧めします。

このシステム設定は、デフォルトでは無効になっています。 有効にすると、グリッド内の製品数を特定の値に制限できます。 **[!UICONTROL Records Limit]** は、カスタマイズ可能な設定で、デフォルトの最小値は `20000` です。
**[!UICONTROL Limit Number of Products in Grid]** 設定が有効で、グリッド内の製品数がレコード制限を超えている場合、限られたレコードのコレクションが返されます。 制限に達すると、検出された合計レコード数、選択したレコード数、ページネーション要素がグリッドヘッダーに表示されなくなります。

グリッド内の製品の総数が制限されている場合、製品グリッドのマスアクションには影響しません。 製品グリッドのプレゼンテーションレイヤーにのみ影響します。 例えば、グリッド内の `20000` 製品の数が制限されている場合、ユーザーが **[!UICONTROL Select All]** をクリックし、**[!UICONTROL Update attributes]** の一括アクションを選択して、一部の属性を更新します。 その結果、`20000` しいレコードの限られたコレクションではなく、すべての製品が更新されます。

製品グリッドの制限は、UI コンポーネントで使用される製品コレクションにのみ影響します。 その結果、すべての商品グリッドがこの制限の影響を受けるわけではありません。 `Magento\Catalog\Ui\DataProvider\Product\ProductCollection` を使用している場合のみ。
製品グリッドのコレクションは、次のページでのみ制限できます。

* カタログ製品グリッド
* 関連/アップセル/クロスセル製品グリッドの追加
* バンドル製品への製品の追加
* 製品をグループ製品に追加
* 管理者による注文の作成ページ

製品グリッドを制限しない場合は、結果コレクションの項目を **[!UICONTROL Records Limit]** よりも少なくするために、より正確にフィルターを使用することをお勧めします。
