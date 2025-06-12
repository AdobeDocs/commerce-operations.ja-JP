---
title: ACSD-55231：クイックオーダー機能の使用中に SKU が見つからないというエラーが発生する
description: ACSD-55231 パッチを適用すると、クイックオーダー機能を使用して買い物かごに商品を追加しようとすると、「The SKU was not found in the catalog」（SKU がカタログに見つかりませんでした）というエラーが発生するAdobe Commerceの問題を修正できます。
feature: Products, Checkout, B2B
role: Admin, Developer
exl-id: f0a04773-7395-4945-a72b-5a6a018bc94e
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '496'
ht-degree: 0%

---

# ACSD-55231：クイックオーダー機能の使用中に SKU が見つからないというエラーが発生する

ACSD-55231 パッチでは、クイックオーダー機能を使用して買い物かごに製品を追加しようとすると、「*カタログに SKU が見つかりませんでした* というエラーが発生する問題が修正されています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.44 がインストールされている場合に使用できます。 パッチ ID は ACSD-55231 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4-p3

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3 ～ 2.4.6-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

クイックオーダー機能 *使用して買い物かごに追加する製品を検索する際に、カタログ* エラーに「SKU が見つかりませんでした」が表示される。

<u> 再現手順 </u>:

1. B2B モジュールと共にAdobe Commerceをインストールします。
1. **[!UICONTROL Admin]**/**[!UICONTROL Stores]**/**[!UICONTROL Configuration]**/**[!UICONTROL B2B Features]** に移動し、以下を設定します。
   * **[!UICONTROL Enable company]**: *はい*
   * **[!UICONTROL Enable Shared Catalog]**: *はい*
   * **[!UICONTROL Enable Quick Order]**: *はい*
1. 上記の設定を保存します。
1. **[!UICONTROL Catalog]**/**[!UICONTROL Shared Catalogs]** に移動し、新しい共有カタログを作成します。
1. **[!UICONTROL Customers]**/**[!UICONTROL All Customers]** に移動し、新しい顧客を作成します。
   * グループ フィールドで、最近作成した共有カタログを選択し、*[!UICONTROL Allow remote shopping assistance]* を *はい* に設定します。
1. SKU *p12* を持つシンプルな製品を生成してカテゴリ *c1* に関連付け、「[!UICONTROL Product in Shared Catalog]」セクションで新しく作成した共有カタログを選択します。
1. 実行：

   ```
   bin/magento ind:rei 
   bin/magento c:f 
   bin/magento cron:run (multiple times)
   ```

1. 管理ページを更新します。
1. **[!UICONTROL Customers]**/**[!UICONTROL All Customers]** に移動し、以前に作成した顧客を編集します。
1. 「**[!UICONTROL Login as customer]**」をクリックします。
1. **[!UICONTROL Quick order]** に移動します。
1. *p12* SKU を検索し、**[!UICONTROL Product Suggestion]** をクリックします。
1. この商品を買い物かごに追加して注文します。
1. **[!UICONTROL Quick Order]** に戻り、SKU *p12* をもう一度検索し、「**[!UICONTROL Product Suggestion]**」をクリックします。

<u> 期待される結果 </u>:

クイックオーダー機能を使用して、商品を買い物かごに追加できます。

<u> 実際の結果 </u>:

クイックオーダー機能を使用して商品を買い物かごに追加できず、「*&#39;The SKU was not found in the catalog&#39;* error」が表示される（商品 SKU の検索中）。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md)[!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)」を参照してください。
