---
title: 概要：[!DNL Quality Patches Tool] （QPT） v1.1.39
description: このサブセクションでは、[!DNL Quality Patches Tool] （QPT） v1.1.39で利用可能なパッチによって修正された問題について詳しく説明します。
feature: Tools and External Services
role: Admin, Developer
exl-id: 6116f566-2ff8-4148-ab60-cec65f9b7a6f
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
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 0%
---
# 概要：[!DNL Quality Patches Tool] （QPT） v1.1.39

このサブセクションでは、[!DNL Quality Patches Tool] （QPT） v1.1.39で利用可能なパッチによって修正された問題について詳しく説明します。

QPT v1.1.39には次のパッチが含まれています。

1. **ACSD-53704**：報酬ポイントの有効期限が切れた後、報酬ポイントの残高の履歴が誤って計算される問題を修正します。
1. **ACSD-53583**: *カテゴリ製品*&#x200B;および&#x200B;*製品カテゴリ* インデクサーの部分的なインデックス再作成パフォーマンスを向上させます。
1. **ACSD-54026**：権限のないユーザーに対する`updateCompanyRole` GraphQL リクエストの誤ったエラーメッセージを修正します。
1. **ACSD-54106**: トルコ語のアクセント記号の名前によるカテゴリ製品の並べ替えが正しくない問題を修正します。
1. **ACSD-52219**：ブックマーク ビューを頻繁に切り替える際に、管理者グリッドが保存したフィルターが期待どおりに機能しない問題を修正します。
1. **ACSD-54342**：無効なエラーメッセージ *データ構造のエラーを修正します。有効なデータを含まないCSV ファイルを読み込むと、値が混在します*。
1. **ACSD-54660**:GraphQLのお客様の注文を`sort_field`および`sort_direction`で並べ替えるために、新しい入力属性&#x200B;*sort*&#x200B;を追加しました。
1. **ACSD-54776**:2番目のweb サイト、ストア、ストアビューで、チェックされていない&#x200B;*[!UICONTROL Use Default Value]*&#x200B;およびデフォルト以外の製品フィールド値が保存されない問題を修正します。
1. **ACSD-53998**：顧客アカウントからログアウトした後、**[!UICONTROL Customer Segment]**&#x200B;に基づく&#x200B;**[!UICONTROL Dynamic Block]**&#x200B;が正しく機能しない問題を修正します。
1. **ACSD-53204**：修正&#x200B;*製品を保存できません。* `rest/V1/products/<sku>/media` エンドポイントを使用して製品ギャラリーに画像を追加する同時要求を行う際にエラーが発生しました。
1. **ACSD-47657**: AWS資格情報のキャッシュ メカニズムを追加しました。 認証情報プロバイダーは、EC2設定のためにAWSから取得した認証情報をキャッシュするために、Magento キャッシュを使用するようになりました。

左側のメニューを使用して、特定のパッチページに移動します。
