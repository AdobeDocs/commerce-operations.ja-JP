---
title: ACSD-47027：低速クエリ B2B [!UICONTROL CompanyRole] [!DNL GraphQL] update
description: ACSD-47027 パッチを適用して、クエリ B2B [!UICONTROL CompanyRole] [!DNL GraphQL] update が遅いAdobe Commerceの問題を修正してください。
feature: B2B, Companies, GraphQL, Roles/Permissions
role: Admin
exl-id: 91eb0297-1ba8-47b7-9581-29bee835843c
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# ACSD-47027：低速クエリ B2B [!UICONTROL CompanyRole] [!DNL GraphQL] の更新

ACSD-47027 パッチを使用すると、低速のクエリ B2B [!UICONTROL CompanyRole] [!DNL GraphQL] アップデートが期待どおりに動作しない問題を解決できます。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.23 がインストールされている場合に使用できます。 パッチ ID は ACSD-47027 です。 この問題はAdobe Commerce 2.4.6 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**
* Adobe Commerce（すべてのデプロイメント方法） 2.4.2-p1

**Adobe Commerce バージョンとの互換性：**
* Adobe Commerce（すべてのデプロイメント方法） 2.4.2 ～ 2.4.5-p1

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

低速のクエリ B2B [!UICONTROL CompanyRole] [!DNL GraphQL] の更新が期待どおりに動作しません。

<u> 前提条件 </u>:

B2B モジュールをインストールします。

<u> 再現手順 </u>:

1. Adobe Commerce管理者で、**[!UICONTROL Stores]** / **[!UICONTROL Settings]** / **[!UICONTROL Configurations]** / **[!UICONTROL B2B Features]** に移動し、「**[!UICONTROL Enable Company]**」を _はい_ に設定します。
1. フロントエンドに移動し、会社を作成します。
1. 会社ユーザーとしてログインしたら、**[!UICONTROL My Account]**/**[!UICONTROL Roles and Permissions]** に移動し、新しい役割を追加します。
1. `bin/magento dev:que:enab`[!UICONTROL dev] 使用してクエリログを有効にします。
1. 次に、以下の [!DNL GraphQL] リクエストを送信します（ID は [!UICONTROL base64] でエンコードされた役割 ID です）。

   <pre><code>
   mutation &lbrace;
   updateCompanyRole(
      input: &lbrace;
         id: "Mg=="
         permissions: &lbrack;
         "Magento_Company::view"
         "Magento_Company::view_account"
         "Magento_Company::user_management"
         "Magento_Company::roles_view"
        &rbrack;
      &rbrace;
    ) &lbrace;
      role &lbrace;
         id

         name

         permissions &lbrace;
         id

         text

         children &lbrace;
            id

            text

            children &lbrace;
               id

               text
             &rbrace;
           &rbrace;
         &rbrace;
       &rbrace;
     &rbrace;
   &rbrace;
   </code></pre>

1. クエリログを確認します。
1. 上記のクエリが実行されていることがわかります。 このクエリは `app/code/Magento/CompanyGraphQl/Model/Company/Role/ValidateRole.php::validateResources` で実行されます。

<u> 期待される結果 </u>:

**[!UICONTROL company_permissions]** DB テーブルで使用可能なすべてのデータを読み込まないように、`app/code/Magento/CompanyGraphQl/Model/Company/Role/ValidateRole.php::validateResources` を最適化する必要があります。

<u> 実際の結果 </u>:

Adobe Commerceは、フィルターなしでクエリを実行します。 レコード数が多い場合、Adobe Commerceでのデータ収集の準備に多くの時間がかかります。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。 

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)」を参照してください。
