---
title: 'ACSD-51666: エラー「セッションの有効期限が切れています。再度ログインしてください。」 ログイン後'
description: ACSD-51666 パッチを適用して、Adobe Commerceの問題を修正します。*セッションの有効期限が切れています。再度ログインしてください。*ログインを試みると発生します。
feature: Customers
role: Admin, Developer
exl-id: 8968b314-6625-45fa-9733-20560cca7089
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '513'
ht-degree: 0%

---

# ACSD-51666: エラー&#x200B;*セッションの有効期限が切れています。再度ログインしてください。* ログイン後

ACSD-51666 パッチは、エラー&#x200B;*セッションの有効期限が切れた問題を修正します。もう一度ログインしてください。* ログインを試みた後に発生します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.36がインストールされている場合に利用できます。 パッチ IDはACSD-51666です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

エラー&#x200B;*セッションの有効期限が切れています。再度ログインしてください。* 別のデバイスでパスワードをリセットした後、1つのデバイスから新しいパスワードでログインしようとすると。 カスタムモジュールによって追加されたページに追加のAjax リクエストがある場合にのみ発生します。

<u>複製する手順</u>:

1. ストアフロントの各ページにAjax リクエストを追加するカスタムモジュールをインストールします。
1. 新しいアカウントを作成します。
1. ログアウトして、ログインページに戻ります。
1. 別のブラウザーで&#x200B;*パスワードを忘れた* リンクを開き、*パスワードのリセット*&#x200B;の電子メールを送信します。
1. 最初のブラウザーでパスワードリセットの電子メールを開き、新しいパスワードを設定します。
1. 2つ目のブラウザーでログインしてみてください。

<u>期待される結果</u>:

最初の試行で正常にログインできます。

<u>実際の結果</u>:

* *セッションの有効期限が切れています。再度ログインしてください。* エラー：
* ログインしておらず、ホームページにリダイレクトされます。
* 2回目のログインが成功しました。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
