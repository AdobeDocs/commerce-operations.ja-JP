---
title: Beta リリース
description: Adobe Commerce ベータ版リリースとリリースへの参加方法について説明します。
exl-id: 662cb061-995f-4e09-a2ef-9e607cc0000b
source-git-commit: 4643c8392b6d92a2ccbbc2ec5b27d75c112d7521
workflow-type: tm+mt
source-wordcount: '1097'
ht-degree: 0%

---

# Adobe Commerce ベータ版リリース

Adobe Commerce ベータプログラムを使用すると、マーチャントは、プレリリース機能やコードにアクセスし、フィードバックを提供したり、Adobe Commerceの将来をガイドしたりできます。 ベータ版プログラムには次の 2 種類があります。

- パブリック Beta：パブリックベータ版プログラムは、すべてのAdobe Commerceのお客様とパートナーが利用できます
- Private Beta：プライベートベータプログラムでは、参加条件に基づいて承認が必要になる場合があります

>[!IMPORTANT]
>
>Beta リリースには不具合が含まれている場合があり、いかなる保証もなく「現状のまま」提供されます。 Adobeは、ベータ版リリースのメンテナンス、修正、更新、変更、またはその他のサポート（Adobeサポートサービスまたはその他の方法による）を行う義務を負いません。 お客様は、ベータ版リリースおよび/または付属のドキュメントや資料の正しい機能やパフォーマンスに対して、注意を払い、いかなる方法でも依存しないことをお勧めします。 ベータ版の機能と API は、予告なく変更される場合があります。 したがって、ベータ版リリースの使用は、完全にお客様自身の責任で行います。

## 参加のメリット

Adobeが開発中の機能に早期にアクセスすることで、お客様やパートナーは、フィードバックを提供し、製品開発を具体化し、一般提供が開始される前に新しい機能を導入する準備を整えることができます。

## 現在のBeta プログラム

アクティブなベータプログラムのリストについては、次の節を参照してください。

### Live Search （パブリック Beta）の検索機能の強化

このベータ版では、](https://developer.adobe.com/commerce/services/graphql/live-search/product-search/) の 3 つの新しい機能が [`productSearch` クエリでサポートされています。

- **レイヤー検索** – 別の検索コンテキスト内の検索 – この機能を使用すると、検索クエリを最大 2 つのレイヤーで検索できます。 例：

   - **レイヤー 1 検索** – 「product_attribute_1」で「motor」を検索します。
   - **レイヤー 2 検索** – 「product_attribute_2」の「品番 123」を検索します。 この例では、「motor」の結果に含まれる「part number 123」を検索します。

  レイヤー検索は、以下に説明するように、`startsWith` 検索インデックスと `contains` 検索インデックスの両方で使用できます。

- **startsWith 検索インデックス付け** - `startsWith` インデックス付けを使用して検索します。 この新機能により、次のことが可能になります。

   - 属性値が特定の文字列で始まる製品の検索。
   - 「次で終わる」検索の設定による、買い物客での属性値が特定の文字列で終わる製品の検索。 「次で終わる」検索を有効にするには、製品属性を逆に取り込む必要があり、API 呼び出しも逆の文字列にする必要があります。

- **contains search indexation** -contains indexation を使用して属性を検索します。 この新機能により、次のことが可能になります。

   - 大きい文字列内でのクエリの検索。 例えば、買い物客が「HAPE-123」という文字列で製品番号「PE-123」を検索するとします。

      - 注意：この検索タイプは、オートコンプリート検索を実行する既存の [ フレーズ検索 ](https://developer.adobe.com/commerce/services/graphql/live-search/product-search/#phrase) とは異なります。 例えば、製品属性値が「outdoor pants」の場合、フレーズ検索は「out pan」に対する応答を返しますが、「or ants」に対する応答は返しません。 ただし、「を含む」検索では、「または ants」に対する応答が返されます。

これらの新しい条件により、検索クエリのフィルタリングメカニズムが強化され、検索結果を絞り込むことができます。 これらの新しい条件は、メインの検索クエリには影響しません。 ベータ版に参加するには、[commerce-storefront-services](mailto:commerce-storefront-services@adobe.com) にメールリクエストを送信します。

Live Search ベータ版をインストールするには、[Live Search ガイド ](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/install#install-the-live-search-beta) を参照してください。

### CommerceのExperience Manager Assets統合（Private Beta）

Experience Manager AssetsとCommerceの統合により、運用の手間をかけることなく、Experience Manager AssetsからAdobe Commerceに大量の商品画像を効率的に管理および配信できます。

主な機能：

- プラグアンドプレイの統合 – Experience Manager AssetsとAdobe Commerceの間でAdobeを活用した統合を標準で提供し、マーチャントが運用コストを削減して効率を向上させ、最も重要なことに集中できるようにします。

- 大規模な商品画像のパーソナライズ Experience Manager Assetsを使用すると、UI ベースの簡単な編集ツール、Adobe Fireflyを使用したコンテンツの生成機能、アセットの割り当てワークフローによって、パーソナライズされたCommerce エクスペリエンス向けに数百万もの商品バリエーションを生成し、ブランドの一貫性を確保することができます。 適切なアセットが見つかったら、Experience Manager Assets統合を使用してCommerce ストアフロントにシームレスに配信します。

- 簡単なオンボーディング – 設定可能な同期プロセスによって、Experience Manager Assets リポジトリとCommerce カタログ間の完全な同期を可能にし、マーチャントのオンボーディングを簡素化します。

- 柔軟なマッチング戦略 – この統合には、AEM AssetsとCommerceの間で画像を同期させる製品 SKU に基づくデフォルトのアセットマッチングアルゴリズムが含まれており、Adobe Developer App Builderを使用して拡張できます。 ソリューションパートナーと協力して、統合の上にカスタムアセットマッチング戦略を構築し、アセット管理リポジトリ構造に対応します。

ベータ版に参加するには、[Shaun McCran](mailto:mccran@adobe.com) にメールでリクエストを送信します。

### IBM Sterling Order Management System Integration （Private Beta）

IBMスターリングOrder Management向けのこの統合アクセラレータにより、Adobe Commerceのお客様は、IBMスターリング OMS を活用した高度な注文管理機能を開始できます。 この統合により、マーチャントは次を獲得できます。

- 顧客の在庫レベルと正確な配送日をリアルタイムで可視化します。
- 構成可能なルールに基づいてオーダーの自動ソーシングを実行することで、フルフィルメント・ネットワークと在庫を最適化できます。
- 単一のダッシュボードからチャネル間の注文を一元的に確認できるため、サポートチームは優れたサービスを提供し、例外をすばやく特定して処理できます。
- 返品管理を簡素化するためのテンプレート化された返品管理フロー。

このベータ版に参加するには、[sbieber@adobe.com](mailto:sbieber@adobe.com) にメールでリクエストを送信します。

### データ接続およびAudience Activation（パブリック Beta）

Adobe CommerceとAdobe Experience Platform間のデータ共有を拡張し、より強力でパーソナライズされたエクスペリエンスを促進しました。 この機能により、マーチャントは次のことが可能になります。

- Commerce顧客プロファイルの共有
- カスタム属性の作成

このベータ版に参加するには、[DataConnection@adobe.com](mailto:DataConnection@adobe.com) にメールでリクエストを送信します。

### Adobe Commerce財団（パブリックBeta）

各Adobe Commerce Foundation ベータ版リリースには、予定リリース日までにAdobe Commerce コアコードに提供されるすべての変更が含まれます。以下の機能領域が含まれますが、それに限定されるものではありません。

- 最新のセキュリティ修正
- パフォーマンスの向上
- GraphQLの改善点
- 一般的な品質のバグ修正
- コミュニティの投稿
- [Adobe Commerce サービスとの互換性をサポートするために必要な変更 ](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/home.html)

#### 命名規則とスケジュール

Adobeは通常、ベータ版パッチを年に 2 回リリースします。

Beta リリースパッケージには `-betaX` サフィックスがあります。 例えば、Adobe Commerce 2.4.7 ベータリリースパッケージでは、次の命名規則を使用します。

- `2.4.7-beta1`
- `2.4.7-beta2`

今後の公開ベータ版リリース日のリストについては、[ リリーススケジュール ](schedule.md) を参照してください。


#### Beta リリースアクセス

Adobe Commerce ベータ版リリースは、他のAdobe Commerce パッチリリースと同じ方法で配布されます。つまり、`https://repo.magento.com` 上の Composer メタパッケージとして配布されます。 ソースコードは [GitHub](https://github.com/magento/magento2) で入手できます。

詳細は、「[Composer インストール クイック スタート ](../installation/composer.md)」を参照してください。

#### 問題レポート

Adobeでは、ベータ版リリースに対する標準のAdobeサポートサービスを提供していません。

ベータ版リリースに関するフィードバックを送信するには、[GitHub](https://github.com/magento/magento2) の [ 通常のイシューレポートフロー ](https://developer.adobe.com/commerce/contributor/guides/code-contributions/) に従ってください。

社内チームは、最新のベータ版リリースに関して報告されたすべての重要な問題を監視し、GA リリース日より前に解決するように優先順位を付けます。
