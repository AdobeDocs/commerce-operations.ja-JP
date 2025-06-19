---
title: ACSD-63182：バンドル製品の複製後、製品の保存中にエラーが発生する
description: MSI を有効にしてバンドル製品を複製した後、製品の保存中にエラーが発生するAdobe Commerceの問題を修正するために、ACSD-63182 パッチを適用します。
feature: Inventory, Catalog Management
Role: Admin, Developer
exl-id: 2c664c89-e00e-40a8-9127-8c3f36c5bab9
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# ACSD-63182：バンドル製品の複製後、製品の保存中にエラーが発生する

ACSD-63182 パッチは、バンドルオプションとして使用された単純な製品をバンドル製品の複製後に保存できない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58 がインストールされている場合に使用できます。 パッチ ID は ACSD-63182 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p3

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

バンドル製品を複製した後、バンドルオプションとして使用した単純な製品を保存するとエラーが発生します。

<u> 再現手順 </u>:

1. 新しい MSI ソースとストックを作成します。
1. **p1** と **p2** の 2 つのシンプルな製品を作成します。
1. **p1** と **p2** をバンドルオプションとして使用して、バンドル製品 **b1** を作成します。
1. **バンドル製品 b1** を編集して、***[!UICONTROL Save and Duplicate]***&#x200B;をクリックします。
1. **シンプル製品 p1** を編集し、「**[!UICONTROL Save]**」をクリックします。

<u> 期待される結果 </u>:

製品はエラーなしで保存されます。

<u> 実際の結果 </u>:

次のエラーが表示されます。
*例外：同じ ID &#39;XXX&#39;の項目（Magento\Catalog\Model\Product\Interceptor）が既に存在します。*

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
