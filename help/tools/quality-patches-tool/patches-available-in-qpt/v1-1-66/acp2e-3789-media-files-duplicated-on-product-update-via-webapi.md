---
title: ACP2E-3789：製品アップデートでWebAPI経由でメディアファイルが重複する
description: ACP2E-3789 パッチを適用して、WebAPIを介した製品の更新でメディア IDが指定されたときにメディアファイルが重複するAdobe Commerceの問題を修正します。
feature: Catalog Management, Media, REST, Products, Cache
role: Admin, Developer
type: Troubleshooting
exl-id: 1eaa8ed0-fde6-47c4-9339-8f5e7bce7b19
source-git-commit: 4266dbeca837bc62e5a76b2ef22b065a3452e088
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 0%

---

# ACP2E-3789：製品アップデートでWebAPI経由でメディアファイルが重複する

ACP2E-3789 パッチは、メディア IDが指定された場合に、WebAPIを介して製品の更新がメディアファイルを重複する問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.66がインストールされている場合に利用できます。 パッチ IDはACP2E-3789です。 この問題は、Adobe Commerce 2.4.9で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p3

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5 - 2.4.8

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

WebAPI経由でメディア IDを使用して製品を更新すると、メディアファイルを置き換える代わりにシステムがメディアファイルを複製し、API呼び出しごとに新しいファイルを作成し、`/pub/media/catalog/products/cache/` ディレクトリをオーバーロードする画像のビルドアップが発生します。

<u>複製する手順</u>:

1. 商品を作成し、画像を追加する。
1. `base_url/rest/V1/products/<sku>`のREST APIを使用して製品の詳細を取得します。
1. PUT リクエストを実行して、`media_gallery_entrie`を変更せずに製品を更新します（同じ画像名とファイル）。
1. 更新の前後に`pub/media/catalog/product/xx/yy` ディレクトリを確認します。

<u>期待される結果</u>:

メディア IDがリクエストに含まれると、画像ファイルが置き換えられます。

<u>実際の結果</u>:

画像が新しい名前（wb04-blue-1.jpgなど）で複製され、不要なファイルのビルドアップが発生します。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
