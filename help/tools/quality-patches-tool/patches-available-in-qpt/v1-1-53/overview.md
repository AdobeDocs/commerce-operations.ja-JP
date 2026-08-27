---
title: 概要： [!DNL Quality Patches Tool]  （QPT） v1.1.53
description: このサブセクションでは、 [!DNL Quality Patches Tool]  （QPT） v1.1.53で利用可能なパッチによって修正された問題について詳しく説明します。
feature: Tools and External Services
role: Admin, Developer
exl-id: 4e7c8d45-dc0c-4182-8cd0-727b28294d58
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '243'
ht-degree: 0%

---

# 概要：[!DNL Quality Patches Tool] （QPT） v1.1.53

このサブセクションでは、[!DNL Quality Patches Tool] （QPT） v1.1.53で利用可能なパッチによって修正された問題について詳しく説明します。

QPT v1.1.53には、次のパッチが含まれています。

1. **ACSD-48318**：環境エミュレーションのネストが許可されない問題を修正します。 これで、`getInfoBlockHtml()`呼び出しの間にエミュレーションが停止すると、エミュレーションは`send()`呼び出しの間に開始されます。
1. **ACSD-59930**：会社の&#x200B;*[!UICONTROL Create]*、*[!UICONTROL Save]*、*[!UICONTROL Delete]*&#x200B;のフローのパフォーマンスを向上させます。
1. **ACSD-60584**：あるWeb サイトでユーザー用に作成されたアクセストークンが、他のWeb サイトの顧客情報にアクセスまたは変更できる問題を修正します。
1. **ACSD-60804**：削除された会社にリンクされている顧客を編集すると、null *の* メンバー関数`getSuperUserId()`への呼び出しがエラーになる問題を修正します。
1. **ACSD-61133**: `sales_clean_quotes` クローンが未承認の発注から見積を削除する問題を修正します。
1. **ACSD-61528**: GraphQLを使用して[!UICONTROL Admin]からロールを取得しても結果が返されない問題を修正します。
1. **ACSD-61553**：優先度が異なる複数の割引と&#x200B;*[!UICONTROL Maximum Qty Discount is Applied To]*&#x200B;が製品に適用されている場合に&#x200B;*[!UICONTROL Cart Price Rule]*&#x200B;の割引が誤って計算される問題を修正します。
1. **ACSD-61667**: *実店舗での受け取り*&#x200B;で多くのソースの場合に発送を作成する際の在庫パフォーマンスを向上させます。
1. **ACSD-61969**：設定されたクーポンコードと正確に一致する大文字と小文字を区別するクーポンコードを入力する必要がある問題を修正します。

左側のメニューを使用して、特定のパッチページに移動します。
