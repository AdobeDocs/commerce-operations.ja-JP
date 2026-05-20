---
title: Adobe Commerce ライフサイクルポリシー
description: Adobe Commerceのサポート期間、サポート終了およびクラウドの実施日、移行規定、サポート対象リリースへのパスについて説明します。
exl-id: 9ee4ecc8-d893-412a-a605-5a8606a1b9a9
source-git-commit: 620523021580a9dba44e0e2041d8100761b8bce1
workflow-type: tm+mt
source-wordcount: '1526'
ht-degree: 0%

---


# Adobe Commerce ライフサイクルポリシー

Adobe Commerceでは、ソフトウェアライフサイクルポリシーに従って、安全なバージョンでサポートされていることを確認します。 従来のリリースラインを利用している場合、このライフサイクルのどこに位置するのかを把握し、実施の期限を守るために行動することは非常に重要です。 このトピックでは、サポート層の定義、サポート終了と適用日、サポート終了に近づくバージョンの移行規定、サポートされているリリースに残るパスについて説明します。

>[!IMPORTANT]
>
>Adobeでは、Adobe Commerce クラウド版（PaaS）の強制的なバージョンアップグレードポリシーを導入しています。 **2027年6月1日**&#x200B;以降、Adobeは、サポートされていないCommerce バージョンを実行しているCloud環境のメンテナンスを停止し、それらを非アクティブ化する権利を留保します。 Cloud （PaaS）で実行する場合は、リリースラインの延長サポート [&#128279;](lifecycle-policy.md#end-of-support-dates)の公開日終了日までに、サポートされているAdobe Commerce バージョンに移行するか、[!DNL Adobe Commerce as a Cloud Service]に移行する必要があります。 適用日、影響を受けるバージョン、およびサポートされていないバージョンに留まる場合の処理については、[Cloud バージョンのアップグレード適用ポリシー](version-upgrade-enforcement-policy.md)を参照してください。

## サポート層について

Adobe Commerceでは、リリースラインの3つのサポート層を定義しています。 次の節では、各層について説明します。

### 定期的なサポート

一般提供（GA）日からの標準の3年間のサポート期間。 定期的なサポートには、品質修正、セキュリティパッチ、Adobe Commerceのオンコールサポートが含まれます。

- **品質修正** – お客様は、[Adobe Commerce サポート &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide)またはセルフサービス [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)を通じて、品質修正にアクセスできます。

- **セキュリティ修正** - Adobeは、3年間のサポート期間において、累積セキュリティパッチと非累積[個別セキュリティパッチファイル &#x200B;](versioning-policy.md#isolated-security-patch-file)を通じてセキュリティ修正を提供します。

- **ホットフィックス** - ゼロデイ脆弱性などの重大なセキュリティ問題については、最新のパッチまたはセキュリティパッチリリースを使用していない場合でも、Adobeは、サポートされているバージョンのすべてのユーザーに[&#x200B; ホットフィックス &#x200B;](https://support.magento.com/hc/en-us/sections/360003869892-Known-issues-patches-attached-)を提供します。 ホットフィックスは包括的なものではなく、最新のリリースにアップグレードして解決されるすべてのセキュリティ問題を解決するものではありません。

### 拡張サポート

通常のサポートを超える特定のリリースラインで利用できる1年間のサポート拡張機能。 品質およびセキュリティパッチが含まれています。 Adobe Commerceのお客様のみが利用できます。Magento Open Sourceでは利用できません。

### セキュリティのみの移行期間

延長サポートが2025年または2026年に終了した特定のバージョンで利用できる、1回限りの期間限定の移行期間。 セキュリティのみの移行期間では、限定的な個別のセキュリティ修正のみが提供されます。 Adobe Commerce オンコールサポートは含まれていません。 この期間は、通常または延長されたサポートと同等ではなく、今後も延長されません。 長期的なサポート層ではなく、移行期間として扱ってください。 [&#x200B; セキュリティのみの移行規定](#security-only-transitional-provisions)を参照してください。

## サポート終了日

次の表は、Adobe Commerce on Cloud （PaaS）環境の新しいバージョンアップグレードの適用日を含む、各Adobe Commerce バージョンの完全なライフサイクルを示しています。

| リリース | 一般提供 | 定期的なサポートの終了 | 拡張サポートの終了 | セキュリティのみの期間の終了 | [&#x200B; バージョンアップグレードの実施日（クラウドのみ） &#x200B;](version-upgrade-enforcement-policy.md) |
|---------|----------------------|------------------------|-------------------------|-----------------------------|-----------------------------------------------|
| Adobe Commerce 2.4.9 | 2026年5月12日（PT） | 2029年5月31日（PT） | TBD | 該当なし | TBD |
| Adobe Commerce 2.4.8 | 2025年4月8日（PT） | 2028年5月31日（PT） | TBD | 該当なし | TBD |
| Adobe Commerce 2.4.7 | 2024年4月9日（PT） | 2027年5月31日（PT） | 2028年5月31日（PT） | 該当なし | 2028年6月1日（PT） |
| Adobe Commerce 2.4.6 | 2023年3月14日（PT） | 2026年8月11日（PT） | 2027年8月30日（PT） | 2028年5月31日（PT） | 2028年6月1日（PT） |
| Adobe Commerce 2.4.5 | 2022年8月9日（PT） | 2025年8月12日（PT） | 2026年8月12日（PT） | 2027年5月31日（PT） | 2027年6月1日（PT） |
| Adobe Commerce 2.4.4 | 2022年4月12日（PT） | 2025年4月12日（PT） | 2026年4月14日（PT） | 2027年5月31日（PT） | 2027年6月1日（PT） |

{style="table-layout:auto"}

リリースラインがこれらの日付に近づいている、または過ぎている場合は、[&#x200B; アップグレードと移行のオプション &#x200B;](#upgrade-and-migration-options)を参照してください。 クラウドの適用の詳細については、[&#x200B; クラウド バージョンのアップグレードの適用ポリシー](version-upgrade-enforcement-policy.md)を参照してください。

### 四半期ごとのタイムラインのサポート

このグラフを使用して、リリースライン間で重複するサポートウィンドウを確認します。 正確な終了日については、上記の表を参照してください。 2.4.8および2.4.9の拡張サポートは未定であり、表示されません。

<table style="table-layout:auto">
<thead>
  <tr>
    <th colspan="1"></th>
    <th colspan="4">2022</th>
    <th colspan="4">2023</th>
    <th colspan="4">2024</th>
    <th colspan="4">2025</th>
    <th colspan="4">2026</th>
    <th colspan="4">2027</th>
    <th colspan="4">2028</th>
    <th colspan="4">2029</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Commerce</td>
    <td>Q1</td>
    <td>Q2</td>
    <td>Q3</td>
    <td>Q4</td>
    <td>Q1</td>
    <td>Q2</td>
    <td>Q3</td>
    <td>Q4</td>
    <td>Q1</td>
    <td>Q2</td>
    <td>Q3</td>
    <td>Q4</td>
    <td>Q1</td>
    <td>Q2</td>
    <td>Q3</td>
    <td>Q4</td>
    <td>Q1</td>
    <td>Q2</td>
    <td>Q3</td>
    <td>Q4</td>
    <td>Q1</td>
    <td>Q2</td>
    <td>Q3</td>
    <td>Q4</td>
    <td>Q1</td>
    <td>Q2</td>
    <td>Q3</td>
    <td>Q4</td>
    <td>Q1</td>
    <td>Q2</td>
    <td>Q3</td>
    <td>Q4</td>
  </tr>
  <tr>
    <td>2.4.4</td>
    <td></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="4" style="background-color:#ffd700;"></td>
    <td colspan="4" style="background-color:#FFBF00;"></td>
    <td colspan="10"></td>
  </tr>
  <tr>
    <td>2.4.5</td>
    <td colspan="2"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="4" style="background-color:#ffd700;"></td>
    <td colspan="3" style="background-color:#FFBF00;"></td>
    <td colspan="10"></td>
  </tr>
  <tr>
    <td>2.4.6</td>
    <td colspan="4"></td>
    <td colspan="15" style="background-color:#67ac68;"></td>
    <td colspan="4" style="background-color:#ffd700;"></td>
    <td colspan="3" style="background-color:#FFBF00;"></td>
    <td colspan="6"></td>
  </tr>
  <tr>
    <td>2.4.7</td>
    <td colspan="9"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="4" style="background-color:#ffd700;"></td>
    <td colspan="6"></td>
  </tr>
  <tr>
    <td>2.4.8</td>
    <td colspan="13"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="6"></td>
  </tr>
  <tr>
    <td>2.4.9</td>
    <td colspan="17"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="2"></td>
  </tr>
</tbody>
</table>

**キー**

<table style="table-layout:auto">
 <tbody>
  <tr>
   <td style="background-color:#67ac68;"></td>
   <td>定期的なサポート</td>
  </tr>
  <tr>
   <td style="background-color:#ffd700;"></td>
   <td>拡張サポート</td>
  </tr>
    <tr>
   <td style="background-color:#FFBF00;"> </td>
   <td>セキュリティのみの移行期間</td>
  </tr>
 </tbody>
</table>

## 安全保障に関する暫定規定 {#security-only-transitional-provisions}

2.4.4、2.4.5、および2.4.6 バージョンの1回限りの対策として、2025年と2026年にすでに終了した拡張サポートを含むAdobeでは、移行またはアップグレードを計画および実行する時間を追加するために、次の移行規定が提供されます。 これらの規定は、PaaS環境の[Cloud バージョンのアップグレードの適用](version-upgrade-enforcement-policy.md)を置き換えるものではありません。 公開日よりも前に、アップグレードまたは移行する必要があります。

| バージョン | 経過規定 | 期間 | 含まれているもの | 含まれていないもの |
|---------|------------------------|--------|------------------|----------------------|
| 2.4.4および2.4.5 | セキュリティのみの移行期間 | 2027年5月31日（PT）まで | ケース・バイ・ケースの限定的な個別のセキュリティ修正 | Adobe Commerce オンコールサポート、品質修正、プラットフォーム依存関係の更新 |
| 2.4.6 | 拡張サポート + セキュリティのみの移行期間 | 2027年8月30日までサポートを延長しました。 2028年5月31日までのセキュリティのみの期間。 | 拡張サポート期間：品質およびセキュリティパッチ。 セキュリティのみの期間：孤立したセキュリティ修正が限定的です。 | セキュリティのみの期間中：Adobe Commerce オンコールサポート、品質修正、プラットフォーム依存関係の更新 |

{style="table-layout:auto"}

>[!IMPORTANT]
>
>セキュリティのみの移行期間は、1回限りの例外です。 公開日を超えて延長されることはありません。 セキュリティのみの期間は、長期的なサポート層ではなく、移行時間として扱います。

## プラットフォームの依存関係

サポート対象のCommerce リリースを維持するには、サポート対象のプラットフォームの依存関係も必要です。 Adobeでは、サードパーティのサービスおよびソフトウェアの依存関係（PHP、MariaDB、OpenSearch、Redis、Valkey、RabbitMQなど）に関するセキュリティおよび品質修正は提供されません。これらの問題は、Adobe Commerceのサポート期間が3年または延長されている間にサポート終了になる可能性があります。

お客様は、積極的にサポートされているバージョンに対するすべてのサードパーティの依存関係とプラットフォームサービスを維持する責任があります。 テストおよびサポートされているサードパーティ製テクノロジーの完全な一覧については、[必要システム構成](../installation/system-requirements.md)を参照してください。

Adobeでは、サポートされていない依存関係バージョンを実行するデプロイメントに対するセキュリティサポートやサポートは提供されていません。 詳しくは、[共有責任セキュリティと運用モデル &#x200B;](../security-and-compliance/shared-responsibility.md)を参照してください。

>[!IMPORTANT]
>
>サポートされていない依存関係バージョンを実行すると、Adobeで解決できないCloud インスタンスのセキュリティ上の脆弱性が発生する可能性があります。 このような場合、Adobeは、影響を受けるソフトウェア依存関係のアップグレードを実施する権利、またはアップグレードが不可能な場合にサービスを無効にする権利を留保します（Adobe Commerceのバージョンサポートのステータスに関係なく）。

## PHPのサポート終了とPCI認定

お客様は、お客様の環境で使用されているPHP バージョンのサポートステータスを監視する責任があります。

古いCommerceのリリースラインで使用されている以下のPHP バージョンは、PCI認定に直接的な影響を与えるか、サポート終了に達する予定です。

| PHP バージョン | サポート終了日 | 影響を受けるCommerce バージョン | PCI認定の影響 |
|-------------|------------------|----------------------------|------------------------|
| PHP 8.1 | 2025年12月31日（PT） | 2.4.4、2.4.5、および2.4.6 （PHP 8.1が使用されている場合） | PCI コンプライアンスがリスクにさらされる – PHP 8.1がサポート終了の日付を過ぎると、PHPのセキュリティ脆弱性が修正を受け取らない可能性があり、PCI コンプライアンスがリスクにさらされます。 コンプライアンスステータスを評価し、アップグレードを優先する。 |
| PHP 8.2 | 2026年12月31日（PT） | 2.4.6 （PHP 8.2が使用されている場合） | PCI認定のリスクが2026年末から発生 – PCI認定を維持するため、2026年末までにアップグレードまたは移行を計画している。 |

{style="table-layout:auto"}

### PCI認定のお知らせ

PCI認定の取得は、販売者の評価責任です。 Adobeでは、影響を受けるバージョンのマーチャントは、適格なセキュリティ担当者と相談し、サポート対象のCommerce バージョンとサポート対象のPHP バージョンへの移行を優先することを強くお勧めします。 PHP サポートのタイムラインについては、[PHP サポート対象バージョン &#x200B;](https://www.php.net/supported-versions.php)および[PHP提供終了](https://www.php.net/eol.php)を参照してください。

## アップグレードと移行のオプション

サポート終了日に近づいている、またはサポート終了日を過ぎているバージョンの場合は、今すぐアクションを実行してください。 サポートされていないバージョンを維持すると、セキュリティの脆弱性、コンプライアンスの問題、サポートの損失のリスクが生じます。 Adobeには、サポートされているリリースに移行するための次のパスが用意されています。

### 推奨パス：Adobe Commerce as a Cloud Service（ACCS）への移行

[!DNL Adobe Commerce as a Cloud Service]は、Adobeの次世代型ホステッド コマース プラットフォームであり、Adobeの推奨される長期的な目的地は、すべてのAdobe Commerce on Cloudのお客様です。

- Adobeは、あらゆるインフラストラクチャ、パッチ適用、アップグレードを自動的に管理します。
- サポートされ、コンプライアンスを遵守したインフラストラクチャにより常に業務を進めている。
- Adobeの最新機能である、AIを活用したマーチャンダイジング、コンポーザブルストアフロントアーキテクチャ、Adobe Experience Cloudとのネイティブ統合にアクセスできます。
- 定期的なアップグレードサイクルを排除できます。

移行の評価を開始するには、Adobe アカウントチームにお問い合わせください。 詳しくは、[Adobe Commerce as a Cloud Service](https://experienceleague.adobe.com/ja/docs/commerce/cloud-service/overview)を参照してください。

### 代替パス：サポート対象のAdobe Commerce オンクラウド版またはオンプレミス リリースへのアップグレード

すぐに[!DNL Adobe Commerce as a Cloud Service]に移行できない場合は、現在サポートされている最新のAdobe Commerce オンプレミスまたはクラウドリリースにアップグレードできます。 これにより、既存のPaaS デプロイメントモデルを維持しながら、完全にサポートされた最新のインフラストラクチャスタックに移行できます。

このパスでは、今後のアップグレードの義務がなくなるわけではありません。 PaaSを使用しているお客様は、リリースラインがバージョンアップグレードの実施日に達すると、アップグレードを継続する必要があります。
