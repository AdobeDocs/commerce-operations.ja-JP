---
title: MySQL スレーブ接続を設定するためのベストプラクティス
description: クラウドインフラストラクチャにデプロイされたAdobe Commerceサイト用の MySQL スレーブ接続を設定する方法を説明します。
role: Developer
feature-set: Commerce
feature: Best Practices
source-git-commit: cb86772e9ceabc580ec32ad6ae1206a71ea03946
workflow-type: tm+mt
source-wordcount: '313'
ht-degree: 0%

---


# MySQL スレーブ接続を設定するためのベストプラクティス

>[!NOTE]
>
>この記事には、人種差別、性差別、または圧迫的なソフトウェア用語が含まれ、読者が傷ついたり、心に傷を負ったり、歓迎されないと感じる場合があります。 Adobeは、コード、ドキュメントおよびユーザーエクスペリエンスからこれらの用語を削除する作業を進めています。

クラウドインフラストラクチャ Pro アーキテクチャにデプロイされたAdobe Commerceサイトの場合、Adobeは、デフォルトで、データベースに対して MYSQL スレーブ接続を有効にすることをお勧めします。

Adobe Commerceは、複数のデータベースを非同期で読み取ることができます。 MYSQL スレーブ接続を有効にすると、Adobe Commerceはデータベースへの読み取り専用接続を使用して、非マスターノード上の読み取り専用トラフィックを受け取ります。 読み取り/書き込みトラフィックを処理するノードが 1 つだけの場合、ロードバランシングを通じてパフォーマンスが向上します。

## 影響を受けるバージョン

クラウドインフラストラクチャ上のAdobe Commerce、Pro アーキテクチャ

## MySQL スレーブ接続の設定

クラウドインフラストラクチャ上のAdobe Commerceで、MYSQL スレーブ接続のデフォルト設定を上書きするには、 [MYSQL_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#mysql_use_slave_connection) 変数を使用します。 データベースへの読み取り専用接続を自動的に使用するには、この変数を true に設定します。

**MySQL スレーブ接続を有効にするには**:

1. ローカルワークステーションで、プロジェクトディレクトリに移動します。

1. 内 `.magento.env.yaml` ファイル、 `MYSQL_USE_SLAVE_CONNECTION` を true に設定します。

   ```
   stage:
     deploy:
       MYSQL_USE_SLAVE_CONNECTION: true
   ```

1. のコミット `.magento.env.yaml` ファイルを変更し、リモート環境にプッシュします。

   デプロイメントが正常に完了すると、クラウド環境で MySQL スレーブ接続が有効になります。

既存のコマース設定をで上書きして、クラウド環境のカスタマイズについて詳しく説明します。 [環境変数](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html#environment-variables) 内 _Adobe Commerce on cloud infrastructure guide_.

## 追加情報

- [クラウドインフラストラクチャ上のAdobe Commerceでの MySQL の高負荷ボトルネック](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/database/mysql-high-load-bottleneck-in-magento-commerce-cloud.html?lang=en)
- [クラウドインフラストラクチャ上のAdobe Commerceのデータベースのベストプラクティス](database-on-cloud.md)
