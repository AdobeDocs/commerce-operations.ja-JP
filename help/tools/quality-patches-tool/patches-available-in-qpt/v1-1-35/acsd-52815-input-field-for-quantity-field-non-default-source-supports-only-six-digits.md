---
title: ACSD-52815：デフォルト以外のソースの数量フィールドの入力フィールドでは、最大6桁しかサポートされていません
description: ACSD-52815 パッチを適用して、デフォルト以外のソースの数量フィールドの入力フィールドが最大6桁のみをサポートするAdobe Commerceのパフォーマンスの問題を修正します。デフォルトの在庫の8桁とは異なります。
feature: Inventory, Products
role: Admin
exl-id: d863af1f-8a7f-4a43-893e-54525ab68cd7
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-52815：デフォルト以外のソースの数量フィールドの入力フィールドでは、最大6桁しかサポートされていません

ACSD-52815 パッチでは、デフォルト以外のソースの数量フィールドの入力フィールドが最大6桁のみをサポートし、デフォルトの在庫の8桁をサポートする問題を修正します。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.35がインストールされている場合に利用できます。 パッチ IDはACSD-52815です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

デフォルト以外のソースの数量フィールドの入力フィールドは、デフォルトの在庫の8桁とは異なり、最大6桁のみをサポートします。

<u>複製する手順</u>:

1. 新しいストックとソースを作成します。
1. 新しいソースストックを123に設定した商品を作成します。
1. 販売可能数量（123）を確認します。
1. ソース数量を「12345678」に更新します。
1. 販売可能な数量を確認します。

<u>期待される結果</u>:

販売可能数量は正しい金額を示します。

<u>実際の結果</u>:

販売可能数量は999999.9999です。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
