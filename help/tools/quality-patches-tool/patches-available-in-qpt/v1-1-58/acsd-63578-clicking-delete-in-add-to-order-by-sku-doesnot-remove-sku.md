---
title: 'ACSD-63578: [!UICONTROL Add to Order by SKU]の[!UICONTROL Delete] アイコンをクリックしても、SKUが削除されない'
description: 管理者で[!UICONTROL Add to Order by SKU]の[!UICONTROL Delete] アイコンをクリックしてもSKUが削除されないAdobe Commerceの問題を修正するには、ACSD-63578 パッチを適用します。
feature: Orders
role: Admin, Developer
exl-id: 12afceb5-db3c-4783-a532-93c4c71f05f4
type: Troubleshooting
source-git-commit: 4266dbeca837bc62e5a76b2ef22b065a3452e088
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 0%

---

# ACSD-63578: *[!UICONTROL Add to Order by SKU]*&#x200B;の&#x200B;**[!UICONTROL Delete]** アイコンをクリックしても、SKUが削除されない

ACSD-63578 パッチでは、管理画面で&#x200B;*[!UICONTROL Add to Order by SKU]*&#x200B;の&#x200B;**[!UICONTROL Delete]** アイコンをクリックしてもSKUが削除されない問題が修正されました。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58がインストールされている場合に利用できます。 パッチ IDはACSD-63578です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p7

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

管理画面の&#x200B;*[!UICONTROL Add to Order by SKU]*&#x200B;の&#x200B;**[!UICONTROL Delete]** アイコンをクリックしても、SKUが注文から削除されません。

<u>複製する手順</u>:

1. 管理者/**[!UICONTROL Sales]** / **[!UICONTROL Orders]**&#x200B;に移動し、**[!UICONTROL Create New Order]**&#x200B;をクリックします。
1. 顧客を選ぶ。
1. **[!UICONTROL Add to Order by SKU]**&#x200B;をクリックします。
   * SKUを入力します。
   * 「**[!UICONTROL Add another]**」ボタンをクリックします。
1. **[!UICONTROL Delete]** アイコンをクリックします。

<u>期待される結果</u>:

* 製品が追加され、管理者の注文から削除されます。

<u>実際の結果</u>:

* **[!UICONTROL Delete]** アイコンが機能しません。
* コンソールにエラーがあります：

  `jquery.js:130 Refused to execute inline script because it violates the following Content Security Policy directive`

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
