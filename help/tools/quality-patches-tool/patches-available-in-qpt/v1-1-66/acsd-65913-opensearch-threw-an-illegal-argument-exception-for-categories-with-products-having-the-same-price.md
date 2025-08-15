---
title: 'ACSD-65913: [!DNL OpenSearch]  同じ価格の製品を含むカテゴリに対して illegal_argument_exception をスローする'
description: ACSD-65913 パッチを適用すると、が同じ価格のすべての商品を含むカテゴリに  [!DNL Opensearch] illegal_argument_exception （「[from] パラメーターを負にすることはできません」）をスローするAdobe Commerceの問題が修正されます。
feature: Search
role: Admin, Developer
type: Troubleshooting
exl-id: 984db32e-1a0d-4e0a-a83b-7fe909226ed3
source-git-commit: e24b62305ef97c5fff13582b4bb68f622dffb6d3
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# ACSD-65913:[!DNL OpenSearch] が同じ価格の製品を含むカテゴリに対して `illegal_argument_exception` をスロー

ACSD-65913 パッチは、同じ価格の製品を含むカテゴリに対して [!DNL OpenSearch] が `illegal_argument_exception` を投げた問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.66 がインストールされている場合に使用できます。 パッチ ID は ACSD-65913 です。 この問題はAdobe Commerce 2.4.9 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p5

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7 ～ 2.4.8

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

すべての製品が同じ価格を共有するカテゴリを読み込むと、[!DNL OpenSearch] は `illegal_argument_exception` ール （*[from] パラメーターは負にできません*）をスローします。

<u> 再現手順 </u>:

1. [!DNL OpenSearch] バージョン 2.19.1 をインストールし、デフォルトの検索エンジンとして設定します。
1. レイヤナビゲーションに表示されるように **[!UICONTROL Price]** 製品属性を設定します。
   1. **[!UICONTROL Visible in Advanced Search]**: *はい*
   1. **[!UICONTROL Comparable on Storefront]**: *はい*
   1. **[!UICONTROL Use in Layered Navigation]**: *フィルタリング可能（結果を含む）*
1. **[!UICONTROL Stores]**/**[!UICONTROL Configuration]**/**[!UICONTROL Catalog]**/**[!UICONTROL Catalog]**/**[!UICONTROL Layered Navigation]** に移動します。 **[!UICONTROL Price Navigation Step Calculation]** を *自動（製品数を平均化）* に設定します。
1. すべて同じ価格の 6 つの製品でカテゴリを作成します。
   1. SKU: product_super_0-1-1-1、価格：$150
   1. SKU: product_super_0-1-1、価格：$48
   1. SKU: product_super_0-1、価格：$48
   1. SKU: product_super_0、価格：$48
   1. SKU: product_super_0-1-1-1-1-1-1-1-1-1-1-1-1-1-1-1-1-1-1、価格：$48
   1. SKU: product_super_0-1-1-1-1-1-1-1-1-1-1-1、価格：$48
1. 次のコマンドを実行します。
   `bin/magento indexer:reindex`
1. カテゴリページを開きます。 次のエラーが表示されます。
   *[from] パラメーターは負の値にできません。[-1 が見つかりました]*

<u> 期待される結果 </u>:

カテゴリ内のすべての製品が同じ価格の [!DNL OpenSearch] 合は、`illegal_argument_exception` をスローしないでください。

<u> 実際の結果 </u>:

* [!DNL OpenSearch] は次のメッセージを含む `illegal_argument_exception` をスローします。
  *[from] パラメーターは負の値にできません。[-1 が見つかりました]*

* `var/log/exception.log` ファイルには、次の内容が含まれます。

  ```
  [2025-05-14T22:39:33.595272+00:00] report.CRITICAL: [!DNL OpenSearch]\Common\Exceptions\BadRequest400Exception: {"error":{"root_cause":[{"type":"illegal_argument_exception","reason":"[from] parameter cannot be negative, found [-1]"}],"type":"illegal_argument_exception","reason":"[from] parameter cannot be negative, found [-1]"},"status":400}
  ```

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
