---
title: 分割データベースパフォーマンスソリューション
description: Adobe CommerceとMagento Open Sourceの分割データベースソリューションについて
recommendations: noCatalog
exl-id: 922a9af7-2c46-4bf3-b1ad-d966f5564ec0
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '626'
ht-degree: 0%

---

# 分割データベースソリューションの概要

{{ee-only}}

{{deprecate-split-db}}

Adobe Commerceには、Commerce アプリケーションの様々な機能領域に対して 3 つの異なるマスターデータベースを使用できる機能など、いくつかの拡張性の利点があります。

チェックアウト、注文、製品の各データは、オプションでレプリケートできる個別のマスターデータベースを使用できます。 この分離により、必要に応じて、Web サイトのチェックアウト、注文管理アクティビティ、Web サイトの閲覧、マーチャンダイジングアクティビティから読み込み量を個別に拡大できます。 これらの変更により、データベース層の拡張方法を大幅に柔軟に行うことができます。

>[!INFO]
>
>クラウドインフラストラクチャ上のAdobe Commerce _not_ は、この機能をサポートします。

The `ResourceConnections` クラスは、統合 MySQL データベースとコマースアプリケーションとの接続を提供します。 マスターデータベースへのクエリには、Command Query Responsibility Manage(CQRS) データベースパターンを実装します。 このパターンは、読み取りクエリと書き込みクエリを適切なデータベースにルーティングするロジックを処理します。 開発者は、どの設定が使用されているかを知る必要がなく、読み取りと書き込みに関するデータベース接続も別に存在しません。

オプションのデータベースレプリケーションを設定する場合、次の利点があります。

- データのバックアップ
- マスターデータベースに影響を与えないデータ分析
- 拡張性

MySQL データベースは非同期でレプリケートされます。つまり、マスターから更新を受け取るためにスレーブを恒久的に接続する必要はありません。

次の図は、この機能の仕組みを示しています。

![Adobe Commerceは異なるデータベースを使用してテーブルを格納します](../../assets/configuration/split-db-diagram-ee.png)

Magento Open Sourceでは、1 つのマスターデータベースのみが使用されます。

Adobe Commerceでは、3 つのマスターデータベースと設定可能な数のスレーブデータベースをレプリケーションに使用します。 Adobe Commerceは、データベース接続用の単一のインターフェイスを備えているので、パフォーマンスが向上し、拡張性が向上します。

## 設定オプション

分割データベースのパフォーマンスソリューションの設計方法により、カスタムコードとインストール済みのコンポーネントが使用されます。 _できません_ 次のいずれかの操作を行います。

- データベースに直接書き込む ( 代わりに、 Adobe Commerceデータベースインターフェイスを使用する必要があります )
- 販売または見積データベースに影響を与える JOIN を使用します
- チェックアウト、販売、またはメインデータベースのテーブルに外部キーを使用する

>[!WARNING]
>
>コンポーネントの開発者に問い合わせて、コンポーネントが前述のいずれかを実行するかどうかを確認します。 その場合は、次のいずれかを選択する必要があります。
>
>- コンポーネント開発者に、コンポーネントを更新するよう依頼します。
>- コンポーネントをそのまま使用 _なし_ 分割データベースソリューション。
>- 分割データベースソリューションを使用できるように、コンポーネントを削除します。

これは、次のいずれかを実行できることを意味します。

- 分割データベースソリューションの構成 _前_ コマースを実稼動環境に組み込んでいます。

  Adobeでは、Commerce ソフトウェアをインストールした後、できるだけ早く分割データベースを設定することをお勧めします。

- [手動設定](multi-master-manual.md) 分割データベースソリューション。

  既にコンポーネントがインストールされている場合、またはコマースが既に実稼動環境にある場合は、このタスクを実行する必要があります。 (_禁止_ 本番システムを更新します。開発システムで更新を行い、テスト後に変更を同期します。)

  >[!WARNING]
  >
  >2 つの追加のデータベースインスタンスを手動でバックアップする必要があります。 Commerce は、メインデータベースインスタンスのみをバックアップします。 The [`magento setup:backup --db`](../../installation/tutorials/backup.md) コマンドおよび管理オプションでは、追加のテーブルはバックアップされません。

## 前提条件

分割データベースでは、任意のホストに 3 つの MySQL マスターデータベースを設定する必要があります（Commerce サーバー上の 3 つすべて、各データベースを別々のサーバー上に配置するなど）。 これらは _プライマリ_ データベースは次のように使用されます。

- チェックアウトテーブル用の 1 つのマスターデータベース
- 販売テーブル用の 1 つのマスターデータベース ( 別名： _受注管理システム_&#x200B;または _OMS_、テーブル )
- Commerce 2 アプリケーションテーブルの残りの部分に対して 1 つのマスターデータベース

さらに、任意の数の _セカンダリ_ ロードバランサーとバックアップとして機能するデータベース。

このガイドでは、マスター・データベースの設定のみを行う方法について説明します。 必要に応じてスレーブデータベースを設定するためのサンプルの設定と参照を提供しています。

このガイドでは、3 つのマスターデータベースの名前を次に示します。

- `magento_quote`
- `magento_sales`
- `magento`

（データベースに任意の名前を付けることができます）。
