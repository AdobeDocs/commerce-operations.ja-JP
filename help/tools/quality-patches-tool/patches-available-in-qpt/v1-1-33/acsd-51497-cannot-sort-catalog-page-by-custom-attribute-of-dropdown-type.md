---
title: 'ACSD-51497: ドロップダウン タイプのカスタム属性でカタログ ページを並べ替えることができません'
description: ACSD-51497 パッチを適用すると、お客様がドロップダウンタイプのカスタム属性でカタログページを並べ替えることができないAdobe Commerceの問題を修正できます。
feature: Attributes, Cache, Catalog Management, Categories
role: Developer
exl-id: c66a7e04-fd2a-47be-8f7a-7982780a5414
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 0%

---

# ACSD-51497: カタログページをタイプ *ドロップダウン* のカスタム属性で並べ替えることができない

ACSD-51497 パッチでは、顧客がタイプ *ドロップダウン* のカスタム属性でカタログページを並べ替えることができない問題を修正しました。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.33 がインストールされている場合に使用できます。 パッチ ID は ACSD-51497 です。 この問題はAdobe Commerce 2.4.7 で修正されました。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.7 ～ 2.3.7-p4、2.4.1 ～ 2.4.6-p1

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

顧客がタイプ *ドロップダウン* のカスタム属性でカタログページを並べ替えることができない。

<u> 再現手順 </u>

1. 約 6 つのシンプルな製品を作成して、1 つのカテゴリに割り当てます。
1. 製品属性を作成して、リストページで並べ替えオプションとして追加します。

   * **[!UICONTROL Admin]**/**[!UICONTROL Stores]**/**[!UICONTROL Attributes]**/**[!UICONTROL Add New Attribute]** に移動します。
   * 「**[!UICONTROL Properties]**」タブで以下を設定します。

      * *[!UICONTROL Default Label]* = *test*
      * ストア所有者の *[!UICONTROL Catalog Input Type]* = *ドロップダウン*
      * *[!UICONTROL Options]*:

         * *first*
         * *秒*
         * *3 番目*
         * *4 番目*

   * 「**[!UICONTROL Storefront Properties]**」タブで以下を設定します。

      * *[!UICONTROL Used for sorting in product listing]* = *はい*
      * その他のオプションはすべて *デフォルト* のままにします。

1. *>* > *>* で設定した **[!UICONTROL Admin]** デフォルト **[!UICONTROL Stores]** 属性に **[!UICONTROL Attributes]** test **[!UICONTROL Attribute Set]** 属性を割り当てます。
1. *test* 属性値を持つように製品を設定します。

   * SKU: s00001、テスト：4 番目
   * SKU: s00002、テスト：third
   * SKU: s00003、テスト：second
   * SKU: s00004、テスト：最初
   * SKU: s00005、テスト：4 番目
   * SKU: s00006、テスト：third

1. キャッシュの再インデックスとクリア。
1. ストアフロントのカテゴリに移動します。
1. *test* 属性で並べ替えます。

<u> 期待される結果 </u>:

製品は *test* 属性で並べ替えられます。

<u> 実際の結果 </u>:

製品は、*test* 属性で並べ替えられていません。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[[!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html): Search for patches[!DNL Quality Patches Tool]」を参照してください。
