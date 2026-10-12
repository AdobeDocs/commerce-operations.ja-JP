---
title: 概要：[!DNL Quality Patches Tool] （QPT） v1.1.72
description: このサブセクションでは、[!DNL Quality Patches Tool] （QPT） v1.1.72で利用可能なパッチによって修正された問題について詳しく説明します。
feature: Tools and External Services
role: Admin, Developer
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
source-wordcount: '276'
ht-degree: 0%
---
# 概要：[!DNL Quality Patches Tool] （QPT） v1.1.72

このサブセクションでは、[!DNL Quality Patches Tool] （QPT） v1.1.72で利用可能なパッチによって修正された問題について詳しく説明します。

QPT v1.1.72には、次のパッチが含まれています。

1. **ACSD-66807**: `report_viewed_product_index` テーブルに、製品ページビューの数が正しくありません。
1. **ACSD-67187**：デフォルト以外のWeb サイトに制限されている管理者ユーザーにエラーが表示されます。*&quot;*&#x200B;続行するには、少なくともパブリック共有カタログを作成してください*。会社グリッドの&#x200B;**[!UICONTROL Add New Company]** ボタンにアクセスできません。
1. **ACSD-67383**：同じセッションで2つの会社管理者アカウントを持つ顧客としてログインする際にエラーが発生しました。
1. **ACSD-67424**: `GET /carts/search` [!DNL REST] API応答の`updated_at`の値が、交渉可能な見積もりを使用する際に&#x200B;**[!UICONTROL Admin panel]**&#x200B;に表示される値と一致しません。
1. **ACSD-67518**：高度なレポートでは、行数がバッチサイズを超えると、重複したヘッダー行が生成されます。
1. **ACSD-67639**: **[!UICONTROL Dynamic Price]**&#x200B;が&#x200B;*No*&#x200B;に設定されているバンドル製品のクレジットメモの作成に失敗しました。
1. **ACSD-67696**: `media_gallery`個のエントリが、キャッシュフラッシュ後にCart GraphQL製品ノードに戻りません。
1. **ACSD-67941**：不明なフィルター名を持つGraphQL リクエストは、PHP例外ログを発生させます。
1. **ACSD-67946**：買い物かごの更新で、重複したエラーバナーが表示されます。
1. **ACSD-68011**：存在しないSKUが/V1/sharedCatalog/:id/assignProducts APIを介して共有カタログに割り当てられています。
1. **ACSD-68040**: [!DNL MariaDB] 10.6でフロントエンドの検索ページが大きな履歴で遅くなります。
1. **ACSD-68064**：高度にネストされたカテゴリを持つ環境で、スケジュールされた更新中に作成されたエントリを複製します。
1. **ACSD-68092**: スケジュールされた更新とベース製品データ間の同期が不適切なため、複数回保存すると、バンドル製品オプションが失われます。
1. **ACSD-68118**: `customerCart` [!DNL GraphQL] クエリで、ストアビューに対して誤った製品属性値が返されます。


左側のメニューを使用して、特定のパッチページに移動します。
