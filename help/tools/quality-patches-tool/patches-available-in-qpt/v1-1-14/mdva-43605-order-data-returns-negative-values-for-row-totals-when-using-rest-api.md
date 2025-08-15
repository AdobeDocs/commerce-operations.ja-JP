---
title: MDVA-43605:Rest API を使用している場合、注文データが行の合計に対して負の値を返す
description: MDVA-43605 パッチでは、Rest API を使用する際に、注文データが行の合計に対して負の値を返す問題が修正されています。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.14 がインストールされている場合に利用できます。 パッチ ID は MDVA-43605。 この問題はAdobe Commerce 2.4.5 で修正される予定であることに注意してください。
feature: REST, Orders
role: Admin
exl-id: f27439a6-eeee-4176-9ac9-98220752db3f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 0%

---

# MDVA-43605:Rest API を使用している場合、注文データが行の合計に対して負の値を返す

MDVA-43605 パッチでは、Rest API を使用する際に、注文データが行の合計に対して負の値を返す問題が修正されています。 このパッチは、[Quality Patches Tool （QPT） ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)1.1.14 がインストールされている場合に使用できます。 パッチ ID は MDVA-43605。 この問題はAdobe Commerce 2.4.5 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.1 ～ 2.4.4

>[!NOTE]
>
>パッチは、新しい Quality Patches Tool リリースを使用する他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

Rest API を使用する場合、注文データは行の合計に対して負の値を返します。

<u> 再現手順 </u>:

1. 送料無料を有効にします。
1. **Configuration**/**Catalog**/**Price** に移動し、「Catalog Price Scope = Website」と設定します。
1. **Configuration**/**Sales**/**Tax** に移動して、次の項目を更新します。
   * 出荷の税金区分=課税品
   * 計算設定：
      * カタログ価格=税込
      * 送料=込み価格
      * 価格に対する割引の適用=税込
   * 価格表示設定：税を含む（すべてのフィールド）
   * 買い物かごの表示設定：税を含む（すべてのフィールド）
   * 受注、請求書、クレジット・メモ：
      * 出荷金額の表示=税込
1. 米国の税率（都道府県= &#39;*&#39;）、税率= 24.00 を作成します。
1. 前述の税率で税務処理基準を作成します。
1. 特定のクーポンを使用して買い物かご価格ルールを作成します。割引額= $50 の固定金額を買い物かご全体に適用します。
1. 次の価格で 4 つの製品を作成します。8.90 ドル、5.90 ドル、6.90 ドル、および 5.95 ドル。
1. 前の手順で作成したクーポンコードを使用して、これらの 4 つの製品を含む管理注文を作成します。 送料無料をご利用ください。
1. クーポンコードは買い物かごの合計をカバーしているので、支払いは必要ありません。
1. Rest API エンドポイントを使用して作成された注文を取得します。

   ```json
   GET rest/V1/orders/1
   ```

<u> 期待される結果 </u>:

応答内の `base_row_total` と `base_row_total_incl_tax` の値はゼロです。

<u> 実際の結果 </u>:

応答内の `base_row_total` フィールドと `base_row_total_incl_tax` フィールドには負の値が指定されています。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

品質向上パッチツールの詳細については、次を参照してください。

* [ 品質向上パッチツールがリリースされました：品質向上パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) がサポートナレッジベースに追加されました。
* [Quality Patches Tool を使用して、Adobe Commerceの問題に対するパッチが使用可能かどうかを確認します ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!DNL Quality Patches Tool] ガイド）。

QPT で使用可能なその他のパッチの詳細については、[[!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html): Search for patches[!DNL Quality Patches Tool]」を参照してください。
