---
title: ACSD-56546：設定可能なバンドル商品が、ストアフロントに在庫切れとして表示される
description: 「*[!UICONTROL Display Out of Stock Products]*」設定オプションが無効になっている場合に、コンフィギュラブルおよびバンドル製品がストアフロントで在庫切れとして表示されるAdobe Commerceの問題を修正するには、ACSD-56546 パッチを適用します。
feature: Storefront, Products
role: Admin, Developer
exl-id: d9bb05ca-a84e-48bb-957e-55b28631b3cb
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 0%

---

# ACSD-56546：設定可能なバンドル商品が、ストアフロントに在庫切れとして表示される

ACSD-56546 パッチは、設定可能なバンドル製品がストアフロントで在庫切れとして表示される問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.48がインストールされている場合に利用できます。 パッチ IDはACSD-56546です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p3

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.6-p4

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

*[!UICONTROL Display Out of Stock Products]* オプションが無効になっている場合、コンフィグ可能な商品およびバンドル商品はストアフロントで在庫切れとして表示されます。

<u>複製する手順</u>:

1. **[!UICONTROL Display Out of Stock Products]** オプションを&#x200B;*No*&#x200B;に設定します。
1. web サイト、実店舗、ストアビューの作成。
1. ソースと在庫を作成し、それを2番目のweb サイトに割り当てます。
1. 2つの子製品を含む&#x200B;*設定可能な製品*&#x200B;を作成します。 両方のソースと両方のweb サイトに子製品を割り当てます。
1. 両方のソースで&#x200B;*qty=0*&#x200B;を持つように、最初の子製品を更新します。
1. 2番目の子製品を更新し、2番目のweb サイトで無効にします。
1. 完全にインデックス再作成を行います。
1. 2番目のweb サイトの設定可能な製品を含むカテゴリを確認します。

<u>期待される結果</u>:

在庫切れの設定可能な商品は、ストアフロントには表示されません。

<u>実際の結果</u>:

*[!UICONTROL Display Out of Stock Products]* オプションが無効になっている場合でも、在庫切れの設定可能な商品はストアフロントに表示されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) パッチを検索する」を参照してください。
