---
title: ACSD-47079：サブ製品の在庫ステータスが変更された場合、複合製品の在庫ステータスが更新されない
description: ACSD-47079 パッチを適用すると、REST API POST /rest/V1/inventory/source-items を介してサブプロダクトのストックステータスが変更された場合に、複合プロダクト（バンドル、グループ化、設定可能）のストックステータスが更新されないAdobe Commerceの問題が修正されます。
feature: Orders, Products
role: Admin
exl-id: f035f530-fae5-4b61-8af9-044f6ec02284
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# ACSD-47079：サブ製品の在庫ステータスが変更された場合、複合製品の在庫ステータスが更新されない

ACSD-47079 パッチは、REST API POST `/rest/V1/inventory/source-items` を介してサブプロダクトのストックステータスが変更された場合に、複合プロダクトのストックステータス（バンドル、グループ化、設定可能）が更新されない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.24 がインストールされている場合に使用できます。 パッチ ID は ACSD-47079 です。 この問題はAdobe Commerce 2.4.6 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.4-p2

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

サブプロダクトのストックステータスが REST API POST `/rest/V1/inventory/source-items` で変更された場合、複合プロダクトのストックステータス（バンドル、グループ化、設定可能）は更新されません。

<u> 再現手順 </u>:

1. 設定可能でバンドルされた、グループ化された製品を、それぞれに 1 つのシンプルな子製品で作成します。
1. **[!UICONTROL Out of Stock]** API 呼び出しを使用して、シンプルな各子製品のステータスを `source-items` に設定します。
1. 次に、親製品の在庫ステータスを確認します。

<u> 期待される結果 </u>:

親製品のステータスは [!UICONTROL Out of Stock] です。

<u> 実際の結果 </u>:

親製品のステータスは [!UICONTROL In Stock] です。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[[!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html): Search for patches[!DNL Quality Patches Tool]」を参照してください。
