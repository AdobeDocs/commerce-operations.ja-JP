---
title: MDVA-44100：すべてのFPTがショッピングカート内の最後の製品に割り当てられます
description: MDVA-44100 パッチは、すべてのFPTがショッピングカート内の最後の製品に割り当てられる問題を解決します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.14がインストールされている場合に利用できます。 パッチ IDはMDVA-44100です。 この問題は、Adobe Commerce 2.4.5で修正される予定です。
feature: Orders, Products, Shopping Cart
role: Admin
exl-id: b370dcbb-cbe9-4f5d-9b8f-1722ab521fcb
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 0%

---

# MDVA-44100：すべてのFPTがショッピングカート内の最後の製品に割り当てられます

MDVA-44100 パッチは、すべてのFPTがショッピングカート内の最後の製品に割り当てられる問題を解決します。 このパッチは、[品質パッチツール（QPT） &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.14がインストールされている場合に使用できます。 パッチ IDはMDVA-44100です。 この問題は、Adobe Commerce 2.4.5で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3 - 2.4.4

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

すべてのFPTはショッピングカート内の最後の製品に割り当てられ、残りの製品のFPT値はリセットされます。

<u>複製する手順</u>:

1. **Stores** > **Configuration** > **Sales** > **Tax**&#x200B;に移動して、次の項目を設定します。
   * FPTを有効にする=はい
   * FPTに税金を適用=はい
   * 小計にFPTを含める= Yes
1. **ストア** > **属性** > **製品**&#x200B;に移動し、タイプ =固定製品税を持つ新しい属性を作成します。
1. 属性を属性セットに追加します。
1. 属性セットから2つの製品を作成し、国と州のFPT属性を設定します。
1. 両方の項目を注文に追加します。
1. FPTの支払いが必要なアドレスを入力してください。
1. 注文する。
1. 注文のアイテムリストを確認してください。

<u>期待される結果</u>:

FPTは各製品の下に表示されます。

<u>実際の結果</u>:

両方の項目のFPT値は、2番目の項目の下に表示されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [品質パッチツール &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
