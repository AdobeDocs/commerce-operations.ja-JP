---
title: ACSD-63067：ストアフロントでグループ化された製品の数量検証の問題を解決する
description: グループ化された製品内のすべての製品数量が、1つの製品のみに誤った数量がある場合に無効として誤って強調表示されるAdobe Commerceの問題を修正するには、ACSD-63067 パッチを適用します。
feature: Storefront
role: Admin, Developer
exl-id: a497f2c4-8bf0-41da-955a-a58e79f09c08
type: Troubleshooting
source-git-commit: 4266dbeca837bc62e5a76b2ef22b065a3452e088
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 0%

---

# ACSD-63067：ストアフロントでグループ化された製品の数量検証の問題を解決する

ACSD-63067 パッチでは、グループ化された製品内のすべての製品数量が、1つの製品のみに誤った数量がある場合に、誤って無効として強調表示される問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58がインストールされている場合に利用できます。 パッチ IDはACSD-63067です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p2

**Adobe Commerceのバージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

グループ化された製品では、いずれかのサブ製品の無効な数量によって、すべての数量が無効として誤って強調表示されます。 さらに、すべての製品に対して、無効な数量を持つ製品のみではなく、検証メッセージが表示されます。

<u>複製する手順</u>:

1. 少なくとも2つのシンプルな商品をオプションとして含む、新しいグループ化商品を作成します。
1. ストアフロントで商品を開きます。
1. いずれかのオプションに無効な数量（例：-1）を入力し、残りのオプションに有効な数量（例：1）を入力します。
1. **[!UICONTROL Add to Cart]**&#x200B;をクリックします。

<u>期待される結果</u>:

無効な数量を持つ製品のみが無効として強調表示されます。

<u>実際の結果</u>:

すべての製品数量が無効として強調表示され、メッセージ *製品の数量を指定してください。 は、すべての製品*&#x200B;に対して表示されます。


## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。


## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
