---
title: 概要： [!DNL Quality Patches Tool]  （QPT） v1.1.82
description: このサブセクションでは、 [!DNL Quality Patches Tool]  （QPT） v1.1.82で使用可能なパッチによって修正された問題について詳しく説明します。
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
autotag-review: '2026-07-24T20:44:59.025Z'
TQID: 'https://experienceleague.adobe.com/Qoz-3w1ddXeHyDsyfsM0gD1kwi-Z6dc-C6P9Q-nYrUo'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
  - id: c1256247-af4b-46d8-9dca-0c654ecfa157
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
source-git-commit: 4358eb2865fbd8a66716ffc6b7a7b133a7e10e5d
workflow-type: tm+mt
source-wordcount: 485
ht-degree: 0%

---

# 概要：[!DNL Quality Patches Tool] （QPT） v1.1.82

このサブセクションでは、[!DNL Quality Patches Tool] （QPT） v1.1.82で利用可能なパッチによって修正された問題について詳しく説明します。

QPT v1.1.82には、次のパッチが含まれています。

1. **ACP2E-4815**: ログでPHPの例外が発生する複数のGraphQLの問題、GraphQLを介して注文後に作成されたお客様アカウントとの正しい注文関連付け、HTTP仕様を介したGraphQLとの応答の整合を修正します。
1. **ACP2E-4194**：無効、不正、または形式が正しくないリクエストに対して、GraphQLの応答が誤ったHTTP ステータス コードを返す問題を修正しました。
1. **ACP2E-4547**：管理者ユーザーが管理者の&#x200B;**[!UICONTROL Add Products by SKU]**&#x200B;を使用して、標準カタログから、共有カタログにリンクされていない顧客グループに割り当てられた会社の交渉可能な見積もりに製品を追加できない問題を修正します。
1. **ACP2E-4593**: マルチサイト展開のセカンダリ web サイトで、web サイトの制限に対して表示されるCMS ページが正しくない問題を修正しました。
1. **ACP2E-4682**：見積`isActive`の状態を確認するストアフロントページにアクセスすると、ページが読み込まれるたびに空の見積もりレコードが作成される問題を修正します。
1. **ACP2E-4695**: カタログ ルール インデクサーが過剰なメモリを消費し、完了に失敗して、不安定およびメモリ不足エラーが発生する問題を修正します。
1. **ACP2E-4698**: ページビルダーのテキストコンテンツで画像を再度編集すると、ポータブルメディアディレクティブを保持する代わりに絶対メディア URLが保存される問題を修正しました。
1. **[ACP2E-4748](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4748.md)**：報酬ポイントの有効期限が大きな報酬ポイント履歴を持つストアでゆっくりと実行され、報酬ポイントの有効期限が遅くなる問題を修正します。
1. **ACP2E-4797**: データベースが`utf8mb4`をサポートするように設定されている場合でも、管理者のWYSIWYG エディターまたはページビルダーのコンテンツに4 バイトのUnicode文字を入力すると誤ってブロックされる問題を修正しました。
1. **ACP2E-4799**: `requisition_lists` GraphQL クエリが、クエリ条件に一致する要件リストの合計数ではなく、現在のページの項目数のみを反映する`total_count`値を返す問題を修正しました。
1. **ACP2E-4805**：最初の販売可能な子製品がリストの後半に表示される場合、多くの子製品で設定可能な製品のチェックアウト API リクエストが大幅に遅くなる問題を修正しました。
1. **ACP2E-4840**: `products` GraphQL クエリで要求された数量の値が&#x200B;*null*&#x200B;を返す問題を修正します。
1. **ACP2E-4870**: **[!UICONTROL Product Alerts]**&#x200B;件のメール通知がストアビューのメール設定を無視する問題を修正しました。
1. **[ACP2E-4875](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4875.md)**：管理者で大きなアドレス帳を持つ顧客アカウントを表示すると、管理者ユーザーが予期せずログアウトする問題を修正しました。
1. **ACP2E-4894**: **[!UICONTROL Asynchronous Indexing]**&#x200B;が大容量ストアで有効になっている場合に、管理注文管理グリッドに新しい注文が表示されにくくなる問題を修正します。
1. **ACP2E-4981**: ページビルダー製品カルーセルで、管理者で設定された位置を反映しない順序で製品が表示され、一致する子製品が個別に表示される場合に設定可能な製品が含まれる問題を修正しました。

左側のメニューを使用して、特定のパッチページに移動します。
