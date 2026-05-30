---
title: 概要： [!DNL Quality Patches Tool]  （QPT） v1.1.57
description: このサブセクションでは、 [!DNL Quality Patches Tool]  （QPT） v1.1.57で使用可能なパッチによって修正された問題について詳しく説明します。
feature: Tools and External Services
role: Admin, Developer
exl-id: 3e252a71-f35f-4046-9353-169060451ffe
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---

# 概要：[!DNL Quality Patches Tool] （QPT） v1.1.57

このサブセクションでは、[!DNL Quality Patches Tool] （QPT） v1.1.57で利用可能なパッチによって修正された問題について詳しく説明します。

QPT v1.1.57には、次のパッチが含まれています。

1. **ACSD-57570**：特定のストアへのアクセス権を持つ制限付き管理者ユーザーが、製品が割り当てられているすべての共有カタログを常に表示できない、または保存できない顧客を表示できるため、システムの不整合が生じる、という問題を修正します。
1. **ACSD-58325**：検証エラーの後でも[!UICONTROL Import] ボタンが使用できる問題を修正します。
1. **ACSD-59083**: [!DNL mview]の更新が同時に実行されている場合に、一部のデータベースの更新操作が&#x200B;_ベーステーブルまたはビューが見つからない_ エラーが発生する問題を修正します。
1. **ACSD-61622**：応答で[!DNL FedEx] アカウント固有のレートが欠落している問題を修正します。 ACSD-61622は、 [!DNL SOAP] から [!DNL RESTful API][&#128279;](https://experienceleague.adobe.com/ja/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/fedex-shipping-method-integration-migration-soap-restful-api)への[!DNL FedEx] 出荷方法の統合移行で説明されている修正に代わるものです。
1. **ACSD-61895**: ルートカテゴリに&#x200B;*allow*&#x200B;権限がない場合でも、カテゴリ [!DNL GraphQL] クエリが&#x200B;*allow*&#x200B;権限を持つカテゴリを返す問題を修正しました。
1. **ACSD-62212**: [!UICONTROL Forgot Password]電子メールコンテンツがストアビューの言語に翻訳されない問題を修正します。
1. **ACSD-62481**: [!UICONTROL Persistence]が有効になっている場合でも、顧客の買い物かごが空になる問題を修正します。
1. **ACSD-62629**: [!UICONTROL Widgets]で使用されている製品リストがカテゴリ条件を尊重しない問題を修正します。
1. **ACSD-62635**: [!DNL GraphQL]製品クエリでマルチストア関連製品が正しく表示されない問題を修正します。
1. **ACSD-62671**：最初の試行で[!DNL GraphQL] リクエストが最新のアドレス情報を返さない問題を修正します。
1. **ACSD-62689**：深度4の後で[!UICONTROL Related Product Rules]および[!UICONTROL Widgets]のカテゴリを顧客が追加できない問題を修正します。
1. **ACSD-62708**：修正を[!UICONTROL ACP2E-3430]から適用した後、管理画面の[!DNL TinyMCE] 7 エディターのフォントサイズが[!UICONTROL pt]と[!UICONTROL px]ではなくと表示される問題を修正しました。 [!UICONTROL pt]ではなく[!UICONTROL px]でフォントサイズを設定することもできます。
1. **ACSD-62758**: URLに選択したオプションが含まれている場合に、[!UICONTROL Configurable Product]の詳細ページで製品ビデオが正しくレンダリングされない問題を修正します。
1. **ACSD-62951**：項目と合計を含めずに[!UICONTROL Credit Memo] メールが送信される問題を修正します。
1. **ACSD-62965**: *LocalizedException* メッセージが注文プレースメント [!DNL GraphQL response]に含まれていない問題を修正します。
1. **ACSD-63286**: APIを介して共有カタログに割り当てられた製品が、手動でインデックス再作成が実行されるまでストアフロントに表示されない問題を修正します。
1. **ACSD-63326**：管理者がバックエンドから注文した後、壊れたページにリダイレクトされる問題を修正します。


左側のメニューを使用して、特定のパッチページに移動します。
