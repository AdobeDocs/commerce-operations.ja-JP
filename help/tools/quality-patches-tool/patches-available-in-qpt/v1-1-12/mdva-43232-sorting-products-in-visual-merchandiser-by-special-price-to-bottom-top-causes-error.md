---
title: MDVA-43232：ビジュアルマーチャンダイザーで商品を特別価格で上（または下）に並べ替えるとエラーが発生する
description: MDVA-43232 パッチは、ビジュアルマーチャンダイザーの製品を特別価格で上（または下）に並べ替えると、カテゴリの保存中にエラーが発生する問題を修正します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.12 がインストールされている場合に利用できます。 パッチ ID は MDVA-43232。 この問題はAdobe Commerce 2.4.5 で修正される予定であることに注意してください。
feature: Categories, Merchandising, Orders, Personalization, Products
role: Admin
exl-id: c977bec8-f99c-4799-abce-26aad49b77e8
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '509'
ht-degree: 0%

---

# MDVA-43232：ビジュアルマーチャンダイザーで商品を特別価格で上（または下）に並べ替えるとエラーが発生する

MDVA-43232 パッチは、ビジュアルマーチャンダイザーの製品を特別価格で上（または下）に並べ替えると、カテゴリの保存中にエラーが発生する問題を修正します。 このパッチは、[Quality Patches Tool （QPT） ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)1.1.12 がインストールされている場合に使用できます。 パッチ ID は MDVA-43232。 この問題はAdobe Commerce 2.4.5 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2-p1

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.4 - 2.4.3

>[!NOTE]
>
>パッチは、新しい Quality Patches Tool リリースを使用する他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

ビジュアルマーチャンダイザーで製品を特別価格から上（または下）に並べ替えると、カテゴリの保存中にエラーが発生します。

<u> 再現手順 </u>:

1. 2 つの web サイトがあることを確認します。
1. **Stores**/**Configuration**/**Catalog**/**Price** に移動し、「Catalog Price Scope = Website」と設定します。
1. 再度、**ストア**/**設定**/**カタログ**/**ビジュアルマーチャンダイザー**/**カテゴリルールの表示可能な属性** に移動し、特別価格を追加します。
1. シンプルな製品を作成して、両方の web サイトに製品を割り当てます。
1. 商品のデフォルトの範囲に特別価格を追加します。
1. 他の店舗のスコープに切り替え、その商品の価格と特別価格の両方を上書きします。
1. `catalog_product_price` の再インデックスを実行します。
1. **カタログ**/**カテゴリ** に移動し、新しいカテゴリを作成します。
1. カテゴリ ルールを追加して、特別価格のある製品をフィルターします。
1. カテゴリの保存。
1. 「カテゴリの製品」セクションで、「並べ替え順=特別価格」を「上（または下）」に設定します。
1. カテゴリを再度保存します。

<u> 期待される結果 </u>:

カテゴリはエラーなしで保存されます。

<u> 実際の結果 </u>:

例外がスローされます。

```php
[2022-02-07T05:58:46.297621+00:00] report.CRITICAL: Exception: Item (Magento\Catalog\Model\Product\Interceptor) with the same ID "1" already exists. in /lib/internal/Magento/Framework/Data/Collection.php:407
```

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

品質向上パッチツールの詳細については、次を参照してください。

* [ 品質向上パッチツールがリリースされました：品質向上パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) がサポートナレッジベースに追加されました。
* [Quality Patches Tool を使用して、Adobe Commerceの問題に対するパッチが使用可能かどうかを確認します ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!DNL Quality Patches Tool] ガイド）。

QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)」を参照してください。
