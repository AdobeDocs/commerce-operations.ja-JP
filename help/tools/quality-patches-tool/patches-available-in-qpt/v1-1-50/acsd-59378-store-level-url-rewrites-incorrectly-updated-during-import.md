---
title: 'ACSD-59378：読み込み時にストアレベルの書き換えが誤って更新される  [!DNL URL] '
description: ACSD-59378 パッチを適用して、読み込み時にストアレベルの書き換えが誤って更新されるAdobe Commerceの問題  [!DNL URL]  修正してください。
feature: Data Import/Export
role: Admin, Developer
exl-id: dc54d810-dcc6-42c6-a877-d00d3cf4f9a5
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# ACSD-59378：読み込み時にストアレベルの [!DNL URL] 書き換えが誤って更新される

ACSD-59378 パッチは、読み込み時にストアレベルの [!DNL URL] 書き換えが誤って更新される問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.50 がインストールされている場合に使用できます。 パッチ ID は ACSD-59378 です。 この問題はAdobe Commerce 2.4.7 で修正されました。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p5

**Adobe Commerce バージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方法） 2.4.5x （すべてのバージョンの 2.4.5）

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

読み込み時に、ストアレベルの [!DNL URL] 書き換えが誤って更新される。

<u> 再現手順 </u>:

1. **すべてのストア表示** 範囲に `url_key = key_default` を持つ製品を作成します。
1. **デフォルトのストア表示** 範囲で `url_key = key_store` を設定します。
1. 商品を書き出します。
1. 次のデータを含むこの製品の [!DNL CSV] ファイルをインポートします：
   * 列 `store_view_code`*すべてのストア表示* 範囲に適用されるように、**空** に設定されます。
   * `url_key` はデフォルトのキー *`key_default`* に設定されます。

<u> 期待される結果 </u>:

[!DNL URL] の書き換えは、上書きされた `url_key` が存在しない（デフォルト `url_key` が適用される）ストアビューの場合にのみ再生成されます。

<u> 実際の結果 </u>:

`key_store` [!DNL URL] の書き換えは削除されますが、製品の **デフォルトストア表示** レベルの [!DNL URL] 書き換えは引き続き *`key_store`* に設定されます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)」を参照してください。
