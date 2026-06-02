---
title: 'ACSD-53636: [!UICONTROL Product Listing] ページに正規価格が表示されません'
description: ACSD-53636 パッチを適用して、特別価格の子商品を含む設定可能な商品の*[!UICONTROL Product Listing]* ページに通常価格が表示されないAdobe Commerceの問題を修正します。
feature: Catalog Management, Products
role: Admin, Developer
exl-id: e6d66ae4-2c21-466a-b03c-a1f486e7fa29
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 0%

---

# ACSD-53636: *[!UICONTROL Product Listing]* ページに正規価格が表示されません

ACSD-53636 パッチは、特別価格の子製品を持つ設定可能な製品について、*[!UICONTROL Product Listing]* ページに正規価格が表示されない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.43がインストールされている場合に利用できます。 パッチ IDはACSD-53636です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3 - 2.4.4-p6

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

特別価格の子商品を含む設定可能な商品については、*[!UICONTROL Product Listing]* ページに正規価格は表示されません。

<u>複製する手順</u>:

1. 管理者にログインして&#x200B;**[!UICONTROL Admin]** > **[!UICONTROL Catalog]**&#x200B;に移動し、設定可能な製品を作成または開きます。
2. 子商品を開き、子商品のすべてまたは1つに特別価格を追加して、商品を保存します。
3. フロントエンドに移動して、設定可能な製品の&#x200B;**[!UICONTROL Product Detail]** ページを開きます。特別価格の子製品のスウォッチで、*[!UICONTROL Regular price]*&#x200B;が取り消されます（予想）。
4. フロントエンドに移動し、特別価格で設定可能な製品の&#x200B;**[!UICONTROL Product Listing]** ページを開きます。設定可能な製品スウォッチの変更で、*[!UICONTROL Product Detail Page]*&#x200B;やその他のシンプルな製品と異なり、通常価格が表示されないことをご確認ください。

<u>期待される結果</u>:

*[!UICONTROL Product Listing]* ページで、コンフィグ可能な製品に子製品の通常価格が表示されます。

<u>実際の結果</u>:

*[!UICONTROL Product Listing]* ページで、コンフィグ可能な製品には、子製品の通常の価格が表示されません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) パッチを検索する」を参照してください。
