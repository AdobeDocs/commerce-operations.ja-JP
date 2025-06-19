---
title: ACSD-61348：ウィッシュリスト項目がGraphQL経由で表示されるが、ストアフロントでは表示されない
description: 複数の web サイト環境のストアフロントではなくGraphQL経由でウィッシュリストの項目が表示されるAdobe Commerceの問題を修正するために、ACSD-61348 パッチを適用してください。
feature: Customers
role: Admin, Developer
exl-id: fcba2c28-077d-4663-b129-7da436e2791d
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# ACSD-61348：ウィッシュリスト項目がGraphQL経由で表示されるが、ストアフロントでは表示されない

ACSD-61348 パッチは、複数の web サイト環境において、ウィッシュリストの項目がGraphQL経由で表示されてもストアフロントには表示されない問題を修正しました。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55 がインストールされている場合に使用できます。 パッチ ID は ACSD-61348 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p5

**Adobe Commerce バージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

ウィッシュリストの項目は、GraphQLを通じて表示されますが、複数の web サイトのストアフロントには表示されません。

<u> 再現手順 </u>:

1. 2 つの web サイトを設定します。
1. **[!UICONTROL Config Customers]**/**[!UICONTROL Customer Configuration]**/**[!UICONTROL Account Sharing Options]** に移動し、**[!UICONTROL Share Customer Accounts]** を *[!UICONTROL Global]* に設定します。
1. **[!UICONTROL Config Customers]**/**[!UICONTROL Wishlist]**/**[!UICONTROL General Options]** に移動し、「**[!UICONTROL Enable Multiple Wish Lists]**」を *はい* に設定します。
1. **[!UICONTROL Config General]**/**[!UICONTROL Web]** に移動し、「**[!UICONTROL Add Store Code to URLs]**」を *はい* に設定します。
1. シンプルな製品を作成して、2 番目の web サイトに割り当てます。
1. 顧客を作成し、ログインします。
1. ウィッシュリストに商品を追加します。
1. 製品をデフォルトの web サイトに割り当てます。
1. デフォルトの web サイトの *[!UICONTROL Wishlist]* ページに移動します。

<u> 期待される結果 </u>:

その商品はウィッシュリストに載っている。

<u> 実際の結果 </u>:

ウィッシュリストに商品がありません。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
