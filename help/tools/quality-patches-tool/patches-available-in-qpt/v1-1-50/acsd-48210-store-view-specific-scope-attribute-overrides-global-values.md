---
title: ACSD-48210：ストア表示固有のスコープ属性がグローバル値を上書きする
description: ACSD-48210 パッチを適用すると、特定のストアビューで*[!UICONTROL Website Scope]*属性を更新するとグローバルスコープの属性値が上書きされるというAdobe Commerceの問題が修正されます。
feature: Products, Attributes
role: Admin, Developer
exl-id: 944089c6-2f05-4c51-86ea-ede124bff80b
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 0%

---

# ACSD-48210：ストアビュー固有のスコープ属性がグローバル値を上書きする

ACSD-48210 パッチでは、特定のストア表示内の *[!UICONTROL Website Scope]* 属性を更新すると、グローバルスコープの属性値が上書きされる問題が修正されています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.50 がインストールされている場合に使用できます。 パッチ ID は ACSD-48210 です。 この問題はAdobe Commerce 2.4.7 で修正されました。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4-p2

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

特定のストア表示内の *[!UICONTROL Website Scope]* 属性を更新すると、グローバルスコープの属性値が上書きされます。

同じ `SKU` と `store_view_code` を共有する複数の行がある製品価格をインポートすると、*[!UICONTROL All Store View]* と *[!UICONTROL Default Store]* の範囲の価格が誤って更新されていました。 特定のストア表示で web サイト範囲属性を変更しても、グローバルスコープの属性の値が上書きされなくなりました。
<u> 再現手順 </u>:

1. *[!UICONTROL Website]* に *[!UICONTROL Catalog Price Scope]* を設定します。
1. *SP01* という名前のシンプルな製品を作成し、価格を *$84.50* に設定します。
1. 以下の CSV を使用して製品を読み込みます。

   ```
   sku,store_view_code,price
   SP01,default,99.99
   SP01,default,86.59
   ```

1. *[!UICONTROL All Store View]* と *[!UICONTROL Default Store]* の範囲で製品価格を確認してください。

<u> 期待される結果 </u>:

* 最初の空でない値が *[!UICONTROL Default Store]* スコープに使用されます。
* *[!UICONTROL All Store View]* 範囲は変更されません。

<u> 実際の結果 </u>:

* スコープ *[!UICONTROL All Store View]* 価格は 86.59 *ド* に変更される。
* スコープ *[!UICONTROL Default Store]* 価格は 86.59 *ド* に変更される。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)」を参照してください。
