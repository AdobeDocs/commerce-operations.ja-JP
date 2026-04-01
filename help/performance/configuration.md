---
title: 設定のベストプラクティス
description: Adobe Commerceのパフォーマンスを最適化するための設定のベストプラクティスについて説明します。 レスポンス時間とスループットを向上させる設定とツールを確認します。
feature: Best Practices, Configuration
exl-id: 4cb0f5e7-49d5-4343-a8c7-b8e351170f91
source-git-commit: 0185c3d88a370c6932198eb4c44ec6dbfa0a6cf0
workflow-type: tm+mt
source-wordcount: '1402'
ht-degree: 0%

---

# 設定のベストプラクティス

Commerceには、ページの応答時間を向上させるだけでなく、スループットを向上させるために使用できる多くの設定とツールが用意されています。

## Cron Jobs

Commerceのすべての非同期処理は、Linux `cron` コマンドを使用して実行されます。 [cron](../configuration/cli/configure-cron-jobs.md)の設定と実行を参照して、正しく設定してください。

## インデクサー

インデクサーは、**[!UICONTROL Update on Save]**&#x200B;または&#x200B;**[!UICONTROL Update on Schedule]** モードで実行できます。 **[!UICONTROL Update on Save]** モードでは、カタログまたはその他のデータが変更されるたびに、すぐにインデックスが作成されます。 このモードでは、ストアでの更新と閲覧の操作の強度が低いことを前提としています。 これにより、高負荷時に大幅な遅延やデータの利用不能が発生する可能性があります。 パフォーマンスの目的で&#x200B;**スケジュールの更新**&#x200B;を使用することをお勧めします。これは、データ更新に関する情報を保存し、特定のcron ジョブを通じてバックグラウンドの部分でインデックス作成を実行するためです。 各[!DNL Commerce] インデクサーのモードは、**[!UICONTROL System]** > [!UICONTROL Tools] > **[!UICONTROL Index Management]**&#x200B;設定ページで個別に変更できます。 [!UICONTROL Customer Grid] インデックスは常に&#x200B;**[!UICONTROL Update on Save]** モードに設定する必要があります。

>[!TIP]
>
>MariaDB 10.4および10.6でのインデックス再作成は、他のMariaDBまたは[!DNL MySQL] バージョンと比較してより多くの時間がかかります。 デフォルトのMariaDB設定を変更することをお勧めします。これは、[&#x200B; インストールの前提条件](../installation/prerequisites/database/mysql.md)に記載されています。

## キャッシュ

実稼動環境でストアを起動する場合、**[!UICONTROL System]** > [!UICONTROL Tools] > **[!UICONTROL Cache Management]** ページのすべてのキャッシュをアクティブ化します。 効率的な実稼動ページキャッシュソリューションであるため、[!DNL Varnish]を使用することを強くお勧めします。

## 非同期メール通知

**[!UICONTROL Asynchronous email notifications]**&#x200B;設定を有効にすると、チェックアウトと注文処理のメール通知を処理するプロセスがバックグラウンドに移動します。 この機能を有効にするには、**[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Sales] > [!UICONTROL Sales Emails] > [!UICONTROL General Settings] >[!UICONTROL Asynchronous Sending]**&#x200B;に移動します。 詳しくは、[管理者ユーザーガイド &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-admin/config/sales/sales-emails)の&#x200B;_セールスメール_&#x200B;を参照してください。

## 非同期注文データ処理

Commerceでの集中的な注文処理と同時に、ストアフロントでの集中的な販売が発生することもあります。 対応するテーブルで読み取り操作と書き込み操作の競合を避けるために、Commerceを構成して、データベースレベルでこれらの2つのトラフィックパターンを区別できます。 注文データを非同期で保存し、インデックスを作成できます。 注文は一時的な保管として保管され、衝突することなくOrder Managementのグリッドに一括で移動されます。 このオプションは、**[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Advanced] > [!UICONTROL Developer] > [!UICONTROL Grid Settings] >[!UICONTROL Asynchronous indexing]**&#x200B;から有効にできます。 詳しくは、管理者ユーザーガイドの「[&#x200B; スケジュールされたグリッドの更新](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/order-management/orders/order-scheduled-operations#enable-scheduled-grid-updates-and-reindexing)」を参照してください。

>[!WARNING]
>
>**[!UICONTROL Developer]** タブとオプションは、[開発者モード &#x200B;](../configuration/cli/set-mode.md)でのみ使用できます。 [&#x200B; クラウドインフラストラクチャ &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/overview#cloud-req-test)上のAdobe Commerceは`Developer` モードをサポートしていません。

## 非同期設定の保存

多数のストアレベル設定を持つプロジェクトの場合、ストア設定の保存には膨大な時間がかかったり、タイムアウトが発生したりする可能性があります。 _非同期設定_ モジュールは、消費者を使用してメッセージキュー内の保存を処理するcron ジョブを実行することで、非同期設定の保存を有効にします。 AsyncConfigはデフォルトで&#x200B;*無効*&#x200B;です。

コマンドラインインターフェイスを使用してAsyncConfigを有効にできます。

```bash
bin/magento setup:config:set --config-async 1
```

`set` コマンドは、次の内容を`app/etc/env.php` ファイルに書き込みます。

```conf
...
   'config' => [
       'async' => 1
   ]
```

次のコンシューマーを開始して、キュー内のメッセージの処理を先入れ先出しで開始します。

```bash
bin/magento queue:consumers:start saveConfigProcessor --max-messages=1
```

## 繰延在庫更新

集中的なセールスが発生した場合、Commerceでは、注文に関連する在庫更新を延期することができます。 これにより、操作数を最小限に抑え、注文配置プロセスを高速化できます。 ただし、このオプションはリスクが高く、ストアでバックオーダーがアクティブ化された場合にのみ使用できます。このオプションは、在庫量がマイナスになる可能性があるためです。 このオプションにより、チェックアウトフローを大幅に改善し、オンデマンドで容易に在庫を補充できる店舗を実現できます。 サイトで延期された在庫更新を有効にするには、**[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Catalog] > [!UICONTROL Inventory] > [!UICONTROL Product Stock Options] >[!UICONTROL Use Deferred Stock Update]**&#x200B;に移動します。 詳しくは、[Adobe Commerce ユーザーガイド &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-cloud)の&#x200B;_在庫管理_&#x200B;を参照してください。

>[!INFO]
>
>このオプションは、**[!UICONTROL Backorder with any mode]**&#x200B;がアクティブ化されている場合にのみ使用できます。

>[!INFO]
>
>このオプションは、[Inventory management](high-throughput-order-processing.md#asynchronous-order-placement)と組み合わせて[非同期注文処理](https://experienceleague.adobe.com/docs/commerce-admin/inventory/guide-overview.html)でも使用できます。

## クライアントサイド最適化設定

[!DNL Commerce] インスタンスのストアフロントの応答性を向上させるには、デフォルトモードまたは開発者モードで管理者に移動し、次の設定を変更します。

**[!UICONTROL Stores]-> [!UICONTROL Configuration] -> [!UICONTROL Advanced] -> [!UICONTROL Developer]:**

| 設定グループ | 設定 | 値 |
| ------------------- | -------------------------- | ------ |
| グリッド設定 | 非同期インデックス作成 | 有効にする |
| CSS設定 | CSS ファイルを縮小 | はい |
| [!DNL JavaScript]設定 | [!DNL JavaScript] ファイルを縮小 | はい |
| [!DNL JavaScript]設定 | [!DNL JavaScript] バンドルを有効にする | はい |
| テンプレート設定 | HTMLを縮小 | はい |

>[!INFO]
>
>**[!UICONTROL Developer]** タブとオプションは、[開発者モード &#x200B;](../configuration/cli/set-mode.md)でのみ使用できます。 [&#x200B; クラウドインフラストラクチャ &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/overview#cloud-req-test)上のAdobe Commerceは`Developer` モードをサポートしていません。

**[!UICONTROL Enable [!DNL JavaScript] Bundling]** オプションを有効にすると、CommerceがすべてのJS リソースを1つまたはストアフロントページに読み込まれる一連のバンドルに統合できるようになります。 JSをバンドルすると、サーバーへのリクエストが少なくなり、ページのパフォーマンスが向上します。 また、ブラウザが最初の呼び出しでJS リソースをキャッシュし、それ以降のすべてのブラウジングに再利用するのに役立ちます。 このオプションでは、すべてのJSがテキストとして読み込まれるため、遅延評価も行われます。 特定のアクションがページ上でトリガーされた後にのみ、コードの分析と評価が開始されます。 ただし、すべてのJS コンテンツが最初の呼び出しに読み込まれるため、最初のページ読み込み時間が非常に重要なストアでは、この設定はお勧めしません。

>[!INFO]
>
>CSSとJavascriptの最適化について詳しくは、[&#x200B; リソースファイルの最適化](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/optimize-css-js-files)を参照してください。

### バンドルのヒント {#bundling-tips}

* 縮小とバンドルには、サードパーティ製ツール（[r.js](https://requirejs.org/)など）を使用することをお勧めします。 Commerceの組み込みメカニズムは最適ではなく、代替として提供されます。
* HTTP/2 プロトコルをアクティブ化することは、JS バンドルを使用する代わりに良い方法です。 プロトコルは、同じ利点の多くを提供します。 クラウドインフラストラクチャプロジェクトのAdobe Commerceでは、デフォルトで有効になっています。
* JSやCSS ファイルの結合など、非推奨の設定を使用することはお勧めしません。これらの設定は、ページのHEAD セクションで同期ロードされたJSにのみ設計されています。 この手法を使用すると、バンドルが発生し、JS ロジックが正しく動作しない可能性があります。

## 顧客セグメントの検証

多数の[顧客セグメント &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-admin/customers/segments/customer-segments)を持つマーチャントは、顧客ログインや製品のカートへの追加など、顧客の行動に伴ってパフォーマンスが大幅に低下する可能性があります。

顧客の行動は、顧客セグメントの検証プロセスをトリガー化します。これにより、パフォーマンスが低下する可能性があります。 デフォルトでは、Adobe Commerceは各セグメントをリアルタイムで検証し、一致する顧客セグメントとそうでない顧客セグメントを定義します。

パフォーマンスの低下を回避するには、**[!UICONTROL Real-time Check if Customer is Matched by Segment]** システム構成オプションを&#x200B;*No*&#x200B;に設定して、単一の複合条件SQL クエリで顧客セグメントを検証します。

この最適化を有効にするには、**[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Customers] > [!UICONTROL Customer Configuration] > [!UICONTROL Customer Segments] >[!UICONTROL Real-time Check if Customer is Matched by Segment]**&#x200B;に移動します。

この設定は、システム内に顧客セグメントが多い場合に、顧客セグメント検証のパフォーマンスを向上させます。 ただし、[分割データベース &#x200B;](../configuration/storage/multi-master.md)実装では機能しません。また、登録された顧客がいない場合も機能しません。

## データベースのメンテナンススケジュール {#database}

ステージングおよび実稼動インスタンスのデータベースバックアップを定期的に実行することをお勧めします。 I/Oを大量に使用するバックアップ操作のため、バックアップが遅くなり、潜在的な問題が発生する可能性があります。 複数の環境で同時にデータベースプロセスを実行すると、使用可能なリソースの競合が原因で実行が遅くなる場合があります。

パフォーマンスを向上させるには、バックアップを1回ずつ、オフピーク時に連続して実行するようにスケジュールします。 この方法は、I/O競合を回避し、特に小規模なインスタンスや大規模なデータベースなどの場合、完了までの時間を短縮します。

例えば、実稼動データベースのバックアップをスケジュールし、ストアの訪問回数が少ない場合にステージングデータベースをフォローアップすることをお勧めします。

## グリッド内の製品数の制限

大規模なカタログの製品グリッドのパフォーマンスを向上させるには、**[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Advanced] > [!UICONTROL Admin] > [!UICONTROL Admin Grids] >[!UICONTROL Limit Number of Products in Grid]** システム構成設定でグリッド内の製品数を制限することをお勧めします。

このシステム構成設定は、デフォルトでは無効になっています。 これを有効にすると、グリッド内の商品数を特定の値に制限できます。 **[!UICONTROL Records Limit]**&#x200B;はカスタマイズ可能な設定で、デフォルトの最小値は`20000`です。
**[!UICONTROL Limit Number of Products in Grid]**&#x200B;設定が有効になっていて、グリッド内の製品数がレコードの制限を超えている場合、制限されたレコードのコレクションが返されます。 制限に達すると、見つかったレコードの合計、選択したレコードの数、ページネーション要素がグリッドヘッダーから非表示になります。

グリッド内の製品の合計数が制限されている場合、製品グリッドのマスアクションには影響しません。 商品グリッドのプレゼンテーション層にのみ影響します。 例えば、グリッド内の製品の数は限られており、`20000`をクリックし、**[!UICONTROL Select All]**&#x200B;個のマス アクションを選択し、一部の属性を更新します。 **[!UICONTROL Update attributes]**&#x200B;その結果、すべての製品が更新され、`20000`件のレコードの限定コレクションは更新されません。

製品グリッドの制限は、UI コンポーネントで使用される製品コレクションにのみ影響します。 その結果、すべての製品グリッドがこの制限の影響を受けるわけではありません。 `Magento\Catalog\Ui\DataProvider\Product\ProductCollection`を使用しているユーザーのみ。
商品グリッドコレクションは、次のページでのみ制限できます。

* カタログ商品グリッド
* 関連/アップセル/クロスセル商品の追加グリッド
* 製品をバンドル製品に追加
* 製品をグループ製品に追加
* Admin Create Order Page

製品グリッドを制限しない場合は、結果コレクションに&#x200B;**[!UICONTROL Records Limit]**&#x200B;より少ない項目を含めるように、フィルターをより正確に使用することをお勧めします。
