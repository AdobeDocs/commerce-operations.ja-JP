---
title: ACSD-62952：ストアフロントにギフトレジストリの日付が正しく表示されない
description: ACSD-62952 パッチを適用すると、ストアフロントにギフトレジストリの日付が正しく表示されないAdobe Commerceの問題が修正されます。
feature: Gift, Storefront
role: Admin, Developer
exl-id: c11e95ab-775d-4aa7-828b-29ec52685d47
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 0%

---

# ACSD-62952：ストアフロントにギフトレジストリの日付が正しく表示されない

ACSD-62952 パッチにより、ギフトレジストリの日付がストアフロントに正しく表示されない問題が修正されました。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56 がインストールされている場合に使用できます。 パッチ ID は ACSD-62952 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p3

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

共有ギフトレジストリのストアフロントに表示されるイベントの日付が、実際の日付よりも 1 日早く誤って表示されます。

<u> 再現手順 </u>:

1. フロントエンドに顧客としてログインします。
1. [!UICONTROL My Account] ダッシュボードで、「**[!UICONTROL Gift Registry]**」をクリックします。
1. 既存のレジストリがない場合は、レジストリを作成し、任意の日付を指定します。
1. カートに商品を追加します。
1. 買い物かごページで、「**[!UICONTROL Add all items to Gift Registry]**」をクリックします。
1. ギフト レジストリを共有します。

<u> 期待される結果 </u>:

ギフト レジストリには、正しいイベントの日付が表示されます。

<u> 実際の結果 </u>:

招待メールから開かれたギフトレジストリには、イベントの日付が 1 日前と表示されます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 &#x200B;](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* Adobe Commerce on Cloud Infrastructure: アップグレードとパッチ > Commerce on Cloud Infrastructure ガイドのパッチの適用

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
