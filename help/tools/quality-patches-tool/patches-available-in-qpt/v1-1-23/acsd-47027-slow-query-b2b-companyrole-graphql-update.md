---
title: ACSD-47027：遅いクエリ B2B [!UICONTROL CompanyRole] [!DNL GraphQL]の更新
description: ACSD-47027 パッチを適用して、クエリ B2B [!UICONTROL CompanyRole] [!DNL GraphQL]の更新が遅いAdobe Commerceの問題を修正します。
feature: B2B, Companies, GraphQL, Roles/Permissions
role: Admin
exl-id: 91eb0297-1ba8-47b7-9581-29bee835843c
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: e9004f3c-09ae-5d24-acd2-fa0987fdb66e
    internal-label: Companies
  - id: e439352c-5b67-587d-b34e-d2a0aa5a0242
    internal-label: Roles/Permissions
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
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%
---
# ACSD-47027：遅いクエリ B2B [!UICONTROL CompanyRole] [!DNL GraphQL]の更新

ACSD-47027 パッチは、低速なクエリ B2B [!UICONTROL CompanyRole] [!DNL GraphQL]の更新が期待どおりに機能しない問題を解決します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.23がインストールされている場合に利用できます。 パッチ IDはACSD-47027です。 この問題は、Adobe Commerce 2.4.6で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました
* Adobe Commerce（すべてのデプロイメント方法） 2.4.2-p1

**Adobe Commerceのバージョンとの互換性：**
* Adobe Commerce（すべてのデプロイメント方法） 2.4.2 - 2.4.5-p1

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

低速のクエリ B2B [!UICONTROL CompanyRole] [!DNL GraphQL]の更新が期待どおりに機能しません。

<u>前提条件</u>:

B2B モジュールをインストールします。

<u>複製する手順</u>:

1. Adobe Commerce管理者で、**[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configurations]** > **[!UICONTROL B2B Features]**&#x200B;に移動し、**[!UICONTROL Enable Company]**&#x200B;を&#x200B;_Yes_&#x200B;に設定します。
1. フロントエンドに移動し、会社を作成します。
1. 会社ユーザーとしてログインした後、**[!UICONTROL My Account]** > **[!UICONTROL Roles and Permissions]**&#x200B;に移動し、新しい役割を追加します。
1. `bin/magento dev:que:enab`を使用して[!UICONTROL dev] クエリ ログを有効にします。
1. 次に、以下の[!DNL GraphQL] リクエストを送信します（IDは[!UICONTROL base64] エンコードされた役割ID）。

   ```graphql
   mutation {
   updateCompanyRole(
      input: {
         id: "Mg=="
         permissions: [
         "Magento_Company::view"
         "Magento_Company::view_account"
         "Magento_Company::user_management"
         "Magento_Company::roles_view"
        ]
      }
    ) {
      role {
         id
   
         name
   
         permissions {
         id
   
         text
   
         children {
            id
   
            text
   
            children {
               id
   
               text
             }
           }
         }
       }
     }
   }
   ```

1. クエリログを確認します。
1. 上記のクエリが実行されます。 このクエリは`app/code/Magento/CompanyGraphQl/Model/Company/Role/ValidateRole.php::validateResources`で実行されます。

<u>期待される結果</u>:

**[!UICONTROL company_permissions]** DB テーブルで使用可能なすべてのデータを読み込まないように、`app/code/Magento/CompanyGraphQl/Model/Company/Role/ValidateRole.php::validateResources`を最適化する必要があります。

<u>実際の結果</u>:

Adobe Commerceは、フィルターなしでクエリを実行します。 レコード数が多い場合、Adobe Commerceでデータ収集の準備を行うには多くの時間がかかります。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。 

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) パッチを検索する」を参照してください。
