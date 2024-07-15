---
title: '[!DNL Site-Wide Analysis Tool]'
description: ツール  [!DNL Site-Wide Analysis]  その使用方法、インストールプロセス、アクセス方法について説明します
exl-id: 32774040-d322-43d6-9c26-c340a0ab58a9
source-git-commit: 5f39a2d8440225b3a2e463894e2bd866196fbac2
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 0%

---

# [!DNL Site-Wide Analysis Tool]

>[!IMPORTANT]
>
>2024 年 4 月 23 日（PT）より、Adobe Commerceのオンプレミス環境のお客様の [!DNL Site-Wide Analysis Tool] は廃止されます。

このガイドでは、[!DNL Site-Wide Analysis Tool] の全体的な概要を説明します。 使用方法、インストール手順、ツールへのアクセス方法について説明します。

## [!DNL Site-Wide Analysis Tool] とは

[!DNL Site-Wide Analysis Tool] は、プロアクティブなセルフサービスツールで、Adobe Commerce インストールのセキュリティと操作性を確保するための詳細なシステムインサイトおよびレコメンデーションが含まれている中央リポジトリです。 24 時間 365 日、パフォーマンスの監視、レポート、アドバイスをリアルタイムで行うことで、潜在的な問題を特定し、サイトの正常性、安全性、アプリケーションの設定をより明確に把握します。 これにより、解決時間が短縮され、サイトの安定性とパフォーマンスが向上します。

![Site-Wide Analysis Tool ダッシュボード ](../../assets/tools/swat-dashboard.png){zoomable="yes"}

詳しくは、この [ 入門ビデオ ](https://www.youtube.com/watch?v=KW2R8ki_RG4) を参照してください。

## ツールの概要

- **ダッシュボード**
   - 検出された問題の通知と優先度別の特定の推奨事項を含む、システムの全体的な状態を表示します。<br>
また、Web サイトのヘルスが時間の経過と共にどのように変化しているかを追跡する履歴グラフも含まれています。
   - アクセスできる **[!UICONTROL Security Center Widget]** を表示します。
      - [ 技術バージョ  [!DNL Stack]  への準拠  [!DNL end of life (EOL)]](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html)
      - [Adobeセキュリティ速報 ](https://helpx.adobe.com/security/security-bulletin.html)
      - [Recommendations [!DNL Security Scan Tool]](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html)
      - [[!DNL Site-Wide Analysis Tool]  セキュリティのベストプラクティスのRecommendations](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/recommendations.html)

- **情報** – お客様の連絡先情報および現在のチケットの概要と、インストールされている各Adobe Commerce製品の詳細情報を提供します。

- **Recommendations** - サイトで検出された問題に対処するためのベストプラクティスに基づくお勧めを一覧表示します。
   - インフラストラクチャの更新を必要とする変更については、サポートリクエストを送信します。
   - アプリケーションの更新が必要な変更については、自分で変更してください。
   - [ コードデプロイメント ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/pro-develop-deploy-workflow.html#deployment-workflow) など、手動の介入が必要な変更については、システム管理者または開発者にお問い合わせください。

- **例外** - エラーハンドラーのない異常な状態が原因でアプリケーションによってスローされたエラーを一覧表示します。

- **拡張機能** - サードパーティの拡張機能とサードパーティライブラリをすべて一覧表示します。

- **パッチ** - [!DNL Quality Patches Tool] と統合され、Adobe Commerce インスタンスに固有の使用可能なすべてのパッチのリストを提供します。

## その他のAdobe Commerce サポートツールとの統合

サイトに関する重要なインサイトをすべて 1 か所で表示します。 [!DNL Site-Wide Analysis Tool] を使用すると、[!UICONTROL Security Center Widget]、[!DNL Upgrade Compatability Tool] および [!DNL Managed Alerts] から、およびの情報に直接アクセスできます。

- [**[!UICONTROL Security Center Widget]**] - サイトのセキュリティインサイトを表示します。<br>
表示されるセキュリティ情報には、[ セキュリティRecommendationsのテクニカルバージョ  [!DNL Stack]  への準拠  [!DNL end of life (EOL)]](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html), [Adobe Security Bulletin](https://helpx.adobe.com/security/security-bulletin.html), [Recommendations from the [!DNL Security Scan Tool]](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html), and [[!DNL Site-Wide Analysis Tool]  ベストプラクティス ](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/recommendations.html) が含まれます。<br>
[[!DNL Security Scan Tool]](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html) は、Adobe CommerceおよびMagentoのオープンSourceのお客様に、マルウェアをプロアクティブに検出して店舗が危険にさらされた場合に通知することで、店舗のセキュリティステータスに関するリアルタイムのインサイトを提供します。

- [**[!DNL Upgrade Compatability Tool]**](../../upgrade/upgrade-compatibility-tool/overview.md) - ターゲットのアップグレードバージョンに対してAdobe Commerceのカスタマイズされたインスタンスを実行し、対処が必要な重要な問題、エラー、警告の概要を返します。これにより、アップグレード分析プロセスがより簡単に、より高速に、より安価になります。

- [**[!DNL Managed Alerts]**](https://support.magento.com/hc/en-us/sections/360010758472-Managed-alerts-for-Adobe-Commerce) – 複数の指標を監視して、プラットフォームのパフォーマンスをプロアクティブに追跡し、問題のトラブルシューティング方法に関する具体的な手順を提供します。これにより、マーチャントは重大なダウンタイムを回避し、CPU、アプリケーションパフォーマンス、ディスク、メモリ、データベースに関する情報を常に得ることができます。

## このガイドは誰を対象としていますか？

Adobe Commerceの web サイトをより明確に把握したいと考えているマーチャントやパートナー。 これにより、マーチャントは顧客のエクスペリエンスを向上させ、ベストプラクティスの推奨事項と基本的な問題により近い関係を築くことができます。

## [!DNL Site-Wide Analysis Tool] デモ

[!DNL Site-Wide Analysis Tool] について詳しくは、このビデオをご覧ください。

>[!VIDEO](https://video.tv.adobe.com/v/344001?quality=12)
