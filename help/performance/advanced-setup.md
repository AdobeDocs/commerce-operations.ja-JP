---
title: 詳細設定
description: 大量のデータを処理するように設計された大規模企業システムのベストプラクティスと推奨事項を確認します。
exl-id: eb9ca9fa-b099-4e77-ab33-16cd0f382ffe
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '1173'
ht-degree: 0%

---

# 詳細設定

[!DNL Commerce] は、あらゆる規模のマーチャント向けのソリューションを含む、非常に柔軟で拡張性の高い製品です。 この節では、大量のデータを扱うように [!DNL Commerce] を設定する際のベストプラクティスや推奨事項、極端な負荷、その他の大規模法人の場合に関する推奨事項について説明します。

## インデックスのパフォーマンスの調整

大量のデータを処理する場合、インデックスの再作成が問題になる可能性があります。 [!DNL Commerce] チームは、最も読み込まれているインデックスを選択し、バッチインデックスを有効にしました。これにより、各イテレーションで処理するデータの一部を設定できます。 この方法で、ユーザーはデータベース内のデータのタイプとサイズに基づいてバッチサイズを調整できます。

この設定を管理するには、対応するモジュールの `di.xml` ファイルで `batchRowsCount` パラメーターを編集します。 この機能をサポートしているインデックスは次のとおりです。

* カテゴリ製品インデックス（カタログモジュール）
* 物価指数（カタログモジュール）
* EAV Index （カタログモジュール）
* 在庫インデックス （CatalogInventory モジュール）

インデックスバッチサイズ変数を調整すると、インデクサーのパフォーマンスを調整できます。 これは、インデクサーによって一度に処理されるエンティティの数を制御します。 状況によっては、インデックス作成時間が大幅に短縮することがあります。

例えば、B2B Mediumに似たプロファイルを実行している場合、`app/code/Magento/catalog/etc/di.xml` の設定値 `batchRowsCount` を上書きし、デフォルト値 `5000` を `1000` に上書きできます。 これにより、デフォルトの [!DNL MySQL] 設定で、完全なインデックス作成時間が 4 時間から 2 時間に短縮されます。

>[!NOTE]
>
>カタログルールインデクサーのバッチ処理が有効になっていません。 多数のカタログルールを持つマーチャントは、インデックス作成時間を最適化するために [!DNL MySQL] 設定を調整する必要があります。 このような場合、[!DNL MySQL] 設定ファイルを編集し、より多くのメモリを TMP_TABLE_SIZE およびMAX_HEAP_TABLE_SIZE 設定値（両方のデフォルトは 16M）に割り当てると、このインデクサーのパフォーマンスは向上しますが、より多くの RAM を消費す [!DNL MySQL] ことになります。

### 顧客グループと共有カタログを Web サイト別に制限する

多数の製品 SKU、web サイト、顧客グループまたは共有カタログが、製品価格とカタログルールインデクサーの実行時間に影響を与えます。 これは、デフォルトでは、すべての web サイトがすべての顧客グループ（共有カタログ）に割り当てられるからです。

インデックス作成時間を短縮するには、[ 特定の web サイトを顧客グループから除外（共有カタログ） ](https://developer.adobe.com/commerce/php/development/components/indexing/optimization/#customer-group-limitations-by-websites) します。

## Redis の設定

1 つの Redis インスタンスでは、受信リクエストを処理するのに十分でない場合があります。 この状況に対処するために推奨できる解決策がいくつかあります。

まず、[!DNL Commerce] を使用すると、キャッシュタイプごとに個別のキャッシュストレージを設定できます。 これにより、Magentoに登録されているキャッシュの種類の数に応じて、別々の Redis インスタンスをインストールできます。 現実的には、設定、レイアウト、ブロックなど、最もアクティブに使用されているキャッシュに Redis インスタンスを使用する場合があります。

別の解決策として、設定キャッシュをファイルシステムに配置し、他のキャッシュを Redis サーバーに移動する方法があります。 このソリューションでは、すべての web ノードの設定キャッシュを一元的に無効化するための個別のツールが必要になります。

また、ノード数が自動的に増加する並列の読み取り/書き込み操作を実行する Redis クラスターを使用することもできます。 この場合、[!DNL Commerce] は設定を提供しませんが、マイナーカスタマイズを使用して起動できます。

## [!DNL RabbitMQ] の設定

Adobe Commerceは、[!DNL RabbitMQ] を通じて実装されたメッセージキューをサポートします。 [!DNL Commerce] では、このサービスを使用して、B2B カタログ操作や非同期在庫更新など、多数の非同期操作を実行します。 ジョブ サーバにジョブを追加するためのすべてのインタフェースは、製品とともに配布され、サードパーティ拡張機能の範囲でカスタムの非同期ロジック実装に使用できます。 他の統合の場合と同様に、[!DNL Commerce] では、すべての推奨設定を含み、実稼動で使用するための完全な準備が整った [!DNL RabbitMQ] 用のサンプル設定ファイルを提供します。

## データベースの分割

>[!WARNING]
>
>Adobe Commerceのバージョン 2.4.2 では、分割データベース機能は [ 非推奨 ](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Split-Database-in-Magento-Commerce/ba-p/465187) となりました。 [ 分割データベースから単一データベースへの復帰 ](../configuration/storage/revert-split-database.md) を参照してください。

Adobe Commerceを使用すると、スケーラブルなデータベースストレージを設定して、拡大するビジネスのニーズに対応できます。 特定のドメインを提供する 3 つの個別のマスター・データベースを設定できます。

* メイン（カタログ）データベース
* データベースのチェックアウト
* Order Management System （OMS）データベース

追加のデータベースを構成するには、空のデータベースを作成し、次のいずれかのコマンドを実行する必要があります。

チェックアウトマスターDB

```bash
bin/magento setup:db-schema:split-quote
```

OMSマスターDB の場合

```bash
bin/magento setup:db-schema:split-sales
```

これらのコマンドは、特定のドメイン テーブルをメイン データベースからドメイン データベースに移行します。 また、[!DNL Commerce] の設定を変更して、対応する接続と制約を処理できるようにします。

チェックアウトとOrder Managementに別々のデータベースを持たせることで、データベースサーバー間で負荷を分散させることができます。 カタログの可用性や他の操作に影響を与えることなく、より多くのチェックアウトを提供し、1 秒あたりの多くの注文を処理できます。 データベースをフラッシュまたはアクティブなセールスの期間に分割するか、自然発生的に負荷の高いプロジェクトに永続的に使用することをお勧めします。 データベース間での現在のデータの移行は、システム管理者の監督の下で実行する必要があります。  本番モードの間は、データベースを分割しないでください。

マスターデータベースに加え、[!DNL Commerce] では多数のスレーブデータベース（システムで宣言されたデータリソースごとに 1 つ）を設定できます。 スレーブ・データベースは、メイン・データベースのフル・レプリカとして、またはドメイン・マスター・データベースの 1 つとして機能します。 特定のリソースに対する読み取り操作のために発行されます。

次のコマンドを実行して、スレーブ・データベースを追加できます。

```bash
bin/magento setup:db-schema:add-slave
```

このコマンドは構成の変更を実行しますが、レプリケーション自体は構成しません。 手動で行う必要があります。

マスター・データベースを分割してスレーブ・データベースを設定した後、[!DNL Commerce] は指定したデータベースへの接続を自動的に調整し、リクエストのタイプ（POST、PUT、GETなど）とデータ・リソースに基づいて判断を行います。 [!DNL Commerce] またはその拡張機能がGETリクエストに対して書き込み処理を行うと、スレーブからマスターデータベースへの接続が自動的に切り替わります。 マスターデータベースでも同様に機能します。チェックアウト関連のテーブルを操作するとすぐに、システムはすべてのクエリを特定のデータベースにリダイレクトします。 その間、カタログ関連のクエリはすべてメインデータベースに送られます。

設定および複数のマスター/スレーブ設定の利点について詳しくは、を参照してください。
[ 分割データベースパフォーマンスソリューション ](../configuration/storage/multi-master.md)。

## メディアコンテンツの提供

Magentoでは、メディアコンテンツを提供および配信するための特別な統合は提供しません。 Magentoでは、すべての一般的なアプローチを一緒に使用できます。

メディアコンテンツを提供する最も簡単な方法は、[!DNL Varnish] サーバーでの配信とキャッシュです。 このアプローチでは、メディアコンテンツを保存するための共有ファイルシステム、または [!DNL Varnish] を指す専用サーバーを想定しています。

中負荷および高負荷環境の場合は、Fastly、Akamai などのコンテンツ配信ネットワーク（CDN）サービスを使用することをお勧めします。 これらのサービスを使用する場合、[!DNL Commerce] はコンテンツの更新に従来のプル アプローチを使用します。 対応する CDN サービスと連携するように [!DNL Commerce] URL を設定する必要があります。 メディアコンテンツを CDN に移動すると、インスタンスの負荷が大幅に軽減されます。

## ログストレージの設定

ログの保存とその他のディスク操作への影響は、特に高負荷の状況で、web ノードの可用性に影響を与えます。 ログが必要ない場合は、最小限に抑えることをお勧めします。 また、高いアクセス速度を持つ別のストレージ・システムに書き込まれるようにログを構成することもできます。 ログストレージへのアクセスに関するボトルネックは、書き込みまたは読み取り操作をフローの一部としてログに記録する受信リクエストの処理に直接影響を与える可能性があります。
