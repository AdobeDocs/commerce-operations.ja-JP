---
title: ソフトウェアのライフサイクルポリシー
description: Adobe Commerce リリースのソフトウェアサポート終了の主な日付について説明します。
exl-id: 9ee4ecc8-d893-412a-a605-5a8606a1b9a9
source-git-commit: 7b32ed40efb7e72810f571c8b4b71a77c8aa6a20
workflow-type: tm+mt
source-wordcount: '521'
ht-degree: 4%

---


# Adobe Commerce ライフサイクルポリシー

Adobe Commerce 2.4.4 以降のリリースの場合：

- Adobe Commerceのライフサイクルポリシーを合理化し、お客様のミッションクリティカルなニーズをサポートするために、Adobeでは、Adobe Commerce 2.4.4 以降の一般提供（GA）日から 3 年にサポートウィンドウを拡大しました。 Adobeは、2.4.4 以降のリリースに対して 3 年間のサポート期間中、質の高い修正を提供します。 お客様は、[Adobe Commerce サポートに問い合わせるか ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide) バージョンが品質サポートの対象である場合はセルフサービス [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) を通じて、品質修正プログラムにアクセスできます。 次の表に、Adobe Commerce リリースラインのソフトウェアサポート終了日を示します。

- Adobeは、3 年間のサポート期間を対象としたセキュリティパッチリリースにより、セキュリティ修正を提供します。

- ゼロデイ脆弱性などの重要なセキュリティの問題については、最新のパッチまたはセキュリティパッチリリースに準拠していない場合でも、Adobeでは、サポート対象のバージョンを使用するすべてのお客様に [ ホットフィックス ](https://support.magento.com/hc/en-us/sections/360003869892-Known-issues-patches-attached-) を提供しています。 なお、ホットフィックスは包括的ではなく、最新リリースにアップグレードすることで解決されるすべてのセキュリティ問題に対応するわけではありません。

- Adobeでは、お客様がAdobe Commerceに対して 3 年間のサポートを受けている間に提供が終了する可能性のある、サードパーティのサービスやソフトウェアの依存関係（PHP や MySQL など）に対するセキュリティおよび品質の修正を提供していません。 テスト済みおよびサポート済みのサードパーティテクノロジーの完全なリストについては、[ システム要件 ](../installation/system-requirements.md) を参照してください。

- Adobeは、サードパーティのサービスおよびソフトウェアの依存関係との互換性を提供しますが、お客様のAdobe Commerceのサポート期間は、セキュリティのみを対象とするパッチリリースの 3 年間です。ただし、後方互換性のない変更を加えることなくサポートできる場合に限ります。

## 拡張サポート

Adobeでは、できるだけ早くアップグレードすることをお勧めします。 ただし、アップグレードプランとビジネスニーズに準拠する柔軟性を高めるために、Adobeでは、バージョン 2.4.4 および 2.4.5 のAdobe Commerceのお客様に対して、追加コストなしで 1 年間のサポート延長を提供します。サポート拡張機能には、コアアプリケーションの品質およびセキュリティパッチが最長 1 年間含まれます。

>[!NOTE]
>
>拡張サポートは、Adobe Commerceのお客様のみが利用できます。 Magento Open Sourceコードベースには使用できません。

## ソフトウェアサポートの終了

| リリース | 一般公開 | 標準サポートの終了 <sup>1</sup> | 拡張サポートの終了 | 依存する PHP バージョン | 依存する MariaDB バージョン |
|----------------------|----------------------|------------------------------------|-------------------------|-----------------------|------------------------------|
| Adobe Commerce 2.4.7 | 2024 年 4 月 9 日（Pt） | 2027 年 4 月 9 日（Pt） | 該当なし | 8.2 および 8.3 | 10.6 |
| Adobe Commerce 2.4.6 | 2023 年 3 月 14 日（Pt） | 2026 年 8 月 11 日 <sup>2</sup> | 該当なし | 8.1 および 8.2 | 10.6 |
| Adobe Commerce 2.4.5 | 2022 年 8 月 9 日（Pt） | 2025 年 8 月 9 日（Pt） | 2026 年 8 月 11 日（Pt） | 8.1 | 10.6<sup>3</sup> |
| Adobe Commerce 2.4.4 | 2022 年 4 月 12 日（Pt） | 2025 年 4 月 12 日（Pt） | 2026 年 4 月 14 日（Pt） | 8.1 | 10.6<sup>4</sup> |

{style="table-layout:auto"}

>[!NOTE]
>
>- <sup>1</sup> ソフトウェアのサポート終了には、品質修正の終了とセキュリティ修正の終了の両方が含まれます。
>- <sup>2</sup> 2.4.5 の拡張サポートの終了に合わせて更新されました。
>- <sup>3</sup> 2.4.5-p11 セキュリティパッチ以降。
>- <sup>4</sup> 2.4.4-p12 セキュリティパッチ以降。
>- [ ソフトウェア ライフサイクル ポリシー ](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf) を参照してください。

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
    <td colspan="4" style="background-color:#ffd700;"></td>
    <td colspan="6"></td>
  </tr>
  <tr>
    <td>2.4.5</td>
    <td colspan="2"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="4" style="background-color:#ffd700;"></td>
    <td colspan="6"></td>
  </tr>
  <tr>
    <td>2.4.6</td>
    <td colspan="4"></td>
    <td colspan="15" style="background-color:#67ac68;"></td>
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
   <td style="background-color:#67ac68;"></td>
   <td>定期的なサポート</td>
  </tr>
  <tr>
   <td style="background-color:#ffd700;"></td>
   <td>拡張サポート</td>
  </tr>
 </tbody>
</table>
