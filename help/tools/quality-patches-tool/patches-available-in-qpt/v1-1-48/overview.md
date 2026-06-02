---
title: 概要： [!DNL Quality Patches Tool]  （QPT） v1.1.48
description: このサブセクションでは、 [!DNL Quality Patches Tool]  （QPT） v1.1.48で使用可能なパッチによって修正された問題について詳しく説明します。
feature: Tools and External Services
role: Admin, Developer
exl-id: 250c88e9-1422-4af5-a0f0-32b15d9ab078
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 0%

---

# 概要：[!DNL Quality Patches Tool] （QPT） v1.1.48

このサブセクションでは、[!DNL Quality Patches Tool] （QPT） v1.1.48で利用可能なパッチによって修正された問題について詳しく説明します。

QPT v1.1.48には次のパッチが含まれています。

1. **ACSD-55566**: ソースと宛先の買い物かごが同じバンドルされたアイテムを持つ場合に、GraphQLの応答で&#x200B;*[!UICONTROL mergeCart mutation]*&#x200B;が&#x200B;*内部サーバーエラー*&#x200B;で失敗する問題を修正します。
1. **ACSD-56546**: *[!UICONTROL Display Out of Stock Product]*&#x200B;設定が無効になっている場合に、ストアフロントで構成可能な製品とバンドルされた製品が&#x200B;*[!UICONTROL Out of Stock]*&#x200B;として表示される問題を修正しました。
1. **ACSD-56635**: [!UICONTROL Account Sharing]を&#x200B;*[!UICONTROL Global]*&#x200B;に設定してインポートを使用すると、インポートした顧客が同じ電子メールアドレスで複製される問題を修正します。
1. **ACSD-56741**: データベースに索引付けメカニズムと[!DNL MView]に関連しないカスタム MySQL トリガーが含まれている場合、`setup:upgrade`に表示されるタイプ null *の値で配列オフセットにアクセスしようとすると、エラーメッセージ*&#x200B;が修正されました。
1. **ACSD-57315**: [!UICONTROL Admin]の「トランザクションを表示」画面で&#x200B;**[!UICONTROL Fetch]** ボタンをクリックするたびに、[!DNL PayPal Payflow Pro]で新しいトランザクションが作成される問題を修正します。
1. **ACSD-57337**：特定のweb サイトへのアクセス制限を持つ管理者ユーザーが、*[!UICONTROL Companies]* グリッドのすべてのweb サイトの企業を表示できる問題を修正します。
1. **ACSD-57394**: GraphQLの複数のソートフィールドによる誤った商品の並べ替えを修正します。
1. **ACSD-57565**：期間が更新されるまで、*[!UICONTROL Order]* ダッシュボードに誤った注文情報が表示される問題を修正します。 ダッシュボードに、初回読み込み時に正しい注文統計が表示されるようになりました。
1. **ACSD-57854**：商品GraphQL リクエストがカテゴリ集計内の無効なカテゴリを返す問題を修正します。
1. **ACSD-58008**：終了日が指定されていない場合に、スケジュールされた更新を更新すると、ステージングされたアイテムの以前のバージョンが削除される問題を修正します。

左側のメニューを使用して、特定のパッチページに移動します。
