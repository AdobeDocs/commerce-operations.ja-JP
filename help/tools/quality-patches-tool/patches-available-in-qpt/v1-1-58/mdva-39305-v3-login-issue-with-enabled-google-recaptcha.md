---
title: MDVA-39305-V3：有効になっているログインの問題 [!DNL Google reCAPTCHA]
description: MDVA-39305-V3 パッチを適用して、 [!DNL Google reCAPTCHA] が有効になっている場合に登録ユーザーがログインできないAdobe Commerceの問題を修正します。 このパッチは、 [!DNL Google reCAPTCHA] 完全に読み込まれる前にフォームを送信できる問題も修正します。 さらに、CMS ページのデフォルト以外の場所でブロックが使用されている場合に、null*で*メンバー関数への呼び出し*isDisabled （）というエラーが修正されます。
feature: Console
role: Admin
exl-id: 63e880aa-9a2e-4c34-9ead-20bfc5204f2c
type: Troubleshooting
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '522'
ht-degree: 0%

---

# MDVA-39305-V3：有効な[!DNL Google reCAPTCHA]でのログインの問題

>[!NOTE]
>
>このパッチは、[MDVA-39305](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-1/mdva-39305-login-issues-with-enabled-google-recaptcha.md) パッチのアップデートです。

MDVA-39305-V3 パッチは、[!DNL Google reCAPTCHA]が有効になっている場合に登録された顧客がログインできない問題を修正します。 このパッチは、[!DNL Google reCAPTCHA]が完全に読み込まれる前にフォームを送信できる問題も修正します。 さらに、CMS ページのデフォルト以外の場所でブロックが使用されている場合、null *のメンバー関数への呼び出し*&#x200B;が無効（）になるエラーを修正します。

このパッチは、[品質パッチツール （QPT） &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.48 リリースで追加されました。 QPT 1.1.58 リリースで更新され、新しいAdobe Commerce バージョン 2.4.7 - 2.4.7-p4が含まれるようになりました。 パッチ IDはMDVA-39305-V3です。 この問題は、Adobe Commerce バージョン 2.4.4、2.4.5-p2、および2.4.7で修正されています。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4、2.4.5-p2、2.4.7

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4-p1 - 2.4.7-p4

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

### ケース I

1. 登録済みのお客様は、有効な[!DNL Google reCAPTCHA]を使用してログインできません。
1. [!DNL Google reCAPTCHA]が完全に読み込まれる前にフォームを送信できます。

<u>複製する手順</u>:

1. **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Security]** > **[!DNL Google reCAPTCHA Storefront]**&#x200B;に移動し、***[!DNL Google reCAPTCHA]***&#x200B;を有効にします。
1. フロントエンドに移動します。
1. ブラウザーで&#x200B;**[!UICONTROL Developer Tool Console]**&#x200B;を開きます。

<u>期待される結果</u>:

コンソールにCSP警告はありません。

<u>実際の結果</u>:

コンソールのCSP警告。

### 事例II

CMS ページのデフォルト以外の場所でブロックを使用すると、null *の* メンバー関数への呼び出しisDisabled （）というエラーがスローされます。

<u>複製する手順</u>:

1. 次の内容の静的ブロックを作成します。

   ```text
   {{block class="Magento\Newsletter\Block\Subscribe" name="home.form.subscribe"
   template="Magento_Newsletter::subscribe.phtml"}}
   ```

1. **[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Pages]** > **[!UICONTROL Add/Edit CMS page]** > **[!UICONTROL Content]**&#x200B;のCMS ページに静的ブロックを追加します。
1. ページを保存します。

<u>期待される結果</u>:

ページがエラーなしで読み込まれます。

<u>実際の結果</u>:

ストアフロントのページで500 エラーが発生します。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
