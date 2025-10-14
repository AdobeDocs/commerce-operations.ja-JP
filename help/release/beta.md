---
title: Beta リリース
description: Adobe Commerce ベータ版リリースとリリースへの参加方法について説明します。
exl-id: 662cb061-995f-4e09-a2ef-9e607cc0000b
source-git-commit: a15422e4e135eba01931172960dfb0a6b359cde8
workflow-type: tm+mt
source-wordcount: '728'
ht-degree: 0%

---

# Adobe Commerce ベータ版リリース

Adobe Commerce ベータプログラムを使用すると、マーチャントは、プレリリース機能やコードにアクセスし、フィードバックを提供したり、Adobe Commerceの将来をガイドしたりできます。 ベータ版プログラムには次の 2 種類があります。

- パブリック Beta：パブリックベータ版プログラムは、すべてのAdobe Commerceのお客様とパートナーが利用できます
- Private Beta：プライベートベータプログラムでは、参加条件に基づいて承認が必要になる場合があります

>[!IMPORTANT]
>
>Beta リリースには不具合が含まれている場合があり、いかなる保証もなく「現状のまま」提供されます。 Adobeは、ベータ版リリースの保守、修正、更新、変更、修正、またはその他のサポートをおこなう義務を（Adobe サポートサービスを通じてまたはその他の方法で）負いません。 お客様は、ベータ版リリースおよび/または付属のドキュメントや資料の正しい機能やパフォーマンスに対して、注意を払い、いかなる方法でも依存しないことをお勧めします。 ベータ版の機能と API は、予告なく変更される場合があります。 したがって、ベータ版リリースの使用は、完全にお客様自身の責任で行います。

## 参加のメリット

Adobeが開発中の機能に早期にアクセスすることで、お客様およびパートナーは、フィードバックを提供し、製品開発を具体化し、一般提供が開始される前に新しい機能を導入する準備を整えることができます。

## 現在のBeta プログラム

アクティブなベータプログラムのリストについては、次の節を参照してください。

### Cloud Automation Patching Service （Private Beta）

[Cloud Automation Patching Service](../tools/caps-tool/intro.md) は、クラウドインフラストラクチャー上の [Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/overview) 環境に個別のセキュリティパッチを適用するプロセスを自動化します。

2025 年 10 月に、Cloud Automation パッチ適用サービスのベータ版リリースが [Site-Wide Analysis tool ダッシュボード ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/site-wide-analysis-tool/dashboard) に追加されます。 このサービスは、以下を含む合理化されたパッチ適用ワークフローで、Commerce プロジェクト管理者をサポートします。

- パッチの自動インストール
- ロールバック・リカバリ
- デプロイメント後の検証。

このサービスにより、手動の労力とリスクを最小限に抑えて、安全で安定した、更新された環境を維持できます。

ベータ版には次の機能が含まれています。

- **パッチのインストールを自動化**：環境全体で重要な脆弱性をパッチするプロセスを簡素化し、自動化します。
- **リスクの最小化**：導入後のヘルスチェックおよびロールバック機能により、サイトの停止を防ぎます。

>[!NOTE]
>
>クラウド自動修正パッチサービスは個別のセキュリティパッチを自動的に適用するので、これを使用するには [ 投稿者またはプロジェクト管理者の役割 ](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/project/user-access) が必要です。

このベータ版に参加するには、[Cloud Automation Patching Service - Beta サインアップフォーム ](https://forms.office.com/r/3Wfxj5nPdB) に記入して送信します。

### IBM Sterling Order Management System Integration （Private Beta）

IBMスターリングOrder Management向けのこの統合アクセラレータにより、Adobe Commerceのお客様は、IBMスターリング OMS を活用した高度な注文管理機能を開始できます。 この統合により、マーチャントは次を獲得できます。

- 顧客の在庫レベルと正確な配送日をリアルタイムで可視化します。
- 構成可能なルールに基づいてオーダーの自動ソーシングを実行することで、フルフィルメント・ネットワークと在庫を最適化できます。
- 単一のダッシュボードからチャネル間の注文を一元的に確認できるため、サポートチームは優れたサービスを提供し、例外をすばやく特定して処理できます。
- 返品管理を簡素化するためのテンプレート化された返品管理フロー。

このベータ版に参加するには、[sbieber@adobe.com](mailto:sbieber@adobe.com) にメールでリクエストを送信します。

### Adobe Commerce財団（パブリックAlpha/Beta）

Adobe Commerce Foundation の各アルファ版およびベータ版のリリースには、予定リリース日までにAdobe Commerce コアコードに提供されるすべての変更が含まれています。これには次の機能領域が含まれますが、それに限定されるものではありません。

- 最新のセキュリティ修正
- パフォーマンスの向上
- GraphQLの改善点
- 一般的な品質のバグ修正
- コミュニティの投稿
- [Adobe Commerce サービスとの互換性をサポートするために必要な変更 ](https://experienceleague.adobe.com/en/docs/commerce/user-guides/home)

#### 命名規則とスケジュール

Adobeは通常、アルファ版およびベータ版のパッチを年に数回リリースします。

Alpha リリースパッケージには `-alphaX` サフィックスがあります。 例えば、Adobe Commerce 2.4.7 アルファリリースパッケージでは、次の命名規則を使用します。

- `2.4.7-alpha1`
- `2.4.7-alpha2`

Beta リリースパッケージには `-betaX` サフィックスがあります。 例えば、Adobe Commerce 2.4.7 ベータリリースパッケージでは、次の命名規則を使用します。

- `2.4.7-beta1`
- `2.4.7-beta2`

今後の公開アルファ版およびベータ版のリリース日のリストについては、[ リリーススケジュール ](schedule.md) を参照してください。

#### リリースへのアクセス

Adobe Commerceのアルファ版およびベータ版のリリースは、他のAdobe Commerceのパッチリリースと同じ方法で配布されます。つまり、`https://repo.magento.com` 上の Composer メタパッケージとして配布されます。 ソースコードは [GitHub](https://github.com/magento/magento2) で入手できます。

詳細は、「[Composer インストール クイック スタート ](../installation/composer.md)」を参照してください。

#### 問題レポート

Adobeは、アルファ版およびベータ版のリリースに対して標準のAdobe サポートサービスを提供しません。

アルファ版およびベータ版リリースに関連するフィードバックを送信するには、[GitHub](https://developer.adobe.com/commerce/contributor/guides/code-contributions/) の [ 通常のイシューレポートフロー ](https://github.com/magento/magento2) に従います。

Adobeは、最新のアルファ版またはベータ版のリリースに対して報告されたすべての重要な問題を監視し、GA リリース日より前に解決されるように優先順位を付けます。
