---
title: ' [!DNL Site-Wide Analysis Tool] を統合します。'
description: 次の手順に従って、Adobe Commerce プロジェクトの  [!DNL Site-Wide Analysis Tool] dashboard から  [!DNL Upgrade Compatibility Tool]  レポートを取得します。
exl-id: 1ef37294-a837-47a4-841c-4027087acf12
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 0%

---

# [!DNL Site-Wide Analysis Tool] の統合

[!DNL Site-Wide Analysis Tool] は、Adobe Commerce インスタンスのセキュリティと操作性を確保するために、24 時間 365 日、リアルタイムのパフォーマンスモニタリング、レポート、推奨事項を提供します。

[!DNL Upgrade Compatibility Tool] が [!DNL Site-Wide Analysis Tool] と統合され、技術者以外のユーザーが [!DNL Upgrade Compatibility Tool] を実行して、各ファイルの問題のリストを含む [ レポート ](../upgrade-compatibility-tool/reports.md) を取得できるようになりました。

詳しくは、[[!DNL Site-Wide Analysis Tool]  ユーザーガイド ](https://docs.magento.com/user-guide/reports/site-wide-analysis-tool.html) を参照してください。

## [!DNL Site-Wide Analysis Tool] から [!DNL Upgrade Compatibility Tool] を実行します

プロジェクトの [!DNL Site-Wide Analysis Tool] ダッシュボードに移動し、[!DNL Upgrade Compatibility Tool] ウィジェットを見つけます。

![UCT SWAT ウィジェット – 初期 ](../../assets/upgrade-guide/uct-swat-initial.png)

「**[!UICONTROL Run Upgrade Scan]**」をクリックします。 プロジェクトのサイズによっては、スキャンに時間がかかる場合があります。 スピナーは、スキャンが進行中であることを示します。

![UCT SWAT ウィジェット – 処理中 ](../../assets/upgrade-guide/uct-swat-progress.png)

スキャンが完了すると、高レベルの結果がウィジェットに表示されます。

![UCT SWAT ウィジェット – 結果 ](../../assets/upgrade-guide/uct-swat-results.png)

**[!UICONTROL Download Report]** をクリックして [!DNL Upgrade Compatibility Tool] [HTMLレポートを取得し ](../upgrade-compatibility-tool/reports.md#html-report) 詳細を確認します。


>[!NOTE]
>
> [!DNL Site-Wide Analysis Tool] を通じて [!DNL Upgrade Compatibility Tool] を実行すると、結果が最適化され、Target のアップグレードにとって新しく重要な問題に集中できるようになります。 [`--ignore-current-version-compatibility-errors`](run.md#optimize-your-results) オプションが使用され、プロジェクトのバージョンと最新のリリースバージョンを常に比較して結果が表示されます。
