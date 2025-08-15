---
title: ACSD-50367：顧客アドレスのエクスポートが複数選択属性で機能しない
description: 値のない複数選択**ーザーの顧客アドレス属性が作成された場合に、顧客アドレスの書き出しが機能しないAdobe Commerceの問題を修正するため**ACSD-50367 パッチを適用します。
feature: Admin Workspace, Attributes, Data Import/Export, Shipping/Delivery
role: Admin
exl-id: 3f33a590-e7c2-424e-aacd-2df7ab893c3e
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# ACSD-50367：顧客アドレスのエクスポートが機能しない

ACSD-50367 パッチでは、値のない複数選択 **`Customer Address`** 属性が作成された場合に、顧客アドレスの書き出しが機能しない問題が修正されています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.30 がインストールされている場合に使用できます。 パッチ ID は ACSD-50367 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p1

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.7 ～ 2.4.6

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

値のない複数選択 **`Customer Address`** 属性が作成される場合、顧客アドレスの書き出しが機能しません。

<u> 前提条件 </u>:

住所を持つ顧客を作成します。

<u> 再現手順 </u>:

1. **`Customer Address`** > **[!UICONTROL Admin]** > **[!UICONTROL Stores]** で複数選択 **[!UICONTROL Customer Addresses]** 属性を作成します。
1. **[!UICONTROL Admin]**/**[!UICONTROL System]**/**[!UICONTROL Export]** に移動し、エンティティタイプ **`Customer Address`** 選択します。
1. 顧客アドレスをエクスポートします。 何も書き出されていないことがわかります。
1. 複数選択 **`Customer Address`** 属性を削除し、顧客アドレスを再び書き出します。 今回は、アドレスの CSV ファイルが生成されます。

<u> 期待される結果 </u>:

顧客アドレスは、複数選択 **`Customer Address`** 属性の作成時に CSV ファイルとして書き出すことができます。

<u> 実際の結果 </u>:

複数選択の **`Customer Address`** 属性が作成されている場合、顧客アドレスを CSV ファイルとして書き出すことはできません。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[[!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja): Search for patches[!DNL Quality Patches Tool]」を参照してください。
