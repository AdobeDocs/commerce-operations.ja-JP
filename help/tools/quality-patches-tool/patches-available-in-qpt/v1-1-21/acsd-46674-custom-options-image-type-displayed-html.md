---
title: 「ACSD-46674：お客様のメールでHTMLとして表示される画像タイプのカスタムオプション」
description: ACSD-46674 パッチを適用すると、画像タイプのカスタムオプションが顧客のメールでHTMLとして表示されるAdobe Commerceの問題が修正されます。
feature: Communications, Personalization
role: Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-46674：お客様のメールにHTMLとして表示される画像タイプのカスタムオプション

ACSD-46674 パッチを使用すると、画像タイプのカスタムオプションが顧客のメールでHTMLとして表示される問題が修正されます。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.21 がインストールされている場合に使用できます。 パッチ ID は ACSD-46674 です。 この問題はAdobe Commerce 2.4.6 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2-p2

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.0 ～ 2.4.5-p1

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

画像タイプのカスタムオプションは、お客様へのメールでHTMLとして表示されます。

<u> 再現手順 </u>:

1. カスタムオプションを使用して製品を作成します。
   * オプションの種類：*ファイル*
   * 互換性のあるファイル拡張子：*png、jpg、gif*
   * 必須：*はい*
1. カスタムオプションとしてアップロードされた画像を使用して、この製品を注文します。
1. 手順 2 で作成した注文の請求書を作成します。
1. クレジットメモを作成します。
1. すべての確認メールを確認します。

<u> 期待される結果 </u>:

確認メールには、アップロードされた画像が表示されます。

<u> 実際の結果 </u>:

確認メールには、製品のカスタムオプション画像ではなく、プレーンなHTMLコードが含まれています。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Sourceオンプレミス：[[!DNL Quality Patches Tools] > Usage](/help/tools/quality-patches-tool/usage.md) in the [!DNL Quality Patches Tool] guide.
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


[!DNL QPT] で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)」を参照してください。
