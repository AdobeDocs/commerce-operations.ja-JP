---
title: MDVA-43605:Rest APIを使用すると、注文データが行の合計に対して負の値を返す
description: MDVA-43605 パッチは、Rest APIを使用する際に注文データが行の合計に対して負の値を返す問題を修正します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.14がインストールされている場合に利用できます。 パッチ IDはMDVA-43605です。 この問題は、Adobe Commerce 2.4.5で修正される予定です。
feature: REST, Orders
role: Admin
exl-id: f27439a6-eeee-4176-9ac9-98220752db3f
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '568'
ht-degree: 0%

---

# MDVA-43605:Rest APIを使用すると、注文データが行の合計に対して負の値を返す

MDVA-43605 パッチは、Rest APIを使用する際に注文データが行の合計に対して負の値を返す問題を修正します。 このパッチは、[品質パッチツール（QPT） &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.14がインストールされている場合に使用できます。 パッチ IDはMDVA-43605です。 この問題は、Adobe Commerce 2.4.5で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.1 - 2.4.4

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

Rest APIを使用すると、注文データは行の合計に対して負の値を返します。

<u>複製する手順</u>:

1. 送料無料を有効にする。
1. **Configuration** > **Catalog** > **Price** >に移動し、Catalog Price Scope = Websiteを設定します。
1. **Configuration** > **Sales** > **Tax**&#x200B;に移動して、次の更新を行います。
   * 送料の税区分=課税商品
   * 計算設定：
     * カタログ価格=税込
     * 送料=価格を含む
     * 価格に割引を適用=税込み
   * 価格表示設定：税込み（すべてのフィールド）
   * 買い物かごの表示設定：税込（すべてのフィールド）
   * 注文、請求書、クレジットメモ：
     * 配送金額の表示=税込
1. 米国の税率を作成（州= &#39;*&#39;）、率パーセント = 24.00
1. 上記の税率を使用して税ルールを作成します。
1. 特定のクーポンでカート価格ルールを作成し、カート全体の固定額の割引= 50 ドルにします。
1. 価格が8.90 ドル、5.90 ドル、6.90 ドル、5.95 ドルの4つの商品を作成します。
1. 前の手順で作成したクーポンコードを使用して、これらの製品のうち4つを含む管理者注文を作成します。 送料無料を利用する：
1. クーポンコードはカートの合計をカバーするため、支払いは必要ありません。
1. Rest API エンドポイントを介して作成された順序を取得します。

   ```json
   GET rest/V1/orders/1
   ```

<u>期待される結果</u>:

応答の`base_row_total`と`base_row_total_incl_tax`の値は0です。

<u>実際の結果</u>:

応答の`base_row_total`および`base_row_total_incl_tax` フィールドには負の値があります。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [品質パッチツール &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) パッチを検索する」を参照してください。
