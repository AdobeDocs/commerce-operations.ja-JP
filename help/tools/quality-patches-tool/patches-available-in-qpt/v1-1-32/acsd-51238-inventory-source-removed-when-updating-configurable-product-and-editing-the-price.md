---
title: ACSD-51238：設定可能な製品を更新し、価格を編集すると、在庫ソースが削除される
description: ACSD-51238 パッチを適用して、設定可能な商品を更新し、価格を編集する際に在庫源が削除されるAdobe Commerceの問題を修正します。
feature: Configuration, Inventory, Orders, Products
role: Admin
exl-id: 785f012f-e064-4ac6-b559-9e9aa42c679c
type: Troubleshooting
source-git-commit: 7054a5286f01e26e324401f4d8505e4e0faed93e
workflow-type: tm+mt
source-wordcount: '381'
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
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

設定可能な製品を更新し、価格を編集する際に、在庫ソースが削除されます。

<u>複製する手順</u>:

1. **[!DNL Adobe Commerce]**&#x200B;と&#x200B;**[!DNL Inventory module]**&#x200B;のインストール
1. **[!UICONTROL Admin]** -> **[!UICONTROL Stores]** -> **[!UICONTROL Inventory]**&#x200B;に移動し、*2つのソース*&#x200B;と&#x200B;*2つのストック*&#x200B;を作成します。
1. **[!UICONTROL configurable product]**&#x200B;を作成し、**[!UICONTROL default sources]**&#x200B;または&#x200B;**[!UICONTROL newly created sources]**&#x200B;に割り当てます。
1. 「**[!UICONTROL next button]**」をクリックし、製品を&#x200B;*保存*&#x200B;します。
1. 次に、同じ&#x200B;**[!UICONTROL Configurable Product]**&#x200B;を編集し、**[!UICONTROL Edit Configuration]**&#x200B;内の&#x200B;**[!UICONTROL Configuration tab]**&#x200B;をクリックします。
1. `Step 3: Bulk Images,Price and Quantity`で、`price`を変更し、`Quantity`と`Images`をそれぞれ`Skip quantity at this time`と`Skip image uploading at this time`に残します。
1. **[!UICONTROL next button]**&#x200B;をクリックして製品を生成します。

<u>期待される結果</u>

**[!UICONTROL Configuration tab]**&#x200B;内のソースあたりの数量は空にしないでください。

<u>実際の結果</u>

**[!UICONTROL Configuration tab]**&#x200B;内のソースあたりの数量が空です。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool]  ガイドの](/help/tools/quality-patches-tool/usage.md)>使用状況[!DNL Quality Patches Tool]。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [&#x200B; [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) ガイドの[!UICONTROL Quality Patches Tool]を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) ガイドの「[!DNL Quality Patches Tool] パッチを検索する」を参照してください。
