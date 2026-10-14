---
title: 概要：[!DNL Quality Patches Tool] （QPT） v1.1.83
description: このサブセクションでは、[!DNL Quality Patches Tool] （QPT） v1.1.83で利用可能なパッチによって修正された問題について詳しく説明します。
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
source-git-commit: 09eedab06d326baa0d4155274266dc3ef5356589
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 0%
---
# 概要：[!DNL Quality Patches Tool] （QPT） v1.1.83

このサブセクションでは、[!DNL Quality Patches Tool] （QPT） v1.1.83で利用可能なパッチによって修正された問題について詳しく説明します。

QPT v1.1.83には次のパッチが含まれています。

1. **AC-17975**：特定のPHP環境での管理者ワークフロー、チェックアウト認証、CAPTCHA処理、カテゴリ管理、設定ページ、コマンドライン操作に影響する複数のPHP 8.5互換性の問題を修正します。
1. **AC-18128**: GraphQLから返された注文日と注文コメントのタイムスタンプが、英語以外のロケール設定で誤ったカレンダー日付を表示する問題を修正しました。
1. **AC-18096**: Sales GraphQLの日付フィールドで、日付の形式をスラッシュ区切り（`/`）からダッシュ区切り（`-`）に戻すことで、以前のリリースとは異なる形式で日付が返される問題を修正しました。
1. **[ACP2E-4639](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-83/acp2e-4639.md)**:GraphQL スキーマで購買リストのアイテムの種類のスペルが間違っている問題を修正します。 古い`items` フィールドと`RequistionListItems` タイプは引き続き使用できますが、非推奨です。
1. **ACP2E-4838**：権限が制限された管理者ユーザーが顧客グリッドから顧客を削除できない問題を修正します。
1. **ACP2E-4877**: *保留中*&#x200B;の状態で&#x200B;**[!UICONTROL Payment on Account]**&#x200B;を使用して配置された注文を管理者で編集できない問題を修正しました。
1. **ACP2E-4908**：各ストアビューで各製品に対して別々のレイアウトキャッシュエントリが作成されたため、大きなカタログがRedisまたはValkeyで過度のメモリ使用を引き起こす問題を修正します。
1. **[AC-12854](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-83/ac-12854.md)**：管理画面で注文を再注文すると、次の順序番号を割り当てるのではなく、`-1`接尾辞を付けた新しい注文番号が作成される問題を修正します。
1. **ACP2E-4977**：設定可能な製品の請求書とクレジットメモの総計に&#x200B;**[!UICONTROL Fixed Product Tax]** （FPT）が含まれず、合計が注文合計よりも低くなる問題を修正します。
1. **AC-16530**: ショッピングカートがカタログ価格ルールの更新スケジュールを一貫して反映しなかった問題を修正します。
1. **AC-11389**：一部の丸めシナリオで割引、税金、注文合計が正しく計算されない問題を修正します。
1. **ACP2E-4998**: ペイロード内の1つのSKUが存在せず、有効なSKUが更新されない場合、`POST /V1/products/tier-prices` REST API リクエストがリクエスト全体に対して失敗する問題を修正します。
1. **ACP2E-5015**：管理者に共有カタログを保存すると、必要なカタログデータが利用できない場合に、割り当てられた製品と価格を誤って削除できる問題を修正しました。
1. **AC-14940**：管理画面で顧客アカウントの&#x200B;**[!UICONTROL Reset Password]**&#x200B;をクリックしても、ストア関連の一部のケースでパスワードリセットの電子メールが送信されない問題を修正しました。
1. **[ACP2E-5101](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-83/acp2e-5101.md)**: インデクサーが&#x200B;**[!UICONTROL Update by Schedule]**&#x200B;に設定されている場合にB2B モジュールのインストールが失敗する問題を修正します。
1. **ACP2E-5205**: カテゴリの読み込みに多額の時間がかかったり、多数のカテゴリや製品が含まれている場合にタイムアウトが発生したりする問題を修正します。 また、カテゴリのリーフごとに製品数が適切に表示されるようになりました。
1. **ACP2E-3211**: ストアフロントで同じ商品を同時にカートに追加すると、同じSKUのカート内に同じ商品を1つの商品にまとめるのではなく、別の商品が作成される問題を修正します。
1. **[ACP2E-5223](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-83/acp2e-5223.md)**: **[!UICONTROL Catalog Permissions]** インデックスに顧客グループから除外されたWeb サイトが含まれている問題を修正します。

左側のメニューを使用して、特定のパッチページに移動します。
