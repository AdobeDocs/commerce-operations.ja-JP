---
title: クラウドインフラストラクチャ環境
description: 適切な使用例に対して適切な環境を使用する。
exl-id: 0c36145f-8de2-45e5-9050-9acbc9fb6100
feature: Cloud
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 0%

---

# 環境

Adobe Commerce on cloud infrastructure Pro アーキテクチャは、ストアの開発、テスト、起動に使用できる環境をサポートします。 各環境には、データベースと Web サーバーが含まれます。 Adobe Commerceで利用される 4 つの環境は、次のとおりです。

- **統合**-1 つの環境ブランチを提供し、最大 4 つの環境ブランチを追加で作成できます。 これにより、Platform-as-a-Service(PaaS) コンテナにデプロイされるアクティブなブランチを最大で 5 つ作成できます。

- **ステージング** — 専用の Infrastructure-as-a-S(IaaS) コンテナに展開される 1 つの環境ブランチを提供します。

- **実稼動** — 専用の Infrastructure-as-a-S(IaaS) コンテナに展開される 1 つの環境ブランチを提供します。

- **グローバルマスター**— Platform-as-a-Service(PaaS) コンテナにデプロイされる master ブランチを提供します。

![Adobe Commerceクラウド環境間の関係を示す図](../../../assets/playbooks/environment-diagram.svg)

## Git ブランチ

統合環境は、Platform-as-a-Service(PaaS) コンテナにデプロイされたAdobe Commerceコードを含む、単一のベース統合ブランチを提供します。

クラウドインフラストラクチャ環境のAdobe Commerceは、柔軟で継続的な統合プロセスをサポートしています。 最初に、ローカルプロジェクトフォルダーに統合ブランチを複製します。 新しいブランチ（複数のブランチ）を作成して、新しい機能の開発、変更の設定、拡張機能の追加をおこないます。 開発されたコードブランチと対応する設定ファイルがあれば、コードの変更を統合ブランチにマージして、より包括的なテストをおこなう準備が整います。

![Adobe Commerceクラウド環境の Git ベースの分岐戦略を示す図](../../../assets/playbooks/branching-diagram.svg)
