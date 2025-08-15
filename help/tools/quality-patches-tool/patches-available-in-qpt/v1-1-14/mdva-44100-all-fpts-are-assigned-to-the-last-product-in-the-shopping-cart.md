---
title: MDVA-44100：すべての FPT が買い物かごの最後の製品に割り当てられる
description: MDVA-44100 パッチを適用すると、買い物かごの最後の製品にすべての FPT が割り当てられる問題が解決されます。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.14 がインストールされている場合に利用できます。 パッチ ID は MDVA-44100。 この問題はAdobe Commerce 2.4.5 で修正される予定であることに注意してください。
feature: Orders, Products, Shopping Cart
role: Admin
exl-id: b370dcbb-cbe9-4f5d-9b8f-1722ab521fcb
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# MDVA-44100：すべての FPT が買い物かごの最後の製品に割り当てられる

MDVA-44100 パッチを適用すると、買い物かごの最後の製品にすべての FPT が割り当てられる問題が解決されます。 このパッチは、[Quality Patches Tool （QPT） ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)1.1.14 がインストールされている場合に使用できます。 パッチ ID は MDVA-44100。 この問題はAdobe Commerce 2.4.5 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3-p1

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3 ～ 2.4.4

>[!NOTE]
>
>パッチは、新しい Quality Patches Tool リリースを使用する他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

すべての FPT が買い物かごの最後の製品に割り当てられ、残りの製品の FPT 値はリセットされます。

<u> 再現手順 </u>:

1. **Stores**/**Configuration**/**Sales**/**Tax** に移動し、次のように設定します。
   * FPT を有効にする= Yes
   * FPT への税金の適用= Yes
   * 小計に FPT を含める=はい
1. **ストア**/**属性**/**製品** に移動し、type = Fixed Product Tax という新しい属性を作成します。
1. 属性セットに属性を追加します。
1. 属性セットから 2 つの製品を作成し、国と州の FPT 属性を設定します。
1. 両方の品目を受注に追加します。
1. FPT の支払いが必要な住所を入力します。
1. 注文します。
1. 注文の品目リストを確認します。

<u> 期待される結果 </u>:

FPT は各製品の下に表示されます。

<u> 実際の結果 </u>:

両方の項目の FPT 値が 2 番目の項目の下に表示されます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

品質向上パッチツールの詳細については、次を参照してください。

* [ 品質向上パッチツールがリリースされました：品質向上パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) がサポートナレッジベースに追加されました。
* [Quality Patches Tool を使用して、Adobe Commerceの問題に対するパッチが使用可能かどうかを確認します ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!DNL Quality Patches Tool] ガイド）。

QPT で使用可能なその他のパッチの詳細については、[[!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html): Search for patches[!DNL Quality Patches Tool]」を参照してください。
