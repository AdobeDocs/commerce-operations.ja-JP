---
title: 'ACSD-66302: web サイトではなくストア IDでフィルタリングされたウィッシュリスト項目'
description: ACSD-66302 パッチを適用して、[!DNL GraphQL] リクエストでweb サイトではなくストア IDでウィッシュリスト項目がフィルタリングされるAdobe Commerceの問題を修正します。
feature: GraphQL
role: Admin, Developer
type: Troubleshooting
exl-id: c1a9eadc-0321-4f5c-ba82-533286a1f24f
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
source-wordcount: '395'
ht-degree: 0%
---
# ACSD-66302: web サイトではなくストア IDでフィルタリングされたウィッシュリスト項目

ACSD-66302 パッチは、[!DNL GraphQL]要求でweb サイトではなくストア IDでウィッシュリスト項目がフィルタリングされる問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69がインストールされている場合に利用できます。 パッチ IDはACSD-66302です。 この問題は、Adobe Commerce 2.4.9で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.8

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.8 - 2.4.8-p1

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

ウィッシュリストのアイテムが、web サイトではなくストア IDで誤ってフィルタリングされる。

<u>複製する手順</u>:

1. シンプルな商品の作成。
1. 追加のストアビューを作成します。
1. 管理画面で、**[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Wish List]** > **[!UICONTROL General Options]**&#x200B;に移動し、**[!UICONTROL Enable Multiple Wish Lists]**&#x200B;を`Yes`に設定します。
1. **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Web]** > **[!UICONTROL Url Options]**&#x200B;に移動し、**[!UICONTROL Add Store Code to Urls]**&#x200B;を`Yes`に設定します。
1. 顧客アカウントの作成。
1. [!DNL GraphQL] リクエストを使用して、顧客認証トークンを取得します。
1. 顧客としてログインします。
1. **[!UICONTROL Default Store View]**&#x200B;を選択し、商品をウィッシュリストに追加します。
1. ストア ビューを&#x200B;*テスト*&#x200B;に切り替えます。
1. 商品がウィッシュリストに引き続き表示されることを確認します（正しい動作）。
1. 次の[!DNL GraphQL] クエリを実行します。

   ```text
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

1. デフォルトのストアでクエリを実行します。製品は期待どおりに表示されます。
1. テストストアで同じクエリを実行します。製品は表示されません。

<u>期待される結果</u>:

[!DNL GraphQL]件のクエリを使用して、同じweb サイト内のすべてのストアビューに製品を表示する必要があります。

<u>実際の結果</u>:

ストアビューを切り替えると、商品がウィッシュリストから消える。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
