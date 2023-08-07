---
title: MySQL スレーブ接続を設定するためのベストプラクティス
description: クラウドインフラストラクチャにデプロイされたAdobe Commerceサイト用の MySQL スレーブ接続を設定する方法を説明します。
role: Developer
feature: Best Practices
exl-id: d65bc80a-c4ec-4ea4-aff1-110592838201
source-git-commit: 3532480e2172c39ceb4ec55c9819d5271fd1fcdb
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 0%

---

# MySQL スレーブ接続を設定するためのベストプラクティス

>[!NOTE]
>
>この記事には、人種差別、性差別、または圧迫的なソフトウェア用語が含まれ、読者が傷ついたり、心に傷を負ったり、歓迎されないと感じる場合があります。 Adobeは、コード、ドキュメントおよびユーザーエクスペリエンスからこれらの用語を削除する作業を進めています。

Adobe Commerceは、複数のデータベースを非同期で読み取ることができます。 クラウドインフラストラクチャ Pro アーキテクチャにデプロイされたコマースサイトの MySQL データベースの負荷が高くなると予想される場合、Adobeは MYSQL スレーブ接続を有効にすることをお勧めします。

MYSQL スレーブ接続を有効にすると、Adobe Commerceはデータベースへの読み取り専用接続を使用して、非マスターノード上の読み取り専用トラフィックを受け取ります。 読み取り/書き込みトラフィックを処理するノードが 1 つだけの場合、ロードバランシングを通じてパフォーマンスが向上します。

## 影響を受けるバージョン

クラウドインフラストラクチャ上のAdobe Commerce、Pro アーキテクチャのみ

## MySQL スレーブ接続の設定

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

## 追加情報

既存のコマース設定をで上書きして、クラウド環境のカスタマイズについて詳しく説明します。 [環境変数](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html#environment-variables) （内） _Adobe Commerce on cloud infrastructure guide_.

詳しくは、 [クラウドインフラストラクチャ上のAdobe Commerceでの MySQL の高負荷ボトルネック](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/database/mysql-high-load-bottleneck-in-magento-commerce-cloud.html) 記事内の _サポートナレッジベース_.
