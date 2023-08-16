---
title: MySQLトリガー使用
description: Adobe Commerceで MySQLトリガーを効果的に使用する方法を学びます。
role: Developer
feature: Best Practices
exl-id: acac3e47-67c8-4eea-80e3-e26f2854391a
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 0%

---

# MySQLトリガー使用のベストプラクティス

この記事では、MySQLトリガーを使用する際のパフォーマンスの問題を回避する方法について説明します。 トリガーは、変更を監査テーブルに記録するために使用されます。

## 影響を受ける製品およびバージョン

- Adobe Commerceオンプレミス
- Adobe Commerce an cloud infrastructure

>[!WARNING]
>
>クラウドプロジェクト上のAdobe Commerceの場合は、必ず、実稼動環境の設定を変更する前に、ステージング環境で設定の変更をテストしてください。

## パフォーマンスへの影響の理解

トリガーは、MySQL が事前にコンパイルしないことを意味するコードとして解釈されます。

クエリのトランザクションスペースに接続すると、トリガーは、テーブルで実行される各クエリに対して、パーサとインタプリタにオーバーヘッドを追加します。 トリガーは、元のクエリと同じトランザクション領域を共有し、これらのクエリがテーブルのロックを競合しますが、トリガーは別のテーブルのロックを個別に競合します。

多数のトリガーを使用する場合、この追加のオーバーヘッドがサイトのパフォーマンスに悪影響を与える可能性があります。

>[!WARNING]
>
>Adobe Commerceは、Adobe Commerceデータベース内のカスタムトリガーをサポートしていません。カスタムトリガーでは、将来のAdobe Commerceバージョンとの互換性が失われる可能性があるからです。 ベストプラクティスについては、 [一般的な MySQL ガイドライン](../../../installation/prerequisites/database/mysql.md) (Adobe Commerceドキュメント ) を参照してください。

## 効果的にトリガーを使用

トリガー使用時のパフォーマンスの問題を回避するには、次のガイドラインに従います。

- トリガーの実行時に一部のデータを書き込むカスタムトリガーがある場合は、このロジックを移動して、監査テーブルに直接書き込みます。 例えば、アプリケーションコードにクエリを追加して、トリガーの作成対象のクエリの後にクエリを追加します。
- 既存のカスタムトリガーを確認し、それらを削除して、アプリケーション側からテーブルに直接書き込むことを検討します。 を使用して、データベース内の既存のトリガーを確認します。 [`SHOW TRIGGERS` SQL 文](https://dev.mysql.com/doc/refman/8.0/en/show-triggers.html).
- その他のサポート、質問、または懸念事項の場合 [Adobe Commerceサポートチケットを送信する](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?#submit-ticket).

## 追加情報

- [MySQL の前提条件](../../../installation/prerequisites/database/mysql.md)
- [クラウドインフラストラクチャ上のAdobe Commerceに関するデータベースのベストプラクティス](database-on-cloud.md)
