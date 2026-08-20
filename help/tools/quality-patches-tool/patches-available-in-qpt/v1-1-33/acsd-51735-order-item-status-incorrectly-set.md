---
title: ACSD-51735：商品在庫が0の場合、注文品目のステータスが*[!UICONTROL Ordered]*に誤って設定される
description: ACSD-51735 パッチを適用して、商品在庫が0の場合に注文商品のステータスが*[!UICONTROL Ordered]*に誤って設定されるAdobe Commerceの問題を修正します。
feature: Orders, Products
role: Admin
exl-id: 56c8b58c-819f-46bd-8912-f543f56b66d6
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 0%

---

# ACSD-51735：商品在庫が0の場合、注文品目のステータスが&#x200B;*[!UICONTROL Ordered]*&#x200B;に誤って設定される

ACSD-51735 パッチは、製品在庫が0の場合に注文品目のステータスが&#x200B;*[!UICONTROL Ordered]*&#x200B;に誤って設定される問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.33がインストールされている場合に利用できます。 パッチ IDはACSD-50895です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.4-p4

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

商品の在庫が0の場合、注文品目のステータスが&#x200B;*[!UICONTROL Ordered]*&#x200B;に誤って設定されます。

<u>前提条件</u>:

* Adobe Commerce Inventory management（MSI）モジュールがインストールされます。
* バックオーダーは、**[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Product Stock Options]** > **[!UICONTROL Backorders]**&#x200B;で有効になっています。

<u>複製する手順</u>:

1. 新しいストックを作成します。
1. 新しいソースを作成します。
1. デフォルトのweb サイトを新しい在庫に割り当て、新しいソースを割り当てます。
1. 新製品を作成します。

   * デフォルトのソース数量を10に、新しいソース数量を0に設定します。

1. ストアフロントのカートに商品を追加します。
1. チェックアウト時に、製品が新しいソースから提供されていることを示すバックオーダー警告を確認します。
1. 注文する。
1. 管理画面で注文を開き、バックオーダーのステータスを確認します。

<u>期待される結果</u>:

このオーダーは、数量1がバックオーダーされていることを示します。

<u>実際の結果</u>:

このオーダーは、数量1が受注済であり、バックオーダーではないことを示しています。

>[!MORELIKETHIS]
>
>[注文項目のステータスが&#x200B;*[!UICONTROL Backordered]*](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-33/acsd-51408-order-item-status-is-set-to-backordered.md)に正しく設定されていません

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
