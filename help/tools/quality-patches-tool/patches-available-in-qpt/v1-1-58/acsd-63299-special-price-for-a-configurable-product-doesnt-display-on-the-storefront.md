---
title: ACSD-63299：設定可能な製品の特別価格がストアフロントに表示されない
description: ACSD-63299 パッチを適用して、特別価格属性が設定可能な商品の特別価格の表示に影響を与えなくなったAdobe Commerceの問題を修正します。
feature: Catalog Management
Role: Admin, Developer
exl-id: cd1775c5-783e-4ed5-a148-1dae0b7542f8
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 0%

---

# ACSD-63299：設定可能な製品の特別価格がストアフロントに表示されない

ACSD-63299 パッチは、特別価格属性が設定可能な製品の特別価格の表示に影響を与えなくなった問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58がインストールされている場合に利用できます。 パッチ IDはACSD-63299です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p8

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

[!DNL Adobe Commerce]で、特別価格属性の&#x200B;*製品リストで使用*&#x200B;の値を変更しても、設定可能な製品の特別価格の表示方法には影響しなくなりました。

<u>複製する手順</u>:

1. **[!UICONTROL Stores]** > *[!UICONTROL Attributes]* > **[!UICONTROL Products]**&#x200B;に移動します。
1. ***[!UICONTROL special_price]***&#x200B;属性を検索し、**[!UICONTROL Storefront Properties]**&#x200B;に移動します。
1. ***[!UICONTROL Used in Product Listing]***&#x200B;を***[!UICONTROL No]***に変更します。
1. 1人の子を持つ設定可能な製品を作成します。
   * 名前とSKU: テスト
   * 価格：159 ドル
   * 色に基づいてオプションを生成します。 新しいカラーを追加：青
   * 保存
1. 子製品を開き、次の手順に従います。
   * **[!UICONTROL Advanced Pricing]**&#x200B;の特別価格を$99.90に設定
   * [!UICONTROL Visibility]を&#x200B;**[!UICONTROL Catalog, Search]**&#x200B;に変更します。
1. シンプルな商品ページを開き、特別価格が表示されていることを確認します。
1. 設定可能な製品ページを開きます。
1. 青色の商品を選択します。

<u>期待される結果</u>:

シンプルな商品と同じように特別価格が表示されます。

<u>実際の結果</u>:

1. 設定可能な製品を選択すると、全額が表示されます。
1. セクション *の低い値（$99.90）と実際の価格（$99.90 + $59.10 = $159.00）の間に不一致があります。*

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
