---
title: ACSD-49179：注文レポートに、様々な店舗に対して誤った金額が表示される。
description: ACSD-49179 パッチを適用すると、店舗ごとに異なる通貨が使用されている場合に注文レポートに誤った金額が表示されるAdobe Commerceの問題を修正できます。
feature: Admin Workspace, Orders
role: Admin
exl-id: b10653ef-c4b1-40df-8bfe-7da755db621b
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%

---

# ACSD-49179：注文レポートに、様々な店舗に対して誤った金額が表示される

ACSD-49179 パッチは、異なる店舗で異なる通貨が使用されている場合に、注文レポートに誤った金額が表示される問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.28 がインストールされている場合に使用できます。 パッチ ID は ACSD-49179 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3-p3

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2 ～ 2.4.6

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

注文レポートには、店舗ごとに異なる通貨の場合に誤った金額が表示されます。

<u> 再現手順 </u>:

1. **[!UICONTROL Stores]**/**[!UICONTROL Config]**/**[!UICONTROL Catalog]**/**[!UICONTROL Price]** に移動し、[!UICONTROL Catalog Price Scope]=[!UICONTROL Website] を設定します。
1. 追加の web サイト、ストア、ストア表示を作成します。
1. **[!UICONTROL Stores]**/**[!UICONTROL Config]**/**[!UICONTROL General]**/**[!UICONTROL Currency Setup]**/**[!UICONTROL Currency Options]** に移動し、次のように設定します。
   * デフォルトの設定：
      * 基準通貨：USD
      * 既定の表示通貨：USD
      * 使用可能な通貨：EUR、USD および THB （タイバーツ）
   * メインウェブサイト：
      * 基準通貨：EUR
      * デフォルト表示通貨：EUR
      * 使用可能な通貨：EUR
   * 追加の新しい Web サイト：
      * 基準通貨：THB （タイバーツ）
      * 既定の表示通貨：THB （タイ バーツ）
      * 使用可能な通貨：THB （タイバーツ）
1. **[!UICONTROL Stores]**/**[!UICONTROL Currency]**/**[!UICONTROL Currency Rates]** に移動して、THB の空のコンバージョン率を設定します（率を 1.0000 に設定します）。
1. 製品を作成して両方の web サイトに割り当て、以前に作成した追加の web サイトでこの製品を注文します。
1. 注文が *処理中* ステータスであることを確認します（請求書）。
1. バックエンドで、**[!UICONTROL Reports]** / **[!UICONTROL Sales]** / **[!UICONTROL Orders]** に移動します。
1. 統計を更新するには、**[!UICONTROL Yellow]** の警告をクリックします。
1. 作成済みの追加 web サイトでレポートの範囲を設定し、次のようにフィルターを設定します。
   * [!UICONTROL Date Used]: [!UICONTROL Created]
   * [!UICONTROL Period]: [!UICONTROL Day]
   * [!UICONTROL From and To]: テスト注文を行った同じ日
   * [!UICONTROL Order Status]: [!UICONTROL Any]
   * [!UICONTROL Empty rows]: [!UICONTROL No]
   * [!UICONTROL Show Actual Values]: [!UICONTROL No]

<u> 期待される結果 </u>:

売上高の合計は、Web サイトの通貨に変換された正しい金額を示します。

<u> 実際の結果 </u>:

合計はゼロです。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)」を参照してください。
