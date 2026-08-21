---
title: 'ACSD-61348: GraphQLを通じて表示されるウィッシュリスト項目が、ストアフロントには表示されない'
description: ACSD-61348 パッチを適用して、ウィッシュリスト項目がGraphQLを介して表示されますが、マルチサイト環境のストアフロントには表示されないAdobe Commerceの問題を修正します。
feature: Customers
role: Admin, Developer
exl-id: fcba2c28-077d-4663-b129-7da436e2791d
type: Troubleshooting
source-git-commit: 4266dbeca837bc62e5a76b2ef22b065a3452e088
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# ACSD-61348: GraphQLを通じて表示されるウィッシュリスト項目が、ストアフロントには表示されない

ACSD-61348 パッチでは、ウィッシュリスト項目がGraphQLを介して表示されますが、複数のweb サイト環境のストアフロントには表示されない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55がインストールされている場合に利用できます。 パッチ IDはACSD-61348です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p5

**Adobe Commerceのバージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

ウィッシュリストのアイテムは、GraphQLでは表示されますが、マルチサイト環境のストアフロントには表示されません。

<u>複製する手順</u>:

1. 2つのweb サイトを設定します。
1. **[!UICONTROL Config Customers]** > **[!UICONTROL Customer Configuration]** > **[!UICONTROL Account Sharing Options]**&#x200B;に移動し、**[!UICONTROL Share Customer Accounts]**&#x200B;を&#x200B;*[!UICONTROL Global]*&#x200B;に設定します。
1. **[!UICONTROL Config Customers]** > **[!UICONTROL Wishlist]** > **[!UICONTROL General Options]**&#x200B;に移動し、**[!UICONTROL Enable Multiple Wish Lists]**&#x200B;を&#x200B;*Yes*&#x200B;に設定します。
1. **[!UICONTROL Config General]** > **[!UICONTROL Web]**&#x200B;に移動し、**[!UICONTROL Add Store Code to URLs]**&#x200B;を&#x200B;*はい*&#x200B;に設定します。
1. シンプルな商品を作成し、2番目のweb サイトに割り当てる：
1. 顧客を作成してログインします。
1. ウィッシュリストに商品を追加する。
1. 商品をデフォルトのweb サイトに割り当てます。
1. 既定のWeb サイトの&#x200B;*[!UICONTROL Wishlist]* ページに移動します。

<u>期待される結果</u>:

その製品は希望者リストに載っている。

<u>実際の結果</u>:

ウィッシュリストに商品はありません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
