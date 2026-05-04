---
title: MySQL設定のベストプラクティス
description: MySQL トリガーとスレーブ接続がCommerce サイトのパフォーマンスにどのように影響するか、またそれらを効果的に使用する方法について説明します。
role: Developer
feature: Best Practices
exl-id: 7c2f51fd-9333-4954-bd35-79c2de3cb2ff
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '549'
ht-degree: 0%

---

# MySQL設定のベストプラクティス

>[!NOTE]
>
>このトピックには、業界標準のソフトウェア用語が含まれており、人種差別的、性差別的、または抑圧的である可能性があり、読者が傷ついたり、トラウマを抱いたり、歓迎されていないと感じたりする可能性があります。 Adobeでは、コード、ドキュメント、ユーザーエクスペリエンスからこれらの条件を削除する取り組みを進めています。

## トリガー

この記事では、MySQL トリガーを使用する際のパフォーマンスの問題を回避する方法について説明します。 トリガーは、監査テーブルに変更を記録するために使用されます。

### 影響を受ける製品とバージョン

- Adobe Commerce オンプレミス
- Adobe Commerce on cloud infrastructure

>[!WARNING]
>
>クラウドプロジェクト上のAdobe Commerceの場合は、実稼動環境の設定を変更する前に、必ずステージング環境で設定変更をテストしてください。

### パフォーマンスへの影響

トリガーは、MySQLがプリコンパイルしないコードとして解釈されます。

クエリのトランザクションスペースに接続すると、トリガーは、テーブルで実行される各クエリのパーサーとインタプリターにオーバーヘッドを追加します。 トリガーは元のクエリと同じトランザクションスペースを共有し、それらのクエリはテーブル上のロックを競いますが、トリガーは別のテーブルのロックを競います。

多くのトリガーを使用している場合、このようなオーバーヘッドが増えることで、サイトのパフォーマンスに悪影響を及ぼす可能性があります。

>[!WARNING]
>
>Adobe Commerceでは、カスタムトリガーが将来のAdobe Commerce バージョンと互換性を持たなくなる可能性があるため、Adobe Commerce データベースのカスタムトリガーはサポートされません。 ベストプラクティスについては、Adobe Commerce ドキュメントの[一般MySQL ガイドライン &#x200B;](../../../installation/prerequisites/database/mysql.md)を参照してください。

### 効果的な利用

トリガーを使用する際のパフォーマンスの問題を回避するには、次のガイドラインに従います。

- トリガーの実行時に一部のデータを書き込むカスタムトリガーがある場合は、代わりに監査テーブルに直接書き込むようにこのロジックを移動します。 例えば、トリガーコードにクエリを追加し、クエリの後にアプリケーションコードを追加します。
- 既存のカスタムトリガーを確認し、それらを削除して、アプリケーション側からテーブルに直接書き込むことを検討します。 [`SHOW TRIGGERS` SQL ステートメント &#x200B;](https://dev.mysql.com/doc/refman/8.0/en/show-triggers.html)を使用して、データベース内の既存のトリガーを確認します。
- 追加サポート、質問、懸念事項については、[Adobe Commerce サポートチケットを送信してください](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?#submit-ticket)。

## スレーブ接続

Adobe Commerceは、複数のデータベースを非同期で読み取ることができます。 Cloud Infrastructure Pro アーキテクチャにデプロイされたCommerce サイトのMySQL データベースに高い負荷が発生する場合は、AdobeでMYSQL スレーブ接続を有効にすることをお勧めします。

MYSQL スレーブ接続を有効にすると、Adobe Commerceはデータベースへの読み取り専用接続を使用して、非マスターノードで読み取り専用トラフィックを受信します。 読み取りと書き込みのトラフィックを処理するノードが1つしかない場合、負荷分散によってパフォーマンスが向上します。

### 影響のあるバージョン

Adobe Commerce オンクラウドインフラストラクチャ、プロアーキテクチャのみ

### 設定

Adobe Commerce on cloud インフラストラクチャでは、[MYSQL_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#mysql_use_slave_connection)変数を設定することで、MYSQL スレーブ接続のデフォルト設定を上書きできます。 この変数を`true`に設定すると、データベースへの読み取り専用接続が自動的に使用されます。

**MySQL スレーブ接続を有効にするには**:

1. ローカル ワークステーションで、プロジェクト ディレクトリに移動します。

1. `.magento.env.yaml` ファイルで、`MYSQL_USE_SLAVE_CONNECTION`をtrueに設定します。

   ```yaml
   stage:
     deploy:
       MYSQL_USE_SLAVE_CONNECTION: true
   ```

1. `.magento.env.yaml` ファイルの変更を確定し、リモート環境にプッシュします。

   デプロイメントが正常に完了すると、クラウド環境でMySQL スレーブ接続が有効になります。
