---
title: ACP2E-3789:WebAPI を使用した製品アップデートでメディアファイルが重複する
description: ACP2E-3789 パッチを適用して、WebAPI を介した製品のアップデートでメディア ID が指定された場合にメディアファイルが重複するAdobe Commerceの問題を修正してください。
feature: Catalog Management, Media, REST, Products, Cache
role: Admin, Developer
type: Troubleshooting
source-git-commit: 8c1924a47248b22327dfc9a15ae426b2802e126b
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%

---


# ACP2E-3789:WebAPI を使用した製品アップデートでメディアファイルが重複する

ACP2E-3789 パッチは、メディア ID が指定されている場合に、WebAPI を介した製品のアップデートによってメディアファイルが重複する問題を修正しました。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.66 がインストールされている場合に使用できます。 パッチ ID は ACP2E-3789 です。 この問題はAdobe Commerce 2.4.9 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p3

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5 ～ 2.4.8

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

WebAPI を使用して製品をメディア ID で更新すると、システムはメディアファイルを置き換えるのではなく複製し、API 呼び出しごとに新しいファイルを作成し、`/pub/media/catalog/products/cache/` ディレクトリをオーバーロードする画像の蓄積が発生します。

<u> 再現手順 </u>:

1. 製品を作成して画像を追加します。
1. `base_url/rest/V1/products/<sku>` で REST API を使用して製品の詳細を取得します。
1. PUT リクエストを実行して、`media_gallery_entrie` を変更しない（画像名とファイルが同じ）まま、商品をアップデートします。
1. 更新前と更新後に `pub/media/catalog/product/xx/yy` ディレクトリを確認します。

<u> 期待される結果 </u>:

画像ファイルは、メディア ID がリクエストに含まれる際に置き換えられます。

<u> 実際の結果 </u>:

画像が新しい名前（wb04-blue-1.jpg など）で複製されるので、不要なファイルが蓄積されます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md)[!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
