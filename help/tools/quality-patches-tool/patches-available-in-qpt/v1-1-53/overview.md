---
title: 概要： [!DNL Quality Patches Tool]  （QPT） v1.1.53
description: ここでは、 [!DNL Quality Patches Tool]  （QPT） v1.1.53 で使用可能なパッチによって修正された問題について詳しく説明します。
feature: Tools and External Services
role: Admin, Developer
exl-id: 4e7c8d45-dc0c-4182-8cd0-727b28294d58
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 0%

---

# 概要：[!DNL Quality Patches Tool] （QPT） v1.1.53

このサブセクションでは、[!DNL Quality Patches Tool] （QPT） v1.1.53 で使用可能なパッチによって修正された問題について詳しく説明します。

QPT v1.1.53 には、次のパッチが含まれています。

1. **ACSD-48318**：環境エミュレーションのネストが許可されていない問題を修正しました。 これで、`send()` 呼び出し中にエミュレーションが停止した後、`getInfoBlockHtml()` 呼び出し中にエミュレーションが開始されます。
1. **ACSD-59930**：会社の *[!UICONTROL Create]*、*[!UICONTROL Save]* および *[!UICONTROL Delete]* フローのパフォーマンスを向上させます。
1. **ACSD-60584**：ある web サイトのユーザー用に作成されたアクセストークンが、他の web サイトの顧客情報にアクセスしたり変更したりできる問題を修正しました。
1. **ACSD-60804**：削除された会社にリンクされている顧客を編集すると、エラー *メンバー関数の呼び出しが null で `getSuperUserId()` まる* が発生する問題を修正しました。
1. **ACSD-61133**:`sales_clean_quotes` Cron が未承認の発注書から見積もりを削除する問題を修正しました。
1. **ACSD-61528**:GraphQLを使用して [!UICONTROL Admin] からロールを取得しても結果が返されない問題を修正しました。
1. **ACSD-61553**：優先度や *[!UICONTROL Maximum Qty Discount is Applied To]* が異なる複数の割引が製品に適用されると、*[!UICONTROL Cart Price Rule]* の割引が誤って計算される問題を修正しました。
1. **ACSD-61667**: *店舗での受け取り* を含む多数のソースが存在する場合に、出荷を作成するための在庫パフォーマンスを向上させます。
1. **ACSD-61969**：設定されたクーポンコードと完全に一致する、大文字と小文字を区別するクーポンコードを入力する必要がある問題を修正しました。

左側のメニューを使用して、特定のパッチページに移動します。
