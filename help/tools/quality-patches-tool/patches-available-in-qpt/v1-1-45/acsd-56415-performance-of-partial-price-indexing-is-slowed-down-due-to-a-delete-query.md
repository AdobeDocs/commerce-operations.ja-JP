---
title: 'ACSD-56415: ''DELETE'' クエリが原因で[!UICONTROL Partial Price Indexing]のパフォーマンスが低下しました'
description: ACSD-56415 パッチを適用して、Adobe Commerceに部分的な価格データが多くインデックスに含まれている場合、「DELETE」クエリが原因で[!UICONTROL Partial Price Indexing]のパフォーマンスが低下するデータベースの問題を修正します。
feature: Catalog Service
role: Admin, Developer
exl-id: c877844e-79d3-4756-97a5-de44e6fb5170
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# ACSD-56415: `DELETE` クエリが原因で[!UICONTROL Partial Price Indexing]のパフォーマンスが遅くなっています

ACSD-56415 パッチは、データベースに部分的な価格データインデックスが多い場合に`DELETE` クエリが原因で[!UICONTROL Partial Price Indexing]のパフォーマンスが低下する問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.45がインストールされている場合に利用できます。 パッチ IDはACSD-56023です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p3

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

データベースに部分的な価格データインデックスが多い場合、`DELETE` クエリが原因で、[!UICONTROL Partial Price Indexing]のパフォーマンスが低下します。

<u>複製する手順</u>:

1. 大きなパフォーマンスプロファイルを使用して&#x200B;*300000製品*&#x200B;と&#x200B;*10 web サイト*&#x200B;を作成します。
1. Admin Panelにログインします。
1. *10個の顧客グループ*&#x200B;を作成します。
1. 以下のクエリを実行して、製品を`_cl` テーブルに追加します。

   ``
    insert into catalog_product_price_cl (entity_id) select entity_id from catalog_product_entity
 ``

1. 次のコマンドを実行して、価格インデックス作成プロセスの一部をトリガーします。

   ``
    bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1
 ``

<u>期待される結果</u>:

`catalog_product_index_price`からのSQL クエリ DELETE `main_table`が迅速に実行されます。

<u>実際の結果</u>:

`catalog_product_index_price`からのSQL クエリ DELETE `main_table`の実行が非常に遅くなっています。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > Commerce クラウドインフラストラクチャ上のパッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」ガイド

## 関連トピックス

* [[!DNL Quality Patches Tool]  リリース：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを確認します
* [Commerce実装プレイブックのデータベーステーブルを修正するためのベストプラクティス ](/help/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables.md#why-adobe-recommends-avoiding-modifications)

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
