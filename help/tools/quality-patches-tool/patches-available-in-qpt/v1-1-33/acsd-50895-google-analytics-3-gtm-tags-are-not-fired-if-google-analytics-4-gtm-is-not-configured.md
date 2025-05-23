---
title: '「ACSD-50895: [!DNL Google Analytics] 3 GTM が設定されていない場合、GTM タグが実行され  [!DNL Google Analytics]  せん」'
description: ' [!DNL Google Analytics] 4 GTM が設定されていない場合、 [!DNL Google Analytics] 3 GTM タグが実行されないAdobe Commerceの問題を修正するために、ACSD-50895 パッチを適用します。'
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 0%

---

# ACSD-50895:[!DNL Google Analytics] 3 GTM が設定されていない場合、[!DNL Google Analytics] 4 GTM タグが実行されない

ACSD-50895 パッチは、[!DNL Google Analytics] 4 GTM が設定されていない場合に [!DNL Google Analytics] 3 GTM タグが起動されない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ja/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.33 がインストールされている場合に使用できます。 パッチ ID は ACSD-50895 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p1

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5 ～ 2.4.6-p1

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

[!DNL Google Analytics] 3 GTM が設定されていない場合、[!DNL Google Analytics] 4 GTM タグは実行されません。

<u> 再現手順 </u>:

1. 管理者ユーザーとしてログインします。
1. **Admin**/**Store**/**Configuration**/**Sales**/10&rbrace;Google API **/** Google Analytics **で、**&#x200B;[!DNL Google Analytics 3]&#x200B;**と&#x200B;**&#x200B;[!DNL Google Tag Manager]&#x200B;**を有効にします。**
1. **[!DNL Google Analytics 4]** と **[!DNL Google Tag Manager]** を有効にしないでください。
1. ストアフロントの商品ページを開きます。

<u> 期待される結果 </u>:

GTM タグは、**[!DNL Google Analytics]** 3 GTM のみが有効な場合に実行されます。

<u> 実際の結果 </u>:

**[!DNL Google Analytics]** 4 GTM が無効になっている場合、GTM タグは実行されません。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Sourceオンプレミス：[[!DNL Quality Patches Tool] > Usage](/help/tools/quality-patches-tool/usage.md) in the [!DNL Quality Patches Tool] guide.
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)」を参照してください。
