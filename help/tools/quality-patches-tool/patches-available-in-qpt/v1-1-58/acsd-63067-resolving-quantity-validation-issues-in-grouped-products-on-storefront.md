---
title: ACSD-63067：ストアフロントのグループ化製品での数量検証の問題の解決
description: ACSD-63067 パッチを適用すると、グループ化された商品のすべての商品数量が、1 つの商品の数量が正しくない場合に、誤って無効とハイライト表示されるAdobe Commerceの問題を修正できます。
feature: Storefront
role: Admin, Developer
source-git-commit: 7446f4d83932eedc6fa711ad09c6ee559d357f70
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 0%

---

# ACSD-63067：ストアフロントのグループ化製品での数量検証の問題の解決

ACSD-63067 パッチは、グループ化された製品の全製品数量が、1 つの製品の数量が正しくない場合に無効と誤って強調表示される問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58 がインストールされている場合に使用できます。 パッチ ID は ACSD-63067 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p2

**Adobe Commerce バージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

グループ化された製品で、サブ製品の 1 つに無効な数量があると、すべての数量が誤って無効としてハイライト表示されます。 さらに、無効な数量の製品だけでなく、すべての製品に対して検証メッセージが表示されます。

<u> 再現手順 </u>:

1. 少なくとも 2 つのシンプルな製品をオプションとする新しいグループ製品を作成します。
1. ストアフロントで商品を開きます。
1. いずれかのオプションに無効な数量（例：-1）を入力し、残りのオプションに有効な数量（例：1）を入力します。
1. 「**[!UICONTROL Add to Cart]**」をクリックします。

<u> 期待される結果 </u>:

無効な数量を持つ製品のみが無効としてハイライト表示されます。

<u> 実際の結果 </u>:

すべての商品数量が無効とハイライト表示され、メッセージが表示されます *商品の数量を指定してください。 は、すべての製品に対して表示され* す。


## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Sourceオンプレミス：[[!DNL Quality Patches Tool] > Usage](/help/tools/quality-patches-tool/usage.md) in the [!DNL Quality Patches Tool] guide.
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。


## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
