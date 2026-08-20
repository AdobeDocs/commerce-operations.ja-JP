---
title: 'ACSD-61322: [!UICONTROL Shared Catalogue]に割り当てられていない製品がXML サイトマップに含まれる'
description: 既定（一般）グループの[!UICONTROL Shared Catalog]に割り当てられていない製品/カテゴリがXML サイトマップに含まれているAdobe Commerceの問題を修正するには、ACSD-61322 パッチを適用します。
feature: Site Navigation, B2B
role: Admin, Developer
exl-id: 4698ba5a-673e-4bf0-b36c-39f6122dab26
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# ACSD-61322: [!UICONTROL Shared Catalogue]に割り当てられていない製品がXML サイトマップに含まれる

ACSD-61322 パッチは、デフォルト（一般）グループの[!UICONTROL Shared Catalog]に割り当てられていない製品/カテゴリが、XML サイトマップにまだ含まれている問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.52がインストールされている場合に利用できます。 パッチ IDはACSD-61322です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p1

**Adobe Commerceのバージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方法） 2.4.6 - 2.4.7-p2

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

既定（一般）グループの[!UICONTROL Shared Catalog]に割り当てられていない製品/カテゴリは、引き続きXML サイトマップに含まれます。

<u>複製する手順</u>:

1. いくつかのカテゴリを作成し、製品を追加します（例えば、カテゴリ 1とカテゴリ 2）。
1. **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**&#x200B;に移動し、*[!UICONTROL Company and Shared Catalog]*&#x200B;を有効にします。
1. **[!UICONTROL Catalog]** > **[!UICONTROL Shared Catalogs]**&#x200B;に移動し、既定のカタログを変更します。
1. **[!UICONTROL Select]** ドロップダウンから、**[!UICONTROL Set Pricing and Structure]**&#x200B;を選択し、**[!UICONTROL Configure]**&#x200B;をクリックします。
1. *カテゴリ 1 > カテゴリ 2* カテゴリの下で、[!UICONTROL Shared Catalog]に含まれない製品の選択を解除します。
1. **[!UICONTROL Next]**&#x200B;をクリックしてカタログを生成します。
1. ストアフロントで顧客アカウントを作成します。
1. *カテゴリ 1 > カテゴリ 2* カテゴリに移動します。 [!UICONTROL Shared Catalog]に割り当てられた製品のみが表示されます。
1. **[!UICONTROL Marketing]** > **[!UICONTROL SEO & Search]** > **[!UICONTROL Site Map]**&#x200B;に移動し、新しいサイトマップを生成します。
1. ストアフロントで`sitemap.xml`を開きます。
1. [!UICONTROL Shared Catalog]に含まれていない商品を検索します。

<u>期待される結果</u>:

サイトマップには、[!UICONTROL Shared Catalog]に割り当てられていない製品とカテゴリへのリンクは含まれていません。

<u>実際の結果</u>:

サイトマップには、[!UICONTROL Shared Catalog]に割り当てられていない製品とカテゴリへのリンクが含まれています。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
