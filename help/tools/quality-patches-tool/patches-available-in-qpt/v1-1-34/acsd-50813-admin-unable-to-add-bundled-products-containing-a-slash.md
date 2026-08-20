---
title: ACSD-50813：管理者がスラッシュを含むバンドル製品を追加できない
description: 管理者がSKUにスラッシュマーク（'/'）を含むバンドル商品を管理者注文に*Add Products by SKU*機能でSKUに追加できないAdobe Commerceのパフォーマンス問題を修正するには、ACSD-50813 パッチを適用します。
exl-id: ff6fa673-bac1-4ef8-a427-60c2f56068f3
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# ACSD-50813：管理者がスラッシュを含むバンドル製品を追加できない

ACSD-50813 パッチは、管理者が管理者注文に&#x200B;*[!UICONTROL Add Products by SKU]*&#x200B;機能を持つSKUにスラッシュマーク（`/`）を含むバンドル製品を管理者が追加できない問題を修正します。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.34がインストールされている場合に利用できます。 パッチ IDはACSD-50813です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

管理者は、管理者注文に&#x200B;*[!UICONTROL Add Products by SKU]*&#x200B;機能を持つSKUにスラッシュマーク （`/`）を含むバンドル製品を追加できません。

<u>複製する手順</u>:

1. **[!UICONTROL Catalog]** > **[!UICONTROL Products]**&#x200B;に移動します。
1. シンプルな商品の作成。
1. 新しいバンドル製品を作成します。
1. SKUの中央にスラッシュマーク（`/`）を追加します（例：*Bu/ndle*）。
1. **[!UICONTROL Input Type]** = *[!UICONTROL Dropdown]*&#x200B;のバンドルオプションを追加します。
1. オプションに少なくとも1つのシンプルな製品を割り当てます。
1. **[!UICONTROL Sales]** > **[!UICONTROL Orders]**&#x200B;に移動し、新しい注文を作成します。
1. **[!UICONTROL Add Products by SKU]**&#x200B;をクリックします。
1. SKUを入力し、**[!UICONTROL Add to Order]**&#x200B;をクリックします。
1. ブラウザーコンソールを開きます。
1. **[!UICONTROL Configure]**&#x200B;をクリックします。

<u>期待される結果</u>:

エラーはありません。

<u>実際の結果</u>:

コンソールのJS エラー：

*エラー：構文エラー、認識できない式：div[id=sku_bu/ndle]*

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
