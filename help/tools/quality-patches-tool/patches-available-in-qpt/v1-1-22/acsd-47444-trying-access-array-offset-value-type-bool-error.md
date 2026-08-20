---
title: 'ACSD-47444: PHP 7.4で既知の製品に対する特定の存在しないカテゴリパスにアクセスする際に_[!UICONTROL Trying to access array offset on value of type bool]_ エラーが発生する'
description: ACSD-47444 パッチを適用して、PHP 7.4で既知の製品に対する特定の非既存のカテゴリパスにアクセスする際に_[!UICONTROL Trying to access array offset on value of type bool]_ エラーが発生するAdobe Commerceの問題を修正します。
feature: Categories, Products
role: Admin
exl-id: 9f04ee28-d22c-4fdf-9228-e436abe973e8
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%

---

# ACSD-47444: PHP 7.4の既知の製品に対する特定の存在しないカテゴリーパスにアクセスする際に&#x200B;_[!UICONTROL Trying to access array offset on value of type bool]_&#x200B;エラーが発生しました

ACSD-47444 パッチは、PHP 7.4で既知の製品の特定の非既存のカテゴリパスにアクセスする際に&#x200B;_[!UICONTROL Trying to access array offset on value of type bool]_&#x200B;エラーが発生する問題を解決します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.22がインストールされている場合に利用できます。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました
* Adobe Commerce（すべてのデプロイメント方法） 2.4.2-p1

**Adobe Commerceのバージョンとの互換性：**
* Adobe Commerce（すべてのデプロイメント方法） 2.4.0 - 2.4.2-p2

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

PHP 7.4で、既知の製品に対する特定の存在しないカテゴリ パスにアクセスすると、次のエラーが発生します：_[!UICONTROL Trying to access array offset on value of type bool]_。

<u>前提条件</u>:

PHP 7.4。

<u>複製する手順</u>:

1. 「test」という名前の新しい製品を作成します。
1. **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL CATALOG]** > **[!UICONTROL Catalog]** > **[!UICONTROL Search Engine Optimization]** > set **[!UICONTROL Generate "category/product" URL Rewrites]** = _No_&#x200B;に移動します。
1. ストアフロントに移動し、../abc/test.htmlなどのURLにアクセスします（「abc」 – 存在しない必要があります）。

<u>期待される結果</u>:

404 ページ。

<u>実際の結果</u>:

500 エラー：

_[!UICONTROL Notice: Trying to access array offset on value of type bool in /app/code/Magento/CatalogUrlRewrite/Model/Storage/DynamicStorage.php on line 182]_

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce: [&#x200B; アップグレードとパッチ > パッチの適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) （開発者用ドキュメント）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) パッチを検索する」を参照してください。
