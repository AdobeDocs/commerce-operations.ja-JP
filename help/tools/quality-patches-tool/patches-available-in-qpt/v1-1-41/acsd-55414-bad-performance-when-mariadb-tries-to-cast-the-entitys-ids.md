---
title: ACSD-55414:MariaDB が entitys_ids をキャストしようとすると、パフォーマンスが低下します
description: MariaDB が「entitys_ids」を文字列から整数に変換しようとすると、インデックス再作成のパフォーマンスが妨げられ、Adobe Commerceの問題を修正するために ACSD-55414 パッチを適用してください。
feature: Attributes
role: Admin, Developer
exl-id: 76309cef-559e-4a55-a27b-7d807ef9f74e
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 0%

---

# ACSD-55414:MariaDB が `entitys_ids` をキャストしようとすると、パフォーマンスが低下します

ACSD-55414 パッチでは、MariaDB が `entitys_ids` を文字列から整数に変換しようとすると、インデックス再作成のパフォーマンスが妨げられる問題が修正されています。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.41 がインストールされている場合に使用できます。 パッチ ID は ACSD-55414 です。 この問題はAdobe Commerce 2.4.6 で修正されていることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p4

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.0 ～ 2.4.5-p5

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

MariaDB が `entitys_ids` を文字列から整数にキャストしようとすると、インデックス再作成のパフォーマンスが妨げられます。

<u> 再現手順 </u>:

1. `setup/performance-toolkit/profiles/ce/small.xml`50000 *の簡単な製品を設定して* を更新します。
1. コマンド `bin/magento setup:perf:generate-fixtures setup/performance-toolkit/profiles/ce/small.xml` を実行して、このプロファイルを生成します。
1. 再インデックス（`bin/magento indexer:reindex catalog_product_attribute`）を実行します。

<u> 期待される結果 </u>:

再インデックスの完了には十分な時間がかかります。

<u> 実際の結果 </u>:

この再インデックスの完了に時間がかかりすぎます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 &#x200B;](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [&#x200B; アップグレードとパッチ &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [&#x200B; を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[[!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja): Search for patches[!DNL Quality Patches Tool]」を参照してください。
