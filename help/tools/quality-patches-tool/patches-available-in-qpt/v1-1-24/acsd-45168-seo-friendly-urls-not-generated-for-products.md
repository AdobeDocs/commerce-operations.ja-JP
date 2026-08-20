---
title: ACSD-45168:url_key属性がオーバーライドされた製品に対して、SEO対応URLが生成されない
description: ストアビューレベルでurl_key属性がオーバーライドされている商品に対してSEO対応URLが生成されないAdobe Commerceの問題を修正するには、ACSD-45168 パッチを適用します。
feature: Attributes, Cache, Categories, Marketing Tools, Products
role: Admin
exl-id: 7d908307-f60c-4758-ad0f-f108ebb94558
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# ACSD-45168:url_key属性がオーバーライドされた製品に対して、SEO対応URLが生成されない

ACSD-45168 パッチでは、ストアビューレベルでurl_key属性がオーバーライドされた製品に対して、SEO対応URLが生成されない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.24がインストールされている場合に利用できます。 パッチ IDはACSD-45168です。 この問題は、Adobe Commerce 2.4.6で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2 - 2.4.5-p1

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

url_key属性がstore-view レベルで上書きされた製品に対して、SEO対応URLは生成されません。

<u>複製する手順</u>:

1. **[!UICONTROL Commerce Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Search Engine Optimization]**&#x200B;に移動して、設定を次のように設定します。
   * [!UICONTROL Use Categories Path for Product URLs] = *はい*
   * [!UICONTROL Generate "category/product" URL Rewrites] = *はい*
1. 設定キャッシュをクリーニングします。
1. [!UICONTROL Category 1]と[!UICONTROL Category 2]の2つのカテゴリを作成します。
1. 2つの製品を作成します：[!UICONTROL Category 1]の[!UICONTROL Product 1]、[!UICONTROL Category 1]の[!UICONTROL Product 2]。
1. [!UICONTROL Product 1]の範囲を[!UICONTROL Default Store View]に変更します。
1. [!UICONTROL Search Engine Optimization]のオプションのURL [!UICONTROL Key]のチェックを外します。
1. 製品を保存します。
1. [!UICONTROL All Store Views]に切り替えます。
1. [!UICONTROL Product 1]を[!UICONTROL Category 2]に追加し、[!UICONTROL Product 2]を[!UICONTROL Category 2]に追加します。
1. `url_rewrite` テーブルまたは[!UICONTROL Marketing] > [!UICONTROL SEO & Search] > [!UICONTROL URL Rewrites]を確認してください。

<u>期待される結果</u>:

[!UICONTROL Category 2]のSEO対応URLは、[!UICONTROL Product 1]用に作成されています。

<u>実際の結果</u>:

[!UICONTROL Category 2]のSEOに適したURLが、[!UICONTROL Product 1]には見つかりません。ストア ビューのスコープ用にURL キー属性が上書きされたからです。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > Commerce クラウドインフラストラクチャ上のパッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」ガイド

## 関連トピックス

* [[!DNL Quality Patches Tool]  リリース：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを確認します
* [Commerce実装プレイブックのデータベーステーブルを修正するためのベストプラクティス &#x200B;](/help/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables.md#why-adobe-recommends-avoiding-modifications)

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
