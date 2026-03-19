---
title: Beta リリース
description: Adobe Commerce ベータ版リリースとリリースへの参加方法について説明します。
exl-id: 662cb061-995f-4e09-a2ef-9e607cc0000b
badgePaas: label="Paa" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Adobe Commerce on Cloud プロジェクト（Adobeが管理する PaaS インフラストラクチャ）およびオンプレミスプロジェクトにのみ適用されます。"
badgeSaas: label="SaaS" type="Positive" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Adobe Commerce as a Cloud ServiceおよびAdobe Commerce Optimizer プロジェクトにのみ適用されます（Adobeで管理される SaaS インフラストラクチャ）。"
source-git-commit: 7265cb40541f3e5a1c416094b3759f9b750153cf
workflow-type: tm+mt
source-wordcount: '1347'
ht-degree: 0%

---

# Adobe Commerce ベータ版リリース

Adobe Commerce ベータプログラムを使用すると、マーチャントは、プレリリース機能やコードにアクセスし、フィードバックを提供したり、Adobe Commerceの将来をガイドしたりできます。 ベータ版プログラムには次の 2 種類があります。

- パブリック Beta：パブリックベータ版プログラムは、すべてのAdobe Commerceのお客様とパートナーが利用できます
- Private Beta：プライベートベータプログラムでは、参加条件に基づいて承認が必要になる場合があります

>[!IMPORTANT]
>
>**免責事項**<br/>
>Beta リリースには、不具合が含まれている可能性のあるプレリリース機能およびコードが含まれており、「現状のまま」でいかなる保証もなく提供されています。 ベータ版リリースを一般公開するかどうかは、Adobeが単独で決定します。 Adobeは、特定の日付までにかかるベータ版リリースの保守、修正、更新、変更、修正、サポート（Adobe サポートサービス経由を含む）または配信について、一切の義務を負いません。 ベータ版のリリースが一般公開された場合、該当する料金を含む追加の利用条件が適用される場合があります。 Betaのリリースは、予告なく変更される場合があります（廃止を含む）。 お客様は、ベータ版リリースの機能やパフォーマンスについて、中断やエラーがないことに対して注意を払い、いかなる形でも依存しないことをお勧めします。  したがって、ベータ版リリースの使用は、完全にお客様自身の責任で行います。

## 参加のメリット

Adobeが開発中の機能に早期にアクセスすることで、お客様およびパートナーは、フィードバックを提供し、製品開発を具体化し、一般提供が開始される前に新しい機能を導入する準備を整えることができます。

## 現在のBeta プログラム

アクティブなベータプログラムのリストについては、次の節を参照してください。

### グローバルおよびカタログ表示ごとのマーチャンダイジングルール（パブリック Beta）

[!BADGE SaaS のみ &#x200B;]{type=Positive url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Adobe Commerce as a Cloud ServiceおよびAdobe Commerce Optimizer プロジェクトにのみ適用されます（Adobeで管理される SaaS インフラストラクチャ）。"}

Adobe Commerce Optimizerでは、柔軟な範囲でマーチャンダイジングルールを定義する機能が導入されました。これにより、マーチャントは、すべてのカタログビューをまたいでルールを適用したり、特定のカタログビューにルールをスコープ設定したりできます。 この機能により、複数のストアフロント、ブランドまたは言語を操作するマーチャントに対するマーチャンダイジングルールの管理が簡素化されます。 カタログビュー固有のルールを使用すると、マーチャントは、ローカライズされたエクスペリエンスやブランド固有のエクスペリエンスが必要な場合に、検索結果やマーチャンダイジングロジックを個々のチャネルに合わせてカスタマイズできます。 カタログビュー固有のルールが存在する場合は、そのビューのグローバルルールが上書きされるので、効率的な設定管理を維持しながら正確に制御できます。

**主なメリット**

- すべてのカタログビューでマーチャンダイジングルールをグローバルに定義します。
- ローカライズされたエクスペリエンスが必要な場合に、特定のカタログビューのルールを上書きします。
- ストアフロント間での設定の重複を減らします。
- マルチブランドおよび多言語コマース実装のスケーラビリティを向上させます。

この機能により、マーチャンダイジングの柔軟性と運用効率が向上し、マーチャントがより関連性の高い製品検出エクスペリエンスを大規模に提供できるようになります。 詳しくは、「[&#x200B; マーチャンダイジングルール &#x200B;](https://experienceleague.adobe.com/en/docs/commerce/optimizer/merchandising/rules/add)」を参照してください。

>[!NOTE]
>
>Betaの参加者は、新しいカタログビューの範囲を活用するために、既存のマーチャンダイジングルールを再作成する必要があります。

このベータ版機能を使用する際にフィードバックを共有するには、[commerce-storefront-services@adobe.com](mailto:commerce-storefront-services@adobe.com) にメールを送信してください。

### グローバルおよびカタログ表示ごとの商品レコメンデーション（パブリック Beta）

[!BADGE SaaS のみ &#x200B;]{type=Positive url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Adobe Commerce as a Cloud ServiceおよびAdobe Commerce Optimizer プロジェクトにのみ適用されます（Adobeで管理される SaaS インフラストラクチャ）。"}

Adobe Commerce Optimizerでは、Product Recommendations 設定の制御が強化され、マーチャントは、すべてのカタログビューをまたいでグローバルに、または個々のカタログビューに合わせてレコメンデーションユニットを定義できるようになりました。

この機能により、複数のストアフロント、ブランド、地域または言語を運用する企業のレコメンデーション管理が簡素化されます。 マーチャントは、グローバルに 1 回レコメンデーションユニットを作成でき、すべてのカタログビューに適用されるので、チャネル間で一貫した製品検出戦略を確保できます。 同時に、カタログビュー固有のレコメンデーションユニットを使用すると、マーチャントは必要に応じて特定のストアフロント用にエクスペリエンスをカスタマイズできます。

ストアフロントのエンゲージメントイベントとレコメンデーション指標は、カタログ表示レベルで追跡され、様々なストアフロントでの買い物客の行動に関するより正確なインサイトを提供します。

**主なメリット**

- すべてのカタログビューで製品のレコメンデーションユニットをグローバルに設定する。
- ローカライズされたストアフロントエクスペリエンスについては、カタログビュー固有のレコメンデーションを作成します。
- マルチブランドまたは多言語のストアフロント間で重複する設定を減らします。
- カタログビュー別に追跡される指標とイベントを使用して、より正確なインサイトを得ます。

この機能強化により、マーチャントは複雑なコマース環境全体でレコメンデーションの管理を簡素化しながら、より関連性の高い製品検出エクスペリエンスを提供できるようになります。 詳しくは、[recommendations](https://experienceleague.adobe.com/en/docs/commerce/optimizer/manage-results/recommendation-performance) を参照してください。

>[!NOTE]
>
>Betaの参加者は、新しいカタログビューの範囲を活用するために、既存のレコメンデーションユニットを再作成する必要があります。

このベータ版機能を使用する際にフィードバックを共有するには、[commerce-storefront-services@adobe.com](mailto:commerce-storefront-services@adobe.com) にメールを送信してください。

### セマンティック検索：よりスマートなコンテキスト対応のショッピングエクスペリエンス（Private Beta）

[!BADGE SaaS のみ &#x200B;]{type=Positive url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Adobe Commerce as a Cloud ServiceおよびAdobe Commerce Optimizer プロジェクトにのみ適用されます（Adobeで管理される SaaS インフラストラクチャ）。"}

セマンティック検索は、正確な単語だけでなく、買い物客のクエリの背後にある *意味* を理解する e コマース検索テクノロジーです。 クエリに不慣れな用語やスペルミスのある用語が含まれる場合に失敗することが多い従来のキーワードベースの検索とは異なり、この AI を活用したアプローチは、自然言語処理（NLP）とコンテキストを使用して意図を解釈し、より関連性の高い結果を提供します。

このテクノロジーは、従来の検索における主な制限に対応しています。つまり、買い物客がカタログに存在しない単語を使用した場合に発生する結果がゼロのページです。 AI を活用した手法を使用して、ユーザークエリと製品データを共有された意味空間にマッピングします。 例えば、「ランニングシューズ」と「ジョギングスニーカー」が同じタイプの製品を参照していることをシステムが認識し、次のことが可能になります。

- 同義語認識
- コンテキスト関連度
- あいまいなクエリ、スペルミスのクエリ、複合クエリのインテリジェントな処理
- 自然言語および会話言語の理解

ベータ版プログラムへの招待をリクエストするには、[commerce-storefront-services@adobe.com](mailto:commerce-storefront-services@adobe.com) にメールを送信します。 Adobe チームは、次のステップと実施要件で対応します。

### Cloud Automation Patching Service （Private Beta）

[!BADGE PaaS のみ &#x200B;]{type=Informative url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Adobe Commerce on Cloud プロジェクト（Adobeが管理する PaaS インフラストラクチャ）およびオンプレミスプロジェクトにのみ適用されます。"}

[Cloud Automation Patching Service](../tools/caps-tool/intro.md) は、クラウドインフラストラクチャー上の [Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/overview) 環境に個別のセキュリティパッチを適用するプロセスを自動化します。

2025 年 10 月に、Cloud Automation パッチ適用サービスのベータ版リリースが [Site-Wide Analysis tool ダッシュボード &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/site-wide-analysis-tool/dashboard) に追加されます。 このサービスは、以下を含む合理化されたパッチ適用ワークフローで、Commerce プロジェクト管理者をサポートします。

- パッチの自動インストール
- ロールバック・リカバリ
- デプロイメント後の検証。

このサービスにより、手動の労力とリスクを最小限に抑えて、安全で安定した、更新された環境を維持できます。

ベータ版には次の機能が含まれています。

- **パッチのインストールを自動化**：環境全体で重要な脆弱性をパッチするプロセスを簡素化し、自動化します。
- **リスクの最小化**：導入後のヘルスチェックおよびロールバック機能により、サイトの停止を防ぎます。

>[!NOTE]
>
>クラウド自動修正パッチサービスは個別のセキュリティパッチを自動的に適用するので、これを使用するには [&#x200B; 投稿者またはプロジェクト管理者の役割 &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/project/user-access) が必要です。

このベータ版に参加するには、[Cloud Automation Patching Service - Beta サインアップフォーム &#x200B;](https://forms.office.com/r/3Wfxj5nPdB) に記入して送信します。

### Adobe Commerce財団（パブリックAlpha/Beta）

[!BADGE PaaS のみ &#x200B;]{type=Informative url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Adobe Commerce on Cloud プロジェクト（Adobeが管理する PaaS インフラストラクチャ）およびオンプレミスプロジェクトにのみ適用されます。"}

Adobe Commerce Foundation の各アルファ版およびベータ版のリリースには、予定リリース日までにAdobe Commerce コアコードに提供されるすべての変更が含まれます。これには、次の機能領域が含まれますが、それに限定されるものではありません。

- 最新のセキュリティ修正
- パフォーマンスの向上
- GraphQLの改善点
- 一般的な品質のバグ修正
- コミュニティの投稿
- [Adobe Commerce サービスとの互換性をサポートするために必要な変更 &#x200B;](https://experienceleague.adobe.com/en/docs/commerce/user-guides/home)

#### 命名規則とスケジュール

Adobeは通常、アルファ版およびベータ版のパッチを年に数回リリースします。

Alpha リリースパッケージには `-alphaX` サフィックスがあります。 例えば、Adobe Commerce 2.4.7 アルファリリースパッケージでは、次の命名規則を使用します。

- `2.4.7-alpha1`
- `2.4.7-alpha2`

Beta リリースパッケージには `-betaX` サフィックスがあります。 例えば、Adobe Commerce 2.4.7 ベータリリースパッケージでは、次の命名規則を使用します。

- `2.4.7-beta1`
- `2.4.7-beta2`

今後の公開アルファ版およびベータ版のリリース日のリストについては、[&#x200B; リリーススケジュール &#x200B;](schedule.md) を参照してください。

#### リリースへのアクセス

Adobe Commerceのアルファ版およびベータ版のリリースは、他のAdobe Commerceのパッチリリースと同じ方法で配布されます。つまり、`https://repo.magento.com` 上の Composer メタパッケージとして配布されます。 ソースコードは [GitHub](https://github.com/magento/magento2) で入手できます。

詳細は、「[Composer インストール クイック スタート &#x200B;](../installation/composer.md)」を参照してください。

#### 問題レポート

Adobeは、アルファ版およびベータ版のリリースに対して標準のAdobe サポートサービスを提供しません。

アルファ版およびベータ版リリースに関連するフィードバックを送信するには、[GitHub](https://developer.adobe.com/commerce/contributor/guides/code-contributions/) の [&#x200B; 通常のイシューレポートフロー &#x200B;](https://github.com/magento/magento2) に従います。

Adobeは、最新のアルファ版またはベータ版のリリースに対して報告されたすべての重要な問題を監視し、GA リリース日より前に解決されるように優先順位を付けます。
