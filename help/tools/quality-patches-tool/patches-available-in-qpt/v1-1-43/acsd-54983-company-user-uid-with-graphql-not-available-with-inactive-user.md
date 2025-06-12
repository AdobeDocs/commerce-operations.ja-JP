---
title: ACSD-54983：非アクティブユーザーでGraphQLを使用できる会社ユーザーUIDがない
description: ユーザーステータスが非アクティブに設定されている場合、GraphQLを使用して会社のユーザーUID リクエストを取得できないAdobe Commerceの問題を修正するために ACSD-54983 パッチを適用します。
feature: GraphQL
role: Admin, Developer
exl-id: b188270f-5454-41c9-8370-f4c396095297
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 0%

---

# ACSD-54983：非アクティブユーザーでGraphQLを使用できる会社ユーザーUIDがない

ACSD-54983 パッチは、ユーザーステータスが非アクティブに設定されている場合、GraphQL リクエストを含んだ会社ユーザーのUIDを取得できない問題を修正しました。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.43 がインストールされている場合に使用できます。 パッチ ID は ACSD-54983 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p2

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2 ～ 2.4.6-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

ユーザーステータスが非アクティブに設定されている場合、GraphQL リクエストで会社ユーザーのUIDを取得できません。

<u> 再現手順 </u>:

1. 管理者ユーザーで会社を作成します。 例：company@test.com
1. 顧客を新規作成します。
1. 新しい顧客を会社に割り当てます。
1. **[!UICONTROL company admin token]** を入手してください。
1. **[!UICONTROL company admin token]** を使用して、会社構造を取得します。 開発者向けドキュメントの [ 会社構造を返す ](https://developer.adobe.com/commerce/webapi/graphql/schema/b2b/company/queries/company/#return-the-company-structure) を参照してください。
1. 応答には、ID を持つ *アクティブ* 顧客のみが含まれます。
1. 会社ユーザーを *非アクティブ* に更新します。
1. 会社構造を再度取得します。

<u> 期待される結果 </u>:

ステータスが非アクティブに設定されている場合は、会社ユーザーのUIDを取得できます。

<u> 実際の結果 </u>:

非アクティブな顧客はリストに含まれていません。 ステータスが非アクティブに設定されている場合、会社ユーザーのUIDを取得できません。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md)[!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)」を参照してください。
