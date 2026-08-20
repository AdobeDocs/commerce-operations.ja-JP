---
title: ACSD-66049：英語以外のストアフロントで、ICU ライブラリバージョンにより誤った価格が表示される
description: 古いPHP環境（バージョン 63.1から74.1）でICU ライブラリのバージョンが一致しないために、英語以外のストアフロントに誤った価格が表示されるAdobe Commerceの問題を修正するには、ACSD-66049 パッチを適用します。
feature: Products
role: Admin, Developer
type: Troubleshooting
exl-id: e667d462-87f6-4db5-bf3f-3213edac2f09
source-git-commit: 4266dbeca837bc62e5a76b2ef22b065a3452e088
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 0%

---

# ACSD-66049：英語以外のストアフロントで、ICU ライブラリバージョンにより誤った価格が表示される

ACSD-66049 パッチは、古いPHP環境（バージョン 63.1から74.1）でICU ライブラリバージョンが一致しないために、英語以外のストアフロントで誤った価格が表示される問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67がインストールされている場合に利用できます。 パッチ IDはACSD-66049です。 この問題は、Adobe Commerce 2.4.9で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p3

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方式） 2.4.5-p3 - 2.4.5-p13、2.4.7 - 2.4.8-p1

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

英語以外のストアフロントでは、古いバージョンのPHP ICU ライブラリ（63.1 ～ 74.1）を使用すると、誤った価格が表示されます。

<u>複製する手順</u>:

1. ICU バージョンを確認：
   * SSH経由でサーバーに接続し、コマンド `php -a`を実行します
   * プロンプトに次のように入力します。`echo INTL_ICU_VERSION;`
1. **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Locale]** > **[!UICONTROL Locale Options]**&#x200B;に移動します。**[!UICONTROL Configure Locale]** = *[!UICONTROL Hebrew (Israel)]*。
1. 価格= 100の商品を作成します。
1. ストアフロントで商品ページを表示します。

<u>期待される結果</u>:

表示された価格は0ではありません。

<u>実際の結果</u>:

100として簡単に表示された後、価格はすぐに0に更新されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
