---
title: ACSD-52202：初期設定の在庫販売可能数量が、初期設定の在庫以外の在庫を順番に0数量に設定すると、エラーで0に変更される
description: ACSD-52202 パッチを適用して、注文でデフォルト以外の在庫が0数量に設定されている場合にデフォルトの在庫販売可能数量が0に変わるAdobe Commerceの問題を修正します。
feature: Inventory, Products
role: Admin
exl-id: 2ba5cc3b-9774-49f6-948f-371ab3c0c9df
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---

# ACSD-52202：注文でデフォルト以外の在庫を0に設定すると、デフォルトの在庫販売可能数量が0に変更される

ACSD-52202 パッチでは、注文でデフォルト以外の在庫が0数量に設定されている場合に、デフォルトの在庫販売可能数量（qty）がエラーで0に変更される問題を修正します。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.35がインストールされている場合に利用できます。 パッチ IDはACSD-52202です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3 - 2.4.6-p1

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

注文でデフォルト以外の在庫が0に設定されている場合、デフォルトの在庫販売可能数量はエラーで0に変更されます。

<u>複製する手順</u>:

1. [!DNL Admin]にログインします。
1. **web サイト 2**&#x200B;を作成します。
1. カスタム **source2**&#x200B;を作成します。
1. カスタム **stock2**&#x200B;を作成します。
1. **source2**&#x200B;と&#x200B;**stock2**&#x200B;を&#x200B;**website1**&#x200B;に割り当て、デフォルトのソースと在庫をデフォルトのweb サイトに割り当てます。
1. シンプルな商品を作成し、デフォルトソースに&#x200B;**qty** = *10*&#x200B;を割り当て、**source2** ソースに&#x200B;**qty** = *1*&#x200B;を割り当てます。
1. **web サイト 2**&#x200B;の&#x200B;**qty** = *1*&#x200B;で注文します。
1. 請求書と配送を作成します。
1. 簡易商品&#x200B;**販売可能数量**&#x200B;を確認してください。

<u>期待される結果</u>:

**source2**&#x200B;の&#x200B;**販売可能数量** = *10*。

<u>実際の結果</u>:

両方のソースの&#x200B;**販売可能な数量** = *0*。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
