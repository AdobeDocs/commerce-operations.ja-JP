---
title: ACSD-56979：ステージングアップデートの削除後に製品画像が削除される
description: ACSD-56979 パッチを適用すると、ステージングアップデートを削除した後に商品イメージが削除されるAdobe Commerceの問題が修正されます
feature: Products
role: Admin, Developer
exl-id: 1e0fbd5c-285b-408e-ba52-72619e29167b
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-56979：ステージングアップデートの削除後に製品画像が削除される

ACSD-56979 パッチは、ステージング環境の更新を削除した後に製品の画像が削除される問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.49 がインストールされている場合に使用できます。 パッチ ID は ACSD-56979 です。 この問題はAdobe Commerce 2.5.0 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6

**Adobe CommerceおよびMagento Open Source バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3 ～ 2.4.6-p7

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

製品画像は、ステージング更新を削除した後に削除されます。

<u> 再現手順 </u>:

1. Commerce管理サイドバーで、**[!UICONTROL Catalog]**/**[!UICONTROL Products]** に移動し、商品を作成します。
1. **[!UICONTROL Images and Videos]** の下で、画像をアップロードし、製品を保存します。
1. 「**[!UICONTROL Scheduled Changes]**」ボックスで「**[!UICONTROL Schedule New Update]**」を選択します。
   1. 数分後に開始日を選択してください。
   1. 終了日は選択しないでください。
1. **[!UICONTROL Scheduled Changes]** のボックスで、**[!UICONTROL View/Edit]** リンクを選択します。
1. **[!UICONTROL Remove from Update]**/**[!UICONTROL Delete the Update]** に移動し、「**[!UICONTROL Done]**」を選択します。
1. ページを更新します。

<u> 期待される結果 </u>:

予定されている開始日より前に更新が削除されるので、製品は変わりません。

<u> 実際の結果 </u>:

画像の内容が失われ、0 バイトと表示されます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md)[!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)」を参照してください。
