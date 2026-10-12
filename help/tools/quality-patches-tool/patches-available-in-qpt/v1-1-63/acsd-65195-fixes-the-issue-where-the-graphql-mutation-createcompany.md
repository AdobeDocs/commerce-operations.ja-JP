---
title: 'ACSD-65195: GraphQLの「createCompany」変異が、必須リージョンのない国のエラーを返す'
description: ACSD-65195 パッチを適用して、GraphQLの「createCompany」変異がリージョンを必要としない国でエラーをスローするAdobe Commerceの問題を修正します。
feature: B2B, Companies, GraphQL
role: Admin, Developer
exl-id: b9eed00c-26f2-47fe-b1a0-6b020527f0c1
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: e9004f3c-09ae-5d24-acd2-fa0987fdb66e
    internal-label: Companies
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
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
source-wordcount: '346'
ht-degree: 0%
---
# ACSD-65195: GraphQL `createCompany`の突然変異が、必須リージョンのない国のエラーを返します

ACSD-65195 パッチでは、地域を必要としない国で[!UICONTROL GraphQL] `createCompany`の突然変異がエラーをスローする問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.63がインストールされている場合に利用できます。 パッチ IDはACSD-65195です。 この問題は、Adobe Commerce 2.4.9で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p3

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方式） 2.4.4 - 2.4.6-p9、2.4.7 - 2.4.7-p4

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

[!UICONTROL GraphQL] `createCompany`の突然変異は、地域が必要のない国に対して指定されている場合にエラーを返します。

<u>複製する手順</u>:

1. **[!UICONTROL B2B Companies]**&#x200B;を有効にします。
1. 指定された地域フィールドを持つ`createCompany` [!UICONTROL GraphQL]の変異を、国が必要でない国に送信します。 例：[!UICONTROL country_id]: *AE*&#x200B;および[!UICONTROL region]: *ドバイ*。
1. GraphQLの応答を確認します。

<u>期待される結果</u>:

会社を必要としない国に地域を指定した場合、エラーを返さずに会社を正常に作成する必要があります。

<u>実際の結果</u>:

会社は作成されず、次のエラーが返されます。
`Error: Invalid value of "Dubai" provided for the region field.`

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* Adobe Commerce オンクラウドインフラストラクチャ：アップグレードとパッチ/パッチの適用については、Commerce オンクラウドインフラストラクチャガイドを参照してください。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
