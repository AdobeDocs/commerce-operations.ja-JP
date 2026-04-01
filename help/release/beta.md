---
title: Beta リリース
description: Adobe Commerce ベータ版のリリースと参加方法について説明します。
exl-id: 662cb061-995f-4e09-a2ef-9e607cc0000b
badgePaas: label="PaaS" type="Informative" url="https://experienceleague.adobe.com/ja/docs/commerce/user-guides/product-solutions" tooltip="Adobe Commerce on Cloud プロジェクト（Adobeで管理されるPaaS インフラストラクチャ）とオンプレミス プロジェクトにのみ適用されます。"
badgeSaas: label="SaaS" type="Positive" url="https://experienceleague.adobe.com/ja/docs/commerce/user-guides/product-solutions" tooltip="Adobe Commerce as a Cloud ServiceおよびAdobe Commerce Optimizer プロジェクト（Adobeが管理するSaaS インフラストラクチャ）にのみ適用されます。"
source-git-commit: 804022abf074be8997d038426e228069f7b68afd
workflow-type: tm+mt
source-wordcount: '1351'
ht-degree: 0%

---

# Adobe Commerce ベータ版リリース

[Adobe Commerce製品ソリューション &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce/user-guides/product-solutions)のBeta プログラムは、販売者がプレリリース機能とコードにアクセスし、フィードバックを提供し、Adobe Commerceの将来を導くための手段です。 ベータプログラムには2種類あります。

- パブリック Beta:Adobe Commerceのすべてのユーザーおよびパートナーは、パブリックベータプログラムを利用できます
- Private Beta：プライベートベータプログラムに参加するには、資格基準に基づく承認が必要になる場合があります

>[!IMPORTANT]
>
>**法的免責事項**<br/>
>Betaのリリースには、不具合を含む可能性のあるプレリリース機能とコードが含まれており、いかなる保証もなく「現状のまま」提供されます。 Adobeは、ベータ版リリースを一般公開するかどうかを単独で決定します。 Adobeは、（Adobe サポートサービスまたはその他の方法を介して）メンテナンス、修正、更新、変更、変更、サポートを行う義務を負いません。また、特定の日付までにそのようなベータリリースを提供する義務も負いません。 ベータリリースが一般公開された場合、適用手数料を含む追加の条件が適用される場合があります。 Betaのリリースは、中止を含め、予告なく変更される場合があります。 お客様は、ベータ版リリースの中断のない、またはエラーのない機能やパフォーマンスに依存しないように、慎重に使用することをお勧めします。  したがって、ベータ版リリースの使用は、完全にお客様の責任で行います。

## 参加の利点

Adobeで開発している機能に早期にアクセスできれば、顧客やパートナーはフィードバックを提供し、製品開発を調整して、新機能を一般公開する前に導入する準備を整えることができます。

## 現在のBeta プログラム

アクティブなベータ版プログラムの一覧については、次の節を参照してください。

### グローバルおよびカタログビューごとのマーチャンダイジングルール（パブリックBeta）

[!BADGE SaaSのみ]{type=Positive url="https://experienceleague.adobe.com/ja/docs/commerce/user-guides/product-solutions" tooltip="Adobe Commerce as a Cloud ServiceおよびAdobe Commerce Optimizer プロジェクト（Adobeが管理するSaaS インフラストラクチャ）にのみ適用されます。"}

Adobe Commerce Optimizerでは、柔軟な範囲でマーチャンダイジングルールを定義し、あらゆるカタログビューにルールを適用したり、特定のカタログビューにルールを適用したりすることができます。 この機能により、複数のストアフロント、ブランド、言語を運営しているマーチャントのマーチャンダイジングルールの管理が簡素化されます。 カタログビュー固有のルールを利用することで、各地域に合わせたエクスペリエンスやブランド独自のエクスペリエンスが必要な場合に、個々のチャネルに合わせた検索結果やマーチャンダイジングロジックを提供できます。 カタログビュー固有のルールが存在する場合は、そのビューのグローバルルールを上書きし、効率的な設定管理を維持しながら正確な制御を提供します。

**主なメリット**

- あらゆるカタログビューをまたいで、グローバルなマーチャンダイジングルールを定義します。
- ローカライズされたエクスペリエンスが必要な場合は、特定のカタログビューのルールを上書きします。
- ストアフロントをまたいで設定の重複を減らします。
- マルチブランドおよび多言語のコマース実装のスケーラビリティを向上。

これにより、マーチャンダイジングの柔軟性と業務効率が向上し、より適切な製品体験を大規模に提供できるようになります。 詳しくは、[&#x200B; マーチャンダイジングルール &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce/optimizer/merchandising/rules/add)を参照してください。

>[!NOTE]
>
>Betaの参加者は、新しいカタログビュースコープを活用するために、既存のマーチャンダイジングルールを再作成する必要があります。

このベータ版の機能を使用する際にフィードバックを共有するには、[commerce-storefront-services@adobe.com](mailto:commerce-storefront-services@adobe.com)にメールを送信してください。

### グローバルおよびカタログビューごとの商品レコメンデーション（パブリックBeta）

[!BADGE SaaSのみ]{type=Positive url="https://experienceleague.adobe.com/ja/docs/commerce/user-guides/product-solutions" tooltip="Adobe Commerce as a Cloud ServiceおよびAdobe Commerce Optimizer プロジェクト（Adobeが管理するSaaS インフラストラクチャ）にのみ適用されます。"}

Adobe Commerce Optimizerでは、商品レコメンデーションの設定に対する高度な制御が導入され、すべてのカタログビューをまたいで、または個々のカタログビューに特化してレコメンデーションユニットを定義できるようになりました。

この機能により、複数のストアフロント、ブランド、地域、言語を運用している企業のレコメンデーション管理が簡素化され、 加盟店は、グローバルでレコメンデーションユニットを一度作成すれば、あらゆるカタログビューに適用され、チャネルをまたいで一貫性のある商品ディスカバリー戦略を実現できます。 同時に、カタログビューに特化したレコメンデーションユニットにより、必要に応じて特定のストアフロント向けに体験をカスタマイズすることができます。

ストアフロントのエンゲージメントイベントとレコメンデーション指標は、カタログビューレベルで追跡されるため、様々なストアフロントをまたいで買い物客の行動に関するより正確なインサイトを獲得できます。

**主なメリット**

- あらゆるカタログビューをまたいで、世界中の商品レコメンデーションユニットを設定できます。
- ローカライズされたストアフロント体験を実現するために、カタログビューに特化したレコメンデーションを作成します。
- マルチブランドまたは多言語のストアフロントをまたいで設定の重複を減らすことができます。
- カタログビューで追跡された指標とイベントにより、より正確なインサイトを獲得できます。

この機能強化により、複雑なコマース環境をまたいでレコメンデーションを管理することが簡素化され、より適切な商品発見体験を提供できるようになります。 詳しくは、[推奨事項](https://experienceleague.adobe.com/ja/docs/commerce/optimizer/manage-results/recommendation-performance)を参照してください

>[!NOTE]
>
>Betaの参加者は、新しいカタログビュースコープを活用するために、既存のレコメンデーションユニットを再作成する必要があります。

このベータ版の機能を使用する際にフィードバックを共有するには、[commerce-storefront-services@adobe.com](mailto:commerce-storefront-services@adobe.com)にメールを送信してください。

### セマンティック検索：よりスマートでコンテキストに即したショッピング体験（Private Beta）

[!BADGE SaaSのみ]{type=Positive url="https://experienceleague.adobe.com/ja/docs/commerce/user-guides/product-solutions" tooltip="Adobe Commerce as a Cloud ServiceおよびAdobe Commerce Optimizer プロジェクト（Adobeが管理するSaaS インフラストラクチャ）にのみ適用されます。"}

セマンティック検索は、正確な単語だけでなく、買い物客のクエリの背後にある&#x200B;*意味*&#x200B;を理解できるe コマース検索テクノロジーです。 従来のキーワードベースの検索では、馴染みのない単語やスペルが間違っている単語が含まれている場合に失敗することが多かったのですが、このAIを活用したアプローチでは、自然言語処理（NLP）とコンテキストを使用して意図を解釈し、より適切な結果を提供します。

このテクノロジーは、従来の検索における大きな制限である、買い物客がカタログに存在しない単語を使用した場合に発生する結果がゼロのページに対処します。 AIを活用した手法を使用して、ユーザークエリと製品データを共有のセマンティックスペースにマッピングします。 例えば、システムは、「ランニングシューズ」と「ジョギングスニーカー」が同じ種類の製品を指していることを認識し、次のことを可能にします。

- 同義語認識
- コンテキストの関連性
- 曖昧な、スペルが間違っている、または複合クエリのインテリジェントな処理
- 自然言語の理解

ベータプログラムへの招待をリクエストするには、[commerce-storefront-services@adobe.com](mailto:commerce-storefront-services@adobe.com)に電子メールを送信してください。 Adobeチームは、次のステップと適格要件で対応します。

### Cloud Automation Patching Service （Private Beta）

[!BADGE PaaSのみ]{type=Informative url="https://experienceleague.adobe.com/ja/docs/commerce/user-guides/product-solutions" tooltip="Adobe Commerce on Cloud プロジェクト（Adobeで管理されるPaaS インフラストラクチャ）とオンプレミス プロジェクトにのみ適用されます。"}

[Cloud Automation Patching Service](../tools/caps-tool/intro.md)は、Cloud Infrastructure[環境の](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/overview)Adobe Commerceに個別のセキュリティ パッチを適用するプロセスを自動化します。

2025年10月、Cloud Automation Patching Serviceのベータ版リリースが[&#x200B; サイト全体の分析ツール ダッシュボード &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/site-wide-analysis-tool/dashboard)に追加されます。 このサービスは、次のような合理化されたパッチワークフローにより、Commerce プロジェクト管理者をサポートします。

- 自動パッチインストール
- ロールバック回復
- 導入後の検証：

このサービスは、最小限の手作業とリスクで、安全で安定した、更新された環境を維持できることを保証します。

ベータ版には次の機能が含まれています。

- **パッチのインストールの自動化**：環境全体で重要な脆弱性にパッチを適用するプロセスを簡略化および自動化します。
- **リスクを最小限に抑える**：デプロイメント後のヘルスチェックとロールバック機能により、サイトの停止を防ぎます。

>[!NOTE]
>
>Cloud Automation Patching Serviceは分離されたセキュリティ パッチを自動的に適用するため、それを使用するには[&#x200B; コントリビューターまたはプロジェクト管理者の役割](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/project/user-access)が必要です。

このベータ版に参加するには、[Cloud Automation Patching Service - Beta サインアップフォーム &#x200B;](https://forms.office.com/r/3Wfxj5nPdB)に記入して送信してください。

### （財）Adobe Commerce財団（パブリックAlpha/Beta）

[!BADGE PaaSのみ]{type=Informative url="https://experienceleague.adobe.com/ja/docs/commerce/user-guides/product-solutions" tooltip="Adobe Commerce on Cloud プロジェクト（Adobeで管理されるPaaS インフラストラクチャ）とオンプレミス プロジェクトにのみ適用されます。"}

Adobe Commerce Foundationの各アルファ版およびベータ版リリースには、次の機能領域を含むがこれに限定されない、リリース予定日までにAdobe Commerce コアコードに配信されたすべての変更点が含まれます。

- 最新のセキュリティ修正
- パフォーマンスの向上
- GraphQLの機能強化
- 一般的な品質バグの修正
- コミュニティへの貢献
- [Adobe Commerce サービス &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce/user-guides/home)との互換性をサポートするために必要な変更点

#### 命名規則とスケジュール

Adobeは通常、年に数回、アルファ版とベータ版のパッチをリリースします。

Alpha リリースパッケージには、`-alphaX`という接尾辞が付いています。 例えば、Adobe Commerce 2.4.7 アルファリリースパッケージでは、次の命名規則が使用されます。

- `2.4.7-alpha1`
- `2.4.7-alpha2`

Beta リリースパッケージには、`-betaX`という接尾辞が付いています。 例えば、Adobe Commerce 2.4.7 ベータ版リリースパッケージでは、次の命名規則が使用されます。

- `2.4.7-beta1`
- `2.4.7-beta2`

今後の公開アルファ版とベータ版のリリース日のリストについては、[&#x200B; リリーススケジュール &#x200B;](schedule.md)を参照してください。

#### リリースアクセス

Adobe Commerce アルファ版とベータ版のリリースは、他のAdobe Commerce パッチリリースと同じように配布されます：`https://repo.magento.com`のComposer メタパッケージと同じです。 ソースコードは[GitHub](https://github.com/magento/magento2)で入手できます。

詳しくは、[Composer インストールクイックスタート &#x200B;](../installation/composer.md)を参照してください。

#### 問題レポート

Adobeでは、アルファ版およびベータ版のリリースに対して標準のAdobe サポートサービスを提供していません。

アルファ版とベータ版のリリースに関連するフィードバックを送信するには、[GitHub](https://developer.adobe.com/commerce/contributor/guides/code-contributions/)の[通常の問題報告フロー](https://github.com/magento/magento2)に従ってください。

Adobeでは、最新のアルファ版またはベータ版リリースに対して報告されたすべての重大な問題を監視し、GA リリース日より前に解決するように優先順位付けします。
