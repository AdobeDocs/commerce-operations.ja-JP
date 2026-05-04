---
title: MDVA-40550：インデックス再作成後にフロントエンドで製品が見つからない
description: MDVA-40550 パッチは、インデックス再作成によって一部またはすべてのストアフロントカテゴリに製品が欠落する問題を解決します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.6がインストールされている場合に利用できます。 パッチ IDはMDVA-40550です。 この問題は、Adobe Commerce 2.4.4で修正される予定です。
feature: Categories, Console, Products
role: Admin
exl-id: 5ce7e341-e165-4668-9de7-8e9ca3a70c70
type: Troubleshooting
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '512'
ht-degree: 0%

---

# MDVA-40550：インデックス再作成後にフロントエンドで製品が見つからない

MDVA-40550 パッチは、インデックス再作成によって一部またはすべてのストアフロントカテゴリに製品が欠落する問題を解決します。 このパッチは、[品質パッチツール （QPT） &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.6がインストールされている場合に使用できます。 パッチ IDはMDVA-40550です。 この問題は、Adobe Commerce 2.4.4で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.5 - 2.4.3-p1

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

<u>複製する手順</u>:

1. 商品を作成する。
1. インデックスを&#x200B;**スケジュール別に更新**&#x200B;に切り替えます。
   * 製品をカテゴリに割り当てます。
1. `\Magento\Indexer\Model\Indexer::reindexAll`および`\Magento\Indexer\Model\IndexMutex::execute`でxdebugを有効にし、xdebug ブレークポイントを作成します。
1. 次のコマンドを使用して、`catalog_category_product`の&#x200B;**full reindex**&#x200B;を実行します。

   ```shell
   bin/magento indexer:reindex catalog_category_product
   ```

   * ブレークポイント `\Magento\Indexer\Model\Indexer::reindexAll`で実行が停止するのを待ちます。

1. 別のコンソールで、次のコマンドと並行して&#x200B;**部分インデックス**&#x200B;を実行します。

   ```shell
   bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1
   ```

1. ブレークポイント `\Magento\Indexer\Model\IndexMutex::execute`で実行が停止するのを待ちます。 `catalog_category_product` インデクサーがロックされます。
1. フル インデックス `catalog_category_product`の実行を再開し、ロック タイムアウト （60秒）を待ちます。

<u>期待される結果</u>:

コンソールにエラーメッセージが表示されない。

<u>実際の結果</u>:

次のエラーが表示されます。

*catalog_category_productのインデックスのロックを取得できませんでした。*

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [品質パッチツール &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
