---
title: 'ACSD-55414: MariaDBがentitys_idsをキャストしようとするとパフォーマンスが低下する'
description: MariaDBが「entitys_ids」を文字列から整数に変換しようとすると、インデックス再作成のパフォーマンスが妨げられるため、Adobe Commerceの問題を修正するためにACSD-55414 パッチを適用します。
feature: Attributes
role: Admin, Developer
exl-id: 76309cef-559e-4a55-a27b-7d807ef9f74e
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# ACSD-55414: MariaDBが`entitys_ids`をキャストしようとするとパフォーマンスが低下する

ACSD-55414 パッチは、MariaDBが`entitys_ids`を文字列から整数に変換しようとすると、インデックス再作成のパフォーマンスが妨げられる問題を修正します。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.41がインストールされている場合に利用できます。 パッチ IDはACSD-55414です。 この問題は、Adobe Commerce 2.4.6で修正されています。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p4

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.0 - 2.4.5-p5

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

MariaDBが`entitys_ids`を文字列から整数にキャストしようとすると、インデックス再作成のパフォーマンスが妨げられます。

<u>複製する手順</u>:

1. *50000*&#x200B;個のシンプルな製品を設定して、`setup/performance-toolkit/profiles/ce/small.xml`を更新します。
1. 次のコマンドを実行してこのプロファイルを生成します：`bin/magento setup:perf:generate-fixtures setup/performance-toolkit/profiles/ce/small.xml`。
1. インデックス再作成を実行：`bin/magento indexer:reindex catalog_product_attribute`。

<u>期待される結果</u>:

インデックス再作成には妥当な時間がかかります。

<u>実際の結果</u>:

インデックス再作成の完了に時間がかかりすぎる。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
