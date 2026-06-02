---
title: 'ACSD-60538: [!UICONTROL All Store Views]で製品が無効になっている場合、属性が正しく表示されない'
description: Adobe Commerceの問題を修正するには、ACSD-60538 パッチを適用します。このパッチでは、*すべてのストアビュー*で商品が無効になっていて、特定のストアビューの範囲でのみ有効になっている場合、GraphQLのレスポンスに商品属性が正しく表示されず、商品が正しく表示されません。
feature: Attributes, GraphQL
role: Admin, Developer
exl-id: 2ea9de11-b750-4ab6-9cc7-e940e1791f22
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '511'
ht-degree: 0%

---

# ACSD-60538: *[!UICONTROL All Store Views]*&#x200B;で製品が無効になっている場合、属性が正しく表示されない

ACSD-60538 パッチでは、*[!UICONTROL All Store Views]*&#x200B;で商品が無効になっていて、特定のストアビュースコープでのみ有効になっている場合、GraphQLのレスポンスで商品属性が正しく表示されず、商品が正しく表示されない問題が修正されました。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.51がインストールされている場合に利用できます。 パッチ IDはACSD-60538です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p1

**Adobe Commerceのバージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方法） 2.4.7 - 2.4.7-p2

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

*[!UICONTROL All Store Views]*&#x200B;で商品が無効になっていて、特定のストアビュースコープでのみ有効になっている場合、GraphQLのレスポンスに商品属性が正しく表示されず、商品が正しく表示されません。

<u>前提条件</u>:

インベントリモジュールがインストールされている。

<u>複製する手順</u>:

1. *color*&#x200B;属性と3つの子商品（*blue*、*black*、および&#x200B;*brown*）を持つ設定可能な商品を作成します。
1. *[!UICONTROL All Store Views]* スコープの2つの関連する子製品（*blue*&#x200B;および&#x200B;*black*）を無効にします。
1. **[!UICONTROL Store View]** スコープに移動します。
1. *[!UICONTROL Store View]*&#x200B;のスコープで子製品（*青*&#x200B;および&#x200B;*黒*）を有効にします。
1. 以下のGraphQL リクエストを実行します。

   ```GraphQL
   {
     products(filter: { sku: { eq: "SKU" } }) {
       items {
           ... on ConfigurableProduct {
             configurable_options {
               attribute_id,
               attribute_code,
            values {
             value_index
             label
           }
       }
       variants {
         product {
           sku
         }
         attributes {
           label
           code
           value_index
          }
         }
        }
       }
      }
     }  
   ```

<u>期待される結果</u>:

GraphQLの応答には、*[!UICONTROL All Store Views]*&#x200B;で無効になり、*[!UICONTROL Store View]* スコープで有効になっている子に関連付けられた製品の属性値が含まれます。

<u>実際の結果</u>:

*[!UICONTROL All Store Views]*&#x200B;で製品が無効になり、*[!UICONTROL Store View]* スコープで製品が有効になっている場合、GraphQLの応答に関連付けられた子製品の属性値が空になります。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) パッチを検索する」を参照してください。
