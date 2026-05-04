---
title: ACSD-58446:GraphQLを介して子ユーザーまたは子チームを含むチームを削除すると、情報のないエラーメッセージが表示される
description: ACSD-58446 パッチを適用して、GraphQLを介して子ユーザーまたはグループを持つチームを削除すると、UIと一致しない情報のないエラーメッセージが返されるAdobe Commerceの問題を修正します。
feature: GraphQL
role: Admin, Developer
exl-id: 943ab281-cc41-4b96-8a7c-fff8c074267c
type: Troubleshooting
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 0%

---

# ACSD-58446:GraphQLを介して子ユーザーまたは子チームを含むチームを削除すると、情報のないエラーメッセージが表示される

ACSD-58446 パッチでは、GraphQLを介して子ユーザーまたはグループを持つチームを削除すると、UIと一致しない情報のないエラーメッセージが返されるAdobe Commerceの問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.49がインストールされている場合に利用できます。 パッチ IDはACSD-58446です。 この問題は、Adobe Commerce B2B 1.5.1で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p4

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6 - 2.4.6-p7

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

GraphQLを使用して子ユーザーまたはグループを持つグループを削除すると、UIと一致しない情報のないエラーメッセージが返されます。

## 前提条件：

Adobe Commerce B2B モジュールの導入：

<u>複製する手順</u>:

1. *[!UICONTROL Company]*&#x200B;機能を有効にします。
1. 新しい会社アカウントを作成します。
1. **[!UICONTROL Admin]**&#x200B;にログインし、会社アカウントをアクティブにします。
1. メールを確認し、新しい会社アカウントのパスワードを設定します。
1. 会社の新しいチームを作成します。
1. ストアフロントの会社ユーザーとしてログインし、作成したチームの新しいユーザーを追加します。
1. **[!UICONTROL Admin]**&#x200B;にログインし、会社ユーザーを無効にし、*[!UICONTROL Customer Active]* = *No*&#x200B;を設定します
1. 作成したチームをGraphQL経由で削除してください。

   ```graphql
   mutation {
     deleteCompanyTeam(
       id: "MQ=="
     ) {
       success
     }
   }
   ```

<u>期待される結果</u>:

UIと一致する有益なエラーメッセージが返されます。

<u>実際の結果</u>:

UIと一致しない一般的な内部サーバーエラーメッセージが返されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
