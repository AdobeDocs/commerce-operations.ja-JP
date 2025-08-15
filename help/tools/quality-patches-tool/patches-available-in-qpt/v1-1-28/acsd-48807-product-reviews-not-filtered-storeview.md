---
title: ACSD-48807：製品レビューが storereview でフィルタリングされない
description: ACSD-48807 パッチを適用すると、GraphQLを介した storereview で商品レビューがフィルタリングされないAdobe Commerceの問題が修正されます。
feature: Admin Workspace, Products
role: Admin
exl-id: ce2cf5a1-a650-4eaa-8caf-f34dd0111c36
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# ACSD-48807：製品レビューが storereview でフィルタリングされない

ACSD-48807 パッチは、商品レビューがGraphQLを介して storereview でフィルタリングされない問題を修正しました。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.28 がインストールされている場合に使用できます。 パッチ ID は ACSD-48807 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3-p1

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.1 ～ 2.4.6

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

商品レビューは、GraphQLを介した storereview でフィルタリングされません。

<u> 再現手順 </u>:

1. 追加の storereview を作成します。
1. 顧客アカウントを作成し、ログインします。
1. デフォルトの storreview で、商品のレビューを作成します。
1. 別のストアレビューに切り替えて、製品の別のレビューを作成します。
1. Adobe Commerce Admin で両方のレビューを承認します。
1. 顧客GraphQL クエリを送信して商品レビューを取得すると、ヘッダーの手順 1 で作成した storereview を指定できます。
1. 応答を確認します。

<u> 期待される結果 </u>:

指定した storreview の製品レビューのみが応答で返されます。

<u> 実際の結果 </u>:

両方のレビューが応答で返されます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[[!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html): Search for patches[!DNL Quality Patches Tool]」を参照してください。
