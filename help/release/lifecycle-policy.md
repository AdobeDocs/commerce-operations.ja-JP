---
title: ソフトウェアライフサイクルポリシー
description: Adobe Commerce リリースのソフトウェアサポート終了の主な日付について説明します。
exl-id: 9ee4ecc8-d893-412a-a605-5a8606a1b9a9
source-git-commit: 3e7cef954a2be506c6f72e704710d16ed1d9b7a3
workflow-type: tm+mt
source-wordcount: '807'
ht-degree: 2%

---


# Adobe Commerce ライフサイクルポリシー

Adobe Commerce ライフサイクルポリシーを合理化し、お客様のミッションクリティカルなニーズをサポートするために、Adobeでは、各バージョンの一般提供（GA）日から3年間のサポート期間を提供し、この期間に品質修正をリリースします。 各リリースのソフトウェアサポート終了の日付と詳細については、[&#x200B; ソフトウェアサポート終了](#end-of-software-support)の表を参照してください。

3年間のサポート期間中、お客様は以下にアクセスできます。

- **品質修正** – お客様は、[Adobe Commerce サポート &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide)またはセルフサービス [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)を通じて、品質修正にアクセスできます。 次の表に、Adobe Commerceのリリースラインのソフトウェアサポート終了日を示します。

- **セキュリティ修正**-Adobeは、3年間のサポート期間において、累積セキュリティパッチと非累積[個別セキュリティパッチファイル &#x200B;](versioning-policy.md#isolated-security-fixes)を通じてセキュリティ修正を提供します。

- **ホットフィックス** – ゼロデイ脆弱性などの重大なセキュリティ問題については、最新のパッチまたはセキュリティパッチリリースを使用していない場合でも、Adobeは、サポートされているバージョンのすべてのユーザーに[&#x200B; ホットフィックス &#x200B;](https://support.magento.com/hc/en-us/sections/360003869892-Known-issues-patches-attached-)を提供します。 ホットフィックスは包括的なものではなく、最新のリリースにアップグレードして解決されるすべてのセキュリティ問題を解決するものではありません。

Adobeでは、Adobe Commerceのサポート期間が3年間または延長されている間にサポート終了に達する可能性があるサードパーティサービスおよびソフトウェアの依存関係（PHPやMySQLなど）に対するセキュリティおよび品質修正は提供されません。 テストおよびサポートされているサードパーティ製テクノロジーの完全な一覧については、[必要システム構成](../installation/system-requirements.md)を参照してください。

## 拡張サポート

Adobeでは、できるだけ早くアップグレードすることをお勧めします。 ただし、アップグレードプランとビジネスニーズに合わせて柔軟に対応できるように、Adobeでは、Adobe Commerceのお客様がバージョン 2.4.6で追加費用なしで1年間のサポート拡張機能を提供しています。サポート拡張機能には、最大1年間のコアアプリケーションの品質およびセキュリティパッチが含まれます。 Adobe Commerce 2.4.4および2.4.5 バージョンの拡張サポートは、予定どおり2026年4月と8月に終了します。

>[!NOTE]
>
>拡張サポートは、Adobe Commerceのお客様のみが利用できます。 Magento Open Source コードベースでは使用できません。

## ソフトウェアのサポート終了

| リリース | 一般提供 | 通常のサポート終了<sup>1</sup> | 拡張サポートの終了 |
|----------------------|----------------------|------------------------------------|-------------------------|
| Adobe Commerce 2.4.8 | 2025年4月8日（PT） | 2028年5月31日（PT） | 未定 |
| Adobe Commerce 2.4.7 | 2024年4月9日（PT） | 2027年5月31日（PT） | 未定 |
| Adobe Commerce 2.4.6 | 2023年3月14日（PT） | 2026年8月11日（PT） | 2027年8月30日（PT） |
| Adobe Commerce 2.4.5 | 2022年8月9日（PT） | 2025年8月12日（PT） | 2026年8月11日（PT） |
| Adobe Commerce 2.4.4 | 2022年4月12日（PT） | 2025年4月12日（PT） | 2026年4月14日（PT） |

{style="table-layout:auto"}

>[!NOTE]
>
>- <sup>1</sup> Adobe Commerceをご利用のお客様は、延長サポート期間を通じて、引き続き1年間セキュリティおよび品質修正プログラムを受け取ることができます。
>- [&#x200B; ソフトウェアライフサイクルポリシー](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)を参照してください。

## Adobe Commerce 2.4.4および2.4.5の追加のセキュリティ修正

1回限りの例外として、Adobeでは、Adobe Commerce バージョン 2.4.4および2.4.5のセキュリティ修正プロビジョニング期間を延長し、お客様がAdobe Commerce as a Cloud Serviceに移行したり、サポート対象のリリースラインにアップグレードしたりする時間を延長します。

このセキュリティ修正プロビジョニング期間中は、次の点に注意してください。

- **個別セキュリティパッチファイルのみ** – 個別セキュリティパッチファイルは、リリーススケジュールに従ってこれらのバージョンに対してリリースされます。 この期間中、セキュリティパッチリリースは提供されません（新しい – p バージョンは提供されません）。

  分離されたセキュリティパッチファイルを適用するには、分離されたセキュリティ修正プログラムはそのバージョンに対してのみテストされるので、お客様はサポートされているリリースラインの最新のセキュリティ専用パッチリリース（最新の – p バージョン）に属している必要があります。

- **バージョン 2.4.4または2.4.5では、この期間中に品質修正またはエンジニアリング支援** – バグ修正、品質更新（[品質パッチツール &#x200B;](../tools/quality-patches-tool/usage.md)）、またはエンジニアリング支援（[Adobe Commerce サポート &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide)）が提供されません。

- **PCI コンプライアンスは保証されていません：**-2.4.4および2.4.5では、使用期限に達したPHP バージョンを使用しているため、これらのリリースの販売者に対してPCI コンプライアンスを保証することはできません。 これらのバージョンを継続的に実行すると、PCI認定のリスクが生じる可能性があります。

完全なセキュリティカバレッジを維持し、PCI認定を確実に行うには、お客様は現在サポートされているバージョンのAdobe Commerceにできるだけ早くアップグレードするか、[Adobe Commerce as a Cloud Service](https://experienceleague.adobe.com/en/docs/commerce/cloud-service/overview)に移行する必要があります。

| リリース | 一般提供 | 拡張サポートの終了 | セキュリティ修正プロビジョニングの終了 |
|----------------------|----------------------|-------------------------|------------------------------------|
| Adobe Commerce 2.4.5 | 2022年8月9日（PT） | 2026年8月11日（PT） | 2027年5月 |
| Adobe Commerce 2.4.4 | 2022年4月12日（PT） | 2026年4月14日（PT） | 2027年5月 |

{style="table-layout:auto"}

>[!NOTE]
>
>その他のセキュリティ修正は、Adobe Commerceのお客様のみが使用でき、Magento Open Source コードベースでは使用できません。


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
    <td colspan="6"></td>
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
   <td>定期的なサポート</td>
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
