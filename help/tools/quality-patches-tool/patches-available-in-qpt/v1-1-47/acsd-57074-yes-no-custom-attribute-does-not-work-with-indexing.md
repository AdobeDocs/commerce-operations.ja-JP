---
title: 「ACSD-57074:「attribute_code」属性のプレフィックス「price_*」を持つカスタム属性がインデックスで機能しない」
description: ACSD-57074 パッチを適用すると、「attribute_code」属性のプレフィックスが「price_*」のカスタム属性がインデックスで機能しないAdobe Commerceの問題を修正できます。
feature: Products, Categories, Catalog Management
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# ACSD-57074：属性に `price_*` のプレフィックスが付いたカスタム属性 *はい/いいえ* がインデックスで機能 `attribute_code` ない

ACSD-57074 パッチでは、`attribute_code` 属性に `price_*` のプレフィックスを持つ *はい/いいえ* カスタム属性がインデックスで機能しない問題を修正しました。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ja/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.47 がインストールされている場合に使用できます。 パッチ ID は ACSD-57074 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p3

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6 - 2.4.6-p4

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

`attribute_code` 属性に `price_*` のプレフィックスが付いた *はい/いいえ* カスタム属性は、インデックスで機能しません。

<u> 再現手順 </u>:

1. 次のオプションを持つカスタム製品属性を作成します。
   * *[!UICONTROL Catalog Input Type]*: *はい/いいえ*
   * *[!UICONTROL Scope]*: *StoreView*
   * *[!UICONTROL Use in Search]*: *はい*
1. 属性をデフォルトの属性セットに割り当てます。
1. 作成した属性で製品を作成します。
1. 作成した製品をカテゴリに割り当てます。
1. 完全な再インデックスを実行します。

<u> 期待される結果 </u>:

割り当てられたカテゴリに製品が表示されます。

<u> 実際の結果 </u>:

製品がカテゴリの前面ページに表示されない。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Sourceオンプレミス：[[!DNL Quality Patches Tool] > Usage](/help/tools/quality-patches-tool/usage.md) in the [!DNL Quality Patches Tool] guide.
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)」を参照してください。
