---
title: 'ACSD-63574:  [!DNL Page Builder] 経由でブロックする[!UICONTROL Bundle Product]件のリストを追加すると、エラーが発生する'
description: ACSD-63574 パッチを適用して、 [!DNL Page Builder] を介してブロックに「Checkbox」または「Multi Select」オプションで**[!UICONTROL Bundle Product]**を追加するとエラーが発生するAdobe Commerceの問題を修正します。
feature: Page Builder, Page Content
role: Admin, Developer
exl-id: bb56c0c2-e094-4173-8260-da154df79748
type: Troubleshooting
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---

# ACSD-63574: [!DNL Page Builder]経由でブロックする[!UICONTROL Bundle Product] リストを追加すると、エラーが発生する

ACSD-63574 パッチは、`Checkbox`または`Multi Select` オプションを含む&#x200B;**[!UICONTROL Bundle Product]**&#x200B;を[!DNL Page Builder]経由でブロックに追加するとエラーが発生する問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.59がインストールされている場合に利用できます。 パッチ IDはACSD-63574です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

Adobe Commerce（すべてのデプロイメント方法） 2.4.4-p10

**Adobe Commerceのバージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.4-p11

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

[!DNL Page Builder]を使用してブロックに&#x200B;**[!UICONTROL Bundle Product]**&#x200B;を追加すると、製品ウィジェットのプレビューが壊れ、エラーメッセージ *申し訳ありません。このコンテンツの生成中にエラーが発生しました*。 この問題は、バンドル製品に`Checkbox`または`Multi Select`個のオプションタイプが含まれ、`indexer dimension mode`が`website_and_customer_group`に設定されている場合に特に発生します。 例外ログには、次のエラーが表示されます。

    &quot;&#39;yaml
    report.CRITICAL: PDOException: SQLSTATE[42S02]：基本テーブルまたはビューが見つかりません：1146 テーブル &#39;db_name.catalog_product_index_price_cg0_ws0&#39;が/home/vendor/magento/framework/DB/Statement/Pdo/Mysql.php:90
    &quot;&#39;
に存在しません
<u>複製する手順</u>:

1. **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]**&#x200B;に移動します。
1. 左側のパネルで、**[!UICONTROL Catalog]**&#x200B;を展開し、以下のオプションから&#x200B;**[!UICONTROL Catalog]**&#x200B;を選択します。
1. **[!UICONTROL Price]** セクションまでスクロールして、**[!UICONTROL Catalog Price Scope]**&#x200B;を&#x200B;**[!UICONTROL Global]**&#x200B;に設定します。
1. 次のコマンドを使用して、`Indexer dimension mode`を`website_and_customer_group`に設定します。

   `bin/magento indexer:set-dimensions-mode catalog_product_price website_and_customer_group`

1. バンドルオプションタイプ `Checkbox`または`Multi Select`を含む&#x200B;**[!UICONTROL Bundle Product]**&#x200B;を作成し、製品をカテゴリに割り当てます。
1. **[!UICONTROL Content]** > **[!UICONTROL Blocks]** > **[!UICONTROL Edit Content with Page Builder]**&#x200B;に移動します。
1. 作成した製品が割り当てられているカテゴリを選択して、**[!UICONTROL Save]**&#x200B;を試してください。

<u>期待される結果</u>:

エラーなく製品が追加されました。

<u>実際の結果</u>:

**[!UICONTROL Bundle Product]** オプションの種類が`Checkbox`または`Multi Select`で、`indexer dimension mode`が`website_and_customer_group`に設定されている場合、[!DNL Page Builder]を通じて製品を追加できません。 エラーがスローされます：*申し訳ありません。このコンテンツの生成中にエラーが発生しました*。


## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。


## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
