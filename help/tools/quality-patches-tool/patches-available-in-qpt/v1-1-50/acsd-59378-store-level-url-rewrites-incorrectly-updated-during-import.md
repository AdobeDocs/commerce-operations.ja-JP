---
title: ACSD-59378：読み込み中にストアレベル  [!DNL URL] の書き換えが正しく更新されない
description: ストアレベル  [!DNL URL] の書き換えが読み込み中に誤って更新されるAdobe Commerceの問題を修正するには、ACSD-59378 パッチを適用します。
feature: Data Import/Export
role: Admin, Developer
exl-id: dc54d810-dcc6-42c6-a877-d00d3cf4f9a5
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 0%

---

# ACSD-59378: インポート中にストアレベル [!DNL URL]の書き換えが正しく更新されない

ACSD-59378 パッチは、ストアレベル [!DNL URL]の書き換えが読み込み中に誤って更新される問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.50がインストールされている場合に利用できます。 パッチ IDはACSD-59378です。 この問題は、Adobe Commerce 2.4.7で修正されています。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p5

**Adobe Commerceのバージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方法） 2.4.5倍（2.4.5のすべてのバージョン）

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

ストア レベル [!DNL URL]の書き換えが、読み込み中に正しく更新されません。

<u>複製する手順</u>:

1. **すべてのストアビュー**&#x200B;の範囲で`url_key = key_default`の商品を作成します。
1. `url_key = key_store`を&#x200B;**デフォルトストアビュー** スコープで設定します。
1. 製品をエクスポートします。
1. この製品の[!DNL CSV] ファイルを、次のデータを含むファイルとして読み込みます。
   * `store_view_code`列が&#x200B;*empty*&#x200B;に設定されているため、**すべてのストアビュー**&#x200B;の範囲に適用されます。
   * `url_key`は既定のキー&#x200B;*`key_default`*&#x200B;に設定されています。

<u>期待される結果</u>:

[!DNL URL]の書き換えは、上書きされていない`url_key` （デフォルトの`url_key`が適用される）ストアビューに対してのみ生成されます。

<u>実際の結果</u>:

`key_store` [!DNL URL]個の書き換えは削除されますが、製品の&#x200B;**既定のストアビュー** レベルの[!DNL URL]個の書き換えは引き続き&#x200B;*`key_store`*&#x200B;に設定されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
