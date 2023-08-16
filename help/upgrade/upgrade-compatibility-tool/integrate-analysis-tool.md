---
title: の統合 [!DNL Site-Wide Analysis Tool]
description: 次の手順に従って、 [!DNL Upgrade Compatibility Tool] からの報告 [!DNL Site-Wide Analysis Tool] ダッシュボードをAdobe Commerceプロジェクトに貼り付けます。
exl-id: 1ef37294-a837-47a4-841c-4027087acf12
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 0%

---

# の統合 [!DNL Site-Wide Analysis Tool]

The [!DNL Site-Wide Analysis Tool] では、Adobe Commerceインスタンスのセキュリティと操作性を確保するため24/7、リアルタイムでのパフォーマンス監視、レポートおよび推奨事項を提供しています。

The [!DNL Upgrade Compatibility Tool] は、 [!DNL Site-Wide Analysis Tool] 非技術者が [!DNL Upgrade Compatibility Tool] そして、 [レポート](../upgrade-compatibility-tool/reports.md) 各ファイルの問題のリストを含んでいます。

詳しくは、 [[!DNL Site-Wide Analysis Tool] ユーザーガイド](https://docs.magento.com/user-guide/reports/site-wide-analysis-tool.html) を参照してください。

## を実行します。 [!DNL Upgrade Compatibility Tool] から [!DNL Site-Wide Analysis Tool]

次に移動： [!DNL Site-Wide Analysis Tool] プロジェクトのダッシュボードを使用して、 [!DNL Upgrade Compatibility Tool] ウィジェット。

![UCT SWAT ウィジェット — 初期](../../assets/upgrade-guide/uct-swat-initial.png)

クリック **[!UICONTROL Run Upgrade Scan]**. スキャンは、プロジェクトのサイズによっては時間がかかる場合があります。 スピナーは、スキャンが進行中であることを示します。

![UCT SWAT ウィジェット — 進行中](../../assets/upgrade-guide/uct-swat-progress.png)

スキャンが完了すると、高レベルの結果がウィジェットに表示されます。

![UCT SWAT ウィジェット — 結果](../../assets/upgrade-guide/uct-swat-results.png)

クリック **[!UICONTROL Download Report]** を取得するには [!DNL Upgrade Compatibility Tool] [HTMLレポート](../upgrade-compatibility-tool/reports.md#html-report) 詳細を確認します。


>[!NOTE]
>
> の実行 [!DNL Upgrade Compatibility Tool] から [!DNL Site-Wide Analysis Tool] により結果が最適化され、target のアップグレードにとって新しく重要な問題に焦点を当てるのに役立ちます。 使用するのは [`--ignore-current-version-compatibility-errors`](run.md#optimize-your-results) 「 」オプションを選択すると、常に、プロジェクトのバージョンと最新のリリースバージョンを比較した結果が表示されます。
