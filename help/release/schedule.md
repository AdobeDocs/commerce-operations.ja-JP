---
title: リリーススケジュール
description: アドビが Adobe Commerce の新機能リリースの発表を予定しているタイミングを学びます。
exl-id: ae1e09cd-966f-44a3-9e4d-b90bb838429d
source-git-commit: e9ef167f5425407f6b1850f0dd913d5d3e2bd628
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 2%

---

# リリーススケジュール

Adobeは、製品のアップグレードをシンプルで予測可能なものにすると同時に、早期導入者に対して改善や新機能をより迅速に提供することの間で適切なバランスを継続的に見つけ出そうと努めています（[ バージョンポリシー ](versioning-policy.md) を参照）。 このスケジュールの目的は、Adobeが実質的な新機能のリリースを発表する予定の日付を指定することです。 これらの機能は、年間を通じて異なる場合があります。 ただし、Adobeでは、このページで指定した日付の間に、拡張ツール、インフラストラクチャ、および SaaS 製品（サービス）の機能強化を定期的かつ継続的にリリースしています。

コア Adobe Commerce PHP アプリケーションのサポート対象の各リリースラインに対するAdobeリリース [ パッチ ](versioning-policy.md#patch-release)。 パッチリリースは、プラットフォームの安全性、信頼性、パフォーマンスを維持するために、コアコードベースをアップグレードする機会です。 機能はコアコードベースには依存せず、[ 外部モジュール、拡張機能、ツールまたは web サービス ](versioning-policy.md#extensibility-infrastructure-and-services-release) から利用できます。

>[!NOTE]
>
>2024 年以降、Adobeはパッチへの「プレリリース」アクセスを提供しなくなりました。 代わりに、2.4.7 以降では、Adobe Commerceのお客様は [ ベータリリース ](beta.md) を使用して、テストや開発の目的で、一般提供される前のコードにアクセスできます。

予定されているリリースの日付を次の表に示します（日付は変更される場合があります）。

<table>
<thead>
  <tr>
    <th>一般公開</th>
    <th>機能</th>
    <th>PHP コア</th>
  </tr>
</thead>
<tfoot>
   <tr>
      <td colspan="3"><strong> 凡例 </strong>
         <ul>
           <li><strong><img alt="B2B 機能アイコン" src="../assets/icons/enterprise.svg"></img> B2B</strong> - Adobe Commerceの B2B 拡張機能の新機能、機能強化およびバグ修正です。 B2B 拡張機能のリリースについて詳しくは、<a href="https://experienceleague.adobe.com/docs/commerce-admin/b2b/release-notes.html">B2B リリースノート </a> を参照してください。</li>
            <li><strong><img alt="拡張機能アイコン" src="../assets/icons/brackets.svg"></img> 拡張機能 </strong> - パッチリリースとは別に提供される、プロセス外の拡張機能のための新しい開発者ツールおよびサービス。 例えば、管理 UI SDK、CommerceのAdobe I/Oイベント、API メッシュなどです。</li>
            <li><strong><img alt="インフラストラクチャ機能アイコン" src="../assets/icons/servers.svg"></img> Infrastructure</strong> - クラウドインフラストラクチャー上のAdobe CommerceおよびCommerce パッケージ用の Cloud Tools Suite の新機能と機能強化です。これらのパッケージは、クラウドプラットフォーム上でのAdobe Commerceのインストールとアップグレードのデプロイと管理を目的として設計されています。</li>
            <li><strong><img alt="パッチリリースアイコン" src="../assets/icons/file-code.svg"></img> パッチ </strong> - セキュリティ、コンプライアンス、パフォーマンス、および優先度の高い品質修正を含む、Adobe Commerce PHP コアアプリケーションのアップデート。</li>
            <li><strong><img alt="サービス機能アイコン" src="../assets/icons/feature.svg"></img> Services</strong>：パッチ・リリースとは独立して提供される新しい SaaS 機能。 例えば、カタログサービス、ライブ検索、製品Recommendationsなどです。</li>
         </ul>
      </td>
   </tr>
</tfoot>
<tbody>
  <tr>
    <td>2024 年 2 月 13 日（Pt）</td>
    <td><img alt="拡張機能アイコン" src="../assets/icons/brackets.svg"></img> <a href="https://developer.adobe.com/commerce/extensibility/"> 拡張性 </a><br><img alt="インフラストラクチャ機能アイコン" src="../assets/icons/servers.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite.html"> インフラストラクチャ </a><br><img alt="サービス機能アイコン" src="../assets/icons/feature.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/release-information/release-notes-all.html"> サービス </a></td>
    <td><img alt="パッチリリースアイコン" src="../assets/icons/file-code.svg"></img> <a href="release-notes/security/overview.md"> セキュリティパッチ </a>:2.4.6-p4、2.4.5-p6、2.4.4-p7</td>
  </tr>
  <tr>
    <td>2024 年 3 月 12 日（Pt）</td>
    <td>—</td>
    <td><img alt="パッチリリースアイコン" src="../assets/icons/file-code.svg"></img> <a href="release-notes/commerce/overview.md">Beta パッチ </a>: 2.4.7-beta3</td>
  </tr>
  <tr>
    <td>2024 年 4 月 9 日（Pt）</td>
    <td><img alt="拡張機能アイコン" src="../assets/icons/brackets.svg"></img> <a href="https://developer.adobe.com/commerce/extensibility/"> 拡張性 </a><br><img alt="インフラストラクチャ機能アイコン" src="../assets/icons/servers.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite.html"> インフラストラクチャ </a><br><img alt="サービス機能アイコン" src="../assets/icons/feature.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/release-information/release-notes-all.html"> サービス </a></td>
    <td><img alt="パッチリリースアイコン" src="../assets/icons/file-code.svg"></img> <a href="release-notes/commerce/overview.md"><strong>Adobe Commerce 2.4.7</a></strong>:<ul><li>パフォーマンスの向上</li><li>品質の強化</li><li>セキュリティ機能の強化</li><li>サードパーティの依存関係の更新</li></ul><img alt="パッチリリースアイコン" src="../assets/icons/file-code.svg"></img> <a href="release-notes/security/overview.md"> セキュリティパッチ </a>:2.4.6-p5、2.4.5-p7、2.4.4-p8</td>
  </tr>
  <tr>
    <td>2024 年 6 月 11 日（Pt）</td>
    <td><img alt="拡張機能アイコン" src="../assets/icons/brackets.svg"></img> <a href="https://developer.adobe.com/commerce/extensibility/"> 拡張性 </a><br><img alt="インフラストラクチャ機能アイコン" src="../assets/icons/servers.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite.html"> インフラストラクチャ </a><br><img alt="サービス機能アイコン" src="../assets/icons/feature.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/release-information/release-notes-all.html"> サービス </a></td>
    <td><img alt="パッチリリースアイコン" src="../assets/icons/file-code.svg"></img> <a href="release-notes/security/overview.md"> セキュリティパッチ </a>:2.4.7-p1、2.4.6-p6、2.4.5-p8、2.4.4-p9</td>
  </tr>
  <tr>
    <td>2024 年 8 月 13 日（Pt）</td>
    <td><img alt="拡張機能アイコン" src="../assets/icons/brackets.svg"></img> <a href="https://developer.adobe.com/commerce/extensibility/"> 拡張性 </a><br><img alt="インフラストラクチャ機能アイコン" src="../assets/icons/servers.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite.html"> インフラストラクチャ </a><br><img alt="サービス機能アイコン" src="../assets/icons/feature.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/release-information/release-notes-all.html"> サービス </a></td>
    <td><img alt="パッチリリースアイコン" src="../assets/icons/file-code.svg"></img> <a href="release-notes/security/overview.md"> セキュリティパッチ </a>:2.4.7-p2、2.4.6-p7、2.4.5-p9、2.4.4-p10</td>
  </tr>
  <tr>
    <td>2024 年 10 月 8 日（Pt）</td>
    <td><img alt="拡張機能アイコン" src="../assets/icons/brackets.svg"></img> <a href="https://developer.adobe.com/commerce/extensibility/"> 拡張性 </a><br><img alt="インフラストラクチャ機能アイコン" src="../assets/icons/servers.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite.html"> インフラストラクチャ </a><br><img alt="サービス機能アイコン" src="../assets/icons/feature.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/release-information/release-notes-all.html"> サービス </a></td>
    <td><img alt="パッチリリースアイコン" src="../assets/icons/file-code.svg"></img> <a href="release-notes/commerce/overview.md">Beta パッチ </a>: 2.4.8-beta1<br><img alt="パッチリリースアイコン" src="../assets/icons/file-code.svg"></img><a href="release-notes/security/overview.md"> セキュリティパッチ </a>: 2.4.7-p3、2.4.6-p8、2.4.5-p10、2.4.4-p11</td>
  </tr>
</tbody>
</table>
