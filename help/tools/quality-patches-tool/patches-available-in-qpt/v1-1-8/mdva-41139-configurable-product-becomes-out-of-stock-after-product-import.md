---
title: MDVA-41139：製品をインポートすると、設定可能な製品が在庫切れになる
description: MDVA-41139 パッチでは、製品のソースの1つに対する単純な製品の数量= 0の場合、製品のインポート後に設定可能な製品が在庫切れになる問題を修正します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.8がインストールされている場合に利用できます。 パッチ IDはMDVA-41139です。 この問題は、Adobe Commerce 2.4.4で修正される予定です。
feature: Data Import/Export, Configuration, Orders, Products
role: Admin
exl-id: 7366230c-3b7f-4211-9f0d-55a528dffdbd
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 0%

---

# MDVA-41139：製品をインポートすると、設定可能な製品が在庫切れになる

MDVA-41139 パッチでは、製品のソースの1つに対する単純な製品の数量= 0の場合、製品のインポート後に設定可能な製品が在庫切れになる問題を修正します。 このパッチは、[品質パッチツール （QPT） ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.8がインストールされている場合に使用できます。 パッチ IDはMDVA-41139です。 この問題は、Adobe Commerce 2.4.4で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

製品の簡易製品の数量= 0がソースの1つに対して設定された製品が、製品のインポート後に在庫切れになります。

<u>前提条件</u>:

在庫モジュールが取り付けられています。

<u>複製する手順</u>:

1. 新しいソースと在庫を作成する。
1. デフォルトのソースと新しいソースに割り当てられた子製品を含む設定可能な製品を作成します。
1. 各子商品= 0のデフォルトの在庫の値と、その他の在庫> 0の値を設定します。
1. コンフィグ商品は在庫あり。
1. この製品をエクスポートして、もう一度インポートします。

<u>期待される結果</u>:

第2のソースの数量が0を超えているため、コンフィグ可能な商品は在庫にあります。

<u>実際の結果</u>:

コンフィグ商品は在庫切れです。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [品質パッチツール ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
