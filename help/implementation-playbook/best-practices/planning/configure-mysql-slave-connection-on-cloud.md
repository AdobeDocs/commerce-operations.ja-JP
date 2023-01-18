---
title: MySQL スレーブ接続を設定するためのベストプラクティス
description: クラウドインフラストラクチャにデプロイされたAdobe Commerceサイト用の MySQL スレーブ接続を設定する方法を説明します。
role: Developer
feature-set: Commerce
feature: Best Practices
source-git-commit: a5a6e25e3fd303e07a07110b85aa1d460f53cd54
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 0%

---


# MySQL スレーブ接続を設定するためのベストプラクティス

>[!NOTE]
>
>この記事には、人種差別、性差別、または圧迫的なソフトウェア用語が含まれ、読者が傷ついたり、傷ついたり、不快に感じたりする恐れがあるので、まだ業界標準のソフトウェア用語が含まれています。 Adobeは、コード、ドキュメントおよびユーザーエクスペリエンスからこれらの用語を削除する作業を進めています。

クラウドインフラストラクチャ Pro アーキテクチャにデプロイされたAdobe Commerceサイトの場合、Adobeは、デフォルトで、データベースに対して MYSQL スレーブ接続を有効にすることをお勧めします。

Adobe Commerceは、複数のデータベースを非同期で読み取ることができます。  MYSQL スレーブ接続を有効にすると、Adobe Commerceはデータベースへの読み取り専用接続を使用して、非マスターノード上の読み取り専用トラフィックを受け取ります。 読み取り/書き込みトラフィックを処理する必要があるノードは 1 つだけなので、ロードバランシングによるパフォーマンスが向上します。

## 影響を受けるバージョン

クラウドインフラストラクチャ上のAdobe Commerce、Pro アーキテクチャ

## MySQL スレーブ接続の設定

MYSQL スレーブ接続の設定は、 [MYSQL_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#mysql_use_slave_connection) クラウドインフラストラクチャ環境設定ファイルのAdobe Commerceに変数をデプロイする `.magento.env.yaml`. この変数をに設定します。 `true` 接続を有効にします。

MySQL スレーブ接続を有効にするには：

1. の `.magento.env.yaml` ファイルを作成し、 `MYSQL_USE_SLAVE_CONNECTION` が有効になっている。

   ```
   stage:
      deploy:
      MYSQL_USE_SLAVE_CONNECTION: true
   ```

1. 変更をコミットし、環境ブランチにプッシュして更新を展開します。

   デプロイメントが正常に完了すると、クラウドインフラストラクチャで MySQL スレーブ接続が有効になります。

## 追加情報

- [環境変数](https://devdocs.magento.com/cloud/env/variables-intro.html)
- [クラウドインフラストラクチャ上のAdobe Commerceでの MySQL の高負荷ボトルネック](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/database/mysql-high-load-bottleneck-in-magento-commerce-cloud.html?lang=en)
- [クラウドインフラストラクチャ上のAdobe Commerceのデータベースのベストプラクティス](database-on-cloud.md)
