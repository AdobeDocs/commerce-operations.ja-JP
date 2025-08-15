---
title: ACSD-65195:GraphQL「createCompany」ミューテーションが、必要なリージョンのない国に対してエラーを返す
description: ACSD-65195 パッチを適用すると、GraphQLの「createCompany」ミューテーションによって、地域を必要としない国でエラーがスローされるAdobe Commerceの問題を修正できます。
feature: B2B, Companies, GraphQL
role: Admin, Developer
exl-id: b9eed00c-26f2-47fe-b1a0-6b020527f0c1
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---

# ACSD-65195:GraphQL `createCompany` mutation が、必要なリージョンのない国に対してエラーを返す

ACSD-65195 パッチは、[!UICONTROL GraphQL] `createCompany` ミューテーションが地域を必要としない国に対してエラーをスローする問題を修正しました。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.63 がインストールされている場合に使用できます。 パッチ ID は ACSD-65195 です。 この問題はAdobe Commerce 2.4.9 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p3

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.6-p9、2.4.7 - 2.4.7-p4

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

地域が必要でない国に指定されている場合、[!UICONTROL GraphQL] `createCompany` ミューテーションはエラーを返します。

<u> 再現手順 </u>:

1. **[!UICONTROL B2B Companies]** を有効にします。
1. 必要のない国に対して、指定した地域フィールドを使用して `createCompany` [!UICONTROL GraphQL] ミューテーションを送信します。 例：[!UICONTROL country_id]:*AE*、[!UICONTROL region]:*ドバイ*。
1. GraphQLの応答を確認します。

<u> 期待される結果 </u>:

会社は、地域を必要としない国に地域が指定されている場合、エラーを返さずに正常に作成される必要があります。

<u> 実際の結果 </u>:

会社が作成されず、次のエラーが返されます。
`Error: Invalid value of "Dubai" provided for the region field.`

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* Adobe Commerce on Cloud Infrastructure: アップグレードとパッチ > Commerce on Cloud Infrastructure ガイドのパッチの適用

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
