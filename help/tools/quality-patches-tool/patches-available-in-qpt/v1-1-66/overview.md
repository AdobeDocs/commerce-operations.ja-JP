---
title: 概要： [!DNL Quality Patches Tool]  （QPT） v1.1.66
description: このサブセクションでは、 [!DNL Quality Patches Tool]  （QPT） v1.1.66 で使用可能なパッチによって修正された問題について詳しく説明します。
feature: Tools and External Services
role: Admin, Developer
exl-id: b5b80bfa-a52c-466b-b95c-23590e850aed
source-git-commit: 31a6b8296681a8f8aa23aa941c0637510b330cdc
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 0%

---

# 概要：[!DNL Quality Patches Tool] （QPT） v1.1.66

このサブセクションでは、[!DNL Quality Patches Tool] （QPT） v1.1.66 で使用可能なパッチによって修正された問題について詳しく説明します。

QPT v1.1.66 には、次のパッチが含まれています。
1. **ACP2E-3789**:WebAPI を使用した製品アップデート時にメディアファイルが重複していました。
1. **ACP2E-3918**：デフォルトの請求先住所なしで店舗での受け取りを使用している、ログインしている会社の顧客のチェックアウトに失敗しました。
1. **ACSD-65750**:GraphQLの「ルート」クエリが、ページビルダー製品コンテンツタイプで商品を順不同で返しました。
1. **ACSD-65775**：同じ項目の複数の数量が注文された場合に、REST API の注文の詳細で、誤った `base_row_total` と `row_total` の値が返されました。
1. **ACSD-65777**:`MediaGallery` GraphQL リクエストの商品イメージタイプの「types」フィールドが見つかりませんでした。
1. **ACSD-65848**：管理者のカテゴリの読み込みが非常に遅い。
1. **ACSD-65913**:OpenSearch が、同じ価格の製品を含むカテゴリに対して `illegal_argument_exception` をスローしました。
1. **ACSD-66041**:CountryID が見つからないため、アイルランド（IE）の郵便番号で受け取り場所を検索できませんでした。
1. **ACSD-66212**：顧客の CSV ファイルを 2 回読み込むと、2 回目以降の試行で失敗する問題を修正しました。

左側のメニューを使用して、特定のパッチページに移動します。
