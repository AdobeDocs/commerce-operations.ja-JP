---
title: 'ACSD-61756: データベース インデックスがないことが原因で、''AdvancedSalesRule'' フィルターのパフォーマンスが低下しています'
description: ACSD-61756 パッチを適用すると、「magento_salesrule_filter」クエリがインデックスを使用せずにフルテーブルスキャンを実行し、大量のレコードを処理する際のパフォーマンスの低下につながるAdobe Commerceの問題を修正できます。 このパッチにより、「AdvancedSalesRule」フィルターに欠落しているデータベースインデックスが追加され、パフォーマンスが向上します。
feature: Price Rules, Price Indexer
role: Admin, Developer
exl-id: 418c7c40-83ee-4cd9-8ebb-b356886ffb58
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# ACSD-61756：データベースインデックスがないことが原因で、`AdvancedSalesRule` フィルターのパフォーマンスが低下します

ACSD-61756 パッチを適用して、欠落しているデータベースインデックスを追加することで `AdvancedSalesRule` フィルターのパフォーマンスを向上させます。 これにより、`magento_salesrule_filter` クエリがインデックスを使用せずにフルテーブルスキャンを実行し、テーブルに多数のレコードがある場合にパフォーマンスが低下する問題が修正されました。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.54 がインストールされている場合に使用できます。 パッチ ID は ACSD-61756 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4-p9

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.6-p8

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

`magento_salesrule_filter` クエリは、インデックスを使用せずに完全なテーブルスキャンを実行するので、テーブルに多数のレコードがある場合に `AdvancedSalesRule` フィルターのパフォーマンスが低下します。

<u> 再現手順 </u>:

1. 複数のアクティブな販売ルールでチェックアウトします。

<u> 期待される結果 </u>:

販売ルールのパフォーマンスが向上しました。

<u> 実際の結果 </u>:

クエリは完全なテーブルスキャンを実行し、インデックスを使用できないので、テーブルに多数のレコードがある場合にパフォーマンスが低下します。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。

QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)」を参照してください。
