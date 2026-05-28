---
title: ACSD-48570:URLのストアコードで管理者リセットのパスワードリンクの問題を修正する
description: ACSD-48570 パッチを適用して、[!UICONTROL Add Store Code to URLs]設定が有効になっている場合に、管理者パスワードのリセット リンクを介してパスワードのリセット ページにアクセスできないAdobe Commerceの問題を修正します。
feature: Security, User Account
role: Admin, Developer
exl-id: 049a82ff-80e3-46a1-8472-ac74de0e365f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 0%

---

# ACSD-48570:URLのストアコードで管理者リセットのパスワードリンクの問題を修正する

*[!UICONTROL Add Store Code to URLs]*&#x200B;設定が有効になっているときに、管理者パスワードのリセット リンクを介してパスワードのリセット ページにアクセスできないAdobe Commerceの問題を修正するためのACSD-48570 パッチ。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58がインストールされている場合に利用できます。 パッチ IDはACSD-48570です。 この問題は、Adobe Commerce 2.4.7で修正されています。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.6-p8

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

**[!UICONTROL Add Store Code to URLs]**設定が有効になっている場合、管理者パスワードのリセット機能が正しく機能しません。
管理者ユーザーがパスワードリセットをリクエストし、電子メールの回復リンクをクリックすると、パスワードリセット フォームに移動する代わりに、ログインページにリダイレクトされるか、404 エラーが表示されます。 これにより、管理者は手動で操作することなくアカウントを回復できます。

<u>複製する手順</u>:

1. **[!UICONTROL Add Store Code to URLs]**&#x200B;設定を&#x200B;**[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Web]** > **[!UICONTROL URL Options]**&#x200B;で有効にします。
1. 管理者パネルからログアウトし、管理者ログインページの&#x200B;**[!UICONTROL Forgot your password?]** リンクをクリックします。
1. 管理者ユーザーの電子メールを入力し、Captchaを渡して、**[!UICONTROL Retrieve Password]**&#x200B;をクリックします。
1. パスワードリセットの電子メールを開き、パスワード回復リンクをクリックします。

<u>期待される結果</u>:

パスワードのリセット フォームが表示されます。

<u>実際の結果</u>:

パスワードのリセットフォームの代わりに、ログインページまたは404 エラーページが表示されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
