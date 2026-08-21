---
title: 'ACSD-46767: [!UICONTROL Category] ページキャッシュは、在庫量が変更されると無効になります'
description: ACSD-46767 パッチを適用して、在庫量が変更されたときに[!UICONTROL Category] ページキャッシュが無効になるAdobe Commerceの問題を修正します。商品がまだ在庫がある場合でも、この問題を修正します。
feature: Cache, Products, Inventory
role: Admin, Developer
exl-id: 5872dca7-fdef-47ad-8718-bf343cd3a42a
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%

---

# ACSD-46767: [!UICONTROL Category] ページキャッシュは、在庫量が変更されると無効になります

ACSD-46767 パッチは、在庫量が変更されたときに、商品がまだ在庫がある場合でも[!UICONTROL Category] ページキャッシュが無効になる問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.46がインストールされている場合に利用できます。 パッチ IDはACSD-46767です。 この問題は、Adobe Commerce 2.4.6で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.5-p5

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

在庫量が変更されると、[!UICONTROL Category] ページキャッシュは無効になります。

<u>複製する手順</u>:

1. いくつかの商品を作成し、同じカテゴリーに追加します。
1. ストアフロントで&#x200B;*[!UICONTROL Category]* ページを開き、ページがキャッシュされていることを確認します。
1. カテゴリ *の商品の1つに注文します（商品の数量は変更されましたが、商品の在庫は残っています）*。
1. ストアフロントの[!UICONTROL Category] ページをもう一度開きます。

<u>実際の結果</u>:

ページがキャッシュから読み込まれない。 再生成されます。

<u>期待される結果</u>:

ページがキャッシュから読み込まれます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) パッチを検索する」を参照してください。
