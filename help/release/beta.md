---
title: ベータ版リリース
description: Adobe Commerce ベータ版リリースとリリースへの参加方法について説明します。
exl-id: 662cb061-995f-4e09-a2ef-9e607cc0000b
source-git-commit: d761bd089fbd2046e993d4652e9e0e2b3c4d2777
workflow-type: tm+mt
source-wordcount: '596'
ht-degree: 0%

---

# Adobe Commerce ベータ版リリース

Adobe Commerce ベータプログラムを使用すると、マーチャントは、プレリリース機能やコードにアクセスし、フィードバックを提供したり、Adobe Commerceの将来をガイドしたりできます。 ベータ版プログラムには次の 2 種類があります。

- パブリックベータ版：パブリックベータ版プログラムは、すべてのAdobe Commerce顧客およびパートナーが利用できます
- プライベートベータ版：プライベートベータ版プログラムに参加するには、選定基準に基づいて承認が必要になる場合があります

>[!IMPORTANT]
>
>ベータ版リリースには欠陥が含まれている場合があり、いかなる保証もなく「現状のまま」提供されます。 Adobeは、ベータ版リリースのメンテナンス、修正、更新、変更、またはその他のサポート（Adobeサポートサービスまたはその他の方法による）を行う義務を負いません。 お客様は、ベータ版リリースおよび/または付属のドキュメントや資料の正しい機能やパフォーマンスに対して、注意を払い、いかなる方法でも依存しないことをお勧めします。 ベータ版の機能と API は、予告なく変更される場合があります。 したがって、ベータ版リリースの使用は、完全にお客様自身の責任で行います。

## 参加のメリット

Adobeが開発中の機能に早期にアクセスすることで、お客様やパートナーは、フィードバックを提供し、製品開発を具体化し、一般提供が開始される前に新しい機能を導入する準備を整えることができます。

## 現在のベータ版プログラム

アクティブなベータプログラムのリストについては、次の節を参照してください。

### IBM Sterling Order Management System Integration （プライベートベータ版）

このIBM Sterling Order Management 用の統合アクセラレータにより、Adobe Commerceのお客様は、IBM Sterling OMS を活用した高度な注文管理機能を開始できます。 この統合により、マーチャントは次を獲得できます。
- 顧客の在庫レベルと正確な配送日をリアルタイムで可視化します。
- 構成可能なルールに基づいてオーダーの自動ソーシングを実行することで、フルフィルメント・ネットワークと在庫を最適化できます。
- 単一のダッシュボードからチャネル間の注文を一元的に確認できるため、サポートチームは優れたサービスを提供し、例外をすばやく特定して処理できます。
- 返品管理を簡素化するためのテンプレート化された返品管理フロー。

このベータ版に参加するには、次のアドレスにメールでリクエストを送信します： [sbieber@adobe.com](mailto:sbieber@adobe.com).

### データ接続とAudience Activation（パブリックベータ版）

Adobe CommerceとAdobe Experience Platform間のデータ共有を拡張し、より強力でパーソナライズされたエクスペリエンスを促進しました。 この機能により、マーチャントは次のことが可能になります。
- Commerce顧客プロファイルの共有
- カスタム属性の作成
- Real-Time CDPとAdobe Journey OptimizerでCommerceのインサイトを取得
- 複数のデータセットとデータストリームのサポート

このベータ版に参加するには、次のアドレスにメールでリクエストを送信します： [DataConnection@adobe.com](mailto:DataConnection@adobe.com).

### Adobe Commerce Foundation （パブリックベータ版）

各Adobe Commerce Foundation ベータ版リリースには、予定リリース日までにAdobe Commerce コアコードに提供されるすべての変更が含まれます。以下の機能領域が含まれますが、それに限定されるものではありません。

- 最新のセキュリティ修正
- パフォーマンスの向上
- GraphQLの改善点
- 一般的な品質のバグ修正
- コミュニティの投稿
- との互換性をサポートするために必要な変更 [Adobe Commerce サービス](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/home.html)

#### 命名規則とスケジュール

Adobeは通常、ベータ版パッチを年に 2 回リリースします。

ベータ版リリースパッケージには、 `-betaX` サフィックス。 例えば、Adobe Commerce 2.4.7 ベータリリースパッケージでは、次の命名規則を使用します。

- `2.4.7-beta1`
- `2.4.7-beta2`

を参照してください。 [リリーススケジュール](schedule.md) 今後のパブリックベータ版リリース日のリストについては、こちらを参照してください。


#### ベータ版リリースへのアクセス

Adobe Commerce ベータ版リリースは、他のAdobe Commerce パッチ リリースと同じ方法で配布されます。Composer メタパッケージとして `https://repo.magento.com`. ソースコードは、次の場所で入手できます [GitHub](https://github.com/magento/magento2).

参照： [Composer インストール クイック スタート](../installation/composer.md) を参照してください。

#### 問題レポート

Adobeでは、ベータ版リリースに対する標準のAdobeサポートサービスを提供していません。

ベータ版リリースに関連するフィードバックを送信するには、次に従います [通常のイシューレポートフロー](https://developer.adobe.com/commerce/contributor/guides/code-contributions/) 日付： [GitHub](https://github.com/magento/magento2).

社内チームは、最新のベータ版リリースに関して報告されたすべての重要な問題を監視し、GA リリース日より前に解決するように優先順位を付けます。
