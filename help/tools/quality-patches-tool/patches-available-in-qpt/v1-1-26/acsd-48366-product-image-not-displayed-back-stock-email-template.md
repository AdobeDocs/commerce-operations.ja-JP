---
title: ACSD-48366：メールテンプレートに製品画像 [!UICONTROL Back to Stock] 表示されない
description: ACSD-48366 パッチを適用すると、製品の在庫通知メールに製品のサムネール画像が表示されないAdobe Commerceの問題を修正できます。
feature: Admin Workspace, Communications, Orders, Products
role: Admin
exl-id: a721f399-f50a-4a13-9f5d-17ae7f3985f6
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# ACSD-48366：メールテンプレートに製品画像 [!UICONTROL Back to Stock] 表示されない

ACSD-48366 パッチは、製品の在庫通知メールに製品のサムネール画像が表示されない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.26 がインストールされている場合に使用できます。 パッチ ID は ACSD-48366 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.6

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

商品画像は [!UICONTROL Back to Stock] メールテンプレートには表示されません。

<u> 再現手順 </u>:

1. *[!UICONTROL Product Alert]*/*[!UICONTROL Back in Stock]*/**[!UICONTROL Store]**/**[!UICONTROL Configuration]**/**[!UICONTROL Catalog]**=**[!UICONTROL Product Alert]** に移動して、**[!UICONTROL Allow Alert When Product Comes Back in Stock]** の *[!UICONTROL Yes]* を有効にします。
1. *[!UICONTROL Display Out of Stock Products]*/**[!UICONTROL Store]**/**[!UICONTROL Configuration]**/**[!UICONTROL Catalog]**/**[!UICONTROL Inventory]**=**[!UICONTROL Display Out of Stock]** に移動して、*[!UICONTROL Yes]* を有効にします。
1. 数量= 0 の単純製品を作成します。
1. ストアフロントから顧客を作成し、上記の製品を購読して、在庫がある場合に製品アラートを取得します。
1. 商品を在庫にしてください。
1. 製品アラート cron を実行します。

   ```
   n98-magerun2.phar sys:cron:run catalog_product_alert
   ```

1. 顧客の製品アラートを開始します。

   ```
   bin/magento queue:consumers:start product_alert
   ```

1. メールを確認します。 在庫アラートメールがメールキャッチャーで使用できるようになりました。

<u> 期待される結果 </u>:

商品画像は、在庫アラートメールに表示されます。

<u> 実際の結果 </u>:

在庫通知メールに製品画像は表示されません。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 &#x200B;](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [&#x200B; アップグレードとパッチ &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [&#x200B; を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[[!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja): Search for patches[!DNL Quality Patches Tool]」を参照してください。
