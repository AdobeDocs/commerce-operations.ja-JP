---
title: 'ACSD-63283: Adobe Commerceで[!UICONTROL Gift Registry]件の電子メールと注文プレースメントの問題を解決しています'
description: ACSD-63283 パッチを適用して、[!UICONTROL Gift Registry]から商品を注文すると例外が発生し、[!UICONTROL Gift Registry Updates]に正しい商品のみが含まれるようにするAdobe Commerceの問題を修正します。
feature: Gift, Shopping Cart
role: Admin, Developer
exl-id: cff5b9e6-56ee-4df2-961a-6d90ec83c0c2
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---

# ACSD-63283: Adobe Commerceで[!UICONTROL Gift Registry]件の電子メールと注文プレースメントの問題を解決しています

ACSD-63283 パッチでは、[!UICONTROL Gift Registry]から項目を注文すると例外が発生し、[!UICONTROL Gift Registry Updates]に正しい項目のみが含まれるという問題が修正されます。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58がインストールされている場合に利用できます。 パッチ IDはACSD-63283です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

>[!NOTE]
>このパッチは、[ACSD-56280](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-44/acsd-56280-gift-registry-purchases-are-not-completed) QPT パッチに置き換わり、拡張されます。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p3

**Adobe Commerceのバージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

Adobe Commerceの[!UICONTROL Gift Registry]機能には、次の2つの重要な問題が影響します。

* お客様が[!UICONTROL Gift Registry]からのアイテムを注文すると、例外がトリガーされたため、プロセスが失敗します。
* さらに、レジストリ所有者に送信された[!UICONTROL Gift Registry Updates]電子メールには、更新される特定のレジストリ内の項目に対する更新を制限するのではなく、すべてのギフトレジストリの項目が誤って含まれています。

<u>複製する手順</u>:

1. 商品Aと商品Bの2つの商品を作成します。
1. 顧客Aと顧客Bの2つの顧客を作成します。
1. 顧客Aとしてログインし、新しい[!UICONTROL Gift Registry]を作成します。
1. 製品Aの製品ページに移動し、[!UICONTROL Wishlist]に追加します。 [!UICONTROL Wishlist Page]を開き、[!UICONTROL Add to Gift Registry]を使用して製品Aを[!UICONTROL Gift Registry]に移動します。
1. 顧客Bとしてログインし、新しい[!UICONTROL Gift Registry]を作成し、製品Bを追加します。
1. 顧客Bとして、電子メールで[!UICONTROL Gift Registry]を共有します：**[!UICONTROL My Account]> [!UICONTROL Gift Registry] >[!UICONTROL Share]**。
1. 顧客Bとしてログアウトします。
1. メールで受信したリンクをクリックします。 商品Bを[!UICONTROL Cart]に追加して注文します。

<u>期待される結果</u>:

顧客Bは、ギフトレジストリからのみ、更新されたアイテムを含むメールを受け取ります。

<u>実際の結果</u>:

顧客Bは、すべてのギフトレジストリからのアイテムを含むメールを受信します。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)」（Commerce クラウドインフラストラクチャガイド）。


## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
