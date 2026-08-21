---
title: MDVA-36309：管理者グリッドで属性による製品検索が遅い
description: MDVA-36309 パッチは、管理者グリッドで製品の属性による検索が遅くなる問題を解決します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.3がインストールされている場合に利用できます。 パッチ IDはMDVA-36309です。 この問題は、Adobe Commerce 2.4.3で修正されています。
feature: Admin Workspace, Attributes, Products, Search
role: Admin
exl-id: fe23f129-15b4-4239-a699-4776587cc4b8
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 0%

---

# MDVA-36309：管理者グリッドで属性による製品検索が遅い

MDVA-36309 パッチは、管理者グリッドで製品の属性による検索が遅くなる問題を解決します。 このパッチは、[品質パッチツール （QPT） &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.3がインストールされている場合に使用できます。 パッチ IDはMDVA-36309です。 この問題は、Adobe Commerce 2.4.3で修正されています。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2 - 2.4.2-p2

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

属性による製品の検索は、管理者グリッドで遅くなります。

<u>複製する手順</u>:

検索可能な属性のタイプに応じて、さまざまな管理者グリッドで検索を実行します。

<u>期待される結果</u>:

検索は妥当な時間で行われます。

<u>実際の結果</u>:

検索には多くの時間がかかります。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：品質パッチをセルフサービスで提供するための新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [品質パッチツール &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを確認します。

QPTで使用可能な他のパッチについて詳しくは、「QPT[&#128279;](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-)で使用可能な パッチ」セクションを参照してください。
