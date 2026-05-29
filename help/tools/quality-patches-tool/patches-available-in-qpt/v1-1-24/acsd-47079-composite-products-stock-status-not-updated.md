---
title: ACSD-47079：サブ製品在庫状況が変更された場合、複合製品の在庫状況が更新されない
description: REST API POST /rest/V1/inventory/source-itemsを介してサブ商品の在庫ステータスが変更された場合、複合商品（バンドル、グループ化、設定可能）の在庫ステータスが更新されないAdobe Commerceの問題を修正するには、ACSD-47079 パッチを適用します。
feature: Orders, Products
role: Admin
exl-id: f035f530-fae5-4b61-8af9-044f6ec02284
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 0%

---

# ACSD-47079：サブ製品在庫状況が変更された場合、複合製品の在庫状況が更新されない

ACSD-47079 パッチは、REST API POST `/rest/V1/inventory/source-items`を介してサブ製品在庫ステータスが変更されたときに、複合製品の在庫ステータス（バンドル、グループ化、設定可能）が更新されない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.24がインストールされている場合に利用できます。 パッチ IDはACSD-47079です。 この問題は、Adobe Commerce 2.4.6で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.4-p2

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

REST API POST `/rest/V1/inventory/source-items`を使用してサブ製品在庫ステータスを変更すると、複合製品（バンドル、グループ化、設定可能）の在庫ステータスが更新されません。

<u>複製する手順</u>:

1. 各製品に1つのシンプルな子製品を持つ、設定可能、バンドル、グループ化された製品を作成します。
1. `source-items` API呼び出しを使用して、各単純な子製品のステータスを&#x200B;**[!UICONTROL Out of Stock]**&#x200B;に設定します。
1. 次に、親製品の在庫状況を確認します。

<u>期待される結果</u>:

親製品の状態は[!UICONTROL Out of Stock]です。

<u>実際の結果</u>:

親製品の状態は[!UICONTROL In Stock]です。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
