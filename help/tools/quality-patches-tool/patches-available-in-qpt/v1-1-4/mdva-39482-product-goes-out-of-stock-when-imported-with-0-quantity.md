---
title: MDVA-39482：取り寄せ注文が有効で「0」の数量で取り込まれた場合、商品が在庫切れになる
description: MSIおよび取り寄せ注文が有効で、在庫切れしきい値がマイナス値に設定されている場合に「0」数量で取り込むと、MDVA-39482で商品が在庫切れになる問題が修正されます。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.4がインストールされている場合に利用できます。 パッチ IDはMDVA-39482です。 この問題は、Adobe Commerce 2.4.4で修正される予定です。
feature: Data Import/Export, Orders, Products
role: Admin
exl-id: 9d705ebf-2372-4e59-b447-cdb5b0db32f4
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 601e4abe-d9bf-58de-a779-32ed6794dcbe
    internal-label: Data Import/Export
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '520'
ht-degree: 0%
---
# MDVA-39482：取り寄せ注文が有効で「0」の数量で取り込まれた場合、商品が在庫切れになる

MSIおよび取り寄せ注文が有効で、在庫切れしきい値がマイナス値に設定されている場合に「0」数量で取り込むと、MDVA-39482で商品が在庫切れになる問題が修正されます。 このパッチは、[品質パッチツール （QPT） &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.4がインストールされている場合に使用できます。 パッチ IDはMDVA-39482です。 この問題は、Adobe Commerce 2.4.4で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

Adobe Commerce（すべてのデプロイメント方法） 2.4.1-p1

**Adobe Commerceのバージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方式） 2.3.6 - 2.3.7-p2、2.4.1 - 2.4.3-p1

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

MSIおよび取り寄せ注文が有効で、在庫切れしきい値がマイナス値に設定されている場合、商品は「0」の数量で取り込まれた場合、在庫切れになります。

<u>前提条件</u>:

1. MSIとサンプルデータをインストールする必要があります。
1. **ストア** > **設定** > **カタログ** > **インベントリ**&#x200B;に移動します。
   * バックオーダーを「0未満の数量を許可」に設定します。
   * 在庫切れしきい値を「–10」に設定

<u>複製する手順</u>:

1. SKUが&#x200B;**In Stock**&#x200B;で、数量&#x200B;**24-MB01**&#x200B;であることを確認してください。
1. ストックソースのCSVを読み込みます。 エンティティタイプで「ストックソース」を選択します。

   ```code panel
   sku,qty,out_of_stock_qty
   24-MB01,0,-10
   ```

1. 在庫ソースをインポートした後、製品の在庫ステータスを確認します。

<u>期待される結果</u>:

24-MB01はStorefrontの&#x200B;**In Stock**&#x200B;です。

<u>実際の結果</u>:

24-MB01は、Storefrontで&#x200B;**在庫切れ**&#x200B;です。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [品質パッチツール &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、「QPT[&#128279;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で使用可能な パッチ」セクションを参照してください。
