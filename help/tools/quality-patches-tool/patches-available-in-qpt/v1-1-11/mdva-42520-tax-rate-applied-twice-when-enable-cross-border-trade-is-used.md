---
title: MDVA-42520:「国境を越えた取引を有効にする」が使用されている場合に2回適用される税率
description: MDVA-42520 パッチでは、**Enable Cross Border Trade**を使用すると税率が2回適用される問題が修正されています。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.11がインストールされている場合に利用できます。 パッチ IDはMDVA-42520です。 この問題は、Adobe Commerce 2.4.5で修正される予定です。
feature: Catalog Management, Orders, Taxes
role: Admin
exl-id: 34c101fd-3a47-4877-8a41-ccaeaa010969
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 42e094d8-211b-5acf-b52f-d8979151ab30
    internal-label: Taxes
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 0%
---
# MDVA-42520:「国境を越えた取引を有効にする」が使用されている場合に2回適用される税率

MDVA-42520 パッチでは、**クロスボーダー取引を有効にする**&#x200B;を使用すると、税率が2回適用される問題が修正されます。 このパッチは、[品質パッチツール（QPT） ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.11がインストールされている場合に使用できます。 パッチ IDはMDVA-42520です。 この問題は、Adobe Commerce 2.4.5で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

税率は、**越境取引を有効にする**&#x200B;が使用されている場合に2回適用されます。

<u>複製する手順</u>:

1. **会社**、**共有カタログ**&#x200B;および&#x200B;**見積**&#x200B;を有効にする
1. スクリーンショットに従って税金を設定します。 **クロスボーダー取引**&#x200B;を有効にしてください。

   ![国境を越えた取引オプションとレート計算を表示する税構成設定ページ ](/help/assets/tools/tax_settings_1.png){width="700"}

1. ドイツの税率（10%）。
1. 税率を適用する税ルールを作成します。
1. 会社とカスタム共有カタログを作成します。
1. 価格が100の商品を作成し、カスタム共有カタログに20%の価格割引で掲載します。
1. ドイツの住所を持つ顧客を作成し、それを会社に割り当てます
1. 顧客としてカードに10個の商品を追加します。
1. ショッピングカートに移動し、見積もりを依頼します。
1. バックエンドでこの見積もりを開き、さらに10%の割引を追加してみてください。

<u>期待される結果</u>:

見積の小計（税込み）および見積の大計（税込み） = 720 ドル

<u>実際の結果</u>:

見積の小計（税込み）および見積の大計（税込み） = 649.50 ドル。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [品質パッチツール ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
