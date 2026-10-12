---
title: ACSD-51238：設定可能な製品を更新し、価格を編集すると、在庫ソースが削除される
description: ACSD-51238 パッチを適用して、設定可能な商品を更新し、価格を編集する際に在庫源が削除されるAdobe Commerceの問題を修正します。
feature: Configuration, Inventory, Orders, Products
role: Admin
exl-id: 785f012f-e064-4ac6-b559-9e9aa42c679c
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: 8dc0e58b-adf0-51bb-8db5-bb36e3e656fb
    internal-label: Inventory
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
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
source-wordcount: '403'
ht-degree: 0%
---
# ACSD-51238：設定可能な製品を更新し、価格を編集すると、在庫ソースが削除される

ACSD-51238 パッチは、設定可能な製品を更新し、価格を編集する際に在庫源が削除される問題を修正します。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.32がインストールされている場合に利用できます。 パッチ IDはACSD-51238です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.6

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

設定可能な製品を更新し、価格を編集する際に、在庫ソースが削除されます。

<u>複製する手順</u>:

1. **[!DNL Adobe Commerce]**&#x200B;と&#x200B;**[!DNL Inventory module]**&#x200B;のインストール
1. **[!UICONTROL Admin]** -> **[!UICONTROL Stores]** -> **[!UICONTROL Inventory]**&#x200B;に移動し、*2つのソース*&#x200B;と&#x200B;*2つのストック*&#x200B;を作成します。
1. **[!UICONTROL configurable product]**&#x200B;を作成し、**[!UICONTROL default sources]**&#x200B;または&#x200B;**[!UICONTROL newly created sources]**&#x200B;に割り当てます。
1. 「**[!UICONTROL next button]**」をクリックし、製品を&#x200B;*保存*&#x200B;します。
1. 次に、同じ&#x200B;**[!UICONTROL Configurable Product]**&#x200B;を編集し、**[!UICONTROL Configuration tab]**&#x200B;内の&#x200B;**[!UICONTROL Edit Configuration]**&#x200B;をクリックします。
1. `Step 3: Bulk Images,Price and Quantity`で、`price`を変更し、`Quantity`と`Images`をそれぞれ`Skip quantity at this time`と`Skip image uploading at this time`に残します。
1. **[!UICONTROL next button]**&#x200B;をクリックして製品を生成します。

<u>期待される結果</u>

**[!UICONTROL Configuration tab]**&#x200B;内のソースあたりの数量は空にしないでください。

<u>実際の結果</u>

**[!UICONTROL Configuration tab]**&#x200B;内のソースあたりの数量が空です。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
