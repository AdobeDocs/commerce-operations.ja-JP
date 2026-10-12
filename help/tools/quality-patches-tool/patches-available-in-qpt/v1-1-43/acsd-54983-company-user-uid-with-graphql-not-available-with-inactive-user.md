---
title: ACSD-54983:GraphQLを使用した会社ユーザーのUIDが、非アクティブユーザーでは使用できない
description: ユーザーのステータスが非アクティブに設定されている場合、Adobe Commerceの問題を修正するには、ACSD-54983 パッチを適用して、GraphQL リクエストで企業ユーザーのUIDを取得できない問題を修正します。
feature: GraphQL
role: Admin, Developer
exl-id: b188270f-5454-41c9-8370-f4c396095297
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
subfeature_v2:
  - id: e396cff5-f586-484c-89f0-7f1da3308f92
    internal-label: GraphQL
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 0%
---
# ACSD-54983:GraphQLを使用した会社ユーザーのUIDが、非アクティブユーザーでは使用できない

ACSD-54983 パッチでは、ユーザーステータスが非アクティブに設定されている場合に、GraphQL リクエストを使用して企業ユーザーのUIDを取得できない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.43がインストールされている場合に利用できます。 パッチ IDはACSD-54983です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

ユーザーステータスが非アクティブに設定されている場合、GraphQL リクエストを含む会社ユーザーのUIDを取得できません。

<u>複製する手順</u>:

1. 管理者ユーザーを持つ会社を作成します。 例：company@test.com
1. 新規顧客の作成：
1. 新規顧客を会社に割り当てます。
1. **[!UICONTROL company admin token]**&#x200B;を取得します。
1. **[!UICONTROL company admin token]**&#x200B;を使用して、会社構造を取得します。 開発者ドキュメントの[会社構造を返す](https://developer.adobe.com/commerce/webapi/graphql/schema/b2b/company/queries/company/#return-the-company-structure)を参照してください。
1. 応答には、IDを持つ&#x200B;*ACTIVE*&#x200B;人の顧客のみが含まれます。
1. 会社ユーザーを&#x200B;*INACTIVE*&#x200B;に更新します。
1. 会社構造を再度フェッチします。

<u>期待される結果</u>:

ステータスが非アクティブに設定されている場合は、会社ユーザーのUIDを取得できます。

<u>実際の結果</u>:

非アクティブな顧客はリストに含まれていません。 ステータスが非アクティブに設定されている場合、会社ユーザーのUIDを取得できません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) パッチを検索する」を参照してください。
