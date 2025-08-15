---
title: MDVA-39305-V3：が有効になっている場合のログインの問題  [!DNL Google reCAPTCHA]
description: が有効になっている場合に、登録されたお客様がログインできないAdobe Commerceの問題を修正するために、MDVA-39305-V3 パッチ  [!DNL Google reCAPTCHA]  適用します。 このパッチでは、完全に読み込まれる前にフォームを送信できる問題も修正  [!DNL Google reCAPTCHA]  れています。 また、CMSページのデフォルト以外の場所でブロックが使用された場合の、「メンバー関数の呼び出しが null で isDisabled （）」というエラーも修正されます。
feature: Console
role: Admin
exl-id: 63e880aa-9a2e-4c34-9ead-20bfc5204f2c
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

---

# MDVA-39305-V3：有効な [!DNL Google reCAPTCHA] でのログインの問題

>[!NOTE]
>
>このパッチは [MDVA-39305](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-1/mdva-39305-login-issues-with-enabled-google-recaptcha.md) パッチのアップデートです。

MDVA-39305-V3 パッチにより、登録ユーザが [!DNL Google reCAPTCHA] が有効な場合にログインできない問題が修正されました。 また、このパッチでは、フォームが完全に読み込まれる前にフォームを送信でき [!DNL Google reCAPTCHA] 問題も修正されています。 さらに、CMSページのデフォルト以外の場所でブロックが使用された場合の、エラー *メンバー関数の呼び出しが null の場合は isDisabled （）* が修正されます。

このパッチは、[Quality Patches Tool （QPT） ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)1.1.48 リリースで追加されました。 QPT 1.1.58 リリースで更新され、新しいAdobe Commerce バージョン 2.4.7 ～ 2.4.7-p4 が含まれるようになりました。 パッチ ID は MDVA-39305-V3 です。 この問題は、Adobe Commerce バージョン 2.4.4、2.4.5-p2、2.4.7 で修正されました。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4、2.4.5-p2、2.4.7

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4-p1 - 2.4.7-p4

>[!NOTE]
>
>パッチは、新しい Quality Patches Tool リリースを使用する他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

### ケース I

1. 登録されたお客様は、有効な [!DNL Google reCAPTCHA] を使用してログインすることはできません。
1. フォームは、完全に読み込まれる前に送信 [!DNL Google reCAPTCHA] きます。

<u> 再現手順 </u>:

1. **[!UICONTROL Store]**/**[!UICONTROL Configuration]**/**[!UICONTROL Security]**/**[!DNL Google reCAPTCHA Storefront]** に移動し、***[!DNL Google reCAPTCHA]***&#x200B;を有効にします。
1. フロントエンドに移動します。
1. ブラウザーで **[!UICONTROL Developer Tool Console]** を開きます。

<u> 期待される結果 </u>:

コンソールに CSP 警告はありません。

<u> 実際の結果 </u>:

コンソールでの CSP 警告。

### 事例 2

CMS ページのデフォルト以外の場所でブロックが使用されると、*null の場合はメンバー関数 isDisabled （）の呼び出し* というエラーがスローされます。

<u> 再現手順 </u>:

1. 次の内容の静的ブロックを作成します。

   ```
   {{block class="Magento\Newsletter\Block\Subscribe" name="home.form.subscribe"
   template="Magento_Newsletter::subscribe.phtml"}}
   ```

1. **[!UICONTROL Admin]**/**[!UICONTROL Content]**/**[!UICONTROL Pages]**/**[!UICONTROL Add/Edit CMS page]**/**[!UICONTROL Content]** を使用して、CMSページに静的ブロックを追加します。
1. ページを保存します

<u> 期待される結果 </u>:

エラーなしでページが読み込まれます。

<u> 実際の結果 </u>:

ストアフロントのページで 500 エラーが発生。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
