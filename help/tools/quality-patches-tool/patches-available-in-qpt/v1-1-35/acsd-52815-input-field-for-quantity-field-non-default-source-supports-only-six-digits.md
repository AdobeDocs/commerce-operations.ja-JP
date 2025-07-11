---
title: ACSD-52815：デフォルト以外のソースの数量フィールドの入力フィールドでサポートできる数字は、6 桁までです
description: ACSD-52815 パッチを適用すると、デフォルト以外のソースの数量フィールドの入力フィールドが、デフォルトの在庫の 8 桁とは異なり、最大 6 桁しかサポートしないAdobe Commerceのパフォーマンスの問題を修正できます。
feature: Inventory, Products
role: Admin
exl-id: d863af1f-8a7f-4a43-893e-54525ab68cd7
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# ACSD-52815：デフォルト以外のソースの数量フィールドの入力フィールドでサポートできる数字は、6 桁までです

ACSD-52815 パッチは、デフォルト以外のソースの数量フィールドの入力フィールドが、デフォルトの在庫の 8 桁とは異なり、最大 6 桁しかサポートしない問題を修正します。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.35 がインストールされている場合に使用できます。 パッチ ID は ACSD-52815 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p1

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

デフォルト以外のソースの数量フィールドの入力フィールドでは、デフォルトの在庫の 8 桁とは異なり、最大 6 桁までサポートできます。

<u> 再現手順 </u>:

1. 新しい在庫とソースを作成します。
1. 新しいソース在庫を 123 に設定して製品を作成します。
1. 販売可能数量（123）をチェックします。
1. ソース数量を 12345678 に更新します。
1. 販売可能数量を再確認します。

<u> 期待される結果 </u>:

販売可能数量は、正しい金額を示します。

<u> 実際の結果 </u>:

販売可能数量は 999999.9999 です。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)」を参照してください。
