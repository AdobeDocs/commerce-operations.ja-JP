---
title: 概要： [!DNL Quality Patches Tool]  （QPT） v1.1.76
description: このサブセクションでは、 [!DNL Quality Patches Tool]  （QPT） v1.1.76で利用可能なパッチによって修正された問題について詳しく説明します。
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
source-git-commit: 33361f8de36b1d3f346d216244efb413835d88ef
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 0%

---

# 概要：[!DNL Quality Patches Tool] （QPT） v1.1.76

このサブセクションでは、[!DNL Quality Patches Tool] （QPT） v1.1.76で利用可能なパッチによって修正された問題について詳しく説明します。

QPT v1.1.76には、次のパッチが含まれています。
1. **[ACSD-67091](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-67091.md)**: データ ボリュームに基づいて2つの削除戦略を実装することで、カタログ ルール製品インデックスのクリーンアップを確保するための最大書き込みセット サイズ エラーを修正します。
1. **[ACSD-67370](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-67370.md)**: PDP/PLPのバンドル製品と複数通貨ストアの買い物かごページに誤った価格が表示される複数の問題を修正します。
1. **[ACSD-68410](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-68410.md)**：交渉可能な見積もりに対する注文で、見積に追加の買い物かご行が誤って追加または結合される問題を修正します。 交渉可能な見積もりチェックアウトの最後の手順を終了すると、製品がショッピングカートに正しく追加されるようになりました。
1. **[ACSD-69086](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69086.md)**: cron ジョブで変更ログテーブルをクリアできない問題を修正し、大量のデータを処理する際に[!DNL Galera Cluster]がクラッシュします。
1. **[ACSD-69115](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69115.md)**：デフォルト以外のweb サイトに割り当てられている顧客のショッピングカートを管理する際に、管理者ユーザーにショッピングカートのエラーが表示されない問題を修正しました。
1. **[ACSD-69129](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69129.md)**: [!DNL REST] APIを使用してセカンダリ web サイトの階層の価格を更新しようとすると、デフォルトの基本web サイトを削除し、セカンダリ web サイトをデフォルトとして使用するとエラーが発生する問題を修正しました。
1. **[ACSD-69203](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69203.md)**：複数のカテゴリがカテゴリ条件にリストされている場合に&#x200B;**[!UICONTROL Products List]** ウィジェットが誤った結果を返す問題を修正します。
1. **[ACSD-69261](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69261.md)**：部分的な請求書および残りの数量キャンセルシナリオで`times_used`属性が誤って処理されたため、顧客ごとに1回使用するように設定されたカート価格ルールクーポンが複数回再利用された問題を修正します。
1. **[ACSD-69308](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69308.md)**: `special_price`がweb サイトレベルでのみ設定された場合（**[!UICONTROL All Store Views]**&#x200B;ではなく）にカタログ価格ルールが適用されなかった問題を修正します。 修正の後、最初にweb サイトのデフォルトのストアを確認することで、カタログ価格ルールが正しく適用されます。
1. **[ACSD-69319](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69319.md)**：子商品がカスタムソースで在庫を持っている場合に、バンドル価格が適切にインデックス化されない問題を修正します。
1. **[ACSD-69325](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69325.md)**: SKU ケースを変更すると、ストアフロントで商品が在庫切れになる問題を修正しました。
1. **[ACSD-69331](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69331.md)**: メディアギャラリーのコンテンツ作成者が`create_folder`権限のみのフォルダーを作成できない問題を修正します。 修正の後、彼らは期待どおりにフォルダを作成することができます。
1. **[ACSD-69333](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69333.md)**：アクティブなスケジュール済み更新を含む製品に対してSKUの変更が許可されていた問題を修正します。 修正の後、アクティブな更新中はSKUの変更が禁止され、明確なエラーで保存が失敗し、管理者SKU フィールドが無効になります。 これにより、ステージング ロールバック中にSKUの変更によって発生するMSI インベントリの不整合を防ぐことができます。
1. **[ACSD-69541](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69541.md)**: [!UICONTROL Admin]内の商品の数量を、カート内に既に存在する数量よりも少なくすると、GraphQLを介してカート内の商品数量を編集できない問題を修正します。

左側のメニューを使用して、特定のパッチページに移動します。
