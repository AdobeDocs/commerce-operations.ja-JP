---
title: 概要：[!DNL Quality Patches Tool] （QPT） v1.1.86
description: このサブセクションでは、[!DNL Quality Patches Tool] （QPT） v1.1.86で利用可能なパッチによって修正された問題について詳しく説明します。
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
source-git-commit: f7162ccff3f6011af51e0b32eec4bf405633050b
workflow-type: tm+mt
source-wordcount: '625'
ht-degree: 0%
---
# 概要：[!DNL Quality Patches Tool] （QPT） v1.1.86

このサブセクションでは、[!DNL Quality Patches Tool] （QPT） v1.1.86で利用可能なパッチによって修正された問題について詳しく説明します。

QPT v1.1.86には、次のパッチが含まれています。


1. **[ACP2E-5046](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-86/acp2e-5046.md)**：管理者で注文を作成する際にページを更新すると、同じSKUが複数回追加される問題を修正しました。
1. **[ACP2E-3094](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-86/acp2e-3094.md)**：多くの権限を持つカテゴリの&#x200B;**[!UICONTROL Category Permissions]**&#x200B;を表示または編集すると、ブラウザーが応答しなくなる問題を修正しました。
1. **[ACP2E-5050](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-86/acp2e-5050.md)**：管理者でRMAを表示または保存すると、**[!UICONTROL Action Logs]** レポートにRMA番号が表示されない問題を修正します。
1. **ACP2E-5057**: **[!UICONTROL Catalog Price Scope]**&#x200B;が&#x200B;**[!UICONTROL Website]**&#x200B;に設定されている場合に、バンドル製品の[!DNL GraphQL]件のクエリで、web サイト固有の価格ではなくグローバルバンドルオプション価格が返される問題を修正しました。
1. **ACP2E-5061**: カテゴリ マーチャンダイジング ルールが`AND`条件を複数の値のいずれかに一致する条件と組み合わせることができない問題を修正します。
1. **ACP2E-5071**：買い物客の買い物かごに既に利用可能な全数量が含まれている場合に、在庫の利用不可メッセージが商品ページに必ずしも表示されない問題を修正します。
1. **ACP2E-5094**: `MAGENTO_DC_*`環境変数が設定されている場合にページの読み込みが大幅に遅くなる問題を修正します。
1. **ACP2E-5118**: **[!UICONTROL Translations]** キャッシュが無効になっている場合、[!DNL Page Builder] プレビューがレンダリングされない問題を修正します。
1. **ACP2E-5134**：企業の[!UICONTROL Shared Catalog]からバンドルのコンポーネント製品を削除すると、ショッピングカートにバンドル製品が残り、カートとチェックアウト中にエラーが発生する問題を修正します。
1. **ACP2E-5146**：別のWeb サイトの顧客が管理者ユーザーと同じIDを持つ場合、特定のWeb サイトに制限された管理者ユーザーが顧客を削除できない問題を修正します。
1. **ACP2E-5176**: [!DNL Google Analytics 4]から[!DNL Google Tag Manager]に送信されたe コマースイベントが[!DNL Universal Analytics]形式を使用し、複数のチェックアウトイベントを省略する問題を修正します。
1. **ACP2E-5185**: カテゴリーツリー内のカテゴリを移動すると、エラー`There was a category move error`が表示されるか、ストアに多数のURL書き換えが行われた場合に完了するのに数分かかる問題を修正します。
1. **ACP2E-4191**: **[!UICONTROL EAV types and attributes]** キャッシュが無効になっている場合に、特定のREST API リクエストが無限ループに入る問題を修正します。
1. **ACP2E-4973**: **[!UICONTROL In-Store Delivery]**&#x200B;から別の配信方法に切り替えても、関連付けられているストア アドレスがカートからクリアされない問題を修正します。
1. **ACP2E-5221**：多くのストアと顧客グループを含むインストールで&#x200B;**[!UICONTROL Quick Order]**&#x200B;が有効になっている場合、**[!UICONTROL Catalog Product Permissions]** インデクサーが大幅に長くなる問題を修正します。
1. **ACP2E-5245**：最初の注文で同じ住所を使用して配送および請求を行う新規登録のお客様が、次回のチェックアウト時に、その住所が2回表示される問題を修正しました。
1. **ACP2E-5248**: [!DNL PHP] 8.5で&#x200B;**[!UICONTROL Add Product]** ページを開くときに&#x200B;**[!UICONTROL Edit Product Status]**&#x200B;権限のない管理者ユーザーに`null as array offset`非推奨エラーが表示される問題を修正しました。
1. **ACP2E-5254**：顧客がリストを開いたときに、キャッシュがクリアされるまで、購買リストに追加された製品が表示されない問題を修正します。
1. **ACP2E-5268**: **[!UICONTROL Enable Frontend Resize]**&#x200B;が&#x200B;**[!UICONTROL No]**&#x200B;に設定されている場合に設定可能な製品の作成が失敗する問題を修正します。
1. **ACP2E-3752**：多数の製品インポート操作を作成すると、製品インポート処理でエラー`Undefined array key "apply_to"`がスローされる問題を修正します。
1. **ACP2E-5280**: **[!UICONTROL Category Permissions]**&#x200B;が有効になっている間にサインインする際にエラーが発生する問題を修正します。
1. **ACP2E-5295**：同じプロセスで&#x200B;**[!UICONTROL Inventory]** インデクサーの後に実行すると、並列製品価格のインデックス再作成がエラー`Fail in child process`で失敗する問題を修正します。
1. **ACP2E-5298**: カート価格ルールへの表示専用アクセス権を持つ管理者ユーザーがクーポンコードを生成または削除できる問題を修正しました。
1. **ACP2E-5333**: **[!UICONTROL is not]**&#x200B;演算子を使用し、1つ以上の値を持つ&#x200B;**[!UICONTROL Total Number of Orders]**&#x200B;条件で顧客セグメントを更新すると、エラー`Unknown operator specified`で失敗する問題を修正します。
1. **ACP2E-5425**：顧客が同じ注文に対して重複した注文確認メールを受信する問題を修正します。

左側のメニューを使用して、特定のパッチページに移動します。
