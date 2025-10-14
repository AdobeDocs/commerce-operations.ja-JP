---
title: MDVA-40550：インデックス再作成後にフロントエンドに製品が表示されない
description: MDVA-40550 パッチでは、インデックス再作成によって一部またはすべてのストアフロントカテゴリに製品が欠落する問題が解決されます。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.6 がインストールされている場合に利用できます。 パッチ ID は MDVA-40550。 この問題はAdobe Commerce 2.4.4 で修正される予定であることに注意してください。
feature: Categories, Console, Products
role: Admin
exl-id: 5ce7e341-e165-4668-9de7-8e9ca3a70c70
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# MDVA-40550：インデックス再作成後にフロントエンドに製品が表示されない

MDVA-40550 パッチでは、インデックス再作成によって一部またはすべてのストアフロントカテゴリに製品が欠落する問題が解決されます。 このパッチは、[Quality Patches Tool （QPT） &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)1.1.6 がインストールされている場合に使用できます。 パッチ ID は MDVA-40550。 この問題はAdobe Commerce 2.4.4 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2-p1

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.5 ～ 2.4.3-p1

>[!NOTE]
>
>パッチは、新しい Quality Patches Tool リリースを使用する他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

<u> 再現手順 </u>:

1. 商品を作成します。
1. インデクサーを **スケジュールに従って更新** に切り替えます。
   * 製品をカテゴリに割り当てます。
1. `\Magento\Indexer\Model\Indexer::reindexAll` と `\Magento\Indexer\Model\IndexMutex::execute` で xdebug を有効にし、xdebug ブレークポイントを設定します。
1. **の** full reindex`catalog_category_product` をコマンドを使用して実行します。

   ```bash
   bin/magento indexer:reindex catalog_category_product
   ```

   * ブレークポイント `\Magento\Indexer\Model\Indexer::reindexAll` で実行が停止するまで待ちます。

1. 別のコンソールで、次のコマンドと並行して **部分的な再インデックス** を実行します。

   ```bash
   bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1
   ```

1. ブレークポイント `\Magento\Indexer\Model\IndexMutex::execute` で実行が停止するまで待ちます。 `catalog_category_product` インデクサーがロックされます。
1. `catalog_category_product` の完全な再インデックスの実行を再開し、ロックタイムアウト（60 秒）待ちます。

<u> 期待される結果 </u>:

コンソールにエラーメッセージはありません。

<u> 実際の結果 </u>:

次のエラーが発生します。

*インデックス：catalog_category_product のロックを取得できませんでした*

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 &#x200B;](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [&#x200B; アップグレードとパッチ &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

品質向上パッチツールの詳細については、次を参照してください。

* [&#x200B; 品質向上パッチツールがリリースされました：品質向上パッチをセルフサービスで提供する新しいツール &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) がサポートナレッジベースに追加されました。
* [Quality Patches Tool を使用して、Adobe Commerceの問題に対するパッチが使用可能かどうかを確認します &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!DNL Quality Patches Tool] ガイド）。

QPT で使用可能なその他のパッチの詳細については、[[!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja): Search for patches[!DNL Quality Patches Tool]」を参照してください。
