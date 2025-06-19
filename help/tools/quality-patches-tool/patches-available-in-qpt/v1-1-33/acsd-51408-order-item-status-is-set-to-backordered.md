---
title: ACSD-51408：注文項目のステータスが正しく [!UICONTROL backordered] に設定されていません
description: ACSD-51408 パッチを適用して、注文項目のステータスが誤って [!UICONTROL backordered] に設定されているAdobe Commerceの問題を修正してください。
feature: B2B, Orders
role: Admin
exl-id: 51abb4c6-5618-43a5-89ca-a3879be2c3c4
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 0%

---

# ACSD-51408：注文項目のステータスが正しく *[!UICONTROL backordered]* に設定されていません

ACSD-51408 パッチは、注文項目のステータスが誤って [!UICONTROL backordered] に設定されている問題を修正します。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.33 がインストールされている場合に使用できます。 パッチ ID は ACSD-51408 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

注文項目のステータスが正しく *[!UICONTROL backordered]* に設定されていません。

<u> 前提条件 </u>:

Adobe Commerce B2B およびInventory management（MSI）モジュールがインストールされている。

<u> 再現手順 </u>:

1. 新しい web サイト、ストア、ストア表示を作成します。
1. 新規ソースを作成します。
1. 手順 1 で作成した新しい web サイトにリンクした新しい在庫を作成し、手順 2 で作成したソースを割り当てます。
1. 会社を作成して、手順 1 で作成した新しい web サイトに割り当てます。
1. 新しい顧客を作成して、手順 4 で作成した会社に割り当てます。
1. 製品を作成して新しい web サイトに割り当て、**[!UICONTROL default stock]** = *0*、**[!UICONTROL new stock]** を *0* 以上に設定します。
1. **[!UICONTROL backorders]** を有効にします。
1. 新しい web サ **[!UICONTROL Check/Money Order]** ト範囲の支払い方法を有効にします。
1. 新しい web サイト範囲の **[!UICONTROL Flat Rate shipping method]** を有効にします。
1. **[!UICONTROL Admin]**/**[!UICONTROL Sales]**/**[!UICONTROL Orders]**/**[!UICONTROL Create New Order]** から新しい注文を作成します。
1. 手順 5 で作成した新しい顧客を選択します。
1. 手順 1 で作成した新規ストアを選択します。
1. 手順 6 で作成した製品を選択します。
1. 支払い方法や発送方法などの注文情報を入力します。
1. 注文を送信します。
1. *項目ステータス* を確認します。

<u> 期待される結果 </u>

品目を在庫から出荷できます。 項目のステータスが「*[!UICONTROL ordered]*」です。

<u> 実績 </u>

項目のステータスが「*[!UICONTROL backordered]*」です。

>[!MORELIKETHIS]
>
>[ 製品在庫が 0 の場合、注文項目のステータスが誤って *[!UICONTROL Ordered]* に設定される。](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-33/acsd-51735-order-item-status-incorrectly-set.md)

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md)[!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)」を参照してください。
