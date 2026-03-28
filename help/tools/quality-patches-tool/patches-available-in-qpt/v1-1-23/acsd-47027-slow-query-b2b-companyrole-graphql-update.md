---
title: ACSD-47027：遅いクエリ B2B [!UICONTROL CompanyRole] [!DNL GraphQL] 更新
description: ACSD-47027 パッチを適用して、クエリ B2B [!UICONTROL CompanyRole] [!DNL GraphQL] の更新が遅いAdobe Commerceの問題を修正します。
feature: B2B, Companies, GraphQL, Roles/Permissions
role: Admin
exl-id: 91eb0297-1ba8-47b7-9581-29bee835843c
type: Troubleshooting
source-git-commit: 7054a5286f01e26e324401f4d8505e4e0faed93e
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# ACSD-47027：遅いクエリ B2B [!UICONTROL CompanyRole] [!DNL GraphQL]の更新

ACSD-47027 パッチは、低速なクエリ B2B [!UICONTROL CompanyRole] [!DNL GraphQL]の更新が期待どおりに機能しない問題を解決します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.23がインストールされている場合に利用できます。 パッチ IDはACSD-47027です。 この問題は、Adobe Commerce 2.4.6で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました
* Adobe Commerce（すべてのデプロイメント方法） 2.4.2-p1

**Adobe Commerceのバージョンとの互換性：**
* Adobe Commerce（すべてのデプロイメント方法） 2.4.2 - 2.4.5-p1

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

低速のクエリ B2B [!UICONTROL CompanyRole] [!DNL GraphQL]の更新が期待どおりに機能しません。

<u>前提条件</u>:

B2B モジュールをインストールします。

<u>複製する手順</u>:

1. Adobe Commerce管理者で、**[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configurations]** > **[!UICONTROL B2B Features]**&#x200B;に移動し、**[!UICONTROL Enable Company]**&#x200B;を&#x200B;_Yes_&#x200B;に設定します。
1. フロントエンドに移動し、会社を作成します。
1. 会社ユーザーとしてログインした後、**[!UICONTROL My Account]** > **[!UICONTROL Roles and Permissions]**&#x200B;に移動し、新しい役割を追加します。
1. [!UICONTROL dev]を使用して`bin/magento dev:que:enab` クエリ ログを有効にします。
1. 次に、以下の[!DNL GraphQL] リクエストを送信します（IDは[!UICONTROL base64] エンコードされた役割ID）。

   ```
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

`app/code/Magento/CompanyGraphQl/Model/Company/Role/ValidateRole.php::validateResources` DB テーブルで使用可能なすべてのデータを読み込まないように、**[!UICONTROL company_permissions]**&#x200B;を最適化する必要があります。

<u>実際の結果</u>:

Adobe Commerceは、フィルターなしでクエリを実行します。 レコード数が多い場合、Adobe Commerceでデータ収集の準備を行うには多くの時間がかかります。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool]  ガイドの](/help/tools/quality-patches-tool/usage.md)>使用状況[!DNL Quality Patches Tool]。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。 

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [ [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) ガイドの[!UICONTROL Quality Patches Tool]を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) ガイドの「[!DNL Quality Patches Tool] パッチを検索する」を参照してください。
