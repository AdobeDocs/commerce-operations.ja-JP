---
title: の統合 [!DNL Site-Wide Analysis Tool]
description: を取得するには、次の手順に従います [!DNL Upgrade Compatibility Tool] からのレポート [!DNL Site-Wide Analysis Tool] Adobe Commerce プロジェクトのダッシュボード。
exl-id: 1ef37294-a837-47a4-841c-4027087acf12
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 0%

---

# の統合 [!DNL Site-Wide Analysis Tool]

この [!DNL Site-Wide Analysis Tool] は、Adobe Commerce インスタンスのセキュリティと操作性を確保するために、24 時間 365 日、リアルタイムのパフォーマンスモニタリング、レポート、推奨事項を提供します。

この [!DNL Upgrade Compatibility Tool] はと統合されました [!DNL Site-Wide Analysis Tool] 技術に詳しくないユーザーが [!DNL Upgrade Compatibility Tool] を取得します [報告書](../upgrade-compatibility-tool/reports.md) 各ファイルの問題のリストが含まれます。

を参照してください。 [[!DNL Site-Wide Analysis Tool] ユーザーガイド](https://docs.magento.com/user-guide/reports/site-wide-analysis-tool.html) を参照してください。

## を実行 [!DNL Upgrade Compatibility Tool] から [!DNL Site-Wide Analysis Tool]

に移動します。 [!DNL Site-Wide Analysis Tool] プロジェクトのダッシュボードでを見つけます。 [!DNL Upgrade Compatibility Tool] ウィジェット。

![UCT SWAT ウィジェット – 初期](../../assets/upgrade-guide/uct-swat-initial.png)

クリック **[!UICONTROL Run Upgrade Scan]**. プロジェクトのサイズによっては、スキャンに時間がかかる場合があります。 スピナーは、スキャンが進行中であることを示します。

![UCT SWAT ウィジェット – 処理中](../../assets/upgrade-guide/uct-swat-progress.png)

スキャンが完了すると、高レベルの結果がウィジェットに表示されます。

![UCT SWAT ウィジェット – 結果](../../assets/upgrade-guide/uct-swat-results.png)

クリック **[!UICONTROL Download Report]** を取得するには [!DNL Upgrade Compatibility Tool] [HTMLレポート](../upgrade-compatibility-tool/reports.md#html-report) 詳細を確認します。


>[!NOTE]
>
> の実行 [!DNL Upgrade Compatibility Tool] 経由 [!DNL Site-Wide Analysis Tool] 結果を最適化し、target のアップグレードにとって新しく重要な問題に集中できるようにします。 このストアでは、 [`--ignore-current-version-compatibility-errors`](run.md#optimize-your-results) 」オプションを選択すると、プロジェクトのバージョンと最新のリリースバージョンを比較して常に結果が表示されます。
