---
title: 'ACSD-48404: *[!UICONTROL Remember Category Pagination] = [!UICONTROL Yes]*は、ブラウザーの戻るボタンを押すとエラーが発生します'
description: ブラウザーの戻るボタンを押すと、*[!UICONTROL Remember Category Pagination] = [!UICONTROL Yes]*がエラーを引き起こすAdobe Commerceの問題を修正するには、ACSD-48404 パッチを適用します。
feature: Categories
role: Admin
exl-id: 8c08f0e2-d4f9-4ac8-b8e8-85b4a7de98fb
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# ACSD-48404: *[!UICONTROL Remember Category Pagination]=[!UICONTROL Yes]*&#x200B;は、ブラウザーの戻るボタンを押すとエラーが発生します

ACSD-48404 パッチは、*[!UICONTROL Remember Category Pagination]=[!UICONTROL Yes]*&#x200B;でブラウザーの戻るボタンを押すとエラーが発生する問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.27がインストールされている場合に利用できます。 パッチ IDはACSD-48404です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3-p3

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.0 - 2.4.3-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

ブラウザーの戻るボタンを押すと、*[!UICONTROL Remember Category Pagination]=[!UICONTROL Yes]*&#x200B;がエラーを引き起こします。


<u>複製する手順</u>:

1. **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Storefront]**&#x200B;に移動し、*[!UICONTROL Remember Category Pagination]*&#x200B;を&#x200B;*Yes*&#x200B;に設定します。
1. ストアフロントでカテゴリを開きます。
1. *[!UICONTROL Show Per Page]* ドロップダウンで、デフォルト値ではない値を選択します。 オプションを選択すると、ページが再ロードされます。
1. ページが再読み込みされたら、カタログページで任意の商品をクリックします。
1. 開いた製品詳細ページで、ブラウザーの&#x200B;**[!UICONTROL Back]** ボタンをクリックします。

<u>期待される結果</u>:

カタログページが再度開きます。

<u>実際の結果</u>:

カテゴリーページがエラーを返します。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
