---
title: ACSD-59036：下限と上限の両方が$0に設定された製品価格を読み込むと、例外が発生する
description: ACSD-59036 パッチを適用して、下限と上限の両方を*$0*に設定した製品価格を読み込む際に例外が発生するAdobe Commerceの問題を修正します。
feature: Categories, Products, Storefront, Search
role: Admin, Developer
exl-id: a7d05108-0b03-4eb4-84ab-0dc5601530cb
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 0%

---

# ACSD-59036：下限と上限の両方が&#x200B;*$0*&#x200B;に設定された製品価格を読み込むと例外が発生する

ACSD-59036 パッチは、下限と上限の両方を&#x200B;*$0*&#x200B;に設定した製品価格を読み込む際に例外が発生する問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.50がインストールされている場合に利用できます。 パッチ IDはACSD-59036です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

Adobe Commerce（すべてのデプロイメント方法） 2.4.7

**Adobe Commerceのバージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方法） 2.4.7 - 2.4.7-p2

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

下限と上限の両方が&#x200B;*$0*&#x200B;に設定された製品価格を読み込むと、例外が発生します。

価格帯を含むクエリを読み込む際に、アルゴリズムがNULL値を考慮しないため、問題が発生しています。 これを修正するには、下位範囲と上位範囲の両方がNULLであるかどうかを確認し、それらがNULLである場合は、両方の制限に&#x200B;*0*&#x200B;の値を割り当てます。 これにより、エラーがスローされるのを防ぐ必要があります。

<u>複製する手順</u>:

1. *13*&#x200B;個のシンプルな商品を作成します。
1. すべての&#x200B;*13*&#x200B;製品をカテゴリに割り当てます。
1. 1つの商品の価格を&#x200B;*$1322.94*&#x200B;に設定します。
1. その他のすべての商品の価格を&#x200B;*$0*&#x200B;に設定します。
1. [!DNL OpenSearch]を検索エンジンとして設定します。
1. **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Storefront]**&#x200B;に移動し、**[!UICONTROL PLP]** カウントを&#x200B;*16*&#x200B;に設定します。
1. **[!UICONTROL Price Navigation Step Calculation]**&#x200B;を&#x200B;*自動（製品数を等しくする）*&#x200B;に設定します。
1. 完全なインデックス再作成を実行します。
1. *[!UICONTROL Category]* ページを開きます。

<u>期待される結果</u>:

*[!UICONTROL Category]* ページには、すべての製品が表示されます。

<u>実際の結果</u>:

エラーが発生します。

```JSON
report.CRITICAL: OpenSearch\Common\Exceptions\BadRequest400Exception: {"error":{"root_cause":[{"type":"x_content_parse_exception","reason":"[1:193] [bool] failed to parse field [must]"}],"type":"x_content_parse_exception","reason":"[1:193] [bool] failed to parse field [filter]","caused_by":{"type":"x_content_parse_exception","reason":"[1:193] [bool] failed to parse field [must]","caused_by":{"type":"illegal_argument_exception","reason":"field name is null or empty"}}},"status":400} in /vendor/opensearch-project/opensearch-php/src/OpenSearch/Connections/Connection.php:664
```

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
