---
title: ACSD-48300：設定可能な製品が削除されている場合、返品を作成できない
description: 設定可能な商品が削除されると返品を作成できないAdobe Commerceの問題を修正するために、ACSD-48300 パッチを適用してください。
feature: Admin Workspace, Configuration, Orders, Products, Returns
role: Admin
exl-id: 50139364-e2ea-47a8-9bca-09876dd0e70d
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# ACSD-48300：設定可能な製品が削除されている場合、返品を作成できない

ACSD-48300 パッチは、設定可能な製品が削除された場合にリターンを作成できない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.25 がインストールされている場合に使用できます。 パッチ ID は ACSD-48300 です。 この問題はAdobe Commerce 2.4.6 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.0 ～ 2.4.5-p1

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

設定可能な商品が削除されている場合、返品を作成することはできません。

<u> 再現手順 </u>:

1. **[!UICONTROL Stores]**/**[!UICONTROL Configuration]**/**[!UICONTROL Sales]**/**[!UICONTROL Sales]**/**[!UICONTROL RMA Settings]** のストアフロントで RMA を有効にします。
1. 設定可能な商品を作成します。
1. ストアフロントで、アカウントを作成（またはログイン）します。
1. 設定可能な製品を最初の項目として買い物かごに追加します。
1. 後で簡単な製品を追加してください。
1. 注文します。
1. 注文を発送します。
1. ここで、設定可能な製品のみを削除します（子製品は削除しないでください）。
1. ストアフロントで **[!UICONTROL My Orders]** に移動し、注文を確認します。
1. 「**[!UICONTROL Return]**」をクリックします。

<u> 期待される結果 </u>:

管理者は、設定可能な商品が削除された場合でも、項目を返すことができます。

<u> 実際の結果 </u>:

項目を返す際にエラーが発生します。

```
report.CRITICAL: Error: Call to a member function getShipmentType() on null in magento2ee/app/code/Magento/Rma/view/frontend/templates/return/create.phtml:52
```

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)」を参照してください。
