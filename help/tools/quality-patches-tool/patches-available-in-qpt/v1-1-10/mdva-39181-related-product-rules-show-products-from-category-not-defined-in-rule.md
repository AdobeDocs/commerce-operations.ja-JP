---
title: MDVA-39181：関連する製品ルールに、ルールで定義されていないカテゴリの製品が表示される
description: MDVA-39181 パッチは、関連する製品ルールがルールで定義されていないカテゴリの製品を表示する問題を解決します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.10がインストールされている場合に利用できます。 パッチ IDはMDVA-39181です。 この問題は、Adobe Commerce 2.4.5で修正される予定です。
feature: Categories, Products
role: Admin
exl-id: 98f65b7d-2cb3-49ff-95ef-c23a922e49f2
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '551'
ht-degree: 0%

---

# MDVA-39181：関連する製品ルールに、ルールで定義されていないカテゴリの製品が表示される

MDVA-39181 パッチは、関連する製品ルールがルールで定義されていないカテゴリの製品を表示する問題を解決します。 このパッチは、[品質パッチツール（QPT） &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.10がインストールされている場合に使用できます。 パッチ IDはMDVA-39181です。 この問題は、Adobe Commerce 2.4.5で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

関連製品ルール ルール ルールには、ルールで定義されていないカテゴリの製品が表示されます。

<u>前提条件</u>:

サンプルデータをインストールします。

<u>複製する手順</u>:

1. 属性ブランドを作成し、**トップレベルの属性セット**&#x200B;に追加します。
1. **Josie**、**Augusta**、および&#x200B;**Ingrid** ジャケットを選択して、**Women** > **Tops** > **Jackets カテゴリ**&#x200B;からBrand Kittyに追加します。
1. **Beaumont**、**Hyperion**、**Kenobi**&#x200B;のジャケットを選択して、**Men** > **Tops** > **ジャケットカテゴリ**&#x200B;からブランドキティに追加します。
1. 関連商品の作成：

   ```markdown
   Apply To: Related Products
   Customer Segments: All
   ```

   * 一致する製品：

   ```markdown
   If ALL of these conditions are TRUE
     Category is {}
     Brand is {}
   ```

   * 表示する製品：

   ```markdown
   If ALL of these conditions are TRUE
      Product Category is the same as Matched Product Category
      Product brand is Matched Product Brand
   ```

1. フロントエンドからSKU WJ04を開き、関連製品を確認します。
1. **女性** > **トップス** > **ジャケット**&#x200B;からカテゴリ IDを更新します。これとは異なる場合があります。

<u>期待される結果</u>:

関連製品には、同じブランドと同じ子カテゴリの製品のみが表示されます。

<u>実際の結果</u>:

関連商品は、同じブランドで表示されますが、ランダムな親カテゴリから表示されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [品質パッチツール &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
