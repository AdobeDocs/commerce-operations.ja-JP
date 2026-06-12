---
title: Beta リリース
description: Adobe Commerce ベータ版のリリースと参加方法について説明します。
exl-id: 662cb061-995f-4e09-a2ef-9e607cc0000b
badgePaas: label="PaaS" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Adobe Commerce on Cloud プロジェクト（Adobeで管理されるPaaS インフラストラクチャ）とオンプレミス プロジェクトにのみ適用されます。"
badgeSaas: label="SaaS" type="Positive" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Adobe Commerce as a Cloud ServiceおよびAdobe Commerce Optimizer プロジェクト（Adobeが管理するSaaS インフラストラクチャ）にのみ適用されます。"
source-git-commit: 41e4aa725848fd7fa4910eaea09a802326fa3995
workflow-type: tm+mt
source-wordcount: '1451'
ht-degree: 0%

---

# Adobe Commerce ベータ版リリース

[Adobe Commerce製品ソリューション ](https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions)のBeta プログラムは、販売者がプレリリース機能とコードにアクセスし、フィードバックを提供し、Adobe Commerceの将来を導くための手段です。 ベータプログラムには2種類あります。

- パブリック Beta:Adobe Commerceのすべてのユーザーおよびパートナーは、パブリックベータプログラムを利用できます
- Private Beta：プライベートベータプログラムに参加するには、資格基準に基づく承認が必要になる場合があります

>[!IMPORTANT]
>
>**法的免責事項**<br/>
>Betaのリリースには、不具合を含む可能性のあるプレリリース機能とコードが含まれており、いかなる保証もなく「現状のまま」提供されます。Adobeは、ベータ版リリースを一般公開するかどうかを単独で決定します。Adobeは、（Adobe サポートサービスまたはその他の方法を介して）メンテナンス、修正、更新、変更、変更、サポートを行う義務を負いません。また、特定の日付までにそのようなベータリリースを提供する義務も負いません。ベータリリースが一般公開された場合、適用手数料を含む追加の条件が適用される場合があります。Betaのリリースは、中止を含め、予告なく変更される場合があります。お客様は、ベータ版リリースの中断のない、またはエラーのない機能やパフォーマンスに依存しないように、慎重に使用することをお勧めします。 したがって、ベータ版リリースの使用は、完全にお客様の責任で行います。

## 参加の利点

Adobeで開発している機能に早期にアクセスできれば、顧客やパートナーはフィードバックを提供し、製品開発を調整して、新機能を一般公開する前に導入する準備を整えることができます。

## 現在のBeta プログラム

アクティブなベータ版プログラムの一覧については、次の節を参照してください。

### 検索マッチングとランキング（Private Beta）

[!BADGE SaaSのみ]{type=Positive url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Adobe Commerce as a Cloud ServiceおよびAdobe Commerce Optimizer プロジェクト（Adobeが管理するSaaS インフラストラクチャ）にのみ適用されます。"}

[!BADGE PaaSのみ]{type=Informative url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Adobe Commerce on Cloud プロジェクト（Adobeで管理されるPaaS インフラストラクチャ）とオンプレミス プロジェクトにのみ適用されます。"}

Adobeでは、[!DNL Adobe Commerce]および[!DNL Adobe Commerce Optimizer]の[!DNL Live Search]の検索結果を商品の検索でランク付けする方法を改善しています。 更新では、**完全一致とほぼフレーズ一致**&#x200B;が優先され、次に&#x200B;**すべてのクエリ用語が同じ検索可能な属性**&#x200B;に表示され、最後に&#x200B;**クロスフィールド**&#x200B;が一致します（オートコンプリート形式の提案をサポートする動作を含む）。 この階層化されたモデルは、高い意図を示すクエリが、最も関連性の高い製品を最初に表示でありながら、有用な代替品を返すのに役立ちます。

同じ関連性モデルが、**検索ウェイト**、**インテリジェントランキング**、**類義語**、および&#x200B;**マーチャンダイジングルール** （ピン、ブースト、埋め込み）と相互作用します。 ドイツのストアフロントでは、同様の全体的な優先順位付けアプローチで、複合語に&#x200B;**減算**&#x200B;を使用できます。

**主なメリット**

- 完全一致とほぼフレーズ一致（単数や複数形などの正規化されたフォームを含む）の強力なブースト。
- すべてのクエリワードが1つの検索可能なフィールドに一緒に表示される場合に、より高いランキング。
- クエリ時に、重み付け、インテリジェントなランキング、手動のルールをどのように組み合わせるかについて明確な期待値を示します。
- 変更後に価値の高いクエリを検証し、ブーストルールを調整するためのガイダンス。

[Adobe Commerce Optimizer （SaaS） ](https://experienceleague.adobe.com/en/docs/commerce/optimizer/search-relevance-matching)および[ ライブサーチ （PaaS） ](https://experienceleague.adobe.com/en/docs/commerce/live-search/search-relevance-matching)の検索マッチングとランキング戦略について詳しく説明します。

このプライベートベータ版への招待をリクエストするには、[commerce-storefront-services@adobe.com](mailto:commerce-storefront-services@adobe.com)にメールを送信してください。 Adobeチームは、次のステップと適格要件で対応します。

### 推奨価格フィルター（パブリックBeta） {#recommendation-price-filters-public-beta}

[!BADGE SaaSのみ]{type=Positive url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Adobe Commerce as a Cloud ServiceおよびAdobe Commerce Optimizer プロジェクト（Adobeが管理するSaaS インフラストラクチャ）にのみ適用されます。"}

[!DNL Adobe Commerce Optimizer]では、商品レコメンデーションに&#x200B;**価格フィルター**&#x200B;が追加されるので、レコメンデーション単位を作成または編集する際に、価格に基づいて推奨される商品を含めたり除外したりできます。 フィルターでは、ストアフロントの&#x200B;**アクティブな価格表**&#x200B;から各商品の&#x200B;**最終計算価格**&#x200B;を使用し、その価格表の割引やプロモーションを含めます（リスト価格だけではありません）。 プライスルールは、候補セットを絞り込みます。これらは、商品を再ランク付けしません。

ストアの基本通貨で固定最小値と最大値を持つ&#x200B;**static**&#x200B;の範囲、またはアンカー価格の値以上または値内またはパーセンテージの範囲内などの演算子を使用して、推奨商品を&#x200B;**現在表示されている商品**&#x200B;と比較する商品詳細ページの&#x200B;**dynamic**&#x200B;のルールを定義できます。 製品コンテキストで実行されるSKU関連のレコメンデーションタイプに対して、動的フィルターを使用できます（例：*閲覧、閲覧*、閲覧&#x200B;*詳細*）。

**主なメリット**

- **商品のフィルター**&#x200B;手順の包含ルールと除外ルールを使用して、価格による推奨候補を含めるか除外します。
- 固定のマーチャンダイジング目標に対して固定価格帯を適用します（例：予算対応のアドオンやプレミアムアップセル）。
- 商品詳細ページで動的な価格ルールを使用して、閲覧中の商品に対して同等の価格帯の中で代替品を表示します。
- フィルタリングと表示に使用されるアクティブな価格表と同じ最終価格である、買い物客が表示する価格に合わせてフィルタリングを調整します。

詳しくは、マーチャントガイドの「[ レコメンデーションフィルター – 価格](https://experienceleague.adobe.com/en/docs/commerce/optimizer/merchandising/recommendations/filters#price)」、ストアフロントドロップインガイドの「[商品レコメンデーションの設定](https://experienceleague.adobe.com/developer/commerce/storefront/merchants/content-customizations/product-recommendations/)」を参照してください。

このベータ版の機能を使用する際にフィードバックを共有するには、[commerce-storefront-services@adobe.com](mailto:commerce-storefront-services@adobe.com)にメールを送信してください。

### Cloud Automation Patching Service （Private Beta）

[!BADGE PaaSのみ]{type=Informative url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Adobe Commerce on Cloud プロジェクト（Adobeで管理されるPaaS インフラストラクチャ）とオンプレミス プロジェクトにのみ適用されます。"}

[Cloud Automation Patching Service](../tools/caps-tool/intro.md)は、Cloud Infrastructure](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/overview)環境の[Adobe Commerceに個別のセキュリティ パッチを適用するプロセスを自動化します。

2025年10月、Cloud Automation Patching Serviceのベータ版リリースが[ サイト全体の分析ツール ダッシュボード ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/site-wide-analysis-tool/dashboard)に追加されます。 このサービスは、次のような合理化されたパッチワークフローにより、Commerce プロジェクト管理者をサポートします。

- 自動パッチインストール
- ロールバック回復
- 導入後の検証：

このサービスは、最小限の手作業とリスクで、安全で安定した、更新された環境を維持できることを保証します。

ベータ版には次の機能が含まれています。

- **パッチのインストールの自動化**：環境全体で重要な脆弱性にパッチを適用するプロセスを簡略化および自動化します。
- **リスクを最小限に抑える**：デプロイメント後のヘルスチェックとロールバック機能により、サイトの停止を防ぎます。

>[!NOTE]
>
>Cloud Automation Patching Serviceは分離されたセキュリティ パッチを自動的に適用するため、それを使用するには[ コントリビューターまたはプロジェクト管理者の役割](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/project/user-access)が必要です。

このベータ版に参加するには、[Cloud Automation Patching Service - Beta サインアップフォーム ](https://forms.office.com/r/3Wfxj5nPdB)に記入して送信してください。

### Merchant Productivity AI アシスタント （パブリック Beta）

加盟店の生産性を向上させるAI アシスタントは、Adobe Commerce管理画面に組み込まれた会話型インターフェイスで、自然言語を使って日常的なタスクを遂行し、ビジネスインサイトにオンデマンドでアクセスするのに役立ちます。 これにより、既存のワークフロー内で、プロモーションの管理、商品カタログ情報の更新、最近の注文やアクティブなプロモーションなどの運用データを直接取得することができます。 また、AI アシスタントは、マーチャントが管理者をより効率的にナビゲートして使用できるよう、コンテキストに沿ったガイダンスも提供します。

**主なメリット**

- 自然言語の指示を使用して、プロモーションの作成やカタログのメタデータの更新などの一般的なマーチャンダイジングタスクを自動化できます。
- 管理者ワークフロー内で、コンテクストに関する支援やガイダンスに直接アクセスできます。
- ライブストアのデータをオンデマンドでクエリできます。たとえば、最後の10件の注文の取得、現在アクティブなプロモーションの表示、在庫状況の確認などができます。
- 管理者の反復的なタスクにかかる時間を削減し、マーチャントを戦略や成長に集中させることができます。

このベータ版に参加するには、[commerce-storefront-services@adobe.com](mailto:commerce-storefront-services@adobe.com)に電子メールを送信してください。

### （財）Adobe Commerce財団（パブリックAlpha/Beta）

[!BADGE PaaSのみ]{type=Informative url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Adobe Commerce on Cloud プロジェクト（Adobeで管理されるPaaS インフラストラクチャ）とオンプレミス プロジェクトにのみ適用されます。"}

Adobe Commerce Foundationの各アルファ版およびベータ版リリースには、次の機能領域を含むがこれに限定されない、リリース予定日までにAdobe Commerce コアコードに配信されたすべての変更点が含まれます。

- 最新のセキュリティ修正
- パフォーマンスの向上
- GraphQLの機能強化
- 一般的な品質バグの修正
- コミュニティへの貢献
- [Adobe Commerce サービス ](https://experienceleague.adobe.com/en/docs/commerce/user-guides/home)との互換性をサポートするために必要な変更点

#### 命名規則とスケジュール

Adobeは通常、年に数回、アルファ版とベータ版のパッチをリリースします。

Alpha リリースパッケージには、`-alphaX`という接尾辞が付いています。 例えば、Adobe Commerce 2.4.7 アルファリリースパッケージでは、次の命名規則が使用されます。

- `2.4.7-alpha1`
- `2.4.7-alpha2`

Beta リリースパッケージには、`-betaX`という接尾辞が付いています。 例えば、Adobe Commerce 2.4.7 ベータ版リリースパッケージでは、次の命名規則が使用されます。

- `2.4.7-beta1`
- `2.4.7-beta2`

今後の公開アルファ版とベータ版のリリース日のリストについては、[ リリーススケジュール ](schedule.md)を参照してください。

#### リリースアクセス

Adobe Commerce アルファ版とベータ版のリリースは、他のAdobe Commerce パッチリリースと同じように配布されます：`https://repo.magento.com`のComposer メタパッケージと同じです。 ソースコードは[GitHub](https://github.com/magento/magento2)で入手できます。

詳しくは、[Composer インストールクイックスタート ](../installation/composer.md)を参照してください。

#### 問題レポート

Adobeでは、アルファ版およびベータ版のリリースに対して標準のAdobe サポートサービスを提供していません。

アルファ版とベータ版のリリースに関連するフィードバックを送信するには、[GitHub](https://github.com/magento/magento2)の[通常の問題報告フロー](https://developer.adobe.com/commerce/contributor/guides/code-contributions/)に従ってください。

Adobeでは、最新のアルファ版またはベータ版リリースに対して報告されたすべての重大な問題を監視し、GA リリース日より前に解決するように優先順位付けします。
