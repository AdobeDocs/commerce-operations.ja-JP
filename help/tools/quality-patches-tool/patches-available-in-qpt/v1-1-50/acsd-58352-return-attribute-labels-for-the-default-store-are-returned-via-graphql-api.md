---
title: 'ACSD-58352: デフォルトストアの属性ラベルを[!DNL GraphQL] APIを介して返す'
description: デフォルト以外のストアビューがリクエストヘッダーで指定されている場合、デフォルトのストアの戻り属性ラベルが[!DNL GraphQL] APIを介して返されるAdobe Commerceの問題を修正するには、ACSD-58352 パッチを適用します。
feature: GraphQL, Returns
role: Admin, Developer
exl-id: e513039e-42cd-4dac-963b-3068ba8bf7ee
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: ac07462c-732c-5c1c-947b-4ce533b4fcfb
    internal-label: Returns
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
source-wordcount: '417'
ht-degree: 0%
---
# ACSD-58352: デフォルトストアの属性ラベルを[!DNL GraphQL] APIを介して返す

ACSD-58352 パッチは、リクエストヘッダーでデフォルト以外のストアビューが指定されている場合に、デフォルトストアの戻り属性ラベルが[!DNL GraphQL] APIを介して返される問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.50がインストールされている場合に利用できます。 パッチ IDはACSD-58352です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

デフォルトストアの属性ラベルを[!DNL GraphQL] APIを介して返します。

<u>複製する手順</u>:

1. **[!UICONTROL Return Merchandising Authorization]**&#x200B;を有効にします。
1. 既定のWeb サイトの下に&#x200B;*[!UICONTROL Additional Store]*&#x200B;と&#x200B;*[!UICONTROL Store View]*&#x200B;を作成します。
1. **[!UICONTROL Reason for Return]**&#x200B;の戻り値の属性を編集し、すべてのストアビューのラベルを追加します。
1. *[!UICONTROL Order]*&#x200B;を作成します。
1. その注文の&#x200B;*[!UICONTROL Return]*&#x200B;を作成します。 *[!UICONTROL Return]*&#x200B;のステータスが&#x200B;*[!UICONTROL Pending]*&#x200B;であることを確認してください。
1. ヘッダーにデフォルト以外の[!UICONTROL Store View]が指定された顧客[!DNL GraphQL] クエリを送信します。

   ```graphql
   query {
       customer {
           returns {
               items {
                   items {
                       custom_attributes {
                           label
                           value
                       }
                   }
               }
           }
       }
   }
   ```

1. 応答を観察します。

<u>期待される結果</u>

[!DNL GraphQL]応答の戻り値ラベルは、リクエストヘッダーに設定された[!UICONTROL Store View]に対するものです。

<u>実際の結果</u>:

[!DNL GraphQL]応答の戻り値ラベルは、デフォルトの[!UICONTROL Store View]用です。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
