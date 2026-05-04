---
title: ACSD-55231：クイック注文機能の使用中にSKUが見つかりませんエラーが発生する
description: クイック注文機能を使用して商品をカートに追加しようとすると、「カタログにSKUが見つかりません」というエラーが表示されるAdobe Commerceの問題を修正するには、ACSD-55231 パッチを適用します。
feature: Products, Checkout, B2B
role: Admin, Developer
exl-id: f0a04773-7395-4945-a72b-5a6a018bc94e
type: Troubleshooting
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '554'
ht-degree: 0%

---

# ACSD-55231：クイック注文機能の使用中にSKUが見つかりませんエラーが発生する

ACSD-55231 パッチは、クイック注文機能を使用して商品をカートに追加しようとすると、*&#39;商品がカタログ&#39;* エラーでSKUが見つからなかった」という問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.44がインストールされている場合に利用できます。 パッチ IDはACSD-55231です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4-p3

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3 - 2.4.6-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

クイック注文機能を使用してカートに追加する商品を検索する際に、*&#39;のSKUがカタログ&#39;* エラーで見つかりませんでした。

<u>複製する手順</u>:

1. B2B モジュールを搭載したAdobe Commerceの導入。
1. **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL B2B Features]**&#x200B;に移動して、次を設定します。
   * **[!UICONTROL Enable company]**: *はい*
   * **[!UICONTROL Enable Shared Catalog]**: *はい*
   * **[!UICONTROL Enable Quick Order]**: *はい*
1. 上記の設定を保存します。
1. **[!UICONTROL Catalog]** > **[!UICONTROL Shared Catalogs]**&#x200B;に移動し、新しい共有カタログを作成します。
1. **[!UICONTROL Customers]** > **[!UICONTROL All Customers]**&#x200B;に移動し、新しい顧客を作成します。
   * グループフィールドで、最近作成した共有カタログを選択し、*[!UICONTROL Allow remote shopping assistance]*&#x200B;を&#x200B;*Yes*&#x200B;に設定します。
1. SKU *p12*&#x200B;でシンプルな製品を生成し、カテゴリ *c1*&#x200B;に関連付け、新しく作成された共有カタログを[!UICONTROL Product in Shared Catalog] セクションで選択します。
1. 実行：

   ```shell
   bin/magento ind:rei 
   bin/magento c:f 
   bin/magento cron:run (multiple times)
   ```

1. 管理者ページを更新します。
1. **[!UICONTROL Customers]** > **[!UICONTROL All Customers]**&#x200B;に移動し、以前に作成した顧客を編集します。
1. **[!UICONTROL Login as customer]**&#x200B;をクリックします。
1. **[!UICONTROL Quick order]**&#x200B;に移動します。
1. *p12* SKUを検索し、**[!UICONTROL Product Suggestion]**&#x200B;をクリックします。
1. この商品をカートに入れて注文します。
1. **[!UICONTROL Quick Order]**&#x200B;に戻り、SKU *p12*&#x200B;をもう一度検索して、**[!UICONTROL Product Suggestion]**&#x200B;をクリックします。

<u>期待される結果</u>:

クイック注文機能を使用して、商品をカートに追加できます。

<u>実際の結果</u>:

クイック注文機能を使用して商品をカートに追加できず、商品SKUの検索時に「*カタログにSKUが見つかりません」エラーが表示されます。*

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
