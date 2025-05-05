---
title: '[!DNL Dashboard]'
description: ' [!DNL Site-Wide Analysis Tool] のタブ  [!DNL Dashboard]  要素、使用するタイミング、メリット、ベストプラクティスについて説明します。'
exl-id: 37d848ff-2cff-48b1-8391-520531300bbc
source-git-commit: 786be8bfa915fe82d9316f51662b20bde71abbaa
workflow-type: tm+mt
source-wordcount: '686'
ht-degree: 0%

---

# [!UICONTROL Dashboard]

[!UICONTROL Dashboard] ページには、Adobe Commerce web サイトのヘルスと現在のステータスを「1 つのパネルから把握」できる [!DNL widgets] ールが一目でわかります。 各 [!DNL widget] には、各機能のページ、各ツール自体またはレポート（[!DNL widget] によって異なる）へのアクセスリンクが含まれています。
また、[Adobe Commerce ヘルプセンターのサポートナレッジベース（ヘルプセンター） ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html)、[Adobe Commerce開発者向けドキュメント（DevDocs） ](https://developer.adobe.com/commerce/docs/)、[[!DNL Quality Patches Tool]: パッチの検索 ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}、[ セキュリティセンター ](https://helpx.adobe.com/security.html)、[Adobe Commerce（OAC）の監視 ](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html) など、Adobe Commerceの [!UICONTROL External Resources] のリンクもあります。

## 要素

* **[!UICONTROL Recommendations]**：サイトのベストプラクティスの推奨事項を表示します。 Recommendations（見つかった問題と修正する推奨事項）は、優先度別に並べ替えられています。P0 （重大）から P4 （通知）です。
Recommendationsには、説明、推奨事項、サイトへの影響、根本原因、シナリオ/前提条件、使用されるツールが含まれます。

* **[!UICONTROL Upgrade Compatibility Tool]**:Adobe Commerceでカスタマイズされたインスタンスにインストールされているすべてのモジュールとコアコードを分析し、特定のバージョンに照らしてインスタンスを確認します。 Adobe Commerceの最新バージョンにアップグレードする前に対処する必要がある重要な問題、エラー、警告のリストを返します。 また、Adobe Commerceの新しいバージョンにアップグレードする前に、コードで修正する必要がある潜在的な問題も特定します。
[!UICONTROL Upgrade Compatibility Tool] を使用すると、カスタマイズされた機能に対してコアコードがいつ変更されたかを特定できます。

* **[!UICONTROL Security Center Widget]**：サイトのセキュリティインサイトを表示します。
表示されるセキュリティ情報には、[ セキュリティRecommendationsのテクニカルバージョ  [!DNL Stack]  への準拠  [!DNL end of life (EOL)]](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html), [Adobe Security Bulletin](https://helpx.adobe.com/security/security-bulletin.html), [Recommendations from the [!DNL Security Scan Tool]](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html), and [[!DNL Site-Wide Analysis Tool]  ベストプラクティス ](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/recommendations.html) が含まれます。<br>
[[!UICONTROL Security Scan Tool]](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html) は、Adobe Commerce サイトのセキュリティリスクを監視します。 商店のマルウェアをプロアクティブかつ効率的に検出し、セキュリティ上のリスク、マルウェア、脅威がある場合は商店に通知し、Adobe Commerceのパッチやアップデートが見つからないかどうかを特定できます。

* **[!UICONTROL Extensions]**:Adobe Commerce インスタンスに現在インストールされている拡張機能を表示します。 [Adobe Commerce Marketplace](https://marketplace.magento.com/extensions.html) に一覧表示されている拡張機能に関する情報が、利用可能な場合は提供されています。

* **[!UICONTROL Alerts]**:Adobe Commerce インスタンスの最新の [!DNL New Relic Managed Alerts] を表示します。 [Adobe Commerceの管理アラート ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/managed-alerts/managed-alerts-for-magento-commerce.html) および [New Relic サービスへのアクセス ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/faq/access-new-relic-services.html) について詳しくは、Adobe Commerce サポートナレッジベースを参照してください。

* **[!UICONTROL Non-recommended software in use]**:Adobe Commerceのバージョンに基づいて、Adobe Commerce インスタンスで現在使用されている非推奨ソフトウェアを表示します。 推奨されないソフトウェアの一覧は、[!UICONTROL Name]、[!UICONTROL Installed Version]、および [!UICONTROL Recommended Version] で示されています。

* **[!UICONTROL Recommended Patches]**：既にインストールされているパッチおよびAdobe Commerceのバージョンの両方に基づいて、推奨されるパッチの短いリストを表示します。 推奨されるパッチの完全なリストは、「**[!UICONTROL Patches]** 機能」タブにあります。このタブも [!DNL Site-Wide Analysis Tool] 内にあります。 パッチは、[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"} で提供されます。 表示されるすべてのパッチは、現在のAdobe Commerce インスタンスと互換性があります。
Adobe Commerce インスタンスに表示するおすすめのパッチがない場合は、この [!DNL widget] が表示されます（**[!UICONTROL No Recommended Patches]**）。

## 使用するタイミング

**[!UICONTROL Dashboard]** のページは、サイト全体のヘルスの「全体像」を簡単に確認できるだけでなく、各 [!DNL widget] ージを通じてAdobe Commerce web サイトの特定のツール、レコメンデーション、レポートを表示およびアクセスできる、[!DNL Site-Wide Analysis Tool] の一目で確認できるコマンドセンターです。

## 利点

* [!UICONTROL Security Center]、[!UICONTROL Recommendations]、[!UICONTROL Extensions] および [!UICONTROL Security Scan] の [!DNL widgets] では、読みやすい色分けされたインタラクティブな円グラフを使用しています。グラフの凡例を横に並べ、中央にカウントの合計を表示して、各機能に含まれる [!UICONTROL Recommendations]、[!UICONTROL Extensions]、[!UICONTROL Security Scan Tool] の項目の数を示します。 [!UICONTROL Recommendations] グラフと [!UICONTROL Security Scan Tool] グラフは重要度で区切られています。 [!UICONTROL Extensions] は、現在のバージョン、古いバージョン、無効、不明の 4 つの分類に分かれています。

* 簡単 [!DNL New Relic Alerts] 説明やアラートが発生した期間など、最新のアラートが表示されます。

* [!UICONTROL Recommendations] と [!UICONTROL Extensions] は、**[!UICONTROL View All]** をクリックすると、各機能のデータの完全なページにアクセスで [!DNL widgets] ます。

* [!UICONTROL Security Scan Tool] の [!DNL widget] ウィンドウには **[!UICONTROL View Report]** のリンクがあり、[!UICONTROL Recommendations] のページに移動します。

* [!DNL Upgrade Compatibility Tool] の [!DNL widget] ウィンドウには「**[!UICONTROL Run Upgrade Scan]**」ボタンが表示されます。

## [!UICONTROL Dashboard] を使用する際のベストプラクティス

* 各 [!DNL widget] をクリックして、提供される詳細なデータにアクセスすると、web サイトのセキュリティ、ヘルス、推奨事項、ベストプラクティスに関するインサイトと理解の両方を得て、改善できます。

* [!UICONTROL Security Scan Tool] [!DNL widget] に移動して [[!UICONTROL View Report]] をクリックし、サイトの [!UICONTROL Recommendations] レポートを表示します。

* [!DNL External Resources] のリンクを使用して、詳細情報を参照したり、セキュリティパッチ、アップデート、ベストプラクティスを常に最新の状態に保ったり、[Adobe Commerce ヘルプセンターのサポートナレッジベース （ヘルプセンター） ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html)、[Adobe Commerce開発者向けドキュメント （DevDocs） ](https://developer.adobe.com/commerce/docs/)、&lbrace;[[!DNL Quality Patches Tool]: パッチを検索 ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}、セキュリティセンター [&#128279;](https://helpx.adobe.com/security.html) 、および [Adobe Commerceの監視（OAC） ](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html) の情報を活用したりできます。
