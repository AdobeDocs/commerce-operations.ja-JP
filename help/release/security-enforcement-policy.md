---
title: セキュリティポリシー：必要なアクションと期限
description: 期限、必要なアクション、リスクなど、Cloud版およびソフトウェアの依存関係でサポートされていないAdobe Commerceのセキュリティを適用する方法について説明します。
TQID: 'https://experienceleague.adobe.com/0JX-Z-dRjsiQk5jO-LLRi-J4GWdylTh4pOfXRPOabxs'
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
badgePaas: label="Adobe Commerce クラウド版のみ" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Adobe Commerce Cloud バージョン 2.4.4 ～ 2.4.9にのみ適用"
nudge: true
source-git-commit: 7512d5cd3fa1917c87b53e25ca69a3dc3c813727
workflow-type: tm+mt
source-wordcount: 1985
ht-degree: 0%

---

# セキュリティポリシー：必要なアクションと期限

Adobeでは、サポートされているソフトウェア依存関係バージョンやサポートされているAdobe Commerce バージョンなど、Adobe Commerce on Cloud環境のセキュリティ要件が適用されます。 このページでは、何が必要か、施行の日付、要件が満たされない場合の処理について説明します。

## 何が起こっていますか？

Adobeの企業セキュリティポリシーでは、AdobeでホストされているすべてのAdobe Commerce環境が、以下を含む安全でコンプライアンスに準拠したソフトウェア上で動作する必要があります。

1. サポートされているすべてのサードパーティソフトウェアの依存関係のバージョン（PHP、MariaDB、Elasticsearch/OpenSearch、Redis、RabbitMQ）

1. 安全でコンプライアンスに準拠したAdobe Commerce Cloud版（バージョン 2.4.8、2.4.9または最新バージョン）

これは、e コマース環境のセキュリティリスクを軽減するためのものです。 [表1](#determine-your-required-actions)の期限までにこれらの要件を満たさない環境では、ストアフロントをオフラインにして、インバウンドトラフィックが一時停止されます。 この通知は、実施日を含むセキュリティおよびコンプライアンス要件と見なしてください。

2つのアクションを実行する必要がある場合があります。

1. サードパーティ製ソフトウェアの依存関係がサポートされているかどうかを確認します。 そうでない場合は、サポートされているバージョンにアップグレードしてください。

1. Adobe Commerce Cloud版をサポート対象バージョンにアップグレードする必要があるかどうかを確認します。

以下のAdobe Commerce Cloud版を参照して、必要な機能と要件を確認してください。

1. サードパーティソフトウェアの依存関係

1. Adobe Commerce Cloud版

| 自分のバージョン | サードパーティソフトウェアの依存関係のアップグレード <br> （PHP、MariaDB、Elasticsearch/OpenSearch、Redis、RabbitMQ） <br>*詳細と次の手順については、[&#x200B; アクション 1: サードパーティソフトウェアの依存関係のアップグレード &#x200B;](#action-1-upgrade-third-party-software-dependencies)を参照してください。* | Adobe Commerce バージョンをアップグレードまたは移行する&#x200B;<br>*詳しくは、[&#x200B; アクション 2: Adobe Commerce on Cloud バージョンをアップグレードする必要がある場合](#action-2-if-you-need-to-upgrade-your-adobe-commerce-on-cloud-version)と次の手順*&#x200B;を参照してください。 |
| --- | --- | --- |
| 2.4.4または2.4.5 | 2026年10月30日までに必要です。 | 2027年6月1日までに必要 |
| 2.4.6または2.4.7 | ソフトウェアによっては、2026年10月30日（PT）または2027年5月31日（PT）までに必要となります。 | 2028年6月1日までに必要 |
| 2.4.8または2.4.9 | ソフトウェアによっては、2026年10月30日（PT）または2027年5月31日（PT）までに必要となります。 | 現時点では必要ありません |

**表1：必要なアクションとバージョン別の期限**

## アクションを起こす必要がない

この通知は、次の場合には適用されません。

* Adobe Commerce Cloud バージョン 2.4.8または2.4.9を使用しており、サポート対象のサードパーティソフトウェアを使用している環境を使用しているお客様

* [!DNL Adobe Commerce as a Cloud Service]のお客様

### 実行中のバージョンの確認方法

実行しているバージョンを確認するには、e コマース管理者から次の手順を実行する必要があります。

**お使いのCloud版Adobe Commerceのバージョン**

1. Adobe Commerce管理パネルにログインします。

   現在のバージョンは、管理者ページの右下隅に表示されます。

1. 管理者にバージョンが表示されない場合は、[Adobe Commerce コマンドラインツール &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/config-cli){target="_blank"}を使用してversion コマンドを実行します。

   ```shell
   bin/magento --version
   ```

**ソフトウェア依存関係のバージョン**

1. [Cloud Console](https://console.adobecommerce.com/)にログインします。
1. 関連するプロジェクトを開き、確認する環境を選択します。
1. クラウドインフラストラクチャ上のAdobe Commerceで使用されるサポートされているサービス名とバージョンを定義する`.magento/services.yaml` ファイルで、その環境のサービス構成を確認します。
詳細な手順については、[&#x200B; サービスの設定](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/services/config-services){target="_blank"}のドキュメントを参照してください。

## このセキュリティマンデートが重要な理由

ベンダーサポートを終了したソフトウェアには、セキュリティパッチが適用されなくなりました。つまり、そのソフトウェアの既知のセキュリティ問題は修正できません。 さらに、[Adobe ライフサイクルポリシー](https://experienceleague.adobe.com/en/docs/commerce-operations/release/planning/lifecycle-policy)に従って、

* **Adobe Commerce バージョン 2.4.4および2.4.5**&#x200B;では、2027年5月31日（PT）まで、コアアプリケーションの限定的な個別のセキュリティ修正のみが適用されるようになりました。 この限定的なサポートには、品質の修正、アプリケーション依存関係（PHPなど）の互換性サポート、プラットフォーム依存関係の更新は含まれません

* **Adobe Commerce 2.4.6**&#x200B;は、2027年8月30日（PT）まで延長サポートを受け、2028年5月31日（PT）までコアアプリケーションの限定的な個別のセキュリティ修正のみを受け取ります

* **Adobe Commerce バージョン 2.4.7**&#x200B;は、2027年5月31日まで標準サポートを受け、2028年5月31日まで拡張サポートを受けます

* **Cloud バージョン 2.4.8および2.4.9**&#x200B;のAdobe Commerceは引き続きサポートされており、現時点ではバージョンのアップグレードは必要ありません。

サポートされていないソフトウェアでe コマースストアフロントを運営し続けると、PCI コンプライアンスの維持や顧客データの保護など、ビジネスにとって現実的で成長中のセキュリティリスクが生じます。

>[!IMPORTANT]
>
>お使いの環境が[表1](#determine-your-required-actions)に記載されている期限までに要件を満たさない場合、Adobeは影響を受ける環境へのインバウンドトラフィックを一時停止します。 コマースのストアフロントはオフラインになり、買い物客にはサービスを提供しません。 [&#x200B; アクションが実行されない場合はどうなりますか](#what-happens-if-no-action-is-taken)を参照してください。

## 実行する必要のあるアクションの詳細

### アクション 1: サードパーティ製ソフトウェアの依存関係をアップグレードする

ソフトウェアによっては、サポートされていないソフトウェアの依存関係はすべて、次の表で共有されているタイムラインでアップグレードする必要があります。 [Cloud Console](https://console.adobecommerce.com/)で環境を表示し、これらの[手順](#check-software-dependency-versions)を使用して実行中の依存関係バージョンを確認できます。 ソフトウェア依存関係のアップグレードは、すべてのAdobe Commerce on Cloud バージョン 2.4.4 ～ 2.4.9に適用されます。

| 依存関係 | バージョン | にアップグレードする必要があります | 施行日 |
| --- | --- | --- | --- |
| PHP | 8.1以前 | 8.2以上 | 2027年5月31日（PT） |
| MariaDB/Galera | 10.5以下 | 10.6以上 | 2026年10月30日（PT） |
| MariaDB/Galera | 10.5より大きく10.11より小さい | 10.11以上 | 2027年5月31日（PT） |
| Elasticsearch | 任意のバージョン | OpenSearch:<br><br>- 2.4.4および2.4.5のお客様のバージョン 2.19<br>- 2.4.6以降のお客様のバージョン 3。 | 2026年10月30日（PT） |
| OpenSearch | 1.x | 2.4.4および2.4.5のお客様のバージョン 2.19。<br>2.4.6以降のお客様のバージョン 3。 | 2027年5月31日（PT） |
| Redis | 5以下 | Valkey 8以上 | 2027年5月31日（PT） |
| RabbitMQ | 3.9以前 | 3.13以上 | 2026年10月30日（PT） |
| RabbitMQ | 3.9より大きく3.13より小さい | 4.3以上 | 2027年5月31日（PT） |

**表2: ソフトウェア依存関係のアップグレード要件**

#### サードパーティ製ソフトウェアの依存関係アップグレードの準備

Adobeを使用すると、これらのソフトウェアの依存関係を直接アップグレードできます。

* **はじめに：** アップグレードが必要な環境と関連する依存関係が一覧表示された[&#x200B; サポートチケット &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket)を開きます。 少なくとも30日前にチケットを開き、当社のチームが作業をスケジュールできるようにします。

* **ダウンタイム：** Adobeは、スケジュールを設定するときに、想定されるウィンドウを確定します。

* **テスト：**&#x200B;実稼動以外の環境を実稼動前にアップグレードして検証します。 チェックアウト、検索、カート、その他のカスタム統合を検証します。 要件はすべての環境に適用されるので、実稼動環境ではなく、すべての環境をアップグレードすることを計画してください。

* **互換性：**&#x200B;これらの変更のほとんどは、同じソフトウェア内のバージョンのアップグレードであり、リスクは低くなります。 以下は注意が必要です。

  * **ElasticsearchからOpenSearch**&#x200B;および&#x200B;**RedisからValkey**&#x200B;への移行は、バージョンのアップグレードではなく、別のソフトウェアへの移行です。 元のサービスを参照するカスタムコード、拡張機能、設定を更新する必要がある場合があります。
  * **PHP 8.1から8.2**&#x200B;は、カスタムコードとサードパーティの拡張機能で非推奨化が表示される可能性があります。

サードパーティの拡張機能を使用している場合は、現在のリリースがターゲットバージョンをサポートしていることを拡張機能ベンダーに確認します。 ソリューションインテグレーターと連携する場合は、その人と一緒に計画や検証に参加させます。

### アクション 2: Adobe Commerce Cloud版をアップグレードする必要がある場合：

（i）サポート対象のAdobe Commerce Cloud版へのアップグレードまたは（ii）Adobe Commerce as a Cloud Service（Adobeのフルマネージドコマースプラットフォーム）への移行を選択できます

現在のバージョンの適用日は、どのオプションを選択しても適用されます。

| 現在のバージョン | アクション | 施行日 |
| --- | --- | --- |
| Cloud バージョン 2.4.4または2.4.5でのAdobe Commerceの使用 | Adobe Commerce Cloud版バージョン 2.4.9 （または最新バージョン）へのアップグレードまたはAdobe Commerce as a Cloud Serviceへの移行 | 2027年6月1日（PT） |
| Cloud バージョン 2.4.6または2.4.7でのAdobe Commerceの使用 | Adobe Commerce Cloud版バージョン 2.4.9 （または最新バージョン）へのアップグレードまたはAdobe Commerce as a Cloud Serviceへの移行 | 2028年6月1日（PT） |
| Cloud バージョン 2.4.8または2.4.9でのAdobe Commerceの使用 | 現時点では、Adobe Commerce Cloud版のアップグレードアクションは必要ありません。 アクション 1のソフトウェア依存関係の期限は引き続き適用されます。 | なし |

**表3：現在のAdobe Commerce on Cloud バージョンをアップグレードする必要がある場合のガイドラインと期限**

Adobe Commerce on Cloud バージョン 2.4.9およびAdobe Commerce as a Cloud Serviceの詳細については、次のマトリックスを参照してください。情報に基づいた意思決定を行うことができます。

**表4: Cloud上のAdobe CommerceへのアップグレードとAdobe Commerce as a Cloud Serviceへの移行**

| | Adobe Commerce Cloud版バージョン 2.4.9 | Adobe Commerce as a Cloud Service |
| --- | --- | --- |
| 現状 | 完全なセキュリティ範囲、品質修正、プラットフォーム依存関係のアップデートを含む最新のAdobe Commerce リリース。 | 継続的なイノベーションのために構築され、アップグレードのオーバーヘッドを排除できる、Adobeのフルマネージドコマースプラットフォーム。 [学習を増やす](https://experienceleague.adobe.com/en/docs/commerce/cloud-service/overview)。 |
| 最適です | 今のところ、独自のインフラストラクチャ、アップグレード、パッチを管理し続ける必要があります。 Adobe Commerce as a Cloud Serviceに移行する準備ができたら、いつでも移行できます。 | アップグレードサイクルを大幅に短縮し、総所有コストを削減しながら、Adobeの最新の機能を追加の作業なしで自動的に入手できます。 |
| 主なメリット | 既存の設定を維持しながら、今すぐセキュリティ要件を満たします。 | 高速でエッジ配信のストアフロント、拡張性の高いカタログ、ネイティブのデジタルアセット管理、組み込みの生成AIなど、Adobeが管理するインフラストラクチャ上に構築されています。 |

## 何も行動を起こさなかったらどうなるか。

環境が[上記](#determine-your-required-actions)で共有された適用日までに、これらの要件を満たしていない場合、Adobeは適切なアクションを実行します。 これには、影響を受けるインフラストラクチャへのトラフィックの一時停止が含まれます。これにより、e コマースのストアフロントがオフラインになります。

トラフィックの停止後もコンプライアンスを遵守していない環境が続く場合、Adobeはクラウドサービスを終了し、廃止プロセスを開始する可能性があります。 廃止の結果、ホストされているe コマース環境内のすべてのデータとアセット（すべてのインスタンス、環境、ブランチを含む）が完全に削除され、復元できなくなります。

## Adobeがお客様のビジネスにどのように役立つのかをご案内します

Adobeには、アップグレードや移行を行う場合でも、移行を可能な限りスムーズにするツールとサポートが用意されています。

**Cloud バージョン 2.4.9**&#x200B;でAdobe Commerceにアップグレードする場合

* **アップグレード互換性レポート：** Adobeには、時間とコストの範囲など、Adobe Commerce バージョン 2.4.9へのアップグレードに必要な内容を正確に示す詳細なレポートが用意されています。 [&#x200B; アップグレード互換性レポートを生成](https://supportinsights.adobe.com/commerce/tab/main)。

* **ソフトウェア依存関係のアップグレード：** ソフトウェア依存関係を直接アップグレードできないため、[Adobeのサポートチケット &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket){target="_blank"}を開いて、アップグレードを処理してください。 詳しくは、[&#x200B; サービスの設定](https://experienceleague.adobe.com/en/docs/commerce/cloud-service/configuration/overview){target="_blank"}を参照してください。

**Adobe Commerce as a Cloud Serviceへの移行を選択した場合**

Adobeには、Adobe Commerce as a Cloud Serviceへの移行にかかるコストと時間を削減するツールが用意されています。 これは君には代償の必要はない。 これらのツールは移行にのみ適用されます。Adobe Commerce on Cloudのバージョンのアップグレードには使用されません。 移行パスとフェーズを含む完全な移行ガイドについては、[移行の概要](https://experienceleague.adobe.com/en/docs/commerce/cloud-service/migration/overview)を参照してください。

* **移行評価：** カスタマイズの移行複雑さを評価します。 [移行評価ツールの概要](https://experienceleague.adobe.com/en/docs/commerce/cloud-service/migration/migration-tools/assessment)を参照してください。

* **データ移行：** [一括および増分データ移行ツール &#x200B;](https://experienceleague.adobe.com/en/docs/commerce/cloud-service/migration/migration-tools/bulk-data/migration-tool)を使用すると、データを新しいAdobe Commerce as a Cloud Service環境に移行できます。

* Adobeの[AI支援による移行および開発者ツール &#x200B;](https://developer.adobe.com/commerce/extensibility/developer-agent/) （**[!DNL Adobe Developer App Builder]**&#x200B;および&#x200B;**[!DNL Commerce Storefront powered by Edge Delivery Services]**&#x200B;を含む）は、ストアフロントの近代化と拡張機能の再プラットフォーム化を加速するのに役立ちます。

ご不明な点がある場合は、アカウントチーム、ソリューションアカウントマネージャー、リニューアルスペシャリストにお問い合わせいただくか、[&#x200B; サポートサービス &#x200B;](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide?lang=en#submit-ticket)にお問い合わせください。
