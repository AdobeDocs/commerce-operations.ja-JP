---
title: ACSD-58352：デフォルトストアの戻り値の属性ラベルは、 [!DNL GraphQL] API を使用して返されます
description: ACSD-58352 パッチを適用すると、リクエストヘッダーでデフォルト以外のストアビューが指定されている場合に、デフォルトストアの戻り属性ラベルが  [!DNL GraphQL] API を介して返されるAdobe Commerceの問題が修正されます。
feature: GraphQL, Returns
role: Admin, Developer
exl-id: e513039e-42cd-4dac-963b-3068ba8bf7ee
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 0%

---

# ACSD-58352：デフォルトストアの戻り値の属性ラベルは、[!DNL GraphQL] API を使用して返されます

ACSD-58352 パッチでは、リクエストヘッダーでデフォルト以外のストア表示が指定されている場合に、[!DNL GraphQL] API を介してデフォルトストアの戻り属性ラベルが返される問題を修正しています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.50 がインストールされている場合に使用できます。 パッチ ID は ACSD-58352 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

デフォルトストアの戻り値の属性ラベルは、API[!DNL GraphQL] 介して返されます。

<u> 再現手順 </u>:

1. **[!UICONTROL Return Merchandising Authorization]** を有効にします。
1. デフォルトの web サイトの下に、*[!UICONTROL Additional Store]* と *[!UICONTROL Store View]* を作成します。
1. **[!UICONTROL Reason for Return]** return 属性を編集し、すべてのストアビューのラベルを追加します。
1. *[!UICONTROL Order]* を作成します。
1. その注文の *[!UICONTROL Return]* を作成します。 *[!UICONTROL Return]* のステータスが *[!UICONTROL Pending]* であることを確認します。
1. ヘッダーに指定されたデフォルト以外の [!UICONTROL Store View] を含む Customer [!DNL GraphQL] クエリを送信します。

   ```
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

1. 応答を確認します。

<u> 期待される結果 </u>

[!DNL GraphQL] 応答の返信ラベルは、リクエストヘッダーで設定された [!UICONTROL Store View] に対するものです。

<u> 実際の結果 </u>:

応答の返 [!DNL GraphQL] ラベルはデフォルトの [!UICONTROL Store View] です。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)」を参照してください。
