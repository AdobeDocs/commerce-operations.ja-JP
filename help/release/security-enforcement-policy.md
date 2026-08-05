---
title: セキュリティとコンプライアンス：必要なアクションと期限
description: 期限、必要なアクション、リスクなど、Cloud版およびソフトウェアの依存関係でサポートされていないAdobe Commerceのセキュリティを適用する方法について説明します。
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
  - id: cdf0c6dd-1717-4e20-9530-a24eee57088b
feature_v2:
  - id: b5f00040-57a0-4a6d-a39e-383b1936c2c9
  - id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
  - id: c32adafa-ed01-4b31-997e-2413013911b0
  - id: cc250cf1-34eb-4863-80d0-d170d45ea067
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
subfeature_v2:
  - id: f2261633-201d-46c5-8a66-999e70527a83
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
badgePaas: label="Adobe Commerce クラウド版のみ" type="Informative" url="https://experienceleague.adobe.com/ja/docs/commerce/user-guides/product-solutions" tooltip="Cloud バージョン 2.4.4 ～ 2.4.9のAdobe Commerceにのみ適用されます"
color: blue
source-git-commit: 79afa4fa95c425dfd4bc0fd894abc24db2d1b33b
workflow-type: tm+mt
source-wordcount: 2040
ht-degree: 0%

---


# セキュリティとコンプライアンスに関するお知らせ：必要なアクションと期限

>[!NOTE]
>
> **Adobe Commerce バージョン 2.4.4 ～ 2.4.9を実行しているAdobe Commerce on Cloud （PaaS）環境**&#x200B;に適用されます。
>
> このガイダンスは、[!DNL Adobe Commerce as a Cloud Service] （SaaS）環境またはAdobe Commerce オンプレミスのデプロイメントには適用されません。

サイバーセキュリティを取り巻く状況は根本的に変化しており、企業が導入する防御的メカニズムは急速に進化する必要があります。 セキュリティは、e コマースビジネスにとって非常に重要です。オンライン取引では、機密性の高い個人データとビジネスデータを扱う必要があり、侵害が発生した場合に財務リスクやID リスクに晒す必要があります。 PaaS e コマース環境は、Adobeとお客様の間で共通のセキュリティ責任モデルを持っています。このモデルでは、お客様がアプリケーションレイヤーの依存関係のメンテナンス、サードパーティソフトウェアとの統合、デプロイメントパイプラインを担当します。

Adobeでは、変化するリスクに積極的に対処し、Adobe Commerce on Cloudのお客様を最高のセキュリティ基準に設定することを保証します。 次の項目を含みます。

* 重大な脆弱性に対する迅速かつ予測可能な保護のための、毎月および個別のセキュリティ修正
* 長期サポート付きの年間パッチリリース
* 各リリースのライフサイクルポリシーを合理化し、3年間のサポートウィンドウを提供

Adobeは、お客様のセキュリティを維持するために必要な手順を実行しますが、Adobe Commerce on Cloudの[責任共有モデル &#x200B;](../security-and-compliance/shared-responsibility.md)では、お客様が常にサポートされているバージョンのAdobe Commerce on Cloudおよびサードパーティのソフトウェアを使用し、アプリケーションパッチを適用し、サードパーティの拡張機能を監査し、カスタムコードを保護する必要があります。 ベンダーサポートを終了したソフトウェアにはセキュリティパッチが適用されなくなり、ソフトウェアのセキュリティ問題は未解決のままになります。 サポートされていないソフトウェアでコマースストアフロントを運営し続けると、セキュリティリスクが高まり、さらに大きくなる可能性があります。

このページでは、Adobe Commerce on Cloud （バージョン 2.4.4～2.4.9）を利用しているすべてのお客様が、e コマース環境を安全に保つために必要なアクションについて、実施日とともに、セキュリティ要件が満たされない場合に想定される対応について説明します。

## 安全でコンプライアンスを維持するために必要なアクション

コマース環境を安全でコンプライアンスを維持するには、Adobe Commerce on Cloudをご利用のお客様は次の要件を満たす必要があります。

1. サポートされているすべてのサードパーティソフトウェアのバージョン（PHP、MariaDB、Elasticsearch/OpenSearch、Redis、RabbitMQ）

1. Adobe Commerce on Cloudの安全なサポート対象

以下のガイドラインに従って、Adobe Commerce on Cloud環境を保護するためにアクションを実行する必要があるかどうかを確認します。 以下の表1に記載されている期限までにセキュリティ要件を満たさない環境では、ストアフロントをオフラインにしてインバウンドトラフィックが停止します。 期限の遵守に関して懸念があり、短い延長が必要な場合は、アカウントチームまたはAdobe [&#x200B; サポート &#x200B;](https://experienceleague.adobe.com/ja/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#support-case)にお問い合わせください。

**表1: セキュリティ要件と期限**

| Adobe Commerce Cloud版 | サポートされているサードパーティ製ソフトウェアの依存関係へのアップグレード | 最新のAdobe Commerce on Cloud バージョンにアップグレードするか、[!DNL Adobe Commerce as a Cloud Service]に移行します |
| --- | --- | --- |
| 2.4.4または2.4.5 | 2026年10月30日までに必要です。 | 2027年6月1日までに必要 |
| 2.4.6または2.4.7 | ソフトウェアによっては、2026年10月30日（PT）または2027年5月31日（PT）までに必要となります。 | 2028年6月1日までに必要 |
| 2.4.8または2.4.9 | ソフトウェアによっては、2026年10月30日（PT）または2027年5月31日（PT）までに必要となります。 | 現時点では必要ありません |

## 環境を保護するための詳細な手順

### アクション 1: サードパーティ製ソフトウェアの依存関係を確認してアップグレードする

ご使用の環境で、PHP、MariaDB、Elasticsearch/OpenSearch、Redis、RabbitMQなどのサードパーティソフトウェアの依存関係をベンダーサポートで実行していることを確認してください。 そうでない場合は、ソフトウェア依存関係をサポートされているバージョンにアップグレードします。

#### 手順1：サードパーティソフトウェアの依存関係のバージョンを確認する

1. [Cloud Console](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/start/cloud-console)にログインします。
2. 関連するプロジェクトを開き、確認する環境を選択します。
3. Adobe Commerce on Cloudでサポートされているサービス名とバージョンを定義する`.magento/services.yaml` ファイルで、その環境のサービス設定を確認します。

詳細な手順については、[Configure Services](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/configure/service/services-yaml)を参照してください。

サポートされていないソフトウェアの依存関係はすべて、以下の表2のタイムラインで概説されているバージョンにアップグレードする必要があります。

**表2：必要な依存関係のアップグレード**

| 依存関係 | バージョン | にアップグレードする必要があります | 期限 |
| --- | --- | --- | --- |
| PHP | 8.1以前 | 8.2以上 | 2027年5月31日（PT） |
| MariaDB/Galera | 10.5以下 | 10.6以上 | 2026年10月30日（PT） |
| MariaDB/Galera | 10.5より大きく10.11より小さい | バージョン 10.11以降 | 2027年5月31日（PT） |
| Elasticsearch | 任意のバージョン | OpenSearch: バージョン 2.19 （2.4.4および2.4.5のお客様向け）。 2.4.6以降のお客様のバージョン 3。 | 2026年10月30日（PT） |
| OpenSearch | 1.x | 2.4.4および2.4.5のお客様向けのバージョン 2.19。 2.4.6以降のお客様のバージョン 3。 | 2027年5月31日（PT） |
| Redis | 5以下 | Valkey バージョン 8以降 | 2027年5月31日（PT） |
| RabbitMQ | 3.9以前 | バージョン 3.13以降 | 2026年10月30日（PT） |
| RabbitMQ | 3.9より大きく3.13より小さい | 4.3以上 | 2027年5月31日（PT） |

#### 手順2：サードパーティのソフトウェア依存アップグレードの準備

Adobeを使用すると、これらのソフトウェアの依存関係を直接アップグレードできます。

* **開始：** アップグレードが必要な環境と関連する依存関係を一覧表示する[&#x200B; サポートチケット &#x200B;](https://experienceleague.adobe.com/ja/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#support-case)を開きます。 Adobeが作業をスケジュールできるように、少なくとも施行日の30日前にチケットを開きます。

* **ダウンタイム：** Adobeは、スケジュールを設定するときに、想定される時間枠を確定します。

* **テスト：**&#x200B;実稼動以外の環境を実稼動前にアップグレードして検証します。 チェックアウト、検索、カート、その他のカスタム統合を検証します。 要件はすべての環境に適用されるので、実稼動環境ではなく、すべての環境をアップグレードすることを計画してください。

* **互換性：**&#x200B;これらの変更のほとんどは、同じソフトウェア内のバージョンのアップグレードであり、リスクは低くなります。 以下の変更は、注意を払う必要があります。

  * **ElasticsearchからOpenSearch**&#x200B;および&#x200B;**RedisからValkey**&#x200B;への移行は、バージョンのアップグレードではなく、別のソフトウェアへの移行です。 元のサービスを参照するカスタムコード、拡張機能、設定を更新する必要がある場合があります。
  * **PHP 8.1から8.2**&#x200B;にアップグレードすると、カスタムコードおよびサードパーティの拡張機能で非推奨化の警告が表示される場合があります。

サードパーティの拡張機能を使用している場合は、現在のリリースがターゲットソフトウェアのバージョンをサポートしていることをベンダーに確認します。 ソリューションインテグレーターと連携する場合は、アップグレードの計画、テスト、検証の早い段階でIT担当者を関与させます。

### アクション 2: Commerce on Cloud バージョンを確認し、サポートされているバージョンにアップグレードする

お使いの環境で実行されているAdobe Commerce on Cloud バージョンを確認します。 サポートされているバージョンに環境がない場合は、バージョン 2.4.9またはサポートされている最新バージョンにアップグレードするか、[!DNL Adobe Commerce as a Cloud Service]に移行できます。

#### 手順1:Adobe Commerce on Cloud バージョンと必要な操作を確認する

1. Adobe Commerce管理パネルにログインします。

   現在のバージョンは、管理者ページの右下隅に表示されます。

1. バージョンが管理パネルから非表示の場合：

   * [&#x200B; リモート環境](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/secure-connections#connect-to-a-remote-environment)に接続します。
   * Adobe Commerce [&#x200B; コマンドラインツール &#x200B;](../configuration/cli/config-cli.md)を使用して、バージョンを確認します。

     ```shell
     bin/magento --version
     ```

次の表で、Adobe Commerce バージョンに必要なアクションを確認します。

**表3: Cloud版Adobe Commerceのアップグレード要件**

| Adobe Commerce on Cloudの現在のバージョン | 必要なアクション | 期限 |
|---|---|---|
| バージョン 2.4.4または2.4.5 | Cloud バージョン 2.4.9 （または最新バージョン）でAdobe Commerceにアップグレードするか、[!DNL Adobe Commerce as a Cloud Service]に移行します。<br>理由：v2.4.4および2.4.5には、2027年5月31日（PT）まで、コアアプリケーションの限定的な個別のセキュリティ修正のみが適用されます。これには、品質修正、アプリケーション依存関係（PHPなど）の互換性サポート、プラットフォーム依存関係の更新は含まれません。 Adobeの[&#x200B; ライフサイクルポリシー](https://experienceleague.adobe.com/ja/docs/commerce-operations/release/planning/lifecycle-policy)を参照してください。 | 2027年6月1日（PT） |
| バージョン 2.4.6または2.4.7 | Cloud バージョン 2.4.9 （または最新バージョン）でAdobe Commerceにアップグレードするか、[!DNL Adobe Commerce as a Cloud Service]に移行します。理由：バージョン 2.4.6は、2027年8月30日（PT）までの延長サポートを受け、2028年5月31日（PT）までコアアプリケーションに対する限定的な個別のセキュリティ修正のみを受け取ります。 <br>バージョン 2.4.7では、2027年5月31日（PT）まで標準サポートが提供され、2028年5月31日（PT）まで拡張サポートが提供されます。 Adobeの[&#x200B; ライフサイクルポリシー](https://experienceleague.adobe.com/ja/docs/commerce-operations/release/planning/lifecycle-policy)を参照してください。 | 2028年6月1日（PT） |
| バージョン 2.4.8または2.4.9 | Adobe Commerce Cloud版のアップグレードアクションは必要ありません。 アクション 1のサードパーティ製ソフトウェアの依存関係の期限は引き続き適用されます。<br>理由：期限が設定されていません。 | 現時点では必要ありません |

#### 手順2：アップグレードまたは移行パスの決定

Adobe Commerce Cloud版をアップグレードする必要がある場合は、次の2つのオプションがあります。

1. サポートされているAdobe Commerce Cloud版へのアップグレード
1. [!DNL Adobe Commerce as a Cloud Service]への移行（SaaS）

最適なパスを決めるには、次の表を参考に選択肢を比較してください。

**表4: Adobe Commerce on Cloudと[!DNL Adobe Commerce as a Cloud Service]**&#x200B;の比較

| | Adobe Commerce Cloud版バージョン 2.4.9 | [!DNL Adobe Commerce as a Cloud Service] |
|---|---|---|
| **概要** | 完全なセキュリティ範囲、品質修正、プラットフォーム依存関係のアップデートを含む最新のAdobe Commerce リリース。 | 継続的なイノベーションのために構築され、アップグレードのオーバーヘッドを排除できる、Adobeのフルマネージドコマースプラットフォーム。 [学習を増やす](https://experienceleague.adobe.com/ja/docs/commerce/cloud-service/overview)。 |
| **お客様に最適** | 今後も独自のインフラストラクチャ、アップグレード、パッチを管理する必要があります。 | アップグレードサイクルを大幅に短縮し、総所有コストを削減しながら、Adobeの最新の機能を追加の作業なしで自動的に入手できます。 |
| **主なメリット** | 既存の設定を維持しながら、セキュリティ要件を満たします。 | 高速でエッジ配信のストアフロント、拡張性の高いカタログ、ネイティブのデジタルアセット管理、組み込みの生成AIなど、Adobeが管理するインフラストラクチャ上に構築されています。 |

## 期限までに何も行動を起こさなかったらどうなるか。

Adobeは、お客様がサポート対象バージョンのAdobe Commerce クラウド版およびサードパーティソフトウェアにアップグレードするために必要な手順を実行できるよう、引き続きサポートします。

上記の適用日までにセキュリティ要件を満たさない場合、Adobeは、大規模なインストールベースのセキュリティを保証するために適切な措置を講じる必要があります。 これには、影響を受けるインフラストラクチャへのトラフィックを停止することも含まれます。これにより、コマースストアフロントがオフラインになります。

トラフィックの停止後もコンプライアンスを遵守していない環境が続く場合、Adobeはクラウドサービスを終了し、廃止プロセスを開始する可能性があります。 廃止の結果、ホストされているe コマース環境内のすべてのデータとアセット（すべてのインスタンス、環境、ブランチを含む）が完全に削除され、復元できなくなります。

## アップグレードや移行をサポートするリソース

**Cloud バージョン 2.4.9でAdobe Commerceにアップグレードする場合：**

* **アップグレード互換性レポート：** Adobeには、Adobe Commerce バージョン 2.4.9へのアップグレードに必要なコスト範囲など、正確な内容を示す詳細なレポートが用意されています。 [&#x200B; アップグレード互換性レポートを生成](https://supportinsights.adobe.com/commerce/tab/main)。

* **ソフトウェア依存関係のアップグレード：** ソフトウェア依存関係を直接アップグレードできないので、[&#x200B; サポートチケット &#x200B;](https://experienceleague.adobe.com/ja/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#support-case)をAdobeで開いて、アップグレードを処理してください。 詳しくは、[&#x200B; サービスの設定](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/configure/service/services-yaml)を参照してください。

**[!DNL Adobe Commerce as a Cloud Service]への移行を選択した場合：**

Adobeには、[!DNL Adobe Commerce as a Cloud Service]への移行にかかるコストと時間を削減するツールが用意されています。 無料でご利用いただけます。 これらのツールは、移行にのみ適用されます。 Adobe Commerce on Cloud バージョンのアップグレードには使用されません。 移行パスとフェーズを含む完全な移行ガイドについては、[移行の概要](https://experienceleague.adobe.com/ja/docs/commerce/cloud-service/migration/overview)を参照してください。

* **移行評価：** カスタマイズの移行複雑さを評価します。 [移行評価ツールの概要](https://experienceleague.adobe.com/ja/docs/commerce/cloud-service/migration/migration-tools/assessment)を参照してください。

* **データ移行：** [一括および増分データ移行ツール &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce/cloud-service/migration/migration-tools/bulk-data/migration-tool)は、データを新しい[!DNL Adobe Commerce as a Cloud Service]環境に移動します。

* **AIを活用した移行と開発ツール：** Edge Delivery Servicesを搭載したAdobe Developer App BuilderとCommerce Storefrontは、ストアフロントの近代化と拡張機能の再プラットフォーム化を加速するのに役立ちます。

ご不明な点がある場合は、アカウントチームにお問い合わせいただくか、[&#x200B; サポートサービス &#x200B;](https://experienceleague.adobe.com/ja/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide?lang=en#submit-ticket)にお問い合わせください。

>[!MORELIKETHIS]
>
>* [&#x200B; ライフサイクルポリシー](lifecycle-policy.md)
>* [Adobe Commerce on Cloud](version-upgrade-enforcement-policy.md)のバージョンアップグレードポリシー
>* [責任セキュリティと運用モデルの共有](../security-and-compliance/shared-responsibility.md)
