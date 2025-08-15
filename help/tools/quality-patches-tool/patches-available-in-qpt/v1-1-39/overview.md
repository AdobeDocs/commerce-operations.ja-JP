---
title: 概要： [!DNL Quality Patches Tool]  （QPT） v1.1.39
description: ここでは、 [!DNL Quality Patches Tool]  （QPT） v1.1.39 で使用可能なパッチによって修正された問題について詳しく説明します。
feature: Tools and External Services
role: Admin, Developer
exl-id: 6116f566-2ff8-4148-ab60-cec65f9b7a6f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---

# 概要：[!DNL Quality Patches Tool] （QPT） v1.1.39

このサブセクションでは、[!DNL Quality Patches Tool] （QPT） v1.1.39 で使用可能なパッチによって修正された問題について詳しく説明します。

QPT v1.1.39 には、次のパッチが含まれています。

1. **ACSD-53704**：報酬ポイントの有効期限が切れた後に、報酬ポイントのバランス履歴が誤って計算される問題を修正しました。
1. **ACSD-53583**:*カテゴリ製品* および *製品カテゴリ* インデクサーの部分的な再インデックスパフォーマンスを向上します。
1. **ACSD-54026**：許可されていないユーザーの `updateCompanyRole` GraphQL リクエストに対する誤ったエラーメッセージを修正しました。
1. **ACSD-54106**：トルコ語のアクセント付き文字に対して、カテゴリ製品を名前で並べ替えると誤って表示される問題を修正しました。
1. **ACSD-52219**：ブックマークビューを頻繁に切り替えると、管理グリッドの保存済みフィルターが期待どおりに動作しない問題を修正しました。
1. **ACSD-54342**：有効なデータのない CSV ファイルを読み込む場合に、誤ったエラーメッセージ *データ構造のエラー：値が混在します* を修正しました。
1. **ACSD-54660**:GraphQLのお客様の注文を *と* で並べ替える新しい入力属性 `sort_field`sort`sort_direction` が追加されました。
1. **ACSD-54776**:2 つ目の web サイト、ストア、ストア表示で、オフの *[!UICONTROL Use Default Value]* フィールドとデフォルト以外の製品フィールドの値が保存されない問題を修正しました。
1. **ACSD-53998**：カスタマーアカウントからログアウトした後、**[!UICONTROL Dynamic Block]** に基づく **[!UICONTROL Customer Segment]** が正しく機能しない問題を修正しました。
1. **ACSD-53204**：修正点 *製品を保存できません。* エンドポイントを使用して製品ギャラリーに画像を追加する同時リクエストを行う際に `rest/V1/products/<sku>/media` エラーが発生します。
1. **ACSD-47657**:AWS資格情報のキャッシングメカニズムが追加されました。 認証情報プロバイダーは、Magento キャッシュを使用して、AWSから取得した認証情報を EC2 設定用にキャッシュするようになりました。

左側のメニューを使用して、特定のパッチページに移動します。
