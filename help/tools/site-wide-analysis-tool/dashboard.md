---
title: '"[!DNL Dashboard]"'
description: 詳しくは、 [!DNL Dashboard] 」タブをクリックします。 [!DNL Site-Wide Analysis Tool]、要素、使用するタイミング、メリットおよびベストプラクティス
source-git-commit: 87a8d411de32f051037ade5ecc90aaa709a54e82
workflow-type: tm+mt
source-wordcount: '700'
ht-degree: 0%

---

# [!UICONTROL Dashboard]

この [!UICONTROL Dashboard] 一目でわかるページ [!DNL widgets] これは、Adobe Commerce Web サイトの正常性と現在のステータスを「1 つのパネルで表示」できます。 これら [!DNL widgets] それぞれには、各機能のページ、各ツール自体へのアクセスリンク、またはレポート ( [!DNL widget]) をクリックします。
また、 [!UICONTROL External Resources] Adobe Commerce( [Adobe Commerce Help Center サポートナレッジベース（ヘルプセンター）](https://support.magento.com/), [Adobe Commerce開発者向けドキュメント (DevDocs)](https://devdocs.magento.com/), [品質パッチツール](https://devdocs.magento.com/quality-patches/tool.html#patch-grid), [セキュリティセンター](https://magento.com/security)、および [Adobe Commerce(OAC) の観測](https://support.magento.com/hc/en-us/articles/4402379845901-Use-Observation-for-Adobe-Commerce).

## 要素

* **[!UICONTROL Recommendations]**:サイトのベストプラクティスのレコメンデーションを表示します。 Recommendations（検出された問題と修正の推奨事項）は、優先順位 P0（重大）から P4（通知）に分類されます。
Recommendationsには、説明、推奨事項、サイトへの影響、根本原因、シナリオ/前提条件、使用するツールが含まれます。

* **[!UICONTROL Upgrade Compatibility Tool]**:インストールされているすべてのモジュールとコアコードを分析することで、Adobe Commerceのカスタマイズされたインスタンスを特定のバージョンと照合します。 最新バージョンのAdobe Commerceにアップグレードする前に対処する必要がある重要な問題、エラーおよび警告のリストを返します。 また、新しいバージョンのAdobe Commerceにアップグレードする前にコードで修正する必要がある潜在的な問題も識別します。
この [!UICONTROL Upgrade Compatibility Tool] では、いつコアコードがカスタマイズされた機能に変更されたかを識別できます。

* **[!UICONTROL Security Scan Tool]**:Adobe Commerceサイトのセキュリティリスクを監視します。 マーチャントストアでマルウェアを事前かつ効率的に検出し、セキュリティ上のリスク、マルウェア、脅威がある場合はマーチャントに通知し、Adobe Commerceの不足しているパッチや更新を特定できます。

* **[!UICONTROL Extensions]**:現在Adobe Commerceインスタンスにインストールされている拡張機能が表示されます。 [Adobe Commerce Marketplace](https://marketplace.magento.com/extensions.html) 表示される拡張機能に関する情報が、利用可能な場合は提供されます。

* **[!UICONTROL Alerts]**:最新の [!DNL New Relic Managed Alerts] (Adobe Commerceインスタンス用 ) 詳細情報： [Adobe Commerce用管理アラート](https://support.magento.com/hc/en-us/articles/360045806832) そして方法 [New Relic サービスにアクセス](https://support.magento.com/hc/en-us/articles/360039127712) ( Adobe Commerce Support Knowledge Base )。

* **[!UICONTROL Non-recommended software in use]**:Adobe Commerceのバージョンに応じて、Adobe Commerceインスタンスが現在使用している推奨されないソフトウェアが表示されます。 非推奨ソフトウェアは、次のリストに表示されます。 [!UICONTROL Name], [!UICONTROL Installed Version]、および [!UICONTROL Recommended Version].

* **[!UICONTROL Recommended Patches]**:既にインストール済みのパッチと、Adobe Commerceバージョンの両方に基づく推奨パッチの短いリストを表示します。 推奨パッチの完全なリストは、 **[!UICONTROL Patches]** 機能タブ ( 同じく [!DNL Site-Wide Analysis Tool]. パッチは、 [品質パッチツール](https://devdocs.magento.com/quality-patches/tool.html). 一覧に表示されるすべてのパッチは、現在のAdobe Commerceインスタンスと互換性があります。
お使いのAdobe Commerceインスタンスに対して表示する推奨パッチがない場合は、次の手順を実行します。 [!DNL widget] が表示されます。 **[!UICONTROL No Recommended Patches]**.

## 使用するタイミング

この **[!UICONTROL Dashboard]** ページは、 [!DNL Site-Wide Analysis Tool] を使用すると、サイトの正常性の「全体像」を簡単に表示できるだけでなく、Adobe Commerce Web サイトの特定のツール、レコメンデーション、レポートの各ページを通じて、 [!DNL widget].

## メリット

* この [!DNL widgets] 対象 [!UICONTROL Recommendations], [!UICONTROL Extensions]、および [!UICONTROL Security Scan] すべてのグラフの凡例を横に付け、中央に合計を数えて、数を表す、読みやすい色分けされたインタラクティブな円グラフを使用します。 [!UICONTROL Recommendations], [!UICONTROL Extensions]、および [!UICONTROL Security Scan Tool] 各機能に含まれる項目。 [!UICONTROL Recommendations] および [!UICONTROL Security Scan Tool] グラフは重大度別に分けられます。 [!UICONTROL Extensions] は次の 4 つの分類に分かれます。現在のバージョン、古いバージョン、無効、不明。

* [!DNL New Relic Alerts] には、短い説明やアラートが発生した時間など、最新のアラートが上部に表示されます。

* この [!UICONTROL Recommendations] および [!UICONTROL Extensions] [!DNL widgets] 各機能のすべてのページのデータにアクセスするには、 **[!UICONTROL View All]**.

* この [!UICONTROL Security Scan Tool] には、 **[!UICONTROL View Report]** リンク [!DNL widget] ウィンドウが開き、 [!UICONTROL Recommendations] ページ。

* この [!DNL Upgrade Compatibility Tool] には、 **[!UICONTROL Run Upgrade Scan]** ボタン [!DNL widget] ウィンドウ

## を使用する際のベストプラクティス [!UICONTROL Dashboard]

* 各 [!DNL widget] を使用すると、Web サイトの正常性、推奨事項、および改善のためのベストプラクティスを把握し、理解できるようになります。

* 次に移動： [!UICONTROL Security Scan Tool] [!DNL widget] をクリックし、 [!UICONTROL View Report] 見る [!UICONTROL Recommendations] レポートを表示します。

* 以下を使用： [!DNL External Resources] 詳細情報の入手、セキュリティパッチ、更新、ベストプラクティスの最新情報の入手、または [Adobe Commerce Help Center サポートナレッジベース（ヘルプセンター）](https://support.magento.com/), [Adobe Commerce開発者向けドキュメント (DevDocs)](https://devdocs.magento.com/), [品質パッチツール](https://devdocs.magento.com/quality-patches/tool.html#patch-grid), [セキュリティセンター](https://helpx.adobe.com/security.html)、および [Adobe Commerce(OAC) の観測](https://support.magento.com/hc/en-us/articles/4402379845901-Use-Observation-for-Adobe-Commerce).