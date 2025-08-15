---
title: MDVA-39181：関連製品ルールで、ルールに定義されていないカテゴリの製品が表示される
description: MDVA-39181 パッチを使用すると、関連する製品ルールに定義されていないカテゴリの製品が表示される問題を解決できます。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.10 がインストールされている場合に利用できます。 パッチ ID は MDVA-39181。 この問題はAdobe Commerce 2.4.5 で修正される予定であることに注意してください。
feature: Categories, Products
role: Admin
exl-id: 98f65b7d-2cb3-49ff-95ef-c23a922e49f2
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# MDVA-39181：関連製品ルールで、ルールに定義されていないカテゴリの製品が表示される

MDVA-39181 パッチを使用すると、関連する製品ルールに定義されていないカテゴリの製品が表示される問題を解決できます。 このパッチは、[Quality Patches Tool （QPT） ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)1.1.10 がインストールされている場合に使用できます。 パッチ ID は MDVA-39181。 この問題はAdobe Commerce 2.4.5 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.1 ～ 2.4.3-p1

>[!NOTE]
>
>パッチは、新しい Quality Patches Tool リリースを使用する他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

関連する製品ルールには、ルールで定義されていないカテゴリの製品が表示されます。

<u> 前提条件 </u>:

サンプルデータをインストールします。

<u> 再現手順 </u>:

1. 属性ブランドを作成して、**Tops 属性セット** に追加します。
1. **Josie**、**Augusta**、**Ingrid** の各ジャケットを選択し、**Women**/**Tops**/**Jackets category** からブランドキティに追加します。
1. **Men**/**Tops**/**Jacket category** からブランドのキティに追加するジャケットは、**Beaumont**、**Hyperion**、**Kenobi** を選択してください。
1. 関連製品を次のように作成します。

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

1. フロントエンドから SKU WJ04 を開き、関連製品を確認します。
1. カテゴリ ID が次と異なる場合は、**Women**/**Tops**/**Jackets** からカテゴリ ID を更新します。

<u> 期待される結果 </u>:

関連製品には、同じブランドおよび同じ子カテゴリの製品のみが表示されます。

<u> 実際の結果 </u>:

関連製品は、同じブランドで、ランダムな親カテゴリから表示されます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md)[!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

品質向上パッチツールの詳細については、次を参照してください。

* [ 品質向上パッチツールがリリースされました：品質向上パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) がサポートナレッジベースに追加されました。
* [Quality Patches Tool を使用して、Adobe Commerceの問題に対するパッチが使用可能かどうかを確認します ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!DNL Quality Patches Tool] ガイド）。

QPT で使用可能なその他のパッチの詳細については、[[!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html): Search for patches[!DNL Quality Patches Tool]」を参照してください。
