---
title: 'ACSD-62212: [!UICONTROL Forgot Password] メールがストアビュー言語に翻訳されていません'
description: ACSD-62212 パッチを適用して、*[!UICONTROL Forgot Password]*電子メールの内容がストアビューの言語に翻訳されないAdobe Commerceの問題を修正します。
feature: GraphQL
role: Admin, Developer
exl-id: 29e6f2fa-574f-4ab1-82f5-88e1eb1de83e
type: Troubleshooting
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 0%

---

# ACSD-62212: *[!UICONTROL Forgot Password]* メールがストアビュー言語に翻訳されていません

ACSD-62212 パッチは、*[!UICONTROL Forgot Password]*&#x200B;電子メールのコンテンツがストアビュー言語に翻訳されない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ja) 1.1.57がインストールされている場合に利用できます。 パッチ IDはACSD-62212です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

登録済み以外のストアビューでGraphQLを介してパスワードをリセットする際、パスワードのリセットのリンクは、開始されたストアビューと一致しません。

<u>複製する手順</u>:

1. *[!UICONTROL Main Website Store]*&#x200B;の下にセカンダリストアビューを作成します。
1. セカンダリ ストア ビューのスコープで&#x200B;*[!UICONTROL Locale]*&#x200B;を&#x200B;*[!UICONTROL French (France)]*&#x200B;に切り替えます。
1. フランス語の翻訳パックをインストールします。
1. 顧客アカウントの作成。
1. セカンダリストアビューコードで&#x200B;*store* ヘッダーを持つ次のGraphQLのミューテーションを使用します。

   ```graphql
   mutation {
       requestPasswordResetEmail(
           email: "test@gmail.com"
       )
   }
   ```

1. メールをチェック。

<u>期待される結果</u>:

* メールの件名、リンク、コンテンツの言語は、ストアビューのロケールと一致しています。
* パスワードリセットのリクエストは、リクエストのストアヘッダーに関係なく、お客様のアカウントが実際に登録されているストアから送信されます。

<u>実際の結果</u>:

メールには次のような内容が記載されています。

* パスワードのリセット リンクには、「デフォルト」のストアコードがあります。
* その問題は英語です。
* 内容はフランス語です。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
