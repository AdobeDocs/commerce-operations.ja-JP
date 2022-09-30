---
title: ソフトウェアライフサイクルポリシー
description: Adobe Commerceリリースのソフトウェアサポート終了の主な日付について説明します。
source-git-commit: 79f36e3728e6bc436e8093bd4051143a48e681d6
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 5%

---


# Adobe Commerceライフサイクルポリシー

Adobe Commerce 2.4 以降のリリースの場合：

- ライフサイクルポリシーをより効率的に行うため、Adobeは、PHP バージョンのサポート終了日までの 2.4 リリース行に対して、品質の修正を提供します。 お客様は、次の連絡先に問い合わせて品質の修正にアクセスできます [Adobe Commerceサポート](https://developer.adobe.com/commerce/contributor/community/support/) または自己奉仕を通じて [品質パッチツール](https://devdocs.magento.com/quality-patches/tool.html) もし、そのバージョンが品質サポートの対象となる場合に限ります。 Adobe Commerceのリリースラインのソフトウェアサポート終了日については、次の表を参照してください。

- Adobeは、最新のパッチまたはセキュリティパッチリリースを通じてのみセキュリティ修正を提供します。お客様のバージョンが品質サポートの対象となっている場合でも同様です。 品質の修正とは異なり、セキュリティ修正は、サポートされるマイナーリリース内の以前のマイナーリリースや以前のパッチリリースにバックポートできません。

- セキュリティ上の重要な問題（ゼロ日の脆弱性など）に対して、Adobeは [hotfixs](https://support.magento.com/hc/en-us/sections/360003869892-Known-issues-patches-attached-) サポート対象バージョンのすべてのお客様（最新のパッチまたはセキュリティパッチリリースにない場合を含む）に対して。 ホットフィックスは包括的なものではなく、最新のリリースにアップグレードすることで修正されるセキュリティ上の問題には対処しないことに注意する必要があります。

## ソフトウェアサポートの終了

| リリース | リリース日 | ソフトウェアサポートの終了<sup>1</sup> | 依存 PHP バージョン |
| -------------------------------- | ----------------- | ----------------------------------- | --------------------------- |
| Adobe Commerce 2.3 | 2018 年 11 月 29 日 | 2022 年 9 月 9 日<sup>2</sup> | PHP 7.3 および 7.4<sup>3</sup> |
| Adobe Commerce 2.4.0～2.4.3 | 2020 年 7 月 29 日 | 2022 年 11 月 29 日 | PHP 7.4 |
| Adobe Commerce 2.4.4-2.4.6 | 2022 年 4 月 13 日 | 2024 年 11 月 26 日 | PHP 8.1 |

<sup>1 ソフトウェアサポートの終了には、品質に関する修正の終了とセキュリティ修正の終了の両方が含まれます。</sup><br>
<sup>2 2.3 のソフトウェアサポート終了日は、2022 年 3 月 8 日に一般に提供される 2.4.4 リリースにアップグレードするまでの時間を短縮するために、2.3 年 9 月 8 日まで延長されました。</sup><br>
<sup>3 2.3.0-2.3.6 は PHP 7.3 に依存します。2.3.7 は PHP 7.4 に依存します。</sup>

>[!NOTE]
>
>詳しくは、 [ソフトウェアライフサイクルポリシー](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

<table>
<thead>
  <tr>
    <th colspan="2"></th>
    <th colspan="4">2022 年</th>
    <th colspan="4">2023 年</th>
    <th colspan="4">2024 年</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>コマース</td>
    <td>PHP</td>
    <td>第 1 四半期</td>
    <td>第 2 四半期</td>
    <td>第 3 四半期</td>
    <td>第 4 四半期</td>
    <td>第 1 四半期</td>
    <td>第 2 四半期</td>
    <td>第 3 四半期</td>
    <td>第 4 四半期</td>
    <td>第 1 四半期</td>
    <td>第 2 四半期</td>
    <td>第 3 四半期</td>
    <td>第 4 四半期</td>
  </tr>
  <tr>
    <td>2.4.0～2.4.3</td>
    <td style="text-align:center">7.4</td>
    <td colspan="3" style="background-color:#67ac68;"></td>
    <td style="background-color:#cd3c3c;">11 月</td>
    <td colspan="8" ></td>
  </tr>
  <tr>
    <td>2.4.4</td>
    <td rowspan="2" style="text-align:center">8.1</td>
    <td></td>
    <td colspan="10" style="background-color:#67ac68;">3 月</td>
    <td rowspan="2" style="background-color:#cd3c3c;">11 月</td>
  </tr>
  <tr>
    <td>2.4.5</td>
    <td colspan="2"></td>
    <td colspan="9" style="background-color:#67ac68;">8 月</td>
  </tr>
</tbody>
</table>

## キー

<table>
  <thead>
   <tr>
    <th></th>
    <th></th>
   </tr>
  </thead>
 <tbody>
  <tr>
   <td style="background-color:#67ac68;">サポート</td>
   <td>完全にテストされ、サポートされているAdobe。</td>
  </tr>
  <tr>
   <td style="background-color:#cd3c3c;">ソフトウェアサポートの終了</td>
   <td>ソフトウェアサポートの終了に達したバージョン。</td>
  </tr>
 </tbody>
</table>
