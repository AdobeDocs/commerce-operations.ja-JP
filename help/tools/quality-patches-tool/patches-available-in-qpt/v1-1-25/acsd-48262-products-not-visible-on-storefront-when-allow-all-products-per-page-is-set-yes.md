---
title: 'ACSD-48262: [!UICONTROL Allow All Products Per Page]が[!UICONTROL Yes]に設定されている場合、ストアフロントに製品が表示されない'
description: '[!UICONTROL Allow All Products Per Page]設定が[!UICONTROL Yes]に設定されている場合、ストアフロントに商品が表示されないAdobe Commerceの問題を修正するには、ACSD-48262 パッチを適用します。'
feature: Admin Workspace, Cache, Categories, Orders, Products, Storefront
role: Admin
exl-id: 733ac476-5c3c-4cbe-88b7-f436d15f1c7d
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# ACSD-48262: [!UICONTROL Allow All Products Per Page]が&#x200B;*[!UICONTROL Yes]*&#x200B;に設定されている場合、ストアフロントに製品が表示されない

ACSD-48262 パッチは、[!UICONTROL Allow All Products Per Page]設定が&#x200B;*[!UICONTROL Yes]*&#x200B;に設定されている場合に、ストアフロントに製品が表示されない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.25がインストールされている場合に利用できます。 パッチ IDはACSD-48262です。 この問題は、Adobe Commerce 2.4.6で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） >=2.4.5 &lt; 2.4.6

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

ACSD-48262 パッチは、[!UICONTROL Allow All Products Per Page]設定が&#x200B;*[!UICONTROL Yes]*&#x200B;に設定されている場合に、ストアフロントに製品が表示されない問題を修正します。

<u>複製する手順</u>:

1. テストカテゴリを作成します。
1. テストカテゴリにテスト製品を作成します。
1. ストアフロントでカテゴリーページをテストするには、製品を参照し、製品が表示されていることを確認します。
1. **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]**&#x200B;に移動し、[!UICONTROL Allow All Products Per Page]設定を&#x200B;*[!UICONTROL Yes]*&#x200B;に設定します。
1. キャッシュをクリアします。
1. ストアフロントのカテゴリーページを確認します。

<u>期待される結果</u>:

製品が表示されます。

<u>実際の結果</u>:

製品は表示されません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。


## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
