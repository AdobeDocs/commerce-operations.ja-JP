---
title: 概要：[!DNL Quality Patches Tool] （QPT） v1.1.84
description: このサブセクションでは、[!DNL Quality Patches Tool] （QPT） v1.1.84で利用可能なパッチによって修正された問題について詳しく説明します。
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
subfeature_v2:
  - id: 618ab558-d6ad-5352-99d6-d5702c6fdf80
    internal-label: Tools and External Services
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: c8d03788bf553af1808c2511114b14efaf27c7c5
workflow-type: tm+mt
source-wordcount: '558'
ht-degree: 0%
---
# 概要：[!DNL Quality Patches Tool] （QPT） v1.1.84

このサブセクションでは、[!DNL Quality Patches Tool] （QPT） v1.1.84で利用可能なパッチによって修正された問題について詳しく説明します。

QPT v1.1.84には、次のパッチが含まれています。

1. **[ACP2E-4913](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-84/acp2e-4913.md)**: データベースのデッドロック後にREST APIの出荷と請求書の作成が永続的に失敗する問題を修正します。
1. **ACP2E-5005**：管理でバンドル製品を再設定し、数量を編集すると、交渉可能な見積もりのバンドル製品オプションの数量が以前の値に戻る問題を修正します。
1. **ACP2E-5009**: Magento Open SourceからAdobe Commerceへのデータ移行で、カテゴリのスケジュールされたデザイン変更と製品&#x200B;**[!UICONTROL Special Price]**&#x200B;のスケジュールされた更新が正しく移行されず、移行中に一部のスケジュールされた更新が欠落またはスキップする問題が修正され、移行のパフォーマンスが向上します。
1. **[ACP2E-5017](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-84/acp2e-5017.md)**：お客様が会社に割り当てられていない場合に、GraphQLを通じてお客様`role`にクエリを実行すると&#x200B;*社内サーバーエラー*&#x200B;が返される問題を修正しました。
1. **ACP2E-5027**: ファイルのロックが有効になっている場合に、インデックスがループ内で停止したままになり、インデックス再作成が完了しない問題を修正します。
1. **ACP2E-5029**: カタログ価格ルールの変更が&#x200B;**[!DNL Live Search]**&#x200B;に表示されない問題を修正して、手動再同期を実行します。
1. **ACP2E-5041**：更新スケジュール中に製品を保存すると、ストアフロントで更新終了後に&#x200B;**[!UICONTROL Special Price]**&#x200B;ではなく通常価格が表示される問題を修正しました。
1. **ACP2E-5059**：顧客が同じ注文に対して重複した注文確認メールを受信する問題を修正します。
1. **[ACP2E-5122](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-84/acp2e-5122.md)**：ショッピングカートに対するGraphQL リクエストから処理されたエラーが、例外ログにアプリケーションエラーとして誤って記録される問題を修正します。
1. **[ACP2E-5143](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-84/acp2e-5143.md)**: メタデータのルーティングのみが要求された場合にGraphQL `route` クエリがCMS ページ全体のコンテンツをレンダリングする問題を修正し、Page Builder ウィジェットを含むCMS ページのデータベースクエリの数を増やしました。
1. **ACP2E-5183**: `@magento_import` ディレクティブを使用する`LESS` ファイルのコンパイル中にPHP 8.5で静的コンテンツのデプロイメントが失敗する問題を修正します。
1. **ACP2E-5242**: カートに商品を追加する際に製品の可用性を確認すると、web サイトが見つからないことを示すエラーが表示される問題を修正しました。
1. **ACP2E-5263**：すべての製品が含まれる前にCSV ファイルへの製品の書き出しが停止し、ファイルが不完全になる問題を修正します。
1. **ACP2E-5034**：配送方法を選択した後に見積もりを再計算する際に、交渉可能な見積もり管理が誤って合計を&#x200B;*ゼロ*&#x200B;にリセットし、管理者の&#x200B;**[!UICONTROL Configure]** アクションを通じて行われた製品オプション数量のバンドルの更新を破棄し、見積もり小計の動的な価格バンドル製品に適用されたアイテムレベル割引が正正反映反映されない問題を修正しました。
1. **[ACP2E-4741](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-84/acp2e-4741.md)**：既定以外の在庫とソースを使用している間に、関連製品、アップセル、またはクロスセルとしてリンクされている製品が保存された後、ストアフロントから製品が消える問題を修正します。
1. **ACP2E-5079**：複数のweb サイトに割り当てられた顧客セグメントを評価すると、顧客アカウントがグローバルに共有された場合に、最初のweb サイトからのみ一致する顧客が返される問題を修正します。
1. **ACP2E-5127**: デフォルト以外のロケールを使用して管理パネルで会社アカウントを編集すると、その&#x200B;**[!UICONTROL Credit Limit]**&#x200B;が&#x200B;*ゼロ*&#x200B;にリセットされる問題を修正します。
1. **AC-15494**：商品クエリで、元の文字の代わりにHTML エスケープされた特殊文字を含む商品名が返される問題を修正します。

左側のメニューを使用して、特定のパッチページに移動します。
