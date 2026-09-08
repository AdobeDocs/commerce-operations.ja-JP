---
title: 'ACSD-65195: GraphQLの「createCompany」変異が、必須リージョンのない国のエラーを返す'
description: ACSD-65195 パッチを適用して、GraphQLの「createCompany」変異がリージョンを必要としない国でエラーをスローするAdobe Commerceの問題を修正します。
feature: B2B, Companies, GraphQL
role: Admin, Developer
exl-id: b9eed00c-26f2-47fe-b1a0-6b020527f0c1
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
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
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

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

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
