---
title: 'ACSD-65913: [!DNL OpenSearch] 同じ価格の製品を含むカテゴリに対してillegal_argument_exceptionをスローします'
description: ACSD-65913 パッチを適用して、 [!DNL Opensearch] が同じ価格のすべての商品を含むカテゴリに対してillegal_argument_exception （「[from] パラメーターを負にすることはできません」）をスローしているAdobe Commerceの問題を修正します。
feature: Search
role: Admin, Developer
type: Troubleshooting
exl-id: 984db32e-1a0d-4e0a-a83b-7fe909226ed3
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---

# ACSD-65913: [!DNL OpenSearch]が、同じ価格の製品を持つカテゴリに`illegal_argument_exception`をスローします

ACSD-65913 パッチは、[!DNL OpenSearch]が同じ価格の製品を含むカテゴリに`illegal_argument_exception`をスローした問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.66がインストールされている場合に利用できます。 パッチ IDはACSD-65913です。 この問題は、Adobe Commerce 2.4.9で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p5

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7 - 2.4.8

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

[!DNL OpenSearch]は、すべての製品が同じ価格を共有するカテゴリを読み込む際に、`illegal_argument_exception` （*[から] パラメーターを負にすることはできません*）をスローします。

<u>複製する手順</u>:

1. [!DNL OpenSearch] バージョン 2.19.1をインストールし、既定の検索エンジンとして設定します。
1. レイヤーナビゲーションに表示する&#x200B;**[!UICONTROL Price]**&#x200B;製品属性を設定します。
   1. **[!UICONTROL Visible in Advanced Search]**: *はい*
   1. **[!UICONTROL Comparable on Storefront]**: *はい*
   1. **[!UICONTROL Use in Layered Navigation]**: *フィルター可能（結果付き）*
1. **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog]** > **[!UICONTROL Layered Navigation]**&#x200B;に移動します。 **[!UICONTROL Price Navigation Step Calculation]**&#x200B;を&#x200B;*自動（製品数を等しくする）*&#x200B;に設定します。
1. 次の6つの商品をすべて同じ価格で扱うカテゴリを作成します。
   1. SKU: product_super_0-1-1-1、価格：$150
   1. SKU: product_super_0-1-1、価格：$48
   1. SKU: product_super_0-1、価格：$48
   1. SKU: product_super_0、価格：$48
   1. SKU: product_super_0-1-1-1-1-1-1-1-1-1-1-1-1-1-1価格：$48
   1. SKU: product_super_0-1-1-1-1-1-1-1-1-1-1、価格：$48
1. 次のコマンドを実行します。
   `bin/magento indexer:reindex`
1. カテゴリーページを開きます。 エラーが表示されます：
   *[from] パラメーターを負にすることはできません。[-1]*&#x200B;が見つかりました

<u>期待される結果</u>:

[!DNL OpenSearch]は、カテゴリ内のすべての製品が同じ価格を持っている場合、`illegal_argument_exception`をスローしないでください。

<u>実際の結果</u>:

* [!DNL OpenSearch]が次のメッセージで`illegal_argument_exception`をスローします：
  *[from] パラメーターを負にすることはできません。[-1]*&#x200B;が見つかりました

* `var/log/exception.log` ファイルには次が含まれています。

  ```text
  [2025-05-14T22:39:33.595272+00:00] report.CRITICAL: [!DNL OpenSearch]\Common\Exceptions\BadRequest400Exception: {"error":{"root_cause":[{"type":"illegal_argument_exception","reason":"[from] parameter cannot be negative, found [-1]"}],"type":"illegal_argument_exception","reason":"[from] parameter cannot be negative, found [-1]"},"status":400}
  ```

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
