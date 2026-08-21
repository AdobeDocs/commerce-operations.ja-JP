---
title: ACSD-57941：製品オプションが管理者ストアに誤って割り当てられる
description: ACSD-57941 パッチを適用して、製品オプションが各ストアではなく管理者ストアに誤って割り当てられるAdobe Commerceの問題を修正します。
feature: Products
role: Admin, Developer
exl-id: a78c1797-c366-4931-b036-966d3dcf59bb
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---

# ACSD-57941：製品オプションが管理者ストアに誤って割り当てられる

ACSD-57941 パッチは、製品オプションがそれぞれのストアではなく管理者ストアに誤って割り当てられる問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.49がインストールされている場合に利用できます。 パッチ IDはACSD-57941です。 この問題は、Adobe Commerce 2.4.7で修正されています。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p3

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3 - 2.4.6-p7

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

製品オプションが、それぞれのストアではなく、管理者ストアに誤って割り当てられる。

<u>複製する手順</u>:

1. シンプルな商品の作成。
1. いくつかのカスタムオプションを使用して、同じ製品をインポートします。
1. **[!UICONTROL Catalog]** > **[!UICONTROL Products]**&#x200B;に移動し、作成した製品を開きます。 **[!UICONTROL Customizable options]**&#x200B;をクリックし、読み込んだオプションが表示されていることを確認します。
1. 同じファイルをもう数回読み込みます。

<u>期待される結果</u>:

カスタムオプションが更新されます。

<u>実際の結果</u>:

製品のカスタムオプションが重複しています。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
