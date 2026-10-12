---
title: 'MDVA-40545: ページの最初のノードのみが取得されます'
description: MDVA-40545 パッチは、同じページに複数のノードがある場合でも、ページの最初のノードのみが取得される問題を解決します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.5がインストールされている場合に利用できます。 パッチ IDはMDVA-40545です。 この問題は、Adobe Commerce 2.4.4で修正される予定です。
feature: CMS, Cache
role: Admin
exl-id: f87344e9-5a63-4c38-af2b-1500ef053dec
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: ddbd0f6e-b569-5a04-8a70-55058777c373
    internal-label: CMS
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '487'
ht-degree: 0%
---
# MDVA-40545: ページの最初のノードのみが取得されます

MDVA-40545 パッチは、同じページに複数のノードがある場合でも、ページの最初のノードのみが取得される問題を解決します。 このパッチは、[品質パッチツール （QPT） ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.5がインストールされている場合に使用できます。 パッチ IDはMDVA-40545です。 この問題は、Adobe Commerce 2.4.4で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

同じページに複数のノードがある場合でも、ページの最初のノードのみが取得されます。

<u>複製する手順</u>:

1. 管理パネルで、**階層**&#x200B;に移動し、2つのメニュー項目/ノードを追加します。
1. 各ノードに同じCMS ページを追加します。
1. キャッシュをクリアし、フロントエンドを確認します。
1. 最初に追加されたサブメニューのリンクとパンくずリストを確認します。
1. 2番目に追加されたサブメニューのリンクとパンくずリストを確認します。

<u>期待される結果</u>:

2番目のサブメニューのパンくずリストとリンクは、2番目のノードに関連しています。

<u>実際の結果</u>:

2番目のサブメニューのパンくずリストとリンクは、最初のサブメニューと同じです。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [品質パッチツール ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、「QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-)で使用可能な[ パッチ」セクションを参照してください。
