---
title: MySQL スレーブ接続を設定するためのベストプラクティス
description: クラウドインフラストラクチャにデプロイされたAdobe Commerceサイト用の MySQL スレーブ接続を設定する方法を説明します。
role: Developer
feature-set: Commerce
feature: Best Practices
source-git-commit: 48c5666ee9b83bbf8a5c6375ec53762d918bcece
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 0%

---


# MySQL スレーブ接続を設定するためのベストプラクティス

クラウドインフラストラクチャ Pro アーキテクチャにデプロイされたAdobe Commerceサイトの場合、Adobeは、デフォルトで、データベースに対して MYSQL スレーブ接続を有効にすることをお勧めします。

Adobe Commerceは、複数のデータベースを非同期で読み取ることができます。  MYSQL スレーブ接続を有効にすると、Adobe Commerceはデータベースへの読み取り専用接続を使用して、非マスターノード上の読み取り専用トラフィックを受け取ります。 読み取り/書き込みトラフィックを処理する必要があるノードは 1 つだけなので、ロードバランシングによるパフォーマンスが向上します。

## 影響を受けるバージョン

クラウドインフラストラクチャ上のAdobe Commerce、Pro アーキテクチャ

## MySQL スレーブ接続の設定

MYSQL スレーブ接続の設定は、 [MYSQL_SLAVE_CONNECTION](https://devdocs.magento.com/cloud/env/variables-deploy.html#mysql_use_slave_connection) クラウドインフラストラクチャ環境設定ファイルのAdobe Commerceに変数をデプロイする `.magento.env.yaml`. この変数をに設定します。 `true` 接続を有効にします。

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

>!![NOTE]
この記事には、人種差別、性差別、または圧制的なソフトウェア用語が含まれ、読者に傷つき、傷つき、傷つき、または歓迎されないと感じさせる可能性があるので、私たちは認識しています。 Adobeは、コード、ドキュメントおよびユーザーエクスペリエンスからこれらの用語を削除する作業を進めています。
