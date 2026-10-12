---
title: 'ACSD-57854: *GraphQL*応答に、カテゴリ集計にリストされない無効なカテゴリが含まれています'
description: ACSD-57854 パッチを適用して、*GraphQL*応答にカテゴリ集計にリストされない無効なカテゴリが含まれているAdobe Commerceの問題を修正します。
feature: GraphQL
role: Admin, Developer
exl-id: 216aad2a-f470-49f9-b8ca-79107ca07891
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
source-wordcount: '401'
ht-degree: 0%
---
# ACSD-57854: *GraphQL*&#x200B;応答に、カテゴリ集計にリストされない無効なカテゴリが含まれています

ACSD-57854 パッチは、*GraphQL*&#x200B;応答に、カテゴリ集計にリストされない無効なカテゴリが含まれている問題を修正します。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.48がインストールされている場合に利用できます。 パッチ IDはACSD-57854です。 この問題は、Adobe Commerce 2.5.0で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5 - 2.4.6-p4

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

*GraphQL*&#x200B;の応答に、カテゴリ集計に表示しない無効なカテゴリが含まれています。

<u>複製する手順</u>:

1. 2つのカテゴリを作成します。
1. 商品を作成し（Test Adobe Product）、両方のカテゴリに商品を割り当てます。
1. 作成されたカテゴリの1つを無効にします。
1. 商品&#x200B;*GraphQL*&#x200B;を使用して商品を検索します。
1. *GraphQL*&#x200B;回答の商品カテゴリの一覧を確認してください。

<u>期待される結果</u>:

無効なカテゴリは、*GraphQL*&#x200B;の応答に一覧表示されません。

<u>実際の結果</u>:

無効なカテゴリは、カテゴリ集計&#x200B;*GraphQL*&#x200B;応答に一覧表示されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
