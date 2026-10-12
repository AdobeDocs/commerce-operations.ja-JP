---
title: 'ACSD-61756: データベース インデックスが欠落しているため、「AdvancedSalesRule」フィルターのパフォーマンスが低下する'
description: 「magento_salesrule_filter」クエリがインデックスを使用せずにテーブル全体のスキャンを実行し、大量のレコードを処理する際にパフォーマンスが低下するAdobe Commerceの問題を修正するには、ACSD-61756 パッチを適用します。 このパッチは、「AdvancedSalesRule」フィルターに欠落しているデータベースインデックスを追加することで、パフォーマンスを向上させます。
feature: Price Rules, Price Indexer
role: Admin, Developer
exl-id: 418c7c40-83ee-4cd9-8ebb-b356886ffb58
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: a507b1ed-4937-53da-97ae-57d36bd5b9e0
    internal-label: Price Rules
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
subfeature_v2:
  - id: b0d35b91-b9b0-5983-b37c-f35bd2650b53
    internal-label: Price Indexer
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 0%
---
# ACSD-61756: データベース インデックスが見つからないため、`AdvancedSalesRule` フィルターのパフォーマンスが低下する

ACSD-61756 パッチを適用して、見つからないデータベース インデックスを追加することで、`AdvancedSalesRule` フィルターのパフォーマンスを向上させます。 これにより、`magento_salesrule_filter` クエリがインデックスを利用せずにテーブル全体のスキャンを実行し、テーブルに多数のレコードがある場合にパフォーマンスが低下する問題が修正されます。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54がインストールされている場合に利用できます。 パッチ IDはACSD-61756です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4-p9

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.6-p8

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

`magento_salesrule_filter` クエリは、インデックスを使用せずにテーブル全体のスキャンを実行します。これにより、テーブル内に多数のレコードがある場合に、`AdvancedSalesRule` フィルターのパフォーマンスが低下します。

<u>複製する手順</u>:

1. 複数のアクティブなセールスルールを活用。

<u>期待される結果</u>:

セールスルールのパフォーマンスの向上：

<u>実際の結果</u>:

クエリはテーブル全体のスキャンを実行し、インデックスの利用に失敗し、テーブル内に多数のレコードがある場合にパフォーマンスが低下します。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) パッチを検索する」を参照してください。
