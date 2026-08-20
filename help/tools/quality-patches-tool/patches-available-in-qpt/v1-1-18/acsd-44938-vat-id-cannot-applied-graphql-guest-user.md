---
title: 'ACSD-44938: ゲストユーザーの [!DNL GraphQL]  リクエストでVAT_IDを適用できない'
description: ACSD-44938 パッチは、ゲストユーザーの [!DNL GraphQL]  リクエストで「VAT_ID」を適用できない問題を修正します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.18がインストールされている場合に利用できます。 パッチ IDはACSD-44938です。 この問題は、Adobe Commerce 2.4.6で修正される予定です。
feature: Admin Workspace, GraphQL
role: Admin
exl-id: 62d36c27-545a-4c32-be69-a92e4b3ca2ca
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 0%

---

# ACSD-44938: ゲストユーザーの[!DNL GraphQL] リクエストでVAT_IDを適用できない

ACSD-44938 パッチは、ゲストユーザーの[!DNL GraphQL] リクエストで`VAT_ID`を適用できない問題を修正します。 このパッチは、[品質パッチツール（QPT） &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.18がインストールされている場合に使用できます。 パッチ IDはACSD-44938です。 この問題は、Adobe Commerce 2.4.6で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.0 - 2.4.3-p3

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

`VAT_ID`は、ゲストユーザーの[!DNL GraphQL] リクエストに適用できません。

<u>複製する手順</u>:

1. ゲストカートを作成するには、開発者ドキュメントの[[!DNL GraphQL]  チュートリアル &#x200B;](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/)に記載されている手順に従います。
1. [!DNL GraphQL]を使用して、ゲストユーザーに`VAT_ID`を適用してみてください。

<u>期待される結果</u>:

`VAT_ID`は、登録済みの顧客と同じように適用できます。 開発者用ドキュメントの[`createCustomerAddress`の変異](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/mutations/create-address/)の記事を参照してください。

<u>実際の結果</u>:

`VAT_ID`は、[!DNL GraphQL]を使用するゲスト ユーザーに適用できません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [品質パッチツール &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) パッチを検索する」を参照してください。
