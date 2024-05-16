---
title: '[!DNL Dashboard]'
description: について説明します [!DNL Dashboard] タブ [!DNL Site-Wide Analysis Tool]、要素、使用するタイミング、メリットおよびベストプラクティス。
exl-id: 37d848ff-2cff-48b1-8391-520531300bbc
source-git-commit: 786be8bfa915fe82d9316f51662b20bde71abbaa
workflow-type: tm+mt
source-wordcount: '686'
ht-degree: 0%

---

# [!UICONTROL Dashboard]

この [!UICONTROL Dashboard] ページの表示が一目でわかる [!DNL widgets] これにより、Adobe Commerce web サイトのヘルスと現在のステータスに関する「1 つのパネル」が提供されます。 Each [!DNL widget] 各機能のページ、各ツール自体またはレポート（によって異なる）へのアクセスリンクが含まれています [!DNL widget]）に設定します。
次のリストもあります [!UICONTROL External Resources] 次を含むAdobe Commerceのリンク [Adobe Commerce ヘルプセンターのサポートナレッジベース（ヘルプセンター）](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html), [Adobe Commerce開発者向けドキュメント（DevDocs）](https://developer.adobe.com/commerce/docs/), [[!DNL Quality Patches Tool]：パッチの検索](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}, [セキュリティセンター](https://helpx.adobe.com/security.html)、および [Adobe Commerceの監視（OAC）](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html).

## 要素

* **[!UICONTROL Recommendations]**：サイトのベストプラクティスの推奨事項を表示します。 Recommendations（見つかった問題と修正する推奨事項）は、優先度別に並べ替えられています。P0 （重大）から P4 （通知）です。
Recommendationsには、説明、推奨事項、サイトへの影響、根本原因、シナリオ/前提条件、使用されるツールが含まれます。

* **[!UICONTROL Upgrade Compatibility Tool]**:Adobe Commerceにインストールされているすべてのモジュールとコアコードを分析し、カスタマイズされたインスタンスを特定のバージョンと照合して確認します。 Adobe Commerceの最新バージョンにアップグレードする前に対処する必要がある重要な問題、エラー、警告のリストを返します。 また、Adobe Commerceの新しいバージョンにアップグレードする前に、コードで修正する必要がある潜在的な問題も特定します。
この [!UICONTROL Upgrade Compatibility Tool] では、カスタマイズされた機能に対してコアコードがいつ変更されたかを特定できます。

* **[!UICONTROL Security Center Widget]**：サイトのセキュリティインサイトを表示します。
表示されるセキュリティ情報には、次のものが含まれます [技術 [!DNL Stack] バージョン準拠 [!DNL end of life (EOL)]](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html), [Adobe Security Bulletin](https://helpx.adobe.com/security/security-bulletin.html), [Recommendations from the [!DNL Security Scan Tool]](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html), and [[!DNL Site-Wide Analysis Tool] セキュリティのベストプラクティス Recommendations](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/recommendations.html).<br>
この [[!UICONTROL Security Scan Tool]](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html) Adobe Commerce サイトのセキュリティ上のリスクを監視します。 商店のマルウェアをプロアクティブかつ効率的に検出し、セキュリティ上のリスク、マルウェア、脅威がある場合は商店に通知し、Adobe Commerceのパッチやアップデートが見つからないかどうかを特定できます。

* **[!UICONTROL Extensions]**:Adobe Commerce インスタンスに現在インストールされている拡張機能が表示されます。 [Adobe Commerce Marketplace](https://marketplace.magento.com/extensions.html) 利用可能な場合は、そこに一覧表示されている拡張機能に関する情報が提供されます。

* **[!UICONTROL Alerts]**：最新のを表示します [!DNL New Relic Managed Alerts] （Adobe Commerce インスタンスの場合）。 の詳細情報 [Adobe Commerceの管理アラート](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/managed-alerts/managed-alerts-for-magento-commerce.html) および方法 [New Relic サービスへのアクセス](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/faq/access-new-relic-services.html) （Adobe Commerce サポートナレッジベース）

* **[!UICONTROL Non-recommended software in use]**:Adobe Commerceのバージョンに基づいて、Adobe Commerce インスタンスが現在使用している推奨されないソフトウェアを表示します。 推奨されないソフトウェアのリストは、次のとおりです。 [!UICONTROL Name], [!UICONTROL Installed Version]、および [!UICONTROL Recommended Version].

* **[!UICONTROL Recommended Patches]**：インストール済みのパッチおよびAdobe Commerceのバージョンに基づいて、推奨されるパッチの短いリストを表示します。 推奨されるパッチの完全なリストは、にあります。 **[!UICONTROL Patches]** 「機能」タブ（「」内にも存在） [!DNL Site-Wide Analysis Tool]. パッチは、 [[!DNL Quality Patches Tool]：パッチの検索](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}. 表示されるすべてのパッチは、現在のAdobe Commerce インスタンスと互換性があります。
Adobe Commerce インスタンスに推奨されるパッチを表示しない場合は、次の点に注意してください。 [!DNL widget] 次が表示されます。 **[!UICONTROL No Recommended Patches]**.

## 使用するタイミング

この **[!UICONTROL Dashboard]** ページは、の一目でわかるコマンドセンターです。 [!DNL Site-Wide Analysis Tool] を使用すると、サイトのヘルス全体の「全体像」を簡単に確認できるだけでなく、各ツールを通じてAdobe Commerce web サイトの特定のツール、推奨事項、レポートを表示し、アクセスすることもできます [!DNL widget].

## 利点

* この [!DNL widgets] （用） [!UICONTROL Security Center], [!UICONTROL Recommendations], [!UICONTROL Extensions]、および [!UICONTROL Security Scan] いずれも、横側にグラフの凡例を表示し、中央に合計をカウントして数を示す、読みやすい色分けされたインタラクティブな円グラフを使用しています [!UICONTROL Recommendations], [!UICONTROL Extensions]、および [!UICONTROL Security Scan Tool] 各機能が持つ項目。 [!UICONTROL Recommendations] および [!UICONTROL Security Scan Tool] グラフは重大度で区切られています。 [!UICONTROL Extensions] は、現在のバージョン、古いバージョン、無効、不明の 4 つの分類に分類されます。

* [!DNL New Relic Alerts] は、簡単な説明とアラートが発生した期間を含む、最新のアラートを先頭に表示します。

* この [!UICONTROL Recommendations] および [!UICONTROL Extensions] [!DNL widgets] をクリックして、各機能のデータの完全なページにアクセスできる **[!UICONTROL View All]**.

* この [!UICONTROL Security Scan Tool] 持つ **[!UICONTROL View Report]** 内のリンク [!DNL widget] に移動するウィンドウ [!UICONTROL Recommendations] ページ。

* この [!DNL Upgrade Compatibility Tool] 持つ **[!UICONTROL Run Upgrade Scan]** のボタン [!DNL widget] ウィンドウ。

## を使用する際のベストプラクティス [!UICONTROL Dashboard]

* 各をクリック [!DNL widget] に表示される詳細なデータにアクセスすることで、web サイトのセキュリティ、正常性、推奨事項、ベストプラクティスに関するインサイトと理解の両方を得て、データを改善できます。

* に移動します [!UICONTROL Security Scan Tool] [!DNL widget] をクリックして、 [!UICONTROL View Report] を表示するには [!UICONTROL Recommendations] サイトのレポート。

* の使用 [!DNL External Resources] 詳細情報へのリンク、セキュリティパッチ、アップデート、ベストプラクティスの最新情報の維持、のインサイトの活用へのリンク [Adobe Commerce ヘルプセンターのサポートナレッジベース（ヘルプセンター）](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html), [Adobe Commerce開発者向けドキュメント（DevDocs）](https://developer.adobe.com/commerce/docs/), [[!DNL Quality Patches Tool]：パッチの検索](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}, [セキュリティセンター](https://helpx.adobe.com/security.html)、および [Adobe Commerceの監視（OAC）](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html).
