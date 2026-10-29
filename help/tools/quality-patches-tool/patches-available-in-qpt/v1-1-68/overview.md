---
title: 概要：[!DNL Quality Patches Tool] （QPT） v1.1.68
description: このサブセクションでは、[!DNL Quality Patches Tool] （QPT） v1.1.68で利用可能なパッチによって修正された問題について詳しく説明します。
feature: Tools and External Services
role: Admin, Developer
exl-id: 74094036-cb1b-419f-b287-ca24d351a448
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
source-git-commit: a257144a94d94d7eb572031e2a188809cbff6ea8
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 0%
---
# 概要：[!DNL Quality Patches Tool] （QPT） v1.1.68

このサブセクションでは、[!DNL Quality Patches Tool] （QPT） v1.1.68で利用可能なパッチによって修正された問題について詳しく説明します。

QPT v1.1.68には次のパッチが含まれています。

1. **ACSD-58131**&#x200B;古いメディアギャラリーは、0 バイトの画像ファイルが原因で画像を読み込めません。
1. **ACSD-62146**：アドレス検索が有効で「顧客アドレス数の制限」が1に設定されている場合、選択した請求先住所がチェックアウト支払いページに表示されなくなります。
1. **ACSD-62415**: Adobe Commerceのバックエンドでは、カテゴリーの読み込みが非常に遅くなっています。
1. **ACSD-65938**：請求書の作成に失敗した場合でも、ギフトカードの電子メールが送信されました。
1. **ACSD-66072**: [!UICONTROL Related Products Rule]の設定時に内部サーバーエラーが発生したため、製品詳細ページのGraphQLから関連製品が返されません。
1. **ACSD-66082**：製品の読み込みによって製品のスウォッチ画像を更新できません。
1. **ACSD-66179**: 「取り込みなし」支払いタイプの請求書をキャンセルすると、404 エラーページが表示されます。
1. **ACSD-66233**：管理者ユーザーは、[!UICONTROL Add Product] ポップアップが読み込まれなかったため、カテゴリに製品を追加できませんでした。
1. **ACSD-66506**：共有カタログ製品の削除と再割り当て後にバックエンドエラーが発生します。
1. **ACSD-66865**: **[!UICONTROL Catalog Price Rule]**&#x200B;を保存すると、インデクサーが無効になり、影響を受ける製品のみを再インデックスする代わりに使用できます。
1. **ACSD-66889**: CLIでインベントリの再インデックス中にエラーが発生しました。
1. **ACSD-66963**: `estimateTotals`の突然変異は、仮想商品を含むカートに割引コードが適用された場合、割引として&#x200B;*null*&#x200B;を返します。
1. **[!UICONTROL Requisition List]** ページの&#x200B;**ACSD-66965**: **[!UICONTROL Print]** オプションでエラーが発生します。
1. **ACSD-67039**: `rp_token` システム属性の検証により、顧客レコードが保存されませんでした。

左側のメニューを使用して、特定のパッチページに移動します。
