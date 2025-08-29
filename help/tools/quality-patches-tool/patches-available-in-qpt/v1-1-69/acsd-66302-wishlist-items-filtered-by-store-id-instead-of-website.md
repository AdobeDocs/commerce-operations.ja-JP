---
title: ACSD-66302:Web サイトではなくストア ID でフィルターされたウィッシュリスト項目
description: ACSD-66302 パッチを適用すると、ウィッシュリストの項目が web サイトの in [!DNL GraphQL] requests ではなくストア ID でフィルタリングされるAdobe Commerceの問題が修正されます。
feature: GraphQL
role: Admin, Developer
type: Troubleshooting
exl-id: c1a9eadc-0321-4f5c-ba82-533286a1f24f
source-git-commit: bec27df19ce5d34be063dce3de74ffe253c3e8f4
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---

# ACSD-66302:Web サイトではなくストア ID でフィルターされたウィッシュリスト項目

ACSD-66302 パッチは、ウィッシュリストの項目が [!DNL GraphQL] リクエストで web サイトではなくストア ID でフィルタリングされる問題を修正しました。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69 がインストールされている場合に使用できます。 パッチ ID は ACSD-66302 です。 この問題はAdobe Commerce 2.4.9 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.8

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.8 - 2.4.8-p1

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

ウィッシュリストの項目が、web サイトではなくストア ID で誤ってフィルタリングされます。

<u> 再現手順 </u>:

1. シンプルな製品を作成します。
1. 追加の storereview を作成します。
1. 管理者で、**[!UICONTROL Stores]**/*[!UICONTROL Settings]*/**[!UICONTROL Configuration]**/**[!UICONTROL Customers]**/**[!UICONTROL Wish List]**/**[!UICONTROL General Options]** に移動し、**[!UICONTROL Enable Multiple Wish Lists]** を `Yes` に設定します。
1. **[!UICONTROL Stores]**/*[!UICONTROL Settings]*/**[!UICONTROL Configuration]**/**[!UICONTROL General]**/**[!UICONTROL Web]**/**[!UICONTROL Url Options]** に移動し、**[!UICONTROL Add Store Code to Urls]** を `Yes` に設定します。
1. 顧客アカウントを作成します。
1. [!DNL GraphQL] リクエストを使用して、顧客認証トークンを取得します。
1. 顧客としてログインします。
1. **[!UICONTROL Default Store View]** を選択して、ウィッシュリストに製品を追加します。
1. ストア表示を *テスト* に切り替えます。
1. その製品がウィッシュリストにまだ表示されていることを確認します（正しい動作）。
1. 次の [!DNL GraphQL] クエリを実行します。

   ```
   {
     customer {
       wishlists {
         id
         name
         items_count
         items_v2 {
           items {
             id
             product {
               uid
               name
               sku
             }
           }
         }
       }
     }
   }
   ```

1. デフォルトストアでクエリを実行します。製品が期待どおりに表示されます。
1. テストストアで同じクエリを実行します。製品が表示されません。

<u> 期待される結果 </u>:

製品は、[!DNL GraphQL] のクエリを使用して、同じ web サイト内のすべてのストアビューで表示される必要があります。

<u> 実際の結果 </u>:

ストアビューを切り替えると、商品がウィッシュリストから消える。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
