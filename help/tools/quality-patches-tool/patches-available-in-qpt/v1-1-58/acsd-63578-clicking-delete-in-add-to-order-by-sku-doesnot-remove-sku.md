---
title: ACSD-63578:[!UICONTROL Delete] で [!UICONTROL Add to Order by SKU] アイコンをクリックしても、SKU が削除されない
description: ACSD-63578 パッチを適用すると、管理者の [!UICONTROL Delete] の [!UICONTROL Add to Order by SKU] アイコンをクリックしても SKU が削除されないAdobe Commerceの問題が修正されます。
feature: Orders
role: Admin, Developer
exl-id: 12afceb5-db3c-4783-a532-93c4c71f05f4
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 0%

---

# ACSD-63578:**[!UICONTROL Delete]** で「*[!UICONTROL Add to Order by SKU]*」アイコンをクリックしても、SKU が削除されない

ACSD-63578 パッチでは、管理者の **[!UICONTROL Delete]** で *[!UICONTROL Add to Order by SKU]* アイコンをクリックしても SKU が削除されない問題が修正されています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58 がインストールされている場合に使用できます。 パッチ ID は ACSD-63578 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p7

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

管理画面で **[!UICONTROL Delete]** の「*[!UICONTROL Add to Order by SKU]*」アイコンをクリックしても、SKU は注文から削除されません。

<u> 再現手順 </u>:

1. 管理者/ **[!UICONTROL Sales]** / **[!UICONTROL Orders]** に移動し、「**[!UICONTROL Create New Order]**」をクリックします。
1. 顧客を選択します。
1. 「**[!UICONTROL Add to Order by SKU]**」をクリックします。
   * SKU を入力します。
   * **[!UICONTROL Add another]** ボタンをクリックします。
1. **[!UICONTROL Delete]** アイコンをクリックします。

<u> 期待される結果 </u>:

* 製品が追加されたり、管理者の注文から削除されたりする。

<u> 実際の結果 </u>:

* **[!UICONTROL Delete]** アイコンが機能しません。
* コンソールにエラーがあります：

  `jquery.js:130 Refused to execute inline script because it violates the following Content Security Policy directive`

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
