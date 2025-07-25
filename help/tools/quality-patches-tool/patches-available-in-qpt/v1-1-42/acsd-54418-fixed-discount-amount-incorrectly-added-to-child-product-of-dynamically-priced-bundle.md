---
title: ACSD-54418：動的に価格設定されたバンドルの子製品に、誤って追加された固定割引額
description: ACSD-54418 パッチを適用すると、動的に価格が設定されるバンドルの各子製品に固定割引額が誤って適用されるAdobe Commerceの問題を修正できます。
feature: Shopping Cart
role: Admin, Developer
exl-id: f7b57361-9056-4eec-a393-dadb65aa595b
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# ACSD-54418：動的に価格設定されたバンドルの子製品に、誤って追加された固定割引額。

ACSD-54418 パッチでは、動的に価格設定されたバンドルの各子製品に固定割引額が誤って適用される問題が修正されています。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.42 がインストールされている場合に使用できます。 パッチ ID は ACSD-54418 です。 この問題はAdobe Commerce 2.4.7 で修正されていることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p1

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.0 ～ 2.4.6-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

固定割引額が、動的に価格設定されたバンドルの各子製品に誤って適用されます。

<u> 再現手順 </u>:

1. 動的な価格と *2* バンドルオプションを使用して **[!UICONTROL bundle product]** を作成します。
1. バンドルされた商品 **[!UICONTROL SKU]** ータにのみ適用され、固定割引がある特定のクーポンコードを持つ **[!UICONTROL cart price rule]** ールを作成します。
1. バンドルされた製品を買い物かごに追加します。
1. **[!UICONTROL coupon code]** を適用します。
1. 買い物かごに適用される割引を確認します。

<u> 期待される結果 </u>:

割引は、バンドルされた製品全体に 1 回だけ適用されます。

<u> 実際の結果 </u>:

割引は、各バンドル子製品に適用されます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)」を参照してください。
