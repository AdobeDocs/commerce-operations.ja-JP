---
title: '[!DNL Dashboard]'
description: ' [!DNL Site-Wide Analysis Tool]の [!DNL Dashboard]  タブについて、要素、使用するタイミング、利点、ベストプラクティスを説明します。'
exl-id: 37d848ff-2cff-48b1-8391-520531300bbc
source-git-commit: 4266dbeca837bc62e5a76b2ef22b065a3452e088
workflow-type: tm+mt
source-wordcount: '866'
ht-degree: 0%

---

# [!UICONTROL Dashboard]

[!UICONTROL Dashboard] ページには、Adobe Commerce web サイトの正常性と現在のステータスの「一元的なウィンドウ表示」を提供する[!DNL widgets]が一目で表示されます。 各[!DNL widget]には、各機能のページ、各ツール自体、またはレポートへのアクセス リンクが含まれています（[!DNL widget]によって異なります）。
Adobe Commerceの[!UICONTROL External Resources]のリンクのリストもあります。たとえば、[Adobe Commerce ヘルプセンターのサポートナレッジベース（ヘルプセンター） ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/overview)、[Adobe Commerce開発者向けドキュメント（開発ドキュメント） ](https://developer.adobe.com/commerce/docs/)、[[!DNL Quality Patches Tool]：パッチを検索](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}、[ セキュリティセンター](https://helpx.adobe.com/security.html)、および[Adobe Commerceの観察（OAC） ](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html)です。

## 要素

* **[!UICONTROL Recommendations]**: サイトのベストプラクティスの推奨事項を表示します。 レコメンデーション（見つかった問題と修正する推奨事項）は、優先度P0 （クリティカル）からP4 （通知）でソートされます。
推奨事項には、説明、推奨事項、サイトへの影響、根本原因、シナリオ/前提条件、使用するツールなどが含まれます。

* **[!UICONTROL Upgrade Compatibility Tool]**: Adobe Commerceでカスタマイズされたインスタンスにインストールされているすべてのモジュールとコアコードを分析して、特定のバージョンと比較します。 最新バージョンのAdobe Commerceにアップグレードする前に対処する必要がある重大な問題、エラー、警告のリストが返されます。 また、新しいバージョンのAdobe Commerceにアップグレードする前に、コードで修正する必要がある潜在的な問題も特定します。
[!UICONTROL Upgrade Compatibility Tool]を使用すると、カスタマイズされた機能にコアコードが変更されたタイミングを特定できます。

* **[!UICONTROL Security Center Widget]**: サイトのセキュリティインサイトを表示します。
表示されるセキュリティ情報には、[技術 [!DNL Stack]  バージョンのコンプライアンスに関する [!DNL end of life (EOL)]](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html), [Adobe Security Bulletin](https://helpx.adobe.com/security/security-bulletin.html), [Recommendations from the [!DNL Security Scan Tool]](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html), and [[!DNL Site-Wide Analysis Tool]  ベストプラクティス セキュリティの推奨事項](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/recommendations.html)が含まれています。<br>
[[!UICONTROL Security Scan Tool]](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html)は、セキュリティ リスクについてAdobe Commerce サイトを監視します。 また、セキュリティリスク、マルウェア、脅威が発生した場合には、加盟店ストア上のマルウェアを先見的かつ効率的に検出して、加盟店に通知したり、Adobe Commerceのパッチやアップデートが欠けていることを特定したりできます。

* **[!UICONTROL Extensions]**：現在Adobe Commerce インスタンスにインストールされている拡張機能を表示します。 [Adobe Commerce Marketplace](https://commercemarketplace.adobe.com//extensions.html)の情報は、利用可能な場合、そこに記載されている拡張機能について提供されます。

* **[!UICONTROL Alerts]**: Adobe Commerce インスタンスの最新の[!DNL New Relic Managed Alerts]を表示します。 Adobe Commerce](/help/tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md)の[管理済みアラートの詳細と、New Relic サービス ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/faq/access-new-relic-services)へのアクセス方法については、Adobe Commerce サポート サポート ナレッジベースを参照してください。[

* **[!UICONTROL Non-recommended software in use]**: Adobe Commerceのバージョンに基づいて、現在Adobe Commerce インスタンスで使用している推奨されないソフトウェアを表示します。 推奨されないソフトウェアは、[!UICONTROL Name]、[!UICONTROL Installed Version]および[!UICONTROL Recommended Version]によってリストされています。

* **[!UICONTROL Recommended Patches]**：既にインストールしている可能性のあるパッチとAdobe Commerceのバージョンの両方に基づいて、推奨されるパッチの簡単なリストを表示します。 推奨されるパッチの完全なリストは、**[!UICONTROL Patches]**&#x200B;機能タブにあります。このタブは、[!DNL Site-Wide Analysis Tool]内にあります。 パッチは、[[!DNL Quality Patches Tool]: パッチを検索](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}することによって提供されます。 リストされているすべてのパッチは、現在のAdobe Commerce インスタンスと互換性があります。
Adobe Commerce インスタンスに表示する推奨パッチがない場合、この[!DNL widget]は&#x200B;**[!UICONTROL No Recommended Patches]**&#x200B;と表示されます。

## 使用するタイミング

**[!UICONTROL Dashboard]** ページは、[!DNL Site-Wide Analysis Tool]の一目でわかるコマンドセンターで、サイトの健全性を全体として簡単に確認できるだけでなく、各[!DNL widget]を通じて、Adobe Commerce web サイトの特定のツール、推奨事項、レポートを表示してアクセスすることもできます。

## Adobe Workfrontの利点

* [!UICONTROL Security Center]、[!UICONTROL Recommendations]、[!UICONTROL Extensions]および[!UICONTROL Security Scan]の[!DNL widgets]はすべて、グラフの凡例を横に配置し、中央の合計を数える、読みやすい色分けされたインタラクティブな円形グラフを使用して、各機能に含まれる[!UICONTROL Recommendations]、[!UICONTROL Extensions]、[!UICONTROL Security Scan Tool]項目の数を示します。 [!UICONTROL Recommendations]と[!UICONTROL Security Scan Tool]のグラフは重大度で区切られています。 [!UICONTROL Extensions]は、現在のバージョン、古いバージョン、無効、不明の4つの分類に分けられます。

* [!DNL New Relic Alerts]は、簡単な説明とアラートが発生した期間を含め、最新のアラートが上部に表示されます。

* [!UICONTROL Recommendations]と[!UICONTROL Extensions] [!DNL widgets]は、**[!UICONTROL View All]**&#x200B;をクリックして、各機能のデータの完全なページにアクセスできます。

* [!UICONTROL Security Scan Tool]には、[!DNL widget] ウィンドウに&#x200B;**[!UICONTROL View Report]** リンクがあり、[!UICONTROL Recommendations] ページに移動します。

* [!DNL Upgrade Compatibility Tool]には、[!DNL widget] ウィンドウに&#x200B;**[!UICONTROL Run Upgrade Scan]** ボタンがあります。

## [!UICONTROL Dashboard]の使用に関するベストプラクティス

* 各[!DNL widget]をクリックすると、insightの詳細データにアクセスし、web サイトのセキュリティ、健全性、推奨事項、ベストプラクティスについて理解を深めることができます。

* [!UICONTROL Security Scan Tool] [!DNL widget]に移動し、[!UICONTROL View Report]をクリックして、サイトの[!UICONTROL Recommendations] レポートを表示します。

* [!DNL External Resources]のリンクを使用して、詳細情報の確認、セキュリティパッチ、アップデート、ベストプラクティスの最新情報の入手、insightの[Adobe Commerce ヘルプセンターサポートナレッジベース（ヘルプセンター） ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/overview)、[Adobe Commerce開発者用ドキュメント（DevDocs） ](https://developer.adobe.com/commerce/docs/)、[[!DNL Quality Patches Tool]: パッチ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}、[ セキュリティセンター](https://helpx.adobe.com/security.html)、[Observation for Adobe Commerce（OAC） ](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html)の活用を行います。
