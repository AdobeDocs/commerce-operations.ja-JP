---
title: MDVA-43232：ビジュアルマーチャンダイザーの商品を特別価格で上（または下）に並べ替えるとエラーが発生する
description: MDVA-43232 パッチは、ビジュアルマーチャンダイザーの商品を特別価格で上位（または下位）に並べ替えると、カテゴリを保存する際にエラーが発生する問題を修正します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.12がインストールされている場合に利用できます。 パッチ IDはMDVA-43232です。 この問題は、Adobe Commerce 2.4.5で修正される予定です。
feature: Categories, Merchandising, Orders, Personalization, Products
role: Admin
exl-id: c977bec8-f99c-4799-abce-26aad49b77e8
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 58c984c2-e237-5c50-9718-500e40d1e82c
    internal-label: Merchandising
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: f37757d8-3174-5335-b977-1161792f965d
    internal-label: Personalization
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
subfeature_v2:
  - id: e91a50b1-0b31-436e-9033-00e4776e94cb
    internal-label: Categories
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '538'
ht-degree: 0%
---
# MDVA-43232：ビジュアルマーチャンダイザーの商品を特別価格で上（または下）に並べ替えるとエラーが発生する

MDVA-43232 パッチは、ビジュアルマーチャンダイザーの商品を特別価格で上位（または下位）に並べ替えると、カテゴリを保存する際にエラーが発生する問題を修正します。 このパッチは、[品質パッチツール（QPT） &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.12がインストールされている場合に使用できます。 パッチ IDはMDVA-43232です。 この問題は、Adobe Commerce 2.4.5で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.4 - 2.4.3

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

ビジュアルマーチャンダイザーの商品を特別価格で上位（または下位）に並べ替えると、カテゴリを保存する際にエラーが発生します。

<u>複製する手順</u>:

1. 2つのWeb サイトがあることを確認します。
1. **Stores** > **Configuration** > **Catalog** > **Price**&#x200B;に移動し、Catalog Price Scope = Websiteを設定します。
1. 繰り返しますが、**ストア** > **設定** > **カタログ** > **ビジュアルマーチャンダイザー** > **カテゴリルールの表示属性** >に移動し、特別価格を追加します。
1. シンプルな商品を作成し、両方のweb サイトに商品を割り当てる。
1. 製品のデフォルトスコープに特別価格を追加します。
1. 他のストアの範囲に切り替えて、その商品の価格と特別価格の両方を上書きします。
1. `catalog_product_price`のインデックス再作成を行います。
1. **カタログ** > **カテゴリー**&#x200B;に移動し、新しいカテゴリーを作成します。
1. 特別価格を持つ製品をフィルタリングするカテゴリルールを追加します。
1. カテゴリを保存します。
1. 「カテゴリ内の製品」セクションで、「並べ替え順序=特別価格」を「上（または下）」に設定します。
1. カテゴリをもう一度保存します。

<u>期待される結果</u>:

カテゴリはエラーなしで保存されます。

<u>実際の結果</u>:

例外がスローされます。

```php
[2022-02-07T05:58:46.297621+00:00] report.CRITICAL: Exception: Item (Magento\Catalog\Model\Product\Interceptor) with the same ID "1" already exists. in /lib/internal/Magento/Framework/Data/Collection.php:407
```

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [品質パッチツール &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
