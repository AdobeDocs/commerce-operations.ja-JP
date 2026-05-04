---
title: ACSD-53750：マルチスレッド catalog_product_priceのインデックス再作成中に「壊れたパイプまたは閉じた接続」エラーが発生する
description: マルチスレッド catalog_product_priceの再インデックス中に*壊れたパイプまたは閉じた接続*エラーが発生するAdobe Commerceの問題を修正するには、ACSD-53750 パッチを適用します。
feature: Products
role: Admin, Developer
exl-id: 6c2f092f-a98e-4990-839c-a7291635f8af
type: Troubleshooting
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# ACSD-53750: マルチスレッド `catalog_product_price`の再インデックス中に&#x200B;*パイプが破損しているか、接続が閉じられているというエラー*&#x200B;が発生しました

ACSD-53750 パッチは、マルチスレッド `catalog_product_price`の再インデックス中に&#x200B;*パイプが破損しているか、接続が閉じられている*&#x200B;というエラーが発生する問題を修正します。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.37がインストールされている場合に利用できます。 パッチ IDはACSD-53750です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.6-p2

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

マルチスレッド `catalog_product_price`のインデックス再作成中に&#x200B;*パイプが破損しているか、接続が閉じられています* エラーが発生します。

<u>複製する手順</u>:

1. RabbitMqを設定します。
1. 添付された`small.xml` ファイルを使用してサンプルデータを生成します。
1. **[!UICONTROL Stores]** > **[!UICONTROL Config]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Inventory Indexer Setting]**&#x200B;に移動し、**[!UICONTROL Stock/Source reindex strategy]** = **[!UICONTROL Asynchronous]**&#x200B;と設定します。
1. それをサポートするインデックスのディメンションモードを設定します。 例：`catalog_product_price_website_and_customer_group`または`customer_group`

   ```shell
   bin/magento indexer:set-dimensions-mode catalog_product_price customer_group
   ```

1. `catalog_product_price`のインデクサーのリセットを実行します。

   ```shell
   bin/magento indexer:reset catalog_product_price
   ```

1. 複数のスレッドを使用して、リセットインデクサーのインデクサーを実行します。

   ```shell
   MAGE_INDEXER_THREADS_COUNT=10 bin/magento indexer:reindex catalog_product_price
   ```

<u>期待される結果</u>:

エラーは発生しません。

<u>実際の結果</u>:

次のエラーは、AMQP接続が原因で発生します。*パイプが破損しているか、接続が閉じられている*。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
