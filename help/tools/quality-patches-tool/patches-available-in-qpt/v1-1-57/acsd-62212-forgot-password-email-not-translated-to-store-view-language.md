---
title: ACSD-62212:[!UICONTROL Forgot Password] メールは、ストア表示言語に翻訳されません
description: ACSD-62212 パッチを適用すると、*[!UICONTROL Forgot Password]* メールのコンテンツがストア表示の言語に翻訳されないAdobe Commerceの問題を修正できます。
feature: GraphQL
role: Admin, Developer
exl-id: 29e6f2fa-574f-4ab1-82f5-88e1eb1de83e
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# ACSD-62212:*[!UICONTROL Forgot Password]* メールは、ストア表示言語に翻訳されません

ACSD-62212 パッチでは、*[!UICONTROL Forgot Password]* メールのコンテンツがストア表示言語に翻訳されない問題が修正されています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 1.1.57 がインストールされている場合に使用できます。 パッチ ID は ACSD-62212 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p2

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

登録されたストア以外のストアビューでGraphQLを介してパスワードをリセットすると、パスワードリセットリンクが起動元のストアビューと一致しません。

<u> 再現手順 </u>:

1. *[!UICONTROL Main Website Store]* の下にセカンダリストア表示を作成します。
1. セカンダリ ストア ビューのスコープで *[!UICONTROL Locale]* を *[!UICONTROL French (France)]* に切り替えます。
1. 翻訳用のフランス語言語パックをインストールします。
1. 顧客アカウントを作成します。
1. 次のGraphQLミューテーションを *store* ヘッダーと共に、セカンダリストア表示コードで使用します。

   ```
   mutation {
       requestPasswordResetEmail(
           email: "test@gmail.com"
       )
   }
   ```

1. メールを確認します。

<u> 期待される結果 </u>:

* メールの件名、リンクおよびそのコンテンツの言語は、ストア表示のロケールと一致します。
* パスワードリセットリクエストは、リクエストのストアヘッダーに関係なく、顧客のアカウントが実際に登録されているストアから送信されます。

<u> 実際の結果 </u>:

メールには次の内容が含まれています。

* パスワードのリセットリンクには、「デフォルト」のストアコードが含まれています。
* 主題は英語です。
* コンテンツはフランス語です。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md)[!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
