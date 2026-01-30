---
title: '[!DNL Site-Wide Analysis Tool]'
description: ツール  [!DNL Site-Wide Analysis]  その使用方法、インストールプロセス、アクセス方法について説明します
exl-id: 32774040-d322-43d6-9c26-c340a0ab58a9
source-git-commit: 62ca9093228d4d928d6c61c4c5dcf26e142c9fdb
workflow-type: tm+mt
source-wordcount: '542'
ht-degree: 0%

---

# [!DNL Site-Wide Analysis Tool]

>[!IMPORTANT]
>
>2024 年 4 月 23 日（PT）より、Adobe Commerceのオンプレミス環境のお客様の [!DNL Site-Wide Analysis Tool] は廃止されます。

このガイドでは、[!DNL Site-Wide Analysis Tool] の全体的な概要を説明します。 使用方法、インストール手順、ツールへのアクセス方法について説明します。

## [!DNL Site-Wide Analysis Tool] は何？

[!DNL Site-Wide Analysis Tool] は、プロアクティブなセルフサービスツールで、Adobe Commerce インストールのセキュリティと操作性を確保するための詳細なシステムインサイトおよびレコメンデーションが含まれている中央リポジトリです。 24 時間 365 日、パフォーマンスの監視、レポート、アドバイスをリアルタイムで行うことで、潜在的な問題を特定し、サイトの正常性、安全性、アプリケーションの設定をより明確に把握します。 これにより、解決時間が短縮され、サイトの安定性とパフォーマンスが向上します。

>[!NOTE]
>
>レコメンデーションを適用した後、サイト全体の分析ツールダッシュボードまたは生成されたレポートでレコメンデーションが更新されるまで数日かかる場合があります。
>
>[!DNL Site-Wide Analysis Tool] は、システムレベルのデータに関するレポートを作成します。 Adobe Commerce製品、セールス、マーケティングおよびその他のコマースアプリケーションデータに関するレポートについては、[Adobe Commerce レポート &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-admin/start/reporting/reports-menu) を参照してください。

![Site-Wide Analysis Tool ダッシュボード &#x200B;](../../assets/tools/swat-dashboard.png){zoomable="yes"}

詳しくは、この [&#x200B; 入門ビデオ &#x200B;](https://www.youtube.com/watch?v=KW2R8ki_RG4) を参照してください。

## ツールの概要

- **ダッシュボード**
   - 検出された問題の通知と優先度別の特定の推奨事項を含む、システムの全体的な状態を表示します。<br>
また、Web サイトのヘルスが時間の経過と共にどのように変化しているかを追跡する履歴グラフも含まれています。
   - 次のリソースへのリンクを提供する **[!UICONTROL Security Center Widget]** を表示します。
      - [&#x200B; 技術バージョ  [!DNL Stack]  への準拠  [!DNL end of life (EOL)]](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/system-requirements)
      - [Adobe セキュリティ速報 &#x200B;](https://helpx.adobe.com/security/security-bulletin.html)
      - [&#x200B; の推奨事項  [!DNL Security Scan Tool]](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security-scan)
      - [[!DNL Site-Wide Analysis Tool]  セキュリティに関するベストプラクティスの推奨事項 &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/site-wide-analysis-tool/recommendations)

- **情報** – お客様の連絡先情報および現在のチケットの概要と、インストールされている各Adobe Commerce製品の詳細情報を提供します。

- **Recommendations** - サイトの健全性を追跡するための [SWAT ヘルスインデックススコア &#x200B;](#swat-health-index.md) を提供し、サイトで検出された問題に対処するためのベストプラクティスに基づいたレコメンデーションを一覧表示します。
   - インフラストラクチャの更新を必要とする変更については、サポートリクエストを送信します。
   - アプリケーションの更新が必要な変更については、自分で変更してください。
   - [&#x200B; コードデプロイメント &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/pro-develop-deploy-workflow#deployment-workflow) など、手動の介入が必要な変更については、システム管理者または開発者にお問い合わせください。

- **例外** - エラーハンドラーのない異常な状態が原因でアプリケーションによってスローされたエラーを一覧表示します。

- **拡張機能** - サードパーティの拡張機能とサードパーティライブラリをすべて一覧表示します。

- **パッチ** - [!DNL Quality Patches Tool] と統合され、Adobe Commerce インスタンスに固有の使用可能なすべてのパッチのリストを提供します。

## その他のAdobe Commerce サポートツールとの統合

サイトに関する重要なインサイトを 1 か所で表示します。 [!DNL Site-Wide Analysis Tool] を使用すると、[!UICONTROL Security Center Widget]、[!DNL Upgrade Compatibility Tool] および [!DNL Managed Alerts] から、およびの情報に直接アクセスできます。

- **[!UICONTROL Security Center Widget]** - サイトのセキュリティインサイトを表示します。<br>
セキュリティ情報には、[&#x200B; [!DNL Stack]  ベストプラクティスのセキュリティ推奨事項に対する技術バージョ  [!DNL end of life (EOL)]](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/system-requirement), [Adobe Security Bulletin](https://helpx.adobe.com/security/security-bulletin.html), [Recommendations from the [!DNL Security Scan Tool]](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security-scan), and [[!DNL Site-Wide Analysis Tool]  のコンプライアンス &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/site-wide-analysis-tool/recommendations) が含まれます。

  [[!DNL Security Scan Tool]](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security-scan) は、Adobe CommerceおよびMagento オープンSourceのお客様に、マルウェアをプロアクティブに検出し、店舗が危険にさらされた場合にアラートを送信することで、店舗のセキュリティ状況に関するリアルタイムのインサイトを提供します。

- **[[!DNL Upgrade Compatibility Tool]](../../upgrade/upgrade-compatibility-tool/overview.md)** - アップグレードのバージョンと照合してAdobe Commerce インスタンスをチェックし、アップグレード前に修正する重要な問題、エラー、警告にフラグを付けます。 これらの問題に対処することで、アップグレードプロセスを合理化できます。」

- **[[!DNL Managed Alerts]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce)** – 主要指標（CPU、アプリケーションのパフォーマンス、ディスク、メモリ、データベースの正常性）を監視し、商社が問題に先立ち、ダウンタイムを回避するのに役立つ明確なトラブルシューティング手順を提供します。

## このガイドは誰を対象としていますか？

Adobe Commerceの web サイトをより明確に把握したいと考えているマーチャントやパートナー。 これにより、マーチャントは顧客のエクスペリエンスを向上させ、ベストプラクティスの推奨事項と基本的な問題により近い関係を築くことができます。

## [!DNL Site-Wide Analysis Tool] デモ

[!DNL Site-Wide Analysis Tool] について詳しくは、このビデオをご覧ください。

>[!VIDEO](https://video.tv.adobe.com/v/344001?quality=12)
