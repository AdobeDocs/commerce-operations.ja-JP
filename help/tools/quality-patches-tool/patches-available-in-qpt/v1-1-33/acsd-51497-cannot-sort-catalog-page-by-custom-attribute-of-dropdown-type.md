---
title: 'ACSD-51497: ドロップダウン型のカスタム属性でカタログページを並べ替えられない'
description: お客様がカタログページをドロップダウン型のカスタム属性でソートできないAdobe Commerceの問題を修正するには、ACSD-51497 パッチを適用します。
feature: Attributes, Cache, Catalog Management, Categories
role: Developer
exl-id: c66a7e04-fd2a-47be-8f7a-7982780a5414
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

---

# ACSD-51497: *ドロップダウン*&#x200B;型のカスタム属性でカタログページを並べ替えることができません

ACSD-51497 パッチは、顧客がカタログページをタイプ *Dropdown*&#x200B;のカスタム属性で並べ替えることができない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.33がインストールされている場合に利用できます。 パッチ IDはACSD-51497です。 この問題は、Adobe Commerce 2.4.7で修正されています。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方式） 2.3.7 - 2.3.7-p4、2.4.1 - 2.4.6-p1

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

お客様は、タイプ *ドロップダウン*&#x200B;のカスタム属性でカタログページを並べ替えることができません。

<u>複製する手順</u>

1. 約6つのシンプルな商品をひとつのカテゴリーに割り当てます。
1. 商品属性を作成して、リストページの並べ替えオプションとして追加します。

   * **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Add New Attribute]**&#x200B;に移動します。
   * 「**[!UICONTROL Properties]**」タブで、次の値を設定します。

     * *[!UICONTROL Default Label]* = *テスト*
     * ストア所有者の&#x200B;*[!UICONTROL Catalog Input Type]* = *ドロップダウン*
     * *[!UICONTROL Options]*:

       * *first*
       * *秒*
       * *third*
       * *第四*

   * 「**[!UICONTROL Storefront Properties]**」タブで、次の値を設定します。

     * *[!UICONTROL Used for sorting in product listing]* = *はい*
     * 他のすべてのオプションを&#x200B;*デフォルト*&#x200B;のままにします。

1. *test*&#x200B;属性を&#x200B;**[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Attribute Set]**&#x200B;で設定された&#x200B;*Default*&#x200B;属性に割り当てます。
1. *test*&#x200B;属性値を持つように製品を設定します。

   * SKU: s00001、テスト：4番目
   * SKU: s00002、テスト：third
   * SKU: s00003、テスト：秒
   * SKU: s00004、テスト：最初
   * SKU: s00005、テスト：4番目
   * SKU: s00006、テスト：third

1. インデックスを再作成してキャッシュをクリアします。
1. ストアフロントのカテゴリに移動します。
1. *test*&#x200B;属性で並べ替えます。

<u>期待される結果</u>:

製品は、*test*&#x200B;属性で並べ替えられます。

<u>実際の結果</u>:

製品は、*test*&#x200B;属性で並べ替えられません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
