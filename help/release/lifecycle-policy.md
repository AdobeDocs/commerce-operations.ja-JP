---
title: ソフトウェアライフサイクルポリシー
description: Adobe Commerce リリースのソフトウェアサポート終了の主な日付について説明します。
exl-id: 9ee4ecc8-d893-412a-a605-5a8606a1b9a9
nudge: true
source-git-commit: ed2757282c079ea7399d4df92000f346aecfbdd8
workflow-type: tm+mt
source-wordcount: '1376'
ht-degree: 1%

---


# Adobe Commerce ライフサイクルポリシー

Adobe Commerce ライフサイクルポリシーを合理化し、お客様のミッションクリティカルなニーズをサポートするために、Adobeでは、各バージョンの一般提供（GA）日から3年間の標準サポートウィンドウを提供し、この期間に品質修正をリリースします。 各リリースのソフトウェアサポート終了の日付と詳細については、[&#x200B; ソフトウェアサポート終了](#end-of-software-support)の表を参照してください。

Adobeでは、Adobe Commerceのサポート期間が3年間または延長されている間にサポート終了に達する可能性があるサードパーティサービスおよびソフトウェアの依存関係（PHPやMySQLなど）に対するセキュリティおよび品質修正は提供されません。 テストおよびサポートされているサードパーティ製テクノロジーの完全な一覧については、[必要システム構成](../installation/system-requirements.md)を参照してください。

## 標準サポート

一般提供（GA）日からの標準の3年間のサポート期間。 標準サポートには、品質修正、セキュリティパッチ、Adobe Commerceのオンコールサポートが含まれています。

- **品質修正** – お客様は、[Adobe Commerce サポート &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide)またはセルフサービス [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)を通じて、品質修正にアクセスできます。

- **セキュリティ修正** - Adobeは、3年間のサポート期間において、累積セキュリティパッチと非累積[個別セキュリティパッチファイル &#x200B;](versioning-policy.md#isolated-security-patch-file)を通じてセキュリティ修正を提供します。

- **ホットフィックス** - ゼロデイ脆弱性などの重大なセキュリティ問題については、最新のパッチまたはセキュリティパッチリリースを使用していない場合でも、Adobeは、サポートされているバージョンのすべてのユーザーに[&#x200B; ホットフィックス &#x200B;](https://support.magento.com/hc/en-us/sections/360003869892-Known-issues-patches-attached-)を提供します。 ホットフィックスは包括的なものではなく、最新のリリースにアップグレードして解決されるすべてのセキュリティ問題を解決するものではありません。

## 拡張サポート

Adobeでは、できるだけ早くアップグレードすることをお勧めします。 ただし、アップグレードプランとビジネスニーズに合わせて柔軟に対応できるように、Adobeでは、バージョン 2.4.6および2.4.7のAdobe Commerceのお客様に追加費用なしで1年間の追加サポートを提供しています。 サポート拡張機能には、コアアプリケーションの品質およびセキュリティパッチが含まれています。 Adobe Commerce 2.4.4および2.4.5 バージョンの拡張サポートは、予定どおり2026年4月と8月に終了します。

>[!NOTE]
>
>Adobeでは、Adobe Commerce Cloud版の強制的なバージョンアップグレードポリシーを導入しています。 2027年6月1日（PT）以降、Adobeでは、サポートされていないバージョンのCommerceを実行しているCloud環境を管理しなくなり、サポートを終了する権利が留保されます。 **&#x200B;**&#x200B;Cloudで実行する場合は、リリースラインの延長サポートの公開日[終了日](lifecycle-policy.md#end-of-support-dates)までに、サポートされているAdobe Commerce バージョンに移行するか、[!DNL Adobe Commerce as a Cloud Service]に移行する必要があります。 適用日、影響を受けるバージョン、およびサポートされていないバージョンに留まる場合の処理については、[Cloud バージョンのアップグレード適用ポリシー](version-upgrade-enforcement-policy.md)を参照してください。

## セキュリティのみの移行期間

1回限りの期間限定の移行期間。2.4.4、2.4.5、および2.4.6のバージョンでのみ使用でき、2025年または2026年に延長サポートが終了しました。 セキュリティのみの移行期間では、限定的な個別のセキュリティ修正のみが提供されます。 Adobe Commerceの品質修正プログラムは提供されていません。 この期間は、標準サポートまたは拡張サポートと同等ではなく、今後も延長されません。 長期的なサポート層ではなく、移行期間として扱ってください。

>[!IMPORTANT]
>
>セキュリティのみの移行期間は、1回限りの例外です。 公開日を超えて延長されることはありません。 セキュリティのみの期間は、長期的なサポート層ではなく、移行時間として扱います。

## サポート終了日

次の表に、Adobe Commerce on Cloud環境の新しいバージョンアップグレードの適用日を含む、各Adobe Commerce バージョンの完全なライフサイクルを示します。

| リリース | 一般提供 | 標準サポートの終了 | 拡張サポートの終了 | セキュリティのみの期間の終了 | [&#x200B; バージョンアップグレードの実施日（クラウドのみ） &#x200B;](version-upgrade-enforcement-policy.md) |
| --------- | ---------------------- | ------------------------ | ------------------------- |-----------------------------| ----------------------------------------------- |
| Adobe Commerce 2.4.9 | 2026年5月12日（PT） | 2029年5月31日（PT） | TBD | 該当なし | TBD |
| Adobe Commerce 2.4.8 | 2025年4月8日（PT） | 2028年5月31日（PT） | TBD | 該当なし | TBD |
| Adobe Commerce 2.4.7 | 2024年4月9日（PT） | 2027年5月31日（PT） | 2028年5月31日（PT） | 該当なし | 2028年6月1日（PT） |
| Adobe Commerce 2.4.6 | 2023年3月14日（PT） | 2026年8月11日（PT） | 2027年8月30日（PT） | 2028年5月31日（PT） | 2028年6月1日（PT） |
| Adobe Commerce 2.4.5 | 2022年8月9日（PT） | 2025年8月12日（PT） | 2026年8月12日（PT） | 2027年5月31日（PT） | 2027年6月1日（PT） |
| Adobe Commerce 2.4.4 | 2022年4月12日（PT） | 2025年4月12日（PT） | 2026年4月14日（PT） | 2027年5月31日（PT） | 2027年6月1日（PT） |

{style="table-layout:auto"}

## サポートタイムライン

サポートタイムラインマップは、各Adobe Commerce リリースラインのサポート期間を四半期ごとに示します。 正確な終了日については、このトピックで前述した表を使用してください。

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
  </tr>
  <tr>
    <td>2.4.4</td>
    <td></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="4" style="background-color:#ffd700;"></td>
    <td colspan="5" style="background-color:#FFBF00"></td>
    <td colspan="10"></td>
  </tr>
  <tr>
    <td>2.4.5</td>
    <td colspan="2"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="4" style="background-color:#ffd700;"></td>
    <td colspan="4" style="background-color:#FFBF00"></td>
    <td colspan="9"></td>
  </tr>
  <tr>
    <td>2.4.6</td>
    <td colspan="4"></td>
    <td colspan="15" style="background-color:#67ac68;"></td>
    <td colspan="4" style="background-color:#ffd700;"></td>
    <td colspan="10"></td>
  </tr>
  <tr>
    <td>2.4.7</td>
    <td colspan="9"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="4" style="background-color:#ffd700;"></td>
    <td colspan="2"></td>
  </tr>
  <tr>
    <td>2.4.8</td>
    <td colspan="13"></td>
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
   <td>標準サポート</td>
  </tr>
  <tr>
   <td style="background-color:#ffd700;"></td>
   <td>拡張サポート</td>
  </tr>
    <tr>
   <td style="background-color:#FFBF00;"> </td>
   <td>拡張セキュリティの修正</td>
  </tr>
 </tbody>
</table>

## プラットフォームの依存関係

サポート対象のCommerce リリースを維持するには、サポート対象のプラットフォームの依存関係も必要です。 Adobeでは、Adobe Commerceのサポート期間が3年または延長されている間にサポート終了に達する可能性のある、サードパーティサービスおよびソフトウェアの依存関係（MariaDB、OpenSearch、Redis、Valkey、RabbitMQなど）に対するセキュリティおよび品質修正は提供されません。 詳しくは、[共有責任セキュリティと運用モデル &#x200B;](../security-and-compliance/shared-responsibility.md)を参照してください。

お客様は、積極的にサポートされているバージョンに対するすべてのサードパーティの依存関係とプラットフォームサービスを維持する責任があります。 テストおよびサポートされているサードパーティ製テクノロジーの完全な一覧については、[必要システム構成](../installation/system-requirements.md)を参照してください。

>[!IMPORTANT]
>
>サポートされていない依存関係バージョンを実行すると、Adobeで解決できないCloud インスタンスのセキュリティ上の脆弱性が発生する可能性があります。 このような場合、Adobeは、影響を受けるソフトウェア依存関係のアップグレードを実施する権利、またはアップグレードが不可能な場合にインスタンスを解約する権利を留保します（Adobe Commerceのバージョンサポートのステータスに関係なく）。

## PHPのサポート終了とPCI認定

お客様は、お客様の環境で使用されているPHP バージョンのサポートステータスを監視する責任があります。

古いCommerceのリリースラインで使用されている以下のPHP バージョンは、PCI認定に直接的な影響を与えるか、サポート終了に達する予定です。

| PHP バージョン | サポート終了日 | 影響を受けるCommerce バージョン | PCI認定の影響 |
| ------------- | ------------------ | ---------------------------- | ------------------------ |
| PHP 8.1 | 2025年12月31日（PT） | 2.4.4、2.4.5、および2.4.6 （PHP 8.1が使用されている場合） | PCI コンプライアンスがリスクにさらされる – PHP 8.1がサポート終了の日付を過ぎると、PHPのセキュリティ脆弱性が修正を受け取らない可能性があり、PCI コンプライアンスがリスクにさらされます。 コンプライアンスステータスを評価し、アップグレードを優先する。 |
| PHP 8.2 | 2026年12月31日（PT） | 2.4.6 （PHP 8.2が使用されている場合） | PCI認定のリスクが2026年末から発生 – PCI認定を維持するため、2026年末までにアップグレードまたは移行を計画している。 |

{style="table-layout:auto"}

>[!IMPORTANT]
>
>**PCI コンプライアンス通知：** PCI コンプライアンスは、販売者が評価する責任です。 Adobeでは、影響を受けるバージョンのマーチャントは、適格なセキュリティ担当者と相談し、サポート対象のCommerce バージョンとサポート対象のPHP バージョンへの移行を優先することを強くお勧めします。 PHP サポートのタイムラインについては、[PHP サポート対象バージョン &#x200B;](https://www.php.net/supported-versions.php)および[PHP提供終了](https://www.php.net/eol.php)を参照してください。

## アップグレードと移行のオプション

サポート終了日に近づいている、またはサポート終了日を過ぎているバージョンの場合は、今すぐアクションを実行してください。 サポートされていないバージョンを維持すると、セキュリティの脆弱性、コンプライアンスの問題、サポートの損失のリスクが生じます。 Adobeには、サポートされているリリースに移行するための次のパスが用意されています。

### おすすめのパス：Adobe Commerce as a Cloud Serviceへの移行

[!DNL Adobe Commerce as a Cloud Service]は、Adobeの次世代型ホステッド コマース プラットフォームであり、Adobeの推奨される長期的な目的地は、すべてのAdobe Commerce on Cloudのお客様です。

- Adobeは、あらゆるインフラストラクチャ、パッチ適用、アップグレードを自動的に管理します。
- サポートされ、コンプライアンスを遵守したインフラストラクチャにより常に業務を進めている。
- Adobeの最新機能である、AIを活用したマーチャンダイジング、コンポーザブルストアフロントアーキテクチャ、Adobe Experience Cloudとのネイティブ統合にアクセスできます。
- 定期的なアップグレードサイクルを排除できます。

移行の評価を開始するには、Adobe アカウントチームにお問い合わせください。 詳しくは、[Adobe Commerce as a Cloud Service](https://experienceleague.adobe.com/en/docs/commerce/cloud-service/overview)を参照してください。

### 代替パス：サポート対象のAdobe Commerce オンクラウド版またはオンプレミス リリースへのアップグレード

[!DNL Adobe Commerce as a Cloud Service]にすぐに移行できない場合は、現在サポートされている最新のAdobe Commerce Cloud版リリースにアップグレードできます。 これにより、既存のCommerce on Cloud デプロイメントモデルを維持しながら、完全にサポートされた最新のインフラストラクチャスタックに移行できます。

このパスでは、今後のアップグレードの義務がなくなるわけではありません。 Adobe Commerce on Cloud デプロイメントを使用しているお客様は、リリースラインがバージョンアップグレードの実施日に達すると、アップグレードを続行する必要があります。
