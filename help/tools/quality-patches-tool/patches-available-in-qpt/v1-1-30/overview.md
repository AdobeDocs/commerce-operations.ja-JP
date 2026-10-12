---
title: 概要：[!DNL Quality Patches Tool] （QPT） v1.1.30
description: このサブセクションでは、[!DNL Quality Patches Tool] （QPT） v1.1.30で利用可能なパッチによって修正された問題について詳しく説明します。
feature: Tools and External Services
role: Admin
exl-id: 36c6e0cc-fd8c-4583-b147-fe4897b101d8
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
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 0%
---
# 概要：[!DNL Quality Patches Tool] （QPT） v1.1.30

このサブセクションでは、[!DNL Quality Patches Tool] （QPT） v1.1.30で利用可能なパッチによって修正された問題について詳しく説明します。

QPT v1.1.30には次のパッチが含まれています。

1. **ACSD-50336**：商品の再入荷や価格の変更の際に商品アラートメールが送信されない問題を修正します。
1. **ACSD-50367**：値のない複数選択の顧客アドレス属性が作成された場合に、顧客アドレスの書き出しが機能しない問題を修正します。
1. **ACSD-49877**：ビデオがストリーミングサービスではなくリモートビデオファイルに直接リンクされている場合に、モバイル [!DNL Safari]でビデオ自動再生が機能しない問題を修正しました。
1. **ACSD-50165**: エラー&#x200B;*ファイルを削除できません。 警告！unlink：管理者*&#x200B;からJS/CSS キャッシュをフラッシュする際に、そのようなファイルまたはディレクトリはありません。
1. **ACSD-49737**: カード支払いに失敗した後、クーポンが誤って「使用」としてマークされる問題を修正します。
1. **ACSD-50814**：管理者ユーザーがクレジットメモを作成できない問題を修正します。
1. **ACSD-50116**：管理者ユーザーがサブカテゴリーレベル 3以下のURL書き換えを作成できない問題を修正します。
1. **ACSD-49513**: 0 バイトのファイルが原因でリモート ストレージの同期が失敗する問題を修正します。
1. **ACSD-46683**：送料が&#x200B;*まだ計算されていません*&#x200B;と表示される問題を修正します。
1. **ACSD-49129**: `rest/V1/products/sku/media`個の製品メディア API応答でコンテンツ属性（[!UICONTROL base64 image code]）が返されない問題を修正します。
1. **ACSD-50276**：複数選択の顧客属性が作成された場合に、ストアフロントで顧客登録フォームが機能しない問題を修正します。
1. **ACSD-50527**：空の動的ブロックを含むページを保存する際に発生するエラーを修正します。
1. **ACSD-49973**: GraphQLを使用してバンドルされた商品を取得する際のパフォーマンスが向上します。
1. **ACSD-51114**：非同期インデックス作成が有効になっている場合に、大きなカタログからランダムな商品が消える問題を修正します。 大規模なカタログの非同期インデックス再作成のパフォーマンスを向上させます。
1. **B2B-2598**: `availableStores`、`countries`、`country`、`currency`および`storeConfig`のGraphQL クエリにキャッシュ機能を追加します。

左側のメニューを使用して、特定のパッチページに移動します。
