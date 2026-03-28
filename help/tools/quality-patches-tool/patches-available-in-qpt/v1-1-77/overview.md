---
title: 概要： [!DNL Quality Patches Tool]  （QPT） v1.1.77
description: このサブセクションでは、 [!DNL Quality Patches Tool]  （QPT） v1.1.77で使用可能なパッチによって修正された問題について詳しく説明します。
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
source-git-commit: 98ccb5c357ebcb3bc2a7bb48e61b8557a65049f9
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---

# 概要：[!DNL Quality Patches Tool] （QPT） v1.1.77

このサブセクションでは、[!DNL Quality Patches Tool] （QPT） v1.1.77で利用可能なパッチによって修正された問題について詳しく説明します。

QPT v1.1.77には次のパッチが含まれています。

1. **[ACSD-63687](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-63687.md)**: [!DNL Redis] キャッシュをクリーンアップできないため、誤った価格が表示される問題を修正しました。
1. **[ACSD-68341](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-68341.md)**: PDPの読み込み中に`X-Magento-Vary` Cookieが複数回設定される問題を修正しました。この問題は、ストアで複数の顧客セグメントが作成される場合に発生します。
1. **[ACSD-68537](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-68537.md)**：顧客セグメントの数が増えるにつれてチェックアウトパフォーマンスが低下する問題を修正します。
1. **[ACSD-68664](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-68664.md)**：カスタムドメインを持つストアのコンテンツをプレビューしようとすると、スケジュールされた更新プレビューが壊れる問題を修正します。
1. **[ACSD-68759](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-68759.md)**: アラビア語のロケールを使用し、ストアフロントに生年月日（DOB）属性が表示されるように設定されている場合に、顧客アカウントの作成が失敗する問題を修正しました。
1. **[ACSD-68892](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-68892.md)**: キャッシュ可能なページが[!DNL Fastly] キャッシュに適切に保存または提供されない問題を修正し、結果としてキャッシュ動作の一貫性が失われ、パフォーマンスが低下します。
1. **[ACSD-69016](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-69016.md)**：異なるタイムゾーンで作成されたweb サイトに特別価格が適用されない問題を修正します。
1. **[ACSD-69020](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-69020.md)**：子製品のいずれかがフィルタリング条件を満たす場合に、設定可能な製品が[!DNL Page Builder]製品カルーセルリストに自動的に含まれる問題を修正します。
1. **[ACSD-69237](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-69237.md)**: `sales_*_async_insert` cron ジョブを通じて処理および挿入できるエントリの数が、実行ごとに&#x200B;*100*&#x200B;に制限される問題を修正しました。
1. **[ACSD-69311](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-69311.md)**：以前のクレジットメモが注文ビューページから作成された場合に、請求書から部分的な払い戻しを作成する際にクレジットメモで誤った税計算が発生する問題を修正します。
1. **[ACSD-69351](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-69351.md)**：割り当てられたweb サイトの範囲に従って、ギフトカードの残高と有効期限が表示されない問題を修正します。
1. **[ACSD-69494](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-69494.md)**: `is_online` パラメーターを使用した返金要求が正しく処理されない非同期返金処理の問題を修正します。

左側のメニューを使用して、特定のパッチページに移動します。
