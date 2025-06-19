---
title: 'ACSD-47908: チェックアウト中に*0 以下の値が想定されます* エラー'
description: チェックアウト時に発送手順でソースと数量を選択する際に、Adobe Commerceエラー*0 以下の値が想定されます*を修正するために ACSD-47908 パッチを適用してください。
feature: Admin Workspace, Checkout, Orders
role: Admin
exl-id: f1429bd9-652d-43c0-af52-b2258e2a7643
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '472'
ht-degree: 0%

---

# ACSD-47908:*0 以下の値が想定されます* チェックアウト中にエラーが発生しました

チェックアウト時の出荷手順でソースと数量を選択する際に、ACSD-47908 パッチによってエラー *0 以下の値が想定される* が修正されます。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.27 がインストールされている場合に使用できます。 パッチ ID は ACSD-47908 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4-p2

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.7 ～ 2.4.6

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

チェックアウト中に出荷ステップでソースと数量を選択すると、次のエラーがスローされます。*0 以下の値が想定されます*。

<u> 前提条件 </u>:

Adobe Commerce Inventory management（MSI）モジュールをインストールします。

<u> 再現手順 </u>:

1. **[!UICONTROL Stores]**/**[!UICONTROL Inventory]**/**[!UICONTROL Sources]** に移動し、複数のソースを設定します。
1. **[!UICONTROL Stores]**/**[!UICONTROL Inventory]**/**[!UICONTROL Stock]** に移動し、新しい在庫を作成します。
   * 次に、ソースを新しい在庫に割り当てます。
1. **[!UICONTROL Catalog]**/**[!UICONTROL Products]** に移動し、少なくとも 1 つの製品を編集します。
   * 製品が新しいソースに割り当てられていることを確認し、使用可能な数量を指定します。
1. **[!UICONTROL Sales]**/**[!UICONTROL Orders]** に移動し、新しい注文を作成します。
1. その商品を注文に追加して配置します。
1. 「**[!UICONTROL Ship]**」をクリックします。
1. 出荷元のソースを選択します。
1. 出荷する各品目の数量を指定します。
1. ページをリロードします。
1. 「**[!UICONTROL Proceed to Shipment]**」をクリックします。

<u> 期待される結果 </u>:

新しい出荷ページがエラーなしで開きます。

<u> 実際の結果 </u>:

* 入力した数量は検証できません。
* 次のエラーがスローされます。*0 以下の値を入力してください*。

  ただし、このエラーは一貫性がなく、常に表示されるとは限りません。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md)[!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)」を参照してください。
