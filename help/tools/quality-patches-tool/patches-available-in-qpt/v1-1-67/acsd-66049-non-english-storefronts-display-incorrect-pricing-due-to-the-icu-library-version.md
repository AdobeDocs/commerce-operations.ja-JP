---
title: ACSD-66049：英語以外のストアフロントで、ICU ライブラリバージョンが原因で誤った価格が表示される
description: ACSD-66049 パッチを適用すると、古い PHP 環境（バージョン 63.1～74.1）で ICU ライブラリのバージョンが一致していないために、英語以外のストアフロントで誤った価格が表示されるAdobe Commerceの問題を修正できます。
feature: Products
role: Admin, Developer
type: Troubleshooting
source-git-commit: 39e0b972dfa41f74f3c19e61d8fc1188d5c93f7c
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 0%

---


# ACSD-66049：英語以外のストアフロントで、ICU ライブラリバージョンが原因で誤った価格が表示される

ACSD-66049 パッチは、古い PHP 環境（バージョン 63.1 から 74.1）における ICU ライブラリのバージョンの不一致により、英語以外のストアフロントで誤った価格が表示される問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67 がインストールされている場合に使用できます。 パッチ ID は ACSD-66049 です。 この問題はAdobe Commerce 2.4.9 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p3

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p3 - 2.4.5-p13、2.4.7 - 2.4.8-p1

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

英語以外のストアフロントでは、古い PHP ICU ライブラリバージョン （63.1 ～ 74.1）を使用すると誤った価格が表示されます。

<u> 再現手順 </u>:

1. ICU のバージョンを確認します。
   * SSH 経由でサーバーに接続し、コマンド `php -a` を実行します。
   * プロンプトで、`echo INTL_ICU_VERSION;` と入力します。
1. **[!UICONTROL Stores]**/**[!UICONTROL Configuration]**/**[!UICONTROL General]**/**[!UICONTROL Locale]**/**[!UICONTROL Locale Options]** に移動します。 **[!UICONTROL Configure Locale]** = *[UICONTOL ヘブライ語（イスラエル）]*.
1. 価格= 100 の製品を作成します。
1. ストアフロントの製品ページを表示します。

<u> 期待される結果 </u>:

表示価格が 0 ではありません。

<u> 実際の結果 </u>:

100 と表示された後、価格はすぐに 0 に更新されます。
（この問題は PHP ICU ライブラリバージョン 63.1 から 74.1 に影響します。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
