---
title: 設定のベストプラクティス
description: これらのベストプラクティスを使用して、Adobe CommerceまたはMagento Open Sourceのデプロイメントの応答時間を最適化します。
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '938'
ht-degree: 0%

---


# 設定のベストプラクティス

Commerce には、ページの応答時間を改善し、より高いスループットを提供するために使用できる多くの設定およびツールが用意されています。

## Cron ジョブ

でのすべての非同期操作 [!DNL Commerce] は、Linux を使用して実行されます。 `cron` コマンドを使用します。 詳しくは、 [cron の設定と実行](../configuration/cli/configure-cron-jobs.md) を設定してください。

## インデクサー

インデクサーは **[!UICONTROL Update on Save]** または **[!UICONTROL Update on Schedule]** モード。 この **[!UICONTROL Update on Save]** mode は、カタログや他のデータが変更されるたびに、即座にインデックスを作成します。 このモードでは、ストアでの更新操作と参照操作が少ないことを前提としています。 高負荷時に大きな遅延が生じ、データが使用できなくなる可能性があります。 次を使用することをお勧めします。 **スケジュールに従って更新** 実稼動環境のモードです。データの更新に関する情報を保存し、特定の cron ジョブを通じてバックグラウンドの一部によるインデックス作成を実行するからです。 各 [!DNL Commerce] インデクサーが別々に  **[!UICONTROL System]** > [!UICONTROL Tools] > **[!UICONTROL Index Management]** 設定ページを開きます。

MariaDB 10.4 でのインデックス再作成は、他の MariaDB や [!DNL MySQL] バージョン。 回避策として、デフォルトの MariaDB 設定を変更し、次のパラメーターを設定することをお勧めします。

* [`optimizer_switch='rowid_filter=off'`](https://mariadb.com/kb/en/optimizer-switch/)
* [`optimizer_use_condition_selectivity = 1`](https://mariadb.com/products/skysql/docs/reference/es/system-variables/optimizer_use_condition_selectivity/)

## キャッシュ

実稼動環境でストアを起動したら、 **[!UICONTROL System]** > [!UICONTROL Tools] > **[!UICONTROL Cache Management]** ページ。 を使用することを強くお勧めします。 [!DNL Varnish]（効率的な実稼動ページキャッシュソリューションであるため）

## 非同期電子メール通知

「非同期電子メール通知」設定を有効にすると、チェックアウトおよび注文処理の電子メール通知を処理するプロセスがバックグラウンドに移動します。 この機能を有効にするには、に移動します。 **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Sales] > [!UICONTROL Sales Emails] > [!UICONTROL General Settings] >[!UICONTROL Asynchronous Sending]**. 詳しくは、 [セールスメール](https://docs.magento.com/user-guide/configuration/sales/sales-emails.html) 内 _Magento Open Sourceユーザーガイド_ を参照してください。

## 非同期の注文データ処理

ストアフロントで集中的に売り上げを行う場合と、 [!DNL Commerce] は集中的な注文処理を実行しています。 次の項目を設定できます。 [!DNL Commerce] 対応するテーブルの読み取り操作と書き込み操作の間の競合を避けるために、データベースレベルでこれら 2 つのトラフィックパターンを区別します。 注文データの保存とインデックス作成は、非同期でおこなうことができます。 受注は一時保管に置かれ、衝突なしに受注管理グリッドに一括で移動されます。 このオプションは、次の場所から有効化できます。 **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Advanced] > [!UICONTROL Developer] > [!UICONTROL Grid Settings] >[!UICONTROL Asynchronous indexing]**. 詳しくは、 [スケジュールされたグリッドの更新](https://docs.magento.com/user-guide/sales/order-grid-updates-schedule.html) 内 _Magento Open Sourceユーザーガイド_ を参照してください。

>[!WARNING]
>
>この **[!UICONTROL Developer]** タブとオプションは、 [開発者モード](../configuration/cli/set-mode.md). [Adobe Commerce an cloud infrastructure](https://devdocs.magento.com/cloud/requirements/cloud-requirements.html#cloud-req-test) はをサポートしていません `Developer` モード。

## 遅延在庫更新

集中的な売り上げの時に [!DNL Commerce] は、注文に関連する在庫更新を延期できます。 これにより、操作の数を最小限に抑え、注文の配置プロセスを高速化できます。 ただし、このオプションは危険で、在庫数量がマイナスになる可能性があるので、店舗で「バックオーダー」が有効になっている場合にのみ使用できます。 このオプションを使用すると、店舗のチェックアウトフローのパフォーマンスが大幅に向上し、在庫をオンデマンドで簡単に補充できます。 サイトでの遅延在庫更新を有効にするには、次に移動します： **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Catalog] > [!UICONTROL Inventory] > [!UICONTROL Product Stock Options] >[!UICONTROL Use Deferred Stock Update]**. 詳しくは、 [在庫の管理](https://docs.magento.com/user-guide/catalog/inventory.html) 内 _Adobe Commerce User Guide_ を参照してください。

>[!INFO]
>
>このオプションは、 **[!UICONTROL Backorder with any mode]** がアクティブ化されている。

## クライアント側の最適化設定

ストアフロントの応答性を向上させるには [!DNL Commerce] インスタンスの場合は、「デフォルト」または「開発者」モードで「管理者」に移動し、次の設定を変更します。

**[!UICONTROL Stores]-> [!UICONTROL Configuration] -> [!UICONTROL Advanced] -> [!UICONTROL Developer]:**

| 設定グループ | 設定 | 値 |
| ------------------- | -------------------------- | ------ |
| グリッド設定 | 非同期インデックス作成 | 有効にする |
| CSS 設定 | CSS ファイルの縮小 | はい |
| [!DNL JavaScript] 設定 | 縮小 [!DNL JavaScript] ファイル | はい |
| [!DNL JavaScript] 設定 | 有効にする [!DNL JavaScript] バンドル | はい |
| テンプレート設定 | 縮小HTML | はい |

>[!INFO]
>
>この **[!UICONTROL Developer]** タブとオプションは、 [開発者モード](../configuration/cli/set-mode.md). [Adobe [!DNL Commerce] クラウドインフラストラクチャ](https://devdocs.magento.com/cloud/requirements/cloud-requirements.html#cloud-req-test) はをサポートしていません `Developer` モード。

次をアクティブ化すると、 **[!UICONTROL Enable [!DNL JavaScript] Bundling]** 」オプションを使用すると、Commerce はすべての JS リソースを、ストアフロントページに読み込まれた 1 つまたは複数のバンドルに結合できます。 JS をバンドルすると、サーバーへのリクエスト数が少なくなり、ページのパフォーマンスが向上します。 また、最初の呼び出しでブラウザーが JS リソースをキャッシュし、それらを以降の参照で再利用するのにも役立ちます。 また、このオプションは、すべての JS がテキストとして読み込まれるので、遅延評価をもたらします。 ページ上で特定のアクションがトリガーされた後にのみ、コードの分析と評価を開始します。 ただし、最初の呼び出しですべての JS コンテンツが読み込まれるので、最初のページ読み込み時間が非常に重要なストアでは、この設定はお勧めしません。

>[!INFO]
>
>詳しくは、 [クラウドインフラストラクチャ上のAdobe CommerceとAdobe Commerceでの CSS および JavaScript ファイルの最適化](https://support.magento.com/hc/en-us/articles/360044482152) (CSS と JavaScript の最適化について詳しくは、 Adobe Commerceヘルプセンター_を参照 )。

### バンドルのヒント

* 縮小化とバンドル ( [r.js](https://requirejs.org/)) をクリックします。 [!DNL Commerce] 組み込みのメカニズムは最適ではなく、代替手段として提供されています。
* JS バンドルを使用する代わりに、HTTP2 プロトコルをアクティブ化する方法を使用できます。 このプロトコルには、ほぼ同じ利点があります。
* JS ファイルと CSS ファイルの結合などの非推奨の設定は、ページのHEADセクションで同期的に読み込まれる JS 用にのみ設計されているので、使用しないことをお勧めします。 この方法を使用すると、バンドルが発生し、requireJS ロジックが正しく機能しなくなる場合があります。

## データベースメンテナンススケジュール {#database}

ステージングインスタンスと実稼動インスタンスに対して、定期的なデータベースバックアップを実行することをお勧めします。 バックアップ・オペレーションの I/O 負荷が高い性質が原因で、バックアップの速度が低下し、潜在的な問題が発生する可能性があります。 複数の環境に対して同時にデータベース・プロセスを実行すると、使用可能なリソースの競合が原因で実行に時間がかかる場合があります。

パフォーマンスを向上させるために、バックアップを連続して、1 回ずつ、オフピーク時に実行するようにスケジュールします。 この方法では、I/O の競合を回避し、特に小規模なインスタンス、大規模なデータベースなどで、完了までの時間を短縮できます。

例えば、実稼動データベースのバックアップをスケジュールし、ストアの訪問数が少なくなった場合にステージングデータベースをスケジュールすることをお勧めします。
