---
title: 概要： [!DNL Quality Patches Tool]  （QPT） v1.1.68
description: ここでは、 [!DNL Quality Patches Tool]  （QPT） v1.1.68 で使用可能なパッチによって修正された問題について詳しく説明します。
feature: Tools and External Services
role: Admin, Developer
exl-id: 74094036-cb1b-419f-b287-ca24d351a448
source-git-commit: 674aa68a0f7ecf30481a6d4f33b119d295c51a6b
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 0%

---

# 概要：[!DNL Quality Patches Tool] （QPT） v1.1.68

このサブセクションでは、[!DNL Quality Patches Tool] （QPT） v1.1.68 で使用可能なパッチによって修正された問題について詳しく説明します。

QPT v1.1.68 には、次のパッチが含まれています。
1. **ACSD-58131**：メディアギャラリーに 0 バイトの画像が存在するため、ディレクトリ内のすべての画像が表示または選択できません。
1. **ACSD-62146**：住所検索が有効で、「顧客住所制限の数」が 1 に設定されている場合、選択した請求先住所がチェックアウト支払いページに表示されません。
1. **[ACSD-62415](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-68/acsd-62415-adobe-commerce-backend-loads-categories-very-slowly.md)**:Adobe Commerce バックエンドによるカテゴリの読み込みに時間がかかる。
1. **ACSD-65938**：請求書の作成に失敗した場合でも、ギフトカードの E メールが送信されていました。
1. **ACSD-66072**:[!UICONTROL Related Products Rule] が設定されているときに内部サーバーエラーが発生したため、関連商品が商品詳細ページのGraphQLで返されません。
1. **ACSD-66082**：製品の読み込みから製品のスウォッチ画像を更新できない。
1. **ACSD-66179**:「Not Capture」支払タイプの請求書をキャンセルすると、404 エラーページが表示される。
1. **ACSD-66233**：製品を追加ポップアップが読み込まれないので、管理者ユーザーがカテゴリに製品を追加できませんでした。
1. **ACSD-66506**：共有カタログ製品を削除して再割り当てした後、バックエンドエラーが発生する。
1. **ACSD-66865**：カタログ価格ルールを保存するとインデクサーが無効になり、影響を受ける製品のみを再インデックス化する代替手段が提供されます。
1. **ACSD-66233**：製品リストポップアップが応答しないため、管理者が製品を追加できない。
1. **ACSD-66506**：以前に割り当てられた共有カタログの製品が削除され、新しい製品が割り当てられると、バックエンドエラーが発生しました。
1. **ACSD-66865**:**[!UICONTROL Catalog Price Rule]** を保存するとインデクサーが無効になり、影響を受ける製品のみを再インデックス化する代替手段が提供されます。
1. **ACSD-66889**: CLI でインベントリの再インデックス中にエラーが発生しました。
1. **ACSD-66963**：仮想製品の割引に対して、`estimateTotals` mutation が null を返します。
1. **ACSD-66965**：購買依頼リスト・ページの「印刷」オプションでエラーが発生します。
1. **ACSD-67039**: rp_token システム属性の検証により、顧客レコードが保存されませんでした。
1. **ACSD-66963**：仮想商品を含む買い物かごに割引コードが適用された場合、EstimateTotals ミューテーションが割引に対して null を返します。
1. **ACSD-66965**：ページの **[!UICONTROL Print]** オプション **[!UICONTROL Requisition List]** 原因でエラーが発生します。
1. **ACSD-67039**:`rp_token` システム属性の検証が原因で、顧客レコードが保存されませんでした。


左側のメニューを使用して、特定のパッチページに移動します。
