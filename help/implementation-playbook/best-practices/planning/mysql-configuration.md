---
title: MySQL 設定のベストプラクティス
description: MySQLトリガーとスレーブ接続が Commerce サイトのパフォーマンスに与える影響と、それらを効果的に使用する方法について説明します。
role: Developer
feature: Best Practices
source-git-commit: 3e0187b7eeb6475ea9c20bc1da11c496b57853d1
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 0%

---


# MySQL 設定のベストプラクティス

>[!NOTE]
>
>このトピックには、人種差別、性差別、または圧迫的なソフトウェア用語が含まれ、読者が傷ついたり、傷ついたり、不快に感じたり、歓迎されなかったりする場合があります。 Adobeは、コード、ドキュメントおよびユーザーエクスペリエンスからこれらの用語を削除する作業を進めています。

## トリガー

この記事では、MySQLトリガーを使用する際のパフォーマンスの問題を回避する方法について説明します。 トリガーは、変更を監査テーブルに記録するために使用されます。

### 影響を受ける製品およびバージョン

- Adobe Commerceオンプレミス
- Adobe Commerce an cloud infrastructure

>[!WARNING]
>
>クラウドプロジェクト上のAdobe Commerceの場合は、必ず、実稼動環境の設定を変更する前に、ステージング環境で設定の変更をテストしてください。

### パフォーマンスへの影響

トリガーは、MySQL が事前にコンパイルしないことを意味するコードとして解釈されます。

クエリのトランザクションスペースに接続すると、トリガーは、テーブルで実行される各クエリに対して、パーサとインタプリタにオーバーヘッドを追加します。 トリガーは、元のクエリと同じトランザクション領域を共有し、これらのクエリがテーブルのロックを競合しますが、トリガーは別のテーブルのロックを個別に競合します。

多数のトリガーを使用する場合、この追加のオーバーヘッドがサイトのパフォーマンスに悪影響を与える可能性があります。

>[!WARNING]
>
>Adobe Commerceは、Adobe Commerceデータベース内のカスタムトリガーをサポートしていません。カスタムトリガーでは、将来のAdobe Commerceバージョンとの互換性が失われる可能性があるからです。 ベストプラクティスについては、 [一般的な MySQL ガイドライン](../../../installation/prerequisites/database/mysql.md) (Adobe Commerceドキュメント ) を参照してください。

### 効果的な使用

トリガー使用時のパフォーマンスの問題を回避するには、次のガイドラインに従います。

- トリガーの実行時に一部のデータを書き込むカスタムトリガーがある場合は、このロジックを移動して、監査テーブルに直接書き込みます。 例えば、アプリケーションコードにクエリを追加して、トリガーの作成対象のクエリの後にクエリを追加します。
- 既存のカスタムトリガーを確認し、それらを削除して、アプリケーション側からテーブルに直接書き込むことを検討します。 を使用して、データベース内の既存のトリガーを確認します。 [`SHOW TRIGGERS` SQL 文](https://dev.mysql.com/doc/refman/8.0/en/show-triggers.html).
- その他のサポート、質問、または懸念事項の場合 [Adobe Commerceサポートチケットを送信する](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?#submit-ticket).

## スレーブ接続

Adobe Commerceは、複数のデータベースを非同期で読み取ることができます。 クラウドインフラストラクチャ Pro アーキテクチャにデプロイされたコマースサイトの MySQL データベースの負荷が高くなると予想される場合、Adobeは MYSQL スレーブ接続を有効にすることをお勧めします。

MYSQL スレーブ接続を有効にすると、Adobe Commerceはデータベースへの読み取り専用接続を使用して、非マスターノード上の読み取り専用トラフィックを受け取ります。 読み取り/書き込みトラフィックを処理するノードが 1 つだけの場合、ロードバランシングを通じてパフォーマンスが向上します。

### 影響を受けるバージョン

クラウドインフラストラクチャ上のAdobe Commerce、Pro アーキテクチャのみ

### 設定

クラウドインフラストラクチャ上のAdobe Commerceで、MYSQL スレーブ接続のデフォルト設定を上書きするには、 [MYSQL_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#mysql_use_slave_connection) 変数を使用します。 この変数をに設定します。 `true` データベースへの読み取り専用接続を自動的に使用する。

**MySQL スレーブ接続を有効にするには**:

1. ローカルワークステーションで、プロジェクトディレクトリに移動します。

1. Adobe Analytics の `.magento.env.yaml` ファイル、 `MYSQL_USE_SLAVE_CONNECTION` を true に設定します。

   ```
   stage:
     deploy:
       MYSQL_USE_SLAVE_CONNECTION: true
   ```

1. をコミットする `.magento.env.yaml` ファイルを変更し、リモート環境にプッシュします。

   デプロイメントが正常に完了すると、クラウド環境で MySQL スレーブ接続が有効になります。
