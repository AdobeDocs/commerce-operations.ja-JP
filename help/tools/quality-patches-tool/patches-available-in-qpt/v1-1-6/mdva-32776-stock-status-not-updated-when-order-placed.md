---
title: MDVA-32776：注文の配置で在庫ステータスが更新されない
description: MDVA-32776 パッチでは、注文が行われても配送されないときに在庫状況が更新されない問題を修正します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.6がインストールされている場合に利用できます。 パッチ IDはMDVA-32776です。 この問題はAdobe Commerce 2.4.2で修正されています。
feature: Orders
role: Admin
exl-id: 6f872c72-c96f-4c23-b6df-44e3da3a81c2
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '507'
ht-degree: 0%

---

# MDVA-32776：注文の配置で在庫ステータスが更新されない

MDVA-32776 パッチでは、注文が行われても配送されないときに在庫状況が更新されない問題を修正します。 このパッチは、[品質パッチツール （QPT） ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.6がインストールされている場合に使用できます。 パッチ IDはMDVA-32776です。 この問題はAdobe Commerce 2.4.2で修正されています。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

Adobe Commerce（すべてのデプロイメント方法） 2.4.0

**Adobe Commerceのバージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方法） 2.4.0 - 2.4.1-p1

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

注文しても在庫状況は更新されませんが、発送はされません。

<u>前提条件</u>:

1. インベントリモジュールがインストールされている。
1. 在庫切れ商品の表示は&#x200B;*はい*&#x200B;に設定されています。

   設定するには、**Stores** > **Configuration** > **Catalog** > **Inventory** > **在庫切れ商品の表示** = *Yes*&#x200B;に移動します。

<u>複製する手順</u>:

1. qty = 11と22の2つの単純な製品を作成します。
1. 手順1で作成したシンプルな製品を使用して、グループ化された製品を作成します。
1. いずれかの商品数量を11に設定し、他のシンプルな商品を在庫切れにすることで、グループ化された商品をカートに追加します。
1. チェックアウトを完了し、注文します。

<u>期待される結果</u>:

グループ化された商品は、関連付けられたシンプルな商品が在庫切れになると`out-of-stock` ラベルが表示されます。

<u>実際の結果</u>:

1. qty = 11のシンプルな商品は在庫切れです。
1. グループ化された製品には、数量= 11の製品に対する&#x200B;*在庫切れ* メッセージが表示されません。 ただし、この商品をカートに追加すると、*在庫切れ*&#x200B;のエラーが発生します。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [品質パッチツール ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、「QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で使用可能な[ パッチ」セクションを参照してください。
