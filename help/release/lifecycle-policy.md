---
title: ソフトウェアのライフサイクルポリシー
description: Adobe Commerce リリースのソフトウェアサポート終了の主な日付について説明します。
exl-id: 9ee4ecc8-d893-412a-a605-5a8606a1b9a9
source-git-commit: 2e81a28502d369bc8903e6b9e9154e693260234d
workflow-type: tm+mt
source-wordcount: '612'
ht-degree: 3%

---


# Adobe Commerce ライフサイクルポリシー

Adobe Commerce 2.4.4 以降のリリースの場合：

- Adobe Commerceのライフサイクルポリシーを合理化し、お客様のミッションクリティカルなニーズをサポートするために、Adobeでは、Adobe Commerce 2.4.4 以降の一般提供（GA）日から 3 年にサポートウィンドウを拡大しました。 Adobeは、2.4.4 以降のリリースに対して、3 年間のサポート期間中、品質に関する修正を提供します。 お客様は、[Adobe Commerce サポートに問い合わせるか &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide) バージョンが品質サポートの対象である場合はセルフサービス [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) を通じて、品質修正プログラムにアクセスできます。 次の表に、Adobe Commerce リリースラインのソフトウェアサポート終了日を示します。

- Adobeでは、3 年間のサポート期間を対象に、セキュリティパッチリリースによりセキュリティ修正を提供しています。

- ゼロデイ脆弱性などの重大なセキュリティ問題の場合、Adobeでは、最新のパッチまたはセキュリティパッチリリースに対応していない場合でも、サポート対象のバージョンを使用しているすべてのお客様に対して [&#x200B; ホットフィックス &#x200B;](https://support.magento.com/hc/en-us/sections/360003869892-Known-issues-patches-attached-) を提供します。 なお、ホットフィックスは包括的ではなく、最新リリースにアップグレードすることで解決されるすべてのセキュリティ問題に対応するわけではありません。

- Adobeでは、お客様がAdobe Commerceに対して 3 年間のサポートを受けている間に提供が終了する可能性のある、サードパーティのサービスやソフトウェアの依存関係（PHP や MySQL など）に対するセキュリティおよび品質の修正は提供していません。 テスト済みおよびサポート済みのサードパーティテクノロジーの完全なリストについては、[&#x200B; システム要件 &#x200B;](../installation/system-requirements.md) を参照してください。

- Adobe Commerce on Cloud をご利用のお客様がバージョン 2.4.4 および 2.4.5 を使用している場合、Adobeは PHP 8.1 のライフタイムセキュリティの修正をインフラストラクチャに自動的に適用するため、PHP 8.1 のサポート終了の影響を受けることはありません。 Adobe Commerce 2.4.4 および 2.4.5 を使用しているオンプレミス環境のお客様は、必要に応じてAdobe サポートに連絡して、PHP 8.1 のライフタイムセキュリティパッチをリクエストする必要があります。

- Adobeは、サードパーティのサービスおよびソフトウェアの依存関係との互換性を備えていますが、お客様のAdobe Commerceの 3 年間のサポート期間は、セキュリティのみのパッチリリースの範囲です。ただし、後方互換性のない変更を加えることなくサポートできる場合に限ります。

## 拡張サポート

Adobeでは、できるだけ早くアップグレードすることをお勧めします。 ただし、アップグレードプランとビジネスニーズに準拠する柔軟性を高めるために、Adobeでは、バージョン 2.4.4 および 2.4.5 のAdobe Commerceのお客様に対して、1 年間のサポート延長を無料で提供します。サポート拡張機能には、コアアプリケーションの品質およびセキュリティパッチが最長 1 年間含まれます。

>[!NOTE]
>
>拡張サポートは、Adobe Commerceのお客様のみが利用できます。 Magento Open Source コードベースには使用できません。

## ソフトウェアサポートの終了

| リリース | 一般公開 | 標準サポートの終了 <sup>1</sup> | 拡張サポートの終了 | 依存する PHP バージョン | 依存する MariaDB バージョン |
|----------------------|----------------------|------------------------------------|-------------------------|-----------------------|---------------------------|
| Adobe Commerce 2.4.8 | 2025 年 4 月 8 日（Pt） | 2028 年 4 月 11 日（Pt） | 該当なし | 8.3 および 8.4 | 11.4 |
| Adobe Commerce 2.4.7 | 2024 年 4 月 9 日（Pt） | 2027 年 4 月 9 日（Pt） | 該当なし | 8.2 および 8.3 | 10.11<sup>3</sup> |
| Adobe Commerce 2.4.6 | 2023 年 3 月 14 日（Pt） | 2026 年 8 月 11 日 <sup>2</sup> | 該当なし | 8.1 および 8.2 | 10.11<sup>4</sup> |
| Adobe Commerce 2.4.5 | 2022 年 8 月 9 日（Pt） | 2025 年 8 月 12 日（Pt） | 2026 年 8 月 11 日（Pt） | 8.1 | 10.6<sup>5</sup> |
| Adobe Commerce 2.4.4 | 2022 年 4 月 12 日（Pt） | 2025 年 4 月 12 日（Pt） | 2026 年 4 月 14 日（Pt） | 8.1 | 10.6<sup>6</sup> |

{style="table-layout:auto"}

>[!NOTE]
>
>- <sup>1</sup> ソフトウェアのサポート終了には、品質修正の終了とセキュリティ修正の終了の両方が含まれます。
>- <sup>2</sup> 2.4.5 の拡張サポートの終了に合わせて更新されました。
>- <sup>3</sup> 2.4.7-p6 セキュリティパッチ以降。
>- <sup>4</sup> 2.4.6-p11 セキュリティパッチ以降。
>- <sup>5</sup> 2.4.5-p11 セキュリティパッチ以降。
>- <sup>6</sup> 2.4.4-p12 セキュリティパッチ以降。
>- [&#x200B; ソフトウェア ライフサイクル ポリシー &#x200B;](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf) を参照してください。

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
    <td colspan="10"></td>
  </tr>
  <tr>
    <td>2.4.5</td>
    <td colspan="2"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="4" style="background-color:#ffd700;"></td>
    <td colspan="9"></td>
  </tr>
  <tr>
    <td>2.4.6</td>
    <td colspan="4"></td>
    <td colspan="15" style="background-color:#67ac68;"></td>
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
 </tbody>
</table>
