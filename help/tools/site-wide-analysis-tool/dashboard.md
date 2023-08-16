---
title: '[!DNL Dashboard]'
description: 詳しくは、 [!DNL Dashboard] 」タブをクリックします。 [!DNL Site-Wide Analysis Tool]、要素、使用するタイミング、メリットおよびベストプラクティス
exl-id: 37d848ff-2cff-48b1-8391-520531300bbc
source-git-commit: 786be8bfa915fe82d9316f51662b20bde71abbaa
workflow-type: tm+mt
source-wordcount: '771'
ht-degree: 0%

---

# [!UICONTROL Dashboard]

The [!UICONTROL Dashboard] 一目でわかるページ [!DNL widgets] これは、Adobe Commerce Web サイトの正常性と現在のステータスを「1 つのパネルで表示」できます。 各 [!DNL widget] には、各機能のページ、各ツール自体、またはレポート ( [!DNL widget]) をクリックします。
また、 [!UICONTROL External Resources] Adobe Commerceのリンク ( [Adobe Commerce Help Center サポートナレッジベース（ヘルプセンター）](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html), [Adobe Commerce開発者向けドキュメント (DevDocs)](https://developer.adobe.com/commerce/docs/), [[!DNL Quality Patches Tool]：パッチを検索します。](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}, [セキュリティセンター](https://helpx.adobe.com/security.html)、および [Adobe Commerce(OAC) の観測](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html).

## 要素

* **[!UICONTROL Recommendations]**：サイトのベストプラクティスのレコメンデーションを表示します。 Recommendations（検出された問題と修正の推奨事項）は、優先順位 P0（重大）から P4（通知）に分類されます。
Recommendationsには、説明、推奨事項、サイトへの影響、根本原因、シナリオ/前提条件、使用するツールが含まれます。

* **[!UICONTROL Upgrade Compatibility Tool]**：インストールされているすべてのモジュールとコアコードを分析することで、Adobe Commerceカスタマイズ済みのインスタンスを特定のバージョンと照合します。 最新バージョンのAdobe Commerceにアップグレードする前に対処する必要がある重要な問題、エラーおよび警告のリストを返します。 また、新しいバージョンのAdobe Commerceにアップグレードする前にコードで修正する必要がある潜在的な問題も識別します。
The [!UICONTROL Upgrade Compatibility Tool] では、いつコアコードがカスタマイズされた機能に変更されたかを識別できます。

* **[!UICONTROL Security Center Widget]**：サイトのセキュリティに関するインサイトを表示します。
表示されるセキュリティ情報には、以下が含まれます。 [テクニカル [!DNL Stack] 次のバージョンへの準拠 [!DNL end of life (EOL)]](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html), [Adobe Security Bulletin](https://helpx.adobe.com/security/security-bulletin.html), [Recommendations from the [!DNL Security Scan Tool]](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html), and [[!DNL Site-Wide Analysis Tool] ベストプラクティスセキュリティRecommendations](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/recommendations.html).<br>
The [[!UICONTROL Security Scan Tool]](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html) はAdobe Commerceサイトのセキュリティリスクを監視します。 マーチャントストアでマルウェアを事前かつ効率的に検出し、セキュリティ上のリスク、マルウェア、脅威がある場合はマーチャントに通知し、Adobe Commerceの不足しているパッチや更新を特定できます。

* **[!UICONTROL Extensions]**：現在Adobe Commerceインスタンスにインストールされている拡張機能が表示されます。 [Adobe Commerce Marketplace](https://marketplace.magento.com/extensions.html) 表示される拡張機能に関する情報が、利用可能な場合は提供されます。

* **[!UICONTROL Alerts]**：最新の [!DNL New Relic Managed Alerts] (Adobe Commerceインスタンス用 ) 詳細情報： [Adobe Commerce用管理アラート](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/managed-alerts/managed-alerts-for-magento-commerce.html) そして方法は [New Relic services にアクセス](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/faq/access-new-relic-services.html) ( Adobe Commerce Support Knowledge Base )。

* **[!UICONTROL Non-recommended software in use]**：ご使用のAdobe Commerceのバージョンに基づき、Adobe Commerceインスタンスが現在使用している推奨されないソフトウェアが表示されます。 非推奨ソフトウェアは、次のリストに表示されます。 [!UICONTROL Name], [!UICONTROL Installed Version]、および [!UICONTROL Recommended Version].

* **[!UICONTROL Recommended Patches]**：既にインストール済みの可能性のあるパッチと、Adobe Commerceバージョンの両方に基づく推奨パッチの短いリストを表示します。 推奨パッチの完全なリストは、 **[!UICONTROL Patches]** 機能タブ ( 同じく [!DNL Site-Wide Analysis Tool]. パッチは次の場所で提供されます。 [[!DNL Quality Patches Tool]：パッチを検索します。](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}. 一覧に表示されるすべてのパッチは、現在のAdobe Commerceインスタンスと互換性があります。
お使いのAdobe Commerceインスタンスに対して表示する推奨パッチがない場合は、次の手順を実行します。 [!DNL widget] が表示されます。 **[!UICONTROL No Recommended Patches]**.

## 使用するタイミング

The **[!UICONTROL Dashboard]** ページは、 [!DNL Site-Wide Analysis Tool] を使用すると、サイトの正常性の「全体像」を簡単に表示できるだけでなく、Adobe Commerce Web サイトの特定のツール、レコメンデーション、レポートの各ページを通じて、 [!DNL widget].

## メリット

* The [!DNL widgets] 対象： [!UICONTROL Security Center], [!UICONTROL Recommendations], [!UICONTROL Extensions]、および [!UICONTROL Security Scan] すべてのグラフの凡例を横に付け、中央に合計を数えて、数を表す、読みやすい色分けされたインタラクティブな円グラフを使用します。 [!UICONTROL Recommendations], [!UICONTROL Extensions]、および [!UICONTROL Security Scan Tool] 各機能に含まれる項目。 [!UICONTROL Recommendations] および [!UICONTROL Security Scan Tool] グラフは重大度別に分けられます。 [!UICONTROL Extensions] は、現在のバージョン、古いバージョン、無効、不明の 4 つの分類に分けられます。

* [!DNL New Relic Alerts] には、短い説明やアラートが発生した時間など、最新のアラートが上部に表示されます。

* The [!UICONTROL Recommendations] および [!UICONTROL Extensions] [!DNL widgets] 各機能のすべてのページのデータにアクセスするには、 **[!UICONTROL View All]**.

* The [!UICONTROL Security Scan Tool] には、 **[!UICONTROL View Report]** リンクを [!DNL widget] ウィンドウが開き、 [!UICONTROL Recommendations] ページに貼り付けます。

* The [!DNL Upgrade Compatibility Tool] には、 **[!UICONTROL Run Upgrade Scan]** ボタン [!DNL widget] ウィンドウ

## を使用する際のベストプラクティス [!UICONTROL Dashboard]

* 各 [!DNL widget] を使用すると、Web サイトのセキュリティ、正常性、推奨事項、および改善のためのベストプラクティスのインサイトと理解を得ることができます。

* 次に移動： [!UICONTROL Security Scan Tool] [!DNL widget] をクリックします。 [!UICONTROL View Report] 表示する [!UICONTROL Recommendations] レポートを作成します。

* 以下を使用します。 [!DNL External Resources] 詳細情報の入手、セキュリティパッチ、更新、ベストプラクティスの最新情報の入手、または [Adobe Commerce Help Center サポートナレッジベース（ヘルプセンター）](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html), [Adobe Commerce開発者向けドキュメント (DevDocs)](https://developer.adobe.com/commerce/docs/), [[!DNL Quality Patches Tool]：パッチを検索します。](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}, [セキュリティセンター](https://helpx.adobe.com/security.html)、および [Adobe Commerce(OAC) の観測](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html).
