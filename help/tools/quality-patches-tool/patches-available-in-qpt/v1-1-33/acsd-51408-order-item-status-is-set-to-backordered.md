---
title: ACSD-51408：注文項目のステータスが誤って[!UICONTROL backordered]に設定されている
description: ACSD-51408 パッチを適用して、注文項目のステータスが[!UICONTROL backordered]に誤って設定されているAdobe Commerceの問題を修正します。
feature: B2B, Orders
role: Admin
exl-id: 51abb4c6-5618-43a5-89ca-a3879be2c3c4
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 0%

---

# ACSD-51408：注文項目のステータスが誤って&#x200B;*[!UICONTROL backordered]*&#x200B;に設定されている

ACSD-51408 パッチは、注文項目のステータスが誤って[!UICONTROL backordered]に設定される問題を修正します。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.33がインストールされている場合に利用できます。 パッチ IDはACSD-51408です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

注文項目のステータスが&#x200B;*[!UICONTROL backordered]*&#x200B;に正しく設定されていません。

<u>前提条件</u>:

Adobe Commerce B2BおよびInventory management（MSI）モジュールがインストールされます。

<u>複製する手順</u>:

1. 新しいweb サイト、ストア、ストアビューを作成する。
1. 新しいソースを作成します。
1. 手順1で作成した新しいweb サイトにリンクされた新しいストックを作成し、手順2で作成したソースを割り当てます。
1. 会社を作成し、手順1で作成した新しいweb サイトに割り当てます。
1. 新規顧客を作成し、手順4で作成した会社に割り当てます。
1. 製品を作成し、新しいweb サイトに割り当て、**[!UICONTROL default stock]** = *0*、および&#x200B;**[!UICONTROL new stock]**&#x200B;を&#x200B;*0*&#x200B;より大きく設定します。
1. **[!UICONTROL backorders]**&#x200B;を有効にします。
1. 新しいweb サイト スコープの&#x200B;**[!UICONTROL Check/Money Order]**&#x200B;支払い方法を有効にします。
1. 新しいweb サイト スコープの&#x200B;**[!UICONTROL Flat Rate shipping method]**&#x200B;を有効にします。
1. **[!UICONTROL Admin]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Create New Order]**&#x200B;から新しい注文を作成します。
1. 手順5で作成した新規顧客を選択します。
1. 手順1で作成した新しいストアを選択します。
1. 手順6で作成した製品を選択します。
1. 支払いや配送方法などの注文情報を入力します。
1. 注文を送信します。
1. *アイテムの状態*&#x200B;を確認してください。

<u>期待される結果</u>

商品は在庫から発送できます。 アイテムの状態は&#x200B;*[!UICONTROL ordered]*&#x200B;です。

<u>実際の結果</u>

アイテムの状態は&#x200B;*[!UICONTROL backordered]*&#x200B;です。

>[!MORELIKETHIS]
>
>製品在庫が0の場合、[注文品目のステータスが&#x200B;*[!UICONTROL Ordered]*&#x200B;に誤って設定される。](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-33/acsd-51735-order-item-status-incorrectly-set.md)

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) パッチを検索する」を参照してください。
