---
title: ACSD-63574：経由でブロックする [!UICONTROL Bundle Product] リストを追加すると  [!DNL Page Builder]  エラーが発生する
description: ACSD-63574 パッチを適用すると、Adobe Commerceの問題が修正されます。この問題では、「Checkbox」または「Multi Select」オプションを持つ**[!UICONTROL Bundle Product]**を  [!DNL Page Builder]  経由でブロックに追加するとエラーが発生します。
feature: Page Builder, Page Content
role: Admin, Developer
exl-id: bb56c0c2-e094-4173-8260-da154df79748
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 0%

---

# ACSD-63574:[!UICONTROL Bundle Product] を使用してブロックに [!DNL Page Builder] リストを追加すると、エラーが発生する

ACSD-63574 パッチは、**[!UICONTROL Bundle Product]** を使用して `Checkbox` オプションまたは `Multi Select` オプションの [!DNL Page Builder] をブロックに追加すると、エラーが発生する問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.59 がインストールされている場合に使用できます。 パッチ ID は ACSD-63574 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

Adobe Commerce（すべてのデプロイメント方法） 2.4.4-p10

**Adobe Commerce バージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.4-p11

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

**[!UICONTROL Bundle Product]** を使用してブロックに [!DNL Page Builder] を追加すると、製品ウィジェットのプレビューが壊れ、エラーメッセージ *このコンテンツの生成中にエラーが発生しました* が表示されます。 この問題は、バンドル製品に `Checkbox` または `Multi Select` のオプションタイプが含まれ、`indexer dimension mode` が `website_and_customer_group` に設定されている場合に特に発生します。 例外ログには、次のエラーが表示されます。

    ```
    report.CRITICAL: PDOException: SQLSTATE[42S02]：ベース テーブルまたはビューが見つかりません：1146 テーブル &#39;db_name.catalog_product_index_price_cg0_ws0&#39;が/home/vendor/magento/framework/DB/Statement/Pdo/Mysql.php:90
    ```に存在しません 

<u> 再現手順 </u>:

1. **[!UICONTROL Stores]**/*[!UICONTROL Settings]*/**[!UICONTROL Configuration]** に移動します。
1. 左側のパネルで「**[!UICONTROL Catalog]**」を展開し、以下のオプションから「**[!UICONTROL Catalog]**」を選択します。
1. **[!UICONTROL Price]** セクションまで下にスクロールし、**[!UICONTROL Catalog Price Scope]** を **[!UICONTROL Global]** に設定します。
1. 次のコマンドを使用して、`Indexer dimension mode` を `website_and_customer_group` に設定します。

   `bin/magento indexer:set-dimensions-mode catalog_product_price website_and_customer_group`

1. バンドルオプションタイプ **[!UICONTROL Bundle Product]** または `Checkbox` の `Multi Select` を作成し、製品をカテゴリに割り当てます。
1. **[!UICONTROL Content]**/**[!UICONTROL Blocks]**/**[!UICONTROL Edit Content with Page Builder]** に移動します。
1. 作成した商品が割り当てられているカテゴリを選択し、**[!UICONTROL Save]** 試行します。

<u> 期待される結果 </u>:

エラーのない製品が追加されました。

<u> 実際の結果 </u>:

[!DNL Page Builder] オプションの種類が **[!UICONTROL Bundle Product]** または `Checkbox` で、`Multi Select` が `indexer dimension mode` に設定されている場合、`website_and_customer_group` 経由で製品を追加できない。 次のエラーがスローされます。*申し訳ありません。このコンテンツの生成中にエラーが発生しました*。


## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。


## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
