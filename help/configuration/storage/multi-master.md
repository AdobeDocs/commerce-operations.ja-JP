---
title: スプリット・データベースのパフォーマンス・ソリューション
description: Adobe Commerceの分割データベースソリューションについて説明します。
recommendations: noCatalog
exl-id: 922a9af7-2c46-4bf3-b1ad-d966f5564ec0
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '623'
ht-degree: 0%

---

# 分割データベース・ソリューションの概要

{{ee-only}}

{{deprecate-split-db}}

Adobe Commerceには、Commerce アプリケーションの様々な機能領域に対して 3 つの個別のマスターデータベースを使用する機能など、拡張性の利点がいくつかあります。

チェックアウト、注文、および製品データは、それぞれ個別のマスターデータベースを使用でき、必要に応じて複製できます。 この分離により、必要に応じて、web サイトのチェックアウト、注文管理アクティビティ、web サイトのブラウジング、マーチャンダイジングアクティビティから負荷を個別に調整できます。 これらの変更により、データベース層の拡張方法にかなりの柔軟性がもたらされます。

>[!INFO]
>
>クラウドインフラストラクチャー上のAdobe Commerceでは、この機能をサポートして _ません_。

`ResourceConnections` クラスは、Commerce アプリケーションへの統合 MySQL データベース接続を提供します。 マスターデータベースへのクエリには、Command Query Responsibility Segregation （CQRS）データベースパターンを実装します。 このパターンでは、読み取りおよび書き込みクエリを適切なデータベースにルーティングするロジックを処理します。 開発者は、使用されている設定を把握する必要はなく、別の読み取りおよび書き込みデータベース接続はありません。

オプションのデータベース・レプリケーションを設定すると、次の利点があります。

- データバックアップ
- マスターデータベースに影響を与えないデータ分析
- 拡張性

MySQL データベースは非同期でレプリケートするので、スレーブがマスターから更新を受け取るために永続的に接続される必要はありません。

次の図に、この機能の仕組みを示します。

![Adobe Commerceは、異なるデータベースを使用してテーブルを保存します ](../../assets/configuration/split-db-diagram-ee.png)

Magento Open Sourceでは、1 つのマスターデータベースのみが使用されます。

Adobe Commerceでは、レプリケーションに 3 つのマスターデータベースと設定可能な数のスレーブデータベースを使用します。 Adobe Commerceにはデータベース接続用のインターフェイスが 1 つしかないので、パフォーマンスとスケーラビリティが向上します。

## 設定オプション

分割データベースパフォーマンスソリューションの設計方法により、カスタムコードとインストール済みコンポーネントでは _次の操作を行うことができません_。

- データベースに直接書き込む（代わりに、Adobe Commerce データベースインターフェイスを使用する必要があります）
- 販売データベースまたは見積データベースに影響する JOIN の使用
- チェックアウト、販売、またはメイン データベースのテーブルに外部キーを使用する

>[!WARNING]
>
>コンポーネントの開発者に問い合わせて、そのコンポーネントが上記のいずれかを実行しているかどうかを確認してください。 その場合は、次のいずれか 1 つのみを選択する必要があります。
>
>- コンポーネント開発者に、コンポーネントの更新を依頼します。
>- 分割データベースソリューションを使用せずに _コンポーネントをそのまま_ 使用します。
>- 分割データベースソリューションを使用できるように、コンポーネントを削除します。

つまり、次のいずれかの操作を行うこともできます。

- Commerceを実稼動環境に導入する前に _分割データベースソリューションを設定_ ます。

  Adobeでは、Commerce ソフトウェアのインストール後はできるだけ早くスプリットデータベースを設定することをお勧めします。

- [ 手動で構成 ](multi-master-manual.md) 分割データベース ソリューション。

  コンポーネントを既にインストールしている場合、またはCommerceが既に実稼動環境にある場合は、このタスクを実行する必要があります。 （_実稼動システムは更新しないでください_ 開発システムで更新を行い、テスト後に変更を同期します）。

  >[!WARNING]
  >
  >2 つの追加のデータベース・インスタンスを手動でバックアップする必要があります。 Commerceは、メインデータベースインスタンスのみをバックアップします。 [`magento setup:backup --db`](../../installation/tutorials/backup.md) コマンドおよび管理オプションでは、追加のテーブルはバックアップされません。

## 前提条件

分割データベースでは、任意のホストに 3 つの MySQL マスターデータベースを設定する必要があります（3 つのデータベースはすべてCommerce サーバー上、各データベースは個別のサーバー上など）。 これらは _master_ データベースであり、次のように使用されます。

- チェックアウト テーブル用の 1 つのマスターデータベース
- 営業用テーブル （_Order Management System_ または _OMS_ テーブルとも呼ばれます）用の 1 つのマスターデータベース
- Commerce 2 アプリケーションテーブルの残りの部分に 1 つのマスターデータベース

さらに、ロード・バランサおよびバックアップとして機能する任意の数の _スレーブ_ データベースをオプションで設定できます。

このガイドでは、マスターデータベースのみをセットアップする方法について説明します。 必要に応じて、スレーブデータベースを設定するためのサンプル設定と参照を提供します。

このガイドでは、3 つのマスター・データベースの名前を次に示します。

- `magento_quote`
- `magento_sales`
- `magento`

（データベースに任意の名前を付けることができます）。
