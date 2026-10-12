---
title: ACSD-49370:GraphQL スキーマでProduct属性に「FilterMatchTypeInput」タイプがある
description: ACSD-49370 パッチを適用して、GraphQL スキーマでproduct属性に「FilterMatchTypeInput」タイプがあるAdobe Commerceの問題を修正します。
feature: Admin Workspace, Attributes, GraphQL, Products
role: Admin
exl-id: 05cc6db6-6ea6-4eb7-8dc0-fcb9f479fd89
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 76cfaac4-e563-56dd-8938-708bf8b84956
    internal-label: Attributes
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
subfeature_v2:
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
  - id: e396cff5-f586-484c-89f0-7f1da3308f92
    internal-label: GraphQL
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 6%
---
# ACSD-49370:GraphQL スキーマにProduct属性の型が`FilterMatchTypeInput`件あります

ACSD-49370 パッチは、product属性がGraphQL スキーマに`FilterMatchTypeInput`型を持つ問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.28がインストールされている場合に利用できます。 パッチ IDはACSD-49370です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.7 - 2.4.6

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

product属性は、GraphQL スキーマに`FilterMatchTypeInput` タイプがあります。

<u>複製する手順</u>:

1. *日付と時刻*&#x200B;の製品属性を作成します。

   * [!UICONTROL Type]: [!UICONTROL DateTime]
   * [!UICONTROL Default Label]: [!UICONTROL Date Time]
   * [!UICONTROL Use in Search]: [!UICONTROL Yes]
   * [!UICONTROL Visible in Advanced Search]: [!UICONTROL Yes]

1. `ProductAttributeFilterInput` タイプ定義の&#x200B;*GQL API* ドキュメントをクエリします。
1. 作成した属性の入力タイプを確認します。

<u>期待される結果</u>:

*Date Time*&#x200B;属性は、フィルター入力タイプ `FilterRangeTypeInput`を示します。

<u>実際の結果</u>:

*Date Time*&#x200B;属性は、フィルター入力タイプ `FilterMatchInputType`を示します。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) パッチを検索する」を参照してください。
