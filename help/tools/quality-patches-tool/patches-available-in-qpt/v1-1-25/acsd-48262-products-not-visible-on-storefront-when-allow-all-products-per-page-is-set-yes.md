---
title: ACSD-48262:[!UICONTROL Allow All Products Per Page] が [!UICONTROL Yes] に設定されている場合、ストアフロントに製品が表示されない
description: '[!UICONTROL Allow All Products Per Page] 設定が [!UICONTROL Yes] に設定されている場合にストアフロントに商品が表示されないAdobe Commerceの問題を修正するために、ACSD-48262 パッチを適用してください。'
feature: Admin Workspace, Cache, Categories, Orders, Products, Storefront
role: Admin
exl-id: 733ac476-5c3c-4cbe-88b7-f436d15f1c7d
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---

# ACSD-48262:[!UICONTROL Allow All Products Per Page] が *[!UICONTROL Yes]* に設定されている場合、ストアフロントに製品が表示されない

[!UICONTROL Allow All Products Per Page] 設定が *[!UICONTROL Yes]* に設定されている場合、ACSD-48262 パッチにより、ストアフロントに製品が表示されない問題が修正されました。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.25 がインストールされている場合に使用できます。 パッチ ID は ACSD-48262 です。 この問題はAdobe Commerce 2.4.6 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） >=2.4.5 &lt; 2.4.6

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

[!UICONTROL Allow All Products Per Page] 設定が *[!UICONTROL Yes]* に設定されている場合、ACSD-48262 パッチにより、ストアフロントに製品が表示されない問題が修正されました。

<u> 再現手順 </u>:

1. テストカテゴリを作成します。
1. テストカテゴリでテスト製品を作成します。
1. 製品を参照してストアフロントのカテゴリページをテストし、製品が表示されていることを確認します。
1. **[!UICONTROL Stores]**/**[!UICONTROL Configuration]**/**[!UICONTROL Catalog]** に移動し、[!UICONTROL Allow All Products Per Page] 設定を *[!UICONTROL Yes]* に設定します。
1. キャッシュをクリアします。
1. ストアフロントのカテゴリページをご確認ください。

<u> 期待される結果 </u>:

商品が表示されます。

<u> 実際の結果 </u>:

商品が表示されません。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。


## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)」を参照してください。
