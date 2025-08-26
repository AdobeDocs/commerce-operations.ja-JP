---
title: ACP2E-4050：複数出荷チェックアウトでは適用されませ [!UICONTROL Free Shipping]
description: ACP2E-4050 パッチを適用すると、サブセレクトの条件や特定の価格の商品を含める場合に、複数アドレスのチェックアウト中に [!UICONTROL Free Shipping] が適用されないAdobe Commerceの問題 [!UICONTROL Cart Price Rules] 修正できます。
feature: Shopping Cart, Shipping/Delivery
role: Admin, Developer
type: Troubleshooting
source-git-commit: d36ce39fcd897261b784d57f8806b3eceb66fc01
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---


# ACP2E-4050：複数出荷チェックアウトでは適用されませ **[!UICONTROL Free Shipping]**

ACP2E-4050 パッチは、サブ選択の条件と特定の価格の製品を含める場合に、複数の配送チェックアウト中に **[!UICONTROL Free Shipping]** が適用され **[!UICONTROL Cart Price Rules]** い問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69 がインストールされている場合に使用できます。 パッチ ID は ACP2E-4050 です。 この問題はAdobe Commerce 2.4.9 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p10

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5 ～ 2.4.7-p6

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

サブ選択の条件や特定の価格の製品を含める場合、マルチシッピン **[!UICONTROL Free Shipping]** チェックアウト時に **[!UICONTROL Cart Price Rules]** は適用されません。

<u> 再現手順 </u>:

1. 2 つのアドレスで顧客アカウントを作成します。
1. **[!UICONTROL Free Shipping]** を有効にして、**[!UICONTROL Minimum Order Amount]** を *999999* に設定します。
1. [!UICONTROL Admin]/[!UICONTROL Marketing]/[!UICONTROL Cart Price Rules] に移動し、次の条件を持つ買い物かご価格ルールを作成します。

```
If ALL of these conditions are TRUE:
 * Subtotal is at least 50
 * The subtotal is at most 500
 * Apply this condition if the total amount is 50 or more for a subset of cart items that meet all specified criteria:
 * Category is 23
```

1. サンプルデータをインストールします。
1. 指定した順序で買い物かごに次の製品を追加します。
   * ウェイファーラーメッセンジャーバッグ
   * Olivia 1/4 Zip Light ジャケット
   * Sprite Yoga Companion Kit。
1. 買い物かごを開き、「**[!UICONTROL Free Shipping]**」オプションが使用可能であることを確認します。
1. 「**[!UICONTROL Check Out with Multiple Addresses]**」をクリックします。
1. シンプルな商品に対して別の配送先住所を選択します。
1. 「**[!UICONTROL Go to Shipping Information]**」をクリックします。

<u> 期待される結果 </u>:

**[!UICONTROL Free Shipping]** は、設定可能な製品およびバンドル製品の出荷に適用されます。

<u> 実際の結果 </u>:

**[!UICONTROL Free Shipping]** は利用できません。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md)[!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
