---
title: MDVA-39305：有効なGoogle reCAPTCHAでのログインの問題
description: MDVA-39305 パッチを適用して、Google reCAPTCHAが有効になっている場合に登録ユーザーがログインできないAdobe Commerceの問題を修正します。
feature: Console
role: Admin
exl-id: c40fd84a-73dc-42bd-8cda-58738615fbba
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%

---

# MDVA-39305：有効なGoogle reCAPTCHAでのログインの問題

>[!NOTE]
>
>このパッチは更新され、最新のパッチ IDはMDVA-39305-V3です。 新しいパッチは、Adobe Commerce バージョン 2.4.4、2.4.5-p2、および2.4.7用に作成されました。 詳しくは、[MDVA-39305-V3](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-58/mdva-39305-v3-login-issue-with-enabled-google-recaptcha.md) パッチ記事を参照してください。

MDVA-39305 パッチでは、Google reCAPTCHAが有効になっている場合に、登録されたお客様がログインできない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.1がインストールされている場合に利用できます。 パッチ IDはMDVA-39305です。 この問題は、Adobe Commerce バージョン 2.4.4および2.4.7で修正されています。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce on cloud infrastructure 2.4.2-p1、2.4.3-p3、2.4.5-p2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方式） 2.4.1-p1 - 2.4.3-p3、2.4.4-p1 - 2.4.4-p5、2.4.5 - 2.4.6-p2

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

登録済みのお客様は、有効なGoogle reCAPTCHAを使用してログインできません。

<u>複製する手順</u>:

1. **Store** > **Configuration** > **Security** > **Google reCAPTCHA Storefront**&#x200B;に移動し、**Google reCAPTCHA**&#x200B;を有効にします。
1. **フロントエンド**&#x200B;に移動します。
1. ブラウザーで&#x200B;**Developer Tool Console**&#x200B;を開きます。

<u>期待される結果</u>:

コンソールにCSP警告はありません。

<u>実際の結果</u>:

コンソールのCSP警告。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [品質パッチツール ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
