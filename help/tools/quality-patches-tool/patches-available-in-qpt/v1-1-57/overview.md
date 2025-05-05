---
title: 概要： [!DNL Quality Patches Tool]  （QPT） v1.1.57
description: このサブセクションでは、 [!DNL Quality Patches Tool]  （QPT） v1.1.57 で使用可能なパッチによって修正された問題について詳しく説明します。
feature: Tools and External Services
role: Admin, Developer
exl-id: 3e252a71-f35f-4046-9353-169060451ffe
source-git-commit: fc5c790108a3c62d4591631128743259824c4c6b
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# 概要：[!DNL Quality Patches Tool] （QPT） v1.1.57

このサブセクションでは、[!DNL Quality Patches Tool] （QPT） v1.1.57 で使用可能なパッチによって修正された問題について詳しく説明します。

QPT v1.1.57 には、次のパッチが含まれています。

1. **ACSD-57570**：特定のストアへのアクセスを持つ制限付きの管理者ユーザーが、製品が割り当てられているすべての共有カタログを常に表示できない、または保存できない顧客を表示でき、システムの不整合が発生する問題を修正しました。
1. **ACSD-58325**：検証エラーの後も「[!UICONTROL Import]」ボタンが使用可能な問題を修正。
1. **ACSD-59083**：一部のデータベース更新操作で、データベース更新が同時に実行されている場合に _ベーステーブルまたはビューが見つかりません_ というエラーが発 [!DNL mview] する問題を修正しました。
1. **ACSD-61622**：応答でアカウント固有 [!DNL FedEx] レートが欠落している問題を修正しました。 ACSD-61622 は、[[!DNL FedEx]  出荷方法の統合の移行  [!DNL SOAP]  からへの移行  [!DNL RESTful API]](https://experienceleague.adobe.com/ja/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/fedex-shipping-method-integration-migration-soap-restful-api) で説明されている修正を置き換えます。
1. **ACSD-61895**：ルートカテゴリに *許可* 権限がない場合でも、クエリ [!DNL GraphQL] カテゴリが *許可* 権限を持つカテゴリを返す問題を修正しました。
1. **ACSD-62212**:[!UICONTROL Forgot Password] メールのコンテンツがストア表示の言語に翻訳されない問題を修正しました。
1. **ACSD-62481**:[!UICONTROL Persistence] が有効になっていても、顧客の買い物かごが空になる問題を修正しました。
1. **ACSD-62629**:[!UICONTROL Widgets] で使用される製品リストがカテゴリ条件を尊重しない問題を修正しました。
1. **ACSD-62635**：マルチストア関連製品が [!DNL GraphQL] 製品クエリに正しく表示されない問題を修正しました。
1. **ACSD-62671**:[!DNL GraphQL] リクエストが最初の試行で最新のアドレス情報を返さない問題を修正しました。
1. **ACSD-62689**：深さ 4 の後で、顧客が [!UICONTROL Related Product Rules] および [!UICONTROL Widgets] でカテゴリを追加できない問題を修正。
1. **ACSD-62708**:[!UICONTROL ACP2E-3430] から修正を適用した後、管理画面の [!DNL TinyMCE] 7 エディターのフォントサイズが [!UICONTROL pt] と表示され、[!UICONTROL px] と表示されない問題を修正しました。 フォントサイズを [!UICONTROL pt] ではなく [!UICONTROL px] で設定できるようになりました。
1. **ACSD-62758**：選択したオプションが URL に含まれている場合、製品ビデオが [!UICONTROL Configurable Product] の詳細ページで正しくレンダリングされない問題を修正しました。
1. **ACSD-62951**：項目と合計を含めずに [!UICONTROL Credit Memo] メールが送信される問題を修正しました。
1. **ACSD-62965**: *LocalizedException* メッセージが注文配置 [!DNL GraphQL response] ードに含まれていない問題を修正しました。
1. **ACSD-63286**:API を介して共有カタログに割り当てられた製品が、手動の再インデックスが実行されるまでストアフロントに表示されない問題を修正しました。
1. **ACSD-63326**：バックエンドから注文した後、管理者が壊れたページにリダイレクトされる問題を修正しました。


左側のメニューを使用して、特定のパッチページに移動します。
