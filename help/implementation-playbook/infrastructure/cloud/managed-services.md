---
title: Managed Services
description: クラウドインフラストラクチャの実装に関するAdobe Commerceに対する、AdobeManaged Services、お客様、クラウドサービスプロバイダーの責任を確認します。
exl-id: b1442e31-06f4-4aa6-b24a-b6cda630d52f
feature: Cloud, Services
source-git-commit: 7c2e2bdabf47e1367ffb6761230d3d43f0f9d0cf
workflow-type: tm+mt
source-wordcount: '521'
ht-degree: 0%

---

# Managed Services

Adobe Commerce on cloud infrastructure managed services は、デフォルトでセキュリティで保護されています。

![Adobe Commerce Managed Services を示す図](../../../assets/playbooks/managed-services.svg)

## 共有された責任

Adobe Commerce Pro は、共有責任セキュリティモデルに依存する予定です。 このモデルでは、異なる当事者は、システムのセキュリティを維持するための責任の領域が異なります。 このアプローチにより、優れたクラウドテクノロジーを柔軟に使用し、使い勝手を向上させることができます。

![Adobe Commerce共有職責モデルを示す図](../../../assets/playbooks/shared-responsibility.svg)

### AdobeManaged Servicesの責務

AdobeManaged Servicesは、Adobe Commerce Pro クラウド環境、コアAdobe Commerce Pro アプリケーションコード、および内部コマースシステムのセキュリティと可用性を担当します。 これには以下が含まれますが、これらに限定されません。

- サーバレベルのパッチ適用
- Adobe Commerce Pro プランの提供に必要なサービスの運用
- 脆弱性テスト
- セキュリティイベントのログと監視
- インシデント管理
- 運用監視
- 24/7サポート
- SLA に従って顧客インフラストラクチャが利用可能であることの確認

AdobeManaged Servicesは、サーバーファイアウォール設定 (iptables) および境界ファイアウォール設定（セキュリティグループ）の管理も担当します。 Adobeは、コアアプリケーションのセキュリティアップデートを定期的にリリースする場合もあります。 これらのパッチを適用するのは、お客様の責任です。 これらの領域はすべて、クラウドインフラストラクチャシステム上のAdobe Commerceの PCI 認定によってカバーされます。

### AWSの責任

AdobeManaged Servicesは、クラウドサーバーインフラストラクチャにAmazon Web Services(AWS) を使用します。 AWSは、ファイアウォールシステムや侵入検出システム (IDS) を介したルーティング、スイッチング、境界ネットワークセキュリティを含む、ネットワークのセキュリティを担当します。 AWSは、Adobe Commerceクラウド環境を管理するデータセンターに対する物理的なセキュリティと、適切な電力、冷却、メカニズムの制御を確実におこなう環境セキュリティを担当します。

Adobe Commerce Pro プランでは、次を使用します。

- Amazon Elastic Compute Cloud (EC2)
- Amazon Simple Storage Service(S3)
- Amazon Elastic Block Store (EBS)
- Amazon Virtual Private Cloud (VPC)
- Amazon Elastic Load Balancer(ELB)
- Amazon Cloud Trail Services を参照してください。

Amazonは、PCI DSS、SOC 2、ISO 27001認定を含む広範なコンプライアンスプログラムを提供しています。

### ソリューションパートナー/お客様の責任

お客様は、主に、Adobe Commerce Pro プランクラウド環境で実行されるAdobe Commerceアプリケーションのカスタマイズされた実装のセキュリティに責任を負います。 これには以下が含まれます。

- 侵入テストや定期的な脆弱性スキャンを含む、アプリケーションとセキュリティ監視アクティビティの安全な設定とコーディングを確保します。

- システムで使用されるカスタマイズ、拡張機能、他のアプリケーション、統合のセキュリティ。

- ユーザーのセキュリティと、設定およびアプリケーションへのアクセス権の付与。

- お客様が、実稼動環境以外へのすべてのコードデプロイメントを制御します。 また、この制御には、コアAdobe Commerceアプリケーション、拡張機能、またはカスタムコードにアプリケーションセキュリティパッチを適用する責任も伴います。

- お客様は、カスタマイズしたアプリケーションの侵入テストを実施する必要があります。 これらの責任は、お客様、実装パートナー、またはAdobe Commerce Professional Services の技術リソースによって対処できます。

- お客様は、カスタマイズされたアプリケーションと独自のプロセスの PCI 要件に対して責任を負います。 お客様の PCI コンプライアンスは、レビューが必要な領域を最小限に抑えるために、AWSとAdobe Commerceの PCI 認定に基づいて構築されています。
