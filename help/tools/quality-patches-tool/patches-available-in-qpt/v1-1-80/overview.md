---
title: 概要： [!DNL Quality Patches Tool]  （QPT） v1.1.80
description: このサブセクションでは、 [!DNL Quality Patches Tool]  （QPT） v1.1.80で使用可能なパッチによって修正された問題について詳しく説明します。
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
autotag-review: '2026-06-11T01:10:37.916Z'
TQID: 'https://experienceleague.adobe.com/q2sNWUJQCm4eRUP8RusytBAqQoscU4F9qDtDIeNmm6E'
product_v2: id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: c1256247-af4b-46d8-9dca-0c654ecfa157id: d1e21356-0064-4f48-9089-16e3f0dbd2a6id: dac87252-6066-4d6e-a9d2-f6d84c323de7
topic_v2: id: c1579802-ddd4-4214-8a91-97b2066abe11
source-git-commit: 6e8a9f1bf5ac0495cbaf9178b9a422fd76721789
workflow-type: tm+mt
source-wordcount: 413
ht-degree: 0%

---

# 概要：[!DNL Quality Patches Tool] （QPT） v1.1.80

このサブセクションでは、[!DNL Quality Patches Tool] （QPT） v1.1.80で利用可能なパッチによって修正された問題について詳しく説明します。

QPT v1.1.80には、次のパッチが含まれています。

1. **[ACP2E-4493](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4493.md)**：非同期インデックス作成が有効になっている場合に、Sales Order Archive グリッドに誤った注文ステータスが表示される問題を修正します。
1. **[ACP2E-4239](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4239.md)**：日付属性を使用する管理者グリッドフィルターが、選択した日付、保存された[!DNL UTC]値、および設定済みのストアタイムゾーンの間にタイムゾーンが一致しないため、結果が返されない問題を修正しました。
1. **[ACP2E-4481](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4481.md)**：注文キャンセル後にバンドル製品の販売可能性が誤って再計算される問題を修正します。
1. **[ACP2E-4472](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4472.md)**: **[!UICONTROL Login as Customer]** フロー中に`quote` データベーステーブルにヌル引用符レコードが作成される問題を修正します。
1. **[ACP2E-4488](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4488.md)**：大規模な属性セットを持つ製品の管理画面での製品の保存または編集が遅くなる問題を修正します。
1. **[ACP2E-4610](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4610.md)**: `sales_clean_quotes` cron ジョブにパフォーマンスの問題がある問題を修正します。
1. **[ACP2E-4552](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4552.md)**:GraphQLの応答で会社のステータスが返されない問題を修正します。
1. **[ACP2E-4496](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4496.md)**:Analytics cron ジョブが実行中にパフォーマンスの低下を引き起こし、全体的なシステムパフォーマンスが向上する問題を修正します。
1. **[ACP2E-4533](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4533.md)**: URLにストアコードが含まれている場合に、ストアフロントでプレースホルダー画像が読み込まれない問題を修正しました。
1. **[ACP2E-4615](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4615.md)**: *PayPal ゲートウェイがリクエストを拒否するというPayPal エラーにより、オンライン注文の返金が失敗する問題を修正します。 内部エラー。*.
1. **[ACP2E-4626](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4626.md)**：一部のストアフロント JavaScript ファイルがリクエストされ、2回実行され、断続的に重複する読み込みと不安定な動作が発生する問題を修正します。
1. **[ACP2E-4813](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4813.md)**: チェックアウト時にUSPSの配送方法が利用できない問題を修正し、複数のパッケージに分割される注文を含む、特定の製品の配送見積りが正しくありません。
1. **[ACP2E-4653](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4653.md)**: [!DNL REST] APIを使用してルールを取得または更新する際に&#x200B;**[!UICONTROL Category (Parent Only)]**&#x200B;および&#x200B;**[!UICONTROL Category (Children Only)]**&#x200B;のカート価格ルール条件属性の範囲が公開されない問題を修正しました。
1. **[ACP2E-4808](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4808.md)**: ストアフロント製品ページのWeight属性に、設定された測定単位（lbsまたはkgs）を含めずに&#x200B;**[!UICONTROL Additional Information]**&#x200B;または&#x200B;**[!UICONTROL More Information]** セクションに生の数値のみが表示される問題を修正しました。
1. **[ACP2E-4156](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4156.md)**: [!DNL REST] APIの配送先住所の検証が、Adminで定義された属性設定に準拠しない問題を修正します。
1. **[ACSD-53502](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acsd-53502.md)**: New Relic モニタリングスクリプトへの再帰呼び出しにより、**[!UICONTROL Add to Cart]**&#x200B;がiOS [!DNL Safari]のストアフロントで断続的に失敗し、ページのリロードが発生する問題を修正します。

左側のメニューを使用して、特定のパッチページに移動します。
