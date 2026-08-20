---
title: ACSD-49179：注文レポートに、異なるストアの誤った金額が表示される。
description: ACSD-49179 パッチを適用して、異なるストアの異なる通貨の場合に注文レポートに誤った金額が表示されるAdobe Commerceの問題を修正します。
feature: Admin Workspace, Orders
role: Admin
exl-id: b10653ef-c4b1-40df-8bfe-7da755db621b
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '519'
ht-degree: 4%

---

# ACSD-49179：注文レポートに異なるストアの誤った金額が表示される

ACSD-49179 パッチは、異なるストアの通貨が異なる場合に注文レポートに誤った金額が表示される問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.28がインストールされている場合に利用できます。 パッチ IDはACSD-49179です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3-p3

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2 - 2.4.6

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

異なる店舗の異なる通貨の場合、注文レポートに誤った金額が表示されます。

<u>複製する手順</u>:

1. **[!UICONTROL Stores]** > **[!UICONTROL Config]** > **[!UICONTROL Catalog]** > **[!UICONTROL Price]**&#x200B;に移動し、[!UICONTROL Catalog Price Scope] = [!UICONTROL Website]と設定します。
1. web サイト、ストア、ストアビューを追加作成する。
1. **[!UICONTROL Stores]** > **[!UICONTROL Config]** > **[!UICONTROL General]** > **[!UICONTROL Currency Setup]** > **[!UICONTROL Currency Options]**&#x200B;に移動して、次を設定します。
   * デフォルト設定：
     * 基本通貨：USD
     * デフォルトの表示通貨：USD
     * 通貨：EUR、USD、THB （タイバーツ）
   * メインサイト：
     * 基本通貨：EUR
     * デフォルト表示通貨：EUR
     * 使用可能な通貨：EUR
   * 追加の新しいWeb サイト：
     * 基本通貨：THB （タイバーツ）
     * デフォルトの表示通貨：THB （タイバーツ）
     * ご利用可能な通貨：THB （タイバーツ）
1. **[!UICONTROL Stores]** > **[!UICONTROL Currency]** > **[!UICONTROL Currency Rates]**&#x200B;に移動し、THBの空のコンバージョン率を設定します（レートを1.0000に設定）。
1. 商品を作成し、両方のweb サイトに割り当て、以前に作成した追加のweb サイトでこの商品を注文します。
1. 注文が&#x200B;*処理中*&#x200B;の状態（請求書）であることを確認してください。
1. バックエンドで、**[!UICONTROL Reports]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]**&#x200B;に移動します。
1. **[!UICONTROL Yellow]**&#x200B;の警告をクリックして、統計を更新します。
1. 以前に作成した追加のweb サイトでレポートの範囲を設定し、フィルターを次のように設定します。
   * [!UICONTROL Date Used]: [!UICONTROL Created]
   * [!UICONTROL Period]: [!UICONTROL Day]
   * [!UICONTROL From and To]: テスト注文が行われた日
   * [!UICONTROL Order Status]: [!UICONTROL Any]
   * [!UICONTROL Empty rows]: [!UICONTROL No]
   * [!UICONTROL Show Actual Values]: [!UICONTROL No]

<u>期待される結果</u>:

売上合計は、web サイトの通貨に変換された正しい金額を示します。

<u>実際の結果</u>:

合計はゼロです。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
