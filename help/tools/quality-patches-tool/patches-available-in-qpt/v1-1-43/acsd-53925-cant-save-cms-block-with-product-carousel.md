---
title: 'ACSD-53925: [!UICONTROL Product Carousel]でCMS ブロックを保存できません'
description: 「catalog_product_price」のディメンションモードがweb サイトに設定されている場合、管理者がProduct Carouselを使用してCMS ブロックを保存できないAdobe Commerceの問題を修正するには、ACSD-53925 パッチを適用します。
feature: CMS, Page Builder, Price Indexer, Products
role: Admin, Developer
exl-id: f6d286ab-d904-4f08-8265-99632f74b88a
type: Troubleshooting
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---

# ACSD-53925: *[!UICONTROL Product Carousel]*&#x200B;でCMS ブロックを保存できません

ACSD-53925 パッチでは、`catalog_product_price`のディメンションモードがweb サイトに設定されている場合、管理者が&#x200B;*[!UICONTROL Product Carousel]*&#x200B;を含むCMS ブロックを保存できない問題を修正します。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.43がインストールされている場合に利用できます。 パッチ IDはACSD-53925です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p3

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

`catalog_product_price`のディメンション モードがweb サイトに設定されている場合、管理者は&#x200B;*[!UICONTROL Product Carousel]*&#x200B;のCMS ブロックを保存できません。

<u>複製する手順</u>:

1. シンプルな商品を2つ作成する：
   * simple1 - $10
   * simple2 - $20
1. シンプルな製品SKUに基づいて、2つのオプションを含むバンドル製品&#39;*bundle1-dyn*&#39;を作成します。
1. 製品価格インデクサーのディメンション モードを設定します。

   `bin/magento indexer:set-dimensions-mode catalog_product_price website`

1. **[!UICONTROL Content]** > **[!UICONTROL Blocks]**&#x200B;に移動し、新しいCMS ブロックを作成します。
1. [!DNL Page Builder]を使用してコンテンツを編集します：
   * *[!UICONTROL Row]*&#x200B;要素を追加
   * *[!UICONTROL Products]*&#x200B;要素を追加
   * *[!UICONTROL Product Carousel]*&#x200B;を選択
   * 製品SKUを入力 – *bundle1-dyn*
1. CMS ブロックを保存します。

<u>期待される結果</u>:

ユーザーはエラーなしで製品カルーセルを追加できます。

<u>実際の結果</u>:

* UIにメッセージがスローされました：*申し訳ありません。このコンテンツの生成中にエラーが発生しました*
* `var/log/exception.log`に次のエラーが含まれています：

  ```text
  [2023-08-18T20:58:14.533374+00:00] report.CRITICAL: PDOException: SQLSTATE[42S02]: Base table or view not found: 1146 Table 'username_dev.catalog_product_index_price_ws0' doesn't exist in /test/lib/internal/Magento/Framework/DB/Statement/Pdo/Mysql.php:90
  ```

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
