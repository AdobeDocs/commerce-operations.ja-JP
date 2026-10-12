---
title: ACSD-51230：ギフトカードアカウントが削除される
description: ACSD-51230 パッチを適用して、注文から製品の部分的な払い戻しを処理する際にギフトカードのアカウントが削除されるAdobe Commerceの問題を修正します。
feature: Customer Service, Gift, Marketing Tools
role: Admin
exl-id: a4aed574-3908-42e0-ac32-911f61b44995
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4fc0a729-4349-5307-bd06-1b4bfbaf5d0c
    internal-label: Gift
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
  - id: da76473c-f99b-5ad0-9b14-896aed473f8a
    internal-label: Services
subfeature_v2:
  - id: deedbb4d-f1b7-58ea-a34a-de1f481f9d4c
    internal-label: Customer Service
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
# ACSD-51230：ギフトカードアカウントが削除される

ACSD-51230 パッチは、注文から製品の部分的な払い戻しを処理する際に、ギフトカードのアカウントが削除される問題を修正します。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.32がインストールされている場合に利用できます。 パッチ IDはACSD-51230です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.7 - 2.4.6

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

ギフトカードのアカウントは、注文から製品の部分的な払い戻しが処理されると削除されます。

<u>複製する手順</u>:

1. *ギフトカード*&#x200B;と&#x200B;*シンプルな商品*&#x200B;を使用して注文を作成します（例：*追加：SKU: GI000XX000XXX、SKU: PC046CP042076*） – （支払いと配送方法は機能します）。
1. 注文の請求書を作成します。
1. **[!UICONTROL Marketing]** > **[!UICONTROL Gift Card accounts]**&#x200B;に移動します。 ギフトカードのアカウントが作成されます。
1. 次に&#x200B;**[!UICONTROL Order]**&#x200B;に移動し、**[!UICONTROL Credit Memo]**&#x200B;を作成します。
1. *ギフトカード*&#x200B;の数量を0に変更して更新します。 これにより、*シンプル製品*&#x200B;の部分的な払い戻しが行われます。
1. **[!UICONTROL Refund]**&#x200B;をクリックします。
1. 次に、**[!UICONTROL Marketing]** > **[!UICONTROL Gift Card accounts]**&#x200B;を更新します。 新しく作成したアカウントが削除されます。

<u>期待される結果</u>

払い戻しはギフトカードに対して作成されていないため、ギフトカードアカウントを使用できます。

<u>実際の結果</u>

ギフトカードのアカウントは削除され、ギフトカードは返金されません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
