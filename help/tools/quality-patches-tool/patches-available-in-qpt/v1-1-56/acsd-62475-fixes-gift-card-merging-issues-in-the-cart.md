---
title: ACSD-62475：買い物かごでのギフトカードの結合の問題を修正しました
description: ACSD-62475 パッチを適用すると、詳細が異なるギフトカード商品が誤ってカート内の 1 行項目に結合されるAdobe Commerceの問題を修正できます。
feature: Shopping Cart, Quotes
role: Admin, Developer
exl-id: fc97c3c0-dc1b-4546-aad0-ef3b4b6a3415
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# ACSD-62475：買い物かごでのギフトカードの結合の問題を修正しました

ACSD-62475 パッチは、詳細が異なるギフトカード製品が誤ってカート内の 1 行項目に結合される問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56 がインストールされている場合に使用できます。 パッチ ID は ACSD-62475 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p1

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

一意の送信者または受信者の詳細を含むギフトカード製品が買い物かごに追加されると、誤って 1 行の項目に結合され、データの不一致が発生します。

<u> 再現手順 </u>:

1. 次の設定で [!UICONTROL Gift Card] 製品を作成します。
   * **[!UICONTROL Card Type]**: [!UICONTROL Virtual]
   * **[!UICONTROL Amount]**: 10

1. ストアフロントで新しいユーザーを作成し、ログインします。

1. 次の詳細を入力して、ギフトカード製品を買い物かごに追加します。
   * **[!UICONTROL Sender Name]**：送信者 1
   * **[!UICONTROL Sender Email**]: sender1@test.com
   * **[!UICONTROL Recipient Name**]：受信者 1
   * **[!UICONTROL Recipient Email**]: recipient1@test.com


1. ログアウト

1. 同じギフトカード製品を、次の詳細と共に買い物かごに追加します。
   * **[!UICONTROL Sender Name]**：送信者 2
   * **[!UICONTROL Sender Email**]: sender2@test.com
   * **[!UICONTROL Recipient Name**]：受信者 2
   * **[!UICONTROL Recipient Email**]: recipient2@test.com

1. 再度ログインし、カートを確認します。

<u> 期待される結果 </u>:

どちらのギフトカードも、それぞれの詳細を含む 2 つの異なる行項目として表示される必要があります。

<u> 実際の結果 </u>:

ギフトカードは、最初のギフトカードの詳細を保持して、数量が 2 の 1 つの行項目に結合されます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 &#x200B;](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [&#x200B; アップグレードとパッチ &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
