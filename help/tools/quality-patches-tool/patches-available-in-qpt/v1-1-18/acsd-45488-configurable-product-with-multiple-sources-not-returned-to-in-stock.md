---
title: ACSD-45488：複数のソースを持ち、在庫に自動的に戻されない設定可能な製品
description: ACSD-45488 パッチを使用すると、複数のソースを持つ設定可能な製品が在庫として自動的に返されない問題を解決できます。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.18 がインストールされている場合に利用できます。 パッチ ID は ACSD-45488 です。 この問題はAdobe Commerce 2.4.6 で修正される予定であることに注意してください。
feature: Configuration, Orders, Products, Returns
role: Admin
exl-id: 53f34e8e-00bd-4386-bebf-b15882e36da1
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 0%

---

# ACSD-45488：複数のソースを持ち、在庫に自動的に戻されない設定可能な製品

ACSD-45488 パッチを使用すると、複数のソースを持つ設定可能な製品が在庫として自動的に返されない問題を解決できます。 このパッチは、[Quality Patches Tool （QPT） ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)1.1.18 がインストールされている場合に使用できます。 パッチ ID は ACSD-45488 です。 この問題はAdobe Commerce 2.4.6 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2-p2

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2 ～ 2.4.5

>[!NOTE]
>
>パッチは、新しい Quality Patches Tool リリースを使用する他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

複数のソースを持つ設定可能な製品は、在庫に自動的には戻されません。

<u> 再現手順 </u>:

1. サブ在庫ソースを作成します。
1. 関連する 2 つの仮想製品を使用して設定可能な製品を作成します。
1. 関連製品をデフォルトの在庫ソースに割り当て、数量を 1 に設定します。
1. `stock_status` から `cataloginventory_stock_status` を確認します。
1. 関連する両方の製品を *在庫切れ* に設定します。
1. `stock_status` から `cataloginventory_stock_status` を確認します。
1. 関連する両方の製品を *在庫* に設定します。
1. `stock_status` から `cataloginventory_stock_status` を確認します。

<u> 期待される結果 </u>:

関連する商品が在庫中に設定されると、設定可能な商品の在庫ステータスが *在庫中* に更新されます。

<u> 実際の結果 </u>:

関連する商品が在庫中に設定されている場合、設定可能な商品の在庫ステータスは *在庫中* に更新されません。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

品質向上パッチツールの詳細については、次を参照してください。

* [ 品質向上パッチツールがリリースされました：品質向上パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) がサポートナレッジベースに追加されました。
* [Quality Patches Tool を使用して、Adobe Commerceの問題に対するパッチが使用可能かどうかを確認します ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!DNL Quality Patches Tool] ガイド）。

QPT で使用可能なその他のパッチの詳細については、[[!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html): Search for patches[!DNL Quality Patches Tool]」を参照してください。
