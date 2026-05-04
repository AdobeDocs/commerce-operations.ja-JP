---
title: 'ACSD-58352: デフォルトストアの属性ラベルを [!DNL GraphQL] APIを介して返す'
description: デフォルト以外のストアビューがリクエストヘッダーで指定されている場合、デフォルトのストアの戻り属性ラベルが [!DNL GraphQL] APIを介して返されるAdobe Commerceの問題を修正するには、ACSD-58352 パッチを適用します。
feature: GraphQL, Returns
role: Admin, Developer
exl-id: e513039e-42cd-4dac-963b-3068ba8bf7ee
type: Troubleshooting
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---

# ACSD-58352: デフォルトストアの属性ラベルを[!DNL GraphQL] APIを介して返す

ACSD-58352 パッチは、リクエストヘッダーでデフォルト以外のストアビューが指定されている場合に、デフォルトストアの戻り属性ラベルが[!DNL GraphQL] APIを介して返される問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.50がインストールされている場合に利用できます。 パッチ IDはACSD-58352です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

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
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
