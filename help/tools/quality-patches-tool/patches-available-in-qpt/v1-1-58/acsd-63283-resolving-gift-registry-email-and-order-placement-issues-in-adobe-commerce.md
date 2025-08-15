---
title: ACSD-63283:Adobe Commerce[!UICONTROL Gift Registry] 電子メールと注文の問題の解決
description: ACSD-63283 パッチを適用して、[!UICONTROL Gift Registry] からの項目の並べ替えによって例外が発生し、正しい項目のみが含まれ [!UICONTROL Gift Registry Updates] ようにするAdobe Commerceの問題を修正してください。
feature: Gift, Shopping Cart
role: Admin, Developer
exl-id: cff5b9e6-56ee-4df2-961a-6d90ec83c0c2
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# ACSD-63283:Adobe Commerce[!UICONTROL Gift Registry] 電子メールと注文の問題の解決

ACSD-63283 パッチは、[!UICONTROL Gift Registry] からの項目の並べ替えによって例外が発生し、正しい項目のみが含まれ [!UICONTROL Gift Registry Updates] ようにする問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58 がインストールされている場合に使用できます。 パッチ ID は ACSD-63283 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

>[!NOTE]
>このパッチは、[ACSD-56280](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-44/acsd-56280-gift-registry-purchases-are-not-completed) QPT パッチに取って代わり、拡張するものです。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p3

**Adobe Commerce バージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

Adobe Commerceの [!UICONTROL Gift Registry] の機能は、次の 2 つの重大な問題の影響を受けます。

* 顧客が [!UICONTROL Gift Registry] から品目を注文すると、例外がトリガーされてプロセスが失敗します。
* さらに、レジストリ所有者に送信される [!UICONTROL Gift Registry Updates] の電子メールには、更新される特定のレジストリ内の項目に更新を制限するのではなく、すべてのギフトレジストリの項目が誤って含まれます。

<u> 再現手順 </u>:

1. 製品 A と製品 B の 2 つの製品を作成します。
1. 顧客 A と顧客 B の 2 つの顧客を作成します。
1. 顧客 A としてログインし、新しい [!UICONTROL Gift Registry] を作成します。
1. 製品 A の製品ページに移動し、[!UICONTROL Wishlist] に追加します。 [!UICONTROL Wishlist Page] を開き、[!UICONTROL Gift Registry] を使用して製品 A を [!UICONTROL Add to Gift Registry] に移動します。
1. 顧客 B としてログインし、新しい [!UICONTROL Gift Registry] を作成して、製品 B を追加します。
1. 顧客 B として、[!UICONTROL Gift Registry]/**[!UICONTROL My Account]/[!UICONTROL Gift Registry] のメールで[!UICONTROL Share]** を共有します。
1. 顧客 B としてログアウトします。
1. メールに記載されているリンクをクリックします。 製品 B を [!UICONTROL Cart] に追加し、注文します。

<u> 期待される結果 </u>:

顧客 B は、更新された項目を含むメールをギフト登録時にのみ受け取ります。

<u> 実際の結果 </u>:

顧客 B は、すべてのギフトレジストリから項目付きのメールを受け取ります。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。


## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
