---
title: ソフトウェアのライフサイクルポリシー
description: Adobe Commerce リリースのソフトウェアサポート終了の主な日付について説明します。
exl-id: 9ee4ecc8-d893-412a-a605-5a8606a1b9a9
source-git-commit: 7df5edf2acba706fb01f58cc3749c4a2bf136fc5
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 5%

---


# Adobe Commerce ライフサイクルポリシー

Adobe Commerce 2.4.4 以降のリリースの場合：

- Adobe Commerceのライフサイクルポリシーを合理化し、お客様のミッションクリティカルなニーズをサポートするために、Adobeでは、Adobe Commerce 2.4.4 以降の一般提供（GA）日から 3 年にサポートウィンドウを拡大しました。 Adobeは、2.4.4 以降のリリースに対して 3 年間のサポート期間中、質の高い修正を提供します。 お客様は、[Adobe Commerce サポートに問い合わせるか ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html) バージョンが品質サポートの対象である場合はセルフサービス [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) を通じて、品質修正プログラムにアクセスできます。 Adobe Commerce リリースラインのソフトウェアサポート終了日については、次の表を参照してください。

- Adobeは、3 年間のサポート期間を対象としたセキュリティパッチリリースにより、セキュリティ修正を提供します。

- ゼロデイ脆弱性などの重要なセキュリティの問題については、最新のパッチまたはセキュリティパッチリリースに準拠していない場合でも、Adobeでは、サポート対象のバージョンを使用するすべてのお客様に [ ホットフィックス ](https://support.magento.com/hc/en-us/sections/360003869892-Known-issues-patches-attached-) を提供しています。 ホットフィックスは包括的なものではなく、最新リリースにアップグレードすることで修正されるすべてのセキュリティの問題に対応しているわけではありません。

- Adobeでは、お客様がAdobe Commerceに対して 3 年間のサポートを受けている間に提供が終了する可能性のある、サードパーティのサービスやソフトウェアの依存関係（PHP や MySQL など）に対するセキュリティおよび品質の修正を提供していません。 テスト済みおよびサポート済みのサードパーティテクノロジーの完全なリストについては、[ システム要件 ](../installation/system-requirements.md) を参照してください。

- Adobeは、サードパーティのサービスおよびソフトウェアの依存関係との互換性を提供しますが、お客様のAdobe Commerceのサポート期間は、セキュリティのみを対象とするパッチリリースの 3 年間です。ただし、後方互換性のない変更を加えることなくサポートできる場合に限ります。

## ソフトウェアサポートの終了

| リリース | 一般公開 | ソフトウェア サポート終了 <sup>1</sup> | 依存する PHP バージョン | 依存する MariaDB バージョン |
|----------------------|----------------------|-------------------------------------|-----------------------|------------------------------|
| Adobe Commerce 2.4.7 | 2024 年 4 月 9 日（Pt） | 2027 年 4 月 9 日（Pt） | 8.2 および 8.3 | 10.6 |
| Adobe Commerce 2.4.6 | 2023 年 3 月 14 日（Pt） | 2026 年 3 月 14 日（Pt） | 8.1 および 8.2 | 10.6 |
| Adobe Commerce 2.4.5 | 2022 年 8 月 9 日（Pt） | 2025 年 8 月 9 日（Pt） | 8.1 | 10.5<sup>2</sup> |
| Adobe Commerce 2.4.4 | 2022 年 4 月 12 日（Pt） | 2025 年 4 月 24 日（Pt） | 8.1 | 10.5<sup>3</sup> |

{style="table-layout:auto"}

>[!NOTE]
>
>- <sup>1</sup> ソフトウェアのサポート終了には、品質修正の終了とセキュリティ修正の終了の両方が含まれます。
>- <sup>2</sup> 2.4.5-p8 セキュリティパッチ以降。
>- <sup>3</sup> 2.4.4-p9 セキュリティパッチ以降。
>- [ ソフトウェア ライフサイクル ポリシー ](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf) を参照してください。

<table style="table-layout:auto">
<thead>
  <tr>
    <th colspan="2"></th>
    <th colspan="4">2022</th>
    <th colspan="4">2023</th>
    <th colspan="4">2024</th>
    <th colspan="4">2025</th>
    <th colspan="4">2026</th>
    <th colspan="4">2027</th>
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
  </tr>
  <tr>
    <td>2.4.4</td>
    <td></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="10"></td>
  </tr>
  <tr>
    <td>2.4.5</td>
    <td colspan="2"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="9"></td>
  </tr>
  <tr>
    <td>2.4.6</td>
    <td colspan="4"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="8"></td>
  </tr>
  <tr>
    <td>2.4.7</td>
    <td colspan="9"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="2"></td>
  </tr>
</tbody>
</table>

**キー**

<table style="table-layout:auto">
 <tbody>
  <tr>
   <td style="background-color:#67ac68;">サポート</td>
   <td>Adobe Commerceのセキュリティおよび品質に関するパッチ</td>
  </tr>
  <!-- <tr>
   <td style="background-color:#cd3c3c;">End of software support</td>
   <td>Version that has reached end of software support.</td>
  </tr>
 </tbody> -->
</table>
