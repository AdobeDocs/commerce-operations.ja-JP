---
title: ACSD-45488：複数のソースを持つ設定可能な製品が自動的に在庫に戻されない
description: ACSD-45488 パッチは、複数のソースを持つ設定可能な製品が自動的に在庫に戻されない問題を解決します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.18がインストールされている場合に利用できます。 パッチ IDはACSD-45488です。 この問題は、Adobe Commerce 2.4.6で修正される予定です。
feature: Configuration, Orders, Products, Returns
role: Admin
exl-id: 53f34e8e-00bd-4386-bebf-b15882e36da1
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '486'
ht-degree: 0%

---

# ACSD-45488：複数のソースを持つ設定可能な製品が自動的に在庫に戻されない

ACSD-45488 パッチは、複数のソースを持つ設定可能な製品が自動的に在庫に戻されない問題を解決します。 このパッチは、[品質パッチツール（QPT） ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.18がインストールされている場合に使用できます。 パッチ IDはACSD-45488です。 この問題は、Adobe Commerce 2.4.6で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2-p2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2 - 2.4.5

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

複数のソースを持つ設定可能な商品は、自動的に在庫に戻されません。

<u>複製する手順</u>:

1. セカンダリ在庫ソースの作成。
1. 2つの関連付けられた仮想製品を持つ設定可能な製品を作成します。
1. 関連付けられた製品をデフォルトの在庫ソースに割り当て、数量を1に設定します。
1. `cataloginventory_stock_status`の`stock_status`を確認してください。
1. 関連付けられている製品の両方を&#x200B;*在庫切れ*&#x200B;に設定します。
1. `cataloginventory_stock_status`の`stock_status`を確認してください。
1. 両方の関連商品を&#x200B;*在庫*&#x200B;に設定します。
1. `cataloginventory_stock_status`の`stock_status`を確認してください。

<u>期待される結果</u>:

関連付けられた製品が在庫に設定されると、設定可能な製品の在庫ステータスが&#x200B;*在庫*&#x200B;に更新されます。

<u>実際の結果</u>:

関連付けられた製品が在庫に設定されている場合、設定可能な製品の在庫ステータスは&#x200B;*in stock*&#x200B;に更新されません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [品質パッチツール ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
