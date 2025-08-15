---
title: MDVA-44533：バンドルされた子製品に誤って適用された割引
description: MDVA-44533 パッチは、バンドルされた子製品にディスカウントが誤って適用される問題を修正します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.15 がインストールされている場合に利用できます。 パッチ ID は MDVA-44533。 この問題はAdobe Commerce 2.4.5 で修正される予定であることに注意してください。
feature: Orders, Personalization, Products
role: Admin
exl-id: 150fe577-a61a-451e-838a-d60be7754bf4
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '470'
ht-degree: 0%

---

# MDVA-44533：バンドルされた子製品に誤って適用された割引

MDVA-44533 パッチは、バンドルされた子製品にディスカウントが誤って適用される問題を修正します。 このパッチは、[Quality Patches Tool （QPT） ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)1.1.15 がインストールされている場合に使用できます。 パッチ ID は MDVA-44533。 この問題はAdobe Commerce 2.4.5 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2-p2

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.1 ～ 2.4.3-p2

>[!NOTE]
>
>パッチは、新しい Quality Patches Tool リリースを使用する他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

バンドルされた子製品に誤って割引が適用される。

<u> 再現手順 </u>:

1. 50 ドルの価格でシンプルな製品を作成してください。
1. バンドルされた製品を作成し、バンドルされた製品の唯一のオプションとしてシンプルな製品を割り当てます。
1. 次を使用して買い物かご価格ルールを作成します。

   * 条件：合計金額が 130 ドルを超える場合
   * アクション：10 ドルの固定金額割引が適用されます

1. ストアフロントに移動し、バンドル製品を qty = 1 でカートに追加します。
1. カートに移動し、バンドル製品の合計コストが 50 ドルで、割引が適用されないことを確認します。
1. 数量を 2 に変更し、買い物かごを更新します。 バンドルされた製品の合計コストは 100 ドルになります。

<u> 期待される結果 </u>:

ルール条件の小計が 130\$未満の 100\$であるため、割引が適用されません。

<u> 実際の結果 </u>:

割引が適用されます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md)[!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

品質向上パッチツールの詳細については、次を参照してください。

* [ 品質向上パッチツールがリリースされました：品質向上パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) がサポートナレッジベースに追加されました。
* [Quality Patches Tool を使用して、Adobe Commerceの問題に対するパッチが使用可能かどうかを確認します ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!DNL Quality Patches Tool] ガイド）。

QPT で使用可能なその他のパッチの詳細については、[[!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html): Search for patches[!DNL Quality Patches Tool]」を参照してください。
