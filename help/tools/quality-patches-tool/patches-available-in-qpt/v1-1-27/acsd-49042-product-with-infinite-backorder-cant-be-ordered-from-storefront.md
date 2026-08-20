---
title: ACSD-49042：無限のバックオーダーを持つ製品をストアフロントから注文できない
description: 無限のバックオーダーを持つ商品をストアフロントから注文できないAdobe Commerceの問題を修正するには、ACSD-49042 パッチを適用します。
feature: Admin Workspace, Orders, Products, Storefront
role: Admin
exl-id: b94d06c0-806a-40be-bcd4-d6b8e5e474c3
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 0%

---

# ACSD-49042：無限のバックオーダーを持つ製品をストアフロントから注文できない

ACSD-49042 パッチは、無限のバックオーダーを持つ製品をストアフロントから注文できない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.27がインストールされている場合に利用できます。 パッチ IDはACSD-49042です。 この問題はAdobe Commerce 2.4.5で修正されています。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.4-p2

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

このエラーは、バックオーダーが無限にある商品をストアフロントから注文できない場合に発生します。

<u>複製する手順</u>:

1. 次の設定設定を設定します。
   * **[!UICONTROL Display Out of Stock Products]**&#x200B;が&#x200B;*[!UICONTROL Yes]*&#x200B;に設定されました。
   * **[!UICONTROL Backorders]**&#x200B;が&#x200B;*[!UICONTROL Allow Qty Below 0]*&#x200B;に設定されました。
1. 新しい&#x200B;**[!DNL custom stock]**&#x200B;と&#x200B;**[!DNL custom source]**&#x200B;を追加します。
1. 商品を&#x200B;**[!DNL custom source]**&#x200B;に割り当て、在庫番号が設定されていることを確認します（例：*10*）。
1. 製品編集ページで、**[!UICONTROL Advanced Inventory]**&#x200B;を開きます。 買い物かごに&#x200B;**[!UICONTROL minimum quantity]**&#x200B;を設定します（例：*160*）。 数量は在庫を超える必要があります。
1. ストアフロントに行き、製品を購入して予約を作成します。
1. **[!UICONTROL product quantity]**&#x200B;を&#x200B;*0*&#x200B;に変更します。 重要な点は、予約が発生したときに&#x200B;**[!DNL Admin panel]**&#x200B;から商品を保存することです。
1. ストアフロントで&#x200B;**[!UICONTROL product page]**&#x200B;を開き、商品をカートに追加してみてください。

<u>期待される結果</u>:

数量が&#x200B;*0*&#x200B;未満の取り寄せ注文は許可されているため、商品をカートに追加できます。

<u>実際の結果</u>:

その商品は在庫切れと表示されている。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
