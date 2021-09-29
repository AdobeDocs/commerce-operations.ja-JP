---
title: クラウドインフラストラクチャ環境
description: 適切な使用例に適した環境を使用する。
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 0%

---


# 環境

クラウドインフラストラクチャのAdobeコマース Pro アーキテクチャは、ストアの開発、テスト、起動に使用できる環境をサポートします。 各環境には、データベースと Web サーバーが含まれます。 Experience Commerce で利用される 4 つのAdobeは、次のとおりです。

- **統合** - 1 つの環境ブランチを提供し、最大 4 つの追加の環境ブランチを作成できます。これにより、Platform-as-a-Service(PaaS) コンテナにデプロイできるアクティブなブランチを最大 5 つに制限できます。

- **ステージング**：専用の Infrastructure-as-a-S(IaaS) コンテナに展開される単一の環境ブランチを提供します。

- **本番**：専用の Infrastructure-as-a-Service(IaaS) コンテナに展開される 1 つの環境ブランチを提供します。

- **グローバルマスター**:Platform-as-a-Service(PaaS) コンテナに展開されるマスターブランチを提供します。

![Commerce クラウド環境間の関係を示すAdobe図](../../../assets/playbooks/environment-diagram.svg)

## Git ブランチ

統合環境は、Platform-as-a-Service(PaaS) コンテナにデプロイされたAdobeコマースコードを含む、単一のベース統合ブランチを提供します。

クラウドインフラストラクチャ環境でのAdobeコマースは、柔軟で継続的な統合プロセスをサポートします。 最初に、統合ブランチをローカルプロジェクトフォルダーにクローンします。 新しいブランチ（複数のブランチ）を作成して、新しい機能の開発、変更の設定、拡張機能の追加を行います。 開発済みのコードブランチと対応する設定ファイルがあれば、コードの変更を統合ブランチにマージして、より包括的なテストをおこなう準備が整います。

![Git ベースの分岐戦略を示す図 (AdobeCommerce クラウド環境用 )](../../../assets/playbooks/branching-diagram.svg)
