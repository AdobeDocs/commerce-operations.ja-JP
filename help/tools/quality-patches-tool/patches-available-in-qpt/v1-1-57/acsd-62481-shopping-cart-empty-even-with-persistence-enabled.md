---
title: 'ACSD-62481: [!UICONTROL Persistence]が有効になっている場合でも、ショッピングカートが空のままになります'
description: チェックアウト時にログインポップアップを使用すると、永続的なカート機能が失敗するAdobe Commerceの問題を修正するには、ACSD-62481 パッチを適用します。
feature: Shopping Cart, Checkout
role: Admin, Developer
exl-id: 79fb3161-f56e-45f3-9933-cf95703f1554
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---

# ACSD-62481: *[!UICONTROL Persistence]*&#x200B;が有効になっている場合でも、ショッピングカートが空のままになります

ACSD-62481 パッチでは、チェックアウト時にログインポップアップを使用すると、*[!UICONTROL Remember Me]* チェックボックスがないため、ログアウト後に製品がカートから消えてしまう問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57がインストールされている場合に利用できます。 パッチ IDはACSD-62481です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

チェックアウト時にログインポップアップを使用すると、*[!UICONTROL Remember Me]* チェックボックスがないため、永続的なカート機能が失敗します。 これにより、ログアウト後に商品がカートから消えてしまいます。

<u>複製する手順</u>:

1. 管理画面で、次のようにゲストアカウントと永続的なカート設定を設定します。

   * **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Checkout]** > **[!UICONTROL Checkout Options]**&#x200B;に移動し、*[!UICONTROL Allow Guest Checkout]*&#x200B;を&#x200B;*No*&#x200B;に設定します。

     * **[!UICONTROL Save Config]**&#x200B;をクリックします。

   * **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Persistent Shopping Cart]** > **[!UICONTROL General Options]**&#x200B;に移動し、*[!UICONTROL Enable Persistence]*&#x200B;を&#x200B;*はい*&#x200B;に設定します。
   * 他のすべての設定をデフォルトのままにしますが、*[!UICONTROL Clear Persistence on Sign Out]*&#x200B;を&#x200B;*No*&#x200B;に変更します。

     * **[!UICONTROL Save Config]**&#x200B;をクリックします。

1. **[!UICONTROL Catalog]** > **[!UICONTROL Products]** > **[!UICONTROL Add product]**&#x200B;に移動して、シンプルな商品をカタログに追加します。

   * 必要な最低限の情報を入力し、在庫があることを確認します。

1. フロントエンドで、メインフォーム `(../customer/account/create/)`を使用して顧客アカウントを作成し、ログアウトします。
1. 商品をゲストとしてカートに追加します。
1. 右上のアイコンでミニカートを開き、**[!UICONTROL View and Edit Cart]**&#x200B;をクリックします。
1. チェックアウトに進みます。
1. 表示されるポップアップダイアログから新しい顧客アカウントにログインし、ログアウトします。

<u>期待される結果</u>:

カートには、以前ログインしたユーザーの商品が保持されます。

<u>実際の結果</u>:

* 買い物かごは空です。
* ポップアップログインダイアログに&#x200B;*[!UICONTROL Remember Me]* オプションが表示されません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* Adobe Commerce オンクラウドインフラストラクチャ：アップグレードとパッチ/パッチの適用については、Commerce オンクラウドインフラストラクチャガイドを参照してください。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
