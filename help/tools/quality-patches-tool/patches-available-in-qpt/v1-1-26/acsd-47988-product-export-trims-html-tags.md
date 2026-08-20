---
title: ACSD-47988：製品の書き出しにより、ページビルダーからHTML タグがトリミングされる製品説明
description: ACSD-47988 パッチを適用して、製品エクスポートがページビルダー製品の説明からHTML タグをトリミングするAdobe Commerceの問題を修正します。
feature: Admin Workspace, Data Import/Export, Page Builder, Products
role: Admin
exl-id: 2cb3b4ac-38df-4832-b894-b34bb3d7bbc6
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# ACSD-47988：製品の書き出しにより、ページビルダーからHTML タグがトリミングされる製品説明

ACSD-47988 パッチでは、製品エクスポートでページビルダー製品の説明からHTML タグがトリミングされる問題が修正されています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.26がインストールされている場合に利用できます。 パッチ IDはACSD-47988です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.7 - 2.4.6

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

商品の書き出しは、ページビルダーの商品説明からHTML タグをトリミングします。

<u>複製する手順</u>:

1. 説明にHTMLを使用して商品を作成します。 ページビルダーのHTML エレメントを使用して、HTML タグを挿入します。
1. Adobe Commerceの読み込み/書き出し機能を使用して、商品を書き出します。
1. 書き出したCSVを読み込みます。
1. 製品を開き、説明の下のHTML要素を確認します。

<u>期待される結果</u>:

同じ内容を読み込んだ後も、HTML タグは商品説明に残ります。

<u>実際の結果</u>:

HTML タグは、読み込み後に削除されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
