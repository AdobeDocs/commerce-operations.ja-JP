---
title: ACSD-45169：設定可能な製品の誤った在庫と価格がビジュアルマーチャンダイザーに表示される
description: ACSD-45169 パッチは、ステージング更新が適用された後、ビジュアルマーチャンダイザーに設定可能な製品の正しい在庫と価格が表示されない問題を修正しました。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.17 がインストールされている場合に利用できます。 パッチ ID は ACSD-45169 です。 この問題はAdobe Commerce 2.4.6 で修正される予定であることに注意してください。
feature: Categories, Configuration, Merchandising, Orders, Products
role: Admin
exl-id: 3f1218ee-2fd0-4f3e-80d7-7e6f9342e0fb
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 0%

---

# ACSD-45169：設定可能な製品の誤った在庫と価格がビジュアルマーチャンダイザーに表示される

ACSD-45169 パッチは、ステージング更新が適用された後、ビジュアルマーチャンダイザーに設定可能な製品の正しい在庫と価格が表示されない問題を修正しました。 このパッチは、[Quality Patches Tool （QPT） ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)1.1.17 がインストールされている場合に使用できます。 パッチ ID は ACSD-45169 です。 この問題はAdobe Commerce 2.4.6 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2-p2

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.1 ～ 2.4.4

>[!NOTE]
>
>パッチは、新しい Quality Patches Tool リリースを使用する他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

ステージング更新が適用された後、ビジュアルマーチャンダイザーに、設定可能な製品の正しい在庫と価格が表示されません。

<u> 再現手順 </u>:

1. シンプルな製品を作成します。
1. シンプルな製品のスケジュールされた更新を作成します（必要なのは、異なる行 ID とエンティティ ID だけです）。
1. 設定可能な商品を作成します。
1. 設定可能な製品をカテゴリに割り当てます。
1. カテゴリを開き、「ビジュアルマーチャンダイザー」セクションで設定可能な製品を確認します。

<u> 期待される結果 </u>:

ビジュアルマーチャンダイザーに正しい在庫と価格が表示されます。

<u> 実際の結果 </u>:

ビジュアルマーチャンダイザーで間違った在庫と価格が表示される。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md)[!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

品質向上パッチツールの詳細については、次を参照してください。

* [ 品質向上パッチツールがリリースされました：品質向上パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) がサポートナレッジベースに追加されました。
* [Quality Patches Tool を使用して、Adobe Commerceの問題に対するパッチが使用可能かどうかを確認します ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!DNL Quality Patches Tool] ガイド）。

QPT で使用可能なその他のパッチの詳細については、[[!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html): Search for patches[!DNL Quality Patches Tool]」を参照してください。
