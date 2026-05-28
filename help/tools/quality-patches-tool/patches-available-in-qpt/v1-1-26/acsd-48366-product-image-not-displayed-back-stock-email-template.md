---
title: 'ACSD-48366: [!UICONTROL Back to Stock]電子メールテンプレートに製品画像が表示されない'
description: ACSD-48366 パッチを適用して、商品のサムネイル画像が商品の在庫アラートメールに表示されないAdobe Commerceの問題を修正します。
feature: Admin Workspace, Communications, Orders, Products
role: Admin
exl-id: a721f399-f50a-4a13-9f5d-17ae7f3985f6
type: Troubleshooting
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 0%

---

# ACSD-48366: [!UICONTROL Back to Stock]電子メールテンプレートに製品画像が表示されない

ACSD-48366 パッチは、製品のサムネール画像が製品の在庫アラートメールに表示されない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.26がインストールされている場合に利用できます。 パッチ IDはACSD-48366です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.6

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

製品画像が[!UICONTROL Back to Stock]電子メールテンプレートに表示されません。

<u>複製する手順</u>:

1. **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Product Alert]** > **[!UICONTROL Allow Alert When Product Comes Back in Stock]** = *[!UICONTROL Yes]*&#x200B;に移動して、*[!UICONTROL Back in Stock]*&#x200B;の&#x200B;*[!UICONTROL Product Alert]*&#x200B;を有効にします。
1. *[!UICONTROL Display Out of Stock Products]*&#x200B;を有効にするには、**[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Display Out of Stock]** = *[!UICONTROL Yes]*&#x200B;に移動します。
1. qty = 0のシンプルな商品を作成します。
1. ストアフロントで顧客を作成し、上記の商品を購入すると、在庫状況に関するアラートが表示されます。
1. 商品を在庫にする：
1. 製品アラート cronを実行します。

   ```text
   n98-magerun2.phar sys:cron:run catalog_product_alert
   ```

1. 顧客に対する製品アラートを開始します。

   ```shell
   bin/magento queue:consumers:start product_alert
   ```

1. メールをチェック。 Stockのアラートメールがメールキャッチャーに表示されるようになりました。

<u>期待される結果</u>:

在庫通知メールに商品画像が表示されます。

<u>実際の結果</u>:

在庫通知メールでは商品画像を利用できません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
