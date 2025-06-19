---
title: ACSD-48570:URL のストアコードに関する管理者リセットパスワードリンクの問題の修正
description: '[!UICONTROL Add Store Code to URLs] 設定が有効な場合に、管理者によるパスワードのリセットリンクからパスワードのリセットページにアクセスできなかったAdobe Commerceの問題を修正するために、ACSD-48570 パッチを適用してください。'
feature: Security, User Account
role: Admin, Developer
exl-id: 049a82ff-80e3-46a1-8472-ac74de0e365f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# ACSD-48570:URL のストアコードに関する管理者リセットパスワードリンクの問題の修正

*[!UICONTROL Add Store Code to URLs]* 設定が有効な場合に、管理者のパスワードリセットリンクからパスワードリセットページにアクセスできなかったAdobe Commerceの問題を修正するための ACSD-48570 パッチ。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58 がインストールされている場合に使用できます。 パッチ ID は ACSD-48570 です。 この問題はAdobe Commerce 2.4.7 で修正されました。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.6-p8

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

**[!UICONTROL Add Store Code to URLs]** 設定が有効になっている場合、管理者のパスワードのリセット機能が正しく動作しません。
管理者ユーザーがパスワードのリセットを要求してメール内の回復リンクをクリックすると、パスワードのリセットフォームに移動する代わりに、ログインページにリダイレクトされるか、404 エラーが表示されます。 これにより、管理者は手動で操作せずにアカウントを復元できなくなります。

<u> 再現手順 </u>:

1. **[!UICONTROL Store]**/**[!UICONTROL Configuration]**/**[!UICONTROL General]**/**[!UICONTROL Web]**/**[!UICONTROL URL Options]** で **[!UICONTROL Add Store Code to URLs]** 設定を有効にします。
1. 管理パネルからログアウトし、管理者ログインページの「**[!UICONTROL Forgot your password?]**」リンクをクリックします。
1. 管理者ユーザーのメールアドレスを入力し、captcha を渡して、「**[!UICONTROL Retrieve Password]**」をクリックします。
1. パスワードリセットメールを開き、パスワード回復リンクをクリックします。

<u> 期待される結果 </u>:

パスワードリセットフォームが表示されます。

<u> 実際の結果 </u>:

ログインページまたは 404 エラーページが、パスワードリセットフォームの代わりに表示されます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
