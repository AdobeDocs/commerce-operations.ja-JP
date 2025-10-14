---
title: ACSD-58446:GraphQLを使用してチームを子ユーザーまたはチームと削除すると、未情報のエラーメッセージが表示される
description: ACSD-58446 パッチを適用すると、GraphQLを介して子ユーザーまたはチームを持つチームを削除すると、UI に一致しない非情報エラーメッセージが返されるAdobe Commerceの問題が修正されます。
feature: GraphQL
role: Admin, Developer
exl-id: 943ab281-cc41-4b96-8a7c-fff8c074267c
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 0%

---

# ACSD-58446:GraphQLを使用してチームを子ユーザーまたはチームと削除すると、未情報のエラーメッセージが表示される

ACSD-58446 パッチは、GraphQLを介して子ユーザーまたはチームを持つチームを削除すると、UI と一致しない非情報エラーメッセージが返されるAdobe Commerceの問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.49 がインストールされている場合に使用できます。 パッチ ID は ACSD-58446 です。 この問題はAdobe Commerce B2B 1.5.1 で修正される予定です

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p4

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6 - 2.4.6-p7

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

GraphQLを使用してチームを子ユーザーまたはチームと削除すると、UI に一貫性のない非情報エラーメッセージが返される。

## 前提条件：

Adobe Commerce B2B モジュールがインストールされている。

<u> 再現手順 </u>:

1. *[!UICONTROL Company]* 機能を有効にします。
1. 新しい会社アカウントを作成します。
1. **[!UICONTROL Admin]** にログインし、会社アカウントをアクティブにします。
1. メールを確認し、新しい会社アカウントのパスワードを設定します。
1. 会社の新しいチームを作成します。
1. ストアフロントに会社ユーザーとしてログインし、作成したチームに新しいユーザーを追加します。
1. **[!UICONTROL Admin]** にログインし、会社ユーザーを無効にして、*[!UICONTROL Customer Active]* = *いいえ* を設定します
1. 作成したチームは必ずGraphQLから削除してください。

   ```
   mutation {
     deleteCompanyTeam(
       id: "MQ=="
     ) {
       success
     }
   }
   ```

<u> 期待される結果 </u>:

UI と一致する情報エラーメッセージが返されます。

<u> 実際の結果 </u>:

UI と一致しない、一般的な内部サーバーエラーメッセージが返されます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 &#x200B;](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [&#x200B; アップグレードとパッチ &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [&#x200B; を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[[!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja): Search for patches[!DNL Quality Patches Tool]」を参照してください。
