---
title: Beta リリース
description: Adobe Commerce ベータ版リリースとリリースへの参加方法について説明します。
exl-id: 662cb061-995f-4e09-a2ef-9e607cc0000b
source-git-commit: 1c0dd720df944a5784c850a3f4ea63b8984069f1
workflow-type: tm+mt
source-wordcount: '963'
ht-degree: 0%

---

# Adobe Commerce ベータ版リリース

Adobe Commerce ベータプログラムを使用すると、マーチャントは、プレリリース機能やコードにアクセスし、フィードバックを提供したり、Adobe Commerceの将来をガイドしたりできます。 ベータ版プログラムには次の 2 種類があります。

- パブリック Beta：パブリックベータ版プログラムは、すべてのAdobe Commerceのお客様とパートナーが利用できます
- Private Beta：プライベートベータプログラムでは、参加条件に基づいて承認が必要になる場合があります

>[!IMPORTANT]
>
>Beta リリースには不具合が含まれている場合があり、いかなる保証もなく「現状のまま」提供されます。 Adobeは、ベータ版リリースのメンテナンス、修正、更新、変更、またはその他のサポートをおこなう義務を（Adobe サポートサービスを通じてまたはその他の方法で）負いません。 お客様は、ベータ版リリースおよび/または付属のドキュメントや資料の正しい機能やパフォーマンスに対して、注意を払い、いかなる方法でも依存しないことをお勧めします。 ベータ版の機能と API は、予告なく変更される場合があります。 したがって、ベータ版リリースの使用は、完全にお客様自身の責任で行います。

## 参加のメリット

Adobeが開発中の機能に早期にアクセスすることで、お客様およびパートナーは、フィードバックを提供し、製品開発を具体化し、一般提供が開始される前に新しい機能を導入する準備を整えることができます。

## 現在のBeta プログラム

アクティブなベータプログラムのリストについては、次の節を参照してください。

### Adobe Commerce Optimizer

Adobe Commerce Optimizerは、高性能なストアフロントにより e コマースのエクスペリエンスを強化し、オーガニックトラフィック、カスタマーエンゲージメント、売上高を向上させます。

Adobe Commerce Optimizerを使用すると、次のことができます。

- コマーススタック全体を再プラットフォームすることなく、カタログを拡張および拡大します。
- 任意のソースからカタログデータを取り込みます。
- ビジネスチャネルとポリシーを定義します。
- AI と ML を使用して、パーソナライズされた検索とレコメンデーションを作成します。
- 正確な実装とトラブルシューティングのために、同期ステータスやストアフロントのイベントデータなど、重要な製品データの可用性を表示します。

Adobe Commerce Optimizerについて [ 詳細情報 ](https://experienceleague.adobe.com/docs/commerce/optimizer/overview.html) します。 早期アクセスプログラムの詳細については、[!DNL Adobe Commerce Optimizer] 早期アクセス申請フォーム [ にご記入ください ](https://forms.office.com/Pages/ResponsePage.aspx?id=Wht7-jR7h0OUrtLBeN7O4WOxhjY2doZPikS2hIbfmL5UMlhTMTYzVDhPQVFNTUFYUjJHNlRKTE5TWS4u)。

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

Live Search ベータ版をインストールするには、[Live Search ガイド ](https://experienceleague.adobe.com/en/docs/commerce/live-search/install#install-the-live-search-beta) を参照してください。

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

アルファ版およびベータ版リリースに関連するフィードバックを送信するには、[GitHub](https://github.com/magento/magento2) の [ 通常のイシューレポートフロー ](https://developer.adobe.com/commerce/contributor/guides/code-contributions/) に従います。

Adobeは、最新のアルファ版またはベータ版のリリースに対して報告されたすべての重要な問題を監視し、GA リリース日より前に解決されるように優先順位を付けます。
