---
title: ACSD-51204：クレジットメモを作成した後に商品が再入荷しない
description: ACSD-51204 パッチを適用して、クレジットメモを作成した後に商品が在庫に戻らないAdobe Commerceの問題を修正します。
feature: Orders, Products, Returns
role: Admin
exl-id: a4dba28c-c239-4812-8b3a-ce0493f9b1aa
type: Troubleshooting
source-git-commit: 7054a5286f01e26e324401f4d8505e4e0faed93e
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 0%

---

# ACSD-51204：クレジットメモを作成した後に商品が再入荷しない

ACSD-51204 パッチは、クレジットメモを作成した後に製品が在庫を返品しない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.32がインストールされている場合に利用できます。 パッチ IDはACSD-51204です。 この問題は、Adobe Commerce 2.4.7で修正されています。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3 - 2.4.6-p1

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

売り切れた商品は、クレジットメモを作成した後に在庫に戻りません。

<u>複製する手順</u>:

1. **[!UICONTROL Adobe Commerce]**&#x200B;をインストールし、デフォルトの&#x200B;**[!UICONTROL Inventory Management Module]** source *と* stock *のみで*&#x200B;を有効にします。
1. 数量が&#x200B;**[!UICONTROL new product]** 10 *の*&#x200B;を追加します。
1. 製品を&#x200B;**[!UICONTROL default stock]**&#x200B;に割り当てます。
1. ストアフロントで、商品をカートに追加し、利用可能な全数量10を注文します。
1. 管理パネルで、注文の&#x200B;*請求書*&#x200B;と&#x200B;*配送*&#x200B;を生成します。
1. すべてのアイテムに「**[!UICONTROL Credit Memo]**&#x200B;在庫に戻る&#x200B;*」チェックボックスを選択して、*&#x200B;を作成します。
1. 管理画面で製品の&#x200B;**[!UICONTROL Salable Quantity]**&#x200B;を確認します。

<u>期待される結果</u>:

製品の販売可能数量は&#x200B;*10*&#x200B;に戻る必要があります。

<u>実際の結果</u>:

商品の販売可能数量は&#x200B;*0*&#x200B;のままです。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool]  ガイドの](/help/tools/quality-patches-tool/usage.md)>使用状況[!DNL Quality Patches Tool]。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [&#x200B; [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) ガイドの[!UICONTROL Quality Patches Tool]を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) ガイドの「[!DNL Quality Patches Tool] パッチを検索する」を参照してください。
