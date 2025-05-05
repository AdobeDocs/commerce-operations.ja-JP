---
title: ACSD-64684:1,000 のコンマが原因で、999 を超える値のギフトカードを保存すると検証エラーが発生する
description: ACSD-64684 パッチを適用すると、「1,000」のコンマにより、999 を超える値のギフトカードを保存すると検証エラーが発生するAdobe Commerceの問題を修正できます。
feature: Catalog Management
role: Admin, Developer
source-git-commit: 58d385c0e3479f5f9d826dc6e892c8ec2ebfdbb5
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---


# ACSD-64684:1,000 のコンマが原因で、999 を超える値のギフトカードを保存すると検証エラーが発生する

ACSD-64684 パッチでは、「1,000」のコンマが原因で、999 を超える値のギフトカードを保存すると検証エラーが発生する問題を修正しました。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61 がインストールされている場合に使用できます。 パッチ ID は ACSD-64684 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p3

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

999 より大きい値を持つギフト カードを編集および保存すると、検証エラーが発生します。これは、「1,000」（1,000）などの数字のコンマ （桁区切り記号）が原因です。

<u> 再現手順 </u>:

1. ギフトカード製品を作成します。
   1. [!UICONTROL Amount] として 1,000 と入力します。
   1. 「**[!UICONTROL Save]**」をクリックします。

<u> 期待される結果 </u>:

* 金額が 1,000 の新しいギフトカードが保存されます。

<u> 実際の結果 </u>:

* ギフトカードの金額が 999 を超えると、検証エラーが発生します。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
