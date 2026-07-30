---
title: ACSD-50345：チェックアウト時のreCAPTCHAの問題
description: ACSD-50345 パッチを適用して、注文中およびチェックアウト中にreCAPTCHA v2およびv3の検証が失敗するAdobe Commerceの問題を修正します。
feature: Checkout, Orders
role: Admin
exl-id: eae9a6ad-0999-4581-b3c0-7667ee7beb54
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '505'
ht-degree: 0%

---

# ACSD-50345：チェックアウト時のreCAPTCHAの問題

ACSD-50345 パッチは、注文中およびチェックアウト中にreCAPTCHA v2およびv3の検証が失敗する問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.31がインストールされている場合に利用できます。 パッチ IDはACSD-50345です。 この問題はAdobe Commerce 2.4.6で部分的に修正され、Adobe Commerce 2.4.7で完全に修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3 - 2.4.5-p2

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

**ケース #1**

Google reCAPTCHA v2は、支払い失敗を送信した後にリロードされません。

<u>複製する手順</u>

1. **[!UICONTROL Google reCAPTCHA v2]**&#x200B;を設定します（*ロボットではありません*）。
1. チェックアウト用に&#x200B;**[!UICONTROL reCAPTCHA]**&#x200B;を有効にします。
1. **[!UICONTROL reCAPTCHA]**&#x200B;をクリックせずに注文を試みます。
1. 見つからないreCAPTCHAのエラーメッセージ（*reCAPTCHA検証に失敗しました、*）をユーザーが受け取ったら、もう一度&#x200B;**[!UICONTROL reCAPTCHA]**&#x200B;をクリックして注文を試してください。

<u>期待される結果</u>

誤ったreCAPTCHAを使用して注文することはありません。

<u>実際の結果</u>

エラーがスローされました – *reCAPTCHA検証に失敗しました。もう一度やり直してください*、*ID = 4*&#x200B;のそのようなカートはありません

**ケース #2**

Google reCAPTCHA v3 Invisibleはチェックアウト時に機能しておらず、注文を行うことはできません。 `PlaceOrder` イベントはトリガーされません。

<u>複製する手順</u>

1. **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Security]**&#x200B;から&#x200B;**[!UICONTROL reCAPTCHA v3 Invisible]**&#x200B;を設定します。
1. 「**[!UICONTROL Storefront]**」タブで、チェックアウトまたは注文を行う場合は「**[!UICONTROL reCAPTCHA v3 Invisible]**」を有効にします。
1. [!UICONTROL Check/Money order]支払い方法で注文を試みます。

<u>期待される結果</u>

**[!UICONTROL reCAPTCHA]**&#x200B;をオンにして注文する必要があります。

<u>実際の結果</u>

**[!UICONTROL Place Order]** ボタンをクリックすると無効になり、それ以上何も起こりません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
