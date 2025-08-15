---
title: 概要： [!DNL Quality Patches Tool]  （QPT） v1.1.48
description: ここでは、 [!DNL Quality Patches Tool]  （QPT） v1.1.48 で使用可能なパッチによって修正された問題について詳しく説明します。
feature: Tools and External Services
role: Admin, Developer
exl-id: 250c88e9-1422-4af5-a0f0-32b15d9ab078
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---

# 概要：[!DNL Quality Patches Tool] （QPT） v1.1.48

このサブセクションでは、[!DNL Quality Patches Tool] （QPT） v1.1.48 で使用可能なパッチによって修正された問題について詳しく説明します。

QPT v1.1.48 には、次のパッチが含まれています。

1. **ACSD-55566**：変換元と変換先の買い物かごに同じバンドル *[!UICONTROL mergeCart mutation]* ンテムがある場合に、GraphQL応答で *内部サーバーエラー* が発生して変換が失敗する問題を修正しました。
1. **ACSD-56546**:*[!UICONTROL Out of Stock]* 設定が無効な場合に、設定可能な製品とバンドルされた製品がストアフロントに *[!UICONTROL Display Out of Stock Product]* のように表示される問題を修正しました。
1. **ACSD-56635**：読み込みを使用し、[!UICONTROL Account Sharing] を *[!UICONTROL Global]* に設定すると、読み込まれた顧客が同じメールアドレスで重複する問題を修正しました。
1. **ACSD-56741**：データベースにインデックスメカニズムと *に関連しないカスタム MySQL トリガーが含まれている場合に* 行中に表示されるエラーメッセージ `setup:upgrade` 型 null の値の配列オフセットにアクセスしようとしています [!DNL MView] を修正しました。
1. **ACSD-57315**:[!DNL PayPal Payflow Pro] のトランザクションを表示画面で「**[!UICONTROL Fetch]**」ボタンをクリックするたびに、[!UICONTROL Admin] で新しいトランザクションが作成される問題を修正しました。
1. **ACSD-57337**：特定の web サイトへのアクセス制限を持つ管理者ユーザーが、*[!UICONTROL Companies]* グリッド内のすべての web サイトの会社を表示できる問題を修正しました。
1. **ACSD-57394**:GraphQLで、複数の並べ替えフィールドを使用した誤った商品の並べ替えを修正しました。
1. **ACSD-57565**：期間が更新されるまで、*[!UICONTROL Order]* ダッシュボードに間違った注文情報が表示される問題を修正しました。 ダッシュボードは、最初の読み込み時に正しい順序の統計を表示するようになりました。
1. **ACSD-57854**：製品GraphQL リクエストが、カテゴリ集計で無効なカテゴリを返す問題を修正しました。
1. **ACSD-58008**：終了日が指定されていない場合、スケジュールされた更新を更新するとステージングされた項目の以前のバージョンが削除される問題を修正しました。

左側のメニューを使用して、特定のパッチページに移動します。
