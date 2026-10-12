---
title: 'MDVA-27239: クロスセル製品が表示されない'
description: MDVA-27239 パッチは、クロスセル製品が表示されない問題を修正します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.7がインストールされている場合に利用できます。 この問題は、Adobe Commerce 2.3.6で修正されています。
feature: Products
role: Admin
exl-id: ab8fe64d-adbe-4756-be43-1a35ba6b4123
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%
---
# MDVA-27239: クロスセル製品が表示されない

MDVA-27239 パッチは、クロスセル製品が表示されない問題を修正します。 このパッチは、[品質パッチツール （QPT） ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.7がインストールされている場合に使用できます。 この問題は、Adobe Commerce 2.3.6で修正されています。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

Adobe Commerce（すべてのデプロイメント方法） 2.3.4、2.4.0

**Adobe Commerceのバージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方式） 2.3.0 - 2.3.5-p2、2.4.0 - 2.4.0-p1

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

クロスセル商品は、ショッピングカートページのクロスセルブロックには表示されません。

<u>前提条件</u>:

1. Magento_TargetRule モジュールを無効にするか、レイアウトブロック Magento\TargetRule\Block\Checkout\Cart\Crosssellから削除します。
1. 商品を作成する1.
1. 製品1のスケジュール更新を作成して、新しく作成した製品のrow_idがentity_idと異なるようにします。
1. 製品2、製品3、製品4を作成します。
1. 製品3を製品4のクロスセルとして設定します。
1. Product 4をProduct 2のクロスセルとして設定します。

<u>複製する手順</u>:

1. 商品4と商品2をショッピングカートに追加します。
1. ショッピングカートのページをご覧ください。

<u>期待される結果</u>:

商品3がクロスセルブロックに表示されます。

<u>実際の結果</u>:

クロスセル ブロックが空です。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [品質パッチツール ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
