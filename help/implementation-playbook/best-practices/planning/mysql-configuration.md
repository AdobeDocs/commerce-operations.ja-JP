---
title: MySQL 設定のベストプラクティス
description: MySQL トリガーとスレーブ接続がCommerce サイトのパフォーマンスに与える影響と、それらを効果的に使用する方法について説明します。
role: Developer
feature: Best Practices
exl-id: 7c2f51fd-9333-4954-bd35-79c2de3cb2ff
source-git-commit: 823498f041a6d12cfdedd6757499d62ac2aced3d
workflow-type: tm+mt
source-wordcount: '506'
ht-degree: 0%

---

# MySQL 設定のベストプラクティス

>[!NOTE]
>
>このトピックには、業界標準のソフトウェア用語が含まれています。これらの用語を人種差別的、性差別的、または抑圧的と見なす場合があり、読者が苦痛を感じたり、トラウマを抱いたり、歓迎されないと感じたりする場合があります。 Adobeでは、これらの用語をコード、ドキュメントおよびユーザーエクスペリエンスから削除するよう取り組んでいます。

## トリガー

この記事では、MySQL トリガーを使用する際にパフォーマンスの問題を回避する方法について説明します。 トリガーは、変更を監査テーブルに記録するために使用されます。

### 影響を受ける製品とバージョン

- Adobe Commerce オンプレミス
- クラウドインフラストラクチャー上のAdobe Commerce

>[!WARNING]
>
>クラウドプロジェクト上のAdobe Commerceの場合、実稼動環境用の設定を変更する前に、必ずステージング環境で設定変更をテストしてください。

### パフォーマンスへの影響

トリガーは、MySQL が事前にコンパイルしないことを意味するコードとして解釈されます。

問い合わせのトランザクション空間に接続すると、トリガーは、テーブルに対して行われる問い合わせごとにパーサとインタプリタにオーバーヘッドを加えます。 トリガーは元の問い合わせと同じトランザクション領域を共有し、それらの問い合わせがテーブルのロックを競合する間、トリガーは別のテーブルのロックを競合しません。

多くのトリガーを使用すると、このオーバーヘッドの増加により、サイトのパフォーマンスが低下する可能性があります。

>[!WARNING]
>
>Adobe Commerceでは、Adobe Commerce データベース内のカスタムトリガーをサポートしていません。カスタムバージョンは、今後のAdobe Commerce トリガーとの互換性を失う可能性があるからです。 ベストプラクティスについては、Adobe Commerce ドキュメントの [ 一般的な MySQL ガイドライン ](../../../installation/prerequisites/database/mysql.md) を参照してください。

### 効果的な使用

トリガーを使用する際のパフォーマンスの問題を防ぐには、次のガイドラインに従います。

- トリガーの実行時にデータを書き込むカスタムトリガーがある場合、代わりに、監査テーブルに直接書き込むように、このロジックを移動します。 例えば、トリガーを作成するクエリの後に、アプリケーションコードにクエリを追加します。
- 既存のカスタムトリガーを確認し、それらを削除して、アプリケーション側からテーブルに直接書き込むことを検討します。 [`SHOW TRIGGERS` SQL 文 ](https://dev.mysql.com/doc/refman/8.0/en/show-triggers.html) を使用して、データベース内の既存のトリガーを確認します。
- その他のサポート、質問または懸念については、[Adobe Commerce サポートチケットを送信 ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?#submit-ticket) してください。

## スレーブ接続

Adobe Commerceは、複数のデータベースを非同期で読み取ることができます。 Cloud infrastructure Pro アーキテクチャにデプロイされたCommerce サイトの MySQL データベースに大きな負荷がかかると予想される場合は、Adobeで MYSQL スレーブ接続を有効にすることをお勧めします。

MYSQL スレーブ接続を有効にすると、Adobe Commerceはデータベースへの読み取り専用接続を使用して、非マスターノードで読み取り専用トラフィックを受け取ります。 読み取り/書き込みトラフィックを処理するノードが 1 つだけの場合は、ロードバランシングによってパフォーマンスが向上します。

### 影響を受けるバージョン

Adobe Commerce on cloud infrastructure、Pro アーキテクチャのみ

### 設定

クラウドインフラストラクチャー上のAdobe Commerceでは、[MYSQL_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#mysql_use_slave_connection) 変数を設定することで、MYSQL スレーブ接続のデフォルト設定を上書きできます。 データベースへの読み取り専用接続を自動的に使用するには、この変数を `true` に設定します。

**MySQL スレーブ接続を有効にするには**:

1. ローカルワークステーションで、をプロジェクトディレクトリに変更します。

1. `.magento.env.yaml` ファイルで、`MYSQL_USE_SLAVE_CONNECTION` を true に設定します。

   ```
   stage:
     deploy:
       MYSQL_USE_SLAVE_CONNECTION: true
   ```

1. `.magento.env.yaml` ファイルの変更をコミットし、リモート環境にプッシュします。

   デプロイメントが正常に完了すると、クラウド環境に対して MySQL スレーブ接続が有効になります。
