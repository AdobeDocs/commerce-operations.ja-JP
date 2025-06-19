---
title: ACSD-58828：クライアントサイドの検証と共に、空の必須フィールドに対してサーバーサイドの「*アドレスが必要*」メッセージが表示される
description: ACSD-58828 パッチを適用すると、クライアントサイドの検証メッセージと共に、必須フィールドが空のままの場合、サーバーサイドの検証メッセージ「*address is required*」が表示されるAdobe Commerceの問題が修正されます。
feature: Shipping/Delivery, Checkout
role: Admin, Developer
exl-id: 6c19773d-cb75-409f-bbd7-78d285a0252a
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---

# ACSD-58828：クライアントサイドの検証と共に、サーバーサイド *address is required* メッセージが空の必須フィールドに表示される

ACSD-58828 パッチでは、クライアントサイドの検証メッセージと共に、必須フィールドが空のままの場合、サーバーサイドの検証メッセージ *address is required* が表示される問題が修正されています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55 がインストールされている場合に使用できます。 パッチ ID は ACSD-58828 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**
* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p2

**Adobe Commerce バージョンとの互換性：**
* Adobe Commerce（すべてのデプロイメント方法） 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

サーバーサイドの検証メッセージ *address is required* は、クライアントサイドの検証メッセージと共に、必須フィールドが空のままの場合に表示されます。

再現手順：

1. 顧客としてログインします。
1. 商品を買い物かごに追加します。
1. チェックアウトに進みます。
1. 配送先住所はそのままにしておきます。
1. **[!UICONTROL Flat rate]** を選択し、「**[!UICONTROL Next]**」を選択します。
1. 「**[!UICONTROL My billing and shipping address are the same]**」をオフにします。
1. ドロップダウンから新しいアドレスを追加します。
1. 必須フィールドは空のままにして、「**[!UICONTROL Update]**」を選択します。

期待される結果：

このエラーメッセージは、チェックアウトに必要な情報が見つからないか、正しくないことを示しています。

実際の結果：

エラー *アドレスが必要です。 を入力して、もう一度試してください。* が表示されます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
