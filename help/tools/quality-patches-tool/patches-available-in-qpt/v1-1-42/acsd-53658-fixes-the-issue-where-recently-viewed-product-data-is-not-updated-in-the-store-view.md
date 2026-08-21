---
title: 'ACSD-53658: **[!UICONTROL Recently Viewed Product]** データがストアビューで正しく更新されない'
description: ストアビューで**[!UICONTROL Recently Viewed Product]** データが正しく更新されないAdobe Commerceの問題を修正するには、ACSD-53658 パッチを適用します。
feature: CMS, Personalization
role: Admin, Developer
exl-id: a91fac3d-cb6f-4f65-aec2-d28cee4fd39f
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# ACSD-53658: **[!UICONTROL Recently Viewed Product]** データがストアビューで正しく更新されません

ACSD-53658 パッチは、**[!UICONTROL Recently Viewed Product]** データがストアビューで正しく更新されない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.42がインストールされている場合に利用できます。 パッチ IDはACSD-53658です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p3

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

ストアビューで&#x200B;**[!UICONTROL Recently Viewed Product]** データが正しく更新されません。

<u>複製する手順</u>:

1. Admin パネルにログインします。
1. デフォルトのweb サイトの2番目のストアビューを作成します。
1. シンプルな商品の作成。
1. 新しいストアビューに別の商品名を設定します。
1. **[!UICONTROL Recently Viewed Product]** ウィジェットを作成します。
1. このウィジェットをホームページに表示するように設定します。
1. デフォルトのストアビューから、ストアフロントで製品ページを開きます。
1. ホームページを開きます。
1. ストアスイッチャーを使用して、2番目のストアビューに切り替えます。

<u>期待される結果</u>:

製品名がウィジェットで更新されます。

<u>実際の結果</u>:

製品名はウィジェットで更新されません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
