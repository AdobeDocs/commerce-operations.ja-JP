---
title: 'ACP2E-4050: [!UICONTROL Free Shipping]は複数配送チェックアウトで適用されません'
description: ACP2E-4050 パッチを適用して、[!UICONTROL Cart Price Rules]にサブセレクト条件と特定の価格の商品が含まれている場合、マルチアドレスチェックアウト中に[!UICONTROL Free Shipping]が適用されないAdobe Commerceの問題を修正します。
feature: Shopping Cart, Shipping/Delivery
role: Admin, Developer
type: Troubleshooting
exl-id: 447d2460-5c29-4849-81d0-a9aaf0a758b4
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# ACP2E-4050: **[!UICONTROL Free Shipping]**&#x200B;は複数配送チェックアウトで適用されません

ACP2E-4050 パッチは、**[!UICONTROL Cart Price Rules]**&#x200B;にサブセレクト条件と特定の価格の製品が含まれている場合、複数配送のチェックアウト中に&#x200B;**[!UICONTROL Free Shipping]**&#x200B;が適用されない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69がインストールされている場合に利用できます。 パッチ IDはACP2E-4050です。 この問題は、Adobe Commerce 2.4.9で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p10

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5 - 2.4.7-p6

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

**[!UICONTROL Cart Price Rules]**&#x200B;にサブセレクト条件と特定の価格の製品が含まれている場合、複数配送のチェックアウト中に&#x200B;**[!UICONTROL Free Shipping]**&#x200B;は適用されません。

<u>複製する手順</u>:

1. 2つのアドレスを持つ顧客アカウントを作成します。
1. **[!UICONTROL Free Shipping]**&#x200B;を有効にし、**[!UICONTROL Minimum Order Amount]**&#x200B;を&#x200B;*999999*&#x200B;に設定します。
1. [!UICONTROL Admin] > [!UICONTROL Marketing] > [!UICONTROL Cart Price Rules]に移動し、次の条件を使用してカート価格ルールを作成します。

```text
If ALL of these conditions are TRUE:
 * Subtotal is at least 50
 * The subtotal is at most 500
 * Apply this condition if the total amount is 50 or more for a subset of cart items that meet all specified criteria:
 * Category is 23
```

1. サンプルデータをインストールします。
1. 以下の商品を、指定した順序でカートに追加します。
   * Wayfarer Messenger バッグ
   * Olivia 1/4 ジップライトジャケット
   * スプライトヨガコンパニオンキット。
1. ショッピングカートを開き、**[!UICONTROL Free Shipping]** オプションが利用可能であることを確認します。
1. **[!UICONTROL Check Out with Multiple Addresses]**&#x200B;をクリックします。
1. シンプルな商品に別の配送先住所を選択します。
1. **[!UICONTROL Go to Shipping Information]**&#x200B;をクリックします。

<u>期待される結果</u>:

**[!UICONTROL Free Shipping]**&#x200B;は、設定可能な製品およびバンドル製品の出荷に適用されます。

<u>実際の結果</u>:

**[!UICONTROL Free Shipping]**&#x200B;は使用できません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
