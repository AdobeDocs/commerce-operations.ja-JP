---
title: MDVA-42689：読み込み中に製品カテゴリを更新する際に、ユーザーに「整合性の制約の違反」エラーが発生する
description: MDVA-42689 パッチは、読み込み中に製品カテゴリを更新する際に、ユーザーが統合制約違反エラーを受け取る問題を解決します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.12がインストールされている場合に利用できます。 パッチ IDはMDVA-42689です。 この問題は、Adobe Commerce 2.4.5で修正される予定です。
feature: Categories, Data Import/Export, Products
role: Admin
exl-id: 3f81f195-5a95-45f6-8970-403b8398e759
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '490'
ht-degree: 0%

---

# MDVA-42689：読み込み中に製品カテゴリを更新する際に、ユーザーに「整合性の制約の違反」エラーが発生する

MDVA-42689 パッチは、読み込み中に製品カテゴリを更新する際に、ユーザーが統合制約違反エラーを受け取る問題を解決します。 このパッチは、[品質パッチツール（QPT） &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.12がインストールされている場合に使用できます。 パッチ IDはMDVA-42689です。 この問題は、Adobe Commerce 2.4.5で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

読み込み中に製品カテゴリを更新すると、Adobe CommerceでIntegrity Constraint Violation エラーがスローされる。

<u>複製する手順</u>:

1. 2つのweb サイトを設定する。
1. ルートカテゴリの下にサブカテゴリを作成し、カテゴリーページで最大2つのレベルを作成します。 例えば、ルートカテゴリ > **ギア** > **ウォッチ**&#x200B;などです。
1. 2つのシンプルな商品を作成し、両方の商品を同じ&#x200B;**ギア**/**ウォッチ** カテゴリーに割り当てます。
1. 両方のweb サイトにひとつのシンプルな商品を割り当てる。
1. 製品を保存します。
1. 読み込むCSV ファイルを準備します。 ストアビューが異なる2つの商品レコードがあるべきです。 これらのストアビューの両方に属している必要があります。
1. 次に、**System** > **Import** > **Entity Type** （Products）に移動して、CSV ファイルを読み込みます。

<u>期待される結果</u>:

CSV ファイルはエラーなく読み込まれます。

<u>実際の結果</u>:

Adobe Commerceは次のエラーをスローします。

```SQL
SQLSTATE[23000]: Integrity constraint violation: 1062 Duplicate entry '1302' for key 'PRIMARY', query was: INSERT INTO `catalog_url_rewrite_product_category` (`url_rewrite_id`,`category_id`,`product_id`) VALUES (?, ?, ?), (?, ?, ?), (?, ?, ?)
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
