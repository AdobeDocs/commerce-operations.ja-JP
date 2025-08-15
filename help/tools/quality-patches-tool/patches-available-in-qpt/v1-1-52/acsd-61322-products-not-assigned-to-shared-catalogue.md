---
title: ACSD-61322:[!UICONTROL Shared Catalogue] に割り当てられていない製品は、XML サイトマップに含まれます
description: ACSD-61322 パッチを適用すると、Adobe Commerceの問題が修正されます。この問題では、デフォルト（一般）グループの [!UICONTROL Shared Catalog] に割り当てられていない products/categories が、XML サイトマップに引き続き含まれます。
feature: Site Navigation, B2B
role: Admin, Developer
exl-id: 4698ba5a-673e-4bf0-b36c-39f6122dab26
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---

# ACSD-61322:[!UICONTROL Shared Catalogue] に割り当てられていない製品は、XML サイトマップに含まれます

ACSD-61322 パッチにより、デフォルト（一般）グループの [!UICONTROL Shared Catalog] に割り当てられていない製品/カテゴリが XML サイトマップにまだ含まれている問題が修正されました。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.52 がインストールされている場合に使用できます。 パッチ ID は ACSD-61322 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p1

**Adobe Commerce バージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方法） 2.4.6 ～ 2.4.7-p2

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

デフォルト（一般）グループの [!UICONTROL Shared Catalog] に割り当てられていない製品やカテゴリは、XML サイトマップに引き続き含まれます。

<u> 再現手順 </u>:

1. いくつかのカテゴリを作成して、製品を追加します（例えば、カテゴリ 1 とカテゴリ 2）。
1. **[!UICONTROL Stores]**/**[!UICONTROL Configuration]**/**[!UICONTROL General]**/**[!UICONTROL B2B Features]** に移動し、*[!UICONTROL Company and Shared Catalog]* を有効にします。
1. **[!UICONTROL Catalog]**/**[!UICONTROL Shared Catalogs]** に移動し、デフォルトカタログを変更します。
1. 「**[!UICONTROL Select]**」ドロップダウンから「**[!UICONTROL Set Pricing and Structure]**」を選択し、「**[!UICONTROL Configure]**」をクリックします。
1. *カテゴリ 1/カテゴリ 2* カテゴリで、[!UICONTROL Shared Catalog] に含めない製品の選択を解除します。
1. 「**[!UICONTROL Next]**」をクリックし、カタログを生成します。
1. ストアフロントで、顧客アカウントを作成します。
1. *カテゴリ 1/カテゴリ 2* カテゴリに移動します。 [!UICONTROL Shared Catalog] ーザーに割り当てられた製品のみが表示されます。
1. **[!UICONTROL Marketing]**/**[!UICONTROL SEO & Search]**/**[!UICONTROL Site Map]** に移動して、新しいサイトマップを生成します。
1. ストアフロントの `sitemap.xml` を開きます。
1. [!UICONTROL Shared Catalog] に含めなかった製品を検索します。

<u> 期待される結果 </u>:

サイトマップには、[!UICONTROL Shared Catalog] ーザーに割り当てられていない製品およびカテゴリへのリンクは含まれていません。

<u> 実際の結果 </u>:

サイトマップには、[!UICONTROL Shared Catalog] ージに割り当てられていない製品およびカテゴリへのリンクが含まれています。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md)[!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[[!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html): Search for patches[!DNL Quality Patches Tool]」を参照してください。
